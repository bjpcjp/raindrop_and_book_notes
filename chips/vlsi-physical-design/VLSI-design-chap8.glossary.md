---
title: "VLSI Physical Design, Springer Verlag — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VLSI-design-chap8]
---

- **AAT (Actual Arrival Time)** — The time at which a signal actually arrives at the output of a node during timing analysis.  
- **BRBC (Bounded-Radius, Bounded-Cost) Algorithm** — A routing method balancing delay (radius) and wirelength (cost) with adjustable bounds.  
- **Clock Skew** — The time difference in clock arrival at sequential elements, affecting timing constraints.  
- **Critical Path** — The longest delay path in a circuit that determines maximum operating speed.  
- **Critical Sink** — The most timing-critical sink node in routing optimization for minimizing delays.  
- **DAG (Directed Acyclic Graph)** — A graph representing a combinational circuit with nodes as gates and edges as signal flow without cycles.  
- **Delay Budgeting** — Allocating delay targets to gates and nets to guide layout timing optimization.  
- **Gate Sizing** — Adjusting the physical size of a gate to modify its drive strength and delay for timing improvement.  
- **Hold Time Constraint** — The minimum time data must remain stable after a clock edge to ensure correct operation.  
- **HPWL (Half-Perimeter Wirelength)** — An estimate of net wirelength calculated as the half perimeter of the net’s bounding box.  
- **Linear Program (LP)** — A mathematical model used to optimize placement including timing and physical constraints.  
- **Load Capacitance** — The capacitive load a gate output drives, affecting its delay and performance.  
- **Minimum Spanning Tree (MST)** — A tree connecting all points (nodes) with minimum total edge weight for routing.  
- **Net Weight** — A factor representing the timing criticality of a net, used to prioritize placement or routing optimization.  
- **Physical Synthesis** — Post-placement and routing netlist modifications such as gate sizing and buffering to improve timing.  
- **Prim-Dijkstra Tradeoff** — A routing technique interpolating between MST (Prim) and shortest-path (Dijkstra) solutions.  
- **RAT (Required Arrival Time)** — The latest time a signal must arrive at a node’s output without violating timing constraints.  
- **Routing Cost** — The penalty or metric representing wirelength and delay for routing edges.  
- **Setup Time Constraint** — The required time data must be stable before the clock edge for correct storage element operation.  
- **Slack** — The difference between a signal’s required arrival time and actual arrival time; positive slack satisfies timing, negative slack violates it.  
- **Static Timing Analysis (STA)** — A method to evaluate timing of a circuit without simulation by computing arrival and required times.  
- **Timing Closure** — The iterative process of modifying design and layout until all timing constraints are met.  
- **Timing Endpoint** — Nodes in the timing graph where timing constraints are checked, such as sequential element inputs or outputs.  
- **Total Negative Slack (TNS)** — The sum of all timing slacks that are negative, quantifying overall timing violations.  
- **Worst Negative Slack (WNS)** — The largest magnitude negative slack, representing the worst timing violation in the design.  
- **Zero-Slack Algorithm** — A method to distribute available slack evenly along timing paths to improve budgeting and optimization.
