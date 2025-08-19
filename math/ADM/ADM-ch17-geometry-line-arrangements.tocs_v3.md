![ADM-ch17-geometry-line-arrangements](ADM-ch17-geometry-line-arrangements.best.png)

- **17.15 Maintaining Line Arrangements**  
  - A line arrangement decomposes the plane into regions defined by n lines and line segments.  
  - Incremental construction inserts lines one at a time, traversing affected cells efficiently using the zone theorem.  
  - The arrangement size grows quadratically, with total construction time O(n²).  
  - Applications include degeneracy testing and maximizing satisfied linear constraints by analyzing arrangement cells.  
  - Duality transforms points to lines and vice versa, enabling point problems to be solved with arrangements.  
  - Sweepline algorithms traverse each face once by sorting intersection points and sweeping left to right.  
  - CGAL provides a robust C++ implementation for arrangements of curves; Arrange supports polygon arrangements with randomized incremental algorithms.  
  - Foundational references include [Edelsbrunner 1987](https://example.org), [Agarwal and Sharir 2000], and practical CGAL discussion [FWH04, HH00].  
- **17.16 Minkowski Sum**  
  - The Minkowski sum of point sets or polygons A and B combines points x ∈ A and y ∈ B by vector addition x + y.  
  - Minkowski sums fatten objects for applications such as motion planning, shape simplification, and boundary smoothing.  
  - The sum can be understood as the union of all translations of A by every point in B.  
  - Rasterized input suggests a pixel-based approach initializing a matrix of sufficient size.  
  - Related applications include polygonal motion planning and shape simplification techniques detailed in Sections 17.14 and 17.12.
