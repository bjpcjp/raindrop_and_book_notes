![](VLSI-design-chap7.pdf-0-0.png)

-----

##### 7.1 Introduction to Area Routing

 7.2 Net Ordering in Area Routing


##### 7.3 Non-Manhattan Routing

###### 7.3.1 Octilinear Steiner Trees

 7.3.2 Octilinear Maze Search


##### 7.4 Basic Concepts in Clock Networks

###### 7.4.1 Terminology


###### 7.4.2 Problem Formulations for Clock-Tree Routing


##### 7.5 Modern Clock Tree Synthesis

###### 7.5.1 Constructing Trees with Zero Global Skew


###### 7.5.2 Clock Tree Buffering in the Presence of Variation


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

-----

![](VLSI-design-chap7.pdf-4-0.png)


##### • Area routing directly constructs metal routes for signal connections (no global and detailed routing, Secs. 7.1-7.2)

 • Non-Manhattan routing is presented in Sec. 7.3

 • Clock signals and other nets that require special treatment are discussed in Secs. 7.4-7.5


-----

##### • The goal of area routing is to route all nets in the design

###### − without global routing


###### − within the given layout space

 − while meeting all geometric and electrical design rules



##### • Area routing performs the following optimizations

###### − minimizing the total routed length and number of vias of all nets


###### − minimizing the total area of wiring and the number of routing layers

 − minimizing the circuit delay and ensuring an even wire density


###### − avoiding harmful capacitive coupling between neighboring routes



##### • Subject to

###### − technology constraints (number of routing layers, minimal wire width, etc.)


###### − electrical constraints (signal integrity, coupling, etc.)

 − geometry constraints (preferred routing directions, wire pitch, etc.)


-----

##### Minimal wirelength:


##### Alternative routing path:


-----

###### Distance metric between two points P1 (x1,y1) and P2 (x2,y2)

|Col1|P 1|Col3|Col4|Col5|d M|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||d E||||
|||||||||
|||d M||||P 2||


![](VLSI-design-chap7.pdf-7-0.png)

###### P1 dM

 dE

 dM P2


-----

##### • Multiple Manhattan shortest paths between two points


-----

##### • Multiple Manhattan shortest paths between two points

###### m = 210  

 ∆y


###### ∆x

##### With no obstacles, the number of Manhattan shortest paths in an Δx × Δy region is


#  Δx + Δy   Δx + Δy  (Δx + Δy)!
 m = = =
 [] [] [] []
 Δx Δy Δx!Δy!
    


-----

##### • Two pairs of points may admit non-intersecting Manhattan shortest paths, while their Euclidean shortest paths intersect (but not vice versa).


-----

##### • If all pairs of Manhattan shortest paths between two pairs of points intersect, then so do Euclidean shortest paths.


-----

##### • The Manhattan distance dM is (slightly) larger than the Euclidean distance dE:

 1.41  worst case: a square where  Δx = Δy


### d
M
### d

E


### =


##### 1.27  on average, without obstacles

 1.15  on average, with obstacles


-----

##### 7.1 Introduction to Area Routing

 7.2 Net Ordering in Area Routing


##### 7.3 Non-Manhattan Routing

###### 7.3.1 Octilinear Steiner Trees

 7.3.2 Octilinear Maze Search


##### 7.4 Basic Concepts in Clock Networks

###### 7.4.1 Terminology


###### 7.4.2 Problem Formulations for Clock-Tree Routing


##### 7.5 Modern Clock Tree Synthesis

###### 7.5.1 Constructing Trees with Zero Global Skew


###### 7.5.2 Clock Tree Buffering in the Presence of Variation


-----

##### Effect of net ordering on routability


##### A´ B´

 Optimal routing of net A

|Col1|Col2|Col3|Col4|A|Col6|Col7|
|---|---|---|---|---|---|---|
|||||B|||
||||||||
||||||||
|||A´||||B´|
||||||||
||||||||

|Col1|Col2|Col3|Col4|A|Col6|Col7|
|---|---|---|---|---|---|---|
|||||B|||
||||||||
||||||||
|||A´||||B´|
||||||||
||||||||

|Col1|Col2|Col3|Col4|A|Col6|Col7|
|---|---|---|---|---|---|---|
|||||B|||
||||||||
||||||||
|||A´||||B´|
||||||||
||||||||


##### Optimal routing of net B


