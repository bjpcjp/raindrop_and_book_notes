![ATD-ch51-nonlinear-opt-subgradients-subdifferentials](ATD-ch51-nonlinear-opt-subgradients-subdifferentials.best.png)

- **51.1 Extended Real-Valued Convex Functions**
  - Extended real-valued functions map from \(\mathbb{R}^n\) to \(\mathbb{R} \cup \{-\infty, +\infty\}\).
  - The epigraph of such a function generalizes the notion of convexity and includes infinite values.
  - Proper convex functions have nonempty epigraphs with no vertical lines, ensuring well-defined domains.
  - Lower semi-continuity corresponds to the epigraph being a closed set.
  - The section relies heavily on Rockafellar [136] for detailed proofs and theory.

- **51.2 Subgradients and Subdifferentials**
  - Subgradients generalize gradients for convex functions not necessarily differentiable at every point.
  - The subdifferential \(\partial f(x)\) is the set of all subgradients at \(x\), always a closed convex set.
  - A convex function attains a minimum at \(x\) if and only if \(0 \in \partial f(x)\).
  - Subgradients correspond geometrically to normals of supporting hyperplanes to the epigraph at \((x, f(x))\).
  - Detailed study of supporting hyperplanes and normal cones is essential; Rockafellar [136] is a key reference.

- **51.3 Basic Properties of Subgradients and Subdifferentials**
  - One-sided directional derivatives exist for all directions at points with finite function values.
  - The directional derivative function is positively homogeneous and convex.
  - A vector \(u\) is a subgradient at \(x\) if the directional derivative dominates the linear form defined by \(u\).
  - The subdifferential is nonempty at points in the relative interior of the domain.
  - Classic convex analysis results are stated from Rockafellar [136] without proof.

- **51.4 Additional Properties of Subdifferentials**
  - The normal cone to a sublevel set at a point relates to the convex cone spanned by the subdifferential.
  - Subdifferentials over compact subsets of the relative interior are bounded, implying Lipschitz continuity.
  - The conjugate function properties link subdifferentials of \(f\) and \(f^*\).
  - Approximate subgradients (ε-subgradients) generalize subgradients and relate to conjugates of localized functions.
  - Rockafellar [136] and Bertsekas [17, 19] provide further elaboration on these concepts.

- **51.5 The Minimum of a Proper Convex Function**
  - The minimum set of a proper convex function is convex and closed iff the function is closed.
  - A point belongs to the minimum set iff zero is in the subdifferential at that point.
  - Directions of recession characterize when the minimum is attained or finite.
  - Adding a strictly convex quadratic to a proper closed convex function ensures a unique minimum.
  - The section's core theorem and examples appear in Rockafellar [136], including key optimization implications.

- **51.6 Generalization of the Lagrangian Framework**
  - Lagrangian duality extends to ordinary convex programs with proper convex and possibly nondifferentiable functions.
  - The KKT conditions generalize using subdifferentials replacing gradients.
  - Qualification conditions (e.g., Slater’s condition) ensure existence of Lagrange multipliers and zero duality gap.
  - The dual function is concave but may take infinite values, requiring careful interpretation.
  - Theorems and duality properties are detailed in Rockafellar [136], Part VI, Sections 28 and 29.

- **51.7 Summary**
  - The chapter summarizes key definitions and results on extended real-valued convex functions, subgradients, subdifferentials, and optimization.
  - Emphasizes the role of subdifferentials to extend differentiability and optimization theory.
  - Highlights the linkage between epigraph geometry and convex analysis.
  - Recommends Rockafellar [136] for comprehensive foundations and related frameworks by Bertsekas.
