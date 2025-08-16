![](VLSI-design-chap3.pdf-0-0.png)

-----

###### 3.1 Introduction to Floorplanning

 3.2 Optimization Goals in Floorplanning


###### 3.3 Terminology

 3.4 Floorplan Representations 3.4.1 Floorplan to a Constraint-Graph Pair 3.4.2 Floorplan to a Sequence Pair 3.4.3 Sequence Pair to a Floorplan


###### 3.5 Floorplanning Algorithms 3.5.1 Floorplan Sizing 3.5.2 Cluster Growth 3.5.3 Simulated Annealing 3.5.4 Integrated Floorplanning Algorithms

 3.6 Pin Assignment


###### 3.7 Power and Ground Routing 3.7.1 Design of a Power-Ground Distribution Network 3.7.2 Planar Routing 3 7 3 Mesh Routing


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

###### I/O Pads


###### Floorplan


![](VLSI-design-chap3.pdf-3-0.png)

###### Block c
 Block a

 GND VDD
 Block d
 Block Pins

 Block b
 Block e


###### Supply Network

|Col1|Col2|Col3|
|---|---|---|
|Block c Block a GND VDD Block d Block Pins Block b Block e|||
||||


![](VLSI-design-chap3.pdf-3-0.png)

###### Chip Planning


-----

###### Example Given: Three blocks with the following potential widths and heights Block A: w = 1, h = 4 or w = 4, h = 1 or w = 2, h = 2 Block B: w = 1, h = 2 or w = 2, h = 1  Block C: w = 1, h = 3 or w = 3, h = 1

 Task: Floorplan with minimum total area enclosed


###### B


###### B

|C|Col2|
|---|---|

|A|Col2|
|---|---|


###### A


-----

###### Example Given: Three blocks with the following potential widths and heights Block A: w = 1, h = 4 or w = 4, h = 1 or w = 2, h = 2 Block B: w = 1, h = 2 or w = 2, h = 1  Block C: w = 1, h = 3 or w = 3, h = 1

 Task: Floorplan with minimum total area enclosed


-----

###### Example Given: Three blocks with the following potential widths and heights Block A: w = 1, h = 4 or w = 4, h = 1 or w = 2, h = 2 Block B: w = 1, h = 2 or w = 2, h = 1  Block C: w = 1, h = 3 or w = 3, h = 1

 Task: Floorplan with minimum total area enclosed


###### Solution: Aspect ratios Block A with w = 2, h = 2; Block B with w = 2, h = 1; Block C with w = 1, h = 3

 This floorplan has a global bounding box with minimum possible area (9 square units).


-----

###### • Area and shape of the global bounding box

 − Global bounding box of a floorplan is the minimum axis-aligned rectangle that contains all floorplan blocks.


###### − Area of the global bounding box represents the area of the top-level floorplan

 − Minimizing the area involves finding (x,y) locations, as well as shapes, of the individual blocks.



###### • Total wirelength

 − Long connections between blocks may increase signal propagation delays in the design.



###### • Combination of area area(F) and total wirelength L(F) of floorplan F

 − Minimize α ∙ area(F) + (1 – α) ∙ L(F)  where the parameter 0 ≤ α ≤ 1 gives the relative importance between area(F) and L(F)



###### • Signal delays

 − Static timing analysis is used to identify the interconnects that lie on critical paths.


-----

###### • A rectangular dissection is a division of the chip area into a set of blocks or non-overlapping rectangles.

 • A slicing floorplan is a rectangular dissection


###### − Obtained by repeatedly dividing each rectangle, starting with the entire chip area, into two smaller rectangles

 − Horizontal or vertical cut line.



###### • A slicing tree or slicing floorplan tree is a binary tree with k leaves and k – 1 internal nodes

 − Each leaf represents a block


###### − Each internal node represents a horizontal or vertical cut line.


-----

###### Slicing floorplan and two possible corresponding slicing trees

|b|c e f d|
|---|---|
|a||


![](VLSI-design-chap3.pdf-9-0.png)

###### c
 b

 e f

 a
 d


![](VLSI-design-chap3.pdf-9-1.png)

###### a


![](VLSI-design-chap3.pdf-9-2.png)

###### c


![](VLSI-design-chap3.pdf-9-3.png)

###### f


![](VLSI-design-chap3.pdf-9-4.png)

###### V


![](VLSI-design-chap3.pdf-9-5.png)

###### H


![](VLSI-design-chap3.pdf-9-6.png)

###### H


![](VLSI-design-chap3.pdf-9-7.png)

###### c


![](VLSI-design-chap3.pdf-9-8.png)

###### f


![](VLSI-design-chap3.pdf-9-9.png)

###### V


![](VLSI-design-chap3.pdf-9-10.png)

###### a


![](VLSI-design-chap3.pdf-9-11.png)

###### d


-----

###### Polish expression


