---
title: "VLSI Physical Design, Springer Verlag — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [VLSI-design-chap2]
---

- **Area balance** — Ensuring partitions have nearly equal total node or cell area within defined constraints.  
- **Base cell** — A cell with the highest gain that can be moved without violating balance criteria during partitioning.  
- **Cell** — A basic unit or node in a VLSI partitioning problem, often representing a logic block.  
- **Clustering** — Grouping tightly connected nodes together to simplify partitioning.  
- **Cut cost** — The total weight or number of edges/nets that cross between different partitions.  
- **Cut set** — The collection of edges or nets that connect nodes in different partitions.  
- **DRC (Design Rule Check)** — Verification process ensuring that a layout meets manufacturing rules.  
- **Edge** — A connection between two nodes in a graph representing nets or signals.  
- **Fiduccia-Mattheyses (FM) Algorithm** — A heuristic partitioning algorithm that moves single cells to reduce cut cost while maintaining partition balance.  
- **Gain (∆g)** — The change in cut cost resulting from moving or swapping nodes or cells during partitioning.  
- **Graph** — A representation of the netlist with nodes and edges depicting components and connections.  
- **Hyperedge (Net)** — A net connecting two or more nodes in a hypergraph, generalizing regular edges.  
- **Kernighan-Lin (KL) Algorithm** — A heuristic partitioning algorithm that swaps pairs of nodes to minimize cut cost and maintain equal partition sizes.  
- **Multilevel partitioning** — A framework that coarsens a graph by clustering nodes before partitioning and then refines it back.  
- **Netlist** — A list or description of circuit components (nodes) and their interconnections (nets).  
- **Node (Vertex)** — A basic graph element representing a circuit component or cell.  
- **Optimization goals** — Objectives to minimize cut cost, satisfy partition size constraints, and balance partitions.  
- **Partition** — A subset of nodes forming one block in the divided graph or netlist.  
- **Partitioning algorithm** — A method used to divide a netlist graph into balanced subgraphs with minimal interconnections.  
- **Ratio factor** — A measure of relative area balance between partitions used to maintain feasible partitioning.  
- **Retention force (TE)** — Number of uncut nets connected to a cell, representing the benefit of keeping it in its current partition.  
- **Swap gain** — Improvement in cut cost gained by swapping two nodes between partitions in the KL algorithm.  
- **System partitioning** — Dividing a circuit netlist or design into smaller parts for implementation, e.g., on multiple FPGAs.  
- **Timing closure** — The design process step that ensures all timing requirements are met after physical design partitioning.
