![](VLSI-design-chap4.pdf-0-0.png)

-----

###### 4.1 Introduction

 4.2 Optimization Objectives


###### 4.3 Global Placement 4.3.1 Min-Cut Placement 4.3.2 Analytic Placement 4.3.3 Simulated Annealing
 4.3.4 Modern Placement Algorithms


###### 4.4 Legalization and Detailed Placement


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

###### Linear Placement
 c

 g h a c b g h d f

 f

 h e d a

**VDD**

###### e d a

**GND**

###### g f c b
 f c b

 2D Placement Placement and Routing with Standard Cells

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||h e d a g f c b|||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||h e||||||||||||||||||||||
|||||||||||||||||||||||||||
||||||h||||e||||d||||||a|||||||
|||||||||||||||||||||||||||
||VDD|||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||GND||
||||||g|||||f|||c||||||b|||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||
|||||||||||||||||||||||||||


![](VLSI-design-chap4.pdf-3-0.png)

###### h e d a

**VDD**

**GND**

###### g f c b


![](VLSI-design-chap4.pdf-3-1.png)

###### a c b g h d f e


![](VLSI-design-chap4.pdf-3-2.png)

-----

###### Global Placement


###### Detailed Placement


![](VLSI-design-chap4.pdf-4-0.png)

-----

###### Total Wirelength


###### Number of Cut Nets


###### Wire Congestion


###### Signal Delay


![](VLSI-design-chap4.pdf-5-0.png)

-----

|f|Col2|Col3|
|---|---|---|
|||l|


![](VLSI-design-chap4.pdf-6-0.png)

###### e
 h a j

 c
 f l i

 b

 k g
 d


![](VLSI-design-chap4.pdf-6-2.png)

-----

###### Wirelength estimation for a given placement


###### Half-perimeter wirelength (HPWL)


###### Complete graph (clique)


###### Monotone chain


###### Star model

|Col1|Col2|4|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
|||||||5|
||||||||
||||||||
||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|8|||||||
||||||5||
||||||||
||||||||
|||3||||6|
||||||3||
||4||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||3||||6||
||||||||
|||3|||||
||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||3||||8||
||||||||
||||||||
||4||||||


![](VLSI-design-chap4.pdf-7-0.png)

###### 3 8

 4


![](VLSI-design-chap4.pdf-7-1.png)

###### 8
 5

 3 6 3

 4


###### Star Length = 15


![](VLSI-design-chap4.pdf-7-0.png)

###### 4

 5


###### Chain Length = 12


![](VLSI-design-chap4.pdf-7-0.png)

###### 3 6

 3


###### HPWL = 9


###### Clique Length = (2/p)Σe ∈ cliquedM(e) = 14.5


-----

###### Wirelength estimation for a given placement (cont‘d.)


###### Rectilinear minimum spanning tree (RMST)


###### Rectilinear Steiner minimum tree (RSMT)


###### Rectilinear Steiner arborescence model (RSA)


###### Single-trunk  Steiner tree (STST)

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
|||||||5|||
||||||||||
||3||||||||
||||||||||
|||3|||||||
||||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
|||||||6|||
|||||1|||||
||3||||||||
||||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
||||||||+5||
||||||||||
||3|||+2|||||
||||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||3||
||||||||||
||4||||||||
||1||||||||
|||||2|||||
||||||||||


![](VLSI-design-chap4.pdf-8-0.png)

###### +5

 3 [+2]


![](VLSI-design-chap4.pdf-8-1.png)

###### 6
 1
 3


###### RMST Length = 11


![](VLSI-design-chap4.pdf-8-0.png)

###### 5
 3

 3


###### RSMT Length = 10


![](VLSI-design-chap4.pdf-8-0.png)

###### 3
 4

 1 2


###### RSA Length = 10


###### STST Length = 10


-----

###### Wirelength estimation for a given placement (cont‘d.)

 Preferred method: Half-perimeter wirelength (HPWL)
 • Fast (order of magnitude faster than RSMT)
 • Equal to length of RSMT for 2- and 3-pin nets
 • Margin of error for real circuits approx. 8% [Chu, ICCAD 04]


