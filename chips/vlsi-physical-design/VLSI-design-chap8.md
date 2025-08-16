![](VLSI-design-chap8.pdf-0-0.png)

-----

###### 8.1 Introduction

 8.2 Timing Analysis and Performance Constraints 8.2.1 Static Timing Analysis 8.2.2 Delay Budgeting with the Zero-Slack Algorithm


###### 8.3 Timing-Driven Placement
 8.3.1 Net-Based Techniques 8.3.2 Embedding STA into Linear Programs for Placement


###### 8.4 Timing-Driven Routing
 8.4.1 The Bounded-Radius, Bounded-Cost Algorithm 8.4.2 Prim-Dijkstra Tradeoff 8.4.3 Minimization of Source-to-Sink Delay


###### 8.5 Physical Synthesis
 8.5.1 Gate Sizing 8.5.2 Buffering 8.5.3 Netlist Restructuring


###### 8.6 Performance-Driven Design Flow

 8 7 Conclusions


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

###### • IC layout must satisfy geometric constraints, electrical constraints, power & thermal constraints as well as timing constraints

 − Setup (long-path) constraints


###### − Hold (short-path) constraints



###### • Chip designers must complete timing closure

 − Optimization process that meets timing constraints


###### − Integrates point optimizations discussed in previous chapters, e.g., placement and routing, with specialized methods to improve circuit performance 


-----

###### Components of timing closure covered in this lecture:

 • Timing-driven placement (Sec. 8.3) minimizes signal delays when assigning locations to circuit elements



###### • Timing-driven routing (Sec. 8.4) minimizes signal delays when selecting routing topologies and specific routes

 • Physical synthesis (Sec. 8.5) improves timing by changing the netlist


###### − Sizing transistors or gates: increasing the width:length ratio of transistors to decrease the delay or increase the drive strength of a gate

 − Inserting buffers into nets to decrease propagation delays


###### − Restructuring the circuit along its critical paths

 • Performance-driven physical design flow (Sec. 8.6)


-----

###### • Timing optimization engines must estimate circuit delays quickly and accurately to improve circuit timing

 • Timing optimizers adjust propagation delays through circuit components, with the primary goal of satisfying timing constraints, including


###### − Setup (long-path) constraints, which specify the amount of time a data input signal should be stable (steady) before the clock edge for each storage element (e.g., flip-flop or latch)

 − Hold-time (short-path) constraints, which specify the amount of time a data input signal should be stable after the clock edge at each storage element


###### t ≥ t + t + t t ≥ t + t cycle combDelay setup skew combDelay hold skew


-----

###### • Timing closure is the process of satisfying timing constraints through layout optimizations and netlist modifications

 • Industry jargon: “the design has closed timing”


-----

###### 8.1 Introduction

 8.2 Timing Analysis and Performance Constraints 8.2.1 Static Timing Analysis 8.2.2 Delay Budgeting with the Zero-Slack Algorithm


###### 8.3 Timing-Driven Placement
 8.3.1 Net-Based Techniques 8.3.2 Embedding STA into Linear Programs for Placement


###### 8.4 Timing-Driven Routing
 8.4.1 The Bounded-Radius, Bounded-Cost Algorithm 8.4.2 Prim-Dijkstra Tradeoff 8.4.3 Minimization of Source-to-Sink Delay


###### 8.5 Physical Synthesis
 8.5.1 Gate Sizing 8.5.2 Buffering 8.5.3 Netlist Restructuring


###### 8.6 Performance-Driven Design Flow

 8 7 Conclusions


-----

###### Sequential circuit, “unrolled” in time

 Combinational Combinational Logic FF Logic

 Copy 1 Copy 2

 Clock

 Storage elements Combinational logic


-----

###### • Main delay concerns in sequential circuits

 − Gate delays are due to gate transitions


###### − Wire delays are due to signal propagation along wires

 − Clock skew is due to the difference in time the sequential elements activate



###### • Need to quickly estimate sequential circuit timing

 − Perform static timing analysis (STA)


###### − Assume clock skew is negligible, postpone until after clock network synthesis


-----

###### • STA: assume worst-case scenario where every gate transitions

 • Given combinational circuit, represent as directed acyclic graph (DAG)


###### − Every edge (node) has weight = wire (gate) delay



###### • Compute the slack = RAT – AAT for each node

 − RAT is the required arrival time, latest time signal can transition


###### − AAT is the actual arrival time


###### − By convention, AAT is defined at the output of every node

 ⇒ Negative slack at any output means the circuit does not meet timing


###### ⇒ Positive slack at all outputs means the circuit meets timing


-----

###### Combinational circuit as DAG


###### (0.2)


###### a

 b


###### (0.15)


###### (0.2)


###### f

|s DAG|Col2|Col3|
|---|---|---|
|||y (2)|
||||
||||


