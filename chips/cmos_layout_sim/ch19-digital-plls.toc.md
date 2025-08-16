---
title: "ch19-digital-plls"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch19-digital-plls]
---

- Chapter 19 Digital Phase-Locked Loops
  - 19.1 The Phase Detector
    - 19.1.1 The XOR Phase Detector
    - 19.1.2 The Phase Frequency Detector
  - 19.2 The Voltage-Controlled Oscillator
    - 19.2.1 The Current-Starved VCO
    - Linearizing the VCO's Gain
    - 19.2.2 Source-Coupled VCOs
  - 19.3 The Loop Filter
    - 19.3.1 XOR DPLL
    - Active-PI Loop Filter
    - 19.3.2 PFD DPLL
      - Tri-State Output
      - Implementing the PFD in CMOS
      - PFD with a Charge Pump Output
  - 19.4 System Considerations
    - Distortionless Transmission and Equalizers
    - Clock Recovery from NRZ Data
      - Edge Detector
      - The Hogge Phase Detector
    - Jitter in DPLLs
  - 19.5 Delay-Locked Loops
    - Delay Elements
    - Practical VCO and VCDL Design
  - 19.6 Some Examples
    - 19.6.1 A 2 GHz DLL
