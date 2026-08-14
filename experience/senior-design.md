# Senior Design — EV Active Sensor Adapter

The final senior-design architecture used an **STMicroelectronics microcontroller**, a **TI BQ-family battery-monitor/ADC**, and **external CAN transceivers**. It did **not** use the MSP430FR2355; that device belongs to ECE 306. Exact ST, BQ, and CAN-transceiver part-number suffixes were not recovered from the current Markdown, archived résumés, project repository, or user-message history, so public wording should remain at the family/function level unless Connor supplies them.

## System Purpose and Architecture

- Developed an EV active-sensor adapter around an STMicroelectronics MCU.
- Connected the controller, TI BQ-family battery measurement, CAN physical-layer interfaces, sensing and power hardware, custom-PCB interfaces, embedded control, and telemetry in one end-to-end architecture.
- Defined subsystem boundaries, data paths, power/control relationships, and electrical/firmware interfaces.
- Considered how component behavior, firmware state, sensing, communications, and presentation of telemetry affected the complete system rather than treating each board or peripheral independently.

### Short subsystem map

- **Control and firmware:** STMicroelectronics MCU executing sensing, system-state/control, and communications logic.
- **Battery measurement:** TI BQ-family ADC/battery-monitor device interfacing to the monitored battery signals.
- **Vehicle/network interface:** external CAN transceivers connecting controller-side CAN to the physical bus.
- **Board-level integration:** custom-PCB power and sensing interfaces tying together the controller, battery monitor, CAN physical layer, telemetry, and test points.

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

- Developed firmware around the STMicroelectronics controller and the defined sensing, battery-measurement, and CAN interfaces.
- Structured subsystem work so the MCU control, BQ measurement, CAN physical layer, and board-level sensing/power interfaces could be exercised independently before full-system integration.
- Used focused tests and diagnostic output to surface mismatched expectations between devices, firmware, and custom interfaces.
- Earlier project material contains an MSP430 interrupt-driven SPI prototype, but that was preliminary work and is not evidence that the final senior-design architecture used the MSP430. Do not put it in the final-system résumé summary without additional context.

## Validation and Custom-Hardware Integration

- Planned and performed subsystem-level validation before full-system/custom-PCB integration.
- Checked communication behavior, acquired measurements, controller state, CAN connectivity, timing, and telemetry at the interface level.
- Used test results to identify technical risk, refine interface definitions, and guide the next integration step.
- Do not claim a fully completed production-ready or vehicle-deployed system until the final prototype and validation status are confirmed.

## Documentation, Reviews, and Teamwork

- Coordinated interfaces and dependencies across team members and subsystem responsibilities.
- Communicated specifications, design choices, technical risks, progress, and validation results during design reviews.
- Used written requirements and interface definitions to keep firmware, hardware, sensing, and communication work aligned.
- Created documentation that made design rationale and remaining work visible to teammates rather than keeping decisions in individual notes.

## Best Resume Themes

- End-to-end embedded system architecture
- STMicroelectronics MCU control and firmware
- TI BQ-family battery measurement/ADC
- CAN interfaces and external transceivers
- BMS/power-management integration and component trade studies
- Sensing, power, communications, and telemetry subsystems
- Custom-PCB interfaces and subsystem validation
- Requirements, specifications, risks, test plans, design reviews, and team coordination

## Details Requiring Confirmation

- Exact team size and Connor's individually owned subsystems
- Final integrated-prototype status and highest completed level of validation
- Exact ST MCU, TI BQ device, and CAN-transceiver part numbers
- Exact final prototype state and which interfaces reached hardware bring-up
- Whether additional I2C, vehicle-interface, or safety-monitoring details are public
