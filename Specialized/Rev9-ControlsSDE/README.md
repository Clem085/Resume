# Rev 9 — Aditi Turf & Compact Utility Software Engineer I

Rev9 is a one-page, ATS-readable résumé tailored to the Cary, North Carolina embedded-controls contract shared by Aditi Consulting. It presents Connor as an embedded firmware engineer with directly relevant MATLAB, controls, CAN/J1939, FreeRTOS, requirements, integration, and validation experience.

## Files

- `Resume.tex` — self-contained LaTeX source
- `Resume.pdf` — compiled application résumé
- `.build/` — LaTeX compiler outputs and local validation artifacts

Build from this directory with:

```sh
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

## Targeting Decisions

Rev9 deliberately prioritizes the experience that maps most directly to this posting:

1. Professional MATLAB analysis of captured CAN telemetry, ADC scaling, digital-filter selection, and embedded-C implementation.
2. Artifact-backed MATLAB signal, transfer-function, and first-/second-order dynamic-response analysis.
3. Embedded C, FreeRTOS, CAN/J1939, peripheral integration, and TMS320 real-time power control from AEGIS.
4. Datasheet-, schematic-, and instrument-driven dsPIC33CK bring-up and fault isolation.
5. Python robotics controls, deterministic Lustre PID control, and CARLA longitudinal-control integration and evaluation.
6. Senior-design requirements, interface specifications, design reviews, and host-side/subsystem testing.
7. TEAM Industries tolerance-validation automation and manufacturing collaboration.

Lower-relevance material was removed before cutting any of those themes. Rev9 therefore omits VPX/IPMI, detailed Yocto/kernel work, the full firmware-update architecture, teaching, MATLAB machine learning, MOSFET characterization, and unrelated programming projects. Embedded Linux remains once as supporting system-integration breadth rather than the primary identity.

## Requirement Coverage

| Posting theme | Evidence used in Rev9 |
| --- | --- |
| Embedded C/C++ | Current dsPIC33CK firmware; PIC32/FreeRTOS; bare-metal TMS320 control; C++ update tooling |
| MATLAB and engineering analysis | Professional CAN/ADC filter analysis plus academic signal, transfer-function, and transient-response modeling |
| Control design and tuning | Robotics PD/PID loops, Lustre cruise control, and CARLA longitudinal control |
| CAN/J1939 | Professional PIC32/FreeRTOS communication and current CAN-connected power-system integration |
| Embedded OS and hardware integration | FreeRTOS, supporting Embedded Linux work, peripheral/HAL bring-up, and multiprocessor integration |
| Requirements and testing | Senior-design requirements/interfaces, staged integration, and seven passing host-side tests |
| Diagnostics and lab tools | JTAG, Code Composer Studio, oscilloscopes, logic/protocol analyzers, schematics, and datasheets |
| Team and manufacturing context | Distributed-firmware-team standups plus two TEAM Industries internships |

## Claim Boundaries

- The professional MATLAB workflow parsed captured CAN text output; Rev9 does not imply that MATLAB directly acquired a live CAN bus.
- Rolling-average and EMA approaches were selected from multiple candidates. The rolling-sum average is the filter explicitly stated as implemented in embedded C; no quantitative performance improvement is claimed.
- No verified experience currently supports Simulink, Stateflow, Model-in-the-Loop, or tool-specific Model-Based Design, so those posting keywords are deliberately absent.
- The robotics, Lustre, and CARLA work is academic. The CARLA work was completed on a three-person team and is not presented as production autonomous-driving experience.
- Rev9 does not claim unsupported Stateflow, Agile/Scrum, continuous integration, LIN, automotive Ethernet, hydraulic-system diagnosis, production vehicle deployment, or code-review ownership.
- The posting says it prefers mid-career candidates and no recent graduates. Because the recruiter contacted Connor directly, Rev9 keeps the May 2026 graduation date and foregrounds the complete 2021–present engineering timeline rather than obscuring either fact.

## Supporting Records

- [`../experience/controls-and-autonomy.md`](../experience/controls-and-autonomy.md) — robotics, Lustre, CARLA, and controls claim boundaries
- [`../experience/matlab-data-analysis.md`](../experience/matlab-data-analysis.md) — professional and academic MATLAB evidence
- [`../experience/adc-monitoring-card.md`](../experience/adc-monitoring-card.md) — ADC scaling and filter-selection details
- [`../experience/aegis-power-systems.md`](../experience/aegis-power-systems.md) — professional role attribution and firmware workflows
- [`../experience/senior-design.md`](../experience/senior-design.md) — requirements, hardware/software architecture, and validation
- [`../experience/team-industries.md`](../experience/team-industries.md) — tolerance validation and manufacturing experience
