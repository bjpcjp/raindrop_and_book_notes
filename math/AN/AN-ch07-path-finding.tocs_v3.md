![AN-ch07-path-finding](AN-ch07-path-finding.best.png)

- **Overview**
  - Path finding solves problems without a clear algorithm by exploring potential states dynamically.
  - Two main approaches: game trees (two-player alternating moves) and search trees (single agent goal).
  - The complexity arises as trees are too large to compute entirely, requiring on-demand expansion.
  - For further reading, see Schaeffer (2007) on game complexity.

- **Game Trees**
  - Tic-tac-toe is a simple example with 765 unique board states and deterministic outcomes.
  - Game trees consist of alternating AND/OR nodes: OR nodes for player's moves, AND nodes for opponent's countermoves.
  - Larger games like checkers have roughly 5*10^20 states, making exhaustive search challenging.
  - Early AI approaches include Type A (fixed-depth evaluation) and Type B (adaptive evaluation).
  - Refer to Nilsson (1971) for tic-tac-toe evaluation functions and Schaeffer (2007) for checkers insights.

  - **Core Concepts**
    - Interfaces separate game logic from search algorithms via IGameState, IPlayer, IGameMove, and IGameScore abstractions.
    - Evaluation functions assign scores reflecting the strength of game states from a player's perspective.
    - The IEvaluation interface defines the bestMove method to find optimal moves assuming perfect opponent play.
    - Example evaluation uses measures of potential winning lines in tic-tac-toe.

- **Search Trees**
  - Search trees model sequential move sequences by a single agent, seeking a unique goal state.
  - The 8-puzzle is a canonical example with moves sliding tiles toward the goal configuration.
  - Search algorithms prevent revisiting states and manage open and closed sets for explored nodes.
  - INode and related interfaces encapsulate board states, move generation, evaluation scores, and equality checks.
  - ISearch interface abstracts the search method taking initial and goal states to produce solutions.
  - For more on search structures, consult Hartmann (1999) on project scheduling or Wichmann & Wuensche (2004) on pathfinding heuristics.

  - **Depth-First Search**
    - DEPTH-FIRST SEARCH explores moves as deeply as possible, using depth limits to manage infinite paths.
    - Stores open states in a stack and visited states in a hash set to prune revisited boards.
    - Can fail to find solutions if depth limit is too low, and may produce suboptimal paths.
    - Complexity depends on branching factor (b) and depth bound (d), typically O(b^d).
    - See Reinefeld (1993) for analysis on 8-puzzle branching factors.

  - **Breadth-First Search**
    - BREADTH-FIRST SEARCH explores all nodes reachable in k moves before those in k+1 moves.
    - Stores open states in a queue and visited in a hash set; guarantees shortest path if solution exists.
    - Requires more memory than depth-first search due to storing all frontier nodes.
    - Time and space complexity approximately O(b^d).
    - Classic algorithm detailed in Russell and Norvig’s *Artificial Intelligence: A Modern Approach* (2003).

  - **A*Search**
    - A*SEARCH combines path cost so far (g*) and heuristic estimate to goal (h*) into evaluation function f* = g* + h*.
    - Heuristics must be admissible (0 ≤ h*(n) ≤ true cost h(n)) to guarantee optimal solutions.
    - Uses priority queue (balanced tree) for efficiently selecting next node with lowest f*.
    - Dramatically reduces search space compared to blind methods when effective heuristics are applied.
    - Extensions include iterative deepening A* (IDA*) and hierarchical abstractions.
    - See Pearl (1984) for heuristics design and Korf (2000) on IDA* applications.

- **Game Tree Algorithms**
  - **Minimax**
    - Computes optimal move by recursively evaluating max and min values assuming perfect play from both players.
    - Evaluation function scores game states from the original player's perspective.
    - Computational complexity grows exponentially in branching factor and ply depth.
    - Requires static evaluation functions to guide search.
    - Refer to Shannon (1950) for early chess AI concepts.

  - **NegMax**
    - Refactors Minimax into a single recursive function maximizing the negative score of opponents.
    - Simplifies implementation by evaluating from the perspective of the current player at each node.
    - Equivalent results to Minimax but suitable for AlphaBeta pruning.
    - Utilizes symmetric score negations requiring careful minimum/maximum value management.

  - **AlphaBeta**
    - Prunes branches in the game tree that cannot affect the final decision, improving efficiency over Minimax.
    - Maintains alpha (best already explored option along path to root for maximizer) and beta (minimizer) bounds.
    - Pruing occurs when α ≥ β, stopping exploration of inferior moves.
    - Can halve the number of nodes explored compared to Minimax.
    - Fundamental optimization discussed in Knuth & Moore (1975).

- **Related Algorithms and Variations**
  - Iterative deepening combines depth-limited DFS with increasing bounds for trade-off between time and memory.
  - Transposition tables cache repeated game states to avoid redundant computations.
  - Hierarchical search (e.g., Hierarchical Path-Finding A*) reduces complexity by clustering state spaces.
  - Memory-bounded methods like SMA* manage search space size by discarding less promising nodes.
  - Bidirectional search explores from both initial and goal states to potentially halve search depth.
  - For practical heuristics and large-scale searches, see Barr and Feigenbaum (1981) and Reinefeld and Marsland (1994).
