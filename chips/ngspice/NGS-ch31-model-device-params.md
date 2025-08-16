# Chapter 31

 Model and Device Parameters

The following tables summarize the parameters available on each of the devices and models in
ngspice. There are two tables for each type of device supported by ngspice. Input parameters
to instances and models are parameters that can occur on an instance or model definition line in
the form keyword=value where keyword is the parameter name as given in the tables. Default
input parameters (such as the resistance of a resistor or the capacitance of a capacitor) obviously
do not need the keyword specified.

## 31.1 Accessing internal device parameters

Output parameters are those additional parameters that are available for many types of instances
for the output of operating point and debugging information. These parameters are specified as
```
@device[keyword] and are available for the most recent point computed or, if specified in

```
a .save statement, for an entire simulation as a normal output vector. Thus, to monitor the
gate-to-source capacitance of a MOSFET, a command
```
   save @m1[cgs]

```
given before a transient simulation causes the specified capacitance value to be saved at each
time-point, and a subsequent command such as
```
   plot @m1[cgs]

```
produces the desired plot. (Note that the show command does not use this format).

Some variables are listed as both input and output, and their output simply returns the previously
input value, or the default value after the simulation has been run. Some parameters are input
only because the output system can not handle variables of the given type yet, or the need for
them as output variables has not been apparent. Many such input variables are available as
output variables in a different format, such as the initial condition vectors that can be retrieved
as individual initial condition values. Finally, internally derived values are output only and are
provided for debugging and operating point output purposes.


-----

If you want to access a device parameter of a device used inside of a subcircuit, you may use
the syntax as shown below.

General form:
```
   @device_identifier.subcircuit_name.<subcircuit_name_nn >
  +.device_name[parameter]

```
Example input file:
```
  * transistor output characteristics
  * two nested subcircuits
   vdd d1 0 2.0
   vss vsss 0 0
   vsig g1 vsss 0
   xmos1 d1 g1 vsss level1
  .subckt level1 d3 g3 v3
   xmos2 d3 g3 v3 level2
  .ends
  .subckt level2 d4 g4 v4
  m1 d4 g4 v4 v4 nmos w=1e-5 l=3.5e-007
  .ends
  .dc vdd 0 5 0.1 vsig 0 5 1
  .control
   save all @m.xmos1.xmos2.m1[vdsat]
   run
   plot vss#branch $ current measured at the top level
   plot @m.xmos1.xmos2.m1[vdsat]
  .endc
  .MODEL NMOS NMOS LEVEL = 8
  +VERSION = 3.2.4 TNOM = 27 TOX = 7.4E-9
  .end

```
The device identifier is the first letter extracted from the device name, e.g. m for a MOS transistor.

Please note that the parameter tables presented below do not provide the detailed information
available about the parameters provided in the section on each device and model, but are provided as a quick reference guide.


-----

## 31.2 Elementary Devices

### 31.2.1 Resistor

**31.2.1.1** **Resistor instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|resistance (r)|InOut|real|Resistance|
|10|ac|InOut|real|AC resistance value|
|8|temp|InOut|real|Instance operating temperature|
|14|dtemp|InOut|real|Instance temperature difference with the rest of the circuit|
|3|l|InOut|real|Length|
|2|w|InOut|real|Width|
|12|m|InOut|real|Multiplication factor|
|16|tc|InOut|real|First order temp. coefficient|
|16|tc1|InOut|real|First order temp. coefficient|
|17|tc2|InOut|real|Second order temp. coefficient|
|13|scale|InOut|real|Scale factor|
|15|noisy (noise)|InOut|integer|Resistor generate noise|
|5|sens_resist|In|flag|flag to request sensitivity WRT resistance|
|6|i|Out|real|Current|
|7|p|Out|real|Power|
|206|sens_dc|Out|real|dc sensitivity|
|201|sens_real|Out|real|dc sensitivity and real part of ac sensitivity|
|202|sens_imag|Out|real|dc sensitivity and imag part of ac sensitivity|
|203|sens_mag|Out|real|ac sensitivity of magnitude|
|204|sens_ph|Out|real|ac sensitivity of phase|
|205|sens_cplx|Out|complex|ac sensitivity|


-----

**31.2.1.2** **Resistor model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|103|rsh|InOut|real|Sheet resistance|
|106|narrow|InOut|real|Narrowing of resistor|
|106|dw|InOut|real||
|109|short|InOut|real|Shortening of resistor|
|109|dlr|InOut|real||
|101|tc1|InOut|real|First order temp. coefficient|
|102|tc2|InOut|real|Second order temp. coefficient|
|104|defw|InOut|real|Default device width|
|104|w|InOut|real|Default device width|
|105|l|InOut|real|Default device length|
|110|kf|InOut|real|Flicker noise coefficient|
|111|af|InOut|real|Flicker noise exponent|
|108|tnom|InOut|real|Parameter measurement temperature|
|107|r|InOut|real|Resistance|
|107|res|InOut|real|Resistance|
||wf|InOut|real|Flicker noise width exponent|
||lf|InOut|real|Flicker noise length exponent|
||ef|InOut|real|Flicker noise frequency exponent|
||r|In|flag|Device is a resistor model|


-----

### 31.2.2 Capacitor - Fixed capacitor

**31.2.2.1** **Capacitor instance parameters**

# Name Direction Type

1 capacitance InOut real

1 cap InOut real

1 c InOut real

2 ic InOut real

8 temp InOut real

9 dtemp InOut real

3 w InOut real

4 l InOut real

11 m InOut real

10 scale InOut real

5 sens_cap In flag

6 i Out real

7 p Out real

206 sens_dc Out real

201 sens_real Out real

202 sens_imag Out real

203 sens_mag Out real

204 sens_ph Out real

205 sens_cplx Out complex

**31.2.2.2** **Capacitor model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|capacitance|InOut|real|Device capacitance|
|1|cap|InOut|real|Device capacitance|
|1|c|InOut|real|Device capacitance|
|2|ic|InOut|real|Initial capacitor voltage|
|8|temp|InOut|real|Instance operating temperature|
|9|dtemp|InOut|real|Instance temperature difference from the rest of the circuit|
|3|w|InOut|real|Device width|
|4|l|InOut|real|Device length|
|11|m|InOut|real|Parallel multiplier|
|10|scale|InOut|real|Scale factor|
|5|sens_cap|In|flag|flag to request sens. WRT cap.|
|6|i|Out|real|Device current|
|7|p|Out|real|Instantaneous device power|
|206|sens_dc|Out|real|dc sensitivity|
|201|sens_real|Out|real|real part of ac sensitivity|
|202|sens_imag|Out|real|dc sens. & imag part of ac sens.|
|203|sens_mag|Out|real|sensitivity of ac magnitude|
|204|sens_ph|Out|real|sensitivity of ac phase|
|205|sens_cplx|Out|complex|ac sensitivity|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|112|cap|InOut|real|Model capacitance|
|101|cj|InOut|real|Bottom Capacitance per area|
|102|cjsw|InOut|real|Sidewall capacitance per meter|
|103|defw|InOut|real|Default width|
|113|defl|InOut|real|Default length|
|105|narrow|InOut|real|width correction factor|
|106|short|InOut|real|length correction factor|
|107|tc1|InOut|real|First order temp. coefficient|
|108|tc2|InOut|real|Second order temp. coefficient|
|109|tnom|InOut|real|Parameter measurement temperature|
|110|di|InOut|real|Relative dielectric constant|
|111|thick|InOut|real|Insulator thickness|
|104|c|In|flag|Capacitor model|


-----

### 31.2.3 Inductor - Fixed inductor

**31.2.3.1** **Inductor instance parameters**

# Name Direction Type

1 inductance InOut real

2 ic InOut real

5 sens_ind In flag

9 temp InOut real

10 dtemp InOut real

8 m InOut real

11 scale InOut real

12 nt InOut real

3 flux Out real

4 v Out real

4 volt Out real

6 i Out real

6 current Out real

7 p Out real

206 sens_dc Out real

201 sens_real Out real

202 sens_imag Out real

203 sens_mag Out real

204 sens_ph Out real

205 sens_cplx Out complex

**31.2.3.2** **Inductor model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|inductance|InOut|real|Inductance of inductor|
|2|ic|InOut|real|Initial current through inductor|
|5|sens_ind|In|flag|flag to request sensitivity WRT inductance|
|9|temp|InOut|real|Instance operating temperature|
|10|dtemp|InOut|real|Instance temperature difference with the rest of the circuit|
|8|m|InOut|real|Multiplication Factor|
|11|scale|InOut|real|Scale factor|
|12|nt|InOut|real|Number of turns|
|3|flux|Out|real|Flux through inductor|
|4|v|Out|real|Terminal voltage of inductor|
|4|volt|Out|real||
|6|i|Out|real|Current through the inductor|
|6|current|Out|real||
|7|p|Out|real|instantaneous power dissipated by the inductor|
|206|sens_dc|Out|real|dc sensitivity sensitivity|
|201|sens_real|Out|real|real part of ac sensitivity|
|202|sens_imag|Out|real|dc sensitivity and imag part of ac sensitivty|
|203|sens_mag|Out|real|sensitivity of AC magnitude|
|204|sens_ph|Out|real|sensitivity of AC phase|
|205|sens_cplx|Out|complex|ac sensitivity|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|100|ind|InOut|real|Model inductance|
|101|tc1|InOut|real|First order temp. coefficient|
|102|tc2|InOut|real|Second order temp. coefficient|
|103|tnom|InOut|real|Parameter measurement temperature|
|104|csect|InOut|real|Inductor cross section|
|105|length|InOut|real|Inductor length|
|106|nt|InOut|real|Model number of turns|
|107|mu|InOut|real|Relative magnetic permeability|
|108|l|In|flag|Inductor model|


-----

### 31.2.4 Mutual - Mutual Inductor

**31.2.4.1** **Mutual instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|401|k|InOut|real|Mutual inductance|
|401|coefficient|InOut|real||
|402|inductor1|InOut|instance|First coupled inductor|
|403|inductor2|InOut|instance|Second coupled inductor|
|404|sens_coeff|In|flag|flag to request sensitivity WRT coupling factor|
|606|sens_dc|Out|real|dc sensitivity|
|601|sens_real|Out|real|real part of ac sensitivity|
|602|sens_imag|Out|real|dc sensitivity and imag part of ac sensitivty|
|603|sens_mag|Out|real|sensitivity of AC magnitude|
|604|sens_ph|Out|real|sensitivity of AC phase|
|605|sens_cplx|Out|complex|mutual model parameters:|


-----

## 31.3 Voltage and current sources

### 31.3.1 ASRC - Arbitrary source

**31.3.1.1** **ASRC instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|2|i|In|parsetree|Current source|
|1|v|In|parsetree|Voltage source|
|7|i|Out|real|Current through source|
|6|v|Out|real|Voltage across source|
|3|pos_node|Out|integer|Positive Node|
|4|neg_node|Out|integer|Negative Node|


-----

### 31.3.2 Isource - Independent current source

**31.3.2.1** **Isource instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|dc|InOut|real|DC value of source|
|2|acmag|InOut|real|AC magnitude|
|3|acphase|InOut|real|AC phase|
|5|pulse|In|real vector|Pulse description|
|6|sine|In|real vector|Sinusoidal source description|
|6|sin|In|real vector|Sinusoidal source description|
|7|exp|In|real vector|Exponential source description|
|8|pwl|In|real vector|Piecewise linear description|
|9|sffm|In|real vector|Single freq. FM description|
|21|am|In|real vector|Amplitude modulation description|
|10|neg_node|Out|integer|Negative node of source|
|11|pos_node|Out|integer|Positive node of source|
|12|acreal|Out|real|AC real part|
|13|acimag|Out|real|AC imaginary part|
|14|function|Out|integer|Function of the source|
|15|order|Out|integer|Order of the source function|
|16|coeffs|Out|real vector|Coefficients of the source|
|20|v|Out|real|Voltage across the supply|
|17|p|Out|real|Power supplied by the source|
|4|ac|In|real vector|AC magnitude,phase vector|
|1|c|In|real|Current through current source|
|22|current|Out|real|Current in DC or Transient mode|
|18|distof1|In|real vector|f1 input for distortion|
|19|distof2|In|real vector|f2 input for distortion|


-----

### 31.3.3 Vsource - Independent voltage source

**31.3.3.1** **Vsource instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|dc|InOut|real|D.C. source value|
|3|acmag|InOut|real|A.C. Magnitude|
|4|acphase|InOut|real|A.C. Phase|
|5|pulse|In|real vector|Pulse description|
|6|sine|In|real vector|Sinusoidal source description|
|6|sin|In|real vector|Sinusoidal source description|
|7|exp|In|real vector|Exponential source description|
|8|pwl|In|real vector|Piecewise linear description|
|9|sffm|In|real vector|Single freq. FM descripton|
|22|am|In|real vector|Amplitude modulation descripton|
|16|pos_node|Out|integer|Positive node of source|
|17|neg_node|Out|integer|Negative node of source|
|11|function|Out|integer|Function of the source|
|12|order|Out|integer|Order of the source function|
|13|coeffs|Out|real vector|Coefficients for the function|
|14|acreal|Out|real|AC real part|
|15|acimag|Out|real|AC imaginary part|
|2|ac|In|real vector|AC magnitude, phase vector|
|18|i|Out|real|Voltage source current|
|19|p|Out|real|Instantaneous power|
|20|distof1|In|real vector|f1 input for distortion|
|21|distof2|In|real vector|f2 input for distortion|
|23|r|In|real|pwl repeat start time value|
|24|td|In|real|pwl delay time value|


-----

### 31.3.4 CCCS - Current controlled current source

**31.3.4.1** **CCCS instance parameters**

# Name Direction Type Description

1 gain InOut real Gain of source

2 control InOut instance Name of controlling source

6 sens_gain In flag flag to request sensitivity WRT gain

4 neg_node Out integer Negative node of source

3 pos_node Out integer Positive node of source

7 i Out real CCCS output current

9 v Out real CCCS voltage at output

