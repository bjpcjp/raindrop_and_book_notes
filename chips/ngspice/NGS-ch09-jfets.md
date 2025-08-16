# Chapter 9

 JFETs

## 9.1 Junction Field-Effect Transistors (JFETs)

General form:
```
   JXXXXXXX nd ng ns mname <area> <off> <ic=vds,vgs> <temp=t>

```
Examples:
```
  J1 7 2 3 JM1 OFF
nd, ng, and ns are the drain, gate, and source nodes, respectively. mname is the model name,
area is the area factor, and off indicates an (optional) initial condition on the device for dc

```
analysis. If the area factor is omitted, a value of 1.0 is assumed. The (optional) initial condition
specification, using ic=VDS,VGS is intended for use with the uic option on the .TRAN control
line, when a transient analysis is desired starting from other than the quiescent operating point.
See the .ic control line for a better way to set initial conditions. The (optional) temp value is
the temperature where this device is to operate, and overrides the temperature specification on
the .option control line.

## 9.2 JFET Models (NJF/PJF)

### 9.2.1 JFET level 1 model with Parker Skellern modification

The level 1 JFET model is derived from the FET model of Shichman and Hodges. The dc
characteristics are defined by the parameters VTO and BETA, which determine the variation
of drain current with gate voltage, LAMBDA, which determines the output conductance, and
IS, the saturation current of the two gate junctions. Two ohmic resistances, RD and RS, are
included.

_vgst = vgs_ _VTO_ (9.1)
_−_


-----

_βp = BETA_ (1 + _LAMBDAvds)_ (9.2)


_IDrain =_


1 _B_
_−_
_bfac =_ (9.3)

_PB_ _VTO_
_−_



_vds_ _GMIN,_ if vgst 0

 _·_ _≤_


_βp vds_ (vds (bfacvds _−_ _B)_ _vgst (2B_ + 3bfac (vgst − _vds)))+_ _vds_ _·_ _GMIN,_ if vgst ≥ _vds_


βp vgst[2] (B + _vgst bfac)+_ _vds_ _·_ _GMIN,_ if vgst < vds

(9.4)


Note that in Spice3f and later, the fitting parameter B has been added by Parker and Skellern.
For details, see [9]. If parameter B is set to 1 equation above simplifies to


_IDrain =_




_vds_ _GMIN,_ if vgst 0

 _·_ _≤_


_βp vds_ (2vgst − _vds)+_ _vds_ _·_ _GMIN,_ if vgst ≥ _vds_ (9.5)


βp vgst[2] + _vds_ _·_ _GMIN,_ if vgst < vds


Charge storage is modeled by nonlinear depletion layer capacitances for both gate junctions,
which vary as the _/2 power of junction voltage and are defined by the parameters CGS, CGD,_
_−[1]_
and PB.

|which vary as and PB.|s the −1/2 power of junction voltage and|d are def|fined by th|he parameter|rs CGS, CGD,|
|---|---|---|---|---|---|
|Name|Parameter|Units|Default|Example|Scaling factor|
|VTO|Threshold voltage V T0|V|-2.0|-2.0||
|BETA|Transconductance parameter (β)|A/V ”|1.0e-4|1.0e-3|area|
|LAMBDA|Channel-length modulation parameter (λ)|1/V|0|1.0e-4||
|RD|Drain ohmic resistance|Ω|0|100|area|
|RS|Source ohmic resistance|Ω|0|100|area|
|CGS|Zero-bias G-S junction capacitance C gs|F|0|5pF|area|
|CGD|Zero-bias G-D junction capacitance C gd|F|0|1pF|area|
|PB|Gate junction potential|V|1|0.6||
|IS|Gate saturation current I S|A|1.0e-14|1.0e-14|area|
|B|Doping tail parameter|-|1|1.1||
|KF|Flicker noise coefficient|-|0|||
|AF|Flicker noise exponent|-|1|||
|NLEV|Noise equation selector|-|1|3||
|GDSNOI|Channel noise coefficient for nlev=3||1.0|2.0||
|FC|Coefficient for forward-bias depletion capacitance formula||0.5|||
|TNOM|Parameter measurement temperature|◦C|27|50||
|TCV|Threshold voltage temperature coefficient|1/°C|0.0|0.1||
|BEX|Mobility temperature exponent|-|0.0|1.1||


-----

