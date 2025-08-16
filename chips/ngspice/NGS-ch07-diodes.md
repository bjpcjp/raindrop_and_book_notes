# Chapter 7

 Diodes

## 7.1 Junction Diodes

General form:
```
   DXXXXXXX n+ n- mname <area=val> <m=val> <pj=val> <off>
  + <ic=vd> <temp=val> <dtemp=val>

```
Examples:
```
   DBRIDGE 2 10 DIODE1
   DCLMP 3 7 DMOD AREA=3.0 IC=0.2

```
The pn junction (diode) implemented in ngspice expands the one found in SPICE3f5. Perimeter
effects and high injection level have been introduced into the original model and temperature
dependence of some parameters has been added. n+ and n- are the positive and negative nodes,
respectively. mname is the model name. Instance parameters may follow, dedicated to only
the diode described on the respective line. `area is the area scale factor, which may scale`
the saturation current given by the model parameters (and others, see table below). pj is the
perimeter scale factor, scaling the sidewall saturation current and its associated capacitance. m
is a multiplier of area and perimeter, and off indicates an (optional) starting condition on the
device for dc analysis. If the area factor is omitted, a value of 1.0 is assumed. The (optional)
initial condition specification using ic is intended for use with the uic option on the .tran
control line, when a transient analysis is desired starting from other than the quiescent operating
point. You should supply the initial voltage across the diode there. The (optional) temp value
is the temperature at which this device is to operate, and overrides the temperature specification
on the .option control line. The temperature of each instance can be specified as an offset to
the circuit temperature with the dtemp option.

## 7.2 Diode Model (D)

The dc characteristics of the diode are determined by the parameters is and n. An ohmic
resistance, rs, is included. Charge storage effects are modeled by a transit time, tt, and a


-----

nonlinear depletion layer capacitance that is determined by the parameters cjo, vj, and m. The
temperature dependence of the saturation current is defined by the parameters eg, the energy,
and xti, the saturation current temperature exponent. The nominal temperature where these
parameters were measured is tnom, which defaults to the circuit-wide value specified on the
```
.options control line. Reverse breakdown is modeled by an exponential increase in the reverse

```
diode current and is determined by the parameters bv and ibv (both of which are positive
numbers).

**Junction DC parameters**

**_Name_** **_Parameter_** **_Units_** **_Default_** **_Example_** **_Scale factor_**

BV Reverse breakdown voltage _V_ ∞ 40

IBV Current at breakdown voltage _A_ 1.0e-3 1.0e-4

IK (IKF) Forward knee current _A_ 1.0e-3 1.0e-6

IKR Reverse knee current _A_ 1.0e-3 1.0e-6

IS (JS) Saturation current _A_ 1.0e-14 1.0e-16 area

JSW Sidewall saturation current _A_ 1.0e-14 1.0e-15 perimeter

N Emission coefficient - 1 1.5

RS Ohmic resistance Ω 0.0 100 1/area

**Junction capacitance parameters**

|Name|Parameter|Units|Default|Example|Scale factor|
|---|---|---|---|---|---|
|BV|Reverse breakdown voltage|V|∞|40||
|IBV|Current at breakdown voltage|A|1.0e-3|1.0e-4||
|IK (IKF)|Forward knee current|A|1.0e-3|1.0e-6||
|IKR|Reverse knee current|A|1.0e-3|1.0e-6||
|IS (JS)|Saturation current|A|1.0e-14|1.0e-16|area|
|JSW|Sidewall saturation current|A|1.0e-14|1.0e-15|perimeter|
|N|Emission coefficient|-|1|1.5||
|RS|Ohmic resistance|Ω|0.0|100|1/area|

