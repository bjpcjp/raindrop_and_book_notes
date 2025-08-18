# Extracted Terms and Definitions

## ADFM-algos-decision-makingbook.pdf

### Artifi-
cial Intelligence

A Modern Approach,
4th ed. Pearson, 2021.

### De-
cision Making Under Uncertainty

Theory and Application. MIT Press,
2015.

### Rein-
forcement Learning

An Introduction,
2nd ed. MIT Press, 2018.

### Between Human
and Machine

Feedback, Control, and

### Search and Screen-
ing

General Principles with Historical

### Xiv

2001.01818v1.

### Xiv

1606.06565v2
.

### Probability
Theory

The Logic of Science. Cam-
bridge University Press, 2003.

### Probabilistic Graphi-
cal Models

Principles and Techniques.

### Probabilis-
tic Graphical Models

Principles and

### Prob-
abilistic Reasoning in Intelligent Sys-
tems

Networks of Plausible Inference.

### Solution

One solution is U([−10, −10], [−5, 10]), U([−5, 0], [0, 10]), U([−5, −10], [0, 0]),

### Solution

We start with the most common probabilities, 0.13, which occurs when Z = 0
and Y = 0, and 0.05, which occurs when Z = 0 and Y = 1. We choose to make Z the root
of our decision tree and when Z = 0 we continue to a Y node. Based on the value of Y we
branch to either 0.13 or 0.05. Next, we continue with cases when Z = 1. The most common
probabilities are 0.02, which occurs when Z = 1 and X = 0, and 0.12, which occurs when

### Solution

For a Gaussian distribution over four variables (n = 4) with independence
assumptions, we need to specify n + n = 2n = 8 independent parameters; there are four
parameters for the mean vector and four parameters for the covariance matrix (which is
equivalent to the mean and variance parameters of four independent univariate Gaussian
distributions). For a Gaussian distribution over four variables without independence
assumptions, we need to specify n + n(n + 1)/2 = 14 independent parameters; there
are four parameters for the mean vector and ten parameters for the covariance matrix.

### Solution

If we have a piecewise-constant density with m bins edges, then there are m −1
bins and m −2 independent parameters. For this problem, there will be (4 −2) + (7 −
2) + (3 −2) = 8 independent parameters.

### Solution

The number of independent parameters for each node is equal to (k −1)km where
k is the number of values the node can take on and m is the number of parents that the
node has. The variable A has 3, B has 12, C has 48, D has 3, E has 12, and F has 48 and
independent parameters. There are 126 total independent parameters for this Bayesian
network.

### There are two paths from A to E

A →D →E and A →C →E. There is
d-separation along the second path, but not the first. Hence, A is not d-separated from E
given C.

### Solution

Paths from B to A can only be d-separated given A. Paths from B to D can only be
d-separated given D. Paths from B to E and simultaneously F, G, and H can be efficiently
d-separated given E. Paths from B to C are naturally d-separated due to a v-structure;
however, since E must be contained in our Markov blanket, paths from B to C given E can
only be d-separated given C. So, the Markov blanket of B is {A, C, D, E}.

### Solution

There is a direct arrow from A to B, which indicates that independence is not
implied. However, this does not mean that they are not independent. Whether or not A
and B are independent depends on the choice of conditional probability tables. We can
choose the tables so that there is independence. For example, suppose both variables are
binary and P(a) = 0.5 is uniform and P(b | a) = 0.5. Clearly, P(A)P(B | A) = P(A)P(B),
which means they are independent.

### Solution

We first expand the inference expression using the definition of conditional
probability.

### Solution

We first expand the inference expression using the definition of conditional
probability.

### Solution

We have P(c1
3 | x1
2, x0
3, x1
4) = 1 because x1
2, x0
3, x1
4 makes the third clause true, and

### Solution

For likelihood-weighted sampling, the sample weights are the product of the
distributions over evidence variables conditioned on the values of their parents. Thus, the
general form for our weights is P(b0 | a)P(d1 | b0, c). We then match each of the values for
each sample from the joint distribution.

### Machine
Learning

A Probabilistic Perspective.

### Solution

Since our first toss lands on heads, we have m = 1 successes and n = 1 trials.

### Solution

Assuming the marginal distribution over X1 is a Gaussian, we can compute the
marginal mode, which is the mean parameter of the Gaussian distribution

### Probabilis-
tic Graphical Models

Principles and

### Learning from Data

Artificial Intelligence and Statistics

### Inf

bayesian_score(vars, G′, D)
if y′ > y

### This textbook provides an
overview

M. J. Kochenderfer and

### Learning Bayesian Net-
works

The Combination of Knowl-
edge and Statistical Data,’’ Machine

### Solution

Of the three basic graph operations, we can only add edges. We can add any edge to
an edgeless directed acyclic graph and it will remain acyclic. There are m(m −1) = m2 −m
node pairs, and therefore that many neighbors.

### Solution

At each iteration, local search can move from the original network to a network in
its neighborhood, which is at most one edge operation from the original network. Since
there are three differences between the edges of G and G∗, performing local search from

### The
Expected
Utility
Model

Its Variants, Purposes, Evidence
and

### Exactly one of the following holds

A ≻B, B ≻A, or A ∼B.

### Utilities are like temperatures

you can com-
pare temperatures using Kelvin, Celsius, or Fahrenheit, all of which are affine
transformations of each other.

### Sn

pn]) =
n
∑
i=1
piU(Si)
(6.2)

### Artificial Intelligence

A Modern Ap-
proach, 4th ed. Pearson, 2021.

### Applications to decision networks
can be found in

S. L. Dittmer and

### Solution

Risk aversion implies that the utility function is concave, which requires that the
second derivative of the utility function is negative. The utility function and its derivatives
are computed as follows

### Solution

We are interested in computing

### Markov Decision Processes

Discrete Stochastic Dynamic Program-
ming. Wiley, 2005.

### Eye of the Hurricane

an Autobiography. World Scientific,
1984.

### Solution

We can prove that the infinite sequence of discounted constant rewards converges
to r/(1 −γ) in the following steps

### Solution

The optimal value of U∗(s1) is associated with following the optimal policy π∗

### Solution

We can compute U(s), π(s), and A(s, a) using the following equations

### Solution

We are given ∥U −U∗∥∞< ϵ. The worst-case deviation between the policy
extracted from U and an optimal policy occurs when the policy from U has value just
under U + ϵ and the true optimal policy has value just above U −ϵ. In this case, Uπ −U∗<

### Solution

The problem in example 7.4 has quadratic reward that penalizes deviations
from the origin. The longer the horizon, the greater the negative reward is that can be
accumulated, making it more worthwhile to reach the origin sooner.

### Solution

Let U be the value function produced by value iteration. We want to show that

### Solution

A matrix M is positive definite if for all non-zero x, that x⊤Mx > 0. In equa-
tion (7.31), every Vi is negative semi-definite, so w⊤Vw ≤0 for all w. Thus, these q terms
are guaranteed to be non-positive. This should be expected, as in LQR problems it is
impossible to obtain positive reward, and we seek instead to minimize cost.

### Approxi-
mate Dynamic Programming

Solving
the Curses of Dimensionality, 2nd ed.

### The Elements
of Statistical Learning

Data Mining,

### The Elements of Statisti-
cal Learning

Data Mining, Inference,
and Prediction, 2nd ed. Springer Se-
ries in Statistics, 2001.

### Solution

In local approximation methods, the state-action values are the parameters. We
will have |S| × |A| = 100 × 5 = 500 parameters in θ. In global approximation methods,
the coefficients of the basis functions are the parameters. Since there are six components
in β(s, a), we will have six parameters in θ.

### Solution

The first set of weighting functions is not valid, as it violates the constraint
∑i βi(s) = 1. We can modify the weighting functions by normalizing them by their sum

### Solution

The general form for bilinear interpolation is given in equation (8.12) and repro-
duced below. To generate the interpolant, we substitute our values into the equation and
simplify

### Solution

For the given state s, we have 0 ≤x1 ≤x3 ≤x2 ≤1, and so our permutation
vector is p = [1, 3, 2]. The vertices of our simplex can be generated by starting from (0, 0, 0)
and changing each 0 to a 1 in reverse order of the permutation vector. Thus, the vertices of
the simplex are (0, 0, 0), (0, 1, 0), (0, 1, 1), and (1, 1, 1).

### Inf

sqrt(log(Ns)/Nsa)

### Only two states are labeled in
this iteration

the hidden terminal
state and the state with a hexag-
onal border. Both the exploratory
run and the labeling step update
the value function.

### Robust Model Predictive Control

A Survey,’’ in Robustness in Identi-
fication and Control, A. Garulli, A.

### Modulating Robustness in Con-
trol Design

Principles and Algo-
rithms,’’ IEEE Control Systems Mag-
azine, vol. 33, no. 2, pp. 36–51, 2013.
of multi-forecast model predictive control, which is a type of hindsight optimization15

### Solution

In the worst case, branch and bound will never prune, resulting in a traversal of
the same search tree as forward search with the same complexity.

### Solution

Create a new heuristic h(s) = min{h1(s), h2(s)} and use it instead. This strictly
improves a heuristic search algorithm. Moreover, this new heuristic is guaranteed to be
admissible. Both h1(s) ≥U∗(s) and h2(s) ≥U∗(s) imply that h(s) ≥U∗(s).

### Solution

Would could define a new heuristic h3(s) = max(h1(s), h2(s)) to get a potentially
admissible or a ‘‘less-inadmissible’’ heuristic. It may be slower to converge, but it may be
more likely to not miss out on a better solution.

### Solution

We need
|S′| = |S|
1
d
and
|A′| = |A|
1
d

### Solution

The computational complexity of forward search is given by O

(|S||A|)d
, which

### Solution

Forward search enumerates over all possible future actions. It may return different
actions if there are ties in their expected utilities. Branch and bound maintains the same
optimality guarantee over the horizon as forward search by sorting by upper bound. The
ordering of the action space can affect branch and bound’s visitation rate when the upper
bound produces the same expected value for two or more actions. Below we show this
effect on the modified mountain car problem from example 9.2. The plot compares the
number of states visited in forward search to that of branch and bound for different action
orderings to depth 6. Branch and bound consistently visits far fewer states than forward
search, but action ordering can still affect state visitation.

### Solution

No. While the computational complexities are identical at O

|S|d|A|d
, forward
search will branch on all states in the state space, while sparse sampling will branch on
|S| randomly sampled states.

### Deep Neuroevolution

Ge-
netic Algorithms Are a Competi-
tive Alternative for Training Deep

### Xiv

1712
.06567v3. The implementation in
this section follows their relatively
simple formulation. Their formu-
lation does not include crossover,
which is typically used to mix pa-
rameterizations across a popula-
tion.

### Mu-
tation Distributions in Evolution
Strategies

the Covariance Matrix

### Xiv

1703.03864v2.

### Xiv

