# 5nm FinFET Standard Cell Library Optimization and Circuit Synthesis in Near- and Super-Threshold Voltage Regimes

## Qing Xie, Xue Lin, Yanzhi Wang, Mohammad Javad Dousti, Alireza Shafaei, Majid Ghasemi-Gol, Massoud Pedram

Department of Electrical Engineering, University of Southern California, Los Angeles, CA

{xqing, xuelin, yanzhiwa, dousti, shafaeib, ghasemig, pedram}@usc.edu


**_Abstract— FinFET device has been proposed as a promising_**
**substitute for the traditional bulk CMOS-based device at the**
**nanoscale, due to its extraordinary properties such as improved**
**channel controllability, high ON/OFF current ratio, reduced**
**short-channel effects, and relative immunity to gate line-edge**
**roughness. In addition, the near-ideal subthreshold behavior**
**indicates the potential application of FinFET circuits in the near-**
**threshold supply voltage regime, which consumes an order of**
**magnitude less energy than the regular strong-inversion circuits**
**operating in the super-threshold supply voltage regime. This**
**paper presents a design flow of creating standard cells by using**
**the FinFET 5nm technology node, including both near-threshold**
**and super-threshold operations, and building a Liberty-format**
**standard cell library. The circuit synthesis results of various**
**combinational and sequential circuits based on the 5nm FinFET**
**standard cell library show up to 40X circuit speed improvement**
**and three orders of magnitude energy reduction compared to**
**those of 45nm bulk CMOS technology.**

**_Keywords- FinFET; 5nm technology; standard cell library;_**
**_near-threshold computing; power consumption; performance_**

I. INTRODUCTION

Energy consumption has always been a critical
performance metric for integrated-circuits (ICs). The voltage
down-scaling has been shown effective in reducing the energy
consumption of ICs. For some relaxed-performance
applications, such as portable wireless devices, medical
devices, and sensor network nodes, reducing the supply
voltage to a very low value, slightly higher than the threshold
voltage values of transistors, results in the minimal amount of
energy consumption [1][2][3]. The supply voltage that results
in this minimum energy consumption, referred as the minimal
_energy point (MEP), has been proved and typically observed_
in the near-threshold voltage regime [4][5][6].

The steady down-scaling of feature sizes of CMOS
technology has been the driving force of the continual
improvement in circuit speed and cost per functionality over
the past several decades. However, due to the fundamental
material and process technology limits, great challenges (i.e.,
how to mitigate the short-channel effects, minimize the
leakage current, reduce the device-to-device variability) are

This research is supported by grants from the PERFECT program of
the Defense Advanced Research Projects Agency and the Software
and Hardware Foundations of the National Science Foundation.


encountered during the scaling down of traditional planar
CMOS transistor beyond the 22nm [7][8]. Therefore, the
FinFET device, a type of quasi-planar double gate (DG)
device with a process flow and layout similar to that of the
traditional planar CMOS [9], has been proposed as a substitute
of CMOS for future technology nodes beyond 32nm [10]. It
has been reported that FinFET devices offer superior
scalability [11], lower gate leakage current [12], excellent
control of short-channel effects [13], and relative
immunization to the gate line-edge roughness [14].

Due to the promising future of FinFET device at the
nanoscale, considerable research efforts have been invested in
modeling and characterizing FinFET devices. Sinha et. al.
presented a _predictive technology model for multi-gate_
transistors (PTM-MG) for FinFETs in sub-20nm technology
nodes [15]. This model is based on BSIM-CMG model [16].
An alternative approach based on the fundamental physics
principle is adopted by Gupta et. al, and generates FinFET
device models at 5nm [17]. The device model in [17] is
specified by using look-up-tables (LUTs) and is compatible
with SPICE through a Verilog-A interface. To predict the
trend of circuit behaviors of future deeply scaled FinFET
devices, we consider the most advanced FinFET technology
node and adopt the 5nm FinFET device model developed in

[17]. In this work, we build a Synopsys Liberty-format
standard cell library [18], which is widely used for logic
synthesis and static timing analysis, using the 5nm FinFET
technology node.

