![ADM-ch17-geometry-minkowski-sum](ADM-ch17-geometry-minkowski-sum.best.png)

- **Input**
  - The input consists of point sets or polygons A and B with n and m vertices respectively.
  - The objective is to compute the Minkowski sum defined as A + B = {x + y | x ∈ A, y ∈ B}.
  - Minkowski sums are used in geometric operations such as fattening objects for motion planning and shape simplification.
  - See [CGAL Minkowski Sum Package](https://www.cgal.org) for implementations.

- **Problem Description**
  - The Minkowski sum is the vector sum of points from two polygons positioned in a coordinate system.
  - This sum represents the union of all translations of polygon A by points from polygon B.
  - Key applications include motion planning for polygonal robots and smoothing boundaries by convolving with circles.
  - Further theoretical treatment can be found in [dBvKOS00, O’R01].

- **Challenges in Computing Minkowski Sums**
  - Object representation affects computation: rasterized images allow simpler pixel-based summation, explicit polygons require more complex handling.
  - Offsetting by a fixed amount is common, achieved by summing with a disk of radius t, resulting in boundaries with circular arcs and line segments.
  - Polygon convexity strongly influences complexity: convex polygons yield O(n+m) algorithms, while nonconvex cases may have quadratic or quartic size complexity.
  - Nonconvex sums may create or destroy holes unpredictably.

- **Approaches to Computation**
  - Triangulation method: triangulate both polygons, compute sums pairwise for triangles, then union results using plane sweep algorithms.
  - Convex polygons permit efficient edge-based tracing to compute sums.
  - Decomposition of nonconvex polygons into convex pieces usually improves efficiency over full triangulation.
  - See Section 17.8 and 17.11 for plane sweep and convex partitioning techniques.

- **Implementations and Algorithms**
  - The CGAL library offers robust implementations for Minkowski sums of arbitrary polygons and offsetting.
  - 3D Minkowski sums of convex polyhedra are discussed and implemented in [FH06] with source available online.
  - Efficient translational motion planning algorithms based on Minkowski sums are described in [KS90].
  - Optimal convex decomposition for Minkowski sums is studied by Agarwal et al. [AFH02].

- **Combinatorial Complexity and Research**
  - The complexity of Minkowski sums of convex polyhedra in 3D is fully resolved in [FHW07].
  - Minkowski sums for nonconvex polygons are typically complex and possibly large in size.
  - Fast algorithms for specific Minkowski sum cases are available in [KOS91, Sha87].
  - Research emphasizes the importance of decomposition methods on practical computational efficiency.