8 p Out real CCCS power

206 sens_dc Out real dc sensitivity

201 sens_real Out real real part of ac sensitivity

202 sens_imag Out real imag part of ac sensitivity

203 sens_mag Out real sensitivity of ac magnitude

204 sens_ph Out real sensitivity of ac phase

205 sens_cplx Out complex ac sensitivity

### 31.3.5 CCVS - Current controlled voltage source

**31.3.5.1** **CCVS instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|gain|InOut|real|Gain of source|
|2|control|InOut|instance|Name of controlling source|
|6|sens_gain|In|flag|flag to request sensitivity WRT gain|
|4|neg_node|Out|integer|Negative node of source|
|3|pos_node|Out|integer|Positive node of source|
|7|i|Out|real|CCCS output current|
|9|v|Out|real|CCCS voltage at output|
|8|p|Out|real|CCCS power|
|206|sens_dc|Out|real|dc sensitivity|
|201|sens_real|Out|real|real part of ac sensitivity|
|202|sens_imag|Out|real|imag part of ac sensitivity|
|203|sens_mag|Out|real|sensitivity of ac magnitude|
|204|sens_ph|Out|real|sensitivity of ac phase|
|205|sens_cplx|Out|complex|ac sensitivity|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|gain|InOut|real|Transresistance (gain)|
|2|control|InOut|instance|Controlling voltage source|
|7|sens_trans|In|flag|flag to request sens. WRT transimpedance|
|3|pos_node|Out|integer|Positive node of source|
|4|neg_node|Out|integer|Negative node of source|
|8|i|Out|real|CCVS output current|
|10|v|Out|real|CCVS output voltage|
|9|p|Out|real|CCVS power|
|206|sens_dc|Out|real|dc sensitivity|
|201|sens_real|Out|real|real part of ac sensitivity|
|202|sens_imag|Out|real|imag part of ac sensitivity|
|203|sens_mag|Out|real|sensitivity of ac magnitude|
|204|sens_ph|Out|real|sensitivity of ac phase|
|205|sens_cplx|Out|complex|ac sensitivity|


-----

### 31.3.6 VCCS - Voltage controlled current source

**31.3.6.1** **VCCS instance parameters**

# Name Direction Type Description

1 gain InOut real Transconductance of source (gain)

8 sens_trans In flag

3 pos_node Out integer Positive node of source

4 neg_node Out integer Negative node of source

5 cont_p_node Out integer Positive node of contr. source

6 cont_n_node Out integer Negative node of contr. source

2 ic In real

9 i Out real Output current

11 v Out real Voltage across output

10 p Out real Power

206 sens_dc Out real dc sensitivity

201 sens_real Out real real part of ac sensitivity

202 sens_imag Out real imag part of ac sensitivity

203 sens_mag Out real sensitivity of ac magnitude

204 sens_ph Out real sensitivity of ac phase

205 sens_cplx Out complex ac sensitivity

### 31.3.7 VCVS - Voltage controlled voltage source

**31.3.7.1** **VCVS instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|gain|InOut|real|Transconductance of source (gain)|
|8|sens_trans|In|flag|flag to request sensitivity WRT transconductance|
|3|pos_node|Out|integer|Positive node of source|
|4|neg_node|Out|integer|Negative node of source|
|5|cont_p_node|Out|integer|Positive node of contr. source|
|6|cont_n_node|Out|integer|Negative node of contr. source|
|2|ic|In|real|Initial condition of controlling source|
|9|i|Out|real|Output current|
|11|v|Out|real|Voltage across output|
|10|p|Out|real|Power|
|206|sens_dc|Out|real|dc sensitivity|
|201|sens_real|Out|real|real part of ac sensitivity|
|202|sens_imag|Out|real|imag part of ac sensitivity|
|203|sens_mag|Out|real|sensitivity of ac magnitude|
|204|sens_ph|Out|real|sensitivity of ac phase|
|205|sens_cplx|Out|complex|ac sensitivity|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|gain|InOut|real|Voltage gain|
|9|sens_gain|In|flag|flag to request sensitivity WRT gain|
|2|pos_node|Out|integer|Positive node of source|
|3|neg_node|Out|integer|Negative node of source|
|4|cont_p_node|Out|integer|Positive node of contr. source|
|5|cont_n_node|Out|integer|Negative node of contr. source|
|7|ic|In|real|Initial condition of controlling source|
|10|i|Out|real|Output current|
|12|v|Out|real|Output voltage|
|11|p|Out|real|Power|
|206|sens_dc|Out|real|dc sensitivity|
|201|sens_real|Out|real|real part of ac sensitivity|
|202|sens_imag|Out|real|imag part of ac sensitivity|
|203|sens_mag|Out|real|sensitivity of ac magnitude|
|204|sens_ph|Out|real|sensitivity of ac phase|
|205|sens_cplx|Out|complex|ac sensitivity|


-----

## 31.4 Transmission Lines

### 31.4.1 CplLines - Simple Coupled Multiconductor Lines

**31.4.1.1** **CplLines instance parameters**

# Name Direction Type Description

1 pos_nodes InOut string vector in nodes

2 neg_nodes InOut string vector out nodes

3 dimension InOut integer number of coupled lines

4 length InOut real length of lines

**31.4.1.2** **CplLines model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|pos_nodes|InOut|string vector|in nodes|
|2|neg_nodes|InOut|string vector|out nodes|
|3|dimension|InOut|integer|number of coupled lines|
|4|length|InOut|real|length of lines|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|101|r|InOut|real vector|resistance per length|
|104|l|InOut|real vector|inductance per length|
|102|c|InOut|real vector|capacitance per length|
|103|g|InOut|real vector|conductance per length|
|105|length|InOut|real|length|
|106|cpl|In|flag|Device is a cpl model|


-----

### 31.4.2 LTRA - Lossy transmission line

**31.4.2.1** **LTRA instance parameters**

# Name Direction Type

6 v1 InOut real

8 v2 InOut real

7 i1 InOut real

9 i2 InOut real

10 ic In real vector

13 pos_node1 Out integer

14 neg_node1 Out integer

15 pos_node2 Out integer

16 neg_node2 Out integer

**31.4.2.2** **LTRA model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|6|v1|InOut|real|Initial voltage at end 1|
|8|v2|InOut|real|Initial voltage at end 2|
|7|i1|InOut|real|Initial current at end 1|
|9|i2|InOut|real|Initial current at end 2|
|10|ic|In|real vector|Initial condition vector:v1,i1,v2,i2|
|13|pos_node1|Out|integer|Positive node of end 1 of t-line|
|14|neg_node1|Out|integer|Negative node of end 1 of t.line|
|15|pos_node2|Out|integer|Positive node of end 2 of t-line|
|16|neg_node2|Out|integer|Negative node of end 2 of t-line|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|0|ltra|InOut|flag|LTRA model|
|1|r|InOut|real|Resistance per meter|
|2|l|InOut|real|Inductance per meter|
|3|g|InOut|real||
|4|c|InOut|real|Capacitance per meter|
|5|len|InOut|real|length of line|
|11|rel|Out|real|Rel. rate of change of deriv. for bkpt|
|12|abs|Out|real|Abs. rate of change of deriv. for bkpt|
|28|nocontrol|InOut|flag|No timestep control|
|32|steplimit|InOut|flag|always limit timestep to 0.8*(delay of line)|
|33|nosteplimit|InOut|flag|don’t always limit timestep to 0.8*(delay of line)|
|34|lininterp|InOut|flag|use linear interpolation|
|35|quadinterp|InOut|flag|use quadratic interpolation|
|36|mixedinterp|InOut|flag|use linear interpolation if quadratic results look unacceptable|
|46|truncnr|InOut|flag|use N-R iterations for step calculation in LTRAtrunc|
|47|truncdontcut|InOut|flag|don’t limit timestep to keep impulse response calculation errors low|
|42|compactrel|InOut|real|special reltol for straight line checking|
|43|compactabs|InOut|real|special abstol for straight line checking|


-----

### 31.4.3 Tranline - Lossless transmission line

**31.4.3.1** **Tranline instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|z0|InOut|real|Characteristic impedance|
|1|zo|InOut|real||
|4|f|InOut|real|Frequency|
|2|td|InOut|real|Transmission delay|
|3|nl|InOut|real|Normalized length at frequency given|
|5|v1|InOut|real|Initial voltage at end 1|
|7|v2|InOut|real|Initial voltage at end 2|
|6|i1|InOut|real|Initial current at end 1|
|8|i2|InOut|real|Initial current at end 2|
|9|ic|In|real vector|Initial condition vector:v1,i1,v2,i2|
|10|rel|Out|real|Rel. rate of change of deriv. for bkpt|
|11|abs|Out|real|Abs. rate of change of deriv. for bkpt|
|12|pos_node1|Out|integer|Positive node of end 1 of t. line|
|13|neg_node1|Out|integer|Negative node of end 1 of t. line|
|14|pos_node2|Out|integer|Positive node of end 2 of t. line|
|15|neg_node2|Out|integer|Negative node of end 2 of t. line|
|18|delays|Out|real vector|Delayed values of excitation|


-----

### 31.4.4 TransLine - Simple Lossy Transmission Line

**31.4.4.1** **TransLine instance parameters**

# Name Direction Type Description

1 pos_node In integer Positive node of txl

2 neg_node In integer Negative node of txl

3 length InOut real length of line

**31.4.4.2** **TransLine model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|pos_node|In|integer|Positive node of txl|
|2|neg_node|In|integer|Negative node of txl|
|3|length|InOut|real|length of line|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|101|r|InOut|real|resistance per length|
|104|l|InOut|real|inductance per length|
|102|c|InOut|real|capacitance per length|
|103|g|InOut|real|conductance per length|
|105|length|InOut|real|length|
|106|txl|In|flag|Device is a txl model|


-----

### 31.4.5 URC - Uniform R. C. line

**31.4.5.1** **URC instance parameters**

# Name Direction Type

1 l InOut real

2 n InOut real

3 pos_node Out integer

4 neg_node Out integer

5 gnd Out integer

**31.4.5.2** **URC model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|l|InOut|real|Length of transmission line|
|2|n|InOut|real|Number of lumps|
|3|pos_node|Out|integer|Positive node of URC|
|4|neg_node|Out|integer|Negative node of URC|
|5|gnd|Out|integer|Ground node of URC|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|101|k|InOut|real|Propagation constant|
|102|fmax|InOut|real|Maximum frequency of interest|
|103|rperl|InOut|real|Resistance per unit length|
|104|cperl|InOut|real|Capacitance per unit length|
|105|isperl|InOut|real|Saturation current per length|
|106|rsperl|InOut|real|Diode resistance per length|
|107|urc|In|flag|Uniform R.C. line model|


-----

## 31.5 BJTs

### 31.5.1 BJT - Bipolar Junction Transistor

**31.5.1.1** **BJT instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|2|off|InOut|flag|Device initially off|
|3|icvbe|InOut|real|Initial B-E voltage|
|4|icvce|InOut|real|Initial C-E voltage|
|1|area|InOut|real|(Emitter) Area factor|
|10|areab|InOut|real|Base area factor|
|11|areac|InOut|real|Collector area factor|
|9|m|InOut|real|Parallel Multiplier|
|5|ic|In|real vector|Initial condition vector|
|6|sens_area|In|flag|flag to request sensitivity WRT area|
|202|colnode|Out|integer|Number of collector node|
|203|basenode|Out|integer|Number of base node|
|204|emitnode|Out|integer|Number of emitter node|
|205|substnode|Out|integer|Number of substrate node|
|206|colprimenode|Out|integer|Internal collector node|
|207|baseprimenode|Out|integer|Internal base node|
|208|emitprimenode|Out|integer|Internal emitter node|
|211|ic|Out|real|Current at collector node|
|212|ib|Out|real|Current at base node|
|236|ie|Out|real|Emitter current|
|237|is|Out|real|Substrate current|
|209|vbe|Out|real|B-E voltage|
|210|vbc|Out|real|B-C voltage|
|215|gm|Out|real|Small signal transconductance|
|213|gpi|Out|real|Small signal input conductance - pi|
|214|gmu|Out|real|Small signal conductance - mu|
|225|gx|Out|real|Conductance from base to internal base|
|216|go|Out|real|Small signal output conductance|
|227|geqcb|Out|real|d(Ibe)/d(Vbc)|
|228|gccs|Out|real|Internal C-S cap. equiv. cond.|
|229|geqbx|Out|real|Internal C-B-base cap. equiv. cond.|
|239|cpi|Out|real|Internal base to emitter capactance|
|240|cmu|Out|real|Internal base to collector capactiance|
|241|cbx|Out|real|Base to collector capacitance|
|242|ccs|Out|real|Collector to substrate capacitance|
|218|cqbe|Out|real|Cap. due to charge storage in B-E jct.|
|220|cqbc|Out|real|Cap. due to charge storage in B-C jct.|
|222|cqcs|Out|real|Cap. due to charge storage in C-S jct.|
|224|cqbx|Out|real|Cap. due to charge storage in B-X jct.|
|226|cexbc|Out|real|Total Capacitance in B-X junction|


-----

|217|qbe|Out|real|Charge storage B-E junction|
|---|---|---|---|---|
|219|qbc|Out|real|Charge storage B-C junction|
|221|qcs|Out|real|Charge storage C-S junction|
|223|qbx|Out|real|Charge storage B-X junction|
|238|p|Out|real|Power dissipation|
|235|sens_dc|Out|real|dc sensitivity|
|230|sens_real|Out|real|real part of ac sensitivity|
|231|sens_imag|Out|real|dc sens. & imag part of ac sens.|
|232|sens_mag|Out|real|sensitivity of ac magnitude|
|233|sens_ph|Out|real|sensitivity of ac phase|
|234|sens_cplx|Out|complex|ac sensitivity|
|7|temp|InOut|real|instance temperature|
|8|dtemp|InOut|real|instance temperature delta from circuit|


