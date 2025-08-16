---
title: "ch23-voltage-refs — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch23-voltage-refs]
---

- **Bandgap Reference (BGR)** — A voltage reference combining PTAT and CTAT voltages to produce a temperature-stable output near 1.2 V.  
- **Beta-Multiplier Reference (BMR)** — A self-biased voltage reference circuit using MOSFET current mirrors to set stable bias currents.  
- **Body-Effect** — The variation in MOSFET threshold voltage caused by changes in the voltage difference between the body and the source.  
- **Cascode** — A circuit technique involving stacking transistors to improve output resistance and reduce voltage sensitivity.  
- **Common-Mode Voltage** — A voltage level midway between power rails used as a reference or bias point in analog circuits.  
- **Complementary to Absolute Temperature (CTAT)** — A voltage or current that decreases with increasing temperature, like the forward voltage of a diode.  
- **Diode-Referenced Self-Biasing** — A reference design using a diode voltage to set operating current, resulting in a CTAT current behavior.  
- **Emission Coefficient (n)** — A parameter in diode equations that shapes the diode's I-V characteristic to match real devices.  
- **Forward Voltage Drop (VD)** — The voltage across a forward-biased diode, sensitive to temperature and current.  
- **MOSFET-Only Voltage Divider** — A voltage reference formed solely with MOSFETs, relying on their gate-source voltages and current matching.  
- **MOSFET-Resistor Divider** — A voltage reference using one MOSFET and one resistor to form a voltage divider, producing a voltage linked to the MOSFET’s threshold.  
- **Parasitic Diode** — A diode formed unintentionally in CMOS processes, typically at p-n junctions like the p+ implant and n-well.  
- **Process, Voltage, and Temperature (PVT) Variations** — Changes in device parameters due to manufacturing, supply voltage differences, or operating temperature shifts.  
- **Proportional to Absolute Temperature (PTAT)** — A voltage or current that increases linearly with temperature, such as thermal voltage-based references.  
- **Resistor Temperature Coefficient (TCR)** — A measure of how much a resistor’s resistance changes with temperature.  
- **Self-Biased Reference** — A reference circuit that uses feedback to force currents and voltages into specific stable operating points without external biasing.  
- **Series Resistance** — The parasitic resistance in series with a diode, affecting its I-V characteristics.  
- **Start-up Circuit** — A mechanism ensuring that a self-biased reference circuit begins operating correctly from zero initial current.  
- **Thermal Voltage (VT)** — A voltage proportional to absolute temperature (kT/q ≈ 26 mV at room temperature) used in PTAT references.  
- **Threshold Voltage (VTH)** — The minimum gate-to-source voltage required to turn on a MOSFET.  
- **Voltage Reference (VREF)** — A circuit output voltage that ideally remains stable despite changes in supply voltage, temperature, and process variations.  
- **Voltage Sensitivity** — The degree to which a reference voltage changes when supply voltage varies.  
- **Weak Inversion Operation** — The operating region of a MOSFET where it conducts very little current, below threshold voltage, commonly used in precision analog circuits.
