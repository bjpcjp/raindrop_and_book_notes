- **13 Actor-Critic Methods**
  - **13.1 Actor-Critic**
    - Actor-critic methods combine a parameterized policy (actor) and a value function estimator (critic) and optimize both with gradient-based methods.
    - The actor uses policy gradient ascent based on advantage estimates obtained via the critic.
    - The critic minimizes the squared temporal difference residual between its estimate and the observed reward-to-go.
    - Stability can be enhanced by updating the policy more frequently than the value function.
    - Refer to [Policy Gradient Methods for RL with Function Approximation](https://papers.nips.cc/paper/1999/hash/464d828b85b67f66b9722a5b2166d7aa-Abstract.html) for foundational context.

  - **13.2 Generalized Advantage Estimation**
    - Generalized Advantage Estimation (GAE) uses exponentially weighted averages of k-step advantage estimations to balance bias and variance in policy gradient estimates.
    - The parameter λ ∈ [0,1] controls the tradeoff between low variance (temporal difference residual, λ=0) and low bias (full rollout, λ=1).
    - GAE computes advantages as weighted sums of temporal difference residuals along rollouts.
    - Empirically, GAE improves policy and value function learning efficiency over the basic actor-critic method.
    - See [High-Dimensional Continuous Control Using Generalized Advantage Estimation](https://arxiv.org/abs/1506.02438) for algorithmic details and experiments.

  - **13.3 Deterministic Policy Gradient**
    - Deterministic policy gradient applies to continuous action spaces with deterministic policies and critics parameterized as action-value functions.
    - The critic is updated by minimizing the temporal difference residual of Q-values.
    - The actor’s gradient is computed using the chain rule combining policy Jacobian and action-value gradients.
    - Exploration is promoted by adding Gaussian noise to deterministic actions, enhancing learning stability.
    - See [Deterministic Policy Gradient Algorithms (Silver et al. 2014)](https://proceedings.mlr.press/v32/silver14.html) for theoretical grounding and applications.

  - **13.4 Actor-Critic with Monte Carlo Tree Search**
    - Integrates Monte Carlo tree search (MCTS) with actor-critic learning to improve policy and value function estimates.
    - Uses an upper confidence bound that incorporates the learned policy to guide exploration in tree search.
    - Updates policy parameters by minimizing the cross-entropy to the MCTS-derived policy distribution.
    - Updates value function by minimizing squared error relative to MCTS value estimates.
    - This approach resembles AlphaGo Zero’s method of combining planning and learning; see [Mastering the Game of Go Without Human Knowledge](https://www.nature.com/articles/nature24270).

  - **13.5 Summary**
    - Actor-critic methods optimize parameterized policies with the assistance of value-function estimators using gradient methods.
    - Generalized advantage estimation reduces policy gradient variance by mixing multi-step temporal difference residuals.
    - Deterministic policy gradients extend actor-critic methods to continuous action spaces with deterministic policies.
    - Online planning methods like MCTS can enhance actor-critic training by guiding exploration and learning.
    - For deeper understanding, consult original references cited in each method section.

  - **13.6 Exercises**
    - Exercises test comprehension on applying actor-critic methods, recognizing proper advantage functions, and computing gradients in deterministic policy gradients.
    - Highlights that Monte Carlo tree search is less appropriate for continuous state spaces without discretization.
    - Clarifies benefits and tradeoffs of temporal difference residuals versus rollout rewards for advantage estimation.
    - Provides examples of gradient calculations for parameterized action-value functions.
    - Useful for practice in applying theoretical concepts to concrete problems in reinforcement learning.