The contribution of this work is in three-fold. First, we
create standard cells, including both combinational logic cells
and sequential logic cells, by using 5nm FinFET devices. The
sizing of a standard cell is derived by properly setting the
number of N-type fins and P-type fins that produce almost
equal rise and fall times. Second, we characterize the 5nm
FinFET combinational and sequential standard cells at two
supply voltages in near- and super-threshold regimes,
respectively, and build the multi-𝑉𝑑𝑑 standard cell library by
using the Liberty format. The timing, power, and capacitance
parameters of the standard cells are measured by using
HSPICE and stored in 2D LUTs. Third, we predict the timing
and power performance of 5nm FinFET technology by
synthesizing various combinational and sequential benchmark
circuits using the Synopsys Design Compiler and the
characterized 5nm FinFET standard cell library. Compared to


-----

baseline circuits synthesized using 45nm CMOS technology,
the 5nm FinFET technology improves the circuit speed by up
to 40X and reduces the energy consumption by three orders of
magnitude.

The rest of this paper is organized as follows. Section II
introduces the properties of 5nm FinFET devices at multiple
supply voltages. Section III explains the standard cell sizing.
The library format and characterization flow are elaborated in
Section IV. We show the synthesis results in Section V and
conclude the paper in Section VI.

II. 5NM FINFET TECHNOLOGY NODE


0.01


built with the 5nm FinFET devices at different supply
voltages. One can observe from Figure 2 that the minimal
energy point for typical circuit operations occurs near 0.2V,
which is less than the threshold value of the FinFET device
(0.2V ~ 0.25V). To enable both low power and high
performance applications, we build a standard cell library that
includes two supply voltages: 0.3V for near-threshold regime
and 0.45V for super-threshold regime.

0.02


Figure 1 shows the structure of a 5nm FinFET device. The
FinFET device consists of a thin silicon body, with thickness
of 𝑇𝑓𝑖𝑛, which is wrapped by gate electrodes. The device is
termed quasi-planar as the current flows parallel to the wafer
plane, and the channel is formed perpendicular to the plane.
The effective gate length 𝐿𝐺 is twice as large as the fin height
ℎ𝑓𝑖𝑛. The spacer length 𝐿𝑆𝑃 is an important design parameter
that directly relates to the short channel effects [17]. Each fin
has two gates: a front gate and a back gate. The FinFET
device allows independent control of the front and back gates
by etching away the gate electrode at the top of the channel.
The FinFET device model developed in [17] considers a
shorted-gate mode, in which the front gate and back gate are
tied together to achieve the highest drive strength [8]. Note
that in this work we focus on the shorted-gate FinFET devices
as the independent gate devices suffer from many fabrication
issues in practice.


_A._ _Inverter Sizing_

First we investigate the numbers of P-type fins and N-type
fins in an inverter that achieves approximately equal rise and
fall delays. According to the trans-regional FinFET model [6],
the drain current of a FinFET in the sub- and near-threshold
regions is given by


0
0.1 0.2 0.3 0.4 0.5

Supply Voltage (V)

Figure 2. MEPs (denoted by dots) of a 20-stage 5nm FinFET
inverter chain at different activity factors.


III. CREATING STANDARD CELLS

As shown in Figure 1 (a), the drive strength of a FinFET
device depends on the ratio of fin height and channel length,
whereas both parameters are determined by the fabrication
technology. Thus, the FinFET standard cell sizing is to select
the appropriate number of fins for the pull-up and pull-down
network of each logic cell.


Front Gate


Fins


−𝑉𝑑𝑠 (1)

𝑣𝑇 )


𝐼𝑑𝑠 = 𝐼0𝑒


�𝑉𝑔𝑠+𝜆𝑉𝑑𝑠−𝑉𝑡ℎ�−𝑎�𝑉𝑔𝑠+𝜆𝑉𝑑𝑠−𝑉𝑡ℎ�[2]