###### L = w + h
HPWL

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
|||||||||||
|||||||||6||
|||||||1||||
|||||||||||
||||3|||||||
|||||||||||
|||||||||||

|Col1|Col2|Col3|Col4|4|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
|||||||||||
||||h||||||5|
|||||||||||
|||||||||||
|||||w||||||
|||||||||||
|||||||||||


![](VLSI-design-chap4.pdf-9-0.png)

###### 4

 h
 5

 w


###### RSMT Length = 10


![](VLSI-design-chap4.pdf-9-0.png)

###### 6
 1
 3


###### HPWL = 9


-----

###### Total wirelength with net weights (weighted wirelength)



###### • For a placement P, an estimate of total weighted wirelength is


###### L(P) = w(net) ⋅ L(net)

#### ∑

###### net∈P


###### where w(net) is the weight of net, and L(net) is the estimated wirelength of net.



###### • Example:

 Nets Weights

|c|Col2|
|---|---|


###### N1 = (a1, b1, d2) w(N1) = 2
 d
 N2 = (c1, d1, f1) w(N2) = 4
 b
 N3 = (e1, f2) w(N3) = 1 b1

 L(P) = w(net) ⋅ L(net) = 2 ⋅ 7 + 4 ⋅ 4 +1⋅ 3 = 33
#### ∑

|d|Col2|
|---|---|

|e|Col2|
|---|---|

|a|a 1|c|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||c 1||||||
|||d 1|||||||
||||||||||
|||d|||f 1||f||
|b||d 2|||f 2||||
||b 1||e 1||||||
||||e||||||


![](VLSI-design-chap4.pdf-10-0.png)

###### a c
 a 1
 c
1

###### d
1

###### f
 d 1 f
 d
2 _f_

###### b 2
 b1 e1
 e


-----

###### Cut sizes of a placement



###### • To improve total wirelength of a placement P, separately calculate the number of crossings of global vertical and horizontal cutlines, and minimize

 L(P) = ψ (v) + ψ (h) P P

# ∑ ∑

###### v∈VP h∈H P


###### where ΨP(cut) be the set of nets cut by a cutline cut


-----

###### Cut sizes of a placement



###### • Example:

 Nets N1 = (a1, b1, d2) N2 = (c1, d1, f1) N3 = (e1, f2)

|c|Col2|
|---|---|


###### h
2 _d_

1

###### f
 d 1
 d
 h1 b 2 f2

|d|Col2|
|---|---|



###### • Cut values for each global cutline ψP(v1) = 1 ψP(v2) = 2
 ψP(h1) = 3 ψP(h2) = 2

 • Total number of crossings in P ψP(v1) + ψP(v2) + ψP(h1) + ψP(h2) = 1 + 2 + 3 + 2 = 8

|Col1|e|
|---|---|

|a|Col2|Col3|a 1|c|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||c 1||||||
||||||||||||
||||||||||||
|||||d|||||||
|||||1 d|||f 1||f||
|||||d 2|||f||||
||||||||||||
||b||||||2||||
||||b 1||e 1||||||
||||||||e||||


![](VLSI-design-chap4.pdf-12-0.png)

###### a c
 a 1
 c
1

###### d
1

###### f
 d 1 f
 d
2 _f_

###### b 2
 b
1 _e_
1

###### e


###### v v
1 2



###### • Cut sizes X(P) = max(ψP(v1),ψP(v2)) = max(1,2) = 2 Y(P) = max(ψP(h1),ψP(h2)) = max(3,2) = 3


-----

###### Routing congestion of a placement



###### • Ratio of demand for routing tracks to the supply of available routing tracks

 • Estimated by the number of nets that pass through the boundaries of individual routing regions


###### SB CH SB CH

 Wire capacities

|Col1|Col2|Col3|
|---|---|---|
||SB||
||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||SB||||CH||
|||||||||
|||||||||
|||||||||


![](VLSI-design-chap4.pdf-13-0.png)

###### SB CH


-----

###### Routing congestion of a placement



###### • Formally, the local wire density φP(e) of an edge e between two neighboring grid cells is
 η (e) φ (e) = P
 P
 σ (e) P

 where ηP(e) is the estimated number of nets that cross e and σP(e) is the maximum number of nets that can cross e



