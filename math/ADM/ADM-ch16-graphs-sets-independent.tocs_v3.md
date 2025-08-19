![ADM-ch16-graphs-sets-independent](ADM-ch16-graphs-sets-independent.best.png)

- **16.2 Independent Set**  
  - The problem asks for the largest subset of vertices with no two adjacent in graph G = (V, E).  
  - Independent sets model facility dispersion and coding theory problems by avoiding conflicts.  
  - The maximum independent set in G corresponds exactly to the maximum clique in the complement graph G̅.  
  - Vertex coloring partitions vertices into independent sets, linking independent set problems to coloring heuristics.  
  - The simplest heuristic adds lowest-degree vertices and removes their neighbors to find a maximal independent set.  
  - Maximum independent sets in trees can be found in linear time using leaf-stripping and deletion of adjacent nodes.  
  - Efficient algorithms for maximum clique can be applied to find maximum independent sets via graph complementation.  
  - Additional algorithms include branch-and-bound (GOBLIN) and GRASP heuristics for approximate solutions.  
  - The problem remains NP-complete even for planar cubic graphs but is solvable efficiently for bipartite graphs.  
  - See [GOBLIN Graph Library](http://www.math.uni-augsburg.de/~fremuth/goblin.html) and [ACM Algorithm 787](http://www.research.att.com/~mgcr/src/) for implementations.
