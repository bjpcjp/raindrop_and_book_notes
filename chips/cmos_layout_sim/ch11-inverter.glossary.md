---
title: "ch11-inverter — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch11-inverter]
---

- **Buffer** — A cascade of inverters used to drive large capacitive loads with minimum delay.  
- **Cascaded Inverters** — A series of inverters where each subsequent inverter is larger by a factor to optimize delay.  
- **Capacitance (Input/Output)** — Parasitic or intentional charge storage elements seen at the input or output terminals of a gate.  
- **CMOS Inverter** — A digital logic circuit using complementary NMOS and PMOS transistors to invert an input signal.  
- **Crossing Current** — The current flowing when both NMOS and PMOS transistors in an inverter are partially on during input transitions.  
- **Dynamic Power Dissipation** — Power consumed by a CMOS inverter when charging and discharging the output capacitance during switching.  
- **Inverter Switching Point (Vsp)** — The input voltage where the inverter output voltage equals the input voltage, marking the switching threshold.  
- **Input Capacitance (Cin)** — The effective capacitance seen looking into the gate of the inverter, including the gate oxide capacitances.  
- **Latch-Up** — A parasitic condition where unintended bipolar transistors turn on due to layout-induced feedback, causing the circuit to lock in a state.  
- **Load Capacitance (Cload)** — The effective capacitance that a gate must drive at its output, including parasitic and connected gate capacitances.  
- **Minimum Delay Buffer Design** — A methodology to choose inverter widths and stage count to minimize total delay driving a large load.  
- **NMOS Device (Ml)** — The n-channel MOS transistor in the inverter that pulls the output low when turned on.  
- **NMOS-Only Inverter** — An inverter topology using only NMOS transistors for output drive, often used to avoid latch-up.  
- **Noise Margin** — The allowable voltage range within which an input or output signal is still recognized as a valid logic level.  
- **Output Capacitance (Cout)** — The capacitance at the output node of the inverter affected by transistor drains and wiring.  
- **PMOS Device (M2)** — The p-channel MOS transistor in the inverter that pulls the output high when turned on.  
- **Propagation Delay (tpHL, tpLH)** — The intrinsic delay times for output transition from high-to-low and low-to-high, respectively.  
- **Power Delay Product (PDP)** — The product of average power dissipation and propagation delay; a metric to compare energy efficiency of circuits.  
- **Ring Oscillator** — A circuit made by connecting an odd number of inverters in a loop, used to characterize process speed through oscillation frequency.  
- **Switching Threshold (Vm)** — The voltage at which the inverter output transitions between logic levels during input voltage sweep.  
- **Switching Region** — The input voltage range where both NMOS and PMOS transistors are partially on, causing output transition.  
- **Tri-State Output** — An inverter output that can be driven high, low, or put into a high-impedance state to allow shared communication lines.  
- **Voltage Transfer Characteristic (VTC)** — The voltage relationship between the inverter input and output during a DC sweep.  
- **Voltage Swing** — The range of output voltage variation from ground to VDD, ideally full rail-to-rail in a CMOS inverter.  
- **Well and Substrate Contacts** — Implant regions connected to VDD or ground to minimize parasitic resistances and reduce latch-up risk.
