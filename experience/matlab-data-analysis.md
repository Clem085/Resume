# MATLAB, Data Analysis, and Modeling Experience

This file consolidates Connor's professional and academic MATLAB work. The items below are intentionally separated by setting: the AEGIS filter-analysis tool is professional engineering work, while the MOSFET, signals, linear-algebra, and machine-learning work is coursework.

## Evidence Summary

- **Direct:** Connor described the AEGIS CAN/ADC filtering work and identifies MATLAB as a strong programming language.
- **Artifact-supported:** retained Spring 2024 ECE 220 MATLAB scripts and submitted lab PDFs cover signals, complex functions, transfer functions, matrices, and differential equations.
- **Artifact-supported:** the March 2025 ECE 302 MOSFET report contains measured datasets, MATLAB analysis code, plots, parameter extraction, and measured-versus-modeled comparisons.
- **Artifact-supported:** the March 2025 `301_MATLAB_AI_LEARNING.pdf` assignment contains MATLAB image classification, CNN training/evaluation, transfer learning, PCA, least-squares projection, and visualization work. The PDF itself is titled only `HW8`; its archive filename suggests ECE 301, so confirm the course number before publishing it.

## AEGIS Power Systems — ADC Filter Analysis and CAN Data Visualization

**Setting:** AEGIS Power Systems — full-time Embedded Firmware Engineer, May 2026–Present

### Engineering problem

- ADC-derived voltage and current readings could fluctuate enough to make raw output difficult to interpret or use directly.
- Filtering could reduce that fluctuation, but an overly smooth filter could delay recognition of genuine, rapid voltage or current changes.
- The selection problem therefore required balancing reading variation under steady input against the time needed to follow a large electrical change, rather than simply minimizing visible variation.
- Correct scaling also had to be established so the filter comparison operated on meaningful telemetry rather than misleading raw values.

### Monitoring-card and embedded-firmware context

- The data came from four-channel `VIN`, `IIN`, `VOUT`, and `IOUT` power-converter telemetry; the exact electrical ranges were supporting context, not the main engineering accomplishment.
- Channel conversion used per-channel scale factors and calibration logic to translate ADC output into engineering telemetry.
- Connor implemented a rolling average in embedded C using a fixed sample window, circular replacement, persistent state, and a maintained rolling sum.
- The second selected technique was an exponential moving average (EMA), which retained only the previous filtered value and moved it toward each new sample by a fraction of the difference without a sample buffer.
- See [`adc-monitoring-card.md`](adc-monitoring-card.md) for the complete scaling math, C implementation, sampled-power considerations, and implementation boundaries.

### MATLAB analysis workflow

- Built a MATLAB data-analysis and plotting workflow for evaluating ADC filtering functions used in embedded firmware.
- Parsed captured CAN text output into data that MATLAB could compare and visualize.
- Determined and checked per-channel scaling factors from the captured output.
- Applied several filtering functions to the same dataset so their behavior could be compared directly.
- Evaluated both sides of the tradeoff:
  - stable readings with little variation while the underlying value was unchanged;
  - short response time when the underlying value changed drastically.
- Selected rolling-average and EMA approaches based on the plotted comparisons and used the results to guide embedded-firmware behavior.

### Team and communication context

- Participates in engineering standups as part of the full-time AEGIS role.
- Coordinates with a firmware team whose members are based remotely, communicating current work, test observations, blockers, technical constraints, and next steps.
- The filter-analysis workflow produces plots and captured-data comparisons that can support technical communication. Current evidence does not establish whether those plots were specifically presented during standups.

### Evidence boundaries

- Rolling-average implementation and selection of rolling-average and EMA approaches are confirmed. The other candidate functions, window length, EMA coefficient, sample cadence, CAN message format, dataset size, quantitative results, and whether both selected approaches were deployed have not been documented.
- Do not claim a measured noise reduction, latency improvement, deployment result, production calibration accuracy, or production-performance metric until Connor provides it.
- `Parsed CAN text output` means offline processing of captured textual CAN data; it does not by itself establish that MATLAB interfaced directly with the live CAN bus.
- The evidence supports heuristic comparison and engineering judgment. Do not describe this as automated optimization, machine-learned filtering, formal signal-processing validation, or a closed-loop controller.

## Electric Zero-Turn Mower Controls — MATLAB/Simulink

**Setting:** NC State controls work; exact course and term not yet recorded  
**Evidence:** Connor's direct August 2026 description; a retained `.slx` artifact has not yet been added to this résumé repository

- Used MATLAB and Simulink for Model-in-the-Loop development of electric zero-turn-mower controls.
- Developed tooling for PID tuning and control-logic testing.
- Created a repeatable method for finding and adjusting PID values.
- Compared simulated controller behavior with real-vehicle test behavior.
- Used the work to connect model-based controls, controller tuning, and validation with later Lustre, CARLA, robotics, and embedded-firmware experience.

### Evidence boundaries

