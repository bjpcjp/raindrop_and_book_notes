![](VLSI-design-chap6.pdf-0-0.png)

-----

### 6.1 Terminology

 6.2 Horizontal and Vertical Constraint Graphs


##### 6.2.1 Horizontal Constraint Graphs

 6.2.2 Vertical Constraint Graphs


### 6.3 Channel Routing Algorithms

##### 6.3.1 Left-Edge Algorithm


##### 6.3.2 Dogleg Routing


### 6.4 Switchbox Routing

##### 6.4.1 Terminology


##### 6.4.2 Switchbox Routing Algorithms


### 6.5 Over-the-Cell Routing Algorithms

##### 6.5.1 OTC Routing Methodology 6.5.2 OTC Routing Algorithms


### 6.6 Modern Challenges in Detailed Routing


-----

|ENTITY test is port a: in bit; end ENTITY test;|Col2|
|---|---|
|||

|DRC LVS ERC|Col2|
|---|---|
|||


-----

### Non-Manhattan and clock routing (Chap. 7)


-----

![](VLSI-design-chap6.pdf-4-0.png)


### • The objective of detailed routing is to assign route segments of signal nets to specific routing tracks, vias, and metal layers in a manner consistent with given global routes of those nets

 • Similar to global routing

#### − Use physical wires to do connections

 − Estimating the wire resistance and capacitance, which determines whether the design meets timing requirements

### • Detailed routing techniques are applied within routing regions, such as

#### − channels (Sec. 6.3), switchboxes (Sec. 6.4) , and global routing cells (Sec. 6.5)

### • Detailed routers must account for manufacturing rules and the impact of manufacturing faults (Sec. 6.6)


-----

![](VLSI-design-chap6.pdf-5-0.png)


### • Detailed Routing Stages

#### − Assign routing tracks

 − Perform entire routing – no open connection left

 − Search and repair – resolving all the physical design rules

 − Perform optimizations, e.g. add redundant vias (reduce resistivity, better yield)


-----

### Global Routing
#### Detailed Routing

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


![](VLSI-design-chap6.pdf-6-0.png)

#### Horizontal Vertical Via Segment Segment


-----

### Channel and Switchbox Routing


### E

|Col1|Col2|Col3|Col4|B|Col6|E|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
|||||||||E|
||||||||||
||||||||||
||||||||||
|B|||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
|||E cal||D ha|||||

|Col1|Col2|Col3|
|---|---|---|
||||
||||
||||
|B nel|||


-----

### Channel Routing


![](VLSI-design-chap6.pdf-8-0.png)

###### Standard Cell Row
 External Pad

 Channel
 Power Rail


![](VLSI-design-chap6.pdf-8-1.png)

###### External Pad


-----

|Cell Area B B C D B C A C A B B C Cell Area|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
||B||||B||C||D||B||C||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||||||||||||||
||||C||||B||||B||C||

|A|Col2|A|
|---|---|---|
||||
||||
||||


### Metal2


![](VLSI-design-chap6.pdf-9-0.png)

### Via


-----

### Columns


### a b c d e f g


### B 0 B


### C


### D B C


### Vertical Segment (Branch)


### 1


### 2


### Tracks


### Horizontal Segment (Trunk)


### 3

|B B C D 0|B|B 0|Col4|Col5|B|Col7|C|Col9|D|Col11|B|Col13|C|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|t|||||||||||||||
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


### A C A B 0 B


### C


-----

### Horizontal Constraint



### • Assumption: one layer for horizontal routing

 • A horizontal constraint exists between two nets if their horizontal segments overlap


### Horizontally constrained

|Col1|Col2|Col3|A|B C|
|---|---|---|---|---|
|||||Hori con B C|
||||||
||||||
||||||
||||||
||||||


### Horizontally unconstrained


-----

### Vertical Constraint



### • A vertical constraint exists between two nets if they have pins in the same column

 ⇒ The vertical segment coming from the top must “stop” before overlapping with the vertical segment coming from the bottom in the same column


