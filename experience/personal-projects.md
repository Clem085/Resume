# Programming Projects and Technical Coursework

This file is the long-form inventory behind future tailored resumes. It records what the retained source code, reports, simulations, and Git history actually support. A resume should select only the projects that reinforce the target role; it should not try to reproduce this entire file.

## Evidence and Selection Labels

- **Core candidate:** unusually strong evidence for embedded, low-level software, computer architecture, real-time, controls, validation, or hardware-facing roles.
- **Targeted candidate:** useful when the job specifically asks for the associated language or domain.
- **Archive/supporting:** valid experience that is now superseded by professional work or is too small for the general resume.
- **Source-backed:** implementation plus a report, test output, simulation log, or Connor-specific authorship marker was found.
- **Boundary:** wording that prevents a defensible project from becoming an inflated claim.

## Highest-Value Resume Candidates

### For general embedded-firmware roles

Professional Aegis work, senior design, and ECE 306 should remain ahead of academic projects. If space permits, the strongest project additions are:

1. **Real-time systems and formal verification:** C/POSIX threads, periodic releases, concurrency, timing traces, schedulability analysis, Lustre, and bounded model checking.
2. **C++ microarchitecture simulators:** cache hierarchy, branch prediction, and out-of-order scheduling, especially for low-level, performance, CPU, or platform roles.
3. **Verilog Wallace-tree multiplier:** structural RTL, testbench-driven simulation, and synthesis evidence for firmware roles that interact closely with FPGA or custom digital logic.
4. **MATLAB MOSFET characterization:** measurement import, data cleaning, curve fitting, parameter extraction, and model-versus-measurement plots for mixed-signal, power, or test roles.
5. **LC-3 graphics programs:** substantial assembly, memory-mapped I/O, input handling, and explicit state management when an employer values assembly or very low-level programming.

### For targeted roles

- **Controls/robotics:** simulated digital PID and cascaded control, model linearization, state-space analysis, actuator saturation, and anti-windup.
- **MATLAB/data/ML:** CNN and transfer-learning coursework, PCA/eigenfaces, numerical analysis, and the professional ADC-filter comparison documented in `aegis-power-systems.md`.
- **FPGA/digital design:** Wallace multiplier, serial/parallel shift registers, and the multi-operand arithmetic datapath.
- **Python/data systems:** NLP mentor matching and the constrained supervisor-associate assignment pipeline.
- **Quantum software:** Grover target-sum exploration, Qiskit arithmetic/oracles, QFT addition, and QAOA coursework.

## ECE 463 — C++ Microarchitecture and Performance Simulators, Fall 2025

**Priority:** Core candidate for CPU, low-level software, performance, systems, and computer-architecture roles; targeted supporting evidence for embedded firmware.

