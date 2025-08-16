# Chapter 11

 MOSFETs

Ngspice supports all the original mosfet models present in SPICE3f5 and almost all the newer
ones that have been published and made open-source. Both bulk and SOI (Silicon on Insulator) models are available. When compiled with the cider option, ngspice implements the four
terminals numerical model that can be used to simulate a MOSFET (please refer to numerical
modeling documentation for additional information and examples).

## 11.1 MOSFET devices

General form:
```
   MXXXXXXX nd ng ns nb mname <m=val> <l=val> <w=val>
  + <ad=val> <as=val> <pd=val> <ps=val> <nrd=val>
  + <nrs=val> <off> <ic=vds, vgs, vbs> <temp=t>

```
Examples:
```
  M1 24 2 0 20 TYPE1
   M31 2 17 6 10 MOSN L=5U W=2U
  M1 2 9 3 0 MOSP L=10U W=5U AD=100P AS=100P PD=40U PS=40U

```
Note the suffixes in the example: the suffix ‘u’ specifies microns (1e-6 m) and ‘p’ sq-microns
(1e-12 m[2]).

The instance card for MOS devices starts with the letter ’M’. nd, ng, ns, and nb are the drain,
gate, source, and bulk (substrate) nodes, respectively. mname is the model name and m is the
multiplicity parameter, which simulates ‘m’ paralleled devices. All MOS models support the
‘m’ multiplier parameter. Instance parameters l and w, channel length and width respectively,
are expressed in meters. The areas of drain and source diffusions: ad and as, in squared meters
(m[2]).

If any of l, w, ad, or as are not specified, default values are used. The use of defaults simplifies
input file preparation, as well as the editing required if device geometries are to be changed. pd
and ps are the perimeters of the drain and source junctions, in meters. nrd and nrs designate
the equivalent number of squares of the drain and source diffusions; these values multiply the


-----

sheet resistance rsh specified on the .model control line for an accurate representation of the
parasitic series drain and source resistance of each transistor. pd and ps default to 0.0 while nrd
and nrs to 1.0. off indicates an (optional) initial condition on the device for dc analysis. The
(optional) initial condition specification using ic=vds,vgs,vbs is intended for use with the
```
uic option on the .tran control line, when a transient analysis is desired starting from other

```
than the quiescent operating point. See the .ic control line for a better and more convenient
way to specify transient initial conditions. The (optional) temp value is the temperature at
which this device is to operate, and overrides the temperature specification on the .option
control line.

The temperature specification is ONLY valid for level 1, 2, 3, and 6 MOSFETs, not for level 4
or 5 (BSIM) devices.

BSIM3 (v3.2 and v3.3.0), BSIM4 (v4.7 and v4.8) and BSIMSOI models are also supporting the
instance parameter delvto and mulu0 for local mismatch and NBTI (negative bias temperature
instability) modeling:

Name Parameter Units Default Example

delvto (delvt0) Threshold voltage shift _V_ 0.0 0.07

mulu0 Low-field mobility multiplier (U0)   - 1.0 0.9

## 11.2 MOSFET models (NMOS/PMOS)

