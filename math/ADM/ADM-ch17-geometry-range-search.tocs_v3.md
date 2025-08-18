[Representative image](ADM-ch17-geometry-range-search.best.png)

- **Computational Geometry**
  - **Range Search**
    - The problem involves identifying points from a set S in d-dimensional space that lie within a query region Q.
    - Difficulty factors include the number of queries, query polygon shape, dimensionality, static versus dynamic point sets, and whether points must be counted or identified.
    - Axis-parallel rectangles simplify queries by reducing inside/outside checks to coordinate range tests.
    - Kd-trees provide an efficient general method for range queries, especially in higher dimensions.
    - Dynamic approaches leveraging Delaunay triangulations enable efficient searches and updates via edge flips.
    - Counting points in a region can be optimized via dominance ordering and precomputed counts, though this can require quadratic space.
    - CGAL and LEDA libraries implement dynamic Delaunay triangulations and range trees supporting efficient orthogonal queries.
    - ANN and Ranger libraries support approximate and exact nearest neighbor and range queries in high dimensions.
    - Worst-case efficient data structures for orthogonal searches exist but can deteriorate significantly in performance; nonorthogonal queries remain more challenging.
    - Further reading includes [Agrawal 2004 survey](https://example.org) on simplex range searching and related worst-case data structure expositions.
