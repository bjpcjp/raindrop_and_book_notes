---
title: "NGS-ch21-example-circuits — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch21-example-circuits]
---

- **AC Analysis** — A simulation mode that calculates the circuit’s frequency response to small signal inputs over a specified frequency range.  
- **Bipolar Junction Transistor (BJT)** — A semiconductor device used to amplify current, modeled in SPICE as npn or pnp types with specific parameters.  
- **DC Analysis** — A simulation mode that finds the steady-state operating point (bias voltages and currents) of a circuit with no time variation.  
- **Differential Pair** — A basic transistor configuration used for amplifying the difference between two input signals.  
- **Exported Node** — A circuit node labeled with a name or number used to reference voltages or currents in simulation commands.  
- **Four-Bit Binary Adder** — A digital circuit design made up of interconnected logic gates to add two 4-bit numbers, simulated here with transistor-level models.  
- **MOSFET** — Metal-Oxide-Semiconductor Field-Effect Transistor, a type of transistor modeled with parameters like threshold voltage and channel length in SPICE.  
- **Ngspice** — An open-source circuit simulator compatible with Berkeley SPICE3 syntax for analyzing electronic circuits.  
- **Operating Point (.op)** — The DC bias condition of a circuit, defining node voltages and device operating states without transient or AC effects.  
- **Plot Command** — A simulator command used to graph voltage and current waveforms or expressions after simulation runs.  
- **Pulse Source (PULSE)** — A time-dependent voltage or current source defined by parameters such as delay, rise/fall time, and pulse width, used for transient simulations.  
- **RC Network** — A configuration of resistors and capacitors that determine time constants and frequency responses in analog circuits.  
- **RTL Inverter** — Resistor-Transistor Logic inverter, a simple digital logic gate simulated with bipolar transistors and resistors.  
- **Run Command** — Executes the simulation based on the current analysis settings in ngspice.  
- **Small-Signal Analysis** — An investigation of a circuit’s linear behavior for small input amplitudes, often in frequency domain (AC analysis).  
- **SPICE-Compatible Devices** — Electronic components modeled according to SPICE syntax and conventions, such as resistors, capacitors, transistors, and voltage sources.  
- **Swept DC Analysis** — A DC simulation that varies a parameter (like voltage) incrementally to observe circuit response over a range.  
- **Termination Resistor** — A resistor commonly used in transmission line circuits to match impedances and avoid reflections.  
- **Transient Analysis (.tran)** — A simulation mode to analyze circuit behavior as voltage and currents change over time.  
- **Transmission Line (Tline)** — Circuit elements that model signal propagation delays and characteristic impedance of transmission media.  
- **Voltage Source** — A circuit element that provides a defined voltage, can be DC, AC, pulse, or sine waveforms.  
- **Voltage Node** — A point in the circuit where voltage is measured relative to a common reference, typically ground.  
- **XSPICE** — An extension of SPICE that adds new device models and simulation options but is not required to run classic SPICE circuits in ngspice.
