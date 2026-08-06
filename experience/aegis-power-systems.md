# AEGIS Power Systems Experience

This file is the detailed source for professional AEGIS work. It intentionally separates the current engineering role from the 2024 and 2025 internships and generalizes internal products, customer details, network data, register maps, and proprietary power-stage information.

## Current Embedded Firmware Role

The official title and start date still need confirmation. The work itself spans embedded firmware, power electronics, component integration, communication buses, Embedded Linux, test automation, and system-level debugging.

### Programmable bidirectional power conversion

- Developed firmware control for custom programmable power supplies built around variable bidirectional buck-boost converter stages; PWM is the switching-control mechanism inside the power-conversion architecture, not the project by itself.
- Coordinated 24 independently configurable PWM channels across transformer-coupled input and output stages rather than treating each PWM output as an unrelated signal.
- Translated requested input/output voltage behavior into coordinated switching configuration for the associated converter channels.
- Managed timing, duty-cycle relationships, paired-channel behavior, synchronization, ADC feedback, and safe-operating constraints through centralized configuration logic.
- Built the control interface so converter behavior could be changed without rewriting low-level peripheral code for each power channel.
- Verified that requested operating changes were translated to the intended input-side and output-side control settings.

### BMS, monitoring, protection, and component integration

- Evaluated multiple battery-management, cell-monitoring, protection, interface, and supporting ICs rather than reducing the work to a single part search.
- Compared voltage and cell-count support, sensing architecture, balancing, protection behavior, host protocol, package/footprint, tool support, reference designs, sourcing risk, availability, and integration constraints.
- Reviewed datasheets, schematics, reference designs, evaluation hardware, and existing system interfaces to identify electrical, protocol, pinout, and software compatibility issues before integration.
- Distinguished the stages of the workflow: candidate research, selection/recommendation, bench validation, peripheral bring-up, system integration, and fault diagnosis.
- Converted component trade studies into firmware requirements, hardware-interface decisions, initialization plans, bring-up sequences, and focused validation tests.
- Used breadboards and breakout/evaluation hardware to validate one peripheral or interface at a time before committing the design to a custom PCB.

### I2C implementation and root-cause debugging

- Debugged acknowledgement failures, device and register addressing, transaction format, timing, pull-up networks, open-drain pin configuration, voltage compatibility, bus state, and shared-bus behavior.
- Checked firmware register transactions against device register maps and datasheet timing requirements instead of treating a missing acknowledgement as a purely software problem.
- Correlated logic-analyzer/protocol-decoder captures with schematics, firmware configuration, and known-good hardware.
- Wrote focused test routines that isolated one device, peripheral, or register transaction at a time.
- Used breakout boards, single-device tests, controlled hardware substitutions, and direct measurements to separate firmware, wiring, configuration, physical-layer, and device faults.
- Considered whether development boards already supplied pull-ups and whether logic levels and electrical configuration were compatible across the complete signal path.

### CAN and CAN FD validation

- Diagnosed classical CAN and CAN FD behavior with SocketCAN, PCAN hardware, known-good nodes, bit-timing analysis, acknowledgement-state testing, DBC interpretation, signal mapping, and frame validation.
- Compared working and failing nodes/adapters to isolate configuration, wiring, physical-layer, timing, and target-device faults.
- Checked bitrate and timing assumptions, frame content, signal packing, and acknowledgement state instead of stopping at successful frame transmission.
- Used controlled substitutions among adapters, development hardware, and target devices to narrow failures to a specific layer of the system.
- FDCAN clock correction and MCU-migration work should remain out of the public résumé until source support and disclosure approval are confirmed.

### Other firmware and board bring-up

- Worked across SPI, UART, RS232, ADC, GPIO, timers, PWM, and debug interfaces during component-level and board-level integration.
- Brought up hardware one peripheral at a time, using logs, register reads, JTAG, oscilloscopes, logic/protocol analyzers, serial diagnostics, schematics, and datasheets.
- Used known-good hardware, breadboards, breakout boards, and controlled substitutions to identify whether failures originated in firmware, wiring, configuration, timing, or the target IC.
- Documented resolved faults and repeatable bring-up procedures so later testing did not depend on a one-off debugging session.

### IPMI and embedded platform management

