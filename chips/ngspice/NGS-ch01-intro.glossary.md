---
title: "NGS-ch01-intro — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch01-intro]
---

- **AC Analysis** — Small-signal analysis that determines circuit response to sinusoidal inputs over a range of frequencies.
- **Analog Simulation** — Simulation focused on continuous-time, linear and nonlinear behavior of circuits using Kirchhoff’s laws.
- **BJT (Bipolar Junction Transistor)** — A transistor model based on Gummel-Poon or Ebers-Moll models to simulate bipolar devices.
- **CIDER** — Mixed-level circuit and device simulator integrated into ngspice that combines compact and numerical device models.
- **DC Analysis** — Determines the steady-state operating point of a circuit with inductors shorted and capacitors opened.
- **Digital Simulation** — Simulation method focusing on logic state changes and event-driven updates without solving circuit equations.
- **DSIM** — Internal C-based numerical device simulator within CIDER for one- and two-dimensional semiconductor device modeling.
- **Event** — A change in logic state in digital simulation that triggers updates to connected circuit elements.
- **Mixed-Level Simulation** — Simulation combining numerical device models with compact models for improved accuracy in critical devices.
- **Mixed-Mode Simulation** — Simulation combining both analog (continuous) and digital (event-driven) algorithms within a single simulator.
- **Mutual Inductor** — An inductor model incorporating magnetic coupling between coil elements.
- **Ngspice** — General-purpose circuit simulator supporting linear, nonlinear, analog, digital, and mixed-mode analyses.
- **NR Algorithm (Newton-Raphson)** — Iterative method used to solve nonlinear circuit equations for convergence.
- **Pole-Zero Analysis** — Computes poles and zeros of the small-signal AC transfer function for a circuit.
- **Pulse Source** — A waveform source used in transient analysis that switches between voltage or current levels.
- **RELTOL** — Relative tolerance parameter controlling convergence precision in node voltages and branch currents.
- **Sensitivity Analysis** — Analysis measuring the effect of parameter variations on circuit output variables.
- **Small-Signal Distortion Analysis** — Computes harmonic and intermodulation distortion products caused by small input signals.
- **Temperature (Circuit)** — Parameter defining the thermal conditions for simulation, affecting device behavior and parameters.
- **Transient Analysis** — Time-domain simulation that computes circuit responses as a function of time, starting from DC operating point.
- **User-Defined Node** — A node type in ngspice that propagates arbitrary data using event-driven simulation, beyond voltages or logic states.
- **VNTOL** — Absolute voltage tolerance used in convergence criteria to handle nodes with near-zero voltages.
- **XSPICE** — An extension providing mixed-signal simulation capabilities, including pure digital simulation and code-model interfacing.
