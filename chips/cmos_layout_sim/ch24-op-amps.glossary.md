---
title: "ch24-op-amps — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch24-op-amps]
---

- **Active Load** — A transistor-based load used to increase gain and output resistance in amplifier stages.
- **Biasing** — Setting the DC operating point of transistors to achieve desired amplifier performance.
- **Cascode Amplifier** — A two-transistor stage combining a common-source and common-gate amplifier to increase gain and output resistance.
- **Common-Mode Rejection Ratio (CMRR)** — The ability of a differential amplifier or op-amp to reject signals common to both inputs.
- **Compensation Capacitor (Cc)** — A capacitor added to an op-amp to stabilize it by shifting poles and zeros in frequency response.
- **Common-Mode Range (CMR)** — The allowable range of input voltage common to both inputs for proper amplifier operation.
- **Current Mirror** — A circuit that copies current from one branch to another to provide bias currents or active loads.
- **Differential Amplifier (Diff-Amp)** — An amplifier stage that amplifies the voltage difference between two inputs.
- **Gain-Bandwidth Product (GBWP or f_utm)** — The frequency at which the open-loop gain of an op-amp falls to unity; product of gain and bandwidth.
- **Gain-Enhancement (GE)** — Technique to increase amplifier gain by regulating cascode node voltages via feedback amplifiers.
- **Input Common-Mode Voltage** — The voltage level present simultaneously on both input terminals of an op-amp.
- **Input-Referred Offset Voltage** — The equivalent input voltage offset that accounts for output voltage shifts due to device mismatches.
- **Miller Compensation** — A method using a capacitor between amplifier stages to improve stability by pole splitting.
- **Nested Miller Compensation** — A compensation technique for multi-stage op-amps involving capacitors nested inside feedback loops.
- **Noise Margin** — Not explicitly defined but implied as the ability to tolerate power supply or signal variations without significant distortion.
- **Offset Voltage (Systematic Offset)** — A predictable offset voltage due to intentional device sizing mismatches.
- **Operational Amplifier (Op-Amp)** — A high-gain amplifier with differential inputs and typically a single-ended output, used with feedback.
- **Operational Transconductance Amplifier (OTA)** — An amplifier converting voltage differential at its inputs into an output current, commonly used in capacitive loads.
- **Output Buffer** — A stage following an amplifier that provides current gain and isolates the previous stage from load effects.
- **Output Swing** — The range of output voltages an amplifier can produce without distortion or device saturation.
- **Phase Margin (PM)** — The difference between the phase shift at unity gain frequency and 180°, indicating stability degree.
- **Power Dissipation** — The total power consumed by the op-amp, often product of supply voltage and total current.
- **Power Supply Rejection Ratio (PSRR)** — A measure of how well an amplifier rejects fluctuations in its power supply voltages.
- **Push-Pull Amplifier** — A complementary pair output stage used to provide higher current drive with reduced distortion.
- **Pole Splitting** — The process of separating dominant and non-dominant poles to enhance stability in multi-stage amplifiers.
- **Slew Rate** — The maximum rate of change of the output voltage of an amplifier, limited by internal current capabilities.
- **Transconductance (gm)** — The ratio of output current change to input voltage change in a transistor or amplifier.
- **Unity-Gain Frequency (f_utm)** — See Gain-Bandwidth Product, the frequency where the amplifier gain equals one.
- **Zero-Nulling Resistor (Rz)** — A resistor added in compensation networks to move right half-plane zeros to left half-plane, improving stability.
