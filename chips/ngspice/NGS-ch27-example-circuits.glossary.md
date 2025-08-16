---
title: "NGS-ch27-example-circuits — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch27-example-circuits]
---

- **Aamp** — An XSPICE code model device representing an amplifier with user-defined gain and offset.
- **Analog node** — Circuit node carrying continuous voltage or current signals used in analog simulation.
- **Code model** — A user-defined XSPICE device model created with custom executable code for simulation.
- **Digital node** — Circuit node carrying discrete logic states, used in event-driven digital simulation.
- **Eprint command** — Ngspice command that outputs a tabular listing of event-driven simulation data for analysis.
- **Gain block** — An XSPICE code model that simulates an amplifier with specified gain and offset parameters.
- **Node bridge** — An XSPICE model that translates between different node data types, such as digital to real or real to analog.
- **Ngspice** — A widely used open-source circuit simulator that supports the XSPICE extension for mixed-signal simulation.
- **Null node** — A special placeholder in XSPICE denoted as NULL, indicating an unconnected port in a device model.
- **Operating point** — The steady-state solution of circuit voltages and currents before transient simulation begins.
- **Op-amp subcircuit** — A subcircuit model in XSPICE representing an operational amplifier with gain-limiting behavior.
- **Pulse waveform** — A time-dependent voltage source generating a pulse signal, used for stimulating circuits.
- **Real node** — An XSPICE User-Defined Node type carrying real-valued event-driven data in simulations.
- **Ripple counter** — A digital circuit formed by flip flops used to divide a clock signal frequency.
- **Run command** — The ngspice command that starts transient or other specified circuit simulations.
- **Sampled-data system** — A system combining continuous analog signals with discrete digital events for simulation.
- **Subcircuit** — A hierarchical reusable block of circuit elements and models defined within ngspice.
- **Transient analysis** — A simulation mode analyzing circuit response over time with changing signals.
- **User-Defined Node** — A node type in XSPICE for carrying custom event-driven data not limited to logic states.
- **XSPICE** — An extension to ngspice enabling mixed-mode (analog, digital, and user-defined) simulation with code models.
- **XSPICE executable** — A custom ngspice simulator build that includes user-compiled XSPICE code models.
- **Zener diode (implied: device modeling)** — While not present explicitly, device modeling of nonlinear devices like transistors or comparators is implied by code models.
