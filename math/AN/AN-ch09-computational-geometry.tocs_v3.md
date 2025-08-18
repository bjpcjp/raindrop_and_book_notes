![AN-ch09-computational-geometry](AN-ch09-computational-geometry.best.png)

- **Overview**
  - Computational geometry studies geometric algorithms and data structures for efficient processing of geometric objects.
  - Problems are characterized by input data type, computation performed, and whether the task is static or dynamic.
  - Fundamental geometric objects include points, line segments, rectangles, polygons, and their higher dimensional analogs.
  - Floating-point computations are necessary but have challenges such as round-off errors.
  - External resource: [Computational Geometry on Wikipedia](https://en.wikipedia.org/wiki/Computational_geometry)

- **Classifying Problems**
  - Input data types commonly involve sets of points, line segments, rectangles, polygons, or their n-dimensional versions.
  - Computations are queries, calculations, or preprocessing tasks on the input geometric data.
  - Tasks vary between static (one-time) and dynamic (multiple queries or changing data), impacting algorithm design.
  - Approaches differ regarding data structures that support growth and shrinkage for dynamic datasets.

- **Classic Problems in Computational Geometry**
  - Classic problems include convex hull computation, line segment intersections, nearest neighbor queries, and range queries.
  - Initial naive algorithms often have high time complexity (e.g., O(n⁴) for convex hull, O(n²) for line intersections).
  - Efficient algorithms use problem-specific strategies and data structures to improve performance significantly.

- **Convex Hull**
  - The convex hull is the smallest convex polygon enclosing all points in a plane.
  - The naive approach checks all triangles, resulting in O(n⁴) time complexity.
  - The Convex Hull Scan algorithm computes the hull in O(n log n) time by sorting points and incrementally building the hull.
  - The Akl-Toussaint heuristic improves performance by discarding points inside an extreme quadrilateral.
  - External resource: [Convex Hull on Wikipedia](https://en.wikipedia.org/wiki/Convex_hull)

- **Convex Hull Scan**
  - Constructs partial upper and lower hulls by iterating over sorted points and maintaining convexity via cross product checks.
  - Uses primitive arithmetic operations avoiding complex trigonometric functions for robustness.
  - Requires sorting points initially, often using HEAPSORT to avoid worst-case Quicksort behavior.
  - Supports efficient handling of large point sets and provides variations such as Quickhull and bucket sort implementations.
  - Benchmarking confirms near O(n log n) average performance with substantial reduction of points by the heuristic.

- **LineSweep**
  - Detects intersections among a set of line segments efficiently compared to brute force O(n²).
  - Conceptualizes a horizontal sweep line moving top to bottom, processing event points at segment endpoints and intersections.
  - Maintains a balanced binary tree as line state, tracking neighboring segments to detect intersections.
  - Employs an event queue holding unique event points for processing in order.
  - Achieves expected O((n+k) log n) time where k is the number of intersections.
  - External resource: [Line Sweep Algorithm on Wikipedia](https://en.wikipedia.org/wiki/Sweep_line_algorithm)

- **LineSweep Implementation**
  - Involves classes EventPoint, EventQueue, and LineState that together track sweep line state and events.
  - Inserts 2n segment endpoints into event queue, processing them to update line state and detect intersections dynamically.
  - Handles horizontal and vertical segments and ensures each intersection is recorded once.
  - Requires sophisticated data structures supporting quick insertion, deletion, predecessor, and successor queries.

- **LineSweep Analysis and Performance**
  - Uses balanced binary trees for event queue and line state operations to maintain O(log n) complexity per operation.
  - Performs poorly in worst case with O(n²) intersections, where brute force may be more efficient.
  - Benchmarks on Buffon's needle problem highlight efficiency gains with sparse intersections.
  - External resource: [Buffon's Needle Problem on MathWorld](http://mathworld.wolfram.com/BuffonsNeedleProblem.html)

- **Nearest Neighbor Queries**
  - Given a set of points P, find the closest point to any query point x, possibly not in P.
  - Naive search is O(n); improvement achieved by partitioning the space using kd-trees.
  - kd-tree partitions k-dimensional space recursively by alternating coordinate dimensions.
  - Nearest neighbor queries in kd-trees can be answered in O(log n) for low dimensions.
  - External resource: [kd-tree on Wikipedia](https://en.wikipedia.org/wiki/K-d_tree)

- **kd-tree Construction**
  - Built recursively by selecting median points on each dimension in cycle, ensuring balanced trees.
  - Utilizes selection algorithms (e.g., BFPRT) to find medians efficiently.
  - Balancing reduces worst-case search to O(log n) instead of O(n).
  - Construction has an upfront cost amortized across multiple queries.

- **Nearest Neighbor Search in kd-tree**
  - Searches down the kd-tree to locate the region where the query point would be inserted.
  - Recursively backs up the tree checking sibling subtrees if their regions could contain closer points.
  - Uses distance comparisons efficiently, abandoning exploration branches that cannot improve the current best.
  - Performance deteriorates as dimensions increase, often becoming comparable to brute-force linear search.
  - Benchmarks identify dimensionality thresholds beyond which brute-force is preferable.

- **Range Queries**
  - Given a rectangular (or hypercube in d dimensions) query region, report all points contained within.
  - Naive query scans all points in O(n).
  - kd-trees allow range queries to execute in O(n1–1/d + r) where r is number of points returned.
  - Algorithm descends the kd-tree, adding entire subtrees if fully contained and pruning otherwise.
  - Performance depends strongly on data distribution, query size, and dimensionality.
  - External resource: [Range Searching in Computational Geometry](https://en.wikipedia.org/wiki/Range_searching)

- **Range Query Algorithm**
  - Tests whether node's region lies fully inside query to add points collectively (drain).
  - Checks intersection of query with node's point for inclusion.
  - Descends into below or above subtrees depending on intersection along current dimension.
  - Efficient pruning leads to reduction of unnecessary subtree visits.

- **Range Query Performance**
  - Best performance when query region contains few points relative to dataset size.
  - Performance approaches O(n) when nearly all points are in query or query region is large.
  - Increasing dimension reduces pruning effectiveness, approaching linear time.
  - Benchmarks show kd-tree outperforms brute-force for small query result ratios and low-to-moderate dimensions.

- **References**
  - Lists seminal papers and textbooks fundamental to computational geometry and algorithms discussed:
    - Akl and Toussaint (1978) on Convex Hull heuristic
    - Cormen et al. (2001) "Introduction to Algorithms"
    - Graham (1972) on Convex Hull algorithm
    - Melkman (1987) on convex hull of simple polygon
    - Overmars and van Leeuwen (1981) on dynamic convex hull maintenance
    - Palazzi and Snoeyink (1994) on segment intersections
    - Preparata and Shamos (1985) textbook "Computational Geometry"