![](VLSI-design-chap3.pdf-10-1.png)

###### H


![](VLSI-design-chap3.pdf-10-2.png)

###### H


![](VLSI-design-chap3.pdf-10-8.png)

###### V


###### e f a b c

 a
 d

 • Bottom up: V → ∗ and H → +


### AB+ C D EF∗ ++∗

|b|c e f d|
|---|---|
|a||


![](VLSI-design-chap3.pdf-10-0.png)

###### c
 b

 e f

 a
 d


![](VLSI-design-chap3.pdf-10-1.png)

###### c


![](VLSI-design-chap3.pdf-10-2.png)

###### f


![](VLSI-design-chap3.pdf-10-3.png)

###### V


![](VLSI-design-chap3.pdf-10-4.png)

###### d



###### • Length 2n-1 (n = Number of leaves of the slicing tree)


![](VLSI-design-chap3.pdf-10-0.png)

###### a


![](VLSI-design-chap3.pdf-10-1.png)

###### H


-----

###### Non-slicing floorplans (wheels)


##### a c


![](VLSI-design-chap3.pdf-11-0.png)

##### b
 a
 e
 c
 d


-----

###### Floorplan tree: Tree that represents a hierarchical floorplan

|b|d e g c f|Col3|e|
|---|---|---|---|
|a||||
|||f||
|h||||
|i||||


![](VLSI-design-chap3.pdf-12-0.png)

###### d
 b
 e
 g
 c
 a
 f

 h

 i


![](VLSI-design-chap3.pdf-12-1.png)

###### H


![](VLSI-design-chap3.pdf-12-2.png)

###### V


![](VLSI-design-chap3.pdf-12-3.png)

###### c


![](VLSI-design-chap3.pdf-12-4.png)

###### e


![](VLSI-design-chap3.pdf-12-5.png)

###### a


![](VLSI-design-chap3.pdf-12-8.png)

###### h


![](VLSI-design-chap3.pdf-12-9.png)

###### f


###### Horizontal division HH (objects to the top and bottom)
 Vertical division HV (objects to the left and right)


![](VLSI-design-chap3.pdf-12-0.png)

###### H


![](VLSI-design-chap3.pdf-12-1.png)

###### W


![](VLSI-design-chap3.pdf-12-2.png)

###### g


![](VLSI-design-chap3.pdf-12-5.png)

###### i


###### Wheel (4 objects cycled WH around a center object)


![](VLSI-design-chap3.pdf-12-0.png)

###### HH


![](VLSI-design-chap3.pdf-12-1.png)

###### HH


![](VLSI-design-chap3.pdf-12-2.png)

###### WH


-----

###### • In a vertical constraint graph (VCG), node weights represent the heights of the corresponding blocks.
 − Two nodes vi and vj, with corresponding blocks mi and mj, are connected with a directed edge from vi to vj if mi is below mj.



###### • In a horizontal constraint graph (HCG), node weights represent the widths of the corresponding blocks.
 − Two nodes vi and vj, with corresponding blocks mi and mj, are connected with a directed edge from vi to vj if mi is to the left of mj.



###### • The longest path(s) in the VCG / HCG correspond(s) to the minimum vertical / horizontal floorplan span required to pack the blocks (floorplan height / width).

 • A constraint-graph pair is a floorplan representation that consists of two directed graphs – vertical constraint graph and horizontal constraint graph – which capture the relations between block positions.


-----

###### Constraint graphs

|b|d e g c f|
|---|---|
|a||
|h||
|i||


![](VLSI-design-chap3.pdf-14-0.png)

###### d
 b
 e
 g
 c
 a
 f

 h
 i


###### a


###### f


###### e


###### t


###### g


###### Vertical Constraint Graph


###### t


###### d


###### c


###### b


###### i


###### e


###### g


###### d


###### s


###### Horizontal Constraint Graph


###### h


###### f


###### c


###### a


-----

###### Sequence pair



###### • Two permutations represent geometric relations between every pair of blocks

 • Example: (ABDCE, CBAED)

|A|D|Col3|
|---|---|---|
|B|||
|||E|
|C|||



###### • Horizontal and vertical relations between blocks A and B:

 (… A … B …, … A … B …) → A is left of B (… A … B …, … B … A …) → A is above B (… B … A …, … A … B …) → A is below B (… B … A …, … B … A …) → A is right of B


-----

###### 3.1 Introduction to Floorplanning

 3.2 Optimization Goals in Floorplanning


###### 3.3 Terminology

 3.4 Floorplan Representations 3.4.1 Floorplan to a Constraint-Graph Pair 3.4.2 Floorplan to a Sequence Pair 3.4.3 Sequence Pair to a Floorplan


###### 3.5 Floorplanning Algorithms 3.5.1 Floorplan Sizing 3.5.2 Cluster Growth 3.5.3 Simulated Annealing 3.5.4 Integrated Floorplanning Algorithms

 3.6 Pin Assignment


