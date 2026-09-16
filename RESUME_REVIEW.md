# Resume Evidence Review

## Rev9 Aditi Turf & Compact Utility Controls Variant — August 17, 2026

Rev9 targets the Cary, North Carolina Software Engineer I contract shared by Aditi Consulting. It leads with MATLAB, embedded C, controls, CAN/J1939, FreeRTOS, testing, and hardware integration while keeping the résumé to one page.

- The full-time AEGIS MATLAB bullet is filter-first: captured CAN text was parsed to compare candidate functions using variation under steady input and time to follow large electrical changes. Rolling-average and EMA approaches were selected, channel scaling was derived, and rolling-sum averaging was implemented in embedded C. No live-MATLAB-CAN acquisition or quantified improvement is claimed.
- Retained ECE 220 scripts and reports support MATLAB analysis of continuous/discrete signals, an RLC transfer function, and first-/second-order circuit and mechanical responses. Rev9 uses this artifact-backed dynamic-system work without claiming Simulink or production model-based development.
- The Python robotics work is source-backed within an NC State/BYU course framework and supports mass-spring-damper, planar-VTOL, and Hummingbird models; PD/PID/cascaded control; saturation; anti-windup; and PWM actuator mixing. It remains academic simulation, not deployed robotics firmware.
- A recovered Connor-authored Spring 2026 commit supports the stateful Lustre PID cruise controller. Direct context adds tuning and comparison with an earlier controller. Luke artifacts separately support counterexample-guided temporal-monitor corrections and verification of four properties at induction depth 2.
- The CARLA work was a three-person academic assignment. Source and direct context support Python agent/planner integration, PID-based longitudinal control, Town10HD testing, target-speed tuning, completion timing, collision counts, and lane-invasion counts. Rev9 does not claim production autonomous-driving work, a retained custom low-level PID equation, final gains, or a measured improvement.
- The current dsPIC33CK entry is based on schematics, datasheets, reference manuals, protocol specifications, JTAG, and bench-debug evidence; it does not attach unsupported formal-requirements ownership to that work.
- Explicit requirements, interface specifications, design reviews, staged integration, and seven passing host-side tests come from Senior Design. The adapter is described as team-built, and BMS remains confined to Senior Design.
- The internship bullets preserve the single-TMS320, PIC32/FreeRTOS, and twelve-A/B-pair/twenty-four-output distinctions. Host C++/Python tools and embedded programming/recovery logic are presented as connected stages rather than one monolithic tool.
- TEAM Industries remains as one compact entry because tolerance validation, manufacturing collaboration, and the 2021–2022 timeline are relevant to a factory-adjacent equipment role.
- Rev9 intentionally omits unsupported Simulink, Stateflow, Model-in-the-Loop, tool-specific Model-Based Design, Agile/Scrum, continuous integration, LIN, Ethernet, hydraulics, production-vehicle claims, and code-review ownership. It also cuts lower-priority VPX/IPMI, detailed Linux, teaching, MATLAB ML, and MOSFET content.
- The posting says it seeks mid-career candidates and no recent graduates. Because the recruiter contacted Connor directly, the résumé accurately retains the May 2026 graduation date and foregrounds the continuous 2021–present engineering history.

## Rev8 MATLAB and Programming-Project Expansion — August 14, 2026

Rev8 keeps the low-level-firmware positioning of Rev7 while adding professional MATLAB data analysis and verified academic MATLAB depth.

