# Contents

## I Ngspice User Manual 3

**1** **Introduction** **31**

1.1 Simulation Algorithms . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 32

1.1.1 Analog Simulation . . . . . . . . . . . . . . . . . . . . . . . . . . . . 32

1.1.2 Digital Simulation . . . . . . . . . . . . . . . . . . . . . . . . . . . . 33

1.1.3 Mixed-Signal Simulation . . . . . . . . . . . . . . . . . . . . . . . . . 33

1.1.4 Mixed-Level Simulation . . . . . . . . . . . . . . . . . . . . . . . . . 34

1.2 Supported Analyses . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 35

1.2.1 DC Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 35

1.2.2 AC Small-Signal Analysis . . . . . . . . . . . . . . . . . . . . . . . . 36

1.2.3 Transient Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . 36

1.2.4 Pole-Zero Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . 36

1.2.5 Small-Signal Distortion Analysis . . . . . . . . . . . . . . . . . . . . 37

1.2.6 Sensitivity Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . 37

1.2.7 Noise Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37

1.2.8 Periodic Steady State Analysis . . . . . . . . . . . . . . . . . . . . . . 38

1.3 Analysis at Different Temperatures . . . . . . . . . . . . . . . . . . . . . . . . 38

1.4 Convergence . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 39

1.4.1 Voltage convergence criterion . . . . . . . . . . . . . . . . . . . . . . 40

1.4.2 Current convergence criterion . . . . . . . . . . . . . . . . . . . . . . 40

1.4.3 Convergence failure . . . . . . . . . . . . . . . . . . . . . . . . . . . 41

**2** **Circuit Description** **43**

2.1 General Structure and Conventions . . . . . . . . . . . . . . . . . . . . . . . . 43

2.1.1 Input file structure . . . . . . . . . . . . . . . . . . . . . . . . . . . . 43

2.1.2 Circuit elements (device instances) . . . . . . . . . . . . . . . . . . . 43

2.1.3 Some naming conventions . . . . . . . . . . . . . . . . . . . . . . . . 45


-----

2.2 Basic lines . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 46

2.2.1 .TITLE line . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 46

2.2.2 .END Line . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 46

2.2.3 Comments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47

2.2.4 End-of-line comments . . . . . . . . . . . . . . . . . . . . . . . . . . 47

2.3 .MODEL Device Models . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47

2.4 .SUBCKT Subcircuits . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 48

2.4.1 .SUBCKT Line . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 49

2.4.2 .ENDS Line . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 50

2.4.3 Subcircuit Calls . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 50

2.5 .GLOBAL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 50

2.6 .INCLUDE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 51

2.7 .LIB . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 51

2.8 .PARAM Parametric netlists . . . . . . . . . . . . . . . . . . . . . . . . . . . 51

2.8.1 .param line . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 52

2.8.2 Brace expressions in circuit elements: . . . . . . . . . . . . . . . . . . 52

2.8.3 Subcircuit parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . 53

2.8.4 Symbol scope . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 54

2.8.5 Syntax of expressions . . . . . . . . . . . . . . . . . . . . . . . . . . 54

2.8.6 Reserved words . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 57

2.8.7 Alternative syntax . . . . . . . . . . . . . . . . . . . . . . . . . . . . 57

2.9 .FUNC . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 57

2.10 .CSPARAM . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 58

2.11 .TEMP . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 59

2.12 .IF Condition-Controlled Netlist . . . . . . . . . . . . . . . . . . . . . . . . . 59

2.13 Parameters, functions, expressions, and command scripts . . . . . . . . . . . . 61

2.13.1 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 61

2.13.2 Nonlinear sources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 61

2.13.3 Control commands, Command scripts . . . . . . . . . . . . . . . . . . 61

**3** **Circuit Elements and Models** **63**

3.1 General options and information . . . . . . . . . . . . . . . . . . . . . . . . . 63

3.1.1 Paralleling devices with multiplier m . . . . . . . . . . . . . . . . . . 63

3.1.2 Technology scaling . . . . . . . . . . . . . . . . . . . . . . . . . . . . 65

3.1.3 Model binning . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 65


-----

3.1.4 Initial conditions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 65

3.2 Elementary Devices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 66

3.2.1 Resistors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 66

3.2.2 Semiconductor Resistors . . . . . . . . . . . . . . . . . . . . . . . . . 67

3.2.3 Semiconductor Resistor Model (R) . . . . . . . . . . . . . . . . . . . 68

3.2.4 Resistors, dependent on expressions (behavioral resistor) . . . . . . . . 69

3.2.5 Capacitors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 70

3.2.6 Semiconductor Capacitors . . . . . . . . . . . . . . . . . . . . . . . . 71

3.2.7 Semiconductor Capacitor Model (C) . . . . . . . . . . . . . . . . . . . 71

3.2.8 Capacitors, dependent on expressions (behavioral capacitor) . . . . . . 73

3.2.9 Inductors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 74

3.2.10 Inductor model . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 74

3.2.11 Coupled (Mutual) Inductors . . . . . . . . . . . . . . . . . . . . . . . 76

3.2.12 Inductors, dependent on expressions (behavioral inductor) . . . . . . . 76

3.2.13 Capacitor or inductor with initial conditions . . . . . . . . . . . . . . . 77

3.2.14 Switches . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 78

3.2.15 Switch Model (SW/CSW) . . . . . . . . . . . . . . . . . . . . . . . . 79

**4** **Voltage and Current Sources** **81**

4.1 Independent Sources for Voltage or Current . . . . . . . . . . . . . . . . . . . 81

4.1.1 Pulse . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 82

4.1.2 Sinusoidal . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 83

4.1.3 Exponential . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 83

4.1.4 Piece-Wise Linear . . . . . . . . . . . . . . . . . . . . . . . . . . . . 84

4.1.5 Single-Frequency FM . . . . . . . . . . . . . . . . . . . . . . . . . . 84

4.1.6 Amplitude modulated source (AM) . . . . . . . . . . . . . . . . . . . 85

4.1.7 Transient noise source . . . . . . . . . . . . . . . . . . . . . . . . . . 86

4.1.8 Random voltage source . . . . . . . . . . . . . . . . . . . . . . . . . . 87

4.1.9 External voltage or current input . . . . . . . . . . . . . . . . . . . . . 87

4.1.10 Arbitrary Phase Sources . . . . . . . . . . . . . . . . . . . . . . . . . 88

4.2 Linear Dependent Sources . . . . . . . . . . . . . . . . . . . . . . . . . . . . 88

