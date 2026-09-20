# Archive Inventory and Evidence Audit

## Scope

The recovered import originally contained 311 files in 41 directories (about 42 MiB). It included 53 PDFs, 11 Word documents, 16 ZIP archives, and four saved career-page bundles. It was audited together with the 36 documents already held in the former `experience/history/` directory.

After preserving the originals, extracting the LaTeX archives for inspection, and adding two MATLAB coursework artifacts in August 2026, `history/` contains 413 archived payload files plus this inventory and two archive README files (416 files total, about 53 MiB), including:

- 81 PDFs
- 21 Word documents
- 16 original ZIP archives
- 40 extracted TeX files, representing 33 distinct text hashes
- 255 files belonging to saved pages or image assets, including the extracted signature assets

Every distinct authored resume, cover letter, application essay, extracted TeX body, and newly added MATLAB assignment was read. Saved webpage scripts and assets were classified but were not treated as evidence of Connor's experience.

The file accounting reconciles exactly: 311 newly recovered originals + 36 earlier archived documents + two later MATLAB assignments = 349 originals; extracting 64 ZIP members produced 413 payload files; this inventory and two archive README files bring the directory total to 416. No original file was discarded.

## Recovered-Import Classification

The 53 PDF-named files comprised 23 resumes, 23 authored cover letters, four transcripts, two unrelated/generated templates, and one Word document carrying an incorrect `.pdf` extension. The 11 `.docx` files comprised five resumes, two authored cover letters, one NVIDIA application questionnaire, and three unrelated or blank templates. The 16 ZIPs comprised three resume-source archives, twelve cover-letter-source archives, and one generic cover-letter template.

## Exact-Byte Duplicate Groups

Duplicates are intentionally retained when they preserve application context. Git stores byte-identical files as one blob internally, so keeping logical copies does not duplicate tracked blob content.

- The two AEGIS cover-letter PDFs are identical.
- The M.C. Dean and Northrop Grumman resume PDFs are identical.
- The generic 2025-summer, Lenovo, and Schneider Electric resume PDFs are identical.
- The Dell, Intel, NVIDIA, Qualcomm, and one undated resume PDFs are identical.
- The two AEGIS resume PDFs are identical.
- The NREIP and SSEP NC State transcripts are identical.
- The black layout variant and Shield AI one-page resume are identical.

Files with matching extracted text but different bytes were kept because typography, colors, metadata, or layout may differ. Saved webpage assets were never deduplicated because doing so could break relative links.

## Evidence Strength

- **Direct:** explicitly supplied by Connor in the current project. Preserve it unless a newer correction supersedes it.
- **Corroborated:** repeated in multiple contemporaneous documents or supported by an official record.
- **Archive-derived / confirm:** useful detail found in only one draft or cover letter. Keep it in the experience library, but verify it before publication.
- **Conflicted:** two sources disagree or a package combines mismatched body/metadata. Do not select either version silently.
- **Excluded:** templates, employer requirements, aspirational role-alignment language, private narrative, and unrelated third-party material.

## High-Value Facts Recovered

- An official Tri-County record supports an Associate in Arts awarded August 1, 2023, with a 4.0 GPA and “Graduated Top of Class.” The record remains private; only the normalized fact belongs in the experience library.
- Contemporaneous 2024 files support the AEGIS title `Computer Science Intern`, May–August 2024, plus the restricted SSH/Embedded Linux interface, RS232, CAN, Python, and Bash work.
- Newer resume source describes a PIC32/TMS320 firmware-update architecture, J1939, a C++ flasher, a Python TCP/IP sender, checksum/chunking logic, SPI-flash image storage, a golden image, and extensive Git documentation. Connor confirmed that these were connected stages of one product's update and boot-control workflow, not one monolithic program.
- IEEE drafts add the ECE 306 parts-distribution program, a ten-week Open Project Space 2 course designed to pair theory with hands-on electronics, PlatformIO/VS Code/GitHub, and $10,000 raised in two weeks while lowering student costs. Connor corrected and approved the fundraising result for résumé use on September 16, 2026.
- ECE 306 sources add two programmable buttons, a rotary selector, mode selection, and software debouncing.
- Project sources add Qiskit/Aer Grover search, Verilog/AMD Vivado work, and real-time scheduling theory. An older Kogge--Stone claim and lone VHDL claim are not supported by the currently retained ECE 310 source, which instead supports a structural Wallace-tree multiplier and Verilog datapaths.
- Added MATLAB artifacts support CNN training/evaluation, SqueezeNet transfer learning, PCA/KLT, least-squares visualization, and measured MOSFET data analysis with numerical fitting and model comparison.

