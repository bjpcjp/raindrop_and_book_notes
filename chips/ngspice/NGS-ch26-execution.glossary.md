---
title: "NGS-ch26-execution — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch26-execution]
---

- **.ac** — Control directive for frequency domain AC analysis specifying sweep type and range.  
- **.dc** — Control directive for DC sweep analysis over specified source values.  
- **.end** — Statement marking the end of a circuit description file.  
- **.model** — Defines parameters for semiconductor device or Code Models used in the simulation.  
- **.op** — Directive to compute the operating point or quiescent DC solution of the circuit.  
- **.subckt** — Begins the definition of a reusable subcircuit with specified nodes.  
- **.tran** — Directive to perform transient time-domain simulation specifying time step and duration.  
- **.ends** — Marks the end of a subcircuit definition.  
- **Code Model** — User-programmable device model written in C for simulating complex or non-ideal device behavior.  
- **Control Directive** — Line starting with a dot (.) that instructs the simulator on analysis type or options.  
- **Device Model** — Mathematical representation of a circuit component like a diode or transistor.  
- **Digital Node** — Node type simulated by an event-driven algorithm for faster digital circuit simulation.  
- **Event-Driven Algorithm** — Simulation method that updates only when events occur, improving efficiency.  
- **Node** — Connection point in a circuit identified by an alphanumeric label; ‘0’ is reserved for ground.  
- **Node Bridge Model** — Model that translates simulation data between analog and event-driven (digital) algorithms or different node types.  
- **Nutmeg** — The user interface tool used to create and interact with SPICE circuit descriptions and simulations.  
- **Parameter** — A numeric or symbolic attribute that defines model or device behavior.  
- **Poles and Zeros** — (Implied in behavioral sources) Parameters defining frequency response characteristics.  
- **Resistor (R)** — A passive circuit element defined by its resistance value and connected nodes.  
- **Subcircuit (Subckt)** — A hierarchical grouping of devices functioning as a single block in a circuit.  
- **Supply Ramping** — Simulation option that gradually increases supply voltages and initial conditions during transient analysis.  
- **User-Defined Node** — Custom node type supporting arbitrary data and integrated with the event-driven algorithm.  
- **Voltage Controlled Voltage Source (E)** — Ideal device used to simulate amplifiers; output voltage controlled by input voltage.  
- **XSPICE** — Extension of NGSPICE supporting Code Models, User-Defined Nodes, and mixed analog/digital simulation.
