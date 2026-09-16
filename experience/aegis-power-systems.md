# AEGIS Power Systems Experience

This file is the detailed source for Connor's current engineering role and his 2024 and 2025 internships. It generalizes internal products, customer details, network data, register maps, and proprietary power-stage information.

## Attribution Boundaries

- **Embedded Firmware Engineer (full-time):** May 2026–Present
- **Embedded Systems Intern:** May–August 2025
- **Computer Science Intern:** May–August 2024
- The STM32G474/BQ79616 EV sensor-adapter BMS research, component evaluation, and integration belongs to NC State senior design. Separate professional smart-battery CAN interface and power-system integration work belongs to AEGIS; do not merge the projects or describe either as a complete production BMS.
- Use exact task language for TI Embedded Linux work. Do not label it generically as “BSP work”; Connor's direct experience is with Yocto/Arago images and toolchains, kernel and device-tree compilation, boot/service integration, and board-level validation.

## Embedded Firmware Engineer — May 2026–Present

The current role spans low-level embedded firmware, CAN-connected power hardware, MATLAB data analysis, VPX platform management, 16-bit dsPIC33CK bring-up, Embedded Linux integration, cross-platform development, and root-cause debugging.

### TI Embedded Linux development and integration

- Develop and maintain software for TI AM62-class Embedded Linux systems using Yocto images and the Arago toolchain.
- Compile and integrate Linux kernels and device trees for board-specific configuration and peripheral support.
- Work with DTS, DTSI, and DTB artifacts, boot configuration, Linux images/root filesystems, and serial-console diagnostics during system bring-up.
- Prepare and flash images, verify boot behavior, and use Linux logs and service diagnostics to trace failures through startup and runtime.
- Treat device trees, kernels, services, scripts, configuration, and test procedures as maintained parts of the embedded product rather than one-off setup tasks.

### APU/EPU battery, CAN, and watchdog integration

- Integrate and debug an APU/EPU embedded power subsystem spanning battery hardware, CAN-connected devices, a TI Embedded Linux controller, application software, and system services.
- Trace faults across batteries and power, wiring, CAN traffic, Linux boot/service logs, configuration, and application behavior rather than assuming a failure belongs to only hardware or software.
- Implemented an external-watchdog solution and supporting Linux service behavior to supervise the system and provide controlled recovery from failures.
- Use SocketCAN/PCAN, known-good nodes, bus-state and acknowledgement testing, logs, scopes, logic/protocol analyzers, and controlled substitutions during validation.
- The APU/EPU acronyms have not yet been expanded or reviewed for public disclosure; use them without expansion or describe the work generically as an embedded power subsystem.

### Smart-battery CAN interface and hardware review

- **Direct — September 15, 2026:** Develop a CAN-based interface board to configure and control smart batteries and communicate between the battery system and an external MCU.
- This professional work is separate from the NC State STM32G474/BQ79616 sensor adapter. Its relationship to the APU/EPU subsystem, exact MCU, board-design ownership, and completion status are not yet recorded.
- Diagnose CAN 2.0, CAN FD, and J1939-related systems across controllers, smart batteries, wiring harnesses, bitrate/address configuration, and communication diagnostics; this does not establish that the battery interface uses all three protocols.
- Read and interpret KiCad schematics and review PCB designs in KiCad, P-CAD, and Altium for troubleshooting, validation, firmware development, and integration. Review experience alone does not establish sole schematic or PCB-layout authorship.
- Interpret component/MCU datasheets, reference manuals, and electrical specifications to validate hardware implementation, determine interface requirements, and implement peripheral firmware.
- Isolate faults across PCBs, wiring, power, firmware, networks, sensors/interfaces, device configuration, test processes, engineering tooling, and application software.

### Docker and Windows/Linux compatibility

- Use Docker in the current development workflow.
- Improve shared code, build flows, and engineering tools so they behave consistently across Linux and Windows rather than depending on one developer's host environment.
- Identify and remove operating-system-specific assumptions while preserving behavior on the embedded Linux target.
- Do not claim a specific container architecture, CI system, build framework, or measured portability result until those details are confirmed.