### A


### A B B
 A B


### B A


### B A


### B A


### Vertically constrained without conflict


### Vertically constrained with a vertical conflict


-----

### 6.1 Terminology

 6.2 Horizontal and Vertical Constraint Graphs


##### 6.2.1 Horizontal Constraint Graphs

 6.2.2 Vertical Constraint Graphs


### 6.3 Channel Routing Algorithms

##### 6.3.1 Left-Edge Algorithm


##### 6.3.2 Dogleg Routing


### 6.4 Switchbox Routing

##### 6.4.1 Terminology


##### 6.4.2 Switchbox Routing Algorithms


### 6.5 Over-the-Cell Routing Algorithms

##### 6.5.1 OTC Routing Methodology 6.5.2 OTC Routing Algorithms


### 6.6 Modern Challenges in Detailed Routing


-----

### • The relative positions of nets in a channel routing instance can be modeled by horizontal and vertical constraint graphs

 • These graphs are used to


#### − initially predict the minimum number of tracks that are required

 − detect potential routing conflicts


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G

 S(b) = {A, B, C}



### • Let S(col) denote the set of nets that pass through column col

 • S(col) contains all nets that either (1) are connected to a pin in column col or (2) have pin connections to both the left and right of col



### • Since horizontal segments cannot overlap, each net in S(col) must be assigned to a different track in column col

 • S(col) represents the lower bound on the number of tracks in colum col; lower bound of the channel height is given by maximum cardinality of any S(col)


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G

 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G

 S(a) = {A} S(a) S(b)S(c)S(d)S(e)S(f)S(g)S(h)S(i) S(j) S(k) S(b) = {A,B,C}
 0 B D E B F G 0 D 0 0
 S(c) = {A,B,C,D,E}
 A S(d) = {A,B,C,D,E}
 B
 S(e) = {A,B,D,E}
 C D
 S(f) = {A,D,F}
 E F S(g) = {D,F,G}
 G
 S(h) = {D,G,H}
 H
 S(i) = {D,G,H}
 A C E C E A F H 0 H G S(j) = {G,H}


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G

 S(a) S(b)S(c)S(d)S(e)S(f)S(g)S(h)S(i) S(j) S(k)


### S(a) = {A} S(b) = {A,B,C} S(c) = {A,B,C,D,E} S(d) = {A,B,C,D,E} S(e) = {A,B,D,E} S(f) = {A,D,F} S(g) = {D,F,G} S(h) = {D,G,H} S(i) = {D,G,H} S(j) = {G,H}


### 0 B D E B F G 0 D 0 0

 A
 B
 C D
 E F
 G H

 A C E C E A F H 0 H G


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G


### S(c) S(f)S(g) S(i)

 0 B D E B F G 0 D 0 0

|S(c)|S(f)|S(g)|S(i)|
|---|---|---|---|
|A B C|F|G||
||||H|
|D E||||
|||||


### A C E C E A F H 0 H G


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G


### Lower bound on the number of tracks = 5

|S(c)|S(f)|S(g)|S(i)|
|---|---|---|---|
|A B C|F|G||
||||H|
|D E||||
|||||


-----

### Column a  b   c  d   e   f   g  h   i   j   k
 0 B D E B F G 0 D 0 0


### A C E C E A F H 0 H G


### Graphical Representation

|S(c)|S(f)|S(g)|S(i)|
|---|---|---|---|
|A B C|F|G||
||||H|
|D E||||
|||||


![](VLSI-design-chap6.pdf-21-1.png)

## G


![](VLSI-design-chap6.pdf-21-2.png)

## E


![](VLSI-design-chap6.pdf-21-3.png)

## D


![](VLSI-design-chap6.pdf-21-4.png)

## C


-----

### • A directed edge e(i,j) ∈ E connects nodes i and j if the horizontal segment of net i must be located above net j

 A