1703 . 03864v2. They
included other techniques as well,
including weight decay.
benefit of this technique is shown in figure 10.8.

### Solution

The computational cost per iteration scales linearly with the number of samples.

### Solution

The added Gaussian noise around the policy parameters can smooth discontinu-
ities in the original objective, which can lead more reliable optimization.

### Solution

The Hooke-Jeeves method improves a single policy parameterization, so it cannot
retain multiple policies. Both the cross entropy method and evolution strategies use search
distributions. In order to successfully represent multiple types of policies, a multi-modal
distribution would have to be used. One common multi-modal distribution is a mixture of

### Solution

The Hooke-Jeeves method evaluates the objective function at the center point ±α
along each coordinate direction. In order to guarantee improvement in the first iteration of

### Solution

We first compute the numerator of the first term from equation (10.13), for all i

### Xiv

1707.0634
7v2.

### Xiv

1506.02438v6.
difference residual has low variance but introduces bias due to a potentially

### Xiv

1509.02
971v6.

### Solution

The Monte Carlo tree search expands a tree based on visited states. The cart-pole
problem has a continuous state space, leading to a search tree with an infinite branching
factor. Use of this algorithm would require adjusting the problem, such as discretizing the
state space.

### Solution

Approximation using a temporal difference residual is more computationally
efficient than using a sequence of rollouts. Temporal difference residual approximation has
low variance but high bias due to using the critic value function Uφ as an approximator of
the true value function Uπθ. On the other hand, rollout approximation has high variance

### Solution

We need to calculate two gradients. For the actor we need to compute ∇φQφ(s, a),
while for the critic we need to compute ∇aQφ(s, a).

### Xiv

2005.02979.

### The
adversary has two objectives to balance

minimizing our return and maximizing
the likelihood of the resulting trajectory according to our transition model. We
can transform our original problem into an adversarial problem. The adversarial
state space is the same as in the original problem, but the adversarial action space
is the state space of the original problem. The adversarial reward is

### Solution

The log-likelihood of the trajectory is

### Solution

The collision probability estimate is

### Solution

The optimal proposal distribution is

### Solution

The weight is p(x)/p∗(x) = 0.2/1. Since f (0.3) = −1, the estimate is −0.2, which
is the exact answer.

### Solution

Only π1 is dominated by other policies. Hence, π2, π3, and π4 are on the Pareto
frontier.

### Reinforcement Learning

State of the

### Solution

Below we plot the expected reward-per-step for the three different strategies. The
effectiveness of the parameterization depends on the problem horizon, so several different
depths are shown as well.

### Solution

Below we plot the expected reward-per-step for the three different strategies.

### Solution

There are many different multi-armed bandit problems. Consider, for example, a
news company that would like to maximize interaction (clicks) on articles on its website.

### Solution

A lower bound on our posterior probability of winning ρ can be computed
assuming all pulls result in a loss, e.g. ℓ= 10 and w = 0. We can similarly compute an
upper bound ρ assuming all pulls result in a win, e.g. w = 10 and ℓ= 0. Thus, the bounds
are

### Solution

Since x < ϵ1 in the first iteration, we explore and choose a with probability 0.5
and b with probability 0.5. At the ninth iteration, ϵ9 = α8ϵ1 ≈0.129. Since x > ϵ9, we
exploit and select a.

### Solution

We can rewrite the equation more generally as follows

### Solution

We begin by counting the number of solutions to w1 + ℓ1 + · · · + wn + ℓn = k,
where 0 ≤k ≤h. If n = 2 and k = 6, one solution is 2 + 0 + 3 + 1 = 6. For our counting
argument, we will use tally marks to represent our integers. For example, we can write a
solution like 2 + 0 + 3 + 1 = ||++|||+| = 6. For general values for n and k, we would have
k tally marks and 2n −1 plus signs. Given that many tally marks and plus signs, we can
arrange them in any order we want. We can represent a solution as a string of k + 2n −1
characters, where a character is either | or +, with k of those characters being |. To obtain
the number of solutions, we count the number of ways we can choose k positions for |
from the set of k + 2n −1 positions, resulting in

### Prioritized Sweeping

Reinforce-
ment Learning With Less Data
and Less Time,’’ Machine Learning,
vol. 13, no. 1, pp. 103–130, 1993.

### Solution

A lower bound on the number of updates performed in an iteration of prioritized
sweeping is 1. This could occur during our first iteration using a maximum likelihood
model, where the only nonzero entry in our transition model is T(s′ | s, a). Since no
state-action pairs (s−, a−) transition to s, our priority queue would be empty and thus the
only update performed would be for U(s).

### Solution

For each state and action, we specify a Dirichlet distribution over the transition
probability parameters, so we will have |S||A| Dirichlet distributions. Each Dirichlet
is specified using |S| independent parameters. In total, we have |S|2|A| independent
parameters.

### Solution

Dir(θ(s2,a1) | [2, 1, 2])

### Rein-
forcement Learning

An Introduction,
2nd ed. MIT Press, 2018.

### Xiv

1312.5602v1.

### Solution

The incremental estimation of the mean equation is

### Solution

The Sarsa(λ) update rules are

### D of expert state-action
pairs

maximize
θ
∏
(s,a)∈D
πθ(a | s)
(18.1)

### Guided
Cost Learning

Deep Inverse Op-
timal Control via Policy Optimiza-
tion,’’ in International Conference on

### Solution

In imitation learning, we are generally limited to a relatively small set of expert
demonstrations. The distribution P(a | s) has (|A| −1)|S| independent parameters that
must be learned, which is often prohibitively large. Expert demonstrations typically only
cover a small portion of the state-space. Even if P(a | s) can be reliably trained for the
states covered in the provided dataset, the resulting policy would be untrained in other
states. Using a feature function allows for generalization to unseen states.

### Solution

Maximum margin inverse reinforcement learning extracts binary features from
the expert data and seeks a reward function whose optimal policy produces trajectories
with the same frequencies of these binary features. There is no guarantee that multiple
policies do not produce the same feature expectations. For example, an autonomous car
that only makes left lane changes could have the same lane change frequencies as an
autonomous car that only makes right lane changes.

### Solution

If we use non-binary features, then it is possible that some features can get
larger than others, incentivizing the agent to match those features over those that tend
to be smaller. Scale is not the only issue. Even if all features are constrained to lie within
[0, 1], then a policy that consistently produces φ(s, a)1 = 0.5 will have the same feature
expectations as one that produces φ(s, a)1 = 0 half the time and φ(s, a)1 = 1 half the time.

### Solution

These distributions over relative duration are analogous to distributions over
trajectories for this elevator problem. In applying the principle of maximum entropy, we
prefer the distribution with most entropy. Hence, we would choose policy B, which in
being most uniform, has the greatest entropy.

### Solution

Yes. The POMDP formulation extends the MDP formulation by introducing state
uncertainty in the form of the observation distribution. Any MDP can be framed as a

### Solution

Yes, overconfidence in a belief can be a problem when the models or belief updates
do not perfectly represent reality. The overconfident belief may have converged on a state
that does not match the true state. Once the vehicle moves again, new observations may
be inconsistent with the belief and result in poor estimates. To help address this issue, we
can require that the values of the diagonal elements of the covariance matrix be above
some threshold.

### Solution

We seek the posterior distribution p(λ | d, α, β), which we can obtain through

### Solution

Rejection sampling requires repeatedly sampling the transition and observation
functions until the sampled observation matches the true observation. The probability
of sampling any particular value in a continuous probability distribution is zero, making
rejection sampling run forever. In practice, we would use a finite representation for contin-
uous values such as 64-bit floating point numbers, but rejection sampling can run for an
extremely long time for each particle.

### Solution

The particle filter with adaptive injection injects new particles when νwfast/wslow
is less than 1. Spelunker Joe assumes perfect observations and has a belief with particles
that match his current observation. Thus, every particle has a weight of 1, and so both
wfast and wslow are 1. It follows that wfast/wslow is always 1, leading to no new particles.

### Solution

Particle injection was designed to inject particles when the current observations
have lower likelihood than a historic trend over the observation likelihood. Thus, injection
typically only occurs when the short-term estimate of the mean particle weight wfast is less
than the long-term estimate of the mean particle weight wslow. If ν < 1, then particles can
still be generated even if wfast ≥wslow, despite indicating that current observations have
higher likelihood than the past average.

### Solution

The transition and observation dynamics can be written in linear form as follows
"
x′

### Solution

Since we have a two-dimensional Gaussian distribution and we are given λ = 2,
we need to compute 2n + 1 = 5 sigma points. We need to compute the square-root matrix

### Solution

The transformed sigma points are

### Incre-
mental Pruning

A Simple, Fast, Ex-
act Method for Partially Observ-
able Markov Decision Processes,’’
in Conference on Uncertainty in Arti-
ficial Intelligence (UAI), 1997.

### Solution

Yes. Any POMDP can equivalently be viewed as a belief-state MDP whose state
space is the space of beliefs in the POMDP, whose action space is the same as that of the

### Solution

Recall that there are |A|(|O|h−1)/(|O|−1) possible h-step plans. Exponential growth
(nx) is faster than polynomial growth (xn), and we have better-than exponential growth
in |O| and polynomial growth in |A|. The number of plans thus increases faster with
respect to the number of observations. To demonstrate, let us use |A| = 3, |O| = 3, and
h = 3 as a baseline. The baseline has 1,594,323 plans. Incrementing the number of actions
results in 67,108,864 plans, whereas incrementing the number of observations results in
10,460,353,203 plans.

### Solution

Depending on the probability of incorrect results, we may want to perform the
same test multiple times to improve our confidence in whether the patient has the disease
or is healthy. The results of the tests are independent given the disease state.

### Suppose we have three alpha vectors

[1, 0], [0, 1], and [θ, θ], for some con-
stant θ. Under what conditions on θ can we prune alpha vectors?

### Solution

We can prune alpha vectors if θ < 0.5 or θ > 1. If θ < 0.5, then [θ, θ] is dominated
by the other two alpha vectors. If θ > 1, then [θ, θ] dominates the other two alpha vectors.

### Solution

The alpha vectors in Γ are shown in blue and the alpha vector α is shown in red.

### The iteration is

5 The relationship between QMDP
and the fast informed bound to-
gether with empirical results is dis-
cussed by M. Hauskrecht, ‘‘Value-

### SARSOP

Efficient Point-

### Robotics

Science
and Systems, 2008.

### SARSOP

Efficient Point-Based

### Robotics

Science and

### There are two actions

move left (ℓ) and move right (r). The effects of those actions are deterministic. Moving
left in s1 or moving right in s4 gives a reward of 100 and ends the game. With a discount
factor of 0.9, compute alpha vectors using QMDP. Then, using the alpha vectors, compute
the approximately optimal action given the belief b = [0.3, 0.1, 0.5, 0.1].

### Robotics

Science and Systems, 2010.

### DESPOT

