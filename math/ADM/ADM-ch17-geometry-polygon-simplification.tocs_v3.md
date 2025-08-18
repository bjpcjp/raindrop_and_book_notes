[Representative image](ADM-ch17-geometry-polygon-simplification.best.png)

- **17.12 Simplifying Polygons**  
  - Polygon simplification reduces vertex count while maintaining shape fidelity.  
  - Key issues include whether to use convex hull, vertex insertion vs. deletion, polygon simplicity, and image noise cleanup.  
  - The Douglas-Peucker algorithm incrementally refines a polygon by adding vertices to minimize maximum deviation.  
  - Simplification in 3D is NP-complete; heuristic and approximation algorithms exist for polyhedra.  
  - Implementations include Douglas-Peucker code by Snoeyink, simplification envelopes, QSlim, Cocone, Powercrust, and CGAL.  
  - Further reading: [Douglas-Peucker algorithm implementation](http://www.cs.unc.edu/~snoeyink/papers/DPsimp.arch), [Powercrust](http://www.cs.utexas.edu/users/amenta/powercrust/).
