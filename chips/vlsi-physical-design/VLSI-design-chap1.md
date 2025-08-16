![](VLSI-design-chap1.pdf-0-0.png)

-----

##### 1.1 Electronic Design Automation (EDA)

 1.2 VLSI Design Flow


##### 1.3 VLSI Design Styles

 1.4 Layout Layers and Design Rules


##### 1.5 Physical Design Optimizations

 1.6 Algorithms and Complexity


##### 1.7 Graph Theory Terminology

 1.8 Common EDA Terminology


-----

###### Moore’s Law

 In 1965, Gordon Moore (Fairchild) stated that the number of transistors on an IC would double every year. 10 years later, he revised his statement, asserting that they double every 18 months. Since then, this “rule” has been famously known as Moore’s Law.


![](VLSI-design-chap1.pdf-2-0.png)

-----

|Col1|ITRS 2009 Cost Chart (in Millions of Dollars) ITRS 2009 Cost Chart (in Millions of Dollars)|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||
|0||||||||||||||||
|0|55.7 46.7 79.0|||||||||||||||
|0|42.5|||||||||||||||
||46.6 56.4 33.6 35.2 40.5 31.1 34.0|||||||||||||||
|0||||||||||||||||
||40.7 27.2 29.4 29.6 21.4 43.5|||||||||||||||
|0|44.9|||||||||||||||
||15.7 20.3 19.4 26.3 32.9 29.5 39.8 25.2 32.6 27.0 36.9 16.9 23.1 31.7|||||||||||||||
|||||||||||||||||

|Impact of EDA technologies on overall IC design productivity and IC design cost|Col2|
|---|---|
|ITRS 2009 Cost Chart ITR(Sin 2 M0i0ll9io Cnso sotf CDhoallartrs) (in Millions of Dollars) 120.0 100.0 80.0 55.7 46.7 79.0 60.0 42.5 46.6 56.4 33.6 35.2 40.5 31.1 34.0 40.0 40.7 27.2 29.4 29.6 21.4 43.5 20.0 15.7 20.3 19.4 26.3 32.9 44.9 29.5 39.8 25.2 32.6 27.0 36.9 16.9 23.1 31.7 0.0 2009 2010 2011 2012 2013 2014 2015 2016 2017 2018 2019 2020 2021 2022 2023 2024 Total HW Engineering Costs + EDA Tool Costs Total SW Engineering Costs + ESDA Tool Costs Total HW Engineering Costs + EDA Tool Costs Total SW Engineering Costs + ESDA Tool Costs||
|ITRS 2009 Cost Chart ITR(Sin 2 M0i0ll9io Cnso sotf CDhoallartrs) (in Millions of Dollars) 120.0 100.0 80.0 55.7 46.7 79.0 60.0 42.5 46.6 56.4 33.6 35.2 40.5 31.1 34.0 40.0 40.7 27.2 29.4 29.6 21.4 43.5 20.0 15.7 20.3 19.4 26.3 32.9 44.9 29.5 39.8 25.2 32.6 27.0 36.9 16.9 23.1 31.7 0.0 2009 2010 2011 2012 2013 2014 2015 2016 2017 2018 2019 2020 2021 2022 2023 20 Total HW Engineering Costs + EDA Tool Costs Total SW Engineering Costs + ESDA Tool Costs Total HW Engineering Costs + EDA Tool Costs Total SW Engineering Costs + ESDA Tool Costs||
|||


-----

|Time Period|Circuit and Physical Design Process Advancements|
|---|---|
|||
|1950 -1965|Manual design only.|
|1965 -1975|Layout editors, e.g., place and route tools, first developed for printed circuit boards.|
|1975 -1985|More advanced tools for ICs and PCBs, with more sophisticated algorithms.|
|1985 -1990|First performance-driven tools and parallel optimization algorithms for layout; better understanding of underlying theory (graph theory, solution complexity, etc.).|
|1990 -2000|First over-the-cell routing, first 3D and multilayer placement and routing techniques developed. Automated circuit synthesis and routability-oriented design become dominant. Start of parallelizing workloads. Emergence of physical synthesis.|


