![](VLSI-design-chap2.pdf-0-0.png)

-----

###### 2.1 Introduction

 2.2 Terminology


###### 2.3 Optimization Goals

 2.4 Partitioning Algorithms


###### 2.4.1 Kernighan-Lin (KL) Algorithm 2.4.2 Extensions of the Kernighan-Lin Algorithm 2.4.3 Fiduccia-Mattheyses (FM) Algorithm


###### 2.5 Framework for Multilevel Partitioning
 2.5.1 Clustering 2.5.2 Multilevel Partitioning


###### 2.6 System Partitioning onto Multiple FPGAs


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

###### Circuit:


###### Cut cb

|1 2 4 5|Cut c b 3 7 8 6|
|---|---|
|||
|||


###### Cut ca

 Block A Block B Block A Block B

|8 3 7 6|Col2|Col3|4 1 5 2|
|---|---|---|---|
|||||
|||||
|||||
|||||

|8 5 7 6|Col2|4 1 3 2|
|---|---|---|
||||
||||


![](VLSI-design-chap2.pdf-3-0.png)

###### Cut ca: four external connections


![](VLSI-design-chap2.pdf-3-0.png)

###### Cut cb: two external connections


-----

###### Block (Partition)


###### Graph G1: Nodes 3, 4, 5.


###### 5 6 3 5 6
 3

 2

 Cells

 Graph G2: Nodes 1, 2, 6.


###### Collection of cut edges

 Cut set:  (1,3), (2,3), (5,6),


-----

###### • Given a graph G(V,E) with |V| nodes and |E| edges where each node v ∈ V and each edge e ∈ E.

 • Each node has area s(v) and each edge has cost or weight w(e).



###### • The objective is to divide the graph G into k disjoint subgraphs such that all optimization goals are achieved and all original edge relations are respected.


-----

###### • In detail, what are the optimization goals?

 − Number of connections between partitions is minimized


###### − Each partition meets all design constraints (size, number of external connections..)

 − Balance every partition as well as possible



###### • How can we meet these goals?

 − Unfortunately, this problem is NP-hard


###### − Efficient heuristics are developed in the 1970s and 1980s. They are high quality and in low-order polynomial time.


-----

###### 2.1 Introduction

 2.2 Terminology


###### 2.3 Optimization Goals

 2.4 Partitioning Algorithms


###### 2.4.1 Kernighan-Lin (KL) Algorithm 2.4.2 Extensions of the Kernighan-Lin Algorithm 2.4.3 Fiduccia-Mattheyses (FM) Algorithm


###### 2.5 Framework for Multilevel Partitioning
 2.5.1 Clustering 2.5.2 Multilevel Partitioning


###### 2.6 System Partitioning onto Multiple FPGAs


-----

###### Given: A graph with 2n nodes where each node has the same weight.

 Goal: A partition (division) of the graph into two disjoint subsets A and B with minimum cut cost and |A| = |B| = n.


###### Example: n = 4 1 5

 2 6
 Block A Block B

|Col1|7|
|---|---|


-----

###### Cost D(v) of moving a node v

 D(v) = |Ec(v)| – |Enc(v)|,


###### where Ec(v) is the set of v’s incident edges that are cut by the cut line, and Enc(v) is the set of v’s incident edges that are not cut by the cut line.

 High costs (D > 0) indicate that the node should move, while low costs (D < 0) indicate that the node should stay within the same partition.

|Col1|7|
|---|---|


-----

###### Gain of swapping a pair of nodes a und b

 ∆g = D(a) + D(b) - 2* c(a,b),


###### where
 • D(a), D(b) are the respective costs of nodes a, b
 • c(a,b) is the connection weight between a and b:
 If an edge exists between a and b, then c(a,b) = edge weight (here 1), otherwise, c(a,b) = 0.

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### The gain ∆g indicates how useful the swap between two nodes will be

 The larger ∆g, the more the total cut cost will be reduced


-----

###### Gain of swapping a pair of nodes a und b

 ∆g = D(a) + D(b) - 2* c(a,b),


###### where
 • D(a), D(b) are the respective costs of nodes a, b
 • c(a,b) is the connection weight between a and b:
 If an edge exists between a and b, then c(a,b) = edge weight (here 1), otherwise, c(a,b) = 0.

|Col1|7|
|---|---|


