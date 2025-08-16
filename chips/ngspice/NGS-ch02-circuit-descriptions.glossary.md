---
title: "NGS-ch02-circuit-descriptions — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch02-circuit-descriptions]
---

- **.CONTROL section** — A block of command scripts enclosed by `.control` and `.endc`, used to run interactive or batch commands after simulation.  
- **.END line** — The mandatory final line in a netlist file indicating the end of input; must begin with a period.  
- **.INCLUDE** — A directive to insert the contents of an external file directly into the netlist at the point of inclusion.  
- **.LIB** — Includes a device library file and selects a specific library section for use in the netlist.  
- **.MODEL** — Defines a device model with specified parameters for semiconductor and other devices.  
- **.PARAM** — Assigns numerical or expression-based parameter values used for defining variables and expressions throughout the netlist.  
- **.SUBCKT** — Defines a reusable subcircuit with external nodes and optional parameters; enclosed by `.SUBCKT` and `.ENDS` lines.  
- **.ENDS** — Marks the end of a subcircuit definition, optionally specifying which subcircuit is ended.  
- **.TEMP** — Specifies the simulation temperature in degrees Celsius, overriding default or option settings.  
- **.TITLE line** — The first line in the input file that serves as the title and description for the simulation; can be overridden by a `.TITLE` statement.  
- **.GLOBAL** — Declares nodes that are accessible globally across all circuits and subcircuits regardless of hierarchy.  
- **.IF conditional** — A netlist control structure allowing conditional inclusion of lines in the netlist based on parameter expressions.  
- **.FUNC** — Defines a symbolic function that can replace expressions and be used in parametric definitions.  
- **.CSPARAM** — Creates a constant vector from an evaluated parameter for use in plotting or scripting contexts.  
- **Brace expression `{}`** — A syntax for including arithmetic expressions evaluated during netlist parsing, used in parameters and device values.  
- **Element instance line** — A netlist line defining a circuit element with a name, nodes, and parameter values specifying its electrical behavior.  
- **Node** — A connection point in a circuit; named arbitrarily except the ground node which must be `0`.  
- **Parameter** — A named numerical or expression value used to make netlists parametric and reusable.  
- **Scale factor suffixes** — Letter codes like `k`, `m`, `u` appended to numbers to denote multipliers (e.g., `k` for 10³, `m` for 10⁻³).  
- **Subcircuit call** — Instantiation of a subcircuit within a netlist using a line beginning with `X`, connecting subcircuit ports to circuit nodes and optional parameters.  
- **Switch element types** — Voltage-controlled (`S`) or current-controlled (`W`) switches used in circuit descriptions.  
- **Voltage source (V)** — An element representing an ideal voltage source.  
- **Current source (I)** — An element representing an ideal current source.  
- **Digital, analog, mixed-signal elements** — Categories of device types supported, such as XSPICE models, for various simulation needs.  
- **Expression syntax** — Defines arithmetic and logical operations used in parameters and functions, supporting operators like `+`, `-`, `*`, logical `&&`, `||`, and ternary `?:`.  
- **Logical operators** — Operators like `&&` (and), `||` (or), and `!` (not) used in parametric expressions for boolean logic.  
- **Ground node (`0`)** — The universal reference node in a circuit, mandatory for all netlists.  
- **Element name prefix** — The first letter of an element's instance name indicating its type (e.g., `R` for resistor, `C` for capacitor).