![](VLSI-design-chap6.pdf-22-0.png)

### A


### B


![](VLSI-design-chap6.pdf-22-0.png)

### B


-----

-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-24-0.png)

### A


![](VLSI-design-chap6.pdf-24-1.png)

### C


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-25-0.png)

### A


![](VLSI-design-chap6.pdf-25-1.png)

### B


![](VLSI-design-chap6.pdf-25-2.png)

### C


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-26-0.png)

### A


![](VLSI-design-chap6.pdf-26-1.png)

### B


![](VLSI-design-chap6.pdf-26-2.png)

### C


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


### Vertical Constraint Graph (VCG)


![](VLSI-design-chap6.pdf-27-2.png)

### B


### Note: an edge that can be derived by transitivity is not included, such as edge (B,C)


![](VLSI-design-chap6.pdf-27-0.png)

### A


![](VLSI-design-chap6.pdf-27-1.png)

### D


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-28-0.png)

### F


![](VLSI-design-chap6.pdf-28-1.png)

### E


![](VLSI-design-chap6.pdf-28-2.png)

### D


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-29-0.png)

### F


![](VLSI-design-chap6.pdf-29-1.png)

### G


![](VLSI-design-chap6.pdf-29-2.png)

### B


![](VLSI-design-chap6.pdf-29-3.png)

### C


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-30-0.png)

### H


![](VLSI-design-chap6.pdf-30-1.png)

### A


![](VLSI-design-chap6.pdf-30-2.png)

### E


![](VLSI-design-chap6.pdf-30-3.png)

### D


-----

### 0 B D E B F G 0 D 0 0

 A C E C E A F H 0 H G


![](VLSI-design-chap6.pdf-31-0.png)

### A


![](VLSI-design-chap6.pdf-31-1.png)

### H


![](VLSI-design-chap6.pdf-31-2.png)

### E


![](VLSI-design-chap6.pdf-31-3.png)

### G


-----

![](VLSI-design-chap6.pdf-32-1.png)

### A


### A B B

 B 0 A


### A B B

 B A


### Net splitting


### Cyclic conflict


![](VLSI-design-chap6.pdf-32-0.png)

### B


-----

### 6.1 Terminology

 6.2 Horizontal and Vertical Constraint Graphs


##### 6.2.1 Horizontal Constraint Graphs

 6.2.2 Vertical Constraint Graphs


### 6.3 Channel Routing Algorithms

##### 6.3.1 Left-Edge Algorithm


##### 6.3.2 Dogleg Routing


### 6.4 Switchbox Routing

##### 6.4.1 Terminology


##### 6.4.2 Switchbox Routing Algorithms


### 6.5 Over-the-Cell Routing Algorithms

##### 6.5.1 OTC Routing Methodology 6.5.2 OTC Routing Algorithms


### 6.6 Modern Challenges in Detailed Routing


-----

### • Based on the VCG and the zone representation, greedily maximizes the usage of each track

#### − VCG: assignment order of nets to tracks


#### − Zone representation: determines which nets may share the same track

### • Each net uses only one horizontal segment (trunk)


-----

#### Input: channel routing instance CR
 Output: track assignments for each net


#### curr_track = 1 // start with topmost track
 nets_unassigned = Netlist while (nets_unassigned != Ø) // while nets still unassigned


#### VCG = VCG(CR) // generate VCG and zone
 ZR = ZONE_REP(CR) //  representation


#### SORT(nets_unassigned,start column) // find left-to-right ordering //  of all unassigned nets
 for (i =1 to |nets_unassigned|)


#### curr_net = nets_unassigned[i] if (PARENTS(curr_net) == Ø && // if curr_net has no parent
 (TRY_ASSIGN(curr_net,curr_track)) //  and does not cause //  conflicts on curr_track,


#### ASSIGN(curr_net,curr_track) //  assign curr_net


#### REMOVE(nets_unassigned,curr_net)
 curr_track = curr_track + 1 // consider next track


