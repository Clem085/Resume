# Public GitHub Project Inventory

This file records what Connor's public repositories actually demonstrate so future resume revisions can select relevant evidence without treating every checked-in file as Connor-authored or every README plan as completed work.

Audit date: **August 14, 2026**

Sources reviewed:

- the public repository list and public commit metadata under [Clem085](https://github.com/Clem085)
- current repository trees, READMEs, reports, source files, test artifacts, and commit messages
- full local clones where available, including the broader `Programming_Dir_Tree.txt`
- existing normalized experience files in this repository

Commit counts below are attribution clues, not productivity metrics. A commit can import starter code, merge another branch, or contain a large body of original work. File-level evidence and known course/team context take precedence.

## Resume-selection map

| Priority | Project | Strongest evidence | Best-fit roles |
|---|---|---|---|
| Highest | EV Active Sensor Adapter | STM32/BQ79616 bring-up, ADC, UART, CAN, timing, degraded-mode firmware, team integration | embedded firmware, automotive, BMS, power, hardware integration |
| Highest for architecture/performance | ECE463 Microarchitecture | C++ cache, branch-predictor, and out-of-order pipeline simulators; automated experiments | firmware performance, computer architecture, silicon-adjacent software |
| High for real-time roles | rtos-ml | periodic POSIX tasks, scheduling analysis, traces, Lustre, bounded model checking | real-time systems, controls, validation, safety-oriented software |
| High supporting evidence | ECE306 | MSP430FR2355 C firmware, peripherals, interrupts, vehicle integration, debugging | entry-level embedded, MCU firmware, teaching/technical leadership |
| Targeted | RoboticsControls | Python dynamics simulations and PD/PID/cascaded control exercises | controls, robotics, modeling, simulation |
| Targeted | Git_Src_Ctrl | cross-platform Git/GitLab workflow and training documentation | team process, documentation, developer enablement |
| Targeted | AI_Matching | Python data pipeline, filtering, TF-IDF, logistic regression, capacity-constrained matching | Python, data, applied-ML roles |
| Targeted | ECE310-Verilog | structural Verilog, arithmetic circuits, FSMs, serial datapaths, testbenches | FPGA, RTL, digital design |
| Narrow | ECE469 Quantum Programming | Python/Qiskit circuits, QFT arithmetic, Grover experiments, environment setup | quantum-software or algorithm-focused roles |
| Supporting duplicate | Git_Src_Ctrl-WINDOWS | Windows-specific Git setup and GUI workflow | documentation or Windows-heavy team environments |
| Do not use as experience | Resume | versioned application-material system | portfolio link only |
| Do not use | Music4All | README-only product concept | none until implementation exists |

For a general full-time embedded-firmware resume, select at most one or two project entries after professional experience. Senior design usually deserves the first slot. ECE463 or `rtos-ml` can take the second slot when the posting emphasizes architecture/performance or real-time behavior. ECE306 is most useful when teaching and broad MCU debugging are more important than adding another advanced academic project.

## 1. Senior_Design-EV_Active_Sensor_Adapter

Repository: [Clem085/Senior_Design-EV_Active_Sensor_Adapter](https://github.com/Clem085/Senior_Design-EV_Active_Sensor_Adapter)

### Verified system

The current source implements a Formula SAE EV sensing and telemetry controller around:

- an **STM32G474** MCU
- a **TI BQ79616** battery-monitor device
- ten thermistor channels sampled through the STM32 ADC
- USART1 at 1 Mbps for the BQ79616 protocol path
- USART2 at 115200 baud for STLINK virtual-COM logging
- FDCAN1 used to transmit extended-ID CAN telemetry at a 1 Mbps nominal setting
- timers, subsystem-status flags, UART logs, and LEDs for scheduling and diagnostics

The active firmware is a timer-assisted service-loop design. `main()` repeatedly services the thermistor, CAN, and battery-voltage paths. The initialization flow brings up HAL, clocks, GPIO, two UARTs, ADC, CAN, timers, and the BQ startup sequence. The code keeps the thermistor/CAN path operational when BQ communication fails, which is concrete evidence of subsystem isolation and degraded-mode design.

### Verified implementation details

- Implemented BQ79616 command/response framing, CRC-16 validation, UART transport, wake-pulse generation, baud configuration, register access, keep-alive/fault behavior, cell-voltage reads, and an explicit shutdown path.
- Switched a UART pin between GPIO and alternate-function modes to generate the BQ wake pulse, then restored UART operation.
- Used the Cortex-M DWT cycle counter for microsecond wake timing.
- Sampled ten thermistor inputs with the STM32G4 ADC, calibrated the ADC, allowed channel-settling time, discarded the first conversion after channel changes, and converted measurements through a lookup/interpolation path.
- Maintained separate subsystem status variables so a failed voltage-monitor path did not stop thermistor acquisition or CAN reporting.
- Worked within the team-developed CAN path that encoded and scheduled address-claim, BMS thermal summary, individual thermistor, and segmented external-voltage messages using extended identifiers.
- Diagnosed a CAN cadence problem caused by both incorrect TIM7 period/interrupt wiring and long blocking BQ reads. The documented resolution corrected the STM32G474 `TIM7_DAC` vector path and reduced selected BQ timeouts so the service loop could meet 100/200 ms send intervals.
- Added structured, color-coded subsystem logs and per-subsystem LED status behavior to make initialization and runtime faults visible during bring-up.
- Maintained bring-up, flashing, pinout, communication, troubleshooting, architecture, code-map, and known-issue documentation for handoff.
- A checked-in test-results report records seven passing host-side helper tests for temperature conversion, CAN identifiers/payloads, min/max/average calculations, boundary cases, and checksums.

### Teamwork and ownership boundary

The public history contains **46 commits**: 35 under Connor/Connor Savugot and 11 under teammate Kayla Radu. Connor's history specifically records BQ bring-up, successful voltage-tap reads, wake-path simplification, CRC/fault fixes, service-loop and subsystem-status restructuring, thermistor logging/data changes, shutdown control, logging/LED improvements, and documentation. Teammate commits record meaningful CAN, fault-testing, external-ADC-to-CAN, and timing work. Present this as a collaborative senior-design system and identify Connor's BQ/bring-up/integration work; Connor explicitly confirmed that he did not author CAN middleware or messaging. His CAN work involved timer, GPIO, and interrupt integration. Do not imply CAN middleware/message ownership or sole board ownership. See [the direct contribution clarification](senior-design.md#personal-contribution-clarification--september-19-2026).

### Important source-of-truth boundary

The root README contains an older aspirational RTOS/ADC-DMA architecture and stale build examples that do not match the current `src/` implementation. The current firmware documentation explicitly identifies a service loop with timer flags, not FreeRTOS. Some older documents also mention MAX17841/MAX17854 or CAN-FD, while the active source and current documentation use BQ79616 over UART and extended Classical-CAN-style frames. Do not claim FreeRTOS, DMA, MAX17841, or a completed CAN-FD implementation for this project without separate confirmation.

The repository includes TI TMS570 sample code and legacy MSP430/reference material. Those directories are vendor/reference inputs, not evidence that the final firmware targeted TMS570 or MSP430.

### Resume guidance

This is the strongest public academic embedded project. Useful concise themes are:

- STM32G474 firmware integrating BQ79616 voltage monitoring, ten-channel thermistor acquisition, UART, and CAN telemetry
- datasheet-driven BQ wake/protocol/CRC bring-up and cell-voltage validation
- timer and blocking-I/O root-cause analysis restoring scheduled CAN traffic
- subsystem isolation, diagnostics, and collaborative hardware/firmware integration

Avoid calling the system production-ready, vehicle-deployed, or fully safety-certified. The repository supports bench integration and test work, but not those outcomes.

See also `senior-design.md` for requirements, architecture, team, and component-selection context not fully represented in GitHub.

## 2. rtos-ml

Repository: [Clem085/rtos-ml](https://github.com/Clem085/rtos-ml)

Course context: ECE 591 / CSC 549, Embedded Systems for Autonomous Driving, Spring 2026.

### Verified work

- Implemented periodic tasks in C with POSIX threads, CPU affinity, absolute-time releases, shared timestamp tracing, and a priority-inheritance mutex.
- Built and ran the programs with GCC/Make on Linux and produced normalized execution traces and Gantt-style timing plots.
- Evaluated earliest-deadline-first, rate-monotonic, and deadline-monotonic scheduling using utilization and timing-demand analysis.
- Modeled synchronous switch/control logic in Lustre and compiled models into executable C artifacts for simulation.
- Used the Luke bounded model checker, counterexample traces, and monitor revisions to check required temporal invariants within the configured bounds.
- Implemented and simulated a Lustre PID cruise controller using deterministic tick execution, initialized prior-state memory, integral/derivative state, target-speed behavior, and bounded actuator output.
- Integrated a Python `MyPID` agent with CARLA's navigation/planning flow and evaluated PID-based longitudinal behavior using target speed, completion time, collisions, and lane invasions in Town10HD.
- Used SSH, remote development, NC State's ARC Linux environment, and course-provided real-time/formal-verification tooling.

### Ownership and evidence boundary

All six public commits are Connor-authored, and the local history likewise identifies Connor. The repository also vendors a large course tool distribution; GitHub therefore labels Tcl as the dominant language even though Connor's meaningful implementation work is C, Python, Lustre, shell, and build configuration.

This is not an RTOS kernel implementation and is not FreeRTOS-on-MCU work. The scheduler exercises run with POSIX threads on Linux. The recovered Lustre source now supports the PID implementation. The recovered CARLA work was a group assignment; `MyPID.py` wraps planner behavior, the modified `local_planner.py` and final gains are not retained, and no quantified performance improvement is recorded. Claim PID-based CARLA integration/evaluation, not authorship of CARLA's complete low-level controller or production autonomous-driving software.

### Resume guidance

Strong for real-time, controls, verification, automotive, or performance roles. A targeted résumé can connect the Lustre PID, CARLA integration, periodic-task implementation, timing instrumentation, and counterexample-driven formal verification. It is optional on a generic embedded résumé if professional firmware already fills the page.

## 3. ECE463-MicroArch

Repository: [Clem085/ECE463-MicroArch](https://github.com/Clem085/ECE463-MicroArch)

Course context: ECE 463 Microprocessor Architecture, Fall 2025.

### Project 1 — cache hierarchy simulator

- Built a command-line C++ trace simulator for configurable L1 and optional L2 caches.
- Implemented address decomposition, set/way storage, write-back/write-allocate behavior, dirty evictions, inter-level traffic, and least-recently-used replacement.
- Reported reads, writes, misses, miss rates, writebacks, and total memory traffic in the course validation format.
- Added Python/YAML/CSV/Matplotlib automation to sweep cache sizes, associativity, block sizes, and hierarchy choices and calculate/plot average access time.
- The retained implementation explicitly reports no prefetching; do not describe this project as a cache-prefetcher implementation.

The current simulator builds and runs successfully in the audited clone.

### Project 2 — branch prediction simulator

- Implemented bimodal and gshare predictors using indexed two-bit saturating-counter tables and global history.
- Implemented a hybrid predictor with a chooser table selecting between gshare and bimodal outcomes.
- Added command-line parsing, trace processing, statistics, table dumps, and Python sweep/plot tooling for predictor-size and history-length experiments.
- Commit history records successful validation runs, but the current verification script cannot reproduce the full suite because its expected-output directory is not checked in. Keep the claim at implemented/tested coursework rather than claiming independently revalidated perfection.

The hybrid predictor is present as a Connor-authored source extension; the retained graded report covers bimodal and gshare results only. Describe hybrid as implemented code, not as a separately graded result.

### Project 3 — superscalar out-of-order pipeline simulator

- Implemented fetch, decode, rename, register-read, dispatch, issue, execute, writeback, and in-order retirement stages.
- Modeled a reorder buffer, register-map table, issue queue, operand tags/readiness, wakeup/broadcast behavior, execution latencies, width limits, and pipeline backpressure.
- Produced per-instruction stage timing and total instructions, cycles, and IPC.
- Automated ROB/IQ/width sweeps with shell and Python scripts and graphed performance trends for GCC and Perl traces.
- The checked-in quick tests for dependency-chain, parallel, and mixed traces all pass in the audited clone.

### Ownership and evidence boundary

All 12 public commits are Connor-authored, and source headers identify Connor. Course traces, validation data, report templates, and starter reader/tool files are supplied educational material. Claim the simulators and experiment automation, not ownership of the benchmark traces or course specification.

### Resume guidance

This is unusually relevant for processor, SoC, performance, power/limits, compiler-adjacent, and low-level systems roles. It demonstrates C++ systems programming and concrete understanding of cache behavior, control speculation, instruction-level parallelism, resource sizing, and performance tradeoffs. For a broad hardware-integration role it is secondary to senior design and professional firmware.

## 4. RoboticsControls

Repository: [Clem085/RoboticsControls](https://github.com/Clem085/RoboticsControls)

Course context: NCSU robotics-controls coursework based on the BYU Controlbook, Fall 2025.

### Verified Connor work

- Modified Python dynamic simulations for a mass-spring-damper plant, planar VTOL, and Hummingbird laboratory platform.
- Worked through equilibrium/linearized dynamics, parameter perturbations, animation/simulation plumbing, and response visualization.
- Implemented PD controllers and digital PID controllers for mass and planar-VTOL exercises.
- Implemented a cascaded Hummingbird controller: longitudinal pitch PID, inner roll PD, and outer yaw PI, including dirty derivatives, actuator saturation, PWM mixing, and anti-windup back-calculation.
- Documented pole-placement math, system type/steady-state-error reasoning, selected gains, simulation checks, and expected behavior.
- Connor's commit-level changes include added controller/simulation files and material changes to dynamics files, rather than documentation alone.

### Ownership boundary

The repository README says it is a slightly customized BYU Controlbook used by NC State. The public history sample contains 28 Connor-authored commits alongside a substantial imported history from BYU and NC State authors. Many base dynamics, plotting, animation, tutorial notebooks, and problem statements are upstream course framework.

Attribute the specific assignments and modified controller/dynamics files to Connor. Do not present the entire Controlbook repository, VTOL model, or Hummingbird framework as an original ground-up codebase. The work is simulation/coursework, not deployed robot firmware or hardware control.

### Resume guidance

Useful for control-algorithm, robotics, autonomous-systems, or modeling roles. It can support keywords such as Python, state-space/dynamics, PD/PID, cascaded control, saturation, anti-windup, simulation, and validation. Usually omit it from a one-page general embedded resume because the professional power-control and real-time work is stronger.

## 5. Git_Src_Ctrl

Repository: [Clem085/Git_Src_Ctrl](https://github.com/Clem085/Git_Src_Ctrl)

### Verified work

- Created a detailed engineer-facing guide to Git/GitLab source control using both command-line and graphical workflows.
- Documented main/develop/feature/release/hotfix/hardware branches, non-fast-forward merges, annotated tags, upstream tracking, safe reverts, merge-conflict resolution, branch comparison, and repository-history visualization.
- Addressed Windows/Linux line-ending policy through `.gitattributes` and documented cross-platform setup through VS Code, WSL/Ubuntu, Git for Windows, Git Extensions, SSH keys, credential management, and GitLab access.
- Created extensive screenshot-based GUI instructions, CLI reference material, a handout, and presentation material suitable for onboarding or team training.
- The repository's 56 public commits are all Connor-authored and intentionally exercise branches, merges, releases, hotfixes, and tags as part of the learning/demo history.

### Evidence boundary

The material explicitly includes an AEGIS development workflow and company-specific setup examples. It proves that Connor authored substantial process documentation and trained/practiced the workflow. The public repository alone does not establish how many engineers used it, whether it became formal company policy, or a measured productivity improvement. Do not add adoption metrics without confirmation.

### Resume guidance

Do not list this as a primary programming project. Use it as supporting evidence for technical documentation, remote-team collaboration, developer onboarding, cross-platform tooling, Git/GitLab, release hygiene, and explaining engineering workflows to others. It can become a strong professional bullet when paired with Connor's direct account of team use and impact.

## 6. Git_Src_Ctrl-WINDOWS

Repository: [Clem085/Git_Src_Ctrl-WINDOWS](https://github.com/Clem085/Git_Src_Ctrl-WINDOWS)

### Verified work

- Preserves the Windows-specific predecessor/companion material for the larger source-control guide.
- Covers Git for Windows, WSL/Ubuntu, branch history, VS Code diff/merge behavior, and repeatable setup instructions.
- Both public commits are Connor-authored.

### Resume guidance and boundary

Treat this as supporting history for `Git_Src_Ctrl`, not a second independent accomplishment. The consolidated repository is broader and stronger. Do not occupy resume space with both.

## 7. AI_Matching

Repository: [Clem085/AI_Matching](https://github.com/Clem085/AI_Matching)

Repository context: a Fall 2025 hackathon-style supervisor/associate matching prototype. It is distinct from the later collaborative Spring 2026 `NLP_Matching` independent-study project recorded in `personal-projects.md`.

### Verified pipeline

- Generated synthetic supervisor and associate CSV datasets with states, license categories, availability, and capacity.
- Built deterministic candidate filters for state overlap and license compatibility.
- Parsed availability and created exact-overlap plus TF-IDF/cosine-similarity features.
- Generated labeled candidate pairs and trained a scikit-learn pipeline using standardization and logistic regression.
- Blended model probability with availability similarity, then performed a greedy assignment that enforced one assignment per associate and supervisor-capacity limits.
- Added a command-line orchestrator for generate/build/train/score stages and produced matched/unassigned CSV outputs.
- Built notebook diagnostics for validation reports, class imbalance, precision/recall, confusion matrices, capacity audits, match coverage, and tuning ideas.

### Ownership and evidence boundary

All three public commits are Connor-authored. The repository is a prototype using synthetic data, generated labels, TF-IDF, and logistic regression. It is not a deployed staffing system, not an optimal assignment solver, and not evidence of training a neural network or foundation model. A checked-in 84.2% validation snapshot predicts only the majority class (`TN=0`, `FP=9`, `FN=0`, `TP=48`), so do not advertise the accuracy or present it as model quality or real-world impact.

### Resume guidance

Useful for Python, data-pipeline, applied-ML, or tooling roles. Strong keywords are pandas, scikit-learn, feature engineering, deterministic constraints, explainable scoring, CSV pipelines, validation diagnostics, and capacity-aware assignment. It is normally lower priority than embedded work.

## 8. Music4All

Repository: [Clem085/Music4All](https://github.com/Clem085/Music4All)

### Verified status

The repository contains only a short README describing a concept for downloading YouTube-sourced music in M4A format. It contains no implementation, tests, architecture, or usable feature record. Both commits are Connor-authored, but one is the initial repository creation and one updates the README.

### Resume guidance

Do not include this project on a resume or describe its proposed features as implemented. Retain it only as an idea stub until source code and a legally/technically defensible scope exist.

## 9. ECE469-QuantumProgramming

Repository: [Clem085/ECE469-QuantumProgramming](https://github.com/Clem085/ECE469-QuantumProgramming)

Course context: ECE 469 Quantum Programming, Spring 2025.

### Verified work

- Configured Python virtual environments for Qiskit/Aer under Arch Linux in WSL and a separate Python/Classiq environment, then documented reproducible setup and troubleshooting.
- Built and simulated Qiskit circuits using registers, state vectors, controlled gates, measurement, and Aer simulators.
- Implemented an in-place four-qubit QFT adder using QFT/inverse-QFT and controlled phase rotations, with multiple input checks.
- Built a Grover-search exercise for values satisfying `a + b = 17` and compared success across iteration counts.
- Retained coursework artifacts involving equality/oracle circuits, quantum Fourier transform, Grover exploration, and introductory QAOA/Max-Cut and Classiq/Qmod exercises.

### Ownership and evidence boundary

All 59 public commits are under Connor's accounts, but the repository contains instructor-provided notebooks, downloaded tutorials, assignment prompts, Classiq examples, and a checked-in virtual environment. Individually named completed notebooks and Connor's added code are evidence of coursework; the complete repository is not a from-scratch quantum library.

Do not claim quantum-hardware execution, novel quantum-algorithm research, or ownership of Qiskit/Classiq tutorial code. A prior resume source mentions comparison to a classical baseline; the public artifacts support algorithm exploration but should not be used for a quantified speedup claim.

### Resume guidance

Relevant only for quantum-software, Python/algorithm, or unusually broad research roles. It demonstrates learning agility, mathematical programming, environment troubleshooting, and technical documentation, but is not competitive with Connor's embedded portfolio for firmware jobs.

## 10. ECE306

Repository: [Clem085/ECE306](https://github.com/Clem085/ECE306)

Course context: ECE 306 embedded-systems vehicle project, Fall 2024, with later material preserved while Connor supported the course.

### Verified firmware work

- Developed modular embedded C for the TI **MSP430FR2355** in Code Composer Studio.
- Configured clocks, GPIO, timers, interrupts, ADC, DAC, UART/serial paths, LCD output, switches, LEDs, motors, and target/linker configuration.
- Built an incremental vehicle-control sequence including motor movement, ADC/IR-based line sensing, line following, serial control, and Wi-Fi/IoT integration.
- Implemented timer/PWM motor control, switch interrupts, software debouncing, operating modes, LCD/menu behavior, and resistor/selector input workflows.
- Used explicit modules and headers for peripherals and application behavior, providing useful evidence of peripheral-by-peripheral bring-up and later integration.
- Maintained multiple project checkpoints, refactored module/header organization, and preserved final/known-good variants for teaching and debugging.

### Ownership and evidence boundary

All 62 public commits map to Connor's account aliases. The repository contains many duplicated project versions, generated Code Composer artifacts, provided board/support files, and later TA/reference copies. The 2025/2026 repository activity does not mean the student vehicle was a multi-year production project. Separate the Fall 2024 implementation from Spring 2025–Spring 2026 teaching/support.

The linker command files and TI support artifacts are tool/vendor inputs. Their presence does not by itself prove Connor designed a custom linker script. Likewise, this project used PWM for a small vehicle; it is not the professional bidirectional power-conversion PWM architecture.

### Resume guidance

Strong supporting evidence for foundational embedded C, MCU peripherals, interrupt-driven design, physical-board debugging, and the technical depth behind Connor's ECE 306 teaching. For a one-page experienced-candidate resume, the later TA role often communicates more value than listing the student car separately.

See `ece-306.md` for the clean separation between student work and later teaching duties.

## 11. ECE310-Verilog

Repository: [Clem085/ECE310-Verilog](https://github.com/Clem085/ECE310-Verilog)

Course context: NCSU ECE 310 digital design, Fall 2024.

### Verified work

- Wrote structural and behavioral Verilog in AMD Vivado.
- Constructed full/half adders, ripple-carry adders, multiplexers/demultiplexers, D flip-flops, and serial/parallel shift registers.
- Built an **8x8 Wallace-tree-style multiplier** from explicit partial products and adder stages, with a multi-case testbench.
- Built a register-based arithmetic datapath for captured inputs and addition/subtraction behavior.
- Developed a serial-input/serial-output BCD arithmetic unit using a packet header, SIPO input, operand/opcode extraction, four-digit BCD addition/subtraction, FSM control, and PISO result framing.
- Retained testbenches and waveform/configuration artifacts for functional simulation.

### Ownership and evidence boundary

The public repository has only two Connor-authored bulk-import commits, so commit history cannot attribute every file. Many key source headers identify Connor, but at least one retained Project 2 testbench identifies Christopher Mori. Claim Connor's modules and course implementation, not sole authorship of every copied/reference/test artifact.

The public tree supports a Wallace multiplier, BCD serial ALU, SIPO/PISO, and Verilog. It does **not** contain a Kogge–Stone implementation or identifiable VHDL source. Do not use the older Kogge–Stone or VHDL claims unless a separate artifact is recovered.

A retained end-to-end BCD serial-ALU simulation log fails at packet-header detection. The source supports development of the serial datapath and its component modules, but do not claim that the complete BCD transaction passed end-to-end verification until a corrected test result is retained.

### Resume guidance

Useful for FPGA, RTL, digital-design, or firmware roles that value hardware understanding. Usually omit it from a general one-page embedded resume unless the job asks for Verilog, Vivado, digital logic, serial datapaths, or hardware state machines.

## 12. Resume

Repository: [Clem085/Resume](https://github.com/Clem085/Resume)

### Verified purpose

- Maintains versioned LaTeX resumes and cover letters, normalized experience sources, historical application materials, build rules, and revision documentation.
- Demonstrates evidence management, LaTeX, reproducible document builds, revision control, and tailoring application material to job requirements.
- All public commits are Connor-authored.

### Resume guidance

This is a useful portfolio and process repository, not a technical engineering project to list in the resume's Projects section. It may be linked publicly only if Connor is comfortable exposing all checked-in historical material and application context.

## Cross-project claims that are now safe to make

With appropriate context, the public portfolio supports these broader statements:

- Embedded C across MSP430FR2355 and STM32G474 academic systems, plus the separately documented professional PIC/dsPIC/TMS320 work.
- Datasheet-driven bring-up and protocol debugging spanning ADC, UART, CAN, timers, interrupts, GPIO, and battery-monitor communication.
- C++ simulation of caches, branch prediction, and out-of-order execution, with Python/shell experiment automation and performance analysis.
- Real-time scheduling, Linux/POSIX concurrency, trace instrumentation, synchronous modeling, and formal verification.
- Python modeling/data work across controls simulation, applied ML, experiment automation, and quantum coursework.
- Technical documentation ranging from firmware handoff/bring-up guides to cross-platform Git workflow training.
- Verilog/digital logic through structural arithmetic, FSMs, SIPO/PISO, BCD, and testbench-based simulation.

## Claims the public portfolio does not support

- sole ownership of the complete senior-design system, CAN subsystem, PCB, or RoboticsControls framework
- FreeRTOS, DMA, or CAN-FD implementation in senior design based only on its stale root README
- an RTOS kernel implementation in `rtos-ml`
- cache prefetching in ECE463 Project 1
- custom-trained transformer/foundation models in either matching project
- production deployment or real-world impact for `AI_Matching`
- quantum-hardware execution or novel quantum research
- Kogge–Stone adder or VHDL based on the current ECE310 public repository
- implemented Music4All functionality
- production certification, vehicle deployment, or safety sign-off for senior design

## Portfolio cleanup opportunities

These are not prerequisites for using the evidence, but they would make the GitHub profile stronger for recruiters:

1. Replace the stale senior-design root README with the current `documentation/` architecture and label legacy/vendor directories clearly.
2. Add a concise top-level README to ECE463 with the three simulators, build commands, validation status, and representative graphs.
3. Add a small top-level README to `rtos-ml` that distinguishes Connor's assignments from the vendored course tools.
4. Remove checked-in virtual environments, binaries, caches, and duplicate generated projects from ECE306/ECE469/ECE310 where safe, or archive the repositories read-only with an explanatory README.
5. Mark Music4All as an unimplemented concept or make it private until it has source.
6. In RoboticsControls, add a short `CONTRIBUTIONS.md` naming Connor's controller/dynamics files and explicitly crediting the BYU/NCSU base.
7. Keep `AI_Matching` and the later `NLP_Matching` project clearly separated by date, purpose, algorithm, and collaboration model.
