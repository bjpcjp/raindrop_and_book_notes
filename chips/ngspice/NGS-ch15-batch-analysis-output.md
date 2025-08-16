# Chapter 15

 Analyses and Output Control (batch mode)

The command lines described in this chapter are specifying analyses and outputs within the
circuit description file. They start with a ‘.’ (dot commands). Specifying analyses and plots
(or tables) in the input file with dot commands is used with batch runs. Batch mode is entered
when either the -b option is given upon starting ngspice
```
ngspice -b -r rawfile.raw circuitfile.cir

```
or when the default input source is redirected from a file (see also Chapt. 16.4.1).
```
ngspice < circuitfile.cir

```
In batch mode, the analyses specified by the control lines in the input file (e.g. .ac, .tran, etc.)
are immediately executed. If the -r rawfile option is given then all data generated is written to
a ngspice rawfile. The rawfile may later be read by the interactive mode of ngspice using the
load command (see 17.5.38). In this case, the .save line (see 15.6) may be used to record the
value of internal device variables (see Appendix, Chapt. 31).

If a rawfile is not specified, then output plots (in ‘line-printer’ form) and tables can be printed
according to the .print, .plot, and .four control lines, described in Chapt. 15.6.

If ngspice is started in interactive mode (see Chapt. 16.4.2), like
```
ngspice circuitfile.cir

```
and no control section (.control ... .endc, see 16.4.3) is provided in the circuit file, the dot
commands are not executed immediately, but are waiting for manually receiving the command
run.

## 15.1 Simulator Variables (.options)

Various parameters of the simulations available in Ngspice can be altered to control the accuracy, speed, or default values for some devices. These parameters may be changed via the
option command (described in Chapt. 17.5.44) or via the .options line:


-----

General form:
```
  .options opt1 opt2 ... (or opt=optval ...)

```
Examples:
```
  .options reltol=.005 trtol=8

```
The options line allows the user to reset program control and user options for specific simulation
purposes. Options specified to Ngspice via the option command (see Chapt. 17.5.44) are also
passed on as if specified on a .options line. Any combination of the following options may
be included, in any order. ‘x’ (below) represents some positive number.

### 15.1.1 General Options

**ACCT causes accounting and run time statistics to be printed.**

**NOACCT no printing of statistics, no printing of the Initial Transient Solution.**

**NOINIT suppresses only printing of the Initial Transient Solution, maybe combined with**
ACCT.

**LIST causes the summary listing of the input data to be printed.**

**NOMOD suppresses the printout of the model parameters.**

**NOPAGE suppresses page ejects.**

**NODE causes the printing of the node table.**

**OPTS causes the option values to be printed.**

**TEMP=x Resets the operating temperature of the circuit. The default value is 27** _[◦]C (300K)._
TEMP can be overridden per device by a temperature specification on any temperature
dependent instance. May also be generally overridden by a .TEMP card (2.11).

**TNOM=x resets the nominal temperature at which device parameters are measured. The de-**
fault value is 27 _[◦]C (300 deg K). TNOM can be overridden by a specification on any_
temperature dependent device model.

**WARN=1|0 enables or turns of SOA (Safe Operating Area) voltage warning messages (default:**
0).

**MAXWARNS=x specifies the maximum number of SOA (Safe Operating Area) warning mes-**
sages per model (default: 5).

**SAVECURRENTS save currents through all terminals of the following devices: M, J, Q, D,**
R, C, L, B, F, G, W, S, I (see 2.1.2). Recommended only for small circuits, because
otherwise memory requirements explode and simulation speed suffers. See 15.7 for more
details.


-----

### 15.1.2 DC Solution Options

The following options controls properties pertaining to DC analysis and algorithms. Since
transient analysis is based on DC many of the options affect the latter one.

**ABSTOL=x resets the absolute current error tolerance of the program. The default value is 1**
pA.

**GMIN=x resets the value of GMIN, the minimum conductance allowed by the program. The**
default value is 1.0e-12.

**ITL1=x resets the dc iteration limit. The default is 100.**

**ITL2=x resets the dc transfer curve iteration limit. The default is 50.**

**KEEPOPINFO Retain the operating point information when either an AC, Distortion, or Pole-**
Zero analysis is run. This is particularly useful if the circuit is large and you do not want
to run a (redundant) .OP analysis.

