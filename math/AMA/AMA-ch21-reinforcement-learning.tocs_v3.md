![AMA-ch21-reinforcement-learning](AMA-ch21-reinforcement-learning.best.png)

- **21.1 Introduction**  
  - Reinforcement learning enables agents to learn from rewards and punishments when labeled examples of actions are unavailable.  
  - The agent learns optimal policies that maximize expected total rewards in unknown Markov decision processes.  
  - Three agent designs are covered: utility-based, Q-learning, and reflex agents.  
  - Understanding Markov decision processes (MDPs) is essential as background ([MDP chapter](https://example.org/mdp)).  

- **21.2 Passive Reinforcement Learning**  
  - A fixed-policy agent learns the utilities of states without exploratory action choices.  
  - Direct utility estimation uses observed total rewards-to-go as supervised learning targets.  
  - Adaptive dynamic programming (ADP) learns a transition model and solves Bellman equations for utilities.  
  - Temporal-difference (TD) learning updates utilities incrementally using observed transitions without a model.  
  - ADP is computationally intensive but accurate; TD is simpler but slower to converge.  

- **21.3 Active Reinforcement Learning**  
  - Active agents choose actions and must balance exploitation of current knowledge with exploration of unknown states.  
  - Greedy agents that always pick the optimal action for the current model can converge to suboptimal policies.  
  - Exploration strategies trade off immediate rewards against acquiring information to improve future decisions.  
  - GLIE schemes ensure all actions are tried infinitely often and the policy becomes greedy in the limit.  
  - The exploration function biases toward under-explored state-action pairs to encourage exploration.  
  - Q-learning learns action-utility values without an explicit model, enabling model-free learning and action selection.  
  - SARSA differs from Q-learning by updating based on the policy actually followed (on-policy vs off-policy).  

- **21.4 Generalization in Reinforcement Learning**  
  - Tabular representations are impractical for large state spaces; function approximation compresses utility or Q-functions.  
  - Function approximation enables generalization from visited to unvisited states using parameterized representations like linear functions or neural networks.  
  - Online learning applies gradient-based updates such as the Widrow–Hoff (delta) rule to parameterize approximations.  
  - Temporal-difference and Q-learning can incorporate function approximators but convergence can be unstable especially with nonlinear functions.  
  - Function approximation is also applicable to model learning using supervised methods.  

- **21.5 Policy Search**  
  - Policy search adjusts parameterized policies directly to improve expected reward without learning utilities or models explicitly.  
  - Stochastic policies with softmax parameterizations provide differentiability for gradient-based methods.  
  - Gradient estimations can be obtained from trial executions using the REINFORCE algorithm, which is more sample-efficient than naive hill climbing.  
  - Correlated sampling exploits fixed random seeds to reduce variance in policy comparisons, as in the PEGASUS algorithm.  

- **21.6 Applications of Reinforcement Learning**  
  - **Game Playing**  
    - Samuel’s checkers program pioneered reinforcement learning with linear evaluation functions and temporal difference updates.  
    - TD-GAMMON used neural networks and self-play to learn expert-level backgammon play from end-of-game rewards.  
    - Reinforcement learning can learn effective evaluation functions with minimal handcrafted features.  
  - **Robot Control**  
    - The cart–pole balancing problem introduced continuous states and bang-bang control to reinforcement learning.  
    - Discretization and function approximation methods improved generalization and learning speed for continuous control.  
    - Policy search methods like PEGASUS have enabled helicopter control achieving expert-level maneuvers using learned simulators.  

- **21.7 Summary**  
  - Reinforcement learning encompasses model-based agents learning models and utilities, model-free agents learning Q-functions, and reflex agents learning policies.  
  - Utility learning methods include direct estimation, ADP, and TD learning, each with tradeoffs in model requirements and computational complexity.  
  - Active agents must solve exploration-exploitation tradeoffs; heuristic exploration functions provide practical solutions.  
  - Function approximation enables scaling to large, complex state spaces by permitting generalization.  
  - Policy search optimizes parameterized policies directly using gradient methods or sampling.  
  - Reinforcement learning’s promise is substantial in robotics and domains requiring complex control and large action spaces.  

- **Bibliographical and Historical Notes**  
  - Early ideas stem from Turing (1948,1950) and Samuel’s pioneering checkers research (1959).  
  - Temporal difference learning originated from adaptive control theory and was linked to psychological models of animal learning.  
  - The interplay between reinforcement learning and Markov decision processes was formalized in the 1980s.  
  - Key algorithms include TD(λ), Q-learning, SARSA, and ADP; challenges arose in exploration and function approximation.  
  - Function approximation successes include TD-GAMMON; policy gradient methods like REINFORCE improved gradient-based learning.  
  - Advances address hierarchical, multiagent, and apprenticeship learning frameworks for real-world tasks.  
  - Further resources: Sutton and Barto's [Reinforcement Learning book](http://incompleteideas.net/book/the-book.html) and Kaelbling et al. (1996) survey.  

- **Exercises**  
  - Implement and compare passive learning algorithms: direct utility estimation, TD, and ADP in grid worlds.  
  - Analyze and address issues with learned transition models and improper policies.  
  - Develop approximate ADP algorithms using prioritized sweeping heuristics.  
  - Derive parameter update rules for function approximators with nonlinear features.  
  - Evaluate exploration strategies with and without function approximation in grid environments.  
  - Design features for reinforcement learning in environments with obstacles and multiple rewards.  
  - Extend game-playing environments to reinforcement learning settings with competing agents.  
  - Compare true and approximated utility functions in various gridworld configurations.  
  - Implement policy search algorithms REINFORCE and PEGASUS, then test on gridworlds.  
  - Discuss connections between reinforcement learning and biological evolution.