###### c


###### (0.25)
 (0.1) x (1) (0.3)
 z (2)
 (0.1)

|Col1|(0.1)|Col3|
|---|---|---|
||x (1)||
||||
||||


![](VLSI-design-chap8.pdf-11-1.png)

###### (0.15)


![](VLSI-design-chap8.pdf-11-0.png)

![](VLSI-design-chap8.pdf-11-1.png)

###### y (2)


![](VLSI-design-chap8.pdf-11-3.png)

###### a (0)


###### (0)


###### (0.1) (0.2)


###### (0) b (0) (0.1) x (1) w (2) (0.2) f (0)


![](VLSI-design-chap8.pdf-11-0.png)

###### x (1)


![](VLSI-design-chap8.pdf-11-1.png)

###### f (0)


###### s


###### (0.3) (0.6)


![](VLSI-design-chap8.pdf-11-0.png)

###### w (2)


###### (0.25)


![](VLSI-design-chap8.pdf-11-0.png)

###### b (0)


###### c (0)


###### (0 1)


###### z (2)


###### z (2)


-----

###### Compute AATs at each node:

 AAT (v) = max (AAT (u) + t(u, v)) u∈FI (v)


###### where FI(v) is the fanin nodes, and t(u,v) is the delay between u and v

 (AATs of inputs are given)


###### (0.15)


![](VLSI-design-chap8.pdf-12-1.png)

###### y (2)


![](VLSI-design-chap8.pdf-12-4.png)

###### a (0)


###### A 0


###### A 3.2
 (0.1) (0.2)


###### (0)


###### (0) b (0) (0.1) x (1) w (2) (0.2) f (0)


![](VLSI-design-chap8.pdf-12-0.png)

###### x (1)


![](VLSI-design-chap8.pdf-12-1.png)

###### w (2)


![](VLSI-design-chap8.pdf-12-2.png)

###### b (0)


###### s


###### A 0 A 0 A 1.1 A 5.65 A 5.85
 (0.6) (0.3) (0.25)

 c (0) (0.1) z (2)


![](VLSI-design-chap8.pdf-12-0.png)

###### z (2)


![](VLSI-design-chap8.pdf-12-1.png)

###### c (0)


###### A 0.6


![](VLSI-design-chap8.pdf-12-0.png)

###### f (0)


###### A 3.4


-----

###### Compute RATs at each node:

 RAT (v) = min (RAT (u) − t(u, v)) u∈FO(v)


###### where FO(v) are the fanout nodes, and t(u,v) is the delay between u and v

 (RATs of outputs are given)


###### (0.15)


![](VLSI-design-chap8.pdf-13-1.png)

###### y (2)


![](VLSI-design-chap8.pdf-13-4.png)

###### a (0)


###### R 0.95


###### R 3.1
 (0.1) (0.2)


###### (0)


###### (0) b (0) (0.1) x (1) w (2) (0.2) f (0)


![](VLSI-design-chap8.pdf-13-0.png)

###### x (1)


![](VLSI-design-chap8.pdf-13-1.png)

###### w (2)


![](VLSI-design-chap8.pdf-13-2.png)

###### b (0)


###### s


###### R -0.35


![](VLSI-design-chap8.pdf-13-1.png)

###### f (0)


###### R -0.35 R 0.75 R 5.3
 (0.6) (0.3) (0.25)

 c (0) (0.1) z (2)


###### R 5.5


###### R 0.95


###### R 3.05


![](VLSI-design-chap8.pdf-13-0.png)

###### z (2)


-----

###### Compute slacks at each node:

 slack(v) = RAT (v) − AAT (v)


###### (0.15)


![](VLSI-design-chap8.pdf-14-2.png)

###### y (2)


![](VLSI-design-chap8.pdf-14-5.png)

###### a (0)


###### A 3.2 R 3.1
 (0.1) (0.2)
 S -0.1


###### (0)


###### A 0 R 0.95 S 0.95


###### (0) b (0) (0.1) x (1) w (2) (0.2) f (0)


![](VLSI-design-chap8.pdf-14-0.png)

###### b (0)


![](VLSI-design-chap8.pdf-14-2.png)

###### w (2)


###### s


###### A 0 R -0.35 S -0.35


![](VLSI-design-chap8.pdf-14-0.png)

###### x (1)


![](VLSI-design-chap8.pdf-14-1.png)

###### f (0)


###### A 0 A 1.1 R -0.35 R 0.75 (0.3)
 (0.6)
 S -0.35 S -0.35

 c (0) (0.1)


###### A 5.85 R 5.5 S -0.35


###### (0.25)


###### A 5.65 R 5.3 S -0.35


![](VLSI-design-chap8.pdf-14-0.png)

###### z (2)


###### A 0.6 R 0.95