##### Nets A and B can be routed only with detours


-----

##### Effect of net ordering on total wirelength

|A|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|||||B|||
|||B´|||||
||||||||
||||||||
||||||||
|||||A´|||

|A|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|||||B|||
|||B´|||||
||||||||
||||||||
||||||||
|||||A´|||


##### Routing net A first


##### Routing net B first


-----

##### • For n nets, there are n! possible net orderings

 ⇒ Constructive heuristics are used


-----

##### • Rule 1: For two nets i and j, if aspect ratio (i ) > aspect ratio (j ), then i is routed before j

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||A||||
|B´|||||||
||||A´|||B|
||||||||
||||||||
||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||A||||
|B´|||||||
||||A´|||B|
||||||||
||||||||
||||||||


##### Net A has a higher aspect ratio of its bounding box; routing A first results in shorter total wirlength


##### Routing net B first results in longer total wirelength


-----

##### • Rule 2: For two nets i and j, if the pins of i are contained within MBB(j ), then i is routed before j

###### Constraint Graph Net Ordering

|Col1|Col2|Col3|Col4|Col5|C|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||A||||||
||B||||||||
||||D|||D′|||
||||||||||
|||C´||||B′|||
||||||||||

|Col1|Col2|Col3|Col4|Col5|C|Col7|Col8|
|---|---|---|---|---|---|---|---|
||||A|||||
||B|||||||
||||D|||D′||
|||||||||
|||C´||||B′||
|||||||||


###### A′


###### B


###### A

 C


###### D


###### Ordering D-A-C-B or  D-C-B-A (not D-B-A-C)


###### A′


-----

##### • Rule 3: Let Π(net) be the number of pins within MBB(net) for net net. For two nets i and j, if Π(i ) < Π(j ), then i is routed before j.

###### - For each net, consider the pins of other nets within its bounding box


###### - The net with the smallest number of such pins is routed first

 - Ties are broken based on the number of pins that are contained within the bounding box and on its edge 


##### A B

 D

 E´


##### D´

 E

 C´


##### A B

 D

 E´


##### D´

 E

 C´

|Col1|Pins Inside (Edge)|π (net)|
|---|---|---|
|MBB (A) B C D E|D (B,C,D) - (A,C,D) - (A) - (-) - (A,C)|3 3 1 0 2|

|Col1|Col2|Col3|Col4|Col5|C|Col7|Col8|
|---|---|---|---|---|---|---|---|
||||D||||D´|
|||||||||
||||||A´||E|
|||||||||
||||||||C´|
|||E´||||||

|Col1|Col2|Col3|Col4|C|Col6|Col7|
|---|---|---|---|---|---|---|
|||D||||D´|
||||||||
|||||A´||E|
||||||||
|||||||C´|
||E´||||||


##### B´


##### B´


-----

##### 7.1 Introduction to Area Routing

 7.2 Net Ordering in Area Routing


##### 7.3 Non-Manhattan Routing

###### 7.3.1 Octilinear Steiner Trees

 7.3.2 Octilinear Maze Search


##### 7.4 Basic Concepts in Clock Networks

###### 7.4.1 Terminology


###### 7.4.2 Problem Formulations for Clock-Tree Routing


##### 7.5 Modern Clock Tree Synthesis

###### 7.5.1 Constructing Trees with Zero Global Skew


###### 7.5.2 Clock Tree Buffering in the Presence of Variation


-----

##### • Allow 45- or 60-degree segments in addition to horizontal and vertical segments

 • λ-geometry, where λ represents the number of possible routing directions and the angles π / λ at which they can be oriented


###### − λ = 2 (90 degrees): Manhattan routing (four routing directions)

 − λ = 3 (60 degrees): Y-routing (six routing directions)


###### − λ = 4 (45 degrees): X-routing (eight routing directions)

##### • Non-Manhattan routing is primarily employed on printed circuit boards (PCBs)


![](VLSI-design-chap7.pdf-21-0.png)

-----

##### • Route planning using octilinear Steiner minimum trees (OSMT)

 • Generalize rectilinear Steiner trees by allowing segments that extend in eight directions



##### • More freedom when placing Steiner points

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||||||||||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||


![](VLSI-design-chap7.pdf-22-0.png)

###### 3
 2

 5 4
 6 7

 8 9

 10
 12 11


-----

