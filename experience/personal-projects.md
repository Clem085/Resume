# Technical and Personal Projects

These projects preserve useful technical history from older résumés. Most are no longer strong enough for the general résumé because later professional work demonstrates the same skills at greater depth, but they can support project-focused, software, digital-design, or early-career variants.

## Discrete Power-Circuit Experiments

- Prototyped charge-pump and boost-converter circuits to create a higher-voltage supply when the required barrel-jack adapter was unavailable.
- Built a 555-timer astable multivibrator and used a potentiometer to make the switching frequency adjustable.
- Explored switching, capacitor charge transfer, voltage/current tradeoffs, and the practical difference between a target voltage and a supply that can support the required load.
- Used a Keysight programmable power supply in an NC State laboratory to characterize the device's required voltage/current behavior before building the circuit.
- An archived résumé describes a 5 V to 9 V target. Treat this as an exploratory learning project, not as a regulated or efficiency-validated converter design.

## ECE 212 — Sequential-Logic Vending Machine, Spring 2024

- Designed and built a sequential-logic vending-machine circuit on a breadboard.
- Validated logic behavior with WaveForms and an Analog Discovery 2.
- Reduced gate usage while preserving the required state behavior.
- Demonstrated digital-logic design, breadboard implementation, structured test, and hardware troubleshooting.

## ECE 309 — C++ Maze Solver and Search Algorithms, Spring 2024

- Implemented breadth-first search, depth-first search, and greedy best-first search in C++.
- Compared behavior across multiple maze configurations.
- Examined runtime and memory tradeoffs among the three search strategies.
- Useful for software/algorithm variants, but less relevant than production firmware and hardware-integration experience for a general embedded résumé.

## LC-3 Assembly Translation Tool

- Built binary, hexadecimal, and numeric conversion logic as part of an assembly-processing tool.
- Parsed an assembly file, removed comments, interpreted instructions, and wrote the corresponding binary representation to an output file.
- The archive does not establish a complete production assembler with full symbol resolution, so describe it as an assembly translation/parser project rather than a complete compiler.

## AutoHotkey Build Automation

- Learned AutoHotkey to automate repetitive desktop tasks.
- Created a shortcut-driven workflow that opened, compiled, and executed LC-3 assembly work that otherwise required a repeated sequence of commands.
- Shared the workflow with classmates; no verified time-savings metric is available.

## Linux and Operating-System Experiments

### Windows Subsystem for Linux

- Set up an Ubuntu environment under WSL to compile C programs and become comfortable with Linux shells, command-line tools, paths, and build workflows.

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

- Do not add the Chromebook, WSL, calculator, or AutoHotkey projects to the general embedded résumé; professional Linux and firmware work makes them redundant.
- Consider the logic or algorithm projects only for narrowly targeted digital-design/software applications.
- Keep the early 555/power experiment in the source archive, but lead power-electronics applications with the professional programmable bidirectional buck-boost work.
