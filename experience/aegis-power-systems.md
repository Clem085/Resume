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

## Production Programming and Engineering Tools

**Direct — September 15, 2026:** Connor supplied these details for AEGIS production and engineering work; the serial flasher is now confirmed as summer 2025; dates for other tools remain unconfirmed.

### TI C2000 production serial flasher
Completed during the summer 2025 Embedded Systems Internship (confirmed September 19, 2026).
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

## Embedded Systems Internship — Summer 2025: Converter Control

**Current résumé update — September 20, 2026:** The active bullet is explicitly grouped under the 2025 internship. This resolves the previously unassigned summer for converter control.

### TMS320 DSP power-conversion control

- Programmed the TMS320 DSP in bare-metal C using TI hardware-abstraction/peripheral libraries rather than an RTOS.
- Developed C firmware for custom programmable bidirectional buck-boost power supplies across transformer-coupled input and output stages.
- Controlled 24 physical PWM outputs arranged as twelve A/B pairs.
- Independently configured each A output's duty cycle, switching period/frequency, and phase shift relative to another signal.
- Configured each dependent B output to match or exactly invert its paired A waveform; B was not independently parameterized.
- Translated requested converter behavior into coordinated switching configuration and supported ADC/PWM validation in Code Composer Studio.
- A newer source also describes an ADC-read potentiometer that adjusted PWM6 duty cycle live during test.

## Other Internship Projects — Exact Summer Unresolved

The recovered sources grouped the projects below across both internships, but did not establish each exact summer. They are not supported as 2024 work by the reviewed presentation or latest clarification. Keep them unassigned pending confirmation rather than moving them into 2024 or guessing 2025. Any separately established 2025 dates remain unchanged.

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

## Computer Science Internship — May–August 2024

### Sources and chronology corrections

- **Presentation corroboration:** `FINAL-AegisInternship-ConnorSavugot.pptx`, title slide dated July 31, 2024; reviewed from `/home/connor/Downloads/Internships/2024_Summer/Aeigis/FINAL-AegisInternship-ConnorSavugot.pptx`. Slides 4–6 cover SCB301, 8–10 ATP, and 13–15 resistive loads/test hardware.
- **Direct clarification:** Connor's latest Summer 2024 reference-update brief adds the board-review ownership details and automated burn-in fixture concept below. These additions are distinguished from presentation evidence.
- **Superseded attribution:** Earlier records first assigned ATP to TEAM Industries and then to AEGIS summer 2025. The presentation and latest explicit correction establish AEGIS summer 2024. The correct role title is Computer Science Intern, not the 2025 title Embedded Systems Intern.
- Only projects supported by this presentation or the explicit 2024 clarification belong in this section. Similar technologies do not move later work into 2024. The TI C++ serial flasher remains summer 2025; full-time work remains May 2026–present.

### 1. SCB301 embedded Linux command-line environment

- Designed and implemented a custom command-line interface for managing the SCB301 embedded device.
- Worked in a stripped TI embedded Linux environment based on Yocto/Arago; researched the Arago toolchain and opkg/package-management environment under limited tooling constraints.
- Created a chroot environment and restricted user login with limited permissions; the earlier source describes SSH access. Do not treat chroot alone as proof of a hardened security boundary.
- Implemented specialized AEGIS commands in Bash and Python to view/modify system or product data and control approved operations.
- Supported firmware updates to connected devices; slide 6 records uploading firmware to other devices.
- Debugged and tested the embedded Linux environment (direct clarification). Slide 6 also lists further debugging/testing and additional commands as next steps; do not imply all planned features were completed.
- Reviewed the SCB301 schematic as part of this work. The CLI/software contribution does not establish design ownership of the hardware platform.

### 2. SCB301 KiCad schematic and board-revision review

- Presentation slides 2 and 4 establish schematic review; the following specific scope and ownership come from Connor's latest clarification.
- Grant created a new AEGIS board revision derived from a TI evaluation/reference-board design, simplifying it for the product and removing unnecessary evaluation-board features such as HDMI support.
- Connor performed an independent review of the modified KiCad schematic against the original TI evaluation-kit/reference schematic and documentation.
- Cross-checked required circuitry, component connections, and interfaces to verify that they remained correctly implemented after the reference-design features were removed.
- Reviewed changes for discrepancies and implementation mistakes before/during hardware validation.
- **Ownership:** Grant made the board revision. Connor's contribution was independent review, comparison, verification, and design validation—not entire PCB design or personal removal of every unused feature.

Reference wording: Performed an independent KiCad schematic review of a new AEGIS PCB revision derived from a TI evaluation/reference design. Cross-checked the modified design against the TI reference schematic to verify component connections and interfaces after unnecessary evaluation-board features, including HDMI support, were removed.

### 3. Acceptance Test Procedure (ATP) database and manufacturing test-data automation

- Created a Microsoft Access database structure intended to centralize historical and current manufacturing test data in one maintainable system.
- Created multiple Access user forms for entering test data and wrote VBA input-validation code.
- Wrote VBA scripts to parse existing Excel test files and upload parsed results into the ATP database.
- **Current active résumé — September 20, 2026:** Parsed and validated **50,000+ entries of test data** using SQL/VBA with Access and Excel. This is an entry count, not a count of devices, files, or distinct test runs; no timing or accuracy improvement is implied.
- Supported retrieval/reference of historical records and worked toward searchable, centralized test information.
- Addressed inconsistent legacy spreadsheet formatting; slide 10 records continued parser rewrites as next steps, not a completed universal importer.
- Slide 10 records an initially empty database plus forms and parsing/upload scripts. Do not infer a fully populated production database, complete migration, or final deployment.
- SQL remains previously user-reported experience; this presentation specifically corroborates Access, VBA, Excel, and user forms, not particular SQL queries or SQL Server/MySQL.
- The presentation's reference to a similar earlier TEAM database describes prior experience, not the employer for ATP.
- See [manufacturing test-data automation](manufacturing-test-automation.md) for the detailed record and reuse boundaries.

