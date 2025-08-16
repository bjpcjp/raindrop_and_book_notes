# Chapter 8

 BJTs

## 8.1 Bipolar Junction Transistors (BJTs)

General form:
```
   QXXXXXXX nc nb ne <ns> mname <area=val> <areac=val>
  + <areab=val> <m=val> <off> <ic=vbe,vce> <temp=val>
  + <dtemp=val>

```
Examples:
```
   Q23 10 24 13 QMOD IC=0.6, 5.0
   Q50A 11 26 4 20 MOD1
nc, nb, and ne are the collector, base, and emitter nodes, respectively. ns is the (optional) sub
```
strate node. When unspecified, ground is used. mname is the model name, area, areab, areac
are the area factors (emitter, base and collector respectively), and off indicates an (optional)
initial condition on the device for the dc analysis. If the area factor is omitted, a value of 1.0 is
assumed.

The (optional) initial condition specification using ic=vbe,vce is intended for use with the
```
uic option on a .tran control line, when a transient analysis is desired to start from other

```
than the quiescent operating point. See the .ic control line description for a better way to set
transient initial conditions. The (optional) temp value is the temperature where this device is
to operate, and overrides the temperature specification on the .option control line. Using the
```
dtemp option one can specify the instance’s temperature relative to the circuit temperature.

## 8.2 BJT Models (NPN/PNP)

```
Ngspice provides three BJT device models, which are selected by the .model card.
```
.model QMOD1 BJT level=2

```
This is the minimal version, further optional parameters listed in the table below may replace
the ngspice default parameters. The level keyword specifies the model to be used:


-----

  - level=1: This is the original SPICE BJT model, and it is the default model if the level
keyword is not specified on the .model line.

  - level=2: This is a modified version of the original SPICE BJT that models both vertical
and lateral devices and includes temperature corrections of collector, emitter and base
resistors.