Online POMDP Planning with

### It consists of the two main steps

policy evaluation
(left) and policy improvement (center), as well as the optional pruning step
(right).

### Solution

Unlike tree-based conditional plans, controllers can represent policies that can be
executed indefinitely. They do not have to grow exponentially in size with the horizon.

### Solution

Controller policy iteration is guaranteed to converge on an optimal policy in
the limit. However, the method cannot find more compact representations of optimal
controller policies that may require stochastic nodes.

### Solution

Let x′ be the new node from some iteration i, and x be a previous node from
iteration i −1.

### Solution

The idea is to create an outer loop that increments the fixed-size of the controller,
after knowing the utility of the large fixed-sized controller. First, we must compute the
large fixed-sized controller’s utility U∗= ∑s b1(s)U(x1, s) at initial node x1 and initial
belief b1. Next, we create a loop that increments the size ℓof the controller. At each step, we
evaluate the policy and compute the utility Uℓ. By our assumption, the controller returned
produces a globally optimal utility for the fixed size ℓ. Once we arrive at a utility Uℓ, if we
see that Uℓ= U∗, then we stop and return the policy.

### Solution

Computing the inverse Z−1 = (I −γTθ) is the most computationally expensive
part of the gradient step, as well as the entire gradient algorithm. The matrix Z is of size
|X × S|. Gauss–Jordan elimination requires O(|X × S|3) operations, though the 3 in the
exponent can be reduced to 2.3728639 using a state-of-the-art matrix inversion algorithm.10

### Sev-
eral standard introductory books
include

D. Fudenberg and J. Tirole,

### Game Theory

Analysis of

### Multiagent Systems

Algo-
rithmic, Game Theoretic, and Logical

### Multiagent Systems

Algo-
rithmic, Game Theoretic, and Logical

### Behavioral Game
Theory

Experiments in Strategic

### Beyond
Equilibrium

Predicting Human Behavior in

### Solution

Suppose the action space of each agent consists of the negative real numbers
and their reward is equal to their action. Since no greatest negative number exists, a Nash
equilibrium cannot exist.

### Solution

Here is one example.16 Suppose we have two aircraft on a collision course, and
16 This example comes from M. J.

### Decision Making Un-
der Uncertainty

Theory and Applica-
tion. MIT Press, 2015.

### Solution

Given any Nash equilibrium π, define a correlated joint policy π(a) such that

### Solution

Consider the following game in which two people want to go on a date but have
a conflicting preference on what kind of date, in this case a dinner or a movie.

### Multiagent Systems

Algo-
rithmic, Game Theoretic, and Logical

### Solution

It converges to the Nash equilibrium of $2.

### Solution

Markov games generalize simple games. For any simple game with I, A, R, we
can construct a Markov game by just having a single state that self-loops. In other words,
this Markov game has S = {s1}, T(s1 | s1, a) = 1, and R(s1, a) = R(a).

### Solution

No, if given fixed policies of other agents π−i, a deterministic best response is
sufficient to obtain the highest utility. The best response can be formulated as solving an

### Solution

The algorithm presented in this chapter performs a single backup for the visited
state s and all joint actions a. This approach has the benefit of being relatively efficient
because it is a single backup. Updating all joint actions at that state results in exploring
actions that were not observed. The drawback of this approach is that we may need to do
this update at all states many times to obtain a suitable policy.

### Solution

For any POMDP, we can define a POMG with one agent I = {1}. The states S
are identical, as are the actions A = (A1) and observations O = (O1). Thus, the state
transition, observation function, and rewards of the POMG directly follow. The Nash
equilibrium optimization only has one agent, so it results in a simple maximization of
expected value, identical to a POMDP.

### Solution

The action space for the agents can be augmented to include communication
actions. The other agents can observe these communication actions according to their
observation model.

### Solution

Agents in POMGs are often competitive, in which case there would be no incentive
to communicate with others. If their rewards are aligned to some degree, they may be
inclined to communicate.

### Solution

Recall that there are |A|(|O|d−1)/(|O|−1) possible d-step single-agent conditional
plans. We can construct a joint policy of conditional plans using every combination of these
single-agent conditional plans across agents. The number of d-step multiagent conditional
plans is
∏
i∈I
|Ai|(|Oi|d−1)/(|Oi|−1)

### There are three hyper edges

one in-
volving agents 1, 2, and 3; another
involving agents 3 and 4; and an-
other involving agent 5 on its own.

### Solution

Dec-POMDPs are fully-cooperative. Multi-robot domains, such as search and
rescue, require the robots to work together as a team. The engineers have full control of
the executable policies of each robot. Conversely, in a competitive POMG (or even MG),
the algorithms compute policies for all agents. However, in competitive settings, we likely
only have control over one agent’s policy. Additionally, the model realistically captures the
limited sensors and sensor models in robotics, as in POMDPs, except in the multiagent
setting.

### Solution

Full joint observability means if agents were to share their individual observations,
then the team would know the true state. This can be done offline during planning. Thus
in Dec-MDPs, the true state is essentially known during planning. The issue is that it
requires agents to share their individual observations, which cannot be done online during
execution. Therefore, planning still needs to reason about the uncertain observations made
by the other agents.

### Solution

We can assume free communication for planning. At each time step t, all agents
know at and ot, allowing us to maintain a multiagent belief bt, resulting in an MPOMDP.

### Solution

For an agent i, the best response controller Xi, ψi, and ηi can be computed by a
nonlinear program. The program is similar to section 27.6, except that X−i, ψ−i, and η−i

### Xiv

1907.08611v1.

### Com-
putational Complexity

A Conceptual

### NP

problems whose solutions can be verified in polynomial time,

### NP-hard

problems that are at least as hard as the hardest problems in NP, and

### NP-complete

problems that are both NP-hard and in NP.

### Eval-
uating Derivatives

Principles and

### Our implementation does use two
value functions

the heuristic for
guiding the search and an approxi-
mate value function for evaluating
terminal states.

### Residual Algo-
rithms

Reinforcement Learning
with Function Approximation,’’ in

### Xiv

1606.01540v1.

### Decision Making Un-
der Uncertainty

Theory and Applica-
tion. MIT Press, 2015.

### Dilem-
ma

Paradoxes of Rationality in

### The states contain the locations of each agent

S = S1 × · · · × S|I|, with each Si

### IterTools

subsets
julia> collect(subsets(X))
# iterate over all subsets

### CachingOptimizer state

EMPTY_OPTIMIZER

### Xiv

1606.06565v2 (cit. on p. 13).

### Predictably Irrational

The Hidden Forces That Shape Our Decisions. Harper,
2008 (cit. on p. 120).

### Residual Algorithms

Reinforcement Learning with Function Approx-
imation,’’ in International Conference on Machine Learning (ICML), 1995 (cit. on
p. 600).

### Dilemma

Paradoxes of Rationality in Game Theory,’’ The

### Eye of the Hurricane

an Autobiography. World Scientific, 1984 (cit. on
p. 132).

### Robust Model Predictive Control

A Survey,’’ in

### Xiv

1907.08611v1 (cit. on p. 563).

### Labeled RTDP

Improving the Convergence of Real-Time

### Xiv

1606.01540v1 (cit. on p. 601).

### Behavioral Game Theory

Experiments in Strategic Interaction. Princeton

### Incremental Pruning

A Sim-
ple, Fast, Exact Method for Partially Observable Markov Decision Processes,’’ in

### Learning from
Data

Artificial Intelligence and Statistics V, D. Fisher and H.-J. Lenz, eds., Springer,
1996, pp. 121–130 (cit. on p. 95).

### Xiv

2005.02979 (cit. on p. 275).

### Guided Cost Learning

Deep Inverse Optimal

### Modulating Robustness in Control Design

Principles
and Algorithms,’’ IEEE Control Systems Magazine, vol. 33, no. 2, pp. 36–51, 2013 (cit.
on p. 202).

### Bayesian Reinforcement
Learning

A Survey,’’ Foundations and Trends in Machine Learning, vol. 8, no. 5–6,
pp. 359–483, 2015 (cit. on p. 317).

### Computational Complexity

A Conceptual Perspective. Cambridge Uni-
versity Press, 2008 (cit. on p. 565).

### Evaluating Derivatives

Principles and Techniques of

### Mutation Distributions
in Evolution Strategies

the Covariance Matrix Adaptation,’’ in IEEE International

### Learning Bayesian Networks

The Combination of Knowledge and Statistical Data,’’ Machine Learning, vol. 20,
no. 3, pp. 197–243, 1995 (cit. on p. 102).

### Probability Theory

The Logic of Science. Cambridge University Press,
2003 (cit. on p. 19).

### Prospect Theory

An Analysis of Decision Under

### Decision Making Under Uncertainty

Theory and Application. MIT

### Probabilistic Graphical Models

Principles and Techniques.

### Search and Screening

General Principles with Historical Applications.

### SARSOP

Efficient Point-Based POMDP

### Robotics

Science
and Systems, 2008 (cit. on pp. 430, 432).

### Xiv

1509.02971v6 (cit. on
p. 268).

### Planning with Markov Decision Processes

An AI Perspective.

### Between Human and Machine

Feedback, Control, and Computing before

### Prioritized Sweeping

Reinforcement Learning

### Machine Learning

A Probabilistic Perspective. MIT Press, 2012 (cit. on
p. 71).

### Game Theory

Analysis of Conflict. Harvard University Press, 1997 (cit.
on p. 487).

### Taming Decentral-
ized POMDPs

Towards Efficient Policy Computation for Multiagent Settings,’’ in

### Policy Invariance Under Reward Transforma-
tions

Theory and Application to Reward Shaping,’’ in International Conference on

### Probabilistic Reasoning in Intelligent Systems

Networks of Plausible Inference.

### Robotics

Science and Systems,
2010 (cit. on p. 450).

### Approximate Dynamic Programming

Solving the Curses of Dimensionality,
2nd ed. Wiley, 2011 (cit. on p. 157).

### Markov Decision Processes

Discrete Stochastic Dynamic Programming.

### Artificial Intelligence

A Modern Approach, 4th ed. Pearson,
2021 (cit. on pp. 2, 114).

### Xiv

1703.03864v2 (cit.
on pp. 217, 220).

### The Expected Utility Model

Its Variants, Purposes, Evidence
and Limitations,’’ Journal of Economic Literature, vol. 20, no. 2, pp. 529–563, 1982 (cit.
on p. 109).

### Xiv

1506.02438v6 (cit. on
p. 262).

### Xiv

1707.06347v2 (cit. on p. 251).

### Xiv

2001.01818v1 (cit. on p. 12).

### Multiagent Systems

Algorithmic, Game Theoretic,
and Logical Foundations. Cambridge University Press, 2009 (cit. on pp. 487, 506).

### Perseus

Randomized Point-Based Value Iteration
for POMDPs,’’ Journal of Artificial Intelligence Research, vol. 24, pp. 195–220, 2005
(cit. on p. 423).

