---
title: "NGS-ch06-transmission-lines — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch06-transmission-lines]
---

- **ABS** — Absolute breakpoint control parameter used to manage simulation accuracy during transient analysis.  
- **AC Analysis** — Frequency domain analysis type not supported by KSPICE lossy transmission line models.  
- **Breakpoints** — Specific time points where the simulation solver adjusts step sizes to maintain accuracy.  
- **Characteristic Impedance (Z0)** — The inherent impedance of a transmission line, usually specified for lossless lines.  
- **COMPACTABS** — Absolute tolerance parameter for history compaction in convolution-based simulation.  
- **COMPACTREL** — Relative tolerance parameter for history compaction affecting simulation speed and accuracy.  
- **Convolution Method** — Technique for simulating lossy transmission lines by convolving impulse responses with inputs.  
- **Coupled Multiconductor Line (CPL)** — Model of multiple, interacting transmission lines without frequency-dependent loss.  
- **Distributed Parameters** — Transmission line properties (resistance, inductance, conductance, capacitance) spread continuously along its length.  
- **FREQ (Frequency)** — Frequency parameter used to define normalized electrical line length in lossless lines.  
- **Impulse Response** — Output signal of a system in response to an impulse input, fundamental to convolution simulation.  
- **Initial Conditions (IC)** — Starting voltage and current values required for transient simulation with UIC option.  
- **KSPICE** — Simulator which uses recursive convolution and Pade approximations for efficient lossy line transient simulation.  
- **LEN (Length)** — Physical length of a transmission line, critical for modeling delay and distributed effects.  
- **LTRA Model** — An improved lossy transmission line model using recursive convolution offering better accuracy and speed.  
- **Lossless Transmission Line** — A transmission line model ignoring resistive and conductive losses, defined by Z0 and delay.  
- **Lossy Transmission Line** — Transmission line model including resistance and conductance, modeled using more complex methods.  
- ** MIXEDINTERP** — Flag selecting between linear and quadratic interpolation based on dynamic criteria.  
- **NOSTEPLIMIT** — Flag allowing time steps longer than the line delay in simulation, potentially reducing accuracy.  
- **NO CONTROL** — Flag disabling automatic timestep control based on convolution error, for faster but less accurate simulation.  
- **Normalized Electrical Length (NL)** — Normalized measure of a transmission line’s electrical length relative to a wavelength.  
- **Pade Approximation** — Mathematical approach used to obtain recursive convolution impulse responses in lossy line models.  
- **REL** — Relative breakpoint control parameter influencing solver accuracy and performance in transient simulation.  
- **Recursive Convolution** — Computational method for simulating lossy lossy transmission lines by using impulse responses efficiently.  
- **RLGC Parameters** — Matrix parameters representing resistance (R), inductance (L), conductance (G), and capacitance (C) per unit length.  
- **SPICE3f5** — Original SPICE simulator version implementing state-based lossy transmission line models.  
- **StepWise Equivalent Conductance (SWEC)** — Technique referenced for timing simulation of CMOS circuits related to transmission lines.  
- **TXL Model** — KSPICE single lossy transmission line model using recursive convolution, for transient simulation only.  
- **UIC (Use Initial Conditions)** — Simulation option activating the use of specified initial voltages and currents on transmission lines.  
- **Uniform Distributed RC Line (URC)** — Model approximating a transmission line with a segmental resistor-capacitor ladder network.