- Connor directly reports using captured converter telemetry to determine per-channel ADC scaling factors; the exact voltage/current ranges are supporting design context rather than the public résumé's main emphasis.
- A rolling average implemented in embedded C is confirmed, including a fixed `N`-sample window, circular replacement, a maintained rolling sum, startup behavior, and integer/fixed-point considerations.
- Connor directly reports building a MATLAB workflow in the full-time AEGIS role to parse captured CAN output and compare several filtering functions by steady-input variation and time to follow large electrical changes. Rolling-average and exponential moving average (EMA) approaches were selected; the EMA required only the previous filtered value rather than an `N`-sample history buffer.
- Other candidate functions, rolling-window length, EMA coefficient, sample cadence, production deployment, calibration results, and quantitative improvements remain unconfirmed.
- The MCP3428 channels are multiplexed rather than simultaneously sampled. Rev8 therefore presents voltage/current filtering and paired-sample slow telemetry without claiming switching-waveform power, true RMS, fast protection, or simultaneous power analysis.
- Connor directly reports engineering standups and ongoing communication with a geographically distributed firmware team. Rev8 does not add unsupported team size, cadence, process framework, or review ownership.
- A retained March 2025 ECE 302 report supports MATLAB ingestion of measured MOSFET data, numerical gradients and fits, parameter estimation, plots, and measured-versus-modeled analysis. Apparent placeholders/copy errors prevent claims of validated extraction accuracy.
- A retained Spring 2025 assignment supports MATLAB CNN training with a reported 99.24% validation result, SqueezeNet transfer learning with an approximately 90% test result, pretrained GoogLeNet inference, PCA/KLT eigenface analysis, and least-squares visualization. These remain academic results, not production or embedded ML.
- Retained Spring 2024 ECE 220 scripts/PDFs support repeated MATLAB work in vectorized programming, signals, transfer functions, complex arithmetic, matrices, plotting, and analytical transient-response models.
- The Spring 2025 machine-learning PDF does not identify its course internally; the archive filename suggests ECE 301, so the public résumé uses `Selected Coursework` rather than asserting a course number.
- The public senior-design repository resolves the active final architecture to STM32G474, BQ79616, ten STM32 ADC thermistor channels, UART, and extended-identifier CAN telemetry. Active source uses a timer-assisted service loop; the root README's FreeRTOS/DMA plan is stale and is not used as résumé evidence.
- Public Git history supports attributable Connor contributions to BQ bring-up, CRC/fault handling, subsystem-state integration, thermistor/logging changes, shutdown behavior, diagnostics, and documentation while also showing meaningful teammate CAN/timing work. Rev8 therefore presents this as a collaborative system.
- The public GitHub and local-project inventories are evidence-discovery aids. Repository ownership or possession alone is not treated as proof of personal implementation; public claims require source, report, or attributable-commit support.

## Rev7 Qualcomm Power and Limits Variant — August 14, 2026

Rev7 is a one-page targeted variant for Qualcomm's Power and Limits Software Engineer role. It preserves the Rev6 processor and attribution corrections while replacing lower-relevance general content with verified real-time, performance-analysis, and supporting machine-learning evidence.

- A Spring 2026 Connor-authored Git repository supports periodic POSIX-thread work in C using CPU affinity, absolute-time releases, priority-inheritance mutexes, timestamp traces, GCC/Make, and execution plots, plus academic EDF/rate/deadline-monotonic schedulability analysis.
- The same repository supports Lustre synchronous models and bounded model checking with counterexample-guided monitor corrections. This is academic formal verification, not pre-silicon evaluation or silicon sign-off.
- The C++ maze project supports BFS, DFS, greedy best-first search, and an academic runtime/memory comparison; it does not establish production profiling or optimization outcomes.
- A collaborative independent-study repository contains multiple Connor-authored Python commits covering parsing, configurable scoring, state/constraints, explanations, and semantic matching with pretrained sentence-transformer embeddings. Rev7 does not claim sole ownership, custom model training, embedded ML, or ML on power/silicon data.
- TI AM62 is described as an Arm-based SoC only in the context of Embedded Linux/Yocto integration. Rev7 does not claim bare-metal Arm, Arm assembly, or CPU-microarchitecture expertise.
- Compiler/toolchain configuration, GCC, and Make are supported; custom linker scripts, startup code, memory maps, and compiler optimization work remain unclaimed.
- Rev7 does not claim pre-silicon work, silicon profiling, DVFS/thermal algorithms, hardware acceleration, DMA, Android, Agile/Kanban, or quantified CPU/memory/power improvements.
- BMS remains confined to senior design, the 12-pair/24-output distinction is preserved, internship projects remain grouped across both summers, and no burn-in execution is implied.

## Rev6 Additions — August 14, 2026

Connor directly clarified the processor roles and current VPX work used in Rev6:

- **Positioning correction:** low-level embedded firmware is Connor's primary discipline. Embedded Linux is valuable supporting systems-integration experience and must not be presented as the main professional identity.
- **Burn-in correction:** Connor helped construct the relay/load/power-supply test circuit during the 2024 internship but did not perform, conduct, monitor, or run burn-in tests. Public wording must not imply otherwise.