- `MATLAB/Simulink` and `Model-in-the-Loop` are directly confirmed.
- Do not add Stateflow, automatic code generation, Hardware-in-the-Loop, production deployment, hydraulic controls, or quantitative results without additional evidence.
- The exact plant model, controller structure, individual/team split, term, and test procedure remain unrecorded.
- See [`controls-and-autonomy.md`](controls-and-autonomy.md) for the combined controls progression and targeted résumé guidance.

## ECE 302 — MOSFET Characterization and Parameter Extraction

**Date:** March 2025  
**Artifact:** `../history/academic-projects/matlab/Lab Report 5-Connor Savugot.pdf`

### Laboratory and data collection

- Characterized HEF4007 nMOS and pMOS devices across multiple gate-source and drain-source voltages.
- Collected current-voltage measurements manually and with the DCA Pro, including families of \(I_{DS}\)-versus-\(V_{DS}\) curves.
- Recorded data for multiple bias conditions and used captured text/CSV-compatible datasets for subsequent analysis.

### MATLAB analysis

- Loaded measured nMOS and pMOS datasets with `readmatrix` and organized voltage/current columns for analysis.
- Selected points by bias condition and operating region, then used linear fits with `polyfit` to estimate channel-length modulation.
- Used numerical operations including discrete differences, array filtering, averaging with omitted invalid values, and parameterized calculations.
- Computed or estimated device parameters including threshold voltage, transconductance, mobility, mobility degradation, channel-length modulation, and process transconductance.
- Produced labeled plots that distinguished operating regions and compared measured device behavior with fitted or predicted behavior.
- Analyzed the difference between idealized MOSFET equations and observed non-ideal behavior, including channel-length modulation and mobility degradation.
- Documented the experiment, raw data, MATLAB code, output tables, plots, interpretation, and limitations in a 26-page technical report.

### Evidence boundaries

- This is academic laboratory analysis, not production transistor characterization or semiconductor process engineering.
- Some retained report code contains placeholder assumptions and apparent data-selection/copy errors. The artifact supports MATLAB data handling, numerical fitting, plotting, and model comparison, but it should not be used to claim validated extraction accuracy or publish specific parameter values without rerunning the analysis.
- A résumé may accurately say `measured-versus-modeled MOSFET analysis`; avoid claiming development of a compact device model or SPICE model.

## Spring 2025 MATLAB Machine-Learning and Linear-Algebra Assignment

**Artifact:** `../history/academic-projects/matlab/301_MATLAB_AI_LEARNING.pdf`  
**Recorded assignment date:** March 7, 2025

### Image classification and neural networks

- Loaded a pretrained GoogLeNet model, resized an input image to the model's required dimensions, classified it, and displayed the predicted label.
- Defined and trained a convolutional neural network for handwritten-digit classification using image input, convolution, batch-normalization, ReLU, max-pooling, fully connected, softmax, and classification layers.
- Split the digit dataset into randomized training and validation sets, configured stochastic-gradient-descent-with-momentum training, and computed validation accuracy.
- The retained assignment reports **99.24% validation accuracy** for the handwritten-digit CNN.
- Adapted pretrained SqueezeNet for a five-class merchandise-image dataset by replacing its final convolutional and classification layers.
- Split the merchandise images into training, validation, and test sets, trained the modified network, and calculated test accuracy; the report describes the result as approximately **90%**.

### PCA, dimensionality reduction, and visualization

- Computed projections onto principal-component directions and compared the sample variance produced by different unit vectors.
- Applied PCA/Karhunen–Loève Transform helper routines to the Yale Faces dataset, sorted eigenvalues/eigenvectors, and visualized dominant eigenfaces.
- Projected high-dimensional facial-image data into a two-dimensional principal-component space and interpreted class separation and overlap.
- Used scatter plots, quiver plots, eigenvalue plots, tiled images, and image display functions to inspect data and model behavior.

### Least squares and projection matrices

- Solved a least-squares problem using the normal equation.
- Constructed a projection (`hat`) matrix, checked idempotence numerically, separated a vector into projected and residual components, and verified their orthogonality.
- Created a three-dimensional vector visualization for the input, projection, and residual.

### Evidence boundaries

- This work demonstrates MATLAB machine-learning APIs, data preparation, network configuration, evaluation, PCA, and numerical linear algebra.
- Do not describe the GoogLeNet example as training a model; it used an existing pretrained model for inference.
- The SqueezeNet work is transfer learning, not design of the base architecture.
- The PCA section calls supplied `LoadImgData` and `PcaViaKlt` helpers; do not claim implementation of PCA from first principles unless their source and Connor's authorship are recovered.
- The PDF supports assignment-level results, not a peer-reviewed study, novel AI method, production deployment, or embedded-ML implementation.
- Confirm whether ECE 301 is the correct course number before naming the course in a public résumé.

## ECE 220 — Analytical Foundations of ECE

**Term:** Spring 2024  
**Artifacts:** `../../MATLAB/ECE 220 Lab/` in the broader Programming directory

Connor completed a MATLAB-based analytical foundations sequence. Retained `.m` files and submitted PDFs support repeated use of scripts, functions, vectorized computation, plotting, matrix operations, and numerical interpretation.

