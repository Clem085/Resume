# Rev 8 — Low-Level Embedded Firmware and MATLAB Data Analysis

Rev8 keeps low-level embedded firmware as Connor's primary identity while adding verified professional and academic MATLAB experience. The one-page résumé now connects embedded-C filtering with CAN-data parsing, ADC scaling, data-driven rolling-average/EMA selection, electrical modeling, machine learning, and distributed engineering teamwork.

## Files

- `Resume.tex` — self-contained LaTeX source
- `Resume.pdf` — compiled application résumé
- `.build/` — LaTeX intermediates and local validation artifacts

Build from this directory with:

```sh
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

## Rev7 to Rev8 Changes

1. Added MATLAB as a primary working language without displacing embedded C/C++.
2. Added the professional ADC-filter workflow: parsed captured CAN telemetry in MATLAB, determined per-channel scaling factors, compared several functions, and selected rolling-average and EMA approaches using steady-input variation and time to follow large changes.
3. Added engineering standups and collaboration with a geographically distributed firmware team.
4. Added measured MOSFET characterization in MATLAB using CSV data, numerical gradients, curve fits, extracted parameters, and measured-versus-modeled plots.
5. Added MATLAB CNN training, SqueezeNet transfer learning, and PCA/KLT image analysis from a retained Spring 2025 assignment.
6. Compressed the real-time/formal-methods project while preserving its strongest scheduling, tracing, and model-checking evidence.
7. Updated Senior Design from family-level wording to the active-source STM32G474/BQ79616 architecture, ten-channel thermistor acquisition, UART/CAN integration, and subsystem-isolation work.
8. Retained the low-level dsPIC33CK, PIC32/FreeRTOS, TMS320 power-control, VPX/IPMI, update/recovery, and ECE 306 evidence from Rev7.

## Claim Boundaries

- The professional MATLAB workflow parsed offline text captures of CAN telemetry; the source does not establish direct MATLAB access to a live CAN bus.
- Rolling-average implementation and selection of rolling-average and EMA approaches are confirmed. Other candidate functions, window/EMA parameters, sample cadence, final deployment, calibration results, and quantitative improvements are not published because those details are not yet recorded.
- The MCP3428 architecture is multiplexed and intended for slow telemetry; Rev8 does not claim simultaneous sampling, fast protection/control feedback, true-RMS measurement, or production calibration accuracy.
- The MOSFET report demonstrates data handling, fitting, plotting, and model comparison; some report code contains assumptions or apparent copy errors, so Rev8 does not claim validated parameter-extraction accuracy.
- The CNN and SqueezeNet results are academic assignment results. SqueezeNet used transfer learning, PCA/KLT relied on supplied helper routines, and no embedded or production ML deployment is claimed.
- The Spring 2025 MATLAB machine-learning PDF does not identify its course number internally, so Rev8 uses `Selected Coursework` rather than asserting ECE 301.
- The active senior-design source uses a timer-assisted service loop. Rev8 does not repeat the repository root README's stale FreeRTOS/DMA plan or imply sole ownership of the team's CAN subsystem.

## Supporting Records

- [`../experience/matlab-data-analysis.md`](../experience/matlab-data-analysis.md) — detailed MATLAB evidence and résumé-selection guidance
- [`../experience/adc-monitoring-card.md`](../experience/adc-monitoring-card.md) — ADC architecture, range/scale derivations, calibration, embedded-C filter code, and claim boundaries
- [`../experience/aegis-power-systems.md`](../experience/aegis-power-systems.md) — professional role attribution and engineering-workflow details
- [`../experience/personal-projects.md`](../experience/personal-projects.md) — expanded programming-project inventory
- [`../experience/github-projects.md`](../experience/github-projects.md) — public-repository audit and authorship boundaries
- [`../history/academic-projects/README.md`](../history/academic-projects/README.md) — retained assignment provenance