###### ∆g (3,7) = D(3) + D(7) - 2* c(a,b) = 2 + 1 – 2 = 1


###### => Swapping nodes 3 and 7 would reduce the cut size by 1


###### 4


###### 8


-----

###### Gain of swapping a pair of nodes a und b

 ∆g = D(a) + D(b) - 2* c(a,b),


###### where
 • D(a), D(b) are the respective costs of nodes a, b
 • c(a,b) is the connection weight between a and b:
 If an edge exists between a and b, then c(a,b) = edge weight (here 1), otherwise, c(a,b) = 0.

|Col1|7|
|---|---|


###### ∆g (3,5) = D(3) + D(5) - 2* c(a,b) = 2 + 1 – 0 = 3


###### => Swapping nodes 3 and 5 would reduce the cut size by 3


###### 4


###### 8


-----

###### Gain of swapping a pair of nodes a und b

 The goal is to find a pair of nodes a and b to exchange such that ∆g is maximized and swap them.


-----

###### Maximum positive gain Gm of a pass

 The maximum positive gain G m swaps m corresponds to the best prefix of within the swap sequence of a given pass.


###### These m swaps lead to the partition with the minimum cut cost encountered during the pass.

 Gm is computed as the sum of Δg values over the first m swaps of the pass, with m chosen such that Gm is maximized.


###### m

##### G = ∆g
###### m i

## ∑

###### i=1


-----

###### Step 0:  – V = 2n nodes
 – {A, B} is an initial arbitrary partitioning
 Step 1:  – i = 1
 – Compute D(v) for all nodes v∈V


###### Step 2:  – Choose ai and bi such that ∆gi = D(ai) + D(bi) – 2 * c(aibi) is maximized
 – Swap and fix ai and bi
 Step 3:  – If all nodes are fixed, go to Step 4. Otherwise
 – Compute and update D values for all nodes that are connected to ai and bi and are not fixed.
 – i = i + 1
 – Go to Step 2


###### Step 4: 
_m_
###### – Find the move sequence 1...m (1 ≤ m ≤ i), such that Gm = ∑i=1[Δ]gi  is maximized
 – If Gm > 0, go to Step 5. Otherwise, END


###### Step 5:  – Execute m swaps, reset remaining nodes
 – Go to Step 1


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Nodes that lead to maximum gain


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Costs D(v) of each node:


###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


###### Gain in the current pass


###### Nodes that lead to maximum gain

 Gain after node swapping


###### G1 = ∆g1 =3


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


![](VLSI-design-chap2.pdf-19-0.png)

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


![](VLSI-design-chap2.pdf-19-0.png)

###### Gain in the current pass


###### Nodes that lead to maximum gain

 Gain after node swapping


###### G1 = ∆g1 =3


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Cut cost: 6 Not fixed: 1,2,4,6,7,8


![](VLSI-design-chap2.pdf-20-0.png)

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


![](VLSI-design-chap2.pdf-20-0.png)

###### G1 = ∆g1 =3


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Cut cost: 6 Not fixed: 1,2,4,6,7,8


![](VLSI-design-chap2.pdf-21-0.png)

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


![](VLSI-design-chap2.pdf-21-0.png)

###### D(1) = -1 D(6) = 2 D(2) = -1 D(7)=-1 D(4) = 3 D(8)=-1


###### G1 = ∆g1 =3


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Cut cost: 6 Not fixed: 1,2,4,6,7,8


![](VLSI-design-chap2.pdf-22-0.png)

![](VLSI-design-chap2.pdf-22-1.png)

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


![](VLSI-design-chap2.pdf-22-0.png)

###### D(1) = -1 D(6) = 2 D(2) = -1 D(7)=-1 D(4) = 3 D(8)=-1

 ∆g2 = 3+2-0 = 5 Swap (4,6) G2 = G1+∆g2 =8


![](VLSI-design-chap2.pdf-22-0.png)

###### Gain in the current pass


###### Nodes that lead to maximum gain

 Gain after node swapping


###### G1 = ∆g1 =3


-----

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Cut cost: 6 Not fixed: 1,2,4,6,7,8


###### Cut cost: 1 Not fixed: 1,2,7,8


###### Cut cost: 7 Not fixed: 2,8


![](VLSI-design-chap2.pdf-23-0.png)

![](VLSI-design-chap2.pdf-23-1.png)

![](VLSI-design-chap2.pdf-23-2.png)

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