### Lab 1 — Signals and operations

- Wrote vectorized scripts to generate and plot composite sinusoidal and pulse signals.
- Chose time-step resolution from the shortest period or pulse duration represented in a signal.
- Created a reusable half-wave rectifier function and compared original and rectified signals on the same axes.
- Used logical indexing, element-wise arithmetic, functions, plots, axes, labels, legends, and grids.

### Lab 2 — Signals and complex numbers

- Plotted exponential, damped sinusoidal, and piecewise pulse signals.
- Worked with Cartesian, polar, and exponential representations of complex values.
- Used custom conversion helpers and MATLAB's complex-number operations and visualization commands.

### Lab 3 — Complex functions and transfer functions

- Plotted magnitude and phase for continuous and discrete complex-valued functions.
- Evaluated and visualized an RLC circuit transfer function across frequency.
- Used vectorized complex arithmetic, `abs`, `angle`, `subplot`, continuous plots, and discrete stem plots.
- Interpreted frequency-response behavior rather than treating the plot as only a graphics exercise.

### Lab 4 — Vectors and matrices

- Solved an overdetermined system using reduced row-echelon form.
- Performed matrix multiplication, transposition, inversion, indexing, dimensional checks, and identity-matrix operations.
- Used MATLAB output formatting to make computed results inspectable.

### Lab 5 — Analytical solutions of differential equations

- Modeled and plotted first-order forced-circuit responses, comparing steady-state and total solutions.
- Analyzed and plotted underdamped and more heavily damped responses of a second-order mechanical system.
- Connected analytical differential-equation solutions with observable transient and steady-state behavior.

### Evidence boundaries

- The retained sequence establishes substantial undergraduate MATLAB use and supports listing MATLAB as a strong working language.
- The retained ECE 220 sequence alone does not establish Simulink, code generation, fixed-point design, MATLAB Coder, App Designer, control-system toolbox work, or production deployment. Separate direct evidence above establishes Simulink Model-in-the-Loop mower controls, but not the other capabilities.
- Some loose `.m` files in the programming archive are drafts or incomplete experiments. Prefer the submitted lab PDFs and complete report artifacts when supporting public claims.

## Transferable MATLAB Capabilities

- Parsing and organizing captured or measured engineering data
- Vectorized numerical computation and logical data selection
- Plotting time-series, electrical, multidimensional, and image data
- Curve fitting and measured-versus-modeled comparison
- Signal-response and filtering tradeoff analysis
- Matrix methods, least squares, PCA, and dimensionality reduction
- Dataset partitioning, neural-network configuration, transfer learning, and accuracy calculation
- Technical reporting that connects code, plots, measured behavior, and engineering interpretation

## Resume-Ready Bullet Options

### Best professional bullet

- Parsed captured CAN output in MATLAB to determine per-channel ADC scaling and compare several filter functions by steady-input variation and time to follow large electrical changes; selected rolling-average and EMA approaches and implemented the rolling average in embedded C using a circular buffer and rolling sum.

### Best model-based controls bullet

- Developed MATLAB/Simulink Model-in-the-Loop tooling for electric zero-turn-mower controls to tune PID gains, test control logic, and compare simulated response with real-vehicle test behavior.

### More implementation-focused professional option

- Parsed captured CAN output in MATLAB and compared multiple ADC-filter functions by steady-input variation and time to follow large changes, selecting fixed-window rolling-average and single-state EMA approaches for embedded firmware.

### Best power-focused academic option

- Analyzed measured nMOS/pMOS data in MATLAB using numerical fits and operating-region plots to extract device parameters and compare observed behavior with MOSFET models.

### Machine-learning-targeted academic option

- Trained and evaluated MATLAB image-classification models, including a handwritten-digit CNN with 99.24% validation accuracy and SqueezeNet transfer learning on a five-class dataset.

## Resume Selection Guidance

- For embedded firmware, power, controls, validation, or data-oriented roles, lead with the professional CAN/ADC filter-analysis bullet.
- For power-electronics or semiconductor roles, the ECE 302 MOSFET analysis is the strongest academic MATLAB example.
- For machine-learning or computer-vision roles, use the CNN/transfer-learning work, with the pretrained-model and academic boundaries intact.
- In a one-page general embedded résumé, MATLAB can remain in the language list plus one AEGIS filter-analysis bullet; the coursework belongs in the detailed experience library unless the job description specifically rewards modeling, signal processing, or ML.

## Details Worth Confirming

- Names and mathematical forms of candidates other than the confirmed rolling-average and EMA approaches
- Rolling-window length, EMA coefficient, and any numerical selection thresholds
- Which CAN fields carried each voltage/current value and the exact plot arrangement
- Whether the MATLAB analysis tool was retained for regression testing or team reuse
- Any defensible improvement metric for signal stability or transient response
- Correct course number and individual/team scope for the Spring 2025 AI assignment
- Whether the ECE 302 report was an individual or team submission
