# Senior Design — EV Active Sensor Adapter

The final team-developed system used an **STM32G474** microcontroller, a **TI BQ79616** battery-monitor device, ten thermistor channels sampled by the STM32 ADC, UART links for the battery monitor and diagnostics, and extended-identifier CAN telemetry. The active source implements a timer-assisted service loop; an older repository README describes an aspirational FreeRTOS/DMA design that does not match the retained final firmware.

The MSP430FR2355 belongs to ECE 306. MSP430 examples retained beside this repository were preliminary/reference material and must not be presented as the final senior-design controller.

## System Purpose and Architecture

- Helped develop an EV active-sensor adapter that joined cell-voltage monitoring, temperature sensing, embedded control, CAN telemetry, and custom-PCB hardware.
- Used the STM32G474 as the central controller for sensing, subsystem state, scheduling, diagnostics, and communications.
- Connected the BQ79616 through a 1 Mbps UART path for battery-cell measurements and device control.
- Sampled ten thermistors through the STM32 ADC and reported temperature and battery information over CAN.
- Used a second UART for diagnostic logging and LEDs for visible subsystem state during bring-up.
- Defined subsystem boundaries so battery-monitor faults could be isolated without stopping thermistor acquisition or CAN reporting.

### Short subsystem map

- **Controller and scheduling:** STM32G474 running a timer-assisted service loop with subsystem-status flags.
- **Cell-voltage measurement:** TI BQ79616 battery monitor using a framed UART protocol, CRC-16 validation, wake/configuration sequencing, register access, and cell-voltage reads.
- **Temperature measurement:** ten thermistor channels acquired through the STM32G4 ADC with calibration, channel-settling handling, and lookup/interpolation conversion.
- **Vehicle/network interface:** FDCAN peripheral used for extended-identifier CAN telemetry; the exact external CAN-transceiver part number is not yet recovered.
- **Diagnostics and integration:** secondary UART logging, per-subsystem LED states, timers, power/sensing connections, and custom-PCB interfaces.

## Requirements, Interfaces, and Technical Risk

- Developed system requirements and interface specifications spanning sensing, battery monitoring, power, embedded control, communications, and custom hardware.
- Translated operating constraints and component requirements into hardware interfaces, firmware behavior, register/data expectations, and validation criteria.
- Identified integration risks involving electrical compatibility, protocol behavior, timing, blocking I/O, component availability, custom-board interfaces, and subsystem dependencies.
- Maintained architecture diagrams, interface definitions, design decisions, risk tracking, progress reports, and test-planning material.

## Component Evaluation and BMS-Related Design

- Evaluated battery-management and supporting components against voltage range, sensing, protection, communication, packaging, footprint, and sourcing requirements.
- Reviewed datasheets, reference designs, interface requirements, and custom-board constraints before committing hardware and firmware interfaces.
- Documented candidate tradeoffs, selection rationale, limitations, and follow-on validation needs.
- Connected component selection to schematic integration, firmware initialization, communication, test access, and PCB implementation.
- Final active firmware supports the BQ79616 battery-monitor path; do not describe this as a complete production BMS, charger, or safety-certified system.

## Firmware and Peripheral Implementation

### BQ79616 communication and bring-up

- Implemented command/response framing, CRC-16 validation, UART transport, wake-pulse generation, baud configuration, register access, keep-alive/fault behavior, cell-voltage reads, and an explicit shutdown path.
- Switched the BQ UART pin between GPIO and alternate-function modes to generate the wake pulse before restoring UART operation.
- Used the Cortex-M DWT cycle counter for microsecond wake timing.
- Added focused diagnostics for startup, communication, CRC, voltage-read, and subsystem faults.

### Thermistor and ADC acquisition

- Sampled ten thermistor inputs with the STM32G4 ADC.
- Calibrated the ADC, allowed settling after channel changes, discarded the first conversion after a change, and converted measurements through a lookup/interpolation path.
- Computed and packaged individual and summary temperature information for telemetry and diagnostics.

### CAN telemetry and system state

