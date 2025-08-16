![](VLSI-design-chap5.pdf-0-0.png)

-----

###### 5.1 Introduction

 5.2 Terminology and Definitions


###### 5.3 Optimization Goals

 5.4 Representations of Routing Regions


###### 5.5 The Global Routing Flow

 5.6 Single-Net Routing


###### 5.6.1 Rectilinear Routing 5.6.2 Global Routing in a Connectivity Graph 5.6.3 Finding Shortest Paths with Dijkstra’s Algorithm 5.6.4 Finding Shortest Paths with A* Search


###### 5.7 Full-Netlist Routing
 5.7.1 Routing by Integer Linear Programming 5.7.2 Rip-Up and Reroute (RRR)


###### 5.8 Modern Global Routing
 5.8.1 Pattern Routing 5.8.2 Negotiated-Congestion Routing


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

![](VLSI-design-chap5.pdf-3-0.png)

###### Given a placement, a netlist and technology information,

 • determine the necessary wiring, e.g., net topologies and specific routing segments, to connect these cells

 • while respecting constraints, e.g., design rules and routing resource capacities, and

 • optimizing routing objectives, e.g., minimizing total wirelength and maximizing timing slack.


-----

![](VLSI-design-chap5.pdf-4-0.png)

###### Terminology:

 • Net: Set of two or more pins that have the same electric potential

 • Netlist: Set of all nets.

 • Congestion: Where the shortest routes of several nets are incompatible because they traverse the same tracks.

 • Fixed-die routing: Chip outline and routing resources are fixed.

 • Variable-die routing: New routing tracks can be added as needed.


-----

###### Placement result


###### Netlist:

 N1 = {C4, D6, B3}


###### N2 = {D4, B4, C1, A4}
 N3 = {C2, D5}


###### N4 = {B1, A1, C3}


###### Technology Information (Design Rules)


-----

###### Netlist:

 N1 = {C4, D6, B3}


###### N2 = {D4, B4, C1, A4}
 N3 = {C2, D5}


###### N4 = {B1, A1, C3}


###### Technology Information (Design Rules)


-----

###### Netlist:

 N1 = {C4, D6, B3}


###### N2 = {D4, B4, C1, A4}
 N3 = {C2, D5}


###### N4 = {B1, A1, C3}


###### Technology Information (Design Rules)

|5|Col2|
|---|---|


-----

###### Non-Manhattan and clock routing (Chap. 7)


-----

###### Global Routing



###### • Wire segments are tentatively assigned (embedded) within the chip layout

 • Chip area is represented by a coarse routing grid



###### • Available routing resources are represented by edges with capacities in a grid graph

 ⇒ Nets are assigned to these routing resources


-----

###### Global Routing Detailed Routing

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||N 3||||||||||||||
|||||||||||||||||
|||||||||||N 1 N 2 N 3||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
||||N 3 N 1|||||||||||||
|||||||||||||||||
|||||||||||||||||
||||||||||N N 1 2|||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||
|||||||||||||||||


![](VLSI-design-chap5.pdf-10-0.png)

###### Horizontal Vertical Via Segment Segment


-----

![](VLSI-design-chap5.pdf-11-0.png)

###### Global Routing

 Congestion Map


![](VLSI-design-chap5.pdf-11-1.png)

###### Detailed Routing


![](VLSI-design-chap5.pdf-11-2.png)

###### Wire Tracks


![](VLSI-design-chap5.pdf-11-3.png)

-----

###### • Routing Track: Horizontal wiring path

 • Routing Column: Vertical wiring path



###### • Routing Region: Region that contains routing tracks or columns

 • Uniform Routing Region: Evenly spaced horizontal/vertical grid



###### • Non-uniform Routing Region: Horizontal and vertical boundaries that are aligned to external pin connections or macro-cell boundaries resulting in routing regions that have differing sizes


-----

###### Channel


###### Rectangular routing region with pins on two opposite sides

 Standard cell layout (Two-layer routing)


![](VLSI-design-chap5.pdf-13-0.png)

-----

###### Channel


###### Rectangular routing region with pins on two opposite sides

 Routing channel

 Routing channel

 Standard cell layout (Two-layer routing)

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||
||||||||||||||||||
||||Routing channel Routing channel||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||


![](VLSI-design-chap5.pdf-14-0.png)

-----

###### Capacity


###### Number of available routing tracks or columns

|B|Col2|Col3|Col4|Col5|Col6|B|Col8|C|Col10|Col11|Col12|D|Col14|B|Col16|C|Col18|Col19|Col20|B|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
|||C||||||B||||||B||C|||||

|B|B C D B|C B|
|---|---|---|
|A C A B B C D|||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Horizontal Routing Channel B B C D B C B h d pitch A C A B B C D|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||


-----

###### Capacity


###### Number of available routing tracks or columns



###### • For single-layer routing, the capacity is the height h of the channel divided by the pitch dpitch

 • For multilayer routing, the capacity σ is the sum of the capacities of all layers.


###### Horizontal Routing Channel

|B|Col2|Col3|Col4|B|Col6|C|Col8|D|Col10|B|Col12|C|Col14|B|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
|A||C||A||||||B||C|||


######  
 h σ(Layers ) =  

##### ∑

###### d ( ) layer ∈Layers  pitch [layer] 

|B|B C D B|C B|h d pitch|
|---|---|---|---|
|A C A B B C D||||


-----

###### Switchbox (Two-layer macro cell layout)


###### Intersection of horizontal and vertical channels


###### 3

 B


###### Horizontal Channel

|Col1|Col2|Col3|Col4|B|Col6|C|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
|A|||||||||
||||||||||
||||||||||
|||C||A||B|||


###### Vertical Channel

 Horizontal channel is routed after vertical channel is routed

|B C 3 Horizontal B Channel A C A B Vertical|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||


-----

###### T-junction (Two-layer macro cell layout)


###### Horizontal Channel

|Col1|Col2|Col3|B|Col5|C|Col7|
|---|---|---|---|---|---|---|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
|B|||||||
||||||||
||||||B||
|A|||||||
||C||||||
||||A||||


###### Vertical Channel

|B C C B B Horiz Chan A C A B Vertical|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||
||||||||||||||||||||||


-----

###### 2D and 3D Switchboxes


###### Metal5

 Metal4