###### 3.7 Power and Ground Routing 3.7.1 Design of a Power-Ground Distribution Network 3.7.2 Planar Routing 3 7 3 Mesh Routing


-----

###### • Create nodes for every block

 • In addition, create a source node and a sink one


###### a b a b

 s t

|a|Col2|b|
|---|---|---|
|||e|
|c|d||

|a|Col2|b|
|---|---|---|
|||e|
|c|d||


![](VLSI-design-chap3.pdf-17-0.png)

###### a b

 e c d


###### s


-----

###### • Create nodes for every block.

 • In addition, create a source node and a sink one.



###### • Add a directed edge (A,B) if Block A is below/left of Block B. (HCG)

 a b a b


###### s t

|a|Col2|b|
|---|---|---|
|||e|
|c|d||

|a|Col2|b|
|---|---|---|
||||
|c|d|e|


![](VLSI-design-chap3.pdf-18-0.png)

###### a b

 e c d


###### s


-----

###### • Create nodes for every block.

 • In addition, create a source node and a sink one.



###### • Add a directed edge (A,B) if Block A is below/left of Block B. (HCG)

 • Remove the redundant edges that can be derived from other edges by transitivity.


###### a b a b

 s t

|a|Col2|b|
|---|---|---|
|||e|
|c|d||

|a|Col2|b|
|---|---|---|
||||
|c|d|e|


![](VLSI-design-chap3.pdf-19-0.png)

###### a b

 e c d


###### s


-----

###### • Given two blocks A and B with

 − Locations: A = (xA,yA) and B = (xB,yB)


###### − Dimensions: A = (wA,hA) and B = (wB,hB)

 • If             and              or            , x + w ≤ x (! y + h ≤ y y + h ≤ y )
 A A B A A B B B A
 then A is left of B



###### • If             and              or            , y + h ≤ y (!x + w ≤ x x + w ≤ x )
 A A B A A B B B A
 then A is below B

 a b

## S :< acdbe >

###### +
 c d e S− :< cdaeb >

|a|Col2|b|
|---|---|---|
|||e|
|c|d||


![](VLSI-design-chap3.pdf-20-0.png)

###### a b

 e c d


-----

###### • Start with the bottom left corner

 • Define a weighted sequence as a sequence of blocks based on width


###### − Each block B has its own width w(B)

 • Old (traditional) algorithm: find the longest path through edges (O(n[2]))



###### • Newer approach: find the longest common subsequence (LCS)

 − Given two weighted sequences S1 and S2, the LCS(S1,S2) is the longest sequence found in both S1 and S2


###### − The length of LCS(S1,S2) is the sum of weights



###### • For block placement:

 − LCS(S+,S-) returns the x-coordinates of all blocks


###### − LCS(S+R,S-) returns the y-coordinates of all blocks (S+R is the reverse of S+)

_R_


-----

###### Algorithm: Longest Common Subsequence (LCS)

 Input: sequences S1 and S2, weights of n blocks weights


###### Output: positions of each block positions, total span L

 1. for (i = 1 to n) // initialization


###### 2. block_order[S2[i]] = i
 3. lengths[i] = 0
 4. for (i = 1 to n)


###### 5. block = S1[i] // current block
 6. index = block_order[block]
 7. positions[block] = lengths[index] // compute block position


###### 8. t_span = positions[block] + weights[block] // finds length of sequence // from beginning to block
 9. for (j = index to n) // update total length


###### 10. if (t_span > lengths[j]) lengths[j] = t_span
 11. else break


###### 12. L = lengths[n] // total length is stored here


-----

###### Example: S1 = <acdbe>, S2 = <cdaeb>, widths[a b c d e] = [8 4 4 4 4], heights[a b c d e] = [4 2 5 5 6]

 Find x-coordinates – go by S1’s order:


###### Initial: block_order[a b c d e] = [3 5 1 2 4],  lengths = [0 0 0 0 0]

 Iteration 1 – block = a, index = 3: positions[a] = lengths[3] = 0, t_span = 8, lengths = [0 0 8 8 8]


###### Iteration 2 – block = c, index = 1: positions[c] = lengths[1] = 0, t_span = 4, lengths = [4 4 8 8 8]

 Iteration 3 – block = d, index = 2: positions[d] = lengths[2] = 4, t_span = 8, lengths = [4 8 8 8 8]


###### Iteration 4 – block = b, index = 5: positions[b] = lengths[5] = 8, t_span = 12, lengths = [4 8 8 8 12]

 Iteration 5 – block = e, index = 4: positions[e] = lengths[4] = 8, t_span = 12, lengths = [4 8 8 12 12]


###### 0 8 0 8 12


-----

