- **9 Online Planning**
  - Discusses online planning methods that compute actions by reasoning about reachable states.
  - Highlights that online planning can reduce storage and computation compared to offline methods.
  - Introduces pruning, sampling, and deeper planning along promising trajectories as efficiency strategies.

- **9.1 Receding Horizon Planning**
  - Plans from the current state to a fixed horizon depth d and replans after executing each action.
  - Deeper planning increases computation but can be necessary to ensure safety or goal achievement.
  - Example 9.1 illustrates the tradeoff between planning depth and effective collision avoidance.
  - [Model Predictive Control](https://en.wikipedia.org/wiki/Model_predictive_control) is related.

- **9.2 Lookahead with Rollouts**
  - Acts greedily with respect to estimated values computed via simulations (rollouts) of a policy.
  - Rollout policies are stochastic and use a generative model for successor states.
  - Running multiple rollouts improves value estimates at computational cost O(m × |A| × d).
  - Relates to policy improvement in policy iteration algorithms.

- **9.3 Forward Search**
  - Expands all possible state-action transitions up to depth d, forming an exponential search tree.
  - Computational complexity is O((|S| × |A|)^d).
  - Uses recursive depth-first search with value function estimates at depth d for terminal nodes.
  - Hybrid planning combines online forward search with offline value function approximations.

- **9.4 Branch and Bound**
  - Prunes subtrees in forward search using upper and lower bounds on value functions.
  - Pruning occurs when upper bound of an action is lower than lower bound of a better action.
  - Worst-case complexity equals forward search but typically more efficient depending on bound tightness.
  - Actions are explored in descending order by upper bound to maximize pruning.
  - Example 9.2 shows significant speedup in mountain car problem using branch and bound.

- **9.5 Sparse Sampling**
  - Limits branching by sampling a fixed number of next states m per action instead of all states.
  - Computational complexity is O((m × |A|)^d), removing dependence on |S|.
  - Sampling approximates forward search and can perform well in practice.
  - Figure 9.3 visually compares sparse sampling to forward search.

- **9.6 Monte Carlo Tree Search**
  - Runs m simulations to update estimates of action values Q(s,a) and visitation counts N(s,a).
  - Action selection combines exploitation (Q values) with exploration bonuses via upper confidence bounds.
  - Handles large state spaces by selectively exploring promising actions balancing exploration-exploitation.
  - Supports initializing value estimates from rollout policies or expert priors.
  - Progressive widening extension limits considered actions/states as a function of visitation counts.
  - Examples 9.3–9.8 illustrate MCTS applied to the 2048 game.
  - See [Monte Carlo Tree Search Methods](https://doi.org/10.1109/TCIAIG.2012.2186810) for details.

- **9.7 Heuristic Search**
  - Runs m simulations from current state following a greedy policy with respect to an initial heuristic upper bound U.
  - Updates value estimates along simulations using lookahead.
  - Guaranteed to converge to optimal value if heuristic is admissible (upper bound).
  - Efficiency depends on tightness of heuristic.
  - Algorithm complexity is O(m × d × |S| × |A|).
  - See [Planning with Markov Decision Processes: An AI Perspective](https://doi.org/10.2200/S00493ED1V01Y201210AIM017) for more on heuristic search.

- **9.8 Labeled Heuristic Search**
  - Extends heuristic search by labeling states as solved when utility residuals fall below threshold δ.
  - Simulations stop early on reaching solved states, focusing computation on unsolved important states.
  - Labeling uses the greedy envelope of states reachable under the current greedy policy.
  - Figure 9.6 illustrates greedy envelopes; Figures 9.7 and 9.8 show labeling process and search progression.
  - Improves convergence speed compared to basic heuristic search.

- **9.9 Open-Loop Planning**
  - Plans a sequence of actions a1:d without conditioning on future state observations.
  - Reduces computational complexity; known as model predictive control.
  - Optimization problem seeks action sequence maximizing expected return U(a1:d).
  - Example 9.9 shows suboptimality of open-loop planning in stochastic environments.
  - See [Predictive Control for Linear and Hybrid Systems](https://www.cambridge.org/core/books/predictive-control-for-linear-and-hybrid-systems/19E93EC5839B4BBE2E665DF96A5DED43) for background.

  - **9.9.1 Deterministic Model Predictive Control**
    - Assumes deterministic transition dynamics for tractability.
    - Uses deterministic transition function T(s,a) in constraints.
    - Commonly uses most likely transitions or single sampled transitions for approximations.
    - Solves optimization problems efficiently with convex programming.

  - **9.9.2 Robust Model Predictive Control**
    - Maximizes worst-case reward over all possible next states in uncertainty set T(s,a).
    - Formulates minimax optimization problems that can be conservative and nonconvex.
    - Can restrict uncertainty sets to contain a fixed probability mass to reduce conservatism.
    - See [Robust Model Predictive Control: A Survey](https://ieeexplore.ieee.org/document/796453) for survey.

  - **9.9.3 Multi-Forecast Model Predictive Control**
    - Uses multiple forecast scenarios with deterministic transitions per scenario.
    - Optimizes actions against worst-case or expected-case outcomes over scenarios.
    - Facilitates convex or tractable approximations of robust control.
    - Example 9.11 models linear-Gaussian transitions using sampled noise sequences.
    - Related approach called hindsight optimization allows leveraging known realizations.
    - See [Modulating Robustness in Control Design](https://ieeexplore.ieee.org/document/6477000) for detailed methods.

- **9.10 Summary**
  - Online planning focuses computation on reachable states from current state.
  - Receding horizon planning plans fixed horizon and replans iteratively.
  - Lookahead with rollouts simulates rollout policies to estimate values for greedy action selection.
  - Forward search expands all state-action transitions with exponential complexity.
  - Branch and bound prunes subtrees using value bounds to improve efficiency.
  - Sparse sampling reduces branching by sampling limited successor states.
  - Monte Carlo tree search balances exploration and exploitation via simulations.
  - Heuristic search iteratively improves value estimates using greediness and simulations.
  - Labeled heuristic search labels solved states to reduce redundant computation.
  - Open-loop planning finds action sequences for efficient optimization, often assuming deterministic models.

- **9.11 Exercises**
  - Exercise 9.1: Branch and bound has worst-case complexity equal to forward search if no pruning occurs.
  - Exercise 9.2: Combine two admissible heuristics by taking their minimum for guaranteed admissibility.
  - Exercise 9.3: Combine two inadmissible heuristics by taking their maximum to improve heuristic effectiveness.
  - Exercise 9.4: To make forward search complexity depth-invariant, state and action spaces must be reduced exponentially in depth.
  - Exercise 9.5: Keeping original actions and coarser state space requires state space size scaled by |S|^(1/d) / |A|^((d-1)/d).
  - Exercise 9.6: Action ordering can affect branch and bound visited nodes and potentially chosen actions if ties occur.
  - Exercise 9.7: Sparse sampling with m=|S| is not equivalent to forward search; it samples states randomly.
  - Exercise 9.8: Probability that sparse sampling with m=|S| and depth 1 matches forward search is extremely low.
  - Exercise 9.9: Computed upper confidence bounds with parameter c select actions balancing exploration and exploitation.
