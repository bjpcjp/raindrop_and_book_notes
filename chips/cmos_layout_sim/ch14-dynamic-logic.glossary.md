---
title: "ch14-dynamic-logic — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch14-dynamic-logic]
---

- **Charge Leakage** — The loss of stored charge from a dynamic node due to MOSFET off currents and diode leakage paths.  
- **Clocked CMOS Latch** — A memory element where data is stored dynamically on a node controlled by clock signals to enable master and slave stages.  
- **Dynamic Node (Storage Node)** — A high-impedance node in a dynamic circuit where charge is stored on capacitances to hold a logic value temporarily.  
- **Dynamic Logic** — Logic circuits that use capacitive charge storage and clocked switches to operate faster and with less power than static logic.  
- **Evaluate Phase** — The part of a clock cycle when dynamic logic gates compute output based on inputs after precharging.  
- **Keeper MOSFET** — A weak PMOS transistor added to dynamic logic nodes to maintain their voltage level by compensating for leakage currents.  
- **Master-Slave Latch** — A clocked latch divided into master (input capture) and slave (output drive) stages controlled by complementary clock signals.  
- **NMOS Pass Gate (PG)** — A transistor switch used in dynamic logic to charge or discharge a node by passing the input logic level when clocked.  
- **NP Logic (Zipper Logic)** — Dynamic logic design that alternates NMOS and PMOS stages, eliminating the need for inverters between stages for higher speed.  
- **Off Current (IOFF)** — The small leakage current flowing through a MOSFET when it is turned off, responsible for charge loss in dynamic nodes.  
- **PE (Precharge-Evaluate) Logic** — A dynamic logic style where nodes are precharged to high and conditionally discharged during evaluation based on inputs.  
- **PMOS Drain-Well Diode** — The parasitic diode formed between the PMOS drain and the well that can contribute to leakage currents in dynamic circuits.  
- **Precharge Phase** — The stage of a clock cycle in dynamic logic during which the output nodes are charged to a known voltage, usually VDD.  
- **Storage Node Capacitance (Cnode)** — The total capacitance at a dynamic node, including inverter input, interconnect, and junction capacitances.  
- **Transmission Gate (TG)** — A CMOS switch combining NMOS and PMOS transistors to pass signals with minimal voltage drop in dynamic circuits.  
- **True Single-Phase Clocked Flip-Flop (TSPC FF)** — A flip-flop circuit using a single clock phase to achieve edge-triggered operation in dynamic logic.  
- **Vsp (Switching Point Voltage)** — The input voltage at which a logic inverter switches its output state, less relevant in dynamic PE gates.  
- **Nonoverlapping Clock** — Clock signals with deliberate dead time between phases to prevent simultaneous conduction in adjacent transistor stages.  
- **Dynamic Shift Register** — A sequence of dynamic logic stages clocked with nonoverlapping clocks to pass data edge-to-edge without contention.  
- **Leakage Current** — Undesired current through MOSFETs or diodes when transistors are off, causing charge decay on dynamic nodes.  
- **Domino Logic** — A dynamic logic style that adds an inverter after a precharge-evaluate gate to prevent glitches and enable cascading of gates.  
- **Pipelining** — A technique to process multiple data words in stages to increase throughput in sequential logic circuits.  
- **Weak Keeper** — A MOSFET sized to provide minimal current just sufficient to maintain a node's charge without impeding logic operation.