### Deep
Neuroevolution

Genetic Algorithms Are a Competitive Alternative for Training

### Xiv

1712.06567v3
(cit. on p. 211).

### Reinforcement Learning

An Introduction, 2nd ed. MIT

### Reinforcement Learning

State of the Art. Springer,
2012 (cit. on p. 293).

### Points of View

Color Blindness,’’ Nature Methods, vol. 8, no. 6, pp. 441–
442, 2011 (cit. on p. xxiii).

### Beyond Equilibrium

Predicting Human Behav-
ior in Normal Form Games,’’ in AAAI Conference on Artificial Intelligence (AAAI),
2010 (cit. on p. 498).

### DESPOT

Online POMDP Planning with

### Optimum Con

sumption and Portfolio Rules in a

### Distributed Wildfire Surveil

lance with Autonomous Aircraft

### Using Deep Reinforcement Learn

ing,’’ AIAA Journal on Guidance,

### Evaluating the perfor

mance of a decision strategy generally involves running a batch of simulations.

### Kalligeropou

los, and N. Karcanias, ‘‘Systems,

### Cambridge Univer

sity Press, 2009.

### Between Human
and Machine

Feedback, Control, and

### Search and Screen-
ing

General Principles with Historical

### A much more thorough discus

sion is provided by Z. R. Shi, C.

### Xiv

2001.01818v1.

### Part I

Probabilistic Reasoning

### For a more comprehensive elabo

ration, see E. T. Jaynes, Probability

### New Axioms for Rigor

ous Bayesian Probability,’’ Bayesian

### Gaus

sian distribution.

### An example Gaus

sian mixture model.

### Example joint distribu

tion involving binary variables X,

### Named for the English statis

tician and Presbyterian minister

### Probabilistic Graphi-
cal Models

Principles and Techniques.

### Probabilis-
tic Graphical Models

Principles and

### Named after the Russian math

ematician Andrey Andreyevich

### Prob-
abilistic Reasoning in Intelligent Sys-
tems

Networks of Plausible Inference.

### Solution

One solution is U([−10, −10], [−5, 10]), U([−5, 0], [0, 10]), U([−5, −10], [0, 0]),

### Bayesian network struc

ture from example 2.5.

### A naive exact in

ference algorithm for a discrete

### Bird
Suppose from the chain rule we determine

P(bird, slow, little heading fluctuation) = 0.03

### Belief propagation and related al

gorithms are covered in detail by

### The Computa-
tional Complexity of Probabilis

tic Inference Using Bayesian Belief

### This formula also appears in ex

ample C.3 in appendix C.

### Bayesian network rep

resenting a 3SAT problem.

### Inference in a mul

tivariate Gaussian distribution D.

### Machine
Learning

A Probabilistic Perspective.

### The ith component con

sists of a qi × ri matrix of counts.

### A comprehensive introduc

tion and review is provided by G.

### Ver

beke, eds., Handbook of Missing Data

### Example data with con

tinuous values.

### Expectation-maximization was in

troduced by A. P. Dempster, N. M.

### Z for that instance

P(zi | X = 4.2) =

### Probabilis-
tic Graphical Models

Principles and

### Learn

ing Bayesian Networks is NP-

### Learning from Data

Artificial Intelligence and Statistics

### Machine Learn

ing, vol. 4, no. 9, pp. 309–347, 1992.

### The
loggamma function is pro

vided by

### Counting La

beled Acyclic Digraphs,’’ in Ann

### G and
opportunistically moves to a ran

dom graph neighbor whenever its

### This textbook provides an
overview

M. J. Kochenderfer and

### Moral and immoral v

structures.

### The Combination of Knowl

edge and Statistical Data,’’ Machine

### Theory Refine

ment on Bayesian Networks,’’ in

### Markov
equivalence class because it intro

duces an immoral v-structure A →

### Equivalence
Classes of Bayesian-Network Struc

tures,’’ Journal of Machine Learning

### An Introduction to Deci

sion Theory. Cambridge University

### These
constraints
are
some

times called the von Neumann-

### Utility elicitation ap

plied to collision avoidance.

### Extensive discussion of deci

sion networks can be found in

### The utility asso

ciated with an action is equal to the sum of the values at all the utility nodes.

### Applications to decision networks
can be found in

S. L. Dittmer and

### Hidden Forces That Shape Our Deci

sions. Harper, 2008. J. Lehrer, How

### We mul

tiply both sides by 10 and get

### This transform is

ˆU(s) = U(s) −U

### Solution

EU(bring umbrella | forecast sun) = 0.2 × −0.1 + 0.8 × 0.9 = 0.7

### Solution

We are interested in computing

### Part II

Sequential Problems

### Markov decision pro

cess decision diagram.

### Stationary Markov de

cision process decision diagram.

### Intro

duction to Algorithms, 3rd ed. MIT

### The sec

ond version handles the case when

### Lin

ear Programming, Foundations and

### Polynomial
Algo

rithms in Linear Programming,’’

### Bert

sekas, Dynamic Programming and

### Solution

We can compute U(s), π(s), and A(s, a) using the following equations

### SE

U(s3) = max(10, 10, 10, 10, 10, 10) = 10

### Solution

Let U be the value function produced by value iteration. We want to show that

### The resulting
value function is piecewise con

stant.

### In the two

dimensional case, called bilinear interpolation, we interpolate between four vertices.

### Two-dimensional sim

plex interpolation over a 3 × 7 grid.

### Cornell Univer

sity, 1992.

### The Elements
of Statistical Learning

Data Mining,

### It re

turns the total discounted reward.

### This al

gorithm is also used for POMDPs.

### White

house, S. M. Lucas, P. I. Cowling,

### We will discuss exploration strate

gies in chapter 15.

### Each
hex is colored according to the util

ity function value in that iteration.

### We see that the algorithm eventu

ally finds an optimal policy.

### Predictive Control for Lin

ear and Hybrid Systems. Cambridge

### Convex Op

timization. Cambridge University

### Interior-Point Filter Line-Search Al

gorithm for Large-Scale Nonlinear

### The sequence pro

gresses left-to-right, top-to-bottom.

### Robustness in Identi

fication and Control, A. Garulli, A.

### Gaussian dynamics

T(s′ | s, a) = N (Tss + Taa, Σ)

### This approach was applied to op

timizing power flow policies by N.

### Ge-
netic Algorithms Are a Competi

tive Alternative for Training Deep

### The cross entropy
method applied to the simple regu

lator problem using a multivariate

### Glas

machers, Y. Sun, J. Peters, and

### Natural Evolu

tion Strategies,’’ Journal of Machine

### Adapting Arbitrary Normal Mu

tation Distributions in Evolution

### Strategies

the Covariance Matrix

### Several
weight-
ings
constructed
using
equa

tion (10.13).

### Natural Evolution Strate

gies,’’ Journal of Machine Learning

### Mirrored
Sampling
and
Se

quential Selection for Evolution

### International Confer

ence on Parallel Problem Solving from

### I over policy pa

rameterizations for policy π(θ, s).

### Solution

The computational cost per iteration scales linearly with the number of samples.

### The expected value
is

U(θ) = E[a] =

### The policy gradient is

∇U(θ) = [1/2, 1/2]

### Pe

ters and S. Schaal, ‘‘Reinforcement

### In

ternational Conference on Machine

### Interna-
tional Conference on Machine Learn

ing (ICML), 2002.

### The update func-
tion for the natural policy gradi

ent given policy π(θ, s) for an

### Algo

rithm 12.6 provides an implementation.

### It thus follows that

∇θ′UTRPO =

### KL diver

gence of the parameterized policies over the n state samples

### High

Dimensional Continuous Control

### Lilli

crap, J. J. Hunt, A. Pritzel, N. Heess,

### Continu-
ous Control with Deep Reinforce

ment Learning,’’ in International

### This general approach was intro

duced by D. Silver, J. Schrittwieser,

### White

house, S. M. Lucas, P. I. Cowling,

### Kochen

derfer, ‘‘A Survey of Algorithms for

### Risk-Averse Dy

namic Programming for Markov

### This approach
can improve robustness in the con

text of collision avoidance. M. J.

### Robust-
ness of Optimized Collision Avoid

ance Logic to Modeling Errors,’’ in

### Point-Based Meth

ods for Model Checking in Partially

### Testing of Air-
borne Collision Avoidance Sys

tems,’’ in Digital Avionics Systems

### Part III

Model Uncertainty

### A review of the field of reinforce

ment learning is provided in M.

### Reinforcement Learning

State of the

### Ban-
dit Processes and Dynamic Alloca

tion Indices,’’ Journal of the Royal

### The Bayesian up

date function for bandit models.

### On Explore-Then

Commit Strategies,’’ in Advances in

### Kael

bling, Learning in Embedded Systems.

### This is one of many differ

ent strategies discussed by P. Auer,

### Finite-Time Analysis of the Mul

tiarmed Bandit Problem,’’ Machine

### Git

tins, K. Glazebrook, and R. Weber,

### Git

tins Index, and Its Calculation,’’ in

### The state transition and re

ward is used to update the model.

### Solution

Below we plot the expected reward-per-step for the three different strategies.

### Solution

We can rewrite the equation more generally as follows

### The Dirichlet distribution repre

sents a probability distribution over these possible transition probabilities.

### The second term can be computed using integration

P(s′ | s, b, a) =

### Many of the topics in this chap

ter are covered in greater depth by

### On the Con-
vergence of Stochastic Iterative Dy

namic Programming Algorithms,’’

### Rum

mery and M. Niranjan, ‘‘On-Line

### Learning
from
Delayed
Re

wards,’’

### Incremental
Multi-Step
Q

Learning,’’

### In

ternational Conference on Algorithmic

### Policy Invariance Under Re-
ward Transformations

Theory and

### Founda

tions of Deep Reinforcement Learning.

### Sil

ver, A. Graves, I. Antonoglou, D.

### Variations of this approach in

clude prioritizing experiences. T.

### Additional methods and applica

tions are surveyed by A. Hussein,

### Structured Predic-
tion to No-Regret Online Learn

ing,’’ in International Conference on

### Ef

ficient Reductions for Imitation

### International Confer

ence on Artificial Intelligence and

### DAgger with an extreme mix

ing value of zero.

### SMILe mixes the ex

pert into the policy during rollouts.

### Deep Inverse Op-
timal Control via Policy Optimiza

tion,’’ in International Conference on

### The aim is to
eventually produce a policy that re

sembles the expert.

### This approach attempts to find the pa

rameters of the policy that maximizes the likelihood assigned to the training examples.

### One benefit of cost-sensitive classifica

13 C. Elkan, ‘‘The Foundations of

### Inter

national Joint Conference on Artificial

### Part IV

State Uncertainty

### The transition dynamics are

T(sated | hungry, feed) = 100 %

### Kalman filter and its vari