##### Octilinear Steiner Tree Algorithm

 Input: set of all pins P and their coordinates


##### Output: heuristic octilinear minimum Steiner tree OST

 OST = Ø


##### T = set of all three-pin nets of P found by Delaunay triangulation

 sortedT = SORT(T,minimum octilinear distance)


##### for (i = 1 to |sortedT |)

 subT = ROUTE(sortedT [i ] ) // route minimum tree over subT


##### ADD(OST,subT ) // add route to existing tree

 IMPROVE(OST,subT ) // locally improve OST based on subT


-----

###### (1) Triangulate

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||


![](VLSI-design-chap7.pdf-24-0.png)

###### 3
 2

 5 4
 6 7

 8 9

 10
 12 11


-----

###### (1) Triangulate (2) Add route to existing tree

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||


-----

###### (1) Triangulate (2) Add route to existing tree


###### (3) Locally improve OST

 1
 3
 2

 5 4
 6 7

 8

 10
 11

 cost = 6 cost ≈ 5.7

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||


-----

###### Final OST after merging all subtrees


###### (3) Locally improve OST

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||1|||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||

|Col1|Col2|1|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||
||||||||||||3||||||
|2|||||||||||||||||
||||||||||||||||||
|||||||||||||||5|||
|||||4|||||||||||||
||||||||||||||||||
|||||||||||7|||||||
||6||||||||||||||||
||||||||||||||||||
|||||||||||||8||||9|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|||||||1|0||||||||||
||||||||||||||||||
||1|1||||||||||||1|2||
||||||||||||||||||


![](VLSI-design-chap7.pdf-27-0.png)

###### 3
 2

 5 4
 6 7

 8 9

 10
 12 11


-----

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||1|1|1||
||||1|S|1||
||||1|1|1||
||||||||
|||T|||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|||2|2|2|2|2|
|||2|1|1|1|2|
|||2|1|S|1|2|
|||2|1|1|1|2|
|||2|2|2|2|2|
|||T|||||

|Col1|3|3|3|3|3|3|
|---|---|---|---|---|---|---|
||3|2|2|2|2|2|
||3|2|1|1|1|2|
||3|2|1|S|1|2|
||3|2|1|1|1|2|
||3|2|2|2|2|2|
||3|T|3|3|3|3|


###### Expansion (1) Expansion (2)


###### Backtracing


-----

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
|||||S|||
||||||||
||||||||
|||T|||||


-----

##### 7.1 Introduction to Area Routing

 7.2 Net Ordering in Area Routing


##### 7.3 Non-Manhattan Routing

###### 7.3.1 Octilinear Steiner Trees

 7.3.2 Octilinear Maze Search


##### 7.4 Basic Concepts in Clock Networks

###### 7.4.1 Terminology


###### 7.4.2 Problem Formulations for Clock-Tree Routing


##### 7.5 Modern Clock Tree Synthesis

###### 7.5.1 Constructing Trees with Zero Global Skew


###### 7.5.2 Clock Tree Buffering in the Presence of Variation


-----

##### • A clock routing instance (clock net) is represented by n+1 terminals, where s0 is designated as the source, and S = {s1,s2, …,sn} is designated as sinks

###### − Let si, 0 ≤ i ≤ n, denote both a terminal and its location



##### • A clock routing solution consists of a set of wire segments that connect all terminals of the clock net, so that a signal generated at the source propagates to all of the sinks

###### − Two aspects of clock routing solution: topology and geometric embedding 



##### • The clock-tree topology (clock tree) is a rooted binary tree G with n leaves corresponding to the set of sinks

###### − Internal nodes = Steiner points


-----

##### Clock routing problem instance


##### Connection topology


##### Embedding

|Col1|Col2|Col3|Col4|Col5|s 1|Col7|
|---|---|---|---|---|---|---|
|||||||s 2|
||||s 0||||
||s 3|||||s 5|
||||||||
|||s 4||||s 6|
||||||||

|Col1|Col2|Col3|Col4|Col5|s 1|Col7|
|---|---|---|---|---|---|---|
||||||u 1|s 2|
||||s 0||||
||s 3|||||s 5|
|||u 3|u 2|||u 4|
|||s 4||||s 6|
||||||||


![](VLSI-design-chap7.pdf-32-0.png)

#### s
1

#### s
2

#### s
0

#### s s
3 5

#### s4 s6


