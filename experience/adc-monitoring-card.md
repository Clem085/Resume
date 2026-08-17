# AEGIS ADC Filter Selection, Scaling, and MATLAB/CAN Analysis

**Setting:** AEGIS Power Systems — full-time Embedded Firmware Engineer, May 2026–Present  
**Purpose:** Stable, correctly scaled converter telemetry that still responds promptly to real electrical changes  
**Primary tools:** Embedded C, MATLAB, CAN captures, MCP342x/MCP3428 ADC architecture

This entry expands professional work completed in Connor's current full-time AEGIS role; it does not belong to either internship. The central accomplishment was using captured system data to determine ADC scaling and select practical embedded filters—not the absolute voltage/current ranges themselves. The measurements were intended for display, logging, and engineering visibility, not fast protection or closed-loop converter control.

## Core Accomplishment

- Parsed captured CAN text output into MATLAB time-series data.
- Used the recorded data to determine and check the per-channel factors that converted raw ADC output into meaningful telemetry.
- Applied several candidate filtering functions to the same captured data so their behavior could be compared directly.
- Evaluated the characteristics that mattered for the product: variation while the electrical input was stable and the time required for the filtered output to follow a large, real change.
- Selected rolling-average and exponential moving average (EMA) approaches based on that stability-versus-response tradeoff.
- Implemented the rolling average in embedded C with a fixed sample window, circular replacement of the oldest sample, and a maintained rolling sum.
- Kept the EMA state-efficient: it retained only the previous filtered value and moved it toward each new sample by a selected fraction of the difference, with no sample-history buffer.

The component architecture was based on the Microchip MCP342x family, specifically the four-channel MCP3428-style arrangement. Microchip's [MCP3426/7/8 data sheet](https://ww1.microchip.com/downloads/aemDocuments/documents/OTH/ProductDocuments/DataSheets/22226a.pdf) supports the device facts used below: MCP3428 has four differential channels, a 2.048 V internal reference, selectable PGA gains, I2C communication, and a 15-sample-per-second conversion rate in 16-bit mode.

## Hardware Context (Supporting Detail)

The monitoring card covered four converter telemetry channels:

| Channel | Engineering range | Nominal ADC range | Front-end design approach |
| --- | ---: | ---: | --- |
| Input voltage, `VIN` | 0–1000 V | 0–2.000 V | high-voltage divider, approximately 1/500 attenuation |
| Input current, `IIN` | 0–30 A | 0–1.500 V | shunt/current-sense amplifier or isolated Hall/current sensor |
| Output voltage, `VOUT` | 0–300 V | 0–2.000 V | high-voltage divider, approximately 1/150 attenuation |
| Output current, `IOUT` | 0–100 A | 0–1.500 V | shunt/current-sense amplifier or isolated Hall/current sensor |

### Architecture decisions

- Treated the MCP342x as the low-voltage digitizer, not as a device that could directly accept converter voltage or current.
- Specified external scaling/isolation appropriate to each measurement before signals reached the ADC input range.
- Selected 16-bit/15-SPS operation to prioritize resolution for slow monitoring rather than maximizing sample rate.
- Used PGA = 1 for channels whose front ends already mapped the signal into the ADC's approximately ±2.048 V differential range.
- Preserved headroom by mapping the voltage channels to about 2.000 V and current channels to about 1.500 V instead of driving the ADC exactly to positive full scale.
- Recognized that 2.000 V leaves only 48 mV, or about 2.34%, below the nominal 2.048 V positive limit, so divider tolerance, reference error, and electrical overrange still belong in the saturation budget.
- Accounted for signed two's-complement ADC output; a unipolar 0 V-to-positive mapping uses only the positive half of the bipolar code range.
- Used the four-channel architecture for `VIN`, `IIN`, `VOUT`, and `IOUT`; because the channels share an input multiplexer, their conversions are sequential rather than truly simultaneous.
- At the nominal 15 conversions per second in 16-bit mode, one conversion takes about 66.7 ms; cycling four channels yields roughly 3.75 updates per second per channel and a 267 ms scan before command/scheduling overhead.
- Treated temporally adjacent voltage/current samples as sufficiently close for slow DC telemetry. Firmware must select the intended channel, wait for fresh conversion data, and avoid reusing a prior channel's result. This architecture is not evidence of simultaneous-sampling power analysis or fast transient capture.