- Characterized IPMI 2.0 behavior on embedded power-management hardware, including IPMB addressing, sensor enumeration/data, FRU inventory capability, and chassis-management services.
- Separated network reachability and transport availability from session establishment, authentication, protocol support, target addressing, and firmware compatibility.
- Investigated network-accessible management services as possible embedded platform-management interfaces rather than presenting the work as generic network scanning.
- Used Linux command-line tools, service discovery, logs, and protocol-level reasoning to create a reproducible platform-management diagnostic workflow.
- Evidence supports investigation and validation of IPMI/IPMB/sensor/FRU capabilities; it does not support claiming authorship of the underlying IPMI stack.

### Embedded Linux, BSP work, and system services

- Supported TI AM62-class Embedded Linux systems using Yocto/Arago images, board-specific device trees, boot configuration, and peripheral integration.
- Worked with device-tree source and compiled artifacts to maintain or restore board configuration for evaluation and derivative hardware.
- Created systemd services and external-watchdog services, then used boot and service diagnostics to validate startup order, supervision, failure handling, and restart behavior.
- Prepared and flashed Linux images/root filesystems, checked boot configuration, and used serial/service diagnostics during board bring-up.
- Developed Python and Bash tools for hardware monitoring, firmware flashing, automated validation, repeatable bring-up, and field diagnostics.
- Treated scripts and services as maintained system components with defined behavior, logging, reproducible setup, and engineering documentation.

### Engineering workflow, documentation, and teamwork

- Connected component research, firmware implementation, board bring-up, protocol diagnosis, and validation rather than reporting each technology as an isolated task.
- Worked from specifications, schematics, datasheets, reference designs, logs, measurements, and controlled tests when communicating root cause and recommended changes.
- Created handoff documentation for build, flashing, validation, Git/GitLab, test, service, and toolchain workflows.
- Communicated findings and integration constraints to firmware, electrical, and system engineers while coordinating dependencies across hardware and software.

## AEGIS Internships — May–August 2024 and May–August 2025

Archived 2024 résumés identify the official role as **Computer Science Intern**. The official 2025 title is not preserved in the archive, so the public résumé uses the neutral title **Intern** for the combined entry.

### Embedded Linux and remote-control interface

- Built a secured chroot environment and restricted SSH command-line interface on a stripped TI Yocto/Arago system used with embedded power hardware.
- Developed Bash and Python commands that exposed approved inspection and control operations without providing an unrestricted shell.
- Worked with Linux, filesystem/tool availability, secure login, deployment constraints, and remote hardware control as one integrated workflow.

### Firmware update and embedded debugging

- Created packetized Python/Bash firmware-flashing utilities with checksum validation and SPI reflashing support for TI TMS320 targets.
- Supported FreeRTOS firmware, ADC/PWM testing, serial-interface validation, schematic review, and Code Composer Studio debugging.
- Turned manual update and diagnostic steps into documented, repeatable engineering workflows; the measurable time/reliability effect still needs confirmation.

### Communication reverse engineering and validation

- Reverse-engineered RS232 command transactions from limited documentation and generated the checksums required for valid messages.
- Worked with RS232 and CAN communication between embedded devices and host/control systems.
- Compared documented behavior with observed responses and hardware state when validating commands.

### Test hardware and engineering handoff

- Helped construct a relay, resistive-load, and power-supply circuit for burn-in monitoring and test support.
- Reviewed schematics and assisted with soldering, wiring, and hardware setup during validation.
- Documented Git workflows, firmware delivery, test procedures, and toolchain setup for engineering handoff.

## Best Resume Themes

- Embedded C/C++, Python, and Bash across firmware and Linux
- Programmable bidirectional buck-boost power conversion
- BMS and power-management IC evaluation and integration
- I2C, CAN/CAN FD, SPI, UART, RS232, IPMI, and IPMB debugging
- TI AM62 Embedded Linux, Yocto/Arago, device trees, systemd, and watchdogs
- Board bring-up, analyzers, scopes, JTAG, schematics, and datasheets
- Firmware flashing, automated validation, field diagnostics, and documentation

## Details Requiring Confirmation or Disclosure Review

- Official title and start date for the current role
- Official title for the 2025 internship and which deliverables belong to each internship year
- Exact number/types of BMS devices that were evaluated, validated, or fully integrated
- Whether SocketCAN, PCAN, DBC/signal-mapping, and target-family names may be disclosed
- Whether the 24-channel count, transformer-coupled topology, paired-channel behavior, and safe-operating details are public
- Which IPMI/IPMB/FRU/sensor capabilities were investigated, validated, or incorporated into deliverable firmware
