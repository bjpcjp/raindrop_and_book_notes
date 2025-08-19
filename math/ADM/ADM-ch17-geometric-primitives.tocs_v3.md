![ADM-ch17-geometric-primitives](ADM-ch17-geometric-primitives.best.png)

- **17.1 Robust Geometric Primitives**
  - The section discusses the challenges of implementing basic geometric primitives such as point-line and line segment intersection tests.  
  - It identifies two main issues: geometric degeneracy and numerical stability, which can cause incorrect or unstable results.  
  - Three approaches to handling degeneracy are ignoring it, faking it with perturbations, and explicitly dealing with it through special case code.  
  - Numerical stability can be addressed by using integer arithmetic, double precision floating-point, or arbitrary precision arithmetic, each with distinct trade-offs.  
  - Key geometric primitives include area of a triangle, above-below-on tests, line segment intersection, and in-circle tests, with formal determinant-based formulas provided.  
  - Recommendations include using established libraries like CGAL and LEDA for robust implementations and consulting [O’Rourke’s Computational Geometry in C](https://cs.nyu.edu/exact/) for foundational algorithms.