- Worked within the team-developed CAN path that sent address-claim, thermal-summary, individual-thermistor, and segmented external-voltage messages using extended identifiers.
- Maintained separate subsystem states so a failed BQ path did not stop thermistor acquisition or CAN reporting.
- Added structured logs and subsystem-specific LED behavior so initialization and runtime faults were visible during bring-up.
- Do not claim sole authorship of the complete CAN subsystem; public Git history shows meaningful teammate ownership of CAN, fault-testing, timing, and external-ADC-to-CAN work.

## Debugging, Timing, and Validation

- Planned and performed subsystem-level tests before full custom-PCB integration.
- Diagnosed a CAN-cadence problem involving both incorrect TIM7 period/interrupt wiring and long blocking BQ reads.
- Corrected the STM32G474 `TIM7_DAC` interrupt-vector path and reduced selected BQ timeouts so the service loop could meet its recorded 100/200 ms send intervals.
- Used communication checks, measured data, controller state, CAN output, UART logs, timing, and visible status indicators to isolate faults at subsystem boundaries.
- Retained test results record seven passing host-side helper tests covering temperature conversion, CAN identifiers/payloads, min/max/average calculations, boundary cases, and checksums.
- Do not claim a production-ready, vehicle-deployed, or safety-certified system; the evidence supports collaborative implementation, bench integration, and validation.

## Documentation, Reviews, and Teamwork

- Coordinated interfaces and dependencies across firmware, battery-monitor, thermal-sensing, CAN, and hardware responsibilities.
- Communicated specifications, design choices, technical risks, progress, and validation results during design reviews.
- Maintained bring-up, flashing, pinout, communication, troubleshooting, architecture, code-map, and known-issue documentation for team use and handoff.
- Used written requirements and interface definitions to keep firmware, hardware, sensing, and communication work aligned.

### Public Git history and attribution

- The public repository contains 46 commits: 35 under Connor/Connor Savugot and 11 under teammate Kayla Radu. Commit counts are evidence of participation, not a complete measure of contribution.
- Connor's recorded work includes BQ bring-up, successful voltage-tap reads, wake-path simplification, CRC/fault fixes, service-loop and subsystem-status restructuring, thermistor logging/data changes, shutdown control, diagnostics, and documentation.
- Teammate history includes meaningful CAN, fault-testing, external-ADC-to-CAN, and timing work.
- Present the result as a collaborative senior-design system and identify Connor's BQ, bring-up, debugging, and integration work rather than claiming sole system authorship.

## Best Resume Themes

- STM32G474 embedded-C firmware and peripheral bring-up
- BQ79616 UART protocol, CRC, wake/configuration, cell-voltage measurement, and fault handling
- Ten-channel thermistor/ADC acquisition and conversion
- Extended-identifier CAN telemetry and cross-subsystem integration
- Timing and blocking-I/O root-cause analysis
- Degraded-mode subsystem isolation, diagnostic logging, and status indicators
- Custom-PCB interfaces, staged validation, requirements, specifications, design reviews, and team documentation

## Source-of-Truth Boundaries

- Active source supports a timer-assisted service loop, not FreeRTOS.
- Active source does not support the stale README's planned ADC DMA architecture.
- Do not claim MAX17841/MAX17854, TMS570, MSP430, or a completed CAN-FD implementation as the final controller architecture.
- The FDCAN peripheral name does not by itself prove that CAN FD frames were used; public wording should say CAN or extended-identifier CAN telemetry.
- Exact CAN-transceiver part number, final vehicle integration, and safety-certification status remain unconfirmed.

## Details Requiring Confirmation

- Exact team size beyond the two public Git contributors
- PCB schematic/layout ownership and the exact external CAN-transceiver part number
- Final integrated-prototype and vehicle-deployment status
- Highest completed hardware-validation level outside the retained repository evidence
- Whether additional vehicle-interface or safety-monitoring details are public

## Personal Contribution Clarification — September 19, 2026

Connor confirms ownership of voltage and temperature sensing firmware, LED indicators, state-machine logic, and error logging. He did not author the CAN middleware or CAN messaging subsystem. His CAN integration work included adjusting timers used by CAN, validating and modifying CAN-port GPIO configuration, and programming the associated interrupts. Public résumé wording should mention CAN integration without detailing that subsystem or implying CAN middleware/message ownership.