**Evidence:** Connor-signed reports, Connor-owned public repository, C++ source, generated experiment data, validation artifacts, and test output in [`ECE463-MicroArch`](https://github.com/Clem085/ECE463-MicroArch).

### Configurable L1/L2 cache simulator

- Built a trace-driven C++ cache simulator that could model an L1 alone or an L1/L2 hierarchy.
- Implemented address decomposition, configurable cache size/block size/associativity, valid and dirty state, least-recently-used replacement, write-back/write-allocate behavior, dirty eviction, and traffic to the next cache level or memory.
- Collected read/write counts, misses, miss rates, writebacks, and total memory traffic rather than treating the simulator as a functional lookup only.
- Automated large configuration sweeps and graphed miss-rate and average-access-time trends across cache sizes, associativities, block sizes, and L1/L2 combinations.
- The signed report records 55 L1 size/associativity simulations, 16 fixed-L2 simulations, 24 block-size simulations, and 12 L1/L2 co-exploration simulations.
- Best reported configurations within the tested space included a 128 KB four-way L1 at 0.790 ns average access time without L2 and an 8 KB L1 plus 64 KB L2 at 0.812 ns.
- Connected measured behavior to compulsory, capacity, and conflict misses; spatial locality; cache pollution; and the latency/capacity tradeoff.

**Boundary:** The ECE 463 implementation and report explicitly disable prefetching. A stream-buffer section in the assignment was for ECE 563 and is incomplete; do not claim a prefetcher.

### Bimodal, gshare, and hybrid branch-predictor simulator

- Implemented trace-driven bimodal and gshare branch predictors in C++ using saturating two-bit counters, PC-indexed tables, a global history register, XOR-based history indexing, and per-branch predictor updates.
- The retained source also contains a hybrid predictor with bimodal/gshare sub-predictors and a saturating chooser table.
- Automated parameter sweeps in Python and generated CSV results/plots rather than testing a few configurations manually.
- Evaluated bimodal table sizes from 7 through 20 index bits across GCC, JPEG, and Perl traces and swept gshare history length from zero through the table-index width for GCC.
- The signed report records minimum bimodal misprediction rates of 11.19% for GCC, 7.59% for JPEG, and 8.82% for Perl within the assigned sweep.
- In the GCC study, the recorded best gshare point was 6.37% at `m=20, n=11`, compared with 11.17% for the same-size bimodal configuration.
- Used the data to explain destructive aliasing at small tables and why global history becomes more useful when enough counters are available.

**Boundary:** Connor completed ECE 463, so the graded report covers bimodal and gshare. Hybrid logic exists in the source, but the hybrid report section was ECE 563-only; present hybrid as an implemented extension, not as a graded experimental result.

### Out-of-order superscalar pipeline simulator

- Built a 509-line C++ trace simulator for a configurable out-of-order processor with fetch, decode, rename, register-read, dispatch, issue, execute, writeback, and retire timing.
- Implemented a register-map table, circular reorder buffer, issue queue, operand tags/readiness, wakeup/broadcast behavior, variable execution latency, oldest-ready issue, in-order width-limited retirement, and front-end/back-end stalls.
- Recorded each instruction's start cycle and duration in every pipeline stage and calculated total cycles and instructions per cycle.
- Added focused dependency-chain, independent-instruction, and mixed-latency tests. The retained `tests/run_tests.sh` was rerun during this audit and all three tests passed.
- Automated a 240-configuration study across GCC and Perl traces, varying reorder-buffer size, issue-queue size, and machine width; parsed results and generated graphs with Python.
- Identified the smallest issue queue within 6% of the 256-entry baseline for each width. The recorded thresholds rose from 8 to 64 entries for GCC and from 8 to 128 for Perl as width increased from one to eight.
- Used the results to explain instruction-window size, dependency lookahead, long-latency operations, exploitable instruction-level parallelism, and diminishing returns from larger structures.

**Boundary:** This is a trace-based academic performance model, not RTL, a cycle-accurate model of a commercial core, or silicon performance validation.

### Concise resume framing

> Built C++ cache, branch-predictor, and out-of-order pipeline simulators; automated trace-driven design-space sweeps in Python to quantify miss rate, branch accuracy, IPC, and memory-hierarchy tradeoffs.

## MATLAB Engineering, Data Analysis, and Machine Learning

### ECE 302 — MOSFET characterization and parameter extraction

**Priority:** Core candidate for mixed-signal, semiconductor, power, validation, MATLAB, or test roles.

**Evidence:** Connor-named `Lab Report 5`, measured nMOS/pMOS family curves, MATLAB code excerpts, extracted parameters, and plots in `../history/academic-projects/matlab/Lab Report 5-Connor Savugot.pdf`.

- Characterized nMOS and pMOS devices from a HEF4007 transistor array using an Analog Discovery 2/DCA Pro laboratory setup.
- Imported measured data with `readmatrix`, selected operating regions, filtered saturation-region samples, and organized multiple drain-current curves for analysis.
- Used `polyfit` and a discrete derivative of the measured transfer curve to estimate threshold voltage and transconductance-related parameters.
- Calculated and visualized mobility, mobility degradation, channel-length modulation, and process-transconductance behavior.
- Plotted measured and predicted device curves together to inspect how well the extracted model represented laboratory measurements.
- Demonstrates a complete measurement-to-analysis workflow: collect device data, clean it, fit a model, extract physical parameters, visualize the result, and discuss mismatch.

**Boundary:** This was an academic device-characterization laboratory. Do not claim production semiconductor characterization, automated test-equipment ownership, or foundry model extraction. Some retained calculations use stated assumptions, so avoid asserting a specific accuracy unless the report value is rechecked.

### Spring 2025 MATLAB — neural networks, transfer learning, PCA, and least squares

**Priority:** Targeted candidate for MATLAB, data-analysis, or ML-adjacent roles.

**Evidence:** Executed notebook/report `../history/academic-projects/matlab/301_MATLAB_AI_LEARNING.pdf` with code, layer definitions, output metrics, and plots. The archive filename suggests ECE 301, but the PDF itself does not identify its course number.

- Used pretrained GoogLeNet in MATLAB to classify images and display the predicted label.
- Defined and trained a convolutional neural network for digit classification with convolution, batch normalization, ReLU, max-pooling, fully connected, softmax, and classification layers.
- Configured stochastic-gradient-descent-with-momentum training for ten epochs and recorded 99.24% validation accuracy on the provided digit dataset.
- Performed transfer learning with SqueezeNet on a small five-class, 75-image merchandise dataset using a 70/15/15 train/validation/test split; the retained output reports approximately 90% test accuracy.
- Applied principal-component analysis and the Karhunen–Loève transform to eigenface-style image data, inspected eigenvalues, reduced dimensionality, and visualized projections.
- Implemented least-squares fitting and projection-matrix exercises, including residual orthogonality and 3D visualization.

**Boundary:** These were guided academic exercises using MATLAB pretrained networks and provided datasets. Do not claim a custom foundation model, production deployment, novel ML research, or large-scale training.

### ECE 220 — numerical and signals foundation

**Priority:** Supporting evidence that MATLAB is a practiced language rather than a one-off plotting tool.

**Evidence:** 38 retained `.m` files under `../../MATLAB/ECE 220 Lab`.

- Wrote vectorized scripts and reusable functions for sampled and continuous signals, unit steps/pulses, signal rectification, cartesian/polar conversion, and complex arithmetic.
- Visualized sine waves, damped cosines, complex exponentials, real/imaginary components, magnitude, and phase.
- Analyzed first- and second-order system behavior and plotted RC/RLC transfer-function responses.
- Used matrices, reduced row-echelon form, inverses, and numerical linear algebra in laboratory exercises.
- Developed familiarity with MATLAB array operations, plotting, function files, and engineering-oriented numerical workflows in a general programming/signals course.

**Boundary:** Some directories include instructional example files. Base authorship claims on the completed lab scripts and custom functions, not every copied reference file in the folder.

### Professional MATLAB work

The Aegis ADC-filter comparison is professional experience and belongs in `aegis-power-systems.md` and `adc-monitoring-card.md`, not under a personal project. That work combined four-channel converter telemetry scaling/calibration, an embedded-C rolling average, parsed CAN captures, and MATLAB comparison of steady-state smoothing versus response to large voltage/current changes.

## Real-Time Systems and Formal Verification — Spring 2026

**Priority:** Core candidate for real-time firmware, RTOS, safety/validation, controls, or concurrency roles.

**Evidence:** Connor-authored Git history and retained code/results in [`rtos-ml`](https://github.com/Clem085/rtos-ml).

- Implemented periodic tasks in C on Linux with POSIX threads, CPU affinity, absolute-time releases, priority-inheritance mutexes, shared timestamp logging, GCC, and Make.
- Used absolute release schedules to reduce drift and instrumented task start/completion times instead of relying on visual behavior alone.
- Generated normalized execution traces and Gantt-style plots to inspect timing, interference, and schedule behavior.
- Analyzed earliest-deadline-first, rate-monotonic, and deadline-monotonic schedulability using utilization and timing-demand methods.
- Modeled synchronous control logic in Lustre and compiled models into executable C artifacts for simulation.
- Used the Luke bounded model checker and counterexample traces to diagnose incorrect temporal monitors, revise state logic, and verify required invariants within the checked bounds.
- Implemented and simulated a stateful PID cruise controller in Lustre with explicit gain/time-step parameters, initialized prior-state memory, integral/derivative state, target-speed behavior, and bounded output.
- Integrated a Python `MyPID` agent with CARLA's planning/application flow and evaluated PID-based longitudinal behavior in Town10HD using target speed, completion time, collision, and lane-invasion instrumentation.
- Worked through an NC State ARC Linux environment using SSH, remote development, compiler/build tools, and course-provided real-time/formal-verification utilities.

**Boundaries:**

- This is academic real-time application work, not implementation of an RTOS kernel, pre-silicon sign-off, or production silicon profiling.
- The recovered PID gains are labeled example values and no simulation trace preserves a quantified improvement; tuning and comparison are direct user reports, not measured public results.
- CARLA Problem 5 was a group assignment. The retained agent wraps CARLA planner behavior and does not preserve the modified `local_planner.py` or final PID coefficients. Describe integration and evaluation of PID-based longitudinal control, not authorship of CARLA's complete PID/planning stack.
- Do not claim reliable stop-sign behavior, road testing, production autonomous-driving software, or safety certification.

### Concise resume framing

> Implemented a deterministic PID cruise controller in Lustre and integrated PID-based longitudinal control into a Python/CARLA agent; evaluated synchronous state behavior, simulated vehicle response, and temporal properties with Luke counterexample traces.

## ECE 310 — Verilog RTL and Vivado

**Priority:** Core candidate for FPGA, RTL-adjacent firmware, digital design, or hardware/software interface roles.

**Evidence:** Connor headers in key modules, Verilog source, Vivado projects, synthesis artifacts, and xsim logs under `../../Verilog` and [`ECE310-Verilog`](https://github.com/Clem085/ECE310-Verilog).

### Structural 8-by-8 Wallace-tree multiplier

- Implemented a structural 8-bit by 8-bit unsigned Wallace-tree multiplier in Verilog.
- Generated 64 partial products and reduced them through explicit half-adder/full-adder stages rather than using the Verilog multiplication operator as the design.
- Retained source is approximately 344 lines and carries a Connor Savugot engineer header.
- Simulated the design in AMD Vivado/xsim across zero, maximum-value, power-of-two, and random operands.
- The retained self-checking simulation log shows all 11 cases matching expected products, including `8'hFF * 8'hFF = 16'hFE01`.
- Retained Vivado synthesis output supports that this progressed beyond a standalone code sketch.

### Serial/parallel datapath building blocks

- Implemented 8-bit parallel-in/serial-out and serial-in/parallel-out shift registers with synchronous reset, load, and shift behavior.
- Built and simulated these blocks as reusable components for a packet-oriented arithmetic design.
- The SIPO simulation log shows the expected bit-shifting sequence; source modules carry Connor engineer headers.

### Multi-operand arithmetic datapath

- Implemented a Verilog datapath that captured four 8-bit operands selected by an operation field, stored them through mux/demux and D-flip-flop structures, and produced the 9-bit result `(A+B)-(C+D)` using ripple-carry arithmetic and two's complement.
- Retained Connor-authored source and Vivado simulation artifacts support “implemented and simulated.”

### Serial BCD ALU development

- Developed substantial revisions of a serial-in/serial-out BCD arithmetic design with a 41-bit input packet, header/operation decoding, two BCD operands, an FSM, multi-digit BCD add/subtract logic, and a 28-bit serialized response.
- This project is useful evidence of packet framing, state-machine decomposition, serial datapaths, and iterative RTL integration.

**Boundaries:**

- The retained final project-2 simulation log repeatedly reports that the header was not detected and the end-to-end test failed. Do not describe the serial BCD ALU as fully functional or verified.
- The project-2 testbench names another student; claim Connor's module revisions/integration work, not sole ownership of all verification code.
- No Kogge–Stone adder source was found in the local tree or public repository. Remove the historical Kogge–Stone claim unless a separate artifact is recovered.
- The evidence supports Verilog. Do not list VHDL without a VHDL-specific artifact.

### Concise resume framing

> Designed and simulated structural Verilog datapaths in Vivado, including an 8-by-8 Wallace-tree multiplier validated by 11 self-checking cases and reusable PISO/SIPO interfaces.

## ECE 492 — Robotics and Digital Controls, Fall 2025

**Priority:** Targeted candidate for controls, robotics, mechatronics, or embedded-control roles.

**Evidence:** Connor-authored repository commit, controller files, reports, plots, and simulation documentation in [`RoboticsControls`](https://github.com/Clem085/RoboticsControls).

- Extended Python-based course simulation frameworks for mass-spring-damper, planar VTOL, and Hummingbird systems.
- Derived and documented nonlinear/linearized dynamics, transfer functions, state-space models, equilibrium inputs, and pole-placement relationships.
- Implemented or modified PD/PID controllers, including discrete integrators, dirty derivatives, cascaded inner/outer loops, motor-force mixing, command saturation, and anti-windup.
- Used parameter perturbations/model mismatch to study steady-state error and the effect of integral action.
- Simulated response to reference commands and inspected tracking, settling behavior, actuator effort, and saturation through generated plots.
- For the Hummingbird model, retained code includes pitch integral control and an outer yaw-to-roll loop with integral action, anti-windup, and PWM mixing.

**Boundary:** The repository contains a large amount of course/textbook scaffolding and reference implementations committed in one bulk snapshot. Do not claim authorship of the entire controls library. Frame the work as extending and analyzing course-provided models/controllers. Retained documentation includes “expected output” and tuning guidance in places, so do not promote unverified settling-time or error thresholds as measured results. Do not claim deployment to production robotics hardware unless a specific lab artifact is recovered.

## LC-3 Assembly and Memory-Mapped I/O — Spring 2023

**Priority:** Core/targeted candidate for assembly, low-level, computer-architecture, or bare-metal roles.

**Evidence:** Individual-assignment specification, compiled `.obj`/`.sym` files, and large Connor-header assembly sources under `../../LC3/Final Programs`.

### Four-digit graphics counter

- Wrote a roughly 625-line LC-3 assembly program that displayed a four-digit decimal counter from `0000` through `9999` using memory-mapped graphics.
- Implemented keyboard commands for increment, decrement, reset, print, and quit.
- Managed decimal carry/borrow and wraparound behavior explicitly without high-level language/runtime support.
- Drew digit glyphs into the display, handled color/state changes, and organized reusable subroutines within LC-3 calling and register constraints.

### Interactive graphics worm

- Wrote a roughly 509-line LC-3 assembly program for an interactive on-screen worm controlled with WASD input.
- Implemented a persistent trail, direction/state updates, display-memory addressing, edge detection and messaging, reset/quit behavior, and manual/periodic color changes.

### Numeric input and output practice

- Implemented a smaller LC-3 program that validated decimal input in the 0–49 range, converted ASCII digits, performed arithmetic, and printed count-up results.

**Boundaries:**

- The folder contains other students' named files; do not claim blanket ownership of every LC-3 artifact.
- The Python `assemblyparser.py`/`newparser.py` work performs preprocessing, number conversion, comment removal, and partial instruction translation, but the retained implementation is incomplete. Describe it as an experimental parser/translator, not a complete assembler or compiler.
- `BinarySearch.asm` is incomplete and should not appear on a resume.

### Concise resume framing

> Built interactive LC-3 assembly applications with keyboard input, memory-mapped graphics, state machines, decimal carry/borrow, boundary handling, and reusable subroutines.

## Python Data and Machine-Learning Applications

### NLP mentor-matching independent study — Spring 2026

**Priority:** Targeted candidate for Python, applied ML, NLP, or data-product roles.

**Evidence:** Multiple Connor-authored commits in a collaborative local Git repository, source modules, tests, and configuration/data-handling artifacts.

- Developed the initial command-line mentor/mentee matching workflow, CSV parsing, direct-match filters, scoring, and orchestration.
- Added semantic matching with sentence-transformer embeddings using the pretrained `all-mpnet-base-v2` model.
- Implemented configurable weighted scoring across technical/industry alignment and profile attributes.
- Added persistent rejection, exclusion, and lock state plus global/per-user weight overrides and explainable score output.
- Moved ranking weights and the NLP contribution into CSV-backed configuration so the matching policy could change without editing scoring code.
- Added tests and privacy protections, including removal/ignore handling for form-response data.

**Boundary:** This is a collaborative academic application using a pretrained embedding model. Do not claim sole ownership, custom foundation-model training, embedded ML, or ML applied to silicon/power telemetry.

### Supervisor-associate matching pipeline — Fall 2025 hackathon/prototype

**Priority:** Supporting/targeted candidate for Python data pipelines or constrained matching.

**Evidence:** Connor-owned public repository and retained executable outputs in [`AI_Matching`](https://github.com/Clem085/AI_Matching).

- Built a command-line Python pipeline that generated synthetic supervisor/associate data, formed candidate pairs, trained a model, scored candidates, and wrote matched/unassigned CSV outputs.
- Applied deterministic compatibility constraints for state and professional-license eligibility before ML scoring.
- Engineered availability-overlap, TF-IDF/cosine-similarity, and capacity features with pandas and scikit-learn.
- Trained and serialized a standard-scaled logistic-regression pipeline, then blended its probability with availability similarity.
- Implemented a greedy capacity-constrained assignment pass that prevented duplicate associate assignments and supervisor over-allocation.
- Retained outputs show 141 of 200 synthetic associates assigned with no duplicate assignments or capacity violations.

**Boundary:** The labels are rules-generated synthetic data and heavily imbalanced. The retained 84.2% validation accuracy comes from predicting only the majority class (`TN=0`, `FP=9`, `FN=0`, `TP=48`) and is not evidence of a useful learned classifier. Lead with the rules/constraint pipeline, explainability, and end-to-end tooling—not the accuracy number or “AI” branding.

## ECE 469 — Quantum Programming, Spring 2025

**Priority:** Targeted candidate for quantum-software or Python/scientific-computing roles; archive for general embedded roles.

**Evidence:** Connor-owned repository, Connor-named notebooks, executed outputs, and environment documentation in [`ECE469-QuantumProgramming`](https://github.com/Clem085/ECE469-QuantumProgramming).

### Grover target-sum exploration

- Implemented a Qiskit/Aer simulation that searched pairs of `n`-bit integers satisfying `a+b=T`.
- Built an oracle, diffusion operator, iteration-count calculation, measurement/bitstring decoding, and target sweeps in Python.
- Ran the retained experiment at `n=5` and 1,000 shots per target, plotted success probability, and compared Grover iteration counts with a classical search-count baseline.
- Explicitly decoded measured bitstrings back to `(a,b)` and checked whether each pair satisfied the target sum.

**Boundary:** The oracle is constructed by classically enumerating each valid `(a,b)` state. This makes a useful educational amplitude-amplification experiment but does not itself realize an asymptotically efficient arithmetic oracle. The notebook contains inconsistent “advantage” figures, so avoid a numerical speedup claim.

### Additional Qiskit and Classiq coursework

- Built modular four-qubit increment, equality-test, conditional-increment, and controlled-phase functions using primitive/multi-controlled gates and ancilla uncomputation.
- Implemented custom QFT/inverse-QFT components and a QFT-based adder, plus Grover exercises for equations and small factoring examples.
- Formulated Ising/QUBO models and used QAOA exercises for number partitioning and minimum vertex cover.
- Used Classiq/Qmod for permutation synthesis, piecewise approximation of `tanh(x)`, and direct/amplitude-loaded Gaussian state-preparation exercises.
- Documented an Arch Linux under WSL Python virtual environment for Qiskit/Aer and related visualization packages.

**Boundary:** These are guided course notebooks and simulator/synthesis exercises, not execution on production quantum hardware. Several optional optimization/scalability cells are exploratory and should not be described as proven scalable algorithms.

## ECE 309 — C++ Algorithms and Data Structures, Spring 2024

**Priority:** Supporting candidate for general software or new-graduate roles; lower value than professional firmware for embedded applications.

**Evidence:** C++ source, assignment specifications, Connor reports, validation inputs, and compiled artifacts under `../../C++`.

### Maze search

- Implemented breadth-first search, depth-first search, and greedy best-first search with Manhattan-distance priority.
- Parsed maze and coordinate files, used `vector`, `queue`, `stack`, `priority_queue`, and map-like predecessor storage, and reconstructed the resulting path.
- Compared how search order and frontier choice affected solution behavior across maze inputs.

### Self-organizing linked lists

- Implemented move-to-front and transpose update heuristics for a linked list and counted access steps over file-driven request sequences.
- Compared the heuristics empirically rather than asserting that one algorithm was universally better.
- Connor's report records request-set step counts of 164 versus 124, 862 versus 1,095, and 5,519 versus 5,480 for move-to-front versus transpose, respectively.

### Frequency-shaped binary search tree

- Implemented binary-search-tree insertion/search/traversal and built a tree informed by observed access frequencies.
- Parsed file inputs and produced tree/output artifacts for a course performance experiment.

**Boundary:** The retained final report does not provide a complete quantitative comparison table for the tree experiment, so avoid claiming a measured performance improvement. Historical cover letters mention Dijkstra's algorithm, but a clear Connor-authored Dijkstra artifact was not found in the audited tree.

## C and Python Foundations

### C board-game state machine

- Implemented a course version of the Trouble board game in C using arrays, functions, turn/state logic, move validation, and terminal interaction.
- The individual assignment and retained source support a completed coursework implementation.

### Incomplete C data-structure exercises

- Worked on a dynamically allocated linked-list map ADT and appointment/file-I/O exercises.
- Retained implementations contain empty functions and apparent defects; preserve them as learning history but do not list them as completed projects.

### Numerical-method utilities in Python

- Wrote an Euler-method differential-equation tool with expression preprocessing, implicit multiplication handling, and exponent translation.
- Implemented trapezoidal and Simpson numerical integration, error-bound calculations, partial sums, and additional Euler approximations in a separate calculus utility.
- Created VPython/NumPy scripts for vectors, forces, energy, and electromagnetics visualization.

**Boundary:** These are early educational scripts with rough parsing and limited validation, not a production symbolic-math package or numerical library.

## Hardware and Electronics Projects

### ECE 212 sequential-logic vending machine — Spring 2024

- Designed and built a sequential-logic vending-machine circuit on a breadboard.
- Validated state/logic behavior with WaveForms and an Analog Discovery 2.
- Reduced gate usage while preserving required behavior.
- Demonstrates digital-logic design, physical construction, structured test, and hardware troubleshooting.

### Discrete charge-pump and boost-converter experiments

- Prototyped charge-pump and boost-converter circuits to create a higher-voltage source when the required barrel-jack adapter was unavailable.
- Built a 555-timer astable multivibrator and used a potentiometer to vary switching frequency.
- Used a Keysight programmable power supply and oscilloscope to observe voltage/current behavior and frequency/duty-cycle changes during tuning.
- Explored switching, capacitor charge transfer, voltage/current tradeoffs, and the difference between unloaded target voltage and a supply capable of supporting load current.

**Boundary:** An archived resume describes a 5 V to 9 V target. This was an exploratory learning project, not a regulated, load-qualified, or efficiency-characterized converter. Professional bidirectional buck-boost firmware should lead any power-electronics resume.

## Linux, Automation, and Platform Exploration

### AutoHotkey LC-3 workflow automation

- Learned AutoHotkey to automate a repeated desktop workflow for opening, assembling, and launching LC-3 programs.
- Shared the shortcut-driven workflow with classmates.
- No reliable time-savings metric is retained.

### Linux/WSL, boot, and virtualization projects

- Used Ubuntu and Arch Linux under WSL for C/C++ builds, Git/SSH workflows, Python environments, Qiskit, and remote course development.
- Configured Arch/Garuda Linux, Ubuntu, and Windows multi-boot environments managed through GRUB and worked through UEFI/boot troubleshooting.
- Built an HDMI-triggered systemd service that switched integrated/discrete GPU configuration in a personal setup.
- Converted a Lenovo Chromebook to Windows 11 while retaining touchscreen/stylus use and resolving flashing, recovery, driver, and compatibility issues.

**Selection guidance:** Keep these as supporting platform fluency. They are superseded on the general resume by professional Yocto/Arago, device-tree, kernel, systemd, watchdog, boot-diagnostic, and cross-platform build work.

### Linux GPIO / neon-light exploration

- Retained a small C program using `libgpiod` to open `/dev/gpiochip0`, request BCM GPIO 4 as an output, drive it high and low with a delay, handle errors, and release the line/chip cleanly.
- A compiled binary and VS Code task/SFTP files indicate a remote Linux development workflow, but the retained files do not establish the target board, date, deployment status, or an independently completed neon-light system.
- Treat this as an archive-level GPIO experiment. Do not claim a production lighting controller, daemon/service, real-time behavior, or complete hardware installation.
- The SFTP configuration may contain private endpoint information and must not be copied into public documentation.

### NES and calculator exploration

- Retained the cc65 toolchain and NES tutorial/sample repositories while exploring constrained-console development.
- Wrote TI-Basic vector utilities including dot and cross products and explored Game Boy/Game Boy Color emulation on calculator hardware.

**Boundary:** Most NES content is upstream tutorial/sample code; do not claim an independently authored NES game. Calculator work is legitimate early interest but not resume-relevant now.

## Related Experience Sources

- `aegis-power-systems.md`: professional embedded firmware, power conversion, FreeRTOS, dsPIC33CK/PIC32/TMS320, IPMI/VPX, communications, Embedded Linux, cross-platform tooling, and the MATLAB ADC-filter analysis.
- `senior-design.md`: EV Active Sensor Adapter, STM32G474, BQ79616 battery monitoring, ten-channel ADC sensing, UART, CAN telemetry, custom-PCB integration, specification, documentation, and teamwork.
- `ece-306.md`: MSP430FR2355 embedded vehicle and three semesters of teaching-assistant work.
- `teaching-leadership.md`: OPS 2 lead instruction, ECE 306 support, soldering workshops, lectures, lab instruction, and student outcomes.
- `team-industries.md`: automated test creation, tolerance validation, metrology, and manufacturing/test experience.

## Source and Claim Audit Notes

- `Programming_Dir_Tree.txt` was used to locate retained C, C++, LC-3, MATLAB, Python, RTOS, senior-design, and Verilog artifacts.
- Public repositories were checked where available; a repository's presence alone was not treated as proof that every file was Connor-authored.
- Signed reports, Connor headers, Connor-named notebooks, granular Git commits, self-checking output, and reproducible test scripts were weighted more heavily than filenames or old resume wording.
- Large one-commit course repositories require careful attribution. This especially applies to Robotics Controls, where course/textbook scaffolding is mixed with Connor's controller and documentation work.
- Generated Vivado, notebook, binary, or plot artifacts support that work was run, but do not prove every edge case or specification requirement passed.
- Keep professional work, collaborative academic projects, guided coursework, and exploratory personal work labeled distinctly.

## Resume Selection Guidance

- For a one-page general embedded resume, do not force in a project section if Aegis, senior design, ECE 306, TEAM, and teaching already fill the page with stronger evidence.
- Use one project cluster only when it adds a capability the professional section does not show clearly: microarchitecture/performance, formal verification, RTL, controls, MATLAB device analysis, or assembly.
- Prefer one outcome-rich project bullet over a keyword list. Include the engineering object, implementation, validation method, and result/tradeoff.
- Do not repeat languages merely to increase keyword count. The project should prove why the language mattered: C for timing/concurrency, C++ for simulation/data structures, Python for automation/analysis, MATLAB for engineering data/modeling, Verilog for structural RTL, and assembly for direct state/I/O control.
- Keep AI/quantum projects for targeted applications. They demonstrate breadth but should not displace professional low-level firmware on a general embedded resume.