ants is provided by Y. Bar-Shalom,

### Estima

tion with Applications to Tracking and

### Feeding determinis

tically caused the baby to be sated, so the new belief is [1, 0].

### Using a Kalman fil

ter to update the belief in a linear–

### Our particle transition function adds zero

mean Gaussian noise since we remain only approximately still.

### Solution

We seek the posterior distribution p(λ | d, α, β), which we can obtain through

### Kael

bling, M. L. Littman, and A. R.

### A policy repre

sented by a set of alpha vectors Γ.

### What belief b maxi

mizes the utility gap δ as defined by the linear program in equation (20.16)?

### Solution

The alpha vectors in Γ are shown in blue and the alpha vector α is shown in red.

### The Complexity of Markov De

cision Processes,’’ Mathematics of

### On the Undecidabil

ity of Probabilistic Planning and

### Value-
Function Approximations for Par

tially Observable Markov Decision

### A survey of point-based value it

eration methods are provided by

### Perseus

Randomized

### Value-
Function Approximations for Par

tially Observable Markov Decision

### SARSOP

Efficient Point-

### Based POMDP Planning by Ap

proximating Optimally Reachable

### The SARSOP algo

rithm built upon this work. H.

### SARSOP

Efficient Point-Based

### POMDP Planning by Approximat

ing Optimally Reachable Belief

### Robotics

Science and

### This triangu

lation method was applied to

### Com

putationally Feasible Bounds for

### Freudenthal tri

angulation.

### Computing the sim

plex vertices for a sample vector in

### These
vertices can be computed using al

gorithm 21.17.

### Computing the
barycentric coordinates for a sam

ple vector in R3.

### Computationally Feasi

ble Bounds for Partially Observed

### Consider the set of belief-utility pairs given by

V = {([1, 0], 0), ([0, 1], −10), ([0.8, 0.2], −4), ([0.4, 0.6], −6)}

### Computation

ally Feasible Bounds for Partially

### We can calculate d

d = x −v(1) = [0, 0, 0.5]

### Kael

bling, and T. Lozano-Pérez, ‘‘Belief

### Space Planning Assuming Maxi

mum Likelihood Observations,’’ in

### Sil

ver and J. Veness, ‘‘Monte-Carlo

### Interna-
tional Conference on Automated Plan

ning and Scheduling (ICAPS), 2018.

### DESPOT

Online POMDP Planning with

### The up-
per and lower bounds are main

tained by Uhi and Ulo, respectively.

### A finite state con

troller policy representation for a

### The optimization problem is then

maximize

### Solv

ing POMDPs by Searching the

### Part V

Multiagent Systems

### Sev-
eral standard introductory books
include

D. Fudenberg and J. Tirole,

### Game Theory

Analysis of

### Algo

rithmic, Game Theoretic, and Logical

### Algo

rithmic, Game Theoretic, and Logical

### Non

Cooperative Games,’’ Annals of

### Behavioral Game
Theory

Experiments in Strategic

### Ex

perimental Evidence on Players’

### Beyond
Equilibrium

Predicting Human Behavior in

### Bayesian
Framework for Parameter Analy

sis,’’ in International Conference on

### It-
erative Solution of Games by Fic

titious Play,’’ Activity Analysis of

### Orig

inal Fictitious Play,’’ Journal of

### Algo

rithmic, Game Theoretic, and Logical

### Nonlin

ear Programming and Stationary

### Adver

sarial Reinforcement Learning,’’

### An Anal

ysis of Stochastic Game Theory for

### Multiagent Reinforcement Learn

ing,’’ Carnegie Mellon University,

### What other cate

gories of policies are there?

### Exten-
sive Games and the Problem of In

formation,’’ in Contributions to the

### The model
was later introduced to the artifi

cial intelligence community. E. A.

### Decentralized
Control of Markov Decision Pro

cesses,’’ Mathematics of Operation

### An example ND

POMDP structure with five agents.

### This process is identical to dy

namic programming for POMGs, except that each agent shares the same reward.

### Pyna

dath, and S. Marsella, ‘‘Taming

### Decentralized POMDPs

Towards

### Interna

tional Joint Conference on Artificial

### Memory-Bounded
Dynamic Programming for DEC

POMDPs,’’ in International Joint

### A Heuristic Search Al

gorithm for Solving Decentralized

### This metric is often referred to as the Eu

clidean norm.

### Convex and non

convex sets.

### Not all convex func

tions have single global minima.

### Shan

non, ‘‘A Mathematical Theory of

### Taylor expansion of f about x

f (x + h) = f (x) +

### Taylor ex

pansion.

### These distributions are imple

mented in Distributions.jl. M.

### Com-
putational Complexity

A Conceptual

### NP-complete

problems that are both NP-hard and in NP.

### Re

ducibility Among Combinatorial

### Approximation The

ory of the MLP Model in Neural

### Learning Representa

tions by Back-Propagating Errors,’’

### Eval-
uating Derivatives

Principles and

### Gradient-Based
Learning
Ap

plied to Document Recognition,’’

### Schmidhu

ber, ‘‘Long Short-Term Memory,’’

### These techniques were intro

duced by I. Goodfellow, J. Pouget-

### Warde

Farley, S. Ozair, et al., ‘‘Generative

### Neuronlike Adaptive
Elements That Can Solve Diffi

cult Learning Control Problems,’’

### We use the parameters imple

mented in the OpenAI Gym. G.

### Petters

son, J. Schneider, J. Schulman, J.

### Ro

bust Airborne Collision Avoidance

### The transition dynamics are

T(sated | hungry, feed) = 100%

### The observation dynamics are

O(cry | feed, hungry) = 80%

### Simply replacing both com

ponents always incurs 2, but does not have an inspection cost.

### A history is pro

vided by W. Poundstone, Prisoner’s

### Dilem-
ma

Paradoxes of Rationality in

### Model mode

AUTOMATIC

### CachingOptimizer state

EMPTY_OPTIMIZER

### Dilemma

Paradoxes of Rationality in Game Theory,’’ The

### Robust Model Predictive Control

A Survey,’’ in

### Labeled RTDP

Improving the Convergence of Real-Time

### Behavioral Game Theory

Experiments in Strategic Interaction. Princeton

### A Sim

ple, Fast, Exact Method for Partially Observable Markov Decision Processes,’’ in

### Guided Cost Learning

Deep Inverse Optimal

### Evaluating Derivatives

Principles and Techniques of

### Mutation Distributions
in Evolution Strategies

the Covariance Matrix Adaptation,’’ in IEEE International

### Distributed Wildfire Surveillance with Au

tonomous Aircraft Using Deep Reinforcement Learning,’’ AIAA Journal on Guidance,

### Prospect Theory

An Analysis of Decision Under

### Decision Making Under Uncertainty

Theory and Application. MIT

### Probabilistic Graphical Models

Principles and Techniques.

### Search and Screening

General Principles with Historical Applications.

### SARSOP

Efficient Point-Based POMDP

### Planning with Markov Decision Processes

An AI Perspective.

### Between Human and Machine

Feedback, Control, and Computing before

### Prioritized Sweeping

Reinforcement Learning

### Taming Decentral-
ized POMDPs

Towards Efficient Policy Computation for Multiagent Settings,’’ in

### Policy Invariance Under Reward Transforma-
tions

Theory and Application to Reward Shaping,’’ in International Conference on

### Probabilistic Reasoning in Intelligent Systems

Networks of Plausible Inference.

### Markov Decision Processes

Discrete Stochastic Dynamic Programming.

### Deep
Neuroevolution

Genetic Algorithms Are a Competitive Alternative for Training

### Reinforcement Learning

An Introduction, 2nd ed. MIT

### Behavioral Game Theoretic Models

A Bayesian

### DESPOT

Online POMDP Planning with

### Bayes-adaptive Markov decision pro

cess, 320

## ADFM-20-belief-state-planning-exact.pdf

### Incre-
mental Pruning

A Simple, Fast, Ex-
act Method for Partially Observ-
able Markov Decision Processes,’’
in Conference on Uncertainty in Arti-
ficial Intelligence (UAI), 1997.

### Solution

Yes. Any POMDP can equivalently be viewed as a belief-state MDP whose state
space is the space of beliefs in the POMDP, whose action space is the same as that of the

### Solution

Recall that there are |A|(|O|h−1)/(|O|−1) possible h-step plans. Exponential growth
(nx) is faster than polynomial growth (xn), and we have better-than exponential growth
in |O| and polynomial growth in |A|. The number of plans thus increases faster with
respect to the number of observations. To demonstrate, let us use |A| = 3, |O| = 3, and
h = 3 as a baseline. The baseline has 1,594,323 plans. Incrementing the number of actions
results in 67,108,864 plans, whereas incrementing the number of observations results in
10,460,353,203 plans.

### Solution

Depending on the probability of incorrect results, we may want to perform the
same test multiple times to improve our confidence in whether the patient has the disease
or is healthy. The results of the tests are independent given the disease state.

### Suppose we have three alpha vectors

[1, 0], [0, 1], and [θ, θ], for some con-
stant θ. Under what conditions on θ can we prune alpha vectors?

### Solution

We can prune alpha vectors if θ < 0.5 or θ > 1. If θ < 0.5, then [θ, θ] is dominated
by the other two alpha vectors. If θ > 1, then [θ, θ] dominates the other two alpha vectors.

### Solution

The alpha vectors in Γ are shown in blue and the alpha vector α is shown in red.

### A policy repre

sented by a set of alpha vectors Γ.

### What belief b maxi

mizes the utility gap δ as defined by the linear program in equation (20.16)?

### Solution

The alpha vectors in Γ are shown in blue and the alpha vector α is shown in red.

## ADFM-31-neural-representations.pdf

### Eval-
uating Derivatives

Principles and

## ADFM-34-julia.pdf

### IterTools

subsets
julia> collect(subsets(X))
# iterate over all subsets

### CachingOptimizer state

EMPTY_OPTIMIZER

## ADFM-21-belief-state-planning-offline.pdf

### The iteration is

5 The relationship between QMDP
and the fast informed bound to-
gether with empirical results is dis-
cussed by M. Hauskrecht, ‘‘Value-

### SARSOP

Efficient Point-

### Robotics

Science
and Systems, 2008.

### SARSOP

Efficient Point-Based

### Robotics

Science and

### There are two actions

move left (ℓ) and move right (r). The effects of those actions are deterministic. Moving
left in s1 or moving right in s4 gives a reward of 100 and ends the game. With a discount
factor of 0.9, compute alpha vectors using QMDP. Then, using the alpha vectors, compute
the approximately optimal action given the belief b = [0.3, 0.1, 0.5, 0.1].

### SARSOP

Efficient Point-

### Based POMDP Planning by Ap

proximating Optimally Reachable

### The SARSOP algo

rithm built upon this work. H.

### SARSOP

Efficient Point-Based

### POMDP Planning by Approximat

ing Optimally Reachable Belief

