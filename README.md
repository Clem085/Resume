# Connor Savugot Resume

This repository keeps each major résumé design in a separate, self-contained revision folder.

The [`experience/`](experience/) folder is the detailed source library for future résumé variants. Its [index](experience/README.md) covers professional work, senior design, technical teaching, TEAM Industries, earlier projects, and archive-only background while documenting relevance and unresolved facts.

The recovered resumes, cover letters, LaTeX sources, application packets, and supporting files are organized under [`history/`](history/). See its [archive guide](history/README.md) and [evidence inventory](history/INVENTORY.md) before relying on a historical claim; duplicates and conflicted drafts are intentionally preserved.

Current attribution rules supersede wording in older revisions and archived prompts: senior design used an STMicroelectronics controller, TI BQ-family battery-monitor/ADC, and external CAN transceivers; MSP430FR2355 belongs to ECE 306; BMS work belongs to senior design, not AEGIS; Connor's current AEGIS title is Embedded Firmware Engineer beginning May 2026; the current role includes dsPIC33CK and VITA 46.11 Tier 2 VPX/IPMI work; and the exact TI Linux work should be named instead of using the broader label “BSP.”

## Revisions

| Revision | Description |
| --- | --- |
| [`Rev0/`](Rev0/) | Reconstructed November 2024 résumé using the original Source Sans layout, gray contact banner, icon links, ruled headings, and legacy content. `.build/legacy-reference.pdf` is the original uploaded PDF used to verify the reconstruction. |
| [`Rev1/`](Rev1/) | Compact one-page embedded-firmware résumé created before the visual redesign. |
| [`Rev2/`](Rev2/) | Previous content presented in the Rev0 visual style, with expanded AEGIS, BMS, senior-design, soldering-instructor, and teaching-assistant experience. |
| [`Rev3/`](Rev3/) | Rewritten embedded firmware and hardware-integration résumé emphasizing power conversion, BMS integration, protocol debugging, Embedded Linux, IPMI, senior design, and technical teaching. |
| [`Rev4/`](Rev4/) | General full-time embedded-firmware résumé using the reconciled 12-pair/24-output power-control architecture, stronger end-to-end engineering workflows, and a matching adaptable cover letter. |
| [`Rev5/`](Rev5/) | Linux-forward embedded-firmware résumé and blanket cover letter with the exact AEGIS timeline, BMS confined to senior design, TI Yocto/Arago kernel and device-tree work, Docker, APU/EPU system integration, and the connected PIC32/TMS320 update workflow. |
| [`Rev6/`](Rev6/) | Low-level-firmware-first résumé and cover letter emphasizing dsPIC33CK, PIC32/FreeRTOS, bare-metal TMS320 DSP control, communication interfaces, VPX/IPMI, and board bring-up; Embedded Linux remains supporting systems-integration breadth. |

Rev6 is the newest résumé revision.

Each revision root contains:

- `Resume.tex` — self-contained LaTeX source, including contact information
- `Resume.pdf` — compiled résumé
- `CoverLetter.tex` and `CoverLetter.pdf` — matching blanket cover-letter source and PDF in Rev4 and later
- `.build/` — hidden directory for LaTeX intermediates such as `.aux`, `.log`, `.fls`, and SyncTeX files

## Building

VS Code's LaTeX Workshop is configured by [`.vscode/settings.json`](.vscode/settings.json) to keep the final PDF beside the source and send every intermediate file to `.build/`.

For the same behavior from a terminal, run this from the desired revision directory:

```sh
cd Rev6
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. CoverLetter.tex
```

Use `latexmk -C -auxdir=.build -outdir=. Resume.tex` to clean generated outputs. SyncTeX is disabled so it does not place a `.synctex.gz` file beside the PDF. The `.build/` name is used because these files are compiler outputs, not dependencies.


