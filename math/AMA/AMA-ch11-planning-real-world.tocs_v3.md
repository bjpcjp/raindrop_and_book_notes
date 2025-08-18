![AMA-ch11-planning-real-world](AMA-ch11-planning-real-world.best.png)

- **11.1 Time, Schedules, and Resources**
  - The section extends classical planning to include action durations and temporal/resource constraints.
  - Resources are modeled as numeric quantities with consumable and reusable properties.
  - The critical path method is used to find minimal schedules ignoring resource constraints.
  - Scheduling with resources is NP-hard and requires heuristics like the minimum slack algorithm.
  - For deeper background see [Lawler et al., 1993](https://en.wikipedia.org/wiki/Job_shop_scheduling#Complexity).

- **11.2 Hierarchical Planning**
  - Planning at higher abstraction levels manages complexity beyond thousands of primitive actions.
  - High-Level Actions (HLAs) are refined into sequences of HLAs or primitive actions, enabling hierarchical task networks (HTNs).
  - Two hierarchical planning approaches include refining down to primitive actions and reasoning with abstract HLAs via angelic semantics.
  - Angelic semantics ensure provably correct abstract plans by considering reachable state sets for HLAs.
  - Further reading: [Erol, Hendler, and Nau, 1994](https://www.cs.umd.edu/~hjs/pubs/htnsurvey.pdf).

- **11.2.1 High-level Actions**
  - HLAs come with possible refinements into ordered sequences of actions.
  - Primitive actions have no further refinements by definition.
  - Implementations of HLAs can be recursively defined and evaluated for goal achievement.
  - The downward refinement property helps guarantee high-level plan correctness from primitive implementations.

- **11.2.2 Searching for Primitive Solutions**
  - HTN planning can be implemented via breadth-first search over plan refinements.
  - The search space expands over nested refinements rather than primitive action counts.
  - Hierarchies encode domain knowledge, reducing search complexity exponentially for well-structured HLAs.
  - Plan libraries enable reusing learned methods to build increasingly competent agents.

- **11.2.3 Searching for Abstract Solutions**
  - Angelic semantics use reachable sets to represent possible outcomes of HLAs, allowing reasoning without full refinement.
  - Optimistic and pessimistic reachable sets provide approximations to guarantee or disprove goal achievement.
  - The approach prunes search by committing to abstract plans that provably reach the goal.
  - Generalizations support hierarchical lookahead and online search, mirroring human planning processes.

- **11.3 Planning and Acting in Nondeterministic Domains**
  - Planning methods extend to partially observable, nondeterministic, or unknown environments.
  - Belief states represent uncertain world states, updated through action effects and percepts.
  - Three main planning approaches are sensorless (conformant), contingent, and online replanning agents.
  - Extended PDDL is used for modeling percepts and sensing schemas.
  - The topic relates to techniques reviewed in [Bertoli et al., 2001](https://link.springer.com/chapter/10.1007/3-540-44681-0_13).

- **11.3.1 Sensorless Planning**
  - Sensorless planning computes sequences that guarantee goal achievement without observations.
  - Belief states represented as conjunctions of literals remain compact under certain action types.
  - Conditional effects lead to more complex belief states requiring approximation or lazy evaluation.
  - Heuristic estimation for belief states can be composed from singleton physical states or planning graphs.

- **11.3.2 Contingent Planning**
  - Contingent plans include branches with conditional execution based on percepts received at runtime.
  - The agent updates belief states after sensing by incorporating observations and precondition entailments.
  - Search in belief-state space with nondeterministic actions is used to generate contingent plans.
  - Efficient contingent planning leverages algorithms from AND–OR graph search and SAT encoding.

- **11.3.3 Online Replanning**
  - Execution monitoring detects when plans fail due to nondeterminism, exogenous events, or incorrect models.
  - Three monitoring levels are: action monitoring, plan monitoring, and goal monitoring.
  - Plan repair involves finding a reachable state in the original plan to resume or replan from.
  - Robust agents incorporate learning to update models after unexpected outcomes.
  - For practice, see [Wilkins, 1988](https://dl.acm.org/doi/10.5555/16932).

- **11.4 Multiagent Planning**
  - Multiagent planning addresses problems involving multiple effectors, bodies, or autonomous agents.
  - Multiagent settings differ by degree of coupling and communication constraints.
  - Joint actions combine simultaneous actions by multiple actors, increasing branching factors exponentially.
  - Coordination and conventions help agents agree on joint plans to avoid conflicts.
  - Relevant survey: [Weiss, 2000](https://mitpress.mit.edu/books/multiagent-systems).

- **11.4.1 Planning with Multiple Simultaneous Actions**
  - Multiactor planning models actions as joint actions with concurrency constraints.
  - Concurrent action lists prohibit or require simultaneous actions by different actors.
  - Multiactor planning algorithms extend standard planners by handling concurrency constraints.
  - Loose coupling among actors enables approximate linear scaling of complexity with number of actors.

- **11.4.2 Planning with Multiple Agents: Cooperation and Coordination**
  - Cooperation among agents requires conventions, social laws, or communication to enforce coordination.
  - Plan recognition allows agents to infer others’ joint plans from observed actions.
  - Emergent multiagent behavior arises in social insects and boids models without explicit joint plans.
  - Competitive multiagent settings involve both cooperation on teams and opposition to others, demanding advanced planning techniques.

- **11.5 Summary**
  - Resource-aware planning incorporates consumable and reusable resources numerically.
  - Temporal planning integrates scheduling with action durations and deadlines.
  - HTN planning reduces complexity by encoding domain knowledge into hierarchical refinements.
  - Partial observability and nondeterminism demand belief state reasoning and contingent plans.
  - Online planning with monitoring and replanning supports robustness in stochastic or unknown domains.

- **Bibliographical and Historical Notes**
  - Historical developments in temporal planning and scheduling trace back to the 1980s and include systems like O-PLAN and NOPLIN+.
  - HTN planning emerged from early work on macro-operators and abstraction hierarchies in the 1970s.
  - Conformant and contingent planning methods evolved alongside advances in belief-state search and SAT-based encodings.
  - Online replanning and execution monitoring were pioneered on robots like Shakey and refined in later planners like SIPE.
  - Multiagent planning has a rich theoretical history and contemporary challenges in coordination and negotiation.
  - Recommended further reading includes [Erol et al., 1996](https://link.springer.com/chapter/10.1007/BFb0014054).