### Front-end safety and implementation boundary

The divider and current-sensor descriptions are system-design requirements, not a claim that every final analog component, layout, protection element, or isolation barrier was personally selected and production-qualified. A deployable 1000 V divider also requires appropriate resistor voltage/power ratings, series distribution, creepage/clearance, filtering, input protection, fault analysis, and isolation review. The ADC's switched-capacitor input and source impedance can load a high-value divider or affect settling, so buffering/drive requirements must be evaluated. External analog filtering is also required where converter-switching content could alias; digital smoothing cannot repair aliased noise or ADC saturation. The exact current-sensing topology ultimately selected is not yet recorded.

## Ideal ADC Scaling

In 16-bit mode at PGA = 1, the signed MCP342x transfer function uses an ideal LSB of:

```text
LSB = 2.048 V / 32768 counts = 62.5 µV/count
```

The nominal mappings therefore produce these initial engineering-unit scales:

| Channel | Nominal full-scale code | Ideal initial scale |
| --- | ---: | ---: |
| `VIN` at 2.000 V ADC input | 32,000 counts | 0.03125 V/count |
| `IIN` at 1.500 V ADC input | 24,000 counts | 0.00125 A/count |
| `VOUT` at 2.000 V ADC input | 32,000 counts | 0.009375 V/count |
| `IOUT` at 1.500 V ADC input | 24,000 counts | approximately 0.004167 A/count |

The ideal conversions can be expressed as:

```text
VIN  = raw_VIN  × 0.03125 V/count
IIN  = raw_IIN  × 0.00125 A/count
VOUT = raw_VOUT × 0.009375 V/count
IOUT = raw_IOUT × 0.0041667 A/count
```

These constants are design estimates derived from nominal front-end ratios and the ADC transfer function. They are not substitutes for calibration.

## Per-Channel Calibration

- Defined a separate linear calibration model for each voltage/current channel rather than assuming theoretical divider, sensor, reference, and offset values were exact.
- Represented calibrated engineering units with a slope/intercept model:

```text
engineering_value = calibration_slope × raw_code + calibration_intercept
```

- Kept channel-specific constants because divider tolerance, current-sensor gain/offset, wiring, ADC offset/gain, and board behavior can differ between channels.
- Distinguished the ADC's internal self-calibration from end-to-end channel calibration; internal correction does not remove divider, shunt, amplifier, Hall-sensor, wiring, or temperature errors.
- Separated nominal scaling from production calibration so firmware could retain understandable physical units while calibration data corrected the actual measurement path.
- Recognized that a linear slope/intercept model assumes the complete front end is sufficiently linear; sensor nonlinearity or temperature drift may require additional characterization.
- Calibration coefficients, calibration-point count, storage method, production procedure, and measured residual error are not yet documented and should not be invented in a résumé.

## Power and Efficiency Calculations

For monitoring—not high-speed power-quality analysis—the intended computation sequence was:

```text
PIN_sample  = VIN_sample  × IIN_sample
POUT_sample = VOUT_sample × IOUT_sample

PIN  = filtered or averaged PIN_sample
POUT = filtered or averaged POUT_sample

efficiency_percent = (POUT / PIN) × 100
```

Engineering considerations:

- Scale/calibrate voltage and current before interpreting the product in watts.
- Pair temporally adjacent voltage/current conversions and account for channel-multiplexer skew if the electrical values can change materially between samples.
- Treat the product as a low-rate sampled power estimate, not a true instantaneous or switching-waveform measurement.
- Average or filter the sampled power products; in general, multiplying independently averaged voltage and current is not equivalent when ripple or correlated variation exists.
- Guard efficiency calculation against zero or very small input power and define sign conventions for bidirectional behavior before division.
- Evaluate efficiency over a stable time window; during transients, sample skew and energy stored in converter components can make a point ratio misleading.
- Use sufficiently wide intermediate types or carefully scaled fixed-point arithmetic so voltage-current multiplication and accumulated sums cannot overflow.
- Do not describe this as a revenue-grade power meter, simultaneous-sampling analyzer, protection circuit, or closed-loop-control measurement path.

## Filtering Strategy