|Name|Parameter|Units|Default|Example|Scale factor|
|---|---|---|---|---|---|
|CJO (CJ0)|Zero-bias junction bottom-wall capacitance|F|0.0|2pF|area|
|CJP (CJSW)|Zero-bias junction sidewall capacitance|F|0.0|.1pF|perimeter|
|FC|Coefficient for forward-bias depletion bottom-wall capacitance formula|-|0.5|-||
|FCS|Coefficient for forward-bias depletion sidewall capacitance formula|-|0.5|-||
|M (MJ)|Area junction grading coefficient|-|0.5|0.5||
|MJSW|Periphery junction grading coefficient|-|0.33|0.5||
|VJ (PB)|Junction potential|V|1|0.6||
|PHP|Periphery junction potential|V|1|0.6||
|TT|Transit-time|sec|0|0.1ns||


-----

**Temperature effects**

**_Name_** **_Parameter_** **_Units_** **_Default_** **_Example_**

1.11

EG Activation energy _eV_ 1.11 0.69

0.67

TM1 1st order tempco for MJ 1/[◦]C 0.0 
TM2 2nd order tempco for MJ 1/[◦]C[2] 0.0 
TNOM (TREF) Parameter measurement temperature _◦C_ 27 50

TRS1 (TRS) 1st order tempco for RS 1/[◦]C 0.0 
TRS2 2nd order tempco for RS 1/[◦]C[2] 0.0 
TM1 1st order tempco for MJ 1/[◦]C 0.0 
TM2 2nd order tempco for MJ 1/[◦]C[2] 0.0 
TTT1 1st order tempco for TT 1/[◦]C 0.0 
TTT2 2nd order tempco for TT 1/[◦]C[2] 0.0 
3.0 pn
XTI Saturation current temperature exponent - 3.0
2.0 Sbd

TLEV Diode temperature equation selector - 0

TLEVC Diode capac. temperature equation selector - 0

CTA (CTC) Area junct. cap. temperature coefficient 1/[◦]C 0.0 
CTP Perimeter junct. cap. temperature coefficient 1/[◦]C 0.0 
TCV Breakdown voltage temperature coefficient 1/[◦]C 0.0 
**Noise modeling**

**_Name_** **_Parameter_** **_Units_** **_Default_** **_Example_** **_Scale factor_**

KF Flicker noise coefficient - 0

AF Flicker noise exponent - 1

Diode models may be described in the input file (or an file included by .inc) according to the
following example:

General form:
```
  .model mname type(pname1=pval1 pname2=pval2 ... )

```
Examples:
```
  .model DMOD D (bf=50 is=1e-13 vbf=50)

## 7.3 Diode Equations

```
The junction diode is the basic semiconductor device and the simplest one in ngspice, but its
model is quite complex, even when not all the physical phenomena affecting a pn junction are
handled. The diode is modeled in three different regions:

|Name|Parameter|Units|Default|Example|
|---|---|---|---|---|
|EG|Activation energy|eV|1.11|1.11 Si 0.69 Sbd 0.67 Ge|
|TM1|1st order tempco for MJ|1/◦C|0.0|-|
|TM2|2nd order tempco for MJ|1/◦C2|0.0|-|
|TNOM (TREF)|Parameter measurement temperature|◦C|27|50|
|TRS1 (TRS)|1st order tempco for RS|1/◦C|0.0|-|
|TRS2|2nd order tempco for RS|1/◦C2|0.0|-|
|TM1|1st order tempco for MJ|1/◦C|0.0|-|
|TM2|2nd order tempco for MJ|1/◦C2|0.0|-|
|TTT1|1st order tempco for TT|1/◦C|0.0|-|
|TTT2|2nd order tempco for TT|1/◦C2|0.0|-|
|XTI|Saturation current temperature exponent|-|3.0|3.0 pn 2.0 Sbd|
|TLEV|Diode temperature equation selector|-|0||
|TLEVC|Diode capac. temperature equation selector|-|0||
|CTA (CTC)|Area junct. cap. temperature coefficient|1/◦C|0.0|-|
|CTP|Perimeter junct. cap. temperature coefficient|1/◦C|0.0|-|
|TCV|Breakdown voltage temperature coefficient|1/◦C|0.0|-|