**31.5.1.2** **BJT model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|309|type|Out|string|NPN or PNP|
|101|npn|InOut|flag|NPN type device|
|102|pnp|InOut|flag|PNP type device|
|103|is|InOut|real|Saturation Current|
|104|bf|InOut|real|Ideal forward beta|
|105|nf|InOut|real|Forward emission coefficient|
|106|vaf|InOut|real|Forward Early voltage|
|106|va|InOut|real||
|107|ikf|InOut|real|Forward beta roll-off corner current|
|107|ik|InOut|real||
|108|ise|InOut|real|B-E leakage saturation current|
|110|ne|InOut|real|B-E leakage emission coefficient|
|111|br|InOut|real|Ideal reverse beta|
|112|nr|InOut|real|Reverse emission coefficient|
|113|var|InOut|real|Reverse Early voltage|
|113|vb|InOut|real||
|114|ikr|InOut|real|reverse beta roll-off corner current|
|115|isc|InOut|real|B-C leakage saturation current|
|117|nc|InOut|real|B-C leakage emission coefficient|
|118|rb|InOut|real|Zero bias base resistance|
|119|irb|InOut|real|Current for base resistance=(rb+rbm)/2|
|120|rbm|InOut|real|Minimum base resistance|
|121|re|InOut|real|Emitter resistance|
|122|rc|InOut|real|Collector resistance|
|123|cje|InOut|real|Zero bias B-E depletion capacitance|
|124|vje|InOut|real|B-E built in potential|
|124|pe|InOut|real||
|125|mje|InOut|real|B-E junction grading coefficient|
|125|me|InOut|real||


-----

|126|tf|InOut|real|Ideal forward transit time|
|---|---|---|---|---|
|127|xtf|InOut|real|Coefficient for bias dependence of TF|
|128|vtf|InOut|real|Voltage giving VBC dependence of TF|
|129|itf|InOut|real|High current dependence of TF|
|130|ptf|InOut|real|Excess phase|
|131|cjc|InOut|real|Zero bias B-C depletion capacitance|
|132|vjc|InOut|real|B-C built in potential|
|132|pc|InOut|real||
|133|mjc|InOut|real|B-C junction grading coefficient|
|133|mc|InOut|real||
|134|xcjc|InOut|real|Fraction of B-C cap to internal base|
|135|tr|InOut|real|Ideal reverse transit time|
|136|cjs|InOut|real|Zero bias C-S capacitance|
|136|ccs|InOut|real|Zero bias C-S capacitance|
|137|vjs|InOut|real|Substrate junction built in potential|
|137|ps|InOut|real||
|138|mjs|InOut|real|Substrate junction grading coefficient|
|138|ms|InOut|real||
|139|xtb|InOut|real|Forward and reverse beta temp. exp.|
|140|eg|InOut|real|Energy gap for IS temp. dependency|
|141|xti|InOut|real|Temp. exponent for IS|
|142|fc|InOut|real|Forward bias junction fit parameter|
|301|invearlyvoltf|Out|real|Inverse early voltage:forward|
|302|invearlyvoltr|Out|real|Inverse early voltage:reverse|
|303|invrollofff|Out|real|Inverse roll off - forward|
|304|invrolloffr|Out|real|Inverse roll off - reverse|
|305|collectorconduct|Out|real|Collector conductance|
|306|emitterconduct|Out|real|Emitter conductance|
|307|transtimevbcfact|Out|real|Transit time VBC factor|
|308|excessphasefactor|Out|real|Excess phase fact.|
|143|tnom|InOut|real|Parameter measurement temperature|
|145|kf|InOut|real|Flicker Noise Coefficient|
|144|af|InOut|real|Flicker Noise Exponent|


-----

### 31.5.2 BJT - Bipolar Junction Transistor Level 2

**31.5.2.1** **BJT2 instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|2|off|InOut|flag|Device initially off|
|3|icvbe|InOut|real|Initial B-E voltage|
|4|icvce|InOut|real|Initial C-E voltage|
|1|area|InOut|real|(Emitter) Area factor|
|10|areab|InOut|real|Base area factor|
|11|areac|InOut|real|Collector area factor|
|9|m|InOut|real|Parallel Multiplier|
|5|ic|In|real vector|Initial condition vector|
|6|sens_area|In|flag|flag to request sensitivity WRT area|
|202|colnode|Out|integer|Number of collector node|
|203|basenode|Out|integer|Number of base node|
|204|emitnode|Out|integer|Number of emitter node|
|205|substnode|Out|integer|Number of substrate node|
|206|colprimenode|Out|integer|Internal collector node|
|207|baseprimenode|Out|integer|Internal base node|
|208|emitprimenode|Out|integer|Internal emitter node|
|211|ic|Out|real|Current at collector node|
|212|ib|Out|real|Current at base node|
|236|ie|Out|real|Emitter current|
|237|is|Out|real|Substrate current|
|209|vbe|Out|real|B-E voltage|
|210|vbc|Out|real|B-C voltage|
|215|gm|Out|real|Small signal transconductance|
|213|gpi|Out|real|Small signal input conductance - pi|
|214|gmu|Out|real|Small signal conductance - mu|
|225|gx|Out|real|Conductance from base to internal base|
|216|go|Out|real|Small signal output conductance|
|227|geqcb|Out|real|d(Ibe)/d(Vbc)|
|228|gcsub|Out|real|Internal Subs. cap. equiv. cond.|
|243|gdsub|Out|real|Internal Subs. Diode equiv. cond.|
|229|geqbx|Out|real|Internal C-B-base cap. equiv. cond.|
|239|cpi|Out|real|Internal base to emitter capactance|
|240|cmu|Out|real|Internal base to collector capactiance|
|241|cbx|Out|real|Base to collector capacitance|
|242|csub|Out|real|Substrate capacitance|
|218|cqbe|Out|real|Cap. due to charge storage in B-E jct.|
|220|cqbc|Out|real|Cap. due to charge storage in B-C jct.|
|222|cqsub|Out|real|Cap. due to charge storage in Subs. jct.|
|224|cqbx|Out|real|Cap. due to charge storage in B-X jct.|
|226|cexbc|Out|real|Total Capacitance in B-X junction|
|217|qbe|Out|real|Charge storage B-E junction|
|219|qbc|Out|real|Charge storage B-C junction|


-----

|221|qsub|Out|real|Charge storage Subs. junction|
|---|---|---|---|---|
|223|qbx|Out|real|Charge storage B-X junction|
|238|p|Out|real|Power dissipation|
|235|sens_dc|Out|real|dc sensitivity|
|230|sens_real|Out|real|real part of ac sensitivity|
|231|sens_imag|Out|real|dc sens. & imag part of ac sens.|
|232|sens_mag|Out|real|sensitivity of ac magnitude|
|233|sens_ph|Out|real|sensitivity of ac phase|
|234|sens_cplx|Out|complex|ac sensitivity|
|7|temp|InOut|real|instance temperature|
|8|dtemp|InOut|real|instance temperature delta from circuit|


**31.5.2.2** **BJT2 model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|309|type|Out|string|NPN or PNP|
|101|npn|InOut|flag|NPN type device|
|102|pnp|InOut|flag|PNP type device|
|147|subs|InOut|integer|Vertical or Lateral device|
|103|is|InOut|real|Saturation Current|
|146|iss|InOut|real|Substrate Jct. Saturation Current|
|104|bf|InOut|real|Ideal forward beta|
|105|nf|InOut|real|Forward emission coefficient|
|106|vaf|InOut|real|Forward Early voltage|
|106|va|InOut|real||
|107|ikf|InOut|real|Forward beta roll-off corner current|
|107|ik|InOut|real||
|108|ise|InOut|real|B-E leakage saturation current|
|110|ne|InOut|real|B-E leakage emission coefficient|
|111|br|InOut|real|Ideal reverse beta|
|112|nr|InOut|real|Reverse emission coefficient|
|113|var|InOut|real|Reverse Early voltage|
|113|vb|InOut|real||
|114|ikr|InOut|real|reverse beta roll-off corner current|
|115|isc|InOut|real|B-C leakage saturation current|
|117|nc|InOut|real|B-C leakage emission coefficient|
|118|rb|InOut|real|Zero bias base resistance|
|119|irb|InOut|real|Current for base resistance=(rb+rbm)/2|
|120|rbm|InOut|real|Minimum base resistance|
|121|re|InOut|real|Emitter resistance|
|122|rc|InOut|real|Collector resistance|
|123|cje|InOut|real|Zero bias B-E depletion capacitance|
|124|vje|InOut|real|B-E built in potential|
|124|pe|InOut|real||
|125|mje|InOut|real|B-E junction grading coefficient|
|125|me|InOut|real||


-----

|126|tf|InOut|real|Ideal forward transit time|
|---|---|---|---|---|
|127|xtf|InOut|real|Coefficient for bias dependence of TF|
|128|vtf|InOut|real|Voltage giving VBC dependence of TF|
|129|itf|InOut|real|High current dependence of TF|
|130|ptf|InOut|real|Excess phase|
|131|cjc|InOut|real|Zero bias B-C depletion capacitance|
|132|vjc|InOut|real|B-C built in potential|
|132|pc|InOut|real||
|133|mjc|InOut|real|B-C junction grading coefficient|
|133|mc|InOut|real||
|134|xcjc|InOut|real|Fraction of B-C cap to internal base|
|135|tr|InOut|real|Ideal reverse transit time|
|136|cjs|InOut|real|Zero bias Substrate capacitance|
|136|csub|InOut|real||
|137|vjs|InOut|real|Substrate junction built in potential|
|137|ps|InOut|real||
|138|mjs|InOut|real|Substrate junction grading coefficient|
|138|ms|InOut|real||
|139|xtb|InOut|real|Forward and reverse beta temp. exp.|
|140|eg|InOut|real|Energy gap for IS temp. dependency|
|141|xti|InOut|real|Temp. exponent for IS|
|148|tre1|InOut|real|Temp. coefficient 1 for RE|
|149|tre2|InOut|real|Temp. coefficient 2 for RE|
|150|trc1|InOut|real|Temp. coefficient 1 for RC|
|151|trc2|InOut|real|Temp. coefficient 2 for RC|
|152|trb1|InOut|real|Temp. coefficient 1 for RB|
|153|trb2|InOut|real|Temp. coefficient 2 for RB|
|154|trbm1|InOut|real|Temp. coefficient 1 for RBM|
|155|trbm2|InOut|real|Temp. coefficient 2 for RBM|
|142|fc|InOut|real|Forward bias junction fit parameter|
|301|invearlyvoltf|Out|real|Inverse early voltage:forward|
|302|invearlyvoltr|Out|real|Inverse early voltage:reverse|
|303|invrollofff|Out|real|Inverse roll off - forward|
|304|invrolloffr|Out|real|Inverse roll off - reverse|
|305|collectorconduct|Out|real|Collector conductance|
|306|emitterconduct|Out|real|Emitter conductance|
|307|transtimevbcfact|Out|real|Transit time VBC factor|
|308|excessphasefactor|Out|real|Excess phase fact.|
|143|tnom|InOut|real|Parameter measurement temperature|
|145|kf|InOut|real|Flicker Noise Coefficient|
|144|af|InOut|real|Flicker Noise Exponent|


-----

### 31.5.3 VBIC - Vertical Bipolar Inter-Company Model

**31.5.3.1** **VBIC instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|area|InOut|real|Area factor|
|2|off|InOut|flag|Device initially off|
|3|ic|In|real vector|Initial condition vector|
|4|icvbe|InOut|real|Initial B-E voltage|
|5|icvce|InOut|real|Initial C-E voltage|
|6|temp|InOut|real|Instance temperature|
|7|dtemp|InOut|real|Instance delta temperature|
|8|m|InOut|real|Multiplier|
|212|collnode|Out|integer|Number of collector node|
|213|basenode|Out|integer|Number of base node|
|214|emitnode|Out|integer|Number of emitter node|
|215|subsnode|Out|integer|Number of substrate node|
|216|collCXnode|Out|integer|Internal collector node|
|217|collCInode|Out|integer|Internal collector node|
|218|baseBXnode|Out|integer|Internal base node|
|219|baseBInode|Out|integer|Internal base node|
|220|baseBPnode|Out|integer|Internal base node|
|221|emitEInode|Out|integer|Internal emitter node|
|222|subsSInode|Out|integer|Internal substrate node|
|223|vbe|Out|real|B-E voltage|
|224|vbc|Out|real|B-C voltage|
|225|ic|Out|real|Collector current|
|226|ib|Out|real|Base current|
|227|ie|Out|real|Emitter current|
|228|is|Out|real|Substrate current|
|229|gm|Out|real|Small signal transconductance dIc/dVbe|
|230|go|Out|real|Small signal output conductance dIc/dVbc|
|231|gpi|Out|real|Small signal input conductance dIb/dVbe|
|232|gmu|Out|real|Small signal conductance dIb/dVbc|
|233|gx|Out|real|Conductance from base to internal base|
|247|cbe|Out|real|Internal base to emitter capacitance|
|248|cbex|Out|real|External base to emitter capacitance|
|249|cbc|Out|real|Internal base to collector capacitance|
|250|cbcx|Out|real|External Base to collector capacitance|
|251|cbep|Out|real|Parasitic Base to emitter capacitance|
|252|cbcp|Out|real|Parasitic Base to collector capacitance|
|259|p|Out|real|Power dissipation|
|243|geqcb|Out|real|Internal C-B-base cap. equiv. cond.|
|246|geqbx|Out|real|External C-B-base cap. equiv. cond.|
|234|qbe|Out|real|Charge storage B-E junction|
|235|cqbe|Out|real|Cap. due to charge storage in B-E jct.|
|236|qbc|Out|real|Charge storage B-C junction|


-----

|237|cqbc|Out|real|Cap. due to charge storage in B-C jct.|
|---|---|---|---|---|
|238|qbx|Out|real|Charge storage B-X junction|
|239|cqbx|Out|real|Cap. due to charge storage in B-X jct.|
|258|sens_dc|Out|real|DC sensitivity|
|253|sens_real|Out|real|Real part of AC sensitivity|
|254|sens_imag|Out|real|DC sens. & imag part of AC sens.|
|255|sens_mag|Out|real|Sensitivity of AC magnitude|
|256|sens_ph|Out|real|Sensitivity of AC phase|
|257|sens_cplx|Out|complex|AC sensitivity|


