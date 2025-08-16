---
title: "NGS-ch23-optimization — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch23-optimization]
---

- **.control section** — A block in ngspice netlists used to run commands, define simulations, and perform measurements during simulation.  
- **AC simulation** — A frequency domain analysis that calculates circuit response to small sinusoidal stimuli at varying frequencies.  
- **Altermod command** — An ngspice command used to simulate changes in model parameters, helpful for corner analysis.  
- **ASCO** — A standalone optimization program using a differential evolution algorithm that interfaces with ngspice for circuit parameter tuning.  
- **ASCO manual** — The documentation for ASCO, providing configuration, examples, and instructions for setup with ngspice.  
- **Cost function** — A mathematical function combining optimization objectives and constraints, which the optimizer seeks to minimize or maximize.  
- **Differential Evolution** — An optimization algorithm that iteratively improves candidate solutions based on population differences.  
- **.measure statement** — An ngspice command used to extract performance metrics from simulation data, often used for optimization measurements.  
- **Monte Carlo analysis** — A statistical method that simulates circuit parameter variations to assess robustness and performance spread.  
- **Model parameter files** — Files defining transistor or device parameters used by ngspice to model semiconductor devices.  
- **Multi-core processing** — The use of multiple CPU cores concurrently to accelerate simulation and optimization runs.  
- **ngspice** — An open-source circuit simulator providing the simulation engine for analog and mixed-signal circuit analysis.  
- **ngspice scripting language** — The internal scripting environment of ngspice enabling automated control and basic optimization tasks.  
- **ngspice_c.exe** — The console version of ngspice executable used for command-line simulations and optimization interfacing.  
- **Optimization constraints** — Conditions specified to limit circuit performance parameters within desired bounds during optimization.  
- **Optimization objectives** — Performance parameters the optimizer seeks to maximize or minimize during circuit tuning.  
- **Optimization parameters (variables)** — Circuit component values or device sizes adjustable by the optimizer to improve performance.  
- **Parallel processing** — Running multiple simulations simultaneously to improve optimization speed and efficiency.  
- **Phase margin** — A measure of stability in amplifiers, representing how far the system is from oscillation at the unity gain frequency.  
- **.param statement** — ngspice command used to define parameter values, which can be referenced in the netlist or measurement commands.  
- **Post processing** — Analysis performed after simulation to refine results, often done outside ngspice to handle data not easily processed inside.  
- **Python optimizer script** — An external Python program using optimization algorithms (like differential evolution) to control ngspice simulations.  
- **S11, S21 parameters** — Scattering parameters representing input reflection and forward transmission used in RF circuit analysis.  
- **Simulation corners (corner analysis)** — Simulations run at varied process, voltage, and temperature extremes to verify circuit robustness.  
- **Slew rate** — The maximum rate of change of an amplifier’s output voltage, important for transient performance.  
- **Starter set of variables** — Initial values for optimization parameters from which the optimizer begins searching for better solutions.  
- **Tclspice** — A Tcl/Tk based scripting extension for ngspice, allowing advanced simulation control and optimization scripting.  
- **Voltage, process, temperature corners** — Specific variations in supply voltage, fabrication parameters, and operating temperature for robustness testing.