𝑚∙𝑣𝑇 (1 −𝑒


Bulk Si

_LG=5nm_ _LSP_

Back Gate

Source _Tfin=2.5nm_ Drain


(b)


where 𝜆 is the drain voltage dependence coefficient (similar
to, but much smaller than, the DIBL coefficient for bulk
CMOS devices), 𝑣𝑇 is the thermal voltage, and 𝐼0, 𝑎, and 𝑚
are technology-dependent parameters to be extracted from
HSPICE simulation.

In order to achieve equal rise and fall delay, the number of
P-type fins 𝑁𝑃 in an inverter can be determined by

|LG=5nm L|Col2|
|---|---|
|Back Gate||
|||
||T =2.5nm fin|
|||
|Front Gate||


Figure 1. (a) Perspective view and (b) top view [17] of the
5nm FinFET device.

Operating circuits in the near-threshold supply voltage
regime results in a reduced energy consumption at the cost of
circuit speed degradation. When the supply voltage 𝑉𝑑𝑑 is
reduced, the dynamic energy consumption reduces
quadratically. However, the leakage energy consumption,
which is the product of leakage power and circuit delay,
increases, because the increase of the circuit delay (satisfying
an exponential relation versus 𝑉𝑑𝑑) surpasses the reduction of
leakage power (satisfying a linear relation versus 𝑉𝑑𝑑). Figure
2 shows the energy consumption of a 20-stage inverter chain


where 𝐼𝑑𝑠,𝑁 is the drain current of an N-type fin when
𝑉𝑔𝑠 = 𝑉𝑑𝑠 = 𝑉𝐷𝐷, 𝐼𝑑𝑠,𝑃 is the drain current of a P-type fin when
�𝑉𝑔𝑠�= |𝑉𝑑𝑠| = 𝑉𝐷𝐷, and 𝑁𝑁 is the number of N-type fins in
the inverter.

Based on (2) and HSPICE simulation, the 𝑁𝑃/𝑁𝑁 ratios of
INV1X, INV2X, INV4X, and INV8X gates in the nearthreshold region (𝑉𝐷𝐷 = 0.3 V) are 1/1, 2/2, 4/4, and 8/7,
respectively. Note that we round to the nearest integer number
of fins to achieve almost equal driving strengths of the pull-up
and pull-down network.


𝑁𝑃 = 𝑁𝑁 ∙ [𝐼]𝐼[𝑑𝑠,𝑁]𝑑𝑠,𝑃


(2)


-----

_B._ _Stack Sizing of FinFET Logic Cells_

In order to design other combinational logic cells under
near-threshold region, we need to solve the _stack sizing_
problem. In some logic cells, there are several transistors
connected in series forming a _stack, e.g., the pull-down_
network of a NAND or the pull-up network of a NOR. The
stack sizing problem involves determining the transistor sizes
in a stack such that the logic cell achieves equal rise and fall
delays. We use the 2-input NAND1X as an example. Figure 3
shows an INV1X and a 2-input NAND1X, and the number on
top of a FinFET transistor symbol denotes the number of
parallel- connected fins in that FinFET transistor. The INV1X
achieves equal rise and fall delays in the near-threshold
region. We denote the stack sizing factor in an 𝑚 -input
NAND by 𝜌𝑁,𝑚, where the subscript 𝑁 denotes an N-type
FinFET device. Similarly, the stack sizing factor in an 𝑚-input
NOR is denoted by 𝜌𝑃,𝑚. The stack sizing factor 𝜌𝑁,2 of the 2input NAND is defined as the ratio of the number of N-type
fins connected to an input signal in the 2-input NAND1X to
this number in the INV1X, such that the pull down network of
the 2-input NAND1X has the same current driving strength as
it has in the INV1X. From a theoretical calculation based on
FinFET model in (1) and HSPICE simulation, we obtain
𝜌𝑁,2 = 3.25 ≈3 in the near-threshold region. Please note that
𝜌𝑁,2 is larger than 2, which is the typical value for bulk
CMOS in the super-threshold region. Similarly, we obtain
𝜌𝑃,2 = 3, 𝜌𝑁,3 = 6, and 𝜌𝑃,3 = 5. Please note that a stack of
more than three transistors may not be favored in the nearthreshold circuits because of the significant performance
degradation.

|Col1|2-input NOR|1X, 2X, 4X, 8X|
|---|---|---|
||3-input NOR|1X, 2X, 4X|
||AND-OR-INV|1X, 2X, 4X|
||OR-AND-INV|1X, 2X, 4X|
||XNOR|1X, 2X,|
||XOR|1X, 2X,|
||MUX|1X, 2X|
|Sequential logic cells|Latch|Active-high|
||D-flip-flop|Positive-edge|
||D-flip-flop w/ S/R|Positive-edge with asynchronous set and reset signals|


**_VDD_**


**_VDD_**


**_A_**


1 1
1 **_Vout_**

**_A_**


Figure 3. Illustration of stack sizing for a 2-input NAND.

_C._ _Combinational and Sequential Logic Cell Sizing_

Similar to the sizing of INV’s and derived stack sizing
factors, we derive the sizing of all other combinational logic
cells and the sequential logic cells accordingly. All the logic
cells included in the 5nm FinFET standard cell library are
summarized in Table 1. The functionality of each logic cell is
verified by HSPICE simulation. Please note that we use the
same sizing of FinFET logic cells in the super-threshold
region (𝑉𝐷𝐷 = 0.45 V), since we assume our standard cells
support DVFS (dynamic voltage and frequency scaling).

Table 1. Logic cells in 5nm FinFET standard cell library.


IV. STANDARD CELL LIBRARY CHARACTERIZATION

_A._ _Liberty-format Standard Cell Library_

A standard cell library is a set of high quality timing and
power models that accurately and efficiently capture behaviors
of standard cells. The standard cell library is widely used in
many design tools for different purposes, such as logic
synthesis, static timing analysis, power analysis, high-level
design language simulation, and so on, in the computer-aided_design (CAD) domain. The Liberty library format (.lib), which_
was first invented by Synopsys one decade ago, has become
an industrial standard that is adopted by over 100 semiconductor vendors and implemented in over 75 production
electronic design automation (EDA) tools [18]. Therefore, we
build our 5nm FinFET standard cell library in the .lib format.

The Liberty library is built in a hierarchical manner, as
shown in Figure 4. The information of process, supply
voltage, data units, LUT template, triggering thresholds, and
so on, is specified in the library-level. The library contains a
number of standard cells, including both combinational and
sequential cells with different scales. In the cell-level, the cell
area, leakage power, and each individual input/output pin are
specified. The signal direction, symbolic function, and input
capacitance are listed for each pin. In addition, the _timing_
_parameters (propagation delay, output slew, and timing check_
values) and power parameters (internal power) are also stored
in 2D LUTs in the pin-level. We obtain those timing and
power parameters of each logic cell of interest through
HSPICE simulations at various input and output conditions
based on the Verilog-A based 5nm FinFET device model.
```
 library (FinFET5nm) { pin (IN) {
  process, voltage, units,  direction, function, input_cap;
  templates, thresholds, etc.  timing(), interal_power();
  cell (inv_1x) {};
                 }
  ...
 }

```
Data (delay, output slew, power, etc.)
```
 cell (inv_1x) {
  area;
  cell_leakage_power;

```
`pin (IN) {};` Input Slew

Output
```
  ...

```
`}` Capacitance

Figure 4. Hierarchy of Liberty format library.

|Col1|Cell type|Scale/triggering|
|---|---|---|
|Combinational logic cells|Inverter|1X, 2X, 4X, 8X|
||2-input NAND|1X, 2X, 4X, 8X|
||3-input NAND|1X, 2X, 4X|


-----

|Col1|Table 2. Circuit delay and energy consumption|Col3|Col4|Col5|Col6|Col7|of combinational benchmarks.|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
||Circuit Delay (ns)||||||Energy consumption (fJ)||||||
|Library|FinFET 5nm|FinFET 5nm|CMOS 16nm|CMOS 16nm|Nangate 45nm|NCSU 45nm|FinFET 5nm|FinFET 5nm|CMOS 16nm|CMOS 16nm|Nangate 45nm|NCSU 45nm|
|𝑉 (V) 𝑑𝑑|0.30|0.45|0.50|0.70|1.10|1.10|0.30|0.45|0.50|0.70|1.10|1.10|
|c499|0.071|0.024|0.501|0.213|0.6|0.6|0.16|0.95|27.95|65.37|590.4|997.3|
|c1355|0.099|0.034|0.548|0.210|1.02|1.04|0.32|1.44|25.43|62.67|1,235|671.4|
|c1908|0.107|0.039|0.757|0.328|1.26|1.22|0.16|0.76|23.00|57.31|905.77|507.6|
|c3540|0.146|0.048|0.857|0.390|1.79|1.48|0.65|2.42|58.07|121.4|2,395|1,182|
|16-bit adder|0.153|0.051|1.109|0.404|1.45|1.31|0.053|0.33|4.51|10.12|102.5|219.8|
|16-bit multiplier|0.242|0.071|2.827|0.970|2.89|2.71|1.64|7.41|262.8|598.1|3,300|6,300|


_B._ _Library Characterization_

_1)_ _Characterizing_ _timing_ _parameters:_ The timing
parameters of a logic cell refer to propagation delays and
transition times of the output pin when the output makes a
transition. For sequential cells such as D flip-flops and latches,
the timing parameters also include time check parameters such
as the _setup time and_ _hold time of the data signal, and the_
_recovery time and_ _removal time of asynchronous control_
signals. The propagation delays and transition times are
represented by using 2D LUTs, which are indexed by input
transition times and output load capacitance at the output pin,
as shown in Figure 4. The design tools evaluate the path delay
in a circuit by indexing the delay LUTs using the total fanout
load capacitance and transition time of the input pin, which
are obtained by indexing transition time LUTs in the previous
stage. The time check parameters of sequential cells are
independent of the load capacitances, and thus they are
indexed by transition times of data or control signal and
transition times of the clock signal instead.

