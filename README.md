# Connor Savugot Resume

This repository keeps each major résumé design in a separate, self-contained revision folder.

The [`experience/`](experience/) folder is the detailed source library for future résumé variants. Its [index](experience/README.md) covers professional work, senior design, technical teaching, TEAM Industries, MATLAB, controls/autonomy, programming projects, and archive-only background while documenting relevance, attribution, and unresolved facts.

The recovered résumés, cover letters, LaTeX sources, application packets, and supporting files are organized under [`history/`](history/). See the [archive guide](history/README.md) and [evidence inventory](history/INVENTORY.md) before relying on a historical claim; duplicates and conflicted drafts are intentionally preserved.

Current attribution rules supersede wording in older revisions and archived prompts:

- Active senior-design firmware uses an STM32G474, BQ79616 battery monitor, ten ADC thermistor channels, UART, and extended-identifier CAN telemetry in a timer-assisted service loop.
- The STM32G474/BQ79616 EV sensor-adapter work belongs to NC State senior design; separate professional smart-battery CAN interface work belongs to AEGIS. MSP430FR2355 belongs to ECE 306.
- Connor's current AEGIS title is Embedded Firmware Engineer beginning May 2026.
- Current professional work includes dsPIC33CK firmware, VITA 46.11 Tier 2 VPX/IPMI management, data-driven ADC scaling/filter selection using MATLAB/CAN captures and embedded C, and TI AM62 embedded Linux integration.
- Name the supported TI Linux work directly instead of using the broader label “BSP.”

## Revisions

| Revision | Description |
| --- | --- |
| [`Rev0/`](Rev0/) | Reconstructed November 2024 résumé using the original Source Sans layout, gray contact banner, icon links, ruled headings, and legacy content. `.build/legacy-reference.pdf` is the uploaded PDF used to verify the reconstruction. |
| [`Rev1/`](Rev1/) | Compact one-page embedded-firmware résumé created before the visual redesign. |
| [`Rev2/`](Rev2/) | Previous content presented in the Rev0 visual style, with expanded AEGIS, BMS, senior-design, soldering-instructor, and teaching-assistant experience. |
| [`Rev3/`](Rev3/) | Rewritten embedded-firmware and hardware-integration résumé emphasizing power conversion, BMS integration, protocol debugging, embedded Linux, IPMI, senior design, and technical teaching. |
| [`Rev4/`](Rev4/) | General full-time embedded-firmware résumé using the reconciled 12-pair/24-output power-control architecture, end-to-end engineering workflows, and a matching adaptable cover letter. |
| [`Rev5/`](Rev5/) | Linux-forward embedded-firmware résumé and blanket cover letter with the corrected AEGIS timeline, BMS confined to Senior Design, TI Yocto/Arago work, Docker, power-system integration, and the connected PIC32/TMS320 update workflow. |
| [`Rev6/`](Rev6/) | Low-level-firmware-first résumé and cover letter emphasizing dsPIC33CK, PIC32/FreeRTOS, bare-metal TMS320 DSP control, communication interfaces, VPX/IPMI, and board bring-up. |
| [`Rev7/`](Rev7/) | Qualcomm Power and Limits targeted résumé emphasizing real-time C/C++, TMS320 power-conversion control, PIC32/FreeRTOS processor partitioning, JTAG-driven bring-up, execution analysis, formal verification, and Python tooling/ML. |
| [`Rev8/`](Rev8/) | General low-level embedded-firmware résumé adding professional ADC scaling, embedded-C rolling-average/EMA selection, MATLAB/CAN analysis, distributed firmware-team collaboration, MOSFET modeling, and academic MATLAB machine learning. |
| [`Rev9/`](Rev9/) | Aditi Turf & Compact Utility targeted résumé prioritizing professional MATLAB/CAN filter analysis, academic MATLAB dynamic-system analysis, embedded C, FreeRTOS, CAN/J1939, robotics PID, Lustre, CARLA, requirements, and validation. |

[Rev10-EE](Specialized/Rev10-EE/) is the newest résumé revision, emphasizing embedded hardware integration, production programming, and manufacturing automation.

## Revision Layout

Each revision root contains:

- `Resume.tex` — self-contained LaTeX source, including contact information
- `Resume.pdf` — compiled résumé
- `CoverLetter.tex` and `CoverLetter.pdf` — matching cover-letter source and PDF when present
- `.build/` — hidden compiler outputs and validation artifacts

## Building

VS Code's LaTeX Workshop is configured by [`.vscode/settings.json`](.vscode/settings.json) to keep the final PDF beside the source and send intermediate files to `.build/`.

To compile Rev9 from a terminal:

```sh
cd Rev9
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

Use `latexmk -C -auxdir=.build -outdir=. Resume.tex` to clean generated outputs. SyncTeX is disabled so it does not place a `.synctex.gz` file beside the PDF. `.build/` is used because these are compiler outputs, not dependencies.
