# Rev10 Source Brief — September 15, 2026

Connor directly supplied the following experience for this revision:

- Customized TI's C++ `serial_flasher.exe` for C2000 TMS320F28379D, removing unused device, CPU2, and dual-boot functionality for AEGIS production.
- Simplified precompiled-image programming for non-firmware engineers; documented flashing plus CCS source builds and release-image generation.
- Troubleshoot PCBs, wiring, power, firmware, networks, sensors/interfaces, configuration, test processes, engineering tools, and application software.
- Develop/debug STM32, Microchip PIC32/dsPIC, and TI C2000 firmware, including bring-up, peripheral configuration, programming, verification, and integration.
- Interpret KiCad schematics; review PCBs in KiCad, P-CAD, and Altium; use datasheets, reference manuals, and electrical specifications to validate hardware and implement peripherals.
- Develop a CAN interface board for smart-battery configuration/control and communication with an external MCU.
- Develop/troubleshoot CAN 2.0, CAN FD, and J1939-related controllers, batteries, harnesses, bitrate/address settings, and communications.
- Develop AEGIS Power Systems ATP database automation with SQL, VBA, Access, and Excel: parsing, validation, historical retrieval, and database entry.
- Develop TEAM Industries VBA inspection-data parsing and automatic tolerance verification.
- Create and maintain a 17,000+ entry tooling where-used list for TEAM Industries' entire plant using custom Excel lookup formulas and data-validation rules; connect tools with part numbers, operation numbers, storage locations, and vendors.
- Build repeatable internal diagnostic, network-discovery, and programming tools for engineers and production personnel.
- Write firmware-programming, troubleshooting, development, test-setup, configuration, and commissioning procedures.

## Reconciliation

The C++ utility is recorded separately from the existing C++ updater. TEAM tolerance automation already existed and now includes parsing details. The ATP database is confirmed as AEGIS work (corrected September 19, 2026); it was completed during the summer 2024 Computer Science Internship (latest correction, superseding the earlier 2025 assignment). AEGIS battery-interface work is separate from senior design; older blanket exclusions of professional battery work were corrected. The serial flasher is confirmed as summer 2025; other production-tool dates remain unconfirmed.

Connor has used PlatformIO, STM32Cube, MPLAB, and Code Composer Studio. Rev10 omits a general IDE list because it does not strengthen this version; CCS build/image documentation remains in the supporting AEGIS notes; the current résumé retains Connor's preferred concise flasher bullet. STM32 experience is shown through the STM32G474 senior-design firmware rather than only as a skills keyword.

## Visual Reference Boundary

The blue 2024 template is for visual layout and spacing only. Keep Rev10's pre-styling content, tone, and plain wording; do not use the old template as a content reference. Preserve separately confirmed factual updates, including AEGIS ATP attribution and TEAM tooling-list details. Keep the smart-battery interface-board bullet out of the résumé.

## Final Chat Corrections — September 19, 2026

- ATP belongs to the summer 2024 AEGIS internship; TI serial-flasher work remains summer 2025. ATP is spelled out as Acceptance Test Procedure (ATP) and appears once under AEGIS Experience.
- Preserve the existing one-button serial-flasher wording at Connor's request; adding procedure details was a suggestion, not an accepted replacement.
- Senior-design ownership includes voltage/temperature sensing, LEDs, state-machine logic, and error logging. Mention CAN integration generally; Connor did not author CAN middleware or messaging. See [senior design](../experience/senior-design.md).
- Maze comparisons used iteration counts. The current résumé names correctness and iteration counts instead of memory-use/runtime claims. See [project evidence](../experience/personal-projects.md).
- PCB tools were used for review and firmware integration, not established design/layout ownership. No PLC experience; professional PWM was for buck/boost conversion, academic motor PWM for small 3.3 V motors. SQL Server/MySQL, C#, and Creo remain unsupported.
- Current skills use “Embedded Platforms” and “hardware validation against datasheet specifications”; microarchitecture wording uses “processor subsystems.”

## Reference-Only Summer 2024 Correction

The latest explicit clarification and the July 31, 2024 internship presentation establish SCB301 Linux CLI work, independent KiCad reference-design review (Grant authored the revision), ATP Access/VBA/Excel automation, and collaborative programmable-load/relay burn-in fixture proof-of-concept work as summer 2024. See [AEGIS](../experience/aegis-power-systems.md) for technical detail, source distinctions, and outcome boundaries. The 2025 serial flasher and established full-time work retain their dates. This update changes reference Markdown only; it does not update or validate résumé TeX/PDF wording.
