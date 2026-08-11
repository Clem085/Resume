# Archive Inventory and Evidence Audit

## Scope

The recovered import originally contained 311 files in 41 directories (about 42 MiB). It included 53 PDFs, 11 Word documents, 16 ZIP archives, and four saved career-page bundles. It was audited together with the 36 documents already held in the former `experience/history/` directory.

After preserving the originals and extracting the LaTeX archives for inspection, `history/` contains 411 archived payload files plus this inventory and the archive README (413 files total, about 47 MiB), including:

- 79 PDFs
- 21 Word documents
- 16 original ZIP archives
- 40 extracted TeX files, representing 33 distinct text hashes
- 255 files belonging to saved pages or image assets, including the extracted signature assets

Every distinct authored resume, cover letter, application essay, and extracted TeX body was read. Saved webpage scripts and assets were classified but were not treated as evidence of Connor's experience.

The file accounting reconciles exactly: 311 newly recovered originals + 36 earlier archived documents = 347 originals; extracting 64 ZIP members produced 411 payload files; this inventory and the archive README bring the directory total to 413. No original file was discarded.

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
- IEEE drafts add the ECE 306 parts-distribution program, a ten-week Open Project Space 2 sequence, PlatformIO/VS Code/GitHub, and a reported $2,000 raised in two weeks. Titles, dates, and the metric need confirmation.
- ECE 306 sources add two programmable buttons, a rotary selector, mode selection, and software debouncing.
- Project sources add Qiskit/Aer Grover search, Verilog/AMD Vivado work, a Kogge–Stone adder, and real-time scheduling theory. The lone VHDL claim conflicts with the repeated Verilog record.

## Conflicts to Resolve Before Publication

- Verilog in repeated project records versus one VHDL cover-letter claim.
- Multiple historical NC State GPA values; omit GPA without a current transcript.
- Whether OPS2 leadership was sole lead, co-lead, or one of two lead instructors.
- Whether the reported $2,000/two-week IEEE result and C+-to-A- teaching outcome can be documented and publicly attributed.

## Resolved Source Questions

- The twelve-versus-24 PWM discrepancy is resolved: the system had 24 physical outputs arranged as twelve A/B pairs. Each A output had independently configurable duty cycle, period/frequency, and relative phase; its B output could only match or exactly invert the paired A waveform.
- The AEGIS timeline is resolved: Computer Science Intern from May--August 2024, Embedded Systems Intern from May--August 2025, and Embedded Firmware Engineer beginning May 2026.
- The firmware-update descriptions are compatible: the C++ HEX-file programmer, Python/TCP transfer, PIC32 SPI-flash/golden-image handling, and TMS320 UART programming were multiple connected stages for one product.
- BMS work belongs to the NC State senior-design project and must not be attributed to AEGIS employment.
- The NC State B.S. in Computer Engineering was completed in May 2026.
- ECE 306 support ran Spring 2025, Fall 2025, and Spring 2026: two semesters were unofficial support at about 10 hours per week and one was an official TA appointment at about 20 hours per week. The supplied order suggests the official appointment was Spring 2026, but that mapping remains to be explicitly confirmed.

## Privacy and Disclosure

All twelve LaTeX cover-letter ZIPs contain two embedded handwritten-signature images as well as contact information. Academic records include student identifiers, birth information, address data, and grade histories. Some older resumes contain street addresses and GPAs, and saved career pages may retain tracking identifiers. A M.C. Dean draft includes personal health/GPA narrative. These sources are retained for local history, not for publication.

AEGIS descriptions also require a disclosure review before using customer names, internal identifiers, detailed power topology, raw frames, register maps, schematics, or product-specific behavior.