Additional to the standard thermal and flicker noise model an alternative thermal channel noise
model is implemented and is selectable by setting NLEV parameter to 3. This follows in a
correct channel thermal noise in the linear region.

_Snoise =_ [2] _GDSNOI_ (9.6)

3 [4][kT][ ·] _[BETA]_ _[·][Vgst][ (][1]_ [+]1[α]+[ +]α[α] [2][)]


with


_α =_


� _vds_
1 if vgs _VTO_ _vds_
_−_ _vgs−VTO_ _[,]_ _−_ _≥_ (9.7)

0, else


### 9.2.2 JFET level 2 Parker Skellern model

[The level 2 model is an improvement to level 1. Details are available from Macquarie Univer-](http://www.engineering.mq.edu.au/research/groups/cnerf/psmodel/index.htm)
[sity. Some important items are:](http://www.engineering.mq.edu.au/research/groups/cnerf/psmodel/index.htm)

  - The description maintains strict continuity in its high-order derivatives, which is essential
for prediction of distortion and intermodulation.

  - Frequency dependence of output conductance and transconductance is described as a
function of bias.

  - Both drain-gate and source-gate potentials modulate the pinch-off potential, which is consistent with S-parameter and pulsed-bias measurements.

  - Self-heating varies with frequency.

  - Extreme operating regions - subthreshold, forward gate bias, controlled resistance, and
breakdown regions - are included.

  - Parameters provide independent fitting to all operating regions. It is not necessary to
compromise one region in favor of another.

  - Strict drain-source symmetry is maintained. The transition during drain-source potential
reversal is smooth and continuous.

[The model equations are described in this pdf document and in [19].](http://www.engineering.mq.edu.au/research/groups/cnerf/psfet.pdf)


-----

|Name|Description|Unit Type|Default|
|---|---|---|---|
|ID|Device IDText|Text|PF1|
|ACGAM|Capacitance modulation|None|0|
|BETA|Linear-region transconductance scale|None|10−4|
|CGD|Zero-bias gate-source capacitance|Capacitance|0 F|
|CGS|Zero-bias gate-drain capacitance|Capacitance|0 F|
|DELTA|Thermal reduction coefficient|None|0 W|
|FC|Forward bias capacitance parameter|None|0.5|
|HFETA|High-frequency VGS feedback parameter|None|0|
|HFE1|HFGAM modulation by VGD|None|0V−1|
|HFE2|HFGAM modulation by VGS|None|0 V−1|
|HFGAM|High-frequency VGD feedback parameter|None|0|
|HFG1|HFGAM modulation by VSG|None|0 V−1|
|HFG2|HFGAM modulation by VDG|None|0 V−1|
|IBD|Gate-junction breakdown current|Current|0 A|
|IS|Gate-junction saturation current|Current|10−14A|
|LFGAM|Low-frequency feedback parameter|None|0|
|LFG1|LFGAM modulation by VSG|None|0 V−1|
|LFG2|LFGAM modulation by VDG|None|0 V−1|
|MVST|Subthreshold modulation|None|0 V−1|
|N|Gate-junction ideality factor|None|1|
|P|Linear-region power-law exponent|None|2|
|Q|Saturated-region power-law exponent|None|2|
|RS|Source ohmic resistance|Resistance|0 Ohm|
|RD|Drain ohmic resistance|Resistance|0 Ohm|
|TAUD|Relaxation time for thermal reduction|Time|0 s|
|TAUG|Relaxation time for gamma feedback|Time|0 s|
|VBD|Gate-junction breakdown potential|Voltage|1 V|
|VBI|Gate-junction potential|Voltage|1 V|
|VST|Subthreshold potential|Voltage|0 V|
|VTO|Threshold voltage|Voltage|-2.0 V|
|XC|Capacitance pinch-off reduction factor|None|0|
|XI|Saturation-knee potential factor|None|1000|
|Z|Knee transition parameter|None|0.5|
|RG|Gate ohmic resistance|Resistance|0 Ohm|
|LG|Gate inductance|Inductance|0 H|
|LS|Source inductance|Inductance|0 H|
|LD|Drain inductance|Inductance|0 H|
|CDSS|Fixed Drain-source capacitance|Capacitance|0 F|
|AFAC|Gate-width scale factor|None|1|
|NFING|Number of gate fingers scale factor|None|1|
|TNOM|Nominal Temperature (Not implemented)|Temperature|300 K|
|TEMP|Temperature|Temperature|300 K|


-----

