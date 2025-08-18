- Model-Based Methods
  - Maximum Likelihood Models
    - Maximum likelihood estimates of transition and reward functions use counting of observed state transitions and summation of received rewards. Transition probabilities are estimated as ratios of transition counts, and mean rewards are computed per state-action pair. Initial counts can be nonzero to incorporate prior knowledge. The methods require heuristic exploration to balance exploitation.
      External resource: [Reinforcement Learning: An Introduction, Sutton and Barto](http://incompleteideas.net/book/the-book.html)
  - Update Schemes
    - Different update schemes for maintaining and improving the value function under continuously changing models aim to balance computational efficiency and accuracy. Full updates resolve the entire model using linear programming after each transition; randomized updates perform Bellman backups at visited and random states; prioritized sweeping focuses updates on states with the highest priority using a queue propagated by transition likelihood and value changes.
      External resource: [Prioritized Sweeping in Reinforcement Learning](https://papers.nips.cc/paper/1993/file/03de0a9763cc3512beb4ebf412824dda-Paper.pdf)
  - Bayesian Methods
    - Bayesian reinforcement learning represents uncertainty over transition models using Dirichlet distributions, one per state-action pair. This approach uses prior distributions updated with observed counts to form posteriors, enabling reasoning about model uncertainty. Although maintaining a full Bayesian belief state is computationally intensive, it enables principled exploration without heuristic parameters.
      External resource: [Bayesian Reinforcement Learning: A Survey](https://homes.cs.washington.edu/~manishg/papers/brlsurvey.pdf)
  - Bayes-adaptive MDPs
    - A Bayes-adaptive MDP models the unknown MDP parameters as part of the state space by augmenting the original states with belief over model parameters. This creates a continuous belief state space, where the transition function includes Bayesian belief updating. The optimal value function satisfies a generalized Bellman equation but is difficult to solve directly due to belief space complexity.
      External resource: [Bayes-Adaptive MDPs](https://papers.nips.cc/paper/2006/file/20a3b60ba9b3a678405e5c4f69975749-Paper.pdf)
  - Posterior Sampling
    - Posterior sampling reduces computational complexity by sampling a single MDP model from the current Bayesian posterior and solving it optimally to select actions. This procedure alternates between belief updates via observed transitions and resampling models, avoiding heuristic exploration parameters and approximating the Bayes-adaptive solution.
      External resource: [A Bayesian Framework for Reinforcement Learning](https://icml.cc/Conferences/2000/proceedings/papers/StrensM.pdf)