|Name|Parameter|Units|Default|Example|Scale factor|
|---|---|---|---|---|---|
|KF|Flicker noise coefficient|-|0|||
|AF|Flicker noise exponent|-|1|||


-----

  - Forward bias: the anode is more positive than the cathode, the diode is ‘on’ and can
conduct large currents. To avoid convergence problems and unrealistic high current, it is
prudent to specify a series resistance to limit current with the rs model parameter.

  - Reverse bias: the cathode is more positive than the anode and the diode is ‘off’. A reverse
bias diode conducts a small leakage current.

  - Breakdown: the breakdown region is modeled only if the bv model parameter is given.
When a diode enters breakdown the current increases exponentially (remember to limit
it); bv is a positive value.

**Parameters Scaling**

Model parameters are scaled using the unit-less parameters area and pj and the multiplier m as
depicted below:

_AREAe f f = AREA_ _m_

_PJe f f = PJ_ _m_

_ISe f f = IS_ _AREAef f +_ JSW _PJef f_

_IBVe f f = IBV_ _AREAef f_

_IKe f f = IK_ _AREAef f_

_IKRe f f = IKR_ _AREAef f_

_CJe f f = CJ0_ _AREAef f_

_CJPe f f = CJP_ _PJef f_

**Diode DC, Transient and AC model equations**


_ID =_


 _qVD_
ISef f (e _NkT −_ 1)+VD · _GMIN,_ if VD ≥−3 _[NkT]q_


_−ISef f [1_ +( [3]qV[NkT]De [)][3][]+][V][D][ ·] _[GMIN][,]_ if − _BVe f f < VD < −3_ _[NkT]q_

 _−q(BVef f +VD)_
−ISef f (e _NkT_ )+VD · _GMIN,_ if VD ≤−BVe f f


(7.1)


The breakdown region must be described with more depth since the breakdown is not modeled
physically. As written before, the breakdown modeling is based on two model parameters: the
‘nominal breakdown voltage’ bv and the current at the onset of breakdown ibv. For the diode
model to be consistent, the current value cannot be arbitrarily chosen, since the reverse bias and
breakdown regions must match. When the diode enters breakdown region from reverse bias,
the current is calculated using the formula[1]:

_−qBV_
_Ibdwn = −ISe f f (e_ _NkT −_ 1) (7.2)

The computed current is necessary to adjust the breakdown voltage making the two regions
match. The algorithm is a little bit convoluted and only a brief description is given here:

1if you look at the source code in file diotemp.c you will discover that the exponential relation is replaced
with a first order Taylor series expansion.


-----

**Algorithm 2: Diode breakdown current calculation**

Most real diodes shows a current increase that, at high current levels, does not follow the exponential relationship given above. This behavior is due to high level of carriers injected into the
junction. High injection effects (as they are called) are modeled with ik and ikr.


_IDef f =_














�ID _ID_ _,_ if VD ≥−3 _[NkT]q_
1+

_IKe f f_

(7.3)

�ID _,_ otherwise.

_ID_

1+

_IKRe f f_


Diode capacitance is divided into two different terms:

  - Depletion capacitance

  - Diffusion capacitance

Depletion capacitance is composed by two different contributes, one associated to the bottom
of the junction (bottom-wall depletion capacitance) and the other to the periphery (sidewall
depletion capacitance). The basic equations are:

_CDiode = Cdi f fusion +Cdepletion_

Where the depletion capacitance is defined as:

_Cdepletion = Cdeplbw +Cdeplsw_

The diffusion capacitance, due to the injected minority carriers, is modeled with the transit time
```
tt:

```
_Cdi f fusion = TT_ _[∂]_ _[I][De f f]_

_∂VD_

