---
title: "NGS-ch12-mixedmode-behav-modeling-xspice — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch12-mixedmode-behav-modeling-xspice]
---

- **AC Analysis** — Simulation mode analyzing circuit behavior with sinusoidal steady-state signals.  
- **Analog Switch** — A switch modeled as a variable resistor controlled by an input voltage or current.  
- **Capacitance Meter** — Model that outputs a scaled total capacitance seen on its input node.  
- **Code Model** — User-defined or predefined models implemented as C code for behavioral or mixed-mode simulation.  
- **Controlled Limiter** — A limiter where upper and lower limits are set by separate control inputs.  
- **Controlled One-Shot** — A pulse generator triggered by a clock input, outputting pulses whose width is controlled by an input.  
- **Controlled Sine Wave Oscillator** — Oscillator producing a sine wave with frequency controlled by an input’s piecewise linear function.  
- **Controlled Square Wave Oscillator** — Oscillator producing a square wave with controllable frequency, duty cycle, and transition times.  
- **Controlled Triangle Wave Oscillator** — Oscillator producing a triangle wave with frequency controlled by an input’s piecewise linear function.  
- **DAC Bridge** — Model converting digital logic levels (0, 1, U) to corresponding analog voltages.  
- **Differentiator Block** — Model calculating the time-derivative of an input signal with gain and output limits.  
- **Digital Port (%d)** — Model input/output representing digital signals with discrete logical states.  
- **Digital-to-Analog Node Bridge** — Model converting digital inputs into analog output signals.  
- **File Source** — Model that reads a waveform from an external file for use as a time-dependent source.  
- **Gain Block** — Basic model applying gain and input/output offsets to an input signal.  
- **Hysteresis Block** — Model that provides output hysteresis with smoothed transitions based on input thresholds.  
- **Inductance Meter** — Model outputting scaled total inductance seen on its input node.  
- **Inductive Coupling (lcouple)** — Model representing magnetomotive force proportional to current times number of turns, used for magnetic coupling.  
- **Integrator Block** — Model approximating the time integral of an input signal with gain, offset, and output limits.  
- **Limiter** — Model restricting output values to specified upper and lower limits with smoothing near boundaries.  
- **Memristor** — Two-terminal resistor with memory, whose resistance depends on voltage integral over time.  
- **Mixed-Mode Simulation** — Combined simulation of analog and digital circuits using event-driven evaluation for digital parts.  
- **Multi-Input PWL Block** — Voltage-controlled voltage source supporting logical AND/OR functionality with piecewise linear characteristics.  
- **PWL Controlled Source** — Piecewise linear source producing output based on input using defined x/y coordinate pairs with smoothing.  
- **Port Type Modifiers** — Symbols (%v, %i, %vd, etc.) indicating the expected port signal type (voltage, current, digital, differential).  
- **S-domain Transfer Function** — Model implementing a Laplace-domain transfer function defined by numerator and denominator polynomials.  
- **Search Path for File Input** — Ordered locations where simulation looks for external files referenced by code models.  
- **Slew Rate Block** — Model limiting the maximum rising and falling slopes of the output signal.  
- **Static Variable** — Internal memory used during simulations to retain state across iterations (e.g., previous_voltage).