We apply the single input switching (SIS) assumption such
that only one input signal switches at a time. Therefore,
propagation delays and transition times are measured for
output pin related to each input pin, while signals of other
input pins stay unchanged. We define the propagation delay as
the time interval from the moment that the triggering signal of
the related input pin crosses the 50% of 𝑉𝑑𝑑 to the moment
that the output signal crosses the 50% of 𝑉𝑑𝑑 . The output
transition time is measured as the time that the output voltage
takes to transit from 20% to 80% of 𝑉𝑑𝑑for rising and from
80% to 20% of 𝑉𝑑𝑑for falling. For flip-flops, the related input
pin is the clock pin, while for latches, both clock pin and data
pin can be the related input pin.

Setup time and hold time are important timing constraints
for sequential cells that shall be satisfied to ensure correct
circuit functionality. To measure the setup time and hold time,
we start from an initial time range and apply the bisection
method [19] that binarily reduces the time range to locate the
target value, above which the timing failure of the sequential
logic cell occurs. We record setup times and hold times in 2D
LUTs. Similarly, recovery time and removal time are defined
for asynchronous control signal, which can be analogous to


setup time and hold time of the data signal [20]. We measure
recovery times and removal times by using the bisection
method and store them in 2D LUTs indexed by transition
times of clock signal and asynchronous control signal.

