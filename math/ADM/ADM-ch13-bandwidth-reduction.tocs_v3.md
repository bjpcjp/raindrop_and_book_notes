[Representative image](ADM-ch13-bandwidth-reduction.best.png)

- **13.2 Bandwidth Reduction**
  - The section defines the bandwidth reduction problem as finding a vertex permutation minimizing the longest edge length in a linear ordering of a graph.
  - Bandwidth reduction is crucial for sparse matrix operations, enabling Gaussian elimination in O(nb²) time when bandwidth b is small.
  - The problem is NP-complete, including restricted cases such as trees with maximum vertex degree 3.
  - Popular heuristics like Cuthill-McKee and Gibbs-Poole-Stockmeyer use breadth-first search orders to approximate solutions efficiently.
  - Implementations and further empirical studies are available, including Del Corso and Manzini’s exact solutions [bandmin](http://www.mfn.unipmn.it/~manzini/bandmin) and Caprara and Salazar-González’s branch-and-bound code [Caprara-2](http://joc.pubs.informs.org/Supplements/Caprara-2/).
