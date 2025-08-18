- **3 Inference**
  - Inference computes distributions over unobserved variables given observed evidence.
  - It distinguishes query variables, evidence variables, and hidden variables within Bayesian networks.
  - Exact inference methods can be computationally intractable for large or complex networks.
  - Approximate inference algorithms address computational challenges of exact methods.

- **3.1 Inference in Bayesian Networks**
  - Exact inference uses the chain rule, marginalization, and conditioning on evidence to compute posteriors.
  - Factors represent discrete multivariate distributions and are manipulated via factor product, marginalization, and conditioning.
  - Algorithm 3.4 performs exact inference by factor product, evidence conditioning, marginalizing hidden variables, and normalization.
  - Factor product size can grow exponentially with variable domain sizes, limiting practicality.

- **3.2 Inference in Naive Bayes Models**
  - Naive Bayes models assume conditional independence of features given the class.
  - Joint distribution decomposes as the prior over the class times product of class-conditional likelihoods.
  - Posterior inference involves normalizing joint class-feature probabilities.
  - Classification often selects the class with maximum posterior probability but decision theory may adjust based on misclassification costs.

- **3.3 Sum-Product Variable Elimination**
  - Variable elimination interleaves summations and factor products to eliminate hidden variables efficiently.
  - The ordering of variable elimination affects computational complexity.
  - Algorithm 3.5 implements sum-product variable elimination, updating factors as variables are marginalized.
  - Finding an optimal elimination order is NP-hard, making heuristics necessary for large networks.

- **3.4 Belief Propagation**
  - Belief propagation performs inference by passing messages between nodes in networks without undirected cycles.
  - It yields exact solutions on tree-structured networks and approximate solutions otherwise.
  - Junction tree algorithms convert networks with loops into tree structures at the cost of increased variable combinations.
  - Loopy belief propagation provides approximate inference without guarantees but often works well in practice.
  - For further reading, see [Factor Graphs and the Sum-Product Algorithm](https://ieeexplore.ieee.org/document/910572).

- **3.5 Computational Complexity**
  - Inference in Bayesian networks is NP-hard via reduction from the 3SAT problem.
  - The constructed Bayesian network models 3SAT variables and clauses, encoding satisfiability in probabilities.
  - This complexity result motivates the study of approximate inference methods.
  - For complexity background, see [The Computational Complexity of Probabilistic Inference Using Bayesian Belief Networks](https://www.aaai.org/Papers/AI/1990/AI90-035.pdf).

- **3.6 Direct Sampling**
  - Direct sampling draws independent samples from the joint distribution to estimate posterior probabilities.
  - Samples inconsistent with evidence are discarded, reducing efficiency when evidence is rare.
  - Topological sorting ensures sampling parents before children.
  - Algorithm 3.7 implements direct sampling by filtering samples consistent with evidence.
  - For foundational concepts, see [Randomized Algorithms](https://doi.org/10.1017/CBO9780511809071).

- **3.7 Likelihood Weighted Sampling**
  - Likelihood weighting generates samples consistent with evidence and assigns weights reflecting observation likelihoods.
  - It assigns observed variables their evidence values and multiplies the sample weight by the likelihood from conditional distributions.
  - Algorithm 3.8 implements likelihood weighted sampling to produce weighted estimates.
  - While it reduces sample wastage, it can still be inefficient for very unlikely evidence due to weight variance.

- **3.8 Gibbs Sampling**
  - Gibbs sampling is a Markov chain Monte Carlo method generating correlated samples consistent with evidence.
  - Each unobserved variable is resampled conditioned on current values of all other variables (its Markov blanket).
  - Algorithm 3.10 implements Gibbs sampling with burn-in and thinning to reduce sample correlation.
  - Gibbs sampling converges asymptotically to the true posterior distribution.
  - For detailed discussion, see [Bayesian Reasoning and Machine Learning](http://www.cs.ucl.ac.uk/staff/D.Barber/BayesBook/).

- **3.9 Inference in Gaussian Models**
  - Joint Gaussian variables allow exact, closed-form marginal and conditional distributions.
  - The conditional mean and covariance have explicit matrix formulas involving inversion of covariance submatrices.
  - Algorithm 3.11 performs Gaussian inference given query variables and evidence.
  - Multivariate Gaussian inference is efficient and avoids combinatorial explosion of discrete factors.
  - The [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) package implements MvNormal distributions.

- **3.10 Summary**
  - Exact inference requires joint probability computation and marginalization but may be inefficient.
  - Variable elimination and belief propagation improve efficiency depending on network structure.
  - Inference can be reduced to NP-hard problems; approximate methods mitigate computational constraints.
  - Sampling-based approximate inference methods include direct, likelihood weighted, and Gibbs sampling.
  - Gaussian models allow exact inference through linear algebra operations.

- **3.11 Exercises**
  - Exercises address formulating exact inference equations for given Bayesian network queries.
  - Problems focus on naive Bayes classification, Bayesian network construction from 3SAT, and topological sorting.
  - Additional exercises involve likelihood-weighted sampling and conditional Gaussian inference.
  - Solutions demonstrate application of core inference formulas and algorithms discussed.
  - For practice problems in probabilistic graphical models, refer to [Probabilistic Graphical Models Specialization](https://www.coursera.org/specializations/probabilistic-graphical-models).