###### Example: S1 = <acdbe>, S2 = <cdaeb>, widths[a b c d e] = [8 4 4 4 4], heights[a b c d e] = [4 2 5 5 6]

 Find y-coordinates – go by S1R’s order:


###### Initial: block_order[a b c d e] = [3 5 1 2 4],  lengths = [0 0 0 0 0]

 Iteration 1 – block = e, index = 4: positions[e] = lengths[4] = 0, t_span = 6, lengths = [0 0 0 6 6]


###### Iteration 2 – block = b, index = 5: positions[b] = lengths[5] = 6, t_span = 9, lengths = [0 0 0 6 9]

 Iteration 3 – block = d, index = 2: positions[d] = lengths[2] = 0, t_span = 5, lengths = [0 5 5 6 9]


###### Iteration 4 – block = c, index = 1: positions[c] = lengths[1] = 0, t_span = 5, lengths = [5 5 5 6 9]

 Iteration 5 – block = a, index = 3: positions[a] = lengths[3] = 5, t_span = 9, lengths = [5 5 9 9 9]


###### 6 0 0 0 9


-----

###### 3.1 Introduction to Floorplanning

 3.2 Optimization Goals in Floorplanning


###### 3.3 Terminology

 3.4 Floorplan Representations 3.4.1 Floorplan to a Constraint-Graph Pair 3.4.2 Floorplan to a Sequence Pair 3.4.3 Sequence Pair to a Floorplan


###### 3.5 Floorplanning Algorithms 3.5.1 Floorplan Sizing 3.5.2 Cluster Growth 3.5.3 Simulated Annealing 3.5.4 Integrated Floorplanning Algorithms

 3.6 Pin Assignment


###### 3.7 Power and Ground Routing 3.7.1 Design of a Power-Ground Distribution Network 3.7.2 Planar Routing 3 7 3 Mesh Routing


-----

###### Common Goals



###### • To minimize the total length of interconnect, subject to an upper bound on the floorplan area

 or



###### • To simultaneously optimize both wire length and area


-----

###### Shape functions


###### h


###### h
 Legal shapes Legal shapes

 w


###### w


###### ha*aw ≥ A


###### Block with minimum width and height restrictions


-----

###### Shape functions


###### h


###### h


###### w


###### w


###### Discrete (h,w) values


###### Hard library block


-----

###### Corner points


##### 5


##### 2 5


##### 2


##### 2

 5


##### w

|Col1|h|Col3|
|---|---|---|
||5 2||
||||
||5 2||
||||


-----

###### Algorithm


###### This algorithm finds the minimum floorplan area for a given slicing floorplan in

 polynomial time. For non-slicing floorplans, the problem is NP-hard.



###### • Construct the shape functions of all individual blocks

 • Bottom up: Determine the shape function of the top-level floorplan from the shape functions of the individual blocks



###### • Top down: From the corner point that corresponds to the minimum top-level floorplan area, trace back to each block’s shape function to find that block’s dimensions and location.


-----

###### Step 1:  Construct the shape functions of the blocks

 3


###### Block A:

 Block B:


###### 5

 4


###### 5


###### 3


###### 2


###### 2


###### 4


-----

###### Step 1:  Construct the shape functions of the blocks


###### 3


#### h

###### 6
 5
 4


###### Block A:

 Block B:


###### 5

 4

|5 3 6|Col2|
|---|---|


###### 2


###### 2


###### 2


###### 4


###### 2 3 4 6 w


-----

###### Step 1:  Construct the shape functions of the blocks


###### 3


#### h

###### 6

 4
 3
 2


###### Block A:

 Block B:


###### 5

 4

|5 3 6 4|Col2|
|---|---|


###### 2


###### 2


###### 4


###### 2 4 5 6 w


-----

###### Step 1:  Construct the shape functions of the blocks

 3 h


###### Block A:

 Block B:


###### 5

 4


###### 2


###### 4


###### hA(w)

 2 4 6 w


-----

###### Step 1:  Construct the shape functions of the blocks

 3 h


###### Block A:

 Block B:


###### 5

 4


###### 2


###### 4


###### hB(w)

 2 4 6 w


-----

###### Step 2:  Determine the shape function of the top-level floorplan (vertical)

#### h


###### 8

 6


###### 4

 2


###### hA(w)
 hB(w)

 2 4 6 w


-----

-----

###### Step 2:  Determine the shape function of the top-level floorplan (vertical)

#### h h


###### 8 8

 6 6


###### hC(w)


###### 4

 2


###### hA(w)
 hB(w)

 2 4 6 w


###### hB(w)

 2 4 6 w


-----

###### Step 2:  Determine the shape function of the top-level floorplan (vertical)


#### h


#### h


###### 8 8


###### 6

 4


###### 6


###### 4

 2


###### 2


###### hA(w)
 hB(w)

 2 4 6 w

|h (w) C h (w) A 5 x 5 h (w) B 2 4 6 w|Col2|Col3|
|---|---|---|
||||


