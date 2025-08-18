![AJE-greedy-algos](AJE-greedy-algos.best.png)

- **Exercises**
  - **Towers of Hanoi variant with restricted moves**
    - The problem restricts moves to never place smaller disks on larger ones and forbids direct moves from peg 0 to peg 2.
    - It requires an algorithm to compute the exact number of moves to transfer all disks from peg 0 to peg 2.
    - The algorithm must use only O(log n) arithmetic operations and consider the complexity of arithmetic on k-digit numbers as O(k).
    - Matrix methods are hinted as a central tool for the solution.

  - **Splitting Sequences/Arrays**
    - Problem 34 addresses finding a minimal number of 1s in a basic arithmetic expression equaling a given integer.
    - Problem 35 seeks the maximum value from an expression with integers separated by + and − by optimizing parentheses placement.
    - Problem 36 involves maximizing values in expressions with + and ×, with variations depending on positivity of integers.
    - Problem 37 focuses on boolean expressions formed from T and F with operators ∧, ∨, ⊕, deciding if parenthesization evaluates to T.
    - Problem 38 deals with pairwise interactions in a circular snail mating race and maximizing total rewards from matching pairs.

  - **Marble Slab Cutting**
    - Problem 39 requires cutting an n×m slab into rectangles to maximize profit based on given spot prices for various sizes.
    - The algorithm must handle irregular spot prices which may not be monotone in size.

  - **Optimal Balanced Binary Search Trees**
    - Problem 40 explores constructing optimal BSTs under balance constraints: AVL trees, red-black trees, and AA trees.
    - Each subproblem demands an algorithm accommodating specific structural constraints while optimizing search cost.

  - **Guillotine Subdivision of Bitmaps**
    - Problem 41 discusses decomposing a bitmap into solid blocks using recursive guillotine cuts.
    - Subparts require algorithms to minimize subdivision size, minimize subdivision depth, and compute pixel depths.
    - Also includes proofs that guillotine subdivisions do not always yield minimal block decompositions.

  - **Warehouse Robots and Binary Search Trees**
    - Problem 42 involves optimizing robot motion time during binary search of sorted bins considering movement, reading, and turnaround costs.
    - The goal is to construct a binary search tree minimizing total robot search time across queries.

  - **B-trees with Cost Optimization**
    - Problem 43 studies B-trees with node degree B, keys, and children pointers to minimize total search cost given access frequencies.
    - Solutions range from polynomial time algorithms for B=2 to scalable algorithms with running time independent of B.

  - **Balanced Parentheses and Brackets**
    - Problem 44 covers algorithms to determine if strings of parentheses and brackets are balanced.
    - Also includes computing longest balanced subsequences, shortest balanced supersequences, edit distances, and common balanced sequences.

  - **Edit Distance for Arithmetic Expressions**
    - Problem 45 deals with computing minimum edit distance from a token string to a valid arithmetic expression.
    - The alphabet includes digits (#), binary operators (), and parentheses.

  - **RNA Secondary Structure Prediction**
    - Problem 46 models RNA secondary structure with pairing constraints disallowing overlaps.
    - Algorithms must maximize number of valid pairs and minimize sum of squares of gap lengths.

  - **Regular and Generalized Regular Expressions**
    - Problem 47 asks for algorithms to decide membership of a string in languages defined by regular and generalized regular expressions.
    - Generalized expressions include intersection and complement operators.

  - **Trees and Subtrees: Party Guests and Gift Assignments**
    - Problems 48 and 49 describe trees representing company hierarchies with constraints on guest lists and gift assignments.
    - Algorithms optimize sum of fun ratings and minimize firing based on gift label constraints.

  - **Party Guest Awkwardness Minimization**
    - Problem 50 requires selecting exactly k employees from a hierarchy minimizing total awkwardness from supervising relationships.
    - Includes algorithms for binary trees and general trees.

  - **Broadcasting Messages in Trees**
    - Problem 51 studies minimal rounds needed to disseminate a message from root to all nodes where communication is one-to-one per round.
    - Solutions cover binary and general rooted trees.

  - **Climbing Paths on Boulder Holds**
    - Problem 52 models allowed moves on holds as a tree and seeks maximum number of disjoint paths of fixed length k towards the root.
    - No assumptions on branching factor; paths cannot share nodes.

  - **Marking Vertices for Minimum Clustering Cost**
    - Problem 53 defines clustering cost based on distances to marked ancestors.
    - Includes algorithms to minimize clustering cost for fixed k, smallest subset for fixed cost, and implications for efficient runtimes.

  - **Common Subtrees of Rooted Trees**
    - Problem 54 investigates algorithms to find largest common rooted subtrees under binary, ordered, and unordered tree isomorphism definitions.

  - **Optimal Subtrees in Unrooted Trees**
    - Problem 55 involves finding maximum weight paths and subtrees in weighted unrooted trees.
    - Also explores largest common ordered and unordered unrooted subtrees.

  - **Rooted Minors of Rooted Trees**
    - Problem 56 generalizes subtree problems to rooted minors obtained by edge contractions.
    - Algorithms find largest boring, heap-ordered, binary-search-ordered minors, and largest common minors for ordered and unordered labeled rooted trees.
    - Maximum flow techniques are hinted for unordered common minors.
