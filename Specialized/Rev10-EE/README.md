# Rev10 — Embedded Hardware Integration and Production Engineering

Rev10 emphasizes embedded firmware, board bring-up, hardware/software troubleshooting, production firmware programming, manufacturing-data automation, and STM32 senior-design work.

The blue 2024 résumé is a visual reference only: use its color, spacing, and visual styling. Rev10's existing content and plain writing style remain the baseline; do not import the template's wording, experience, or project selection.

## Changes

- Replaced the copied Rev8 profile, metadata, and MATLAB-heavy selection with electrical/embedded integration experience.
- Added TI C2000 TMS320F28379D C++ serial-flasher customization and CCS build/image documentation, separately from the C++/Python/PIC32 updater.
- Added KiCad schematic interpretation, PCB review in KiCad/P-CAD/Altium, and production diagnostic tools. The smart-battery interface-board bullet was removed at Connor's request.
- Restored TEAM Industries inspection parsing/tolerance automation, the 17,000+ entry Inrite plant tooling where-used list, and the SQL/VBA/Access/Excel ATP project.
- Kept the manufacturing automation and STM32 sensor-adapter projects from the pre-styling revision; removed the added C++ simulator entry.
- Applied blue name and section rules, triangular bullets, and more section spacing while retaining separate AEGIS role titles and dates.
- Retained MCU power-control firmware, Embedded Linux integration, senior-design hardware/firmware work, and embedded-systems teaching.

## Attribution

The C++ production utility and other engineering tools are grouped at AEGIS employer level because exact role dates are unconfirmed. ATP automation is attributed to TEAM Industries; its exact internship year remains unconfirmed. The professional battery interface is separate from NC State senior design. PCB review does not imply sole PCB-layout ownership; no unreported performance metrics or completed production release are claimed.

## Files and Build

- `Resume.tex` — current résumé source
- `Resume.pdf` — compiled résumé
- `info.md` — source brief and reconciliation notes
- `.build/` — local build/validation outputs

```sh
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

## Supporting Records

- [AEGIS](../../experience/aegis-power-systems.md)
- [Manufacturing ATP automation](../../experience/manufacturing-test-automation.md)
- [TEAM Industries](../../experience/team-industries.md)
- [Senior design](../../experience/senior-design.md)
- [History update](../../history/INVENTORY.md#september-15-2026-experience-update)