###### • If φP(e) > 1, then too many nets are estimated to cross e, making P more likely to be unroutable. 



###### • The wire density of P is


###### Φ(P) = max(φ (e)) P e∈E


###### where E is the set of all edges

 • If Φ(P) ≤ 1, then the design is estimated to be fully routable, otherwise routing will need to detour some nets through less-congested edges


-----

###### Wire Density of a placement


###### ηP(h1) = 1 ηP(h2) = 2 ηP(h3) = 0 ηP(h4) = 1 ηP(h5) = 1 ηP(h6) = 0


###### ηP(v1) = 1 ηP(v2) = 0 ηP(v3) = 0 ηP(v4) = 0 ηP(v5) = 2 ηP(v6) = 0

|c|Col2|
|---|---|


###### h
4

###### h
1


###### v v
3 6

###### c

 h
5

###### d

 h
2

###### v v
1 4


###### h
6

###### h
3

|d|Col2|
|---|---|

|Col1|e|
|---|---|

|a|Col2|Col3|Col4|c|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|||||h 5|||||||
||||||||||||
||||||||||||
||||v 2|d|||v 5||f||
||||||||||||
||||||||||||
||b||||||||||
|||||h|2||||||
||||||||e||||


![](VLSI-design-chap4.pdf-15-0.png)

###### c
 a
 h
5

###### v2 d v5 f

 b
 h
2

###### e


###### Maximum: ηP(e) = 2

 η (e) 2 Φ(P) = P = Routable


![](VLSI-design-chap4.pdf-15-0.png)

-----

###### Circuit timing of a placement



###### • Static timing analysis using actual arrival time (AAT) and required arrival time (RAT)

 − AAT(v) represents the latest transition time at a given node v measured from the beginning of the clock cycle


###### − RAT(v) represents the time by which the latest transition at v must complete in order for the circuit to operate correctly within a given clock cycle.

 • For correct operation of the chip with respect to setup (maximum path delay) constraints, it is required that AAT(v) ≤ RAT(v).


-----

###### 4.1 Introduction

 4.2 Optimization Objectives


###### 4.3 Global Placement 4.3.1 Min-Cut Placement 4.3.2 Analytic Placement 4.3.3 Simulated Annealing
 4.3.4 Modern Placement Algorithms


###### 4.4 Legalization and Detailed Placement


-----

###### • Partitioning-based algorithms:

 − The netlist and the layout are divided into smaller sub-netlists and sub-regions, respectively


###### − Process is repeated until each sub-netlist and sub-region is small enough to be handled optimally

 − Detailed placement often performed by optimal solvers, facilitating a natural transition from global placement to detailed placement


###### − Example: min-cut placement



###### • Analytic techniques:

 − Model the placement problem using an objective (cost) function, which can be optimized via numerical analysis


###### − Examples: quadratic placement and force-directed placement



###### • Stochastic algorithms:

 − Randomized moves that allow hill-climbing are used to optimize the cost function


###### − Example: simulated annealing


-----

###### Partitioning-based Analytic Stochastic


![](VLSI-design-chap4.pdf-19-0.png)

![](VLSI-design-chap4.pdf-19-1.png)

###### Min-cut placement


![](VLSI-design-chap4.pdf-19-0.png)

###### Quadratic placement


![](VLSI-design-chap4.pdf-19-0.png)

###### Force-directed Simulated annealing placement


-----

###### • Uses partitioning algorithms to divide (1) the netlist and (2) the layout region into smaller sub-netlists and sub-regions

 • Conceptually, each sub-region is assigned a portion of the original netlist



###### • Each cut heuristically minimizes the number of cut nets using, for example,

 − Kernighan-Lin (KL) algorithm


###### − Fiduccia-Mattheyses (FM) algorithm


-----

###### Alternating cutline directions


###### Repeating cutline directions


###### 3a

 1


###### 2a

 1


###### 3c


###### 2a

 2b


###### 3b

 3d


###### 2b

|4a|Col2|Col3|4c|
|---|---|---|---|
|4b|||4d|
|4e|||4g|
|4f|||4h|