**31.5.3.2** **VBIC model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|305|type|Out|string|NPN or PNP|
|101|npn|InOut|flag|NPN type device|
|102|pnp|InOut|flag|PNP type device|
|103|tnom (tref)|InOut|real|Parameter measurement temperature|
|104|rcx|InOut|real|Extrinsic coll resistance|
|105|rci|InOut|real|Intrinsic coll resistance|
|106|vo|InOut|real|Epi drift saturation voltage|
|107|gamm|InOut|real|Epi doping parameter|
|108|hrcf|InOut|real|High current RC factor|
|109|rbx|InOut|real|Extrinsic base resistance|
|110|rbi|InOut|real|Intrinsic base resistance|
|111|re|InOut|real|Intrinsic emitter resistance|
|112|rs|InOut|real|Intrinsic substrate resistance|
|113|rbp|InOut|real|Parasitic base resistance|
|114|is|InOut|real|Transport saturation current|
|115|nf|InOut|real|Forward emission coefficient|
|116|nr|InOut|real|Reverse emission coefficient|
|117|fc|InOut|real|Fwd bias depletion capacitance limit|
|118|cbeo|InOut|real|Extrinsic B-E overlap capacitance|
|119|cje|InOut|real|Zero bias B-E depletion capacitance|
|120|pe|InOut|real|B-E built in potential|
|121|me|InOut|real|B-E junction grading coefficient|
|122|aje|InOut|real|B-E capacitance smoothing factor|
|123|cbco|InOut|real|Extrinsic B-C overlap capacitance|
|124|cjc|InOut|real|Zero bias B-C depletion capacitance|
|125|qco|InOut|real|Epi charge parameter|
|126|cjep|InOut|real|B-C extrinsic zero bias capacitance|
|127|pc|InOut|real|B-C built in potential|
|128|mc|InOut|real|B-C junction grading coefficient|
|129|ajc|InOut|real|B-C capacitance smoothing factor|
|130|cjcp|InOut|real|Zero bias S-C capacitance|
|131|ps|InOut|real|S-C junction built in potential|
|132|ms|InOut|real|S-C junction grading coefficient|


-----

|133|ajs|InOut|real|S-C capacitance smoothing factor|
|---|---|---|---|---|
|134|ibei|InOut|real|Ideal B-E saturation current|
|135|wbe|InOut|real|Portion of IBEI from Vbei, 1-WBE from Vbex|
|136|nei|InOut|real|Ideal B-E emission coefficient|
|137|iben|InOut|real|Non-ideal B-E saturation current|
|138|nen|InOut|real|Non-ideal B-E emission coefficient|
|139|ibci|InOut|real|Ideal B-C saturation current|
|140|nci|InOut|real|Ideal B-C emission coefficient|
|141|ibcn|InOut|real|Non-ideal B-C saturation current|
|142|ncn|InOut|real|Non-ideal B-C emission coefficient|
|143|avc1|InOut|real|B-C weak avalanche parameter 1|
|144|avc2|InOut|real|B-C weak avalanche parameter 2|
|145|isp|InOut|real|Parasitic transport saturation current|
|146|wsp|InOut|real|Portion of ICCP|
|147|nfp|InOut|real|Parasitic fwd emission coefficient|
|148|ibeip|InOut|real|Ideal parasitic B-E saturation current|
|149|ibenp|InOut|real|Non-ideal parasitic B-E saturation current|
|150|ibcip|InOut|real|Ideal parasitic B-C saturation current|
|151|ncip|InOut|real|Ideal parasitic B-C emission coefficient|
|152|ibcnp|InOut|real|Nonideal parasitic B-C saturation current|
|153|ncnp|InOut|real|Nonideal parasitic B-C emission coefficient|
|154|vef|InOut|real|Forward Early voltage|
|155|ver|InOut|real|Reverse Early voltage|
|156|ikf|InOut|real|Forward knee current|
|157|ikr|InOut|real|Reverse knee current|
|158|ikp|InOut|real|Parasitic knee current|
|159|tf|InOut|real|Ideal forward transit time|
|160|qtf|InOut|real|Variation of TF with base-width modulation|
|161|xtf|InOut|real|Coefficient for bias dependence of TF|
|162|vtf|InOut|real|Voltage giving VBC dependence of TF|
|163|itf|InOut|real|High current dependence of TF|
|164|tr|InOut|real|Ideal reverse transit time|
|165|td|InOut|real|Forward excess-phase delay time|
|166|kfn|InOut|real|B-E Flicker Noise Coefficient|
|167|afn|InOut|real|B-E Flicker Noise Exponent|
|168|bfn|InOut|real|B-E Flicker Noise 1/f dependence|
|169|xre|InOut|real|Temperature exponent of RE|
|170|xrb|InOut|real|Temperature exponent of RB|
|171|xrbi|InOut|real|Temperature exponent of RBI|
|172|xrc|InOut|real|Temperature exponent of RC|
|173|xrci|InOut|real|Temperature exponent of RCI|
|174|xrs|InOut|real|Temperature exponent of RS|
|175|xvo|InOut|real|Temperature exponent of VO|
|176|ea|InOut|real|Activation energy for IS|
|177|eaie|InOut|real|Activation energy for IBEI|
|179|eaic|InOut|real|Activation energy for IBCI/IBEIP|


-----

|179|eais|InOut|real|Activation energy for IBCIP|
|---|---|---|---|---|
|180|eane|InOut|real|Activation energy for IBEN|
|181|eanc|InOut|real|Activation energy for IBCN/IBENP|
|182|eans|InOut|real|Activation energy for IBCNP|
|183|xis|InOut|real|Temperature exponent of IS|
|184|xii|InOut|real|Temperature exponent of IBEI,IBCI,IBEIP,IBCIP|
|185|xin|InOut|real|Temperature exponent of IBEN,IBCN,IBENP,IBCNP|
|186|tnf|InOut|real|Temperature exponent of NF|
|187|tavc|InOut|real|Temperature exponent of AVC2|
|188|rth|InOut|real|Thermal resistance|
|189|cth|InOut|real|Thermal capacitance|
|190|vrt|InOut|real|Punch-through voltage of internal B-C junction|
|191|art|InOut|real|Smoothing parameter for reach-through|
|192|ccso|InOut|real|Fixed C-S capacitance|
|193|qbm|InOut|real|Select SGP qb formulation|
|194|nkf|InOut|real|High current beta rolloff|
|195|xikf|InOut|real|Temperature exponent of IKF|
|196|xrcx|InOut|real|Temperature exponent of RCX|
|197|xrbx|InOut|real|Temperature exponent of RBX|
|198|xrbp|InOut|real|Temperature exponent of RBP|
|199|isrr|InOut|real|Separate IS for fwd and rev|
|200|xisr|InOut|real|Temperature exponent of ISR|
|201|dear|InOut|real|Delta activation energy for ISRR|
|202|eap|InOut|real|Exitivation energy for ISP|
|203|vbbe|InOut|real|B-E breakdown voltage|
|204|nbbe|InOut|real|B-E breakdown emission coefficient|
|205|ibbe|InOut|real|B-E breakdown current|
|206|tvbbe1|InOut|real|Linear temperature coefficient of VBBE|
|207|tvbbe2|InOut|real|Quadratic temperature coefficient of VBBE|
|208|tnbbe|InOut|real|Temperature coefficient of NBBE|
|209|ebbe|InOut|real|exp(-VBBE/(NBBE*Vtv))|
|210|dtemp|InOut|real|Locale Temperature difference|
|211|vers|InOut|real|Revision Version|
|212|vref|InOut|real|Reference Version|


-----

## 31.6 MOSFETs

### 31.6.1 MOS1 - Level 1 MOSFET model with Meyer capacitance model

**31.6.1.1** **MOS1 instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|21|m|InOut|real|Multiplier|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|8|nrd|InOut|real|Drain squares|
|7|nrs|InOut|real|Source squares|
|9|off|In|flag|Device initially off|
|12|icvds|InOut|real|Initial D-S voltage|
|13|icvgs|InOut|real|Initial G-S voltage|
|11|icvbs|InOut|real|Initial B-S voltage|
|20|temp|InOut|real|Instance temperature|
|22|dtemp|InOut|real|Instance temperature difference|
|10|ic|In|real vector|Vector of D-S, G-S, B-S voltages|
|15|sens_l|In|flag|flag to request sensitivity WRT length|
|14|sens_w|In|flag|flag to request sensitivity WRT width|
|215|id|Out|real|Drain current|
|18|is|Out|real|Source current|
|17|ig|Out|real|Gate current|
|16|ib|Out|real|Bulk current|
|217|ibd|Out|real|B-D junction current|
|216|ibs|Out|real|B-S junction current|
|231|vgs|Out|real|Gate-Source voltage|
|232|vds|Out|real|Drain-Source voltage|
|230|vbs|Out|real|Bulk-Source voltage|
|229|vbd|Out|real|Bulk-Drain voltage|
|203|dnode|Out|integer|Number of the drain node|
|204|gnode|Out|integer|Number of the gate node|
|205|snode|Out|integer|Number of the source node|
|206|bnode|Out|integer|Number of the node|
|207|dnodeprime|Out|integer|Number of int. drain node|
|208|snodeprime|Out|integer|Number of int. source node|
|211|von|Out|real||
|212|vdsat|Out|real|Saturation drain voltage|
|213|sourcevcrit|Out|real|Critical source voltage|
|214|drainvcrit|Out|real|Critical drain voltage|
|#|Name|Direction|Type|Description|


-----

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|258|rs|Out|real|Source resistance|
|209|sourceconductance|Out|real|Conductance of source|
|259|rd|Out|real|Drain conductance|
|210|drainconductance|Out|real|Conductance of drain|
|219|gm|Out|real|Transconductance|
|220|gds|Out|real|Drain-Source conductance|
|218|gmb|Out|real|Bulk-Source transconductance|
|218|gmbs|Out|real||
|221|gbd|Out|real|Bulk-Drain conductance|
|222|gbs|Out|real|Bulk-Source conductance|
|223|cbd|Out|real|Bulk-Drain capacitance|
|224|cbs|Out|real|Bulk-Source capacitance|
|233|cgs|Out|real|Gate-Source capacitance|
|236|cgd|Out|real|Gate-Drain capacitance|
|239|cgb|Out|real|Gate-Bulk capacitance|
|235|cqgs|Out|real|Capacitance due to gate-source charge storage|
|238|cqgd|Out|real|Capacitance due to gate-drain charge storage|
|241|cqgb|Out|real|Capacitance due to gate-bulk charge storage|
|243|cqbd|Out|real|Capacitance due to bulk-drain charge storage|
|245|cqbs|Out|real|Capacitance due to bulk-source charge storage|
|225|cbd0|Out|real|Zero-Bias B-D junction capacitance|
|226|cbdsw0|Out|real||
|227|cbs0|Out|real|Zero-Bias B-S junction capacitance|
|228|cbssw0|Out|real||
|234|qgs|Out|real|Gate-Source charge storage|
|237|qgd|Out|real|Gate-Drain charge storage|
|240|qgb|Out|real|Gate-Bulk charge storage|
|242|qbd|Out|real|Bulk-Drain charge storage|
|244|qbs|Out|real|Bulk-Source charge storage|
|19|p|Out|real|Instaneous power|
|256|sens_l_dc|Out|real|dc sensitivity wrt length|
|246|sens_l_real|Out|real|real part of ac sensitivity wrt length|
|247|sens_l_imag|Out|real|imag part of ac sensitivity wrt length|
|248|sens_l_mag|Out|real|sensitivity wrt l of ac magnitude|
|249|sens_l_ph|Out|real|sensitivity wrt l of ac phase|
|250|sens_l_cplx|Out|complex|ac sensitivity wrt length|
|257|sens_w_dc|Out|real|dc sensitivity wrt width|
|251|sens_w_real|Out|real|real part of ac sensitivity wrt width|
|252|sens_w_imag|Out|real|imag part of ac sensitivity wrt width|
|253|sens_w_mag|Out|real|sensitivity wrt w of ac magnitude|
|254|sens_w_ph|Out|real|sensitivity wrt w of ac phase|
|255|sens_w_cplx|Out|complex|ac sensitivity wrt width|
|#|Name|Direction|Type|Description|


**31.6.1.2** **MOS1 model parameters**


-----

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|133|type|Out|string|N-channel or P-channel MOS|
|101|vto|InOut|real|Threshold voltage|
|101|vt0|InOut|real||
|102|kp|InOut|real|Transconductance parameter|
|103|gamma|InOut|real|Bulk threshold parameter|
|104|phi|InOut|real|Surface potential|
|105|lambda|InOut|real|Channel length modulation|
|106|rd|InOut|real|Drain ohmic resistance|
|107|rs|InOut|real|Source ohmic resistance|
|108|cbd|InOut|real|B-D junction capacitance|
|109|cbs|InOut|real|B-S junction capacitance|
|110|is|InOut|real|Bulk junction sat. current|
|111|pb|InOut|real|Bulk junction potential|
|112|cgso|InOut|real|Gate-source overlap cap.|
|113|cgdo|InOut|real|Gate-drain overlap cap.|
|114|cgbo|InOut|real|Gate-bulk overlap cap.|
|122|rsh|InOut|real|Sheet resistance|
|115|cj|InOut|real|Bottom junction cap per area|
|116|mj|InOut|real|Bottom grading coefficient|
|117|cjsw|InOut|real|Side junction cap per area|
|118|mjsw|InOut|real|Side grading coefficient|
|119|js|InOut|real|Bulk jct. sat. current density|
|120|tox|InOut|real|Oxide thickness|
|121|ld|InOut|real|Lateral diffusion|
|123|u0|InOut|real|Surface mobility|
|123|uo|InOut|real||
|124|fc|InOut|real|Forward bias jct. fit parm.|
|128|nmos|In|flag|N type MOSfet model|
|129|pmos|In|flag|P type MOSfet model|
|125|nsub|InOut|real|Substrate doping|
|126|tpg|InOut|integer|Gate type|
|127|nss|InOut|real|Surface state density|
|130|tnom|InOut|real|Parameter measurement temperature|
|131|kf|InOut|real|Flicker noise coefficient|
|132|af|InOut|real|Flicker noise exponent|