###### 2000 - now


###### Design for Manufacturability (DFM), optical proximity correction (OPC), and other techniques emerge at the design-manufacturing interface. Increased reusability of blocks, including intellectual property (IP) blocks.


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

###### Layout editor


![](VLSI-design-chap1.pdf-6-0.png)

-----

###### Common digital cells


###### AND OR INV NAND NOR


###### IN1 IN2 OUT

 0 0 1

 1 0 1

 0 1 1

 1 1 0


###### IN1 IN2 OUT

 0 0 1

 1 0 0

 0 1 0

 1 1 0


-----

###### IN1
 OUT IN2


![](VLSI-design-chap1.pdf-8-0.png)

-----

###### IN1
 OUT IN2


![](VLSI-design-chap1.pdf-9-3.png)

###### Power (Vdd)-Rail

 Ground (GND) Rail


![](VLSI-design-chap1.pdf-9-0.png)

![](VLSI-design-chap1.pdf-9-1.png)

-----

###### Standard cell layout with a feedthrough cell


###### Standard cell layout using over-the-cell (OTC routing


###### Power Pad


###### Power Pad


###### Standard Ground
 Pad
 Cells Pad


###### Standard Ground
 Pad
 Cells Pad

|Col1|Col2|Col3|A|Col5|Col6|
|---|---|---|---|---|---|

|Col1|Col2|A|Col4|Col5|
|---|---|---|---|---|


**VDD** **VDD**

|Col1|Col2|Col3|A’|Col5|Col6|Col7|
|---|---|---|---|---|---|---|

|Pa Pad|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|ad Pad Cells|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||
||||||||||||||||||||
||||A A’||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||VDD||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
|||||||||||||||||GND|||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||

|Pa Pad|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|ad Pad Cells|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||
|||||||||||||||||||||
||||A A’|||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
||VDD|||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
||||||||||||||||||GND|||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||


###### Feedthrough Cell


###### Routing Channel


-----

###### Layout with macro cells

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||RAM PLA RAM Standard Cell Block PLA|||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|VDD||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
||||||||||||||||||||||GND|
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||
|||||||||||||||||||||||


###### Pad


###### Routing Regions


-----

###### Field-programmable gate array (FPGA)


###### Logic Element

|Switchbox Connection|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|SSSBBB LLLBBB SSSBBB LLLBBB LB||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||L||B||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||


-----

###### Layout layers of an inverter cell with external connections


###### Inverter Cell


###### Vdd

 GND


###### External Connections


-----

###### Categories of design rules



###### • Size rules, such as minimum width: The dimensions of any component (shape), e.g., length of a boundary edge or area of the shape, cannot be smaller than given minimum values. These values vary across different metal layers.

 • Separation rules, such as minimum separation: Two shapes, either on the same layer or on adjacent layers, must be a minimum (rectilinear or Euclidean diagonal) distance apart.



###### • Overlap rules, such as minimum overlap: Two connected shapes on adjacent layers must have a certain amount of overlap due to inaccuracy of mask alignment to previously-made patterns on the wafer.


-----

###### Categories of design rules


###### λ: smallest meaningful technology- dependent unit of length


###### Minimum Width: a      

 Minimum Separation: b, c, d


###### Minimum Overlap: e     

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||a||||||||λ||
|||||c|||||||
||||||||||||
||||||e||||||
|||||||||d|||
|||b|||||||||
||||||||||||


![](VLSI-design-chap1.pdf-15-0.png)

###### a λ

 c

 e

 d

 b


-----

###### Types of constraints



###### • Technology constraints enable fabrication for a specific technology node and are derived from technology restrictions. Examples include minimum layout widths and spacing values between layout shapes.

 • Electrical constraints ensure the desired electrical behavior of the design. Examples include meeting maximum timing constraints for signal delay and staying below maximum coupling capacitances.