###### Bottom pin connection on 3D switchbox

 3D switchbox


###### Top pin connection on cell

 Pin on channel boundary


###### Horizontal channel

 Metal3

 Metal2

 Metal1


###### 2D switchbox


###### Vertical channel


-----

###### Gcells (Tiles) with macro cell layout

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|Metal1||||||||||||Metal3||||||||
|||||||||||||||||||||


###### Metal2


###### Metal4 etc.


-----

###### Gcells (Tiles) with standard cells

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|Metal1 (Standard cells)||||||||||||Metal3||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||


###### Metal2 (Cell ports)


###### Metal4 usw.


-----

###### Gcells (Tiles) with standard cells (back-to-back)

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|Metal1 (Back-to-back- standard cells)||||||||||||Metal3||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||
|||||||||||||||||||||


###### Metal2 (Cell ports)


###### Metal4 etc.


-----

###### • Global routing seeks to

 − determine whether a given placement is routable, and


###### − determine a coarse routing for all nets within available routing regions



###### • Considers goals such as

 − minimizing total wirelength, and


###### − reducing signal delays on critical nets


-----

###### Full-custom design


###### Layout is dominated by macro cells and routing regions are non-uniform


![](VLSI-design-chap5.pdf-24-1.png)

![](VLSI-design-chap5.pdf-24-2.png)

###### V


###### 3
 A F

|B|5|D|
|---|---|---|
|||4|
|||C 2 E|
|1|||
|A|||
|||3|
|||F|

|B|D C E|
|---|---|
|A||
||F|


![](VLSI-design-chap5.pdf-24-0.png)

![](VLSI-design-chap5.pdf-24-1.png)

###### H


![](VLSI-design-chap5.pdf-24-2.png)

###### F


![](VLSI-design-chap5.pdf-24-3.png)

###### H


![](VLSI-design-chap5.pdf-24-4.png)

###### C


![](VLSI-design-chap5.pdf-24-5.png)

###### B


###### (1) Types of channels


![](VLSI-design-chap5.pdf-24-0.png)

###### H


![](VLSI-design-chap5.pdf-24-1.png)

###### D


![](VLSI-design-chap5.pdf-24-2.png)

###### E


###### (2) Channel ordering


![](VLSI-design-chap5.pdf-24-0.png)

###### A


-----

###### Standard-cell design


###### If number of metal layers is limited, feedthrough cells must be used to route across multiple cell rows


###### Feedthrough cells

|Col1|A|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|


###### Variable-die, standard cell design:

 Total height = ΣCell row heights + All channel heights

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||A||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||||
||||||||||||||||||||||A||
||||||||||||||||||||||||
|||A||||||||||||||A|||||||


-----

###### Standard-cell design


###### Steiner tree solution with minimal wirelength


###### Steiner tree solution with fewest feedthrough cells


-----

###### Gate-array design


###### Cell sizes and sizes of routing regions between cells are fixed

 Available Key Tasks:


###### Determine routability

 Find a feasible solution


-----

###### 5.1 Introduction

 5.2 Terminology and Definitions


###### 5.3 Optimization Goals

 5.4 Representations of Routing Regions


###### 5.5 The Global Routing Flow

 5.6 Single-Net Routing


###### 5.6.1 Rectilinear Routing 5.6.2 Global Routing in a Connectivity Graph 5.6.3 Finding Shortest Paths with Dijkstra’s Algorithm 5.6.4 Finding Shortest Paths with A* Search


###### 5.7 Full-Netlist Routing
 5.7.1 Routing by Integer Linear Programming 5.7.2 Rip-Up and Reroute (RRR)


###### 5.8 Modern Global Routing
 5.8.1 Pattern Routing 5.8.2 Negotiated-Congestion Routing


-----

###### • Routing regions are represented using efficient data structures

 • Routing context is captured using a graph, where


###### − nodes represent routing regions and


###### − edges represent adjoining regions

 • Capacities are associated with both edges and nodes to represent available routing resources


-----

###### Grid graph model


###### 1 2 3 4 5


###### 6 7 8 9 10

 11 12 13 14 15


###### 16 17 18 19 20 16 17 18 19 20

 21 22 23 24 25 21 22 23 24 25

 ggrid = (V,E), where the nodes v ∈ V represent the routing grid cells (gcells) and the edges represent connections of grid cell pairs (vi,vj)

|Col1|7 8|Col3|9 1|
|---|---|---|---|
|1 1|2 1|3 1|4 1|
|||||

|1|2|3|4|5|
|---|---|---|---|---|
|6|7|8|9|10|
|11|12|13|14|15|
|16|17|18|19|20|
|21|22|23|24|25|


-----

###### Channel connectivity graph


###### 1 2 3 6 9 1 2 3

 7

 8 8

 G = (V,E), where the nodes v ∈ V represent channels, and the edges E represent adjacencies of the channels


-----

###### Switchbox connectivity graph


###### G = (V, E), where the nodes v ∈ V represent switchboxes and an edge exists between two nodes if the corresponding switchboxes are on opposite sides of the same channel


-----

###### 1. Defining the routing regions (Region definition)

 − Layout area is divided into routing regions


###### − Nets can also be routed over standard cells

 − Regions, capacities and connections are represented by a graph


###### 2. Mapping nets to the routing regions (Region assignment)

 − Each net of the design is assigned to one or several routing regions to connect all of its pins


###### − Routing capacity, timing and congestion affect mapping


###### 3. Assigning crosspoints along the edges of the routing regions (Midway routing)

 − Routes are assigned to fixed locations or crosspoints along the edges of the routing regions


###### − Enables scaling of global and detailed routing


-----

###### 5.1 Introduction

 5.2 Terminology and Definitions


###### 5.3 Optimization Goals

 5.4 Representations of Routing Regions


###### 5.5 The Global Routing Flow

 5.6 Single-Net Routing


###### 5.6.1 Rectilinear Routing 5.6.2 Global Routing in a Connectivity Graph 5.6.3 Finding Shortest Paths with Dijkstra’s Algorithm 5.6.4 Finding Shortest Paths with A* Search


###### 5.7 Full-Netlist Routing
 5.7.1 Routing by Integer Linear Programming 5.7.2 Rip-Up and Reroute (RRR)


