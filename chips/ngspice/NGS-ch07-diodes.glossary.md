---
title: "NGS-ch07-diodes — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch07-diodes]
---

- **Area** — A scale factor representing the junction area of the diode, affecting saturation current and capacitances.  
- **Avalanche breakdown** — The region where the diode current increases exponentially due to high reverse voltage, modeled by breakdown voltage (BV) and breakdown current (IBV).  
- **BV (Breakdown Voltage)** — The reverse voltage at which the diode enters avalanche breakdown.  
- **Capacitance (CJO, CJP)** — Junction capacitances composed of bottom-wall (CJO) and sidewall (CJP) components affected by voltage and temperature.  
- **Depletion capacitance** — Capacitance due to the depletion region of the diode, includes bottom-wall and sidewall parts.  
- **Diffusion capacitance** — Capacitance associated with charge storage from injected minority carriers, modeled via transit time (TT).  
- **Emission coefficient (N)** — Parameter reflecting the ideality of the diode’s forward current; affects the diode equation exponent.  
- **FC (Forward-bias coefficient)** — Coefficient controlling forward-bias depletion capacitance modeling for the bottom-wall.  
- **FCS** — Coefficient controlling forward-bias depletion capacitance modeling for the sidewall.  
- **High injection effects** — Phenomena at large currents causing deviation from ideal exponential behavior, modeled by knee currents IK and IKR.  
- **IC (Initial condition)** — Specifies the starting voltage across a diode for transient simulations.  
- **IS (Saturation current)** — The diode’s reverse saturation current under nominal conditions, scaled by area and perimeter.  
- **JSW (Sidewall saturation current)** — Saturation current assigned to the diode’s perimeter (sidewall), distinct from bulk saturation current.  
- **KT, kT** — Thermal voltage equivalent at temperature T, used in diode equations (kT/q).  
- **M (MJ)** — Grading coefficient affecting the junction capacitance voltage dependence for the bottom-wall.  
- **MJSW** — Grading coefficient for sidewall depletion capacitance.  
- **Multiplier (m)** — Scales both area and perimeter parameters to model multiple identical diode elements.  
- **NBV (Nominal breakdown voltage)** — See BV; the standard value for breakdown voltage before temperature adjustments.  
- **NOMINAL TEMPERATURE (TNOM)** — Temperature at which model parameters are originally measured or defined.  
- **Off** — Parameter indicating a diode starts off (non-conducting) for DC analysis in simulations.  
- **Perimeter (pj)** — Scale factor representing the diode’s sidewall length, influencing related current and capacitances.  
- **PLE (Periphery junction potential, PHP)** — Built-in potential associated with the diode’s perimeter junction.  
- **Reverse knee current (IKR)** — Current parameter modeling diode behavior in reverse bias high injection conditions.  
- **RS (Series resistance)** — Ohmic resistance in series with the diode, limiting current and affecting voltage drop.  
- **Saturation current temperature exponent (XTI)** — Parameter governing temperature dependence of saturation current.  
- **Sidewall capacitance (CJP, CJSW)** — Junction capacitance associated with the diode’s sidewall region.  
- **Temperature offset (dtemp)** — Instance-level parameter to adjust diode temperature relative to circuit temperature.  
- **Transit Time (TT)** — Time delay parameter modeling charge storage effects, impacts diffusion capacitance and transient response.
