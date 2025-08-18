- **Preface**
  - The book introduces algorithms for optimal decision making under uncertainty.
  - It assumes prior knowledge of calculus, linear algebra, and probability.
  - Algorithms are implemented in Julia and freely available with attribution.
  - The book targets advanced undergraduates, graduate students, and professionals.
  - Ancillary materials are available at the book’s [webpage](http://mitpress.mit.edu/algorithms-for-decision-making).

- **Acknowledgments**
  - The textbook developed from a Stanford course on decision making under uncertainty.
  - Many individuals contributed feedback, student participation, and exercises.
  - The book’s style is influenced by Edward Tufte’s design principles.
  - Several open-source tools and packages support the book’s production.
  - The book uses the JuliaMono typeface and pgfplots for plotting.

- **1 Introduction**
  - **1.1 Decision Making**
    - Defines an agent interacting with the environment via an observe-act loop.
    - Identifies four sources of uncertainty: outcome, model, state, and interaction.
    - Emphasizes the importance of accounting for these uncertainties in decision making.
    - Rational decision making is central to artificial intelligence and other fields.
    - Further reading: [Russell and Norvig’s "Artificial Intelligence: A Modern Approach"](https://aima.cs.berkeley.edu/).

  - **1.2 Applications**
    - Illustrates applications in aircraft collision avoidance, automated driving, and breast cancer screening.
    - Highlights challenges such as uncertain pilot response and sensor noise.
    - Shows benefits of personalized screening and financial portfolio decision systems.
    - Describes distributed wildfire surveillance using autonomous drones.
    - References real-world studies and examples for each application.

  - **1.3 Methods**
    - Reviews explicit programming as a direct but burdensome approach.
    - Supervised learning uses expert examples but may not generalize well.
    - Optimization searches decision strategy space often via simulation.
    - Planning incorporates known models to guide search for decisions.
    - Reinforcement learning learns policies online without a prior model.

  - **1.4 History**
    - Traces decision making roots from ancient automata to modern AI.
    - Economics introduced utility theory and game theory foundations.
    - Psychology contributed theories of trial-and-error and reinforcement learning.
    - Neuroscience inspired neural network models of brains and logic units.
    - Computer science developed symbolic reasoning and connectionism.
    - Engineering focuses on robotics involving perception, planning, and control.
    - Mathematics underpins probabilistic reasoning, Bayesian statistics, and optimization.
    - Operations research developed algorithms like linear and dynamic programming.
    - Further reading: [Koopman’s "Search and Screening"](https://archive.org/details/searchscreening00kooprich).

  - **1.5 Societal Impact**
    - Decision algorithms contribute to energy management, biodiversity protection, and wildlife census.
    - Medical diagnosis and prognosis have benefited from Bayesian networks and deep learning.
    - Urban infrastructure and emergency response optimized using data-driven algorithms.
    - Algorithms can amplify intended and unintended social impacts, including misinformation.
    - Challenges remain to address bias, fairness, robustness, and moral responsibility.
    - Further reading: [Shi et al. "Artificial Intelligence for Social Good"](https://arxiv.org/abs/2001.01818).

  - **1.6 Overview**
    - Divides the book into five parts addressing uncertainty and decision making.
    - Part I covers probabilistic reasoning and utility theory for single-step decisions.
    - Part II discusses sequential decision problems under full observability and known models.
    - Part III addresses model uncertainty and reinforcement learning.
    - Part IV extends to state uncertainty and partially observable Markov decision processes.
    - Part V focuses on multiagent decision making and game-theoretic frameworks.

- **I Probabilistic Reasoning**
  - Explains the need to represent and reason about uncertainty for rational decisions.
  - Introduces probability distributions to capture uncertainty over variables.
  - Describes parameter and structure learning for probabilistic models.
  - Covers utility theory and decision networks as probabilistic graphical models integrated with preferences.

- **2 Representation**
  - **2.1 Degrees of Belief and Probability**
    - Defines plausibility relations between propositions using ordering operators.
    - Assumes universal comparability and transitivity to justify real-valued plausibility.
    - Shows that under additional assumptions, plausibility obeys probability axioms.
    - Probability values range from 0 (impossible) to 1 (certain).
    - Further reading: [Jaynes, Probability Theory: The Logic of Science](https://bayes.wustl.edu/etj/prob/book.pdf).

  - **2.2 Probability Distributions**
    - Distinguishes discrete distributions represented by probability mass functions summing to one.
    - Covers continuous distributions represented by probability density functions integrating to one.
    - Introduces cumulative distribution and quantile functions for continuous variables.
    - Describes common distribution families including uniform, Gaussian, truncated Gaussian, and mixture models.
    - Highlights advantages and limitations of Gaussian distributions, such as support and modality.
    - Further reading: [Bertsekas and Tsitsiklis, Introduction to Probability](http://athenasc.com/probbook.html).

  - **2.3 Joint Distributions**
    - Defines joint probability distributions over multiple variables.
    - Uses marginalization by summing or integrating over variables to compute marginal distributions.
    - Shows discrete joint distributions can be tabulated but scale exponentially with variables.
    - Independence assumptions enable factorization to reduce parameter requirements.
    - Introduces factors as functions over variable assignments and their use in representing distributions.
    - Notes decision trees as another compact representation exploiting repeated values.
    - Further reading: [Koller and Friedman, Probabilistic Graphical Models](https://probabilisticgraphicalmodels.org/).

- **Algorithm 2.1: Factor Type**
  - Implements discrete factors as tables mapping variable assignments to real values.
  - Uses named tuples for assignment representation.
  - Supports functions to list variable names and generate all assignments.
  - Designed to facilitate factor manipulation and probability computations.

- **Example 2.1: Uniform Distribution**
  - Defines uniform distribution U(0,10) with constant density within bounds and zero elsewhere.
  - Computes probability of intervals by integrating constant density.
  - Illustrates that the probability of any exact single value is zero for a continuous uniform distribution.

- **Example 2.2: Gaussian Mixture Model**
  - Constructs a mixture of two Gaussian components with specified means, variances, and weights.
  - Visualizes the mixture density along with individual weighted components.
  - Demonstrates how mixtures yield multimodal continuous distributions.

- **Table 2.1: Joint Distribution Table Example**
  - Presents a joint probability table for three binary variables with probabilities summing to one.
  - Notes the number of independent parameters is one less than the table entries.
  - Exemplifies exponential parameter growth in joint representations for multiple variables.

- **Table 2.2: Independent Joint Distribution Factorization**
  - Shows how joint distribution decomposes into a product of individual variable distributions when variables are independent.
  - Reduces parameters to one per variable for binary variables.
  - Demonstrates large representational savings with independence assumptions.