### dsPIC33CK firmware and board bring-up

- Work with the dsPIC33CK family as a 16-bit digital signal controller rather than describing it as a generic microcontroller.
- Bring up the firmware toolchain and device packs, then develop and debug board peripherals and communication interfaces one subsystem at a time.
- Keep the dsPIC33CK separate from the PIC32/FreeRTOS and TMS320 DSP internship architecture unless a future source confirms that they belong to the same product.

### CAN, interfaces, and board-level debugging

- Diagnose Classical CAN (CAN 2.0) and CAN FD behavior with SocketCAN, PCAN hardware, known-good nodes, bit-timing analysis, acknowledgement-state testing, DBC interpretation, signal mapping, and frame validation.
- Work across I2C, SPI, UART/RS232, ADC, GPIO, timers, PWM, and debug interfaces during component-level and board-level integration.
- Bring up hardware one interface at a time using logs, register reads, JTAG, oscilloscopes, logic/protocol analyzers, serial diagnostics, schematics, and datasheets.
- Use controlled substitutions and known-good hardware to separate firmware, timing, configuration, wiring, physical-layer, and target-device faults.
- FDCAN clock correction and MCU-migration work should remain out of the public résumé until source support and disclosure approval are confirmed.

### Power-converter monitoring card: data-driven filter selection and ADC scaling

- This work was completed during the full-time Embedded Firmware Engineer role, not during either internship.
- Parsed captured CAN output in MATLAB, applied several candidate filtering functions to the same telemetry, and used the comparisons to determine and check per-channel scaling factors.
- Evaluated the filter characteristics that mattered for the product: reading variation under steady input and the time required to reflect genuine, large electrical changes.
- Selected rolling-average and exponential moving average (EMA) approaches from the comparison.
- Implemented the rolling average in embedded C by storing the last `N` samples, maintaining a rolling sum, replacing the oldest sample with the newest, and producing `sum / N`.
- Defined the EMA as a single-state alternative that retained the previous filtered value and moved it toward each new sample by a fraction of their difference, without an `N`-sample history buffer.
- Worked through the sensing and firmware architecture for a four-channel converter-monitoring card covering `VIN`, `IIN`, `VOUT`, and `IOUT` for slow telemetry rather than fast protection or control-loop feedback.
- Designed around a four-channel MCP3428 architecture in 16-bit mode at PGA = 1, with target ranges of 0–1000 V input, 0–30 A input current, 0–300 V output, and 0–100 A output current.
- Specified high-voltage-divider and current-sense front ends that mapped the electrical signals into nominal 0–2.000 V or 0–1.500 V ADC spans.
- Derived ideal initial code scales and used separate slope/intercept calibration logic for each channel rather than relying only on nominal divider and sensor values.
- Considered startup fill behavior, integer truncation/rounding, accumulator width, power-of-two shifts, fixed-divisor scaling, and independent filter state for each ADC channel.
- Distinguished DC averaging from RMS diagnostics, median glitch rejection, and nonlinear transforms rather than treating all operations as interchangeable outlier filters.
- The multiplexed MCP3428 channels are sequential, so voltage/current products are low-rate paired-sample power estimates—not simultaneous-sampling or switching-waveform measurements.
- Rolling-average implementation and selection of rolling-average and EMA approaches are confirmed. Other candidate functions, window size, EMA coefficient, sample cadence, quantitative results, and whether both selected approaches were deployed remain unconfirmed.

See [`adc-monitoring-card.md`](adc-monitoring-card.md) for the range/scale derivations, calibration and power math, cleaned rolling-average code, fixed-point considerations, and disclosure boundaries.

### VPX, IPMI, and embedded platform management