![](VLSI-design-chap8.pdf-14-0.png)

###### c (0)


###### A 3.4 R 3.05


-----

###### • Establish timing budgets for nets

 − Gate and wire delays must be optimized during timing driven layout design


###### − Wire delays depend on wire lengths

 − Wire lengths are not known until after placement and routing



###### • Delay budgeting with the zero-slack algorithm

 − Let vi be the logic gates


###### − Let ei be the nets

 − Let DELAY(v) and DELAY(e) be the delay of the gate and net, respectively


###### − Timing budget TB(v) of a gate corresponds to DELAY(v) + DELAY(e)


-----

###### Input: timing graph G(V,E)

 Output: timing budgets TB for each v ∈ V


###### 1. do

 2. (AAT,RAT,slack) = STA(G)


###### 3. foreach (v V)
_i ∈_

###### 4. TB[v ] = DELAY(v ) + DELAY(e )
_i_ _i_ _i_


###### 5. slack
_min = ∞_

###### 6. foreach (v ∈ V)


###### 7. if ((slack[v] < slack ) and (slack[v] > 0))
_min_

###### 8. slack [v]
_min = slack_


###### 9. v
_min = v_

###### 10. if (slack
_min ≠∞)_

###### 11. path = v
_min_


###### 12. ADD_TO_FRONT(path,BACKWARD_PATH(v,G))
_min_

###### 13. ADD_TO_BACK(path,FORWARD_PATH(v,G))
_min_


###### 14. s = slack path|
_min / |_

###### 15. for (i = 1 to |path|)

 16. node = path[i] // evenly distribute

 17. TB[node] = TB[node] + s // slack along path


-----

###### Forward Path Search (FORWARD_PATH(v,G))
**_min_**

###### Input: node v slack, timing graph G
_min with minimum slack_ _min_


###### Output: maximal downstream path path from v v ∈ V affects
_min such that no node_
###### the slack of path

 1. path = v
_min_


###### 2. do

 3. flag = false


###### 4. node = LAST_ELEMENT(path)

 5. foreach (fanout node fo of node)


###### 6. if ((RAT[fo] == RAT[node] + TB[fo]) and (AAT[fo] == AAT[node] + TB[fo]))

 7. ADD_TO_BACK(path,fo)


###### 8. flag = true

 9. break


###### 10. while (flag == true)

 11. REMOVE_FIRST_ELEMENT(path) // remove v
_min_


-----

###### Backward Path Search (BACKWARD_PATH(v,G))
**_min_**

###### Input: node v slack, timing graph G
_min with minimum slack_ _min_


###### Output: maximal upstream path path from v v ∈ V affects the
_min such that no node_
###### slack of path

 1. path = v
_min_


###### 2. do

 3. flag = false


###### 4. node = FIRST_ELEMENT(path)

 5. foreach (fanin node fi of node)


###### 6. if ((RAT[fi] == RAT[node] – TB[fi]) and (AAT[fi] == AAT[node] – TB[fi]))

 7. ADD_TO_FRONT(path,fi)


###### 8. flag = true

 9. break


###### 10. while (flag == true)

 11. REMOVE_LAST_ELEMENT(path) // remove v
_min_


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]


###### I1 I2

 I3


###### <13,4,17> [0]


###### I4


###### <3 5 8> [0]


###### O1

 O2


###### <6,5,11> [0]


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]



###### • Find the path with the minimum nonzero slack


###### I1 I2

 I3


###### <13,4,17> [0]


###### I4


###### <3 5 8> [0]


###### O1

 O2


###### <6,5,11> [0]


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]



###### • Find the path with the minimum slack

 • Distribute the slacks and update the timing budgets


###### I1 I2

 I3


###### <16,0,16> [1]


###### I4


###### <3 4 7> [0]


###### O1

 O2


###### <6,4,10> [0]


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]



###### • Find the path with the minimum slack

 • Distribute the slacks and update the timing budgets


###### I1 I2

 I3


###### <16,0,16> [1]


###### I4


###### <3 4 7> [0]


###### O1

 O2


###### <6,4,10> [0]


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]



###### • Find the path with the minimum slack

 • Distribute the slacks and update the timing budgets


###### I1 I2

 I3


###### <16,0,16> [1]


###### I4


###### <3 2 5> [0]


###### O1

 O2


###### <6,2,8> [2]


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]



###### • Find the path with the minimum slack

 • Distribute the slacks and update the timing budgets


###### I1 I2

 I3


###### <16,0,16> [1]


###### I4


###### <3 1 4> [0]


###### O1

 O2


###### <7,0,7> [3]


-----

###### • Example: Use the zero-slack algorithm to distribute slack

 • Format: <AAT, Slack, RAT>, [timing budget]



###### • Find the path with the minimum slack

 • Distribute the slacks and update the timing budgets