-----

##### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


-----

##### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


### 1. Generate VCG and zone representation

|A|Col2|Col3|G|Col5|
|---|---|---|---|---|
||B||H||
|C||||I|
|||D||J|
|E||F|||
||||||


###### E


###### F


###### H


###### B


###### J


-----

|Col1|A|Col3|Col4|G|Col6|Col7|
|---|---|---|---|---|---|---|
|||B||H|||
||C||||I||
||||D||J||
||E||F||||
||||||||


###### F


###### H


###### A


###### C


###### J


### 2. Consider next track
 3. Find left-to-right ordering of all unassigned nets If curr_net has no parents and does not cause conflicts on curr_track assign curr_net


###### B


###### I


###### D


### curr_track = 1: Net A Net J

 4 Delete placed nets (A J ) in VCG and zone represenation


###### G


-----

### curr_track = 1

 2


### 3

 4


### 5


### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


-----

|Col1|Col2|Col3|G|Col5|
|---|---|---|---|---|
||B||H||
|C||||I|
|||D|||
|E||F|||
||||||


###### F


###### H


###### E


###### D


### 2. Consider next track
 3. Find left-to-right ordering of all unassigned nets If curr_net has no parents and does not cause conflicts on curr_track assign curr_net


###### B


###### I


### curr_track = 2:


###### G


### Net D


###### C


### 4 Delete placed nets (D ) in VCG and zone representation


-----

### 1


### curr_track = 2

 3


### 4

 5


### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


-----

|Col1|Col2|Col3|Col4|G|Col6|
|---|---|---|---|---|---|
|||B||H||
||C||||I|
|||||||
||E||F|||
|||||||


###### F


###### H


###### E


### 2. Consider next track
 3. Find left-to-right ordering of all unassigned nets If curr_net has no parents and does not cause conflicts on curr_track assign curr_net


###### B


###### I


### curr_track = 3:


###### G


### Net E Net G


###### C


### 4 Delete placed nets (E G ) in VCG and zone representation


-----

### 1

 2


### curr_track = 3

 4


### 5


### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


-----

###### I


###### C H F

 B

### 2. Consider next track

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||B||H||
||C||||I|
|||||||
||||F|||
|||||||


###### B


###### H


### 3. Find left-to-right ordering of all unassigned nets If curr_net has no parents and does not cause conflicts on curr_track assign curr_net


###### F


### curr_track = 4:


###### C


### Net C Net F Net I


### 4 Delete placed nets (C F I ) in VCG and zone representation


-----

### 1

 2

 3


### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


### curr_track = 4

 5


-----

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||B||H||
||||||
||||||
||||||
||||||


###### H


### 2. Consider next track
 3. Find left-to-right ordering of all unassigned nets If curr_net has no parents and does not cause conflicts on curr_track assign curr_net


###### B


### curr_track = 5:


### Net B Net H


### 4 Delete placed nets (B H ) in VCG and zone representation


-----

### 1

 2

 3


### 0 A D E A F G 0 D I J J

 B C E C E B F H I H G I


### 4

 curr_track = 5


### Routing result


-----

### • Improving left-edge algorithm by net splitting

 • Two advantages:


### − Alleviates conflicts in VCG

 − Number of tracks can often be reduced


### A B B

 B 0 A


-----

### Conflict alleviation using a dogleg

 A A B B


![](VLSI-design-chap6.pdf-49-1.png)

### A


### B 0 A


### A B B

 B A


![](VLSI-design-chap6.pdf-49-0.png)

### B


-----

### Track reduction using a dogleg


### A A B

 0 B 0


### B 0

 C C


### A A B

 0 B 0


### B 0

 C C


-----

### • Splitting p-pin nets (p > 2) into p − 1 horizontal segments

 • Net splitting occurs only in columns that contain a pin of the given net



### • After net splitting, the algorithm follows the left-edge algorithm 

 Net splitting
 A A B B 0


