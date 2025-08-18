![AMA-ch03-search](AMA-ch03-search.best.png)

- **3 Solving Problems by Searching**
  - Problem-solving agents find action sequences to achieve goals when no single action suffices.
  - Goal-based agents simplify decision problems by limiting objectives and considering future actions.
  - Problem formulation involves defining initial state, actions, transition model, goal test, and path cost.
  - Search algorithms find solutions by exploring state-action sequences and vary primarily by node expansion order.
  - Further reading: [Artificial Intelligence: A Modern Approach, Chapter 3](https://aima.cs.berkeley.edu/)

- **3.1 Problem-Solving Agents**
  - Agents simplify complex performance measures by adopting explicit goals and formulating problems.
  - Environments assumed are observable, discrete, deterministic, and known for fixed action sequences as solutions.
  - Search solutions form a fixed sequence executed open-loop, ignoring percepts during execution.
  - Problem defined by initial state, actions, transition model (RESULT function), goal test, and path cost.
  - Further reading: [Russell and Norvig, Section 3.1](https://aima.cs.berkeley.edu/)

- **3.2 Example Problems**
  - Toy problems like vacuum world, 8-puzzle, and 8-queens illustrate problem-solving methods with precise state/action definitions.
  - Real-world examples include route-finding, touring problems, traveling salesperson, VLSI layout, robot navigation, and automatic assembly.
  - Real-world problems often require richer state representations and handle uncertainties elaborated in later chapters.
  - Further reading: [Nilsson, "Principles of Artificial Intelligence"](https://books.google.com/books)

- **3.3 Searching for Solutions**
  - Search trees represent expanding states via actions; frontier (open list) contains leaf nodes available for expansion.
  - Redundant and repeated states result in infinite loops or intractable search unless explored states are tracked.
  - Graph search algorithms maintain an explored set (closed list) to avoid redundancy and ensure correctness.
  - Nodes store state, parent node, action, and path cost, enabling solution path extraction.
  - Further reading: [Russell and Norvig, Section 3.3](https://aima.cs.berkeley.edu/)

- **3.4 Uninformed Search Strategies**
  - Uninformed (blind) search uses no problem-specific knowledge beyond problem definition.
  - Breadth-first search expands the shallowest nodes first, is complete and optimal for uniform step cost but has exponential time and space.
  - Uniform-cost search expands nodes in order of lowest path cost and is optimal with general step costs.
  - Depth-first search expands deepest nodes first, has linear space, but is neither complete nor optimal in general.
  - Depth-limited and iterative deepening search provide depth-limiting techniques to balance completeness and resource use.
  - Bidirectional search runs two simultaneous searches from start and goal, potentially halving search complexity.
  - Further reading: [Russell and Norvig, Section 3.4](https://aima.cs.berkeley.edu/)

- **3.5 Informed (Heuristic) Search Strategies**
  - Best-first search expands nodes based on evaluation function f(n), combining path cost g(n) and heuristic estimate h(n).
  - Greedy best-first search uses h(n) alone, aiming for speed but sacrificing completeness and optimality.
  - A* search uses f(n) = g(n) + h(n), guaranteeing completeness and optimality if h is admissible (never overestimates) and consistent (monotonic).
  - Memory-bounded variants like IDA*, RBFS, and SMA* reduce space requirements to linear while preserving completeness/optimality.
  - Meta-level learning adapts search strategies by learning from computational experience to minimize total cost.
  - Further reading: [Hart, Nilsson, and Raphael (1968) Original A* Paper](https://link.springer.com/article/10.1007/BF01694050)

- **3.6 Heuristic Functions**
  - Heuristics estimate cost to goal; good heuristics reduce effective branching factor and search effort.
  - For 8-puzzle, common heuristics include number of misplaced tiles (h1) and Manhattan distance sum (h2).
  - Better heuristics dominate weaker ones and combine heuristics by taking their maximum to preserve admissibility.
  - Admissible heuristics can be derived from relaxed problems by simplifying constraints.
  - Pattern databases store exact subproblem solutions to create highly accurate heuristics.
  - Learning heuristics from experience via features and regression can improve heuristic performance but may sacrifice admissibility.
  - Further reading: [Pearl, J. (1984) Heuristics: Intelligent Search Strategies for Computer Problem Solving](https://dl.acm.org/doi/10.5555/357901)

- **3.7 Summary**
  - Problem-solving involves formulating problems in formal terms and applying search algorithms to find goal-reaching action sequences.
  - Uninformed and informed search algorithms differ by the use of heuristic knowledge; tradeoffs exist among completeness, optimality, time, and space.
  - Selecting effective heuristics is crucial for efficient search.
  - Memory-bounded and learning-based methods address practical limitations of classical algorithms.
  - Further reading: [Artificial Intelligence: A Modern Approach, Summary and Exercises](https://aima.cs.berkeley.edu/)
