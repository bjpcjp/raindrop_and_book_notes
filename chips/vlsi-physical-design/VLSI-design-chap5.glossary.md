---
title: "VLSI Physical Design, Springer Verlag — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VLSI-design-chap5]
---

- **A\* Search** — Algorithm used to find shortest paths using heuristics to speed up pathfinding.
- **Backward Routing** — Routing direction or method starting from the endpoint back to the source.
- **Channel** — Rectangular routing region with pins on two opposite sides.
- **Circuit Design** — The process of creating a circuit's logical structure before placement.
- **Congestion** — Conflict arising when multiple nets compete for the same routing tracks.
- **Connectivity Graph** — Graph representing routing regions or channels as nodes and their adjacencies as edges.
- **Crosspoint** — Fixed point along edges of routing regions used for wiring assignment.
- **Detailed Routing** — Fine-grain assignment of routes to specific wiring tracks within routing regions.
- **Design Rules** — Technology-specific constraints for wire widths, spacing, and routing.
- **Feedsthrough Cells** — Special cells used in standard-cell design to route signals across rows.
- **Fixed-Die Routing** — Routing approach with fixed chip outline and routing resources.
- **Global Routing** — Coarse routing stage assigning nets to routing regions, considering capacity and congestion.
- **Global Routing Flow** — Process including region definition, net-to-region mapping, and crosspoint assignment.
- **Gcells (Grid Cells)** — Tiles representing routing regions in a grid graph.
- **Hanan Grid** — Grid formed by lines through terminal pins used as candidate points for Steiner tree construction.
- **Integer Linear Programming (ILP) Routing** — Routing method formulating net routing as mathematical optimization.
- **Midway Routing** — Assignment of routes to specific points (crosspoints) along region edges during routing.
- **Net** — Set of two or more pins electrically connected.
- **Netlist** — Complete set of all nets in a design.
- **Non-uniform Routing Region** — Routing region with boundaries aligned to pins or macros, resulting in variable sizes.
- **Placement** — Step assigning physical locations to circuit elements.
- **Rectilinear Minimum Spanning Tree (RMST)** — Tree connecting terminals with minimum total rectilinear wirelength without Steiner points.
- **Rectilinear Steiner Minimum Tree (RSMT)** — Wire tree that may include additional Steiner points to minimize wirelength.
- **Region Assignment** — Process of mapping nets to routing regions for connectivity.
- **Routing Column** — Vertical wiring path in routing regions.
- **Routing Region** — Area containing routing tracks or columns for wiring nets.
- **Routing Track** — Horizontal wiring path in routing regions.
- **Routing Resources** — Available wiring tracks or columns represented as capacities in routing graphs.
- **Rip-Up and Reroute (RRR)** — Iterative global routing technique to resolve congestion by rerouting nets.
- **Sequential Steiner Tree Heuristic** — Method to construct Steiner trees incrementally by combining closest points.
- **Signal Routing** — Routing processes to connect all circuit pins after placement.
- **Switchbox** — Intersection area of horizontal and vertical routing channels.
- **Timing Closure** — Step ensuring all timing constraints are met after routing and placement.
- **Variable-Die Routing** — Routing allowing addition of new routing tracks as needed.