[• level=4: Advanced VBIC model (see http://www.designers-guide.org/VBIC/ for details)](http://www.designers-guide.org/VBIC/)

The bipolar junction transistor model in ngspice is an adaptation of the integral charge control
model of Gummel and Poon. This modified Gummel-Poon model extends the original model
to include several effects at high bias levels. The model automatically simplifies to the simpler
Ebers-Moll model when certain parameters are not specified. The parameter names used in the
modified Gummel-Poon model have been chosen to be more easily understood by the user, and
to reflect better both physical and circuit design thinking.

The dc model is defined by the parameters is, bf, nf, ise, ikf, and ne, which determine
the forward current gain characteristics, is, br, nr, isc, ikr, and nc, which determine the
reverse current gain characteristics, and vaf and var, which determine the output conductance
for forward and reverse regions.

The level 1 model has among the standard temperature parameters an extension compatible with
most foundry provided process design kits (see parameter table below tlev).

The level 1 and 2 models include the substrate saturation current iss. Three ohmic resistances
```
rb, rc, and re are included, where rb can be high current dependent. Base charge storage is

```
modeled by forward and reverse transit times, tf and tr, where the forward transit time tf can
be bias dependent if desired. Nonlinear depletion layer capacitances are defined with cje, vje,
and nje for the B-E junction, cjc, vjc, and njc for the B-C junction and cjs, vjs, and mjs
for the C-S (collector-substrate) junction.

The level 1 and 2 model support a substrate capacitance that is connected to the device’s base or
collector, to model lateral or vertical devices dependent on the parameter subs. The temperature
dependence of the saturation currents, is and iss (for the level 2 model), is determined by the
energy-gap, eg, and the saturation current temperature exponent, xti.

In the new model, additional base current temperature dependence is modeled by the beta temperature exponent xtb. The values specified are assumed to have been measured at the temperature tnom, which can be specified on the .options control line or overridden by a specification
on the .model line.

The level 4 model (VBIC) has the following improvements beyond the GP models: improved Early effect modeling, quasi-saturation modeling, parasitic substrate transistor modeling,
parasitic fixed (oxide) capacitance modeling, includes an avalanche multiplication model, improved temperature modeling, base current is decoupled from collector current, electrothermal
modeling, smooth and continuous mode.

The BJT parameters used in the modified Gummel-Poon model are listed below. The parameter
names used in earlier versions of SPICE2 are still accepted.

**Gummel-Poon BJT Parameters (incl. model extensions)**


-----

|Name|Parameters|Units|Default|Example|Scale factor|
|---|---|---|---|---|---|
|SUBS|Substrate connection: for vertical geometry, -1 for lateral geometry (level 2 only).||1|||
|IS|Transport saturation current.|A|1.0e-16|1.0e-15|area|
|ISS|Reverse saturation current, substrate-to-collector for vertical device or substrate-to-base for lateral (level 2 only).|A|1.0e-16|1.0e-15|area|
|BF|Ideal maximum forward beta.|-|100|100||
|NF|Forward current emission coefficient.|-|1.0|1||
|VAF (VA)|Forward Early voltage.|V|∞|200||
|IKF|Corner for forward beta current roll-off.|A|∞|0.01|area|
|NKF|High current Beta rolloff exponent|-|0.5|0.58||
|ISE|B-E leakage saturation current.|A|0.0|1e-13|area|
|NE|B-E leakage emission coefficient.|-|1.5|2||
|BR|Ideal maximum reverse beta.|-|1|0.1||
|NR|Reverse current emission coefficient.|-|1|1||
|VAR (VB)|Reverse Early voltage.|V|∞|200||
|IKR|Corner for reverse beta high current roll-off.|A|∞|0.01|area|
|ISC|B-C leakage saturation current (area is ‘areab’ for vertical devices and ‘areac’ for lateral).|A|0.0|1e-13|area|
|NC|B-C leakage emission coefficient.|-|2|1.5||
|RB|Zero bias base resistance.|Ω|0|100|area|
|IRB|Current where base resistance falls halfway to its min value.|A|∞|0.1|area|
|RBM|Minimum base resistance at high currents.|Ω|RB|10|area|
|RE|Emitter resistance.|Ω|0|1|area|
|RC|Collector resistance.|Ω|0|10|area|
|CJE|B-E zero-bias depletion capacitance.|F|0|2pF|area|
|VJE (PE)|B-E built-in potential.|V|0.75|0.6||
|MJE (ME)|B-E junction exponential factor.|-|0.33|0.33||
|TF|Ideal forward transit time.|sec|0|0.1ns||
|XTF|Coefficient for bias dependence of TF.|-|0|||
|VTF|Voltage describing VBC dependence of TF.|V|∞|||
|ITF|High-current parameter for effect on TF.|A|0|-|area|


-----

1
PTF Excess phase at freq=

|PTF|1 Excess phase at freq= Hz. 2πTF|deg|0|Col5|Col6|
|---|---|---|---|---|---|
|CJC|B-C zero-bias depletion capacitance (area is ‘areab’ for vertical devices and ‘areac’ for lateral).|F|0|2pF|area|
|VJC (PC)|B-C built-in potential.|V|0.75|0.5||
|MJC|B-C junction exponential factor.|-|0.33|0.5||
|XCJC|Fraction of B-C depletion capacitance connected to internal base node.|-|1|||
|TR|Ideal reverse transit time.|sec|0|10ns||
|CJS|Zero-bias collector-substrate capacitance (area is ‘areac’ for vertical devices and ‘areab’ for lateral).|F|0|2pF|area|
|VJS (PS)|Substrate junction built-in potential.|V|0.75|||
|MJS (MS)|Substrate junction exponential factor.|-|0|0.5||
|XTB|Forward and reverse beta temperature exponent.|-|0|||
|EG|Energy gap for temperature effect on IS.|eV|1.11|||
|XTI|Temperature exponent for effect on IS.|-|3|||
|KF|Flicker-noise coefficient.|-|0|||
|AF|Flicker-noise exponent.|-|1|||
|FC|Coefficient for forward-bias depletion capacitance formula.|-|0.5|0||
|TNOM (TREF)|Parameter measurement temperature.|◦C|27|50||
|TLEV|BJT temperature equation selector|-|0|||
|TLEVC|BJT capac. temperature equation selector|-|0|||
|TRE1|1st order temperature coefficient for RE.|1/◦C|0.0|1e-3||
|TRE2|2nd order temperature coefficient for RE.|1/◦C2|0.0|1e-5||
|TRC1|1st order temperature coefficient for RC .|1/◦C|0.0|1e-3||
|TRC2|2nd order temperature coefficient for RC.|1/◦C2|0.0|1e-5||
|TRB1|1st order temperature coefficient for RB.|1/◦C|0.0|1e-3||
|TRB2|2nd order temperature coefficient for RB.|1/◦C2|0.0|1e-5||


-----

|TRBM1|1st order temperature coefficient for RBM|1/◦C|0.0|1e-3|Col6|
|---|---|---|---|---|---|
|TRBM2|2nd order temperature coefficient for RBM|1/◦C2|0.0|1e-5||
|TBF1|1st order temperature coefficient for BF|1/◦C|0.0|1e-3||
|TBF2|2nd order temperature coefficient for BF|1/◦C2|0.0|1e-5||
|TBR1|1st order temperature coefficient for BR|1/◦C|0.0|1e-3||
|TBR2|2nd order temperature coefficient for BR|1/◦C2|0.0|1e-5||
|TIKF1|1st order temperature coefficient for IKF|1/◦C|0.0|1e-3||
|TIKF2|2nd order temperature coefficient for IKF|1/◦C2|0.0|1e-5||
|TIKR1|1st order temperature coefficient for IKR|1/◦C|0.0|1e-3||
|TIKR2|2nd order temperature coefficient for IKR|1/◦C2|0.0|1e-5||
|TIRB1|1st order temperature coefficient for IRB|1/◦C|0.0|1e-3||
|TIRB2|2nd order temperature coefficient for IRB|1/◦C2|0.0|1e-5||
|TNC1|1st order temperature coefficient for NC|1/◦C|0.0|1e-3||
|TNC2|2nd order temperature coefficient for NC|1/◦C2|0.0|1e-5||
|TNE1|1st order temperature coefficient for NE|1/◦C|0.0|1e-3||
|TNE2|2nd order temperature coefficient for NE|1/◦C2|0.0|1e-5||
|TNF1|1st order temperature coefficient for NF|1/◦C|0.0|1e-3||
|TNF2|2nd order temperature coefficient for NF|1/◦C2|0.0|1e-5||
|TNR1|1st order temperature coefficient for IKF|1/◦C|0.0|1e-3||
|TNR2|2nd order temperature coefficient for IKF|1/◦C2|0.0|1e-5||
|TVAF1|1st order temperature coefficient for VAF|1/◦C|0.0|1e-3||
|TVAF2|2nd order temperature coefficient for VAF|1/◦C2|0.0|1e-5||
|TVAR1|1st order temperature coefficient for VAR|1/◦C|0.0|1e-3||


-----

|TVAR2|2nd order temperature coefficient for VAR|1/◦C2|0.0|1e-5|Col6|
|---|---|---|---|---|---|
|CTC|1st order temperature coefficient for CJC|1/◦C|0.0|1e-3||
|CTE|1st order temperature coefficient for CJE|1/◦C|0.0|1e-3||
|CTS|1st order temperature coefficient for CJS|1/◦C|0.0|1e-3||
|TVJC|1st order temperature coefficient for VJC|1/◦C2|0.0|1e-5||
|TVJE|1st order temperature coefficient for VJE|1/◦C|0.0|1e-3||
|TITF1|1st order temperature coefficient for ITF|1/◦C|0.0|1e-3||
|TITF2|2nd order temperature coefficient for ITF|1/◦C2|0.0|1e-5||
|TTF1|1st order temperature coefficient for TF|1/◦C|0.0|1e-3||
|TTF2|2nd order temperature coefficient for TF|1/◦C2|0.0|1e-5||
|TTR1|1st order temperature coefficient for TR|1/◦C|0.0|1e-3||
|TTR2|2nd order temperature coefficient for TR|1/◦C2|0.0|1e-5||
|TMJE1|1st order temperature coefficient for MJE|1/◦C|0.0|1e-3||
|TMJE2|2nd order temperature coefficient for MJE|1/◦C2|0.0|1e-5||
|TMJC1|1st order temperature coefficient for MJC|1/◦C|0.0|1e-3||
|TMJC2|2nd order temperature coefficient for MJC|1/◦C2|0.0|1e-5||


-----