4.2.1 Gxxxx: Linear Voltage-Controlled Current Sources (VCCS) . . . . . . 88

4.2.2 Exxxx: Linear Voltage-Controlled Voltage Sources (VCVS) . . . . . . 89

4.2.3 Fxxxx: Linear Current-Controlled Current Sources (CCCS) . . . . . . 89

4.2.4 Hxxxx: Linear Current-Controlled Voltage Sources (CCVS) . . . . . . 89

4.2.5 Polynomial Source Compatibility . . . . . . . . . . . . . . . . . . . . 90


-----

**5** **Non-linear Dependent Sources (Behavioral Sources)** **91**

5.1 Bxxxx: Nonlinear dependent source (ASRC) . . . . . . . . . . . . . . . . . . 91

5.1.1 Syntax and usage . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 91

5.1.2 Special B-Source Variables time, temper, hertz . . . . . . . . . . . . . 94

5.1.3 par(’expression’) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 95

5.1.4 Piecewise Linear Function: pwl . . . . . . . . . . . . . . . . . . . . . 95

5.2 Exxxx: non-linear voltage source . . . . . . . . . . . . . . . . . . . . . . . . . 97

5.2.1 VOL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 97

5.2.2 VALUE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 97

5.2.3 TABLE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 97

5.2.4 POLY . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 98

5.2.5 LAPLACE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 99

5.3 Gxxxx: non-linear current source . . . . . . . . . . . . . . . . . . . . . . . . . 100

5.3.1 CUR . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 100

5.3.2 VALUE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 100

5.3.3 TABLE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 100

5.3.4 POLY . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 101

5.3.5 LAPLACE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 101

5.3.6 Example . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 101

5.4 Debugging a behavioral source . . . . . . . . . . . . . . . . . . . . . . . . . . 102

**6** **Transmission Lines** **105**

6.1 Lossless Transmission Lines . . . . . . . . . . . . . . . . . . . . . . . . . . . 105

6.2 Lossy Transmission Lines . . . . . . . . . . . . . . . . . . . . . . . . . . . . 106

6.2.1 Lossy Transmission Line Model (LTRA) . . . . . . . . . . . . . . . . 106

6.3 Uniform Distributed RC Lines . . . . . . . . . . . . . . . . . . . . . . . . . . 108

6.3.1 Uniform Distributed RC Model (URC) . . . . . . . . . . . . . . . . . 108

6.4 KSPICE Lossy Transmission Lines . . . . . . . . . . . . . . . . . . . . . . . . 109

6.4.1 Single Lossy Transmission Line (TXL) . . . . . . . . . . . . . . . . . 109

6.4.2 Coupled Multiconductor Line (CPL) . . . . . . . . . . . . . . . . . . . 110

**7** **Diodes** **113**

7.1 Junction Diodes . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 113

7.2 Diode Model (D) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 113

7.3 Diode Equations . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 115


-----

**8** **BJTs** **121**

8.1 Bipolar Junction Transistors (BJTs) . . . . . . . . . . . . . . . . . . . . . . . 121

8.2 BJT Models (NPN/PNP) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 121

**9** **JFETs** **127**

9.1 Junction Field-Effect Transistors (JFETs) . . . . . . . . . . . . . . . . . . . . 127

9.2 JFET Models (NJF/PJF) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 127

9.2.1 JFET level 1 model with Parker Skellern modification . . . . . . . . . 127

9.2.2 JFET level 2 Parker Skellern model . . . . . . . . . . . . . . . . . . . 129

**10 MESFETs** **131**

10.1 MESFETs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 131

10.2 MESFET Models (NMF/PMF) . . . . . . . . . . . . . . . . . . . . . . . . . . 131

10.2.1 Model by Statz e.a. . . . . . . . . . . . . . . . . . . . . . . . . . . . . 131

10.2.2 Model by Ytterdal e.a. . . . . . . . . . . . . . . . . . . . . . . . . . . 132

10.2.3 hfet1 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 132

10.2.4 hfet2 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 132

**11 MOSFETs** **133**

11.1 MOSFET devices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 133

11.2 MOSFET models (NMOS/PMOS) . . . . . . . . . . . . . . . . . . . . . . . . 134

11.2.1 MOS Level 1 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 134

11.2.2 MOS Level 2 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 136

11.2.3 MOS Level 3 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 136

11.2.4 MOS Level 6 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 136

11.2.5 Notes on Level 1-6 models . . . . . . . . . . . . . . . . . . . . . . . . 136

11.2.6 MOS Level 9 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 139

11.2.7 BSIM Models . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 139

11.2.8 BSIM1 model (level 4) . . . . . . . . . . . . . . . . . . . . . . . . . . 140

11.2.9 BSIM2 model (level 5) . . . . . . . . . . . . . . . . . . . . . . . . . . 141

11.2.10 BSIM3 model (levels 8, 49) . . . . . . . . . . . . . . . . . . . . . . . 141

11.2.11 BSIM4 model (levels 14, 54) . . . . . . . . . . . . . . . . . . . . . . . 142

11.2.12 EKV model . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 143

11.2.13 BSIMSOI models (levels 10, 58, 55, 56, 57) . . . . . . . . . . . . . . . 143

11.2.14 SOI3 model (level 60) . . . . . . . . . . . . . . . . . . . . . . . . . . 143

11.2.15 HiSIM models of the University of Hiroshima . . . . . . . . . . . . . . 143


-----

**12 Mixed-Mode and Behavioral Modeling with XSPICE** **145**

12.1 Code Model Element & .MODEL Cards . . . . . . . . . . . . . . . . . . . . . 145

12.1.1 Syntax . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 145

12.1.2 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 149

12.1.3 Search path for file input . . . . . . . . . . . . . . . . . . . . . . . . . 150

12.2 Analog Models . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 150

12.2.1 Gain . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 150

12.2.2 Summer . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 151

12.2.3 Multiplier . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 152

12.2.4 Divider . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 153

12.2.5 Limiter . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 155

12.2.6 Controlled Limiter . . . . . . . . . . . . . . . . . . . . . . . . . . . . 156

12.2.7 PWL Controlled Source . . . . . . . . . . . . . . . . . . . . . . . . . 158

12.2.8 Filesource . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 160

12.2.9 multi_input_pwl block . . . . . . . . . . . . . . . . . . . . . . . . . . 162

12.2.10 Analog Switch . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 163

12.2.11 Zener Diode . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 164

12.2.12 Current Limiter . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 165

12.2.13 Hysteresis Block . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 168

12.2.14 Differentiator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 170

12.2.15 Integrator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 171