###### 5.8 Modern Global Routing
 5.8.1 Pattern Routing 5.8.2 Negotiated-Congestion Routing


-----

|Col1|B (2|, 6)|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
||||||C (6|, 4)||
|||||||||
|||||||||
||A (2|, 1)||||||

|Col1|B (2|, 6)|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|S (2|, 4)||||C (6|, 4)||
|||||||||
|||||||||
||A (2|, 1)||||||


###### Rectilinear minimum spanning tree (RMST)


###### Rectilinear Steiner minimum tree (RSMT)


-----

###### • An RMST can be computed in O(p[2]) time, where p is the number of terminals in the net using methods such as Prim’s Algorithm

 • Prim’s Algorithm builds an MST by starting with a single terminal and greedily adding least-cost edges to the partially-constructed tree



###### • Advanced computational-geometric techniques reduce the runtime to O(p log p)


-----

###### Characteristics of an RSMT

 • An RSMT for a p-pin net has between 0 and p – 2 (inclusive) Steiner points



###### • The degree of any terminal pin is 1, 2, 3, or 4 The degree of a Steiner point is either 3 or 4

 • A RSMT is always enclosed in the minimum bounding box (MBB) of the net



###### • The total edge length LRSMT of the RSMT is at least half the perimeter

 • of the minimum bounding box of the net: LRSMT ≥ LMBB / 2


-----

###### Transforming an initial RMST into a low-cost RSMT


###### p
2


###### p
3


###### p
3


###### p
3


###### p
2


###### p
2


###### p
2

###### p S 3


###### p
1


###### p
1


###### p
1


###### p
1

###### Final tree (RSMT)

|p 2|p 2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||

|p 2|p 2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||

|p 2 S 1|p 2|Col3|Col4|Col5|
|---|---|---|---|---|
||S 1||||
||||||

|p 2 S|p 2|Col3|Col4|Col5|
|---|---|---|---|---|
||S||||
||||||


###### Construct L-shapes between points with (most) overlap of net segments


-----

###### Hanan grid



###### • Adding Steiner points to an RMST can significantly reduce the wirelength

 • Maurice Hanan proved that for finding Steiner points, it suffices to consider only points located at the intersections of vertical and horizontal lines that pass through terminal pins



###### • The Hanan grid consists of the lines x = xp, y = yp that pass through the location (xp,yp) of each terminal pin p

 • The Hanan grid contains at most (n[2]-n) candidate Steiner points (n = number of pins), thereby greatly reducing the solution space for finding an RSMT


-----

###### Terminal pins Intersection lines Hanan points ( ) RSMT


-----

###### Definining routing regions Pin connections Pins assigned to grid cells


-----

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
||A|A||||||||
|||||||||||
||A|||||||||
||A|A|||A||A|||
|||||||||||
||A||||||A|||
||A||||||A|||
|||||||||||
|||||||||||
|||||||||||


###### Pins assigned to grid cells Rectilinear Steiner Assigned routing regions
 minimum tree (RSMT) and feedthrough cells


-----

###### A Sequential Steiner Tree Heuristic

 1. Find the closest (in terms of rectilinear distance) pin pair, construct their minimum bounding box (MBB)


###### 2. Find the closest point pair (pMBB,pC) between any point pMBB on the MBB and pC from the set of pins to consider

 3. Construct the MBB of pMBB and pC


###### 4. Add the L-shape that pMBB lies on to T (deleting the other L-shape). If pMBB is a pin, then add any L-shape of the MBB to T.

 5. Goto step 2 until the set of pins to consider is empty


-----

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||||||
|||1||||
|||||||
|||||||
|||||||


-----

|1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||


-----

###### pc

|1|Col2|Col3|Col4|Col5|3|Col7|
|---|---|---|---|---|---|---|
||||||||
|||2|||||
||||1||||
||||||||
||||||||
||||||||
||||||||


###### MBB


-----

###### 3 1 3

 2
 4
## 1 2

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||2|||4|
|||||||
|||||||
|||||||
|||||||


###### pMBB


-----

###### 3 1 3 1

 2 2
 4
## 1 2 3

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||2|||4|
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||3|||4||
||||||||
||||||5||
||||||||


-----

###### 3 1 3 1

 2 2
 4

## 1 2 3

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||2|||4|
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||3|||4||
||||||||
||||||5||
||||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||4|||4|
|||||||
||||6||5|
|||||||


-----

###### 3 1 3 1

 2 2
 4

## 1 2 3

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||2|||4|
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||3|||4||
||||||||
||||||5||
||||||||


###### 2

 4

## 4 5

###### 6 5 6

 7

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||4|||4|
|||||||
||||6||5|
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||5|||4|
|||||||
||||6||5|
||7|||||


-----

###### 3 1 3 1

 2 2
 4

## 1 2 3

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||2|||4|
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||3|||4||
||||||||
||||||5||
||||||||


###### 2 2
 4 4

## 4 5 6


###### 7


###### 7

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||4|||4|
|||||||
||||6||5|
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||5|||4|
|||||||
||||6||5|
||7|||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||6|||4||
||||||||
||||6||5||
||7||||||


-----

###### 3 1 3 1

 2 2
 4

## 1 2 3

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||1||||
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||2|||4|
|||||||
|||||||
|||||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||3|||4||
||||||||
||||||5||
||||||||


###### 2 2
 4 4

## 4 5 6


###### 7


###### 7

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||4|||4|
|||||||
||||6||5|
|||||||

|1|Col2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||2|||||
|||5|||4|
|||||||
||||6||5|
||7|||||

|1|Col2|Col3|Col4|3|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
||2||||||
|||6|||4||
||||||||
||||6||5||
||7||||||


-----

###### Channel connectivity graph

 Switchbox connectivity graph


###### 9 1 2 3


###### 3


###### 8


###### 14


###### 3


###### 8


###### 14


-----

###### Channel connectivity graph

 Switchbox connectivity graph


-----

###### • Combines switchboxes and channels, handles non-rectangular block shapes

 • Suitable for full-custom design and multi-chip modules


###### Overview:

_A_

1 2

_B_

4 5 6

_A_

8

_B_

10 11

###### Routing regions

|1|A B|2|3|
|---|---|---|---|
|4|5|6|7|
|8|A B||9|
|10|11||12|


###### Graph representation


1 2 3


4

8


7

9


10


11 12


