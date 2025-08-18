![AJE-graph-algos](AJE-graph-algos.best.png)

- **4.4. Huffman Codes**
  - The Huffman code tree is constructed recursively by merging two least frequent symbols and forming an optimal tree.
  - The algorithm uses a priority queue to efficiently build the tree with O(n log n) running time.
  - Encoding and decoding with the Huffman tree run in linear time relative to message length.
  - The correctness relies on maintaining the optimal substructure and exchange argument.
  - For detailed implementation pseudocode, see [Huffman Coding - Wikipedia](https://en.wikipedia.org/wiki/Huffman_coding).

- **4.5. Stable Matching**
  - Stable matching ensures no pair of doctor and hospital prefer each other over their assigned matches.
  - Naive greedy approaches to matching can lead to unstable pairs or infinite loops.
  - The Gale-Shapley algorithm guarantees a stable matching and runs in O(n^2) time, with each hospital making offers and doctors tentatively accepting.
  - The algorithm computes the hospital-optimal stable matching, and its correctness is proven by properties of feasibility and rejection.
  - The stable matching problem and Gale-Shapley algorithm have wide applications, including medical residency and school admissions.
  - For foundational work, see [Gale-Shapley algorithm - Wikipedia](https://en.wikipedia.org/wiki/Gale%E2%80%93Shapley_algorithm).

- **Exercises**
  - The exercises cover a range of greedy algorithm problems including scheduling, interval covers, Huffman code variations, stable matching implementations, and other combinatorial optimization problems.
  - They require proof of correctness, counterexamples for greedy failures, and design of efficient algorithms.
  - Several exercises focus on the stable matching problem’s edge cases, complexity, and extensions.
  - The exercises cover both theoretical and practical settings, such as currency change, coloring intervals, matrix construction, and partitioning problems.
  - Additional references for solving exercises include [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) and [Algorithm Design Manual](https://www.algorist.com/).
