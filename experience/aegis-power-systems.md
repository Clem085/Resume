# AEGIS Power Systems Experience

## Embedded Firmware Engineer — Current

### Programmable power conversion

- Developed firmware control for custom bidirectional buck-boost power supplies.
- Coordinated 24 independently configurable PWM channels across transformer-coupled input and output stages.
- Built a centralized configuration framework that translated requested input and output voltages into coordinated PWM timing, duty cycles, and switching behavior.
- Integrated ADC feedback and safe-operating constraints across paired converter channels.

### BMS and component integration

- Evaluated battery-management, monitoring, interface, and support ICs.
- Compared electrical limits, host protocols, protection features, footprints, tool support, reference designs, and sourcing risk.
- Converted datasheet and component-research findings into firmware and hardware-integration plans.

### Communication and hardware debugging

- Debugged I2C, CAN, CAN FD, SPI, UART, and RS232 communication.
- Correlated firmware register transactions and analyzer captures with schematics, timing requirements, bus configuration, and known-good hardware.
- Created focused test routines for peripheral-by-peripheral bring-up.
- Used datasheets, logs, register reads, JTAG, oscilloscopes, logic analyzers, breadboards, breakout boards, and controlled hardware substitutions.

### Embedded platform management and Linux

- Characterized IPMI 2.0 and chassis-management services on embedded power hardware.
- Validated IPMB addressing, sensor access, and FRU access.
- Distinguished transport, session, authentication, protocol, and firmware-compatibility failures.
- Created external-watchdog and systemd services.
- Supported TI AM62-class Embedded Linux systems, device trees, and Yocto/Arago builds.
- Created Python and Bash tooling for monitoring, flashing, automated validation, and field diagnostics.

## Embedded Systems Intern — May–August 2024 and May–August 2025

- Built a secured chroot environment and restricted SSH command-line interface on a stripped TI Yocto/Arago system.
- Developed custom Bash and Python commands to inspect and control embedded power hardware.
- Created packetized firmware-flashing utilities with checksum validation and SPI reflashing support for TI TMS320 targets.
- Reverse-engineered RS232 command transactions from limited vendor documentation and generated valid checksums.
- Helped construct a relay, resistive-load, and power-supply circuit for burn-in monitoring.
- Supported FreeRTOS firmware, ADC/PWM testing, serial-interface validation, schematic review, and Code Composer Studio debugging.
- Documented Git workflows, firmware delivery, testing, and toolchain procedures for engineering handoffs.

## Resume Themes

- End-to-end embedded engineering
- Power-conversion firmware
- Embedded Linux services
- BMS and component evaluation
- Protocol debugging
- Board bring-up and validation
- Reproducible engineering documentation

