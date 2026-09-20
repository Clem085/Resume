# Experience Source Library

The Markdown files in this directory are the detailed source of truth for résumé variants. They preserve implementation context, debugging methods, tools, teamwork, and evidence boundaries; the one-page résumé intentionally uses only a high-level synthesis.

## Evidence Labels

- **Direct:** Connor supplied the fact in the current project.
- **Corroborated:** multiple contemporaneous documents or an official record support it.
- **Archive-derived / confirm:** a useful detail appears in only one historical draft or cover letter.
- **Conflicted:** sources disagree; retain both versions here and resolve them before publication.
- **Excluded:** a template, job requirement, aspirational statement, private narrative, or unrelated third-party claim.

Historical wording is never promoted automatically. In particular, a cover letter's description of a target job is not evidence that Connor performed that work.

## Target Role Families

The strongest general positioning is for:

1. Embedded firmware engineering
2. Firmware/hardware integration and board bring-up
3. Power-electronics firmware or BMS-focused embedded-system design
4. Embedded Linux, platform-integration, and platform-management engineering
5. Hardware validation, systems test, applications, or field-support engineering
6. Embedded controls, robotics, vehicle simulation, and autonomous-systems integration
7. Engineering data analysis, signal validation, and MATLAB-assisted firmware development

## Source Files

- `aegis-power-systems.md` — current professional work plus the 2024 and 2025 AEGIS internships
- `adc-monitoring-card.md` — professional ADC scaling and data-driven filter selection using MATLAB/CAN captures, embedded-C rolling-average logic, and EMA tradeoffs
- `matlab-data-analysis.md` — professional CAN/ADC filter analysis plus academic signals, MOSFET, numerical, PCA, and machine-learning work in MATLAB
- `controls-and-autonomy.md` — Python robotics control, Lustre PID, CARLA autonomous-driving simulation, and claim boundaries
- `senior-design.md` — EV Active Sensor Adapter architecture, component evaluation, firmware, validation, documentation, and teamwork
- `ece-306.md` — Fall 2024 MSP430 vehicle project and later embedded-systems TA work
- `teaching-leadership.md` — electronics workshop instruction, TA work, mathematics tutoring, and earlier mentoring
- `manufacturing-test-automation.md` — AEGIS SQL/VBA/Access/Excel ATP test-data parsing, validation, historical lookup, and database entry during the summer 2024 Computer Science Internship
- `team-industries.md` — 2021/2022 manufacturing, tolerance validation, Excel/VBA automation, and reporting
- `personal-projects.md` — detailed inventory of microarchitecture, real-time, formal-verification, RTL, controls, assembly, MATLAB, ML, quantum, Linux, and earlier programming projects
- `github-projects.md` — repository-by-repository public-source audit, authorship boundaries, reproducible results, and safe résumé framing
- `earlier-background.md` — plumbing, robotics, aquaponics, leadership, credentials, and archive-only background

## Resume Selection Priority

### Core general résumé

1. Current AEGIS engineering workflows
2. EV Active Sensor Adapter senior design
3. AEGIS internships
4. Embedded-systems TA and soldering workshop leadership
5. TEAM Industries automation and manufacturing data
6. NC State B.S. Computer Engineering

### Targeted variants only

- ECE 306 vehicle project for MSP430/student-project variants
- Mathematics tutoring for instruction, applications, and customer-support roles
- Logic/algorithm projects for digital-design or software variants
- MATLAB data analysis, device characterization, and image-learning projects for controls, test, semiconductor, or data-oriented variants
- Plumbing and early hands-on work for field/manufacturing variants
- Robotics, outreach, and community leadership for leadership-focused applications
- Robotics PID, Lustre, and CARLA for vehicle, controls, real-time, and autonomous-systems variants

### Archive only

- Old objectives, GPAs, high-school awards, routine clubs, personal narratives, and superseded beginner projects
- Private addresses, student IDs, third-party contacts, and the unrelated sample résumé
- Unsupported outcomes or claims whose wording changed across historical revisions

## History Audit

