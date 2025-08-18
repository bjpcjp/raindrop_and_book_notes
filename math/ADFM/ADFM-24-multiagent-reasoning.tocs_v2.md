- **24 Multiagent Reasoning**  
  - **24.1 Simple Games**  
    - A simple game models multiple agents each selecting actions to maximize their own reward without states or transitions.  
    - The joint action space is the cartesian product of individual agents' actions, with rewards given by a joint reward function.  
    - Examples include the Prisoner's Dilemma and Rock-Paper-Scissors, representing classic multiagent strategic scenarios.  
    - A joint policy specifies the probability distribution over joint actions and can be decomposed into individual agent policies.  
    - Refer to [Multiagent Systems: Algorithmic, Game Theoretic, and Logical Foundations](https://doi.org/10.1017/CBO9780511809697) for foundational knowledge.  

  - **24.2 Response Models**  
    - Models how an agent responds given fixed policies of other agents, written as π = (π_i, π_{-i}).  
    - The best response is a policy maximizing the agent's utility given fixed opponents’ policies.  
    - The softmax response models stochastic action selection with parameter λ, moving from random to deterministic best response as λ increases.   
    - Softmax responses capture bounded rationality and can be fit to observed behaviors through learning.  
    - See [Behavioral Game Theory](https://press.princeton.edu/books/paperback/9780691118415/behavioral-game-theory) by Camerer for details on softmax and bounded rationality.  

  - **24.3 Nash Equilibrium**  
    - A Nash equilibrium is a joint policy where no agent can improve their utility by unilaterally changing their policy.  
    - Every finite action simple game has at least one Nash equilibrium, which may be stochastic.  
    - Finding Nash equilibria is PPAD-complete, reflecting computational hardness distinct from NP-completeness.  
    - Nash equilibria can be posed as nonlinear programs optimizing utility subject to best response constraints.  
    - Original work by John Nash: [Non-Cooperative Games (1951)](https://www.jstor.org/stable/1969529).  

  - **24.4 Correlated Equilibrium**  
    - Correlated equilibria relax independence assumptions, using a single joint distribution over actions that may correlate agents’ strategies.  
    - All Nash equilibria are correlated equilibria, but not all correlated equilibria are Nash equilibria.  
    - Correlated equilibria can be computed via linear programming with constraints enforcing no incentive to deviate.  
    - Different objectives allow selection among multiple correlated equilibria to optimize utilitarian, egalitarian, plutocratic, or dictatorial criteria.  
    - For details see [Correlated Q-Learning (Greenwald and Hall, 2003)](https://proceedings.neurips.cc/paper/2003/file/8200e3ac2061f649ae23f50778bc5c45-Paper.pdf).  

  - **24.5 Iterated Best Response**  
    - Iterative procedure where agents cyclically update their policies to best respond to others’ current policies.  
    - This process can converge to a Nash equilibrium for some classes of games but may cycle indefinitely in others.  
    - Initialization often uses uniform random policies, and stopping criteria depend on iteration limits.  
    - Convergence guaranteed in potential games; otherwise, cycling can occur.  
    - [Algorithmic Game Theory (Nisan et al., 2007)](https://doi.org/10.1017/CBO9780511809086) covers convergence conditions.  

  - **24.6 Hierarchical Softmax**  
    - Behavioral model parameterizing agents by rationality level (k) and precision (λ).  
    - Level-0 agents choose actions uniformly at random, level-k agents assume others are level-(k−1) and respond via softmax.  
    - Parameters k and λ can be learned from observed data via maximum likelihood or Bayesian methods.  
    - This approach captures bounded rationality and varying depths of strategic reasoning.  
    - See [Beyond Equilibrium: Predicting Human Behavior in Normal Form Games (Wright & Leyton-Brown, 2010)](https://aaai.org/ocs/index.php/AAAI/AAAI10/paper/view/1553).  

  - **24.7 Fictitious Play**  
    - Learning algorithm where each agent maintains counts of others’ past actions to form maximum likelihood estimates of their policies.  
    - Agents best respond to these estimated policies, updating counts iteratively with observed joint actions.  
    - Does not guarantee convergence but converges in some classes of games such as potential games.  
    - Variants include smooth fictitious play (with regularization) and Bayesian learning (updating beliefs with priors).  
    - Historical foundations in [Iterative Solution of Games by Fictitious Play (Brown, 1951)](https://www.jstor.org/stable/2226414).  

  - **24.8 Summary**  
    - Multiagent decision-making introduces complexity beyond single-agent rationality with multiple solution concepts.  
    - Best response, Nash equilibrium, and correlated equilibrium provide hierarchical notions of optimality.  
    - Iterated best response and fictitious play are dynamic adaptation algorithms with convergence depending on game structure.  
    - Hierarchical softmax models bounded rational human behavior in games.  
    - Refer to comprehensive surveys in [Multiagent Systems (Shoham & Leyton-Brown, 2009)](https://doi.org/10.1017/CBO9780511809697).  

  - **24.9 Exercises**  
    - Exercises explore existence and examples of Nash equilibria including infinite action spaces and multiple equilibria with deterministic policies.  
    - Exercises demonstrate proofs that a Nash equilibrium is also a correlated equilibrium and vice versa.  
    - Examples illustrate games where correlated equilibria outperform any Nash equilibrium and non-convergent iterations of algorithms.  
    - Solutions reinforce understanding of equilibrium concepts and algorithm behaviors.  
    - Reference: [Decision Making Under Uncertainty (Kochenderfer, 2015)](https://web.stanford.edu/~mkockend/DA-book/).