_2)_ _Characterizing the power parameters:_ The power
parameters in the Liberty library include the leakage power
and internal power of a logic cell. The overall power
consumption is evaluated by summing up the leakage power,
internal power, and switching power (power consumed when
charging and discharging the load capacitance.) We measure
the leakage power consumption by multiplying the supply
voltage to the average current flowing out from the 𝑉𝑑𝑑
terminal when there is no input and output signal transition.
The internal power accounts for the short-circuit power
consumption and dynamic power of the diffusion capacitors at
the output pin of the logic cell. For combinational logic cells,
the internal power is measured by subtracting the switching
energy at the load capacitance from the total energy
consumption when output signal transits. For sequential
logics, we measure the swtiching power of output pin, input
data pin, and clock pin. 2D LUTs, similar to the one shown in
Figure 4, are used to store internal power values of the output
pin related to each input pin.

_3)_ _Characterizing the input capacitance: In liberty library,_
the total fanout load capacitance of a logic cell is calculated by
summing up the input capacitance of its fanout cells. For
every input pin of each logic cell, we characterize the input
capacitance by dividing the integral of the driving current of
the input pin over the time that input signal switches by the
supply voltage.

V. SYNTHESIS RESULTS

We synthesize various combinational and sequential
benchmark circuits, as well as the LEON2 processor [21] by
using the developed 5nm FinFET standard cell library. To
show the circuit speed improvement and energy reduction at
this technology node, we compare the timing and energy
results of same circuits synthesized by using different CMOS
standard cell library at 16nm and 45nm. We build the 16nm
multi- 𝑉𝑑𝑑 CMOS standard cell library (0.7V for high
performance usage and 0.5V for low power usage) by