-----

### 31.6.2 MOS2 - Level 2 MOSFET model with Meyer capacitance model

**31.6.2.1** **MOS 2 instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|80|m|InOut|real|Multiplier|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|34|id|Out|real|Drain current|
|34|cd|Out|real||
|36|ibd|Out|real|B-D junction current|
|35|ibs|Out|real|B-S junction current|
|18|is|Out|real|Source current|
|17|ig|Out|real|Gate current|
|16|ib|Out|real|Bulk current|
|50|vgs|Out|real|Gate-Source voltage|
|51|vds|Out|real|Drain-Source voltage|
|49|vbs|Out|real|Bulk-Source voltage|
|48|vbd|Out|real|Bulk-Drain voltage|
|8|nrd|InOut|real|Drain squares|
|7|nrs|InOut|real|Source squares|
|9|off|In|flag|Device initially off|
|12|icvds|InOut|real|Initial D-S voltage|
|13|icvgs|InOut|real|Initial G-S voltage|
|11|icvbs|InOut|real|Initial B-S voltage|
|77|temp|InOut|real|Instance operating temperature|
|81|dtemp|InOut|real|Instance temperature difference|
|10|ic|In|real vector|Vector of D-S, G-S, B-S voltages|
|15|sens_l|In|flag|flag to request sensitivity WRT length|
|14|sens_w|In|flag|flag to request sensitivity WRT width|
|22|dnode|Out|integer|Number of drain node|
|23|gnode|Out|integer|Number of gate node|
|24|snode|Out|integer|Number of source node|
|25|bnode|Out|integer|Number of bulk node|
|26|dnodeprime|Out|integer|Number of internal drain node|
|27|snodeprime|Out|integer|Number of internal source node|
|30|von|Out|real||
|31|vdsat|Out|real|Saturation drain voltage|
|32|sourcevcrit|Out|real|Critical source voltage|
|33|drainvcrit|Out|real|Critical drain voltage|
|78|rs|Out|real|Source resistance|


-----

|28|sourceconductance|Out|real|Source conductance|
|---|---|---|---|---|
|79|rd|Out|real|Drain resistance|
|29|drainconductance|Out|real|Drain conductance|
|38|gm|Out|real|Transconductance|
|39|gds|Out|real|Drain-Source conductance|
|37|gmb|Out|real|Bulk-Source transconductance|
|37|gmbs|Out|real||
|40|gbd|Out|real|Bulk-Drain conductance|
|41|gbs|Out|real|Bulk-Source conductance|
|42|cbd|Out|real|Bulk-Drain capacitance|
|43|cbs|Out|real|Bulk-Source capacitance|
|52|cgs|Out|real|Gate-Source capacitance|
|55|cgd|Out|real|Gate-Drain capacitance|
|58|cgb|Out|real|Gate-Bulk capacitance|
|44|cbd0|Out|real|Zero-Bias B-D junction capacitance|
|45|cbdsw0|Out|real||
|46|cbs0|Out|real|Zero-Bias B-S junction capacitance|
|47|cbssw0|Out|real||
|54|cqgs|Out|real|Capacitance due to gate-source charge storage|
|57|cqgd|Out|real|Capacitance due to gate-drain charge storage|
|60|cqgb|Out|real|Capacitance due to gate-bulk charge storage|
|62|cqbd|Out|real|Capacitance due to bulk-drain charge storage|
|64|cqbs|Out|real|Capacitance due to bulk-source charge storage|
|53|qgs|Out|real|Gate-Source charge storage|
|56|qgd|Out|real|Gate-Drain charge storage|
|59|qgb|Out|real|Gate-Bulk charge storage|
|61|qbd|Out|real|Bulk-Drain charge storage|
|63|qbs|Out|real|Bulk-Source charge storage|
|19|p|Out|real|Instantaneous power|
|75|sens_l_dc|Out|real|dc sensitivity wrt length|
|70|sens_l_real|Out|real|real part of ac sensitivity wrt length|
|71|sens_l_imag|Out|real|imag part of ac sensitivity wrt length|
|74|sens_l_cplx|Out|complex|ac sensitivity wrt length|
|72|sens_l_mag|Out|real|sensitivity wrt l of ac magnitude|
|73|sens_l_ph|Out|real|sensitivity wrt l of ac phase|
|76|sens_w_dc|Out|real|dc sensitivity wrt width|
|65|sens_w_real|Out|real|dc sensitivity and real part of ac sensitivity wrt width|


-----

|66|sens_w_imag|Out|real|imag part of ac sensitivity wrt width|
|---|---|---|---|---|
|67|sens_w_mag|Out|real|sensitivity wrt w of ac magnitude|
|68|sens_w_ph|Out|real|sensitivity wrt w of ac phase|
|69|sens_w_cplx|Out|complex|ac sensitivity wrt width|


**31.6.2.2** **MOS2 model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|141|type|Out|string|N-channel or P-channel MOS|
|101|vto|InOut|real|Threshold voltage|
|101|vt0|InOut|real||
|102|kp|InOut|real|Transconductance parameter|
|103|gamma|InOut|real|Bulk threshold parameter|
|104|phi|InOut|real|Surface potential|
|105|lambda|InOut|real|Channel length modulation|
|106|rd|InOut|real|Drain ohmic resistance|
|107|rs|InOut|real|Source ohmic resistance|
|108|cbd|InOut|real|B-D junction capacitance|
|109|cbs|InOut|real|B-S junction capacitance|
|110|is|InOut|real|Bulk junction sat. current|
|111|pb|InOut|real|Bulk junction potential|
|112|cgso|InOut|real|Gate-source overlap cap.|
|113|cgdo|InOut|real|Gate-drain overlap cap.|
|114|cgbo|InOut|real|Gate-bulk overlap cap.|
|122|rsh|InOut|real|Sheet resistance|
|115|cj|InOut|real|Bottom junction cap per area|
|116|mj|InOut|real|Bottom grading coefficient|
|117|cjsw|InOut|real|Side junction cap per area|
|118|mjsw|InOut|real|Side grading coefficient|
|119|js|InOut|real|Bulk jct. sat. current density|
|120|tox|InOut|real|Oxide thickness|
|121|ld|InOut|real|Lateral diffusion|
|123|u0|InOut|real|Surface mobility|
|123|uo|InOut|real||
|124|fc|InOut|real|Forward bias jct. fit parm.|
|135|nmos|In|flag|N type MOSfet model|
|136|pmos|In|flag|P type MOSfet model|
|125|nsub|InOut|real|Substrate doping|
|126|tpg|InOut|integer|Gate type|
|127|nss|InOut|real|Surface state density|
|129|delta|InOut|real|Width effect on threshold|
|130|uexp|InOut|real|Crit. field exp for mob. deg.|
|134|ucrit|InOut|real|Crit. field for mob. degradation|
|131|vmax|InOut|real|Maximum carrier drift velocity|
|132|xj|InOut|real|Junction depth|


-----

|133|neff|InOut|real|Total channel charge coeff.|
|---|---|---|---|---|
|128|nfs|InOut|real|Fast surface state density|
|137|tnom|InOut|real|Parameter measurement temperature|
|139|kf|InOut|real|Flicker noise coefficient|
|140|af|InOut|real|Flicker noise exponent|


-----

### 31.6.3 MOS3 - Level 3 MOSFET model with Meyer capacitance model

**31.6.3.1** **MOS3 instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|80|m|InOut|real|Multiplier|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|34|id|Out|real|Drain current|
|34|cd|Out|real|Drain current|
|36|ibd|Out|real|B-D junction current|
|35|ibs|Out|real|B-S junction current|
|18|is|Out|real|Source current|
|17|ig|Out|real|Gate current|
|16|ib|Out|real|Bulk current|
|50|vgs|Out|real|Gate-Source voltage|
|51|vds|Out|real|Drain-Source voltage|
|49|vbs|Out|real|Bulk-Source voltage|
|48|vbd|Out|real|Bulk-Drain voltage|
|8|nrd|InOut|real|Drain squares|
|7|nrs|InOut|real|Source squares|
|9|off|In|flag|Device initially off|
|12|icvds|InOut|real|Initial D-S voltage|
|13|icvgs|InOut|real|Initial G-S voltage|
|11|icvbs|InOut|real|Initial B-S voltage|
|10|ic|InOut|real vector|Vector of D-S, G-S, B-S voltages|
|77|temp|InOut|real|Instance operating temperature|
|81|dtemp|InOut|real|Instance temperature difference|
|15|sens_l|In|flag|flag to request sensitivity WRT length|
|14|sens_w|In|flag|flag to request sensitivity WRT width|
|22|dnode|Out|integer|Number of drain node|
|23|gnode|Out|integer|Number of gate node|
|24|snode|Out|integer|Number of source node|
|25|bnode|Out|integer|Number of bulk node|
|26|dnodeprime|Out|integer|Number of internal drain node|
|27|snodeprime|Out|integer|Number of internal source node|
|30|von|Out|real|Turn-on voltage|
|31|vdsat|Out|real|Saturation drain voltage|
|32|sourcevcrit|Out|real|Critical source voltage|
|33|drainvcrit|Out|real|Critical drain voltage|
|78|rs|Out|real|Source resistance|
|28|sourceconductance|Out|real|Source conductance|
|79|rd|Out|real|Drain resistance|


-----

|29|drainconductance|Out|real|Drain conductance|
|---|---|---|---|---|
|38|gm|Out|real|Transconductance|
|39|gds|Out|real|Drain-Source conductance|
|37|gmb|Out|real|Bulk-Source transconductance|
|37|gmbs|Out|real|Bulk-Source transconductance|
|40|gbd|Out|real|Bulk-Drain conductance|
|41|gbs|Out|real|Bulk-Source conductance|
|42|cbd|Out|real|Bulk-Drain capacitance|
|43|cbs|Out|real|Bulk-Source capacitance|
|52|cgs|Out|real|Gate-Source capacitance|
|55|cgd|Out|real|Gate-Drain capacitance|
|58|cgb|Out|real|Gate-Bulk capacitance|
|54|cqgs|Out|real|Capacitance due to gate-source charge storage|
|57|cqgd|Out|real|Capacitance due to gate-drain charge storage|
|60|cqgb|Out|real|Capacitance due to gate-bulk charge storage|
|62|cqbd|Out|real|Capacitance due to bulk-drain charge storage|
|64|cqbs|Out|real|Capacitance due to bulk-source charge storage|
|44|cbd0|Out|real|Zero-Bias B-D junction capacitance|
|45|cbdsw0|Out|real|Zero-Bias B-D sidewall capacitance|
|46|cbs0|Out|real|Zero-Bias B-S junction capacitance|
|47|cbssw0|Out|real|Zero-Bias B-S sidewall capacitance|
|63|qbs|Out|real|Bulk-Source charge storage|
|53|qgs|Out|real|Gate-Source charge storage|
|56|qgd|Out|real|Gate-Drain charge storage|
|59|qgb|Out|real|Gate-Bulk charge storage|
|61|qbd|Out|real|Bulk-Drain charge storage|
|19|p|Out|real|Instantaneous power|
|76|sens_l_dc|Out|real|dc sensitivity wrt length|
|70|sens_l_real|Out|real|real part of ac sensitivity wrt length|
|71|sens_l_imag|Out|real|imag part of ac sensitivity wrt length|
|74|sens_l_cplx|Out|complex|ac sensitivity wrt length|
|72|sens_l_mag|Out|real|sensitivity wrt l of ac magnitude|
|73|sens_l_ph|Out|real|sensitivity wrt l of ac phase|
|75|sens_w_dc|Out|real|dc sensitivity wrt width|
|65|sens_w_real|Out|real|real part of ac sensitivity wrt width|
|66|sens_w_imag|Out|real|imag part of ac sensitivity wrt width|
|67|sens_w_mag|Out|real|sensitivity wrt w of ac magnitude|
|68|sens_w_ph|Out|real|sensitivity wrt w of ac phase|
|69|sens_w_cplx|Out|complex|ac sensitivity wrt width|


-----

-----

**31.6.3.2** **MOS3 model parameters**

# Name Direction Type Description

144 type Out string N-channel or P-channel MOS

133 nmos In flag N type MOSfet model

134 pmos In flag P type MOSfet model

101 vto InOut real Threshold voltage

101 vt0 InOut real

102 kp InOut real Transconductance parameter

103 gamma InOut real Bulk threshold parameter

104 phi InOut real Surface potential

105 rd InOut real Drain ohmic resistance

106 rs InOut real Source ohmic resistance

107 cbd InOut real B-D junction capacitance

108 cbs InOut real B-S junction capacitance

109 is InOut real Bulk junction sat. current

110 pb InOut real Bulk junction potential

111 cgso InOut real Gate-source overlap cap.

112 cgdo InOut real Gate-drain overlap cap.

113 cgbo InOut real Gate-bulk overlap cap.

114 rsh InOut real Sheet resistance

115 cj InOut real Bottom junction cap per area

116 mj InOut real Bottom grading coefficient

117 cjsw InOut real Side junction cap per area

118 mjsw InOut real Side grading coefficient

119 js InOut real Bulk jct. sat. current density

120 tox InOut real Oxide thickness

121 ld InOut real Lateral diffusion

145 xl InOut real Length mask adjustment

146 wd InOut real Width Narrowing (Diffusion)

147 xw InOut real Width mask adjustment

148 delvto InOut real Threshold voltage Adjust

148 delvt0 InOut real

122 u0 InOut real Surface mobility

122 uo InOut real

123 fc InOut real Forward bias jct. fit parm.

124 nsub InOut real Substrate doping

125 tpg InOut integer Gate type

