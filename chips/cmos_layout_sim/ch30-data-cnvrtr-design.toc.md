---
title: "ch30-data-cnvrtr-design"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch30-data-cnvrtr-design]
---

- Chapter 30 Implementing Data Converters  
  - 30.1 R-2R Topologies for DACs  
    - 30.1.1 The Current-Mode R-2R DAC  
    - 30.1.2 The Voltage-Mode R-2R DAC  
    - 30.1.3 A Wide-Swing Current-Mode R-2R DAC  
      - DNL Analysis  
      - INL Analysis  
      - Switches  
      - Experimental Results  
      - Improving DNL (Segmentation)  
      - Trimming DAC Offset  
      - Trimming DAC Gain  
      - Improving INL by Calibration  
    - 30.1.4 Topologies Without an Op-Amp  
      - The Voltage-Mode DAC  
      - The Current-Mode (Current Steering) DAC  
  - 30.2 Op-Amps in Data Converters  
    - Gain Bandwidth Product of the Noninverting Op-Amp Topology  
    - Gain Bandwidth Product of the Inverting Op-Amp Topology  
    - 30.2.1 Op-Amp Gain  
    - 30.2.2 Op-Amp Unity Gain Frequency  
    - 30.2.3 Op-Amp Offset  
      - Adding an Auxiliary Input Port  
      - Offset Trimming Techniques  
      - Fully-Differential Offset Compensation  
      - Continuous-Time Offset Removal  
  - 30.3 Implementing ADCs  
    - 30.3.1 Implementing the S/H  
      - Single-Ended to Differential Output S/H  
      - Common-Mode Feedback Circuit  
    - 30.3.2 The Cyclic ADC  
      - Comparator Placement  
      - Implementing Subtraction in the S/H  
      - Transfer Curves and Output Swing  
    - 30.3.3 The Pipeline ADC  
      - Time-Interleaved ADCs  
      - Pipeline ADC Architecture  
      - Using 1.5 Bits/Stage for Error Correction  
      - Digital Output Combination and Correction
