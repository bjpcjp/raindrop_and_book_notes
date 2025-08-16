1. **Q:** Explain the fundamental distinction between positive and negative feedback in amplifiers and describe how negative feedback impacts the stability and performance of an amplifier system.
   **A:** Positive feedback adds the output back to the input, causing instability and potentially uncontrolled output (e.g., audio feedback squeal in PA systems). Negative feedback subtracts the output from the input, stabilizing the system by desensitizing gain changes due to parameter variations, reducing distortion and noise, extending bandwidth, and controlling input/output impedance. Negative feedback improves linearity and makes the closed-loop gain largely independent of the open-loop gain if the latter is high.
   **External example:** Negative feedback used in op-amps to stabilize gain and improve linearity is standard practice in analog circuit design. [Texas Instruments, "Understanding Op Amp Applications" (see Feedback section)](https://www.ti.com/lit/an/sloa061a/sloa061a.pdf)

2. **Q:** Derive the expression for the closed-loop gain of a feedback amplifier from the open-loop gain and feedback factor, and explain the significance of the loop gain term.
   **A:** The closed-loop gain \(A_{CL}\) is given by \(A_{CL} = \frac{A_{OL}}{1 + A_{OL}\beta}\), where \(A_{OL}\) is the open-loop gain and \(\beta\) the feedback factor. The term \(A_{OL}\beta\), called the loop gain, determines how much the feedback influences overall gain and stability. If \(A_{OL}\) is very large, \(A_{CL} \approx \frac{1}{\beta}\), making the system gain dependent mostly on the feedback network rather than amplifier variations.
   **External example:** The loop gain concept is fundamental in control theory and amplifier design, as explained in [Sedra & Smith, Microelectronic Circuits](https://www.oup.com/us/companion.websites/9780199339136/materials/chapter27.pdf) (Chapter on Negative Feedback Amplifiers).

3. **Q:** Discuss how negative feedback affects the bandwidth of an amplifier and describe the trade-offs in gain and bandwidth as feedback changes.
   **A:** Negative feedback increases the amplifier’s bandwidth by a factor approximately equal to \(1 + A_{OL}\beta\), while simultaneously reducing the gain by the same factor. Essentially, as the feedback factor \(\beta\) decreases, the closed-loop gain increases, but the bandwidth decreases, approaching the original open-loop bandwidth—this trade-off allows one to tailor gain vs. bandwidth performance.
   **External example:** This gain-bandwidth trade-off is a classic principle demonstrated in op-amp frequency response analysis [Analog Devices, "An Introduction to Operational Amplifiers"](https://www.analog.com/en/education/education-library/introduction-to-operational-amplifiers.html).

4. **Q:** Explain how negative feedback influences the input and output impedances of an amplifier depending on the feedback type (series or shunt mixing/sampling) and summarize the impedance relationships for all four feedback topologies.
   **A:** Negative feedback modifies impedances by the factor \(1 + A_{OL}\beta\). If the input mixing is series (voltage), the input impedance increases by this factor; if shunt (current), it decreases by it. Similarly, if output sampling is series (current), output impedance increases; if shunt (voltage), it decreases. Table 31.1 summarizes:  
   - Series-Shunt: \(R_{in} \to R_{in}(1+A_{OL}\beta)\), \(R_{out} \to \frac{R_{out}}{(1+A_{OL}\beta)}\)  
   - Series-Series: \(R_{in} \to R_{in}(1+A_{OL}\beta)\), \(R_{out} \to R_{out}(1+A_{OL}\beta)\)  
   - Shunt-Series: \(R_{in} \to \frac{R_{in}}{1+A_{OL}\beta}\), \(R_{out} \to R_{out}(1+A_{OL}\beta)\)  
   - Shunt-Shunt: \(R_{in} \to \frac{R_{in}}{1+A_{OL}\beta}\), \(R_{out} \to \frac{R_{out}}{1+A_{OL}\beta}\)
   **External example:** These impedance transformation effects are foundational and found in [Sedra & Smith, Microelectronic Circuits, Ch. 27](https://ocw.mit.edu/courses/6-011-introduction-to-electronics-spring-2018/resources/27_negative_feedback/).

5. **Q:** Describe the procedure and rules for identifying the type of feedback topology in a given amplifier circuit.
   **A:** Identify if input variables (source, amplifier input, feedback) are voltages or currents—voltage variables correspond to series (voltage) mixing and current variables to shunt (current) mixing. Then identify the output variable: if it is voltage (feedback network in parallel with load) it is shunt sampling; if current (feedback network in series with load), series sampling. Use counting inversions—each common-source stage adds a 180° inversion—to ensure negative feedback (odd number of inversions leads to negative feedback with subtractive mixing). Consider loading effects from feedback network to determine open-loop gain path and feedback path correctly.
   **External example:** The classification method outlined is consistent with feedback analysis in [Wolaver, "Operational Amplifiers," 2008](https://homepages.rpi.edu/~lkofman/OpAmpCh6.pdf).

6. **Q:** Outline the method for determining the open-loop parameters (AOL, \(R_i\), \(R_o\), \(\beta\)) of a feedback amplifier including how to account for feedback network loading.
   **A:**  
   1. Replace input source with Thevenin/Norton equivalent.  
   2. Identify and isolate the basic amplifier (A0L).  
   3. Determine feedback network loading using two-port rules:  
      - For shunt mixing or sampling, short the respective port to ground to find input/output resistance of \(\beta\) network.  
      - For series mixing or sampling, "break" the connected device ("out-of-socket") and find input/output resistance.  
   4. Calculate feedback factor \(\beta\) as the gain from output to feedback input.  
   5. Compute open-loop gain AOL considering loading resistances.  
   6. Determine open-loop input/output impedances with the network loading included.  
   This accurate open-loop characterization is crucial for correct closed-loop analysis.
   **External example:** This method reflects two-port feedback design principles in [Sedra & Smith, Microelectronic Circuits](https://ocw.mit.edu/courses/6-011-introduction-to-electronics-spring-2018/).

7. **Q:** For the series-shunt voltage amplifier, derive the expressions for the closed-loop gain, input impedance, and output impedance including the loading effects of the feedback network.
   **A:** Closed-loop gain: \(A_{CL} = \frac{A_{OL}}{1 + A_{OL}\beta}\).  
    Input impedance: \(R_{in} = R_i (1 + A_{OL}\beta)\), because series input mixing multiplies input resistance.  
    Output impedance: \(R_{out} = \frac{R_o}{1 + A_{OL}\beta}\), because shunt output sampling divides output resistance.  
   Feedback network loading is accounted for by including the equivalent resistances (\(R_{\beta i}\) and \(R_{\beta o}\)) seen at input and output nodes (shorting output or breaking input as per rules). These modify \(R_i\) and \(R_o\) in the open-loop gain calculation.
   **External example:** These properties are core to op-amp voltage follower design, described in [Analog Devices Op-Amp Applications Handbook](https://www.analog.com/media/en/training-seminars/tutorials/MT-089.pdf).

8. **Q:** Explain the criteria for stability in feedback amplifiers based on the frequency response of the loop gain \(A_{OL}\beta\) and define gain margin and phase margin.
   **A:** Stability requires that at the frequency where the phase shift of the loop gain reaches -180°, the magnitude of \(A_{OL}\beta\) must be less than 1 (0 dB).  
   - If magnitude < 1 when phase = -180°, the system is stable.  
   - If magnitude = 1, system may be marginally stable.  
   - If magnitude > 1 at -180°, system is unstable.  
   Gain margin is the difference in dB between the loop gain magnitude and 0 dB at the phase crossover frequency (-180° phase).  
   Phase margin is the difference in degrees between the phase at the gain crossover frequency (where magnitude = 1) and -180°.  
   Typically, a phase margin ≥ 45° or preferably 60° ensures stable behavior with minimal ringing.
   **External example:** Stability margins are standard in control systems, as summarized by [IEEE Control Systems Society tutorial](https://ieeexplore.ieee.org/document/1213013).

9. **Q:** Define and describe the return ratio (RR) method for evaluating the loop gain and stability of feedback amplifiers, including the procedure for breaking the loop.
   **A:** The return ratio method breaks the feedback loop at the dependent source, replaces it with an independent test source, and measures the returned signal ratio at the break point. Formally, RR = \(\frac{X_f}{X_i}\) (feedback variable over input test variable).  
   Steps:  
   1. Replace all independent sources with their internal impedances.  
   2. Break the feedback loop at the dependent source (i.e., remove and insert a test signal).  
   3. Inject a test signal and determine the returned signal at the dependent source.  
   4. Calculate RR as the ratio of returned signal to test signal. RR approximates the loop gain frequency response for stability analysis.
   **External example:** Return ratio is used in analog IC design tools and is detailed in [Hurst, IEEE Transactions on Circuits and Systems, 1991](https://ieeexplore.ieee.org/document/92794).

10. **Q:** Summarize the key considerations when designing CMOS feedback amplifiers with regard to device sizing, biasing, and the trade-offs evident in the voltage buffer and transimpedance amplifier examples.
    **A:** Device sizing and biasing must maintain consistent overdrive voltages to control transition frequencies and gain-bandwidth trade-offs. Using active MOS loads maximizes open-loop gain. For voltage buffers, reducing body effect (e.g., using complementary transistors) improves gain. Peaking due to inductive output impedance effect from source followers can be mitigated via compensation. For transimpedance amplifiers, minimal input resistance is critical to avoid signal loss, but device leakage and gate currents due to process scaling can degrade accuracy, necessitating smaller devices or older processes to reduce leakage. Resistor/ MOS loads in feedback networks affect gain and input resistance, so size and topology choices are application-dependent.
    **External example:** These CMOS design considerations align with those in [Razavi, "Design of Analog CMOS Integrated Circuits"](https://www.amazon.com/Design-Analog-CMOS-Integrated-Circuits/dp/0072380323).