###### I1 I2

 I3


###### <16,0,16> [1]


###### I4


###### <3 0 3> [1]


###### O1

 O2


###### <7,0,7> [3]


-----

###### 8.1 Introduction

 8.2 Timing Analysis and Performance Constraints 8.2.1 Static Timing Analysis 8.2.2 Delay Budgeting with the Zero-Slack Algorithm


###### 8.3 Timing-Driven Placement
 8.3.1 Net-Based Techniques 8.3.2 Embedding STA into Linear Programs for Placement


###### 8.4 Timing-Driven Routing
 8.4.1 The Bounded-Radius, Bounded-Cost Algorithm 8.4.2 Prim-Dijkstra Tradeoff 8.4.3 Minimization of Source-to-Sink Delay


###### 8.5 Physical Synthesis
 8.5.1 Gate Sizing 8.5.2 Buffering 8.5.3 Netlist Restructuring


###### 8.6 Performance-Driven Design Flow

 8 7 Conclusions


-----

###### • Timing-driven placement optimizes circuit delay
 to satisfy timing constraints



###### • Let T be the set of all timing endpoints

 • Constraint satisfaction is measured by worst negative slack (WNS)


###### WNS = min(slack)τ() τ∈Τ

 • Or total negative slack (TNS)
 TNS = slack )τ(

## ∑

τ∈Τ,slack ()τ<0



###### • Classifications: net-based, path-based, integrated


-----

###### • Net weights are added to each net – placer optimizes weighted wirelength

 • Static net weights: computed before placement (never changes)


###### ω1 if slack > 0
 − Discrete net weights: w =  where ω1 > 0, ω2 > 0, and ω2 > ω1
 ω if slack ≤ 0
  2

 α slack 
 − Continuous net weights: w = −1  where t is the longest path delay
  t  and α is a criticality exponent


###### − Based on net sensitivity to TNS and slack

 SLACK TNS w = w + α(slack − slack) ⋅ s + β ⋅ s o target w w


-----

###### • Dynamic net weights: (re)computed during placement


###### − Estimate slack at every iteration:


###### DELAY slack = slack − s ⋅ ∆L k k −1 L

 where ΔL is the change in wirelength


###### − Update net criticality:


###### υ


###### k


###### 1

#### (υ +1)

######  k −1
 2
 =
 
 1
  υ
 k −1
  2


###### if among the top 3% of critical nets

 otherwise


###### − Update net weight:


###### w = w ⋅(1+ υ ) k k −1 k



###### • Variations include updating every j iterations, different relations between criticality and net weight


-----

###### • Construct a set of constraints for timing-driven placement

 − Physical constraints define locations of cells


###### − Timing constraints define slack requirements



###### • Optimize an optimization objective

 − Improving worst negative slack (WNS)


###### − Improving total negative slack (TNS)

 − Improving a combination of both WNS and TNS


-----

###### • For physical constraints, let:

 − xv and yv be the center of cell v ∈ V


###### − Ve be the set of cells connected to net e ∈ E

 − left(e), right(e), bottom(e), and top(e) respectively be the coordinates of the left, right, bottom, and top boundaries of e’s bounding box


###### − δx(v,e) and δy(v,e) be pin offsets from xv and yv for v’s pin connected to e


-----

###### • Then, for all v ∈ Ve:


###### left(e) ≤ x + δ (v, e)
 v x


###### right (e) ≥ x + δ (v, e)
 v x
 bottom(e) ≤ y + δ (v, e)
 v y


###### top(e) ≥ y + δ (v, e)
 v y

 • Define e’s half-perimeter wirelength (HPWL):


###### L(e) = right(e) − left(e) + top(e) − bottom(e)


-----

###### • For timing constraints, let

 − tGATE(vi,vo) be the gate delay from an input pin vi to the output pin vo for cell v


###### − tNET(e,uo,vi) be net e’s delay from cell u’s output pin uo to cell v’s input pin vi

 − AAT(vj) be the arrival time on pin j of cell v


-----

###### • For every input pin vi of cell v :

 AAT (v ) = AAT (u ) + t (u, v ) i o NET o i



###### • For every output pin vo of cell v :

 AAT (v ) ≥ AAT (v ) + t (v, v ) o i GATE i o



###### • For every pin τp in a sequential cell τ:

 slackτ( ) ≤ RAT τ( ) − AAT τ( ) p p p



###### • Ensure that every slack(τp) ≤ 0


-----

###### • Optimize for total negative slack:

 max : slackτ( )

_p_

## ∑
τ _p_ ∈Pins(τ),τ∈Τ



###### • Optimize for worst negative slack:

 max :WNS



###### • Optimize а linear combination of multiple parameters:

 min : L(e) − α ⋅WNS

## ∑

_e∈E_


-----

###### 8.1 Introduction

 8.2 Timing Analysis and Performance Constraints 8.2.1 Static Timing Analysis 8.2.2 Delay Budgeting with the Zero-Slack Algorithm


###### 8.3 Timing-Driven Placement
 8.3.1 Net-Based Techniques 8.3.2 Embedding STA into Linear Programs for Placement


###### 8.4 Timing-Driven Routing
 8.4.1 The Bounded-Radius, Bounded-Cost Algorithm 8.4.2 Prim-Dijkstra Tradeoff 8.4.3 Minimization of Source-to-Sink Delay


###### 8.5 Physical Synthesis
 8.5.1 Gate Sizing 8.5.2 Buffering 8.5.3 Netlist Restructuring


###### 8.6 Performance-Driven Design Flow

 8 7 Conclusions


-----

###### • Timing-driven routing seeks to minimize:

 − Maximum sink delay: delay from the source to any sink in a net


###### − Total wirelength: routed length of the net



###### • For a signal net net, let

 − s0 be the source node


###### − sinks = {s1, …,sn} be the sinks

 − G = (V,E) be a corresponding weighted graph where:


###### − V = {v0,v1, …,vn} represents the source and sink nodes of net, and

 − the weight of an edge e(vi,vj) ∈ E represents the routing cost between vi and vj


-----

###### • For any spanning tree T over G, let:

 − radius(T) be the length of the longest source-sink path in T


###### − cost(T) be the total edge weight of T

 • Trade off between “shallow” and “light” trees



###### • “Shallow” trees have minimum radius

 − Shortest-paths tree


###### − Constructed by Dijkstra’s Algorithm



###### • “Light” trees have minimum cost

 − Minimum spanning tree (MST)


###### − Constructed by Prim’s Algorithm


-----

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
||2|||||
|||||||
||||6|||
||||||7|
||5|||||
||||s 0|||

|Col1|2|Col3|Col4|3|Col6|
|---|---|---|---|---|---|
|||||||
||3|||||
|||||||
|||||||
||5|||||
||||s 0|||

|Col1|Col2|2|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
||3|||||
||||6|||
|||||||
||5|||||
||||s 0|||


![](VLSI-design-chap8.pdf-39-0.png)

###### 2 3

 3

 5

 s
0


![](VLSI-design-chap8.pdf-39-1.png)

###### 2

 3

 6

 5

 s
0


###### radius(T) = 8
 cost(T) = 20

 “Shallow”


![](VLSI-design-chap8.pdf-39-0.png)

###### 2

 6
 7

 5

 s
0


###### radius(T) = 13
 cost(T) = 13


###### “Light”


###### cost(T) = 16

 Tradeoff between shallow and light


###### radius(T) = 11


-----

###### • Trades off radius for cost by setting upper bounds on both

 • In the bounded-radius, bounded-cost (BRBC) algorithm, let:


###### − TS be the shortest-paths tree
 − TM be the minimum spanning tree



###### • TBRBC is the tree constructed with parameter ε that satisfies:

 radius (T ) ≤ 1(+ )ε ⋅ radius (T ) BRBC S


###### and


##### cost (TBRBC ) ≤ +1 2 ⋅ cost (TM )  ε 

###### • When ε = 0, TBRBC has minimum radius



###### • When ε = ∞, TBRBC has minimum cost


-----

###### • Prim-Dijkstra Tradeoff based on Prim’s algorithm and Dijkstra’s algorithm

 • From the set of sinks S, iteratively add sink s based on different cost function


###### − Prim’s algorithm cost function:

 − Dijkstra’s algorithm cost function:


##### cost(s, )
###### i [s] j


###### − Prim-Dijkstra Tradeoff cost function:

 • γ is a constant between 0 and 1


##### cost(s, s ) + cost(s, s )
###### 0 i i j

##### γ ⋅ cost(s, s ) + cost(s, s )
###### 0 i i j


-----

|Col1|Col2|Col3|4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
||||||7|||||
|||||||||||
|||||||||||
|||||||||||
|||||||8||||
||||||||||7|
||||9|||||||
|||||||||s 0||

|Col1|Col2|Col3|4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
||||||||11|||
|||||||||||
|||||||||||
|||||||8||||
||||||||||7|
||||9|||||||
|||||||||s 0||


![](VLSI-design-chap8.pdf-42-0.png)

###### 4

 11

 8
 7

 9
 s
0


###### radius(T) = 19 cost(T) = 35

 γ = 0.25


![](VLSI-design-chap8.pdf-42-0.png)

###### 4

 7

 8
 7

 9
 s
0


###### radius(T) = 15 cost(T) = 39

 γ = 0.75


-----

###### • Iteratively forms a tree by adding sinks, and optimizes for critical sink(s)

 • In the critical-sink routing tree (CSRT) problem, minimize:


###### n
 α(i) ⋅ t(s, ) 0 [s]i

# ∑

###### i =1
 where α(i) are sink criticalities for sinks si, and t(s0,si) is the delay from s0 to si


-----

###### • In the critical-sink Steiner tree problem, construct a minimum-cost Steiner tree T for all sinks except for the most critical sink sc

 • Add in the critical sink by:


###### − H0: a single wire from sc to s0

 − H1: the shortest possible wire that can join sc to T, so long as the path from s0 to sc is the shortest possible total length


###### − HBest: try all shortest connections from sc to edges in T and from sc to s0. Perform timing analysis on each of these trees and pick the one with the lowest delay at sc


-----

###### 8.1 Introduction

 8.2 Timing Analysis and Performance Constraints 8.2.1 Static Timing Analysis 8.2.2 Delay Budgeting with the Zero-Slack Algorithm


###### 8.3 Timing-Driven Placement
 8.3.1 Net-Based Techniques 8.3.2 Embedding STA into Linear Programs for Placement


###### 8.4 Timing-Driven Routing
 8.4.1 The Bounded-Radius, Bounded-Cost Algorithm 8.4.2 Prim-Dijkstra Tradeoff 8.4.3 Minimization of Source-to-Sink Delay


###### 8.5 Physical Synthesis
 8.5.1 Gate Sizing 8.5.2 Buffering 8.5.3 Netlist Restructuring


###### 8.6 Performance-Driven Design Flow

 8 7 Conclusions


-----

###### • Physical synthesis is a collection of timing optimizations to fix negative slack

 • Consists of creating timing budgets and performing timing corrections



###### • Timing budgets include:

 − allocating target delays along paths or nets


###### − often during placement and routing stages

 − can also be during timing correction operations



###### • Timing corrections include:

 − gate sizing


###### − buffer insertion

 − netlist restructuring


-----

###### • Let a gate v have 3 sizes A, B, C, where:


##### size (v ) > size (v ) > size (v )
###### C B A



###### • Gate with a larger size has lower output resistance

 • When load capacitances are large:


###### t(v ) < t(v ) < t(v ) C B A

 • Gate with a smaller size has higher output resistance



###### • When load capacitances are small:
 t(v ) > t(v ) > t(v ) C B A


-----

###### • Let a gate v have 3 sizes A, B, C, where: size (v ) > size (v ) > size (v ) C B A

 40
 40


###### 35

 30


###### 25

 20


###### 25
 24 28
 23 27 26
 21 24


###### 15

 10


###### 5

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|18||||
|||||
|15||||
|||||

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|21||||
|||||
|20||||
|||||

|25|Col2|
|---|---|
|||
|24||
|||

|30|Col2|
|---|---|
|||
|27||
|26||
|||

|35|Col2|
|---|---|
|||
|30||
|||
|27||
|||

|40|Col2|
|---|---|
|||
|33||
|||
|28||
|||


###### 0.5


###### 1.0 1.5 2.0 2.5 3.0
 L d C it (fF)


-----

###### C(d) = 1.5

 C(e) = 1.0

 C(f) = 0.5


###### a
 b


###### d

 e

 f

|v|Col2|
|---|---|
|||


![](VLSI-design-chap8.pdf-49-0.png)

###### C(d) = 1.5

 C(e) = 1.0

 C(f) = 0.5


![](VLSI-design-chap8.pdf-49-0.png)

###### C(d) = 1.5


###### d

 e

 f

 t(vC) = 28


###### a
 b


###### a
 vA e C(e) = 1.0 b


###### d


###### f

 t(vA) = 40


###### C(f) = 0.5

|v A|Col2|
|---|---|
|||
|||
|||

|v C|Col2|
|---|---|
|||


-----

###### • Buffer: a series of two serially-connected inverters

 • Improve delays by


![](VLSI-design-chap8.pdf-50-0.png)

###### − speeding up the circuit or serving as delay elements

 − changing transition times


###### − shielding capacitive load



###### • Drawbacks:

 − Increased area usage


###### − Increased power consumption


-----

###### C(d) = 1 C(e) = 1


###### d C(d) = 1 e C(e) = 1
 a a vB f C(f) = 1 b b
 g C(g) = 1


###### d e


###### f
 g

 h


###### C(f) = 1 C(g) = 1

 C(h) = 1


![](VLSI-design-chap8.pdf-51-0.png)

###### C(vB) = 5 fF

 t(vB) = 45 ps


###### h


###### C(h) = 1

|v B C(v ) = 5 fF|Col2|
|---|---|
|||
|||
|||


###### C(y) = 3 fF

 t(y) = t(vB) + t(y) = 66 ps


-----

###### • Netlist restructuring only changes existing gates, does not change functionality

 • Changes include


###### − Cloning: duplicating gates

 − Redesign of fanin or fanout tree: changing the topology of gates


###### − Swapping communicative pins: changing the connections

 − Gate decomposition: e.g., changing AND-OR to NAND-NAND


###### − Boolean restructuring: e.g., applying Boolean laws to change circuit gates

 • Can also do reverse transformations of above, e.g., downsizing, merging


-----

###### • Cloning can reduce fanout capacitance

 d C(d) = 1 d
 a
 v
 e C(e) = 1 A e
 b a
 vB f C(f) = 1 f
 b
 g C(g) = 1
 vB g


###### C(d) = 1
 C(e) = 1

 C(f) = 1


![](VLSI-design-chap8.pdf-53-0.png)

###### h


###### C(h) = 1


###### h


###### C(g) = 1

 C(h) = 1

|v B|Col2|
|---|---|
|||
|||
|||



###### • and reduce downstream capacitance


###### d
 d a
 v e
 e b
 a
 f
 v f
 b
 …
 g
 … v’ g …
 h

|v|Col2|
|---|---|
|||
|||
|||


![](VLSI-design-chap8.pdf-53-0.png)

-----

###### Redesigning the fanin tree can change AATs


###### a <4> b <3>

 c <1>
 d <0>


###### f <5>


###### f <6>


###### a <4> (1)
 b <3>
 (1)
 c <1>
 (1)
 d <0>


![](VLSI-design-chap8.pdf-54-0.png)

-----

###### Redesigning fanout trees can change delays on specific paths

 path
1


![](VLSI-design-chap8.pdf-55-0.png)

###### path
2


###### path
2


-----

###### Swapping commutative pins can change the final delay


###### a <0>

 b <1>


###### c <2>
 (1) f <5> (1)
 b <1>
 (1)


###### f <3>


![](VLSI-design-chap8.pdf-56-0.png)

###### c <2>


###### a <0>


-----

###### Gate decomposition can change the general structure of the circuit


-----

###### Boolean restructuring uses laws or properties, e.g., distributive law, to change circuit topology

 (a + b)(a + c) = a + bc


###### x <5>

 y <6>


###### a <4> (1)
 b <1>

 (1)
 c <2>


###### x <6>

 y <6>


###### a <4>

 b <1>
 c <2>


![](VLSI-design-chap8.pdf-58-0.png)

###### x(a,b,c) = (a + b)(a + c)

 y(a,b,c) = (a + c)(b + c)


###### x(a,b,c) = a + bc

 y(a,b,c) = ab + c


-----

###### 8.1 Introduction

 8.2 Timing Analysis and Performance Constraints 8.2.1 Static Timing Analysis 8.2.2 Delay Budgeting with the Zero-Slack Algorithm


###### 8.3 Timing-Driven Placement
 8.3.1 Net-Based Techniques 8.3.2 Embedding STA into Linear Programs for Placement


###### 8.4 Timing-Driven Routing
 8.4.1 The Bounded-Radius, Bounded-Cost Algorithm 8.4.2 Prim-Dijkstra Tradeoff 8.4.3 Minimization of Source-to-Sink Delay


###### 8.5 Physical Synthesis
 8.5.1 Gate Sizing 8.5.2 Buffering 8.5.3 Netlist Restructuring


###### 8.6 Performance-Driven Design Flow

 8 7 Conclusions


-----

###### Baseline Physical Design Flow

 1. Floorplanning, I/O placement, power planning


###### 2. Logic synthesis and technology mapping

 3. Global placement and sequential element legalization


###### 4. Clock network synthesis

 5. Global routing and layer assignment


###### 6. Congestion-driven detailed placement and legalization

 7. Detailed routing


###### 8. Design for manufacturing

 9. Physical verification


###### 10. Mask optimization and generation


-----

###### Floorplanning Example

|Analog Processing|Analog-to-Digital and Digital-to-Analog Converter|Video Pre/Post- processing Control + DSP|Video Codec DSP|Embedded Controller for Dataplane Processing|Protocol Processing|
|---|---|---|---|---|---|
|||Audio Pre/Post- processing|Audio Codec|||
|||Baseband DSP PHY||Baseband MAC/Control|Security|


![](VLSI-design-chap8.pdf-61-0.png)

###### Video Video

 Pre/Post- processing Codec DSP Embedded Control + DSP Controller for Protocol
 Dataplane Processing
 Audio Audio
 Processing
 Pre/Post-
 Codec
 processing

 Baseband DSP Baseband Security PHY MAC/Control

 Main Applications
 Memory
 CPU


-----

###### Global Placement Example


![](VLSI-design-chap8.pdf-62-0.png)

![](VLSI-design-chap8.pdf-62-1.png)

![](VLSI-design-chap8.pdf-62-2.png)

![](VLSI-design-chap8.pdf-62-3.png)

-----

###### Clock Network Synthesis Example


![](VLSI-design-chap8.pdf-63-0.png)

-----

![](VLSI-design-chap8.pdf-64-0.png)

###### Global Routing Congestion Example


![](VLSI-design-chap8.pdf-64-1.png)

###### Global Routing Congestion Example


-----

|Performance-Driven|Col2|
|---|---|
|Chip Planning||
|||

|Block-Level Delay Budgeting|Col2|
|---|---|
|||

|Power Planning|Timing Estimation passes|
|---|---|

|Logic Synthesis and Technology Mapping|Col2|
|---|---|
|||
||Block-level or Top-level Global Placement|


###### (see full flow chart in Figure 8.26)


-----

|Global Placement|Col2|
|---|---|
|With Optional Net Weights||
|||

|Delay Estimation Using Buffers|Col2|
|---|---|
|||


###### (see full flow chart in Figure 8.26)


-----

|Timing Correction|Col2|
|---|---|
|||


###### Routing

|Col1|Routing|
|---|---|


###### (see full flow chart in Figure 8.26)


-----

###### (Re-)Buffering and Detailed Routing Timing Correction

|(Re-)Buffering and Timing Correction|Col2|
|---|---|
|||

|Detailed Routing|Col2|
|---|---|
|||

|2.5D or 3D Parasitic Extraction|Col2|
|---|---|
|||


###### Sign-off


###### (see full flow chart in Figure 8.26)


-----

###### (see full flow chart in Figure 8.26)


-----

###### • Circuit delay is measured on signal paths

 − From primary inputs to sequential elements; from sequentials to primary outputs


###### − From sequentials to sequentials



###### • Components of path delay

 − Gate delays: over-estimated by worst-case transition per gate (to ensure fast Static Timing Analysis)


###### − Wire delays: depend on wire length and (for nets with >2 pins) topology



###### • Timing constraints

 − Actual arrival times (AATs) at primary inputs and output pins of sequentials


###### − Required arrival times (RATs) at primary outputs and input pins of sequentials



###### • Static timing analysis

 − Two linear-time traversals compute AATs and RATs for each gate (and net)


###### − At each timing point: slack = RAT-AAT


###### − Negative slack = timing violation; critical nets/gates are those with negative slack

 • Time budgeting: divides prescribed circuit delay into net delay bounds


-----

###### • Gate/cell locations affect wire lengths, which affect net delays

 • Timing-driven placement optimizes gate/cell locations to improve timing


###### − Interacts with timing analysis to identify critical nets, then biases placement opt.

 − Must keep total wirelength low too, otherwise routing will fail


###### − Timing optimization may increase routing congestion



###### • Placement by net weighting

 − The least invasive technique for timing-driven placement


###### − Performs tentative placement, then changes net weights based on timing analysis



###### • Placement by net budgeting

 − Allocates delay bounds for each net; translates delay bounds into length bounds


###### − Performs placement subject to length constraints for individual nets



###### • Placement based on linear programming

 − Placement is cast as a system of equations and inequalities


###### − Timing analysis and optimization are incorporated using additional inequalities


-----

###### • Timing-driven routing has several aspects

 − Individual nets: trading longer wires for shorter source-to-sink paths


###### − Coupling capacitance and signal integrity: parallel wires act as capacitors and can slow-down/speed-up signal transitions

 − Full-netlist optimization: prioritize the nets that should be optimized first



###### • Individual net optimization

 − One extreme: route each source-to-sink path independently (high wirelength)


###### − Another extreme: use a Minimum Spanning Tree (low wirenegth, high delay)

 − Tunable tradeoff: a hybrid of Prim and Dijkstra algorithms



###### • Coupling capacitance and signal integrity

 − Parallel wires are only worth attention when they transition at the same time


###### − Identify critical nets, push neighboring wires further away to limit crosstalk



###### • Full-netlist optimization

 − Run trial routing, then run timing analysis to identify critical nets


###### − Then adjust accordingly, repeat until convergence


-----

###### • Traditionally, place-and-route have been performed after the netlist is known

 • However, fixing gate sizes and net topologies early does not account for placement-aware timing analysis


###### − Gate locations and net routes are not available

 • Physical synthesis uses information from trial placement to modify the netlist



###### • Net buffering: splits a net into smaller (approx. equal length) segments

 − A long net has high capacitance, the driver may be too weak



###### • Gate/buffer sizing: increases driver strength & physical size of a gate

 − Large gates have higher input pin capacitance, but smaller driver resistance


###### − Larger gates can drive larger fanouts, longer nets; faster transitions

 − Large gates require more space, larger upstream drivers



###### • Gate cloning: splits large fanouts

 − Cloned gates can be placed separately, unlike with a single larger gate


-----