-----

Table 3. Energy-delay product of combinational benchmarks.


4
10

2
10


0 16nm CMOS 0.50V
10 5nm FinFET 0.45V

-2 5nm FinFET 0.30V
10
-2 -1 0 1
10 10 10 10

Delay (ns)


Figure 5. Energy vs. circuit delay for 16-bit adder at

0.526 742.9 580.2 9,537 17,073

different technology nodes.

Table 4. Frequency and power consumption of sequential benchmarks.

|Col1|Energy-delay product (fJ⋅ns)|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|Library|FinFET 5nm|FinFET 5nm|CMOS 16nm|CMOS 16nm|Nangate 45nm|NCSU 45nm|
|𝑉 (V) 𝑑𝑑|0.30|0.45|0.50|0.70|1.10|1.10|
|c499|0.011|0.02.|14.00|13.92|354.2|598.4|
|c1355|0.032|0.049|13.94|13.16|1,259|698.3|
|c1908|0.017|0.030|17.41|18.80|1,141|619.3|
|c3540|0.095|0.116|49.77|47.35|4,287|1,749|
|16-bit adder|0.008|0.017|5.002|4.088|148.6|287.9|
|16-bit multiplier|0.397|0.526|742.9|580.2|9,537|17,073|

|Col1|Frequency (GHz)|Col3|Col4|Col5|Col6|Col7|Power consumption (uW)|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|Library|FinFET 5nm|FinFET 5nm|CMOS 16nm|CMOS 16nm|Nangate 45nm|NCSU 45nm|FinFET 5nm|FinFET 5nm|CMOS 16nm|CMOS 16nm|Nangate 45nm|NCSU 45nm|
|𝑉 (V) 𝑑𝑑|0.30|0.45|0.50|0.70|1.10|1.10|0.30|0.45|0.50|0.70|1.10|1.10|
|s820|25|50|7.7|14.3|2.5|2.5|4.5|31.1|112.8|477.9|735.1|1,483|
|s1423|10|20|3.3|6.7|1.1|1.0|4.2|30.7|135.3|568.9|984.6|1,381|
|Arbiter|10|25|2.9|5.0|1.1|1.0|4.3|26.9|42.7|225.2|888.3|2,235|
|LEON2 SPARC|2.5|6.7|1.0|2.5|0.48|0.48|51|268.2|764.2|4,785|8,173|16,658|


Table 5. Energy per clock cycle of sequential benchmarks.


4
10 Nangate 45nm CMOS 1.1V

16nm CMOS 0.70V

3
10

16nm CMOS 0.50V

2
10 5nm FinFET 0.45V

5nm FinFET

1
10 5nm FinFET 0.30V 16nm CMOS

0 45nm CMOS
10
0 0.5 1 1.5 2 2.5

Clock period (ns)

|Col1|Energy per clock cycle (fJ)|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|Library|FinFET FinFET CMOS CMOS Nangate NCSU 5nm 5nm 16nm 16nm 45nm 45nm||||||
|𝑉 (V) 𝑑𝑑|0.30|0.45|0.50|0.70|1.10|1.10|
|s820|0.18|0.62|14.65|33.42|294.0|593.2|
|s1423|0.42|1.54|41.00|84.91|895.1|1,381|
|Arbiter|0.43|1.08|14.72|45.04|807.5|2,235|
|LEON2 SPARC|20.4|40.03|764.2|1,914|17,027|34,704|


following the same design flow elaborated in Section III and
IV, based on the 16nm PTM CMOS device model [15]. The
45nm standard cell libraries include a commercial library
developed by Nangate Inc. [23] and a library freely distributed
by North Carolina State University [24]. All benchmark
circuits are synthesized by using Synopsys Design Compiler

[25].

