---
title: "ch13-clocked-logic — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch13-clocked-logic]
---

- **Arbiter** — A circuit that decides which of two nearly simultaneous inputs occurred first, ensuring only one output goes high at a time.  
- **Clear input** — A control signal used to asynchronously reset a flip-flop output to zero.  
- **Clock signal** — A timing signal used to control synchronization in digital circuits like latches and flip-flops.  
- **Cross-coupled inverters** — Two inverters connected in a loop providing bistable storage used in latches and flip-flops.  
- **DEMUX (Demultiplexer)** — A circuit that routes a single input line to one of many output lines based on control signals.  
- **Edge-triggered flip-flop (FF)** — A storage element that captures input data on a specific clock edge (rising or falling).  
- **Enable signal** — A control input that enables or disables transmission gates or other logic elements.  
- **Flip-flop (FF)** — A bistable storage device that can hold one bit of data, changing state on clock edges.  
- **Hold time** — The minimum time the input data must remain stable after the clock edge for correct flip-flop operation.  
- **Level-sensitive latch** — A storage element that transparently passes data when the clock is at a certain level and holds data otherwise.  
- **Multiplexer (MUX)** — A circuit that selects one of several input signals based on control signals and forwards it to the output.  
- **Metastability** — An unstable state in cross-coupled inverters where outputs are at intermediate voltages, causing long delays or errors.  
- **NMOS pass transistor (PG)** — A transistor that passes logic low signals well but degrades logic high signals due to threshold voltage drop.  
- **Output load capacitance** — The capacitance that the output of a circuit must drive, impacting delay.  
- **Propagation delay (tpHL, tpLH)** — The time taken for a signal to transition through a circuit from input to output, often measured low-to-high or high-to-low.  
- **Recover time (trec)** — The time required after an asynchronous set or clear input before the clock input of a flip-flop can be valid again.  
- **Setup time (ts)** — The minimum time the input data must be stable before the clock edge in a flip-flop for proper operation.  
- **Set input** — A control signal used to asynchronously set a flip-flop output to one.  
- **Series connection of transmission gates** — Multiple transmission gates connected end-to-end, increasing delay due to added resistances and capacitances.  
- **Static gate** — A logic gate built using transmission gates that can implement logical functions like OR or XOR.  
- **Transmission gate (TG)** — A bidirectional switch made from parallel NMOS and PMOS transistors, passing both logic high and low efficiently.  
- **Transmission line effects** — Delay effects due to distributed resistance and capacitance in series-connected gates.  
- **Triode operation** — The condition where MOSFET transistors act like resistors, relevant for transmission gate resistance estimations.  
- **XOR gate using TGs** — An exclusive OR logic gate implemented using transmission gates for improved performance.