12.2.16 S-Domain Transfer Function . . . . . . . . . . . . . . . . . . . . . . . 172

12.2.17 Slew Rate Block . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 175

12.2.18 Inductive Coupling . . . . . . . . . . . . . . . . . . . . . . . . . . . . 176

12.2.19 Magnetic Core . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 177

12.2.20 Controlled Sine Wave Oscillator . . . . . . . . . . . . . . . . . . . . . 181

12.2.21 Controlled Triangle Wave Oscillator . . . . . . . . . . . . . . . . . . . 182

12.2.22 Controlled Square Wave Oscillator . . . . . . . . . . . . . . . . . . . . 183

12.2.23 Controlled One-Shot . . . . . . . . . . . . . . . . . . . . . . . . . . . 184

12.2.24 Capacitance Meter . . . . . . . . . . . . . . . . . . . . . . . . . . . . 187

12.2.25 Inductance Meter . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 187

12.2.26 Memristor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 188

12.2.27 2D table model . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 189

12.2.28 3D table model . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 191

12.3 Hybrid Models . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 193


-----

12.3.1 Digital-to-Analog Node Bridge . . . . . . . . . . . . . . . . . . . . . 193

12.3.2 Analog-to-Digital Node Bridge . . . . . . . . . . . . . . . . . . . . . 195

12.3.3 Controlled Digital Oscillator . . . . . . . . . . . . . . . . . . . . . . . 196

12.3.4 Node bridge from digital to real with enable . . . . . . . . . . . . . . . 197

12.3.5 A Z**-1 block working on real data . . . . . . . . . . . . . . . . . . . 198

12.3.6 A gain block for event-driven real data . . . . . . . . . . . . . . . . . . 198

12.3.7 Node bridge from real to analog voltage . . . . . . . . . . . . . . . . . 199

12.4 Digital Models . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 200

12.4.1 Buffer . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 200

12.4.2 Inverter . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 201

12.4.3 And . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 202

12.4.4 Nand . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 203

12.4.5 Or . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 204

12.4.6 Nor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 205

12.4.7 Xor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 206

12.4.8 Xnor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 207

12.4.9 Tristate . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 208

12.4.10 Pullup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 209

12.4.11 Pulldown . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 210

12.4.12 D Flip Flop . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 211

12.4.13 JK Flip Flop . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 213

12.4.14 Toggle Flip Flop . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 215

12.4.15 Set-Reset Flip Flop . . . . . . . . . . . . . . . . . . . . . . . . . . . . 217

12.4.16 D Latch . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 219

12.4.17 Set-Reset Latch . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 222

12.4.18 State Machine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 224

12.4.19 Frequency Divider . . . . . . . . . . . . . . . . . . . . . . . . . . . . 227

12.4.20 RAM . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 228

12.4.21 Digital Source . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 231

12.4.22 LUT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 232

12.4.23 General LUT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 234

12.5 Predefined Node Types for event driven simulation . . . . . . . . . . . . . . . 236

12.5.1 Digital Node Type . . . . . . . . . . . . . . . . . . . . . . . . . . . . 236

12.5.2 Real Node Type . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 236

12.5.3 Int Node Type . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 236

12.5.4 (Digital) Input/Output . . . . . . . . . . . . . . . . . . . . . . . . . . 236


-----

**13 Verilog A Device models** **239**

13.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 239

13.2 adms . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 239

13.3 How to integrate a Verilog-A model into ngspice . . . . . . . . . . . . . . . . 239

13.3.1 How to setup a *.va model for ngspice . . . . . . . . . . . . . . . . . . 239

13.3.2 Adding admsXml to your build environment . . . . . . . . . . . . . . 239

**14 Mixed-Level Simulation (ngspice with TCAD)** **241**

14.1 Cider . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 241

14.2 GSS, Genius . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 242

**15 Analyses and Output Control (batch mode)** **243**

15.1 Simulator Variables (.options) . . . . . . . . . . . . . . . . . . . . . . . . . . 243

15.1.1 General Options . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 244

15.1.2 DC Solution Options . . . . . . . . . . . . . . . . . . . . . . . . . . . 245

15.1.3 AC Solution Options . . . . . . . . . . . . . . . . . . . . . . . . . . . 246

15.1.4 Transient Analysis Options . . . . . . . . . . . . . . . . . . . . . . . . 246

15.1.5 ELEMENT Specific options . . . . . . . . . . . . . . . . . . . . . . . 247

15.1.6 Transmission Lines Specific Options . . . . . . . . . . . . . . . . . . . 248

15.1.7 Precedence of option and .options commands . . . . . . . . . . . . . . 248

15.2 Initial Conditions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 248

15.2.1 .NODESET: Specify Initial Node Voltage Guesses . . . . . . . . . . . 248

15.2.2 .IC: Set Initial Conditions . . . . . . . . . . . . . . . . . . . . . . . . 249

15.3 Analyses . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 250

15.3.1 .AC: Small-Signal AC Analysis . . . . . . . . . . . . . . . . . . . . . 250

15.3.2 .DC: DC Transfer Function . . . . . . . . . . . . . . . . . . . . . . . . 251

15.3.3 .DISTO: Distortion Analysis . . . . . . . . . . . . . . . . . . . . . . . 251

15.3.4 .NOISE: Noise Analysis . . . . . . . . . . . . . . . . . . . . . . . . . 253

15.3.5 .OP: Operating Point Analysis . . . . . . . . . . . . . . . . . . . . . . 253

15.3.6 .PZ: Pole-Zero Analysis . . . . . . . . . . . . . . . . . . . . . . . . . 254

15.3.7 .SENS: DC or Small-Signal AC Sensitivity Analysis . . . . . . . . . . 255

15.3.8 .TF: Transfer Function Analysis . . . . . . . . . . . . . . . . . . . . . 255

15.3.9 .TRAN: Transient Analysis . . . . . . . . . . . . . . . . . . . . . . . . 256

15.3.10 Transient noise analysis (at low frequency) . . . . . . . . . . . . . . . 256

15.3.11 .PSS: Periodic Steady State Analysis . . . . . . . . . . . . . . . . . . 260

15.4 Measurements after AC, DC and Transient Analysis . . . . . . . . . . . . . . . 261


-----

15.4.1 .meas(ure) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 261

15.4.2 batch versus interactive mode . . . . . . . . . . . . . . . . . . . . . . 261

15.4.3 General remarks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 261

15.4.4 Input . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 262

15.4.5 Trig Targ . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 262

15.4.6 Find ... When . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 264