![](VLSI-design-chap7.pdf-32-1.png)

#### s
1


![](VLSI-design-chap7.pdf-32-2.png)

#### u
4


![](VLSI-design-chap7.pdf-32-3.png)

#### s
3


![](VLSI-design-chap7.pdf-32-4.png)

#### s
5


![](VLSI-design-chap7.pdf-32-5.png)

#### u
1


-----

##### • Clock skew: (maximum) difference in clock signal arrival times between sinks


# skew(T ) = max | t(s, s ) − t(s, s |)
###### 0 i 0 j s,s ∈S

_i_ _j_



##### • Local skew: maximum difference in arrival times of the clock signal at the clock pins of two or more related sinks

###### − Sinks within distance d > 0


###### − Flip-flops or latches connected by a directed signal path



##### • Global skew: maximum difference in arrival times of the clock signal at the clock pins of any two (related or unrelated) sinks

###### − Difference between shortest and longest source-sink path delays in the clock distribution network


###### − The term “skew” typically refers to “global skew” 


-----

##### • Zero skew: zero-skew tree (ZST)

###### − ZST problem



##### • Bounded skew: true ZST may not be necessary in practice

###### − Signoff timing analysis is sufficient with a non-zero skew bound


###### − In addition to final (signoff) timing, this relaxation can be useful with intermediate delay models when it facilitates reductions in the length of the tree

 − Bounded-Skew Tree (BST) problem



##### • Useful skew: correct chip timing only requires control of the local skews between pairs of interconnected flip-flops or latches

###### − Useful skew formulation is based on analysis of local skew constraints


-----

##### 7.1 Introduction to Area Routing

 7.2 Net Ordering in Area Routing


##### 7.3 Non-Manhattan Routing

###### 7.3.1 Octilinear Steiner Trees

 7.3.2 Octilinear Maze Search


##### 7.4 Basic Concepts in Clock Networks

###### 7.4.1 Terminology


###### 7.4.2 Problem Formulations for Clock-Tree Routing


##### 7.5 Modern Clock Tree Synthesis

###### 7.5.1 Constructing Trees with Zero Global Skew


###### 7.5.2 Clock Tree Buffering in the Presence of Variation


-----

##### • A clock tree should have low skew, while delivering the same signal to every sequential gate

 • Clock tree synthesis is performed in two steps:


##### (1) Initial tree construction (Sec. 7.5.1) with one of these scenarios

###### − Construct a regular clock tree, largely independent of sink locations 


###### − Simultaneously determine a topology and an embedding


###### − Construct only the embedding, given a clock-tree topology as input

##### (2) Clock buffer insertion and several subsequent skew optimizations (Sec. 7.5.2)


-----

##### H-tree


![](VLSI-design-chap7.pdf-37-0.png)


##### • Exact zero skew due to the symmetry of the H-tree

 • Used for top-level clock distribution, not for the entire clock tree


###### − Blockages can spoil the symmetry of an H-tree

 − Non-uniform sink locations and varying sink capacitances also complicate the design of H-trees


-----

##### Method of Means and Medians (MMM)



##### • Can deal with arbitrary locations of clock sinks

 • Basic idea:


###### − Recursively partition the set of terminals into two subsets of equal size (median)

 − Connect the center of gravity (COG) of the set to the centers of gravity of the two subsets (the mean)


-----

##### Method of Means and Medians (MMM)


###### Find the center of gravity 


###### Partition S by the median


###### Find the center of gravity for the left and right subsets of S


###### Connect the center of gravity of S with the centers of gravity of the left and right subsets


###### Final result after recursively performing MMM on each subset


-----

##### Method of Means and Medians (MMM)


##### Input: set of sinks S, empty tree T

 Output: clock tree T


##### if (|S| ≤ 1)

 return


##### (x0,y0) = (xc(S),yc(S)) // center of mass for S
 (SA,SB) = PARTITION(S) // median to determine SA and SB


##### (xA,yA) = (xc(SA),yc(SA)) // center of mass for SA
 (xB,yB) = (xc(SB),yc(SB)) // center of mass for SB
 ROUTE(T,x0,y0,xA,yA) // connect center of mass of S to


##### ROUTE(T,x0,y0,xB,yB) //  center of mass of SA and SB
 BASIC_MMM(SA,T) // recursively route SA
 BASIC_MMM(SB,T) // recursively route SB


-----

