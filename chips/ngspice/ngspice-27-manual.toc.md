---
title: "ngspice user manual"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ngspice-27-manual]
---

- Prefaces
- 1 Introduction
  - 1.1 Simulation Algorithms
    - 1.1.1 Analog Simulation
    - 1.1.2 Digital Simulation
    - 1.1.3 Mixed-Signal Simulation
      - 1.1.3.1 User-Defined Nodes
    - 1.1.4 Mixed-Level Simulation
      - 1.1.4.1 CIDER (DSIM)
      - 1.1.4.2 GSS TCAD
  - 1.2 Supported Analyses
    - 1.2.1 DC Analysis
    - 1.2.2 AC Small-Signal Analysis
    - 1.2.3 Transient Analysis
    - 1.2.4 Pole-Zero Analysis
    - 1.2.5 Small-Signal Distortion Analysis
    - 1.2.6 Sensitivity Analysis
    - 1.2.7 Noise Analysis
    - 1.2.8 Periodic Steady State Analysis
  - 1.3 Analysis at Different Temperatures
  - 1.4 Convergence
    - 1.4.1 Voltage convergence criterion
    - 1.4.2 Current convergence criterion
    - 1.4.3 Convergence failure
- 2 Circuit Description
  - 2.1 General Structure and Conventions
    - 2.1.1 Input file structure
    - 2.1.2 Circuit elements (device instances)
    - 2.1.3 Some naming conventions
  - 2.2 Basic lines
    - 2.2.1 .TITLE line
    - 2.2.2 .END Line
    - 2.2.3 Comments
    - 2.2.4 End-of-line comments
  - 2.3 .MODEL Device Models
  - 2.4 .SUBCKT Subcircuits
    - 2.4.1 .SUBCKT Line
    - 2.4.2 .ENDS Line
    - 2.4.3 Subcircuit Calls
  - 2.5 .GLOBAL