### B1 B2

 0 B 0

|Net splitting A A B B 0 A|Col2|Net splitting|
|---|---|---|
|A|||


### C

 C C

|Col1|Col2|
|---|---|


-----

### A A B B 0

 0 B 0 C C


### A A B B 0

 0 B 0 C C


![](VLSI-design-chap6.pdf-52-0.png)

### A


![](VLSI-design-chap6.pdf-52-1.png)

### C


### Channel routing problem

 A A B B 0


![](VLSI-design-chap6.pdf-52-0.png)

### B


### VCG without net splitting Channel routing solution

 A A B B 0


### A


![](VLSI-design-chap6.pdf-52-0.png)

### A


![](VLSI-design-chap6.pdf-52-1.png)

### B2


### B1 B2


### C

 0 B 0 C C


![](VLSI-design-chap6.pdf-52-0.png)

### B1


### Net splitting


![](VLSI-design-chap6.pdf-52-0.png)

### C


### VCG with net splitting


### 0 B 0 C C

 Channel routing solution


-----

### 6.1 Terminology

 6.2 Horizontal and Vertical Constraint Graphs


##### 6.2.1 Horizontal Constraint Graphs

 6.2.2 Vertical Constraint Graphs


### 6.3 Channel Routing Algorithms

##### 6.3.1 Left-Edge Algorithm


##### 6.3.2 Dogleg Routing


### 6.4 Switchbox Routing

##### 6.4.1 Terminology


##### 6.4.2 Switchbox Routing Algorithms


### 6.5 Over-the-Cell Routing Algorithms

##### 6.5.1 OTC Routing Methodology 6.5.2 OTC Routing Algorithms


### 6.6 Modern Challenges in Detailed Routing


-----

|Col1|Col2|Col3|B|Col5|Col6|E|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|||||||||
|||||||||
|||||||||
|B|||||||B|
|||D||||B||
|||||||||
|D||||||||
||E||D|||||



### • Fixed dimensions and pin connections on all four sides

 • Defined by four vectors TOP, BOT, LEFT, RIGHT



### • Switchbox routing algorithms are usually derived from (greedy) channel routing algorithms


-----

#### R = {0, 1, 2, …, 8} x {0, 1, 2, …, 7} TOP = (1, 2, …, 7) = [0, D, F, H, E, C, C] BOT = (1, 2, …, 7) = [0, 0, G, H, B, B, H] LEFT = (1, 2, …, 6) = [A, 0, D, F, G, 0] RIGHT = (1, 2, …, 6) = [B, H, A, C, E, C]

 Column


![](VLSI-design-chap6.pdf-55-1.png)

#### 0


![](VLSI-design-chap6.pdf-55-1.png)

#### D F H E C C


#### 6

 5

 4

 3

 2

 1


![](VLSI-design-chap6.pdf-55-0.png)

# ?


#### 0

 A


#### C

 E

 C

 A

 H


#### 0

 G

 F

 D


#### A B

 0 0 G H B B H


#### 0

 G

 F

 D

 0


#### a b c d e f g
 0 D F H E C C

 0 0 G H B B H


#### C

 E

 C

 A

 H

 B


# ?


-----

#### TOP = (1, 2, …, 7) = [0, D, F, H, E, C, C] BOT = (1, 2, …, 7) = [0, 0, G, H, B, B, H] LEFT = (1, 2, …, 6) = [A, 0, D, F, G, 0] RIGHT = (1, 2, …, 6) = [B, H, A, C, E, C]

 Column


#### 6

 5

 4

 3

 2

 1


#### 0

 A


#### 0

 G

 F

 D


#### a b c d e f g
 0 D F H E C C

 0 0 G H B B H


#### C

 E

 C

 A

 H

 B


-----

#### TOP = (1, 2, …, 7) = [0, D, F, H, E, C, C] BOT = (1, 2, …, 7) = [0, 0, G, H, B, B, H] LEFT = (1, 2, …, 6) = [A, 0, D, F, G, 0] RIGHT = (1, 2, …, 6) = [B, H, A, C, E, C]

 Column


