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

## Source Files

- `aegis-power-systems.md` — current professional work plus the 2024 and 2025 AEGIS internships
- `senior-design.md` — EV Active Sensor Adapter architecture, component evaluation, firmware, validation, documentation, and teamwork
- `ece-306.md` — Fall 2024 MSP430 vehicle project and later embedded-systems TA work
- `teaching-leadership.md` — electronics workshop instruction, TA work, mathematics tutoring, and earlier mentoring
- `team-industries.md` — 2021/2022 manufacturing, tolerance validation, Excel/VBA automation, and reporting
- `personal-projects.md` — earlier technical, academic, Linux, automation, circuit, and programming projects
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
- Plumbing and early hands-on work for field/manufacturing variants
- Robotics, outreach, and community leadership for leadership-focused applications

### Archive only

- Old objectives, GPAs, high-school awards, routine clubs, personal narratives, and superseded beginner projects
- Private addresses, student IDs, third-party contacts, and the unrelated sample résumé
- Unsupported outcomes or claims whose wording changed across historical revisions

## History Audit

The full archive now lives under [`../history/`](../history/). The initial 36-document audit was expanded to include the newly recovered set: 79 PDFs, 21 Word documents, 16 ZIP archives, and four saved career-page bundles across both imports. All 40 extracted TeX files (33 distinct text hashes) and every distinct authored document body were read. Byte and normalized-text hashes identified exact copies, near-duplicate exports, color/layout variants, and mislabeled files.

The archive is deliberately broader than this library. It preserves private records, duplicate application packets, obsolete objectives, conflicted drafts, unrelated templates, and saved job pages, while these Markdown files retain only normalized experience facts and clearly labeled leads. See the archive [guide](../history/README.md) and [inventory](../history/INVENTORY.md) for classification, privacy restrictions, duplicate groups, and source anomalies.

Important facts recovered from the archive include:

- The 2024 AEGIS role was historically titled **Computer Science Intern** and ran May–August 2024.
- The 2025 AEGIS role was **Embedded Systems Intern** and ran May–August 2025.
- The current AEGIS role is **Embedded Firmware Engineer**, beginning May 2026.
- The 2024 work included a restricted SSH CLI for embedded power hardware, Linux/Bash/Python, RS232, and CAN.
- The C++ HEX-file programmer, Python/TCP transport, PIC32 SPI-flash/golden-image logic, and TMS320 UART programming were connected stages of one product's update and boot-control workflow, not one monolithic program.
- BMS research, selection, firmware prototyping, and integration belong exclusively to senior design; they must not be attributed to an AEGIS internship or job.
- Connor graduated from NC State in May 2026 with a B.S. in Computer Engineering.
- ECE 306 support covered Spring 2025, Fall 2025, and Spring 2026: two semesters of unofficial support at about 10 hours per week and one formal TA appointment at about 20 hours per week. The exact semester-to-status mapping should be confirmed before a targeted version states it.
- OPS2 lead instruction ran in Fall 2025 and Spring 2026; the standalone IEEE soldering-workshop role was separate from OPS2.
- TEAM work included dimensional inspection, spline-tolerance checks, Excel/VBA out-of-spec logic, technical reports, and a catalog of more than 17,000 tooling/part records.
- The ECE 306 MSP430 vehicle was completed in Fall 2024 and used custom PCBs, Wi-Fi control, ADC line following, motor PWM, and LCD output.
- Paid mathematics tutoring ran January–May 2022 and followed extensive volunteer tutoring.
- Older records preserve early power-circuit, digital-logic, C++ search, assembly-parser, Linux, robotics, plumbing, and community-leadership experience.
- Newer LaTeX sources preserve the PIC32/TMS320 two-processor update architecture, CAN/J1939, connected C++ and Python transfer stages, and extensive Git release-process documentation; disclosure boundaries and exact documentation metrics still require confirmation.
- IEEE drafts preserve a ten-week OPS2 project sequence, parts-distribution operations, PlatformIO/VS Code/GitHub instruction, and a reported $2,000 raised in two weeks; the role title and metric still require confirmation.
- An official Tri-County record resolves the Associate in Arts award date as August 1, 2023 and records a 4.0 GPA and “Graduated Top of Class.” The underlying transcript remains private.

## Facts to Reconcile Before Future Variants

- Which internship deliverables belong to 2024 versus 2025
- Current status of Adobe and FAA credentials
- Exact standalone soldering-workshop dates and audience size
- Public-disclosure boundaries for current AEGIS power topology and platform-management work
- What APU and EPU stand for, whether the acronyms are public, and the precise battery/CAN/watchdog ownership that may be described
- Exact Docker usage and the specific build, code, and tooling changes made for Windows/Linux compatibility
- Whether the IEEE $2,000/two-week result and the C+-to-A- teaching result can be documented and publicly attributed
- Whether repeated Verilog records or the lone VHDL cover-letter claim accurately describes each digital-design project