###### Graph-based path search


-----

###### Defining the routing regions


###### +

 Horizontal macro-cell edges Vertical macro-cell edges


-----

###### Defining the connectivity graph

 1 8 17 21 23


###### 1

 2


###### 3

 4


###### 25

 26


###### 5

 6

|8|17|21 23|
|---|---|---|
|9|18|24 22 25|
|10 19 11 12 15 13 14 20|||
|13 14|||


![](VLSI-design-chap5.pdf-57-0.png)

###### 16


###### 7


###### 26

 27


###### 16

|1|8|Col3|Col4|17|21|23|
|---|---|---|---|---|---|---|
|2|9|||18||24|
|3 4|10 1112|||19|||
|||10 12|||||
||11||||||
|5|13|14|15|20|22|25|
|6||||||26|
|7|16|||||27|


-----

###### Horizontal capacity of routing region 1

 2 Tracks


###### Vertical capacity of routing region 1


###### 1,2


###### 23

 24

 25


###### 1

 2


###### 3

 4

|8,2|17|21 23|
|---|---|---|
|2 9|18|24 22 25|
|10 19 11 12 15 13 14 20|||
|13 14|||


![](VLSI-design-chap5.pdf-58-0.png)

###### 26


###### 5

 6


###### 16


###### 7


###### 26

 27


###### 16

|1|8|Col3|Col4|17|21|23|
|---|---|---|---|---|---|---|
|2|9|||18||24|
|3 4|10 1112|||19|||
|||10 12|||||
||11||||||
|5|13|14|15|20|22|25|
|6||||||26|
|7|16|||||27|


-----

###### 2,2


###### 1,2


###### 1,1


###### 23

 24

 25


###### 1

 2


###### 3

 4


###### 2,2


###### 2,2


###### 6,1


###### 3,2


###### 3,1


###### 3,4


###### 3,1


###### 3,1 3,1

 16


###### 3,1

|8,2 1,|17,3 1,|21 23,1 1, 1,4|
|---|---|---|
|2 9|1, 18|1 1,4 1, 1,1 24 6 22 25 1 3,4 3,|
|,2 2,3 2, 10,2 1,1 19 4 11 12,2 2,1 2,1 15 13 14 20,2 3,1 3,|||
|,2 2,1 2 13 14,2 3,|||


![](VLSI-design-chap5.pdf-59-0.png)

###### 26


###### 5

 6


###### 16


###### 7


###### 26

 27

|1|8|Col3|Col4|17|21|23|
|---|---|---|---|---|---|---|
|2|9|||18||24|
|3 4|10 1112|||19|||
|||10 12|||||
||11||||||
|5|13|14|15|20|22|25|
|6||||||26|
|7|16|||||27|


-----

###### Algorithm Overview

 1. Define routing regions


###### 2. Define connectivity graph

 3. Determine net ordering


###### 4. Assign tracks for all pin connections in Netlist

 5. Consider each net


###### a) Free corresponding tracks for net’s pins

 b) Decompose net into two-pin subnets


###### c) Find shortest path for subnet connectivity graph


###### d) If no shortest path exists, do not route, otherwise, assign subnet to the nodes of shortest path and update routing capacities

 6. If there are unrouted nets, goto Step 5, otherwise END


-----

###### Example

 Global routing of the nets A-A and B-B


4

8


7

9

|1|B A|2|3|
|---|---|---|---|
|||||
|4|5|6|7|
|8|A B||9|
|10|11||12|


10


11 12


-----

###### Example

 Global routing of the nets A-A and B-B


7

9

|1|B A|2|3|
|---|---|---|---|
|||||
|4|5|6|7|
|8|A B||9|
|10|11||12|


![](VLSI-design-chap5.pdf-62-0.png)

7

9

|Col1|A B|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
||A B|||||
|||||||


10


11 12


-----

###### Example

 Global routing of the nets A-A and B-B


4

8


7

9

|1|B A|2|3|
|---|---|---|---|
|||||
|4|5|6|7|
|8|A B||9|
|10|11||12|


10


11 12


![](VLSI-design-chap5.pdf-63-0.png)

1 2 3


4

8


7

9

|Col1|A B|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
||A B|||||
|||||||


10

1


11 12

2 3


![](VLSI-design-chap5.pdf-63-0.png)

4 1,2 0,4 0,1

5 6

8 3,1


7

9

|Col1|Col2|Col3|A B|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
||||||||||
||||A B||||||
||||||||||


-----

|w Example|1|B A|2|3|Col6|
|---|---|---|---|---|---|
|Global routing of the nets A-A and B-B|||||© KLMH|
||4|5|6|7||
||8|A B||9||
||10|11||12||

|Col1|Col2|Col3|A B|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
||||||||||
||||A B||||||
||||||||||


![](VLSI-design-chap5.pdf-64-0.png)

-----

|Example|Col2|1|2|3|3,1 3,4 3,3|
|---|---|---|---|---|---|
|Determine routability of a placement|B A||||KLMH 5 6 7 © 4 1,4 1,1 1,4 1,3 3,4 3,1 3,3|
||4|5|6|7||
||8|9|B A|10||


![](VLSI-design-chap5.pdf-65-1.png)

4


8 9 10

1 2 3

3,1 3,4 3,3

5 6 7

0,3 0,1 0,4 0,2

3,4 3,1 2,2

8 9 10

|B A|1|2|3|
|---|---|---|---|
|4|5|6|7|
|8|9|B A||

|B A|Col2|1|2|3|
|---|---|---|---|---|
|4||||7|
|||? 5|6||
||||||


![](VLSI-design-chap5.pdf-65-0.png)

8


1 2 3

_A_

5 6 7

_B_

# ? A

9 10


-----

|Example|Col2|1|2|3|3,1 3,4 3,3|
|---|---|---|---|---|---|
|Determine routability of a placement|B A||||KLMH 5 6 7 © 4 1,4 1,1 1,4 1,3 3,4 3,1 3,3|
||4|5|6|7||
||8|9|B A|10||


![](VLSI-design-chap5.pdf-66-0.png)

4


8 9 10

1 2 3

3,1 3,4 3,3

5 6 7

0,3 0,1 0,4 0,2

3,4 3,1 2,2

8 9 10

|B A|1|2|3|
|---|---|---|---|
|4|5|6|7|
|8|9|B A||

