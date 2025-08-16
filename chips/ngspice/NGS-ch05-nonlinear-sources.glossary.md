---
title: "NGS-ch05-nonlinear-sources — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch05-nonlinear-sources]
---

- **AC analysis** — A simulation that computes the steady-state response of a circuit to sinusoidal inputs at various frequencies.  
- **Behavioral source** — A dependent source that produces voltages or currents based on mathematical expressions, enabling custom device modeling.  
- **B source (ASRC)** — A nonlinear dependent source defined by an expression for current or voltage, supporting temperature and frequency dependency.  
- **Control voltage/current** — The voltage or current used as an input variable for controlling a behavioral source's output.  
- **Derivative (small-signal)** — The proportionality constant of a nonlinear source’s linearized small-signal equivalent at the DC operating point.  
- **dtemp** — Differential temperature input used to modify device temperature; ignored if temp is explicitly set.  
- **E source (nonlinear voltage source)** — A voltage source controlled by an expression or data table, capable of modeling nonlinear behavior, including polynomial and table-based dependencies.  
- **Expression** — A mathematical formula using node voltages, branch currents, parameters, and functions to define source output.  
- **Functions (behavioral sources)** — Supported mathematical functions like trigonometric, hyperbolic, exponential, logarithmic, and piecewise step functions for defining behavioral sources.  
- **hertz** — Special variable representing the frequency in AC analysis, used in frequency-dependent behavioral expressions.  
- **I(T), V(T)** — Temperature-dependent current or voltage defined by polynomial temperature coefficients TC1 and TC2 relative to nominal temperature.  
- **Logarithmic and exponential functions** — Functions such as log, ln, log10, and exp used within behavioral expressions for nonlinear source modeling.  
- **LAPLACE (behavioral source)** — A method to define sources with complex frequency-dependent behavior via Laplace transforms; implemented in ngspice with XSPICE models.  
- **m (multiplier)** — Optional factor multiplying the output current or voltage of G or E sources; evaluated before simulation starts.  
- **Parameter** — A symbolic constant defined with .param, used in expressions for flexible and reusable source definitions.  
- **Piecewise linear (pwl) function** — A function defined by multiple linear segments specified as x,y pairs for modeling nonlinear dependencies in behavioral sources.  
- **POLY (polynomial source)** — A source defined by polynomial expressions of controlling node voltages, available with XSPICE enabled.  
- **Special variables** — Variables like time (simulation time), temper (circuit temperature), and hertz (AC frequency) available within behavioral expressions for dynamic modeling.  
- **Table function** — A behavioral source feature using tabulated x,y pairs to define output values by linear interpolation, optionally with limiting outside the table range.  
- **Temperature behavior (TC1, TC2)** — Coefficients defining linear and quadratic temperature dependence of source outputs relative to nominal temperature.  
- **ternary function (a ? b : c)** — A conditional operator selecting output b if condition a is true, else output c, used in behavioral expressions.  
- **time** — Special variable representing simulation time in transient analysis, zero in AC analysis.  
- **u, u2, uramp functions** — Step and ramp functions used to model piecewise nonlinearities with discontinuities or ramps in expressions.  
- **V( node )** — Voltage at a specified circuit node, used as input in behavioral source expressions.  
- **vpos, vneg** — Positive and negative terminals of a behavioral source.  
- **Voltage source (VCVS, VCVS behavioral)** — Sources generating voltage outputs defined by behavioral expressions, including E and B sources.  
- **Voltage controlled current source (VCCS)** — A source generating current outputs based on controlling voltages, implementable with G or behavioral sources.  
- **XSPICE option** — A simulator feature extending standard behavioral modeling with polynomial sources and Laplace models.
