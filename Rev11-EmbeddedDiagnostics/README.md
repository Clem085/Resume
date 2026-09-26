# Rev11 — Snap-on Sr. Embedded Software Engineer

Target: Snap-on Diagnostics, San Jose, CA; Job ID **2026-20708**. Based on Rev10 and the experience reference library, using the job description supplied by Connor on September 20, 2026. Listing availability was not independently checked.

## Files

- `Resume.tex` — tailored one-page source
- `Resume.pdf` — compiled application copy
- `info.md` — source mapping, significant gaps, and claim boundaries
- `.build/` — build outputs

## Selection

Emphasizes C/C++, real-time converter firmware, PIC32/FreeRTOS update coordination, RS-232 protocol reverse engineering, CAN/Ethernet troubleshooting, TI embedded Linux, STM32 sensing/state machines/diagnostics, validation, and technical communication. Includes academic real-time C/POSIX work and concrete C++ simulators.

Retains a compact TEAM inspection-tool bullet. Omits ATP, tooling inventory, maze solver, fundraising, and detailed PCB review to make space for firmware and protocols. These remain valid source experience. Retains Connor's preferred production-flasher wording and general senior-design CAN integration wording.

The title remains Embedded Firmware Engineer; the résumé does not claim senior status, three years of professional firmware experience, or automotive diagnostic-product ownership. No relocation commitment is assumed. Rev10 is unchanged.

## Build

From this directory:

```sh
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```
