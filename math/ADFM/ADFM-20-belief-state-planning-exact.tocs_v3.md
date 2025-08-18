![ADFM-20-belief-state-planning-exact](ADFM-20-belief-state-planning-exact.best.png)

- **20 Exact Belief State Planning**
  - The chapter explains that since states are not directly observable, POMDP agents use histories of actions and observations to maintain belief states represented as probability distributions.
  - The focus is on methods to compute optimal policies mapping beliefs to actions, including converting POMDPs to belief-state MDPs and using value iteration.
  - For further reading, see Kaelbling, Littman, and Cassandra, "Planning and Acting in Partially Observable Stochastic Domains," Artificial Intelligence, 1998.

- **20.1 Belief-State Markov Decision Processes**
  - Any POMDP can be reformulated as a belief-state MDP, where states are beliefs (distributions over physical states) and actions remain unchanged.
  - The belief-state transition function is derived by marginalizing over observations and next states, with updates implemented as deterministic functions.
  - Reward functions depend on actions and expected rewards under the current belief.
  - For foundational theory, see Åström, "Optimal Control of Markov Processes with Incomplete State Information," Journal of Mathematical Analysis and Applications, 1965.

- **20.2 Conditional Plans**
  - Policies can be represented as conditional plans (trees) where nodes correspond to belief states and edges to observations dictating subplans.
  - Conditional plans describe actions based on observation histories up to a planning horizon; expected utility of plans can be computed recursively.
  - Enumerating all possible conditional plans grows exponentially with horizon and observation space, making direct enumeration generally intractable.
  - See Algorithm 20.1 for the data structure and Algorithm 20.2 for plan evaluation methods.

- **20.3 Alpha Vectors**
  - Alpha vectors represent the expected utility of conditional plans as vectors indexed by states, making value functions piecewise-linear and convex over belief space.
  - The optimal value function is the maximum over these alpha vectors, providing a compact policy representation.
  - Policies can be executed by selecting actions associated with the dominating alpha vector at the current belief.
  - For more on exact solution methods using alpha vectors, refer to Cassandra, Littman, and Zhang, "Incremental Pruning: A Simple, Fast, Exact Method for POMDPs," UAI 1997.

- **20.4 Pruning**
  - Pruning removes alpha vectors or conditional plans that are dominated and do not improve the value function for any belief.
  - Dominance is tested via a linear program maximizing the utility gap to certify if an alpha vector is optimal at some belief.
  - Iterative pruning algorithms refine the set of alpha vectors for computational efficiency in value iteration.
  - Algorithm 20.6 and 20.7 describe implementations for finding maximal beliefs and dominating alpha vectors.

- **20.5 Value Iteration**
  - Value iteration for POMDPs alternates plan expansion (constructing longer conditional plans) and pruning to keep only dominating plans.
  - Each iteration constructs all (k+1)-step plans by combining new actions with previous k-step subplans and computes corresponding alpha vectors efficiently.
  - This procedure converges to the optimal finite-horizon value function while managing combinatorial complexity.
  - For foundational work, see the original POMDP value iteration algorithms by Cassandra et al., 1997.

- **20.6 Linear Policies**
  - In linear-Gaussian systems with quadratic rewards, belief states are Gaussian distributions, and optimal policies can be computed offline using Linear-Quadratic-Gaussian (LQG) control.
  - The belief mean µb suffices for control computations, and actions obtained by applying LQG control to µb are optimal.
  - The chapter illustrates this with a satellite navigation example using noisily observed linear dynamics and Kalman filtering.
  - For details on LQG, see Section 7.8 or control theory literature on LQG.

- **20.7 Summary**
  - Exact POMDP solutions usually apply only to finite-horizon discrete cases due to computational complexity.
  - Policies can be represented as conditional plans or sets of alpha vectors with piecewise-linear convex value functions.
  - Value iteration uses pruning to avoid exhaustive enumeration of conditional plans.
  - Linear-Gaussian problems with quadratic reward admit exact polynomial-time solutions via LQG methods.

- **20.8 Exercises**
  - Exercises cover framing POMDPs as belief-state MDPs, interpreting alpha vectors, computational complexity related to actions and observations, and practical POMDP modeling.
  - Examples include the crying baby problem, multi-test diagnostic decision processes, and alpha vector pruning conditions.
  - Exercise solutions illustrate reasoning about policy dominance, belief updates, and reward calculations relevant to POMDP analysis.
