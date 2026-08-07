# Technical and Personal Projects

These projects preserve useful technical history from older résumés. Most are no longer strong enough for the general résumé because later professional work demonstrates the same skills at greater depth, but they can support project-focused, software, digital-design, or early-career variants.

## Discrete Power-Circuit Experiments

- Prototyped charge-pump and boost-converter circuits to create a higher-voltage supply when the required barrel-jack adapter was unavailable.
- Built a 555-timer astable multivibrator and used a potentiometer to make the switching frequency adjustable.
- Explored switching, capacitor charge transfer, voltage/current tradeoffs, and the practical difference between a target voltage and a supply that can support the required load.
- Used a Keysight programmable power supply and an oscilloscope in an NC State laboratory to characterize voltage/current behavior and observe frequency/duty-cycle changes before and during circuit tuning.
- An archived résumé describes a 5 V to 9 V target. Treat this as an exploratory learning project, not as a regulated or efficiency-validated converter design.

## ECE 212 — Sequential-Logic Vending Machine, Spring 2024

- Designed and built a sequential-logic vending-machine circuit on a breadboard.
- Validated logic behavior with WaveForms and an Analog Discovery 2.
- Reduced gate usage while preserving the required state behavior.
- Demonstrated digital-logic design, breadboard implementation, structured test, and hardware troubleshooting.

## FPGA and HDL Work — Archive-Derived Details

- Repeated historical sources describe Verilog design and test in AMD Vivado, including a Kogge–Stone adder.
- Newer drafts also describe an ALU using SIPO/PISO buses and binary-coded-decimal arithmetic. Confirm the course, individual ownership, and completed verification before turning this into a résumé bullet.
- One tailored cover letter says VHDL while the repeated résumé record says Verilog. Do not list VHDL until Connor identifies the VHDL-specific implementation.
- Keep these HDL artifacts distinct from the physical ECE 212 breadboard vending machine unless they were parts of the same assignment sequence.

## ECE 469 — Quantum Search

- Set up a reproducible Qiskit/Aer environment under Arch Linux in Windows Subsystem for Linux.
- Implemented Grover's search algorithm and studied success probability versus iteration count.
- Compared the quantum-search behavior with a classical baseline.
- The archived source establishes an academic implementation and analysis, not work on production quantum hardware.

## ECE 309 — C++ Maze Solver and Search Algorithms, Spring 2024

- Implemented breadth-first search, depth-first search, and greedy best-first search in C++.
- Compared behavior across multiple maze configurations.
- Examined runtime and memory tradeoffs among the three search strategies.
- Useful for software/algorithm variants, but less relevant than production firmware and hardware-integration experience for a general embedded résumé.

Tailored cover letters also mention Dijkstra's algorithm, linked lists, and search trees. They are plausible coursework leads but lack a named artifact in the archive; confirm before adding them to a skills or projects section.

## LC-3 Assembly Translation Tool

- Built binary, hexadecimal, and numeric conversion logic as part of an assembly-processing tool.
- Parsed an assembly file, removed comments, interpreted instructions, and wrote the corresponding binary representation to an output file.
- The archive does not establish a complete production assembler with full symbol resolution, so describe it as an assembly translation/parser project rather than a complete compiler.

## AutoHotkey Build Automation

- Learned AutoHotkey to automate repetitive desktop tasks.
- Created a shortcut-driven workflow that opened, compiled, and executed LC-3 assembly work that otherwise required a repeated sequence of commands.
- Shared the workflow with classmates; no verified time-savings metric is available.

## Real-Time, Networking, and Signal-Analysis Coursework

- Studied rate-monotonic scheduling, utilization bounds, and exact schedulability tests. This is real-time systems theory, not evidence that an RTOS was implemented on the MSP430.
- Developed interrupt-driven MSP430 code and worked with peripheral communication in coursework.
- Tailored letters mention TCP client/server communication, C/C++ unit testing, and timing-conscious use of print/LED diagnostics. Retain these as confirmation leads until the course or project is identified.
- Coursework claims also include DSP, Fourier/Laplace analysis, and real-time control concepts. Keep these as academic theory unless a concrete implementation or laboratory artifact is recovered.

## Linux and Operating-System Experiments

### Windows Subsystem for Linux

- Set up an Ubuntu environment under WSL to compile C programs and become comfortable with Linux shells, command-line tools, paths, and build workflows.
- Later used Arch Linux under WSL for the Qiskit/Aer quantum-search environment.

### Arch Linux, boot configuration, and virtualization

- Used Arch Linux as a daily-driver environment and worked with operating-system installation/configuration, UEFI settings, boot sequences, and VirtualBox.
- Built a Garuda Linux, Ubuntu, and Windows multi-boot setup managed through GRUB.
- An archived résumé includes an HDMI-triggered systemd service that switched between integrated and discrete GPU configurations. Preserve it here as Linux/systemd history, but Connor has explicitly rejected it as too low-value for a résumé now that professional Embedded Linux service work supersedes it.

### Chromebook Conversion

- Converted a Lenovo Chromebook into a Windows 11 note-taking computer while retaining use of its touchscreen and stylus.
- Worked through operating-system flashing, compatibility errors, recovery, and troubleshooting.

These projects are now superseded on the main résumé by professional Yocto/Arago, device-tree, systemd, watchdog, boot-diagnostic, and firmware-flashing work.

## Calculator Programming and Device Exploration

- Wrote TI-Basic programs for vector operations including cross products and dot products.
- Explored Game Boy/Game Boy Color emulation on calculator hardware.
- Used the work to understand that constrained everyday devices still expose processors, software, storage, and platform limitations.

## Related Project Sources

- See `ece-306.md` for the MSP430 embedded vehicle and later teaching-assistant work.
- See `senior-design.md` for the EV Active Sensor Adapter system architecture and firmware prototyping.
- See `aegis-power-systems.md` for professional power conversion, embedded Linux, protocol debugging, and tooling.

## Resume Selection Guidance

- Do not add the Chromebook, personal multi-boot/GPU service, calculator, or AutoHotkey projects to the general embedded résumé; professional Linux and firmware work makes them redundant.
- Consider the HDL, logic, quantum-search, or algorithm projects only for narrowly targeted digital-design/software applications.
- Keep the early 555/power experiment in the source archive, but lead power-electronics applications with the professional programmable bidirectional buck-boost work.

## Details Requiring Confirmation

- Which HDL projects used Verilog, whether any used VHDL, and what was implemented or verified in Vivado
- Course/date and individual contribution for the Kogge–Stone adder and SIPO/PISO/BCD ALU
- Exact ECE 469 team/individual scope and classical comparison method
- Named projects supporting Dijkstra, linked lists, search trees, TCP client/server work, and C/C++ unit testing
- Which DSP, control, and real-time topics had implementation or laboratory work versus lecture-only coverage