|B A|Col2|Col3|1|Col5|2|Col7|3|
|---|---|---|---|---|---|---|---|
|||||||||
||4||||||7|
||||5|||6||
|||||||||


![](VLSI-design-chap5.pdf-66-0.png)

8


_A_

9 10


-----

|Example|Col2|1|2|3|Col6|
|---|---|---|---|---|---|
|Determine routability of a placement|B A||||© KLMH|
||4|5|6|7||
||8|9|B A|10||

|B A|Col2|Col3|1|Col5|2|Col7|3|
|---|---|---|---|---|---|---|---|
|||||||||
||4||||||7|
||||5|||6||
|||||||||


![](VLSI-design-chap5.pdf-67-0.png)

8


_A_

9 10


-----

###### • Finds a shortest path between two specific nodes in the routing graph

 • Input


###### − graph G(V,E) with non-negative edge weights W,
 − source (starting) node s, and


###### − target (ending) node t



###### • Maintains three groups of nodes

 − Group 1 – contains the nodes that have not yet been visited


###### − Group 2 – contains the nodes that have been visited but for which the shortest-path cost from the starting node has not yet been found


###### − Group 3 – contains the nodes that have been visited and for which the shortest path cost from the starting node has been found

 • Once t is in Group 3, the algorithm finds the shortest path by backtracing


-----

###### Example


###### s
 1,4 8,8
 1 4

 8,6 9,7 3,2


###### Find the shortest path from source s to target t where the path cost ∑w1 + ∑w2 is minimal


![](VLSI-design-chap5.pdf-69-0.png)

###### 1


![](VLSI-design-chap5.pdf-69-2.png)

###### 4


![](VLSI-design-chap5.pdf-69-5.png)

###### 7


###### t


![](VLSI-design-chap5.pdf-69-0.png)

###### 2


![](VLSI-design-chap5.pdf-69-3.png)

###### 8


###### 1,4 2,8 4,5


![](VLSI-design-chap5.pdf-69-0.png)

###### 5


![](VLSI-design-chap5.pdf-69-1.png)

###### 6


-----

###### s


######,,
 1 4 7

 9,7 3,2

 2,6 2,8
 2 5 8

 2,8 4,5

 9,8 3,3
 3 6 9

 Current node: 1


###### Group 2 Group 3


![](VLSI-design-chap5.pdf-70-0.png)

###### 2


![](VLSI-design-chap5.pdf-70-1.png)

###### 3


![](VLSI-design-chap5.pdf-70-2.png)

###### 8


###### 1


###### 7


-----

###### s


######,,
 1 4 7 Group 2 Group 3

 N [2] 8,6

 [1]
 9,7 3,2 W [4] 1,4

 2,6 2,8
 2 5 8 t W [4] 1,4

 2,8 4,5 parent of node [node name] ∑w1(s,node),∑w2(s,node)

 9,8 3,3
 3 6 9

 Current node: 1 Neighboring nodes: 2, 4 Minimum cost in group 2: node 4


![](VLSI-design-chap5.pdf-71-0.png)

###### 2


![](VLSI-design-chap5.pdf-71-1.png)

###### 3


![](VLSI-design-chap5.pdf-71-2.png)

###### 8


###### 1


###### 7


-----

###### s


######,,
 1 4 7

 9,7 3,2

 2,6 2,8
 2 5 8

 2,8 4,5

 9,8 3,3
 3 6 9

 Current node: 4 Neighboring nodes: 1, 5, 7 Minimum cost in group 2: node 2


###### Group 2 Group 3

 N [2] 8,6

 [1]
 W [4] 1,4

 N [5] 10,11 W [4] 1,4
 W [7] 9,12

 N [2] 8,6

 parent of node [node name] ∑w1(s,node),∑w2(s,node)


![](VLSI-design-chap5.pdf-72-0.png)

###### 2


![](VLSI-design-chap5.pdf-72-1.png)

###### 3


![](VLSI-design-chap5.pdf-72-2.png)

###### 8


###### 1


###### 7


-----

###### s


######,,
 1 4 7

 9,7 3,2

 2,6 2,8
 2 5 8

 2,8 4,5

 9,8 3,3
 3 6 9

 Current node: 2 Neighboring nodes: 1, 3, 5 Minimum cost in group 2: node 3


###### Group 2 Group 3

 N [2] 8,6

 [1]
 W [4] 1,4

 N [5] 10,11 W [4] 1,4
 W [7] 9,12

 N [3] 9,10 N [2] 8,6
 W [5] 10,12

 N [3] 9,10

 parent of node [node name] ∑w1(s,node),∑w2(s,node)


![](VLSI-design-chap5.pdf-73-0.png)

###### 2


![](VLSI-design-chap5.pdf-73-1.png)

###### 3


![](VLSI-design-chap5.pdf-73-2.png)

###### 8


###### 1


###### 7


-----

###### s


######,,
 1 4 7


###### Group 2 Group 3


![](VLSI-design-chap5.pdf-74-0.png)

###### 2


![](VLSI-design-chap5.pdf-74-1.png)

###### 3


![](VLSI-design-chap5.pdf-74-2.png)

###### 8


###### 1


###### 7


###### Current node: 3 N [5] 10,11 Neighboring nodes: 2, 6 Minimum cost in group 2: node 5
 parent of node [node name] ∑w1(s,node),∑w2(s,node)


![](VLSI-design-chap5.pdf-74-0.png)

###### 5


![](VLSI-design-chap5.pdf-74-1.png)

###### 9


###### s 1


-----

###### Group 2 Group 3

 N [2] 8,6

 [1]
 W [4] 1,4

 N [5] 10,11 W [4] 1,4
 W [7] 9,12

 N [3] 9,10 N [2] 8,6
 W [5] 10,12

 W [6] 18,18 N [3] 9,10

 N [6] 12,19
 N [5] 10,11
 W [8] 12,19

 W [7] 9,12

 parent of node [node name] ∑w1(s,node),∑w2(s,node)


###### s


######,,
 1 4 7


![](VLSI-design-chap5.pdf-75-0.png)

###### 2


![](VLSI-design-chap5.pdf-75-1.png)

###### 3


![](VLSI-design-chap5.pdf-75-2.png)

###### 8


###### 1


###### 7


-----