The full archive now lives under [`../history/`](../history/). The initial 36-document audit was expanded to include the recovered set and two later MATLAB assignments: 81 PDFs, 21 Word documents, 16 ZIP archives, and four saved career-page bundles. All 40 extracted TeX files (33 distinct text hashes) and every distinct authored document body were read. Byte and normalized-text hashes identified exact copies, near-duplicate exports, color/layout variants, and mislabeled files.

The archive is deliberately broader than this library. It preserves private records, duplicate application packets, obsolete objectives, conflicted drafts, unrelated templates, and saved job pages, while these Markdown files retain only normalized experience facts and clearly labeled leads. See the archive [guide](../history/README.md) and [inventory](../history/INVENTORY.md) for classification, privacy restrictions, duplicate groups, and source anomalies.

Important facts recovered from the archive include:

- The active senior-design firmware uses an STM32G474, TI BQ79616 battery monitor, ten STM32 ADC thermistor channels, UART, and extended-identifier CAN telemetry. It uses a timer-assisted service loop, not the stale root README's planned FreeRTOS/DMA architecture; MSP430FR2355 belongs to ECE 306.
- The 2024 AEGIS role was historically titled **Computer Science Intern** and ran May–August 2024.
- The 2025 AEGIS role was **Embedded Systems Intern** and ran May–August 2025.
- The current AEGIS role is **Embedded Firmware Engineer**, beginning May 2026.
- Current professional work includes dsPIC33CK 16-bit firmware/toolchain bring-up and implementation of a VITA 46.11 Tier 2 IPMI management controller for a VPX power supply over I2C-based IPMB.
- Current full-time AEGIS work includes parsing captured CAN telemetry in MATLAB to determine ADC scaling factors and compare several filter functions by steady-input variation and time to follow large changes. Rolling-average and EMA approaches were selected; the rolling average used a fixed sample window, circular replacement, and a maintained sum in embedded C. This work does not belong to either internship.
- CAN experience spans Classical CAN (CAN 2.0), CAN FD, J1939, and DroneCAN; J1939 and DroneCAN are higher-layer protocols and should not be presented as link-layer CAN variants.
- The 2024 work included a restricted SSH CLI for embedded power hardware, Linux/Bash/Python, RS232, and CAN.
- The 2024 hardware work included independent KiCad reference-design review and collaborative relay/load/power-supply circuit construction for an automated burn-in fixture proof of concept. The current active résumé reports DUT isolation and event logging within the proof of concept; production deployment and detailed validation conditions remain unestablished.
- The C++ HEX-file programmer, Python/TCP transport, PIC32 SPI-flash/golden-image logic, and TMS320 UART programming were connected stages of one product's update and boot-control workflow, not one monolithic program.
- In that product, the PIC32 ran FreeRTOS for communication/update coordination and the TMS320 DSP ran bare-metal C with TI hardware libraries for real-time control.
- The STM32G474/BQ79616 EV sensor-adapter work belongs to NC State senior design; separate professional smart-battery CAN interface work belongs to AEGIS. MSP430FR2355 belongs to ECE 306.
- Connor graduated from NC State in May 2026 with a B.S. in Computer Engineering.
- ECE 306 support covered Spring 2025, Fall 2025, and Spring 2026: two semesters of unofficial support at about 10 hours per week and one formal TA appointment at about 20 hours per week. The exact semester-to-status mapping should be confirmed before a targeted version states it.
- OPS2 lead instruction ran in Fall 2025 and Spring 2026; the standalone IEEE soldering-workshop role was separate from OPS2.
- TEAM work included dimensional inspection, spline-tolerance checks, Excel/VBA out-of-spec logic, technical reports, a 17,000+ entry entire plant tooling where-used list built with custom lookup formulas and data validation. ATP database automation using SQL/VBA/Access/Excel belongs to AEGIS (corrected September 19, 2026).
- The ECE 306 MSP430 vehicle was completed in Fall 2024 and used custom PCBs, Wi-Fi control, ADC line following, motor PWM, and LCD output.
- Paid mathematics tutoring ran January–May 2022 and followed extensive volunteer tutoring.
- Older records preserve early power-circuit, digital-logic, C++ search, assembly-parser, Linux, robotics, plumbing, and community-leadership experience.
- Newer LaTeX sources preserve the PIC32/TMS320 two-processor update architecture, CAN/J1939, connected C++ and Python transfer stages, and extensive Git release-process documentation; disclosure boundaries and exact documentation metrics still require confirmation.
- Spring 2026 project repositories add periodic POSIX-thread scheduling and execution tracing in C, Lustre formal verification with counterexample-guided fixes, and a Connor-authored portion of a collaborative Python/sentence-transformer mentor-matching system.
- Newly recovered Spring 2026 files add a stateful Lustre PID cruise controller and CARLA Python agent integration/evaluation; this supersedes the older no-PID/CARLA-exploration boundary while remaining academic work.
- Current records do not establish Simulink, Model-in-the-Loop, or tool-specific Model-Based Design experience; do not add those claims to future variants without new evidence.
- ECE 463 artifacts support Connor-authored C++ cache, branch-predictor, and out-of-order pipeline simulators plus automated Python design-space sweeps; the retained out-of-order quick-test suite passes all three cases.
- ECE 310 artifacts support a structural Verilog Wallace-tree multiplier and serial/parallel arithmetic blocks. The current public repository does not support the older Kogge--Stone or VHDL claims.
- Professional MATLAB work complements the monitoring-card firmware by comparing captured converter telemetry and the tradeoff between stable voltage/current readings and rapid transient response; Spring 2024–2025 coursework adds signals, transfer functions, MOSFET fitting/model comparison, CNN training, transfer learning, PCA/KLT, and least squares.
- IEEE work includes a ten-week applied OPS2 course designed to close gaps between classroom theory and hands-on electronics, parts-distribution operations, PlatformIO/VS Code/GitHub instruction, and $10,000 raised in two weeks through the ECE 306 parts program while lowering student costs. Connor corrected and approved the fundraising result for résumé use on September 16, 2026.
- An official Tri-County record resolves the Associate in Arts award date as August 1, 2023 and records a 4.0 GPA and “Graduated Top of Class.” The underlying transcript remains private.

