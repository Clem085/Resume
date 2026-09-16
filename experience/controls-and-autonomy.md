# Controls, Robotics, and Autonomous-Vehicle Experience

This file consolidates Connor's controls work across Python robotics simulation, synchronous Lustre software, CARLA autonomous-driving simulation, and related embedded systems. It is the source for controls-, vehicle-, robotics-, and autonomous-systems résumé variants.

## Evidence Summary

- **Artifact-supported:** Connor-authored Spring 2026 files in [`Clem085/rtos-ml`](https://github.com/Clem085/rtos-ml) include a stateful Lustre PID cruise controller and Python CARLA agent integration.
- **Direct plus artifact-supported:** Connor reports tuning/evaluating the Lustre and CARLA controls; retained source and documentation show the controller state, saturation, agent integration, target speed, route completion, collision, and lane-invasion instrumentation.
- **Artifact-supported:** [`Clem085/RoboticsControls`](https://github.com/Clem085/RoboticsControls) contains Connor-attributable Python controller and simulation work within an NC State/BYU course framework.
- **Professional connection:** AEGIS work adds embedded C, real-time power control, MATLAB/CAN filter comparison, FreeRTOS, CAN/J1939, PWM/ADC validation, and hardware-facing debugging.

The exact NC State course number for the Spring 2026 real-time/autonomous-driving work is inconsistent across the newest direct description and retained course materials. Public résumé versions should use a neutral project title rather than an unverified course number.

## Controls Progression

Connor's strongest controls story spans several abstraction levels:

1. Python dynamics simulation and PD/PID/cascaded control for robotics plants.
2. Deterministic, discrete-time PID implementation in Lustre.
3. Python integration and tuning of PID-based longitudinal control in CARLA.
4. Professional embedded-C filtering, PWM/ADC control, CAN/J1939, RTOS, and system validation.

This supports presenting Connor as an embedded/computer engineer with hands-on controls implementation and validation—not only theoretical controls coursework.

## Robotics and Digital Controls — Python Simulation

**Setting:** NC State robotics-controls coursework, Fall 2025  
**Evidence:** Connor-attributable controller files, reports, plots, and commit history in [`Clem085/RoboticsControls`](https://github.com/Clem085/RoboticsControls)

- Extended course-provided Python simulations for mass-spring-damper, planar-VTOL, and Hummingbird systems.
- Derived and documented nonlinear/linearized dynamics, equilibrium inputs, transfer functions, state-space models, and pole-placement relationships.
- Implemented or modified PD, PI, and digital PID controllers with discrete integrators and dirty derivatives.
- Developed cascaded inner/outer control loops for the Hummingbird model, including longitudinal pitch PID, inner roll PD, and outer yaw PI behavior.
- Worked with command and actuator saturation, anti-windup back-calculation, motor-force/PWM mixing, model mismatch, and parameter perturbations.
- Used simulated reference responses and plots to evaluate tracking behavior, settling, actuator effort, saturation, and steady-state error.

### Resume-ready wording

- Extended Python simulations for mass, planar-VTOL, and Hummingbird systems; derived linearized/state-space models and tuned PD/PID/cascaded controllers with saturation, anti-windup, and actuator/PWM mixing using response plots.

### Boundaries

- The repository includes substantial BYU/NCSU course scaffolding. Attribute Connor's controller, dynamics, analysis, and documentation changes; do not claim authorship of the entire framework.
- This was simulation/coursework, not deployed robot firmware or production vehicle control.
- Retained documentation includes supplied expected behavior and tuning guidance; do not claim unsupported numerical settling-time, error, or robustness results.

## Synchronous PID Cruise Control — Lustre

**Setting:** NC State real-time/autonomous-driving coursework, Spring 2026
**Evidence:** Connor-authored commit and retained `RTOS-ARC/hw3/p4/cruisectr2.lus`

- Implemented PID cruise-control logic in Lustre, a deterministic synchronous dataflow language.
- Represented controller configuration with proportional gain, integral time, derivative time, execution timestep, setpoint, measured input, and upper/lower output limits.
- Maintained proportional, integral, derivative, and output state across discrete execution ticks using Lustre's previous-state semantics.
- Initialized controller and cruise state explicitly and updated target speed through stateful toggle/increment/decrement logic.
- Computed error, proportional/integral/derivative contributions, gain application, and bounded actuator pressure output.
- Simulated and tuned the controller while considering speed tracking, settling behavior, smoothness, disturbance response, and comparison with an earlier controller.
- Connected control theory with deterministic embedded-software concerns: initialization, bounded outputs, repeatable state updates, and fixed execution steps.

### Related formal verification

- Modeled synchronous state-machine/control behavior in Lustre and compiled models into executable C artifacts.
- Used Luke bounded model checking, induction, temporal properties, and counterexample traces to find incorrect monitors and revise state logic.
- Retained results support verification of required properties within the configured checks; this was academic formal verification, not production safety certification.

### Resume-ready wording

- Implemented and simulated a discrete-time PID cruise controller in Lustre using initialized state, previous-sample feedback, deterministic ticks, and output saturation; separately used Luke counterexample traces to correct temporal monitors and verify state-machine properties.

## CARLA Autonomous-Vehicle Control — Python

**Setting:** NC State real-time/autonomous-driving coursework, Spring 2026; three-person academic team
**Evidence:** Connor-authored repository commit, `MyPID.py`, `my_automatic_control.py`, retained documentation, and Connor's direct description

- Integrated a Python `MyPID` agent into CARLA's autonomous-driving application flow.
- Connected higher-level agent and route-planning behavior with lower-level longitudinal target-speed control.
- Passed target/control configuration through the agent layer and worked with CARLA's local/global planning architecture.
- Tuned and evaluated longitudinal PID behavior, considering speed tracking, overshoot, oscillation, responsiveness, and stable driving.
- Ran simulated driving tests in CARLA Town10HD.
- Evaluated route-level behavior using completion time, collisions, and lane invasions rather than judging controller response only by visual appearance.
- Iterated on target speed and controller behavior to balance route speed with stable and safe simulated operation.

### Resume-ready wording

- On a three-person team, integrated and evaluated PID-based longitudinal control in CARLA's Python agent/local-planner stack, tuning target-speed behavior and comparing route time, collisions, and lane invasions in Town10HD.

### Boundaries

- This was academic autonomous-driving simulation, not production autonomous-vehicle software, road testing, or safety certification.
- The retained peer record identifies two teammates; do not present the CARLA assignment as a solo project.
- The retained `MyPID.py` wraps CARLA agent/planner behavior; the repository does not retain the modified `local_planner.py` or a standalone low-level PID equation for CARLA.
- The recovered launcher passes an empty `pidVars` dictionary. Connor directly confirms PID integration/tuning, but final gains and parameter-propagation code are not retained; do not publish numerical coefficients or quantified improvement.
- Do not claim reliable stop-sign behavior. The retained agent documentation explicitly says stop signs are ignored.

## Job-Relevant Combined Themes

- Embedded C plus Python control and analysis tooling
- PID/PI/PD, cascaded loops, tuning, saturation, anti-windup, and discrete-time state
- Deterministic synchronous control and real-time scheduling concepts
- Dynamic-system modeling, controller simulation, tuning, and functional evaluation
- CAN/J1939 and hardware/software integration from professional firmware work
- Requirements, interface definitions, staged subsystem tests, and design reviews from senior design
- Schematics, datasheets, JTAG, oscilloscopes, logic analyzers, and cross-layer fault isolation

## Claim Boundaries for Targeted Résumés

- Keep robotics, Lustre, and CARLA work visibly academic; do not blur it into AEGIS employment.
- No retained evidence supports Simulink, Stateflow, Model-in-the-Loop, or tool-specific Model-Based Design. Do not add those claims, LIN, automotive Ethernet, hydraulic controls, Hardware-in-the-Loop, continuous integration, or production vehicle deployment without new evidence.
- Do not label standups as Agile/Scrum unless Connor confirms that development process.
- Do not claim universal controller optimality or unsupported quantitative improvement.
- Keep professional FreeRTOS/PIC32 and TMS320 work separate from Linux/POSIX academic scheduling.