Table 2 compares the delay of some combinational
benchmarks, containing several ISCAS combinational
benchmark circuits, a 16-bit carry-ripple-adder, and a 16-bit
binary multiplier. From Table 2, one may observe that at the
nominal supply voltage of each technology node, operating
5nm FinFET circuits at 0.45V achieves circuit speed
improvement by a factor of 8X ~ 14X against 16nm CMOS
circuits at 0.7V, and 25X ~ 41X against 45nm CMOS circuits


Figure 6. Energy per clock cycle vs. clock period for
LEON2 SPARC at different technology nodes.

at 1.1V, respectively. In low power mode, operating 5nm
FinFET circuits at 0.3V results in 7X ~ 12X circuit speed
improvement against that of 16nm CMOS circuits at 0.5V.

The corresponding energy consumptions at each
technology node for those combinational benchmarks are also
summarized in Table 2. One can observe that in the nominal
condition, 5nm FinFET circuits results in 30X ~ 80X energy
reduction against 16nm CMOS circuits, and 666X ~ 1050X
energy reduction against 45nm CMOS circuits, respectively.
In addition, operating 5nm FinFET circuits in low-power
mode results in 85X ~ 174X energy reduction against 16nm
CMOS circuits.

An important property of FinFET devices comes from the
high 𝐼𝑜𝑛 / 𝐼𝑜𝑓𝑓 ratio, which results in higher ratio between
dynamic energy consumption and leakage energy


-----

consumption, comparing with that of CMOS circuits. It is
more energy efficient to operate FinFET circuits at low 𝑉𝑑𝑑 as
we can save dynamic energy, which is the dominant part for
FinFET circuits, in the near-threshold regime. More energy
reduction is observed in Table 2 for FinFET circuits when we
compare energy results obtained in nominal condition and
low-power condition. For example, we observe 6X energy
reduction with 3X delay extension when we reduce 𝑉𝑑𝑑from
0.45V to 0.3V for FinFET circuits. In contrast, reducing 𝑉𝑑𝑑
from 0.9V to 0.7V results in 2.3X energy reduction at the cost
of 3X delay extension for 16nm CMOS circuits. Therefore,
one can observe a significant drop of energy-delay-products in
Table 3 when reducing 𝑉𝑑𝑑 of FinFET circuits.

Table 4 summarizes the fast operating frequencies we
achieve for different sequential circuits and the corresponding
power consumptions. One can observe from Table 4 that the
clock frequency is improved by up to 5X and 25X by using
the 5nm FinFET technology and applying the super-threshold
supply voltage, against the 16nm and 45nm CMOS
technology, respectively. Meanwhile, operating the circuits in
the near-threshold supply voltage regime can reduce the
average power consumption by up to 32X and 520X,
comparing to that of the 16nm and 45nm CMOS technology,
respectively. Table 5 compares energy consumptions per clock
of sequential benchmark circuits. Significant amount of
energy reduction, up to 98X and 3000X, are achieved by
operating 5nm FinFET circuits in the near-threshold regime
against the 16nm and 45nm CMOS technology, respectively.
While in the super-threshold regime, the corresponding energy
reductions are up to 55X and 900X, respectively.

We show the energy and delay of the 16-bit adder at
different technology nodes in Figure 5, and energy per clock
cycle and period of LEON2 SPARC processor in Figure 6.
One can observe that 5nm FinFET technology achieves much
better circuit speed and lower energy consumption
simultaneously, against the 16nm and 45nm CMOS
technology. The near-threshold and super-threshold supply
voltages provide a design trade-off between the circuit speed
and the energy consumption.

VI. CONCLUSION

FinFET became a promising VLSI technology for recent
future due to its extraordinary properties. We adopted the most
advanced 5nm FinFET device model and presented a design
flow to build a standard cell library with multiple supply
voltage regimes, considering both high performance and low
power usages. The 5nm FinFET standard cell library enabled
static timing analysis, circuit synthesis, and dynamic voltage
and frequency scaling at this technology node. The circuit
synthesis results predicted that the 5nm FinFET technology
can achieve up to 40X circuit speed improvement as well as
up to three orders of magnitude energy reduction against the
45nm CMOS technology. We also observed a significant


energy-delay-product drop by reducing the supply voltage of
the 5nm FinFET circuits.

REFERENCES