##### Recursive Geometric Matching (RGM)



##### • RGM proceeds in a bottom-up fashion

###### − Compare to MMM, which is a top-down algorithm



##### • Basic idea:

###### − Recursively determine a minimum-cost geometric matching of n sinks


###### − Find a set of n / 2 line segments that match n endpoints and minimize total length (subject to the matching constraint)

 − After each matching step, a balance or tapping point is found on each matching segment to preserve zero skew to the associated sinks


###### − The set of n / 2 tapping points then forms the input to the next matching step


-----

##### Recursive Geometric Matching (RGM)


###### Set of n sinks S


###### Min-cost geometric matching


###### Find balance or tapping points (point that achieves zero skew in the subtree, not always midpoint)


###### Min-cost geometric matching


###### Final result after recursively performing RGM on each subset


-----

##### Recursive Geometric Matching (RGM)


##### Input: set of sinks S, empty tree T Output: clock tree T

 if (|S| ≤ 1)


##### return


##### M = min-cost geometric matching over S S’ = Ø foreach (<Pi,Pj > ∈ M)
 TPi = subtree of T rooted at Pi TPj = subtree of T rooted at Pj tp = tapping point on (Pi,Pj) // point that minimizes the skew of //  the tree Ttp = TPi U TPj U (Pi,Pj)
 ADD(S’,tp) // add tp to S’
 ADD(T,(Pi,Pj)) // add matching segment (Pi,Pj) to T


##### if (|S| % 2 == 1) // if |S| is odd, add unmatched node
 ADD(S’, unmatched node)


-----

##### Exact Zero Skew



##### • Adopts a bottom-up process of matching subtree roots and merging the corresponding subtrees, similar to RGM

 • Two important improvements:


###### − Finds exact zero-skew tapping points with respect to the Elmore delay model rather than the linear delay model

 − Maintains exact delay balance even when two subtrees with very different source-sink delays are matched (by wire elongation)


-----

##### Exact Zero Skew


###### Tapping point tp

 z 1 – z
 w1 w2
 s1 s2

 Subtree Ts1 Subtree Ts2


-----

##### Deferred-Merge Embedding (DME)



##### • Defers the choice of merging (tapping) points for subtrees of the clock tree

 • Needs a tree topology as input



##### • Weakness in earlier algorithms:

###### − Determine locations of internal nodes of the clock tree too early; once a centroid is found, it is never changed



##### • Basic idea:

###### − Two sinks in general position will have an infinite number of midpoints, creating a tilted line segment – Manhattan arc


###### − Manhattan arc: same minimum wirelength and exact zero skew 

 − Selection of embedding points for internal nodes on Manhattan arc will be delayed for as long as possible


-----

##### Deferred-Merge Embedding (DME)


###### Euclidean midpoint

 s2

 s1

 Locus of all Manhattan midpoints is a Manhattan arc in the  Manhattan geometry


###### Euclidean midpoint

 s1
 s1 s2

 s2

 Sinks are aligned, hence, Manhattan arc has zero length

|s s 1 2|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|s 1|||||s 2|
|||||||
|||||||

|midpoint|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|s 1 s 2|||||||
|||||s 1|||
||||||||
||||||||
|||||s 2|||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|||||||s 2|
||||||||
||||||||
|s 1|||||||
||||||||


![](VLSI-design-chap7.pdf-47-0.png)

###### s1 s2


-----

##### Deferred-Merge Embedding (DME)



##### • Embeds internal nodes of the given topology G via a two-phase process

 • First phase is bottom-up


###### − Determines all possible locations of internal nodes of G consistent with a minimum-cost ZST T

 − Output: “tree of line segments”, with each line segment being the locus of possible placements of an internal node of T



##### • Second phase is top-down

###### − Chooses the exact locations of all internal nodes in T


###### − Output: fully embedded, minimum-cost ZST with topology G


-----

##### Deferred-Merge Embedding (DME) Tilted Rectangular Region (TRR)


###### for the Manhattan arc of s1 and s2 with a radius of two units


###### Core
 Radius

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||s 1||||||
|||||||||
|||||||||
||||||s 2|||
|||||||||
|||||||||

|with|Col2|Col3|Col4|Col5|Col6|a radius of two|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
|||s 1|||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||s 2||||
||||||||||
||||||||||


![](VLSI-design-chap7.pdf-49-0.png)

