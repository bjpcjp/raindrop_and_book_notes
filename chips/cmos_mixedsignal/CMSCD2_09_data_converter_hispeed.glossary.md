- **1-sigma, K-deltas topology** — A high-speed data converter topology using a single integrator (1-sigma) and K feedback paths (K-deltas), implemented with switched-capacitor circuits for feedback subtraction and integration.

- **Averaging (Filtering)** — The process of summing and averaging multiple outputs to reduce noise and increase resolution, generally resulting in reduced signal bandwidth.

- **Bandwidth** — The range of frequencies a data converter can effectively process or sample.

- **Charge/Discharge Time (Path Settling Time)** — The time required for sampling capacitors to be charged or discharged to represent the analog input accurately within a clock period divided by the number of paths.

- **Clock Signals (Phases)** — Multiple non-overlapping clock phases used to time-interleave sampling and feedback in K-path modulators, enabling effective sampling at a higher frequency than the base clock.

- **Decimation** — The digital down-sampling process used after high-rate conversions to reduce the data rate while filtering out quantization noise.

- **Digital Filter** — A filter applied to the digital output of a modulator to remove quantization noise and shape the effective transfer function, improving resolution.

- **Effective Sampling Frequency (fs,new)** — The sampling frequency achieved by time-interleaving K paths, given by fs,new = K × fs.

- **Feedback Paths (K-deltas)** — Multiple feedback signal paths in the modulator that subtract from the input to shape the noise and improve resolution.

- **Integrator (1-sigma)** — A filter stage in the modulator that integrates the difference between input and feedback, common to all paths to push quantization noise to higher frequencies.

- **Limit-cycle Oscillations** — Unwanted self-sustained oscillations in the modulator output caused by finite delay in feedback and clock timing mismatches.

- **Mixed-Signal Circuit Techniques** — Design methods combining analog and digital circuits to implement high-speed data converters.

- **Modulation Noise** — Noise resulting from quantization errors shaped by the modulator’s noise transfer function.

- **Modulator Output Word Size** — The bit-width of the digital output from the modulator, increased through filtering and decimation.

- **Non-overlapping Clocks** — Clock signals with phases designed to avoid overlap, used to prevent charge-sharing and ensure correct timing in switched-capacitor circuits.

- **Nyquist Frequency** — Half the sampling frequency, representing the highest frequency that can be correctly sampled without aliasing.

- **Quantization Noise** — Noise introduced by representing a continuous signal with a discrete number of bits.

- **Ring Oscillator** — A circuit used to generate the multiple clock phases needed for time-interleaved sampling and feedback.

- **Sampling Capacitors** — Capacitors used to sample and hold the analog input signal in switched-capacitor converters.

- **Signal Bandwidth** — The highest frequency component of the desired input signal.

- **Signal-to-Noise Ratio (SNR)** — The ratio of signal power to noise power, indicating the quality of the data conversion.

- **Switch Resistance** — The effective resistance of MOSFET switches controlling the charge/discharge time of sampling capacitors.

- **Thermal Noise (kT/C noise)** — Noise associated with the thermal energy of electrons, influencing the minimum capacitance size to achieve a desired noise floor.

- **Time-Interleaved Sampling** — Technique of using multiple sampling paths staggered in time to achieve higher effective sampling rates.

- **Transfer Function (Path Filter)** — The frequency response resulting from summing the outputs of multiple paths, typically a sinc function.

- **Using Digital Sinc Filters** — Application of cascaded integrator-comb filters to remove quantization noise and decimate the oversampled digital output.

- **Voltage Output (Summing Circuit Output)** — The summed digital output level representing the combined comparator outputs from multiple paths.

- **Word Decimation Rate** — The ratio at which the high-speed modulator outputs are down-sampled to match a desired lower clock rate.
