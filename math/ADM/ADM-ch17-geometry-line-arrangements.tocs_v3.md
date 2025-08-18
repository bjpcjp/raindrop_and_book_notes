[Representative image](ADM-ch17-geometry-line-arrangements.best.png)

- **17.15 Maintaining Line Arrangements**
  - A fundamental problem is constructing the regions formed by intersections of n lines or segments.
  - Incremental algorithms build arrangements by inserting lines one at a time, maintaining O(n²) total insertion time due to the zone theorem.
  - The zone theorem states the kth inserted line cuts through O(k) cells and boundary edges in the arrangement.
  - Duality transformations convert points to lines and vice versa, enabling use of line arrangements for point problems like degeneracy testing.
  - Robust implementations exist in CGAL and other libraries; further details and proofs appear in references such as [Edelsbrunner's work](https://www.cambridge.org/core/books/algorithms-in-combinatorial-geometery/3456270B07D53A904C6F292BB76F1693).

- **17.16 Minkowski Sum**
  - The Minkowski sum of two polygons A and B is defined as A + B = {x + y | x ∈ A, y ∈ B}, representing a geometric convolution.
  - Applications include fattening obstacles in motion planning and smoothing shapes via boundary convolution.
  - Computing Minkowski sums depends on whether inputs are raster images or explicit polygons, with distinct algorithmic approaches.
  - Positioning of polygons on a coordinate system is necessary before sum computation.
  - Further reading on Minkowski sums and their applications is available in the referenced sections of the document (e.g., 17.14 Motion Planning) and foundational geometry texts.