## Conflicts to Resolve Before Publication

- Whether a separate artifact exists for the older Kogge--Stone or VHDL claims; current ECE 310 artifacts support Verilog and a Wallace-tree multiplier instead.
- Multiple historical NC State GPA values; omit GPA without a current transcript.
- Whether OPS2 leadership was sole lead, co-lead, or one of two lead instructors.
- Whether the C+-to-A- teaching outcome can be documented and publicly attributed.

## Resolved Source Questions

- The twelve-versus-24 PWM discrepancy is resolved: the system had 24 physical outputs arranged as twelve A/B pairs. Each A output had independently configurable duty cycle, period/frequency, and relative phase; its B output could only match or exactly invert the paired A waveform.
- The AEGIS timeline is resolved: Computer Science Intern from May--August 2024, Embedded Systems Intern from May--August 2025, and Embedded Firmware Engineer beginning May 2026.
- The firmware-update descriptions are compatible: the C++ HEX-file programmer, Python/TCP transfer, PIC32 SPI-flash/golden-image handling, and TMS320 UART programming were multiple connected stages for one product.
- The STM32G474/BQ79616 EV sensor-adapter work belongs to NC State senior design; separate professional smart-battery CAN interface work belongs to AEGIS. MSP430FR2355 belongs to ECE 306.
- The NC State B.S. in Computer Engineering was completed in May 2026.
- ECE 306 support ran Spring 2025, Fall 2025, and Spring 2026: two semesters were unofficial support at about 10 hours per week and one was an official TA appointment at about 20 hours per week. The supplied order suggests the official appointment was Spring 2026, but that mapping remains to be explicitly confirmed.
- Public-project review resolves Senior Design's active firmware to STM32G474, BQ79616, ten ADC thermistor channels, UART, and extended-identifier CAN telemetry in a timer-assisted service loop. The stale root README's FreeRTOS/DMA plan is not final-system evidence.

## Privacy and Disclosure

All twelve LaTeX cover-letter ZIPs contain two embedded handwritten-signature images as well as contact information. Academic records include student identifiers, birth information, address data, and grade histories. Some older resumes contain street addresses and GPAs, and saved career pages may retain tracking identifiers. A M.C. Dean draft includes personal health/GPA narrative. These sources are retained for local history, not for publication.

AEGIS descriptions also require a disclosure review before using customer names, internal identifiers, detailed power topology, raw frames, register maps, schematics, or product-specific behavior.

## September 15, 2026 Experience Update

Connor directly supplied additional project details for [Rev10-EE](../Rev10-EE/Resume.tex). These are new source statements, not recovered archive artifacts; historical originals and the recovered-import counts above remain unchanged.

- [AEGIS experience](../experience/aegis-power-systems.md): added C++ customization of TI `serial_flasher.exe` for TMS320F28379D, removal of unused device/CPU2/dual-boot options, production programming for non-firmware engineers, and CCS build/image-generation instructions. This is not established as the same tool as the archived C++ HEX-file programmer or PIC32 golden-image workflow.
- Clarified professional smart-battery CAN interface work versus the separate senior-design battery-monitor project; expanded board-review tools, datasheet/electrical-specification use, CAN configuration diagnostics, full-system troubleshooting, and reusable engineering/production procedures.
- [ATP automation](../experience/manufacturing-test-automation.md): newly recorded SQL/VBA/Access/Excel test-data parsing, validation, historical-record retrieval, and automated database entry. The September 16 TEAM attribution and later AEGIS 2025 attribution are superseded: the July 31, 2024 presentation and latest explicit clarification establish AEGIS summer 2024. See the current source for Access forms, VBA validation/parsing/upload, and remaining completion limits.
- [TEAM Industries](../experience/team-industries.md): expanded the existing tolerance-checker record with directly confirmed inspection-data parsing and automatic part verification, plus a 17,000+ entry entire plant tooling where-used list using custom lookup formulas and data validation. Kept the where-used list and tolerance checker distinct from ATP automation.
- Exact dates for the C++ production tool and network-discovery utilities remain unconfirmed; Rev10 groups them at AEGIS employer level.
