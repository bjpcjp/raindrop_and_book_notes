[Representative image](ADM-ch14-combinatorials-partitions.best.png)

- **14. COMBINATORIAL PROBLEMS**
  - **14.6 Generating Partitions**
    - Integer partitions are multisets of nonzero integers summing exactly to n, with examples provided for n=5.
    - Set partitions divide the set {1,...,n} into nonempty subsets, exemplified by the 15 partitions for n=4.
    - Integer partitions can be generated in lexicographically decreasing order using a subtraction and regrouping method starting from {n}.
    - Random generation of integer partitions requires handling probabilities based on partition counts defined by the recurrence Pn,k = Pn−k,k + Pn,k−1.
    - Set partitions can be represented by restricted growth functions, providing canonical orderings via lexicographic sequencing.
    - Stirling numbers of the second kind count set partitions of n elements into k blocks and satisfy a specific recurrence.
    - Implementations for generating both integer and set partitions are available from multiple sources, including Kreher and Stinson, the Combinatorial Object Server, and Combinatorica.
    - Further reading includes Knuth [Knu05b], Andrews [And98], and implementations at [Kreher and Stinson's site](http://www.math.mtu.edu/~kreher/cages/Src.html).