MOSFET models are the central part of ngspice, probably because they are the most widely
used devices in the electronics world. Ngspice provides all the MOSFETs implemented in the
[original Spice3f and adds several models developed by UC Berkeley’s Device Group and other](http://www-device.eecs.berkeley.edu/bsim/)
independent groups.

Each model is invoked with a .model card. A minimal version is:
```
.model MOSN NMOS level=8 version=3.3.0

```
The model name MOSN corresponds to the model name in the instance card (see 11.1). Parameter NMOS selects an n-channel device, PMOS would point to a p-channel transistor. The
```
level and version parameters select the specific model. Further model parameters are op
```
tional and replace ngspice default values. Due to the large number of parameters (more than
100 for modern models), model cards may be stored in extra files and loaded into the netlist by
the .include (2.6) command. Model cards are specific for a an IC manufacturing process and
are typically provided by the IC foundry. Some generic parameter sets, not linked to a specific
[process, are made available by the model developers, e.g. UC Berkeley’s Device Group for](http://www-device.eecs.berkeley.edu/bsim/)
BSIM4 and BSIMSOI.

Ngspice provides several MOSFET device models, which differ in the formulation of the I-V
characteristic, and are of varying complexity. Models available are listed in table 11.1. Current
models for IC design are BSIM3 (11.2.10, down to channel length of 0.25 µm), BSIM4 (11.2.11,
below 0.25 µm), BSIMSOI (11.2.13, silicon-on-insulator devices), HiSIM2 and HiSIM_HV
(11.2.15, surface potential models for standard and high voltage/high power MOS devices).

### 11.2.1 MOS Level 1

This model is also known as the ‘Shichman-Hodges’ model. This is the first model written and
the one often described in the introductory textbooks for electronics. This model is applicable

|Name|Parameter|Units|Default|Example|
|---|---|---|---|---|
|delvto (delvt0)|Threshold voltage shift|V|0.0|0.07|
|mulu0|Low-field mobility multiplier (U0)|-|1.0|0.9|


-----

|Notes|This is the classical quadratic model.|Described in [2]|A semi-empirical model (see [1])|in [3] Described|Described in [5]|Described in [2]|Col8|extensions by Alan Gillespie|extensions by Serban Popescu|Multi version code|Described in [13]|Col13|Multi version code|Col15|Col16|Col17|adms configured|adms configured|Col20|Col21|Col22|Col23|Col24|High Voltage Version for LDMOS|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|References|||||||||||||||||||||||||
|Developer|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|Alan Gillespie|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|Berkeley|EPFL|Gildenblatt|Berkeley|Berkeley|Berkeley|Southampton|Hiroshima|Hiroshima|
|Version|-|-||||||3.0|3.1|3.2 - 3.2.4|3.3.0|4.3.1|4.0 - 4.5|4.6.5|4.7.0|4.8.1||1.0.2||||SOI3|2.8.0|1.2.4/2.2.0|
|Model|Shichman-Hodges|Grove-Frohman|||||||||||||||||||||||
|Name|MOS1|MOS2|MOS3|BSIM1|BSIM2|MOS6|MOS9|BSIM3v0|BSIM3v1|BSIM3v32|BSIM3|B4SOI|BSIM4v5|BSIM4v6|BSIM4v7|BSIM4|EKV|PSP|B3SOIFD|B3SOIDD|B3SOIPD|STAG|HiSIM2|HiSIM_HV|
|Level|1|2|3|4|5|6|9|8, 49|8, 49|8, 49|8, 49|10, 58|14, 54|14, 54|14, 54|14, 54|44|45|55|56|57|60|68|73|


Table 11.1: MOSFET model summary


-----

only to long channel devices. The use of Meyer’s model for the C-V part makes it non charge
conserving.

### 11.2.2 MOS Level 2

This model tries to overcome the limitations of the Level 1 model addressing several shortchannel effects, like velocity saturation. The implementation of this model is complicated and
this leads to many convergence problems. C-V calculations can be done with the original Meyer
model (non charge conserving).

### 11.2.3 MOS Level 3

This is a semi-empirical model derived from the Level 2 model. In the 80s this model has often
been used for digital design and, over the years, has proved to be robust. A discontinuity in the
model with respect to the KAPPA parameter has been detected (see [10]). The supplied fix has
been implemented in Spice3f2 and later. Since this fix may affect parameter fitting, the option
```
badmos3 may be set to use the old implementation (see the section on simulation variables and

```
the .options line). Ngspice level 3 implementation takes into account length and width mask
adjustments (xl and xw) and device width narrowing due to diffusion (wd).

### 11.2.4 MOS Level 6

This model is described in [2]. The model can express the current characteristics of shortchannel MOSFETs at least down to 0.25 µm channel-length, GaAs FET, and resistance inserted
MOSFETs. The model evaluation time is about 1/3 of the evaluation time of the SPICE3 mos
level 3 model. The model also enables analytical treatments of circuits in short-channel region
and makes up for a missing link between a complicated MOSFET current characteristics and
circuit behaviors in the deep submicron region.

### 11.2.5 Notes on Level 1-6 models

The dc characteristics of the level 1 through level 3 MOSFETs are defined by the device parameters vto, kp, lambda, phi and gamma. These parameters are computed by ngspice if process
parameters (nsub, tox, ...) are given, but users specified values always override. vto is positive (negative) for enhancement mode and negative (positive) for depletion mode N-channel
(P-channel) devices.

Charge storage is modeled by three constant capacitors, cgso, cgdo, and cgbo, which represent
overlap capacitances, by the nonlinear thin-oxide capacitance that is distributed among the gate,
source, drain, and bulk regions, and by the nonlinear depletion-layer capacitances for both
substrate junctions divided into bottom and periphery, which vary as the mj and mjsw power
of junction voltage respectively, and are determined by the parameters cbd, cbs, cj, cjsw, mj,
```
mjsw and pb.

```
Charge storage effects are modeled by the piecewise linear voltages-dependent capacitance model proposed by Meyer. The thin-oxide charge-storage effects are treated slightly different for


-----

the level 1 model. These voltage-dependent capacitances are included only if tox is specified
in the input description and they are represented using Meyer’s formulation.

There is some overlap among the parameters describing the junctions, e.g. the reverse current
can be input either as is (in A) or as js (in _[A]/m[2]). Whereas the first is an absolute value the_
second is multiplied by ad and as to give the reverse current of the drain and source junctions
respectively.

This methodology has been chosen since there is no sense in relating always junction characteristics with ad and as entered on the device line; the areas can be defaulted. The same idea
applies also to the zero-bias junction capacitances cbd and cbs (in F) on one hand, and cj (in
_F/m[2]) on the other._

The parasitic drain and source series resistance can be expressed as either rd and rs (in ohms)
or rsh (in ohms/sq.), the latter being multiplied by the number of squares nrd and nrs input on
the device line.

**NGSPICE level 1, 2, 3 and 6 parameters**

|Name|Parameter|Units|Default|Example|
|---|---|---|---|---|
|LEVEL|Model index|-|1||
|VTO|Zero-bias threshold voltage (V ) T0|V|0.0|1.0|
|KP|Transconductance parameter|A/V 2|2.0e-5|3.1e-5|
|GAMMA|Bulk threshold parameter|√ V|0.0|0.37|
|PHI|Surface potential (U)|V|0.6|0.65|
|LAMBDA|Channel length modulation (MOS1 and MOS2 only) (λ)|1/V|0.0|0.02|
|RD|Drain ohmic resistance|Ω|0.0|1.0|
|RS|Source ohmic resistance|Ω|0.0|1.0|
|CBD|Zero-bias B-D junction capacitance|F|0.0|20fF|
|CBS|Zero-bias B-S junction capacitance|F|0.0|20fF|
|IS|Bulk junction saturation current (I ) S|A|1.0e-14|1.0e-15|
|PB|Bulk junction potential|V|0.8|0.87|
|CGSO|Gate-source overlap capacitance per meter channel width|F/m|0.0|4.0e-11|
|CGDO|Gate-drain overlap capacitance per meter channel width|F/m|0.0|4.0e-11|
|CGBO|Gate-bulk overlap capacitance per meter channel width|F/m|0.0|2.0e-11|


-----

|Name|Parameter|Units|Default|Example|
|---|---|---|---|---|
|RSH|Drain and source diffusion sheet resistance|Ω/□|0.0|10|
|CJ|Zero-bias bulk junction bottom cap. per sq-meter of junction area|F/m2|0.0|2.0e-4|
|MJ|Bulk junction bottom grading coeff.|-|0.5|0.5|
|CJSW|Zero-bias bulk junction sidewall cap. per meter of junction perimeter|F/m|0.0|1.0e-9|
|MJSW|Bulk junction sidewall grading coeff.|-|0.50 (level1) 0.33 (level2,3)||
|JS|Bulk junction saturation current||||
|TOX|Oxide thickness|m|1.0e-7|1.0e-7|
|NSUB|Substrate doping|cm−3|0.0|4.0e15|
|NSS|Surface state density|cm−2|0.0|1.0e10|
|NFS|Fast surface state density|cm−2|0.0|1.0e10|
|TPG|Type of gate material: +1 opp. to substrate, -1 same as substrate, 0 Al gate|-|1.0||
|XJ|Metallurgical junction depth|m|0.0|1M|
|LD|Lateral diffusion|m|0.0|0.8M|
|UO|Surface mobility|cm2/V·sec|600|700|
|UCRIT|Critical field for mobility degradation (MOS2 only)|V/cm|1.0e4|1.0e4|
|UEXP|Critical field exponent in mobility degradation (MOS2 only)|-|0.0|0.1|
|UTRA|Transverse field coeff. (mobility) (deleted for MOS2)|-|0.0|0.3|
|VMAX|Maximum drift velocity of carriers|m/s|0.0|5.0e4|
|NEFF|Total channel-charge (fixed and mobile) coefficient (MOS2 only)|-|1.0|5.0|
|KF|Flicker noise coefficient|-|0.0|1.0e-26|
|AF|Flicker noise exponent|-|1.0|1.2|
|FC|Coefficient for forward-bias depletion capacitance formula|-|0.5||
|DELTA|Width effect on threshold voltage (MOS2 and MOS3)|-|0.0|1.0|
|THETA|Mobility modulation (MOS3 only)|1/V|0.0|0.1|


-----

|Name|Parameter|Units|Default|Example|
|---|---|---|---|---|
|ETA|Static feedback (MOS3 only)|-|0.0|1.0|
|KAPPA|Saturation field factor (MOS3 only)|-|0.2|0.5|
|TNOM|Parameter measurement temperature|◦C|27|50|


### 11.2.6 MOS Level 9

Documentation is not available..

### 11.2.7 BSIM Models

[Ngspice implements many of the BSIM models developed by Berkeley’s BSIM group. BSIM](http://bsim.berkeley.edu/)
stands for Berkeley Short-Channel IGFET Model and groups a class of models that is continuously updated. BSIM3 (11.2.10) and BSIM4 (11.2.11) are industry standards for CMOS
processes down to 0.15 µm (BSIM3) and below (BSIM4), are very stable and are supported by
model parameter sets from foundries all over the world. BSIM1 and BSIM2 are obsolete today.

In general, all parameters of BSIM models are obtained from process characterization, in particular level 4 and level 5 (BSIM1 and BSIM2) parameters can be generated automatically. J.
Pierret [4] describes a means of generating a ‘process’ file, and the program ngproc2mod provided with ngspice converts this file into a sequence of BSIM1 .model lines suitable for inclusion
in an ngspice input file.

Parameters marked below with an * in the l/w column also have corresponding parameters with
a length and width dependency. For example, vfb is the basic parameter with units of Volts,
and lvfb and wvfb also exist and have units of Volt-meter.

The formula

_PL_ _PW_
_P = P0 +_ + (11.1)

_Leffective_ _Weffective_


is used to evaluate the parameter for the actual device specified with

_Leffective = Linput_ _DL_ (11.2)
_−_

_Weffective = Winput_ _DW_ (11.3)
_−_

Note that unlike the other models in ngspice, the BSIM models are designed for use with a
process characterization system that provides all the parameters, thus there are no defaults for
the parameters, and leaving one out is considered an error. For an example set of parameters and
the format of a process file, see the SPICE2 implementation notes [3]. For more information on
BSIM2, see reference [5]. BSIM3 (11.2.10) and BSIM4 (11.2.11) represent state of the art for
submicron and deep submicron IC design.


-----

### 11.2.8 BSIM1 model (level 4)

BSIM1 model (the first is a long series) is an empirical model. Developers placed less emphasis on device physics and based the model on parametrical polynomial equations to model
the various physical effects. This approach pays in terms of circuit simulation behavior but the
accuracy degrades in the submicron region. A known problem of this model is the negative output conductance and the convergence problems, both related to poor behavior of the polynomial
equations.

**Ngspice BSIM (level 4) parameters**

|Name|Parameter|Units|l/w|
|---|---|---|---|
|VFB|Flat-band voltage|V|*|
|PHI|Surface inversion potential|V|*|
|K1|Body effect coefficient|√ V|*|
|K2|Drain/source depletion charge-sharing coefficient|-|*|
|ETA|Zero-bias drain-induced barrier-lowering coefficient|-|*|
|MUZ|Zero-bias mobility|cm2/V·sec||
|DL|Shortening of channel|µm||
|DW|Narrowing of channel|µm||
|U0|Zero-bias transverse-field mobility degradation coefficient|1/V|*|
|U1|Zero-bias velocity saturation coefficient|µ/V|*|
|X2MZ|Sens. of mobility to substrate bias at v=0|cm2/V 2 ·sec|*|
|X2E|Sens. of drain-induced barrier lowering effect to substrate bias|1/V|*|
|X3E|Sens. of drain-induced barrier lowering effect to drain bias at V = V ds dd|1/V|*|
|X2U0|Sens. of transverse field mobility degradation effect to substrate bias|1/V 2|*|
|X2U1|Sens. of velocity saturation effect to substrate bias|µm/V 2|*|
|MUS|Mobility at zero substrate bias and at V = V ds dd|cm2/V 2sec||
|X2MS|Sens. of mobility to substrate bias at V = V ds dd|cm2/V 2sec|*|
|X3MS|Sens. of mobility to drain bias at V = V ds dd|cm2/V 2sec|*|
|X3U1|Sens. of velocity saturation effect on drain bias at Vds=Vdd|µm/V 2|*|
|TOX|Gate oxide thickness|µm||
|TEMP|Temperature where parameters were measured|◦C||
|VDD|Measurement bias range|V||
|CGDO|Gate-drain overlap capacitance per meter channel width|F/m||
|CGSO|Gate-source overlap capacitance per meter channel width|F/m||


-----

|Name|Parameter|Units|l/w|
|---|---|---|---|
|CGBO|Gate-bulk overlap capacitance per meter channel length|F/m||
|XPART|Gate-oxide capacitance-charge model flag|-||
|N0|Zero-bias subthreshold slope coefficient|-|*|
|NB|Sens. of subthreshold slope to substrate bias|-|*|
|ND|Sens. of subthreshold slope to drain bias|-|*|
|RSH|Drain and source diffusion sheet resistance|Ω/□||
|JS|Source drain junction current density|A/m2||
|PB|Built in potential of source drain junction|V||
|MJ|Grading coefficient of source drain junction|-||
|PBSW|Built in potential of source, drain junction sidewall|V||
|MJSW|Grading coefficient of source drain junction sidewall|-||
|CJ|Source drain junction capacitance per unit area|F/m2||
|CJSW|source drain junction sidewall capacitance per unit length|F/m||
|WDF|Source drain junction default width|m||
|DELL|Source drain junction length reduction|m||

```
xpart = 0 selects a 40/60 drain/source charge partition in saturation, while xpart=1 selects

```
a 0/100 drain/source charge partition. nd, ng, and ns are the drain, gate, and source nodes,
respectively. mname is the model name, area is the area factor, and off indicates an (optional)
initial condition on the device for dc analysis. If the area factor is omitted, a value of 1.0 is
assumed. The (optional) initial condition specification, using ic=vds,vgs is intended for use
with the uic option on the .tran control line, when a transient analysis is desired starting from
other than the quiescent operating point. See the .ic control line for a better way to set initial
conditions.

### 11.2.9 BSIM2 model (level 5)

This model contains many improvements over BSIM1 and is suitable for analog simulation.
Nevertheless, even BSIM2 breaks transistor operation into several distinct regions and this leads
to discontinuities in the first derivative in C-V and I-V characteristics that can cause numerical
problems during simulation.

### 11.2.10 BSIM3 model (levels 8, 49)

BSIM3 solves the numerical problems of previous models with the introduction of smoothing
functions. It adopts a single equation to describe device characteristics in the operating regions.
This approach eliminates the discontinuities in the I-V and C-V characteristics. The origi[nal model, BSIM3 evolved through three versions: BSIM3v1, BSIM3v2 and BSIM3v3. Both](http://bsim.berkeley.edu/models/bsim3/)
BSIM3v1 and BSIM3v2 had suffered from many mathematical problems and were replaced by
BSIM3v3. The latter is the only surviving release and has itself a long revision history.

The following table summarizes the story of this model:


-----

|Release|Date|Notes|Version flag|
|---|---|---|---|
|BSIM3v3.0|10/30/1995||3.0|
|BSIM3v3.1|12/09/1996||3.1|
|BSIM3v3.2|06/16/1998|Revisions available: BSIM3v3.2.2, BSIM3v3.2.3, and BSIM3v3.2.4 Parallel processing with OpenMP is available for BSIM3v3.2.4.|3.2, 3.2.2, 3.2.3, 3.2.4|
|BSIM3v3.3|07/29/2005|Parallel processing with OpenMP is available for this model.|3.3.0|


BSIM3v2 and 3v3 models has proved for accurate use in 0.18 µm technologies. The model is
[publicly available as source code form from University of California, Berkeley.](http://bsim.berkeley.edu/BSIM4/BSIM3/ftpv330.zip)

[A detailed description is given in the user’s manual available from here .](http://ngspice.sourceforge.net/external-documents/models/bsim330_manual.pdf)

We recommend that you use only the most recent BSIM3 models (version 3.3.0), because it
contains corrections to all known bugs. To achieve that, change the version parameter in your
modelcard files to
```
VERSION = 3.3.0.

```
If no version number is given in the .model card, this (newest) version is selected as the default.

BSIM3v3.2.4 supports the extra model parameter lmlt on channel length scaling and is still
used by many foundries today.

The older models will not be supported, they are made available for reference only.

### 11.2.11 BSIM4 model (levels 14, 54)

This is the newest class of the BSIM family and introduces noise modeling and extrinsic parasitics. BSIM4, as the extension of BSIM3 model, addresses the MOSFET physical effects into
sub-100nm regime. It is a physics-based, accurate, scalable, robust and predictive MOSFET
SPICE model for circuit simulation and CMOS technology development. It is developed by
the BSIM Research Group in the Department of Electrical Engineering and Computer Sciences
[(EECS) at the University of California, Berkeley (see BSIM4 home page). BSIM4 has a long](http://bsim.berkeley.edu/models/bsim4/)
revision history, which is summarized below.

**Release** **Date** **Notes** **Version flag**

BSIM4.0.0 03/24/2000

BSIM4.1.0 10/11/2000

BSIM4.2.0 04/06/2001

BSIM4.2.1 10/05/2001 - 4.2.1

BSIM4.3.0 05/09/2003 - 4.3.0

BSIM4.4.0 03/04/2004 - 4.4.0

BSIM4.5.0 07/29/2005 - ** 4.5.0

BSIM4.6.0 12/13/2006

...

BSIM4.6.5 09/09/2009 - ** 4.6.5

BSIM4.7.0 04/08/2011 - ** 4.7

BSIM4.8.1 15/02/2017 - ** 4.8

*) supported in ngspice, using e.g. the version=<version flag> flag in the parameter file.

|Release|Date|Notes|Version flag|
|---|---|---|---|
|BSIM4.0.0|03/24/2000|||
|BSIM4.1.0|10/11/2000|||
|BSIM4.2.0|04/06/2001|||
|BSIM4.2.1|10/05/2001|*|4.2.1|
|BSIM4.3.0|05/09/2003|*|4.3.0|
|BSIM4.4.0|03/04/2004|*|4.4.0|
|BSIM4.5.0|07/29/2005|* **|4.5.0|
|BSIM4.6.0|12/13/2006|||
|...||||
|BSIM4.6.5|09/09/2009|* **|4.6.5|
|BSIM4.7.0|04/08/2011|* **|4.7|
|BSIM4.8.1|15/02/2017|* **|4.8|


-----

**) Parallel processing using OpenMP support is available for this model.

Details of any revision are to be found in the Berkeley user’s manuals, a pdf download of the
[most recent edition is to be found here.](http://ngspice.sourceforge.net/external-documents/models/BSIM480_Manual.pdf)

We recommend that you use only the most recent BSIM4 model (version 4.8.1), because it
contains corrections to all known bugs. To achieve that, change the version parameter in your
modelcard files to
```
VERSION = 4.8.

```
If no version number is given in the .model card, this (newest) version is selected as the default.
The older models will typically not be supported, they are made available for reference only.

### 11.2.12 EKV model

Level 44 model (EKV) is not available in the standard distribution since it is not released in
[source form by the EKV group. To obtain the code please refer to the (EKV model home page,](http://ekv.epfl.ch/)
EKV group home page). A verilog-A version is available contributed by Ivan Riis Nielsen
11/2006.

### 11.2.13 BSIMSOI models (levels 10, 58, 55, 56, 57)

BSIMSOI is a SPICE compact model for SOI (Silicon-On-Insulator) circuit design, created by
[University of California at Berkeley. This model is formulated on top of the BSIM3 frame-](http://bsim.berkeley.edu/models/bsimsoi/)
work. It shares the same basic equations with the bulk model so that the physical nature and
smoothness of BSIM3v3 are retained. Four models are supported in ngspice, those based on
BSIM3 and modeling fully depleted (FD, level 55), partially depleted (PD, level 57) and both
(DD, level 56), as well as the modern BSIMSOI version 4 model (levels 10, 58). Detailed des[criptions are beyond the scope of this manual, but see e.g. BSIMSOIv4.4 User Manual for a](http://ngspice.sourceforge.net/external-documents/models/BSIMSOIv4.4_UsersManual.pdf)
very extensive description of the recent model version. OpenMP support is available for levels
10, 58, version 4.4.

### 11.2.14 SOI3 model (level 60)

see literature citation [18] for a description.

### 11.2.15 HiSIM models of the University of Hiroshima

[There are two model implementations available - see also HiSIM Research Center:](https://www.hisim.hiroshima-u.ac.jp/index.php?id=87)

1. HiSIM2 model: Surface-Potential-Based MOSFET Model for Circuit Simulation version
[2.8.0 - level 68 (see link to HiSIM2 for source code and manual).](http://home.hiroshima-u.ac.jp/usdl/HiSIM2/HiSIM_2.5.1_Release_20110407.zip)

2. HiSIM_HV model: Surface-Potential-Based HV/LD-MOSFET Model for Circuit Simu[lation version 1.2.4 and 2.2.0 - level 73 (see link to HiSIM_HV for source code and](http://home.hiroshima-u.ac.jp/usdl/HiSIM_HV/C-Code/HiSIM_HV_1.2.2_Release_20110629.zip)
manual).


-----

