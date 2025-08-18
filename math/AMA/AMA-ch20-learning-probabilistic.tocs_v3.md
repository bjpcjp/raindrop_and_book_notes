![AMA-ch20-learning-probabilistic](AMA-ch20-learning-probabilistic.best.png)

- **20.1 Statistical Learning**
  - Bayesian learning formulates learning as probabilistic inference using Bayes’ rule to update hypotheses probabilities based on observed data.
  - Predictions combine all hypotheses weighted by their posterior probabilities rather than relying on a single best hypothesis.
  - Maximum a posteriori (MAP) learning selects the most probable hypothesis and serves as a tractable approximation of full Bayesian learning.
  - Maximum likelihood (ML) learning maximizes the likelihood of data under hypotheses, equivalent to MAP with a uniform prior.
  - Overfitting is controlled via hypothesis priors, which penalize complexity, reflecting Ockham’s razor; see [Bayesian Probability](https://en.wikipedia.org/wiki/Bayesian_probability).

- **20.2 Learning with Complete Data**
  - Parameter learning estimates numerical parameters for fixed-structure probability models, particularly Bayesian networks, using complete data.
  - Maximum-likelihood estimation involves maximizing the likelihood or log likelihood and yields closed-form solutions for discrete and continuous models.
  - Naive Bayes models assume conditional independence of attributes given the class and are effective scalable learners with closed-form ML solutions.
  - Bayesian parameter learning uses conjugate priors (e.g., Beta distributions) to update distributions over parameters continuously, avoiding zero probabilities.
  - Structure learning searches over network structures optimizing fit versus complexity using MAP or Bayesian model selection; nonparametric methods estimate densities without fixed parameterizations.
  - Nonparametric density estimation methods include k-nearest-neighbors and kernel density estimation with Gaussian kernels; cross-validation selects smoothing parameters.
  - For further reading see [Pattern Recognition and Machine Learning (Bishop, 2006)](https://www.microsoft.com/en-us/research/people/cmbishop/prml-book/).

- **20.3 Learning with Hidden Variables: The EM Algorithm**
  - The EM algorithm iteratively computes expected values of hidden variables (E-step) and maximizes parameters (M-step) to handle incomplete data scenarios.
  - EM is applied to unsupervised clustering by estimating mixture weight and component parameters in mixture of Gaussians models.
  - EM generalizes to Bayesian networks with hidden variables, updating parameters using expected sufficient statistics derived via inference.
  - Learning hidden Markov models (HMMs) via EM uses forward-backward algorithm for computing required posterior distributions for state transitions.
  - Structural EM extends EM to learn Bayesian network structures with hidden variables, alternating between inference and structure/parameter optimization.
  - EM guarantees non-decreasing likelihood and converges to local maxima but not necessarily global optimum; initialization and priors help avoid degeneracies.
  - See [Dempster, Laird, and Rubin (1977)](https://projecteuclid.org/euclid.aos/1176344552) for foundational EM algorithm theory.

- **20.4 Summary**
  - Bayesian learning formulates inference as probabilistic update of hypotheses; MAP and ML provide computationally feasible approximations.
  - Maximum-likelihood estimation is tractable for several models, including naive Bayes and linear regression.
  - EM algorithm enables learning with hidden variables in mixture models, Bayesian networks, and HMMs.
  - Bayesian network structure learning involves model selection balancing complexity and fit.
  - Nonparametric methods estimate density with growing parameter counts and include nearest-neighbor and kernel methods.
  - For recent advances, consult [Statistical Learning: A Bayesian Perspective](https://www.cambridge.org/core/books/statistical-learning/45E1521B299C14398DB3F122EC1B3B7E).

- **Bibliographical and Historical Notes**
  - The chapter consolidates work from AI, statistics, and pattern recognition with Bayesian statistics resurgence post-1980s.
  - Naive Bayes models date to the 1950s; boosting and Bayesian network structure learning have evolved significantly.
  - EM algorithm was formalized by Dempster, Laird, and Rubin (1977); prior related work includes Baum–Welch for HMMs.
  - Structural EM and Bayesian network parameter learning have advanced, though full structure learning with hidden variables remains difficult.
  - Nonparametric methods originate from Rosenblatt (1956), and Dirichlet-process approaches enable flexible mixture modeling.
  - For comprehensive treatments, see [Bayesian Data Analysis](https://www.stat.columbia.edu/~gelman/book/) by Gelman et al., and [Machine Learning: A Probabilistic Perspective](https://mitpress.mit.edu/books/machine-learning) by Murphy.

- **Exercises**
  - Exercises cover application of Bayesian and ML theory to candy-flavor hypotheses, decision making, boosting naive Bayes, linear Gaussian parameter estimation, noisy-OR model learning, Beta distribution properties, and EM algorithm behavior.
  - Include derivations, proofs of likelihood properties, and model construction for classification and mixture models.
  - Exercises illustrate practical aspects including prior influences, likelihood maximization, clustering parameter updates, and hidden variable effects on learning.
  - Designed for in-depth understanding of theoretical and algorithmic implications related to probabilistic model learning.
