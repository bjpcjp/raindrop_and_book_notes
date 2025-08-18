- Preface  
  The Preface introduces the purpose and scope of the book, outlining its focus on decision making and probabilistic reasoning. It frames the foundational concepts and approaches explored throughout the text, setting context for subsequent chapters. For further foundational context, see [Introduction to Decision Making](https://plato.stanford.edu/entries/decision-theory/).

- Acknowledgments  
  This section credits individuals and organizations contributing to the development and refinement of the book. It acknowledges the collaborative and interdisciplinary nature influencing the book's comprehensive coverage. For insights into academic collaboration, refer to [The Nature of Scientific Collaboration](https://royalsocietypublishing.org/doi/full/10.1098/rsos.161136).

- 1 Introduction  
  - 1.1 Decision Making  
    This subsection defines decision making as a process of choosing among alternatives under uncertainty. It highlights foundational theories distinguishing rational preferences and their formal representation. Related foundational principles are detailed in [Decision Theory](https://plato.stanford.edu/entries/decision-theory/).  
  - 1.2 Applications  
    This part details real-world applications of decision-making methods across various domains including robotics, economics, and AI. The causal influence of domain-specific challenges shapes method selection and adaptation. See [Applications of Decision Analysis](https://pubsonline.informs.org/doi/10.1287/educ.1070.0001) for more.  
  - 1.3 Methods  
    Methods discussed include probabilistic modeling, utility theory, and computational algorithms facilitating decision-making under uncertainty. The integration of these methods stems from theoretical and empirical advancements. More on methodology is available at [Decision Making Methods](https://www.sciencedirect.com/topics/computer-science/decision-making-methods).  
  - 1.4 History  
    The history section traces the evolution of decision theory from early philosophical roots to modern algorithmic frameworks. Influential figures and paradigm shifts are identified, shaping current approaches. Detailed history can be found in [A History of Decision Theory](https://www.cambridge.org/core/journals/journal-of-economic-perspectives/article/history-of-decision-theory/3340F6271EE4CA42A832EF8B525C1DB0).  
  - 1.5 Societal Impact  
    This subsection examines how decision theory advances impact society, influencing policy, ethics, and technology deployment. Challenges arising from societal complexity critically inform research directions. For expanded discussion, see [Societal Implications of AI](https://aitopics.org/doc/news/NSF-societal-implications).  
  - 1.6 Overview  
    Provides a roadmap of the book’s structure, summarizing key topics and their interrelations from probabilistic reasoning through multiagent systems. The overview establishes thematic continuity and sets expectations. For pedagogical context, consult [How to Write a Book Overview](https://writingcenter.unc.edu/tips-and-tools/book-reports/).

- I Probabilistic Reasoning  
  - 2 Representation  
    - 2.1 Degrees of Belief and Probability  
      This subsection explains degrees of belief as subjective probabilities quantifying uncertainty. It presents probability axioms as the foundation for coherent reasoning under uncertainty. Key impacts arise from mathematical rigor aligning belief with measurable uncertainty. Explore foundational concepts at [Probability Theory](https://plato.stanford.edu/entries/probability-theory/).  
    - 2.2 Probability Distributions  
      Discusses the formal definition and properties of probability distributions that describe random variable behavior. Variability in distribution types influences modeling choices and inference. For further detail, see [Probability Distributions Overview](https://www.statisticshowto.com/probability-distributions/).  
    - 2.3 Joint Distributions  
      Joint distributions represent combined probabilities over multiple variables capturing dependencies. Conditioning and marginalization emerge as critical operations. This interplay affects computational feasibility. See [Joint Probability Distributions](https://www.khanacademy.org/math/statistics-probability/probability-library).  
    - 2.4 Conditional Distributions  
      Conditional distributions express probabilities given known events, enabling updated beliefs. The core factor is the application of Bayes' theorem formalizing inference. More on conditionals at [Conditional Probability](https://www.britannica.com/science/conditional-probability).  
    - 2.5 Bayesian Networks  
      Bayesian networks model complex joint distributions via directed acyclic graphs encoding conditional independencies. Their structure simplifies inference and learning by exploiting factorization. For technical details, see [Bayesian Networks Tutorial](https://www.cs.ubc.ca/~murphyk/Bayes/bnintro.html).  
    - 2.6 Conditional Independence  
      Introduces conditional independence as a fundamental property enabling simplification of joint distributions and efficient computation. It shapes network structure and inference algorithms. For mathematical grounding, review [Conditional Independence](https://en.wikipedia.org/wiki/Conditional_independence).  
    - 2.7 Summary  
      Summarizes the role of probabilistic representations in capturing uncertainty and enabling algorithmic reasoning. Emphasizes interplay between structure and probability calculus.  
    - 2.8 Exercises  
      Provides practice problems to reinforce understanding of representation concepts, including probabilistic reasoning and Bayesian network structures.

  - 3 Inference  
    - 3.1 Inference in Bayesian Networks  
      Details algorithms to compute posterior probabilities given evidence using network structure, including exact and approximate methods. Complexity constraints shape method applicability. Reference [Probabilistic Inference](https://web.stanford.edu/class/cs228/).  
    - 3.2 Inference in Naive Bayes Models  
      Explains simplified inference by assuming conditional independence of features, enabling efficient computation despite high-dimensional data. The model’s assumptions guide usage scenarios. See [Naive Bayes Classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier).  
    - 3.3 Sum-Product Variable Elimination  
      Introduces an exact inference algorithm exploiting distributive law to compute marginals efficiently by eliminating variables. Algorithmic efficiency depends on graph structure. More at [Variable Elimination](https://web.stanford.edu/class/cs228/handouts/variable_elimination.pdf).  
    - 3.4 Belief Propagation  
      Describes iterative message passing for exact inference on trees and approximate inference on graphs with cycles. Its performance links to graph topology. See [Belief Propagation Algorithms](https://people.eecs.berkeley.edu/~pabbeel/cs287-fa10/readings/pearl1988.pdf).  
    - 3.5 Computational Complexity  
      Analyzes the computational difficulty of inference, establishing that exact inference is often NP-hard. Graph structure influences tractability. See complexity results at [Complexity of Probabilistic Inference](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.11.4556).  
    - 3.6 Direct Sampling  
      Describes basic Monte Carlo methods to approximate distributions by sampling from the joint distribution directly, limited by high-dimensional spaces. Sampling efficiency is influenced by variable dependencies. For an introduction, see [Monte Carlo Methods](https://en.wikipedia.org/wiki/Monte_Carlo_method).  
    - 3.7 Likelihood Weighted Sampling  
      Introduces an importance sampling method that weights samples by likelihood to handle evidence, improving sample efficiency. Its effectiveness depends on evidence incorporation strategy. See [Likelihood Weighting](https://web.stanford.edu/class/cs228/handouts/Inference.pdf).  
    - 3.8 Gibbs Sampling  
      Explains Markov Chain Monte Carlo sampling by iteratively sampling variables conditioned on others, enabling approximate inference in complex models. Convergence depends on mixing properties. See [Gibbs Sampling](https://projecteuclid.org/euclid.aos/1176344076).  
    - 3.9 Inference in Gaussian Models  
      Covers exact inference in models with continuous variables assuming Gaussian distributions, leveraging conjugacy and analytical solutions. Underlying linearity and Gaussian assumptions enable closed-form computations. Details at [Gaussian Processes](http://www.gaussianprocess.org/gpml/).  
    - 3.10 Summary  
      Summarizes inference techniques ranging from exact algorithms to sampling methods, highlighting trade-offs between precision and scalability.  
    - 3.11 Exercises  
      Offers problems to practice inference methods including message passing, sampling, and Gaussian reasoning.

  - 4 Parameter Learning  
    - 4.1 Maximum Likelihood Parameter Learning  
      Describes estimation of model parameters by maximizing data likelihood under assumed models, foundational in statistical learning. Availability and completeness of data influence estimates. For fundamentals, see [MLE Introduction](https://en.wikipedia.org/wiki/Maximum_likelihood_estimation).  
    - 4.2 Bayesian Parameter Learning  
      Presents methods incorporating prior distributions over parameters to update beliefs with data, providing regularization and uncertainty quantification. Priors and likelihoods determine posterior forms. See [Bayesian Learning](https://en.wikipedia.org/wiki/Bayesian_inference).  
    - 4.3 Nonparametric Learning  
      Introduces flexible learning methods without fixed parameter dimension, allowing model complexity to grow with data. Causal necessity arises from unknown or complex model structure. See [Nonparametric Models](https://en.wikipedia.org/wiki/Nonparametric_statistics).  
    - 4.4 Learning with Missing Data  
      Explores algorithms handling incomplete or partially observed data, such as Expectation-Maximization, to infer parameters. Missingness patterns critically affect method design. Refer to [EM Algorithm](https://en.wikipedia.org/wiki/Expectation%E2%80%93maximization_algorithm).  
    - 4.5 Summary  
      Highlights parameter estimation strategies, their strengths, and contextual applicability related to data completeness and prior knowledge.  
    - 4.6 Exercises  
      Provides practical exercises to implement parameter learning in varied scenarios including missing data cases.

  - 5 Structure Learning  
    - 5.1 Bayesian Network Scoring  
      Describes scoring functions evaluating fit of candidate network structures to data, balancing complexity and likelihood. Model selection depends on scoring reliability. See [Bayesian Network Structure Learning](https://link.springer.com/article/10.1007/s10994-006-6222-y).  
    - 5.2 Directed Graph Search  
      Explains search algorithms in the space of directed graphs for optimal structure discovery. Search efficiency influenced by heuristic guidance. See survey at [Graph Search Methods](https://arxiv.org/abs/0909.1950).  
    - 5.3 Markov Equivalence Classes  
      Identifies equivalence classes of network structures yielding identical conditional independencies, reducing redundancy in search. Recognizing equivalence aids efficient model selection. For details, see [Markov Equivalence](https://arxiv.org/abs/1110.0916).  
    - 5.4 Partially Directed Graph Search  
      Discusses search strategies incorporating both directed and undirected edges to represent uncertainty in causality, aiding model identifiability. Further reading at [Causal Discovery Algorithms](https://ftp.cs.ucla.edu/pub/stat_ser/r268.pdf).  
    - 5.5 Summary  
      Summarizes structural learning as combining scoring and search, constrained by equivalence and computational complexity.  
    - 5.6 Exercises  
      Contains problems to deepen understanding of structure scoring, search heuristics, and equivalence concepts.

  - 6 Simple Decisions  
    - 6.1 Constraints on Rational Preferences  
      Details axiomatic foundations restricting rational preference relations, such as completeness and transitivity, forming decision theory basis. Violations affect decision consistency. For axioms, see [Von Neumann–Morgenstern Utility Theorem](https://plato.stanford.edu/entries/decision-theory/#VonNeuMorThe).  
    - 6.2 Utility Functions  
      Defines utility functions as numerical representations of preferences, enabling quantitative decision analysis. Utility scales are construction-dependent and fundamental to expected utility theory. See [Utility Theory](https://en.wikipedia.org/wiki/Utility_theory).  
    - 6.3 Utility Elicitation  
      Covers methods to derive utilities from preferences including direct rating, lotteries, and elicitation protocols. Quality depends on elicitation accuracy and user understanding. See [Utility Assessment](https://www.sciencedirect.com/science/article/pii/S0377221797000297).  
    - 6.4 Maximum Expected Utility Principle  
      Introduces the principle choosing actions maximizing expected utility, providing a normative standard for rational choice. Assumes known probability and utility functions. Related resource: [Expected Utility](https://plato.stanford.edu/entries/rationality/#ExpecUtilPrin).  
    - 6.5 Decision Networks  
      Describes graphical representations combining probabilistic and utility models to analyze complex decision problems effectively. Integration facilitates computation and interpretation. See [Decision Networks](https://en.wikipedia.org/wiki/Influence_diagram).  
    - 6.6 Value of Information  
      Explores how acquiring information influences decision quality by modifying expected utility, guiding information-gathering strategies. Value depends on cost and impact on outcomes. See [Value of Information Analysis](https://en.wikipedia.org/wiki/Value_of_information).  
    - 6.7 Irrationality  
      Discusses deviations from rational decision criteria including biases and paradoxes that challenge classical theory. Understanding these informs more descriptive models. See [Behavioral Decision Theory](https://www.annualreviews.org/doi/full/10.1146/annurev.psych.55.090902.142015).  
    - 6.8 Summary  
      Summarizes foundations of decision theory emphasizing utility, rationality, and computational representations.  
    - 6.9 Exercises  
      Exercises focus on applications and implications of rational choice axioms, utility functions, and decision network analysis.
