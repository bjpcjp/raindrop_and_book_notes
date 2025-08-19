![ADM-ch15-graphs-chinese-postman](ADM-ch15-graphs-chinese-postman.best.png)

- **15.7 Eulerian Cycle/Chinese Postman**
  - The shortest tour visiting each edge at least once solves applications like garbage truck routes and postmen delivery.
  - An Eulerian cycle exists if the graph is connected and all vertex degrees are even; an Eulerian path requires exactly two vertices of odd degree.
  - Directed graphs require strong connectivity and balanced in-degree and out-degree conditions for Eulerian cycles and paths.
  - Constructing Eulerian cycles involves partitioning edges into edge-disjoint cycles and splicing them together at common vertices.
  - The Chinese postman problem finds a minimum-length cycle covering all edges by adding edges to make the graph Eulerian.
  - Finding the minimum cost addition corresponds to a minimum-weight perfect matching on a graph formed by the odd-degree vertices.
  - Bipartite matching algorithms suffice for directed graphs due to the structure of the degree-imbalanced vertices.
  - Eulerian cycles can be constructed in linear time once the graph is Eulerian.
  - Implementations exist in libraries such as GOBLIN, LEDA, and Combinatorica; a Java implementation of directed Chinese postman is available from Thimbleby.
  - The problem originated with Euler’s solution to the seven bridges of Königsberg in 1736.
  - Alternative Eulerian cycle algorithms include Fleury’s algorithm, which avoids bridge edges when possible.
  - The Euler tour technique is widely used in parallel graph algorithms.
  - The Chinese postman algorithm using bipartite matching was developed by Edmonds and Johnson.
  - Mixed graphs containing both directed and undirected edges render the problem NP-complete.
  - De Bruijn sequences, used for shortest sequences covering all strings of a certain length, can be constructed via Eulerian cycles on a constructed de Bruijn graph.
  - Further reading: [Chinese Postman Problem](http://www.cs.swan.ac.uk/~csharold/cpp/index.html), [GOBLIN Library](http://www.math.uni-augsburg.de/~fremuth/goblin.html), [Euler's original paper translation](https://people.math.gatech.edu/~ecroot/math/euler.pdf).
