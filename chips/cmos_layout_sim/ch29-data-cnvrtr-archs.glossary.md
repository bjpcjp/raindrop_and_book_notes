---
title: "ch29-data-cnvrtr-archs — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch29-data-cnvrtr-archs]
---

- **Analog-to-Digital Converter (ADC)** — A device that converts continuous analog signals into discrete digital values.
- **Binary-Weighted Capacitor Array** — A DAC architecture using capacitors with values in powers of two for converting digital values to analog voltage.
- **Charge-Redistribution DAC** — A DAC that uses binary-weighted capacitors and switches to convert charge levels corresponding to digital input codes into an analog output.
- **Charge-Scaling DAC** — A DAC architecture that uses a capacitor array to create a voltage proportional to a charge, representing digital input.
- **Clock Frequency (f_CLK)** — The speed at which sampling or conversion steps occur in a data converter.
- **Comparator Offset Voltage (V_os)** — The input voltage difference required to switch a comparator’s output from one state to another, causing errors.
- **Cyclic DAC/ADC** — A converter using feedback and repeated partial conversions over multiple clock cycles to build up a result.
- **Differential Nonlinearity (DNL)** — The deviation of an actual step size from the ideal one least significant bit step in a DAC or ADC.
- **Digital Input Code** — Binary or other code formats (e.g., Gray, thermometer) representing digital words in data converters.
- **Dynamic Range** — The ratio between the largest and smallest measurable signals of a converter, usually expressed in dB.
- **Effective Number of Bits (ENOB)** — The actual resolution of a converter, factoring in noise and nonidealities.
- **Feedback Factor (β)** — The portion of the output signal fed back into an amplifier or converter’s feedback loop.
- **Flash ADC** — A high-speed ADC architecture using parallel comparators for each quantization threshold, outputting a thermometer code.
- **Integral Nonlinearity (INL)** — The deviation of an actual converter output from a straight line drawn through the ideal transfer function.
- **Noise Shaping** — A technique used in oversampling ADCs to push quantization noise to higher frequencies outside the signal bandwidth.
- **Nyquist Rate** — The minimum sampling rate equal to twice the bandwidth of the input signal to prevent aliasing.
- **Offset Voltage** — An unwanted fixed voltage added to the input of amplifiers, comparators, or integrators causing conversion errors.
- **Oversampling ADC** — An ADC that samples the input signal at a far higher rate than the Nyquist frequency and uses digital filtering to improve resolution.
- **Pipeline ADC** — An ADC architecture where conversion is done in multiple stages, each resolving one or several bits, with high throughput after initial latency.
- **Power Dissipation** — The amount of power converted to heat within the data converter components, influencing design trade-offs.
- **Quantization Noise/Error** — The difference between the actual analog input and its quantized digital representation in converters.
- **R-2R Ladder DAC** — A DAC using resistors arranged in a ladder network alternating values R and 2R for digital-to-analog conversion.
- **Resistor-String DAC** — A DAC using a string of equal resistors to generate reference voltages at discrete taps corresponding to digital inputs.
- **Resolution** — The number of discrete levels or bits a data converter can distinguish.
- **Sample-and-Hold (S/H)** — A circuit that samples and holds the analog input constant during conversion for ADCs.
- **Sigma-Delta (ΣΔ) Modulator** — An oversampling ADC component that uses noise shaping and feedback to convert analog signals into high-rate bit streams.
- **Successive Approximation Register (SAR) ADC** — An ADC that performs a binary search using a DAC and comparator for each bit in the digital output, one at a time.
- **Switch Resistance** — The resistance introduced by switches used in DACs or ADCs, affecting linearity and speed.
- **Thermometer Code** — A binary format where all bits below a transition point are ones and all above are zeros, used in some DACs and ADCs.
