---
title: "VerilogQuickRef — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VerilogQuickRef]
---

- **Always** — A procedural block that triggers on specified events or signals.  
- **Assignment (blocking)** — A type of assignment where statements are executed sequentially within procedural blocks.  
- **Assignment (non-blocking)** — Assignments scheduled without blocking the procedural flow, commonly used for RTL modeling.  
- **Binary Literal** — An integer literal specified in binary form, e.g., `2’b1010`.  
- **Case Statement** — A conditional control structure for multi-way branching based on expressions.  
- **Compiler Directives** — Commands that control the compilation process, starting with a backtick `\``.  
- **Continuous Assignment** — Assignments that drive net values based on changes in source expressions; used for combinational logic.  
- **Data Types** — Defines the kind of data like `reg`, `wire`, `integer`, `real`, used for storage or signals.  
- **Delay** — Specifies timing parameters (rise, fall, turn-off) for gate and path modeling.  
- **Escaped Identifiers** — Names allowing non-alphanumeric characters, starting with a backslash and ending at whitespace.  
- **Gate Primitive** — Basic logic elements like `and`, `or`, `nand`, with possible drive strengths and delays.  
- **Module** — The fundamental building block defining a hardware component with input/output interfaces.  
- **Named Blocks** — Hierarchical grouping of statements within modules used for control and disabling.  
- **Net** — Represents physical connections between hardware components; examples include `wire`, `tri`, `wand`.  
- **Primitive UDP (User Defined Primitive)** — Custom primitives defined by truth tables that augment gate behavior.  
- **Register (`reg`)** — A data storage element that holds a value across simulation cycles.  
- **Reserved Keywords** — Words reserved by the language like `always`, `if`, `module`, and `assign` that have special meaning.  
- **Specify Block** — A block used to specify timing constraints and delay paths within a module.  
- **System Tasks/Functions** — Built-in utility functions for simulation control and output like `$display` and `$time`.  
- **Trireg** — A net type that retains its last driven value when all drivers are high impedance, modeling capacitive behavior.  
- **UDP (User Defined Primitive)** — Custom logic elements with defined truth tables allowing sequential or combinational behavior.  
- **Vectored** — Refers to a multi-bit bus or net that is treated as a vector rather than scalared (single bit).  
- **Wire** — A net type representing simple connections, requiring continuous driving of values.  
- **`ifdef` / `endif`** — Conditional compilation directives enabling or disabling code blocks.
