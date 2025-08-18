[Representative image](ADM-ch05-graph-traversal.best.png)

- **Graph Traversal Overview**
  - Graphs model diverse systems including transportation, social networks, and circuits.
  - Graph G = (V, E) consists of vertices V and edges E representing relationships.
  - Correct problem modeling is essential to leverage known graph algorithms.
  - Advanced graph algorithms and applications are covered in later chapters.
  - Further reading: [The Algorithm Design Manual, Chapter 5](https://doi.org/10.1007/978-1-84800-070-4)

- **Flavors of Graphs**
  - Graphs vary by directionality (undirected vs directed), weighting (weighted vs unweighted), and structural simplicity (simple vs non-simple).
  - Sparsity and cyclicity influence algorithm selection and performance.
  - Graphs can be embedded or topological, explicit or implicit, and labeled or unlabeled.
  - The friendship graph exemplifies these flavors and their real-world implications.
  - Further reading: [Graph Theory and Social Networks](https://doi.org/10.1007/978-1-84800-070-4)

- **Data Structures for Graphs**
  - Two primary graph representations: adjacency matrices and adjacency lists.
  - Adjacency matrices allow O(1) edge lookup but use O(n²) space, inefficient for sparse graphs.
  - Adjacency lists use O(n + m) space and allow efficient graph traversal for sparse graphs.
  - Selecting adjacency lists is recommended for most applications due to space and time efficiencies.
  - Further reading: [Graph Representations](https://doi.org/10.1007/978-1-84800-070-4)

- **War Story: I was a Victim of Moore’s Law**
  - Combinatorica initially used adjacency matrices due to performance trade-offs in Mathematica.
  - Hardware improvements over 15 years increased calculation speeds 200x.
  - Switching to adjacency lists enabled scaling to graphs 50-100 times larger.
  - Asymptotic efficiency becomes critical despite short-term hardware gains.
  - Further reading: [Combinatorica Library](https://www.combinatorica.com)

- **War Story: Getting the Graph**
  - Inefficient dual graph construction resulted from naive triangle adjacency comparisons (O(n²) time).
  - Using vertex-based adjacency lists for triangles reduced construction to near linear time.
  - Proper data structures and algorithms avoid bottlenecks in large-scale graph processing.
  - Emphasizes the importance of efficient preprocessing in algorithm pipelines.
  - Further reading: [Dual Graphs in Computational Geometry](https://doi.org/10.1007/978-1-84800-070-4)

- **Traversing a Graph**
  - Fundamental graph problem: systematic visitation of all vertices and edges.
  - Vertices have three states during traversal: undiscovered, discovered, processed.
  - Uses marking to avoid redundant visits and ensure completeness.
  - Traversal structures determine order and effectiveness.
  - Further reading: [Fundamentals of Graph Traversal](https://doi.org/10.1007/978-1-84800-070-4)

- **Breadth-First Search**
  - Explores graph level-by-level using a FIFO queue.
  - Produces a shortest path tree from the start vertex.
  - Classifies edges based on their position relative to BFS levels.
  - BFS runs in O(n + m) time and is optimal for unweighted shortest paths.
  - Further reading: [Breadth-First Search](https://doi.org/10.1007/978-1-84800-070-4)

- **Applications of Breadth-First Search**
  - Connected Components: Identifies maximal vertex sets with paths between all pairs.
  - Two-Coloring Graphs: Assigns alternating colors in bipartite graphs using BFS.
  - BFS-based algorithms guarantee linear-time performance on sparse graphs.
  - Applied in social network connectivity and scheduling.
  - Further reading: [Graph Coloring Algorithms](https://doi.org/10.1007/978-1-84800-070-4)

- **Depth-First Search**
  - Explores graph by advancing deeply along paths using a LIFO stack (recursion).
  - Records entry and exit times per vertex to capture traversal structure.
  - Classifies edges into tree and back edges (undirected) or more types (directed).
  - DFS facilitates recursive exploration and backtracking.
  - Further reading: [Depth-First Search](https://doi.org/10.1007/978-1-84800-070-4)

- **Applications of Depth-First Search**
  - Cycle Detection: Uses back edges to identify cycles efficiently.
  - Articulation Vertices: Identifies vertices whose removal increases graph disconnectedness using DFS timestamps and reachable ancestors.
  - Bridges (edge biconnectivity): DFS detects edges whose removal disconnects the graph.
  - DFS organizes graph structure to support many fundamental algorithms.
  - Further reading: [Graph Connectivity](https://doi.org/10.1007/978-1-84800-070-4)

- **Depth-First Search on Directed Graphs**
  - Edge classification extends to tree, back, forward, and cross edges.
  - Correct edge classification relies on discovery states and timestamps.
  - DFS sequences each vertex to process all connected components.
  - Enables diverse directed graph algorithms.
  - Further reading: [DFS Edge Classification](https://doi.org/10.1007/978-1-84800-070-4)

- **Topological Sorting**
  - Ordering of DAG vertices such that all directed edges go from earlier to later vertices.
  - Achieved by DFS-based reverse postorder labeling if no back edges are found.
  - Essential for scheduling and task precedence problems.
  - Ensures correctness by detecting cycles via back edges.
  - Further reading: [Topological Sort Algorithms](https://doi.org/10.1007/978-1-84800-070-4)

- **Strongly Connected Components**
  - Partition directed graphs into maximal vertex sets where each vertex is reachable from every other.
  - Uses DFS with low-link values and stack to identify SCCs in O(n + m) time.
  - Considers back and cross edges to update component membership.
  - Algorithm contracts cycles into single vertices iteratively to find all SCCs.
  - Further reading: [Strongly Connected Components Algorithms](https://doi.org/10.1007/978-1-84800-070-4)

- **Chapter Notes**
  - Materials are based on expanded versions from foundational texts such as [SR03] and [Ski90].
  - Combinatorica serves as a case study for practical graph algorithm libraries.
  - Social network analysis is referenced as a rich application domain.
  - Further reading: [The Algorithm Design Manual](https://doi.org/10.1007/978-1-84800-070-4)