15.4.7 AVG|MIN|MAX|PP|RMS|MIN_AT|MAX_AT . . . . . . . . . . . . . . . . 265

15.4.8 Integ . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 265

15.4.9 param . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 266

15.4.10 par(’expression’) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 266

15.4.11 Deriv . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 267

15.4.12 More examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 267

15.5 Safe Operating Area (SOA) warning messages . . . . . . . . . . . . . . . . . . 268

15.5.1 Resistor and Capacitor SOA model parameters . . . . . . . . . . . . . 269

15.5.2 Diode SOA model parameter . . . . . . . . . . . . . . . . . . . . . . . 269

15.5.3 BJT SOA model parameter . . . . . . . . . . . . . . . . . . . . . . . . 269

15.5.4 MOS SOA model parameter . . . . . . . . . . . . . . . . . . . . . . . 269

15.6 Batch Output . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 270

15.6.1 .SAVE: Name vector(s) to be saved in raw file . . . . . . . . . . . . . . 270

15.6.2 .PRINT Lines . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 271

15.6.3 .PLOT Lines . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 271

15.6.4 .FOUR: Fourier Analysis of Transient Analysis Output . . . . . . . . . 272

15.6.5 .PROBE: Name vector(s) to be saved in raw file . . . . . . . . . . . . . 273

15.6.6 par(’expression’): Algebraic expressions for output . . . . . . . . . . . 273

15.6.7 .width . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 274

15.7 Measuring current through device terminals . . . . . . . . . . . . . . . . . . . 274

15.7.1 Adding a voltage source in series . . . . . . . . . . . . . . . . . . . . 274

15.7.2 Using option ’savecurrents’ . . . . . . . . . . . . . . . . . . . . . . . 274

**16 Starting ngspice** **277**

16.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 277

16.2 Where to obtain ngspice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 277

16.3 Command line options for starting ngspice and ngnutmeg . . . . . . . . . . . . 278

16.4 Starting options . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 280

16.4.1 Batch mode . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 280


-----

16.4.2 Interactive mode . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 280

16.4.3 Control mode (Interactive mode with control file or control section) . . 281

16.5 Standard configuration file spinit . . . . . . . . . . . . . . . . . . . . . . . . . 282

16.6 User defined configuration file .spiceinit . . . . . . . . . . . . . . . . . . . . . 283

16.7 Environmental variables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 283

16.7.1 Ngspice specific variables . . . . . . . . . . . . . . . . . . . . . . . . 283

16.7.2 Common environment variables . . . . . . . . . . . . . . . . . . . . . 284

16.8 Memory usage . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 284

16.9 Simulation time . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 285

16.10Ngspice on multi-core processors using OpenMP . . . . . . . . . . . . . . . . 285

16.10.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 285

16.10.2 Some results . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 286

16.10.3 Usage . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 287

16.10.4 Literature . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 287

16.11Server mode option -s . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 287

16.12Ngspice control via input, output fifos . . . . . . . . . . . . . . . . . . . . . . 289

16.13Compatibility . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 291

16.13.1 Compatibility mode . . . . . . . . . . . . . . . . . . . . . . . . . . . 291

16.13.2 Missing functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 291

16.13.3 Devices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 292

16.13.4 Controls and commands . . . . . . . . . . . . . . . . . . . . . . . . . 292

16.14Tests . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 293

16.15Reporting bugs and errors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 294

**17 Interactive Interpreter** **295**

17.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 295

17.2 Expressions, Functions, and Constants . . . . . . . . . . . . . . . . . . . . . . 296

17.3 Plots . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 300

17.4 Command Interpretation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 301

17.4.1 On the console . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 301

17.4.2 Scripts . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 301

17.4.3 Add-on to circuit file . . . . . . . . . . . . . . . . . . . . . . . . . . . 301

17.5 Commands . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 302

17.5.1 Ac*: Perform an AC, small-signal frequency response analysis . . . . . 302

17.5.2 Alias: Create an alias for a command . . . . . . . . . . . . . . . . . . 303


-----

17.5.3 Alter*: Change a device or model parameter . . . . . . . . . . . . . . 303

17.5.4 Altermod*: Change model parameter(s) . . . . . . . . . . . . . . . . 304

17.5.5 Asciiplot: Plot values using old-style character plots . . . . . . . . . . 306

17.5.6 Aspice*: Asynchronous ngspice run . . . . . . . . . . . . . . . . . . . 306

17.5.7 Bug: Mail a bug report . . . . . . . . . . . . . . . . . . . . . . . . . . 306

17.5.8 Cd: Change directory . . . . . . . . . . . . . . . . . . . . . . . . . . . 306

17.5.9 Cdump: Dump the control flow to the screen . . . . . . . . . . . . . . 307

17.5.10 Circbyline*: Enter a circuit line by line . . . . . . . . . . . . . . . . . 307

17.5.11 Codemodel*: Load an XSPICE code model library . . . . . . . . . . . 308

17.5.12 Compose: Compose a vector . . . . . . . . . . . . . . . . . . . . . . . 308

17.5.13 Dc*: Perform a DC-sweep analysis . . . . . . . . . . . . . . . . . . . 309

17.5.14 Define: Define a function . . . . . . . . . . . . . . . . . . . . . . . . . 309

17.5.15 Deftype: Define a new type for a vector or plot . . . . . . . . . . . . . 309

17.5.16 Delete*: Remove a trace or breakpoint . . . . . . . . . . . . . . . . . . 310

17.5.17 Destroy: Delete an output data set . . . . . . . . . . . . . . . . . . . . 310

17.5.18 Devhelp: information on available devices . . . . . . . . . . . . . . . . 310

17.5.19 Diff: Compare vectors . . . . . . . . . . . . . . . . . . . . . . . . . . 311

17.5.20 Display: List known vectors and types . . . . . . . . . . . . . . . . . . 311

17.5.21 Echo: Print text . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 311

17.5.22 Edit*: Edit the current circuit . . . . . . . . . . . . . . . . . . . . . . 311

17.5.23 Edisplay: Print a list of all the event nodes . . . . . . . . . . . . . . . 312

17.5.24 Eprint: Print an event driven node . . . . . . . . . . . . . . . . . . . . 312

17.5.25 Eprvcd: Dump event nodes in VCD format . . . . . . . . . . . . . . . 312

17.5.26 FFT: fast Fourier transform of vectors . . . . . . . . . . . . . . . . . . 312

17.5.27 Fourier: Perform a Fourier transform . . . . . . . . . . . . . . . . . . 314