## Facts to Reconcile Before Future Variants

- Exact summer for the connected PIC32/TMS320 updater and Git/CAN-J1939 handoff work; the four explicitly documented 2024 projects and 2025 serial flasher are now separated
- Current status of Adobe and FAA credentials
- Exact standalone soldering-workshop dates and audience size
- Public-disclosure boundaries for current AEGIS power topology and platform-management work
- What APU and EPU stand for, whether the acronyms are public, and the precise battery/CAN/watchdog ownership that may be described
- Exact Docker usage and the specific build, code, and tooling changes made for Windows/Linux compatibility
- Whether the C+-to-A- teaching result can be documented and publicly attributed
- Whether a separate artifact exists for the older Kogge--Stone or VHDL claims; they are not supported by the current ECE 310 repository
- Professional ADC details beyond the confirmed rolling-average/EMA selection: other candidate functions, window and EMA parameters, acquisition cadence, calibration results, quantitative improvements, final deployment, and public-disclosure approval for exact ranges
- Correct course number and individual/team scope for the Spring 2025 MATLAB machine-learning assignment

## September 2026 Direct Additions

Connor's September 15 account adds the AEGIS C++ `serial_flasher.exe` customization for TMS320F28379D, CCS build/image-generation documentation, smart-battery CAN interface work, KiCad/P-CAD/Altium review, full-system fault isolation, and engineering/production diagnostic utilities. See [AEGIS](aegis-power-systems.md), [ATP automation](manufacturing-test-automation.md), and [TEAM Industries](team-industries.md). The serial-flasher customization is documented separately from the broader C++/Python/PIC32 update workflow; their exact relationship remains open. Connor confirmed the serial flasher as summer 2025 and confirmed ATP as summer 2024 AEGIS internship work (latest correction, superseding the earlier 2025 assignment) on September 19, superseding the September 16 TEAM attribution. The expanded entire plant tooling-inventory details remain TEAM work.

Connor confirmed experience with PlatformIO, STM32Cube, MPLAB, and Code Composer Studio on September 16, 2026. These may be selected for a targeted résumé when the development environment matters; a general résumé does not need to list every IDE.

