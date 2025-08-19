![ADM-ch16-graphs-edge-coloring](ADM-ch16-graphs-edge-coloring.best.png)

- **16.8 Edge Coloring**  
  - The problem asks for the smallest set of colors needed to color edges so that no two edges sharing a vertex have the same color.  
  - Edge coloring is applied in scheduling, such as organizing two-person interviews or NFL game weeks, where colors represent distinct time slots.  
  - Vizing’s theorem states any graph with maximum degree Δ can be edge-colored using at most Δ + 1 colors; at least Δ colors are always necessary.  
  - Vizing’s theorem provides a constructive O(nmΔ) algorithm, while deciding if Δ colors suffice is NP-complete.  
  - Edge coloring problems can be transformed into vertex coloring problems on the line graph of the original graph, but this is less efficient than direct methods.  
  - Implementations include Yan Dong’s C++ code and the GOBLIN branch-and-bound algorithm.  
  - For further reading, see [Vizing’s theorem implementation and discussion](http://www.cs.sunysb.edu/~algorith) and [GOBLIN library](http://www.math.uni-augsburg.de/~fremuth/goblin.html).