17.5.28 Gnuplot: Graphics output via gnuplot . . . . . . . . . . . . . . . . . . 315

17.5.29 Hardcopy: Save a plot to a file for printing . . . . . . . . . . . . . . . 315

17.5.30 Help: Print summaries of Ngspice commands . . . . . . . . . . . . . . 316

17.5.31 History: Review previous commands . . . . . . . . . . . . . . . . . . 316

17.5.32 Inventory: Print circuit inventory . . . . . . . . . . . . . . . . . . . . . 319

17.5.33 Iplot*: Incremental plot . . . . . . . . . . . . . . . . . . . . . . . . . 319

17.5.34 Jobs*: List active asynchronous ngspice runs . . . . . . . . . . . . . . 319

17.5.35 Let: Assign a value to a vector . . . . . . . . . . . . . . . . . . . . . . 319

17.5.36 Linearize*: Interpolate to a linear scale . . . . . . . . . . . . . . . . . 320

17.5.37 Listing*: Print a listing of the current circuit . . . . . . . . . . . . . . 321


-----

17.5.38 Load: Load rawfile data . . . . . . . . . . . . . . . . . . . . . . . . . 321

17.5.39 Meas*: Measurements on simulation data . . . . . . . . . . . . . . . . 321

17.5.40 Mdump*: Dump the matrix values to a file (or to console) . . . . . . . 322

17.5.41 Mrdump*: Dump the matrix right hand side values to a file (or to console)322

17.5.42 Noise*: Noise analysis . . . . . . . . . . . . . . . . . . . . . . . . . . 322

17.5.43 Op*: Perform an operating point analysis . . . . . . . . . . . . . . . . 323

17.5.44 Option*: Set a ngspice option . . . . . . . . . . . . . . . . . . . . . . 323

17.5.45 Plot: Plot vectors on the display . . . . . . . . . . . . . . . . . . . . . 324

17.5.46 Pre_<command>: execute commands prior to parsing the circuit . . . . 325

17.5.47 Print: Print values . . . . . . . . . . . . . . . . . . . . . . . . . . . . 326

17.5.48 Psd: power spectral density of vectors . . . . . . . . . . . . . . . . . . 326

17.5.49 Quit: Leave Ngspice or Nutmeg . . . . . . . . . . . . . . . . . . . . . 327

17.5.50 Rehash: Reset internal hash tables . . . . . . . . . . . . . . . . . . . . 327

17.5.51 Remcirc*: Remove the current circuit . . . . . . . . . . . . . . . . . . 327

17.5.52 Reset*: Reset an analysis . . . . . . . . . . . . . . . . . . . . . . . . . 327

17.5.53 Reshape: Alter the dimensionality or dimensions of a vector . . . . . . 328

17.5.54 Resume*: Continue a simulation after a stop . . . . . . . . . . . . . . 328

17.5.55 Rspice*: Remote ngspice submission . . . . . . . . . . . . . . . . . . 328

17.5.56 Run*: Run analysis from the input file . . . . . . . . . . . . . . . . . . 329

17.5.57 Rusage: Resource usage . . . . . . . . . . . . . . . . . . . . . . . . . 329

17.5.58 Save*: Save a set of outputs . . . . . . . . . . . . . . . . . . . . . . . 330

17.5.59 Sens*: Run a sensitivity analysis . . . . . . . . . . . . . . . . . . . . . 331

17.5.60 Set: Set the value of a variable . . . . . . . . . . . . . . . . . . . . . . 332

17.5.61 Setcirc*: Change the current circuit . . . . . . . . . . . . . . . . . . . 332

17.5.62 Setplot: Switch the current set of vectors . . . . . . . . . . . . . . . . 332

17.5.63 Setscale: Set the scale vector for the current plot . . . . . . . . . . . . 333

17.5.64 Settype: Set the type of a vector . . . . . . . . . . . . . . . . . . . . . 333

17.5.65 Shell: Call the command interpreter . . . . . . . . . . . . . . . . . . . 333

17.5.66 Shift: Alter a list variable . . . . . . . . . . . . . . . . . . . . . . . . . 333

17.5.67 Show*: List device state . . . . . . . . . . . . . . . . . . . . . . . . . 334

17.5.68 Showmod*: List model parameter values . . . . . . . . . . . . . . . . 334

17.5.69 Snload*: Load the snapshot file . . . . . . . . . . . . . . . . . . . . . 334

17.5.70 Snsave*: Save a snapshot file . . . . . . . . . . . . . . . . . . . . . . 335

17.5.71 Source: Read a ngspice input file . . . . . . . . . . . . . . . . . . . . 336

17.5.72 Spec: Create a frequency domain plot . . . . . . . . . . . . . . . . . . 337


-----

17.5.73 Status*: Display breakpoint information . . . . . . . . . . . . . . . . . 337

17.5.74 Step*: Run a fixed number of time-points . . . . . . . . . . . . . . . . 337

17.5.75 Stop*: Set a breakpoint . . . . . . . . . . . . . . . . . . . . . . . . . . 338

17.5.76 Strcmp: Compare two strings . . . . . . . . . . . . . . . . . . . . . . 338

17.5.77 Sysinfo*: Print system information . . . . . . . . . . . . . . . . . . . 339

17.5.78 Tf*: Run a Transfer Function analysis . . . . . . . . . . . . . . . . . . 339

17.5.79 Trace*: Trace nodes . . . . . . . . . . . . . . . . . . . . . . . . . . . 340

17.5.80 Tran*: Perform a transient analysis . . . . . . . . . . . . . . . . . . . 340

17.5.81 Transpose: Swap the elements in a multi-dimensional data set . . . . . 341

17.5.82 Unalias: Retract an alias . . . . . . . . . . . . . . . . . . . . . . . . . 341

17.5.83 Undefine: Retract a definition . . . . . . . . . . . . . . . . . . . . . . 341

17.5.84 Unlet: Delete the specified vector(s) . . . . . . . . . . . . . . . . . . . 341

17.5.85 Unset: Clear a variable . . . . . . . . . . . . . . . . . . . . . . . . . . 342

17.5.86 Version: Print the version of ngspice . . . . . . . . . . . . . . . . . . . 342

17.5.87 Where*: Identify troublesome node or device . . . . . . . . . . . . . . 343

17.5.88 Wrdata: Write data to a file (simple table) . . . . . . . . . . . . . . . . 344

17.5.89 Write: Write data to a file (Spice3f5 format) . . . . . . . . . . . . . . . 344

17.5.90 Wrs2p: Write scattering parameters to file (Touchstone® format) . . . 345