|4a|3a|4e|Col4|
|---|---|---|---|
|4b|3b|4f||
|4c|3c|4g||
|4d|3d|4h||


![](VLSI-design-chap4.pdf-21-0.png)

###### 4a 4c

 4b 4d

 4e 4g

 4f 4h


-----

###### Input: netlist Netlist, layout area LA, minimum number of cells per region cells_min
 Output: placement P


###### P = Ø regions = ASSIGN(Netlist,LA) // assign netlist to layout area
 while (regions != Ø) // while regions still not placed


###### region = FIRST_ELEMENT(regions) // first element in regions
 REMOVE(regions, region) // remove first element of regions


###### if (region contains more than cell_min cells)
 (sr1,sr2) = BISECT(region) // divide region into two subregions //  sr1 and sr2, obtaining the sub- //  netlists and sub-areas


###### ADD_TO_END(regions,sr1) // add sr1 to the end of regions
 ADD_TO_END(regions,sr2) // add sr2 to the end of regions
 else


###### PLACE(region) // place region
 ADD(P,region) // add region to P


-----

###### Given:


###### 1


###### cut1

|2 3|4 5 6|
|---|---|


###### Task: 4 x 2 placement with minimum wirelength using alternative cutline directions and the KL algorithm


-----

###### Vertical cut cut1: L={1,2,3}, R={4,5,6}

 1 4 1 4

 2 5 2

 3 6 0

 0 0 KL Algorithm

 cut1 cut1

|1 4 2|5 3 6|
|---|---|

|1 2 3 0|4 5 6 0|
|---|---|


-----

###### 1


###### 4 5


###### 2 3

 0

 cut1


![](VLSI-design-chap4.pdf-25-2.png)

###### Horizontal cut cut2L: T={1,4}, B={2,0}


![](VLSI-design-chap4.pdf-25-2.png)

###### Horizontal cut cut2R: T={3,5}, B={6,0}


###### cut2L cut2R


![](VLSI-design-chap4.pdf-25-0.png)

###### cut3TL cut3TR

 4 5 3

 2 6 0

 cut cut


![](VLSI-design-chap4.pdf-25-0.png)

###### 1 4 5 3

 2 6

|1 0|4|5|3|
|---|---|---|---|
||2|6|0|


-----

###### 4 1

|2|4 3|
|---|---|
|1||

|2|TR 3|
|---|---|
|1|4 BR|



###### • Terminal Propagation
 − External connections are represented by artificial connection points on the cutline


###### − Dummy nodes in hypergraphs


###### x

|2|x 4 3|
|---|---|
|1||

|2|TR p‘ 4|
|---|---|
|1|3 BR|

|2 4 1 3|Col2|
|---|---|
|||


-----

###### • Advantages:

 − Reasonably fast


###### − Objective function can be adjusted, e.g., to perform timing-driven placement

 − Hierarchical strategy applicable to large circuits



###### • Disadvantages:

 − Randomized, chaotic algorithms – small changes in input lead to large changes in output


###### − Optimizing one cutline at a time may result in routing congestion elsewhere


-----

###### • Objective function is quadratic; sum of (weighted) squared Euclidean distance represents placement objective function

 n
 1 2 2
 L(P) = cij ((xi − x j ) + (yi − y j ) )

##### ∑

###### 2
 i, j=1

 where n is the total number of cells, and c(i,j) is the connection cost between cells i and j.

 • Only two-point-connections



###### • Minimize objective function by equating its derivative to zero which reduces to solving a system of linear equations


-----

###### • Similar to Least-Mean-Square Method (root mean square)

 2
 • Build error function with analytic form: E(a,b) = (a ⋅ x + b − y ) i i
### ∑


![](VLSI-design-chap4.pdf-29-0.png)

-----

###### • Each dimension can be considered independently:
 n n
 2
 L (P) = c(i, j()x − x ) L (P) = c(i, j() y − y ) x i j y i j
### ∑ ∑
###### i =,1 j =1 i =,1 j =1

 • Convex quadratic optimization problem: any local minimum solution is also a global minimum


###### 2



###### • Optimal x- and y-coordinates can be found by setting the partial derivatives of Lx(P) and Ly(P) to zero 


