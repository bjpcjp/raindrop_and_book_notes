---
title: "ch25-dynamic-analog-ckts — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch25-dynamic-analog-ckts]
---

- **Charge Injection** — The transfer of charge from a MOSFET channel to adjacent nodes when a switch turns off, causing voltage errors.
- **Clock Feedthrough** — Capacitive coupling of the gate drive signal to the output node in MOSFET switches, causing voltage disturbances.
- **Common-Mode Feedback (CMFB)** — A circuit technique used in fully-differential amplifiers to control and stabilize the common-mode output voltage.
- **Differential Amplifier (Diff-Amp)** — An amplifier with two inputs and a single or differential output that amplifies the voltage difference between its inputs.
- **Dynamic Amplifier** — An amplifier which employs switching and capacitive storage to reduce sensitivity to threshold voltage and power supply variations.
- **Dynamic Comparator** — A comparator that uses switches and storage capacitors to sense and latch input voltages, often operating in discrete time.
- **Dummy Switch** — A compensating MOSFET switch used in series with the main switch to reduce charge injection.
- **Fully-Differential Circuit** — A circuit with differential inputs and outputs that helps cancel common-mode noise and offset errors.
- **Hold Capacitor (CH)** — The capacitor used in sample-and-hold circuits to store the sampled voltage.
- **kT/C Noise** — Thermal noise associated with a capacitor due to its kT/C noise voltage when sampled; sets the noise floor for dynamic circuits.
- **Mosfet Switch** — A MOSFET transistor operating as an analog switch controlled by clock signals with no DC gate current.
- **Nonoverlapping Clocks** — Two clock signals designed such that their high phases do not overlap to prevent shorting paths in switched-capacitor circuits.
- **Op-Amp Offset Voltage** — The undesired DC voltage difference at the input of an operational amplifier that appears at the output.
- **Output Common-Mode Voltage (VCM)** — The average voltage around which the outputs of a fully-differential amplifier swing.
- **Sample-and-Hold (S/H) Circuit** — A circuit that samples an input signal onto a capacitor during a sample phase and holds the voltage constant during hold phase.
- **Sample Mode** — The phase in a sample-and-hold circuit when the input is connected to the capacitor to track the input signal.
- **Settlng Time** — The time required for an amplifier output to settle within a specified error band of its final value.
- **Slew Rate** — The maximum rate at which an amplifier output can change, limiting speed in dynamic circuits.
- **Signal-Dependent Charge Injection** — Charge injection errors that vary with the input signal level, causing distortion.
- **Switched-Capacitor (SC) Circuit** — A circuit that uses capacitors and switches clocked at a known frequency to emulate resistors and perform filtering and integration.
- **Switched-Capacitor Integrator** — An SC circuit implementing integration by charging and discharging capacitors under clock control.
- **Switching Phases (Φ1, Φ2, Φ3)** — Nonoverlapping clock phases used to control switch timing in dynamic analog circuits.
- **Track Mode** — The phase in a sample-and-hold circuit when the output follows the input signal.
- **Transmission Gate (TG)** — A CMOS switch made of parallel NMOS and PMOS transistors that passes both logic high and low levels without threshold loss.
- **Virtual Ground** — A circuit node held at a constant potential, often zero volts, by an amplifier’s feedback action.
- **Voltage-Controlled Voltage Source (VCVS)** — A device or model that generates an output voltage proportional to an input voltage, used in SPICE op-amp models.