17.5.91 Xgraph: use the xgraph(1) program for plotting. . . . . . . . . . . . . 345

17.6 Control Structures . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 346

17.6.1 While - End . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 346

17.6.2 Repeat - End . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 346

17.6.3 Dowhile - End . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 346

17.6.4 Foreach - End . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 346

17.6.5 If - Then - Else . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 347

17.6.6 Label . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 347

17.6.7 Goto . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 347

17.6.8 Continue . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 348

17.6.9 Break . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 348

17.7 Internally predefined variables . . . . . . . . . . . . . . . . . . . . . . . . . . 348

17.8 Scripts . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 353

17.8.1 Variables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 353

17.8.2 Vectors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 354

17.8.3 Commands . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 354

17.8.4 control structures . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 354


-----

17.8.5 Example script ’spectrum’ . . . . . . . . . . . . . . . . . . . . . . . . 358

17.8.6 Example script for random numbers . . . . . . . . . . . . . . . . . . . 360

17.8.7 Parameter sweep . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 361

17.8.8 Output redirection . . . . . . . . . . . . . . . . . . . . . . . . . . . . 361

17.9 Scattering parameters (s-parameters) . . . . . . . . . . . . . . . . . . . . . . . 363

17.9.1 Intro . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 363

17.9.2 S-parameter measurement basics . . . . . . . . . . . . . . . . . . . . . 363

17.9.3 Usage . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 365

17.10MISCELLANEOUS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 365

17.11Bugs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 366

**18 Ngspice User Interfaces** **367**

18.1 MS Windows Graphical User Interface . . . . . . . . . . . . . . . . . . . . . . 367

18.2 MS Windows Console . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 369

18.3 Linux . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 370

18.4 CygWin . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 370

18.5 Error handling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 370

18.6 Postscript printing options . . . . . . . . . . . . . . . . . . . . . . . . . . . . 371

18.7 Gnuplot . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 372

18.8 Integration with CAD software and ‘third party’ GUIs . . . . . . . . . . . . . . 372

18.8.1 KiCad . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 372

18.8.2 GNU Spice GUI . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 372

18.8.3 XCircuit . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 372

18.8.4 GEDA . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 372

18.8.5 MSEspice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 373

18.8.6 GNU Octave . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 373

**19 ngspice as shared library or dynamic link library** **375**

19.1 Compile options . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 375

19.1.1 How to get the sources . . . . . . . . . . . . . . . . . . . . . . . . . . 375

19.1.2 Linux, MINGW, CYGWIN . . . . . . . . . . . . . . . . . . . . . . . 375

19.1.3 MS Visual Studio . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 376

19.2 Linking shared ngspice to a calling application . . . . . . . . . . . . . . . . . 376

19.2.1 Linking during creating the caller . . . . . . . . . . . . . . . . . . . . 376

19.2.2 Loading at runtime . . . . . . . . . . . . . . . . . . . . . . . . . . . . 376

19.3 Shared ngspice API . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 376


-----

19.3.1 structs and types defined for transporting data . . . . . . . . . . . . . . 376

19.3.2 Exported functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . 378

19.3.3 Callback functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . 380

19.4 General remarks on using the API . . . . . . . . . . . . . . . . . . . . . . . . 382

19.4.1 Loading a netlist . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 382

19.4.2 Running the simulation . . . . . . . . . . . . . . . . . . . . . . . . . . 383

19.4.3 Accessing data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 384

19.4.4 Altering model or device parameters . . . . . . . . . . . . . . . . . . . 385

19.4.5 Output . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 385

19.4.6 Error handling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 385

19.5 Example applications . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 385

19.6 ngspice parallel . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 386

19.6.1 Go parallel! . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 386

19.6.2 Additional exported functions . . . . . . . . . . . . . . . . . . . . . . 387

19.6.3 Additional callback functions . . . . . . . . . . . . . . . . . . . . . . 388

19.6.4 Parallel ngspice example . . . . . . . . . . . . . . . . . . . . . . . . . 389

**20 TCLspice** **391**

20.1 tclspice framework . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 391

20.2 tclspice documentation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 391

20.3 spicetoblt . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 391

20.4 Running TCLspice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 392

20.5 examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 392

20.5.1 Active capacitor measurement . . . . . . . . . . . . . . . . . . . . . . 392

20.5.2 Optimization of a linearization circuit for a Thermistor . . . . . . . . . 395

20.5.3 Progressive display . . . . . . . . . . . . . . . . . . . . . . . . . . . . 399

20.6 Compiling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 400

20.6.1 Linux . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 400

20.6.2 MS Windows . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 400

20.7 MS Windows 32 Bit binaries . . . . . . . . . . . . . . . . . . . . . . . . . . . 401

**21 Example Circuits** **403**

21.1 AC coupled transistor amplifier . . . . . . . . . . . . . . . . . . . . . . . . . . 403

21.2 Differential Pair . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 409

21.3 MOSFET Characterization . . . . . . . . . . . . . . . . . . . . . . . . . . . . 409

21.4 RTL Inverter . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 409

21.5 Four-Bit Binary Adder (Bipolar) . . . . . . . . . . . . . . . . . . . . . . . . . 410

21.6 Four-Bit Binary Adder (MOS) . . . . . . . . . . . . . . . . . . . . . . . . . . 412

21.7 Transmission-Line Inverter . . . . . . . . . . . . . . . . . . . . . . . . . . . . 413


-----

**22 Statistical circuit analysis** **415**

22.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 415

22.2 Using random param(eters) . . . . . . . . . . . . . . . . . . . . . . . . . . . . 415

22.3 Behavioral sources (B, E, G, R, L, C) with random control . . . . . . . . . . . 417

22.4 ngspice scripting language . . . . . . . . . . . . . . . . . . . . . . . . . . . . 418

22.5 Monte-Carlo Simulation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 419

22.5.1 Example 1 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 419

22.5.2 Example 2 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 421

22.5.3 Example 3 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 421

22.6 Data evaluation with Gnuplot . . . . . . . . . . . . . . . . . . . . . . . . . . . 421

**23 Circuit optimization with ngspice** **425**

23.1 Optimization of a circuit . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 425

23.2 ngspice optimizer using ngspice scripts . . . . . . . . . . . . . . . . . . . . . 426

23.3 ngspice optimizer using tclspice . . . . . . . . . . . . . . . . . . . . . . . . . 426

23.4 ngspice optimizer using a Python script . . . . . . . . . . . . . . . . . . . . . 426

