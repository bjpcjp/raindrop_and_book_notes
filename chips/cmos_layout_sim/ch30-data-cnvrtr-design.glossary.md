---
title: "ch30-data-cnvrtr-design — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch30-data-cnvrtr-design]
---

- **1.5 bits per stage** — A pipeline ADC stage resolution using three quantization levels to correct comparator offset errors.  
- **ADC (Analog-to-Digital Converter)** — A device that converts continuous analog signals into discrete digital codes.  
- **AAF (Auxiliary Amplifier or Auxiliary Input Port)** — Additional input used in op-amps to trim or null offset voltages dynamically.  
- **Bottom-plate sampling** — A sampling technique where the capacitor bottom plate is switched last to reduce charge injection errors.  
- **Capacitor matching** — The precision in maintaining equal or proportional capacitor values to ensure linearity and accuracy in circuits.  
- **CMFB (Common-Mode Feedback)** — A feedback circuit that stabilizes and controls the common-mode voltage in fully differential amplifier circuits.  
- **CMRR (Common-Mode Rejection Ratio)** — The ability of an amplifier to reject input signals common to both inputs, critical for DAC linearity.  
- **Current-steering DAC** — A digital-to-analog converter that produces output currents proportionally steered through switches rather than voltages.  
- **DNL (Differential Nonlinearity)** — A measurement of the deviation between the actual and ideal step sizes in a DAC or ADC transfer function.  
- **INL (Integral Nonlinearity)** — The cumulative deviation from the ideal transfer curve in converters, representing overall distortion.  
- **MSB (Most Significant Bit)** — The bit in a binary number with the highest value and greatest weight.  
- **Op-amp offset voltage** — An undesired DC voltage at the input of an operational amplifier causing output errors.  
- **Op-amp unity gain frequency (/un)** — The frequency where an op-amp's gain drops to 1, critical for determining settling time and bandwidth.  
- **Pipeline ADC** — A multi-stage ADC architecture that processes bits sequentially with error correction for high-speed conversions.  
- **Power supply rails** — The highest and lowest voltage levels available in a circuit, typically labeled VDD (positive) and ground.  
- **Rail-to-rail output** — An amplifier or DAC output capability that can swing close to both power supply rails.  
- **Reference voltage (VREF)** — A stable voltage used as a baseline or scale for DACs and ADCs to define their input and output ranges.  
- **Resistor mismatch** — Variations between resistor values in a network affecting DAC linearity and accuracy.  
- **R-2R ladder DAC** — A resistor network consisting of repeating R and 2R resistors used to create binary-weighted output voltages or currents.  
- **Segmentation (DACs)** — Dividing DAC bits into groups (like MSBs and LSBs) to improve linearity and reduce glitches.  
- **Settling time** — The time it takes for an output to reach and remain within a specified error band of its final value.  
- **Switch resistance** — The on-resistance of MOSFET switches in DAC or S/H circuits, ideally much smaller than resistors in the ladder to maintain accuracy.  
- **Thermometer code** — A unary digital code where each level corresponds to a number of consecutive '1's, used to reduce glitches in segmented DACs.  
- **Track-and-hold (S/H) circuit** — A circuit that samples an analog input voltage and holds it constant for processing or conversion.  
- **W-2W current mirror** — A current mirror design using transistor finger sizes to create precise binary-weighted currents for current-steering DACs.  
- **Wide-swing current-mode DAC** — A current-mode R-2R DAC topology optimized for rail-to-rail output and fixed input common-mode voltage.