###### Group 2 Group 3

 N (2) 8,6
 (1)
 W (4) 1,4

 N (5) 10,11 W (4) 1,4
 W (7) 9,12

 N (3) 9,10 N (2) 8,6
 W (5) 10,12

 W (6) 18,18 N (3) 9,10

 N (6) 12,19
 N (5) 10,11
 W (8) 12,19

 N (8) 12,14 W (7) 9,12

 N (8) 12,14

 t f d [ d ] ∑ ( d ) ∑ ( d )


###### s


######,,
 1 4 7


![](VLSI-design-chap5.pdf-76-0.png)

###### 2


![](VLSI-design-chap5.pdf-76-1.png)

###### 3


![](VLSI-design-chap5.pdf-76-2.png)

###### 8


###### 1


###### 7


-----

###### s


######,,
 1 4 7


###### Group 2 Group 3


###### 1


###### 7


###### s 1


###### N (2) 8,6

 W (4) 1,4


###### 4


###### (1)


###### t


![](VLSI-design-chap5.pdf-77-0.png)

###### 2


![](VLSI-design-chap5.pdf-77-1.png)

###### 3


![](VLSI-design-chap5.pdf-77-2.png)

###### 8


###### Retrace from t to s


![](VLSI-design-chap5.pdf-77-0.png)

###### 5


![](VLSI-design-chap5.pdf-77-1.png)

###### 9


###### 8)


###### 8)


-----

###### s


######,,
 1 4 7


###### 1


###### 4


###### 12,14

 t


![](VLSI-design-chap5.pdf-78-0.png)

###### 2


![](VLSI-design-chap5.pdf-78-1.png)

###### 8


![](VLSI-design-chap5.pdf-78-2.png)

###### 6


###### 7


###### Optimal path 1-4-7-8 from s to t with accumulated cost (12,14)


![](VLSI-design-chap5.pdf-78-0.png)

###### 5


![](VLSI-design-chap5.pdf-78-1.png)

###### 9


-----

###### • A* search operates similarly to Dijkstra’s algorithm, but extends the cost function to include an estimated distance from the current node to the target

 • Expands only the most promising nodes; its best-first search strategy eliminates a large portion of the solution space


###### t 22 13 O 11 20 t


###### t


###### s


###### 31 O


###### t


###### s 2 7 6 O 2 s

|Col1|Col2|Col3|30|21|29|19|28|
|---|---|---|---|---|---|---|---|
|||t|22|13|O|11|20|
||||O|6|1|5|12|
||||O|4|s|2|7|
|||27|18|10|3|8|14|
||||26|17|9|15|23|
|||||25|16|24||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||t|5|4|O|||
||||O|3|1|||
||||O|2|s|||
|||||||||
|||||||||
|||||||||


###### s


###### t


###### Dijkstra‘s algorithm
 (exploring 31 nodes)


###### A* search
 (exploring 6 nodes)


###### s


-----

###### • Bidirectional A* search: nodes are expanded from both the source and target until the two expansion regions intersect

 • Number of nodes considered can be reduced 


###### t 5 4 O t 3 6 O
 O 3 1 4 O 5 1


###### t


###### s


###### t


###### s O 2 s

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||t|5|4|O|||
|||O|3|1|||
|||O|2|s|||
||||||||
||||||||
||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||t|3|6|O|||
||4|O|5|1|||
|||O|2|s|||
||||||||
||||||||
||||||||


###### s


###### t


###### Unidirectional A* search


###### Bidirectional A* search


###### s


-----

###### 5.1 Introduction

 5.2 Terminology and Definitions


###### 5.3 Optimization Goals

 5.4 Representations of Routing Regions


###### 5.5 The Global Routing Flow

 5.6 Single-Net Routing


###### 5.6.1 Rectilinear Routing 5.6.2 Global Routing in a Connectivity Graph 5.6.3 Finding Shortest Paths with Dijkstra’s Algorithm 5.6.4 Finding Shortest Paths with A* Search


###### 5.7 Full-Netlist Routing
 5.7.1 Routing by Integer Linear Programming 5.7.2 Rip-Up and Reroute (RRR)


###### 5.8 Modern Global Routing
 5.8.1 Pattern Routing 5.8.2 Negotiated-Congestion Routing


-----

###### • Global routers must properly match nets with routing resources, without oversubscribing resources in any part of the chip

 • Signal nets are either routed


###### − simultaneously, e.g., by integer linear programming, or


###### − sequentially, e.g., one net at a time

 • When certain nets cause resource contention or overflow for routing edges, sequential routing requires multiple iterations: rip-up and reroute


-----

###### • A linear program (LP) consists
 − of a set of constraints and


###### − an optional objective function

 • Objective function is maximized or minimized



###### • Both the constraints and the objective function must be linear
 − Constraints form a system of linear equations and inequalities



###### • Integer linear program (ILP): linear program where every variable can only assume integer values
 − Typically takes much longer to solve


###### − In many cases, variables are only allowed values 0 and 1

 • Several ways to formulate the global routing problem as an ILP, one of which is presented next


-----

###### • Three inputs
 − W × H routing grid G,


###### − Routing edge capacities, and
 − Netlist



###### • Two sets of variables
 − k Boolean variables xnet1, xnet2, …, xnetk, each of which serves as an indicator for one of k specific paths or route options, for each net net ∈ Netlist


###### − k real variables wnet1, wnet2, …, wnetk, each of which represents a net weight for a specific route option for net ∈ Netlist



###### • Two types of constraints
 − Each net must select a single route (mutual exclusion)


###### − Number of routes assigned to each edge (total usage) cannot exceed its capacity 


-----

###### • Inputs
 − W,H: width W and height H of routing grid G


###### − G(i,j): grid cell at location (i,j) in routing grid G
 − σ(G(i,j)~G(i + 1,j)): capacity of horizontal edge G(i,j) ~ G(i + 1,j)


###### − σ(G(i,j)~G(i,j + 1)): capacity of vertical edge G(i,j) ~ G(i,j + 1)
 − Netlist: netlist



###### • Variables
 − xnet1, ..., xnetk: k Boolean path variables for each net net ∈ Netlist


###### − wnet1, ..., wnetk: k net weights, one for each path of net net ∈ Netlist



###### • Maximize

 • Subject to