### 4. Programmable resistive loads and automated burn-in fixture proof of concept

**Presentation-supported communication and hardware work (slides 13–15):**

- Established communications with new programmable resistive loads for power-supply burn-in testing and with relay-control hardware.
- Reverse-engineered RS-232 command transactions using limited manufacturer documentation, trial and error, terminal software/PuTTY, and captured/sniffed serial communication.
- Used the device manual and an Excel checksum-generation tool to determine/generate checksums and construct valid device instructions. Do not imply authorship of the Excel tool.
- Grant set up the communication sniffer; Connor used the captured communication. Slide 14 says “RS302,” while Connor explicitly identifies the protocol as RS-232; retain RS-232 as the corrected reference wording rather than inventing another bus.
- Helped construct and integrate a test circuit containing relays, programmable loads, and a power supply with Mike and other AEGIS engineers.
- Contributed wiring, hardware setup, communication validation, and electrical/system debugging. The circuit was collaborative work, not sole hardware-design ownership.
- The presentation lists accuracy testing and scaling up as next steps; it does not establish completed production qualification or deployment.

**Direct clarification of the proof-of-concept function:**

- The work evolved into development of an automated production burn-in fixture proof of concept for multiple power-supply devices under test (DUTs).
- The control concept monitored DUT behavior and used relays to disconnect/isolate an individual DUT if a parameter exceeded its allowed range or a failure occurred, while leaving the other DUTs powered to continue their tests.
- The concept included recording the relay-trip/fault-event time and the monitored parameter outside its acceptable range, providing traceability for why and when a DUT was removed.
- **Current active résumé — September 20, 2026:** Reports isolating out-of-spec DUTs without interrupting remaining tests and logging trip events and fault parameters in the proof of concept. Preserve this as the current user-selected accomplishment wording, superseding the earlier concept-only description for these functions. Test conditions, number of DUTs, validation records, and production deployment remain unspecified.
- An earlier direct correction says Connor did not run burn-in tests. Fixture development and communication/circuit testing do not contradict that boundary; do not convert them into claims of conducting production burn-in tests.
- This is supported test-fixture proof-of-concept development. A complete production machine, commissioning, production deployment, measured throughput, and quantified reliability improvements are not established.

### General 2024 skills and scope

- Embedded Linux, Python, Bash, Yocto/Arago, Microsoft Access, VBA, Excel, RS-232, checksum/protocol debugging, schematic review, soldering, wiring, test hardware, and hardware/software troubleshooting.
- The explicit clarification additionally supports KiCad reference-design comparison, CAN exposure, and collaboration across engineering disciplines. CAN exposure does not establish 2024 ownership of a CAN stack or the later CAN FD/J1939/DroneCAN work.

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

## Confirmed Skill Boundaries — September 19, 2026

- Altium/KiCad/P-CAD experience supports PCB review and firmware programming/integration, including independent KiCad reference-design validation in 2024, not schematic or PCB-layout design ownership.
- Professional PWM experience includes buck/boost power converters; academic motor experience involves small 3.3 V motors, not large industrial motors or drives.
- No PLC experience. The 2024 burn-in test-fixture proof of concept is supported; the older blanket exclusion of fixture-design experience is superseded by this clarification. Complete production-equipment design, deployment, and commissioning remain unestablished.
- No established SQL Server, MySQL, C#, or Creo experience; do not infer these from SQL/Access or C/C++.

## Rev10 Wording and Reuse Notes — September 19, 2026

- Connor explicitly requested preserving the serial-flasher bullet: “Simplified TI's C++ CLI serial flasher for C2000 devices by removing unused device, CPU2, and dual-boot options, allowing production staff to program precompiled firmware with the click of a single button.” Treat this as user-retained résumé wording; do not infer a specific GUI framework, measured time savings, or ownership of TI's original utility.
- ATP belongs to summer 2024 (latest correction); the serial flasher remains summer 2025 internship work. This does not assign the other combined 2024/2025 internship accomplishments to a particular summer.
- Rev10 describes Git-based development and release processes supporting firmware/hardware traceability, defect and revision history, multi-engineer work, and controlled production releases/documentation. Retain the previously recorded GitLab/Git Extensions and release-tag context; do not add CI/CD automation or unconfirmed metrics.
- Writing commissioning procedures does not by itself establish hands-on installation or commissioning of manufacturing equipment.
- Use “hardware validation against datasheet specifications,” not “datasheet validation.” Use “PCB review in Altium, KiCad, and P-CAD” without implying electrical-design or layout ownership.

## Remaining Year and Outcome Questions

- Exact summer for the connected PIC32/TMS320 updater and Git/CAN-J1939 handoff work remains unresolved in these notes; none is assigned to 2024 from technology overlap alone.
- Dates for general diagnostic/network-discovery tools remain unresolved.
- Final ATP population/deployment and parser coverage, and the test conditions/validation records behind the reported DUT isolation and event logging, remain unrecorded.

## Active Versus Commented Résumé Content — September 20, 2026

The current `Rev10-EE/Resume.tex` actively selects 2025 converter PWM control and serial flashing, and 2024 KiCad review, burn-in proof of concept, and ATP automation. SCB301 CLI remains supported 2024 experience even though its bullet is commented out. The PIC32/TMS320 and Git bullets sit as commented alternatives within the 2025 group; record this as a proposed 2025 placement, not a separately verified date. Existing full-time facts and project details remain unchanged.
