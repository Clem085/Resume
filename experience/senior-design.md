# Senior Design — EV Active Sensor Adapter

The project is best presented as a cross-disciplinary system-design and integration effort around an MSP430FR2355, sensing, BMS/power-management hardware, custom interfaces, firmware, communication, and telemetry. The detailed source supports system architecture and prototype work; the final level of integrated validation still needs confirmation.

## System Purpose and Architecture

- Developed an EV active-sensor adapter concept around the MSP430FR2355.
- Connected the microcontroller, sensing paths, BMS/power-management hardware, custom-PCB interfaces, embedded control, communication links, and telemetry in one end-to-end architecture.
- Defined subsystem boundaries, data paths, power/control relationships, and electrical/firmware interfaces.
- Considered how component behavior, firmware state, sensing, communications, and presentation of telemetry affected the complete system rather than treating each board or peripheral independently.

## Requirements, Interfaces, and Technical Risk

- Developed system requirements and interface specifications spanning sensing, power management, BMS behavior, embedded control, communications, and custom hardware.
- Translated operating constraints and component requirements into hardware interfaces, firmware behavior, register/data expectations, and validation criteria.
- Identified integration risks involving electrical compatibility, protocol behavior, component availability, custom-board interfaces, and subsystem dependencies.
- Maintained architecture diagrams, interface definitions, design decisions, risk tracking, progress reports, and test-planning material.

## BMS and Component Trade Studies

- Evaluated BMS and supporting components against voltage range, sensing, protection, communication, packaging, footprint, and sourcing requirements.
- Reviewed datasheets, reference designs, interface requirements, and custom-board constraints before committing hardware and firmware interfaces.
- Documented candidate tradeoffs, selection rationale, limitations, and follow-on validation needs.
- Connected part selection to the downstream work required for schematic integration, firmware initialization, communication, test access, and PCB implementation.

## Firmware and Peripheral Prototyping

- Prototyped interrupt-driven SPI master/slave register transactions on the MSP430FR2355.
- Worked with ADC acquisition, UART diagnostics, timers, GPIO, sensing paths, and LCD telemetry.
- Structured peripheral work so interfaces could be exercised independently before attempting full-system integration.
- Used diagnostic output and focused tests to surface mismatched expectations between devices, firmware, and custom interfaces.

## Validation and Custom-Hardware Integration

- Planned and performed subsystem-level validation before full-system/custom-PCB integration.
- Checked communication behavior, acquired data, GPIO state, timing, and displayed telemetry at the interface level.
- Used test results to identify technical risk, refine interface definitions, and guide the next integration step.
- Do not claim a fully completed production-ready or vehicle-deployed system until the final prototype and validation status are confirmed.

## Documentation, Reviews, and Teamwork

- Coordinated interfaces and dependencies across team members and subsystem responsibilities.
- Communicated specifications, design choices, technical risks, progress, and validation results during design reviews.
- Used written requirements and interface definitions to keep firmware, hardware, sensing, and communication work aligned.
- Created documentation that made design rationale and remaining work visible to teammates rather than keeping decisions in individual notes.

## Best Resume Themes

- End-to-end embedded system architecture
- MSP430FR2355 firmware and interrupt-driven SPI
- BMS/power-management integration and component trade studies
- ADC, UART, timers, GPIO, sensing, and LCD telemetry
- Custom-PCB interfaces and subsystem validation
- Requirements, specifications, risks, test plans, design reviews, and team coordination

## Details Requiring Confirmation

- Exact team size and Connor's individually owned subsystems
- Final integrated-prototype status and highest completed level of validation
- Exact BMS/power-management devices and which candidates reached hardware bring-up
- Whether any CAN, I2C, vehicle-interface, or safety-monitoring details are part of this project and public