###### s1

 s2


-----

##### Deferred-Merge Embedding (DME) Merging segment for node u3
###### (the parent of nodes u1 and u2) is the locus of feasible locations of u3 with zero skew and minimum wirelength

 ms(u1) ms(u2)


![](VLSI-design-chap7.pdf-50-3.png)

###### u3


###### trr(u1)

 |eu1 |


###### trr(u2)

 |eu2 |

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||
||||||||||||||||||
||||s 1||||||||s 3||||||
||||||||||||||||||
|||||||||||||s 4|||||
||||||||||||||||||
||||||||||||||||||
|||||||s 2|||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||


![](VLSI-design-chap7.pdf-50-0.png)

###### s1 s3
 s4

 s2


![](VLSI-design-chap7.pdf-50-1.png)

###### s1


![](VLSI-design-chap7.pdf-50-2.png)

###### s2


![](VLSI-design-chap7.pdf-50-3.png)

###### s4


###### ms(u3)


![](VLSI-design-chap7.pdf-50-0.png)

###### u1


![](VLSI-design-chap7.pdf-50-1.png)

###### s3


-----

##### Deferred-Merge Embedding (DME)


##### Build Tree of Segments Algorithm (DME Bottom-Up Phase)

|Col1|Col2|Col3|Col4|s|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||||1|||||s|||
||||||||||8|||
|||||||||||||
||s 2||||||||||s 7|
|||||||||||||
|||||||||||s||
||||||||||||6|
||s||||||||||s 5|
||3||s|4|||s|||||
||||||||0|||||


###### s5


###### s7

|Col1|Col2|Col3|Col4|s|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||1||||s|||
|||||||||||8||
|||||||||||s|7|
||s|||||||||||
||2|||||||||||
|||||||||||s 6||
||||||||||||s 5|
|s 3||||||||||||
||||s 4|||||||||
||||||||s|0||||

|Col1|Col2|Col3|Col4|s|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||1||||s 8||||
||||||||||||||
||s 2||||||||||s 7||
||||||||||||||
||||||||||||||
|||||||||||s 6|||
||||||||||||||
|s 3|||||||||||s||
||||||||s||||5||
||||s 4|||||0|||||


###### s3

|Col1|Col2|Col3|Col4|s|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||1||||s 8|||
|s||||||||||||
||2||||||||||s|
||||||||||||7|
|||||||||||||
|||||||||s|6|||
|||||||||||||
|s||||||||||||


###### s


###### s s5


-----

##### Deferred-Merge Embedding (DME)


##### Build Tree of Segments Algorithm (DME Bottom-Up Phase)

 Input: set of sinks S and tree topology G(S,Top) Output: merging segments ms(v) and edge lengths |ev|, v ∈ G


##### foreach (node v ∈ G, in bottom-up order)
 if (v is a sink node) // if v is a terminal, then ms(v) is a


##### ms[v] = PL(v) //  zero-length Manhattan arc


##### else // otherwise, if v is an internal node,
 (a,b) = CHILDREN(v) //  find v’s children and


##### CALC_EDGE_LENGTH(ea,eb)  //  calculate the edge length
 trr[a][core] = MS(a) // create trr(a) – find merging segment


##### trr[a][radius] = |ea| //  and radius of a
 trr[b][core] = MS(b) // create trr(b) – find merging segment


##### trr[b][radius] = |eb| //  and radius of b
 ms[v] = trr[a] ∩ trr[b] // merging segment of v


-----

##### Deferred-Merge Embedding (DME)


##### Find Exact Locations (DME Top-Down Phase)

###### Possible locations of child node v given the location of its parent node par


###### |epar|
 trr(par) pl(par)
 ms(v)


![](VLSI-design-chap7.pdf-53-0.png)

-----

##### Deferred-Merge Embedding (DME)


##### Find Exact Locations (DME Top-Down Phase)

###### s1 s8
 s7
 s2
 s6 s1


###### s1


###### s4

|Col1|Col2|Col3|Col4|s|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||1||||s|8||
|||||||||||||
||||||||||||s 7|
|s||||||||||||
|2||||||||||||
|||||||||||s 6||
|||||||||||||
|s|||||||||||s|
|3|||||||s||||5|
||||s 4|||||0||||


###### s4


###### s4

