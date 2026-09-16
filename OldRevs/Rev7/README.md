# Rev 7 — Qualcomm Power & Limits Software Engineer

This revision targets Qualcomm Technologies' Power and Limits Software Engineer role. It is a one-page, ATS-safe résumé built around verified low-level firmware, real-time power control, multiprocessor integration, hardware-aware debugging, execution analysis, and engineering tooling.

## Files

- `Resume.tex` — self-contained LaTeX source
- `Resume.pdf` — compiled application résumé
- `.build/` — LaTeX compiler outputs and local validation artifacts

Build from this directory with:

```sh
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

## Experience Retrieval Summary

The Qualcomm version uses several useful experiences that were absent or underrepresented in Rev6:

- **Real-time systems coursework, Spring 2026:** Connor's Git history and project artifacts support periodic POSIX-thread work in C using CPU affinity, absolute-time releases, priority-inheritance mutexes, timestamp traces, execution plots, and EDF/rate/deadline-monotonic schedulability analysis.
- **Formal verification:** Lustre models, bounded model checking, and counterexample-guided corrections provide concrete validation evidence adjacent to Qualcomm's pre-silicon and robust-software interests without claiming pre-silicon silicon sign-off.
- **C++ performance analysis:** the maze-search project implemented BFS, DFS, and greedy best-first search and compared runtime and memory behavior across configurations.
- **Meaningful supporting machine learning:** Connor-authored commits in the mentor-matching independent-study repository establish a Python pipeline using sentence-transformer embeddings, configurable weighted scoring, CSV ingestion, persistent constraints/state, and explainable output. Rev7 presents this as academic/supporting ML, not embedded ML or power-management ML.
- **Deeper low-level debugging evidence:** the current dsPIC33CK work is now explicitly tied to reference manuals, schematics, JTAG, register/timing/configuration fault isolation, and bench instruments.
- **Clear processor responsibility split:** Rev7 makes the PIC32/FreeRTOS communication-and-update role distinct from the bare-metal TMS320 DSP real-time power-control role.

## Qualcomm Requirement Coverage

| Qualcomm requirement | Evidence used in Rev7 | Strength |
| --- | --- | --- |
| Embedded C/C++ | dsPIC33CK low-level C; TMS320 bare-metal C; PIC32/FreeRTOS; C++ update CLI | Strong |
| RTOS | Professional PIC32 firmware running FreeRTOS; academic POSIX real-time scheduling | Strong |
| Real-time debugging / JTAG | JTAG, register inspection, Code Composer Studio, scopes, logic analyzers, peripheral-by-peripheral bring-up | Strong |
| Power software | DSP-controlled bidirectional buck--boost supplies; 12 PWM A/B pairs; battery/CAN power-system integration; senior-design battery monitoring | Strong |
| Constrained systems | 16-bit dsPIC33CK, PIC32/FreeRTOS, bare-metal DSP, resource-constrained TI Yocto/Arago target | Strong |
| Python | TCP firmware sender, restricted-system commands, NLP matching pipeline | Strong |
| Computer architecture | Two-processor responsibility partition, RT scheduling work, MCU/DSP platform breadth | Moderate |
| Arm | TI AM62 Arm-based SoC on the Embedded Linux side; no claimed bare-metal Arm or Arm-assembly work | Limited |
| Compilers / linkers | GCC/Make and MCU toolchain/device-pack configuration; no custom linker-script or startup-code claim | Limited |
| SoC interaction | TI AM62 SoC/HLOS integration plus a separate PIC32/TMS320 multiprocessor product | Moderate |
| Profiling / optimization | Periodic-task timing traces and execution plots; academic C++ runtime/memory comparisons; no production power/CPU profiling metrics | Moderate |
| Hardware guides / drivers | Datasheet, reference-manual, schematic, register/HAL-level peripheral bring-up, plus VITA 46.11/IPMI implementation | Strong / Moderate |
| Machine learning | Python sentence-transformer mentor matching with configurable scoring and explainable output | Moderate |
| Git / version control | Git/GitLab across professional firmware workflows and Git-backed academic projects | Strong |

## Rev6 to Rev7 Strategic Changes

1. Repositioned the profile around real-time power/control software rather than general embedded firmware breadth.
2. Elevated bare-metal TMS320 power-conversion control to the first internship accomplishment.
3. Made the PIC32/FreeRTOS and TMS320 responsibility partition explicit without calling the system multicore or claiming ownership of the architecture decision.
4. Added JTAG, reference-manual, register, timing, compiler/toolchain, and bench-debug evidence throughout the top half.
5. Compressed Embedded Linux into a supporting SoC/HLOS integration theme while preserving TI AM62, Yocto/Arago, device-tree, kernel, and watchdog evidence.
6. Added verified real-time scheduling, execution instrumentation, and formal-verification coursework discovered outside the résumé archive.
7. Added the C++ runtime/memory comparison as the most honest available evidence for performance analysis.
8. Added meaningful Python/NLP work while avoiding claims of embedded ML or Qualcomm-style power-model training.
9. Retained one concise ECE 306 teaching entry for technical communication and broad debugging experience; removed TEAM, OPS2, and soldering-workshop material before cutting higher-relevance firmware evidence.
10. Reorganized skills around Qualcomm's language, RTOS, processor, debug/build, and hardware-interface priorities.

## Remaining Gaps

Rev7 intentionally does not disguise these gaps:

- No pre-silicon evaluation/sign-off or silicon bring-up experience is documented.
- No production silicon profiling, CPU-load optimization, memory-footprint reduction, or quantified power-efficiency optimization is documented.
- No DVFS, thermal-governor, performance/thermal-limits algorithm, or Qualcomm-style power-policy work is documented.
- No hardware-acceleration recommendation or software-to-hardware migration study is documented.
- Arm exposure is through TI AM62 Embedded Linux integration; direct Arm microarchitecture, bare-metal Arm, and Arm assembly experience are not established.
- No custom linker scripts, startup code, memory maps, DMA work, or production bootloader ownership is established.
- No Android HLOS experience is documented.
- Machine-learning experience is an academic NLP matching application, not ML over power, silicon, or product-architecture data.
- Agile/Kanban and Perforce experience are not established strongly enough to list.

Accuracy takes priority over eliminating every gap. In particular, Rev7 does not claim pre-silicon work, thermal optimization, production silicon profiling, professional assembly, or measured power-efficiency improvements.
