<div class="nav">

⟵ [Up](index.html)  \|  [Index](index.html)

</div>

# survival-analysis

<div class="cards">

<div class="card">

<div class="card-title">

[High-Dimensional Survival Analysis: Techniques for Big Data in
Time-to-Event
Modeling](https://www.statology.org/high-dimensional-survival-analysis-techniques-for-big-data-in-time-to-event-modeling/)

</div>

<div class="card-image">

[![](https://www.statology.org/wp-content/uploads/2025/07/STA-Shittu-High-Dimensional-Survival-Analysis-Techniques-for-Big-Data-in-Time-to-Event-Modeling.png)](https://www.statology.org/high-dimensional-survival-analysis-techniques-for-big-data-in-time-to-event-modeling/)

</div>

In this article, we'll move past the textbook Cox model and look at how
regularized models, tree-based methods, and deep learning can help
survival analysis scale to meet real-world complexity.

</div>

<div class="card">

<div class="card-title">

[Survival Analysis: Techniques for Analyzing Time-to-Event
Data](https://www.statology.org/?p=55821)

</div>

<div class="card-image">

[![](https://www.statology.org/wp-content/uploads/2025/06/sta-davies-survival-analysis.png)](https://www.statology.org/?p=55821)

</div>

Survival analysis, primarily used for modeling time-to-event data,
provides an arsenal of statistical tools to estimate the expected time
until one or more events of interest, such as death, failure, or
attrition.

</div>

<div class="card">

<div class="card-title">

[Concise Guide to Survival
Analysis](https://www.statology.org/concise-guide-to-survival-analysis/)

</div>

<div class="card-image">

[![](https://www.statology.org/wp-content/uploads/2025/04/sta-concise-guide-survival-analysis.png)](https://www.statology.org/concise-guide-to-survival-analysis/)

</div>

So, if you’ve ever asked, “How long until X happens?” and wanted to back
that up with solid data, you’re in the right place.

</div>

<div class="card">

<div class="card-title">

[Learning curve: The Kaplan-Meier estimator \| The
Actuary](https://www.theactuary.com/2025/03/07/learning-curve-kaplan-meier-estimator)

</div>

<div class="card-image">

[![](https://www.theactuary.com/sites/default/files/styles/uncropped_small/public/2025-03/web_p30-31_Learning-curve_curved-tulip-flower_CREDIT_getty-546736123.jpg?itok=hnv7KvJT)](https://www.theactuary.com/2025/03/07/learning-curve-kaplan-meier-estimator)

</div>

The Kaplan-Meier survival curve estimator is one of the most cited ideas
in science

</div>

<div class="card">

<div class="card-title">

[Olivier Grisel - Predictive survival analysis with scikit-learn,
scikit-survival and
lifelines](https://m.youtube.com/watch?v=gke0hNQMdT8)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/gke0hNQMdT8/hqdefault.jpg)](https://m.youtube.com/watch?v=gke0hNQMdT8)

</div>

</div>

<div class="card">

<div class="card-title">

[A Practical Guide to Survival
Analysis](https://www.statology.org/practical-guide-survival-analysis/)

</div>

<div class="card-image">

[![](https://www.statology.org/wp-content/uploads/2025/01/sta-feature-20250127-04.png)](https://www.statology.org/practical-guide-survival-analysis/)

</div>

Survival analysis consists of statistical methods that help us
understand and predict how long it takes for an event to occur.

</div>

<div class="card">

<div class="card-title">

[Better A/B testing with survival
analysis](https://www.r-bloggers.com/2024/07/better-a-b-testing-with-survival-analysis)

</div>

<div class="card-image">

[![](https://www.r-bloggers.com/wp-content/uploads/2016/04/R_02_2016-05-01.png)](https://www.r-bloggers.com/2024/07/better-a-b-testing-with-survival-analysis)

</div>

Pic by author - using DALL-E 3 When running experiments don’t forget to
bring your survival kit I’ve already made the case in several blog posts
(part 1, part 2, part 3) that using survival analysis can improve churn
prediction. In this blog post I’ll ...

</div>

<div class="card">

<div class="card-title">

[Survival Analysis with
R](https://www.r-bloggers.com/survival-analysis-with-r-3)

</div>

<div class="card-image">

[![](https://rviews.rstudio.com/post/2017-05-05-survival-analysis-with-r-with-comments_files/figure-html/unnamed-chunk-4-1.png)](https://www.r-bloggers.com/survival-analysis-with-r-3)

</div>

With roots dating back to at least 1662 when John Graunt, a London
merchant, published an extensive set of inferences based on mortality
records, survival analysis is one of the oldest subfields of Statistics
\[1\]. Basic life-table methods, including techniques for dealing with
censored data, were discovered before 1700 \[2\], and in the early
eighteenth century, the old masters - de Moivre working on annuities,
and Daniel Bernoulli studying competing risks for the analysis of
smallpox inoculation - developed the modern foundations of the field
\[2\]. Today, survival analysis models are important in Engineering,
Insurance, Marketing, Medicine, and many more application areas. So, it
is not surprising that R should be rich in survival analysis functions.
CRAN’s Survival Analysis Task View, a curated list of the best relevant
R survival analysis packages and functions, is indeed formidable. We all
owe a great deal of gratitude to Arthur Allignol and Aurielien Latouche,
the task view maintainers. Looking at the Task View on a small screen,
however, is a bit like standing too close to a brick wall - left-right,
up-down, bricks all around. It is a fantastic edifice that gives some
idea of the significant contributions R developers have made both to the
theory and practice of Survival Analysis. As well-organized as it is,
however, I imagine that even survival analysis experts need some time to
find their way around this task view. Newcomers - people either new to R
or new to survival analysis or both - must find it overwhelming. So, it
is with newcomers in mind that I offer the following narrow trajectory
through the task view that relies on just a few packages: survival,
ggplot2, ggfortify, and ranger The survival package is the cornerstone
of the entire R survival analysis edifice. Not only is the package
itself rich in features, but the object created by the Surv() function,
which contains failure time and censoring information, is the basic
survival analysis data structure in R. Dr. Terry Therneau, the package
author, began working on the survival package in 1986. The first public
release, in late 1989, used the Statlib service hosted by Carnegie
Mellon University. Thereafter, the package was incorporated directly
into Splus, and subsequently into R. ggfortify enables producing
handsome, one-line survival plots with ggplot2::autoplot. ranger might
be the surprise in my very short list of survival packages. The ranger()
function is well-known for being a fast implementation of the Random
Forests algorithm for building ensembles of classification and
regression trees. But ranger() also works with survival data. Benchmarks
indicate that ranger() is suitable for building time-to-event models
with the large, high-dimensional data sets important to internet
marketing applications. Since ranger() uses standard Surv() survival
objects, it’s an ideal tool for getting acquainted with survival
analysis in this machine-learning age. Load the data This first block of
code loads the required packages, along with the veteran dataset from
the survival package that contains data from a two-treatment, randomized
trial for lung cancer. library(survival) library(ranger)
library(ggplot2) library(dplyr) library(ggfortify) \#------------
data(veteran) head(veteran) \## trt celltype time status karno diagtime
age prior \## 1 1 squamous 72 1 60 7 69 0 \## 2 1 squamous 411 1 70 5 64
10 \## 3 1 squamous 228 1 60 3 38 0 \## 4 1 squamous 126 1 60 9 63 10
\## 5 1 squamous 118 1 70 11 65 10 \## 6 1 squamous 10 1 20 5 49 0 The
variables in veteran are: \* trt: 1=standard 2=test \* celltype:
1=squamous, 2=small cell, 3=adeno, 4=large \* time: survival time in
days \* status: censoring status \* karno: Karnofsky performance score
(100=good) \* diagtime: months from diagnosis to randomization \* age:
in years \* prior: prior therapy 0=no, 10=yes Kaplan Meier Analysis The
first thing to do is to use Surv() to build the standard survival
object. The variable time records survival time; status indicates
whether the patient’s death was observed (status = 1) or that survival
time was censored (status = 0). Note that a “+” after the time in the
print out of km indicates censoring. \# Kaplan Meier Survival Curve km

</div>

<div class="card">

<div class="card-title">

[The Complete Introduction to Survival Analysis in Python \| by Marco
Peixeir](https://towardsdatascience.com/the-complete-introduction-to-survival-analysis-in-python-7523e17737e6)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*TGrU4kiM0nMnlz2M)](https://towardsdatascience.com/the-complete-introduction-to-survival-analysis-in-python-7523e17737e6)

</div>

Understand survival analysis, its use in the industry, and how to apply
it in Python

</div>

<div class="card">

<div class="card-title">

[What Is Survival Analysis? Examples by Hand and in
R](https://towardsdatascience.com/what-is-survival-analysis-examples-by-hand-and-in-r-3f0870c3203f?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*DJ0IXzqw6XtEV2nf)](https://towardsdatascience.com/what-is-survival-analysis-examples-by-hand-and-in-r-3f0870c3203f?source=rss----7f60cf5620c9---4)

</div>

Learn more about survival analysis (also called time-to-event analysis)
and how it is used, and how to apply it by hand and in R

</div>

<div class="card">

<div class="card-title">

[Survival Analysis: Optimize the Partial Likelihood of the Cox
Model](https://towardsdatascience.com/survival-analysis-optimize-the-partial-likelihood-of-the-cox-model-b56b8f112401)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:940/1*xRKLo6Q-Y9FogZ5wwIhpaA.png)](https://towardsdatascience.com/survival-analysis-optimize-the-partial-likelihood-of-the-cox-model-b56b8f112401)

</div>

Finding the coefficients that maximize the log-partial likelihood in
Python

</div>

<div class="card">

<div class="card-title">

[Survival Analysis in R (in under
10-minutes)](https://www.r-bloggers.com/2022/06/survival-analysis-in-r-in-under-10-minutes)

</div>

<div class="card-image">

[![](https://www.business-science.io/assets/survival_plots-2.jpg)](https://www.r-bloggers.com/2022/06/survival-analysis-in-r-in-under-10-minutes)

</div>

Making a survival analysis can be a challenge even for experienced R
users, but the good news is I’ll help you make beautiful,
publication-quality survival plots in under 10-minutes. Here’s what WE
are going to do: Make your first survival model an...

</div>

<div class="card">

<div class="card-title">

[How to Evaluate Survival Analysis
Models](https://link.medium.com/Rn4mYw62Fqb)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*DxCUurqG2FeWNZXsrqE-SA.png)](https://link.medium.com/Rn4mYw62Fqb)

</div>

Introduction to the most popular performance evaluation metrics for
survival analysis along with practical Python examples

</div>

<div class="card">

<div class="card-title">

[Survival Analysis: A Brief
Introduction](https://towardsdatascience.com/survival-analysis-a-brief-introduction-bdba3a275b5f)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*BHokUm8Y-3HwMbLA)](https://towardsdatascience.com/survival-analysis-a-brief-introduction-bdba3a275b5f)

</div>

An initial look into the method best suited for examining time-to-event
data

</div>

<div class="card">

<div class="card-title">

[Survival Analysis in Python: A Quick Guide to The Weibull
Analysis](https://towardsdatascience.com/survival-analysis-in-python-a-quick-guide-to-the-weibull-analysis-5babd4f137f6)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*ofcmBQ79oNJHD7RJ6ckxIw.png)](https://towardsdatascience.com/survival-analysis-in-python-a-quick-guide-to-the-weibull-analysis-5babd4f137f6)

</div>

A Quick Guide to The Weibull Analysis

</div>

<div class="card">

<div class="card-title">

[Introduction to Survival
Analysis](https://towardsdatascience.com/introduction-to-survival-analysis-in-cows-using-r-28b82c2821fb?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1000/1*ShVKH7cjMmVqrbUzGuhjfA.png)](https://towardsdatascience.com/introduction-to-survival-analysis-in-cows-using-r-28b82c2821fb?source=rss----7f60cf5620c9---4)

</div>

In Cows using R

</div>

<div class="card">

<div class="card-title">

[Hands-on Survival Analysis with
Python](https://towardsdatascience.com/hands-on-survival-analysis-with-python-270fa1e6fb41?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*Zqk9SXBRdwmuaxd_phazag.jpeg)](https://towardsdatascience.com/hands-on-survival-analysis-with-python-270fa1e6fb41?source=rss----7f60cf5620c9---4)

</div>

What companies can learn from employee turnover data

</div>

<div class="card">

<div class="card-title">

[A Complete Guide To Survival Analysis In Python, part 3 -
KDnuggets](https://www.kdnuggets.com/2020/07/guide-survival-analysis-python-part-3.html)

</div>

Concluding this three-part series covering a step-by-step review of
statistical survival analysis, we look at a detailed example
implementing the Kaplan-Meier fitter based on different groups, a
Log-Rank test, and Cox Regression, all with examples and shared code.

</div>

<div class="card">

<div class="card-title">

[Introduction to Survival Analysis: the Kaplan-Meier
estimator](https://towardsdatascience.com/introduction-to-survival-analysis-the-kaplan-meier-estimator-94ec5812a97a?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*bVjqr3hUa9NF65SruqT-AQ.jpeg)](https://towardsdatascience.com/introduction-to-survival-analysis-the-kaplan-meier-estimator-94ec5812a97a?source=rss----7f60cf5620c9---4)

</div>

Learn one of the most popular techniques used for survival analysis and
how to implement it in Python!

</div>

<div class="card">

<div class="card-title">

[Practical Survival Analysis — Concepts, techniques,
models](https://towardsdatascience.com/practical-survival-analysis-concepts-techniques-models-10819fd49b4a?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*YfQ0FQIK4l6NMW3wsl9NNw.jpeg)](https://towardsdatascience.com/practical-survival-analysis-concepts-techniques-models-10819fd49b4a?source=rss----7f60cf5620c9---4)

</div>

With worked out examples using Python and Lifelines

</div>

</div>
