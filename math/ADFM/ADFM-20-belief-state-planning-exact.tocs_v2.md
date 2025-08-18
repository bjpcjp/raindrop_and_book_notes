- **Exact Belief State Planning**
  - The agent maintains a belief state as a probability distribution over states due to partial observability.  
  - POMDPs aim to maximize expected cumulative reward considering transitions, observations, and rewards.  
  - Policies map beliefs to actions, with approaches including MDP conversion, conditional plans, and piecewise linear value functions.  
  - [Planning and Acting in Partially Observable Stochastic Domains](https://doi.org/10.1016/S0004-3702(98)00023-X) provides detailed solution methods.

- **Belief-State Markov Decision Processes**
  - Any POMDP can be formulated as an MDP with belief states as its states.  
  - The belief-state transition function integrates over possible observations and system states.  
  - The reward function is the expected reward over the belief distribution.  
  - Solutions are challenging due to the continuous belief space.  
  - [Åström, 1965](https://doi.org/10.1016/0022-247X(65)90031-6) is a seminal reference on control with incomplete state information.

- **Conditional Plans**
  - Policies can be represented as trees of actions conditioned on observations.  
  - The utility of a conditional plan is computed recursively from expected rewards and transitions.  
  - Conditional plans grow exponentially with horizon and observation set size, making enumeration intractable.  
  - Example plans illustrate the tradeoff between feeding and ignoring a crying baby.  

- **Alpha Vectors**
  - Alpha vectors represent expected state utilities of conditional plans and define hyperplanes in belief space.  
  - The value function is piecewise-linear and convex as the maximum over alpha vectors.  
  - Policies can be represented by sets of alpha vectors paired with actions.  
  - One-step lookahead using alpha vectors efficiently approximates optimal actions beyond the original plan horizon.  
  - [Cassandra, Littman, and Zhang 1997](https://www.aaai.org/Papers/UAI/1997/UAI97-053.pdf) discusses incremental pruning of alpha vectors.

- **Pruning**
  - Alpha vectors that do not improve value for any belief point are dominated and can be pruned.  
  - A linear program identifies belief states maximizing the utility gap for an alpha vector compared to others.  
  - Iterative pruning identifies a minimal set of dominating alpha vectors representing the value function.  
  - Pruning improves computational efficiency by eliminating suboptimal plans and vectors.  

- **Value Iteration**
  - POMDP value iteration iteratively constructs and prunes conditional plans of increasing horizon length.  
  - Expansion combines one-step plans with subplans to form longer horizon plans using alpha vectors.  
  - Pruning removes dominated plans at each iteration to limit growth.  
  - Value iteration effectively approximates the optimal policy for finite-horizon POMDPs.  
  - [Value Iteration for POMDPs (Cassandra, Littman, Zhang, 1997)](https://www.aaai.org/Papers/UAI/1997/UAI97-051.pdf) details this method.

- **Linear Policies**
  - For linear-Gaussian dynamics and quadratic rewards, the belief is a Gaussian parameterized by mean and covariance.  
  - The optimal policy corresponds to linear-quadratic-Gaussian (LQG) control treating the belief mean as the state.  
  - Kalman filtering updates the belief mean using observations, enabling exact offline policy computation.  
  - Example: A satellite stabilizes in orbit with linear dynamics, Gaussian noise, and quadratic costs applying LQG control.

- **Summary**
  - Exact POMDP solutions are feasible primarily for finite-horizon, discrete problems.  
  - Conditional plans represent policies as observation-conditioned action trees.  
  - Alpha vectors enable piecewise-linear convex value function representations and efficient policy execution.  
  - Pruning and value iteration mitigate exponential growth in plan enumeration.  
  - Linear-Gaussian problems allow exact offline solutions using methods analogous to fully observable cases.  

- **Exercises**
  - The exercises cover POMDP framing as belief MDPs, alpha vector derivation, computational tradeoffs, and application modeling.  
  - They elucidate the growth rates of plans related to actions and observations, and the role of repeated observations in diagnostics.  
  - Exercise solutions demonstrate pruning conditions based on alpha vector dominance and belief vector optimization.  
  - Diagnostic testing and treatment decision problems are expressed as POMDP with deterministic transitions and observation models.