- Implemented and validated the VITA 46.11 Tier 2 management interface for a VPX power supply, using IPMI 2.0 over the I2C-based IPMB link for sensor, FRU/inventory, and event behavior.
- Characterized IPMI 2.0 behavior on embedded power hardware, including IPMB addressing, sensor enumeration/data, FRU inventory capability, and chassis-management services.
- Separated network reachability and transport availability from session establishment, authentication, protocol support, target addressing, and firmware compatibility.
- Used Linux command-line tools, service discovery, logs, and protocol-level reasoning to create a reproducible platform-management diagnostic workflow.
- Connor's August 2026 correction supports implementation of the VPX power supply's Tier 2 controller. It does not establish authorship of a general-purpose IPMI stack or unrelated chassis-management firmware.

### Engineering workflow, documentation, and teamwork

- Connect specifications, schematics, datasheets, implementation, Linux integration, board bring-up, protocol diagnosis, and validation instead of treating each technology as an isolated task.
- Communicate root cause, constraints, and recommended changes across firmware, electrical, and system-level work.
- Create handoff documentation for builds, flashing, validation, Git/GitLab, tests, services, and toolchains so resolved work remains reproducible.
- Participate in engineering standups and coordinate implementation/debugging with a geographically distributed firmware team.
- Communicate progress, technical constraints, test observations, and integration needs clearly enough for remote teammates to continue work without relying on hallway context.

## Production Programming and Engineering Tools — Exact Role Dates Unconfirmed

**Direct — September 15, 2026:** Connor supplied these details for AEGIS production and engineering work; the specific internship/current-role dates are not yet established.

### TI C2000 production serial flasher

- Customized Texas Instruments' C++-based `serial_flasher.exe` utility for the C2000 TMS320F28379D MCU.
- Removed unused device, CPU2, and dual-boot functionality and simplified the interface for AEGIS production use.
- Enabled non-firmware engineers to reliably program precompiled firmware images without unnecessary device-specific configuration choices.
- Authored both the simplified production flashing procedure and instructions for building source projects in Code Composer Studio and generating the firmware image for release to production.
- Document this C++ serial-flasher customization separately from the broader HEX-file CLI/Python/PIC32 update chain until their relationship is confirmed. The new account does not establish that they are the same tool, or that every older TMS320 reference identifies the TMS320F28379D.
- Removal of CPU2/dual-boot options from this utility does not imply removal of the separate product's golden-image recovery workflow.

### Repeatable diagnostic workflows and documentation

- Develop internal diagnostic and engineering tools, including embedded network-discovery and programming utilities, that turn complex or repetitive troubleshooting into repeatable workflows for engineers and production personnel.
- Create procedures for firmware programming, hardware troubleshooting, embedded development, test setup, device configuration, and system commissioning to improve repeatability and knowledge transfer.
- Tool names, discovery protocols, dates, and quantitative improvements are not yet recorded.

## Projects Recorded Across the 2024 and 2025 Internships

The recovered sources group the projects below across both AEGIS summers. The exact role titles and dates are known, but the specific summer for each newer power-control and updater deliverable should be confirmed before a future résumé assigns it to only 2025.

### TMS320 DSP power-conversion control

- Programmed the TMS320 DSP in bare-metal C using TI hardware-abstraction/peripheral libraries rather than an RTOS.
- Developed C firmware for custom programmable bidirectional buck-boost power supplies across transformer-coupled input and output stages.
- Controlled 24 physical PWM outputs arranged as twelve A/B pairs.
- Independently configured each A output's duty cycle, switching period/frequency, and phase shift relative to another signal.
- Configured each dependent B output to match or exactly invert its paired A waveform; B was not independently parameterized.
- Translated requested converter behavior into coordinated switching configuration and supported ADC/PWM validation in Code Composer Studio.
- A newer source also describes an ADC-read potentiometer that adjusted PWM6 duty cycle live during test.

### Connected PIC32/TMS320 firmware-update system

- Developed connected stages of one PIC32/TMS320 DSP product's firmware-update and boot-control workflow.
- The PIC32 ran FreeRTOS and coordinated communication and update behavior; the TMS320 DSP ran bare-metal control firmware using TI hardware libraries.
- Built a user-facing C++ command-line programmer that accepted a supplied firmware HEX image, making the flashing workflow easier to operate without rewriting the tool for each image.
- Used Python/TCP packet transport with chunking and checksum validation to move firmware into the product.
- Coordinated PIC32 and TMS320 communication for external SPI-flash staging, golden-image handling, UART DSP programming, verification, and boot control.
- The tools and processor interactions belonged to the same product but represented multiple connected stages, not one monolithic program.
- Supported FreeRTOS firmware, serial-interface validation, schematic review, soldering, and Code Composer Studio debugging.
- One archived version mentions repair of legacy `BDC` code; keep that wording internal until the acronym and exact contribution are clarified.

