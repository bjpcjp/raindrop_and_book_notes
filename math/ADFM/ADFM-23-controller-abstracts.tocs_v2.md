- **Controllers**
  - Controllers maintain internal state represented as a finite graph of nodes.
  - Actions depend on the current node via a stochastic action selection distribution ψ.
  - Successor nodes depend on the current node, action, and observation via a distribution η.
  - Controllers generalize conditional plans by allowing stochastic transitions and infinite horizon policies.
  - See [Finite State Controllers in POMDPs](https://cs.stanford.edu/people/eroberts/courses/soco/projects/pomdp/finite_state_controllers.html) for more.

- **Policy Iteration**
  - Policy iteration alternates between policy evaluation and policy improvement steps.
  - Improvement adds new deterministic nodes with fixed action and successor choices.
  - Pruning removes dominated or duplicate nodes to control growth.
  - The algorithm guarantees non-decreasing utility and convergence to an optimal policy.
  - See Hansen, E. A. (1998). [Solving POMDPs by Searching in Policy Space](https://papers.nips.cc/paper_files/paper/1998/file/7b8c180ek9b50a2ca5a6aecd3662b4e0-Paper.pdf).

- **Nonlinear Programming**
  - Reformulates fixed-size controller optimization as a quadratically constrained linear program.
  - Simultaneously optimizes action selection ψ and successor selection η.
  - No alternating evaluation and improvement steps required.
  - Enables use of general-purpose nonlinear solvers like Ipopt.
  - See Amato, C., Bernstein, D. S., & Zilberstein, S. (2010). [Optimizing Fixed-Size Stochastic Controllers for POMDPs](https://doi.org/10.1007/s10458-010-9122-x).

- **Gradient Ascent**
  - Uses gradient-based optimization to iteratively improve fixed-size controllers.
  - Computes gradients of the utility with respect to ψ and η via matrix calculus on the Bellman equation.
  - Updates parameters followed by projection onto probability simplices to maintain validity.
  - Gradient ascent can converge to local optima and benefits from adaptive step sizes.
  - See Meuleau et al. (1999). [Solving POMDPs by Searching the Space of Finite Policies](https://doi.org/10.5555/2074047.2074060).

- **Summary**
  - Controllers avoid explicit belief maintenance, improving computational tractability.
  - Nodes can be interpreted as abstract subsets of the belief space linked to alpha vectors.
  - Policy iteration combines evaluation, improvement, and pruning for convergence on optimal policies.
  - Nonlinear programming and gradient ascent offer optimization approaches for fixed-size controllers.
  - Controllers provide scalable policy representations for infinite horizon POMDPs.

- **Exercises**
  - Compare advantages of controller policies over conditional plans and belief-based methods.
  - Discuss optimality and limitations of deterministic node additions in controller policy iteration.
  - Prove that pruning nodes does not alter the policy utility.
  - Propose an algorithm to find minimal controller size achieving large controller utility.
  - Analyze computational complexity of the gradient ascent step and propose improvements.
  - For further practice, refer to [POMDPs.jl Documentation](https://github.com/JuliaPOMDP/POMDPs.jl).
