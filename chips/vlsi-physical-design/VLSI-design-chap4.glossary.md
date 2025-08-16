---
title: "VLSI Physical Design, Springer Verlag — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VLSI-design-chap4]
---

- **Analytic Placement** — A mathematical approach to placement using cost functions optimized through numerical analysis, such as quadratic or force-directed methods.  
- **Attraction Force** — In force-directed placement, the force proportional to the distance between connected cells, pulling them together.  
- **Balanced Placement** — A placement strategy that balances competing objectives like wirelength, congestion, and delay.  
- **Cell Spreading** — Techniques used after quadratic placement to reduce overlaps by redistributing cells in dense areas.  
- **Circuit Timing** — Analysis of delays in a circuit using arrival and required arrival times to ensure correct operation.  
- **Complete Graph Model (Clique)** — A wirelength estimation method modeling all connections in a net as fully connected edges.  
- **Cut Nets** — Nets that are intersected by a dividing line in the layout, influencing wirelength and congestion.  
- **Cutline** — A vertical or horizontal line used in min-cut placement to divide a layout region.  
- **Detailed Placement** — The step after global placement, refining cell locations to legalize and optimize placement.  
- **Force-Directed Placement** — An analytic placement method modeling cells and nets as springs, moving cells toward force equilibrium.  
- **Global Placement** — The initial placement stage where cells are roughly positioned to minimize objectives like wirelength and congestion.  
- **Half-Perimeter Wirelength (HPWL)** — A fast wirelength estimation based on the perimeter of the bounding box around connected cells.  
- **Kernighan-Lin (KL) Algorithm** — A heuristic for partitioning graphs to reduce the number of cut nets in placement.  
- **Legalization** — The process of adjusting cell positions post-global placement to eliminate overlaps and abide by design rules.  
- **Minimum Cut Placement (Min-Cut Placement)** — A hierarchical placement method dividing netlists and layout into regions to minimize cut nets.  
- **Monotone Chain Model** — A wirelength estimation method using a chain-like model connecting pins in order.  
- **Netlist** — The collection of cells and the connections (nets) between them in a circuit design.  
- **Partial Derivative (in Placement)** — Used in quadratic placement to find optimal positions by setting gradients of the cost function to zero.  
- **Placement Region** — A sub-area of the chip layout assigned to a subset of cells during hierarchical placement.  
- **Required Arrival Time (RAT)** — The latest time a signal must arrive at a node for proper chip operation.  
- **Simulated Annealing** — A stochastic optimization algorithm inspired by metal cooling, accepting worse solutions with decreasing probability.  
- **Signal Delay** — The time duration for a signal to propagate through the circuit, crucial for timing constraints.  
- **Static Timing Analysis** — Technique to determine timing behavior of circuits using arrival and required arrival times.  
- **Star Model** — Wirelength estimation using a central “star” connection point to reduce total wirelength.  
- **Steiner Tree** — A minimal interconnection structure possibly adding extra points (Steiner points) to reduce wirelength.  
- **Total Wirelength** — The sum of estimated connection lengths across all nets, often weighted by net importance.  
- **Wire Congestion** — The density of routing demands relative to available routing resources, impacting route feasibility.  
- **Wire Density (Wireload)** — The ratio of estimated demands for routing tracks to available capacity on layout edges.
