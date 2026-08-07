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

Archived 2024 résumés identify the official role as **Computer Science Intern**. Newer drafts sometimes combine both summers under **Embedded Systems Firmware Intern** and sometimes under **Computer Science Intern**; the official 2025 title is not preserved. Until the two titles are confirmed, a public combined entry should use the neutral title **Intern**.

### TMS320 power-control firmware — archive-derived, topology to confirm

- A newer résumé source describes C firmware on a TI TMS320 DSP that controlled twelve PWM modules/channels with per-channel frequency, duty cycle, and phase settings.
- The same source describes A/B output behavior that could be mirrored or inverted and an ADC-read potentiometer that adjusted PWM6 duty cycle live during test.
- This may describe twelve ePWM modules producing 24 physical A/B outputs, but it cannot yet be merged with the directly supplied claim of 24 independently configurable channels. The pairing, independence, product generation, and whether this was internship or later work must be confirmed.
- The valuable résumé-level story is coordinated switching control inside a programmable power-conversion system; the numerical channel topology should remain unpublished until reconciled.

### Embedded Linux and remote-control interface

- Built a secured chroot environment and restricted SSH command-line interface on a stripped TI Yocto/Arago system used with embedded power hardware.
- Developed Bash and Python commands that exposed approved inspection and control operations without providing an unrestricted shell.
- Worked with Linux, filesystem/tool availability, secure login, deployment constraints, and remote hardware control as one integrated workflow.

### Firmware update and embedded debugging

- Created packetized Python/Bash firmware-flashing utilities with checksum validation and SPI reflashing support for TI TMS320 targets.
- Supported FreeRTOS firmware, ADC/PWM testing, serial-interface validation, schematic review, and Code Composer Studio debugging.
- Turned manual update and diagnostic steps into documented, repeatable engineering workflows; the measurable time/reliability effect still needs confirmation.

#### Recovered two-processor update architecture — confirm before publication

- A newer source describes a PIC32 and TMS320 division of responsibility: the PIC32 coordinated I2C, SPI, CAN/J1939, UART, and update transport while the TMS320 executed PWM control.
- It separately names a C++ serial flasher for the DSP and a Python TCP/IP sender for the PIC32, using chunking and checksum validation during transfer.
- The draft describes the PIC32 storing received firmware in external SPI flash, retaining a golden image, reflashing the DSP over UART, verifying the image, and committing it to DSP on-chip flash.
- Another version summarizes file generation, packetized/checksummed transfer, and SPI reflashing without the same topology. These may be different tools or stages; do not collapse them into one implementation until the path is confirmed.
- One version says legacy `BDC` code was repaired. The acronym, ownership, and actual change are not established well enough for public use.

### Communication reverse engineering and validation

- Reverse-engineered RS232 command transactions from limited documentation and generated the checksums required for valid messages.
- Worked with RS232 and CAN communication between embedded devices and host/control systems.
- Newer sources repeatedly name CAN/J1939 in the PIC32/TMS320 system; preserve J1939 as an archive-supported lead until the exact deliverable and summer are confirmed.
- Compared documented behavior with observed responses and hardware state when validating commands.

### Test hardware and engineering handoff

- Helped construct a relay, resistive-load, and power-supply circuit for burn-in monitoring and test support.
- Reviewed schematics and assisted with soldering, wiring, and hardware setup during validation.
- Collaborated with electrical and mechanical engineers during hardware/firmware integration; archived cover letters also describe schematic review of a custom PCB controlling a Linux-based power supply.
- Standardized a GitLab/Git Extensions workflow around GitFlow-style branches and signed annotated release tags.
- A newer résumé reports an illustrated Git guide exceeding 80 pages plus a shorter handout and training slides. Confirm the exact page count and audience before using the metric publicly.
- Documented firmware delivery, test procedures, CLI use, and toolchain setup for engineering handoff.

### Lower-confidence internship leads

The following appear primarily in tailored cover letters. They are retained for interview follow-up, not treated as established accomplishments without code, documentation, or Connor's confirmation:

- TCP client/server implementation and Python/Bash automation used to manage embedded systems
- C/C++ unit testing and timing-conscious use of print/LED diagnostics
- The exact boundary between FreeRTOS application changes, test code, legacy-code repair, and production firmware
- Customer/market language describing military or aerospace power supplies, which may also be inappropriate to disclose

## Best Resume Themes

- Embedded C/C++, Python, and Bash across firmware and Linux
- Programmable bidirectional buck-boost power conversion
- BMS and power-management IC evaluation and integration
- I2C, CAN/CAN FD, CAN/J1939, SPI, UART, RS232, IPMI, and IPMB debugging
- PIC32/TMS320 distributed control and firmware-update architecture, once topology is confirmed
- TI AM62 Embedded Linux, Yocto/Arago, device trees, systemd, and watchdogs
- Board bring-up, analyzers, scopes, JTAG, schematics, and datasheets
- Firmware flashing, automated validation, field diagnostics, and documentation

## Details Requiring Confirmation or Disclosure Review

- Official title and start date for the current role
- Official title for the 2025 internship and which deliverables belong to each internship year
- Whether the archived twelve ePWM modules/channels produced 24 A/B outputs, and which outputs were independently controllable, mirrored, or inverted
- Whether the C++/UART DSP flasher, Python/TCP PIC32 sender, SPI-flash storage, golden image, and earlier Python/Bash SPI-reflash summary are one path or several tools
- Meaning of `BDC` and the scope of any legacy-code repair
- Whether CAN/J1939, PIC32/TMS320 names, Git tooling, and the 80+ page documentation metric may be disclosed
- Exact number/types of BMS devices that were evaluated, validated, or fully integrated
- Whether SocketCAN, PCAN, DBC/signal-mapping, and target-family names may be disclosed
- Whether the 24-channel count, transformer-coupled topology, paired-channel behavior, and safe-operating details are public
- Which IPMI/IPMB/FRU/sensor capabilities were investigated, validated, or incorporated into deliverable firmware