126 nss InOut real Surface state density

131 vmax InOut real Maximum carrier drift velocity

135 xj InOut real Junction depth

129 nfs InOut real Fast surface state density

138 xd InOut real Depletion layer width

139 alpha InOut real Alpha

127 eta InOut real Vds dependence of threshold voltage

128 delta InOut real Width effect on threshold

140 input_delta InOut real

130 theta InOut real Vgs dependence on mobility

132 kappa InOut real Kappa

141 tnom InOut real Parameter measurement temperature

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|144|type|Out|string|N-channel or P-channel MOS|
|133|nmos|In|flag|N type MOSfet model|
|134|pmos|In|flag|P type MOSfet model|
|101|vto|InOut|real|Threshold voltage|
|101|vt0|InOut|real||
|102|kp|InOut|real|Transconductance parameter|
|103|gamma|InOut|real|Bulk threshold parameter|
|104|phi|InOut|real|Surface potential|
|105|rd|InOut|real|Drain ohmic resistance|
|106|rs|InOut|real|Source ohmic resistance|
|107|cbd|InOut|real|B-D junction capacitance|
|108|cbs|InOut|real|B-S junction capacitance|
|109|is|InOut|real|Bulk junction sat. current|
|110|pb|InOut|real|Bulk junction potential|
|111|cgso|InOut|real|Gate-source overlap cap.|
|112|cgdo|InOut|real|Gate-drain overlap cap.|
|113|cgbo|InOut|real|Gate-bulk overlap cap.|
|114|rsh|InOut|real|Sheet resistance|
|115|cj|InOut|real|Bottom junction cap per area|
|116|mj|InOut|real|Bottom grading coefficient|
|117|cjsw|InOut|real|Side junction cap per area|
|118|mjsw|InOut|real|Side grading coefficient|
|119|js|InOut|real|Bulk jct. sat. current density|
|120|tox|InOut|real|Oxide thickness|
|121|ld|InOut|real|Lateral diffusion|
|145|xl|InOut|real|Length mask adjustment|
|146|wd|InOut|real|Width Narrowing (Diffusion)|
|147|xw|InOut|real|Width mask adjustment|
|148|delvto|InOut|real|Threshold voltage Adjust|
|148|delvt0|InOut|real||
|122|u0|InOut|real|Surface mobility|
|122|uo|InOut|real||
|123|fc|InOut|real|Forward bias jct. fit parm.|
|124|nsub|InOut|real|Substrate doping|
|125|tpg|InOut|integer|Gate type|
|126|nss|InOut|real|Surface state density|
|131|vmax|InOut|real|Maximum carrier drift velocity|
|135|xj|InOut|real|Junction depth|
|129|nfs|InOut|real|Fast surface state density|
|138|xd|InOut|real|Depletion layer width|
|139|alpha|InOut|real|Alpha|
|127|eta|InOut|real|Vds dependence of threshold voltage|
|128|delta|InOut|real|Width effect on threshold|
|140|input_delta|InOut|real||
|130|theta|InOut|real|Vgs dependence on mobility|
|132|kappa|InOut|real|Kappa|


-----

### 31.6.4 MOS6 - Level 6 MOSFET model with Meyer capacitance model

**31.6.4.1** **MOS6 instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|22|m|InOut|real|Parallel Multiplier|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|215|id|Out|real|Drain current|
|215|cd|Out|real|Drain current|
|18|is|Out|real|Source current|
|17|ig|Out|real|Gate current|
|16|ib|Out|real|Bulk current|
|216|ibs|Out|real|B-S junction capacitance|
|217|ibd|Out|real|B-D junction capacitance|
|231|vgs|Out|real|Gate-Source voltage|
|232|vds|Out|real|Drain-Source voltage|
|230|vbs|Out|real|Bulk-Source voltage|
|229|vbd|Out|real|Bulk-Drain voltage|
|8|nrd|InOut|real|Drain squares|
|7|nrs|InOut|real|Source squares|
|9|off|In|flag|Device initially off|
|12|icvds|InOut|real|Initial D-S voltage|
|13|icvgs|InOut|real|Initial G-S voltage|
|11|icvbs|InOut|real|Initial B-S voltage|
|20|temp|InOut|real|Instance temperature|
|21|dtemp|InOut|real|Instance temperature difference|
|10|ic|In|real vector|Vector of D-S, G-S, B-S voltages|
|15|sens_l|In|flag|flag to request sensitivity WRT length|
|14|sens_w|In|flag|flag to request sensitivity WRT width|
|203|dnode|Out|integer|Number of the drain node|
|204|gnode|Out|integer|Number of the gate node|
|205|snode|Out|integer|Number of the source node|
|206|bnode|Out|integer|Number of the node|
|207|dnodeprime|Out|integer|Number of int. drain node|
|208|snodeprime|Out|integer|Number of int. source node|
|258|rs|Out|real|Source resistance|
|209|sourceconductance|Out|real|Source conductance|
|259|rd|Out|real|Drain resistance|
|210|drainconductance|Out|real|Drain conductance|
|211|von|Out|real|Turn-on voltage|
|212|vdsat|Out|real|Saturation drain voltage|
|213|sourcevcrit|Out|real|Critical source voltage|


-----

|214|drainvcrit|Out|real|Critical drain voltage|
|---|---|---|---|---|
|218|gmbs|Out|real|Bulk-Source transconductance|
|219|gm|Out|real|Transconductance|
|220|gds|Out|real|Drain-Source conductance|
|221|gbd|Out|real|Bulk-Drain conductance|
|222|gbs|Out|real|Bulk-Source conductance|
|233|cgs|Out|real|Gate-Source capacitance|
|236|cgd|Out|real|Gate-Drain capacitance|
|239|cgb|Out|real|Gate-Bulk capacitance|
|223|cbd|Out|real|Bulk-Drain capacitance|
|224|cbs|Out|real|Bulk-Source capacitance|
|225|cbd0|Out|real|Zero-Bias B-D junction capacitance|
|226|cbdsw0|Out|real||
|227|cbs0|Out|real|Zero-Bias B-S junction capacitance|
|228|cbssw0|Out|real||
|235|cqgs|Out|real|Capacitance due to gate-source charge storage|
|238|cqgd|Out|real|Capacitance due to gate-drain charge storage|
|241|cqgb|Out|real|Capacitance due to gate-bulk charge storage|
|243|cqbd|Out|real|Capacitance due to bulk-drain charge storage|
|245|cqbs|Out|real|Capacitance due to bulk-source charge storage|
|234|qgs|Out|real|Gate-Source charge storage|
|237|qgd|Out|real|Gate-Drain charge storage|
|240|qgb|Out|real|Gate-Bulk charge storage|
|242|qbd|Out|real|Bulk-Drain charge storage|
|244|qbs|Out|real|Bulk-Source charge storage|
|19|p|Out|real|Instaneous power|
|256|sens_l_dc|Out|real|dc sensitivity wrt length|
|246|sens_l_real|Out|real|real part of ac sensitivity wrt length|
|247|sens_l_imag|Out|real|imag part of ac sensitivity wrt length|
|248|sens_l_mag|Out|real|sensitivity wrt l of ac magnitude|
|249|sens_l_ph|Out|real|sensitivity wrt l of ac phase|
|250|sens_l_cplx|Out|complex|ac sensitivity wrt length|
|257|sens_w_dc|Out|real|dc sensitivity wrt width|
|251|sens_w_real|Out|real|real part of ac sensitivity wrt width|
|252|sens_w_imag|Out|real|imag part of ac sensitivity wrt width|
|253|sens_w_mag|Out|real|sensitivity wrt w of ac magnitude|
|254|sens_w_ph|Out|real|sensitivity wrt w of ac phase|
|255|sens_w_cplx|Out|complex|ac sensitivity wrt width|


-----

**31.6.4.2** **MOS6 model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|140|type|Out|string|N-channel or P-channel MOS|
|101|vto|InOut|real|Threshold voltage|
|101|vt0|InOut|real||
|102|kv|InOut|real|Saturation voltage factor|
|103|nv|InOut|real|Saturation voltage coeff.|
|104|kc|InOut|real|Saturation current factor|
|105|nc|InOut|real|Saturation current coeff.|
|106|nvth|InOut|real|Threshold voltage coeff.|
|107|ps|InOut|real|Sat. current modification par.|
|108|gamma|InOut|real|Bulk threshold parameter|
|109|gamma1|InOut|real|Bulk threshold parameter 1|
|110|sigma|InOut|real|Static feedback effect par.|
|111|phi|InOut|real|Surface potential|
|112|lambda|InOut|real|Channel length modulation param.|
|113|lambda0|InOut|real|Channel length modulation param. 0|
|114|lambda1|InOut|real|Channel length modulation param. 1|
|115|rd|InOut|real|Drain ohmic resistance|
|116|rs|InOut|real|Source ohmic resistance|
|117|cbd|InOut|real|B-D junction capacitance|
|118|cbs|InOut|real|B-S junction capacitance|
|119|is|InOut|real|Bulk junction sat. current|
|120|pb|InOut|real|Bulk junction potential|
|121|cgso|InOut|real|Gate-source overlap cap.|
|122|cgdo|InOut|real|Gate-drain overlap cap.|
|123|cgbo|InOut|real|Gate-bulk overlap cap.|
|131|rsh|InOut|real|Sheet resistance|
|124|cj|InOut|real|Bottom junction cap per area|
|125|mj|InOut|real|Bottom grading coefficient|
|126|cjsw|InOut|real|Side junction cap per area|
|127|mjsw|InOut|real|Side grading coefficient|
|128|js|InOut|real|Bulk jct. sat. current density|
|130|ld|InOut|real|Lateral diffusion|
|129|tox|InOut|real|Oxide thickness|
|132|u0|InOut|real|Surface mobility|
|132|uo|InOut|real||
|133|fc|InOut|real|Forward bias jct. fit parm.|
|137|nmos|In|flag|N type MOSfet model|
|138|pmos|In|flag|P type MOSfet model|
|135|tpg|InOut|integer|Gate type|
|134|nsub|InOut|real|Substrate doping|
|136|nss|InOut|real|Surface state density|
|139|tnom|InOut|real|Parameter measurement temperature|


-----

### 31.6.5 MOS9 - Modified Level 3 MOSFET model

**31.6.5.1** **MOS9 instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|80|m|InOut|real|Multiplier|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|34|id|Out|real|Drain current|
|34|cd|Out|real|Drain current|
|36|ibd|Out|real|B-D junction current|
|35|ibs|Out|real|B-S junction current|
|18|is|Out|real|Source current|
|17|ig|Out|real|Gate current|
|16|ib|Out|real|Bulk current|
|50|vgs|Out|real|Gate-Source voltage|
|51|vds|Out|real|Drain-Source voltage|
|49|vbs|Out|real|Bulk-Source voltage|
|48|vbd|Out|real|Bulk-Drain voltage|
|8|nrd|InOut|real|Drain squares|
|7|nrs|InOut|real|Source squares|
|9|off|In|flag|Device initially off|
|12|icvds|InOut|real|Initial D-S voltage|
|13|icvgs|InOut|real|Initial G-S voltage|
|11|icvbs|InOut|real|Initial B-S voltage|
|10|ic|InOut|real vector|Vector of D-S, G-S, B-S voltages|
|77|temp|InOut|real|Instance operating temperature|
|81|dtemp|InOut|real|Instance operating temperature difference|
|15|sens_l|In|flag|flag to request sensitivity WRT length|
|14|sens_w|In|flag|flag to request sensitivity WRT width|
|22|dnode|Out|integer|Number of drain node|
|23|gnode|Out|integer|Number of gate node|
|24|snode|Out|integer|Number of source node|
|25|bnode|Out|integer|Number of bulk node|
|26|dnodeprime|Out|integer|Number of internal drain node|
|27|snodeprime|Out|integer|Number of internal source node|
|30|von|Out|real|Turn-on voltage|
|31|vdsat|Out|real|Saturation drain voltage|
|32|sourcevcrit|Out|real|Critical source voltage|
|33|drainvcrit|Out|real|Critical drain voltage|
|78|rs|Out|real|Source resistance|
|28|sourceconductance|Out|real|Source conductance|
|79|rd|Out|real|Drain resistance|


-----

|29|drainconductance|Out|real|Drain conductance|
|---|---|---|---|---|
|38|gm|Out|real|Transconductance|
|39|gds|Out|real|Drain-Source conductance|
|37|gmb|Out|real|Bulk-Source transconductance|
|37|gmbs|Out|real|Bulk-Source transconductance|
|40|gbd|Out|real|Bulk-Drain conductance|
|41|gbs|Out|real|Bulk-Source conductance|
|42|cbd|Out|real|Bulk-Drain capacitance|
|43|cbs|Out|real|Bulk-Source capacitance|
|52|cgs|Out|real|Gate-Source capacitance|
|55|cgd|Out|real|Gate-Drain capacitance|
|58|cgb|Out|real|Gate-Bulk capacitance|
|54|cqgs|Out|real|Capacitance due to gate-source charge storage|
|57|cqgd|Out|real|Capacitance due to gate-drain charge storage|
|60|cqgb|Out|real|Capacitance due to gate-bulk charge storage|
|62|cqbd|Out|real|Capacitance due to bulk-drain charge storage|
|64|cqbs|Out|real|Capacitance due to bulk-source charge storage|
|44|cbd0|Out|real|Zero-Bias B-D junction capacitance|
|45|cbdsw0|Out|real|Zero-Bias B-D sidewall capacitance|
|46|cbs0|Out|real|Zero-Bias B-S junction capacitance|
|47|cbssw0|Out|real|Zero-Bias B-S sidewall capacitance|
|63|qbs|Out|real|Bulk-Source charge storage|
|53|qgs|Out|real|Gate-Source charge storage|
|56|qgd|Out|real|Gate-Drain charge storage|
|59|qgb|Out|real|Gate-Bulk charge storage|
|61|qbd|Out|real|Bulk-Drain charge storage|
|19|p|Out|real|Instantaneous power|
|76|sens_l_dc|Out|real|dc sensitivity wrt length|
|70|sens_l_real|Out|real|real part of ac sensitivity wrt length|
|71|sens_l_imag|Out|real|imag part of ac sensitivity wrt length|
|74|sens_l_cplx|Out|complex|ac sensitivity wrt length|
|72|sens_l_mag|Out|real|sensitivity wrt l of ac magnitude|
|73|sens_l_ph|Out|real|sensitivity wrt l of ac phase|
|75|sens_w_dc|Out|real|dc sensitivity wrt width|
|65|sens_w_real|Out|real|real part of ac sensitivity wrt width|
|66|sens_w_imag|Out|real|imag part of ac sensitivity wrt width|
|67|sens_w_mag|Out|real|sensitivity wrt w of ac magnitude|
|68|sens_w_ph|Out|real|sensitivity wrt w of ac phase|
|69|sens_w_cplx|Out|complex|ac sensitivity wrt width|


