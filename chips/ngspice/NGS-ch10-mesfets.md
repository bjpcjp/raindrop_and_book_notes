# Chapter 10

 MESFETs

## 10.1 MESFETs

General form:
```
   ZXXXXXXX ND NG NS MNAME <AREA> <OFF> <IC=VDS, VGS>

```
Examples:
```
  Z1 7 2 3 ZM1 OFF

## 10.2 MESFET Models (NMF/PMF)

### 10.2.1 Model by Statz e.a.

```
The MESFET model level 1 is derived from the GaAs FET model of Statz et al. as described in

[11]. The dc characteristics are defined by the parameters VTO, B, and BETA, which determine
the variation of drain current with gate voltage, ALPHA, which determines saturation voltage,
and LAMBDA, which determines the output conductance. The formula are given by:


3[�]

1B+(bV(gsV−gsV−TV )T[2] ) 1 _−_ ���1 _−_ _AV3ds_ ��� (1 + _LVds)_ for 0 < Vds < _A[3]_

���� ���

_B(Vgs−VT )[2]_ for V > [3]

1+b(Vgs−VT )[(][1] [+] _[LV][ds][)]_ _A_


_Id =_










(10.1)


Two ohmic resistances, rd and rs, are included. Charge storage is modeled by total gate charge
as a function of gate-drain and gate-source voltages and is defined by the parameters cgs, cgd,
and pb.


-----

|Name|Parameter|Units|Default|Example|Area|
|---|---|---|---|---|---|
|VTO|Pinch-off voltage|V|-2.0|-2.0||
|BETA|Transconductance parameter|A/V 2|1.0e-4|1.0e-3|*|
|B|Doping tail extending parameter|1/V|0.3|0.3|*|
|ALPHA|Saturation voltage parameter|1/V|2|2|*|
|LAMBDA|Channel-length modulation parameter|1/V|0|1.0e-4||
|RD|Drain ohmic resistance|Ω|0|100|*|
|RS|Source ohmic resistance|Ω|0|100|*|
|CGS|Zero-bias G-S junction capacitance|F|0|5pF|*|
|CGD|Zero-bias G-D junction capacitance|F|0|1pF|*|
|PB|Gate junction potential|V|1|0.6||
|KF|Flicker noise coefficient|-|0|||
|AF|Flicker noise exponent|-|1|||
|FC|Coefficient for forward-bias depletion capacitance formula|-|0.5|||


Device instance:
```
  z1 2 3 0 mesmod area=1.4

```
Model:
```
  .model mesmod nmf level=1 rd=46 rs=46 vt0=-1.3
  + lambda=0.03 alpha=3 beta=1.4e-3

### 10.2.2 Model by Ytterdal e.a.

```
**level 2 (and levels 3,4) Copyright 1993: T. Ytterdal, K. Lee, M. Shur and T. A. Fjeldly**

to be written

M. Shur, T.A. Fjeldly, T. Ytterdal, K. Lee, "Unified GaAs MESFET Model for Circuit Simulation", Int. Journal of High Speed Electronics, vol. 3, no. 2, pp. 201-233, 1992

### 10.2.3 hfet1

**level 5**

to be written

no documentation available

### 10.2.4 hfet2

**level6**

to be written

no documentation available


-----