![](VLSI-design-chap2.pdf-23-0.png)

![](VLSI-design-chap2.pdf-23-1.png)

###### D(1) = -1 D(6) = 2 D(2) = -1 D(7)=-1 D(4) = 3 D(8)=-1

 ∆g2 = 3+2-0 = 5 Swap (4,6) G2 = G1+∆g2 =8


![](VLSI-design-chap2.pdf-23-0.png)

###### D(1) = -3 D(7)=-3 D(2) = -3 D(8)=-3


###### ∆g3 = -3-3-0 = -6 Gain after node swapping Swap (1,7) Gain in the current pass G3= G2 +∆g3 = 2


###### Nodes that lead to maximum gain


###### G1 = ∆g1 =3


-----

|Col1|7|
|---|---|

|Col1|7|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|

|1 2 3 4|5 6 7 8|
|---|---|


###### Cut cost: 9 Not fixed: 1,2,3,4,5,6,7,8


###### Cut cost: 6 Not fixed: 1,2,4,6,7,8


###### Cut cost: 1 Not fixed: 1,2,7,8


###### Cut cost: 7 Not fixed: 2,8


###### Cut cost: 9 Not fixed: –


![](VLSI-design-chap2.pdf-24-0.png)

![](VLSI-design-chap2.pdf-24-1.png)

![](VLSI-design-chap2.pdf-24-2.png)

![](VLSI-design-chap2.pdf-24-3.png)

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


![](VLSI-design-chap2.pdf-24-0.png)

![](VLSI-design-chap2.pdf-24-1.png)

###### D(1) = -1 D(6) = 2 D(2) = -1 D(7)=-1 D(4) = 3 D(8)=-1

 ∆g2 = 3+2-0 = 5 Swap (4,6) G2 = G1+∆g2 =8


![](VLSI-design-chap2.pdf-24-0.png)

###### D(1) = -3 D(7)=-3 D(2) = -3 D(8)=-3

 ∆g3 = -3-3-0 = -6 Swap (1,7) G3= G2 +∆g3 = 2


![](VLSI-design-chap2.pdf-24-0.png)

###### D(2) = -1 D(8)=-1

 ∆g4 = -1-1-0 = -2 Swap (2,8) G4 = G3 +∆g4 = 0


###### G1 = ∆g1 =3


-----

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


###### D(1) = -3 D(7)=-3 D(2) = -3 D(8)=-3

 ∆g3 = -3-3-0 = -6 Swap (1,7) G3= G2 +∆g3 = 2


###### D(2) = -1 D(8)=-1

 ∆g4 = -1-1-0 = -2 Swap (2,8) G4 = G3 +∆g4 = 0


###### G1 = ∆g1 =3


![](VLSI-design-chap2.pdf-25-0.png)

###### Maximum positive gain Gm = 8 with m = 2.


-----

###### D(1) = 1 D(5) = 1 D(2) = 1 D(6) = 2 D(3) = 2 D(7) = 1 D(4) = 1 D(8) = 1

 ∆g1 = 2+1-0 = 3 Swap (3,5)


###### D(1) = -3 D(7)=-3 D(2) = -3 D(8)=-3

 ∆g3 = -3-3-0 = -6 Swap (1,7) G3= G2 +∆g3 = 2


###### D(2) = -1 D(8)=-1

 ∆g4 = -1-1-0 = -2 Swap (2,8) G4 = G3 +∆g4 = 0


###### G1 = ∆g1 =3


![](VLSI-design-chap2.pdf-26-0.png)

###### Maximum positive gain Gm = 8 with m = 2.


###### Since Gm > 0, the first m = 2 swaps (3,5) and (4,6) are executed. 2


###### Since Gm > 0, more passes are needed until Gm ≤ 0.


###### 4


###### 8


-----

###### • Unequal partition sizes

 − Apply the KL algorithm with only min(|A|,|B|) pairs swapped



###### • Unequal node weights

 − Try to rescale weights to integers, e.g., as multiples of the greatest common divisor of all node weights


###### − Maintain area balance or allow a one-move deviation from balance



###### • k-way partitioning (generating k partitions)

 − Apply the KL two-way partitioning algorithm to all possible pairs of partitions


###### − Recursive partitioning (convenient when k is a power of two)

 − Direct k-way extensions exist


-----