-----

-----

**31.6.5.2** **MOS9 model parameters**

# Name Direction Type Description

144 type Out string N-channel or P-channel MOS

133 nmos In flag N type MOSfet model

134 pmos In flag P type MOSfet model

101 vto InOut real Threshold voltage

101 vt0 InOut real

102 kp InOut real Transconductance parameter

103 gamma InOut real Bulk threshold parameter

104 phi InOut real Surface potential

105 rd InOut real Drain ohmic resistance

106 rs InOut real Source ohmic resistance

107 cbd InOut real B-D junction capacitance

108 cbs InOut real B-S junction capacitance

109 is InOut real Bulk junction sat. current

110 pb InOut real Bulk junction potential

111 cgso InOut real Gate-source overlap cap.

112 cgdo InOut real Gate-drain overlap cap.

113 cgbo InOut real Gate-bulk overlap cap.

114 rsh InOut real Sheet resistance

115 cj InOut real Bottom junction cap per area

116 mj InOut real Bottom grading coefficient

117 cjsw InOut real Side junction cap per area

118 mjsw InOut real Side grading coefficient

119 js InOut real Bulk jct. sat. current density

120 tox InOut real Oxide thickness

121 ld InOut real Lateral diffusion

145 xl InOut real Length mask adjustment

146 wd InOut real Width Narrowing (Diffusion)

147 xw InOut real Width mask adjustment

148 delvto InOut real Threshold voltage Adjust

148 delvt0 InOut real

122 u0 InOut real Surface mobility

122 uo InOut real

123 fc InOut real Forward bias jct. fit parm.

124 nsub InOut real Substrate doping

125 tpg InOut integer Gate type

126 nss InOut real Surface state density

131 vmax InOut real Maximum carrier drift velocity

135 xj InOut real Junction depth

129 nfs InOut real Fast surface state density

138 xd InOut real Depletion layer width

139 alpha InOut real Alpha

127 eta InOut real Vds dependence of threshold voltage

128 delta InOut real Width effect on threshold

140 input_delta InOut real

130 theta InOut real Vgs dependence on mobility

132 kappa InOut real Kappa

141 tnom InOut real Parameter measurement temperature

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|144|type|Out|string|N-channel or P-channel MOS|
|133|nmos|In|flag|N type MOSfet model|
|134|pmos|In|flag|P type MOSfet model|
|101|vto|InOut|real|Threshold voltage|
|101|vt0|InOut|real||
|102|kp|InOut|real|Transconductance parameter|
|103|gamma|InOut|real|Bulk threshold parameter|
|104|phi|InOut|real|Surface potential|
|105|rd|InOut|real|Drain ohmic resistance|
|106|rs|InOut|real|Source ohmic resistance|
|107|cbd|InOut|real|B-D junction capacitance|
|108|cbs|InOut|real|B-S junction capacitance|
|109|is|InOut|real|Bulk junction sat. current|
|110|pb|InOut|real|Bulk junction potential|
|111|cgso|InOut|real|Gate-source overlap cap.|
|112|cgdo|InOut|real|Gate-drain overlap cap.|
|113|cgbo|InOut|real|Gate-bulk overlap cap.|
|114|rsh|InOut|real|Sheet resistance|
|115|cj|InOut|real|Bottom junction cap per area|
|116|mj|InOut|real|Bottom grading coefficient|
|117|cjsw|InOut|real|Side junction cap per area|
|118|mjsw|InOut|real|Side grading coefficient|
|119|js|InOut|real|Bulk jct. sat. current density|
|120|tox|InOut|real|Oxide thickness|
|121|ld|InOut|real|Lateral diffusion|
|145|xl|InOut|real|Length mask adjustment|
|146|wd|InOut|real|Width Narrowing (Diffusion)|
|147|xw|InOut|real|Width mask adjustment|
|148|delvto|InOut|real|Threshold voltage Adjust|
|148|delvt0|InOut|real||
|122|u0|InOut|real|Surface mobility|
|122|uo|InOut|real||
|123|fc|InOut|real|Forward bias jct. fit parm.|
|124|nsub|InOut|real|Substrate doping|
|125|tpg|InOut|integer|Gate type|
|126|nss|InOut|real|Surface state density|
|131|vmax|InOut|real|Maximum carrier drift velocity|
|135|xj|InOut|real|Junction depth|
|129|nfs|InOut|real|Fast surface state density|
|138|xd|InOut|real|Depletion layer width|
|139|alpha|InOut|real|Alpha|
|127|eta|InOut|real|Vds dependence of threshold voltage|
|128|delta|InOut|real|Width effect on threshold|
|140|input_delta|InOut|real||
|130|theta|InOut|real|Vgs dependence on mobility|
|132|kappa|InOut|real|Kappa|


-----

### 31.6.6 BSIM1 - Berkeley Short Channel IGFET Model

**31.6.6.1** **BSIM1 instance parameters**

# Name Direction Type Description

2 l InOut real Length

1 w InOut real Width

14 m InOut real Parallel Multiplier

4 ad InOut real Drain area

3 as InOut real Source area

6 pd InOut real Drain perimeter

5 ps InOut real Source perimeter

8 nrd InOut real Number of squares in drain

7 nrs InOut real Number of squares in source

9 off InOut flag Device is initially off

11 vds InOut real Initial D-S voltage

12 vgs InOut real Initial G-S voltage

10 vbs InOut real Initial B-S voltage

13 ic In unknown vector Vector of DS,GS,BS initial voltages

**31.6.6.2** **BSIM1 Model Parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|14|m|InOut|real|Parallel Multiplier|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|8|nrd|InOut|real|Number of squares in drain|
|7|nrs|InOut|real|Number of squares in source|
|9|off|InOut|flag|Device is initially off|
|11|vds|InOut|real|Initial D-S voltage|
|12|vgs|InOut|real|Initial G-S voltage|
|10|vbs|InOut|real|Initial B-S voltage|
|13|ic|In|unknown vector|Vector of DS,GS,BS initial voltages|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|101|vfb|InOut|real|Flat band voltage|
|102|lvfb|InOut|real|Length dependence of vfb|
|103|wvfb|InOut|real|Width dependence of vfb|
|104|phi|InOut|real|Strong inversion surface potential|
|105|lphi|InOut|real|Length dependence of phi|
|106|wphi|InOut|real|Width dependence of phi|
|107|k1|InOut|real|Bulk effect coefficient 1|
|108|lk1|InOut|real|Length dependence of k1|
|109|wk1|InOut|real|Width dependence of k1|
|110|k2|InOut|real|Bulk effect coefficient 2|
|111|lk2|InOut|real|Length dependence of k2|
|112|wk2|InOut|real|Width dependence of k2|
|113|eta|InOut|real|VDS dependence of threshold voltage|
|114|leta|InOut|real|Length dependence of eta|
|115|weta|InOut|real|Width dependence of eta|
|116|x2e|InOut|real|VBS dependence of eta|
|117|lx2e|InOut|real|Length dependence of x2e|
|118|wx2e|InOut|real|Width dependence of x2e|
|119|x3e|InOut|real|VDS dependence of eta|
|120|lx3e|InOut|real|Length dependence of x3e|
|121|wx3e|InOut|real|Width dependence of x3e|
|122|dl|InOut|real|Channel length reduction in um|
|123|dw|InOut|real|Channel width reduction in um|


-----

|124|muz|InOut|real|Zero field mobility at VDS=0 VGS=VTH|
|---|---|---|---|---|
|125|x2mz|InOut|real|VBS dependence of muz|
|126|lx2mz|InOut|real|Length dependence of x2mz|
|127|wx2mz|InOut|real|Width dependence of x2mz|
|128|mus|InOut|real|Mobility at VDS=VDD VGS=VTH, channel length modulation|
|129|lmus|InOut|real|Length dependence of mus|
|130|wmus|InOut|real|Width dependence of mus|
|131|x2ms|InOut|real|VBS dependence of mus|
|132|lx2ms|InOut|real|Length dependence of x2ms|
|133|wx2ms|InOut|real|Width dependence of x2ms|
|134|x3ms|InOut|real|VDS dependence of mus|
|135|lx3ms|InOut|real|Length dependence of x3ms|
|136|wx3ms|InOut|real|Width dependence of x3ms|
|137|u0|InOut|real|VGS dependence of mobility|
|138|lu0|InOut|real|Length dependence of u0|
|139|wu0|InOut|real|Width dependence of u0|
|140|x2u0|InOut|real|VBS dependence of u0|
|141|lx2u0|InOut|real|Length dependence of x2u0|
|142|wx2u0|InOut|real|Width dependence of x2u0|
|143|u1|InOut|real|VDS depence of mobility, velocity saturation|
|144|lu1|InOut|real|Length dependence of u1|
|145|wu1|InOut|real|Width dependence of u1|
|146|x2u1|InOut|real|VBS depence of u1|
|147|lx2u1|InOut|real|Length depence of x2u1|
|148|wx2u1|InOut|real|Width depence of x2u1|
|149|x3u1|InOut|real|VDS depence of u1|
|150|lx3u1|InOut|real|Length dependence of x3u1|
|151|wx3u1|InOut|real|Width depence of x3u1|
|152|n0|InOut|real|Subthreshold slope|
|153|ln0|InOut|real|Length dependence of n0|
|154|wn0|InOut|real|Width dependence of n0|
|155|nb|InOut|real|VBS dependence of subthreshold slope|
|156|lnb|InOut|real|Length dependence of nb|
|157|wnb|InOut|real|Width dependence of nb|
|158|nd|InOut|real|VDS dependence of subthreshold slope|
|159|lnd|InOut|real|Length dependence of nd|
|160|wnd|InOut|real|Width dependence of nd|
|161|tox|InOut|real|Gate oxide thickness in um|
|162|temp|InOut|real|Temperature in degree Celcius|
|163|vdd|InOut|real|Supply voltage to specify mus|
|164|cgso|InOut|real|Gate source overlap capacitance per unit channel width(m)|
|165|cgdo|InOut|real|Gate drain overlap capacitance per unit channel width(m)|
|166|cgbo|InOut|real|Gate bulk overlap capacitance per unit channel length(m)|
|167|xpart|InOut|real|Flag for channel charge partitioning|
|168|rsh|InOut|real|Source drain diffusion sheet resistance in ohm per square|
|169|js|InOut|real|Source drain junction saturation current per unit area|


-----

|170|pb|InOut|real|Source drain junction built in potential|
|---|---|---|---|---|
|171|mj|InOut|real|Source drain bottom junction capacitance grading coefficient|
|172|pbsw|InOut|real|Source drain side junction capacitance built in potential|
|173|mjsw|InOut|real|Source drain side junction capacitance grading coefficient|
|174|cj|InOut|real|Source drain bottom junction capacitance per unit area|
|175|cjsw|InOut|real|Source drain side junction capacitance per unit area|
|176|wdf|InOut|real|Default width of source drain diffusion in um|
|177|dell|InOut|real|Length reduction of source drain diffusion|
|180|kf|InOut|real|Flicker noise coefficient|
|181|af|InOut|real|Flicker noise exponent|
|178|nmos|In|flag|Flag to indicate NMOS|
|179|pmos|In|flag|Flag to indicate PMOS|


-----

### 31.6.7 BSIM2 - Berkeley Short Channel IGFET Model

**31.6.7.1** **BSIM2 instance parameters**

# Name Direction Type Description

2 l InOut real Length

1 w InOut real Width

14 m InOut real Parallel Multiplier

4 ad InOut real Drain area

3 as InOut real Source area

6 pd InOut real Drain perimeter

5 ps InOut real Source perimeter

8 nrd InOut real Number of squares in drain

7 nrs InOut real Number of squares in source

9 off InOut flag Device is initially off

11 vds InOut real Initial D-S voltage

12 vgs InOut real Initial G-S voltage

10 vbs InOut real Initial B-S voltage

13 ic In unknown vector Vector of DS,GS,BS initial voltages

**31.6.7.2** **BSIM2 model parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|2|l|InOut|real|Length|
|1|w|InOut|real|Width|
|14|m|InOut|real|Parallel Multiplier|
|4|ad|InOut|real|Drain area|
|3|as|InOut|real|Source area|
|6|pd|InOut|real|Drain perimeter|
|5|ps|InOut|real|Source perimeter|
|8|nrd|InOut|real|Number of squares in drain|
|7|nrs|InOut|real|Number of squares in source|
|9|off|InOut|flag|Device is initially off|
|11|vds|InOut|real|Initial D-S voltage|
|12|vgs|InOut|real|Initial G-S voltage|
|10|vbs|InOut|real|Initial B-S voltage|
|13|ic|In|unknown vector|Vector of DS,GS,BS initial voltages|

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|101|vfb|InOut|real|Flat band voltage|
|102|lvfb|InOut|real|Length dependence of vfb|
|103|wvfb|InOut|real|Width dependence of vfb|
|104|phi|InOut|real|Strong inversion surface potential|
|105|lphi|InOut|real|Length dependence of phi|
|106|wphi|InOut|real|Width dependence of phi|
|107|k1|InOut|real|Bulk effect coefficient 1|
|108|lk1|InOut|real|Length dependence of k1|
|109|wk1|InOut|real|Width dependence of k1|
|110|k2|InOut|real|Bulk effect coefficient 2|
|111|lk2|InOut|real|Length dependence of k2|
|112|wk2|InOut|real|Width dependence of k2|
|113|eta0|InOut|real|VDS dependence of threshold voltage at VDD=0|
|114|leta0|InOut|real|Length dependence of eta0|
|115|weta0|InOut|real|Width dependence of eta0|
|116|etab|InOut|real|VBS dependence of eta|
|117|letab|InOut|real|Length dependence of etab|
|118|wetab|InOut|real|Width dependence of etab|
|119|dl|InOut|real|Channel length reduction in um|
|120|dw|InOut|real|Channel width reduction in um|
|121|mu0|InOut|real|Low-field mobility, at VDS=0 VGS=VTH|
|122|mu0b|InOut|real|VBS dependence of low-field mobility|
|123|lmu0b|InOut|real|Length dependence of mu0b|