###### w ⋅ x +  + w ⋅ x

### ∑ net1 net1 netk netk

###### net∈Netlist


###### − Variable ranges
 − Net constraints


###### − Capacity constraints


-----

###### Global Routing Using Integer Linear Programming

 • Given


###### − Nets A, B
 − W = 5 × H = 4 routing grid G


###### − σ(e) = 1 for all e ∈ G
 − L-shapes have weight 1.00 and Z-shapes have weight 0.99


###### − The lower-left corner is (0,0).



###### • Task
 − Write the ILP to route the nets in the graph below


###### A B

 C B

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|A||||
|||C||
|||A||


![](VLSI-design-chap5.pdf-86-0.png)

###### A

 C

 A


-----

###### • Solution
 − For net A, the possible routes are two L-shapes (A1,A2) and two Z-shapes (A3,A4)


###### A1 A


###### Net Constraints: xA1 + xA2 + xA3 + xA4 ≤ 1 Variable Constraints: 0 ≤ xA1 ≤ 1, 0 ≤ xA2 ≤ 1, 0 ≤ xA3 ≤ 1, 0 ≤ xA4 ≤ 1

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|A||A 1||
|A 2||||
|||A||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|A||A 3|||||
|||||A 4|||
||||A||||


###### − For net B, the possible routes are two L-shapes (B1,B2) and one Z-shape (B3)

 Net Constraints: xB1 + xB2 + xB3 ≤ 1
 B2 Variable Constraints:
 0 ≤ xB1 ≤ 1, 0 ≤ xB2 ≤ 1,
 B1 B B3 B 0 ≤ xB3 ≤ 1
 B B
 − For net C, the possible routes are two L-shapes (C1,C2) and two Z-shapes (C3,C4)

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||B 2||
||||B 1|

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||B 3||


###### C2 C C


###### Net Constraints: xC1 + xC2+ xC3 + xC4 ≤ 1 Variable Constraints: 0 ≤ xC1 ≤ 1, 0 ≤ xC2 ≤ 1, 0 ≤ xC3 ≤ 1, 0 ≤ xC4 ≤ 1

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|||||
|C 2||C||
||C 1|||

|Col1|Col2|Col3|Col4|
|---|---|---|---|
||C 3|||
|||C||
|C 4||||


-----

###### Horizontal Edge Capacity Constraints:
 G(0,0) ~ G(1,0): xC1 + xC3 ≤ σ(G(0,0) ~ G(1,0)) = 1
 G(1,0) ~ G(2,0): xC1 ≤ σ(G(1,0) ~ G(2,0)) = 1
 G(2,0) ~ G(3,0): xB1 + xB3 ≤ σ(G(2,0) ~ G(3,0)) = 1
 G(3,0) ~ G(4,0): xB1 ≤ σ(G(3,0) ~ G(4,0)) = 1
 G(0,1) ~ G(1,1): xA2 + xC4 ≤ σ(G(0,1) ~ G(1,1)) = 1
 G(1,1) ~ G(2,1): xA2 + xA3 + xC4 ≤ σ(G(1,1) ~ G(2,1)) = 1
 G(2,1) ~ G(3,1): xB2 ≤ σ(G(2,1) ~ G(3,1)) = 1
 G(3,1) ~ G(4,1): xB2 + xB3 ≤ σ(G(3,1) ~ G(4,1)) = 1
 G(0,2) ~ G(1,2): xA4 + xC2 ≤ σ(G(0,2) ~ G(1,2)) = 1
 G(1,2) ~ G(2,2): xA4 + xC2 + xC3 ≤ σ(G(1,2) ~ G(2,2)) = 1
 G(0,3) ~ G(1,3): xA1 + xA3 ≤ σ(G(0,3) ~ G(1,3)) = 1
 G(1,3) ~ G(2,3): xA1 ≤ σ(G(1,3) ~ G(2,3)) = 1


###### Vertical Edge Capacity Constraints:
 G(0,0) ~ G(0,1): xC2 + xC4 ≤ σ(G(0,0) ~ G(0,1)) = 1
 G(1,0) ~ G(1,1): xC3 ≤ σ(G(1,0) ~ G(1,1)) = 1
 G(2,0) ~ G(2,1): xB2 + xC1 ≤ σ(G(2,0) ~ G(2,1)) = 1
 G(3,0) ~ G(3,1): xB3 ≤ σ(G(3,0) ~ G(3,1)) = 1
 G(4,0) ~ G(4,1): xB1 ≤ σ(G(4,0) ~ G(4,1)) = 1
 G(0,1) ~ G(0,2): xA2 + xC2 ≤ σ(G(0,1) ~ G(0,2)) = 1
 G(1,1) ~ G(1,2): xA3 + xC3 ≤ σ(G(1,1) ~ G(1,2)) = 1
 G(2,1) ~ G(2,2): xA1 + xA4 + xC1 + xC4 ≤ σ(G(2,1) ~ G(2,2)) = 1
 G(0,2) ~ G(0,3): xA2 + xA4 ≤ σ(G(0,2) ~ G(0,3)) = 1


-----

###### • Rip-up and reroute (RRR) framework: focuses on hard-to-route nets

 • Idea: allow temporary violations, so that all nets are routed, but then iteratively remove some nets (rip-up), and route them differently (reroute)


###### A’


###### Routing without allowing violations

 B
 D’

 A
 B’
 D C
 C’

 WL = 21

|Col1|Col2|Col3|B|Col5|Col6|
|---|---|---|---|---|---|
||||D’|||
|||||A||
||||B’|||
|D|C||||C’|
|||||||

|Col1|Col2|Col3|B|Col5|Col6|
|---|---|---|---|---|---|
||||D’|||
|||||A||
||||B’|||
|D|C||||C’|
|||||||

|Col1|Col2|Col3|B|Col5|Col6|
|---|---|---|---|---|---|
||||D’|||
|||||A||
||||B’|||
|D|C||||C’|
|||||||


###### WL = 19


###### C C’


###### Routing with allowing violations and RRR

 B
 A’


###### A’


-----

###### 5.1 Introduction

 5.2 Terminology and Definitions


###### 5.3 Optimization Goals

 5.4 Representations of Routing Regions


###### 5.5 The Global Routing Flow

 5.6 Single-Net Routing