###### • Geometry (design methodology) constraints are introduced to reduce the overall complexity of the design process. Examples include the use of preferred wiring directions during routing, and the placement of standard cells in rows.


-----

###### Runtime complexity



###### • Runtime complexity: the time required by the algorithm to complete as a function of some natural measure of the problem size, allows comparing the scalability of various algorithms

 • Complexity is represented in an asymptotic sense, with respect to the input size n, using big-Oh notation or O(…)

### t(n)

###### • Runtime t(n) is order f (n), written as t(n) = O(f (n)) when lim = k

_n→∞_ _f_ (n)

###### where k is a real number



###### • Example: t(n) = 7n! + n[2] + 100, then t(n) = O(n!) because n! is the fastest growing term as n →∞.


-----

###### Runtime complexity



###### • Example: Exhaustively Enumerating All Placement Possibilities

 − Given: n cells


###### − Task: find a single-row placement of n cells with minimum total wirelength by using exhaustive enumeration.


###### − Solution: The solution space consists of n! placement options. If generating and evaluating the wirelength of each possible placement solution takes 1 µs and n = 20, the total time needed to find an optimal solution would be 77,147 years!

 • A number of physical design problems have best-known algorithm complexities that grow exponentially with n, e.g., O(n!), O(n[n]), and O(2[n]).



###### • Many of these problems are NP-hard (NP: non-deterministic polynomial time)

 − No known algorithms can ensure, in a time-efficient manner, globally optimal solution


###### ⇒ Heuristic algorithms are used to find near-optimal solutions


-----

###### Heuristic algorithms



###### • Deterministic: All decisions made by the algorithm are repeatable, i.e., not random. One example of a deterministic heuristic is Dijkstra’s shortest path algorithm.

 • Stochastic: Some decisions made by the algorithm are made randomly, e.g., using a pseudo-random number generator. Thus, two independent runs of the algorithm will produce two different solutions with high probability. One example of a stochastic algorithm is simulated annealing.



###### • In terms of structure, a heuristic algorithm can be

 − Constructive: The heuristic starts with an initial, incomplete (partial) solution and adds components until a complete solution is obtained.


###### − Iterative: The heuristic starts with a complete solution and repeatedly improves the current solution until a preset termination criterion is reached.


-----

###### Heuristic algorithms


-----

###### Graph Hypergraph Multigraph

 b b

 e

 f
 a a
 d

 e g f d
 c


![](VLSI-design-chap1.pdf-21-0.png)

###### b


![](VLSI-design-chap1.pdf-21-1.png)

###### c


![](VLSI-design-chap1.pdf-21-2.png)

###### b


![](VLSI-design-chap1.pdf-21-3.png)

###### e


![](VLSI-design-chap1.pdf-21-4.png)

###### a


![](VLSI-design-chap1.pdf-21-5.png)

###### g


![](VLSI-design-chap1.pdf-21-6.png)

###### d


![](VLSI-design-chap1.pdf-21-7.png)

###### f


-----

###### Directed graphs with cycles Directed acyclic graph

 c f c f

 a
 a b
 b d g b d g


![](VLSI-design-chap1.pdf-22-0.png)

###### c


![](VLSI-design-chap1.pdf-22-1.png)

###### b


![](VLSI-design-chap1.pdf-22-2.png)

###### g


![](VLSI-design-chap1.pdf-22-3.png)

###### b


![](VLSI-design-chap1.pdf-22-4.png)

###### a


![](VLSI-design-chap1.pdf-22-5.png)

###### e


![](VLSI-design-chap1.pdf-22-6.png)

###### d


![](VLSI-design-chap1.pdf-22-7.png)

###### d


-----

###### Undirected graph with maximum node degree 3 Directed tree

 a
 b a


![](VLSI-design-chap1.pdf-23-0.png)

