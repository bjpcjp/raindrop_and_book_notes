---
title: "ch28-data-cnvrtr-basics — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch28-data-cnvrtr-basics]
---

- **Acquisition time** — The time needed for a sample-and-hold circuit to track an input signal to within a specified accuracy during sampling.  
- **Aperture error (jitter)** — Sampling error caused by uncertainty in the exact time of sampling, leading to voltage errors especially at high signal slew rates.  
- **Analog signal** — A continuous-time, infinite-valued signal representing physical quantities in a continuous range.  
- **Anti-aliasing filter** — A low-pass filter used before sampling to remove frequency components above half the sampling rate to prevent aliasing.  
- **Bit (resolution)** — The number of binary digits in ADC or DAC input or output, defining the number of discrete levels (2^N).  
- **DAC (Digital-to-Analog Converter)** — A circuit that converts digital (discrete-time, quantized) signals into analog voltages or currents.  
- **DNL (Differential Nonlinearity)** — The difference between actual and ideal step sizes between adjacent output codes in a converter, measured in LSBs.  
- **Dynamic range** — The ratio, in decibels, between the largest and smallest output signal levels a converter can handle.  
- **Effective number of bits (ENOB)** — A measure of the resolution of an ADC as indicated by its actual signal-to-noise ratio.  
- **Gain error** — A deviation in converter output slope from ideal, representing scale factor error in the transfer function.  
- **Hold mode** — The phase in sample-and-hold operation where the sampled value is held constant while conversion occurs.  
- **Increment (LSB)** — The smallest change in analog output corresponding to a 1-bit change in digital input for DACs; one least significant bit voltage step for ADCs.  
- **Integral Nonlinearity (INL)** — The deviation of converter output values from an ideal straight line fit between end points, indicating cumulative nonlinearity.  
- **Latency** — Total delay time from digital input change to the stabilized analog output in DACs.  
- **Matching** — A layout technique to improve component uniformity for reduced offset and nonlinearity errors.  
- **Monotonicity** — A property where increasing digital input codes produce non-decreasing analog output voltages, essential for correct converter function.  
- **MSB (Most Significant Bit)** — The highest-order bit in a digital word, representing the largest weighted value.  
- **Nyquist Criterion** — The minimum sampling frequency must be at least twice the highest frequency of the input signal to avoid aliasing.  
- **Offset error** — An unwanted constant shift in converter output voltage or code from the ideal zero input or zero code level.  
- **Quantization error** — The difference between the actual analog input and its nearest quantized digital representation in an ADC.  
- **Resolution** — The smallest measurable or distinguishable change in analog value represented by the digital converter, typically in bits.  
- **Sample-and-Hold (S/H)** — A circuit that samples an analog signal at discrete intervals and holds the value steady for conversion.  
- **Sampling frequency** — The rate at which an analog signal is sampled to create a discrete-time representation.  
- **Slew rate** — The maximum rate at which an amplifier or buffer can change its output voltage.  
- **Signal-to-noise ratio (SNR)** — The ratio of signal power to noise power at a converter output, usually expressed in decibels.  
- **Track-and-Hold (T/H)** — A variation of S/H where the output follows the input during sampling and then holds the last value.  
- **VLSI (Very Large Scale Integration)** — Integration of thousands to millions of transistors on a single chip, used in mixed analog/digital design.
