[Representative image](ADM-ch06-graphs-weighted.best.png)

- **Weighted Graph Algorithms**
  - The chapter extends graph algorithms to weighted graphs where edges have numerical values such as cost or traversal time.
  - It uses an adjacency list structure enhanced to explicitly hold edge weights.
  - Weighted graph problems include minimum spanning trees, shortest paths, and maximum flows.
  - These problems have practical applications in fields like road networks and circuit testing.
  - Further reading: [The Algorithm Design Manual, Chapter 6](https://link.springer.com/book/10.1007/978-1-84800-070-4)

- **Minimum Spanning Trees**
  - A minimum spanning tree connects all vertices with the smallest possible sum of edge weights.
  - Two greedy algorithms, Prim’s and Kruskal’s, guarantee finding a minimum spanning tree.
  - Prim’s algorithm grows the spanning tree vertex-by-vertex by adding the smallest edge connecting the tree to a new vertex.
  - Kruskal’s algorithm sorts all edges and adds them in order while avoiding cycles using a union-find data structure.
  - Both algorithms rely strongly on data structures for efficient implementation.
  - Further reading: [Minimum Spanning Trees](https://en.wikipedia.org/wiki/Minimum_spanning_tree)

  - **Prim’s Algorithm**
    - Starts from an arbitrary vertex and adds the lowest-weight edge connecting the tree to a non-tree vertex in each iteration.
    - Correctness is proven by contradiction using path replacement arguments ensuring global optimality.
    - The naive implementation runs in O(mn), but using data structures this improves to O(n²); advanced heaps achieve O(m + n log n).
    - The parent array encodes the resulting minimum spanning tree structure.
    - Further reading: [Prim's Algorithm](https://en.wikipedia.org/wiki/Prim%27s_algorithm)

  - **Kruskal’s Algorithm**
    - Builds a spanning forest by adding edges in ascending order of weight, merging components without creating cycles.
    - Uses union-find data structure for efficient component checking and merging.
    - Runs in O(m log m) time due to edge sorting; union-find operations run in O(log n).
    - Proven correct by showing that any deviation can be corrected without increasing total weight.
    - Further reading: [Kruskal's Algorithm](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm)

  - **Union-Find Data Structure**
    - Maintains a partition of a universal set into disjoint subsets supporting union and find operations.
    - Uses parent pointers to represent subsets as trees; union by size keeps trees balanced.
    - Each find and union operation runs in O(log n) time; better with path compression.
    - Essential for efficient cycle detection in Kruskal’s algorithm.
    - Further reading: [Disjoint Set Union - Union-Find](https://en.wikipedia.org/wiki/Disjoint-set_data_structure)

  - **Variations on Minimum Spanning Trees**
    - Maximum spanning trees are found by negating edge weights and applying MST algorithms.
    - Minimum product spanning trees use logarithms of edge weights reducing the problem to sum minimization.
    - Minimum bottleneck spanning trees minimize the heaviest edge and coincide with MSTs.
    - Steiner trees and low-degree spanning trees are important variants not solvable by basic MST algorithms.
    - Further reading: [Steiner Tree Problem](https://en.wikipedia.org/wiki/Steiner_tree_problem)

- **War Story: Nothing but Nets**
  - The problem involved verifying connectivity on printed circuit boards by robot arms moving between contact points.
  - The input consisted only of points without explicit wiring; connectivity needed assurance that all points were connected.
  - Clustering big nets into smaller nets using minimum spanning trees allowed efficient testing by robotic arms.
  - Edge weights were modeled using special distance metrics (L∞ metric) to reflect robot movement costs including acceleration.
  - The approach yielded about 30% improvement in robot travel efficiency after preprocessing.
  - Further reading: [Clustering with MST](https://en.wikipedia.org/wiki/Single-linkage_clustering)

- **Shortest Paths**
  - Shortest paths seek minimal total edge weight between vertices, unlike BFS which works only on unweighted graphs.
  - The shortest path from source s to destination t may transit many intermediate vertices.
  - Two main algorithms are Dijkstra’s for single-source shortest path and Floyd’s for all-pairs shortest paths.
  - These techniques underpin applications in routing, networking, and navigation systems.
  - Further reading: [Shortest Path Problem](https://en.wikipedia.org/wiki/Shortest_path_problem)

  - **Dijkstra’s Algorithm**
    - Finds shortest path from a start vertex to all other vertices with non-negative edge weights.
    - It operates greedily, adding the unknown vertex closest to the start at each step.
    - Maintains distances and parent pointers to reconstruct shortest paths.
    - Runs in O(n²) time with simple implementation; priority queues improve efficiency.
    - Fails on graphs with negative edge weights.
    - Further reading: [Dijkstra’s Algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)

  - **All-Pairs Shortest Path (Floyd-Warshall Algorithm)**
    - Computes the shortest distances between every pair of vertices using dynamic programming.
    - Works on adjacency matrices initialized with edge weights or ∞ for absent edges.
    - Iteratively considers intermediate vertices to update the shortest paths matrix.
    - Runs in O(n³) time but is practically fast due to simple tight loops.
    - Can also compute transitive closure to identify reachable vertices.
    - Further reading: [Floyd–Warshall Algorithm](https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm)

  - **Transitive Closure**
    - Determines which vertices are reachable from any given vertex.
    - Can be computed via all-pairs shortest paths by checking path presence (finite distance).
    - Useful for reachability analysis in directed graphs.
    - Further reading: [Transitive Closure](https://en.wikipedia.org/wiki/Transitive_closure)

- **War Story: Dialing for Documents**
  - Text input on telephone keypads can be ambiguous as multiple letters share keys.
  - The system used a combination of trigrams and dictionaries to reconstruct probable English text from keypad input.
  - The decoding problem is modeled as finding shortest paths in a graph where vertices represent candidate words matching codes.
  - Edge weights reflect likelihoods from word frequencies and grammar, improving reconstruction accuracy.
  - This led to high accuracy text decoding licenses for commercial voice systems.
  - Further reading: [Viterbi Algorithm](https://en.wikipedia.org/wiki/Viterbi_algorithm)

- **Network Flows and Bipartite Matching**
  - Edge-weighted graphs represent networks where weights define pipe capacities.
  - The maximum flow problem asks for the greatest flow achievable from source s to sink t without exceeding capacities.
  - Bipartite matching finds the maximum set of edges pairing vertices from two disjoint sets without overlap.
  - Maximum matching in bipartite graphs can be solved as a special case of maximum flow.
  - Further reading: [Network Flow](https://en.wikipedia.org/wiki/Network_flow)

  - **Bipartite Matching**
    - Converts the bipartite graph into a flow network by adding source and sink nodes connected to partitions.
    - Edges and connecting vertices have capacity one, ensuring matchings correspond to unit flows.
    - This reduces maximum matching to maximum flow computation.
    - Further reading: [Maximum Bipartite Matching](https://en.wikipedia.org/wiki/Matching_(graph_theory))

  - **Computing Network Flows (Augmenting Paths)**
    - Uses repeated searches for augmenting paths in the residual graph to increase flow incrementally.
    - The residual graph includes forward edges with leftover capacity and backward edges for flow reversal.
    - Augmentation increases flow until no augmenting paths remain, at which point the flow is maximal.
    - Uses BFS to find shortest augmenting paths ensuring polynomial time (Edmonds-Karp algorithm).
    - Further reading: [Ford–Fulkerson Method](https://en.wikipedia.org/wiki/Ford%E2%80%93Fulkerson_algorithm)

- **Design Graphs, Not Algorithms**
  - Effective use of graph algorithms depends on clever problem modeling as graphs.
  - Complex problems can often be reduced to classical graph problems like MST, shortest paths, or network flows.
  - Examples include shortest path for video game routes, DNA fragment ordering as topological sort, rectangle bucketing as graph coloring, and filename shortening as bipartite matching.
  - This approach favors using established algorithms over inventing new ones.
  - Further reading: [Graph Modeling Techniques](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)#Applications)