- Use **dsPIC33CK** for the 16-bit digital signal controller; do not shorten it to the nonexistent family name “PIC33.” The locally preserved source directly supports dsPIC33CK toolchain and device-pack bring-up.
- The PIC32 ran FreeRTOS and handled communication/update coordination in the connected PIC32/TMS320 product.
- The TMS320 DSP ran bare-metal C using TI hardware-abstraction/peripheral libraries for real-time power control.
- Current work includes a VITA 46.11 Tier 2 IPMI management controller for a VPX power supply, using the I2C-based IPMB link. Tier 2 describes the management controller, not I2C or the entire power supply.
- CAN experience includes Classical CAN (CAN 2.0), CAN FD, J1939, and DroneCAN. The public résumé keeps the full taxonomy in Skills and uses individual protocols in prose only when they explain a specific system.
- The dsPIC33CK experience is not presented as part of the PIC32/TMS320 internship product because no source currently establishes that relationship.
- The C+-to-A- ECE 306 class-average change is a direct user report included in Rev6 with non-exclusive wording; supporting grade documentation is not stored in this repository.

Rev6 removes `APU/EPU` from the public summary and cover letter in favor of the clearer phrase “embedded power system.” It also replaces broad protocol lists in experience bullets with processor roles and system outcomes.

## Rev5 Corrections — August 10, 2026

The following direct corrections supersede conflicting language in Rev3, Rev4, archived cover letters, and older notes:

- **Senior design did not use the MSP430FR2355.** Later public-source review resolved the active architecture to STM32G474 and BQ79616 with ten ADC thermistor channels, UART, and CAN telemetry. The MSP430FR2355 belongs to ECE 306; the external CAN-transceiver part number remains unconfirmed.
- **BMS work is senior design only.** Do not attribute BMS research, selection, firmware, or integration to any AEGIS internship or full-time role.
- Connor graduated from NC State in May 2026 with a B.S. in Computer Engineering.
- The exact AEGIS timeline is Computer Science Intern (May--August 2024), Embedded Systems Intern (May--August 2025), and Embedded Firmware Engineer (May 2026--Present).
- Do not use “BSP” as a claimed skill. Name the supported work instead: TI Embedded Linux, Yocto/Arago images and toolchains, kernel and device-tree compilation, systemd services, Docker, and boot/service diagnosis.
- The C++ HEX-file programmer, Python/TCP transfer, PIC32 SPI-flash/golden-image handling, and TMS320 UART programming were multiple connected stages of one product's firmware-update and boot-control workflow.
- ECE 306 support ran Spring 2025, Fall 2025, and Spring 2026: two semesters of unofficial support at about 10 hours per week and one formal TA appointment at about 20 hours per week. Do not call the unofficial work unpaid, and confirm the exact semester-to-status mapping before stating it in a targeted version.
- OPS2 lead instruction ran Fall 2025 and Spring 2026. Standalone IEEE soldering-workshop coordination, lecturing, and laboratory instruction was a separate role, although OPS2 also taught soldering.

Rev5 uses these corrected facts. The material below documents the earlier Rev3 audit and should be read in that historical context.

## Post-Rev3 Archive Import — August 2026

The complete recovered archive was organized under [`history/`](history/) after Rev3 was produced. Across the original and recovered sets plus two later MATLAB assignments, the audit covered 81 PDFs, 21 Word documents, 16 ZIP archives, all 40 extracted TeX files, and four saved career-page bundles. The newly recovered details were added to the `experience/` source library with evidence labels; **Rev3 itself was not silently rewritten from one-off or conflicted drafts**.

High-value additions include a possible PIC32/TMS320 two-processor update architecture, CAN/J1939, separate C++ and Python transfer tools, GitFlow/signed-tag documentation, the IEEE parts program and OPS2 toolchain, additional ECE 306 controls, Qiskit/Grover work, Verilog/Vivado artifacts, and richer TEAM validation context. See the archive [inventory](history/INVENTORY.md) for the exact conflicts and privacy boundaries.

## Major Changes Made After the History Audit