### Robotics

Science and

### This triangu

lation method was applied to

### Com

putationally Feasible Bounds for

### Freudenthal tri

angulation.

### Computing the sim

plex vertices for a sample vector in

### These
vertices can be computed using al

gorithm 21.17.

### Computing the
barycentric coordinates for a sam

ple vector in R3.

### Computationally Feasi

ble Bounds for Partially Observed

### Consider the set of belief-utility pairs given by

V = {([1, 0], 0), ([0, 1], −10), ([0.8, 0.2], −4), ([0.4, 0.6], −6)}

### Computation

ally Feasible Bounds for Partially

### We can calculate d

d = x −v(1) = [0, 0, 0.5]

## ADFM-06-simple-decisions.pdf

### The
Expected
Utility
Model

Its Variants, Purposes, Evidence
and

### Exactly one of the following holds

A ≻B, B ≻A, or A ∼B.

### Utilities are like temperatures

you can com-
pare temperatures using Kelvin, Celsius, or Fahrenheit, all of which are affine
transformations of each other.

### Sn

pn]) =
n
∑
i=1
piU(Si)
(6.2)

### Artificial Intelligence

A Modern Ap-
proach, 4th ed. Pearson, 2021.

### Applications to decision networks
can be found in

S. L. Dittmer and

### Solution

Risk aversion implies that the utility function is concave, which requires that the
second derivative of the utility function is negative. The utility function and its derivatives
are computed as follows

### Solution

We are interested in computing

### Utility elicitation ap

plied to collision avoidance.

### Extensive discussion of deci

sion networks can be found in

### The utility asso

ciated with an action is equal to the sum of the values at all the utility nodes.

### Applications to decision networks
can be found in

S. L. Dittmer and

### Hidden Forces That Shape Our Deci

sions. Harper, 2008. J. Lehrer, How

### We mul

tiply both sides by 10 and get

### This transform is

ˆU(s) = U(s) −U

### Solution

EU(bring umbrella | forecast sun) = 0.2 × −0.1 + 0.8 × 0.9 = 0.7

### Solution

We are interested in computing

## ADFM-05-struct-learning.pdf

### Probabilis-
tic Graphical Models

Principles and

### Learning from Data

Artificial Intelligence and Statistics

### Inf

bayesian_score(vars, G′, D)
if y′ > y

### This textbook provides an
overview

M. J. Kochenderfer and

### Learning Bayesian Net-
works

The Combination of Knowl-
edge and Statistical Data,’’ Machine

### Solution

Of the three basic graph operations, we can only add edges. We can add any edge to
an edgeless directed acyclic graph and it will remain acyclic. There are m(m −1) = m2 −m
node pairs, and therefore that many neighbors.

### Solution

At each iteration, local search can move from the original network to a network in
its neighborhood, which is at most one edge operation from the original network. Since
there are three differences between the edges of G and G∗, performing local search from

## ADFM-26-state-uncertainty.pdf

### Solution

For any POMDP, we can define a POMG with one agent I = {1}. The states S
are identical, as are the actions A = (A1) and observations O = (O1). Thus, the state
transition, observation function, and rewards of the POMG directly follow. The Nash
equilibrium optimization only has one agent, so it results in a simple maximization of
expected value, identical to a POMDP.

### Solution

The action space for the agents can be augmented to include communication
actions. The other agents can observe these communication actions according to their
observation model.

### Solution

Agents in POMGs are often competitive, in which case there would be no incentive
to communicate with others. If their rewards are aligned to some degree, they may be
inclined to communicate.

### Solution

Recall that there are |A|(|O|d−1)/(|O|−1) possible d-step single-agent conditional
plans. We can construct a joint policy of conditional plans using every combination of these
single-agent conditional plans across agents. The number of d-step multiagent conditional
plans is
∏
i∈I
|Ai|(|Oi|d−1)/(|Oi|−1)

## ADFM-17-model-free-methods.pdf

### Rein-
forcement Learning

An Introduction,
2nd ed. MIT Press, 2018.

### Xiv

1312.5602v1.

### Solution

The incremental estimation of the mean equation is

### Solution

The Sarsa(λ) update rules are

### Rum

mery and M. Niranjan, ‘‘On-Line

### Learning
from
Delayed
Re

wards,’’

### Incremental
Multi-Step
Q

Learning,’’

### In

ternational Conference on Algorithmic

### Policy Invariance Under Re-
ward Transformations

Theory and

### Founda

tions of Deep Reinforcement Learning.

### Sil

ver, A. Graves, I. Antonoglou, D.

### Variations of this approach in

clude prioritizing experiences. T.

## ADFM-23-controller-abstracts.pdf

### It consists of the two main steps

policy evaluation
(left) and policy improvement (center), as well as the optional pruning step
(right).

### Solution

Unlike tree-based conditional plans, controllers can represent policies that can be
executed indefinitely. They do not have to grow exponentially in size with the horizon.

### Solution

Controller policy iteration is guaranteed to converge on an optimal policy in
the limit. However, the method cannot find more compact representations of optimal
controller policies that may require stochastic nodes.

### Solution

Let x′ be the new node from some iteration i, and x be a previous node from
iteration i −1.

### Solution

The idea is to create an outer loop that increments the fixed-size of the controller,
after knowing the utility of the large fixed-sized controller. First, we must compute the
large fixed-sized controller’s utility U∗= ∑s b1(s)U(x1, s) at initial node x1 and initial
belief b1. Next, we create a loop that increments the size ℓof the controller. At each step, we
evaluate the policy and compute the utility Uℓ. By our assumption, the controller returned
produces a globally optimal utility for the fixed size ℓ. Once we arrive at a utility Uℓ, if we
see that Uℓ= U∗, then we stop and return the policy.

### Solution

Computing the inverse Z−1 = (I −γTθ) is the most computationally expensive
part of the gradient step, as well as the entire gradient algorithm. The matrix Z is of size
|X × S|. Gauss–Jordan elimination requires O(|X × S|3) operations, though the 3 in the
exponent can be reduced to 2.3728639 using a state-of-the-art matrix inversion algorithm.10

## ADFM-10-policy-search.pdf

### Deep Neuroevolution

Ge-
netic Algorithms Are a Competi-
tive Alternative for Training Deep

### Xiv

1712
.06567v3. The implementation in
this section follows their relatively
simple formulation. Their formu-
lation does not include crossover,
which is typically used to mix pa-
rameterizations across a popula-
tion.

### Mu-
tation Distributions in Evolution
Strategies

the Covariance Matrix

### Xiv

1703.03864v2.

### Xiv

1703 . 03864v2. They
included other techniques as well,
including weight decay.
benefit of this technique is shown in figure 10.8.

### Solution

The computational cost per iteration scales linearly with the number of samples.

### Solution

The added Gaussian noise around the policy parameters can smooth discontinu-
ities in the original objective, which can lead more reliable optimization.

### Solution

The Hooke-Jeeves method improves a single policy parameterization, so it cannot
retain multiple policies. Both the cross entropy method and evolution strategies use search
distributions. In order to successfully represent multiple types of policies, a multi-modal
distribution would have to be used. One common multi-modal distribution is a mixture of

### Solution

The Hooke-Jeeves method evaluates the objective function at the center point ±α
along each coordinate direction. In order to guarantee improvement in the first iteration of

### Solution

We first compute the numerator of the first term from equation (10.13), for all i

### Ge-
netic Algorithms Are a Competi

tive Alternative for Training Deep

### The cross entropy
method applied to the simple regu

lator problem using a multivariate

### Glas

machers, Y. Sun, J. Peters, and

### Natural Evolu

tion Strategies,’’ Journal of Machine

### Adapting Arbitrary Normal Mu

tation Distributions in Evolution

### Strategies

the Covariance Matrix

### Several
weight-
ings
constructed
using
equa

tion (10.13).

### Natural Evolution Strate

gies,’’ Journal of Machine Learning

### Mirrored
Sampling
and
Se

quential Selection for Evolution

### International Confer

ence on Parallel Problem Solving from

### I over policy pa

rameterizations for policy π(θ, s).

### Solution

The computational cost per iteration scales linearly with the number of samples.

## ADFM-01-intro.pdf

### Artifi-
cial Intelligence

A Modern Approach,
4th ed. Pearson, 2021.

### De-
cision Making Under Uncertainty

Theory and Application. MIT Press,
2015.

### Rein-
forcement Learning

An Introduction,
2nd ed. MIT Press, 2018.

### Between Human
and Machine

Feedback, Control, and

### Search and Screen-
ing

General Principles with Historical

### Xiv

2001.01818v1.

### Xiv

1606.06565v2
.

### Optimum Con

sumption and Portfolio Rules in a

### Distributed Wildfire Surveil

lance with Autonomous Aircraft

### Using Deep Reinforcement Learn

ing,’’ AIAA Journal on Guidance,

### Evaluating the perfor

mance of a decision strategy generally involves running a batch of simulations.

### Kalligeropou

los, and N. Karcanias, ‘‘Systems,

### Cambridge Univer

sity Press, 2009.

### Between Human
and Machine

Feedback, Control, and

### Search and Screen-
ing

General Principles with Historical

### A much more thorough discus

sion is provided by Z. R. Shi, C.

### Xiv

2001.01818v1.

## ADFM-08-sequential-approx-val-functs.pdf

### Approxi-
mate Dynamic Programming

Solving
the Curses of Dimensionality, 2nd ed.

### The Elements
of Statistical Learning

Data Mining,

### The Elements of Statisti-
cal Learning

Data Mining, Inference,
and Prediction, 2nd ed. Springer Se-
ries in Statistics, 2001.

### Solution

In local approximation methods, the state-action values are the parameters. We
will have |S| × |A| = 100 × 5 = 500 parameters in θ. In global approximation methods,
the coefficients of the basis functions are the parameters. Since there are six components
in β(s, a), we will have six parameters in θ.

### Solution

The first set of weighting functions is not valid, as it violates the constraint
∑i βi(s) = 1. We can modify the weighting functions by normalizing them by their sum

### Solution

The general form for bilinear interpolation is given in equation (8.12) and repro-
duced below. To generate the interpolant, we substitute our values into the equation and
simplify

### Solution

For the given state s, we have 0 ≤x1 ≤x3 ≤x2 ≤1, and so our permutation
vector is p = [1, 3, 2]. The vertices of our simplex can be generated by starting from (0, 0, 0)
and changing each 0 to a 1 in reverse order of the permutation vector. Thus, the vertices of
the simplex are (0, 0, 0), (0, 1, 0), (0, 1, 1), and (1, 1, 1).

### The Elements
of Statistical Learning

Data Mining,

## ADFM-27-collaborative-agents.pdf

### There are three hyper edges

one in-
volving agents 1, 2, and 3; another
involving agents 3 and 4; and an-
other involving agent 5 on its own.

### Solution