## Creating New Revisions from Rev10 — September 19, 2026

Use [current Rev10](../Rev10-EE/Resume.tex) as a wording/layout reference and these topic files as the factual source. Direct corrections from Connor supersede older résumé wording and archive summaries. A résumé's inclusion of a skill is not new proof of expertise beyond its supporting record.

| Item | Confirmed fact or boundary | Source |
| --- | --- | --- |
| ATP automation | AEGIS summer 2024 Computer Science Internship; SQL/VBA/Access/Excel; expand Acceptance Test Procedure (ATP) | [ATP](manufacturing-test-automation.md) |
| TI C++ serial flasher | AEGIS summer 2025; preserve Connor's preferred wording; separate from the connected PIC32 updater | [AEGIS](aegis-power-systems.md) |
| TEAM manufacturing tools | 2021: validation of existing 17,000+ record TWUL; 2022: inspection/tolerance tools and ACCEPT/REJECT/INCOMPLETE classifications; no ATP attribution | [TEAM](team-industries.md) |
| Senior design | Voltage/temperature sensing, LEDs, state machine, error logging; CAN integration, not CAN middleware/message authorship | [Senior design](senior-design.md) |
| Maze solver | Correctness and iteration counts compared; no established runtime or memory measurements | [Projects](personal-projects.md) |
| PCB tools | Review and firmware integration, not established schematic/layout design ownership | [AEGIS](aegis-power-systems.md) |
| PWM/motors | Professional buck/boost converter PWM; academic small 3.3 V motors; no industrial-drive or PLC experience | [ECE 306](ece-306.md) |
| Unsupported target keywords | Do not add C#, SQL Server, MySQL, Creo, PLCs, production-equipment commissioning, or deployed production-fixture claims without new evidence | [AEGIS](aegis-power-systems.md) |

For the Snap-on Electrical Engineer role (Murphy, NC; Job ID 2026-20685), emphasize professional C, manufacturing databases, production programming, electrical/firmware troubleshooting, and technical teaching. Experience precedes Projects in Rev10; relevant professional accomplishments belong under the employer rather than duplicated as projects. This is target-specific selection guidance, not a requirement to use the same order or project selection for every future role.

Keep current-role ongoing work in present tense and completed work in past tense. Use “Embedded Platforms” for the MCU/OS list. Preserve the distinction between three semesters of ECE 306 support and one formal TA appointment. The IEEE $10,000/two-week result is already user-confirmed. Do not turn four internships into four years of professional experience.

## Summer 2024 AEGIS Reconciliation — Latest Clarification

The July 31, 2024 presentation `FINAL-AegisInternship-ConnorSavugot.pptx` and Connor's explicit clarification establish four areas: SCB301 restricted Linux CLI; independent KiCad schematic/reference-design review; ATP Access/VBA/Excel database automation; and programmable-load/relay communications with collaborative burn-in fixture proof-of-concept development. The [AEGIS source](aegis-power-systems.md) distinguishes presentation evidence, direct clarification, and remaining validation questions.

Earlier ATP assignments to TEAM and summer 2025 are superseded. The TI C++ serial flasher remains summer 2025; May 2026–present work is unchanged. Unresolved internship deliverables must not be assigned to 2024 merely because they use similar technologies. The older blanket fixture-design exclusion is superseded only to the extent of the supported proof of concept; deployment and commissioning remain unestablished.

## Current Résumé Sync — September 20, 2026

Reconciled the active and commented entries in [Rev10](../Rev10-EE/Resume.tex). Active selections now date TMS320 converter PWM work to 2025, TEAM TWUL validation to 2021, and TEAM inspection automation to 2022. ATP reports 50,000+ test-data entries parsed/validated; burn-in isolation and fault logging are reported proof-of-concept functions. These updates are sourced from the user-selected current résumé.

Commented alternatives remain distinguishable from active selections: PIC32/Git proposed 2025 dates, TEAM cost-tool proposed 2022 date, the approximately 2,000-gear investigation/newly-replaced-oil account, and 2021 merchandise inventory are retained with their evidence limits in the employer files. Existing supported projects are not deleted merely because their résumé bullets are commented out.