- Read the initial 36-file set now stored under `history/resumes/*/legacy-audit/` (10 DOCX and 26 PDF), using byte and extracted-text hashes to verify repeated copies and export/color variants.
- Reorganized the experience library so detailed implementation, debugging, teamwork, and historical context remain available without forcing every fact into the résumé.
- Added archive-supported TEAM details: dimensional inspection, tolerance validation, a factory-facing Excel/VBA checker, manufacturing collaboration, and a 17,000+ record tooling/part catalog.
- Added the archive-supported Fall 2024 date and system scope for the MSP430 ECE 306 vehicle.
- Preserved earlier projects, plumbing, tutoring, robotics, outreach, credentials, and leadership in separate source files for targeted variants.
- Rebuilt Rev3 around four then-understood AEGIS workflows; Rev5 corrects the record by moving BMS entirely to senior design and power-conversion control to the internship period.
- Moved the NC State degree directly below the name and removed the duplicated Education section.
- Reduced taxonomy-heavy bullets and retained ATS keywords within coherent engineering workflows.
- Kept the general résumé focused on embedded firmware, power electronics, senior-design BMS work, hardware integration, Embedded Linux/platform integration, platform management, and validation roles.

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

- Confirm whether the 24-output count, transformer-coupled topology, A/B paired-stage behavior, and safe-operating logic may be disclosed publicly.
- Confirm public use of TI AM62/TMS320 family names, SocketCAN/PCAN, DBC/signal-mapping work, and platform-management behavior.
- Keep customer names, internal board/product identifiers, credentials, IP addresses, raw frames, proprietary register maps, schematics, and electrical specifications out of this public repository.
- Do not link or copy local AEGIS logs into the résumé repository; some contain third-party notices and sensitive system data.

## Facts Requiring User Confirmation

- Exact number/types of BMS, monitoring, protection, charger, and interface ICs evaluated, validated, or integrated.
- Whether SocketCAN, PCAN, DBC interpretation, CAN signal mapping, and target-family names are safe to disclose.
- Whether the confirmed 24 physical outputs/twelve A-B pair topology and transformer-coupled architecture are approved for public disclosure. Each A output was independently parameterized; each B output only matched or inverted its paired A waveform.
- What APU and EPU stand for, whether the acronyms are public, and whether they describe one system or related systems.
- Exact battery/CAN ownership, external-watchdog failure and recovery behavior, Docker usage, and Windows/Linux portability changes in the current role.
- Which additional VITA 46.11/IPMI features beyond the confirmed Tier 2 sensor, FRU/inventory, and event behavior are safe to describe publicly.
- Exact senior-design team size, personally owned subsystems, final prototype state, and completed validation.
- Exact standalone soldering-workshop dates and audience size.
- Whether the C+ to A- class change is documented and public.
- Whether the IEEE parts program's reported $2,000/two-week result and lower-student-cost outcome can be documented and precisely defined.
- Whether OPS2 should be described publicly as lead instructor, co-lead, or one of two lead instructors.
- Whether a separate artifact exists for the older Kogge--Stone or VHDL claims; current ECE 310 evidence supports Verilog and a Wallace-tree multiplier instead.
- Current validity of the Adobe and FAA drone credentials.

## Recommended Role-Specific Variants

- **Embedded firmware:** emphasize C/C++, peripheral drivers, RTOS, register-level debugging, JTAG, automated validation, and board bring-up.
- **Power electronics/BMS firmware:** expand bidirectional buck-boost control, ADC feedback, converter coordination, component trade studies, protection/monitoring ICs, and safe-operation constraints.
- **Embedded Linux/platform integration:** expand AM62, Yocto/Arago, device trees, kernel compilation, boot/root filesystems, systemd/watchdog services, Docker, Python/Bash tooling, and IPMI platform management.
- **Hardware integration/test:** expand schematic/datasheet review, breakout-board prototyping, scopes/analyzers, controlled substitutions, tolerance validation, and reproducible test procedures.
- **Applications/field support/technical training:** expand teaching, soldering workshops, documentation, customer-style diagnosis, manufacturing collaboration, and cross-disciplinary communication.
- **Digital/software:** selectively add the ECE 212 logic design, ECE 309 C++ algorithms, LC-3 parser, or automation projects from `experience/personal-projects.md`.