Dec-POMDPs are fully-cooperative. Multi-robot domains, such as search and
rescue, require the robots to work together as a team. The engineers have full control of
the executable policies of each robot. Conversely, in a competitive POMG (or even MG),
the algorithms compute policies for all agents. However, in competitive settings, we likely
only have control over one agent’s policy. Additionally, the model realistically captures the
limited sensors and sensor models in robotics, as in POMDPs, except in the multiagent
setting.

### Solution

Full joint observability means if agents were to share their individual observations,
then the team would know the true state. This can be done offline during planning. Thus
in Dec-MDPs, the true state is essentially known during planning. The issue is that it
requires agents to share their individual observations, which cannot be done online during
execution. Therefore, planning still needs to reason about the uncertain observations made
by the other agents.

### Solution

We can assume free communication for planning. At each time step t, all agents
know at and ot, allowing us to maintain a multiagent belief bt, resulting in an MPOMDP.

### Solution

For an agent i, the best response controller Xi, ψi, and ηi can be computed by a
nonlinear program. The program is similar to section 27.6, except that X−i, ψ−i, and η−i

## ADFM-24-multiagent-reasoning.pdf

### Sev-
eral standard introductory books
include

D. Fudenberg and J. Tirole,

### Game Theory

Analysis of

### Multiagent Systems

Algo-
rithmic, Game Theoretic, and Logical

### Multiagent Systems

Algo-
rithmic, Game Theoretic, and Logical

### Behavioral Game
Theory

Experiments in Strategic

### Beyond
Equilibrium

Predicting Human Behavior in

### Solution

Suppose the action space of each agent consists of the negative real numbers
and their reward is equal to their action. Since no greatest negative number exists, a Nash
equilibrium cannot exist.

### Solution

Here is one example.16 Suppose we have two aircraft on a collision course, and
16 This example comes from M. J.

### Decision Making Un-
der Uncertainty

Theory and Applica-
tion. MIT Press, 2015.

### Solution

Given any Nash equilibrium π, define a correlated joint policy π(a) such that

### Solution

Consider the following game in which two people want to go on a date but have
a conflicting preference on what kind of date, in this case a dinner or a movie.

### Multiagent Systems

Algo-
rithmic, Game Theoretic, and Logical

### Solution

It converges to the Nash equilibrium of $2.

### Algo

rithmic, Game Theoretic, and Logical

## ADFM-03-inference.pdf

### Solution

We first expand the inference expression using the definition of conditional
probability.

### Solution

We first expand the inference expression using the definition of conditional
probability.

### Solution

We have P(c1
3 | x1
2, x0
3, x1
4) = 1 because x1
2, x0
3, x1
4 makes the third clause true, and

### Solution

For likelihood-weighted sampling, the sample weights are the product of the
distributions over evidence variables conditioned on the values of their parents. Thus, the
general form for our weights is P(b0 | a)P(d1 | b0, c). We then match each of the values for
each sample from the joint distribution.

## ADFM-25-sequential-problems.pdf

### Solution

Markov games generalize simple games. For any simple game with I, A, R, we
can construct a Markov game by just having a single state that self-loops. In other words,
this Markov game has S = {s1}, T(s1 | s1, a) = 1, and R(s1, a) = R(a).

### Solution

No, if given fixed policies of other agents π−i, a deterministic best response is
sufficient to obtain the highest utility. The best response can be formulated as solving an

### Solution

The algorithm presented in this chapter performs a single backup for the visited
state s and all joint actions a. This approach has the benefit of being relatively efficient
because it is a single backup. Updating all joint actions at that state results in exploring
actions that were not observed. The drawback of this approach is that we may need to do
this update at all states many times to obtain a suitable policy.

## ADFM-07-sequential-exact-solns.pdf

### Markov Decision Processes

Discrete Stochastic Dynamic Program-
ming. Wiley, 2005.

### Eye of the Hurricane

an Autobiography. World Scientific,
1984.

### Solution

We can prove that the infinite sequence of discounted constant rewards converges
to r/(1 −γ) in the following steps

### Solution

The optimal value of U∗(s1) is associated with following the optimal policy π∗

### Solution

We can compute U(s), π(s), and A(s, a) using the following equations

### Solution

We are given ∥U −U∗∥∞< ϵ. The worst-case deviation between the policy
extracted from U and an optimal policy occurs when the policy from U has value just
under U + ϵ and the true optimal policy has value just above U −ϵ. In this case, Uπ −U∗<

### Solution

The problem in example 7.4 has quadratic reward that penalizes deviations
from the origin. The longer the horizon, the greater the negative reward is that can be
accumulated, making it more worthwhile to reach the origin sooner.

### Solution

Let U be the value function produced by value iteration. We want to show that

### Solution

A matrix M is positive definite if for all non-zero x, that x⊤Mx > 0. In equa-
tion (7.31), every Vi is negative semi-definite, so w⊤Vw ≤0 for all w. Thus, these q terms
are guaranteed to be non-positive. This should be expected, as in LQR problems it is
impossible to obtain positive reward, and we seek instead to minimize cost.

### Intro

duction to Algorithms, 3rd ed. MIT

### The sec

ond version handles the case when

### Lin

ear Programming, Foundations and

### Polynomial
Algo

rithms in Linear Programming,’’

### Bert

sekas, Dynamic Programming and

### Solution

We can compute U(s), π(s), and A(s, a) using the following equations

### SE

U(s3) = max(10, 10, 10, 10, 10, 10) = 10

### Solution

Let U be the value function produced by value iteration. We want to show that

## ADFM-14-policy-validation.pdf

### Xiv

2005.02979.

### The
adversary has two objectives to balance

minimizing our return and maximizing
the likelihood of the resulting trajectory according to our transition model. We
can transform our original problem into an adversarial problem. The adversarial
state space is the same as in the original problem, but the adversarial action space
is the state space of the original problem. The adversarial reward is

### Solution

The log-likelihood of the trajectory is

### Solution

The collision probability estimate is

### Solution

The optimal proposal distribution is

### Solution

The weight is p(x)/p∗(x) = 0.2/1. Since f (0.3) = −1, the estimate is −0.2, which
is the exact answer.

### Solution

Only π1 is dominated by other policies. Hence, π2, π3, and π4 are on the Pareto
frontier.

### Point-Based Meth

ods for Model Checking in Partially

### Testing of Air-
borne Collision Avoidance Sys

tems,’’ in Digital Avionics Systems

## ADFM-15-explore-exploit.pdf

### Reinforcement Learning

State of the

### Solution

Below we plot the expected reward-per-step for the three different strategies. The
effectiveness of the parameterization depends on the problem horizon, so several different
depths are shown as well.

### Solution

Below we plot the expected reward-per-step for the three different strategies.

### Solution

There are many different multi-armed bandit problems. Consider, for example, a
news company that would like to maximize interaction (clicks) on articles on its website.

### Solution

A lower bound on our posterior probability of winning ρ can be computed
assuming all pulls result in a loss, e.g. ℓ= 10 and w = 0. We can similarly compute an
upper bound ρ assuming all pulls result in a win, e.g. w = 10 and ℓ= 0. Thus, the bounds
are

### Solution

Since x < ϵ1 in the first iteration, we explore and choose a with probability 0.5
and b with probability 0.5. At the ninth iteration, ϵ9 = α8ϵ1 ≈0.129. Since x > ϵ9, we
exploit and select a.

### Solution

We can rewrite the equation more generally as follows

### Solution

We begin by counting the number of solutions to w1 + ℓ1 + · · · + wn + ℓn = k,
where 0 ≤k ≤h. If n = 2 and k = 6, one solution is 2 + 0 + 3 + 1 = 6. For our counting
argument, we will use tally marks to represent our integers. For example, we can write a
solution like 2 + 0 + 3 + 1 = ||++|||+| = 6. For general values for n and k, we would have
k tally marks and 2n −1 plus signs. Given that many tally marks and plus signs, we can
arrange them in any order we want. We can represent a solution as a string of k + 2n −1
characters, where a character is either | or +, with k of those characters being |. To obtain
the number of solutions, we count the number of ways we can choose k positions for |
from the set of k + 2n −1 positions, resulting in

### Git

tins, K. Glazebrook, and R. Weber,

### Git

tins Index, and Its Calculation,’’ in

### The state transition and re

ward is used to update the model.

### Solution

Below we plot the expected reward-per-step for the three different strategies.

### Solution

We can rewrite the equation more generally as follows

## ADFM-30-complexity.pdf

### Com-
putational Complexity

A Conceptual

### NP

problems whose solutions can be verified in polynomial time,

### NP-hard

problems that are at least as hard as the hardest problems in NP, and

### NP-complete

problems that are both NP-hard and in NP.

### NP-complete

problems that are both NP-hard and in NP.

### Re

ducibility Among Combinatorial

## ADFM-09-sequential-planning.pdf

### Inf

sqrt(log(Ns)/Nsa)

### Only two states are labeled in
this iteration

the hidden terminal
state and the state with a hexag-
onal border. Both the exploratory
run and the labeling step update
the value function.

### Robust Model Predictive Control

A Survey,’’ in Robustness in Identi-
fication and Control, A. Garulli, A.

### Modulating Robustness in Con-
trol Design

Principles and Algo-
rithms,’’ IEEE Control Systems Mag-
azine, vol. 33, no. 2, pp. 36–51, 2013.
of multi-forecast model predictive control, which is a type of hindsight optimization15

### Solution

In the worst case, branch and bound will never prune, resulting in a traversal of
the same search tree as forward search with the same complexity.

### Solution

Create a new heuristic h(s) = min{h1(s), h2(s)} and use it instead. This strictly
improves a heuristic search algorithm. Moreover, this new heuristic is guaranteed to be
admissible. Both h1(s) ≥U∗(s) and h2(s) ≥U∗(s) imply that h(s) ≥U∗(s).

### Solution

Would could define a new heuristic h3(s) = max(h1(s), h2(s)) to get a potentially
admissible or a ‘‘less-inadmissible’’ heuristic. It may be slower to converge, but it may be
more likely to not miss out on a better solution.

### Solution

We need
|S′| = |S|
1
d
and
|A′| = |A|
1
d

### Solution

The computational complexity of forward search is given by O

(|S||A|)d
, which

### Solution

Forward search enumerates over all possible future actions. It may return different
actions if there are ties in their expected utilities. Branch and bound maintains the same
optimality guarantee over the horizon as forward search by sorting by upper bound. The
ordering of the action space can affect branch and bound’s visitation rate when the upper
bound produces the same expected value for two or more actions. Below we show this
effect on the modified mountain car problem from example 9.2. The plot compares the
number of states visited in forward search to that of branch and bound for different action
orderings to depth 6. Branch and bound consistently visits far fewer states than forward
search, but action ordering can still affect state visitation.

### Solution

No. While the computational complexities are identical at O

|S|d|A|d
, forward
search will branch on all states in the state space, while sparse sampling will branch on
|S| randomly sampled states.

