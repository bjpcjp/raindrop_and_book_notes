![ADM-ch06-graphs-weighted](ADM-ch06-graphs-weighted.best.png)

- **Weighted Graph Algorithms**
  - The chapter addresses computations on weighted graphs, where edges carry numerical weights.
  - Weighted graphs allow modeling real-world networks like road systems with costs or distances.
  - Data structures like adjacency lists include explicit edge weights for such graphs.
  - Topics include minimum spanning trees, shortest paths, and maximum flows.
  - For broader graph algorithms, see [Skiena's Algorithm Design Manual](https://example.org).

- **Minimum Spanning Trees**
  - A spanning tree connects all vertices with no cycles and minimal edge weight sum.
  - Applications include connecting physical points with minimum wiring or piping.
  - Multiple minimum spanning trees can exist, especially if edges share weights.
  - Greedy algorithms, such as Prim’s and Kruskal’s, optimally find minimum spanning trees.
  - Further details in [Minimum Spanning Tree - Wikipedia](https://en.wikipedia.org/wiki/Minimum_spanning_tree).

  - **Prim’s Algorithm**
    - Starts from a vertex and grows the minimum spanning tree by adding the smallest connecting edge to new vertices.
    - Decisions are made greedily by selecting the minimum weight edge linking tree and non-tree vertices.
    - The algorithm is proven optimal by showing any choice aligns with a minimum spanning tree.
    - Basic implementation runs in O(n²); improvements with data structures can reduce this to O(m + n log n).
    - For advanced techniques see [Prim's Algorithm - GeeksforGeeks](https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/).

  - **Kruskal’s Algorithm**
    - Builds the minimum spanning tree by repeatedly adding the smallest edge that does not form a cycle.
    - Uses union-find data structure to efficiently detect cycles and manage components.
    - Sorting edges is O(m log m), and optimal union-find operations run in nearly O(1) amortized time.
    - Proves correctness by showing any deviation would contradict the minimality of the tree.
    - Recommended resource: [Kruskal's Algorithm - Tutorialspoint](https://www.tutorialspoint.com/kruskals-algorithm).

  - **Union-Find Data Structure**
    - Represents partitions of a set as rooted trees supporting find and union operations efficiently.
    - Uses union-by-size to keep trees shallow, guaranteeing O(log n) complexity for operations.
    - Essential for cycle detection in Kruskal’s algorithm and maintaining connected components.
    - Concept overview at [Union-Find Data Structure - Topcoder](https://www.topcoder.com/thrive/articles/Disjoint%20Set%20Union%20or%20Union-Find).

  - **Variations on Minimum Spanning Trees**
    - Maximum spanning trees obtained by negating edge weights and applying minimum spanning tree algorithms.
    - Minimum product spanning trees solved via logarithmic transformation of weights.
    - Minimum bottleneck spanning trees minimize the maximum edge weight; all MSTs satisfy this.
    - Steiner trees and low-degree spanning trees are complex variants not solvable by standard MST methods.
    - Additional applications in [Steiner Tree Problem - SIAM](https://epubs.siam.org/doi/abs/10.1137/1.9781611974980.ch3).

- **War Story: Nothing but Nets**
  - Describes connecting points (nets) on circuit boards using minimum spanning trees for efficient robot testing.
  - Robots test connectivity by probing points, needing optimized routes to reduce movement.
  - Clustering of nets via breaking long MST edges helps balance workload and reduce travel.
  - Distance weights tailored to robot movement capabilities (L∞ metric and acceleration).
  - Demonstrates modeling real problems as graph problems for practical algorithmic solutions.

- **Shortest Paths**
  - Shortest paths are sequences of edges connecting vertices with minimal total weight.
  - Breadth-first search works for unweighted graphs; weighted graphs require specialized methods.
  - Shortest paths may involve many edges and complex routes, differing from minimum-edge count paths.
  - Two main algorithms discussed: Dijkstra’s single-source and Floyd’s all-pairs shortest paths.
  - For in-depth study, refer to [Shortest Path Problem - MIT OpenCourseWare](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/resources/lecture-12-shortest-paths-dijkstras-algorithm/).

  - **Dijkstra’s Algorithm**
    - Finds shortest paths from a start vertex to all others in weighted graphs without negative edges.
    - Greedily selects the vertex with the smallest provisional distance until all reachable vertices are processed.
    - Similar to Prim’s algorithm structurally, differing primarily in distance updates.
    - Runs in O(n²) with basic data structures; improved to O(m + n log n) with priority queues.
    - Does not work correctly with negative edge weights.
    - Source: [Dijkstra’s Algorithm - Wikipedia](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm).

  - **All-Pairs Shortest Path (Floyd-Warshall Algorithm)**
    - Computes shortest distances between all vertex pairs using dynamic programming.
    - Uses adjacency matrices with non-edges set to MAXINT for effective computation.
    - Runs in O(n³) time and is efficient in practice despite similar asymptotics to running Dijkstra’s n times.
    - Can compute transitive closure indicating reachability in directed graphs.
    - Details at [Floyd-Warshall Algorithm - GeeksforGeeks](https://www.geeksforgeeks.org/floyd-warshall-algorithm-dp-16/).

- **War Story: Dialing for Documents**
  - Developed a telephone keypad text reconstruction system using shortest path graph modeling.
  - Modeled ambiguous keypad inputs and dictionary words as graph vertices with weighted edges.
  - Used dynamic programming (Viterbi algorithm) to find minimum-cost paths representing probable sentences.
  - Achieved high accuracy by integrating word frequencies, grammatical constraints, and trigram statistics.
  - Demonstrates natural graph formulations for complex pattern recognition tasks.

- **Network Flows and Bipartite Matching**
  - Edge-weighted graphs model flow networks where edge weights represent pipe capacities.
  - The maximum s–t flow problem seeks the greatest feasible flow respecting capacity constraints.
  - Bipartite matching finds maximum independent edge sets in bipartite graphs; reducible to max-flow problems.
  - Residual flow graphs track current flow states and allow finding augmenting paths to increase total flow.
  - Ford-Fulkerson method and Edmonds-Karp implementation use BFS for shortest augmenting paths with O(n³) bound.
  - Comprehensive resource: [Introduction to Network Flows - Stanford CS168](https://web.stanford.edu/class/cs168/l/l3.pdf).

  - **Bipartite Matching**
    - Construct source and sink with capacity-1 edges to bipartite partitions; maximum flow corresponds to max matching.
    - No vertex can be part of more than one matched edge due to capacity constraints.
    - Widely applicable in job assignments, resource allocation, and pairing problems.
    - See [Maximum Bipartite Matching - HackerRank Tutorial](https://www.hackerrank.com/topics/maximum-bipartite-matching).

  - **Computing Network Flows**
    - Augmenting paths are found iteratively, transferring flow until no more augmentations exist.
    - Forward and backward edges updated to represent residual capacities.
    - Valid edges in BFS are those with positive residual capacity, ensuring feasible flow increments.
    - Minimum s–t cut capacity equals the maximum flow value, linking flows and cuts.
    - Ford-Fulkerson algorithm detailed at [Network Flow Algorithms - CP-Algorithms](https://cp-algorithms.com/graph/edmonds_karp.html).

- **Design Graphs, Not Algorithms**
  - Emphasizes modeling real problems as graphs to use existing standard graph algorithms.
  - Examples include: maximum spanning trees via negated weights, bipartite matching via network flows.
  - Encourages constructing novel graph representations to leverage classical algorithmic solutions.
  - Problem examples cover shortest paths for navigation, topological sorting for fragment ordering, graph coloring for rectangle bucketing, and matching for file name collisions.
  - For graph modeling techniques, consult [Graph Theory Applications - [MathWorld](https://mathworld.wolfram.com/topics/GraphTheoryApplications.html)].