-----

###### Step 2:  Determine the shape function of the top-level floorplan (vertical)

|3|x 9|
|---|---|


#### h


#### h


###### 8 8


###### 6

 4


###### 6

 4

|Col1|Col2|Col3|
|---|---|---|
|4|x 7||


###### 2


###### hA(w)
 hB(w)

 2 4 6 w


###### 2

|tion of the top-level floorplan (vertical)|Col2|Col3|
|---|---|---|
|3 x 9 4 x 7 h (w) C h (w) A 5 x 5 h (w) B 2 4 6 w|||
||||


-----

###### Step 2:  Determine the shape function of the top-level floorplan (vertical)

 3 x 9

#### h h

|3|x 9|
|---|---|


###### 8 8

 6 6

|Col1|Col2|Col3|
|---|---|---|
|4|x 7||


###### 4

 2


###### hA(w)
 hB(w)

 2 4 6 w


###### Minimimum top-level floorplan with vertical composition


-----

###### Step 2:  Determine the shape function of the top-level floorplan (horizontal)

 hB(w) hA(w) hB(w) hA(w) hC(w)


##### h

###### 6


##### h

|5 x|5|
|---|---|

|Col1|Col2|
|---|---|
|5||


###### 4

 2

|4|Col2|
|---|---|
|||


###### 2

 2 4 6 8 w 2 4 6 8 w


###### 6

 4

|9 x 3|Col2|Col3|Col4|
|---|---|---|---|
||x 3|||
|||||


###### Minimimum top-level floorplan with horizontal composition


-----

###### Step 3:  Find the individual blocks’ dimensions and locations

##### h

###### (1) Minimum area floorplan: 5 x 5

 6

 4

 2

 2 4 6 8 w

|Col1|Col2|Col3|(1) Minimum area floorplan: 5 x 5|
|---|---|---|---|
|||||
|||||


###### Horizontal composition


-----

###### Step 3:  Find the individual blocks’ dimensions and locations

##### h

###### (1) Minimum area floorplan: 5 x 5

 6

 4

 2 (2) Derived block dimensions : 2 x 4 and 3 x 5

 2 4 6 8 w


###### Horizontal composition


-----

###### Step 3:  Find the individual blocks’ dimensions and locations

##### h

###### (1) Minimum area floorplan: 5 x 5

 6

 4

 2 (2) Derived block dimensions : 2 x 4 and 3 x 5

 2 4 6 8 w

|(2) Derived block dimensions : 2 x 4 and 3 x 5|Col2|
|---|---|


###### 2 x 4 3 x 5


###### Horizontal composition


-----

### B


### A

|Col1|Col2|
|---|---|
||Resulting slicing tree|
|||

|Col1|A|
|---|---|
|B||


###### 2 x 4 3 x 5


-----

###### • Iteratively add blocks to the cluster until all blocks are assigned

 • Only the different orientations of the blocks instead of the shape / aspect ratio are taken into account



###### • Linear ordering to minimize total wirelength of connections between blocks


###### h


###### h

 b b


###### Growth direction


###### 6


###### 6


![](VLSI-design-chap3.pdf-47-0.png)

###### 2


![](VLSI-design-chap3.pdf-47-0.png)

###### a a a
 w w


###### w

|Col1|b|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||a||||||||
||||||||||

|Col1|Col2|b|Col4|Col5|c|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
||||||c|||||
|||||||||||
|||||||||||
|||a||||||||
|||||||||||
|||||||||||

|Col1|h|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
||a|||||||
|||||||||
|||||||||


###### 4


###### 4


###### 4


-----

###### • New nets have no pins on any block from the partially-constructed ordering

 • Terminating nets have no other incident blocks that are unplaced



###### • Continuing nets have at least one pin on a block from the partially-constructed ordering and at least one pin on an unordered block

 Terminating nets New nets


###### …

 Continuing nets


-----

###### • Gain of each block m is calculated:

 Gainm = (Number of terminating nets of m) – (New nets of m)


###### N4

 • The block with the maximum gain is selected to be placed next


-----

###### Given: 
#### – Netlist with five blocks A, B, C, D, E and six nets
###### N1 = {A, B}  N2 = {A, D} N3 = {A, C, E} N4 = {B, D} N5 = {C, D, E} N6 = {D, E}

#### – Initial block: A

###### N3


###### N4

 Task: Linear ordering with minimum netlength


-----

1


###### N4

 Iteration Block New Nets #


5

###### D E
 N6

 Terminating Gain Nets


###### Continuing Nets


###### 0 A N,N,N -- -3 -1 2 3


###### 1

 2


###### -

###### C N -- -1 N

5 3

###### D N,N,N N -2 - Initial block 4Gain5 A6 = (Number of terminating nets of 2 A) – (New nets of A)
 E N,N -- -2 N