23.5 ngspice optimizer using ASCO . . . . . . . . . . . . . . . . . . . . . . . . . . 426

23.5.1 Three stage operational amplifier . . . . . . . . . . . . . . . . . . . . . 427

23.5.2 Digital inverter . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 428

23.5.3 Bandpass . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 430

23.5.4 Class-E power amplifier . . . . . . . . . . . . . . . . . . . . . . . . . 431

**24 Notes** **433**

24.1 Glossary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 433

24.2 Acronyms and Abbreviations . . . . . . . . . . . . . . . . . . . . . . . . . . . 434

24.3 To Do . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 435

## II XSPICE Software User’s Manual 439

**25 XSPICE Basics** **441**

25.1 ngspice with the XSPICE option . . . . . . . . . . . . . . . . . . . . . . . . . 441

25.2 The XSPICE Code Model Subsystem . . . . . . . . . . . . . . . . . . . . . . 441

25.3 XSPICE Top-Level Diagram . . . . . . . . . . . . . . . . . . . . . . . . . . . 442


-----

**26 Execution Procedures** **443**

26.1 Simulation and Modeling Overview . . . . . . . . . . . . . . . . . . . . . . . 443

26.1.1 Describing the Circuit . . . . . . . . . . . . . . . . . . . . . . . . . . 443

26.2 Circuit Description Syntax . . . . . . . . . . . . . . . . . . . . . . . . . . . . 449

26.2.1 XSPICE Syntax Extensions . . . . . . . . . . . . . . . . . . . . . . . 449

26.3 How to create code models . . . . . . . . . . . . . . . . . . . . . . . . . . . . 451

**27 Example circuits** **455**

27.1 Amplifier with XSPICE model ‘gain’ . . . . . . . . . . . . . . . . . . . . . . 455

27.2 XSPICE advanced usage . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 457

27.2.1 Circuit example C3 . . . . . . . . . . . . . . . . . . . . . . . . . . . . 457

27.2.2 Running example C3 . . . . . . . . . . . . . . . . . . . . . . . . . . . 460

**28 Code Models and User-Defined Nodes** **465**

28.1 Code Model Data Type Definitions . . . . . . . . . . . . . . . . . . . . . . . . 466

28.2 Creating Code Models . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 466

28.3 Creating User-Defined Nodes . . . . . . . . . . . . . . . . . . . . . . . . . . . 467

28.4 Adding a new code model library . . . . . . . . . . . . . . . . . . . . . . . . . 468

28.5 Compiling and loading the new code model (library) . . . . . . . . . . . . . . 468

28.6 Interface Specification File . . . . . . . . . . . . . . . . . . . . . . . . . . . . 469

28.6.1 The Name Table . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 471

28.6.2 The Port Table . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 471

28.6.3 The Parameter Table . . . . . . . . . . . . . . . . . . . . . . . . . . . 473

28.6.4 Static Variable Table . . . . . . . . . . . . . . . . . . . . . . . . . . . 474

28.7 Model Definition File . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 476

28.7.1 Macros . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 476

28.7.2 Function Library . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 485

28.8 User-Defined Node Definition File . . . . . . . . . . . . . . . . . . . . . . . . 492

28.8.1 Macros . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 493

28.8.2 Function Library . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 493

28.8.3 Example UDN Definition File . . . . . . . . . . . . . . . . . . . . . . 496

**29 Error Messages** **501**

29.1 Preprocessor Error Messages . . . . . . . . . . . . . . . . . . . . . . . . . . . 501

29.2 Simulator Error Messages . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 506

29.3 Code Model Error Messages . . . . . . . . . . . . . . . . . . . . . . . . . . . 507


-----

29.3.1 Code Model aswitch . . . . . . . . . . . . . . . . . . . . . . . . . . . 507

29.3.2 Code Model climit . . . . . . . . . . . . . . . . . . . . . . . . . . . . 508

29.3.3 Code Model core . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 508

29.3.4 Code Model d_osc . . . . . . . . . . . . . . . . . . . . . . . . . . . . 508

29.3.5 Code Model d_source . . . . . . . . . . . . . . . . . . . . . . . . . . 509

29.3.6 Code Model d_state . . . . . . . . . . . . . . . . . . . . . . . . . . . 509

29.3.7 Code Model oneshot . . . . . . . . . . . . . . . . . . . . . . . . . . . 510

29.3.8 Code Model pwl . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 510

29.3.9 Code Model s_xfer . . . . . . . . . . . . . . . . . . . . . . . . . . . . 510

29.3.10 Code Model sine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 511

29.3.11 Code Model square . . . . . . . . . . . . . . . . . . . . . . . . . . . . 511

29.3.12 Code Model triangle . . . . . . . . . . . . . . . . . . . . . . . . . . . 512

## III CIDER 513

**30 CIDER User’s Manual** **515**

30.1 SPECIFICATION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 515

30.1.1 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 516

30.2 BOUNDARY, INTERFACE . . . . . . . . . . . . . . . . . . . . . . . . . . . 517

30.2.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 517

30.2.2 PARAMETERS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 518

30.2.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 518

30.3 COMMENT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 518

30.3.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 519

30.3.2 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 519

30.4 CONTACT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 519

30.4.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 519

30.4.2 PARAMETERS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 519

30.4.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 519

30.4.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 520

30.5 DOMAIN, REGION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 520

30.5.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 520

30.5.2 PARAMETERS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 520

30.5.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 520

30.5.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 521


-----

30.6 DOPING . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 521

30.6.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 521

30.6.2 PARAMETERS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 524

30.6.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 524

30.6.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 525

30.7 ELECTRODE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 525

30.7.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 525

30.7.2 PARAMETERS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 526

30.7.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 526

30.7.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 526

30.8 END . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 526

30.8.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 527

30.9 MATERIAL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 527

30.9.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 527

30.9.2 PARAMETERS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 528

30.9.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 528

30.9.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 528

30.10METHOD . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 529

30.10.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 529

30.10.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 529

30.10.3 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 529

30.11Mobility . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 530

30.11.1 Description . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 530

30.11.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 531

30.11.3 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 531

30.11.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 531

30.11.5 BUGS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 532

30.12MODELS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 532

30.12.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 532

30.12.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 532

30.12.3 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 532

30.12.4 See also . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 533

30.12.5 Bugs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 533

30.13OPTIONS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 533

30.13.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 533


-----

30.13.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 534

30.13.3 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 534

30.13.4 See also . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 534

30.14OUTPUT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 535

30.14.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 535

30.14.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 536

30.14.3 Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 536

30.14.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 537

30.15TITLE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 537

