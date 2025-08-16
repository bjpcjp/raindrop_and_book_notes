---
title: "NGS-ch15-batch-analysis-output — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch15-batch-analysis-output]
---

- **AC Analysis** — Small-signal frequency domain analysis to determine circuit response over a range of frequencies.
- **ABSTOL** — Absolute current error tolerance controlling simulation accuracy in DC calculations.
- **.CONTROL Section** — Scripted command block in input files that executes commands interactively or within batch mode.
- **DC Analysis** — Simulation of steady-state circuit behavior with capacitors open and inductors shorted.
- **DERIV(ATIVE)** — Measurement of the derivative of a variable at a specified time or event point.
- **DISTO Analysis** — Distortion analysis using Volterra series to evaluate harmonic and intermodulation distortion.
- **.END** — Marks the end of a SPICE input file.
- **.IC (Initial Conditions)** — Sets initial node voltages for transient analysis to aid or bypass initial operating point solutions.
- **Interpolation (INTERP)** — Option to linearly interpolate output data on fixed time steps without affecting simulation.
- **.MEASURE** — Command for post-processing simulation data to extract timing, voltage, current, or other parameters.
- **.MODEL Parameters** — Device-specific parameters defining component behavior in simulations.
- **NOOPAC** — Option to skip operating point calculation before AC analysis for linear circuits.
- **Node Voltage** — Voltage measured at a circuit node, relative to ground or another node.
- **.NODESET** — Provides initial voltage guesses for nodes to assist convergence in DC or transient analysis.
- **Operating Point (.OP)** — The steady-state DC solution of the circuit before AC or transient analyses.
- **.OPTIONS** — Command line or input file parameters to adjust simulator behavior and accuracy.
- **.PLOT** — Defines printer plot output for batch mode, graphically showing simulation results.
- **.PRINT** — Specifies variables and analysis types for textual tabular output in batch mode.
- **.PROBE / .SAVE** — Commands to select vectors (voltages, currents, device data) saved into raw output files.
- **RAW File** — Output file format storing simulation data for later interactive analysis or plotting.
- **RELATIVE TOLERANCE (RELTOL)** — Controls relative error convergence threshold for simulation iterations.
- **SOA (Safe Operating Area)** — Limits specified to warn if device operating conditions exceed safe electrical boundaries.
- **SRCSTEPS** — Option limiting the number of source-stepping iterations used in transient simulations.
- **.TF (Transfer Function)** — Calculates DC small-signal gain, input, and output resistance for specified input and output variables.
- **Transient Analysis (.TRAN)** — Time-domain simulation of circuit response to time-varying inputs.
- **TRTOL** — Transient error tolerance parameter controlling integration error estimates.
- **Voltage Source Branch Current** — Current flowing through an independent voltage source, directly accessible in simulations.
- **WARN Option** — Enables or disables warnings related to device safe operating area violations.
- **.WIDTH** — Sets maximum character width for print and plot outputs in batch mode.
