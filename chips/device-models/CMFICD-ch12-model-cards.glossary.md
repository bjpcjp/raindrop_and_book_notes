---
title: "CMFICD-ch12-model-cards — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [CMFICD-ch12-model-cards]
---

- **BSIM4** — A widely used compact MOSFET model for circuit simulation that captures device physics including short-channel effects.  
- **Capacitance-Voltage (C–V)** — A device characteristic showing how capacitance varies with applied voltage, used in compact model parameter extraction.  
- **Channel Length (L)** — The physical length of the transistor's conducting channel, important for modeling short-channel effects.  
- **Channel Width (W)** — The width of the transistor channel, affecting current drive and device performance.  
- **Compact Model** — A simplified mathematical model of a semiconductor device used in circuit simulations to predict electrical behavior efficiently.  
- **Corner Simulation** — Circuit simulations performed using device parameters adjusted to represent process extremes, such as slow or fast device corners.  
- **Device Characteristics** — Electrical measurements (e.g., I–V, C–V) used to fit and extract compact model parameters.  
- **Device Mismatch** — Variations in device parameters, typically caused by random doping fluctuations, affecting threshold voltage and performance uniformity.  
- **Device Parameter Extraction** — The process of fitting measured or simulated device data to a compact model to obtain model parameters.  
- **Device Selection** — Choosing a representative set of device geometries covering the design space to capture physical and geometrical effects in the model.  
- **Golden Die** — A silicon die selected as the reference or standard for device characterization and model generation.  
- **Monte Carlo (MC) Simulation** — Statistical circuit simulation incorporating random variations of model parameters to predict variability effects.  
- **Mismatch Coefficient (Avt)** — A parameter quantifying threshold voltage variation due to random doping fluctuations.  
- **Model Card** — A file containing compact model parameters and settings used by circuit simulators like HSPICE.  
- **Model Library** — A collection of compact model cards representing various devices, corners, and process variations for circuit simulation.  
- **Model Validation** — Testing the compact model’s accuracy and predictive capability by comparing with measured data and ensuring simulation convergence.  
- **Process Corner** — A specific set of model parameters representing a variation condition of device manufacturing, such as typical, slow, or fast.  
- **Process Variability** — Deviations in device parameters caused by manufacturing fluctuations, affecting circuit performance and reliability.  
- **Statistical Compact Model** — A model that includes random and systematic variations to predict device behavior across process spreads.  
- **Subthreshold Region** — The region of transistor operation below the threshold voltage where current changes exponentially with gate voltage.  
- **Supply Voltage (Vdd)** — The nominal operating voltage of the device or circuit, used to define biasing conditions in model extraction.  
- **Systematic Variation** — Process-induced parameter shifts that affect all devices similarly within a wafer or die.  
- **Threshold Voltage (Vth)** — The gate voltage at which the transistor channel begins to conduct significantly.  
- **Temperature Range** — The range of ambient temperatures over which device characteristics are modeled and fitted.  
- **Transistor Folding (n_fingers)** — Layout technique where multiple transistor fingers are used to achieve a desired width while improving performance.  
- **Variability-Aware Circuit Design** — Designing circuits while accounting for device variations to ensure reliable operation across corners.  
- **Worst-Case Corner (SS, FF, SF, FS)** — Specific corners defining combinations of slow and fast NMOS and PMOS devices to envelope worst-case scenarios.