### CAN/J1939 and engineering handoff

- Worked with the FreeRTOS-based PIC32 across I2C, SPI, CAN/J1939, and UART orchestration while the bare-metal TMS320 DSP executed power-control firmware.
- DroneCAN is directly reported as professional protocol experience, but its exact role and product attribution remain unconfirmed. Keep it at skills level until that context is recorded.
- Standardized a GitLab/Git Extensions workflow around GitFlow-style branches and signed annotated release tags.
- A newer résumé reports an illustrated Git guide exceeding 80 pages plus a shorter handout and training slides. Confirm the exact page count and audience before using the metric publicly.
- Documented firmware delivery, CLI usage, test procedures, and toolchain setup for engineering handoff.

## Work Specifically Supported for the Computer Science Internship — May–August 2024

### Embedded Linux and remote-control interface

- Built a secured chroot environment and restricted SSH command-line interface on a resource-constrained TI Yocto/Arago system used with embedded power hardware.
- Developed Bash and Python commands that exposed approved inspection and control operations without providing an unrestricted shell.
- Worked with Linux filesystem/tool availability, secure login, deployment constraints, and remote hardware control as one integrated workflow.

### Communication, test hardware, and debugging

- Reverse-engineered RS232 command transactions from limited documentation and generated the checksums required for valid messages.
- Worked with RS232 and CAN communication between embedded devices and host/control systems.
- Reverse-engineered commands/checksums for programmable resistive loads and relay controllers, then helped construct the associated relay/load/power-supply test circuit; did not perform or run burn-in tests.
- Reviewed schematics and assisted with soldering, wiring, hardware setup, and cross-functional electrical/mechanical integration during validation.

## Best Resume Themes

- TI Embedded Linux, Yocto/Arago, kernel and device-tree compilation, systemd, Docker, and external watchdogs
- VITA 46.11 Tier 2 VPX power-supply management using IPMI over I2C-based IPMB
- dsPIC33CK 16-bit firmware and peripheral bring-up
- Cross-platform Windows/Linux code and tooling
- APU/EPU battery/CAN/Linux system integration and cross-layer debugging
- Embedded C/C++, Python, and Bash
- Data-driven ADC scaling and filter selection using MATLAB/CAN captures, with embedded-C rolling-average and EMA approaches
- TMS320 DSP bidirectional power-conversion control with twelve A/B PWM pairs
- PIC32/TMS320 firmware-update, recovery, programming, and boot coordination
- Classical CAN (CAN 2.0), CAN FD, J1939, DroneCAN, I2C/IPMB/IPMI, SPI, and UART/RS232 debugging
- Board bring-up, analyzers, scopes, JTAG, schematics, datasheets, validation, and documentation
- Engineering standups, remote firmware-team collaboration, and reproducible technical handoffs

## Details Requiring Confirmation or Disclosure Review

- What APU and EPU stand for, whether they describe one system or related systems, and whether the acronyms are public
- Exact battery-interface MCU, board-design ownership, relationship to the APU/EPU subsystem, owned CAN behavior, and watchdog failure/recovery behavior
- Exact Docker usage and the code/build/tooling changes made for Windows/Linux compatibility
- Meaning of `BDC` and the scope of the legacy-code repair
- Whether Git tooling and the 80+ page documentation metric may be disclosed
- Whether SocketCAN, PCAN, DBC/signal-mapping, and target-family names beyond those Connor directly approved are suitable for public disclosure
- ADC details beyond the confirmed rolling-average/EMA selection: other candidate functions, sample cadence, window/EMA parameters, calibration results, final deployment, and quantitative improvements
