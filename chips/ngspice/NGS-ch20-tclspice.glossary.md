---
title: "NGS-ch20-tclspice — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NGS-ch20-tclspice]
---

- **BLT** — A Tcl package that provides vector data structures and plotting capabilities within Tcl/Tk environments.  
- **BLT vector** — A data structure in BLT used to store and manipulate mathematical vectors for calculations and display.  
- **BLT graph** — A graphical object in BLT for plotting data stored in vectors, capable of dynamic updates.  
- **capacitance (virtual capacitance)** — A calculated value representing an active capacitor's effect, plotted as a function of control voltage in simulations.  
- **cost function** — A mathematical function used to measure the error or performance in optimization problems, minimized during circuit optimization.  
- **dylib/shared object (libspice.so)** — A compiled shared library of the SPICE simulation engine used by the Tcl interpreter to execute SPICE commands.  
- **ngspice CLI** — The traditional command-line interface version of the ngspice simulator compiled as a standalone program.  
- **optimization** — The process of iteratively adjusting circuit component values to minimize error between simulated and expected behavior.  
- **package (Tcl package)** — A reusable software module in Tcl providing functionalities such as spice and BLT packages.  
- **proc (procedure)** — A Tcl script-defined function used to organize code and operations such as simulations or calculations.  
- **spice::alter** — A Tclspice command to modify parameters or component values within a SPICE simulation environment.  
- **spice::let** — A Tclspice command used to define or calculate variables or expressions within the simulation context.  
- **spice::source** — A Tclspice command to load and run a SPICE netlist file within the Tcl environment.  
- **spice::vectoblt** — A Tclspice command that copies SPICE vector simulation data into a BLT vector for further processing and plotting.  
- **stripchart** — A BLT widget that displays data in a scrolling time series, useful for observing transient simulation results in real-time.  
- **Tcl (Tool Command Language)** — A scripting language used to interface with the ngspice engine in Tclspice for simulations and data processing.  
- **Tcl interpreter** — The runtime environment executing Tcl scripts and loading libraries like tclspice for SPICE commands.  
- **Tclspice** — A version of ngspice packaged as a Tcl library, enabling SPICE simulations within a Tcl scripting environment.  
- **Tk** — A graphical user interface toolkit for Tcl, used to display windows, graphs, and other visual elements.  
- **transient simulation** — A simulation mode that analyzes circuit behavior over time, often visualized with stripcharts in Tclspice.  
- **vector** — A one-dimensional array of numerical data representing simulation output such as voltage or current over frequency or time.  
- **wish** — The windowing shell for Tcl/Tk scripts, used to run Tclspice graphical simulations and interfaces.
