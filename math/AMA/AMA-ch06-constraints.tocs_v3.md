![AMA-ch06-constraints](AMA-ch06-constraints.best.png)

- **6.1 Defining Constraint Satisfaction Problems**  
  - A CSP consists of variables, domains for each variable, and constraints specifying allowable value combinations.  
  - States correspond to assignments of values to variables; solutions are consistent, complete assignments satisfying all constraints.  
  - Map-coloring and job-shop scheduling are detailed example problems illustrating CSP formulation.  
  - Variations in CSPs include finite/infinite/continuous domains and different constraint types such as unary, binary, and global.  
  - For further study, see [Constraint Satisfaction Problems (Dechter, 2003)](https://www.elsevier.com/books/constraint-processing/dechter/978-1-55860-890-2).

- **6.1.1 Example problem: Map coloring**  
  - Variables correspond to Australian regions, each assigned a color from {red, green, blue}.  
  - Constraints require neighboring regions to have different colors, with a constraint graph representing variable interdependencies.  
  - Constraint propagation drastically reduces search space by eliminating inconsistent values early.  

- **6.1.2 Example problem: Job-shop scheduling**  
  - Tasks are variables with domains as possible start times; constraints enforce precedence and resource limitations.  
  - Disjunctive constraints represent mutually exclusive task sequences, e.g., axle installation order.  
  - Problem complexity grows with task count; continuous domain and specialized planning are referenced for advanced cases.  

- **6.1.3 Variations on the CSP formalism**  
  - CSP domains can be discrete finite/infinite or continuous, affecting possible constraint representations and solution methods.  
  - Constraints range from unary to global, with global constraints like Alldiﬀ requiring all involved variables have distinct values.  
  - Cryptarithmetic puzzles exemplify global and n-ary constraints and their representation via hypergraphs.  
  - Preference constraints and constraint optimization problems (COPs) incorporate solution preferences or costs.

- **6.2 Constraint Propagation: Inference in CSPs**  
  - Constraint propagation infers reductions of variable domains by enforcing local consistencies, intertwined or preceding search.  
  - Different levels of local consistency (node, arc, path, k-consistency) progressively reduce domains and prune search space.

- **6.2.1 Node consistency**  
  - Ensures every value in a variable’s domain satisfies its unary constraints.  
  - Node consistency is a preprocessing step that simplifies CSPs by eliminating unary constraints.  

- **6.2.2 Arc consistency**  
  - Every value of a variable must have a supporting consistent value in connected variables.  
  - AC-3 algorithm enforces arc consistency by iteratively revising domains until no inconsistencies remain or failure is detected.  
  - Generalized arc consistency extends to n-ary constraints.

- **6.2.3 Path consistency**  
  - Extends arc consistency by enforcing consistency over triples of variables, tightening binary constraints using implicit relations.  
  - Path consistency detects some inconsistencies arc consistency cannot, such as insufficient colors in map coloring.  

- **6.2.4 K-consistency**  
  - A CSP is k-consistent if any consistent assignment of k − 1 variables can be extended to a kth variable.  
  - Strongly n-consistent CSPs can be solved in polynomial time but require exponential time and space to enforce.  
  - In practice, checking up to 2- or 3-consistency is common.

- **6.2.5 Global constraints**  
  - Global constraints involve arbitrary numbers of variables and benefit from specialized inference algorithms.  
  - Alldiﬀ constraint pruning is based on counting variables vs. possible values and domain reductions.  
  - Resource constraints limit total resource usage, often enforced via bounds propagation, particularly for large integer domains.  

- **6.2.6 Sudoku example**  
  - Sudoku puzzles can be modeled as CSPs with 81 variables and 27 Alldiﬀ constraints.  
  - Arc consistency and path consistency can solve easy puzzles by domain reduction; harder puzzles require advanced inference.  
  - Complex human strategies are generalized CSP inference techniques, demonstrating CSP methods' wide applicability.

- **6.3 Backtracking Search for CSPs**  
  - Backtracking assigns values to one variable at a time, backtracking when no legal values remain.  
  - CSP commutativity allows restricting search to one variable per node, reducing complexity from n!·d^n leaves to d^n leaves.  
  - Improvements include heuristics for variable and value selection, inference interleaving, and intelligent backtracking.

- **6.3.1 Variable and value ordering**  
  - Minimum-remaining-values (MRV) heuristic selects the variable with the fewest legal values next, causing earlier failure detection.  
  - Degree heuristic selects the variable involved in the most constraints on unassigned variables, commonly as a tiebreaker.  
  - Least-constraining-value heuristic orders values to minimize constraints imposed on neighbors, aiding quicker search success.

- **6.3.2 Interleaving search and inference**  
  - Forward checking enforces arc consistency from assigned variables to prune domains of neighbors during search.  
  - Maintaining Arc Consistency (MAC) further propagates constraints recursively, detecting inconsistencies earlier than forward checking.  

- **6.3.3 Intelligent backtracking: Looking backward**  
  - Chronological backtracking blindly reverses the most recent assignment on failure.  
  - Backjumping uses conflict sets to backtrack directly to variables responsible for failure.  
  - Conflict-directed backjumping generalizes this by tracking failure reasons across variables, improving efficiency.  
  - Constraint learning stores no-goods (failed assignments) to avoid repeating failures, accelerating search.

- **6.4 Local Search for CSPs**  
  - Local search algorithms use complete assignments and iteratively reduce violated constraints.  
  - Min-conflicts heuristic selects variable assignments minimizing conflicts, often solving large CSPs efficiently.  
  - Techniques like plateau search, tabu search, simulated annealing, and constraint weighting enhance local search performance.  
  - Local search adapts well to online and dynamic problem scenarios, such as schedule repair.

- **6.5 The Structure of Problems**  
  - CSP complexity is strongly related to the constraint graph structure; independent subproblems simplify global solutions.  
  - Tree-structured CSPs can be solved in linear time using directed arc consistency and topological ordering.  
  - Cutset conditioning reduces graphs to tree-structured problems by removing variables forming a cycle cutset.  
  - Tree decompositions divide CSPs into connected subproblems solved locally then combined; efficiency depends on tree width.  
  - Value symmetry can inflate search space; symmetry-breaking constraints reduce redundant symmetric solutions.  
  - For in-depth treatment, see [Constraint Processing (Dechter, 2003)](https://www.elsevier.com/books/constraint-processing/dechter/978-1-55860-890-2).

- **6.6 Summary**  
  - CSPs represent states as variable/value assignments and search for consistent, complete assignments.  
  - Inference techniques like node, arc, path, and k-consistency reduce domains before or during search.  
  - Backtracking search can be enhanced with heuristics and inference; conflict-directed backjumping improves backtracking efficiency.  
  - Local search with min-conflicts is effective for many CSPs.  
  - Problem structure influences tractability; tree-structured CSPs and tree decompositions enable efficient solving.
