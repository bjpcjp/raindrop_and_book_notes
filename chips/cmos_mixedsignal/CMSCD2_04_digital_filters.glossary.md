- **ADC (Analog-to-Digital Converter)** — A device that converts an analog input voltage into a digital output code, often implemented with sample-and-hold and comparator stages.

- **Adder** — A digital circuit that sums two or more binary numbers, important in filter implementations for multiplication and addition.

- **Biquad Filter** — A second-order digital filter with two poles and two zeroes, commonly implemented in canonic form, flexible in shaping frequency responses.

- **Binary Offset Format** — A digital number representation where the least significant bit corresponds to zero and the value ranges from zero to full scale, often used in DAC and ADC outputs.

- **Canonic Form (Standard Form)** — A minimal delay digital filter implementation that uses the least number of registers for a given order filter.

- **Cascade** — Connecting multiple filter stages in series to increase the filter order and improve attenuation characteristics.

- **CIC Filter (Cascaded Integrator-Comb filter)** — A digital filter formed by cascaded integrators and comb filters, often used for decimation and interpolation.

- **Comb Filter** — A finite impulse response (FIR) digital filter introducing zeros at regularly spaced frequencies, used in sinc-shaped filters.

- **Decimation** — The process of reducing the sampling rate of a digital signal, often by filtering (anti-aliasing) and downsampling.

- **Differentiator** — A filter or operation that approximates the derivative of the input signal, often implemented as a comb filter.

- **Digital Filter** — A discrete-time filter that processes digital signals using mathematical operations in the z-domain.

- **Digital Resonator** — A filter section used to cancel zeros of a comb filter on the unit circle, enabling bandpass or highpass sinc filter implementations.

- **DSP (Digital Signal Processing)** — The numerical manipulation of signals primarily using digital filters and algorithms.

- **Embedded Multipliers** — Simple multiplier implementations in digital filters using shifts and adders for efficient computation.

- **Finite Impulse Response (FIR) Filter** — A filter whose impulse response lasts a finite duration; non-recursive and inherently stable.

- **Frequency Sampling Filter** — A bandpass filter built by summing sinc-shaped frequency responses, often implemented with comb filters and digital resonators.

- **Integrator** — A recursive filter element that sums input values over time, having an infinite impulse response (IIR).

- **Interpolation** — Increasing the sampling rate of a digital signal by inserting intermediate samples, often using sinc filters for image removal.

- **Least Significant Bit (LSB)** — The smallest voltage or binary step increment in a DAC or ADC, defined as (VREF+ - VREF-)/2^N.

- **Logic Level** — The voltage representing binary "1" or "0"; switching thresholds are typically VDD/2 in SPICE models.

- **Non-recursive Filter** — A digital filter whose output depends only on current and past input values (no feedback).

- **Overflow (in digital filters)** — When a sum or register exceeds its maximum representable value, potentially causing wrap-around errors or instability.

- **Pipeline ADC** — An analog-to-digital converter architecture that passes partial results through multiple stages with subtraction and multiplication.

- **Pole-Zero Cancellation** — A technique used to create selective frequency responses by positioning poles and zeros in the z-plane to cancel each other's effects.

- **Quantization Noise** — Noise introduced by the digital approximation of an analog signal due to finite resolution in ADCs.

- **Recursive Filter (IIR)** — A digital filter that uses feedback; outputs depend on current and previous outputs as well as inputs.

- **Sinc Filter** — A digital filter with a frequency response shaped like the sinc function, often implemented with comb and integrator stages.

- **Two's Complement Format** — A digital number representation for signed values, where the most significant bit represents the sign.

- **Zero Padding** — Inserting zeros between digital samples during interpolation to increase sampling rate before filtering.