### Robustness in Identi

fication and Control, A. Garulli, A.

### Gaussian dynamics

T(s′ | s, a) = N (Tss + Taa, Σ)

### This approach was applied to op

timizing power flow policies by N.

## ADFM-18-imitation-learning.pdf

### D of expert state-action
pairs

maximize
θ
∏
(s,a)∈D
πθ(a | s)
(18.1)

### Guided
Cost Learning

Deep Inverse Op-
timal Control via Policy Optimiza-
tion,’’ in International Conference on

### Solution

In imitation learning, we are generally limited to a relatively small set of expert
demonstrations. The distribution P(a | s) has (|A| −1)|S| independent parameters that
must be learned, which is often prohibitively large. Expert demonstrations typically only
cover a small portion of the state-space. Even if P(a | s) can be reliably trained for the
states covered in the provided dataset, the resulting policy would be untrained in other
states. Using a feature function allows for generalization to unseen states.

### Solution

Maximum margin inverse reinforcement learning extracts binary features from
the expert data and seeks a reward function whose optimal policy produces trajectories
with the same frequencies of these binary features. There is no guarantee that multiple
policies do not produce the same feature expectations. For example, an autonomous car
that only makes left lane changes could have the same lane change frequencies as an
autonomous car that only makes right lane changes.

### Solution

If we use non-binary features, then it is possible that some features can get
larger than others, incentivizing the agent to match those features over those that tend
to be smaller. Scale is not the only issue. Even if all features are constrained to lie within
[0, 1], then a policy that consistently produces φ(s, a)1 = 0.5 will have the same feature
expectations as one that produces φ(s, a)1 = 0 half the time and φ(s, a)1 = 1 half the time.

### Solution

These distributions over relative duration are analogous to distributions over
trajectories for this elevator problem. In applying the principle of maximum entropy, we
prefer the distribution with most entropy. Hence, we would choose policy B, which in
being most uniform, has the greatest entropy.

## ADFM-28-math.pdf

### Taylor expansion of f about x

f (x + h) = f (x) +

### Taylor ex

pansion.

## ADFM-29-prob-distributions.pdf

### Xiv

1907.08611v1.

## ADFM-32-search.pdf

### Our implementation does use two
value functions

the heuristic for
guiding the search and an approxi-
mate value function for evaluating
terminal states.

## ADFM-12-policy-grad-optm.pdf

### Xiv

1707.0634
7v2.

## ADFM-02-representation.pdf

### Probability
Theory

The Logic of Science. Cam-
bridge University Press, 2003.

### Probabilistic Graphi-
cal Models

Principles and Techniques.

### Probabilis-
tic Graphical Models

Principles and

### Prob-
abilistic Reasoning in Intelligent Sys-
tems

Networks of Plausible Inference.

### Solution

One solution is U([−10, −10], [−5, 10]), U([−5, 0], [0, 10]), U([−5, −10], [0, 0]),

### Solution

We start with the most common probabilities, 0.13, which occurs when Z = 0
and Y = 0, and 0.05, which occurs when Z = 0 and Y = 1. We choose to make Z the root
of our decision tree and when Z = 0 we continue to a Y node. Based on the value of Y we
branch to either 0.13 or 0.05. Next, we continue with cases when Z = 1. The most common
probabilities are 0.02, which occurs when Z = 1 and X = 0, and 0.12, which occurs when

### Solution

For a Gaussian distribution over four variables (n = 4) with independence
assumptions, we need to specify n + n = 2n = 8 independent parameters; there are four
parameters for the mean vector and four parameters for the covariance matrix (which is
equivalent to the mean and variance parameters of four independent univariate Gaussian
distributions). For a Gaussian distribution over four variables without independence
assumptions, we need to specify n + n(n + 1)/2 = 14 independent parameters; there
are four parameters for the mean vector and ten parameters for the covariance matrix.

### Solution

If we have a piecewise-constant density with m bins edges, then there are m −1
bins and m −2 independent parameters. For this problem, there will be (4 −2) + (7 −
2) + (3 −2) = 8 independent parameters.

### Solution

The number of independent parameters for each node is equal to (k −1)km where
k is the number of values the node can take on and m is the number of parents that the
node has. The variable A has 3, B has 12, C has 48, D has 3, E has 12, and F has 48 and
independent parameters. There are 126 total independent parameters for this Bayesian
network.

### There are two paths from A to E

A →D →E and A →C →E. There is
d-separation along the second path, but not the first. Hence, A is not d-separated from E
given C.

### Solution

Paths from B to A can only be d-separated given A. Paths from B to D can only be
d-separated given D. Paths from B to E and simultaneously F, G, and H can be efficiently
d-separated given E. Paths from B to C are naturally d-separated due to a v-structure;
however, since E must be contained in our Markov blanket, paths from B to C given E can
only be d-separated given C. So, the Markov blanket of B is {A, C, D, E}.

### Solution

There is a direct arrow from A to B, which indicates that independence is not
implied. However, this does not mean that they are not independent. Whether or not A
and B are independent depends on the choice of conditional probability tables. We can
choose the tables so that there is independence. For example, suppose both variables are
binary and P(a) = 0.5 is uniform and P(b | a) = 0.5. Clearly, P(A)P(B | A) = P(A)P(B),
which means they are independent.

### An example Gaus

sian mixture model.

### Example joint distribu

tion involving binary variables X,

### Named for the English statis

tician and Presbyterian minister

### Probabilistic Graphi-
cal Models

Principles and Techniques.

### Probabilis-
tic Graphical Models

Principles and

### Named after the Russian math

ematician Andrey Andreyevich

### Prob-
abilistic Reasoning in Intelligent Sys-
tems

Networks of Plausible Inference.

### Solution

One solution is U([−10, −10], [−5, 10]), U([−5, 0], [0, 10]), U([−5, −10], [0, 0]),

## ADFM-04-param-learning.pdf

### Machine
Learning

A Probabilistic Perspective.

### Solution

Since our first toss lands on heads, we have m = 1 successes and n = 1 trials.

### Solution

Assuming the marginal distribution over X1 is a Gaussian, we can compute the
marginal mode, which is the mean parameter of the Gaussian distribution

### The ith component con

sists of a qi × ri matrix of counts.

### A comprehensive introduc

tion and review is provided by G.

### Ver

beke, eds., Handbook of Missing Data

### Example data with con

tinuous values.

### Expectation-maximization was in

troduced by A. P. Dempster, N. M.

### Z for that instance

P(zi | X = 4.2) =

## ADFM-19-beliefs.pdf

### Solution

Yes. The POMDP formulation extends the MDP formulation by introducing state
uncertainty in the form of the observation distribution. Any MDP can be framed as a

### Solution

Yes, overconfidence in a belief can be a problem when the models or belief updates
do not perfectly represent reality. The overconfident belief may have converged on a state
that does not match the true state. Once the vehicle moves again, new observations may
be inconsistent with the belief and result in poor estimates. To help address this issue, we
can require that the values of the diagonal elements of the covariance matrix be above
some threshold.

### Solution

We seek the posterior distribution p(λ | d, α, β), which we can obtain through

### Solution

Rejection sampling requires repeatedly sampling the transition and observation
functions until the sampled observation matches the true observation. The probability
of sampling any particular value in a continuous probability distribution is zero, making
rejection sampling run forever. In practice, we would use a finite representation for contin-
uous values such as 64-bit floating point numbers, but rejection sampling can run for an
extremely long time for each particle.

### Solution

The particle filter with adaptive injection injects new particles when νwfast/wslow
is less than 1. Spelunker Joe assumes perfect observations and has a belief with particles
that match his current observation. Thus, every particle has a weight of 1, and so both
wfast and wslow are 1. It follows that wfast/wslow is always 1, leading to no new particles.

### Solution

Particle injection was designed to inject particles when the current observations
have lower likelihood than a historic trend over the observation likelihood. Thus, injection
typically only occurs when the short-term estimate of the mean particle weight wfast is less
than the long-term estimate of the mean particle weight wslow. If ν < 1, then particles can
still be generated even if wfast ≥wslow, despite indicating that current observations have
higher likelihood than the past average.

### Solution

The transition and observation dynamics can be written in linear form as follows
"
x′

### Solution

Since we have a two-dimensional Gaussian distribution and we are given λ = 2,
we need to compute 2n + 1 = 5 sigma points. We need to compute the square-root matrix

### Solution

The transformed sigma points are

## ADFM-13-actor-critic-methods.pdf

### Xiv

1506.02438v6.
difference residual has low variance but introduces bias due to a potentially

### Xiv

1509.02
971v6.

### Solution

The Monte Carlo tree search expands a tree based on visited states. The cart-pole
problem has a continuous state space, leading to a search tree with an infinite branching
factor. Use of this algorithm would require adjusting the problem, such as discretizing the
state space.

### Solution

Approximation using a temporal difference residual is more computationally
efficient than using a sequence of rollouts. Temporal difference residual approximation has
low variance but high bias due to using the critic value function Uφ as an approximator of
the true value function Uπθ. On the other hand, rollout approximation has high variance

### Solution

We need to calculate two gradients. For the actor we need to compute ∇φQφ(s, a),
while for the critic we need to compute ∇aQφ(s, a).

### Lilli

crap, J. J. Hunt, A. Pritzel, N. Heess,

### Continu-
ous Control with Deep Reinforce

ment Learning,’’ in International

### This general approach was intro

duced by D. Silver, J. Schrittwieser,

### White

house, S. M. Lucas, P. I. Cowling,

## ADFM-33-problems.pdf

### Residual Algo-
rithms

Reinforcement Learning
with Function Approximation,’’ in

### Xiv

1606.01540v1.

### Decision Making Un-
der Uncertainty

Theory and Applica-
tion. MIT Press, 2015.

### Dilem-
ma

Paradoxes of Rationality in

### The states contain the locations of each agent

S = S1 × · · · × S|I|, with each Si

## ADFM-22-belief-state-planning-online.pdf

### Robotics

Science and Systems, 2010.

### DESPOT

Online POMDP Planning with

## ADFM-16-model-based-methods.pdf

### Prioritized Sweeping

Reinforce-
ment Learning With Less Data
and Less Time,’’ Machine Learning,
vol. 13, no. 1, pp. 103–130, 1993.

### Solution

A lower bound on the number of updates performed in an iteration of prioritized
sweeping is 1. This could occur during our first iteration using a maximum likelihood
model, where the only nonzero entry in our transition model is T(s′ | s, a). Since no
state-action pairs (s−, a−) transition to s, our priority queue would be empty and thus the
only update performed would be for U(s).

### Solution

For each state and action, we specify a Dirichlet distribution over the transition
probability parameters, so we will have |S||A| Dirichlet distributions. Each Dirichlet
is specified using |S| independent parameters. In total, we have |S|2|A| independent
parameters.

### Solution

Dir(θ(s2,a1) | [2, 1, 2])