30.15.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 537

30.15.2 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 537

30.15.3 BUGS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 537

30.16X.MESH, Y.MESH . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 537

30.16.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 538

30.16.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 539

30.16.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 539

30.16.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 539

30.17NUMD . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 540

30.17.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 540

30.17.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 541

30.17.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 541

30.17.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 542

30.17.5 BUGS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 542

30.18NBJT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 542

30.18.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 542

30.18.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 543

30.18.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 543

30.18.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 544

30.18.5 BUGS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 544

30.19NUMOS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 544

30.19.1 DESCRIPTION . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 544

30.19.2 Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 545

30.19.3 EXAMPLES . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 545

30.19.4 SEE ALSO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 546

30.20Cider examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 546


-----

## IV Appendices 547

**31 Model and Device Parameters** **549**

31.1 Accessing internal device parameters . . . . . . . . . . . . . . . . . . . . . . . 549

31.2 Elementary Devices . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 551

31.2.1 Resistor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 551

31.2.2 Capacitor - Fixed capacitor . . . . . . . . . . . . . . . . . . . . . . . . 553

31.2.3 Inductor - Fixed inductor . . . . . . . . . . . . . . . . . . . . . . . . . 554

31.2.4 Mutual - Mutual Inductor . . . . . . . . . . . . . . . . . . . . . . . . . 555

31.3 Voltage and current sources . . . . . . . . . . . . . . . . . . . . . . . . . . . . 556

31.3.1 ASRC - Arbitrary source . . . . . . . . . . . . . . . . . . . . . . . . . 556

31.3.2 Isource - Independent current source . . . . . . . . . . . . . . . . . . . 557

31.3.3 Vsource - Independent voltage source . . . . . . . . . . . . . . . . . . 558

31.3.4 CCCS - Current controlled current source . . . . . . . . . . . . . . . . 559

31.3.5 CCVS - Current controlled voltage source . . . . . . . . . . . . . . . . 559

31.3.6 VCCS - Voltage controlled current source . . . . . . . . . . . . . . . . 560

31.3.7 VCVS - Voltage controlled voltage source . . . . . . . . . . . . . . . . 560

31.4 Transmission Lines . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 561

31.4.1 CplLines - Simple Coupled Multiconductor Lines . . . . . . . . . . . . 561

31.4.2 LTRA - Lossy transmission line . . . . . . . . . . . . . . . . . . . . . 562

31.4.3 Tranline - Lossless transmission line . . . . . . . . . . . . . . . . . . . 563

31.4.4 TransLine - Simple Lossy Transmission Line . . . . . . . . . . . . . . 564

31.4.5 URC - Uniform R. C. line . . . . . . . . . . . . . . . . . . . . . . . . 565

31.5 BJTs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 566

31.5.1 BJT - Bipolar Junction Transistor . . . . . . . . . . . . . . . . . . . . 566

31.5.2 BJT - Bipolar Junction Transistor Level 2 . . . . . . . . . . . . . . . . 569

31.5.3 VBIC - Vertical Bipolar Inter-Company Model . . . . . . . . . . . . . 572

31.6 MOSFETs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 576

31.6.1 MOS1 - Level 1 MOSFET model with Meyer capacitance model . . . . 576

31.6.2 MOS2 - Level 2 MOSFET model with Meyer capacitance model . . . . 579

31.6.3 MOS3 - Level 3 MOSFET model with Meyer capacitance model . . . . 583

31.6.4 MOS6 - Level 6 MOSFET model with Meyer capacitance model . . . . 587

31.6.5 MOS9 - Modified Level 3 MOSFET model . . . . . . . . . . . . . . . 590

31.6.6 BSIM1 - Berkeley Short Channel IGFET Model . . . . . . . . . . . . 594

31.6.7 BSIM2 - Berkeley Short Channel IGFET Model . . . . . . . . . . . . 597

31.6.8 BSIM3 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 601

31.6.9 BSIM4 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 602


-----

**32 Compilation notes** **605**

32.1 Ngspice Installation under Linux (and other ’UNIXes’) . . . . . . . . . . . . . 605

32.1.1 Prerequisites . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 605

32.1.2 Install from Git . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 605

32.1.3 Install from a tarball, e.g. ngspice-rework-27.tgz . . . . . . . . . . . . 607

32.1.4 Compilation using an user defined directory tree for object files . . . . 607

32.1.5 Advanced Install . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 607

32.1.6 Compilers and Options . . . . . . . . . . . . . . . . . . . . . . . . . . 609

32.1.7 Compiling For Multiple Architectures . . . . . . . . . . . . . . . . . . 610

32.1.8 Installation Names . . . . . . . . . . . . . . . . . . . . . . . . . . . . 610

32.1.9 Optional Features . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 610

32.1.10 Specifying the System Type . . . . . . . . . . . . . . . . . . . . . . . 611

32.1.11 Sharing Defaults . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 611

32.1.12 Operation Controls . . . . . . . . . . . . . . . . . . . . . . . . . . . . 611

32.2 Ngspice Compilation under Windows OS . . . . . . . . . . . . . . . . . . . . 612

32.2.1 Compile ngspice with MS Visual Studio 2015 or 2017 . . . . . . . . . 612

32.2.2 How to make ngspice with MINGW and MSYS . . . . . . . . . . . . 614

32.2.3 64 Bit executables with MINGW-w64 . . . . . . . . . . . . . . . . . . 616

32.2.4 make ngspice with pure CYGWIN . . . . . . . . . . . . . . . . . . . . 618

32.2.5 ngspice mingw or cygwin console executable w/o graphics . . . . . . . 618

32.2.6 ngspice for MS Windows, cross compiled from Linux . . . . . . . . . 618

32.3 Reporting errors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 619

**33 Copyrights and licenses** **621**

33.1 Documentation license . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 621

33.1.1 Spice documentation copyright . . . . . . . . . . . . . . . . . . . . . . 621

33.1.2 XSPICE SOFTWARE (documentation) copyright . . . . . . . . . . . . 621

33.1.3 CIDER RESEARCH SOFTWARE AGREEMENT (superseded by 33.2.1)622

33.2 ngspice license . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 622

33.2.1 ‘Modified’ BSD license . . . . . . . . . . . . . . . . . . . . . . . . . 623

33.2.2 XSPICE . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 624

33.2.3 tclspice, numparam . . . . . . . . . . . . . . . . . . . . . . . . . . . . 624

33.2.4 Linking to GPLd libraries (e.g. readline, fftw, table.cm): . . . . . . . . 624


-----