-----

###### • Each dimension can be considered independently:
 n n
 2
 L (P) = c(i, j()x − x ) L (P) = c(i, j() y − y ) x i j y i j
### ∑ ∑
###### i =,1 j =1 i =,1 j =1

 ∂L (P)
 ∂L (P) y x = AX − b = 0 = AY − b = 0 x y ∂X ∂Y


###### 2



###### • where A is a matrix with A[i][j] = -c(i,j) when i ≠ j, and A[i][i] = the sum of incident connection weights of cell i.

 • X is a vector of all the x-coordinates of the non-fixed cells, and bx is a vector with bx[i] = the sum of x-coordinates of all fixed cells attached to i.

 • Y is a vector of all the y-coordinates of the non-fixed cells, and by is a vector with b [i] = the sum of y coordinates of all fixed cells attached to i


-----

###### • Each dimension can be considered independently:
 n n
 2
 L (P) = c(i, j()x − x ) L (P) = c(i, j() y − y ) x i j y i j
### ∑ ∑
###### i =,1 j =1 i =,1 j =1

 ∂L (P)
 ∂L (P) y x = AX − b = 0 = AY − b = 0 x y ∂X ∂Y


###### 2



###### • System of linear equations for which iterative numerical methods can be used to find a solution


-----

###### • Mechanical analogy: mass-spring system

 − Squared Euclidean distance is proportional to the energy of a spring between these points


###### − Quadratic objective function represents total energy of the spring system; for each movable object, the x (y) partial derivative represents the total force acting on that object

 − Setting the forces of the nets to zero, an equilibrium state is mathematically modeled that is characterized by zero forces acting on each movable object


###### − At the end, all springs are in a force equilibrium with a minimal total spring energy; this equilibrium represents the minimal sum of squared wirelength

 → Result: many cell overlaps


-----

###### • Second stage of quadratic placers: cells are spread out to remove overlaps

 • Methods:


###### − Adding fake nets that pull cells away from dense regions toward anchors

 − Geometric sorting and scaling


###### − Repulsion forces, etc.


![](VLSI-design-chap4.pdf-34-0.png)

-----

###### • Advantages:

 − Captures the placement problem concisely in mathematical terms


###### − Leverages efficient algorithms from numerical analysis and available software

 − Can be applied to large circuits without netlist clustering (flat)


###### − Stability: small changes in the input do not lead to large changes in the output



###### • Disadvantages:

 − Connections to fixed objects are necessary: I/O pads, pins of fixed macros, etc.


-----

###### • Cells and wires are modeled using the mechanical analogy of a mass-spring system, i.e., masses connected to Hooke’s-Law springs

 • Attraction force between cells is directly proportional to their distance



###### • Cells will eventually settle in a force equilibrium → minimized wirelength 


-----

###### • Given two connected cells a and b, the attraction force      exerted on F a by b is
 ab
 F = c(a, b) ⋅ (b − a) ab


###### where

 − c(a,b) is the connection weight (priority) between cells a and b, and


###### − (b − a) is the vector difference of the positions of a and b in the Euclidean plane



###### • The sum of forces exerted on a cell i connected to other cells 1… j is

 F = F i ij

### ∑

###### c(i, j)≠0



###### • Zero-force target (ZFT): position that minimizes this sum of forces 


-----

###### Zero-Force-Target (ZFT) position of cell i


###### a


###### c


-----

###### Basic force-directed placement



###### • Iteratively moves all cells to their respective ZFT positions

 • x- and y-direction forces are set to zero:


###### 0 0 0 0 c(i, j) ⋅ (x − x ) = 0 c(i, j) ⋅ ( y − y ) = 0 j i j i
## ∑ ∑
###### c(i, j)≠0 c(i, j)≠0

 • Rearranging the variables to solve for xi0 and yi0 yields


-----

###### Example: ZFT position


###### Given:
 − Circuit with NAND gate 1 and four I/O pads on a 3 x 3 grid


###### − Pad positions: In1 (2,2),  In2 (0,2),  In3 (0,0),  Out (2,0)


