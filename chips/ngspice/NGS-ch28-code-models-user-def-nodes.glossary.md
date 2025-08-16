---
title: "NGS-ch28-code-models-user-def-nodes — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch28-code-models-user-def-nodes]
---

- **AC_GAIN(y,a)** — Macro returning the AC analysis gain of output ‘y’ with respect to input ‘a’ as a complex value.  
- **ANALYSIS** — Enum indicating simulation type: DC, AC, or TRANSIENT.  
- **ARGS** — Standard argument passed to every code model function holding all function context.  
- **CALL_TYPE** — Macro to determine if model call is event-driven or analog (EVENT or ANALOG).  
- **CODE MODEL** — User-extendable simulation model written in C defining behavior and interface for ngspice.  
- **COMPLEX_T** — A type representing a complex number with `.real` and `.imag` double components.  
- **CODENAME.LST (modpath.lst/udnpath.lst)** — Files listing code model or User-Defined Node directories for compilation linkage.  
- **CODE MODEL LIBRARY** — A shared library (*.cm) grouping multiple code models for dynamic loading into the simulator.  
- **DIGITAL_T** — Composite data type combining Digital_State_t (ZERO, ONE, UNKNOWN) and Digital_Strength_t (STRONG, RESISTIVE, etc.).  
- **DIGITAL_STATE_T** — Enum type for digital states: ZERO (0), ONE (1), or UNKNOWN (2).  
- **DIGITAL_STRENGTH_T** — Enum defining drive strength on a digital node (STRONG, RESISTIVE, HI IMPEDANCE, UNDETERMINED).  
- **EVENT-DRIVEN SIMULATION** — Simulation mode using discrete events rather than continuous time stepping.  
- **INIT** — Boolean macro indicating the first call to a code model instance to perform initialization.  
- **INPUT(port)** — Macro to access the value or pointer on an input port as defined in Interface Specification File.  
- **INTERFACE SPECIFICATION FILE (ifspec.ifs)** — Text file describing the naming, ports, parameters, and static variables of a code model.  
- **LOAD(port)** — Macro to post a capacitive load value to an event-driven port during simulation initialization.  
- **MODEL DEFINITION FILE (cfunc.mod)** — C source file defining the code model's functional behavior called by the simulator.  
- **NULL_ALLOWED** — Field specifying if a port or parameter may legally be left unconnected or omitted.  
- **OUTPUT(port)** — Macro to set or get the value or pointer of a model output port.  
- **OUTPUT_CHANGED(port)** — Macro indicating if a digital output port's value changed during the current simulation pass.  
- **PARTIAL(y,a)** — Macro for setting or accessing partial derivatives of outputs with respect to inputs for analog nodes.  
- **PARAM(name)** — Macro to access code model parameter values passed from the SPICE .MODEL card.  
- **PORT_NULL(port)** — Macro indicating whether a port is unconnected (null) within the simulation deck.  
- **PORT_SIZE(port)** — Macro providing the size of a vector port; undefined for scalar ports.  
- **SHARED LIBRARY (*.cm)** — Dynamically loadable library containing compiled code models or user-defined nodes.  
- **STATIC_VAR(name)** — Macro to access or assign static variables that preserve data between calls within a code model.  
- **USER-DEFINED NODE (UDN)** — Custom node type other than standard SPICE nodes enabling exchange of specialized data structures.  
- **udnfunc.c** — C file defining required and optional functions for implementing a User-Defined Node type.  
- **VECTOR (port/parameter)** — A multi-element port or parameter analogous to a bus with specified size constraints.
