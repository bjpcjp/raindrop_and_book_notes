---
title: "VLSI Physical Design, Springer Verlag — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VLSI-design-chap6]
---

- **Branch** — A vertical routing segment connecting pins or horizontal segments in channel routing.  
- **Channel Routing** — A detailed routing method that routes nets within a channel between two rows of cells.  
- **Constraint Graph** — A directed graph representing routing constraints; includes horizontal and vertical constraint graphs.  
- **Detailed Routing** — The stage assigning exact routing tracks, vias, and metal layers to nets based on global routing.  
- **Dogleg Routing** — A routing technique allowing splitting nets with multiple horizontal segments to reduce conflicts.  
- **Horizontal Constraint** — A restriction where overlapping horizontal segments of different nets cannot share the same track.  
- **Horizontal Constraint Graph (HCG)** — A graph modeling horizontal overlap constraints between nets to determine minimum track counts.  
- **Horizontal Segment (Trunk)** — The horizontal wire portion assigned to a routing track in channel routing.  
- **Left-Edge Algorithm** — A greedy channel routing algorithm that assigns nets to tracks from left to right while respecting constraints.  
- **Net Splitting** — Dividing a net into multiple segments to ease routing and reduce conflicts.  
- **Netlist** — A list of all the nets (connections) to be routed in the routing region.  
- **Over-the-Cell (OTC) Routing** — Routing technique that routes wires on top of standard cells using additional metal layers.  
- **Routing Track** — A predefined routing channel or path where nets are assigned horizontal segments.  
- **Switchbox Routing** — Routing method for connecting nets within switchboxes allowing flexible wire segment connections.  
- **Vertical Constraint** — A restriction where vertical segments from the top and bottom nets in the same column must not overlap.  
- **Vertical Constraint Graph (VCG)** — A directed graph representing vertical precedence constraints between nets to avoid conflicts.  
- **Vertical Segment (Branch)** — A vertical wire portion connecting horizontal segments or pins within a channel routing solution.  
- **Via** — A connection allowing a wire to pass between different metal layers in the routing stack.  
- **Zone Representation** — A representation showing which nets overlap horizontally and may share routing tracks in channel routing.