###### 5.6.1 Rectilinear Routing 5.6.2 Global Routing in a Connectivity Graph 5.6.3 Finding Shortest Paths with Dijkstra’s Algorithm 5.6.4 Finding Shortest Paths with A* Search


###### 5.7 Full-Netlist Routing
 5.7.1 Routing by Integer Linear Programming 5.7.2 Rip-Up and Reroute (RRR)


###### 5.8 Modern Global Routing
 5.8.1 Pattern Routing 5.8.2 Negotiated-Congestion Routing


-----

###### • General flow for modern global routers, where each router uses a unique set of optimizations:

|Global Routing Instance|Col2|
|---|---|
|||


-----

###### • Pattern Routing

 − Searches through a small number of route patterns to improve runtime


###### − Topologies commonly used in pattern routing: L-shapes, Z-shapes, U-shapes


###### Detour-Up Vertical U-Shape


###### Detour- Left Horizontal U-Shape


###### Up-Right L-Shape


###### Right-Up L-Shape


###### Up-Right- Up Z-Shape


###### Right-Up- Right Z-Shape


###### Detour- Down Vertical U-Shape


###### Detour- Right Horizontal U-Shape


-----

###### • Negotiated-Congestion Routing

 − Each edge e is assigned a cost value cost(e) that reflects the demand for edge e


###### − A segment from net net that is routed through e pays a cost of cost(e)

 − Total cost of net is the sum of cost(e) values taken over all edges used by net:


###### cost(net) = cost(e)

#### ∑

###### e∈net


###### − The edge cost cost(e) is increased according to the edge congestion φ(e), defined as the total number of nets passing through e divided by the capacity of e:
 η(e) φ(e) = σ(e)


###### − A higher cost(e) value discourages nets from using e and implicitly encourages nets to seek out other, less used edges

 ⇒ Iterative routing approaches (Dijkstra’s algorithm, A* search, etc.) find routes with minimum cost while respecting edge capacities


-----

###### Global Routing



###### • Input: netlist, placement, obstacles + (usually) routing grid

 • Partitions the routing region (chip or block) into global routing cells (gcells)



###### • Considers the locations of cells within a region as identical

 • Plans routes as sequences of gcells



###### • Minimizes total length of routes and, possibly, routed congestion

 • May fail if routing resources are insufficient


###### − Variable-die can expand the routing area, so can't usually fail

 − Fixed-die is more common today (cannot resize a block in a larger chip)



###### • Interpreting failures in global routing

 − Failure with many violations => must restructure the netlist and/or redo global placement


###### − Failure with few violations => detailed routing may be able to fix the problems


-----

###### Detailed Routing



###### • Input: netlist, placement, obstacles, global routes (on a routing grid), routing tracks, design rules

 • Seeks to implement each global route as a sequence of track segments



###### • Includes layer assignment (unless that is performed during global routing)

 • Minimizes total length of routes, subject to design rules


###### Timing-Driven routing



###### • Minimizes circuit delay by optimizing timing-critical nets

 • Usually needs to trade off route length and congestion against timing



###### • Both global and detailed routing can be timing-driven


-----

###### Large-Net Routing



###### • Nets with many pins can be so complex that routing a single net warrants dedicated algorithms

 • Steiner tree construction


###### − Minimum wirelength, extensions for obstacle-avoidance


###### − Nonuniform routing costs to model congestion

 • Large signal nets are routed as part of global routing and then split into smaller segments processed during detailed routing


###### Clock Tree Routing / Power Routing



###### • Performed before global routing to avoid competition for resources occupied by signal nets


-----

###### • Usually ~50% of the nets are two-pin nets, ~25% have three pins, ~12.5% have four, etc.

 − Two-pin nets can be routed as L-shapes or using maze search (in a connectivity graph of the routing regions)


###### − Three-pin nets usually have 0 or 1 branching point

 − Larger nets are more difficult to handle



###### • Pattern routing

 − For each net, considers only a small number of shapes (L, Z, U, T, E)


###### − Very fast, but misses many opportunities

 − Good for initial routing, sometimes is sufficient



###### • Routing pin-to-pin connections

 − Breadth-first-search (when costs are uniform)


###### − Dijkstra's algorithm (non-uniform costs)

 − A*-search (non-uniform costs and/or using additional distance information)


-----

###### • Minimum Spanning Trees and Steiner Minimal Trees in the rectilinear topology (RMSTs and RSMTs)

 − RMSTs can be constructed in near-linear time


###### − Constructing RSMTs is NP-hard, but feasible in practice

 • Each edge of an RMST or RSMT can be considered a pin-to-pin connection and routed accordingly



###### • Routing congestion introduces non-uniform costs, complicates the construction of minimal trees (which is why A*-search still must be used)

 • For nets with <10 pins, RSMTs can be found using look-up tables (FLUTE) very quickly


-----

###### • Routing by Integer Linear Programming (ILP)

 − Capture the route of each net by 0-1 variables, form equations constraining those variables


###### − The objective function can represent total route length

 − Solve the equations while minimizing the objective function (ILP software)

 − Usually a convenient but slow technique, may not scale to largest netlists (can be extended by area partitioning)



###### • Rip-up and Re-route (RRR) 

 − Processes one net at a time, usually by A*-search and Steiner-tree heuristics


###### − Allows temporary overlaps between nets

 − When every net is routed (with overlaps), it removes (rips up) those with overlaps and routes them again with penalty for overlaps


###### − This process may not finish, but often does, else use a time-out



###### • Both ILP-based routing and RRR can be applied in global and detailed routing

 − ILP-based routing is usually preferable for small, difficult-to-route regions


-----

###### • Initial routes are constructed quickly by pattern routing and the FLUTE package for Steiner tree construction - very fast

 • Several iterations based on modified pattern routing to avoid congestion
 - also very fast


###### − Sometimes completes all routes without violations

 − If violations remain, they are limited to a few congested spots



###### • The main part of the router is based on a variant of RRR called Negotiated-Congestion Routing (NCR)

 − Several proposed alternatives are not competitive



###### • NCR maintains "history" in terms of which regions attracted too many nets

 • NCR increases routing cost according to the historical popularity of the regions


###### − The nets with alternative routes are forced to take those routes

 − The nets that do not have good alternatives remain unchanged

 − Speed of increase controls tradeoff between runtime and route quality


-----