**PIVREL=x resets the relative ratio between the largest column entry and an acceptable pivot**
value. The default value is 1.0e-3. In the numerical pivoting algorithm the allowed minimum pivot value is determined by EPSREL = AMAX1(PIVREL `MAXVAL, PIVTOL) where`

_·_
MAXVAL is the maximum element in the column where a pivot is sought (partial pivoting).

**PIVTOL=x resets the absolute minimum value for a matrix entry to be accepted as a pivot.**
The default value is 1.0e-13.

**RELTOL=x resets the relative error tolerance of the program. The default value is 0.001**
(0.1%).

**RSHUNT=x introduces a resistor from each analog node to ground. The value of the resistor**
should be high enough to not interfere with circuit operations. The XSPICE option has to
be enabled (see 32.1.5) .

**VNTOL=x resets the absolute voltage error tolerance of the program. The default value is 1**
_µV_ .

**15.1.2.1** **Matrix Conditioning info**

In most SPICE-based simulators, problems can arise with certain circuit topologies. One of
the most common problems is the absence of a DC path to ground at some node. This may
happen, for example, when two capacitors are connected in series with no other connection at
the common node or when certain code models are cascaded. The result is an ill-conditioned
or nearly singular matrix that prevents the simulation from completing. The XSPICE option
introduces the rshunt option to help eliminate this problem. When used, this option inserts
resistors to ground at all the analog nodes in the circuit. In general, the value of rshunt should
be set to some very high resistance (e.g. 1000 Meg Ohms or greater) so that the operation of the
circuit is essentially unaffected, but the matrix problems are corrected. If you should encounter
a ‘no DC path to ground’ or a ‘matrix is nearly singular’ error message with your circuit, you
should try adding the following .option card to your circuit description deck.


-----

```
  .option rshunt = 1.0e12

```
Usually a value of 1.0e12 is sufficient to correct the matrix problems. However, if you still have
problems, you may wish to try lowering this value to 1.0e10 or 1.0e9.

Another matrix conditioning problem might occur if you try to place an inductor in parallel to
a voltage source. An ac simulation will fail, because it is preceded by an op analysis. Option
noopac (15.1.3) will help if the circuit is linear. If the circuit is non-linear, you will need the
op analysis. Then adding a small resistor (e.g. 1e-4 Ohms) in series to the inductor will help to
obtain convergence.
```
  .option rseries = 1.0e-4

```
will add a series resistor to each inductor in the circuit. Be careful if you use behavioral inductors (see 3.2.12), because the result may become unpredictable.

### 15.1.3 AC Solution Options

**NOOPAC Do not do an operating point (OP) analysis before the AC analysis. To become**
valid, this option requires that the circuit is linear, thus consists only of R, L, and C
devices, independent V, I sources and linear dependent E, G, H, and F sources (without
poly statement, non-behavioral). If a non-linear device is detected, the OP analysis will
be executed automatically. This option is of interest for example in nested LC circuits,
where there is no series resistance for the L device given, which during OP analysis may
result in an ill formed matrix, yields an error message and aborts the simulation.

### 15.1.4 Transient Analysis Options

**AUTOSTOP stops a transient analysis after successfully calculating all measure functions**
(15.4) specified with the dot command .meas. Autostop is not available with meas
(17.5.39) used in control mode.

**CHGTOL=x resets the charge tolerance of the program. The default value is 1.0e-14.**

**CONVSTEP=x relative step limit applied to code models.**

**CONVABSSTEP=x absolute step limit applied to code models.**

**GMINSTEPS=x [*] sets number of Gmin steps to be attempted. If the value is set to zero, the**
gmin stepping algorithm is disabled. In such case the source stepping algorithm becomes
the standard when the standard procedure fails to converge to a solution.

**INTERP interpolates output data onto fixed time steps, detemined by TSTEP (15.3.9). Uses**
linear interpolation between previous and next time value. Simulation itself is not influenced by this option. May be used in all simulation modes (batch, control or interactive, 16.4). This option may drastically reduce memory requirements in control mode
or file size in batch mode, but be careful not to choose a too large TSTEP value, otherwise your output data may be corrupted by undersampling. See command ’linearize’
(17.5.36) in control or interactive mode to achieve similar outputs by post-processing of
data. See ngspice/examples/xspice/delta-sigma/delta-sigma-1.cir how INTERP will
reduce memory requirements and speeds up plotting.


-----

**ITL3=x resets the lower transient analysis iteration limit. the default value is 4. (Note: not**
implemented in Spice3).

**ITL4=x resets the transient analysis time-point iteration limit. the default is 10.**

**ITL5=x resets the transient analysis total iteration limit. the default is 5000. Set ITL5=0 to**
omit this test. (Note: not implemented in Spice3).

**ITL6=x [*] synonym for SRCSTEPS.**

**MAXEVITER=x sets the number of event iterations that are allowed at an analysis point**

**MAXOPALTER=x specifies the maximum number of analog/event alternations that the simu-**
lator can use in solving a hybrid circuit.

**MAXORD=x [*] specifies the maximum order for the numerical integration method used by**
SPICE. Possible values for the Gear method are from 2 (the default) to 6. Using the value
1 with the trapezoidal method specifies backward Euler integration.

**METHOD=name sets the numerical integration method used by SPICE. Possible names are**
‘Gear’ or ‘trapezoidal’ (or just ‘trap’). The default is trapezoidal.

**NOOPALTER=TRUE|FALSE if set to false alternations between analog/event are enabled.**

**RAMPTIME=x this options sets the rate of change of independent supplies and code model**
inductors and capacitors with initial conditions specified.

**SRCSTEPS=x [*] a non-zero value causes SPICE to use a source-stepping method to find the**
DC operating point. Its value specifies the number of steps.

**TRTOL=x resets the transient error tolerance. The default value is 7. This parameter is an esti-**
mate of the factor by which ngspice overestimates the actual truncation error. If XSPICE
is enabled and ’A’ devices included, the value is internally set to 1 for higher precision.
This will cost a factor of two in CPU time during transient analysis.

**XMU=x sets a damping factor for trapezoidal integration. The default value is XMU=0.5. A**
value < 0.5 may be chosen. Even a small reduction, e.g. to 0.495, may suppress trap
ringing. The reduction has to be set carefully in order not to excessively damp circuits
that are prone to ringing, and lead the simulation (and the user) to believe that the circuit
is stable.

### 15.1.5 ELEMENT Specific options

**BADMOS3 Use the older version of the MOS3 model with the ‘kappa’ discontinuity.**

**DEFAD=x resets the value for MOS drain diffusion area; the default is 0.0.**

**DEFAS=x resets the value for MOS source diffusion area; the default is 0.0.**

**DEFL=x resets the value for MOS channel length; the default is 100.0 µm.**

**DEFW=x resets the value for MOS channel width; the default is 100.0 µm.**


-----

**SCALE=x set the element scaling factor for geometric element parameters whose default unit**
is meters. As an example: scale=1u and a MOSFET instance parameter W=10 will result
in a width of 10µm for this device. An area parameter AD=20 will result in 20e-12 m[2].
Following instance parameters are scaled:

  - Resistors and Capacitors: W, L

  - Diodes: W, L, Area

  - JFET, MESFET: W, L, Area

  - MOSFET: W, L, AS, AD, PS, PD, SA, SB, SC, SD

### 15.1.6 Transmission Lines Specific Options

**TRYTOCOMPACT Applicable only to the LTRA model (see 6.2.1). When specified, the**
simulator tries to condense LTRA transmission line’s past history of input voltages and
currents.

### 15.1.7 Precedence of option and .options commands

There are various ways to set the above mentioned options in Ngspice. If no option or
```
.options lines are set by the user, internal default values are given for each of the simula
```
tor variables.

You may set options in the init files spinit or .spiceinit via the option command (see Chapt.
17.5.44). The values given here will supersede the default values. If you set options via the
```
.options line in your input file, their values will supersede the default and init file data. Finally

```
if you set options inside a .control ... .endc section, these values will supersede any values
of the respective simulator variables given so far.

## 15.2 Initial Conditions

### 15.2.1 .NODESET: Specify Initial Node Voltage Guesses

General form:
```
  .NODESET V(NODNUM)=VAL V(NODNUM)=VAL ...
  .NODESET ALL=VAL

```
Examples:
```
  .NODESET V(12)=4.5 V(4)=2.23
  .NODESET ALL=1.5

```

-----

The .nodeset line helps the program find the dc or initial transient solution by making a
preliminary pass with the specified nodes held to the given voltages. The restriction is then
released and the iteration continues to the true solution. The .nodeset line may be necessary
for convergence on bistable or a-stable circuits. .nodeset all=val allows to set all starting
node voltages (except for the ground node) in a single line. In general, the .nodeset line
should not be necessary.

### 15.2.2 .IC: Set Initial Conditions

General form:
```
  .ic v(nodnum)=val v(nodnum)=val ...

```
Examples:
```
  .ic v(11)=5 v(4)=-5 v(2)=2.2

```
The .ic line is for setting transient initial conditions. It has two different interpretations, depending on whether the uic parameter is specified on the .tran control line. Also, one should
not confuse this line with the .nodeset line. The .nodeset line is only to help dc convergence, and does not affect the final bias solution (except for multi-stable circuits). The two
interpretations of this line are as follows:

1. When the uic parameter is specified on the .tran line, then the node voltages specified
on the .ic control line are used to compute the capacitor, diode, BJT, JFET, and MOSFET
initial conditions. This is equivalent to specifying the ic=... parameter on each device
line, but is much more convenient. The ic=... parameter can still be specified and takes
precedence over the .ic values. Since no dc bias (initial transient) solution is computed
before the transient analysis, one should take care to specify all dc source voltages on the
```
  .ic control line if they are to be used to compute device initial conditions.

```
2. When the uic parameter is not specified on the .tran control line, the dc bias (initial
transient) solution is computed before the transient analysis. In this case, the node voltages specified on the .ic control lines are forced to the desired initial values during the
bias solution. During transient analysis, the constraint on these node voltages is removed.
This is the preferred method since it allows ngspice to compute a consistent dc solution.


-----

## 15.3 Analyses

### 15.3.1 .AC: Small-Signal AC Analysis

General form:
```
  .ac dec nd fstart fstop
  .ac oct no fstart fstop
  .ac lin np fstart fstop

```
Examples:
```
  .ac dec 10 1 10K
  .ac dec 10 1K 100MEG
  .ac lin 100 1 100HZ
dec stands for decade variation, and nd is the number of points per decade. oct stands for

```
octave variation, and no is the number of points per octave. lin stands for linear variation, and
```
np is the number of points. fstart is the starting frequency, and fstop is the final frequency.

```
If this line is included in the input file, ngspice performs an AC analysis of the circuit over the
specified frequency range. Note that in order for this analysis to be meaningful, at least one
independent source must have been specified with an ac value. Typically it does not make much
sense to specify more than one ac source. If you do, the result will be a superposition of all
sources, thus difficult to interpret.

Example:
```
   Basic RC circuit
  r 1 2 1.0
  c 2 0 1.0
   vin 1 0 dc 0 ac 1 $ <--- the ac source
  .options noacct
  .ac dec 10 .01 10
  .plot ac vdb(2) xlog
  .end

```
In this ac (or ’small signal’) analysis all non-linear devices are linearized around their actual dc
operating point. All Ls and Cs get their imaginary value, depending on the actual frequency
step. Each output vector will be calculated relative to the input voltage (current) given by the ac
value (Vin equals to 1 in the example above). The resulting node voltages (and branch currents)
are complex vectors. Therefore you have to be careful using the plot command. Especially
you may use the variants of vxx(node) described in Chapt. 15.6.2 like vdb(2) (see example
above).


-----

### 15.3.2 .DC: DC Transfer Function

General form:
```
  .dc srcnam vstart vstop vincr [src2 start2 stop2 incr2]

```
Examples:
```
  .dc VIN 0.25 5.0 0.25
  .dc VDS 0 10 .5 VGS 0 5 1
  .dc VCE 0 10 .25 IB 0 10u 1u
  .dc RLoad 1k 2k 100
  .dc TEMP -15 75 5

```
The .dc line defines the dc transfer curve source and sweep limits (again with capacitors open
and inductors shorted). srcnam is the name of an independent voltage or current source, a
resistor or the circuit temperature. vstart, vstop, and vincr are the starting, final, and incrementing values respectively. The first example causes the value of the voltage source VIN
to be swept from 0.25 Volts to 5.0 Volts in increments of 0.25 Volts. A second source (src2)
may optionally be specified with associated sweep parameters. In this case, the first source is
swept over its range for each value of the second source. This option can be useful for obtaining
semiconductor device output characteristics. See the example circuit description on transistor
characteristics (21.3).

### 15.3.3 .DISTO: Distortion Analysis

General form:
```
  .disto dec nd fstart fstop <f2overf1 >
  .disto oct no fstart fstop <f2overf1 >
  .disto lin np fstart fstop <f2overf1 >

```
Examples:
```
  .disto dec 10 1kHz 100MEG
  .disto dec 10 1kHz 100MEG 0.9

```
The .disto line does a small-signal distortion analysis of the circuit. A multi-dimensional Volterra series analysis is done using multi-dimensional Taylor series to represent the nonlinearities
at the operating point. Terms of up to third order are used in the series expansions.

If the optional parameter f2overf1 is not specified, .disto does a harmonic analysis - i.e.,
it analyses distortion in the circuit using only a single input frequency F1, which is swept as
specified by arguments of the .disto command exactly as in the .ac command. Inputs at this
frequency may be present at more than one input source, and their magnitudes and phases are
specified by the arguments of the distof1 keyword in the input file lines for the input sources


-----

(see the description for independent sources). (The arguments of the distof2 keyword are not
relevant in this case).

The analysis produces information about the AC values of all node voltages and branch currents
at the harmonic frequencies 2F1 and, vs. the input frequency F1 as it is swept. (A value of 1
(as a complex distortion output) signifies cos(2π(2F1)t) at 2F1 and cos(2π(3F1)t) at 3F1, using
the convention that 1 at the input fundamental frequency is equivalent to cos(2πF1t).) The
distortion component desired (2F1 or 3F1) can be selected using commands in ngnutmeg, and
then printed or plotted. (Normally, one is interested primarily in the magnitude of the harmonic
components, so the magnitude of the AC distortion value is looked at). It should be noted that
these are the AC values of the actual harmonic components, and are not equal to HD2 and HD3.
To obtain HD2 and HD3, one must divide by the corresponding AC values at F1, obtained from
an .ac line. This division can be done using ngnutmeg commands.

If the optional f2overf1 parameter is specified, it should be a real number between (and not
equal to) 0.0 and 1.0; in this case, .disto does a spectral analysis. It considers the circuit with
sinusoidal inputs at two different frequencies F1 and F2. F1 is swept according to the .disto
control line options exactly as in the .ac control line. F2 is kept fixed at a single frequency
as F1 sweeps - the value at which it is kept fixed is equal to f2overf1 times fstart. Each
independent source in the circuit may potentially have two (superimposed) sinusoidal inputs
for distortion, at the frequencies F1 and F2. The magnitude and phase of the F1 component are
specified by the arguments of the distof1 keyword in the source’s input line (see the description of independent sources); the magnitude and phase of the F2 component are specified by the
arguments of the distof2 keyword. The analysis produces plots of all node voltages/branch
currents at the intermodulation product frequencies F1 + F2, F1 − _F2, and (2F1) −_ _F2, vs the_
swept frequency F1. The IM product of interest may be selected using the setplot command,
and displayed with the print and plot commands. It is to be noted as in the harmonic analysis
case, the results are the actual AC voltages and currents at the intermodulation frequencies, and
need to be normalized with respect to .ac values to obtain the IM parameters.

If the distof1 or distof2 keywords are missing from the description of an independent
source, then that source is assumed to have no input at the corresponding frequency. The default
values of the magnitude and phase are 1.0 and 0.0 respectively. The phase should be specified
in degrees.

It should be carefully noted that the number f2overf1 should ideally be an irrational number,
and that since this is not possible in practice, efforts should be made to keep the denominator
in its fractional representation as large as possible, certainly above 3, for accurate results (i.e.,
if f2overf1 is represented as a fraction _[A]/B, where A and B are integers with no common_
factors, B should be as large as possible; note that A < B because f2overf1 is constrained
to be < 1). To illustrate why, consider the cases where f2overf1 is 49/100 and 1/2. In a
spectral analysis, the outputs produced are at F1 + F2, F1 _F2 and 2F1_ _F2. In the latter case,_
_−_ _−_
_F1_ _F2 = F2, so the result at the F1_ _F2 component is erroneous because there is the strong_
_−_ _−_
fundamental F2 component at the same frequency. Also, F1 + F2 = 2F1 _F2 in the latter case,_
_−_
and each result is erroneous individually. This problem is not there in the case where f2overf1
= 49/100, because F1 _F2 = 51/100 F1 <> 49/100 F1 = F2. In this case, there are two very_
_−_
closely spaced frequency components at F2 and F1 _F2. One of the advantages of the Volterra_
_−_
series technique is that it computes distortions at mix frequencies expressed symbolically (i.e.
_nF1 + mF2), therefore one is able to obtain the strengths of distortion components accurately_
even if the separation between them is very small, as opposed to transient analysis for example.
The disadvantage is of course that if two of the mix frequencies coincide, the results are not


-----

merged together and presented (though this could presumably be done as a postprocessing step).
Currently, the interested user should keep track of the mix frequencies himself or herself and
add the distortions at coinciding mix frequencies together should it be necessary.

Only a subset of the ngspice nonlinear device models supports distortion analysis. These are

  - Diodes (DIO),

  - BJT,

  - JFET (level 1),

  - MOSFETs (levels 1, 2, 3, 9, and BSIM1),

  - MESFET (level 1).

### 15.3.4 .NOISE: Noise Analysis

General form:
```
  .noise v(output <,ref>) src ( dec | lin | oct ) pts fstart fstop
  + <pts_per_summary >

```
Examples:
```
  .noise v(5) VIN dec 10 1kHz 100MEG
  .noise v(5,3) V1 oct 8 1.0 1.0e6 1

```
The .noise line does a noise analysis of the circuit. output is the node at which the total
output noise is desired; if ref is specified, then the noise voltage v(output) - v(ref) is
calculated. By default, ref is assumed to be ground. src is the name of an independent source
to which input noise is referred. pts, fstart and fstop are .ac type parameters that specify
the frequency range over which plots are desired. pts_per_summary is an optional integer; if
specified, the noise contributions of each noise generator is produced every pts_per_summary
frequency points. The .noise control line produces two plots:

1. one for the Noise Spectral Density (in _[V]/[√]Hz or_ _[A]/[√]Hz ) curves and_

2. one for the total Integrated Noise (in V or A) over the specified frequency range.

### 15.3.5 .OP: Operating Point Analysis

General form:
```
  .op

```
The inclusion of this line in an input file directs ngspice to determine the dc operating point of
the circuit with inductors shorted and capacitors opened.


-----

Note: a DC analysis is automatically performed prior to a transient analysis to determine the
transient initial conditions, and prior to an AC small-signal, Noise, and Pole-Zero analysis
to determine the linearized, small-signal models for nonlinear devices (see the KEEPOPINFO
variable 15.1.2).

### 15.3.6 .PZ: Pole-Zero Analysis

General form:
```
  .pz node1 node2 node3 node4 cur pol
  .pz node1 node2 node3 node4 cur zer
  .pz node1 node2 node3 node4 cur pz
  .pz node1 node2 node3 node4 vol pol
  .pz node1 node2 NODE3 node4 vol zer
  .pz node1 node2 node3 node4 vol pz

```
Examples:
```
  .pz 1 0 3 0 cur pol
  .pz 2 3 5 0 vol zer
  .pz 4 1 4 1 cur pz
cur stands for a transfer function of the type (output voltage)/(input current) while vol stands

```
for a transfer function of the type (output voltage)/(input voltage). pol stands for pole analysis
only, zer for zero analysis only and pz for both. This feature is provided mainly because if there
is a non-convergence in finding poles or zeros, then, at least the other can be found. Finally,
```
node1 and node2 are the two input nodes and node3 and node4 are the two output nodes.

```
Thus, there is complete freedom regarding the output and input ports and the type of transfer
function.

In interactive mode, the command syntax is the same except that the first field is pz instead of
```
.pz. To print the results, one should use the command print all.

```

-----

### 15.3.7 .SENS: DC or Small-Signal AC Sensitivity Analysis

General form:
```
  .SENS OUTVAR
  .SENS OUTVAR AC DEC ND FSTART FSTOP
  .SENS OUTVAR AC OCT NO FSTART FSTOP
  .SENS OUTVAR AC LIN NP FSTART FSTOP

```
Examples:
```
  .SENS V(1,OUT)
  .SENS V(OUT) AC DEC 10 100 100k
  .SENS I(VTEST)

```
The sensitivity of OUTVAR to all non-zero device parameters is calculated when the SENS
analysis is specified. OUTVAR is a circuit variable (node voltage or voltage-source branch
current). The first form calculates sensitivity of the DC operating-point value of OUTVAR.
The second form calculates sensitivity of the AC values of OUTVAR. The parameters listed
for AC sensitivity are the same as in an AC analysis (see .AC above). The output values are in
dimensions of change in output per unit change of input (as opposed to percent change in output
or per percent change of input).

### 15.3.8 .TF: Transfer Function Analysis

General form:
```
  .tf outvar insrc

```
Examples:
```
  .tf v(5, 3) VIN
  .tf i(VLOAD) VIN

```
The .tf line defines the small-signal output and input for the dc small-signal analysis. outvar
is the small signal output variable and insrc is the small-signal input source. If this line is
included, ngspice computes the dc small-signal value of the transfer function (output/input),
input resistance, and output resistance. For the first example, ngspice would compute the ratio
of V(5, 3) to VIN, the small-signal input resistance at VIN, and the small signal output resistance
measured across nodes 5 and 3.


-----

### 15.3.9 .TRAN: Transient Analysis

General form:
```
  .tran tstep tstop <tstart <tmax>> <uic>

```
Examples:
```
  .tran 1ns 100ns
  .tran 1ns 1000ns 500ns
  .tran 10ns 1us
tstep is the printing or plotting increment for line-printer output. For use with the post
```
processor, tstep is the suggested computing increment. tstop is the final time, and tstart
is the initial time. If tstart is omitted, it is assumed to be zero. The transient analysis always
begins at time zero. In the interval <zero, tstart>, the circuit is analyzed (to reach a steady
state), but no outputs are stored. In the interval <tstart, tstop>, the circuit is analyzed and
outputs are stored. tmax is the maximum stepsize that ngspice uses; for default, the program
chooses either tstep or (tstop-tstart)/50.0, whichever is smaller. tmax is useful when one
wishes to guarantee a computing interval that is smaller than the printer increment, tstep.

An initial transient operating point at time zero is calculated according to the following procedure: all independent voltages and currents are applied with their time zero values, all capacitances are opened, inductances are shorted, the non linear device equations are solved iteratively.
```
uic (use initial conditions) is an optional keyword that indicates that the user does not want

```
ngspice to solve for the quiescent operating point before beginning the transient analysis. If this
keyword is specified, ngspice uses the values specified using IC=... on the various elements as
the initial transient condition and proceeds with the analysis. If the .ic control line has been
specified (see 15.2.2), then the node voltages on the .ic line are used to compute the initial
conditions for the devices. IC=... will take precedence over the values given in the .ic control
line. If neither IC=... nor the .ic control line is given for a specific node, node voltage zero is
assumed.

Look at the description on the .ic control line (15.2.2) for its interpretation when uic is not
specified.

### 15.3.10 Transient noise analysis (at low frequency)

In contrast to the analysis types described above the transient noise simulation (noise current or
voltage versus time) is not implemented as a dot command, but is integrated with the independent voltage source vsrc (isrc not yet available) (see 4.1.7) and used in combination with the
```
.tran transient analysis (15.3.9).

```
Transient noise analysis deals with noise currents or voltages added to your circuits as a time
dependent signal of randomly generated voltage excursion on top of a fixed dc voltage. The
sequence of voltage values has random amplitude, but equidistant time intervals, selectable by
the user (parameter NT). The resulting voltage waveform is differentiable and thus does not
require any modifications of the matrix solving algorithms.


-----

White noise is generated by the ngspice random number generator, applying the Box-Muller
transform. Values are generated on the fly, each time when a breakpoint is hit.

The 1/f noise is generated with an algorithm provided by N. J. Kasdin (‘Discrete simulation of
_colored noise and stochastic processes and 1/ f_ _[a]_ _power law noise generation’, Proceedings of_
the IEEE, Volume 83, Issue 5, May 1995 Page(s):802–827). The noise sequence (one for each
voltage/current source with 1/f selected) is generated upon start up of the simulator and stored
for later use. The number of points is determined by the total simulation time divided by NT,
rounded up the the nearest power of 2. Each time a breakpoint (n ⋆ _NT_, relevant to the noise
signal) is hit, the next value is retrieved from the sequence.

If you want a random, but reproducible sequence, you may select a seed value for the random
number generator by adding
```
set rndseed=nn

```
to the spinit or .spiceinit file, nn being a positive integer number.

The transient noise analysis will allow the simulation of the three most important noise sources.
Thermal noise is described by the Gaussian white noise. Flicker noise (pink noise or 1 over
f noise) with an exponent between 0 and 2 is provided as well. Shot noise is dependent on
the current flowing through a device and may be simulated by applying a non-linear source as
demonstrated in the following example:

Example:
```
  * Shot noise test with B source, diode
  * voltage on device (diode, forward)
   Vdev out 0 DC 0 PULSE(0.4 0.45 10u)
  * diode, forward direction, to be modeled with noise
  D1 mess 0 DMOD
  .model DMOD D IS=1e-14 N=1
  X1 0 mess out ishot
  * device between 1 and 2
  * new output terminals of device including noise: 1 and 3
  .subckt ishot 1 2 3
  * white noise source with rms 1V
  * 20000 sample points
   VNG 0 11 DC 0 TRNOISE(1 1n 0 0)
  *measure the current i(v1)
  V1 2 3 DC 0
  * calculate the shot noise
  * sqrt(2*current*q*bandwidth)
  BI 1 3 I=sqrt(2*abs(i(v1))*1.6e-19*1e7)*v(11)
  .ends ishot
  .tran 1n 20u
  .control
   run
   plot (-1)*i(vdev)
  .endc
  .end

```

-----

The selection of the delta time step (NT) is worth discussing. Gaussian white noise has unlimited
bandwidth and thus unlimited energy content. This is unrealistic. The bandwidth of real noise
is limited, but it is still called ‘White’ if it is the same level throughout the frequency range
of interest, e.g. the bandwidth of your system. Thus you may select NT to be a factor of 10
smaller than the frequency limit of your circuit. A thorough analysis is still needed to clarify the
appropriate factor. The transient method is probably most suited to circuits including switches,
which are not amenable to the small signal .NOISE analysis (Chapt. 15.3.4).

There is a price you have to pay for transient noise analysis: the number of required time steps,
and thus the simulation time, increases.

In addition to white and 1/f noise the independent voltage and current sources offer a random
telegraph signal (RTS) noise source, also known as burst noise or popcorn noise, again for
transient analysis. For each voltage (current) source offering RTS noise an individual noise
amplitude is required for input, as well as a mean capture time and a mean emission time.
The amplitude resembles the influence of a single trap on the current or voltage. The capture
and emission times emulate the filling and emptying of the trap, typically following a Poisson
process. They are generated from an random exponential distribution with respective mean
values given by the user. To simulate an ensemble of traps, you may combine several current or
voltage sources with different parameters.

All three sources (white, 1/f, and RTS) may be combined in a single command line.


-----

RTS noise example:
```
  * white noise, 1/f noise, RTS noise
  * voltage source
   VRTS2 13 12 DC 0 trnoise(0 0 0 0 5m 18u 30u)
   VRTS3 11 0 DC 0 trnoise(0 0 0 0 10m 20u 40u)
   VALL 12 11 DC 0 trnoise(1m 1u 1.0 0.1m 15m 22u 50u)
   VW1of 21 0 DC trnoise(1m 1u 1.0 0.1m)
  * current source
   IRTS2 10 0 DC 0 trnoise(0 0 0 0 5m 18u 30u)
   IRTS3 10 0 DC 0 trnoise(0 0 0 0 10m 20u 40u)
   IALL 10 0 DC 0 trnoise(1m 1u 1.0 0.1m 15m 22u 50u)
   R10 10 0 1
   IW1of 9 0 DC trnoise(1m 1u 1.0 0.1m)
   Rall 9 0 1
  * sample points
  .tran 1u 500u
  .control
   run
   plot v(13) v(21)
   plot v(10) v(9)
  .endc
  .end

```
[Some details on RTS noise modeling are available in a recent article [20], available here.](http://www.see.ed.ac.uk/~tbt/iscas09.pdf)

_This transient noise feature is still experimental._

The following questions (among others) are to be solved:

  - clarify the theoretical background

  - noise limit of plain ngspice (numerical solver, fft etc.)

  - time step (NT) selection

  - calibration of noise spectral density

  - how to generate noise from a transistor model

  - application benefits and limits


-----

### 15.3.11 .PSS: Periodic Steady State Analysis

_Experimental code, not yet made publicly available._

General form:
```
  .pss gfreq tstab oscnob psspoints harms sciter steadycoeff <uic>

```
Examples:
```
  .pss 150 200e-3 2 1024 11 50 5e-3 uic
  .pss 624e6 1u v_plus 1024 10 150 5e-3 uic
  .pss 624e6 500n bout 1024 10 100 5e-3 uic
gfreq is guessed frequency of fundamental suggested by user. When performing transient

```
analysis the PSS algorithm tries to infer a new rough guess rgfreq on the fundamental. If
`gfreq is out of` 10% with respect to rgfreq then gfreq is discarded.
_±_
```
tstab is stabilization time before the shooting begin to search for the PSS. It has to be noticed

```
that this parameter heavily influence the possibility to reach the PSS. Thus is a good practice to
ensure a circuit to have a right tstab, e.g. performing a separate TRAN analysis before to run
PSS analysis.
```
oscnob is the node or branch where the oscillation dynamic is expected. PSS analysis will give

```
a brief report of harmonic content at this node or branch.
```
psspoints is number of step in evaluating predicted period after convergence is reached. It

```
is useful only in Time Domain plots. However this number should be higher than 2 times the
requested harms. Otherwise the PSS analysis will properly adjust it.
```
harms number of harmonics to be calculated as requested by the user.
sciter number of allowed shooting cycle iterations. Default is 50.
steady_coeff is the weighting coefficient for calculating the Global Convergence Error (GCE),

```
which is the reference value in order to infer is convergence is reached. The lower steady_coeff
is set, the higher the accuracy of predicted frequency can be reached but at longer analysis time
and sciter number. Default is 1e-3.
```
uic (use initial conditions) is an optional keyword that indicates that the user does not want

```
ngspice to solve for the quiescent operating point before beginning the transient analysis. If this
keyword is specified, ngspice uses the values specified using IC=... on the various elements as
the initial transient condition and proceeds with the analysis. If the .ic control line has been
specified, then the node voltages on the .ic line are used to compute the initial conditions for
the devices. Look at the description on the .ic control line for its interpretation when uic is
not specified.


-----

## 15.4 Measurements after AC, DC and Transient Analysis

### 15.4.1 .meas(ure)

The .meas or .measure statement (and its equivalent meas command, see Chapt. 17.5.39)
are used to analyze the output data of a tran, ac, or dc simulation. The command is executed
immediately after the simulation has finished.

### 15.4.2 batch versus interactive mode
```
.meas analysis may not be used in batch mode (-b command line option), if an output file

```
(rawfile) is given at the same time (-r rawfile command line option). In this batch mode
ngspice will write its simulation output data directly to the output file. The data is not kept in
memory, thus is no longer available for further analysis. This is made to allow a very large
output stream with only a relatively small memory usage. For .meas to be active you need to
run the batch mode with a .plot or .print command. A better alternative may be to start
ngspice in interactive mode.

If you need batch like operation, you may add a .control ... `.endc section to the input`
file:

Example:
```
  *input file
   ...
  .tran 1ns 1000ns
   ...
   *********************************
  .control
   run
   write outputfile data
  .endc
   *********************************
  .end

```
and start ngspice in interactive mode, e.g. by running the command
```
ngspice inputfile .
.meas<ure> then prints its user-defined data analysis to the standard output. The analysis

```
includes propagation, delay, rise time, fall time, peak-to-peak voltage, minimum or maximum
voltage, the integral or derivative over a specified period and several other user defined values.

### 15.4.3 General remarks

The measure type {DC|AC|TRAN|SP} depends on the data that is to be evaluated, either originating from a dc analysis, an ac analysis, or a transient simulation. The type SP to analyze a
spectrum from the spec or fft commands is only available when executed in a meas command,
see 17.5.39.


-----

**result will be a vector containing the result of the measurement. trig_variable, targ_variable,**
and out_variable are vectors stemming from the simulation, e.g. a voltage vector v(out).
```
VAL=val expects a real number val. It may be as well a parameter delimited by ” or {}

```
expanding to a real number.
```
TD=td and AT=time expect a time value if measure type is tran. For ac and sp AT will be a

```
frequency value, TD is ignored. For dc analysis AT is a voltage (or current), TD is ignored as
well.
```
CROSS=# requires an integer number #. CROSS=LAST is possible as well. The same is expected

```
by RISE and FALL.

Frequency and time values may start at 0 and extend to positive real numbers. Voltage (or
current) inputs for the independent (scale) axis in a dc analysis may start or end at arbitrary real
valued numbers.

Please note that not all of the .measure commands have been implemented.

### 15.4.4 Input

In the following lines you will get some explanation on the .measure commands. A simple
simulation file with two sines of different frequencies may serve as an example. The transient
simulation delivers time as the independent variable and two voltages as output (dependent
variables).

Input file:
```
   File: simple -meas-tran.sp
  * Simple .measure examples
  * transient simulation of two sine
  * signals with different frequencies
   vac1 1 0 DC 0 sin(0 1 1k 0 0)
   vac2 2 0 DC 0 sin(0 1.2 0.9k 0 0)
  .tran 10u 5m
  *
  .measure tran ... $ for the different inputs see below!
  *
  .control
   run
   plot v(1) v(2)
  .endc
  .end

```
After displaying the general syntax of the .measure statement, some examples are posted,
referring to the input file given above.

### 15.4.5 Trig Targ
```
.measure according to general form 1 measures the difference in dc voltage, frequency or time

```
between two points selected from one or two output vectors. The current examples all are using


-----

transient simulation. Measurements for tran analysis start after a delay time td. If you run
other examples with ac simulation or spectrum analysis, time may be replaced by frequency,
after a dc simulation the independent variable may become a voltage or current.

General form 1:
```
  .MEASURE {DC|AC|TRAN|SP} result TRIG trig_variable VAL=
    val
  + <TD=td> <CROSS=# | CROSS=LAST> <RISE=# | RISE=LAST>
  + <FALL=# | FALL=LAST> <TRIG AT=time> TARG
    targ_variable
  + VAL=val <TD=td> <CROSS=# | CROSS=LAST> <RISE=# |
  + RISE=LAST> <FALL=# | FALL=LAST> <TARG AT=time>

```
Measure statement example (for use in the input file given above):
```
.measure tran tdiff TRIG v(1) VAL=0.5 RISE=1 TARG v(1) VAL=0.5 RISE=2

```
measures the time difference between v(1) reaching 0.5 V for the first time on its first rising
slope (TRIG) versus reaching 0.5 V again on its second rising slope (TARG), i.e. it measures
the signal period.

Output:
```
tdiff = 1.000000e-003 targ= 1.083343e-003 trig= 8.334295e-005

```
Measure statement example:
```
.measure tran tdiff TRIG v(1) VAL=0.5 RISE=1 TARG v(1) VAL=0.5 RISE=3

```
measures the time difference between v(1) reaching 0.5 V for the first time on its rising slope
versus reaching 0.5 V on its rising slope for the third time (i.e. two periods).

Measure statement:
```
.measure tran tdiff TRIG v(1) VAL=0.5 RISE=1 TARG v(1) VAL=0.5 FALL=1

```
measures the time difference between v(1) reaching 0.5V for the first time on its rising slope
versus reaching 0.5 V on its first falling slope.

Measure statement:
```
.measure tran tdiff TRIG v(1) VAL=0 FALL=3 TARG v(2) VAL=0 FALL=3

```
measures the time difference between v(1) reaching 0V its third falling slope versus v(2) reaching 0 V on its third falling slope.

Measure statement:
```
.measure tran tdiff TRIG v(1) VAL=-0.6 CROSS=1 TARG v(2) VAL=-0.8 CROSS=1

```
measures the time difference between v(1) crossing -0.6 V for the first time (any slope) versus
v(2) crossing -0.8 V for the first time (any slope).

Measure statement:
```
.measure tran tdiff TRIG AT=1m TARG v(2) VAL=-0.8 CROSS=3

```
measures the time difference between the time point 1ms versus the time when v(2) crosses -0.8
V for the third time (any slope).


-----

### 15.4.6 Find ... When

The FIND and WHEN functions allow to measure any dependent or independent time, frequency,
or dc parameter, when two signals cross each other or a signal crosses a given value. Measurements start after a delay TD and may be restricted to a range between FROM and TO.

General form 2:
```
  .MEASURE {DC|AC|TRAN|SP} result WHEN out_variable=val
  + <TD=td> <FROM=val> <TO=val> <CROSS=# | CROSS=LAST>
  + <RISE=# | RISE=LAST> <FALL=# | FALL=LAST>

```
Measure statement:
```
.measure tran teval WHEN v(2)=0.7 CROSS=LAST

```
measures the time point when v(2) crosses 0.7 V for the last time (any slope).

General form 3:
```
  .MEASURE {DC|AC|TRAN|SP} result
  + WHEN out_variable=out_variable2
  + <TD=td> <FROM=val> <TO=val> <CROSS=# | CROSS=LAST>
  + <RISE=# | RISE=LAST> <FALL=# | FALL=LAST>

```
Measure statement:
```
.measure tran teval WHEN v(2)=v(1) RISE=LAST

```
measures the time point when v(2) and v(1) are equal, v(2) rising for the last time.

General form 4:
```
  .MEASURE {DC|AC|TRAN|SP} result FIND out_variable
  + WHEN out_variable2=val <TD=td> <FROM=val> <TO=val>
  + <CROSS=# | CROSS=LAST> <RISE=# | RISE=LAST>
  + <FALL=# | FALL=LAST>

```
Measure statement:
```
.measure tran yeval FIND v(2) WHEN v(1)=-0.4 FALL=LAST

```
returns the dependent (y) variable drawn from v(2) at the time point when v(1) equals a value
of -0.4, v(1) falling for the last time.

General form 5:
```
  .MEASURE {DC|AC|TRAN|SP} result FIND out_variable
  + WHEN out_variable2=out_variable3 <TD=td>
  + <CROSS=# | CROSS=LAST>
  + <RISE=#|RISE=LAST> <FALL=#|FALL=LAST>

```
Measure statement:
```
.measure tran yeval FIND v(2) WHEN v(1)=v(3) FALL=2

```

-----

returns the dependent (y) variable drawn from v(2) at the time point when v(1) crosses v(3),
v(1) falling for the second time.

General form 6:
```
  .MEASURE {DC|AC|TRAN|SP} result FIND out_variable AT=
    val

```
Measure statement:
```
.measure tran yeval FIND v(2) AT=2m

```
returns the dependent (y) variable drawn from v(2) at the time point 2 ms (given by AT=time).

### 15.4.7 AVG|MIN|MAX|PP|RMS|MIN_AT|MAX_AT

General form 7:
```
  .MEASURE {DC|AC|TRAN|SP} result
  + {AVG|MIN|MAX|PP|RMS|MIN_AT|MAX_AT}
  + out_variable <TD=td> <FROM=val> <TO=val>

```
Measure statements:
```
.measure tran ymax MAX v(2) from=2m to=3m

```
returns the maximum value of v(2) inside the time interval between 2 ms and 3 ms.
```
.measure tran tymax MAX_AT v(2) from=2m to=3m

```
returns the time point of the maximum value of v(2) inside the time interval between 2 ms and
3 ms.
```
.measure tran ypp PP v(1) from=2m to=4m

```
returns the peak to peak value of v(1) inside the time interval between 2 ms and 4 ms.
```
.measure tran yrms RMS v(1) from=2m to=4m

```
returns the root mean square value of v(1) inside the time interval between 2 ms and 4 ms.
```
.measure tran yavg AVG v(1) from=2m to=4m

```
returns the average value of v(1) inside the time interval between 2 ms and 4 ms.

### 15.4.8 Integ

General form 8:
```
  .MEASURE {DC|AC|TRAN|SP} result INTEG<RAL> out_variable
  + <TD=td> <FROM=val> <TO=val>

```
Measure statement:
```
.measure tran yint INTEG v(2) from=2m to=3m

```
returns the area under v(2) inside the time interval between 2 ms and 3 ms.


-----

### 15.4.9 param

General form 9:
```
  .MEASURE {DC|AC|TRAN|SP} result param=’expression ’

```
Measure statement:
```
.param fval=5
.measure tran yadd param=’fval + 7’

```
will evaluate the given expression fval + 7 and return the value 12.

_’Expression’ is evaluated according to the rules given in Chapt. 2.8.5 during start up of ngspice._
It may contain parameters defined with the .param statement. It may also contain parameters
resulting from preceding .meas statements.
```
.param vout_diff=50u
...
.measure tran tdiff TRIG AT=1m TARG v(2) VAL=-0.8 CROSS=3
.meas tran bw_chk param=’(tdiff < vout_diff) ? 1 : 0’

```
will evaluate the given ternary function and return the value 1 in bw_chk, if tdiff measured is
smaller than parameter vout_diff.

The expression may not contain vectors like v(10), e.g. anything resulting directly from a
simulation. This may be handled with the following .meas command option.

### 15.4.10 par(’expression’)

The par(’expression’) option (15.6.6) allows to use algebraic expressions on the .measure
lines. Every out_variable may be replaced by par(’expression’) using the general forms 1... 9
described above. Internally par(’expression’) is substituted by a vector according to the rules
of the B source (Chapt. 5.1). A typical example of the general form is shown below:

General form 10:
```
  .MEASURE {DC|TRAN|AC|SP} result
  + FIND par(’expression ’) AT=val

```
The measure statement
```
.measure tran vtest find par(’(v(2)*v(1))’) AT=2.3m

```
returns the product of the two voltages at time point 2.3 ms.

Note that a B-source, and therefore the par(’...’) feature, operates on values of type complex
in AC analysis mode.


-----

### 15.4.11 Deriv

General form:
```
  .MEASURE {DC|AC|TRAN|SP} result DERIV<ATIVE>
    out_variable
  + AT=val
  .MEASURE {DC|AC|TRAN|SP} result DERIV<ATIVE>
    out_variable
  + WHEN out_variable2=val <TD=td>
  + <CROSS=# | CROSS=LAST> <RISE=#|RISE=LAST>
  + <FALL=#|FALL=LAST>
  .MEASURE {DC|AC|TRAN|SP} result DERIV<ATIVE>
    out_variable
  + WHEN out_variable2=out_variable3
  + <TD=td> <CROSS=# | CROSS=LAST>
  + <RISE=#|RISE=LAST> <FALL=#|FALL=LAST>

### 15.4.12 More examples

```
Some other examples, also showing the use of parameters, are given below. Corresponding
demonstration input files are distributed with ngspice in folder /examples/measure.


-----

Other examples:
```
  .meas tran inv_delay2 trig v(in) val=’vp/2’ td=1n fall
    =1
  + targ v(out) val=’vp/2’ rise=1
  .meas tran test_data1 trig AT = 1n targ v(out)
  + val=’vp/2’ rise=3
  .meas tran out_slew trig v(out) val=’0.2*vp’ rise=2
  + targ v(out) val=’0.8*vp’ rise=2
  .meas tran delay_chk param=’(inv_delay < 100ps) ? 1 :
    0’
  .meas tran skew when v(out)=0.6
  .meas tran skew2 when v(out)=skew_meas
  .meas tran skew3 when v(out)=skew_meas fall=2
  .meas tran skew4 when v(out)=skew_meas fall=LAST
  .meas tran skew5 FIND v(out) AT=2n
  .meas tran v0_min min i(v0)
  + from=’dfall’ to=’dfall+period’
  .meas tran v0_avg avg i(v0)
  + from=’dfall’ to=’dfall+period’
  .meas tran v0_integ integ i(v0)
  + from=’dfall’ to=’dfall+period’
  .meas tran v0_rms rms i(v0)
  + from=’dfall’ to=’dfall+period’
  .meas dc is_at FIND i(vs) AT=1
  .meas dc is_max max i(vs) from=0 to=3.5
  .meas dc vds_at when i(vs)=0.01
  .meas ac vout_at FIND v(out) AT=1MEG
  .meas ac vout_atd FIND vdb(out) AT=1MEG
  .meas ac vout_max max v(out) from=1k to=10MEG
  .meas ac freq_at when v(out)=0.1
  .meas ac vout_diff trig v(out) val=0.1 rise=1 targ v(
    out)
  + val=0.1 fall=1
  .meas ac fixed_diff trig AT = 10k targ v(out)
  + val=0.1 rise=1
  .meas ac vout_avg avg v(out) from=10k to=1MEG
  .meas ac vout_integ integ v(out) from=20k to=500k
  .meas ac freq_at2 when v(out)=0.1 fall=LAST
  .meas ac bw_chk param=’(vout_diff < 100k) ? 1 : 0’
  .meas ac vout_rms rms v(out) from=10 to=1G

## 15.5 Safe Operating Area (SOA) warning messages

```
By setting .option warn=1 the Safe Operation Area check algorithm is enabled. In this case
for .op, .dc and .tran analysis warning messages are issued if the branch voltages of devices


-----

(Resistors, Capacitors, Diodes, BJTs and MOSFETs) exceed limits that are specified by model
parameters. All these parameters are positive with default value of infinity.

The check is executed after Newton-Raphson iteration is finished i.e. in transient analysis in
each time step. The user can specify an additional .option maxwarns (default: 5) to limit the
count of messages.

The output goes on default to stdout or alternatively to a file specified by command line option
```
--soa-log=filename.

### 15.5.1 Resistor and Capacitor SOA model parameters

```
1. Bv_max: if |Vr| or |Vc| exceed Bv_max, SOA warning is issued.

### 15.5.2 Diode SOA model parameter

1. Bv_max: if |Vj| exceeds Bv_max, SOA warning is issued.

2. Fv_max: if |Vf| exceeds Fv_max, SOA warning is issued.

### 15.5.3 BJT SOA model parameter

1. Vbe_max: if |Vbe| exceeds Vbe_max, SOA warning is issued.

2. Vbc_max: if |Vbc| exceeds Vbc_max, SOA warning is issued.

3. Vce_max: if |Vce| exceeds Vce_max, SOA warning is issued.

4. Vcs_max: if |Vcs| exceeds Vcs_max, SOA warning is issued.

### 15.5.4 MOS SOA model parameter

1. Vgs_max: if |Vgs| exceeds Vgs_max, SOA warning is issued.

2. Vgd_max: if |Vgd| exceeds Vgd_max, SOA warning is issued.

3. Vgb_max: if |Vgb| exceeds Vgb_max, SOA warning is issued.

4. Vds_max: if |Vds| exceeds Vds_max, SOA warning is issued.

5. Vbs_max: if |Vbs| exceeds Vbs_max, SOA warning is issued.

6. Vbd_max: if |Vbd| exceeds Vbd_max, SOA warning is issued.


-----

## 15.6 Batch Output

The following commands .print (15.6.2), .plot (15.6.3) and .four (15.6.4) are valid only
if ngspice is started in batch mode (see 16.4.1), whereas .save and the equivalent .probe are
aknowledged in all operating modes.

If you start ngspice in batch mode using the -b command line option, the outputs of .print,
```
.plot, and .four are printed to the console output. You may use the output redirection of your

```
shell to direct this printout into a file (not available with MS Windows GUI). As an alternative
you may extend the ngspice command by specifying an output file:
```
ngspice -b -o output.log input.cir

```
If you however add the command line option -r to create a rawfile, .print and .plot are
ignored. If you want to involve the graphics plot output of ngspice, use the control mode
(16.4.3) instead of the -b batch mode option.

### 15.6.1 .SAVE: Name vector(s) to be saved in raw file

General form:
```
  .save vector vector vector ...

```
Examples:
```
  .save i(vin) node1 v(node2)
  .save @m1[id] vsource#branch
  .save all @m2[vdsat]

```
The vectors listed on the .SAVE line are recorded in the rawfile for use later with ngspice or ngnutmeg (ngnutmeg is just the data-analysis half of ngspice, without the ability to simulate). The
standard vector names are accepted. Node voltages may be saved by giving the nodename or
```
v(nodename). Currents through an independent voltage source are given by i(sourcename)

```
or sourcename#branch. Internal device data are accepted as @dev[param].

If no .SAVE line is given, then the default set of vectors is saved (node voltages and voltage
source branch currents). If .SAVE lines are given, only those vectors specified are saved. For
more discussion on internal device data, e.g. @m1[id], see Appendix, Chapt. 31.1. If you want
to save internal data in addition to the default vector set, add the parameter all to the additional
vectors to be saved. If the command .save vm(out) is given, and you store the data in a rawfile, only the original data v(out) are stored. The request for storing the magnitude is ignored,
because this may be added later during rawfile data evaluation with ngnutmeg or ngspice. See
also the section on the interactive command interpreter (Chapt. 17.5) for information on how to
use the rawfile.


-----

### 15.6.2 .PRINT Lines

General form:
```
  .print prtype ov1 <ov2 ... ov8>

```
Examples:
```
  .print tran v(4) i(vin)
  .print dc v(2) i(vsrc) v(23, 17)
  .print ac vm(4, 2) vr(7) vp(8, 3)

```
The .print line defines the contents of a tabular listing of one to eight output variables. prtype
is the type of the analysis (DC, AC, TRAN, NOISE, or DISTO) for which the specified outputs are
desired. The form for voltage or current output variables is the same as given in the previous
section for the print command; Spice2 restricts the output variable to the following forms
(though this restriction is not enforced by ngspice):

`V(N1<,N2>)` specifies the voltage difference between nodes N1 and N2.
If N2 (and the preceding comma) is omitted, ground (0) is
assumed. See the print command in the previous section
for more details. For compatibility with SPICE2, the
following five additional values can be accessed for the ac
analysis by replacing the ‘V’ in V(N1,N2) with:

VR Real part

VI Imaginary part

VM Magnitude

VP Phase

VDB 20log10(magnitude)

`I(VXXXXXXX)` specifies the current flowing in the independent voltage
source named VXXXXXXX. Positive current flows from
the positive node, through the source, to the negative node.
(Not yet implemented: For the ac analysis, the
corresponding replacements for the letter I may be made
in the same way as described for voltage outputs.)

Output variables for the noise and distortion analyses have a different general form from that of
the other analyses. There is no limit on the number of .print lines for each type of analysis.
The par(’expression’) option (15.6.6) allows to use algebraic expressions in the .print lines.
**.width (15.6.7) selects the maximum number of characters per line.**

### 15.6.3 .PLOT Lines
```
.plot creates a printer plot output.

```
|VR|Real part|
|---|---|
|VI|Imaginary part|
|VM|Magnitude|
|VP|Phase|
|VDB|20log10(magnitude)|

|V(N1<,N2>)|specifies the voltage difference between nodes N1 and N2. If N2 (and the preceding comma) is omitted, ground (0) is assumed. See the print command in the previous section for more details. For compatibility with SPICE2, the following five additional values can be accessed for the ac analysis by replacing the ‘V’ in V(N1,N2) with: VR Real part VI Imaginary part VM Magnitude VP Phase VDB 20log10(magnitude)|
|---|---|
|I(VXXXXXXX)|specifies the current flowing in the independent voltage source named VXXXXXXX. Positive current flows from the positive node, through the source, to the negative node. (Not yet implemented: For the ac analysis, the corresponding replacements for the letter I may be made in the same way as described for voltage outputs.)|


-----

General form:
```
  .plot pltype ov1 <(plo1, phi1)> <ov2 <(plo2, phi2)> ... ov8>

```
Examples:
```
  .plot dc v(4) v(5) v(1)
  .plot tran v(17, 5) (2, 5) i(vin) v(17) (1, 9)
  .plot ac vm(5) vm(31, 24) vdb(5) vp(5)
  .plot disto hd2 hd3(R) sim2
  .plot tran v(5, 3) v(4) (0, 5) v(7) (0, 10)

```
The .plot line defines the contents of one plot of from one to eight output variables. pltype is
the type of analysis (DC, AC, TRAN, NOISE, or DISTO) for which the specified outputs are desired.
The syntax for the ovi is identical to that for the .print line and for the plot command in the
interactive mode.

The overlap of two or more traces on any plot is indicated by the letter ‘X’. When more than
one output variable appears on the same plot, the first variable specified is printed as well
as plotted. If a printout of all variables is desired, then a companion .print line should be
included. There is no limit on the number of .plot lines specified for each type of analysis.
The par(’expression’) option (15.6.6) allows to use algebraic expressions in the .plot lines.

### 15.6.4 .FOUR: Fourier Analysis of Transient Analysis Output

General form:
```
  .four freq ov1 <ov2 ov3 ...>

```
Examples:
```
  .four 100K v(5)

```
The .four (or Fourier) line controls whether ngspice performs a Fourier analysis as a part of
the transient analysis. freq is the fundamental frequency, and ov1 is the desired vector to
be analyzed. The Fourier analysis is performed over the interval <TSTOP-period, TSTOP>,
where TSTOP is the final time specified for the transient analysis, and period is one period of
the fundamental frequency. The dc component and the first nine harmonics are determined. For
maximum accuracy, TMAX (see the .tran line) should be set to period/100.0 (or less for very
high-Q circuits). The par(’expression’) option (15.6.6) allows to use algebraic expressions in
the .four lines.


-----

### 15.6.5 .PROBE: Name vector(s) to be saved in raw file

General form:
```
  .probe vector <vector vector ...>

```
Examples:
```
  .probe i(vin) input output
  .probe @m1[id]

```
Same as .SAVE (see Chapt. 15.6.1).

### 15.6.6 par(’expression’): Algebraic expressions for output

General form:
```
   par(’expression ’)
   output=par(’expression ’) $ not in .measure ac

```
Examples:
```
  .four 1001 sq1=par(’v(1)*v(1)’)
  .measure tran vtest find par(’(v(2)*v(1))’) AT=2.3m
  .print tran output=par(’v(1)/v(2)’) v(1) v(2)
  .plot dc v(1) diff=par(’(v(4)-v(2))/0.01’) out222

```
With the output lines .four, .plot, .print, .save and in .measure evaluation it is possible to add algebraic expressions for output, in addition to vectors. All of these output lines
accept par(’expression’), where expression is any expression valid for a B source (see Chapt.
5.1). Thus expression may contain predefined functions, numerical values, constants, simulator output like v(n1) or i(vdb), parameters predefined by a .param statement, and the variables
```
hertz, temper, and time. Note that a B-source, and therefore the par(’...’) feature, ope
```
rates on values of type complex in AC analysis mode.

Internally the expression is replaced by a generated voltage node that is the output of a B source,
one node, and the B source implementing par(’...’). Several par(’...’) are allowed in each line,
up to 99 per input file. The internal nodes are named pa_00 to pa_99. An error will occur if
the input file contains any of these reserved node names.

In .four, .plot, .print, .save, but not in .measure, an alternative syntax
output=par(’expression’) is possible. par(’expression’) may be used as described above.
output is the name of the new node to replace the expression. So output has to be unique and
a valid node name.

The syntax of output=par(expression) is strict, no spaces between par and (’, or between (
and ’ are allowed, (’ and ’) both are required. Also there is not much error checking on your
input, if there is a typo, for example, an error may pop up at an unexpected place.


-----

### 15.6.7 .width

Set the width of a print-out or plot with the following card:
```
.with out = 256

```
Parameter out yields the maximum number of characters plotted in a row, if printing in columns
or an ASCII-plot is selected.

## 15.7 Measuring current through device terminals

### 15.7.1 Adding a voltage source in series

Originally the ngspice matrix solver delivers node voltages and currents through independent
voltage sources. So to measure the currents through a resistor you may add a voltage source in
series with dc voltage 0.

Current measurement with series voltage source
```
  *measure current through R1
  V1 1 0 1
  R1 1 0 5
  R2 1 0 10
  * will become
  V1 1 0 1
  R1 1 11 5
   Vmess 11 0 dc 0
  R2 1 0 10

### 15.7.2 Using option ’savecurrents’

```
Current measurement with series voltage source
```
  *measure current through R1 and R2
  V1 1 0 1
  R1 1 0 5
  R2 1 0 10
  .options savecurrents

```
The option savecurrents will add .save lines (15.6.1) like
```
.save @r1[i]
.save @r2[i]

```
to your input file information read during circuit parsing. These newly created vectors contain
the terminal currents of the devices R1 and R2.

You will find information of the nomenclature in Chapt. 31, also how to plot these vectors. The
following devices are supported: M, J, Q, D, R, C, L, B, F, G, W, S, I (see 2.1.2). For M only


-----

MOSFET models MOS1 to MOS9 are included so far. Devices in subcircuits are supported as
well. Be careful when choosing this option in larger circuits, because 1 to 4 additional output
vectors are created per device and this may consume lots of memory.


-----

