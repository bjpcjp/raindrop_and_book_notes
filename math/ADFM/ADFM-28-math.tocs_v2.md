- **A.1 Measure Spaces**
  - A sigma-algebra over a set Ω is a collection of subsets closed under complementation, countable unions, and contains Ω.
  - A measure space consists of Ω, a sigma-algebra Σ, and a measure µ satisfying non-negativity, measure of empty set zero, and countable additivity on disjoint sets.
  - For more on measure theory, see [Measure Theory by Paul Halmos](https://link.springer.com/book/10.1007/978-1-4757-5645-5).

- **A.2 Probability Spaces**
  - A probability space is a measure space with the additional requirement that the measure of the entire set Ω is 1.
  - The components are named sample space (Ω), event space (Σ), and probability measure (µ or P).
  - The properties follow the Kolmogorov axioms combining measure properties with µ(Ω) = 1.
  - Refer to [Kolmogorov's Foundations of the Theory of Probability](https://archive.org/details/FoundationsOfTheTheoryOfProbability).

- **A.3 Metric Spaces**
  - A metric space consists of a set X with a distance function d mapping pairs of elements to non-negative reals.
  - The metric satisfies identity of indiscernibles, symmetry, and the triangle inequality.
  - See [Metric Spaces by Mícheál Ó Searcóid](https://www.springer.com/gp/book/9781852339317) for details.

- **A.4 Normed Vector Spaces**
  - Normed vector spaces have a norm function mapping vectors to non-negative reals, zero only at the zero vector, absolutely homogeneous, and obeying the triangle inequality.
  - Lp norms are parameterized by p ≥ 1, including L1 (taxicab), L2 (Euclidean), and L∞ (max norm).
  - Norms induce metrics by defining d(x, y) = ||x - y||.
  - For foundational knowledge, see [Functional Analysis by Walter Rudin](https://www.springer.com/gp/book/9780070542361).

- **A.5 Positive Definiteness**
  - A symmetric matrix A is positive definite if xᵀAx > 0 for all nonzero x; positive semidefinite if xᵀAx ≥ 0.
  - Positive definiteness ensures certain matrix properties relevant in optimization and numerical methods.
  - See [Matrix Analysis by Roger Horn and Charles Johnson](https://www.cambridge.org/core/books/matrix-analysis/46C1842191F055A9165F90E58B9A7D6D).

- **A.6 Convexity**
  - Convex combinations are weighted sums of vectors with nonnegative weights summing to one.
  - A convex set contains all convex combinations of its points.
  - A function is convex on a convex set if for all x, y and α in [0, 1], f(αx + (1 − α)y) ≤ αf(x) + (1 − α)f(y).
  - Strict convexity requires strict inequality for α in (0, 1).
  - See [Convex Optimization by Boyd and Vandenberghe](https://web.stanford.edu/~boyd/cvxbook/).

- **A.7 Information Content**
  - Information content I(x) of observing a value x with probability P(x) is −log P(x).
  - The logarithm base determines units, usually natural logs (nats) or base 2 (bits).
  - Information content measures the minimal bits required to encode value x under ideal coding.
  - See [Shannon's original paper](https://ieeexplore.ieee.org/document/6773024).

- **A.8 Entropy**
  - Entropy H(X) is the expected information content of a discrete variable: H(X) = −∑ P(x) log P(x).
  - Differential entropy h(X) extends this to continuous densities.
  - Entropy quantifies uncertainty inherent in a distribution.
  - Additional reading: [Information Theory, Inference, and Learning Algorithms by David MacKay](http://www.inference.org.uk/itila/).

- **A.9 Cross Entropy**
  - Cross entropy H(P, Q) measures expected information content when using distribution Q to encode samples from P.
  - Defined as −∑ P(x) log Q(x) for discrete, with an integral form for continuous cases.
  - Cross entropy is used in machine learning loss functions.
  - For details, see [Elements of Information Theory by Cover and Thomas](https://www.wiley.com/en-us/Elements+of+Information+Theory%2C+2nd+Edition-p-9780471241959).

- **A.10 Relative Entropy**
  - Relative entropy or KL divergence DKL(P||Q) measures difference between distributions P and Q.
  - Defined as ∑ P(x) log (P(x)/Q(x)), only when support of P is contained in Q's support.
  - Used extensively in statistics and machine learning to measure distribution discrepancy.
  - See [Kullback and Leibler's original work](https://www.amazon.com/Information-Theory-Statistics-Solomon-Kullback/dp/0486445492).

- **A.11 Gradient Ascent**
  - Gradient ascent iteratively updates x by moving in the direction of the gradient to maximize a differentiable function f(x).
  - Step factor α controls step size; decay of α can be applied to improve convergence.
  - Widely used in optimization and machine learning.
  - See [Convex Optimization by Boyd and Vandenberghe](https://web.stanford.edu/~boyd/cvxbook/) for convergence discussion.

- **A.12 Taylor Expansion**
  - Taylor expansion represents a function locally as an infinite sum of polynomial terms based on its derivatives at a point.
  - Linear and quadratic approximations use the first two or three terms.
  - The multivariate version applies gradients and Hessians.
  - See [Advanced Calculus by Patrick M. Fitzpatrick](https://www.worldcat.org/title/advanced-calculus/oclc/799090570) for deeper insight.

- **A.13 Monte Carlo Estimation**
  - Monte Carlo estimation approximates expected values by averaging function evaluations on samples drawn from the target distribution.
  - The variance decreases inversely with the number of samples.
  - Useful when analytic integration is intractable.
  - See [Monte Carlo Methods in Financial Engineering by Paul Glasserman](https://www.springer.com/gp/book/9780387004518).

- **A.14 Importance Sampling**
  - Importance sampling estimates expectations over p by sampling from an alternative distribution q, weighting samples by p(x)/q(x).
  - Enables variance reduction or sampling when direct sampling from p is difficult.
  - Requires q to have support covering p.
  - For further reading, see [Monte Carlo Statistical Methods by Robert and Casella](https://link.springer.com/book/10.1007/978-1-4757-4145-2).

- **A.15 Contraction Mappings**
  - A contraction mapping f on a metric space reduces distances between points by a factor α < 1.
  - The Banach fixed-point theorem guarantees a unique fixed point and convergence of repeated application.
  - Demonstrated with a specific R² example and Euclidean norm.
  - See [Functional Analysis by Walter Rudin](https://www.springer.com/gp/book/9780070542361) for contraction mapping theorem.