###### − Weighted connections: c(a,In1) = 8,  c(a,In2) = 10,  c(a,In3) = 2,  c(a,Out) = 2

 Task: find the ZFT position of cell a


###### 2

 1

|In2|Col2|In1|
|---|---|---|
||||
|In3||Out|


###### 0 1 2


-----

###### Example: ZFT position


###### Given:
 − Circuit with NAND gate 1 and four I/O pads on a 3 x 3 grid


###### − Pad positions: In1 (2,2),  In2 (0,2),  In3 (0,0),  Out (2,0)

 Solution:


0

###### c(a, j) ⋅ x j
 ∑
 xa0 = c(i, j)≠0 = c(a, In)1 ⋅ xIn1 + c(a, In)2 ⋅ xIn2 + c(a, In)3 ⋅ xIn3 + c(a,Out) ⋅ xOut = 8 ⋅ 2 +10 ⋅ 0 + 2 ⋅ 0 + 2 ⋅ 2 = 20 ≈ 9.0
 c(a, j) c(a, In)1 + c(a, In)2 + c(a, In)3 + c(a,Out) 8 +10 + 2 + 2 22
 ∑

_c(i,_ _j)≠0_

###### ∑c(a, j) ⋅ y 0j
 ya0 = c(i, j)≠0 = c(a, In)1 ⋅ yIn1 + c(a, In)2 ⋅ yIn2 + c(a, In)3 ⋅ yIn3 + c(a,Out) ⋅ yOut = 8 ⋅ 2 +10 ⋅ 2 + 2 ⋅ 0 + 2 ⋅ 0 = 36 ≈ 6.1
 c(a, j) c(a, In)1 + c(a, In)2 + c(a, In)3 + c(a,Out) 8 +10 + 2 + 2 22
 ∑

_c(i,_ _j)≠0_


###### ZFT position of cell a is (1,2)


-----

###### Example: ZFT position


###### Given:
 − Circuit with NAND gate 1 and four I/O pads on a 3 x 3 grid


###### − Pad positions: In1 (2,2),  In2 (0,2),  In3 (0,0),  Out (2,0)

 Solution:


###### 2

 1


###### ZFT position of cell a is (1,2)

|In2|a|Col3|In1|
|---|---|---|---|
|||||
|In3|||Out|


###### 0 1 2


-----

###### Input: set of all cells V Output: placement P

 P = PLACE(V) // arbitrary initial placement


###### loc = LOCATIONS(P) // set coordinates for each cell in P
 foreach (cell c ∈ V)


###### status[c] = UNMOVED


###### while (ALL_MOVED(V) || !STOP()) // continue until all cells have been //  moved or some stopping //  criterion is reached
 c = MAX_DEGREE(V,status) // unmoved cell that has largest //  number of connections


###### ZFT_pos = ZFT_POSITION(c) // ZFT position of c
 if (loc[ZFT_pos] == Ø) // if position is unoccupied,


###### loc[ZFT_pos] = c //  move c to its ZFT position


###### else
 RELOCATE(c,loc) // use methods discussed next


###### status[c] = MOVED // mark c as moved


-----

###### Finding a valid location for a cell with an occupied ZFT position

 (p: incoming cell, q: cell in p‘s ZFT position)



###### • If possible, move p to a cell position close to q.

 • Chain move: cell p is moved to cells q’s location.


###### − Cell q, in turn, is shifted to the next position. If a cell r is occupying this space, cell r is shifted to the next position.


###### − This continues until all affected cells are placed.

 • Compute the cost difference if p and q were to be swapped. If the total cost reduces, i.e., the weighted connection length L(P) is smaller, then swap p and q.


-----

###### Given:

 Nets Weight


###### N1 = (b1, b3) c(N1) = 2
 N2 = (b2, b3) c(N2) = 1

|b 1|b 2|b 3|
|---|---|---|
||||


###### 0 1 2


-----

###### Given:

 Nets Weight


###### N1 = (b1, b3) c(N1) = 2
 N2 = (b2, b3) c(N2) = 1

 ZFT position of cell p

0

###### c(b, j) ⋅ x

3 _j_

###### ∑
 x0 = c(b3, j)≠0 = 2 ⋅ 0 +1

_b3_ 2 +1
###### c(b, j)

