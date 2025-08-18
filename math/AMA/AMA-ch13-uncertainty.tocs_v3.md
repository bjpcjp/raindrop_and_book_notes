![AMA-ch13-uncertainty](AMA-ch13-uncertainty.best.png)

- **13.1 Acting under Uncertainty**
  - Agents face uncertainty from partial observability, nondeterminism, or both, requiring belief states and contingency plans.
  - Logical methods struggle with uncertainty due to complexity, unlikely contingencies, and incomplete plans.
  - Probability theory provides degrees of belief as a solution to laziness and ignorance in domains like medical diagnosis.
  - Rational decisions depend on maximizing expected utility, incorporating preferences and probabilities.
  - Relevant reading: [Artificial Intelligence: A Modern Approach, Chapter 13](https://aima.cs.berkeley.edu/)

- **13.2 Basic Probability Notation**
  - Probability theory uses possible worlds (sample space) with associated numerical probabilities satisfying Kolmogorov’s axioms.
  - Propositions correspond to events, and probabilities of propositions sum over possible worlds where they hold.
  - Conditional probabilities express updated beliefs given evidence, defined in terms of unconditional probabilities.
  - Random variables generalize propositions with defined domains for representing uncertain facts.
  - Probability distributions and density functions represent numeric degrees of belief over discrete or continuous variables.
  - Relevant reading: [Kolmogorov’s Axioms](https://plato.stanford.edu/entries/probability-training/)

- **13.3 Inference Using Full Joint Distributions**
  - The full joint distribution specifies probabilities for all variable assignments but scales exponentially and is impractical for large domains.
  - Probabilistic inference uses marginalization (summing out variables) and conditioning with normalization to compute posteriors.
  - The principle of maximum likelihood and normalization shortcuts enable calculation of conditional probabilities without explicit denominator values.
  - Relevant reading: [Probabilistic Inference and Marginalization](https://web.stanford.edu/~jurafsky/slp3/A.pdf)

- **13.4 Independence**
  - Independence asserts that one event’s probability is unaffected by knowledge of another, enabling factorization of joint distributions.
  - Absolute independence between large subsets is rare, but when present, drastically reduces complexity.
  - Larger joint distributions can decompose into products of smaller distributions when variables are independent.
  - Relevant reading: [Independence in Probability Theory](https://www.probabilitycourse.com/chapter3/3_2_1_independence.php)

- **13.5 Bayes’ Rule and Its Use**
  - Bayes’ rule transforms causal conditional probabilities into diagnostic probabilities and vice versa.
  - The rule requires knowledge of priors and conditional probabilities but is robust to changes in priors unlike direct diagnostic probability estimation.
  - Combining multiple pieces of evidence uses conditional independence to factor joint probabilities for tractability.
  - Naive Bayes models assume conditional independence of effects given a cause and grow linearly with evidence.
  - Relevant reading: [Bayesian Inference and Naive Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier)

- **13.6 The Wumpus World Revisited**
  - Probabilistic reasoning improves on logical reasoning in partially observable environments by calculating pit probabilities.
  - Complete joint distributions decompose using independence and conditional independence into prior pit probabilities and conditional breeze probabilities.
  - Summation over frontier variables (adjacent unknowns) and normalization yield tractable computation of pit likelihood.
  - Probabilistic agents can assess relative risk of locations and make better decisions than logical agents.
  - Relevant reading: [AI: The Wumpus World Example](https://ai.stanford.edu/~nilsson/OnlinePubs-Nils/General%20Essays/WumpusWorld.pdf)

- **13.7 Summary**
  - Probability theory addresses uncertainty stemming from ignorance and laziness through degrees of belief consistent with axioms.
  - Combining probability theory with utility theory forms decision theory, supporting rational action selection by expected utility maximization.
  - Full joint distributions enable exact inference but are impractical; independence and conditional independence provide essential scalability.
  - Bayes’ rule facilitates inference from causal knowledge; naive Bayes models exemplify effective conditional independence use.
  - Relevant reading: [Decision Theory in AI](https://plato.stanford.edu/entries/decision-theory/)