###### • Single cells are moved independently instead of swapping pairs of cells --- cannot and do not need to maintain exact partition balance

 • The area of each individual cell is taken into account



###### • Applicable to partitions of unequal size and in the presence of initially fixed cells



###### • Cut costs are extended to include hypergraphs

 • nets with 2+ pins



###### • While the KL algorithm aims to minimize cut costs based on edges, the FM algorithm minimizes cut costs based on nets

 • Nodes and subgraphs are referred to as cells and blocks, respectively


-----

###### Given: a hypergraph G(V,H) with nodes and weighted hyperedges partition size constraints

 Goal: to assign all nodes to disjoint partitions, so as to minimize the total cost (weight) of all cut nets while satisfying partition size constraints


-----

###### Gain ∆g(c) for cell c

 ∆g(c) = FS(c) – TE(c),


###### where

 the “moving force“ FS(c) is the number of nets connected to c but not connected to any other cells within c’s partition, i.e., cut nets that connect only to c, and


###### the “retention force“ TE(c) is the number of uncut nets connected to c.

 The higher the gain ∆g(c), the higher is the priority to move the cell c to the other partition.


-----

###### Gain ∆g(c) for cell c

 ∆g(c) = FS(c) – TE(c),


###### where

 the “moving force“ FS(c) is the number of nets connected to c but not connected to any other cells within c’s partition, i.e., cut nets that connect only to c, and


###### the “retention force“ TE(c) is the number of uncut nets connected to c.


###### Cell 1:   FS(1) = 2 TE(1) = 1 ∆g(1) = 1

 Cell 2:   FS(2) = 0 TE(2) = 1 ∆g(2) = -1

 Cell 3:   FS(3) = 1 TE(3) = 1 ∆g(3) = 0

 Cell 4:   FS(4) = 1 TE(4) = 1 ∆g(4) = 0

 Cell 5:   FS(5) = 1 TE(5) = 0 ∆g(5) = 1


###### 1


###### 5


-----

###### Maximum positive gain Gm of a pass

 The maximum positive gain Gm is the cumulative cell gain of m moves that produce a minimum cut cost.


###### Gm is determined by the maximum sum of cell gains ∆g over a prefix of m moves in a pass


###### m

#### G = ∆g
###### m i

# ∑

###### i=1


-----

###### Ratio factor

 The ratio factor is the relative balance between the two partitions with respect to cell area


###### It is used to prevent all cells from clustering into one partition.


###### The ratio factor r is defined as


#### area( A) r = area( A) + area(B)


###### where area(A) and area(B) are the total respective areas of partitions A and B


-----

###### Balance criterion

 The balance criterion enforces the ratio factor.


###### To ensure feasibility, the maximum cell area areamax(V) must be taken into account.

 A partitioning of V into two partitions A and B is said to be balanced if



###### [ r ∙ area(V) – areamax(V) ] ≤ area(A) ≤ [ r ∙ area(V) + areamax(V) ]


-----

###### Base cell

 A base cell is a cell c that has the greatest cell gain ∆g(c) among all free cells, and whose move does not violate the balance criterion.


###### Base cell


-----

###### Step 0: Compute the balance criterion
 Step 1: Compute the cell gain ∆g1 of each cell


###### Step 2: i = 1 – Choose base cell c1 that has maximal gain ∆g1, move this cell
 Step 3:  – Fix the base cell ci
 – Update all cells’ gains that are connected to critical nets via the base cell ci


###### Step 4: – If all cells are fixed, go to Step 5. If not:
 – Choose next base cell ci with maximal gain ∆gi and move this cell
 – i = i + 1, go to Step 3
 Step 5: 
_m_
###### – Determine the best move sequence c1, c2, .., cm (1 ≤ m ≤ i), so that  Gm = ∑i=1[Δ]gi is maximized


###### – If Gm > 0, go to Step 6. Otherwise, END
 Step 6: 


-----

###### A 2 3 B

 b e
 a
 4

 c
 d
 1 5

 Step 0: Compute the balance criterion


###### Given: Ratio factor r = 0,375 area(Cell_1) = 2 area(Cell_2) = 4 area(Cell_3) = 1 area(Cell_4) = 4 area(Cell_5) = 5.



###### [ r ∙ area(V) – area (V) ] ≤ area(A) ≤ [ r ∙ area(V) + area (V) ]
_max_ _max_