5 6 3


###### 3


###### N
3

###### - N
3

###### N,N
3 5
###### N,N
3 5


###### 4 N1 C N4-- N5 N3,N5 2 -
|Block A B C D tial block E C D E C N E 3|New Nets N,N,N 1 2 3 N 4 N 5 N,N,N Gain = 4 5 A6 N,N 5 6 N 5 N,N 5 6 N,N 5 6 -- --|Terminating Nets -- N 1 -- N (Number of termina 2 -- -- N,N 2 4 -- -- N 6|Col4|
|---|---|---|---|
|||N N 5|,N 3 5|
|||||


###### A B D E C


-----

1


###### N4

 Iteration Block New Nets #


5

###### D E
 N6

 Terminating Gain Nets


###### Continuing Nets


###### 0 A N,N,N -- -3 -1 2 3


###### 1


###### 2

 3


###### N,N
3 5
###### N,N
3 5


###### - N
3

###### - N
3

###### N
3

###### - N
3


###### 4 N1 C N4-- N5 N3,N5 2 -
|Block A B C D E C D E C N E 3|New Nets N,N,N 1 2 3 N 4 N 5 N,N,N 4 5 6 N,N 5 6 N 5 N,N 5 6 N,N 5 6 -- --|Terminating Nets -- N 1 -- N 2 -- -- N,N 2 4 -- -- N 6|Col4|
|---|---|---|---|
|||N N 5|,N 3 5|
|||||


###### A B D E C


-----

1


###### N4

 Iteration Block New Nets #


5

###### D E
 N6

 Terminating Gain Nets


###### Continuing Nets


###### 0 A N,N,N -- -3 -1 2 3


###### 1

 2


###### - N
3

###### - N
3

###### N
3

###### - N
3


###### 3


###### N,N
3 5
###### N,N
3 5


###### 4 N1 C N4-- N5 N3,N5 2 -
|Block A B C D E C D E C N E 3|New Nets N,N,N 1 2 3 N 4 N 5 N,N,N 4 5 6 N,N 5 6 N 5 N,N 5 6 N,N 5 6 -- --|Terminating Nets -- N 1 -- N 2 -- -- N,N 2 4 -- -- N 6|Col4|
|---|---|---|---|
|||N N 5|,N 3 5|
|||||


###### A B D E C


-----

1


5


###### N4

|Iteration # 0 1 2 3 4|Block A B C D E C D E C E C|New Nets N ,N ,N 1 2 3 N 4 N 5 N ,N ,N 4 5 6 N ,N 5 6 N 5 N ,N 5 6 N ,N 5 6 -- -- --|Terminating Nets -- N 1 -- N 2 -- -- N ,N 2 4 -- -- N 6 N ,N 3 5|Gain -3 0 -1 -2 -2 -1 0 -2 0 1 2|Continuing Nets -- -- N 3 -- N 3 N 3 -- N 3 N ,N 3 5 N ,N 3 5 --|
|---|---|---|---|---|---|


-----

###### N3
 N1

 N2

 N3


###### N4


![](VLSI-design-chap3.pdf-55-0.png)

-----

###### Input: set of all blocks M, cost function C

 Output: optimized floorplan F based on C


###### F = Ø

 order = LINEAR_ORDERING(M) // generate linear ordering


###### for (i = 1 to |order|)

 curr_block = order[i]


###### ADD_TO_FLOORPLAN(F,curr_block,C) // find location and orientation

 // of curr_block that causes


###### // smallest increase based on

 // C while obeying constraints


-----

###### Analysis



###### • The objective is to minimize the total wirelength of connections blocks

 • Though this produces mediocre solutions, the algorithm is easy to implement and fast.



###### • Can be used to find the initial floorplan solutions for iterative algorithms such as simulated annealing.


-----

###### Introduction



###### • Simulated Annealing (SA) algorithms are iterative in nature.

 • Begins with an initial (arbitrary) solution and seeks to incrementally improve the objective function.



###### • During each iteration, a local neighborhood of the current solution is considered. A new candidate solution is formed by a small perturbation of the current solution.

 • Unlike greedy algorithms, SA algorithms can accept candidate solutions with higher cost.


-----

###### Cost


###### Solution states


-----

###### What is annealing?



###### • Definition (from material science): controlled cooling process of high-temperature materials to modify their properties.

 • Cooling changes material structure from being highly randomized (chaotic) to being structured (stable).



###### • The way that atoms settle in low-temperature state is probabilistic in nature.

 • Slower cooling has a higher probability of achieving a perfect lattice with minimum-energy


###### − Cooling process occurs in steps

 − Atoms need enough time to try different structures


###### − Sometimes, atoms may move across larger distances and create (intermediate) higher-energy states


-----

###### Simulated Annealing



###### • Generate an initial solution Sinit, and evaluate its cost.

 • Generate a new solution Snew by performing a random walk



###### • Snew is accepted or rejected based on the temperature T
 − Higher T means a higher probability to accept Snew if COST(Snew) > COST(Sinit)


###### − T slowly decreases to form the final solution



###### • Boltzmann acceptance criterion, where r is a random number [0,1)

 COST (S )−COST (S )
_init_ _new_
# e T > r


-----

###### Simulated Annealing



###### • Generate an initial solution and evaluate its cost

 • Generate a new solution by performing a random walk



###### • Solution is accepted or rejected based on a temperature parameter T

 • Higher T indicates higher probability to accept a solution with higher cost



###### • T slowly decreases to form the finalized solution.

 • Boltzmann acceptance criterion:


currsol : current solution

nextsol: new solution after perturbation


![](VLSI-design-chap3.pdf-62-0.png)

T: current temperature

r: random number between[0,1) from normal distr.


-----

![](VLSI-design-chap3.pdf-63-0.png)

-----

###### Input: initial solution init_sol
 Output: optimized new solution curr_sol


###### T = T0 // initialization
 i = 0 curr_sol = init_sol curr_cost = COST(curr_sol) while (T > Tmin)
 while (stopping criterion is not met)
 i = i + 1 (ai,bi) = SELECT_PAIR(curr_sol) // select two objects to perturb
 trial_sol = TRY_MOVE(ai,bi) // try small local change
 trial_cost = COST(trial_sol) ∆cost = trial_cost – curr_cost if (∆cost < 0) // if there is improvement,


###### else


###### curr_cost = trial_cost // update the cost and
 curr_sol = MOVE(ai,bi) // execute the move


###### r = RANDOM(0,1) // random number [0,1]
 if (r < e [–Δ][cost][/][T]) // if it meets threshold,


###### curr_cost = trial_cost //  update the cost and
 curr_sol = MOVE(ai,bi) //  execute the move
 T = α ∙ T // 0 < α < 1 T reduction


-----

###### 3.1 Introduction to Floorplanning

 3.2 Optimization Goals in Floorplanning


###### 3.3 Terminology

 3.4 Floorplan Representations 3.4.1 Floorplan to a Constraint-Graph Pair 3.4.2 Floorplan to a Sequence Pair 3.4.3 Sequence Pair to a Floorplan


###### 3.5 Floorplanning Algorithms 3.5.1 Floorplan Sizing 3.5.2 Cluster Growth 3.5.3 Simulated Annealing 3.5.4 Integrated Floorplanning Algorithms

 3.6 Pin Assignment


###### 3.7 Power and Ground Routing 3.7.1 Design of a Power-Ground Distribution Network 3.7.2 Planar Routing 3 7 3 Mesh Routing


-----

###### During pin assignment, all nets (signals) are assigned to unique pin locations such that the overall design performance is optimized.

 Pin Assignment
 90 Pins 90 Pins


![](VLSI-design-chap3.pdf-66-2.png)

###### 90 Connections

 90 Pins 90 Pins


![](VLSI-design-chap3.pdf-66-0.png)

###### 90 Pins

 90 Pins


-----

###### Given: Two sets of pins (1) Determine the circles


![](VLSI-design-chap3.pdf-67-0.png)

-----

###### (2) Determine the points


-----

###### (2) Determine the points


-----

###### (3) Determine initial mapping


-----

###### (3) Determine initial mapping and (4) optimize the mapping (complete rotation)


-----

###### (3) Determine initial mapping and (4) optimize the mapping (complete rotation)


-----

###### (4) Best mapping (shortest Euclidean distance)


-----

###### (4) Best mapping


![](VLSI-design-chap3.pdf-74-0.png)

-----

###### Pin assignment to an external block B


##### B B

 mm

 l’


-----

###### Pin assignment to two external blocks A and B


##### a7 a6


![](VLSI-design-chap3.pdf-76-0.png)

##### m


##### a


-----

###### 3.1 Introduction to Floorplanning

 3.2 Optimization Goals in Floorplanning


###### 3.3 Terminology

 3.4 Floorplan Representations 3.4.1 Floorplan to a Constraint-Graph Pair 3.4.2 Floorplan to a Sequence Pair 3.4.3 Sequence Pair to a Floorplan


###### 3.5 Floorplanning Algorithms 3.5.1 Floorplan Sizing 3.5.2 Cluster Growth 3.5.3 Simulated Annealing 3.5.4 Integrated Floorplanning Algorithms

 3.6 Pin Assignment


###### 3.7 Power and Ground Routing 3.7.1 Design of a Power-Ground Distribution Network 3.7.2 Planar Routing 3 7 3 Mesh Routing


-----

###### Power-ground distribution for a chip floorplan


##### Power and ground rings per block or abutted blocks

|G V G V V V G G V G V V G G V G V G V|Col2|Col3|G|Col5|Col6|V|Col8|Col9|G|Col11|Col12|Col13|Col14|Col15|V|Col17|Col18|Col19|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||
||||||||||||||||||||
||V|||||||||||||||||V|
||||||||||||||||||||
||G||||||||||||||||||
|||||||||||||||||||G|
||||||||||||||||||||
||V||||||||||||||||||
||||||||||||||||||||
||G|||||||||||||||||V|
||||||||||||||||||||
||||||||||||||||||||
||V||||||||||||||||||
|||||||||||||||||||G|
||||||||||||||||||||
||||||||||||||||||||
||||G||V|||G||V|||G|||V|||
||||||||||||||||||||


##### Trunks connect rings to each other or to top-level power ring


-----

###### Planar routing


![](VLSI-design-chap3.pdf-79-0.png)

###### GND VDD


###### Hamiltonian path


-----

###### Planar routing


###### Step 1: Planarize the topology of the nets

 − As both power and ground nets must be routed on one layer, the design should be split using the Hamiltonian path


###### Step 2: Layer assignment

 − Net segments are assigned to appropriate routing layers


###### Step 3: Determining the widths of the net segments

 − A segment’s width is determined from the sum of the currents from all the cells to which it connects


-----

###### Planar routing


###### GND VDD

 Generating topology of the two supply nets


![](VLSI-design-chap3.pdf-81-0.png)

###### GND VDD


###### Adjusting widths of the segments with regard to their current loads


![](VLSI-design-chap3.pdf-81-0.png)

-----

###### Mesh routing


###### Step 1: Creating a ring

 − A ring is constructed to surround the entire core area of the chip, and possibly individual blocks.


###### Step 2: Connecting I/O pads to the ring

 Step 3: Creating a mesh


###### − A power mesh consists of a set of stripes at defined pitches on two or more layers


###### Step 4: Creating Metal1 rails

 − Power mesh consists of a set of stripes at defined pitches on two or more layers


###### Step 5: Connecting the Metal1 rails to the mesh 


-----

###### Mesh routing


##### Power rail

 Pad
 Ring Mesh

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Connector|Col14|Col15|Col16|Col17|Col18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|Power rail||||||||||||Connector||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||


-----

###### Mesh routing


###### 1µ Metal4 mesh


###### 2µ Metal6 mesh


###### 4µ Metal8 mesh


###### 1µ Metal5 mesh

_GND_
Metal4 mesh

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|l5|||16µ|||||
|||||||||
|||||||||
|||||||||
|||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
|||||||
||||1|6µ||
|||||||
|||||||
|||||||
|||||||
|||||||


Metal4

Via3

Metal3

Via2

Metal2

Via1

Metal1


###### Metal1 rail

_VDD_
Metal4 mesh


_VDD rail_


###### 4µ Metal7 mesh

Metal8

Via7

Metal7

Via6

Metal6


Metal6

Via5

Metal5

Via4

Metal4

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|al7 h|||16µ|||||
|||||||||
|||||||||
|||||||||
|l8 l7||||||||


-----

###### • Traditional floorplanning
 − Assumes area estimates for top-level circuit modules


###### − Determines shapes and locations of circuit modules
 − Minimizes chip area and length of global interconnect



###### • Additional aspects
 − Assigning/placing I/O pads


###### − Defining channels between blocks for routing and buffering
 − Design of power and ground networks


###### − Estimation and optimization of chip timing and routing congestion



###### • Fixed-outline floorplanning
 − Chip size is fixed, focus on interconnect optimization


###### − Can be applied to individual chip partitions (hierarchically)



###### • Structure and types of floorplans
 − Slicing versus non-slicing, the wheels


###### − Hierarchical
 − Packed


###### − Zero-deadspace


-----

###### • Slicing trees and Polish expressions
 − Evaluating a floorplan represented by a Polish expression



###### • Horizontal and vertical constraint graphs
 − A data structure to capture (non-slicing) floorplans


###### − Longest paths determine floorplan dimensions



###### • Sequence pair
 − An array-based data structure that captures the information


###### − contained in H+V constraint graphs
 − Makes constraint graphs unnecessary in practice



###### • Floorplan sizing
 − Shape-function arithmetic


###### − An algorithm for slicing floorplans


-----

###### • Cluster growth
 − Simple, fast and intuitive


###### − Not competitive in practice



###### • Simulated annealing
 − Stochastic optimization with hill-climbing


###### − Many details required for high-quality implementation (e.g., temperature schedule)
 − Difficult to debug, fairly slow


###### − Competitive in practice



###### • Pin assignment
 − Peripheral I/Os versus area-array I/Os


###### − Given "ideal locations", project them onto perimeter and shift around, while preserving initial ordering



###### • Power and ground routing
 − Planar routing in channels between blocks


###### − Can form rings around blocks to increase current supplied and to improve reliability
 − Mesh routing


-----

