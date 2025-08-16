---
title: "clock-tree-design — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [clock-tree-design]
---

- **Clock gating** — A technique to reduce power by disabling clock signals to inactive portions of a design.  
- **Clock latency** — The total time taken for a clock signal to travel from the source to a register clock pin.  
- **Clock mux (Multiplexer)** — A device that selects one of several clock signals to be forwarded to downstream logic.  
- **Clock skew** — The difference in arrival times of a clock signal at different flip-flops.  
- **Clock tree synthesis (CTS)** — The process of designing and implementing the clock distribution network on a chip.  
- **Common clock path** — Portion of the clock path shared between launch and capture registers where process variations are assumed correlated.  
- **DDR (Double Data Rate)** — A type of memory interface that uses both edges of the clock to transfer data.  
- **Derate numbers** — Margins introduced in timing to account for process, voltage, temperature variations, or uncertainties.  
- **Double width double spacing (DWDS)** — A rule to increase wire width and spacing to reduce noise and electromigration on clock lines.  
- **Duty cycle** — The ratio of high time to total period in a clock signal.  
- **EM (Electromigration)** — Degradation of metal wires due to electron flow that can cause failures in the clock tree.  
- **Functional clock** — The clock signal used during normal operation of the SoC.  
- **Hold timing** — A timing constraint ensuring data is stable for some time after the clock edge to prevent errors.  
- **Latency balancing** — Adjusting buffering and routing so different clock paths have matched latencies.  
- **Microcontroller** — A small computer on a single integrated circuit, often with multiple on-chip peripherals.  
- **Mux select signal** — Control input to a clock multiplexer determining which clock source is active.  
- **Non-buffer logic cloning** — Duplicating clock control logic such as multiplexers to enable more flexible clock tree design.  
- **Off SoC clock source** — External clock signals provided to the SoC, e.g., EXTAL.  
- **On SoC clock source** — Internal clock sources within the SoC, e.g., PLL or internal ring oscillators.  
- **Pre CTS timing** — Timing analysis results before clock tree synthesis is applied.  
- **Post CTS timing** — Timing analysis results after the clock tree has been synthesized.  
- **Pulse width** — The minimum duration a clock pulse remains high or low, critical for correct sequential device operation.  
- **Synchronous clocks** — Multiple clocks that are phase-aligned or have a known fixed timing relationship.  
- **Test clock** — Clock signals used specifically during testing, e.g., at-speed or stuck-at testing.  
- **Uncommon clock path** — Portions of the clock path that differ between launch and capture registers and are subject to derates.  
- **Uncommon path reduction** — Techniques to minimize clock path differences between registers to reduce timing uncertainty.  
- **Voltage and temperature corners** — Extreme operating conditions under which timing is analyzed for robustness.  
- **Back-to-back clock gating cells** — Consecutive clock gating cells that can increase clock latency and delay in clock paths.
