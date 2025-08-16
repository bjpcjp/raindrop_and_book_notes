---
title: "VLSI Physical Design, Springer Verlag — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VLSI-design-chap7]
---

- **Area Routing** — Routing technique that directly constructs metal routes within the layout space without separate global and detailed routing steps.  
- **Aspect Ratio** — The ratio of the width to the height of a net’s bounding box, used to prioritize routing order.  
- **Bounding Box (MBB)** — The smallest rectangle enclosing all pins of a net, used for routing and ordering decisions.  
- **Clock Skew** — Difference in arrival times of a clock signal between two or more sinks in a clock network.  
- **Clock Sink** — A point or terminal in a clock network where the clock signal is delivered, often a sequential element.  
- **Clock Source** — The origin point in a clock network where the clock signal is generated.  
- **Clock Tree** — A rooted binary tree connecting the clock source to all sinks for signal distribution with controlled skew.  
- **Constructive Heuristics** — Algorithms that build routing solutions step-by-step, often used to decide net ordering.  
- **Elmore Delay Model** — A method to estimate signal delay along wires based on resistance and capacitance for timing analysis.  
- **Embedding** — The geometric realization or precise placement of the nodes and edges of a clock tree topology on the layout.  
- **Global Skew** — The maximum difference in clock arrival times between any two clock sinks in the entire network.  
- **Local Skew** — The difference in clock arrival times at closely related sinks, such as flip-flops connected by signal paths.  
- **Manhattan Distance** — Distance metric where movement is restricted to horizontal and vertical paths, summing absolute differences in coordinates.  
- **Manhattan Arc** — A line segment representing all possible zero-skew connection points between two sinks in Manhattan geometry.  
- **Method of Means and Medians (MMM)** — A top-down clock tree construction method partitioning sinks by median and connecting their centers of gravity.  
- **Minimum-Cost Geometric Matching** — An optimization step for pairing sinks to minimize total wirelength during clock tree construction.  
- **Net Ordering** — The sequence in which nets are routed, affecting overall routability and wirelength.  
- **Octilinear Routing** — Routing using eight possible directions (horizontal, vertical, and diagonals at 45°) allowing more flexible paths than Manhattan routing.  
- **Octilinear Steiner Minimum Tree (OSMT)** — A Steiner tree constructed with octilinear directions to minimize total wirelength while connecting all pins.  
- **Partitioning** — Dividing sets of points (e.g., sink terminals) into subsets during recursive algorithms for routing or clock tree construction.  
- **Skew Bound** — An allowable maximum difference in clock arrival times, relaxing the zero skew requirement for practical designs.  
- **Steiner Point** — Additional nodes added to a routing tree to reduce total wirelength and improve routing efficiency.  
- **Tapping Point** — A carefully chosen point on an edge in a clock tree used to maintain zero skew by balancing delays.  
- **Via** — A vertical electrical connection between two or more routing layers in integrated circuits.  
- **Wire Length** — The physical length of routed wires connecting pins or terminals; minimizing it is a key routing objective.
