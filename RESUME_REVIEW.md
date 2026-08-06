# Rev3 Resume Review

## Major Changes Made After the History Audit

- Read all 36 files in `experience/history/` (10 DOCX and 26 PDF), using byte and extracted-text hashes to verify repeated copies and export/color variants.
- Reorganized the experience library so detailed implementation, debugging, teamwork, and historical context remain available without forcing every fact into the résumé.
- Added archive-supported TEAM details: dimensional inspection, tolerance validation, a factory-facing Excel/VBA checker, manufacturing collaboration, and a 17,000+ record tooling/part catalog.
- Added the archive-supported Fall 2024 date and system scope for the MSP430 ECE 306 vehicle.
- Preserved earlier projects, plumbing, tutoring, robotics, outreach, credentials, and leadership in separate source files for targeted variants.
- Rebuilt Rev3 around four current AEGIS workflows: programmable power conversion, BMS/component integration, protocol/board debugging, and Embedded Linux/platform management.
- Moved the NC State degree directly below the name and removed the duplicated Education section.
- Reduced taxonomy-heavy bullets and retained ATS keywords within coherent engineering workflows.
- Kept the general résumé focused on embedded firmware, power/BMS, hardware integration, Embedded Linux/BSP, platform management, and validation roles.

## History Material Used in Rev3

- 2024 AEGIS: restricted SSH/chroot CLI for embedded power hardware; Linux, Bash, Python, RS232, and CAN context.
- TEAM Industries: Excel/VBA out-of-spec logic and 17,000+ tooling/part records connecting vendors, operations, locations, and revision data.
- ECE 306: MSP430/custom-PCB vehicle and the technical foundation later used while teaching the course.
- Teaching history: repeated evidence of tutoring, technical explanation, project mentoring, and robotics/coding instruction.

## Material Preserved in Markdown but Excluded From Rev3

- Early 555-timer power experiments, WSL, Chromebook conversion, calculator programming, AutoHotkey automation, and the LC-3 translation tool.
- ECE 212 sequential logic and ECE 309 search-algorithm projects.
- Mathematics tutoring, high-school robotics, aquaponics, community leadership, and plumbing experience.
- Associate degree, old GPAs, high-school honors, Adobe credentials, and FAA drone credential.

These facts may support a targeted variant, but they are weaker than current professional engineering work for the general résumé.

## Claims Removed or Softened

- Excluded the claim that teaching raised the class average from C+ to A- because no grade documentation is stored locally.
- Omitted FDCAN clock-correction and MCU-migration claims because the audited sources do not independently establish them.
- Omitted SMBus because supporting evidence was not located.
- Described IPMI/IPMB/FRU/sensor work as characterization and validation, not authorship of an IPMI stack.
- Described senior-design SPI work as a prototype and avoided claiming a production-ready or vehicle-deployed system.
- Used the neutral historical title `Intern` for the combined 2024/2025 AEGIS entry because only the 2024 `Computer Science Intern` title is archived.
- Avoided internship time-savings, reliability, production-volume, and burn-in outcome claims that lack measured evidence.

## Metrics That Could Strengthen Future Variants

- Number of converter pairs, boards, products, or power-system variants supported, with the counted unit clearly defined.
- Number and categories of BMS/power-management ICs evaluated, brought up, and fully integrated.
- Number of drivers, automated tests, target devices, firmware-update workflows, or field systems supported.
- Measured reduction in flashing, bring-up, or validation time from automation.
- Number of TA semesters, laboratory sections, workshops, or students supported.
- Documented before/after grade distribution for the teaching work.
- Final senior-design validation scope and number of interfaces/test procedures owned.

## Confidentiality Concerns

- Confirm whether the 24-channel count, transformer-coupled topology, paired-stage behavior, and safe-operating logic may be disclosed publicly.
- Confirm public use of TI AM62/TMS320 family names, SocketCAN/PCAN, DBC/signal-mapping work, and platform-management behavior.
- Keep customer names, internal board/product identifiers, credentials, IP addresses, raw frames, proprietary register maps, schematics, and electrical specifications out of this public repository.
- Do not link or copy local AEGIS logs into the résumé repository; some contain third-party notices and sensitive system data.

## Facts Requiring User Confirmation

- Whether the B.S. Computer Engineering degree was conferred in May 2026; the date has now passed.
- Exact official title and start date for the current AEGIS role.
- Official title for the May–August 2025 AEGIS internship and which deliverables belong to 2024 versus 2025.
- Exact number/types of BMS, monitoring, protection, charger, and interface ICs evaluated, validated, or integrated.
- Whether SocketCAN, PCAN, DBC interpretation, CAN signal mapping, and target-family names are safe to disclose.
- Whether the 24 channels are 24 total PWM channels or 24 paired control channels, and the public-safe transformer topology.
- Whether IPMB, FRU, and sensor access were investigated, validated, integrated, or implemented in deliverable code.
- Exact senior-design team size, personally owned subsystems, final prototype state, and completed validation.
- Exact TA semesters, official role/course title, sections, and student count.
- Whether the workshop role should be described as co-lead or joint lead instructor and its exact dates/organization.
- Whether the C+ to A- class change is documented and public.
- Associate in Arts completion date; archived versions conflict between August 2023 and Fall 2024.
- Current validity of the Adobe and FAA drone credentials.

## Recommended Role-Specific Variants

- **Embedded firmware:** emphasize C/C++, peripheral drivers, RTOS, register-level debugging, JTAG, automated validation, and board bring-up.
- **Power electronics/BMS firmware:** expand bidirectional buck-boost control, ADC feedback, converter coordination, component trade studies, protection/monitoring ICs, and safe-operation constraints.
- **Embedded Linux/BSP:** expand AM62, Yocto/Arago, device trees, boot/root filesystems, systemd/watchdog services, Python/Bash tooling, and IPMI platform management.
- **Hardware integration/test:** expand schematic/datasheet review, breakout-board prototyping, scopes/analyzers, controlled substitutions, tolerance validation, and reproducible test procedures.
- **Applications/field support/technical training:** expand teaching, soldering workshops, documentation, customer-style diagnosis, manufacturing collaboration, and cross-disciplinary communication.
- **Digital/software:** selectively add the ECE 212 logic design, ECE 309 C++ algorithms, LC-3 parser, or automation projects from `experience/personal-projects.md`.