3

###### ∑

_c(b3_, _j)≠0_

|b 1|b 2|b 3|
|---|---|---|
||||


###### 0 1 2

 ) / placement

 b33 b22 b11

 ⇒ No swapping of b3 and b1


-----

###### Given:

 Nets Weight


###### N1 = (b1, b3) c(N1) = 2
 N2 = (b2, b3) c(N2) = 1

|b 1|b 2|b 3|
|---|---|---|
||||


###### 0 1 2

 ) / placement

 b33 b22 b1

 → No swapping of b3 and

 b1 b3 b

 → Swapping of b2 and b3


-----

###### • Advantages:

 − Conceptually simple, easy to implement


###### − Primarily intended for global placement, but can also be adapted to detailed placement



###### • Disadvantages:

 − Does not scale to large placement instances


###### − Is not very effective in spreading cells in densest regions

 − Poor trade-off between solution quality and runtime



###### • In practice, FDP is extended by specialized techniques for cell spreading

 − This facilitates scalability and makes FDP competitive


-----

###### Cost

 • Analogous to the physical annealing process


###### Time


###### − Melt metal and then slowly cool it
 − Result: energy-minimal crystal structure 



###### • Modification of an initial configuration (placement) by moving/exchanging of randomly selected cells
 − Accept the new placement if it improves the objective function


###### − If no improvement: Move/exchange is accepted with temperature-dependent (i.e., decreasing) probability


-----

###### Input: set of all cells V
 Output: placement P


###### T = T0 // set initial temperature
 P = PLACE(V) // arbitrary initial placement


###### while (T > Tmin)
 while (!STOP()) // not yet in equilibrium at T


###### new_P = PERTURB(P) Δcost = COST(new_P) – COST(P) if (Δcost < 0) // cost improvement
 P = new_P // accept new placement


###### else // no cost improvement
 r = RANDOM(0,1) // random number [0,1)


###### if (r < e [-Δ][cost][/][T]) // probabilistically accept


###### P = new_P
 T = α ∙ T // reduce T, 0 < α < 1


-----

###### • Advantages:
 − Can find global optimum (given sufficient time)


###### − Well-suited for detailed placement



###### • Disadvantages:
 − Very slow


###### − To achieve high-quality implementation, laborious parameter tuning is necessary
 − Randomized, chaotic algorithms - small changes in the input lead to large changes in the output



###### • Practical applications of SA:
 − Very small placement instances with complicated constraints


###### − Detailed placement, where SA can be applied in small windows (not common anymore)
 − FPGA layout, where complicated constraints are becoming a norm


-----

###### Cost

 • Analogous to the physical annealing process


###### Time


###### − Melt metal and then slowly cool it
 − Result: energy-minimal crystal structure 



###### • Modification of an initial configuration (placement) by moving/exchanging of randomly selected cells
 − Accept the new placement if it improves the objective function


###### − If no improvement: Move/exchange is accepted with temperature-dependent (i.e., decreasing) probability


-----

###### • Predominantly analytic algorithms

 • Solve two challenges: interconnect minimization and cell overlap removal (spreading)



###### • Two families:

 Non-convex Quadratic placers optimization placers


![](VLSI-design-chap4.pdf-53-0.png)

-----

![](VLSI-design-chap4.pdf-54-1.png)

###### Non-convex Quadratic placers optimization placers

 • Solve large, sparse systems of linear equations (formulated using force-directed placement) by the Conjugate Gradient algorithm


![](VLSI-design-chap4.pdf-54-0.png)


###### • Perform cell spreading by adding fake nets that pull cells away from dense regions toward carefully placed anchors


-----

![](VLSI-design-chap4.pdf-55-1.png)

###### Non-convex Quadratic placers optimization placers

 • Model interconnect by sophisticated differentiable functions, e.g., log-sum-exp is the popular choice


![](VLSI-design-chap4.pdf-55-0.png)


###### • Model cell overlap and fixed obstacles by additional (non-convex) functional terms

 • Optimize interconnect by the non-linear Conjugate Gradient algorithm



###### • Sophisticated, slow algorithms

 • All leading placers in this category use netlist clustering to improve computational scalability (this further complicates the implementation)