## Aegent Prompt
```
You are working in the root of the Git repository:

Clem085/Resume

Your task is to create a complete new résumé revision named Rev3.

Do not modify Rev0, Rev1, or Rev2. Preserve them as historical snapshots.

FIRST: AUDIT THE REPOSITORY

Read all of the following before editing:

- README.md
- Rev2/Resume.tex
- experience/aegis-power-systems.md
- experience/ece-306.md
- experience/senior-design.md
- experience/teaching-leadership.md
- experience/team-industries.md
- .vscode/settings.json

Also inspect any other Markdown, TeX, PDF, notes, or build configuration files that contain relevant résumé content.

The existing repository describes Rev2 as the current résumé and stores detailed experience source material in the experience/ directory. Treat those Markdown files as source-of-truth context, but improve them where the current descriptions are incomplete, overly generic, or technically imprecise.

REVISION REQUIREMENT

Create:

Rev3/
├── Resume.tex
├── Resume.pdf
└── .build/

Also update README.md so the revision table includes:

Rev3 — Rewritten embedded firmware and hardware-integration résumé emphasizing power conversion, BMS integration, protocol debugging, Embedded Linux, IPMI, senior design, and technical teaching.

Do not call the new folder “Rev2 updated” or overwrite Rev2. This must be Revision 3.

PRIMARY POSITIONING

The résumé should present Connor Savugot as an embedded firmware and hardware-integration engineer with unusual breadth across:

- programmable power electronics,
- custom bidirectional buck-boost converter control,
- BMS and power-management IC integration,
- I2C, CAN, CAN FD, SPI, UART, RS232, and IPMI debugging,
- Embedded Linux,
- Yocto/Arago,
- systemd,
- device trees,
- watchdog services,
- board bring-up,
- component selection,
- firmware tooling,
- technical teaching,
- soldering instruction,
- and system architecture.

The résumé should not read like a list of undergraduate coursework. It should read like an early-career engineer who can move between firmware, schematics, datasheets, Linux, communication protocols, measurement equipment, component research, testing, and technical communication.

SOURCE-OF-TRUTH RULES

Use only facts supported by:

- the repository files,
- explicit user-provided context in this task,
- locally available documentation,
- and source files found in the repository.

Do not invent:

- percentages,
- device counts,
- class averages,
- time savings,
- efficiency gains,
- performance claims,
- production volume,
- project ownership,
- dates,
- titles,
- or outcomes.

If a claim appears valuable but insufficiently supported, add a comment to RESUME_REVIEW.md instead of placing it in the résumé.

Do not expose confidential, proprietary, customer-specific, or export-controlled information. Generalize internal product names and architectures where necessary.

UPDATE THE CONTEXT FILES FIRST

Before creating Rev3, improve the Markdown source files in experience/.

1. experience/aegis-power-systems.md

Expand and clarify the current embedded firmware work.

The file must make clear that PWM was not the project itself. PWM was the control mechanism used to configure custom programmable power supplies built around variable bidirectional buck-boost converter stages.

Correct framing:

- Developed firmware control for custom bidirectional buck-boost power supplies.
- Coordinated 24 physical PWM outputs as twelve A/B pairs across transformer-coupled input and output stages; each A output had configurable period/frequency, duty cycle, and relative phase, while B matched or inverted A.
- Configured both input-side and output-side converter behavior.
- Translated requested input/output voltage settings into coordinated switching behavior.
- Managed timing, duty-cycle relationships, paired channel behavior, feedback, and safe-operating constraints.
- Treated the system as a programmable power-conversion architecture, not as a generic PWM exercise.

Do not write:

- “Created PWM outputs”
- “Worked with PWM”
- “Configured 24 PWM channels” without explaining the power-conversion purpose
- “Used PWM for motor control”

Expand BMS and component work:

- Evaluated multiple battery-management, monitoring, protection, interface, and supporting ICs.
- Compared voltage range, cell support, sensing, protection architecture, balancing, host protocol, package, footprint, tool support, reference designs, sourcing risk, and integration constraints.
- Used datasheets, schematics, reference designs, evaluation hardware, and component availability to determine compatibility.
- Converted component research into firmware and hardware integration plans.
- Distinguished between selecting a part, validating it, bringing it up, and debugging it.

Expand I2C debugging:

- Debugged acknowledgement failures, register access, address selection, timing, pull-ups, open-drain configuration, voltage compatibility, bus state, and shared-bus behavior.
- Correlated logic-analyzer captures with firmware register transactions, schematics, datasheets, and known-good hardware.
- Created focused peripheral test routines.
- Used controlled substitutions, breakout boards, and isolated transactions to determine whether faults were in firmware, wiring, bus configuration, or the device itself.
- Include SMBus only when supported by source files.

Expand CAN/CAN FD work:

- Used SocketCAN, PCAN hardware, known-good nodes, bit-timing analysis, acknowledgement-state testing, DBC interpretation, signal mapping, and frame validation.
- Distinguished physical-layer, timing, configuration, and target-device failures.
- Include FDCAN clock correction and MCU migration work only if supported by available files.

Expand IPMI and platform-management work:

- Characterized IPMI 2.0, IPMB, FRU, sensors, and chassis-management services.
- Separated network reachability, transport, session establishment, authentication, protocol support, addressing, and firmware compatibility.
- Investigated SSH, HTTP, RPC, and management-service interfaces where supported.
- Frame this as embedded platform-management debugging, not generic network scanning.

Expand Embedded Linux work:

- TI AM62-class systems
- Yocto/Arago
- device trees
- systemd services
- watchdogs
- Python/Bash tooling
- boot and service diagnostics
- firmware flashing
- field diagnostics
- automated validation

Keep internship work separate from current full-time engineering work.

2. experience/senior-design.md

Preserve the EV Active Sensor Adapter project, but improve the system-level framing.

Emphasize:

- STMicroelectronics controller
- TI BQ-family battery-monitor/ADC
- external CAN transceivers
- end-to-end architecture
- BMS and power-management integration
- component trade studies
- custom PCB interfaces
- sensing
- telemetry
- subsystem validation
- design reviews
- requirements
- interface specifications
- technical risks
- team coordination

Do not reduce this to a class project. Present it as cross-disciplinary system design and integration.

3. experience/ece-306.md

Keep a clear distinction between:

- Connor’s own MSP430FR2355 vehicle project
- later work as an embedded systems teaching assistant

For the TA work, emphasize:

- firmware and hardware debugging across many student implementations,
- C,
- MSP430FR2355,
- ADC,
- timers,
- interrupts,
- GPIO,
- LCD,
- serial diagnostics,
- custom PCB bring-up,
- soldering,
- toolchain failures,
- wiring issues,
- and teaching systematic debugging.

Do not emphasize motor-control PWM unless needed for the student project. The professional power-conversion PWM work is more important and should not be confused with ECE 306.

4. experience/teaching-leadership.md

Retain:

- embedded systems teaching assistant,
- project-based electronics workshop,
- through-hole and SMT soldering instruction,
- project scoping,
- debugging,
- mentoring,
- design completion,
- and final demonstrations.

Do not include the claim that the class average rose from C+ to A- unless there is direct, verifiable documentation supporting it. If it cannot be verified, move it to RESUME_REVIEW.md as an unconfirmed metric.

5. experience/team-industries.md

Keep concise and factual:

- VBA automation,
- out-of-spec part identification,
- engineering worksheets,
- revision tracking,
- quality data,
- manufacturing collaboration,
- and technical reporting.

CREATE RESUME_REVIEW.md

Create a repository-root file named:

RESUME_REVIEW.md

It should contain:

- major changes made for Rev3,
- claims removed for lack of verification,
- metrics that could strengthen the résumé if confirmed,
- confidentiality concerns,
- assumptions avoided,
- remaining questions,
- and recommendations for role-specific variants.

Include a section titled:

## Facts Requiring User Confirmation

Potential items:

- exact start date and title for current AEGIS role,
- exact number and type of BMS ICs used,
- whether SMBus should be listed,
- whether IPMB, FRU, and sensor access were implemented, validated, or only investigated,
- exact senior-design team size,
- exact TA semesters,
- number of students or lab sections supported,
- whether the class-average improvement is documented,
- exact measurable effect of the flashing automation,
- whether the 24 channels are 24 total PWM channels or 24 paired control channels,
- exact transformer-pair topology,
- which details may be confidential.

REV3 CONTENT PRIORITY

Use approximately this priority:

1. Professional summary
2. Technical skills
3. Current AEGIS embedded firmware role
4. Senior design
5. Prior AEGIS internships
6. Embedded systems TA
7. Electronics workshop leadership
8. TEAM Industries
9. Education

The personal Linux multi-boot/GPU-switching project should not automatically be included.

Evaluate whether it adds a meaningful skill not already shown through:

- Yocto/Arago,
- systemd,
- device trees,
- watchdog services,
- AM62,
- IPMI,
- and embedded Linux tooling.

Include it only if space allows and it adds clear value. If used, present it as:

Linux Hardware-Aware Power Management and Multi-Boot Integration

Possible themes:

- Garuda Linux, Ubuntu, and Windows UEFI multi-boot
- GRUB discovery and boot-priority repair
- systemd services monitoring HDMI state
- enabling the dedicated GPU when HDMI required it
- disabling the dedicated GPU when disconnected
- integrated power-management and boot-reliability problem solving

Do not claim measured battery improvement without evidence.

REV3 SUMMARY

Replace “Objective” with a concise professional summary.

It should establish:

- B.S. Computer Engineering, May 2026
- current embedded firmware engineering experience
- programmable power conversion
- BMS integration
- communication-bus debugging
- Embedded Linux
- hardware/firmware integration
- relocation openness only if still current and space permits

Avoid generic phrases such as:

- seeking an opportunity
- passionate engineer
- hard-working
- team player
- gained experience

SKILLS STRUCTURE

Use categories such as:

Languages:
C, C++, Python, Bash, MATLAB, VBA, Assembly, Verilog

Embedded Platforms:
MSP430FR2355, STM32, dsPIC33, TI TMS320, TI AM62-class ARM systems

Embedded Systems:
FreeRTOS, Embedded Linux, Yocto/Arago, systemd, device trees, watchdogs, bootloaders

Interfaces and Protocols:
I2C, CAN, CAN FD, SPI, UART, RS232, IPMI, IPMB, ADC, GPIO, JTAG

Power and Hardware:
BMS integration, bidirectional buck-boost converters, programmable power supplies, component evaluation, custom PCBs, board bring-up

Tools:
Git, GitLab, Code Composer Studio, STM32CubeIDE, MPLAB X, PlatformIO, KiCad, SocketCAN, PCAN, oscilloscopes, logic analyzers, protocol analyzers

Only include tools and platforms supported by repository evidence.

PROFESSIONAL EXPERIENCE BULLET STANDARD

Current AEGIS role should have no more than five bullets.

Each bullet should demonstrate a coherent engineering workflow.

Suggested themes:

1. Programmable power conversion
   - custom bidirectional buck-boost supplies
   - 24 configurable PWM channels
   - transformer-coupled input/output stages
   - requested voltage settings translated into coordinated control

2. BMS and component integration
   - multiple ICs
   - trade studies
   - electrical and protocol compatibility
   - firmware/hardware planning

3. Protocol debugging
   - I2C, CAN/CAN FD, SPI, UART
   - register transactions
   - analyzer captures
   - schematics
   - known-good hardware
   - focused test routines

4. IPMI and embedded management
   - IPMI 2.0
   - IPMB
   - FRU
   - sensors
   - session/authentication/transport distinction

5. Embedded Linux and tooling
   - AM62
   - Yocto/Arago
   - device trees
   - systemd
   - watchdogs
   - Python/Bash
   - monitoring, flashing, validation, diagnostics

Avoid six or more bullets unless the layout remains clean and readable.

Prior AEGIS internship should have three or four bullets.

Suggested themes:

- secured chroot and restricted SSH CLI
- Python/Bash control utilities
- packetized firmware flashing with checksums and SPI reflashing
- RS232 reverse engineering
- FreeRTOS and serial-interface validation
- relay/load and power-supply test circuitry (Connor did not perform burn-in tests)
- engineering documentation

SENIOR DESIGN BULLET STANDARD

Use three or four bullets.

Emphasize:

- architecture and interfaces,
- ST MCU control, TI BQ battery measurement/ADC, and CAN physical-layer subsystems,
- BMS and component selection,
- custom-PCB power, sensing, and telemetry integration,
- subsystem validation,
- requirements,
- test plans,
- design reviews,
- and team coordination.

TA AND LEADERSHIP

The Embedded Systems Teaching Assistant role should appear under Professional Experience or Technical Leadership.

Use one or two strong bullets.

Possible structure:

- Delivered supplemental instruction and supported MSP430FR2355 firmware, C, ADC sensing, timer/PWM motor control, interrupts, GPIO, LCD/serial integration, and custom-PCB bring-up.
- Diagnosed firmware, wiring, soldering, toolchain, and board-level failures across diverse student implementations while teaching students to isolate faults independently.

The electronics workshop may use one bullet:

- Co-led a two-semester project-based electronics workshop, guiding students from concept through demonstration and teaching through-hole/SMT soldering, safety, debugging, and project completion.

DESIGN REQUIREMENTS

Rev3 should be:

- one page if readable,
- ATS compatible,
- text selectable,
- visually balanced,
- free of decorative sidebars,
- free of progress bars,
- free of skill ratings,
- free of unsupported icons,
- free of overfull hbox warnings where practical,
- and compilable using the repository’s existing LaTeX Workshop configuration.

Use the Rev2 visual style only if it remains readable.

Do not keep the gray banner simply because Rev2 used it. Evaluate whether a clean white header improves readability and space usage.

Do not use unsupported Font Awesome aliases. Prefer plain text or verified icon commands.

BUILD REQUIREMENTS

Create Rev3/Resume.tex.

Compile it using:

cd Rev3
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex

The final build must:

- exit successfully,
- produce Rev3/Resume.pdf,
- produce no fatal errors,
- avoid undefined control sequences,
- avoid missing fonts,
- and avoid obvious text overflow.

Clean stale artifacts before the final build.

README UPDATE

Update README.md so the revision table includes Rev3 and the example terminal build command points to the latest revision:

cd Rev3
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex

FINAL AUDIT

Before finishing, confirm:

- Rev0, Rev1, and Rev2 are unchanged.
- Rev3 exists and compiles.
- Resume.pdf is one page or intentionally two pages.
- Current engineering work dominates the first half.
- The 24-channel power-conversion work is described as programmable bidirectional buck-boost control, not generic PWM.
- BMS research is connected to actual integration decisions.
- I2C debugging shows methodology.
- IPMI work shows protocol-level reasoning.
- Senior design shows system architecture.
- TA work shows technical teaching and troubleshooting.
- Unverified metrics are excluded.
- Confidential details are generalized.
- README.md identifies Rev3 as the newest revision.
- RESUME_REVIEW.md documents uncertainties and recommended follow-up.
```
