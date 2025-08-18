[Representative image](ADM-ch16-graphs-vertex-cover.best.png)

- **16.3 Vertex Cover**
  - **Problem Description**
    - Finds the smallest vertex subset S such that each edge in E is incident on at least one vertex in S.  
    - Vertex cover problems are a special case of the general set cover problem, where edges correspond to elements and vertices correspond to subsets.  
    - Vertex cover instances are simpler than general set cover because each edge belongs to exactly two subsets.  
    - The problem is NP-complete and closely related to the independent set problem.  
    - See [Set Cover](https://en.wikipedia.org/wiki/Set_cover_problem) for broader context.

  - **Heuristics and Approximation**
    - A simple heuristic repeatedly selects the highest-degree vertex, adds it to the cover, removes its edges, and repeats.  
    - The simple heuristic can produce covers lg(n) times larger than optimal in certain cases.  
    - A 2-approximation algorithm uses a maximal matching M, taking both vertices of each matched edge to form a cover.  
    - This maximal matching approach guarantees a cover size at most twice the minimum.  
    - Practical improvements include selecting matching edges that cover many others and removing redundant vertices.  
    - Relevant approximation discussions can be found in [CLRS](https://mitpress.mit.edu/books/introduction-algorithms), [Hoc96], and [Vaz04].

  - **Related Cover Problems**
    - **Dominating Set**
      - Seeks a minimal vertex set D such that every vertex outside D is adjacent to at least one vertex in D.  
      - Every vertex cover is a dominating set yet dominating sets can be substantially smaller.  
      - Appears in communication and network hub applications.  
      - The dominating set problem reduces to set cover, with a greedy heuristic achieving a Θ(lg n) approximation.  
      - See [Dominating Set](https://en.wikipedia.org/wiki/Dominating_set) for details.

    - **Edge Cover**
      - Seeks the smallest edge set covering all vertices.  
      - Can be solved efficiently by finding a maximum matching and adding arbitrary edges for unmatched vertices.  
      - Differentiates from vertex cover by covering vertices directly via edges.  
      - See Section 15.6 (page 498) for maximum cardinality matchings.

  - **Implementations and References**
    - Maximum clique solvers can be adapted for vertex cover by complementing the graph.  
    - COVER [RHG07] is a stochastic local search vertex cover solver available at http://www.nicta.com.au/people/richters/.  
    - JGraphT Java library provides greedy and 2-approximate vertex cover heuristics accessible at http://jgrapht.sourceforge.net/.  
    - Karp [Kar72] proved vertex cover is NP-complete; 2-approximation algorithms discussed in [CLRS01, Hoc96, Pas97, Vaz04].  
    - The hardness of beating 2-approximation is an open problem, with a known lower bound of 1.1666 from [Has97].  
    - Additional heuristics and experimental studies are discussed in [GMPV06, GW97, RHG07].

  - **Notes and Related Problems**
    - Vertex cover and independent set are complementary: minimizing the cover is equivalent to maximizing the independent set.  
    - The greedy heuristic's lg(n) lower bound example originates from [Joh74] and explained in [PS98].  
    - Dominating set approximation cannot outperform Ω(lg n), connected to set cover intractability [ACG+03].  
    - Important references include the monograph by Haynes et al. [HHS98] and heuristics for connected dominating sets [GK98].  
    - Related problems include independent set (page 528) and set cover (page 621).