|Col1|Col2|Col3|Col4|s|1|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||s|||
||||||||||8|||
||||||||||||s 7|
|s||||||||||||
|2||||||||||||
|||||||||||s 6||
|||||||||||||
|s|||||||||||s|
|3|||||||s||||5|
||||s 4|||||0||||

|Col1|Col2|Col3|Col4|s|1|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||s|8||
|||||||||||||
||||||||||||s 7|
|s||||||||||||
|2||||||||||||
|||||||||||s 6||
|||||||||||||
|s 3|||||||||||s|
||||||||s||||5|
||||s 4|||||0||||


###### s


###### s0

|Col1|Col2|Col3|Col4|s|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||1||||s|8||
|||||||||||||
||||||||||||s 7|
|s||||||||||||
|2||||||||||||
|||||||||||s 6||
|||||||||||||
|s|||||||||||s|
|3|||||||s||||5|


-----

##### Deferred-Merge Embedding (DME)


##### Find Exact Locations (DME Top-Down Phase)

 Input: set of sinks S, tree topology G, outputs of DME bottom-up phase Output: minimum-cost zero-skew tree T with topology G


##### foreach (non-sink node v ∈ G top-down order)
 if (v is the root)


##### loc = any point in ms(v)


##### else
 par = PARENT(v) // par is the parent of v


##### trr[par][core] = PL(par) // create trr(par) – find merging segment
 trr[par][radius] = |ev| //  and radius of par


##### loc = any point in ms[v] ∩ trr[par]
 pl[v] = loc


-----

##### • To address challenging skew constraints, a clock tree undergoes several optimization steps, including

###### − Geometric clock tree construction


###### − Initial clock buffer insertion

 − Clock buffer sizing


###### − Wire sizing

 − Wire snaking



##### • In the presence of process, voltage, and temperature variations, such optimizations require modeling the impact of variations

###### − Variation model encapsulates the different parameters, such as width and thickness, of each library element as well-defined random variables


-----

##### • Area routing: avoiding the division into global and detailed routing

###### − Doing everything at once, subject to design rules


###### − Small netlists with complicated constraints

 − Analog, MCM and PCB routing



##### • Manhattan vs Euclidean paths

###### − Euclidean paths are no longer than Manhattan, usually shorter


###### − Unique Euclidean shortest path

 − Multiple Manhattan paths


###### − When Euclidean shortest paths intersect, there may exist Manhattan shortest paths that do not (not vice versa)



##### • Net ordering is important in area routing

###### − Rule 1: nets with higher aspect ratio (less flexible) routed first


###### − Rule 2: nets surrounded by other nets (more constrained) routed first

 − Rule 3: nets with more pins inside other net's bounding boxes routed first


-----

##### • Recall that Manhattan routing is dictated by the limitations of modern semiconductor manufacturing for thin wires

 • PCB routing is not subject to those limitations


###### − Can use shorter connections



##### • Non-Manhattan connections

###### − Diagonal (45- or 60-degree) segments in addition to horizontal and vertical segments


###### − Create more freedom to place Steiner points 



##### • Octilinear Steiner Tree construction

###### − Algorithms are generally adapted from the Manhattan case


###### − Should produce results that are at least as good as the Manhattan case


-----

##### • Similar to signal-net routing, except for

###### − Very large numbers of sinks


###### − The need to equalize propagation delays from the root to sinks

 − Longer routes (to satisfy the equalization constraint)


###### − Typical algorithms determine topology first, then geometric embedding



##### • Clock skew

###### − Consider propagation delay from the root to each sink


###### − Skew is the maximal pairwise difference between delays (over all pairs of sinks)

 − May be limited to sinks that are within distance d > 0 (local skew)



##### • For a specified wire delay model

###### − ZST: Zero-Skew Tree routing requires that skew = 0


###### − BST: Bounded-Skew Tree routing requires that skew < Bound


-----

##### • Initial clock tree construction 

###### − Topology determination (MMM or RGM)


###### − DME embedding (different flavors for ZST and BST)

 − Working with the Elmore delay model requires more effort than working with linear delay models 



##### • Geometric obstacles (e.g., macros)

###### − May require detours


###### − Can be handled during DME (complicated) or during post-processing (often achieves as good results)



##### • Clock-tree optimization 

###### − Buffer insertion


###### − Buffer sizing

 − Wire sizing


###### − Wire snaking by small amounts

 − Decreasing the impact of process variability


-----

