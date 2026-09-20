# Rev10 — Embedded Hardware Integration and Production Engineering

Rev10 emphasizes embedded firmware, board bring-up, hardware/software troubleshooting, production firmware programming, manufacturing-data automation, and STM32 senior-design work.

The blue 2024 résumé is a visual reference only: use its color, spacing, and visual styling. Rev10's existing content and plain writing style remain the baseline; do not import the template's wording, experience, or project selection.

## Changes

- Replaced the copied Rev8 profile, metadata, and MATLAB-heavy selection with electrical/embedded integration experience.
- Added TI C2000 TMS320F28379D C++ serial-flasher customization and CCS build/image documentation, separately from the C++/Python/PIC32 updater.
- Added KiCad schematic interpretation, PCB review in KiCad/P-CAD/Altium, and production diagnostic tools. The smart-battery interface-board bullet was removed at Connor's request.
- Restored TEAM Industries inspection parsing/tolerance automation, the 17,000+ entry entire plant tooling where-used list, and included SQL/VBA/Access/Excel ATP automation under the AEGIS internships.
- Placed ATP manufacturing automation under AEGIS internship experience. Projects retain the STM32 sensor adapter, C++ maze solver, and C++ microarchitecture simulators.
- Applied blue name and section rules, triangular bullets, and more section spacing while retaining separate AEGIS role titles and dates.
- Tailored skills and wording to the Snap-on Electrical Engineer role, emphasizing manufacturing automation, production support, C/C++, SQL/VBA/Access data tools, Altium review, sensor and PWM experience, procedures, and cross-layer troubleshooting without claiming C#, SQL Server/MySQL, Creo, PLC, or production-equipment design experience.
- Added IEEE leadership through OPS2, a ten-week applied electronics course designed to close gaps between theory and hands-on work, and the ECE 306 parts program that raised $10,000 in two weeks while lowering student costs.
- Current-role bullets use present tense; completed roles and projects use past tense.
- Retained MCU power-control firmware, Embedded Linux integration, senior-design hardware/firmware work, and embedded-systems teaching.

## Attribution

The C++ serial flasher is confirmed as summer 2025 and sits under the combined AEGIS internships. ATP automation belongs to AEGIS (corrected September 19, 2026); it is confirmed as summer 2024 Computer Science Internship work (latest correction, superseding the earlier 2025 assignment) and appears once under the combined AEGIS internships. The professional battery interface is separate from NC State senior design. PCB review does not imply sole PCB-layout ownership; no unreported performance metrics or completed production release are claimed.

## Files and Build

- `Resume.tex` — current résumé source
- `Resume.pdf` — compiled résumé
- `info.md` — source brief and reconciliation notes
- `.build/` — local build/validation outputs

```sh
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

## Supporting Records

- [AEGIS](../experience/aegis-power-systems.md)
- [Manufacturing ATP automation](../experience/manufacturing-test-automation.md)
- [TEAM Industries](../experience/team-industries.md)
- [Senior design](../experience/senior-design.md)
- [History update](../history/INVENTORY.md#september-15-2026-experience-update)

## Final Source Reconciliation — September 19, 2026

The current source is `Rev10-EE/Resume.tex` at the repository root. It uses the corrected maze wording (correctness and iteration counts), the sensing/state-machine/diagnostics senior-design bullet with general CAN integration, and one ATP bullet under AEGIS internships. The [experience index](../experience/README.md#creating-new-revisions-from-rev10--september-19-2026) records the source facts and boundaries for future revisions. Older review suggestions and archived paths are not authoritative when they conflict with these corrections.

## Reference-Only Summer 2024 Correction

The latest explicit clarification and the July 31, 2024 internship presentation establish SCB301 Linux CLI work, independent KiCad reference-design review (Grant authored the revision), ATP Access/VBA/Excel automation, and collaborative programmable-load/relay burn-in fixture proof-of-concept work as summer 2024. See [AEGIS](../experience/aegis-power-systems.md) for technical detail, source distinctions, and outcome boundaries. The 2025 serial flasher and established full-time work retain their dates. This update changes reference Markdown only; it does not update or validate résumé TeX/PDF wording.