-----

|124|wmu0b|InOut|real|Width dependence of mu0b|
|---|---|---|---|---|
|125|mus0|InOut|real|Mobility at VDS=VDD VGS=VTH|
|126|lmus0|InOut|real|Length dependence of mus0|
|127|wmus0|InOut|real|Width dependence of mus|
|128|musb|InOut|real|VBS dependence of mus|
|129|lmusb|InOut|real|Length dependence of musb|
|130|wmusb|InOut|real|Width dependence of musb|
|131|mu20|InOut|real|VDS dependence of mu in tanh term|
|132|lmu20|InOut|real|Length dependence of mu20|
|133|wmu20|InOut|real|Width dependence of mu20|
|134|mu2b|InOut|real|VBS dependence of mu2|
|135|lmu2b|InOut|real|Length dependence of mu2b|
|136|wmu2b|InOut|real|Width dependence of mu2b|
|137|mu2g|InOut|real|VGS dependence of mu2|
|138|lmu2g|InOut|real|Length dependence of mu2g|
|139|wmu2g|InOut|real|Width dependence of mu2g|
|140|mu30|InOut|real|VDS dependence of mu in linear term|
|141|lmu30|InOut|real|Length dependence of mu30|
|142|wmu30|InOut|real|Width dependence of mu30|
|143|mu3b|InOut|real|VBS dependence of mu3|
|144|lmu3b|InOut|real|Length dependence of mu3b|
|145|wmu3b|InOut|real|Width dependence of mu3b|
|146|mu3g|InOut|real|VGS dependence of mu3|
|147|lmu3g|InOut|real|Length dependence of mu3g|
|148|wmu3g|InOut|real|Width dependence of mu3g|
|149|mu40|InOut|real|VDS dependence of mu in linear term|
|150|lmu40|InOut|real|Length dependence of mu40|
|151|wmu40|InOut|real|Width dependence of mu40|
|152|mu4b|InOut|real|VBS dependence of mu4|
|153|lmu4b|InOut|real|Length dependence of mu4b|
|154|wmu4b|InOut|real|Width dependence of mu4b|
|155|mu4g|InOut|real|VGS dependence of mu4|
|156|lmu4g|InOut|real|Length dependence of mu4g|
|157|wmu4g|InOut|real|Width dependence of mu4g|
|158|ua0|InOut|real|Linear VGS dependence of mobility|
|159|lua0|InOut|real|Length dependence of ua0|
|160|wua0|InOut|real|Width dependence of ua0|
|161|uab|InOut|real|VBS dependence of ua|
|162|luab|InOut|real|Length dependence of uab|
|163|wuab|InOut|real|Width dependence of uab|
|164|ub0|InOut|real|Quadratic VGS dependence of mobility|
|165|lub0|InOut|real|Length dependence of ub0|
|166|wub0|InOut|real|Width dependence of ub0|
|167|ubb|InOut|real|VBS dependence of ub|
|168|lubb|InOut|real|Length dependence of ubb|
|169|wubb|InOut|real|Width dependence of ubb|


-----

|170|u10|InOut|real|VDS depence of mobility|
|---|---|---|---|---|
|171|lu10|InOut|real|Length dependence of u10|
|172|wu10|InOut|real|Width dependence of u10|
|173|u1b|InOut|real|VBS depence of u1|
|174|lu1b|InOut|real|Length depence of u1b|
|175|wu1b|InOut|real|Width depence of u1b|
|176|u1d|InOut|real|VDS depence of u1|
|177|lu1d|InOut|real|Length depence of u1d|
|178|wu1d|InOut|real|Width depence of u1d|
|179|n0|InOut|real|Subthreshold slope at VDS=0 VBS=0|
|180|ln0|InOut|real|Length dependence of n0|
|181|wn0|InOut|real|Width dependence of n0|
|182|nb|InOut|real|VBS dependence of n|
|183|lnb|InOut|real|Length dependence of nb|
|184|wnb|InOut|real|Width dependence of nb|
|185|nd|InOut|real|VDS dependence of n|
|186|lnd|InOut|real|Length dependence of nd|
|187|wnd|InOut|real|Width dependence of nd|
|188|vof0|InOut|real|Threshold voltage offset AT VDS=0 VBS=0|
|189|lvof0|InOut|real|Length dependence of vof0|
|190|wvof0|InOut|real|Width dependence of vof0|
|191|vofb|InOut|real|VBS dependence of vof|
|192|lvofb|InOut|real|Length dependence of vofb|
|193|wvofb|InOut|real|Width dependence of vofb|
|194|vofd|InOut|real|VDS dependence of vof|
|195|lvofd|InOut|real|Length dependence of vofd|
|196|wvofd|InOut|real|Width dependence of vofd|
|197|ai0|InOut|real|Pre-factor of hot-electron effect.|
|198|lai0|InOut|real|Length dependence of ai0|
|199|wai0|InOut|real|Width dependence of ai0|
|200|aib|InOut|real|VBS dependence of ai|
|201|laib|InOut|real|Length dependence of aib|
|202|waib|InOut|real|Width dependence of aib|
|203|bi0|InOut|real|Exponential factor of hot-electron effect.|
|204|lbi0|InOut|real|Length dependence of bi0|
|205|wbi0|InOut|real|Width dependence of bi0|
|206|bib|InOut|real|VBS dependence of bi|
|207|lbib|InOut|real|Length dependence of bib|
|208|wbib|InOut|real|Width dependence of bib|
|209|vghigh|InOut|real|Upper bound of the cubic spline function.|
|210|lvghigh|InOut|real|Length dependence of vghigh|
|211|wvghigh|InOut|real|Width dependence of vghigh|
|212|vglow|InOut|real|Lower bound of the cubic spline function.|
|213|lvglow|InOut|real|Length dependence of vglow|
|214|wvglow|InOut|real|Width dependence of vglow|
|215|tox|InOut|real|Gate oxide thickness in um|


-----

|216|temp|InOut|real|Temperature in degree Celcius|
|---|---|---|---|---|
|217|vdd|InOut|real|Maximum Vds|
|218|vgg|InOut|real|Maximum Vgs|
|219|vbb|InOut|real|Maximum Vbs|
|220|cgso|InOut|real|Gate source overlap capacitance per unit channel width(m)|
|221|cgdo|InOut|real|Gate drain overlap capacitance per unit channel width(m)|
|222|cgbo|InOut|real|Gate bulk overlap capacitance per unit channel length(m)|
|223|xpart|InOut|real|Flag for channel charge partitioning|
|224|rsh|InOut|real|Source drain diffusion sheet resistance in ohm per square|
|225|js|InOut|real|Source drain junction saturation current per unit area|
|226|pb|InOut|real|Source drain junction built in potential|
|227|mj|InOut|real|Source drain bottom junction capacitance grading coefficient|
|228|pbsw|InOut|real|Source drain side junction capacitance built in potential|
|229|mjsw|InOut|real|Source drain side junction capacitance grading coefficient|
|230|cj|InOut|real|Source drain bottom junction capacitance per unit area|
|231|cjsw|InOut|real|Source drain side junction capacitance per unit area|
|232|wdf|InOut|real|Default width of source drain diffusion in um|
|233|dell|InOut|real|Length reduction of source drain diffusion|
|236|kf|InOut|real|Flicker noise coefficient|
|237|af|InOut|real|Flicker noise exponent|
|234|nmos|In|flag|Flag to indicate NMOS|
|235|pmos|In|flag|Flag to indicate PMOS|


-----

### 31.6.8 BSIM3

The accessible device parameters (see Chapt. 31.1 for the syntax) are listed here.

**31.6.8.1** **BSIM3 accessible instance parameters**

# Name Direction Type Description

1 id Out real Drain current

2 vgs Out real Gate-Source voltage

3 vds Out real Drain-Source voltage

4 vbs Out real Bulk-Source voltage

5 gm Out real Transconductance

6 gds Out real Drain-Source conductance

7 gmbs Out real Bulk-Source transconductance

8 vdsat Out real Saturation voltage

9 vth Out real Threshold voltage

10 ibd Out real

11 ibs Out real

12 gbd Out real

13 gbs Out real

14 qb Out real Qbulk

15 cqb Out real

16 qg Out real Qgate

17 cqg Out real

18 qd Out real Qdrain

19 cqd Out real

20 cgg Out real

21 cgd Out real

22 cgs Out real

23 cdg Out real

24 cdd Out real

25 cds Out real

26 cbg Out real

27 cbd Out real

28 cbs Out real

29 capbd Out real Diode capacitance

30 capbs Out real Diode capacitance

The parameters are available in the BSIM3 models (level=8 or level=49) version=3.2.4 and version=3.3.0 only. Negative capacitance values may occur, depending on the internal calculation.
Please see the note in Chapt. 31.6.9.1.

**31.6.8.2** **BSIM3 manual**

Further detailed descriptions will not be given here. Unfortunately the details on these para[meters are not documented, even not in the otherwise excellent pdf manual (tarred) issued by](http://www-device.eecs.berkeley.edu/bsim/Files/BSIM3/ftpv330/Mod_doc/b3v33manu.tar)

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
|1|id|Out|real|Drain current|
|2|vgs|Out|real|Gate-Source voltage|
|3|vds|Out|real|Drain-Source voltage|
|4|vbs|Out|real|Bulk-Source voltage|
|5|gm|Out|real|Transconductance|
|6|gds|Out|real|Drain-Source conductance|
|7|gmbs|Out|real|Bulk-Source transconductance|
|8|vdsat|Out|real|Saturation voltage|
|9|vth|Out|real|Threshold voltage|
|10|ibd|Out|real||
|11|ibs|Out|real||
|12|gbd|Out|real||
|13|gbs|Out|real||
|14|qb|Out|real|Qbulk|
|15|cqb|Out|real||
|16|qg|Out|real|Qgate|
|17|cqg|Out|real||
|18|qd|Out|real|Qdrain|
|19|cqd|Out|real||
|20|cgg|Out|real||
|21|cgd|Out|real||
|22|cgs|Out|real||
|23|cdg|Out|real||
|24|cdd|Out|real||
|25|cds|Out|real||
|26|cbg|Out|real||
|27|cbd|Out|real||
|28|cbs|Out|real||
|29|capbd|Out|real|Diode capacitance|
|30|capbs|Out|real|Diode capacitance|


-----

University of California at Berkeley.

### 31.6.9 BSIM4

The accessible device parameters (see Chapt. 31.1 for the syntax) are listed here.

**31.6.9.1** **BSIM4 accessible instance parameters**

|#|Name|Direction|Type|Description|
|---|---|---|---|---|
||gmbs|Out|real|Body effect (Back gate) transconductance|
||gm|Out|real|Transconductance|
||gds|Out|real|Drain-Source conductance|
||vdsat|Out|real|Saturation voltage|
||vth|Out|real|Threshold voltage|
||id|Out|real|Drain current|
||ibd|Out|real|Diode current|
||ibs|Out|real|Diode current|
||gbd|Out|real|Diode conductance|
||gbs|Out|real|Diode conductance|
||isub|Out|real|Substrate current|
||igidl|Out|real|Gate-Induced Drain Leakage current|
||igisl|Out|real|Gate-Induced Source Leakage current|
||igs|Out|real|Gate-Source current|
||igd|Out|real|Gate-drain current|
||igb|Out|real|Gate-Bulk current|
||igcs|Out|real||
||vbs|Out|real|Bulk-Source voltage|
||vgs|Out|real|Gate-Source voltage|
||vds|Out|real|Drain-Source voltage|
||cgg|Out|real||
||cgs|Out|real||
||cgd|Out|real||
||cbg|Out|real||
||cbd|Out|real||
||cbs|Out|real||
||cdg|Out|real||
||cdd|Out|real||
||cds|Out|real||
||csg|Out|real||
||csd|Out|real||
||css|Out|real||
||cgb|Out|real||
||cdb|Out|real||
||csb|Out|real||
||cbb|Out|real||


-----

|Col1|capbd|Out|real|Diode capacitance|
|---|---|---|---|---|
||capbs|Out|real|Diode capacitance|
||qg|Out|real|Gate charge|
||qb|Out|real|Bulk charge|
||qd|Out|real|Drain charge|
||qs|Out|real||
||qinv|Out|real||
||qdef|Out|real||
||gcrg|Out|real||
||gtau|Out|real||


The parameters are available in all BSIM4 models (level=14 or level=54) version=4.2.1 to version=4.8.

Negative capacitance values may occur, depending on the internal calculation. To comparing
with measured data, please just use the absolute values of the capacitance data. For an explanation of negative values and the basics on how capacitance values are evaluated in a BSIM
[model, please refer to the book BSIM4 and MOSFET modeling by Liu and Hu, Chapt. 5.2.](http://ngspice.sourceforge.net/books.html)

**31.6.9.2** **BSIM4 manual**

Detailed descriptions will not be given here. Unfortunately the details on these parameters
[are not documented, even not in the otherwise excellent pdf manual issued by University of](http://www-device.eecs.berkeley.edu/bsim/Files/BSIM4/BSIM470/BSIM470_Manual.pdf)
California at Berkeley.


-----

