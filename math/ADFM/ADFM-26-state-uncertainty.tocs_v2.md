- Partially Observable Markov Games (POMGs)
  - Definition and structure  
    A POMG generalizes Markov games to partial observability and POMDPs to multiple agents. Agents select actions based on local noisy observations of a shared but not fully observed state. Transitions, joint observations, and joint rewards follow defined probabilistic functions, creating highly complex modeling and computational challenges. This section relates POMGs to extensive form games with imperfect information and presents the "crying baby" multiagent example. See [POMDPs and Multiagent Systems](https://mitpress.mit.edu/books/partially-observable-markov-decision-processes).
- Policy Evaluation
  - Evaluating conditional plans  
    Conditional plans represent deterministic policies as trees associating actions with nodes and observations with edges. Joint policies are trees per agent, recursively evaluated using joint state transitions, observations, and rewards to compute expected utilities from initial states or distributions. Algorithm 26.2 formalizes this evaluation for finite horizons. For further details, consult [Reinforcement Learning: An Introduction](http://incompleteideas.net/book/the-book.html).
  - Evaluating stochastic controllers  
    Stochastic controller policies use probabilistic action and successor distributions on graph nodes. Utilities satisfy a linear system defined by joint action probabilities, transition, observation, and reward functions. Policy evaluation reduces to solving linear equations or iterative methods, extending single-agent POMDP controller evaluation to multiagent cases. Additional treatments are in [Dynamic Programming Techniques for POMDPs](https://jair.org/index.php/jair/article/view/10182).
- Nash Equilibrium in POMGs
  - Computing d-step Nash equilibria via enumeration  
    Computing Nash equilibria entails constructing a simple game where joint actions correspond to all possible d-step joint conditional plans in the POMG. Utilities derive from the POMG joint policy values. A Nash equilibrium of this simple game translates to a Nash equilibrium in the POMG. This approach is conceptually straightforward but computationally costly. For the theoretical foundation, see [Nash Equilibrium and Game Theory](https://plato.stanford.edu/entries/game-equilibrium/).
- Dynamic Programming for Nash Equilibria
  - Iterative expansion and pruning of conditional plans  
    Dynamic programming improves Nash equilibrium computation by incrementally constructing longer conditional plans and pruning dominated policies. Pruning uses linear programming checks to eliminate policies that never outperform alternatives across all states and opponents' policies. This reduces combinatorial explosion in policy sets while retaining optimal solutions. The method parallels POMDP alpha-vector pruning. Related methods are discussed in [Sequential Decision Making in Multiagent Systems](https://link.springer.com/chapter/10.1007/978-3-642-35078-5_7).
  - Example: Multi-caregiver crying baby problem  
    The two-agent crying baby problem illustrates policy pruning's efficacy, significantly decreasing policies considered at each iteration. Pruning retains policies that maximize utilities given the stochastic dynamics and shared noisy observations, demonstrating practical benefits of dynamic programming in POMGs. See also [Multiagent Reinforcement Learning](https://book.stanford.edu/materials/handouts/StanfordMultiagentRL.pdf).
- Exercises and Solutions
  - Generalization of POMDPs and MGs by POMG  
    POMGs encompass POMDPs when restricted to one agent and MGs when states are perfectly observed by all agents. This highlights their expressive power spanning single and multiagent, fully and partially observable settings.  
  - Incorporating communication in POMGs  
    Communication integrates by augmenting agent action spaces with communication actions, observable by other agents under the observation function, enabling explicit information exchange.  
  - Incentives for communication  
    Incentives depend on agent objectives; competitive scenarios reduce communication incentives, while aligned rewards encourage it.  
  - Counting joint conditional plans of depth d  
    The number of joint conditional plans grows combinatorially with the product across agents of their action counts raised to the power related to observation branching factor, reflecting explosion in policy spaces with horizon length.  
  - Best response and iterated best response definitions  
    Best responses maximize individual expected utilities given others' policies, formalized via inequalities over expected values from joint policies. Iterated best response applies sequential optimization updating agents' policies to converge toward equilibrium. See in-depth discussions in [Multiagent Systems: Algorithmic, Game-Theoretic, and Logical Foundations](https://www.cs.rutgers.edu/~sanjay/multiagent-book/).
