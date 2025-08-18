- Online Planning Overview
  - The section introduces online planning methods that compute actions based on states reachable from the current state, which is often much smaller than the full state space. These methods reduce computational and storage requirements compared to offline approaches and include pruning, sampling, and deeper trajectory planning in promising directions. For further study, see [Online Planning in Reinforcement Learning](https://web.stanford.edu/class/cs234/).

- Receding Horizon Planning
  - Receding horizon planning plans actions up to a fixed depth d from the current state, executes the first action, transitions to the next state, and replans. The choice of depth d affects computational cost and safety performance, illustrated with aircraft collision avoidance where deeper planning yields earlier advisories and improved safety. Further reading: [Model Predictive Control](https://ieeexplore.ieee.org/document/704923).

- Lookahead with Rollouts
  - This section covers acting greedily with respect to values estimated by simulating rollouts from a policy π to depth d using a generative model. Rollout policies can be stochastic to generate successor states, and multiple rollouts improve value estimates with time complexity O(m × |A| × d). It relates to policy improvement methods in approximate dynamic programming. Additional reading: [Rollout Algorithms](https://www.cs.utexas.edu/~pstone/Papers/bib2html-links/ijcai05-rollout.pdf).

- Forward Search
  - Forward search builds a search tree by expanding all possible actions and successor states up to depth d, with worst-case complexity O((|S| × |A|)^d). It uses recursive calls and an approximate value function U at the depth limit. This approach is combined with offline estimates in hybrid planning to manage computational costs. For more, see [Classical Search Algorithms](https://web.stanford.edu/class/cs221/lectures/search.pdf).

- Branch and Bound
  - Branch and bound prunes subtrees in the forward search tree using lower bounds on the value function and upper bounds on the action-value function Q(s, a). If an action’s upper bound is less than the best found lower bound, it prunes that action’s subtree. Traversing actions by descending upper bound facilitates pruning, significantly reducing explored states under tight bounds. Explore details at [Branch and Bound Methods](https://www.cambridge.org/core/books/design-and-analysis-of-branch-and-bound-algorithms/99683AA60843CB3416D0B6374FB0DB4E).

- Sparse Sampling
  - Sparse sampling reduces complexity by sampling m successor states per action instead of branching on all. Its complexity is O((m × |A|)^d), exponential in depth but independent of the full state space size. This approximation is effective in practice for large spaces, demonstrated with visual examples in grid-world problems. See [Sparse Sampling for MDPs](https://link.springer.com/chapter/10.1007/3-540-44492-7_14).

- Monte Carlo Tree Search (MCTS)
  - MCTS performs m simulations from the current state, updating Q(s, a) and visit counts N(s, a) using an upper confidence bound balancing exploration and exploitation. It expands unexplored nodes via rollouts using a rollout policy and uses counts to guide action selection. Variations include progressive widening for large or continuous spaces. Further reading: [A Survey of MCTS Methods](https://ieeexplore.ieee.org/document/6145622).

- Heuristic Search
  - Heuristic search runs m simulations of a greedy policy with respect to an upper bound on the value function U to depth d, updating U during simulations via lookahead. If U is an admissible heuristic (upper bound), convergence to an optimal policy is guaranteed. Its efficiency depends on heuristic tightness. Refer to [Heuristic Search in AI](https://www.cs.cmu.edu/~rrandell/Papers.pdf).

- Labeled Heuristic Search
  - This variant labels states as solved when their utility residual drops below a threshold δ. Simulations run until the current state is solved. Labeling uses the state’s greedy envelope, updating or marking states solved to avoid reevaluation and focus computation on critical states. For comprehensive understanding, see [Labeled RTDP](https://icaps-conference.org/icalp/editions/). 

- Open-Loop Planning
  - Open-loop planning optimizes a sequence of actions a1:d maximizing expected return without adapting to future state information, enhancing efficiency especially if the problem or approximation is convex. Deterministic approximations (model predictive control) and robust formulations (minimax over uncertainty sets) are discussed, along with multi-forecast scenario-based approaches that improve tractability and robustness. Learn more at [Model Predictive Control and Optimization](https://mitpress.mit.edu/books/model-predictive-control).
