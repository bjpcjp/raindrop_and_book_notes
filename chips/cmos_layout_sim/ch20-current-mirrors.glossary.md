---
title: "ch20-current-mirrors — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch20-current-mirrors]
---

- **Beta-multiplier** — A self-biased circuit that uses transistor ratios and a resistor to generate a stable reference current independent of supply voltage.  
- **Bias current (IREF)** — The reference current set in a current mirror used to bias other transistors or circuits.  
- **Channel-length modulation (λ)** — The effect causing the MOSFET's drain current to vary with the drain-to-source voltage, reducing output resistance.  
- **Compliance range** — The output voltage range where a current mirror behaves like an ideal current source.  
- **Current mirror** — A circuit that copies (mirrors) a reference current to another branch, ideally maintaining a constant output current.  
- **Drain-to-source voltage (VDS)** — Voltage difference between the drain and source terminals of a MOSFET, critical for current mirror matching.  
- **Drain saturation voltage (VDS,sat)** — The minimum VDS required for a MOSFET to operate in saturation (active) region.  
- **Finite output resistance (ro)** — The non-ideal resistance at the output of a MOSFET current source, causing output current variation with output voltage changes.  
- **Footprint (MOSFET layout)** — The physical arrangement and sizing of a MOS transistor in silicon layout.  
- **Gate-source voltage (VGS)** — Voltage difference between the gate and source terminals of a MOSFET controlling its conduction.  
- **Input offset voltage mismatch** — The difference in threshold voltages or other parameters causing current mismatch in matched MOSFET pairs.  
- **Long-channel MOSFET** — A transistor with channel length large enough that short-channel effects are negligible, resulting in higher output resistance.  
- **Low-voltage (wide-swing) cascode** — A cascode current mirror designed to minimize the voltage overhead and enable operation at low supply voltages.  
- **MOSFET output resistance (ro)** — Resistance looking into the drain of a MOSFET in saturation, inversely related to channel-length modulation.  
- **Output resistance enhancement** — Techniques, such as cascode configurations or feedback amplifiers, used to increase the output resistance of current mirrors.  
- **Reference current (IREF)** — The known, stable current established in a current mirror circuit used as a baseline for other currents.  
- **Threshold voltage mismatch (ΔVTH)** — Variations in threshold voltage between matched transistors causing mismatch in mirrored currents.  
- **Transconductance parameter (KP)** — A process-dependent parameter representing a MOSFET’s gain factor, influencing current and matching.  
- **Wide-swing cascode** — A current mirror design that allows a reduced voltage drop across the mirror while maintaining transistor saturation conditions.  
- **Weak inversion (subthreshold) operation** — Mode where a MOSFET operates below threshold voltage, passing very small currents, useful for low-power designs.  
- **W/L ratio** — The width-to-length ratio of a MOSFET channel, used to scale transistor current capabilities and set current mirror ratios.
