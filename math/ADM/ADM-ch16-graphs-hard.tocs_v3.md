[Representative image](ADM-ch16-graphs-hard.best.png)

- **Graph Problems: Hard Problems**
  - All problems in this section are NP-complete, except graph isomorphism whose complexity status is open.
  - NP-completeness reductions serve as practical evidence that no efficient algorithm exists.
  - Recommended approaches include combinatorial search, heuristics, approximation algorithms, and restricted instance algorithms.
  - Key references are Garey and Johnson for NP-completeness theory and Crescenzi and Kann for approximation algorithms.

- **Clique**
  - Identifies the largest complete subgraph in a graph where every vertex is connected to every other vertex in the subset.
  - Finding the maximum clique is NP-complete and hard to approximate within a factor of \(n^{1/2-\epsilon}\).
  - Heuristics include finding maximal cliques quickly and seeking large dense subgraphs instead.
  - Specialized algorithms exist for planar graphs which contain cliques of size at most four.
  - Refer to [Cliquer](http://users.tkk.fi/~pat/cliquer.html) for exact branch-and-bound implementations.

- **Independent Set**
  - Seeks the largest subset of vertices with no edges between them (i.e., no two vertices in the subset are adjacent).
  - Closely related to the clique problem via graph complement and to vertex coloring via color classes.
  - A greedy heuristic selects the lowest-degree vertex repeatedly to find a maximal independent set.
  - Maximum independent set can be found in linear time for trees.
  - See the clique-finding algorithms in Section 16.1 as dual solutions for independent sets.

- **Vertex Cover**
  - Finds the smallest subset of vertices such that every edge in the graph is incident to at least one selected vertex.
  - Problem reduced to set cover where each vertex corresponds to sets of edges.
  - Vertex cover and independent set are complementary problems; the minimum vertex cover corresponds to the complement of maximum independent set.
  - A greedy heuristic chooses highest-degree vertices iteratively; a known 2-approximation can be derived from maximal matchings.
  - See [COVER](http://www.nicta.com.au/people/richters/) for stochastic local search vertex cover solvers.

- **Traveling Salesman Problem**
  - Finds the minimum-cost cycle visiting each vertex exactly once in a weighted graph.
  - Problem variants based on triangle inequality satisfaction, graph symmetry, and feasibility of vertex revisits are discussed.
  - Recommended heuristics include minimum spanning tree based tours, incremental insertion, and k-opt local optimizations.
  - The Christofides heuristic guarantees a 3/2-approximation on Euclidean graphs.
  - Concorde solver is the state-of-the-art choice for exact solutions and can handle thousands of vertices.

- **Hamiltonian Cycle**
  - Determines if a graph has a cycle visiting each vertex exactly once, a special case of TSP with costs 1 or 2.
  - Longest path and cycle problems are also NP-complete but solvable in linear time on DAGs.
  - Dense graphs with minimum vertex degree at least \(n/2\) must contain Hamiltonian cycles.
  - Backtracking with pruning is the practical approach to solve the general problem.
  - Use TSP solvers like Concorde for Hamiltonian cycle via reductions.

- **Graph Partition**
  - Partitions vertices into roughly equal-sized subsets minimizing the edge-cut cost across subsets.
  - The minimum cut for connectivity can be found efficiently but may produce unbalanced partitions.
  - Balanced graph partitioning is NP-complete; heuristics include local optimization and spectral partitioning using graph Laplacian eigenvectors.
  - Well-known partitioning codes include Chaco, METIS, Scotch, and JOSTLE.
  - The planar separator theorem guarantees small separators of size \(O(\sqrt{n})\) for planar graphs.

- **Vertex Coloring**
  - Colors vertices with the minimum number of colors so that no two adjacent vertices share the same color.
  - Bipartite graphs are 2-colorable with a linear-time test; planar graphs can be colored with four colors (four-color theorem).
  - Incremental and heuristic methods such as DSATUR and color interchange improve coloring.
  - Exact computation is NP-complete; approximation guarantees are weak.
  - Refer to Culberson’s [Graph Coloring Page](http://web.cs.ualberta.ca/~joe/Coloring/) for implementations and resources.

- **Edge Coloring**
  - Assigns colors to edges so that adjacent edges receive different colors, minimizing the number of colors.
  - Vizing’s theorem bounds required colors to at most \(\Delta+1\), where \(\Delta\) is the maximum vertex degree.
  - Edge coloring is NP-complete to compute optimally but bipartite graphs are polynomial-time solvable.
  - Can be reduced to vertex coloring on line graphs but specialized algorithms for edge coloring are more efficient.
  - Implementations include Vizing’s constructive algorithm and GOBLIN’s branch-and-bound methods.

- **Graph Isomorphism**
  - Tests whether two graphs are identical via a vertex bijection preserving adjacency.
  - The problem is not known to be in P nor NP-complete; it is suspected to lie in-between.
  - Variants include subgraph isomorphism, induced subgraph isomorphism, labeled graphs, and tree isomorphism.
  - Practical solutions use vertex invariants like degree, shortest path multisets, and backtracking with pruning.
  - Use programs like [nauty](http://cs.anu.edu.au/~bdm/nauty/) and [VFLib](http://amalfi.dis.unina.it/graph/) for efficient isomorphism testing.

- **Steiner Tree**
  - Finds the minimum tree connecting a subset of vertices, possibly adding extra Steiner points to reduce total cost.
  - Applications include network design and VLSI routing; problem is NP-hard beyond trivial cases.
  - MST provides a provably good approximation; geometric Steiner points satisfy degree-3 with 120-degree angle constraints.
  - Specialized packages include GeoSteiner for geometric problems and FLUTE for rectilinear Steiner trees.
  - Phylogenetic tree inference tools like PHYLIP implement related Steiner-like algorithms.

- **Feedback Edge/Vertex Set**
  - Identifies the smallest set of edges or vertices to remove to eliminate cycles and produce an acyclic digraph.
  - Feedback sets simplify scheduling and ranking by breaking cyclic dependencies.
  - Finding minimum feedback sets is NP-complete; heuristics use vertex ordering and maximum acyclic subgraph approximations.
  - Minimum feedback edge sets in undirected graphs can be found via depth-first search back edges, but vertex set remains NP-complete.
  - GRASP heuristics and GOBLIN implementations provide practical approximate solutions.