###### 0,375 * 16 – 5 = 1 ≤ area(A) ≤ 11 = 0,375 * 16 +5.


-----

###### A 2 3 B

 b e
 a
 4

 c
 d
 1 5

 Step 1: Compute the gains of each cell


###### Cell 1:   FS(Cell_1) = 2 TE(Cell_1) = 1 ∆g(Cell_1) = 1
 Cell 2:   FS(Cell_2) = 0 TE(Cell_2) = 1 ∆g(Cell_2) = -1
 Cell 3:   FS(Cell_3) = 1 TE(Cell_3) = 1 ∆g(Cell_3) = 0


###### Cell 4:   FS(Cell_4) = 1 TE(Cell_4) = 1 ∆g(Cell_4) = 0
 Cell 5:   FS(Cell_5) = 1 TE(Cell_5) = 0 ∆g(Cell_5) = 1


-----

###### A 2 3 B

 b e
 a
 4

 c
 d
 1 5

 Step 2: Select the base cell


###### Cell1:    FS(Cell_1) = 2   TE(Cell_1) = 1 ∆g(Cell_1) = 1
 Cell 2:   FS(Cell_2) = 0   TE(Cell_2) = 1 ∆g(Cell_2) = -1
 Cell 3:   FS(Cell_3) = 1   TE(Cell_3) = 1 ∆g(Cell_3) = 0


###### Cell 4:   FS(Cell_4) = 1   TE(Cell_4) = 1 ∆g(Cell_4) = 0
 Cell 5:   FS(Cell_5) = 1   TE(Cell_5) = 0 ∆g(Cell_5) = 1


###### Possible base cells are Cell 1 and Cell 5

 Balance criterion after moving Cell 1: area(A) = area(Cell_2) = 4


###### Balance criterion after moving Cell 5: area(A) = area(Cell_1) + area(Cell_2) + area(Cell_5) = 11

 Both moves respect the balance criterion, but Cell 1 is selected, moved,


###### and fixed as a result of the tie-breaking criterion.


-----

###### A 2 3 B

 b e
 a
 4

 c
 d
 1 5

 Step 3: Fix base cell, update ∆g values


###### Cell 2:   FS(Cell_2) = 2 TE(Cell_2) = 0 ∆g(Cell_2) = 2

 Cell 3:   FS(Cell_3) = 0 TE(Cell_3) = 1 ∆g(Cell_3) = -1

 Cell 4:   FS(Cell_4) = 0 TE(Cell_4) = 2 ∆g(Cell_4) = -2

 Cell 5:   FS(Cell_5) = 0 TE(Cell_5) = 1 ∆g(Cell_5) = -1


###### After Iteration i = 1: Partition A1 = 2 Partition B1 = 1 3 4 5 with fixed cell 1


-----

###### A 2 3 B


###### Iteration i = 1

 Cell 2:   FS(Cell_2) = 2  TE(Cell_2) = 0 ∆g(Cell_2) = 2


###### Cell 3:   FS(Cell_3) = 0  TE(Cell_3) = 1 ∆g(Cell_3) = -1

 Cell 4:   FS(Cell_4) = 0  TE(Cell_4) = 2 ∆g(Cell_4) = -2

 Cell 5:   FS(Cell_5) = 0  TE(Cell_5) = 1 ∆g(Cell_5) = -1


###### Iteration i = 2

 Cell 2 has maximum gain ∆g2 = 2, area(A) = 0, balance criterion is violated.


###### Cell 3 has next maximum gain ∆g2 = -1, area(A) = 5, balance criterion is met.
 Cell 5 has next maximum gain ∆g2= -1, area(A) = 9, balance criterion is met.


###### Move cell 3, updated partitions: A2 = {2,3}, B2 = {1,4,5}, with fixed cells {1,3}


-----

###### A


###### Iteration i = 2

 Cell 2:   ∆g(Cell_2) = 1

 Cell 4:   ∆g(Cell_4) = 0


###### Cell 5:   ∆g(Cell_5) = -1


###### Iteration i = 3

 Cell 2 has maximum gain ∆g3 = 1, area(A) = 1, balance criterion is met.


###### Move cell 2, updated partitions: A3 = {3}, B3 = {1,2,4,5}, with fixed cells {1,2,3}


-----

###### B 2 3 A


###### Iteration i = 3

 Cell 4:   ∆g(Cell_4) = 0