#### D F H E C C


#### 0


#### 6

 5

 4

 3

 2

 1


![](VLSI-design-chap6.pdf-57-0.png)

#### 0

 A


#### C

 E

 C

 A

 H


#### 0

 G

 F

 D


#### 0

 G

 F

 D

 0


#### A B

 0 0 G H B B H


#### 0 D F H E C C

 0 0 G H B B H


#### C

 E

 C

 A

 H

 B


-----

### 6.1 Terminology

 6.2 Horizontal and Vertical Constraint Graphs


##### 6.2.1 Horizontal Constraint Graphs

 6.2.2 Vertical Constraint Graphs


### 6.3 Channel Routing Algorithms

##### 6.3.1 Left-Edge Algorithm


##### 6.3.2 Dogleg Routing


### 6.4 Switchbox Routing

##### 6.4.1 Terminology


##### 6.4.2 Switchbox Routing Algorithms


### 6.5 Over-the-Cell Routing Algorithms

##### 6.5.1 OTC Routing Methodology 6.5.2 OTC Routing Algorithms


### 6.6 Modern Challenges in Detailed Routing


-----

### • Standard cells are placed back-to-back or without routing channels

 • Metal layers are usually represented by a coarse routing grid made up of global routing cells (gcells)


### Back to back Without routing channels


-----

### • Standard cells are placed back-to-back or without routing channels

 • Metal layers are usually represented by a coarse routing grid made up of global routing cells (gcells)

|gcells|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|Metal3|||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||Metal3||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||


### Metal1 (Cells: Back to back)


### Metal2 (Cell ports) Metal4 etc.


-----

### • Standard cells are placed back-to-back or without routing channels

 • Metal layers are usually represented by a coarse routing grid made up of global routing cells (gcells)

|gcells|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|Metal3|||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||Metal3||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||
||||||||||||||||||||


### Metal1 Metal2 (Cell ports) (Without routing channels)


### Metal4 etc.


-----

### • Standard cells are placed back-to-back or without routing channels

 • Metal layers are usually represented by a coarse routing grid made up of global routing cells (gcells)



### • Layers that are not obstructed by standard cells are typically used for over-the-cell (OTC) routing

 • Nets are globally routed using gcells and then detail-routed 


-----

### Three-layer approach

 • Metal3 is used for over-the-cell (OTC) routing

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||
|Metal1 (Cells)||||||||||||Metal3|||||
||||||||||||||||||
||||||||||||||||||
||||||||||||||||||


### Metal2


-----

### Three-layer approach

 • Metal3 is used for over-the-cell (OTC) routing


#### Metal3

 Metal2


#### Metal1

|Cell Area B B C D B C A C A B B C Cell Area|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||B||C|||B||C||
||||||||||||||
||||||||||||||
||||||||||||||
||||||||||||||
||||||||||||||
||||||||||||||
||||||||||||||
||||||||||||||
||||||||||||||
|||C|||||||B||C||

|A|Col2|A|
|---|---|---|
||||
||||


-----

#### Ports in Metal2


![](VLSI-design-chap6.pdf-65-0.png)

**_GND_**

#### Standard cell (only ports shown)

 Channel


-----

### 6.1 Terminology

 6.2 Horizontal and Vertical Constraint Graphs


##### 6.2.1 Horizontal Constraint Graphs

 6.2.2 Vertical Constraint Graphs


### 6.3 Channel Routing Algorithms

##### 6.3.1 Left-Edge Algorithm


##### 6.3.2 Dogleg Routing


### 6.4 Switchbox Routing

##### 6.4.1 Terminology


##### 6.4.2 Switchbox Routing Algorithms


### 6.5 Over-the-Cell Routing Algorithms

##### 6.5.1 OTC Routing Methodology 6.5.2 OTC Routing Algorithms


