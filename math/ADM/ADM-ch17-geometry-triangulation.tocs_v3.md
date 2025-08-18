[Representative image](ADM-ch17-geometry-triangulation.best.png)

- **17.3 Triangulation**
  - A triangulation partitions the interior of a point set or polyhedron into triangles or tetrahedra.  
  - It is fundamental in computational geometry with applications in finite element analysis and computer graphics.  
  - Surface interpolation uses triangulation to estimate values at arbitrary points by interpolating within a triangle.  
  - Triangulations are built by adding nonintersecting chords between vertices until none can be added.  
  - See [Triangle](http://www.cs.cmu.edu/~quake/triangle.html) for a leading 2D triangulation implementation.

  - **Input Types and Convex Hull Construction**
    - Input can be a point set or a polygon, requiring different approaches.  
    - Triangulation of a point set often starts by constructing its convex hull.  
    - An O(n log n) algorithm sorts points by x-coordinate and adds chords as points are incorporated into the hull.  
    - This step is necessary before partitioning the interior into triangles.

  - **Triangle Shape Considerations**
    - Multiple triangulations are possible for the same input, affecting triangle quality.  
    - Minimizing skinny (small angle) triangles is generally desirable.  
    - Delaunay triangulation minimizes the maximum angle, offering a near-optimal shape.  
    - The Delaunay triangulation is dual to the Voronoi diagram.  
    - See [Fortune’s Sweep2](http://www.netlib.org/voronoi/) for Delaunay triangulations.

  - **Improving Triangulation via Edge-Flips**
    - Internal edges shared between two triangles can be “flipped” if the quadrilateral formed is convex.  
    - Edge flips locally improve triangulations by removing skinny triangles.  
    - Any Delaunay triangulation can be obtained through successive edge-flips from any initial triangulation.

  - **Dimensionality Issues**
    - 3D triangulation generalizes to tetrahedralization, partitioning space into tetrahedra.  
    - Some polyhedra cannot be tetrahedralized without adding extra vertices (Steiner points).  
    - Deciding the existence of a tetrahedralization without extra vertices is NP-complete.  
    - Adding Steiner points is a practical approach to simplify 3D triangulation.

  - **Constraints in Triangulation**
    - Polygons and polyhedra impose constraints forbidding chords from intersecting boundary facets.  
    - Constraints may include obstacles that chords cannot cross.  
    - The constrained Delaunay triangulation respects such input restrictions.  
    - Constrained triangulations ensure legal edges while optimizing triangle quality.

  - **Use of Extra Points (Steiner Points)**
    - Adding extra points can help construct triangulations with better quality (avoiding small angles).  
    - Certain polyhedra require Steiner points for any valid triangulation.  
    - Steiner points are added strategically to facilitate high-quality triangulations.

  - **Convex Polygon Triangulation**
    - Triangulation of a convex polygon can be done in linear time.  
    - Selecting an arbitrary vertex and connecting it to all others guarantees valid, nonintersecting chords.  
    - This method relies on polygon convexity to ensure chord validity.

  - **General Polygon Triangulation**
    - Simple polygon triangulation algorithms check O(n²) possible chords for intersections.  
    - Practical algorithms achieve O(n log n) time, with exist linear-time theoretical algorithms.  
    - The linear-time algorithm by Chazelle [Cha91] is a proof of concept and difficult to implement.  
    - See [Bern’s survey](https://www.cs.ubc.ca/~bern/Books/ACM.pdf) for detailed polygon triangulation methods.

  - **Implementations and Software**
    - Triangle by Shewchuk generates Delaunay, constrained, and quality-conforming triangulations; widely used in finite element analysis.  
    - Fortune’s Sweep2 provides a robust Delaunay triangulation and Voronoi diagram implementation based on a sweepline algorithm.  
    - CGAL and LEDA libraries offer comprehensive C++ triangulation algorithms in 2D and 3D.  
    - Qhull performs low-to-moderate dimensional convex hulls and Delaunay triangulation up to eight dimensions.  
    - Additional resources include Steve Owen’s Meshing Research Corner and QMG software.

  - **Notes on Algorithmic Complexity and Theory**
    - Chazelle discovered a linear-time algorithm for simple polygon triangulation, difficult to implement practically.  
    - The first O(n log n) polygon triangulation algorithm was by Garey et al. [GJPT78].  
    - Linear-time triangulation algorithms exist for monotone polygons, which restrict line intersections to two points.  
    - The minimum weight triangulation problem is NP-complete; approximation algorithms are studied instead.  
    - Dynamic programming finds minimum weight triangulation for convex polygons in O(n³) time.

  - **Related Problems**
    - Voronoi diagrams are closely related and dual to Delaunay triangulations.  
    - Polygon partitioning generalizes the problem of decomposing polygons into simpler components.
