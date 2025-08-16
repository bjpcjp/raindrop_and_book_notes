---
title: "ch19-digital-plls — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch19-digital-plls]
---

- **Active-PI loop filter** — A loop filter combining proportional and integral actions to reduce static phase error and improve lock performance in DPLLs.  
- **Charge pump** — A circuit that converts a digital up/down control signal into a current output for the loop filter in a PFD-based DPLL, improving noise immunity.  
- **Clock recovery** — The process of extracting timing information (clock) synchronized with incoming data in a communication receiver.  
- **Current-starved VCO** — A voltage-controlled oscillator design where inverter current is limited by controlled current sources for frequency tuning.  
- **Data encoding** — Methods such as bi-phase or NRZ to modify data for improved timing, clock recovery, or error detection in communication systems.  
- **Data jitter** — Variation in timing of the recovered clock edges once the loop is locked, often caused by noise or VCO gain.  
- **Delay-locked loop (DLL)** — A circuit that aligns the phase of an output clock with a reference clock using a voltage-controlled delay line, avoiding oscillator noise.  
- **Differential voltage-controlled delay line (VCDL)** — A delay line using differential stages controllable by a voltage, used in DLLs to adjust timing delays.  
- **Damping ratio (ζ)** — A parameter quantifying the damping of the DPLL's loop filter system, affecting how quickly and smoothly it locks.  
- **Divide-by-N counter** — A circuit in a DPLL feedback path that divides the oscillator frequency to allow lock at harmonics of input frequency.  
- **Edge detector** — A circuit that converts NRZ data transitions into pulses, enabling clock recovery through phase detection.  
- **Frequency synthesis** — Generating a clock frequency that is a multiple or fraction of a reference input using a PLL or DPLL.  
- **Loop filter** — A filtering stage in a DPLL that smooths the phase detector output to control the VCO input voltage.  
- **Lock range** — The frequency range over which the DPLL can maintain lock quickly and reliably once locked.  
- **Lock time** — The time it takes for the DPLL to converge and synchronize to an input frequency or phase change.  
- **Phase detector (PD)** — A component that detects the phase difference between two signals; common types include XOR and phase frequency detector (PFD).  
- **Phase frequency detector (PFD)** — A phase detector that compares both phase and frequency of input signals, providing edge-aligned outputs with reduced harmonic locking.  
- **Phase jitter** — Unwanted variations in phase timing of the oscillator or recovered clock due to noise or circuit imperfections.  
- **Phase-locked loop (PLL)** — A feedback system that locks the output oscillation phase and frequency to an input reference signal.  
- **Pull-in range** — The broader input frequency range from which the DPLL can eventually lock, though it may take longer than the lock range.  
- **Ripple (loop filter)** — Oscillations in the loop filter output voltage caused by phase detector output pulses causing clock frequency modulation.  
- **Self-correcting phase detector (Hogge PD)** — A phase detector design for clock recovery that automatically aligns clock edge with data transitions, reducing static phase error.  
- **Transfer function** — A mathematical description of the output-to-input ratio of a system as a function of frequency or complex variable s.  
- **Voltage-controlled oscillator (VCO)** — An oscillator whose output frequency varies with the applied input voltage, key to the DPLL operation.  
- **Voltage-controlled delay line (VCDL)** — A circuit element whose delay changes in response to an input voltage, used in DLLs for phase alignment.  
- **XOR phase detector** — A simple phase detector implemented with an exclusive-OR gate, producing a pulse width proportional to phase difference but sensitive to data patterns.