###### Cell 5:   ∆g(Cell_5) = -1


###### Iteration i = 4

 Cell 4 has maximum gain ∆g4 = 0, area(A) = 5, balance criterion is met.


###### Move cell 4, updated partitions: A4 = {3,4}, B3 = {1,2,5}, with fixed cells {1,2,3,4}


-----

###### B 2 3 A


###### Iteration i = 4

 Cell 5:   ∆g(Cell_5) = -1


###### Iteration i = 5

 Cell 5 has maximum gain ∆g5 = -1, area(A) = 10, balance criterion is met.


###### Move cell 5, updated partitions: A4 = {3,4,5}, B3 = {1,2}, all cells {1,2,3,4,5} fixed.


-----

###### Step 5: Find best move sequence c1 … cm G1 = ∆g1 = 1
 G2 = ∆g1 + ∆g2 = 0


###### B 2 3 A


###### G3 = ∆g1 + ∆g2 + ∆g3 = 1
 G4 = ∆g1 + ∆g2 + ∆g3 + ∆g4 = 1


###### G5 = ∆g1 + ∆g2 + ∆g3 + ∆g4 + ∆g5 = 0.

 m
 Maximum positive cumulative gain G = ∆g = 1
 m i

### ∑

###### i =1
 found in iterations 1, 3 and 4.


###### The move prefix m = 4 is selected due to the better balance ratio (area(A) = 5); the four cells 1, 2, 3 and 4 are then moved.

 Result of Pass 1: Current partitions: A = {3,4}, B = {1,2,5}, cut cost reduced from 3 to 2.


-----

###### • Runtime of partitioning algorithms

 − KL is sensitive to the number of nodes and edges


###### − FM is sensitive to the number of nodes and nets (hyperedges)



###### • Asymptotic complexity of partitioning algorithms

 − KL has cubic time complexity per pass


###### − FM has linear time complexity per pass


-----

###### 2.1 Introduction

 2.2 Terminology


###### 2.3 Optimization Goals

 2.4 Partitioning Algorithms


###### 2.4.1 Kernighan-Lin (KL) Algorithm 2.4.2 Extensions of the Kernighan-Lin Algorithm 2.4.3 Fiduccia-Mattheyses (FM) Algorithm


###### 2.5 Framework for Multilevel Partitioning
 2.5.1 Clustering 2.5.2 Multilevel Partitioning


###### 2.6 System Partitioning onto Multiple FPGAs


-----

###### • To simplify the problem, groups of tightly-connected nodes can be clustered, absorbing connections between these nodes

 • Size of each cluster is often limited so as to prevent degenerate clustering, i.e. a single large cluster dominates other clusters



###### • Refinement should satisfy balance criteria


-----

![](VLSI-design-chap2.pdf-49-1.png)

###### c,e


![](VLSI-design-chap2.pdf-49-2.png)

###### b


![](VLSI-design-chap2.pdf-49-3.png)

###### d


![](VLSI-design-chap2.pdf-49-4.png)

###### d


![](VLSI-design-chap2.pdf-49-5.png)

###### b


![](VLSI-design-chap2.pdf-49-6.png)

###### a


###### Initital graph Possible clustering hierarchies of the graph


![](VLSI-design-chap2.pdf-49-0.png)

###### a,b,c


![](VLSI-design-chap2.pdf-49-1.png)

###### c


![](VLSI-design-chap2.pdf-49-2.png)

###### a


![](VLSI-design-chap2.pdf-49-3.png)

###### e


-----

![](VLSI-design-chap2.pdf-50-1.png)

-----

###### FPGA FPGA


###### Reconfigurable system with multiple FPGA and FPIC devices


###### Mapping of a typical system architecture onto multiple FPGAs


-----

###### • Circuit netlists can be represented by graphs

 • Partitioning a graph means assigning nodes to disjoint partitions


###### − Total size of each partition (number/area of nodes) is limited
 − Objective: minimize the number connections between partitions



###### • Basic partitioning algorithms
 − Move-based, move are organized into passes


###### − KL swaps pairs of nodes from different partitions
 − FM re-assigns one node at a time


###### − FM is faster, usually more successful



###### • Multilevel partitioning
 − Clustering


###### − FM partitioning
 − Refinement (also uses FM partitioning)



###### • Application: system partitioning into FPGAs
 − Each FPGA is represented by a partition


-----