[1] R. Dreslinski, M. Wiekowski, D. Blaauw, D. Sylvester, and T. Mudge,
“Near-threshold computing: reclaiming Moore’s law through energy
efficient integrated circuits,” Proc. of IEEE, 2010.

[2] D. Markovic, C. Wang, L. Alarcon, T. Liu, and J. Rabaey, “Ultralowpower design in near-threshold region,” Proc. of IEEE, 2010.

[3] A. Wang and A. Chandrakasan, “A 180 mV FFT processor using circuit
techniques,” ISSCC, 2004.

[4] B. Zhai, D. Blaauw, D. Sylvester, and K. Flautner, “Theoretical and
practical limits of dynamic voltage scaling,” DAC, 2004.

[5] B. H. Calhoun, A. Wang, and A. Chandrakasan, “Modeling and sizing
for minimum energy operation in subthreshold circuits,” IEEE J. Solid_State Circuits, 2005._

[6] X. Lin, Y. Wang, and M. Pedram, “Joint Sizing and Adaptive
Independent Gate Control for FinFET Circuits Operating in Multiple
Voltage Regimes Using the Logical Effort Method”, ICCAD, 2013.

[7] T.-J. King, “FinFETs for nanoscale CMOS digital integrated circuits,”
_ICCAD 2005, pp. 207–210._

[8] N. K. Jha, and D. Chen, Nanoelectronic Circuit Design, Springer Press,
2011.

[9] N. Lindert et. al., "Sub-60-nm quasi-planar FinFETs fabricated using a
simplified process," _IEEE on Electron Device Letters, vol.22, no.10,_
pp.487-489, Oct. 2001.

[10] E. J. Nowak et. al., “Turning silicon on its edge,” _IEEE Circuits and_
_Devices Magazine, vol.20, no.1, pp.20-31, 2004._

[11] C. Wann, K. Noda, T. Tanaka, M. Yoshida, and C. Hu, "A comparative
study of advanced MOSFET concepts," _IEEE on Electron Devices,_
vol.43, no.10, pp.1742-1753, Oct 1996.

[12] L. Chang et. al., "Reduction of direct-tunneling gate leakage current in
double-gate and ultra-thin body MOSFETs," IEDM, 2001.

[13] B. Yu et. al., “FinFET scaling to 10 nm gate length”, IEDM 2002.

[14] A.R. Brown, A. Asenov, J. R. Watling, "Intrinsic fluctuations in sub 10nm double-gate MOSFETs introduced by discreteness of charge and
matter," _IEEE Transactions on Nanotechnology, vol.1, no.4, pp.195-_
200, Dec 2002.

[15] S. Sinha, G. Yeric, V. Chandra, B. Cline, and Y. Cao, “Exploring Sub20nm FinFET Design with Predictive Technology Models”, DAC, 2012.

[16] M. Dunga et al., _BSIM-CMG: A Compact Model for Multi-Gate_
_Transistors. Springer US, 2008._

[17] S. K. Gupta, W. Cho, A. A. Goud, K. Yogendra, and K. Roy, "Design
space exploration of FinFETs in sub-10nm technologies for energyefficient near-threshold circuits," _Device Research Conference (DRC),_
2013.

[18] Synopsys Inc., Liberty Library Modeling, http://www.synopsys.com/
community/interoperability/pages/libertylibmodel.aspx.

[19] Synopsys Inc., HSPICE User Guide: Simulation and Analysis.

[20] Silvaco International., Introduction to Cell Characterization, [online]
http://www.silvaco.com/content/kbase/cell_char_intro_090508.pdf.

[21] LEON2 SPRAC processor, [online] http://vlsicad.eecs.umich.edu/BK/
Slots/cache/www.gaisler.com/products/leon2/leon.html.

[22] 16nm PTM CMOS model, [online] http://ptm.asu.edu/latest.html.

[23] 45nm Open Cell Library, [online] http://www.nangate.com/?page_id=22

[24] FreePDK45, [online] http://www.eda.ncsu.edu/wiki/FreePDK45:Contents

[25] Design Compiler, Synopsys, [online] http://www.synopsys.com/Tools/
Implementation/RTLSynthesis/DCGraphical/Pages/default.aspx.


-----

