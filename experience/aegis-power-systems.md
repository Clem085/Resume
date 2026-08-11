# AEGIS Power Systems Experience

This file is the detailed source for Connor's current engineering role and his 2024 and 2025 internships. It generalizes internal products, customer details, network data, register maps, and proprietary power-stage information.

## Attribution Boundaries

- **Embedded Firmware Engineer:** May 2026–Present
- **Embedded Systems Intern:** May–August 2025
- **Computer Science Intern:** May–August 2024
- The BMS research, component evaluation, and integration work belongs to the NC State senior-design project, not to any AEGIS role. Do not place BMS under AEGIS in future résumés or cover letters.
- Use exact task language for TI Embedded Linux work. Do not label it generically as “BSP work”; Connor's direct experience is with Yocto/Arago images and toolchains, kernel and device-tree compilation, boot/service integration, and board-level validation.

## Embedded Firmware Engineer — May 2026–Present

The current role is Linux-intensive and spans embedded software, system services, CAN-connected power hardware, board integration, cross-platform development, and root-cause debugging.

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

### Docker and Windows/Linux compatibility

- Use Docker in the current development workflow.
- Improve shared code, build flows, and engineering tools so they behave consistently across Linux and Windows rather than depending on one developer's host environment.
- Identify and remove operating-system-specific assumptions while preserving behavior on the embedded Linux target.
- Do not claim a specific container architecture, CI system, build framework, or measured portability result until those details are confirmed.

### CAN, interfaces, and board-level debugging

- Diagnose classical CAN and CAN FD behavior with SocketCAN, PCAN hardware, known-good nodes, bit-timing analysis, acknowledgement-state testing, DBC interpretation, signal mapping, and frame validation.
- Work across I2C, SPI, UART/RS232, ADC, GPIO, timers, PWM, and debug interfaces during component-level and board-level integration.
- Bring up hardware one interface at a time using logs, register reads, JTAG, oscilloscopes, logic/protocol analyzers, serial diagnostics, schematics, and datasheets.
- Use controlled substitutions and known-good hardware to separate firmware, timing, configuration, wiring, physical-layer, and target-device faults.
- FDCAN clock correction and MCU-migration work should remain out of the public résumé until source support and disclosure approval are confirmed.

### IPMI and embedded platform management

- Characterized IPMI 2.0 behavior on embedded power hardware, including IPMB addressing, sensor enumeration/data, FRU inventory capability, and chassis-management services.
- Separated network reachability and transport availability from session establishment, authentication, protocol support, target addressing, and firmware compatibility.
- Used Linux command-line tools, service discovery, logs, and protocol-level reasoning to create a reproducible platform-management diagnostic workflow.
- Evidence supports investigation and validation of IPMI/IPMB/sensor/FRU capabilities; it does not support claiming authorship of the underlying IPMI stack.

### Engineering workflow, documentation, and teamwork

- Connect specifications, schematics, datasheets, implementation, Linux integration, board bring-up, protocol diagnosis, and validation instead of treating each technology as an isolated task.
- Communicate root cause, constraints, and recommended changes across firmware, electrical, and system-level work.
- Create handoff documentation for builds, flashing, validation, Git/GitLab, tests, services, and toolchains so resolved work remains reproducible.

## Projects Recorded Across the 2024 and 2025 Internships

The recovered sources group the projects below across both AEGIS summers. The exact role titles and dates are known, but the specific summer for each newer power-control and updater deliverable should be confirmed before a future résumé assigns it to only 2025.

### TMS320 DSP power-conversion control

- Developed C firmware for custom programmable bidirectional buck-boost power supplies across transformer-coupled input and output stages.
- Controlled 24 physical PWM outputs arranged as twelve A/B pairs.
- Independently configured each A output's duty cycle, switching period/frequency, and phase shift relative to another signal.
- Configured each dependent B output to match or exactly invert its paired A waveform; B was not independently parameterized.
- Translated requested converter behavior into coordinated switching configuration and supported ADC/PWM validation in Code Composer Studio.
- A newer source also describes an ADC-read potentiometer that adjusted PWM6 duty cycle live during test.

### Connected PIC32/TMS320 firmware-update system

- Developed connected stages of one PIC32/TMS320 DSP product's firmware-update and boot-control workflow.
- Built a user-facing C++ command-line programmer that accepted a supplied firmware HEX image, making the flashing workflow easier to operate without rewriting the tool for each image.
- Used Python/TCP packet transport with chunking and checksum validation to move firmware into the product.
- Coordinated PIC32 and TMS320 communication for external SPI-flash staging, golden-image handling, UART DSP programming, verification, and boot control.
- The tools and processor interactions belonged to the same product but represented multiple connected stages, not one monolithic program.
- Supported FreeRTOS firmware, serial-interface validation, schematic review, soldering, and Code Composer Studio debugging.
- One archived version mentions repair of legacy `BDC` code; keep that wording internal until the acronym and exact contribution are clarified.

### CAN/J1939 and engineering handoff

- Worked with the PIC32 across I2C, SPI, CAN/J1939, and UART orchestration while the TMS320 DSP executed power-control firmware.
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
- Helped construct a relay, resistive-load, and power-supply circuit for burn-in monitoring and test support.
- Reviewed schematics and assisted with soldering, wiring, hardware setup, and cross-functional electrical/mechanical integration during validation.

## Best Resume Themes

- TI Embedded Linux, Yocto/Arago, kernel and device-tree compilation, systemd, Docker, and external watchdogs
- Cross-platform Windows/Linux code and tooling
- APU/EPU battery/CAN/Linux system integration and cross-layer debugging
- Embedded C/C++, Python, and Bash
- TMS320 DSP bidirectional power-conversion control with twelve A/B PWM pairs
- PIC32/TMS320 firmware-update, recovery, programming, and boot coordination
- CAN/CAN FD/J1939, I2C, SPI, UART/RS232, IPMI, and IPMB debugging
- Board bring-up, analyzers, scopes, JTAG, schematics, datasheets, validation, and documentation

## Details Requiring Confirmation or Disclosure Review

- What APU and EPU stand for, whether they describe one system or related systems, and whether the acronyms are public
- Exact battery-interface work, owned CAN behavior, watchdog failure/recovery behavior, and public-safe product wording
- Exact Docker usage and the code/build/tooling changes made for Windows/Linux compatibility
- Meaning of `BDC` and the scope of the legacy-code repair
- Whether CAN/J1939, PIC32/TMS320 names, Git tooling, golden-image behavior, and the 80+ page documentation metric may be disclosed
- Whether SocketCAN, PCAN, DBC/signal-mapping, target-family names, the 24-output topology, transformer coupling, and IPMI/IPMB behavior are approved for public disclosure