###### a


![](VLSI-design-chap1.pdf-23-1.png)

###### e


![](VLSI-design-chap1.pdf-23-2.png)

###### g


![](VLSI-design-chap1.pdf-23-3.png)

###### b


![](VLSI-design-chap1.pdf-23-4.png)

###### d


![](VLSI-design-chap1.pdf-23-5.png)

###### f


![](VLSI-design-chap1.pdf-23-6.png)

###### h


![](VLSI-design-chap1.pdf-23-7.png)

###### k


![](VLSI-design-chap1.pdf-23-8.png)

###### f


-----

###### Rectilinear minimum spanning tree (RMST)


###### Rectilinear Steiner minimum tree (RSMT)


###### c (6,4) c (6,4)

|Col1|b (|2,6)|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
||||||c (6|,4)||
|||||||||
|||||||||
||a (2|,1)||||||

|Col1|b (2|,6)|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
||||Stein|er p|oint|||
|||||||||
||||||c (|6,4)||
|||||||||
|||||||||
||a (|2,1)||||||


![](VLSI-design-chap1.pdf-24-0.png)

###### b (2,6)

 c (6,4)

 a (2,1)


-----

###### Netlist


###### a
 x
 N3 N5
 N1 N2 z c


###### (a: N1) (b: N2) (c: N5) (x: IN1 N1, IN2 N2, OUT N3) (y: IN1 N1, IN2 N2, OUT N4) (z: IN1 N3, IN2 N4, OUT N5)


###### (N1: a, x.IN1, y.IN1) (N2: b, x.IN2, y.IN2) (N3: x.OUT, z.IN1) (N4: y.OUT, z.IN2) (N5: z.OUT, c)


###### b


###### Pin-Oriented Netlist Net-Oriented Netlist


-----

###### Connectivity graph


###### a
 x
 N3 N5
 N1 N2 z c


![](VLSI-design-chap1.pdf-26-0.png)

###### a


![](VLSI-design-chap1.pdf-26-1.png)

###### x


![](VLSI-design-chap1.pdf-26-2.png)

###### c


###### b


![](VLSI-design-chap1.pdf-26-0.png)

###### b


![](VLSI-design-chap1.pdf-26-1.png)

###### y


-----

###### Connectivity matrix


###### a
 x
 N3 N5
 N1 N2 z c


###### a b x y z c

 a 0 0 1 1 0 0

 b 0 0 1 1 0 0

 x 1 1 0 2 1 0

 y 1 1 2 0 1 0

 z 0 0 1 1 0 1

 c 0 0 0 0 1 0


###### b


-----

###### Distance metric between two points P1 (x1,y1) and P2 (x2,y2)

 n n
# d = n x − x + y − y
###### 2 1 2 1


###### with n = 2: Euclidean distance

 n = 1: Manhattan distance

|2: Euclidean distance dE|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|E : Manhattan distance d M||||||||
|P 1|(2,4|)|||d M|= 7||
|||||||||
|||||d = E|5|||
|||||||||
|||d = M|7|||P (6 2|,1)|


![](VLSI-design-chap1.pdf-28-0.png)

###### P1 (2,4) dM = 7

 dE = 5

 dM = 7 P2 (6,1)


-----

##### • IC production experienced huge growth since the 1960s

###### − Exponential decrease in transistor size, cost per transistor, power per transistor, etc



##### • IC design is impossible without simplification and automation

###### − Row-based standard-cell layout with design rules


###### − Traditionally, each step in the VLSI design flow has been automated separately by software (CAD) tools



##### • Software tools use sophisticated algorithms

###### − Many problems in physical design are NP-hard – solved by heuristic algorithms that find near-optimal solutions


###### − Deterministic versus stochastic algorithms

 − Constructive algorithms versus iterative improvement


###### − Graph algorithms – deal with circuit connectivity

 − Computational geometry – deal with circuit layout


-----

