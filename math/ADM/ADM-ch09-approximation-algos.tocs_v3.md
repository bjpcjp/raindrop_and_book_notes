[Representative image](ADM-ch09-approximation-algos.best.png)

- **Intractable Problems and Approximation Algorithms**
  - Introduces the concept of proving no efficient algorithm exists for certain problems.
  - Emphasizes the practical benefit of NP-completeness in guiding algorithm design.
  - Discusses reductions to show equivalence or hardness between problems.
  - Introduces complexity theory and approximation algorithms.
  - Recommended reading: [The Algorithm Design Manual by Skiena](https://link.springer.com/book/10.1007/978-1-84800-070-4)

- **Problems and Reductions**
  - Defines key terms like algorithmic problems, instances, and reductions.
  - Explains reductions as translations preserving problem answers.
  - Uses allegory (kids fighting) to illustrate hardness via reductions.
  - Summarizes the implications of polynomial-time reductions on problem hardness.

  - **Key Idea**
    - Reductions map input instances from one problem to another preserving solution correctness.
    - A reduction enables solving one problem via a subroutine of another with additive runtime.
    - If the first problem has a known lower bound, the second problem inherits similar hardness.
    - Highlights reductions as tools to prove problem equivalence and relative difficulty.

  - **Decision Problems**
    - Defines decision problems as those with true/false answers.
    - Shows optimization problems can be reframed as decision problems (e.g., TSP decision).
    - Explains that decision problems simplify reductions and complexity analysis.
    - Shows how decision TSP allows binary search to find optimal values.

- **Reductions for Algorithms**
  - Describes using reductions to solve problem `a` via problem `b` with an efficient algorithm.
  - Running time is sum of reduction time plus solution time on problem `b`.
  - Supplies example reductions that lead to polynomial-time algorithms.

  - **Closest Pair**
    - Problem: find two numbers with smallest difference within a set.
    - Uses sorting to solve decision variant in O(n log n) time.
    - Notes that sorting lower bound does not prove closest pair is at least as hard.
    - Reduction links the complexity of sorting and closest pair tightly.

  - **Longest Increasing Subsequence**
    - LIS can be solved via edit distance reduction by sorting the sequence.
    - Edit distance parameters ensure only insertions and deletions, no substitutions allowed.
    - Reduction yields O(n²) algorithm, matching classical DP approach.
    - Points out an O(n log n) LIS algorithm exists outside this reduction.

  - **Least Common Multiple**
    - Defines LCM and GCD formally.
    - Uses Euclid’s Algorithm for efficient GCD calculation without factoring integers.
    - Shows LCM can be computed by multiplying inputs divided by GCD.
    - This reduction leverages known efficient GCD algorithm to compute LCM efficiently.

  - **Convex Hull**
    - Problem: find smallest convex polygon enclosing points.
    - Reduction maps numbers to points on parabola y = x², always on convex hull.
    - Reading convex hull polygon in order yields sorted sequence of original numbers.
    - Shows convex hull must take Ω(n log n) time due to sorting lower bound.
    - Any O(n log n) convex hull algorithm yields an O(n log n) sorting algorithm.

- **Elementary Hardness Reductions**
  - Presents reductions showing some problems have no known efficient solution.
  - Introduces Hamiltonian cycle and vertex cover as NP-complete problems.
  - Shows how hardness reductions link problems together, beginning from satisfiability.

  - **Hamiltonian Cycle**
    - Problem: decide if graph contains vertex-visit-each-once cycle.
    - Reduction from Hamiltonian cycle to TSP decision problem by assigning weights 1 or 2.
    - Tours of cost n correspond exactly to Hamiltonian cycles.
    - Demonstrates TSP hardness using Hamiltonian cycle hardness.
    - Translation is O(n²) and preserves problem answers exactly.

  - **Independent Set and Vertex Cover**
    - Defines vertex cover as subset of vertices covering all edges.
    - Defines independent set as subset of vertices with no edges between them.
    - Shows complement of vertex cover is an independent set in the same graph.
    - Reduction translates vertex cover instance to independent set instance and vice versa.
    - Proves both problems have equivalent hardness.

  - **Clique**
    - Clique: subset of vertices with edges between every pair.
    - Presents reduction from independent set by complementing edges of the graph.
    - Shows hardness of clique follows from independent set.
    - Chains hardness proofs from vertex cover to independent set to clique.

- **Satisfiability**
  - Defines SAT: Boolean variables and clauses, asks if a satisfying truth assignment exists.
  - Gives examples of satisfiable and unsatisfiable clause sets.
  - Establishes SAT as a certifiably hard problem (first NP-complete).
  - All known attempts to find polynomial-time SAT algorithms have failed.
  - Recommends Section 14.10 for more SAT details.

  - **3-Satisfiability**
    - Defines 3-SAT: each clause has exactly 3 literals.
    - Describes polynomial-time reduction from general SAT to 3-SAT.
    - Introduces auxiliary variables and clauses to convert clauses of various lengths to 3-literal form.
    - Demonstrates equivalence of original SAT instance and reduced 3-SAT instance.
    - Notes 2-SAT is solvable in linear time, distinguishing it from 3-SAT hardness.

- **Creative Reductions**
  - Explains use of NP-complete problems (preferably 3-SAT) as sources for proving hardness.
  - Highlights importance of direction of reductions: must reduce known hard problem to target.
  - Illustrates reduction from 3-SAT to integer programming.
  - Shows integer variables 0/1 correspond to Boolean variables and their complements.
  - Encodes clauses as linear inequalities ensuring at least one literal true per clause.
  - Also presents reduction from 3-SAT to vertex cover using gadgets for variables and clauses.
  - Graph constructed encodes satisfiability via minimal vertex cover existence.
  - Emphasizes chaining of hardness proofs to build library of NP-complete problems.

- **The Art of Proving Hardness**
  - Lists practical advice for proving NP-completeness using reductions.
  - Suggests using restricted versions of hard problems to simplify reductions.
  - Advises making target problem as general as needed to ease hardness proofs.
  - Recommends limiting source problems to 3-SAT, integer partition, vertex cover, and Hamiltonian path.
  - Encourages amplifying penalties in gadgets to enforce correct reductions.
  - Advises strategic thinking and modular gadget construction.
  - Suggests alternating search for algorithms and reductions if stuck.
  - References Garey and Johnson’s book for known NP-complete problems.

- **War Story: Hard Against the Clock**
  - Describes on-the-fly NP-completeness proof for "Inequivalence of Programs with Assignments."
  - Identifies 3-SAT as source problem, maps SAT clauses to program evaluation.
  - Constructs one program encoding clause satisfaction, second trivial program.
  - Shows inequivalence of programs corresponds to satisfiability of clauses.
  - Illustrates interactive reduction construction under time constraints.

- **War Story: And Then I Failed**
  - Narrates difficulty in proving hardness of uniconnected subgraph problem.
  - Discusses challenges in directing undirected graph edges for reduction.
  - Eventually finds solution by splitting edges into gadgets and adding sink node.
  - Demonstrates connection between vertex cover and uniconnected subgraph.
  - Highlights NP-completeness reductions can be simple with right perspective.

- **P vs. NP**
  - Defines P as class of problems solvable in polynomial time.
  - Defines NP as class of problems whose solutions can be verified in polynomial time.
  - Explains the fundamental open question: is P = NP or P ≠ NP?
  - Details verification versus discovery distinction.
  - Notes SAT and other NP-complete problems are in NP but not known to be in P.
  - Explains Cook’s theorem establishes SAT as hardest NP problem.
  - Clarifies difference between NP-hard and NP-complete problems.
  - Notes some problems (e.g., chess) are NP-hard but not in NP.
  - Recommends reading [P vs NP Wikipedia](https://en.wikipedia.org/wiki/P_versus_NP_problem).

- **Dealing with NP-complete Problems**
  - Suggests three approaches for NP-complete problems: fast average-case, heuristics, approximation algorithms.
  - Emphasizes approximation algorithms provide guaranteed closeness to optimal solution.
  - Notes heuristics can sometimes outperform approximations in practice.
  - Suggests combining heuristics and approximation for better results.
  - Provides examples:

  - **Approximating Vertex Cover**
    - Simple algorithm selects both endpoints of arbitrary edges until all edges covered.
    - Guarantees cover at most twice the optimal size.
    - Explains why greedy selection by highest-degree vertex can fail badly.
    - Warns against unnecessary heuristic complications.
    - Recommends post-processing to improve practical performance.

  - **The Euclidean Traveling Salesman**
    - Edge weights satisfy triangle inequality in Euclidean metrics.
    - MST weight is a lower bound on optimal TSP tour.
    - Uses depth-first traversal of MST to form a tour visiting vertices multiple times.
    - Applies shortcuts removing repeated vertices, preserving or shortening tour.
    - Guarantees an approximation within twice the optimal tour length.
    - Notes better approximations exist in literature for Euclidean TSP.

  - **Maximum Acyclic Subgraph**
    - Goal: find largest subset of edges forming a directed acyclic graph.
    - Simple heuristic: order vertices arbitrarily and keep edges consistent with the order.
    - Larger edge set forms acyclic subgraph with at least half the total edges.
    - Suggests randomization and swaps to improve heuristic performance.

  - **Set Cover**
    - Problem: find smallest number of subsets covering all elements.
    - Greedy heuristic: pick subset covering most uncovered elements per step.
    - Defines milestones based on uncovered elements decreasing by powers of two.
    - Proves greedy solution size is at most O(log n) times optimal.
    - Notes existence of worst-case instances demonstrating logarithmic approximation limit.

- **Chapter Notes**
  - NP-completeness introduced by Cook [Coo71] with satisfiability as the first NP-complete problem.
  - Karp [Kar72] provided pioneering reductions from SAT to various problems.
  - Garey and Johnson’s book remains essential for NP-completeness theory and problem catalog.
  - Notes that some problems like graph isomorphism and integer factorization are neither proven in P nor NP-complete.
  - Uniconnected subgraph hardness was established by Mahajan (1976).

- **Exercises**
  - Contains varied exercises covering reductions, NP-completeness proofs, approximation algorithms, and special cases.
  - Includes SAT and 3-SAT transformations, reductions to vertex cover, set cover, knapsack, and Hamiltonian path.
  - Provides algorithm design challenges and proofs of problem membership in NP.
  - Offers practice problems in approximation heuristics and performance analysis.
  - Many programming challenges related to computational geometry and other topics are listed for further practice.
