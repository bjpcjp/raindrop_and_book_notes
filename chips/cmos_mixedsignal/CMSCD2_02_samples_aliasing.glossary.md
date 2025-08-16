- **AAF (Anti-aliasing filter)** — An analog filter limiting the input signal's spectral content to below the Nyquist frequency to prevent aliasing during sampling.

- **Aperture uncertainty** — Error caused when the input to an ADC varies during the sample-and-hold’s track portion, leading to timing inaccuracies.

- **Autozeroing** — Technique where input offset and low-frequency noise are sampled and then subtracted from the output to reduce offset and flicker noise.

- **CDS (Correlated Double Sampling)** — A process combining autozeroing with sample-and-hold to remove offset and low-frequency noise by double sampling.

- **DAC (Digital-to-Analog Converter)** — Device converting digital words back into analog signals.

- **DAI (Discrete Analog Integrator)** — An analog sampled-data integrator circuit used in mixed-signal systems to perform integration in the discrete-time domain.

- **Decimation** — The process of reducing the sampling rate of a digital signal by an integer factor K, often involving lowpass filtering before downsampling.

- **Digital Anti-aliasing Filter** — A filter used prior to decimation to limit the digital signal bandwidth and prevent aliasing.

- **DSP (Digital Signal Processing)** — Manipulation of digital signals using algorithms such as filtering.

- **Gain-bandwidth product (unity-gain frequency)** — Frequency at which an op-amp's open-loop gain drops to one; important for settling time in sample-and-hold circuits.

- **Hold Register** — A method of interpolation holding input samples over multiple output clock cycles to increase sample rate.

- **Impulse Sampling** — Sampling with impulses (Dirac delta functions) at discrete times, producing a sampled spectrum repeated at multiples of the sampling frequency.

- **Interpolation** — Increase of sampling rate by an integer factor K, typically performed by inserting zeroes ("zero padding"), holding samples, or linear interpolation.

- **K-path Sampling** — Technique using multiple parallel sample-and-hold paths clocked in phases to increase effective sampling rate by a factor K.

- **Laplace transform** — Mathematical transform for analyzing continuous-time systems.

- **Linear Interpolation** — Interpolating samples by linearly varying values between input samples; introduces similar spectral response to zero-order hold.

- **LPF (Lowpass Filter)** — Analog or digital filter passing signals below a cutoff frequency; used as anti-aliasing and reconstruction filters.

- **Nyquist frequency (fn)** — Half the sampling frequency (fs/2); maximum frequency that can be unambiguously sampled.

- **Oversampling** — Sampling a signal at a rate significantly higher than twice its highest frequency to ease anti-aliasing and reconstruction filter requirements.

- **Phase response (Linear phase)** — Filter property where phase delay is constant with frequency, preserving waveform shapes.

- **Quantization in time** — Limiting a signal so its amplitude is defined or held only at discrete time intervals.

- **Reconstruction filter (RCF)** — Analog lowpass filter used after digital-to-analog conversion to smooth and remove spectral images above Nyquist frequency.

- **Return-to-zero (RZ) format** — Sample-and-hold output format where output returns to zero between samples to reduce distortion but also signal power.

- **Sample-and-hold (S/H)** — Circuit that samples the input signal at discrete times and holds the sampled value during the sample period, introducing a Sinc frequency response.

- **Sampling frequency (fs)** — Rate at which an analog signal is sampled.

- **Slew rate** — Maximum rate of change of an op-amp output voltage.

- **Sinc response** — Frequency response of a sample-and-hold circuit, shaped as sin(πfTs)/(πfTs), causing attenuation near Nyquist frequency.

- **Switching capacitor circuits** — Circuits using switched capacitors to emulate resistors or perform functions like integration in discrete-time.

- **Track-and-hold (T/H)** — Sampling circuit that tracks the input signal during the track phase and holds the sampled value during the hold phase; causes less attenuation than S/H.

- **Z-transform** — Mathematical transform for analyzing discrete-time systems, representing delays as powers of z.