-----

![](VLSI-design-chap4.pdf-56-1.png)

###### Quadratic Placement


![](VLSI-design-chap4.pdf-56-0.png)

###### Non-convex optimization placers


###### Pros and cons:

 • Quadratic placers are simpler and faster, easier to parallelize



###### • Non-convex optimizers tend to produce better solutions

 • As of 2011, quadratic placers are catching up in solution quality while running 5-6 times faster [[1]]


-----

###### 4.1 Introduction

 4.2 Optimization Objectives


###### 4.3 Global Placement 4.3.1 Min-Cut Placement 4.3.2 Analytic Placement 4.3.3 Simulated Annealing
 4.3.4 Modern Placement Algorithms


###### 4.4 Legalization and Detailed Placement


-----

###### • Global placement must be legalized

 − Cell locations typically do not align with power rails


###### − Small cell overlaps due to incremental changes, such as cell resizing or buffer insertion

 • Legalization seeks to find legal, non-overlapping placements for all placeable modules



###### • Legalization can be improved by detailed placement techniques, such as

 − Swapping neighboring cells to reduce wirelength


###### − Sliding cells to unused space

 • Software implementations of legalization and detailed placement are often bundled


-----

###### Legal positions of standard cells between VDD and GND rails


![](VLSI-design-chap4.pdf-59-0.png)

###### Power Rail Standard Cell Row


###### GND

|Power Rail Standard Cell Row|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|VDD||||||||||||
|||||||||||||
|||||||||||||
|GND||||||||||||
|||||||||||||
|||||||||||||
||||||||||||GND|


![](VLSI-design-chap4.pdf-59-0.png)

###### Power Rail Standard Cell Row


###### INV NAND NOR


![](VLSI-design-chap4.pdf-59-0.png)

###### NOR


![](VLSI-design-chap4.pdf-59-1.png)

###### INV


![](VLSI-design-chap4.pdf-59-2.png)

###### NAND


-----

###### • Row-based standard-cell placement
 − Cell heights are typically fixed, to fit in rows (but some cells may have double and quadruple heights)


###### − Legal cell sites facilitate the alignment of routing tracks, connection to power and ground rails



###### • Wirelength as a key metric of interconnect
 − Bounding box half-perimeter (HPWL)


###### − Cliques and stars
 − RMSTs and RSMTs



###### • Objectives: wirelength, routing congestion, circuit delay
 − Algorithm development is usually driven by wirelength


###### − The basic framework is implemented, evaluated and made competitive on standard benchmarks
 − Additional objectives are added to an operational framework


-----

###### • Combinatorial optimization techniques: min-cut and simulated annealing 
 − Can perform both global and detailed placement


###### − Reasonably good at small to medium scales
 − SA is very slow, but can handle a greater variety of constraints


###### − Randomized and chaotic algorithms – small changes at the input can lead to large changes at the output



###### • Analytic techniques: force-directed placement and non-convex optimization 
 − Primarily used for global placement


###### − Unrivaled for large netlists in speed and solution quality 
 − Capture the placement problem by mathematical optimization


###### − Use efficient numerical analysis algorithms
 − Ensure stability: small changes at the input can cause only small changes at the output


###### − Example: a modern, competitive analytic global placer takes 20mins for global placement of a netlist with 2.1M cells (single thread, 3.2GHz Intel CPU) [[1]]


-----

###### • Legalization ensures that design rules & constraints are satisfied 
 − All cells are in rows


###### − Cells align with routing tracks
 − Cells connect to power & ground rails


###### − Additional constraints are often considered, e.g., maximum cell density



###### • Detailed placement reduces interconnect, while preserving legality 
 − Swapping neighboring cells, rotating groups of three


###### − Optimal branch-and-bound on small groups of cells
 − Sliding cells along their rows


###### − Other local changes

 • Extensions to optimize routed wirelength, routing congestion and circuit timing



###### • Relatively straightforward algorithms, but high-quality, fast implementation is important

 • Most relevant after analytic global placement, but are also used after min-cut placement



###### • Rule of thumb: 50% runtime is spent in global placement, 50% in detailed placement [1]


-----

