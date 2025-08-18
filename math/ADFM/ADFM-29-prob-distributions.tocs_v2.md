- Probability Distributions Overview  
  The section summarizes families of probability distributions relevant to the book’s topics. Distributions are represented by probability mass or density functions, with parameters governing their forms. The section notes implementations in Distributions.jl and illustrates how parameters influence distributions through plots. For further reading, see the [Distributions.jl Paper](https://arxiv.org/abs/1907.08611).

- Uniform Distribution  
  This distribution is defined by lower bound \(a\) and upper bound \(b\), with probability \(p(x) = \frac{1}{b - a}\) for \(x \in (a, b)\). Examples show multiple parameter settings influencing the uniform density shape. The distribution is univariate and serves as a baseline for comparison. Refer to the [Uniform Distribution - Wikipedia](https://en.wikipedia.org/wiki/Uniform_distribution_(continuous)) for more details.

- Gaussian (Univariate) Distribution  
  The univariate Gaussian distribution is parameterized by mean \(\mu\) and variance \(\sigma^2\), with pdf \(p(x) = \frac{1}{\sigma} \phi\left(\frac{x-\mu}{\sigma}\right)\) where \(\phi\) is the standard normal pdf. Parameter variations show effects on location and spread. It is defined over \(\mathbb{R}\) and fundamental in probabilistic modeling. For deeper understanding, consult the [Normal Distribution - Britannica](https://www.britannica.com/science/normal-distribution).

- Beta Distribution  
  The Beta distribution depends on positive shape parameters \(\alpha\) and \(\beta\), with pdf \(p(x) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} x^{\alpha - 1} (1-x)^{\beta - 1}\) for \(x \in (0,1)\). Parameter settings demonstrate diverse shape profiles within the unit interval, useful in modeling proportions. See the [Beta Distribution - Wikipedia](https://en.wikipedia.org/wiki/Beta_distribution) for comprehensive insights.

- Gaussian (Multivariate) Distribution  
  This multivariate Gaussian uses mean vector \(\mu \in \mathbb{R}^n\) and covariance matrix \(\Sigma\), with density \(p(x) = \frac{1}{(2\pi)^{n/2}|\Sigma|^{1/2}} \exp\left(-\frac{1}{2}(x - \mu)^T \Sigma^{-1} (x-\mu)\right)\). Illustrated examples reveal how different \(\mu\) and \(\Sigma\) affect shape and orientation in \(\mathbb{R}^n\). It handles multiple correlated variables. Consult [Multivariate Normal Distribution - Wikipedia](https://en.wikipedia.org/wiki/Multivariate_normal_distribution) for further study.

- Dirichlet Distribution  
  The Dirichlet distribution is governed by concentration parameters \(\alpha_i > 0\), with pdf \(p(x) = \frac{\Gamma(\alpha_0)}{\prod_i \Gamma(\alpha_i)} \prod_i x_i^{\alpha_i - 1}\) where \(\alpha_0 = \sum_i \alpha_i\) and the \(x_i\) sum to 1 within (0,1). Examples with different \(\alpha\) vectors show varied shapes useful for modeling probabilities over simplex spaces. For more, see [Dirichlet Distribution - Wikipedia](https://en.wikipedia.org/wiki/Dirichlet_distribution).
