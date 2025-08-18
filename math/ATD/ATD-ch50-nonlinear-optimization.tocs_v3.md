![ATD-ch50-nonlinear-optimization](ATD-ch50-nonlinear-optimization.best.png)

- **Introduction to Nonlinear Optimization**
  - Investigates local extrema of functions on subsets defined by equational constraints.
  - Recalls necessary conditions with Lagrange multipliers and convex assumptions.
  - Introduces the notion of tangent cones for non-convex constraint sets.
  - Recommends foundational texts including Bertsekas, Boyd, Luenberger, and others.

- **50.1 The Cone of Feasible Directions**
  - Defines cones with apex at a point, foundational to describing variations at boundary points.
  - Introduces the cone of feasible directions at point u in a subset U.
  - Shows construction via limits of unit chords from sequences converging to u within U.
  - Establishes that cones of feasible directions contain velocities of curves through u.
  - States that the cone is closed and provides inequality conditions involving the function J's derivative for local minima.

- **50.2 Active Constraints and Qualified Constraints**
  - Defines active constraints as those tight at point u, and inactive otherwise.
  - Introduces the convex cone C*(u) formed by linearizations of active constraints at u.
  - Establishes that cone of feasible directions C(u) is contained in C*(u), but not always equal.
  - Defines qualification conditions that ensure C(u) = C*(u), involving existence of vectors satisfying linear inequalities related to gradients.
  - Explains qualification fails in singular or self-intersecting cases.
  - Recalls H-polyhedra (H-cones) and their representation.
  - Provides examples illustrating nonconvexity and qualification.

- **50.3 The Karush–Kuhn–Tucker Conditions**
  - States necessary optimality conditions in inequalities defined by constraints with qualification.
  - Uses Farkas lemma and its Hilbert space extension (Farkas–Minkowski) to prove existence of nonnegative multipliers λi.
  - Defines KKT conditions as a system including complementary slackness and multiplier nonnegativity.
  - Applies conditions to equality and inequality constrained problems, including affine constraints.
  - Provides classical formulations of KKT for standard linear programs and convex problems.
  - States that when J and constraints are convex and constraints qualified, KKT conditions are both necessary and sufficient.
  - Introduces Slater’s conditions as sufficient qualification condition for convex constraints.
  - Shows that equality constraints are generally not qualified if nonaffine.
  - Discusses examples including interior point method and constraint qualifications.
  - Explains Newton methods with equality constraints and conditions on KKT matrices.

- **50.4 Equality Constrained Minimization**
  - Focuses on minimizing convex differentiable functions subject to linear equality constraints.
  - Formulates the KKT system of linear equations combining primal and dual feasibility.
  - Describes conditions for invertibility of the KKT matrix involving definiteness on kernel of A.
  - Provides explicit solution via Schur complement when KKT matrix is invertible.
  - Discusses numerical algorithms including Newton’s method variants.
  - Emphasizes importance of positive definiteness of P matrix or augmented system.
  - Applies to quadratic functionals and describes practical solution methods.

- **50.5 Hard Margin Support Vector Machine; Version I**
  - Describes problem of separating two disjoint finite sets in Rn by a hyperplane maximizing minimal distances.
  - Defines margin as minimal distance from data points to separating hyperplane.
  - Formulates as maximizing margin δ subject to distance constraints and norm inequality kwk ≤ 1.
  - Proves that optimal solution always has kwk = 1.
  - Shows uniqueness of maximal margin hyperplane under separability.
  - Expresses maximum margin in terms of a ratio function ρ(w) over a convex set.
  - Illustrates separation problem and non-separability counterexamples.

- **50.6 Hard Margin Support Vector Machine; Version II**
  - Reformulates hard margin SVM to minimize squared norm kwk^2/2 subject to affine linear inequalities.
  - Explains equivalence by scaling constraints and objective function.
  - Provides matrix formulations for constraints and objective function.
  - Applies KKT conditions to derive expressions for w and b in terms of Lagrange multipliers.
  - Discusses support vectors corresponding to active constraints where multipliers are nonzero.
  - Presents example with two blue and two red points illustrating matrix formulation.
  - Explains solution approaches including solving linear systems if support vectors are known.
  - Notes that only support vectors contribute to solution and explains determination of optimal b.
  - Provides explicit solution in simplest case p = q = 1 as bisector hyperplane.
  - Visualizes geometric interpretation of support vectors, margin, and separating slabs.
  - Summarizes implications for margin width and placement of support vectors on parallel hyperplanes.

- **50.7 Lagrangian Duality and Saddle Points**
  - Introduces Lagrangian dual function G(µ) obtained by minimizing L(v, µ) over v for fixed multipliers µ.
  - Describes two-step solution: (1) solve unconstrained minimization in v for each µ; (2) maximize G(µ) over µ ≥ 0.
  - Defines saddle points as points where L(u, λ) is simultaneously minimum in u and maximum in λ.
  - Proves basic saddle point property equating max-min and min-max of L.
  - Shows that solutions of primal problem correspond to saddle points of Lagrangian and vice versa under convexity and qualification.
  - Demonstrates that primal solutions yield complementary slackness and zero duality gap.
  - Establishes equivalences of constrained minimization, saddle points of L, and dual function maximization.
  - Prepares foundation for duality theory and solution methods based on Lagrangian dual.