### 6.6 Modern Challenges in Detailed Routing


-----

### • Manufacturers today use different configurations of metal layers and widths to accommodate high-performance designs

 • Detailed routing is becoming more challenging, for example:


#### − Vias connecting wires of different widths inevitably block additional routing resources on the layer with the smaller wire pitch

 − Advanced lithography techniques used in manufacturing require stricter enforcement of preferred routing direction on each layer


-----

### Representative layer stacks for 130 nm - 32 nm technology nodes

###### U2


###### W2

 W1


###### B3

 B2 B1

 M5
 M4 M3 M2 M1


###### U1

 E1

 B3
 B2 B1
 C2 C1
 M4 M3 M2 M1


###### E2

 E1


###### E2

 E1

 B3 B2 B1
 M4 M3 M2 M1


###### M6 M5 M4
 M3
 M2 M1


###### B2 B1
 M5 M4 M3 M2 M1


-----

### • Semiconductor manufacturing yield is a key concern in detailed routing

#### − Redundant vias and wiring segments as backups (via doubling and non-tree routing)


#### − Manufacturability constraints (design rules) become more restrictive

 − Forbidden pitch rules prohibit routing wires at certain distances apart, but allows smaller or greater spacings 



### • Detailed routers must account for manufacturing rules and the impact of manufacturing faults

#### − Via defects: via doubling during or after detailed routing


#### − Interconnect defects: add redundant wires to already routed nets

 − Antenna-induced defects: detailed routers limit the ratio of metal to gate area on each metal layer


-----

### Antenna Effect


![](VLSI-design-chap6.pdf-70-0.png)

Source: http://en.wikipedia.org/wiki/Antenna_effect


-----

### Antenna Effect Fix


![](VLSI-design-chap6.pdf-71-0.png)

Source: http://en.wikipedia.org/wiki/Antenna_effect


-----

### • Detailed routing is invoked after global routing

 • Usually takes about as much time as global routing


#### − For heavily congested designs can take much longer



### • Generates specific track assignments for each connection

#### − Tries to follow "suggestions" made by global routing, but may alter them if necessary


#### − A small number of failed global routed (disconnected, overcapacity) can be tolerated



### • More affected by technology & manufacturing constraints than global routing

#### − Must satisfy design rules


-----

### • Breaks down the layout area into regions

#### − Channels have net terminals (pins) on two sides


#### − Switch-boxes have terminals on four sides

 − Channels are joined at switchboxes



### • When the number of metal layers is >3, use over-the-cell (OTC) routing

#### − Divide the layout region into a grid of global routing cells (gcells)


#### − OTC routing makes the locations of cells, obstacles and pins less important

 − Channel and switchbox routing can be used during OTC routing when upper metal layers are blocked (by wide buses, other wires, etc.)



### • The capacity of a region is limited by the number of tracks it contains

#### − Channels, switchboxes, gcells


-----

### • Horizontal and vertical constraint graphs capture constraints that must be satisfied by valid routes

 • Simplest algorithms for detailed routing are greedy


#### − Every step satisfies immediate constraints with minimal routing cost

 − Use as few bends as possible (doglegs are used when additional bends are needed)


#### − Very fast, do a surprisingly good job in many cases


#### − Insufficient for congested designs

### • Switchbox routing algorithms are usually derived from channel routing algorithms



### • Strategy 1: Do not create congested designs and rely on greedy algorithms

 • Strategy 2: Accommodate congested designs and develop stronger algorithms


-----

### • Variable-pitch wire stacks

#### − Not addressed in the literature until 2008



### • Satisfying more complex design rules

#### − Min spacing between wires and devices


#### − Forbidden pitch rules

 − Antenna rules



### • Soft rules

#### − Do not need to be satisfied


#### − Can improve yield by decreasing the probability of defects



### • Redundant vias

#### − In case some vias are poorly manufactured



### • Redundant wires

#### − In case some wires get disconnected


-----

