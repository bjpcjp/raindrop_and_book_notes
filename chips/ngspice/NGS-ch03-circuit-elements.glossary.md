---
title: "NGS-ch03-circuit-elements — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch03-circuit-elements]
---

- **AC resistance (ac)** — Resistance value used only during AC analysis, different from the DC resistance if specified.  
- **Binning** — Technique to partition geometry-dependent model parameters into size ranges for improved accuracy.  
- **Capacitor (C)** — Two-terminal device storing electrical energy as capacitance, defined by value or geometry and model data.  
- **Coupled inductors (K)** — Two inductors magnetically linked with a coefficient of coupling between 0 and 1.  
- **Device nodes (n+, n-)** — Terminals of circuit elements where connections are made, positive and negative respectively.  
- **Exponential temperature coefficient (tce)** — Coefficient describing exponential temperature dependence of resistance.  
- **Flicker noise** — Low-frequency noise (1/f noise) in resistors and capacitors modeled with specific parameters.  
- **Frame multiplier (m)** — Parameter used to represent multiple parallel devices as a single element with scaled electrical properties.  
- **Hysteresis (VH, IH)** — Range voltage or current over which a switch changes state with difference between transition points.  
- **Inductor (L)** — Two-terminal device storing energy in a magnetic field, defined by inductance or physical parameters and model.  
- **Initial condition (IC)** — Starting value of voltage or current in capacitors and inductors used in transient analysis.  
- **Multiplier recursion (subcircuits)** — Mechanism where subcircuit multipliers multiply embedded device multipliers recursively.  
- **Model parameters** — Set of physical, geometrical, or behavioral characteristics defining device behavior and temperature dependencies.  
- **Mutual inductance** — Interaction parameter between two inductors representing their magnetic coupling.  
- **Node set (.NODESET)** — Control command to specify initial guesses for node voltages to enhance convergence.  
- **Noise keyword (noisy)** — Parameter to enable or disable noise generation in resistors.  
- **Off-resistance (ROFF)** — High resistance value representing the switch’s open state resistance.  
- **On-resistance (RON)** — Low resistance value representing the switch’s closed state resistance.  
- **Paralleling devices** — Representing multiple identical devices in parallel via multiplier to simplify circuit description.  
- **Sheet resistance (RSH)** — Resistance per square unit of a thin conductive film used to calculate semiconductor resistor values.  
- **Semiconductor capacitor** — Capacitor whose value is calculated using physical geometry and process model parameters.  
- **Semiconductor resistor** — Resistor modeled based on geometry, process parameters, and temperature coefficients.  
- **Switch** — Device that can connect or disconnect a circuit path, voltage or current controlled, with defined ON/OFF states.  
- **Temperature coefficient (tc1, tc2)** — Parameters describing linear and quadratic changes of device values with temperature.  
- **Transient analysis (UIC)** — Simulation mode that uses specified initial capacitor voltages and inductor currents.  
- **Voltage controlled switch (S device)** — Switch controlled by voltage between two designated control nodes.  
- **Voltage multiplier in subcircuits** — Parameter method enabling recursive scaling of device count inside nested subcircuits.