### Engineering objective

- Reduce sample-to-sample variation when the underlying electrical value is not changing.
- Minimize the time required for the filtered output to reflect a genuine, large electrical change.
- Compare both behaviors on the same captured data instead of choosing a filter only from theory or visual smoothness.
- Determine scaling factors and filter behavior together so a stable plot could not hide an incorrectly scaled measurement.
- Keep the selected methods simple, predictable, and inexpensive enough for embedded firmware.

### Evaluated processing sequence

```text
raw ADC code
    → channel scaling/calibration
    → rolling average or exponential moving average
    → display/logging/CAN telemetry
```

- Evaluated several filtering functions by parsing captured CAN output in MATLAB and plotting their responses on the same telemetry.
- Selected a rolling average and an exponential moving average as the useful embedded approaches.
- Used variation under steady input and time to follow a large change as the primary comparison criteria; no unsupported numerical threshold or improvement is claimed.
- Implemented the rolling average in embedded C with the last `N` samples, a rolling sum, circular replacement of the oldest value, and `output = sum / N` once the window was full.
- Defined the EMA using only the prior filtered value: each new sample moved the output by a fraction of the difference, requiring no `N`-sample buffer.
- Recognized that both methods trade smoother readings for lag: a longer rolling window or smaller EMA coefficient produces greater smoothing but slower response.
- Retained the distinction that RMS is an effective/heating diagnostic rather than an outlier-removal or DC-display smoothing method.

### Confirmed versus unconfirmed filtering details

- **Confirmed implementation:** an embedded-C rolling average using persistent samples, a circular index, and a rolling sum.
- **Confirmed analysis:** multiple candidate filters were compared in MATLAB using parsed CAN text captures, including variation under steady input and time to follow large changes.
- **Confirmed selection:** rolling-average and EMA approaches were chosen from the comparison.
- **Not yet recorded:** the other candidate functions, rolling-window length, EMA coefficient, sample cadence, numerical stability/response results, whether both selected approaches were deployed, and reuse in regression testing.

## Embedded-C Rolling Average

The single-channel implementation accepts one new ADC reading per call. During startup it averages only the samples collected so far. Once the buffer is full, it removes the oldest value, inserts the new value, updates the rolling sum, and returns the fixed-window average without rescanning the entire buffer.

The following is a cleaned version of that concept. It uses a 64-bit accumulator to reduce overflow risk while preserving a 32-bit sample and return type:

```c
#include <stddef.h>
#include <stdint.h>

/* NUM_SAMPLES must be greater than zero. */
int32_t filter_avg(int32_t current_reading)
{
    static int32_t samples[NUM_SAMPLES] = {0};
    static int64_t rolling_sum = 0;
    static size_t sample_count = 0;
    static size_t oldest_index = 0;

    if (sample_count == NUM_SAMPLES) {
        /* The window is full: remove the sample being replaced. */
        rolling_sum -= samples[oldest_index];
    } else {
        /* Startup: average only the valid samples collected so far. */
        ++sample_count;
    }

    samples[oldest_index] = current_reading;
    rolling_sum += current_reading;

    /* Advance the circular index without shifting the buffer. */
    if (++oldest_index >= NUM_SAMPLES) {
        oldest_index = 0;
    }

    /* C integer division truncates toward zero. */
    return (int32_t)(rolling_sum / (int64_t)sample_count);
}
```

### Implementation considerations

- The static state persists across calls without dynamic allocation, which is appropriate for a small single-channel embedded filter.
- One shared static function state must not mix `VIN`, `IIN`, `VOUT`, and `IOUT`. A four-channel implementation needs independent state per channel, commonly through separate instances of a filter-state structure.
- Static state also makes the function non-reentrant; ISR/task concurrency requires controlled ownership or synchronization.
- The compact function has no explicit reset path; a reusable state structure makes per-channel initialization and reset easier to test.
- A 32-bit rolling sum can overflow when the window or sample magnitude grows. A 64-bit accumulator or a proven range bound is safer.
- C integer division truncates toward zero. Optional rounding must handle positive and negative values deliberately.
- A right shift replaces division exactly only for power-of-two divisors and only with carefully defined signed/rounding behavior. Division by five cannot be replaced exactly by a simple shift.
- A compiler can often optimize division by a compile-time constant, so manual shift/reciprocal changes should follow measured timing or code-size needs.
- With a fixed sample count, scaling can be folded into the average:

```text
value = (sum_raw / N) × scale
value = sum_raw × (scale / N)
```

- The mathematically equivalent form can save an explicit intermediate average, but fixed-point ordering, coefficient precision, overflow, saturation, and rounding still determine whether the integer implementation remains equivalent.
- For affine calibration, apply the intercept once to the averaged result rather than accumulating the intercept once per sample; startup logic must also use the current sample count rather than the final window length.
- During startup, a partial-window average avoids the artificial low bias produced by averaging real samples together with zero-filled entries. An alternative instantaneous-output startup policy can be selected if required by the display behavior.

## Exponential Moving Average

The selected EMA alternative retained only the previous filtered output rather than an `N`-sample history:

```text
filtered_new = filtered_old + alpha × (sample_new - filtered_old)
```

- `alpha` is the fraction of the new error applied on each update.
- A smaller coefficient suppresses more steady-state fluctuation but takes longer to follow a large change.
- A larger coefficient follows changes faster but allows more sample-to-sample variation through.
- The EMA requires one prior filtered value per channel and no circular sample buffer.
- An embedded fixed-point implementation must define coefficient precision, intermediate width, signed rounding, and startup initialization deliberately.
- The exact coefficient and deployment status are not yet recorded; do not invent a numerical value or measured response time.

## MATLAB Validation and Engineering Communication

- Parsed captured CAN text into scaled telemetry time series.
- Used the captured output to determine and check scaling factors and apply several filtering functions to a common dataset.
- Compared steady-state variation and the time each filtered output took to reflect a large electrical change.
- Used the comparisons to select rolling-average and EMA approaches rather than choosing only from theory.
- Coordinated implementation, blockers, test observations, and next steps through engineering standups with a geographically distributed firmware team.
- Current evidence does not establish that the MATLAB plots themselves were presented in standups; keep the data-analysis and team-communication claims distinct unless confirmed.

## Complete Engineering Workflow Demonstrated

1. Captured telemetry from CAN output and parsed it into MATLAB.
2. Determined and checked per-channel scaling factors against recorded behavior.
3. Ran several candidate filters on the same data.
4. Compared stability during unchanged input with response time after large changes.
5. Selected rolling-average and EMA approaches for embedded use.
6. Implemented the rolling average with integer-aware circular-buffer and rolling-sum logic.
7. Considered EMA state, lag, startup behavior, arithmetic precision, overflow, and coefficient tradeoffs.
8. Communicated implementation status and integration needs within a distributed firmware team.

## Resume-Ready Options

### Best combined embedded-firmware option

- Parsed captured CAN output in MATLAB to determine per-channel ADC scaling and compare several filter functions by steady-input variation and time to follow large electrical changes; selected rolling-average and EMA approaches and implemented the rolling average in embedded C using a circular buffer and rolling sum.

### More low-level-software focused

- Compared fixed-window rolling-average and single-state EMA designs for embedded telemetry, trading sample-history storage against an EMA that retained only its previous output.

### More hardware-integration focused

- Defined MCP3428 ADC scaling for four converter voltage/current channels, mapping high-voltage dividers and current-sense front ends into the ADC range and translating raw codes into calibrated engineering units.

## Claim and Disclosure Boundaries

- This was a slow telemetry path, not fast protection, control-loop feedback, or simultaneous-sampling instrumentation.
- Voltage/current ranges, ideal divider ratios, ADC targets, and nominal scale factors are design values; do not call them measured accuracy or production calibration results.
- The exact current-sensor topology, divider component network, isolation implementation, analog filtering, final PCB ownership, and hardware-qualification status are not yet recorded.
- The MCP3428 uses a channel multiplexer. Do not say all four channels were sampled simultaneously.
- Rolling-average implementation and selection of rolling-average and EMA approaches are confirmed. The other candidates, parameters, quantitative results, and whether both selected approaches were deployed remain unconfirmed.
- MATLAB processed captured CAN text offline; do not claim a live MATLAB-to-CAN interface.
- Do not publish proprietary schematics, calibration constants, raw CAN identifiers/frames, customer names, or internal board/product identifiers.