The depletion capacitance is more complex to model, since the function used to approximate it
diverges when the diode voltage become greater than the junction built-in potential. To avoid
function divergence, the capacitance function is approximated with a linear extrapolation for
applied voltage greater than a fraction of the junction built-in potential.


_Cdeplbw_ =



CJef f (1 _−_ _[V]VJ[D]_ [)][−][MJ][,] if VD < FC _·_ VJ

CJef f 1−FC(1(−1+FCMJ)[(][1]I[+])+[MJ]MJ[)] _[VD]VJ_ _,_ otherwise. (7.4)


-----

_Cdeplsw =_



CJPef f (1 _−_ PHP[V][D] [)][−][MJSW][,] if VD < FCS _·_ PHP

CJPef f 1−FCS((11−+FCSMJSW)[(][1][+])+[MJSW]MJSW[)] _·_ PHP[VD] _,_ otherwise. (7.5)


**Temperature dependence**

The temperature affects many of the parameters in the equations above, and the following equations show how. One of the most significant parameters that varies with the temperature for a
semiconductor is the band-gap energy:

TNOM[2]
_EGnom = 1.16_ _−_ 7.02e[−][4] (7.6)

TNOM + 1108.0


_T_ [2]
_EG(T_ ) = 1.16 7.02e[−][4] (7.7)
_−_

TNOM + 1108.0

The leakage current temperature’s dependence is:

_log factor_
_IS(T_ ) = IS _e_ N (7.8)


_log factor_
_JSW_ (T ) = JSW _e_ N (7.9)


where ‘logfactor’ is defined as

EG _T_
_logfactor =_ (7.10)

_Vt(TNOM)_ _[−]_ _V[EG]t(T_ ) [+] [XTI ln][(]TNOM [)]


The contact potentials (bottom-wall an sidewall) temperature dependence is:

_T_ � _T_ EGnom
_VJ(T_ ) = VJ( 3 ln(

_·_
TNOM[)] _[−][V][t][(][T]_ [)] TNOM[)+] _Vt(TNOM)_ _[−]_ [EG]Vt([(]T[T])[)]


�
(7.11)


_T_ � _T_ EGnom
_PHP(T_ ) = PHP( 3 ln(

_·_
TNOM[)] _[−][V][t][(][T]_ [)] TNOM [)+] _Vt(TNOM)_ _[−]_ [EG]Vt([(]T[T])[)]


�
(7.12)


The depletion capacitances temperature dependence is:

� �
_CJ(T_ ) = CJ 1 + MJ(4.0e[−][4](T TNOM) + 1) (7.13)
_−_ _−_ _[VJ][(][T]_ [)]

VJ


� �
_CJSW_ (T ) = CJSW 1 + MJSW(4.0e[−][4](T TNOM) + 1) (7.14)
_−_ _−_ _[PHP][(][T]_ [)]

PHP

The transit time temperature dependence is:

_TT_ (T ) = TT(1 + TTT1(T TNOM)+ TTT2(T TNOM)[2]) (7.15)
_−_ _−_


-----

The junction grading coefficient temperature dependence is:

_MJ(T_ ) = MJ(1 + TM1(T TNOM)+ TM2(T TNOM)[2]) (7.16)
_−_ _−_

The series resistance temperature dependence is:

_RS(T_ ) = RS(1 + TRS(T TNOM)+ TRS2(T TNOM)[2]) (7.17)
_−_ _−_

**Noise model**

The diode has three noise contribution, one due to the presence of the parasitic resistance rs
and the other two (shot and flicker) due to the pn junction.

The thermal noise due to the parasitic resistance is:

_i[2]_ (7.18)
_RS_ [=][ 4][kT] [∆] _[f]_

_RS_

The shot and flicker noise contributions are:


_i[2]_ _D_ ∆ _f_ (7.19)
_d_ [=][ 2][qI][D][∆] _[f][ +][ KF][ ·]_ _[I][AF]_

_f_


-----

