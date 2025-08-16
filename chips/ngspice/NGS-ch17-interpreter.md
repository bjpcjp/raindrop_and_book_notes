# Chapter 17

 Interactive Interpreter

## 17.1 Introduction

The simulation flow in ngspice (input, simulation, output) may be controlled by dot commands
(see Chapt. 15 and 16.4.1) in batch mode. There is, however, a much more powerful control
scheme available in ngspice, traditionally coined ‘Interactive Interpreter’, but being much more
than just that. In fact there are several ways to use this feature, truly interactively by typing
commands to the input, but also running command sequences as scripts or as part of your input
deck in a quasi batch mode.

You may type in expressions, functions (17.2) or commands (17.5) into the input console to
elaborate on data already achieved from the interactive simulation session.

Sequences of commands, functions and control structures (17.6) may be assembled as a script
(17.8) into a file, and then activated by just typing the file name into the console input of an
interactive ngspice session.

Finally, and most useful, is it to add a script to the input file, in addition the the netlist and dot
commands. This is achieved by enclosing the script into .control ... `.endc (see 16.4.3,`
and 17.8.7 for an example). This feature enables a wealth of control options. You may set
internal (17.7) and other variables, start a simulation, evaluate the simulation output, start a new
simulation based on these data, and finally make use of many options for outputting the data
(graphically or into output files).

Historical note: The final releases of Berkeley Spice introduced a command shell and scripting
possibilities. The former releases were not interactive. The choice for the scripting language
was an early version of ‘csh’, the C-shell, which was en vogue back then as an improvement
over the ubiquitous Bourne Shell. Berkeley Spice incorporated a modified csh source code that,
instead of invoking the unix ‘exec’ system call, executed internal SPICE C subroutines. Apart
from bug fixes, this is still how ngspice works.

The csh-like scripting language is active in .control sections. It works on ‘strings’, and does
string substitution of ‘environment’ variables. You see the csh at work in ngspice with set foo
```
= "bar"; set baz = "bar$foo", and in if, repeat, for, ... constructs. However, ngspice

```
processes mainly numerical data, and support for this was not available in the c-sh implementation. Therefore, Berkeley implemented an additional type of variables, with different syntax, to
access double and complex double vectors (possibly of length 1). This new variable type is modified with let, and can be used without special syntax in places where a numerical expression


-----

is expected: let bar = 4 * 5; let zoo = bar * 4 works. Unfortunately, occasionally
one has to cross the boundary between the numeric and the string domain. For this purpose the
```
$& construct is available – it queries a variable in the numerical let domain, and expands it to

```
a c-sh string denoting the value. This lets you do do something like set another = "this
```
is $&bar". It is important to remember that set can only operate on (c-sh) strings, and that
let operates only on numeric data. Convert from numeric to string with $&, and from string to

```
numeric with $.

## 17.2 Expressions, Functions, and Constants

Ngspice and ngnutmeg store data in the form of vectors: time, voltage, etc. Each vector has a
type, and vectors can be operated on and combined algebraically in ways consistent with their
types. Vectors are normally created as the output of a simulation, or when a data file (output raw
file) is read in again (ngspice, ngnutmeg, see the load command 17.5.38), or when the initial
data-file is loaded directly into ngnutmeg. They can also be created with the let command
817.5.35).

An expression is an algebraic formula involving vectors and scalars (a scalar is a vector of
length 1) and the following operations:
```
  + - * / ^ %,

```
% is the modulo operator, and the comma operator has two meanings: if it is present in the
argument list of a user definable function, it serves to separate the arguments. Otherwise, the
term x, y is synonymous with x + j(y). Also available are the logical operations & (and),
| (or), ! (not), and the relational operations <, >, >=, <=, =, and <> (not equal). If used in an
algebraic expression they work like they would in C, producing values of 0 or 1. The relational
operators have the following synonyms:

Operator Synonym

gt   
lt <

ge >=

le <=

ne <>

and &

or |

not !

eq =

The operators are useful when < and > might be confused with the internal IO redirection (see
17.4, which is almost always happening). It is however safe to use < and > with the define
command (17.5.14).

The following functions are available:

|Operator|Synonym|
|---|---|
|gt|>|
|lt|<|
|ge|>=|
|le|<=|
|ne|<>|
|and|&|
|or|||
|not|!|
|eq|=|


-----

|Name|Function|
|---|---|
|mag(vector)|Magnitude of vector (same as abs(vector)).|
|ph(vector)|Phase of vector.|
|cph(vector)|Phase of vector. Continuous values, no discontinuity at ±π.|
|unwrap(vector)|Phase of vector. Continuous values, no discontinuity at ±π. Real phase vector in degrees as input.|
|j(vector)|i(sqrt(-1)) times vector.|
|real(vector|The real component of vector.|
|imag(vector)|The imaginary part of vector.|
|db(vector)|20 log10(mag(vector)).|
|log10(vector)|The logarithm (base 10) of vector.|
|ln(vector)|The natural logarithm (base e) of vector.|
|exp(vector)|e to the vector power.|
|abs(vector)|The absolute value of vector (same as mag).|
|sqrt(vector)|The square root of vector.|
|sin(vector)|The sine of vector.|
|cos(vector)|The cosine of vector.|
|tan(vector)|The tangent of vector.|
|atan(vector)|The inverse tangent of vector.|
|sinh(vector)|The hyperbolic sine of vector.|
|cosh(vector)|The hyperbolic cosine of vector.|
|tanh(vector)|The hyperbolic tangent of vector.|
|floor(vector)|Largest integer that is less than or equal to vector.|
|ceil(vector)|Smallest integer that is greater than or equal to vector.|
|norm(vector)|The vector normalized to 1 (i.e, the largest magnitude of any component is 1).|
|mean(vector)|The result is a scalar (a length 1 vector) that is the mean of the elements of vector (elements values added, divided by number of elements).|
|avg(vector)|The average of a vector. Returns a vector where each element is the mean of the preceding elements of the input vector (including the actual element).|
|stddev(vector)|The result is a scalar (a length 1 vector) that is the standard deviation of the elements of vector .|
|group_delay(vector)|Calculates the group delay -dphase[rad]/dω[rad/s]. Input is the complex vector of a system transfer function versus frequency, resembling damping and phase per frequency value. Output is a vector of group delay values (real values of delay times) versus frequency.|
|vector(number)|The result is a vector of length number, with elements 0, 1, ... number - 1. If number is a vector then just the first element is taken, and if it isn’t an integer then the floor of the magnitude is used.|
|unitvec(number)|The result is a vector of length number, all elements having a value 1.|


-----

|Name|Function|
|---|---|
|length(vector)|The length of vector.|
|interpolate(plot.vector)|The result of interpolating the named vector onto the scale of the current plot. This function uses the variable polydegree to determine the degree of interpolation.|
|deriv(vector)|Calculates the derivative of the given vector. This uses numeric differentiation by interpolating a polynomial and may not produce satisfactory results (particularly with iterated differentiation). The implementation only calculates the derivative with respect to the real component of that vector’s scale.|
|vecd(vector)|Compute the differential of a vector.|
|vecmin(vector)|Returns the value of the vector element with minimum value. Same as minimum.|
|minimum(vector)|Returns the value of the vector element with minimum value. Same as vecmin.|
|vecmax(vector)|Returns the value of the vector element with maximum value. Same as maximum.|
|maximum(vector)|Returns the value of the vector element with maximum value. Same as vecmax.|
|fft(vector)|fast fourier transform (17.5.26)|
|ifft(vector)|inverse fast fourier transform (17.5.26)|
|sortorder(vector)|Returns a vector with the positions of the elements in a real vector after they have been sorted into increasing order using a stable method (qsort).|
|timer(vector)|Returns CPU-time minus the value of the first vector element.|
|clock(vector)|Returns wall-time minus the value of the first vector element.|


Several functions offering statistical procedures are listed in the following table:


-----

|Name|Function|
|---|---|
|rnd(vector)|A vector with each component a random integer between 0 and the absolute value of the input vector’s corresponding integer element value.|
|sgauss(vector)|Returns a vector of random numbers drawn from a Gaussian distribution (real value, mean = 0, standard deviation = 1). The length of the vector returned is determined by the input vector. The contents of the input vector will not be used. A call to sgauss(0) will return a single value of a random number as a vector of length 1..|
|sunif(vector)|Returns a vector of random real numbers uniformly distributed in the interval [-1 .. 1[. The length of the vector returned is determined by the input vector. The contents of the input vector will not be used. A call to sunif(0) will return a single value of a random number as a vector of length 1.|
|poisson(vector)|Returns a vector with its elements being integers drawn from a Poisson distribution. The elements of the input vector (real numbers) are the expected numbers λ. Complex vectors are allowed, real and imaginary values are treated separately.|
|exponential(vector)|Returns a vector with its elements (real numbers) drawn from an exponential distribution. The elements of the input vector are the respective mean values (real numbers). Complex vectors are allowed, real and imaginary values are treated separately.|


An input vector may be either the name of a vector already defined or a floating-point number
(a scalar). A scalar will result in an output vector of length 1. A number may be written in
any format acceptable to ngspice, such as 14.6Meg or -1.231e-4. Note that you can either use
scientific notation or one of the abbreviations like MEG or G, but not both. As with ngspice, a
number may have trailing alphabetic characters.

The notation expr [num] denotes the num’th element of expr. For multi-dimensional vectors,
a vector of one less dimension is returned. Also for multi-dimensional vectors, the notation
expr[m][n] will return the nth element of the mth subvector. To get a subrange of a vector, use
the form expr[lower, upper]. To reference vectors in a plot that is not the current plot (see the
setplot command, below), the notation plotname.vecname can be used. Either a plotname or
a vector name may be the wildcard all. If the plotname is all, matching vectors from all plots
are specified, and if the vector name is all, all vectors in the specified plots are referenced. Note
that you may not use binary operations on expressions involving wildcards - it is not obvious
what all + all should denote, for instance. Thus some (contrived) examples of expressions are:


-----

Expressions examples:
```
   cos(TIME) + db(v(3))
   sin(cos(log([1 2 3 4 5 6 7 8 9 10])))
   TIME * rnd(v(9)) - 15 * cos(vin#branch) ^ [7.9e5 8]
   not ((ac3.FREQ[32] & tran1.TIME[10]) gt 3)
  (sunif(0) ge 0) ? 1.0 : 2.0
   mag(fft(v(18)))

```
Vector names in ngspice may look like @dname[param], where dname is either the name of
a device instance or of a device model. The vector contains the value of the parameter of the
device or model. See Appendix, Chapt. 31 for details of which parameters are available. The
returned value is a vector of length 1. Please note that finding the value of device and device
model parameters can also be done with the show command (e.g. show v1 : `dc).`

There are a number of pre-defined constants in ngspice, which you may use by their name. They
are stored in plot (17.3) const and are listed in the table below:

Name Description Value

pi _π_ 3.14159...

e _e (the base of natural logarithms)_ 2.71828...

c _c (the speed of light)_ 299,792,500 _[m]/sec_

i i (the square root of -1) 1
_√−_

kelvin (absolute zero in centigrade) -273.15[◦]C

echarge q (the charge of an electron) 1.60219e-19 C

boltz k (Boltzmann’s constant) 1.38062e-23[J]/K

planck h (Planck’s constant) 6.62620e-34

yes boolean 1

no boolean 0

TRUE boolean 1

FALSE boolean 0

These constants are all given in MKS units. If you define another variable with a name that
conflicts with one of these then it takes precedence.

Additional constants may be generated during circuit setup (see .csparam, 2.10).

## 17.3 Plots

The output vectors of any analysis are stored in plots, a traditional SPICE notion. A plot is a
group of vectors. A first tran command will generate several vectors within a plot tran1. A
subsequent tran command will store their vectors in tran2. Then a linearize command will
linearize all vectors from tran2 and store them in tran3, which then becomes the current plot. A
```
fft will generate a plot spec1, again now the current plot. The display command always will

```
show all vectors in the current plot. Echo $plots followed by Return lists all plots generated
so far. `Setplot followed by Return will show all plots and ask for a (new) plot to become`
current. A simple Return will end the command. Setplot name will change the current plot
to ’name’ (e.g. setplot tran2 will make tran2 the current plot). A sequence name.vector
may be used to access the vector from a foreign plot.

|Name|Description|Value|
|---|---|---|
|pi|π|3.14159...|
|e|e (the base of natural logarithms)|2.71828...|
|c|c (the speed of light)|299,792,500 m/sec|
|i|i (the square root of -1)|√ 1 −|
|kelvin|(absolute zero in centigrade)|-273.15◦C|
|echarge|q (the charge of an electron)|1.60219e-19 C|
|boltz|k (Boltzmann’s constant)|1.38062e-23J/K|
|planck|h (Planck’s constant)|6.62620e-34|
|yes|boolean|1|
|no|boolean|0|
|TRUE|boolean|1|
|FALSE|boolean|0|


-----

You may generate plots by yourself: setplot new will generate a new plot named unknown1,
```
set curplottitle=”a new plot” will set a title, set curplotname=myplot will set its

```
name as a short description, set curplotdate=”Sat Aug 28 10:49:42 2010” will set its
date. Note that strings with spaces have to be given with double quotes.

Of course the notion ’plot’ will be used by this manual also in its more common meaning,
denoting a graphics plot or being a plot command. Be careful to get the correct meaning.

## 17.4 Command Interpretation

### 17.4.1 On the console

On the ngspice console window (or into the Windows GUI) you may directly type in any command from 17.5. Within a command sequence Input/output redirection is available (see Chapt.
17.8.8 for an example) - the symbols >, >>, >&, >>&, and < have the same effects as in the
C-shell. This I/O-redirection is internal to ngspice commands, and should not be mixed up with
the ‘external’ I/O-redirection offered by the usual shells (Linux, MSYS etc.), see 17.5.65. You
may type multiple commands on one line, separated by semicolons.

### 17.4.2 Scripts

If a word is typed as a command, and there is no built-in command with that name, the directories in the sourcepath list are searched in order for a file with the name given by the word. If
it is found, it is read in as a command file (as if it were sourced). Before it is read, however, the
variables argc and argv are set to the number of words following the file-name on the command line, and a list of those words respectively. After the file is finished, these variables are
unset. Note that if a command file calls another, it must save its argv and argc since they are
altered. Also, command files may not be re-entrant since there are no local variables. Of course,
the procedures may explicitly manipulate a stack.... This way one can write scripts analogous
to shell scripts for ngnutmeg and ngspice.

Note that for the script to work with ngspice, it must begin with a blank line (or whatever else,
since it is thrown away) and then a line with .control on it. This is an unfortunate result
of the source command being used for both circuit input and command file execution. Note
also that this allows the user to merely type the name of a circuit file as a command and it is
automatically run. The commands are executed immediately, without running any analyses that
may be specified in the circuit (to execute the analyses before the script executes, include a run
command in the script).

There are various command scripts installed in /usr/local/lib/spice/scripts (or whatever the path is on your machine), and the default sourcepath includes this directory, so you
can use these command files (almost) like built-in commands.

### 17.4.3 Add-on to circuit file

The probably most common way to invoke the commands described in the following Chapt.
17.5 is to add a .control ... .endc section to the circuit input file (see 16.4.3).


-----

Example:
```
  .control
   pre_set strict_errorhandling
   unset ngdebug
  *save outputs and specials
   save x1.x1.x1.7 V(9) V(10) V(11) V(12) V(13)
   run
   display
  * plot the inputs, use offset to plot on top of each other
   plot v(1) v(2)+4 v(3)+8 v(4)+12 v(5)+16 v(6)+20 v(7)+24 v(8)+28
  * plot the outputs, use offset to plot on top of each other
   plot v(9) v(10)+4 v(11)+8 v(12)+12 v(13)+16
  .endc

## 17.5 Commands

```
Commands marked with a * are only available in ngspice, not in ngnutmeg.

### 17.5.1 Ac*: Perform an AC, small-signal frequency response analysis

General Form:
```
  ac ( DEC | OCT | LIN ) N Fstart Fstop

```
Do an small signal ac analysis (see also Chapt. 15.3.1) over the specified frequency range.
```
DEC decade variation, and N is the number of points per decade.
OCT stands for octave variation, and N is the number of points per octave.
LIN stands for linear variation, and N is the number of points.
fstart is the starting frequency, and fstop is the final frequency.

```
Note that in order for this analysis to be meaningful, at least one independent source must have
been specified with an ac value.

In this ac analysis all non-linear devices are linearized around their actual dc operating point.
All Ls and Cs get their imaginary value, depending on the actual frequency step. Each output
vector will be calculated relative to the input voltage (current) given by the ac value (Iin equals
to 1 in the example below). The resulting node voltages (and branch currents) are complex
vectors. Therefore you have to be careful using the plot command.


-----

Example:
```
  * AC test
   Iin 1 0 AC 1
  R1 1 2 100
  L1 2 0 1
  .control
  AC LIN 101 10 10K
   plot v(2) $ real part !
   plot mag(v(2)) $ magnitude
   plot db(v(2)) $ same as vdb(2)
   plot imag(v(2)) $ imaginary part of v(2)
   plot real(v(2)) $ same as plot v(2)
   plot phase(v(2)) $ phase in rad
   plot cph(v(2)) $ phase in rad, continuous beyond pi
   plot 180/PI*phase(v(2)) $ phase in deg
  .endc
  .end

```
In addition to the plot examples given above you may use the variants of vxx(node) described in
Chapt. 15.6.2 like vdb(2). An option to suppress OP analysis before AC may be set for linear
circuits (15.1.3).

### 17.5.2 Alias: Create an alias for a command

General Form:
```
   alias [word] [text ...]

```
Causes word to be aliased to text. History substitutions may be used, as in C-shell aliases.

### 17.5.3 Alter*: Change a device or model parameter

Alter changes the value for a device or a specified parameter of a device or model.

General Form:
```
   alter dev = <expression >
   alter dev param = <expression >
   alter @dev[param] = <expression >

```
<expression> must be real (complex isn’t handled right now, integer is fine though, but no
strings. For booleans, use 0/1).


-----

Old style (pre 3f4):
```
   alter device value
   alter device parameter value [ parameter value ]

```
Using the old style, its first form is used by simple devices that have one principal value (resistors, capacitors, etc.) where the second form is for more complex devices (bjt’s, etc.). Model
parameters can be changed with the second form if the name contains a ‘#’. For specifying a
list of parameters as values, start it with ‘[’, followed by the values in the list, and end with ‘]’.
Be sure to place a space between each of the values and before and after the ‘[’ and ‘]’.

Some examples are given below:

Examples (Spice3f4 style):
```
   alter vd = 0.1
   alter vg dc = 0.6
   alter @m1[w]= 15e-06
   alter @vg[sin] [ -1 1.5 2MEG ]
   alter @Vi[pwl] = [ 0 1.2 100p 0 ]

```
**alter may have vectors (17.8.2) or variables (17.8.1) as parameters.**

Examples (vector or variable in parameter list):
```
   let newfreq = 10k
   alter @vg[sin] [ -1 1.5 $&newfreq ] $ vector
   set newperiod = 150u
   alter @Vi[pwl] = [ 0 1.2 $newperiod 0 ] $ variable

```
You may change a parameter of a device residing in a subcircuit, e.g. of MOS transistor msub1
in subcircuit xm1 (see also Chapt. 31.1).

Examples (parameter of device in subcircuit):
```
   alter m.xm1.msub1 w = 20u
   alter @m.xm1.msub1[w] = 20u

### 17.5.4 Altermod*: Change model parameter(s)

```
General form:
```
   altermod mod param = <expression >
   altermod @mod[param] = <expression >

```
Example:
```
   altermod nc1 tox = 10e-9
   altermod @nc1[tox] = 10e-9

```

-----

**Altermod operates on models and is used to change model parameters. The above example**
will change the parameter tox in all devices using the model nc1, which is defined as
```
  *** BSIM3v3 model
  .MODEL nc1 nmos LEVEL=8 version = 3.2.2
  + acm = 2 mobmod = 1 capmod = 1 noimod = 1
  + rs = 2.84E+03 rd = 2.84E+03 rsh = 45
  + tox = 20E-9 xj = 0.25E-6 nch = 1.7E+17
  + ...

```
If you invoke the model by the MOS device
```
M1 d g s b nc1 w=10u l=1u

```
you might also insert the device name M1 for mod as in
```
altermod M1 tox = 10e-9

```
The model parameter tox will be modified, however not only for device M1, but for all devices
using the associated MOS model nc1!

If you want to run corner simulations within a single simulation flow, the following option of
altermod may be of help. The parameter set with name modn may be overrun by the altermod
command specifying a model file. All parameter values fitting to the existing model modn will
be modified. As usual the ’reset’ command (see 17.5.52) restores the original values. The model
file (see 2.3) has to use the standard specifications for an input file, the .model section is the
relevant part. However the first line in the model file will be ignored by the input parser, so it
should contain only some title information. The .model statement should appear then in the
second or any later line. More than one .model section may reside in the file.

General form:
```
   altermod mod1 [mod2 .. mod15] file = <model file name>
   altermod mod1 [mod2 .. mod15] file <model file name>

```
Example:
```
   altermod nch file = BSIM3_nmos.mod
   altermod pch nch file BSIM4_mos.mod

```
Be careful that the new model file corresponds to the existing model selected by modn. The existing models are defined during circuit setup at start up of ngspice. Models have been included
by .model statements (2.3) in your input file or included by the .include command. In the
example given above, the models nch (or nch and pch) have to be already available before calling altermod. If they are not found in the active circuit, ngspice will terminate with an error
message. There is no checking however of the version and level parameters! So you have to
be responsible for offering model data of the same model level (e.g. level 8 for BSIM3). Thus
no new model is selectable by altermod, but the parameters of the existing model(s) may be
changed (partially, completely, temporarily).


-----

### 17.5.5 Asciiplot: Plot values using old-style character plots

General Form:
```
   asciiplot plotargs

```
Produce a line printer plot of the vectors. The plot is sent to the standard output, or you can
put it into a file with asciiplot args ... > file. The set options width, height, and nobreak
determine the width and height of the plot, and whether there are page breaks, respectively.
The ’more’ mode is the standard mode if printing to the screen, that is after a number of lines
given by height, and after a page break printing stops with request for answering the prompt
by <return>, ’c’ or ’q’. If everything shall be printed without stopping, put the command set
```
nomoremode into .spiceinit 16.6 (or spinit 16.5). Note that you will have problems if you try

```
to asciiplot something with an X-scale that isn’t monotonic (i.e, something like sin(TIME)
), because asciiplot uses a simple-minded linear interpolation. The asciiplot command
doesn’t deal with log scales or the delta keywords.

### 17.5.6 Aspice*: Asynchronous ngspice run

General Form:
```
   aspice input-file [output-file]

```
Start an ngspice run, and when it is finished load the resulting data. The raw data is kept in
a temporary file. If output-file is specified then the diagnostic output is directed into that file,
otherwise it is thrown away.

### 17.5.7 Bug: Mail a bug report

General Form:
```
   bug

```
Send a bug report. Please include a short summary of the problem, the version number and
name of the operating system that you are running, the version of ngspice that you are running,
and the relevant ngspice input file. (If you have defined BUGADDR, the mail is delivered to there.)

### 17.5.8 Cd: Change directory

General Form:
```
  cd [directory]

```
Change the current working directory to directory, or to the user’s home directory if none is
given.


-----

### 17.5.9 Cdump: Dump the control flow to the screen

General Form:
```
   cdump

```
Dumps the control sequence to the screen (all statements inside the .control ... .endc structure before the line with cdump). Indentations show the structure of the sequence. The example
below is printed if you add cdump to /examples/Monte_Carlo/MonteCarlo.sp.

Example (abbreviated):
```
   let mc_runs=5
   let run=0
   ...
   define agauss(nom, avar, sig) (nom + avar/sig * sgauss(0))
   define limit(nom, avar) (nom + ((sgauss(0) >=0) ? avar : -avar))
   dowhile run < mc_runs
    alter c1=unif(1e-09, 0.1)
   ...
    ac oct 100 250k 10meg
    meas ac bw trig vdb(out) val=-10 rise=1 targ vdb(out)
  + val=-10 fall=1
    set run="$&run"
   ...
    let run=run + 1
   end
   plot db({$scratch}.allv)
   echo
   print {$scratch}.bwh
   cdump

### 17.5.10 Circbyline*: Enter a circuit line by line

```
General Form:
```
   circbyline line

```
Enter a circuit line by line. line is any circuit line, as found in the *.cir ngspice input files. The
first line is a title line. The entry will be finished by entering .end. Circuit parsing is then
started automatically.


-----

Example:
```
   circbyline test circuit
   circbyline v1 1 0 1
   circbyline r1 1 0 1
   circbyline .dc v1 0.5 1.5 0.1
   circbyline .end
   run
   plot i(v1)

### 17.5.11 Codemodel*: Load an XSPICE code model library

```
General Form:
```
   codemodel [library file]

```
Load a XSPICE code model shared library file (e.g. analog.cm ...). Only available if ngspice
is compiled with the XSPICE option (--enable-xspice) or with the Windows executable
distributed since ngspice21. This command has to be called from spinit (see Chapt. 16.5) (or
.spiceinit for personal code models, 16.6).

### 17.5.12 Compose: Compose a vector

General Form:
```
   compose name values value1 [ value2 ... ]
   compose name param = val [ param = val ... ]

```
The first form takes the values and creates a new vector, where the values may be arbitrary
expressions.

The second form has the following possible parameters:

|start|The value of name[0]|
|---|---|
|stop|The last value of name|
|step|The difference between successive elements of the created vector|
|lin|How many linearly spaced elements the new vector should have|
|log|The number of points, logarithmically spaced (not working)|
|dec|The number of points per decade, logarithmically spaced (not working)|
|center|Where to center the range of points (not working)|
|span|The size of the range of points (not working)|
|gauss|The nominal value for the used Gaussian distribution|
|sd|The standard deviation for the used Gaussian distribution|
|sigma|The sigma for the used Gaussian distribution|
|random|The nominal value for a uniform random distribution|
|rvar|The percentage variation for the uniform random distribution|


-----

### 17.5.13 Dc*: Perform a DC-sweep analysis

General Form:
```
  dc Source Vstart Vstop Vincr [ Source2 Vstart2 Vstop2 Vincr2 ]

```
Do a dc transfer curve analysis. See the previous Chapt. 15.3.2 for more details. Several options
may be set (15.1.2).

### 17.5.14 Define: Define a function

General Form:
```
   define function(arg1, arg2, ...) expression

```
Define the function with the name function and arguments arg1, arg2, ... to be expression,
which may involve the arguments. When the function is later used, the arguments it is given
are substituted for the formal arguments when it was parsed. If expression is not present, any
existing definition for function is printed, and if there are no arguments then all expressions for
all currently active definitions are printed. Note that you may have different functions defined
with the same name but different arities. Some useful definitions are:

Example:
```
   define max(x,y) (x > y) * x + (x <= y) * y
   define min(x,y) (x < y) * x + (x >= y) * y
   define limit(nom, avar) (nom + ((sgauss(0) >= 0) ? avar : -avar))

### 17.5.15 Deftype: Define a new type for a vector or plot

```
General Form:
```
   deftype [v | p] typename abbrev

```
defines types for vectors and plots. abbrev will be used to parse things like abbrev(name) and
to label axes with M<abbrev>, instead of numbers. It may be omitted. Also, the command
‘deftype p plottype pattern ...’ will assign plottype as the name to any plot with one of the
patterns in its Name: field.

Example:
```
   deftype v capacitance F
   settype capacitance moscap
   plot moscap vs v(cc)

```

-----

### 17.5.16 Delete*: Remove a trace or breakpoint

General Form:
```
   delete [ debug-number ... ]

```
Delete the specified saved nodes and parameters, breakpoints and traces. The debug numbers
are those shown by the status command (unless you do status > file, in which case the debug
numbers are not printed).

### 17.5.17 Destroy: Delete an output data set

General Form:
```
   destroy [plotnames | all]

```
Release the memory holding the output data (the given plot or all plots) for the specified runs.

### 17.5.18 Devhelp: information on available devices

General Form:
```
   devhelp [[-csv] device_name [parameter]]

```
Devhelp command shows the user information about the devices available in the simulator. If
called without arguments, it simply displays the list of available devices in the simulator. The
name of the device is the name used inside the simulator to access that device. If the user specifies a device name, then all the parameters of that device (model and instance parameters)
will be printed. Parameter description includes the internal ID of the parameter (id#), the name
used in the model card or on the instance line (Name), the direction (Dir) and the description
of the parameter (Description). All the fields are self-explanatory, except the ‘direction’. Direction can be in, out or inout and corresponds to a ‘write-only’, ‘read-only’ or a ‘read/write’
parameter. Read-only parameters can be read but not set, write only can be set but not read and
_read/write can be both set and read by the user._

The -csv option prints the fields separated by a comma, for direct import into a spreadsheet.
This option is used to generate the simulator documentation.

Example:
```
   devhelp
   devhelp resistor
   devhelp capacitor ic

```

-----

### 17.5.19 Diff: Compare vectors

General Form:
```
   diff plot1 plot2 [vec ...]

```
Compare all the vectors in the specified plots, or only the named vectors if any are given. If
there are different vectors in the two plots, or any values in the vectors differ significantly,
the difference is reported. The variables diff_abstol, diff_reltol, and diff_vntol are used to
determine a significant difference.

### 17.5.20 Display: List known vectors and types

General Form:
```
   display [varname ...]

```
Prints a summary of currently defined vectors, or of the names specified. The vectors are sorted
by name unless the variable nosort is set. The information given is the name of the vector, the
length, the type of the vector, and whether it is real or complex data. Additionally, one vector
is labeled [scale]. When a command such as plot is given without a vs argument, this scale is
used for the X-axis. It is always the first vector in a rawfile, or the first vector defined in a new
plot. If you undefine the scale (i.e, let TIME = []), one of the remaining vectors becomes the
new scale (which one is unpredictable). You may set the scale to another vector of the plot with
the command setscale (17.5.63).

### 17.5.21 Echo: Print text

General Form:
```
   echo [text...] [$variable] ["$&vector"]

```
Echos the given text, variable or vector to the screen. echo without parameters issues a blank
line.

### 17.5.22 Edit*: Edit the current circuit

General Form:
```
   edit [ file-name ]

```
Print the current ngspice input file into a file, call up the editor on that file and allow the user to
modify it, and then read it back in, replacing the original file. If a file-name is given, then edit
that file and load it, making the circuit the current one. The editor may be defined in .spiceinit
or spinit by a command line like
```
set editor=emacs

```

-----

Using MS Windows, to allow the edit command calling an editor, you will have to add the
[editor’s path to the PATH variable of the command prompt windows (see here). edit then calls](http://en.wikipedia.org/wiki/Environment_variable#Examples_of_DOS_environment_variables)
cmd.exe with e.g. notepad++ and file-name as parameter, if you have set
```
set editor=notepad++.exe

```
in .spiceinit or spinit.

### 17.5.23 Edisplay: Print a list of all the event nodes

General Form:
```
   edisplay

```
Print the names of all event driven nodes generated or used by XSPICE ’A’ devices. See
```
eprint, eprvcd, and 27.2.2 for an example.

### 17.5.24 Eprint: Print an event driven node

```
General Form:
```
   eprint node [node]
   eprint node [node] > nodeout.txt $ output redirected

```
Print an event driven node generated or used by an XSPICE ’A’ device. These nodes are vectors
not organized in plots. See edisplay, eprvcd, and Chapt. 27.2.2 for an example. Output
redirection into a file is available.

### 17.5.25 Eprvcd: Dump event nodes in VCD format

General Form:
```
   eprvcd node1 node2 .. noden [ > filename ]

```
Dump the data of the specified event driven nodes to a .vcd file. Such files may be viewed
[with an vcd viewer, for example gtkwave. See edisplay, eprint, eprvcd, and 27.2.2 for an](http://gtkwave.sourceforge.net/)
example.

### 17.5.26 FFT: fast Fourier transform of vectors

General Form:
```
   fft vector1 [vector2] ...

```
This analysis provides a fast Fourier transform of the input vector(s) in forward direction. fft
is much faster than spec (17.5.72) (about a factor of 50 to 100 for larger vectors).


-----

The fft command will create a new plot consisting of the Fourier transforms of the vectors
given on the command line. Each vector given should be a transient analysis result, i.e. it
should have time as a scale. You will have got these vectors by the tran Tstep Tstop
```
Tstart command.

```
The vector should have a linear equidistant time scale. Therefore linearization using the linearize
command is recommended before running fft. Be careful selecting a Tstep value small
enough for good interpolation, e.g. much smaller than any signal period to be resolved by fft
(see linearize command). The Fast Fourier Transform will be computed using a window
function as given with the specwindow variable. A new plot named specx will be generated
with a new vector (having the same name as the input vector, see command above) containing
the transformed data.

Ngspice has two FFT implementations:

1. Standard code is based on the FFT function provided by John Green ‘FFTs for RISC 2.0‘,
[downloaded 2012, now to be found here. These are a power-of-two routines for fft and](http://hyperarchive.lcs.mit.edu/HyperArchive/Archive/dev/src/ffts-for-risc-2-c.hqx)
ifft. If the input size doesn’t fit this requirement the remaining data will be zero padded
up to the next 2N field size. You have to take care of the correlated change in the scale
vector.

2. If available on the operating system (see Chapter 32) ngspice can be linked to the famous
[FFTW-3 package, found here. This high performance package has advantages in speed](http://www.fftw.org/)
and accuracy compared to most of the freely available FFT libraries. It makes arbitrary
size transforms for even and odd data.

How to compute the fft from a transient simulation output:
```
   ngspice 8 -> setplot tran1
   ngspice 9 -> linearize V(2)
   ngspice 9 -> set specwindow=blackman
   ngspice 10 -> fft V(2)
   ngspice 11 -> plot mag(V(2))
Linearize will create a new vector V(2) in a new plot tran2. The command fft V(2) will

```
create a new plot spec1 with vector V(2) holding the resulting data.

The variables listed in the following table control operation of the fft command. Each can be
set with the set command before calling fft.

`specwindow:` This variable is set to one of the following strings, which will determine the
type of windowing used for the Fourier transform in the spec and fft command. If not set, the
default is hanning.

**none No windowing**

**rectangular Rectangular window**

**bartlet Bartlett (also triangle) window**

**blackman Blackman window**


-----

**hanning Hanning (also hann or cosine) window**

**hamming Hamming window**

**gaussian Gaussian window**

**flattop Flat top window**

Figure 17.1: Spec and FFT window functions (Gaussian order = 4)

**specwindoworder:** This can be set to an integer in the range 2-8. This sets the order when
the Gaussian window is used in the spec and fft commands. If not set, order 2 is used.

### 17.5.27 Fourier: Perform a Fourier transform

General Form:
```
   fourier fundamental_frequency [expression ...]

```
**Fourier is used to analyze the output vector(s) of a preceding transient analysis (see 17.5.80).**
It does a Fourier analysis of each of the given values, using the first 10 multiples of the fundamental frequency (or the first nfreqs multiples, if that variable is set - see 17.7). The printed
output is like that of the .four ngspice line (Chapt. 15.6.4). The expressions may be any valid
expression (see 17.2), e.g. v(2). The evaluated expression values are interpolated onto a fixedspace grid with the number of points given by the fourgridsize variable, or 200 if it is not set.
The interpolation is of degree polydegree if that variable is set, or 1. If polydegree is 0, then no
interpolation is done. This is likely to give erroneous results if the time scale is not monotonic,
though.

The fourier command not only issues a printout, but also generates vectors, one per expression.
The size of the vector is 3 x nfreqs (per default 3 x 10). The name of the new vector is fouriermn,


![](NGS-ch17-interpreter.pdf-19-0.png)

-----

where m is set by the mth call to the fourier command, n is the nth expression given in the actual
fourier command. fouriermn[0] is the vector of the 10 (nfreqs) frequency values, fouriermn[1]
contains the 10 (nfreqs) magnitude values, fouriermn[2] the 10 (nfreqs) phase values of the
result.

Example:
```
  * do the transient analysis
   tran 1n 1m
  * do the fourier analysis
   fourier 3.34e6 v(2) v(3) $ first call
   fourier 100e6 v(2) v(3) $ second call
  * get individual values
   let newt1 = fourier11[0][1]
   let newt2 = fourier11[1][1]
   let newt3 = fourier11[2][1]
   let newt4 = fourier12[0][4]
   let newt5 = fourier12[1][4]
   let newt6 = fourier12[2][4]
  * plot magnitude of second expression (v(3))
  * from first call versus frequency
   plot fourier12[1] vs fourier12[0]

```
The plot command from the example plots the vector of the magnitude values, obtained by
the first call to fourier and evaluating the first expression in this call, against the vector of the
frequency values.

### 17.5.28 Gnuplot: Graphics output via gnuplot

General Form:
```
   gnuplot file plotargs

```
Like plot, but using gnuplot for graphics output and further data manipulation. ngspice creates
a file called file.plt containing the gnuplot command sequence, a file called file.data containing
the data to be plotted, and a file called either file.eps (Postscript, this is the default) or file.png
(the compressed binary png format, when the variable gnuplot_terminal is set to png). It
is possible to suppress the latter hardcopy file by using a file name that starts with ’np_’. On
Linux gnuplot is called via xterm, and offers a Gnuplot console to manipulate the data. On
Windows a plot window is opened and the command console window is available with a mouse
click. Of course you have to have gnuplot installed on your system.

### 17.5.29 Hardcopy: Save a plot to a file for printing

General Form:
```
   hardcopy file plotargs

```

-----

Just like plot, except that it creates a file called file containing the plot. The file is a postscript
image. As an alternative the plot(5) format is available by setting the hcopydevtype variable
to plot5, and can be printed by either the plot(1) program or lpr with the -g flag. See also
Chapt. 18.6 for more details (color etc.).

### 17.5.30 Help: Print summaries of Ngspice commands

Prints help. This help information, however, is spice3f5-like, stemming from 1991 and thus
is outdated. If commands are given, descriptions of those commands are printed. Otherwise
help for only a few major commands is printed. On Windows this help command is no longer
[available. Spice3f5 compatible help may be found in the Spice 3 User manual. For ngspice](http://newton.ex.ac.uk/teaching/CDHW/Electronics2/userguide/)
please use this manual.

### 17.5.31 History: Review previous commands

General Form:
```
   history [-r] [number]

```
Print out the history, or the last (first if -r is specified) number commands typed at the keyboard.

A history substitution enables you to reuse a portion of a previous command as you type the
current command. History substitutions save typing. A history substitution normally starts
with a ’!’. A history substitution has three parts: an event that specifies a previous command,
a selector that selects one or more words of the event, and some modifiers that modify the
selected words. The selector and modifiers are optional. A history substitution has the form
```
![event][:]selector[:modifier] . . . ] The event is required unless it is followed by a

```
selector that does not start with a digit. The ’:’ can be omitted before the selector if this
selector does not begin with a digit. History substitutions are interpreted before anything else
```
— even before quotations and command substitutions. The only way to quote the ’!’ of a

```
history substitution is to escape it with a preceding backslash. A ’!’ need not be escaped if it
is followed by whitespace, ’=’, or ’(’.

Ngspice saves each command that you type on a history list, provided that the command contains at least one word. The commands on the history list are called events. The events are
numbered, with the first command that you issue when you start Ngspice being number one.
The history variable specifies how many events are retained on the history list.

These are the forms of an event in a history substitution:

|These are the|forms of an event in a history substitution:|
|---|---|
|!!|The preceding event. Typing ’!!’ is an easy way to reissue the previous command.|
|!n|Event number n.|
|!-n|The nth previous event. For example, !-1 refers to the immediately preceding event and is equivalent to !!.|
|!str|The unique previous event whose name starts with str.|
|!?str[?]|The unique previous event containing the string str. The closing ’?’ can be omitted if it is followed by a newline.|


-----

You can modify the words of an event by attaching one or more modifiers. Each modifier must
be preceded by a colon. The following modifiers assume that the first selected word is a file
name:

`:r` Removes the trailing .str extension from the first selected word.

`:h` Removes a trailing path name component from the first selected word.

`:t` Removes all leading path name components from the first selected word.

`:e` Remove all but the trailing suffix.

`:p` Print the new command but do not execute it.

`s/old/new` Substitute new for the first occurrence of old in the event line. Any delimiter may be
used in place of ‘/’. The delimiter may be quoted in old and new with a single backslash.
If ‘&’ appears in new, it is replaced by old. A single backslash will quote the ‘&
final delimiter is optional if it is the last character on the input line.

`&` Repeat the previous substitution.

`g a` Cause changes to be applied over the entire event line. Used in conjunction with ‘
in gs/old/new/, or with ‘&’.

`G` Apply the following ‘s’ modifier once to each word in the event.

For example, if the command ls /usr/elsa/toys.txt has just been executed, then the command
echo !!^:r !!^:h !!^:t !!^:t:r produces the output /usr/elsa/toys /usr/elsa toys.txt toys . The ’^’
command is explained in the table below.

You can select a subset of the words of an event by attaching a selector to the event. A history
substitution without a selector includes all of the words of the event. These are the possible
selectors for selecting words of the event:

:0 The command name

[:]^ The first argument

[:]$ The last argument

:n The n[th] argument (n 1)
_≥_

:n1-n2 Words n1 through n2

[:]* Words 1 through $

:x* Words x through $

:x- Words x through ($ - 1)

[:]-x Words 0 through x

[:]% The word matched by the last ?str? search used

The colon preceding a selector can be omitted if the selector does not start with a digit.

The following additional special conventions provide abbreviations for commonly used forms
of history substitution:

  - An event specification can be omitted from a history substitution if it is followed by a
selector that does not start with a digit. In this case the event is taken to be the event
used in the most recent history reference on the same line if there is one, or the preceding
event otherwise. For example, the command echo !?qucs?^ !$ echoes the first and last
arguments of the most recent command containing the string qucs .

  - If the first non-blank character of an input line is ’^’, the ’^’ is taken as an abbreviation
for !:s^ . This form provides a convenient way to correct a simple spelling error in the

|name:|Col2|
|---|---|
|:r|Removes the trailing .str extension from the first selected word.|
|:h|Removes a trailing path name component from the first selected word.|
|:t|Removes all leading path name components from the first selected word.|
|:e|Remove all but the trailing suffix.|
|:p|Print the new command but do not execute it.|
|s/old/new|Substitute new for the first occurrence of old in the event line. Any delimiter may be used in place of ‘/’. The delimiter may be quoted in old and new with a single backslash. If ‘&’ appears in new, it is replaced by old. A single backslash will quote the ‘&’. The final delimiter is optional if it is the last character on the input line.|
|&|Repeat the previous substitution.|
|g a|Cause changes to be applied over the entire event line. Used in conjunction with ‘s’, as in gs/old/new/, or with ‘&’.|
|G|Apply the following ‘s’ modifier once to each word in the event.|

|:0|The command name|
|---|---|
|[:]^|The first argument|
|[:]$|The last argument|
|:n|The nth argument (n 1) ≥|
|:n1-n2|Words n1 through n2|
|[:]*|Words 1 through $|
|:x*|Words x through $|
|:x-|Words x through ($ - 1)|
|[:]-x|Words 0 through x|
|[:]%|The word matched by the last ?str? search used|


-----

previous line. For example, if by mistake you typed the command cat /etc/lasswd you
could re-execute the command with lasswd changed to passwd by typing ^l^p .

  - You can enclose a history substitution in braces to prevent it from absorbing the following
characters. In this case the entire substitution except for the starting ’!’ must be within
the braces. For example, suppose that you previously issued the command cp accounts
../money . Then the command !cps looks for a previous command starting with cps
while the command !{cp}s turns into a command cp accounts ../moneys .

Some characters are handled specially as follows:

~ Expands to the home directory

 - Matches any string of characters in a filename

? Matches any single character in a filename

[] Matches any of the characters enclosed in a filename

 - Used within [] to specify a range of characters. For example, [b-k] matches on any
character between and including ‘b’ through to ‘k’.

^ If the ^ is included within [] as the first character, then it negates the following characters
matching on anything but those. For example, [^agm] would match on anything other
than ‘a’, ‘g’ and ‘m’. [^a-zA-Z] would match on anything other than an alphabetic
character.

The wildcard characters *, ?, [, and ] can be used, but only if you unset noglob first. This
makes them rather useless for typing algebraic expressions, so you should set noglob again
after you are done with wildcard expansion.

When the environment variable HOME exists (on Unix, Linux, or CYGWIN), history permanently stores previous command lines in the file $HOME/._ngspice_history. When this
variable does not exist (typically on Windows when the readline library is not officially installed), the history file is called .history and put in the current working directory.

The history command is part of the readline or editline package. The readline program provides a command line editor that is configurable through the file .inputrc. The path to this
configuration file is either found in the shell variable INPUTRC, or it is (on Unix/Linux/CYGWIN) the file ~/.inputrc in the user’s home directory. On Windows systems the configuration
file is /Users/<username>/.inputrc, unless the readline library was officially installed. In that
case the filename is taken from the Windows registry and points to a location that the user speci[fied during installation. See https://cnswww.cns.cwru.edu/php/chet/readline/rltop.html for](https://cnswww.cns.cwru.edu/php/chet/readline/rltop.html)
detailed documentation. Some useful commands are:

|~|Expands to the home directory|
|---|---|
|*|Matches any string of characters in a filename|
|?|Matches any single character in a filename|
|[]|Matches any of the characters enclosed in a filename|
|-|Used within [] to specify a range of characters. For example, [b-k] matches on any character between and including ‘b’ through to ‘k’.|
|^|If the ^ is included within [] as the first character, then it negates the following characters matching on anything but those. For example, [^agm] would match on anything other than ‘a’, ‘g’ and ‘m’. [^a-zA-Z] would match on anything other than an alphabetic character.|

|Left/Right arrow|Move one character to the left or right|
|---|---|
|Home/End|Move to beginning or end of line|
|Up/Down arrow|Cycle through the history buffer|
|C-_-|Undo last editing command|
|C-r|Incremental search backward|
|TAB|completion of a file name|
|C-ak|Erase the command line (kill)|
|C-y|Retrieve last kill (yank)|
|C-u|Erase from cursor to start of line|


-----

### 17.5.32 Inventory: Print circuit inventory

General Form:
```
   inventory

```
This commands accepts no argument and simply prints the number of instances of a particular
device in a loaded netlist.

### 17.5.33 Iplot*: Incremental plot

General Form:
```
   iplot [ node ...]

```
Incrementally plot the values of the nodes while ngspice runs. The iplot command can be used
with the where command to find trouble spots in a transient simulation.

The @name[param] notation (31.1) might not work yet.

### 17.5.34 Jobs*: List active asynchronous ngspice runs

General Form:
```
   jobs

```
Report on the asynchronous ngspice jobs currently running. Ngnutmeg checks to see if the
jobs are finished every time you execute a command. If it is done then the data is loaded and
becomes available.

### 17.5.35 Let: Assign a value to a vector

General Form:
```
   let name = expr

```
Creates a new vector called name with the value specified by expr, an expression as described
above. If expr is [] (a zero-length vector) then the vector becomes undefined. Individual elements of a vector may be modified by appending a subscript to name (ex. name[0]). If there are
no arguments, let is the same as display.

The command let creates a vector in the current plot. Use setplot (17.5.62) to create a new plot.

There is no straightforward way to initialize a new vector. In general, one might want let
initialize a slice (i.e. name[4:4,21:23] = [ 1 2 3 ]) of a multi-dimensional matrix of arbitrary
type (i.e. real, complex ..), where all values and indexes are arbitrary expressions. This will
fail. The procedure is to first allocate a real vector of the appropriate size with either vector(),
```
unitvec(), or [ n1 n2 n3 ... ]. The second step is to optionally change the type of the

```

-----

new vector (to complex) with the j() function. The third step reshapes the dimensions, and
the final step (re)initializes the contents, like so:
```
  let a = j(vector(10))
  reshape a [2][5]
  let a[0][0] = (pi,pi)

```
Initialization of real vectors can be done quite efficiently with compose:
```
  compose a values (pi, pi) (1,1) (2,sqrt(7)) (boltz,e)
  reshape a [2][2]

```
See also unlet (17.5.84), compose (17.5.12).

### 17.5.36 Linearize*: Interpolate to a linear scale

General Form:
```
   linearize vec ...

```
Create a new plot with all of the vectors in the current plot, or only those mentioned as arguments to the command, all data linearized onto an equidistant time scale.

How to compute the fft from a transient simulation output:
```
   ngspice 8 -> setplot tran1
   ngspice 9 -> linearize V(2)
   ngspice 9 -> set specwindow=blackman
   ngspice 10 -> fft V(2)
   ngspice 11 -> plot mag(V(2))tstep
Linearize will redo the vectors vec or renew all vectors of the current plot (e.g. tran3) if no

```
arguments are given and store them into a new plot (e.g. tran4). The new vectors are interpolated
onto a linear time scale, which is determined by the values of tstep, tstart, and tstop in
the currently active transient analysis. The currently loaded input file must include a transient
analysis (a tran command may be run interactively before the last reset, alternately), and
the current plot must be from this transient analysis. The length of the new vector is (tstop
```
- tstart) / tstep + 1.5. This command is needed for example if you want to do a fft

```
analysis (17.5.26). Please note that the parameter tstep of your transient analysis (see Chapt.
15.3.9) has to be small enough to get adequate resolution, otherwise the command linearize
will do sub-sampling of your signal. If no circuit is loaded and the data have been acquired
by the load (17.5.38) command, Linearize will take time data from transient analysis scale
vector.


-----

### 17.5.37 Listing*: Print a listing of the current circuit

General Form:
```
   listing [logical] [physical] [deck] [expand] [param]

```
If the logical argument is given, the listing is with all continuation lines collapsed into one line,
and if the physical argument is given the lines are printed out as they were found in the file. The
default is logical. A deck listing is just like the physical listing, except without the line numbers
it recreates the input file verbatim (except that it does not preserve case). If the word expand is
present, the circuit is printed with all subcircuits expanded. The option param allows to print
all parameters and their actual values.

### 17.5.38 Load: Load rawfile data

General Form:
```
   load [filename] ...

```
Loads either binary or ascii format rawfile data from the files named. The default file-name is
rawspice.raw, or the argument to the -r flag if there was one.

### 17.5.39 Meas*: Measurements on simulation data

General Form (example):
```
   MEAS {DC|AC|TRAN|SP} result TRIG trig_variable VAL=val <TD=td>
  <CROSS=# | CROSS=LAST> <RISE=#|RISE=LAST> <FALL=#|FALL=LAST>
  <TRIG AT=time> TARG targ_variable VAL=val <TD=td>
  <CROSS=# | CROSS=LAST> <RISE=#|RISE=LAST>
  <FALL=#|FALL=LAST> <TRIG AT=time>

```
Most of the input forms found in 15.4 may be used here with the command meas instead of
```
.meas(ure). Using meas inside the .control ... .endc section offers additional features

```
compared to the .meas use. meas will print the results as usual, but in addition will store
its measurement result (typically the token result given in the command line) in a vector.
This vector may be used in following command lines of the script as an input value of another
command. For details of the command see Chapt. 15.4. The measurement type SP is only
available here, because a fft command will prepare the data for SP measurement. Option
```
autostop (15.1.4) is not available.

```
Unfortunately par(’expression’) (15.6.6) will not work here, i.e. inside the .control section.
You may use an expression by the let command instead, giving let vec_new = expression.


-----

Replacement for par(’expression’) in meas inside the .control section
```
   let vdiff = v(n1)-v(n0)
   meas tran vtest find vdiff at=0.04e-3
  *the following will not do here:
  *meas tran vtest find par(’v(n1)-v(n0)’) at=0.04e-3

### 17.5.40 Mdump*: Dump the matrix values to a file (or to console)

```
General Form:
```
   mdump <filename >

```
If <filename> is given, the output will be stored in file <filename>, otherwise dumped to
your console.

### 17.5.41 Mrdump*: Dump the matrix right hand side values to a file (or to console)

General Form:
```
   mrdump <filename >

```
If <filename> is given, the output will be appended to file <filename>, otherwise dumped to
your console.

Example usage after ngspice has started:
```
  * Dump matrix and RHS values after 10 and 20 steps
  * of a transient simulation
   source rc.cir
   step 10
   mdump m1.txt
   mrdump mr1.txt
   step 10
   mdump m2.txt
   mrdump mr2.txt
  * just to continue to the end
   step 10000

```
You may create a loop using the control structures (Chapt. 17.6).

### 17.5.42 Noise*: Noise analysis

See the .NOISE analysis (15.3.4) for details.


-----

The noise command will generate two plots (typically named noise1 and noise2) with Noise
Spectral Density Curves and Integrated Noise data. To write these data into output file(s), you
may use the following command sequence:

Command sequence for writing noise data to file(s):
```
  .control
   tran 1e-6 1e-3
   write test_tran.raw
   noise V(out) vinp dec 333 1 1e8 16
   print inoise_total onoise_total
  *first option to get all of the output (two files)
   setplot noise1
   write test_noise1.raw all
   setplot noise2
   write test_noise2.raw all
  * second option (all in one raw-file)
   write testall.raw noise1.all noise2.all
  .endc

### 17.5.43 Op*: Perform an operating point analysis

```
General Form:
```
  op

```
Do an operating point analysis. See Chapt. 15.3.5 for more details.

### 17.5.44 Option*: Set a ngspice option

General Form:
```
   option [option=val] [option=val] ...

```
Set any of the simulator variables as listed in Chapt. 15.1. See this chapter also for more
information on the available options. The option command without any argument lists the
actual options set in the simulator (to be verified). Multiple options may be set in a single line.

The following example demonstrates a control section, which may be added to your circuit file
to test the influence of variable trtol on the number of iterations and on the simulation time.


-----

Command sequence for testing option trtol:
```
  .control
   set noinit
   option trtol=1
   echo
   echo trtol=1
   run
   rusage traniter trantime
   reset
   option trtol=3
   echo
   echo trtol=3
   run
   rusage traniter trantime
   reset
   option trtol=5
   echo
   echo trtol=5
   run
   rusage traniter trantime
   reset
   option trtol=7
   echo
   echo trtol=7
   run
   rusage traniter trantime
   plot tran1.v(out25) tran1.v(out50) v(out25) v(out50)
  .endc

### 17.5.45 Plot: Plot vectors on the display

```
General Form:
```
   plot exprs [ylimit ylo yhi] [xlimit xlo xhi] [xindices xilo xihi]
  [xcompress comp] [xdelta xdel] [ydelta ydel]
  [xlog] [ylog] [loglog] [nogrid] [vs xname_expr]
  [linplot] [combplot] [pointplot] [nointerp]
  [xlabel word] [ylabel word] [title word] [samep] [linear]

```
Plot the given vectors or exprs on the screen (if you are on a graphics terminal). The xlimit
and ylimit arguments determine the high and low x- and y-limits of the axes, respectively. The
```
xindices arguments determine what range of points are to be plotted - everything between the
xilo’th point and the xihi’th point is plotted. The xcompress argument specifies that only

```
one out of every comp points should be plotted. If an xdelta or a ydelta parameter is present,
it specifies the spacing between grid lines on the X- and Y-axis. These parameter names may


-----

be abbreviated to xl, yl, xind, xcomp, xdel, and ydel respectively.

The xname_expr argument is an expression to use as the scale on the x-axis. If xlog or ylog are
present then the X or Y scale, respectively, are logarithmic (loglog is the same as specifying
both). The xlabel and ylabel arguments cause the specified labels to be used for the X and
Y axes, respectively.

If samep is given, the values of the other parameters (other than xname_expr) from the previous
```
plot, hardcopy, or asciiplot command are used unless re-defined on the command line.

```
The title argument is used in the headline of the plot window and replaces the default text,
which is ‘actual plot: first line of input file’.

The linear keyword is used to override a default logscale plot (as in the output for an AC
analysis).

The keywords linplot, combplot and pointplot select different plot styles. The keyword
```
nointerp turns of interpolation of the vector data, nogrid suppresses the drawing of grid lines.

```
Finally, the keyword polar generates a polar plot. To produce a smith plot, use the keyword
```
smith. Note that the data is transformed, so for smith plots you will see the data transformed

```
by the function (x-1)/(x+1). To produce a polar plot with a smith grid but without performing
the smith transform, use the keyword smithgrid.

If you specify plot all, all vectors (including the scale vector) are plotted versus the scale
vector (see commands display (17.5.20) or setscale (17.5.63) on viewing the vectors of the
current plot). The command plot ally will not plot the scale vector, but all other ’real’ y
values. The command plot alli selects all current vectors, the command plot allv all
voltage vectors.

If the vector name to be plotted contains -, / or other tokens that may be taken for operators of an expression, and plotting fails, try enclosing the name in double quotes, e.g. plot
```
“/vout”.

```
Plotting of complex vectors, as may occur after an ac simulation, requires special considerations. Please see Chapt. 17.5.1 for details.

### 17.5.46 Pre_<command>: execute commands prior to parsing the circuit

General Form:
```
  pre_<command >

```
All commands in a .control ... .endc section are executed after the circuit has been parsed.
If you need command execution before circuit parsing, you may add these commands to the
general spinit or local .spiceinit files. Another possibility is adding a leading pre_ to a command within the .control section of an ordinary input file, which forces the command to be
executed before circuit parsing. Basically <command> may be any command listed in Chapt.
17.5, however only a few commands are indeed useful here. Some examples are given below:


-----

Examples:
```
   pre_unset ngdebug
   pre_set strict_errorhandling
   pre_codemodel mymod.cm
pre_<command> is available only in the .control mode (see 16.4.3), not in interactive mode,

```
where the user may determine herself when a circuit is to be parsed, using the source command
(17.5.71) .

### 17.5.47 Print: Print values

General Form:
```
   print [col] [line] expr ...

```
Prints the vector(s) described by the expression expr. If the col argument is present, print the
vectors named side by side. If line is given, the vectors are printed horizontally. col is the
default, unless all the vectors named have a length of one, in which case line is the default.
The options width (default 80) and height (default 24) are effective for this command (see
```
asciiplot 17.5.5). The ’more’ mode is the standard mode if printing to the screen, that is after

```
a number of lines given by height, and after a page break printing stops with request for answering the prompt by <return> (print next page), ’c’ (print rest) or ’q’ (quit printing). If everything
shall be printed without stopping, put the command set nomoremode into .spiceinit 16.6 (or
spinit 16.5). If the expression is all, all of the vectors available are printed. Thus print col
```
all > filename prints everything into the file filename in SPICE2 format. The scale vector

```
(time, frequency) is always in the first column unless the variable noprintscale is true. You
may use the vectors alli, allv, ally with the print command, but then the scale vector
will not be printed.

Examples:
```
   print all
   set width=300
   print v(1) > outfile.out

### 17.5.48 Psd: power spectral density of vectors

```
General Form:
```
   psd ave vector1 [vector2] ...

```
Calculate the single sided power spectral density of signals (vectors) resulting from a transient
analysis. Windowing is available as described in the fft command (17.5.26). The FFT data are
squared, summarized, weighted and printed as total noise power up to Nyquist frequency, and
as noise voltage or current.


-----

```
ave is the number of points used for averaging and smoothing in a postprocess, useful for noisy

```
data. A new plot vector is created that holds the averaged results of the FFT, weighted by the
frequency bin. The result can be plotted and has the units V^2/Hz or A^2/Hz, depending on the
the input vector.

### 17.5.49 Quit: Leave Ngspice or Nutmeg

General Form:
```
   quit
   quit [exitcode]

```
Quit ngnutmeg or ngspice. Ngspice will ask for an acknowledgment if parameters have not
been saved. If unset askquit is specified, ngspice will terminate immediately.

The optional parameter exitcode is an integer that sets the exit code for ngspice. This is useful
to return a success/fail value to the operating system.

### 17.5.50 Rehash: Reset internal hash tables

General Form:
```
   rehash

```
Recalculate the internal hash tables used when looking up UNIX commands, and make all
UNIX commands in the user’s PATH available for command completion. This is useless unless
you have set unixcom first (see above).

### 17.5.51 Remcirc*: Remove the current circuit

General Form:
```
   remcirc

```
This command removes the current circuit from the list of circuits sourced into ngspice. To select a specific circuit, use setcirc (17.5.61). To load another circuit, refer to source (17.5.71).
The new actual circuit will be the circuit on top of the list of the remaining circuits.

### 17.5.52 Reset*: Reset an analysis

General Form:
```
   reset

```

-----

Throw out any intermediate data in the circuit (e.g, after a breakpoint or after one or more
analyses have been done), and re-parse the input file. The circuit can then be re-run from it’s
initial state, overriding the effect of any set or alter commands.
```
Reset may be required in simulation loops preceding any run (or tran ...) command.

### 17.5.53 Reshape: Alter the dimensionality or dimensions of a vector

```
General Form:
```
   reshape vector vector ...
  or
   reshape vector vector ... [ dimension, dimension, ... ]
  or
   reshape vector vector ... [ dimension ][ dimension ] ...

```
This command changes the dimensions of a vector or a set of vectors. The final dimension
may be left off and it will be filled in automatically. If no dimensions are specified, then the
dimensions of the first vector are copied to the other vectors. An error message of the form
’dimensions of x were inconsistent’ can be ignored.

Example:
```
  * generate vector with all (here 30) elements
   let newvec=vector(30)
  * reshape vector to format 3 x 10
   reshape newvec [3][10]
  * access elements of the reshaped vector
   print newvec[0][9]
   print newvec[1][5]
   let newt = newvec[2][4]

### 17.5.54 Resume*: Continue a simulation after a stop

```
General Form:
```
   resume

```
Resume a simulation after a stop or interruption (control-C).

### 17.5.55 Rspice*: Remote ngspice submission

General Form:
```
   rspice <input file>

```

-----

Runs a ngspice remotely taking the input file as a ngspice input file, or the current circuit if
no argument is given. Ngnutmeg or ngspice waits for the job to complete, and passes output
from the remote job to the user’s standard output. When the job is finished the data is loaded
in as with aspice. If the variable rhost is set, ngnutmeg connects to this host instead of the
default remote ngspice server machine. This command uses the rsh command and thereby
requires authentication via a .rhosts file or other equivalent method. Note that rsh refers to
the ‘remote shell’ program, which may be remsh on your system; to override the default name
of rsh, set the variable remote_shell. If the variable rprogram is set, then rspice uses this
as the pathname to the program to run on the remote system.

Note: rspice will not acknowledge elements that have been changed via the alter or altermod
commands.

### 17.5.56 Run*: Run analysis from the input file

General Form:
```
   run [rawfile]

```
Run the simulation as specified in the input file. If there were any of the control lines .ac, .op,
```
.tran, or .dc, they are executed. The output is put in rawfile if it was given, in addition to

```
being available interactively.

### 17.5.57 Rusage: Resource usage

General Form:
```
   rusage [resource ...]

```
Print resource usage statistics. If any resources are given, just print the usage of that resource.
Most resources require that a circuit be loaded. Currently valid resources are:

**decklineno Number of lines in deck**

**netloadtime Nelist loading time**

**netparsetime Netlist parsing time**

**elapsed The amount of time elapsed since the last rusage elapsed call.**

**faults Number of page faults and context switches (BSD only).**

**space Data space used.**

**time CPU time used so far.**

**temp Operating temperature.**

**tnom Temperature at which device parameters were measured.**


-----

**equations Circuit Equations**

**time Total Analysis Time**

**totiter Total iterations**

**accept Accepted time-points**

**rejected Rejected time-points**

**loadtime Time spent loading the circuit matrix and RHS.**

**reordertime Matrix reordering time**

**lutime L-U decomposition time**

**solvetime Matrix solve time**

**trantime Transient analysis time**

**tranpoints Transient time-points**

**traniter Transient iterations**

**trancuriters Transient iterations for the last time point***

**tranlutime Transient L-U decomposition time**

**transolvetime Transient matrix solve time**

**everything All of the above.**

- listed incorrectly as ‘Transient iterations per point’.

### 17.5.58 Save*: Save a set of outputs

General Form:
```
   save [all | outvec ...]

```
Save a set of outputs, discarding the rest (if not keyword all is given). Maybe used to dramatically reduce memory (RAM) requirements if only a few useful node voltages or branch currents
are saved.

Node voltages may be saved by giving the nodename or v(nodename). Currents through an
independent voltage source are given by i(sourcename) or sourcename#branch. Internal device data (31.1) are accepted as @dev[param]. The syntax is identical to the .save command
(15.6.1).

Note: In the .control .... `.endc section save must occur before the run or tran com-`
mand to become effective.

If a node has been mentioned in a save command, it appears in the working plot after a run has
completed, or in the rawfile written by the write (17.5.89) command. For backward compatibility, if there are no save commands given, all outputs are saved. If you want to trace (17.5.79)


-----

or plot (17.5.45) a node, you have to save it explicitly, except for all given or no save command
at all.

When the keyword all appears in the save command, all node voltages, voltage source currents
and inductor currents are saved in addition to any other vectors listed.

Save voltage and current:
```
   save vd_node vs#branch v(vs_node) i(vs2)
Save allows to store and later access internal device parameters. e.g. in a command like

```
Save internal parameters:
```
   save all @mn1[gm]

```
saves all standard analysis output data plus gm of transistor mn1 to internal memory (see also
31.1).
```
save may store data from nodes or devices residing inside of a subcircuit:

```
Save voltage on node 3 (top level), node 8 (from inside subcircuit x2) and current through vmeas
(from subcircuit x1):
```
   save 3 x1.x2.x1.x2.8 v.x1.x1.x1.vmeas#branch

```
Save internal parameters within subcircuit:
```
   save @m.xmos3.mn1[gm]

```
Use commands listing expand (17.5.37, before the simulation) or display (17.5.20, after simulation) to obtain a list of all nodes and currents available. Please see Chapt. 31 for an
explanation of the syntax for internal parameters.

Entering several save lines in a single .control section will accumulate the nodes and parameters to be saved. If you want to exclude a node, you have to get its number by calling status
(17.5.73) and then calling delete number (17.5.16).

### 17.5.59 Sens*: Run a sensitivity analysis

General Form:
```
   sens output_variable
   sens output_variable ac ( DEC | OCT | LIN ) N Fstart Fstop

```
Perform a Sensitivity analysis. `output_variable is either a node voltage (ex. v(1) or`
```
v(A,out)) or a current through a voltage source (e.g. i(vtest)). The first form calcula
```
tes DC sensitivities, the second form AC sensitivities. The output values are in dimensions of
change in output per unit change of input (as opposed to percent change in output or per percent
change of input).


-----

### 17.5.60 Set: Set the value of a variable

General Form:
```
   set [word]
   set [word = value] ...

```
Set the value of word to value, if it is present. You can set any word to be any value, numeric or
string. If no value is given then the value is the Boolean ‘true’. If you enter a string, you have
to enclose it in double quotes. Set save the lower case version of a word string.

The value of word may be inserted into a command by writing $word. If a variable is set to
a list of values that are enclosed in parentheses (which must be separated from their values by
white space), the value of the variable is the list.

The variables used by ngspice are listed in section 17.7.
```
Set entered without any parameter will list all variables set, and their values, if applicable.

```
Be advised that set sets the lower case variant of word.

### 17.5.61 Setcirc*: Change the current circuit

General Form:
```
   setcirc [circuit number]

```
The current circuit is the one that is used for the simulation commands below. When a circuit
is loaded with the source command (see below, 17.5.71) it becomes the current circuit.
```
Setcirc followed by ’return’ without any parameters lists all circuits loaded.

### 17.5.62 Setplot: Switch the current set of vectors

```
General Form:
```
   setplot [plotname]

```
Set the current plot to the plot with the given name, or if no name is given, prompt the user
with a menu. (Note that the plots are named as they are loaded, with names like tran1 or op2.
These names are shown by the setplot and display commands and are used by diff, below.)
If the ‘New’ item is selected, a new plot is generated that has no vectors defined.

Note that here the word plot refers to a group of vectors that are the result of one ngspice run.
When more than one file is loaded in, or more than one plot is present in one file, ngspice keeps
them separate and only shows you the vectors in the current plot.


-----

### 17.5.63 Setscale: Set the scale vector for the current plot

General Form:
```
   setscale [vector]

```
Defines the scale vector for the current plot. If no argument is given, the current scale vector is
printed. The scale vector delivers the values for the x-axis in a 2D plot.

### 17.5.64 Settype: Set the type of a vector

General Form:
```
   settype type vector ...

```
Change the type of the named vectors to type. Type names can be found in the following table.

Type Unit Type Unit

notype pole

time s zero

frequency Hz s-param

voltage V temp-sweep Celsius

current A res-sweep Ohms

onoise-spectrum (V or A)/[√]Hz impedance Ohms

onoise-integrated V or A admittance Mhos

inoise-spectrum (V or A)/[√]Hz power W

inoise-integrated V or A phase Degree

decibel dB

### 17.5.65 Shell: Call the command interpreter

General Form:
```
   shell [ command ]

```
Call the operating system’s command interpreter; execute the specified command or call for
interactive use.

### 17.5.66 Shift: Alter a list variable

General Form:
```
   shift [varname] [number]

```
If varname is the name of a list variable, it is shifted to the left by number elements (i.e, the
number leftmost elements are removed). The default varname is argv, and the default number
is 1.

|Type|Unit|Col3|Type|Unit|
|---|---|---|---|---|
|notype|||pole||
|time|s||zero||
|frequency|Hz||s-param||
|voltage|V||temp-sweep|Celsius|
|current|A||res-sweep|Ohms|
|onoise-spectrum|√ (V or A)/ Hz||impedance|Ohms|
|onoise-integrated|V or A||admittance|Mhos|
|inoise-spectrum|√ (V or A)/ Hz||power|W|
|inoise-integrated|V or A||phase|Degree|
||||decibel|dB|


-----

### 17.5.67 Show*: List device state

General Form:
```
   show devices [ : parameters ], ...

```
The show command prints out tables summarizing the operating condition of selected devices.
If devices is missing, a default set of devices are listed, if devices is a single letter, devices
of that type are listed. A device’s full name may be specified to list only that device. Finally,
devices may be selected by model by using the form #modelname.

If no parameters are specified, the values for a standard set of parameters are listed. If the list of
parameters contains a ‘+’, the default set of parameters is listed along with any other specified
parameters.

For both devices and parameters, the word all has the obvious meaning.

Note: there must be spaces separating the ‘:’ that divides the device list from the parameter list.

### 17.5.68 Showmod*: List model parameter values

General Form:
```
   showmod models [ : parameters ], ...

```
The showmod command operates like the show command (above) but prints out model parameter values. The applicable forms for models are a single letter specifying the device type letter
(e.g. m, or c), a device name (e.g. m.xbuf22.m4b), or #modelname (e.g. #p1).

### 17.5.69 Snload*: Load the snapshot file

General Form:
```
   snload circuit -file file

```
**snload reads the snapshot file generated by snsave (17.5.70). circuit-file is the original circuit**
input file. After reading, the simulation may be continued by resume (17.5.54).

An input script for loading circuit and intermediate data, resuming simulation and plotting is
shown below:


-----

Typical usage:
```
  * SCRIPT: ADDER - 4 BIT BINARY
  * script to reload circuit and continue the simulation
  * begin with editing the file location
  * to be started with ’ngspice adder_snload.script’
  .control
  * cd to where all files are located
  cd D:\Spice_general\ngspice\examples\snapshot
  * load circuit and snpashot file
   snload adder_mos_circ.cir adder500.snap
  * continue simulation
   resume
  * plot some node voltages
   plot v(10) v(11) v(12)
  .endc

```
Due to a bug we currently need the term ’script’ in the title line (first line) of the script.

### 17.5.70 Snsave*: Save a snapshot file

General Form:
```
   snsave file

```
If you run a transient simulation and interrupt it by e.g. a stop breakpoint (17.5.75), you may
resume simulation immediately (17.5.54) or store the intermediate status in a snapshot file by
```
snsave for resuming simulation later (using snload (17.5.69)), even with a new instance of

```
ngspice.


-----

Typical usage:
```
   Example input file for snsave
  * load a circuit (including transistor models and .tran command)
  * starts transient simulation until stop point
  * store intermediate data to file
  * begin with editing the file location
  * to be run with ’ngspice adder_mos.cir’
  .include adder_mos_circ.cir
  .control
  *cd to where all files are located
  cd D:\Spice_general\ngspice\examples\snapshot
   unset askquit
   set noinit
  *interrupt condition for the simulation
   stop when time > 500n
  * simulate
   run
  * store snapshot to file
   snsave adder500.snap
   quit
  .endc
  .END

```
adder_mos_circ.cir is a circuit input file, including the netlist, .model and .tran statements.

Unfortunately snsave/snload will not work if you have XSPICE devices (or V/I sources with
polynomial statements) in your input deck.

### 17.5.71 Source: Read a ngspice input file

General Form:
```
   source infile

```
For ngspice: read the ngspice input file infile, containing a circuit netlist. Ngnutmeg and ngspice
commands may be included in the file, and must be enclosed between the lines .control and
```
.endc. These commands are executed immediately after the circuit is loaded, so a control

```
line of ac ... works the same as the corresponding .ac card. The first line in any input file
is considered a title line and not parsed but kept as the name of the circuit. Thus, a ngspice
command script in infile must begin with a blank line and then with a .control line. Also,
any line starting with the string ‘*#’ is considered as a control line (.control and .endc is
placed around this line automatically.). The exception to these rules are the files spinit (16.5)
and .spiceinit (16.6).


-----

For ngutmeg: reads commands from the file infile. Lines beginning with the character ‘*’ are
considered comments and are ignored.

The following search path is executed to find infile: current directory (OS dependent), <prefix>/share/ngspice/scripts, env. variable NGSPICE_INPUT_DIR (if defined), see 16.7. This
sequence may be overridden by setting the internal sourcepath variable (see 17.7) before calling source infile.

### 17.5.72 Spec: Create a frequency domain plot

General Form:
```
   spec start_freq stop_freq step_freq vector [vector ...]

```
Calculates a new complex vector containing the Fourier transform of the input vector (typically the linearized result of a transient analysis). The default behavior is to use a Hanning
window, but this can be changed by setting the variables specwindow and specwindoworder
appropriately.

Typical usage:
```
   ngspice 13 -> linearize
   ngspice 14 -> set specwindow = "blackman"
   ngspice 15 -> spec 10 1000000 1000 v(out)
   ngspice 16 -> plot mag(v(out))

```
Possible values for specwindow are: none, hanning, cosine, rectangular, hamming, triangle,
```
bartlet, blackman, gaussian and flattop. In the case of a Gaussian window specwindoworder

```
is a number specifying its order. For a list of window functions see 17.5.26.

### 17.5.73 Status*: Display breakpoint information

General Form:
```
   status

```
Display all of the saved nodes and parameters, traces and breakpoints currently in effect.

### 17.5.74 Step*: Run a fixed number of time-points

General Form:
```
   step [ number ]

```
Iterate number times, or once, and then stop.


-----

### 17.5.75 Stop*: Set a breakpoint

General Form:
```
   stop [ after n] [ when value cond value ] ...

```
Set a breakpoint. The argument after n means stop after iteration number ‘n’, and the argument
```
when value cond value means stop when the first value is in the given relation with the

```
second value, the possible relations being

Symbol Alias Meaning

= eq equal to

<> ne not equal

  - gt greater than

< lt less than

>= ge greater than or equal to

<= le less than or equal to

Symbol or alias may be used alternatively. All stop commands have to be given in the control
flow before the run command. The values above may be node names in the running circuit, or
real values. If more than one condition is given, e.g.
```
stop after 4 when v(1) > 4 when v(2) < 2,

```
the conjunction of the conditions is implied. If the condition is met, the simulation and control
flow are interrupted, and ngspice waits for user input.

In a transient simulation the ‘=’ or eq will only work with vector time in commands like
```
stop when time = 200n.

```
Internally a breakpoint will be set at the time requested. Multiple breakpoints may be set. If the
first stop condition is met, the simulation is interrupted, the commands following run or tran
(e.g. alter or altermod) are executed, then the simulation may continue at the first resume
command. The next breakpoint requires another resume to continue automatically. Otherwise
the simulation stops and ngspice waits for user input.

If you try to stop at
```
stop when V(1) eq 1

```
(or similar) during a transient simulation, you probably will miss this point, because it is not
very likely that at any time step the vector v(1) will have the exact value of 1. Then ngspice
simply will not stop.

### 17.5.76 Strcmp: Compare two strings

General Form:
```
   strcmp _flag $string1 "string2"

```
The command compares two strings, either given by a variable (string1) or as a string in quotes
(‘string2’). _flag is set as an output variable to ’0’, if both strings are equal. A value greater
than zero indicates that the first character that does not match has a greater value in str1 than in
str2; and a value less than zero indicates the opposite (like the C strcmp function).

|Symbol|Alias|Meaning|
|---|---|---|
|=|eq|equal to|
|<>|ne|not equal|
|>|gt|greater than|
|<|lt|less than|
|>=|ge|greater than or equal to|
|<=|le|less than or equal to|


-----

### 17.5.77 Sysinfo*: Print system information

General Form:
```
   sysinfo

```
The command prints system information useful for sending bug report to developers. Information consists of:

  - Name of the operating system,

  - CPU type,

  - Number of physical processors (not available under Windows OS), number of logical
processors,

  - Total amount of DRAM available,

  - DRAM currently available.

The example below shows the use of this command.
```
   ngspice 1 -> sysinfo
  OS: CYGWIN_NT -5.1 1.5.25(0.156/4/2) 2008-06-12 19:34
   CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz
   Logical processors: 2
   Total DRAM available = 1535.480469 MB.
   DRAM currently available = 984.683594 MB.
   ngspice 2 ->

```
This command has been tested under Windows OS and Linux. It may not be available in your
operating system environment.

### 17.5.78 Tf*: Run a Transfer Function analysis

General Form:
```
  tf output_node input_source

```
The tf command performs a transfer function analysis, returning:

  - the transfer function (output/input),

  - output resistance,

  - and input resistance


-----

between the given output node and the given input source. The analysis assumes a small-signal
DC (slowly varying) input. The following example file

Example input file:
```
  * Tf test circuit
  vs 1 0 dc 5
  r1 1 2 100
  r2 2 3 50
  r3 3 0 150
  r4 2 0 200
  .control
  tf v(3,5) vs
   print all
  .endc
  .end

```
will yield the following output:
```
transfer_function = 3.750000e-001
output_impedance_at_v(3,5) = 6.662500e+001
vs#input_impedance = 2.000000e+002

### 17.5.79 Trace*: Trace nodes

```
General Form:
```
   trace [ node ...]

```
For every step of an analysis, the value of the node is printed. Several traces may be active at
once. Tracing is not applicable for all analyses. To remove a trace, use the delete (17.5.16)
command.

### 17.5.80 Tran*: Perform a transient analysis

General Form:
```
   tran Tstep Tstop [ Tstart [ Tmax ] ] [ UIC ]

```
Perform a transient analysis. See Chapt. 15.3.9 of this manual for more details.

An interactive transient analysis may be interrupted by issuing a ctrl-c (control-C) command.
The analysis then can be resumed by the resume command (17.5.54). Several options may be
set to control the simulation (15.1.4).


-----

### 17.5.81 Transpose: Swap the elements in a multi-dimensional data set

General Form:
```
   transpose vector vector ...

```
This command transposes a multidimensional vector. No analysis in ngspice produces multidimensional vectors, although the DC transfer curve may be run with two varying sources. You
must use the reshape command to reform the one-dimensional vectors into two dimensional
vectors. In addition, the default scale is incorrect for plotting. You must plot versus the vector corresponding to the second source, but you must also refer only to the first segment of
this second source vector. For example (circuit to produce the transfer characteristic of a MOS
transistor):

How to produce the transfer characteristic of a MOS transistor:
```
   ngspice > dc vgg 0 5 1 vdd 0 5 1
   ngspice > plot i(vdd)
   ngspice > reshape all [6,6]
   ngspice > transpose i(vdd) v(drain)
   ngspice > plot i(vdd) vs v(drain)[0]

### 17.5.82 Unalias: Retract an alias

```
General Form:
```
   unalias [word ...]

```
Removes any aliases present for the words.

### 17.5.83 Undefine: Retract a definition

General Form:
```
   undefine function

```
Definitions for the named user-defined functions are deleted.

### 17.5.84 Unlet: Delete the specified vector(s)

General Form:
```
   unlet vector [ vector ... ]

```
Delete the specified vector(s). See also let (17.5.35).


-----

### 17.5.85 Unset: Clear a variable

General Form:
```
   unset [word ...]

```
Clear the value of the specified variable(s) (word).

### 17.5.86 Version: Print the version of ngspice

General Form:
```
   version [-s | -f | <version id>]

```
Print out the version of ngnutmeg that is running, if invoked without argument or with -s or -f.
If the argument is a <version id> (any string different from -s or -f is considered a <version id>
), the command checks to make sure that the arguments match the current version of ngspice.
(This is mainly used as a Command: line in rawfiles.)

Options description:

  - No option: The output of the command is the message you can see when running ngspice
from the command line, no more no less.

  - -s(hort): A shorter version of the message you see when calling ngspice from the command line.

  - -f(ull): You may want to use this option if you want to know what extensions are included
into the simulator and what compilation switches are active. A list of compilation options
and included extensions is appended to the normal (not short) message. May be useful
when sending bug reports.

The following example shows what the command returns in some situations:


-----

Use of the version command:
```
   ngspice 10 -> version
   ******
  ** ngspice -24 : Circuit level simulation program
  ** The U. C. Berkeley CAD Group
  ** Copyright 1985-1994, Regents of the University of California.
  ** Please get your ngspice manual from
         http://ngspice.sourceforge.net/docs.html
  ** Please file your bug-reports at
         http://ngspice.sourceforge.net/bugrep.html
  ** Creation Date: Jan 1 2011 13:36:34
   ******
   ngspice 2 ->
   ngspice 11 -> version 14
   Note: rawfile is version 14 (current version is 24)
   ngspice 12 -> version 24
   ngspice 13 ->

```
Note for developers: The option listing returned when version is called with the
```
  -f flag is built at compile time using #ifdef blocks. When new compile switches

```
are added, if you want them to appear on the list, you have to modify the code in
```
  misccoms.c.

### 17.5.87 Where*: Identify troublesome node or device

```
General Form:
```
   where

```
When performing a transient or operating point analysis, the name of the last node or device to
cause non-convergence is saved. The where command prints out this information so that you
can examine the circuit and either correct the problem or generate a bug report. You may do this
either in the middle of a run or after the simulator has given up on the analysis. For transient
simulation, the iplot command can be used to monitor the progress of the analysis. When the
analysis slows down severely or hangs, interrupt the simulator (with control-C) and issue the
```
where command. Note that only one node or device is printed; there may be problems with

```
more than one node.


-----

### 17.5.88 Wrdata: Write data to a file (simple table)

General Form:
```
  <set wr_singlescale >
  <set wr_vecnames >
  <option numdgt=7>
   ...
   wrdata [file] [vecs]

```
Writes out the vectors to file.

This is a very simple printout of data in array form. Variables are written in pairs: scale vector,
value vector. If variable is complex, a triple is printed (scale, real, imag). If more than one
vector is given, the third column again is the default scale, the fourth the data of the second
vector. The default format is ASCII. All vectors have to stem from the same plot, otherwise a
segfault may occur. Setting wr_singlescale as variable, the scale vector will be printed only
once, if scale vectors are of the same length (you have to take care of that yourself). Setting
```
wr_vecnames as variable, scale and data vector names are printed on the first row. The number

```
of significant digits is set with option numdgt.

output example from two vectors:
```
   0.000000e+00 -1.845890e-06 0.000000e+00 0.000000e+00
   7.629471e+06 4.243518e-06 7.629471e+06 -4.930171e-06
   1.525894e+07 -5.794628e-06 1.525894e+07 4.769020e-06
   2.288841e+07 5.086875e-06 2.288841e+07 -3.670687e-06
   3.051788e+07 -3.683623e-06 3.051788e+07 1.754215e-06
   3.814735e+07 1.330798e-06 3.814735e+07 -1.091843e-06
   4.577682e+07 -3.804620e-07 4.577682e+07 2.274678e-06
   5.340630e+07 9.047444e-07 5.340630e+07 -3.815083e-06
   6.103577e+07 -2.792511e-06 6.103577e+07 4.766727e-06
   6.866524e+07 5.657498e-06 6.866524e+07 -2.397679e-06
   ....

```
If variable appendwrite is set, the data may be added to an existing file.

### 17.5.89 Write: Write data to a file (Spice3f5 format)

General Form:
```
   write [file] [exprs]

```
Writes out the expressions to file.

First vectors are grouped together by plots, and written out as such (i.e. if the expression list
contained three vectors from one plot and two from another, then two plots are written, one
with three vectors and one with two). Additionally, if the scale for a vector isn’t present it is
automatically written out as well.


-----

The default format is a compact binary, but this can be changed to ASCII with the set filetype=ascii command. The default file name is either rawspice.raw or the argument of the
optional -r flag on the command line, and the default expression list is all.

If variable appendwrite is set, the data may be added to an existing file.

### 17.5.90 Wrs2p: Write scattering parameters to file (Touchstone® format)

General Form:
```
   wrs2p [file]

```
Writes out the s-parameters of a two-port to file.

In the active plot the following is required: vectors frequency, S11 S12 S21 S22, all having the
same length and complex values (as a result of an ac analysis), and vector Rbase. For details
how to generate these data see Chapt. 17.9.

The file format is Touchstone® Version 1, ASCII, frequency in Hz, real and imaginary parts of
**Snn versus frequency.**

The default file name is s-param.s2p.

output example:
```
  !2-port S-parameter file
  !Title: test for scattering parameters
  !Generated by ngspice at Sat Oct 16 13:51:18 2010
  # Hz S RI R 50
  !freq ReS11 ImS11 ReS21
   ...
   2.500000e+06 -1.358762e-03 -1.726349e-02 9.966563e-01
   5.000000e+06 -5.439573e-03 -3.397117e-02 9.867253e-01 ...

### 17.5.91 Xgraph: use the xgraph(1) program for plotting.

```
General Form:
```
   xgraph file [exprs] [plot options]

```
The ngspice/ngnutmeg xgraph command plots data like the plot command but via xgraph, a
popular X11 plotting program. If file is either temp or tmp a temporary file is used to hold the
data while being plotted. For available plot options, see the plot command. All options except
for polar or smith plots are supported.


-----

## 17.6 Control Structures

### 17.6.1 While - End

General Form:
```
   while condition
   statement
   ...
   end

```
While condition, an arbitrary algebraic expression, is true, execute the statements.

### 17.6.2 Repeat - End

General Form:
```
   repeat [number]
   statement
   ...
   end

```
Execute the statements number times, or forever if no argument is given.

### 17.6.3 Dowhile - End

General Form:
```
   dowhile condition
   statement
   ...
   end

```
The same as while, except that the condition is tested after the statements are executed.

### 17.6.4 Foreach - End

General Form:
```
   foreach var value ...
   statement
   ...
   end

```
The statements are executed once for each of the values, each time with the variable var set to
the current one. (var can be accessed by the $var notation - see below).


-----

### 17.6.5 If - Then - Else

General Form:
```
  if condition
   statement
   ...
   else
   statement
   ...
   end

```
If the condition is non-zero then the first set of statements are executed, otherwise the second
set. The else and the second set of statements may be omitted.

### 17.6.6 Label

General Form:
```
   label word

```
If a statement of the form goto word is encountered, control is transferred to this point, otherwise this is a no-op.

### 17.6.7 Goto

General Form:
```
   goto word

```
If a statement of the form label word is present in the block or an enclosing block, control is
transferred there. Note that if the label is at the top level, it must be before the goto statement
(i.e, a forward goto may occur only within a block). A block to just include goto on the top
level may look like the following example.

Example noop block to include forward goto on top level:
```
  if (1)
   ...
   goto gohere
   ...
   label gohere
   end

```

-----

### 17.6.8 Continue

General Form:
```
   continue

```
If there is a while, dowhile, or foreach block enclosing this statement, control passes to the
test, or in the case of foreach, the next value is taken. Otherwise an error results.

### 17.6.9 Break

General Form:
```
   break

```
If there is a while, dowhile, or foreach block enclosing this statement, control passes out of
the block. Otherwise an error results.

Of course, control structures may be nested. When a block is entered and the input is the
terminal, the prompt becomes a number of >’s corresponding to the number of blocks the user
has entered. The current control structures may be examined with the debugging command
```
cdump (see 17.5.9).

## 17.7 Internally predefined variables

```
The operation of both ngutmeg and ngspice may be affected by setting variables with the set
command (17.5.60). In addition to the variables mentioned below, the set command also
affects the behavior of the simulator via the options previously described under the section
on .OPTIONS (15.1). You also may define new variables or alter existing variables inside
```
.control ... .endc for later use in a user-defined script (see Chapt. 17.8).

```
The following list is in alphabetical order. All of these variables are acknowledged by ngspice.
Frontend variables (e.g. on circuits and simulation) are not defined in ngnutmeg. The predefined
variables that may be set or altered by the set command are:
```
appendwrite Append to the file when a write command is issued, if one already exists.
askquit Check to make sure that there are circuits suspended or plots unsaved. ngspice warns

```
the user when he tries to quit if this is the case.brief If set to FALSE, the netlist will be
printed.
```
batchmode Set by ngspice if run with the -b command line parameter. May be used in input

```
files to suppress plotting if ngspice runs in batch mode.
```
colorN These variables determine the colors used, if X is being run on a color display. N may

```
be between 0 and 15. Color 0 is the background, color 1 is the grid and text color, and
colors 2 through 15 are used in order for vectors plotted. The value of the color variables
should be names of colors, which may be found in the file /usr/lib/rgb.txt. ngspice
for Windows does support only white background (color0=”white” with black grid and
text) or or color0=”black” with white grid and text.


-----

```
cpdebug Print control debugging information.
curplotdate Sets the date of the current plot.
curplotname Sets the name of the current plot.
curplottitle Sets the title (a short description) of the current plot.
debug If set then a lot of debugging information is printed.
device The name (/dev/tty??) of the graphics device. If this variable isn’t set then the

```
user’s terminal is used. To do plotting on another monitor you probably have to set both
the device and term variables. (If device is set to the name of a file, nutmeg dumps the
graphics control codes into this file – this is useful for saving plots.)
```
diff_abstol The relative tolerance used by the diff command (default is 1e-12).
diff_reltol The relative tolerance used by the diff command (default is 0.001).
diff_vntol The absolute tolerance for voltage type vectors used by the diff command (default

```
is 1e-6).
```
echo Print out each command before it is executed.
editor The editor to use for the edit command.
filetype This can be either ascii or binary, and determines the format of the raw file

```
(compact binary or text editor readable ascii). The default is binary.
```
fourgridsize How many points to use for interpolating into when doing Fourier analysis.
gridsize If this variable is set to an integer, this number is used as the number of equally

```
spaced points to use for the Y axis when plotting. Otherwise the current scale is used
(which may not have equally spaced points). If the current scale isn’t strictly monotonic,
then this option has no effect.
```
gridstyle Sets the grid during plotting with the plot command. Will be overridden by direct

```
entry of gridstyle in the plot command. A linear grid is standard for both x and
y axis. Allowed values are lingrid loglog xlog ylog smith smithgrid polar
```
  nogrid.
hcopydev If this is set, when the hardcopy command is run the resulting file is automatically

```
printed on the printer named hcopydev with the command lpr -Phcopydev -g file.
```
hcopyfont This variable specifies the font name for hardcopy output plots. The value is device

```
dependent.
```
hcopyfontsize This is a scaling factor for the font used in hardcopy plots.
hcopydevtype This variable specifies the type of the printer output to use in the hardcopy

```
command. If hcopydevtype is not set, Postscript format is assumed. plot (5) is recognized as an alternative output format. When used in conjunction with hcopydev,
**hcopydevtype should specify a format supported by the printer.**
```
hcopyscale This is a scaling factor for the font used in hardcopy plots (between 0 and 10).

```

-----

```
hcopywidth Sets width of the hardcopy plot.
hcopyheight Sets height of the hardcopy plot.
hcopypscolor Sets the color of the hardcopy output. If not set, black & white plotting is

```
assumed with different linestyles for each output vector. A valid color integer value yields
a colored plot background (0: black 1: white, others see below). and colored solid lines.
This is valid for Postscript only.
```
hcopypstxcolor This variable sets the color of the text in the Postscript hardcopy output. If

```
not set, black on white background is assumed, else it will be white on black background.
Valid colors are 0: black 1: white 2: red 3: blue 4: orange 5: green 6: pink 7: brown 8:
khaki 9: plum 10: orchid 11: violet 12: maroon 13: turquoise 14: sienna 15: coral 16:
cyan 17: magenta 18: gray (for smith grid) 19: gray (for smith grid) 20: gray (for normal
grid).
```
height The length of the page for asciiplot and print col.
history The number of events to save in the history list.
interactive If interactive is set, numparam error handling may be done manually with

```
user input from the console. If not, ngspice will exit upon a numparam error.
```
lprplot5 This is a printf(3s) style format string used to specify the command to use for

```
sending plot(5)-style plots to a printer or plotter. The first parameter supplied is the
printer name, the second parameter is a file name containing the plot. Both parameters
are strings.
```
lprps This is a printf(3s) style format string used to specify the command to use for sen
```
ding Postscript plots to a printer or plotter. The first parameter supplied is the printer
name, the second parameter is the file name containing the plot. Both parameters are
strings.
```
modelcard The name of the model card (normally .MODEL)
moremode If moremode is set, whenever a large amount of data is being printed to the screen

```
(e.g, the print or asciiplot commands), the output is stopped every screenful and
continues when a carriage return is typed. If moremode is unset, then data scrolls off the
screen without pausing.
```
nfreqs The number of frequencies to compute in the Fourier command. (Defaults to 10.)
ngbehavior Sets the compatibility mode of ngspice. Default value is ’all’. To be set in spi
```
nit (16.5) or .spiceinit (16.6). A value of ’all’ improves compatibility with commercial
simulators. Full compatibility is however not the intention of ngspice! The values ’ps’,
```
  ’hs’ and ’spice3’ are available. See Chapt. 16.13.
nobjthack BJTs can have either 3 or 4 nodes, which makes it difficult for the subcircuit ex
```
pansion routines to decide what to rename. If the fourth parameter has been declared as a
model name, then it is assumed that there are 3 nodes, otherwise it is considered a node.
To disable this, you can set the variable nobjthack and force BJTs to have 4 nodes (for
the purposes of subcircuit expansion, at least).


-----

```
nobreak Don’t have asciiplot and print col break between pages.
noasciiplotvalue Don’t print the first vector plotted to the left when doing an asciiplot.
nobjthack Assume that BJTs have 4 nodes.
noclobber Don’t overwrite existing files when doing IO redirection.
noglob Don’t expand the global characters ‘*’, ‘?’, ‘[’, and ‘]’. This is the default.
nonomatch If noglob is unset and a global expression cannot be matched, use the global

```
characters literally instead of complaining.
```
noparse Don’t attempt to parse input files when they are read in (useful for debugging). Of

```
course, they cannot be run if they are not parsed.
```
noprintscale Don’t print the scale in the leftmost column when a print col command is

```
given.
```
nosort Don’t let display sort the variable names.
nosubckt Don’t expand subcircuits.
notrnoise Switch off the transient noise sources (Chapt. 4.1.7).
numdgt The number of digits to use when printing tables of data (print col). The default

```
precision is 6 digits. On the VAX, approximately 16 decimal digits are available using
double precision, so p should not be more than 16. If the number is negative, one fewer
digit is printed to ensure constant widths in tables.
```
num_threads The number of of threads to be used if OpenMP (see Chapt. 16.10) is selected.

```
The default value is 2.
```
outputpath Set the path for all ngspice outputs that are written to files. The directory must

```
exist. Path names with spaces are set in single quotes ’ ’, like set outputpath =
```
  ’C:\My Path’.
plotstyle This should be one of linplot, combplot, or pointplot. linplot, the default,

```
causes points to be plotted as parts of connected lines. combplot causes a comb plot
to be done. It plots vectors by drawing a vertical line from each point to the X-axis, as
opposed to joining the points. pointplot causes each point to be plotted separately.
```
pointchars Set a string as a list of characters to be used as points in a point plot. Standard is

```
‘ox*+#abcdefhgijklmnpqrstuvwyz’. Some characters are forbidden.
```
polydegree The degree of the polynomial that the plot command should fit to the data. If
  polydegree is N, then nutmeg fits a degree N polynomial to every set of N points and

```
draws 10 intermediate points in between each end point. If the points aren’t monotonic,
then nutmeg tries to rotate the curve and reduce the degree until a fit is achieved.
```
polysteps The number of points to interpolate between every pair of points available when

```
doing curve fitting. The default is 10.
```
program The name of the current program (argv[0]).

```

-----

```
prompt The prompt, with the character ‘!’ replaced by the current event number. Single quotes
  ’ ’ are required around the specified string unless you really want it expanded.
rawfile The default name for created rawfiles.
remote_shell Overrides the name used for generating rspice runs (default is rsh).
renumber Renumber input lines when an input file has .includes.
rndseed Seed value for random number generator (used by sgauss, sunif, and rnd functi
```
ons). If not set, the process Id is used as seed value.
```
rhost The machine to use for remote ngspice runs, instead of the default one (see the descrip
```
tion of the rspice command, below).
```
rprogram The name of the remote program to use in the rspice command.
sharedmode Variable is set when ngspice runs in its shared mode (from ngspice.dll or ng
```
spice_xx.so). May be used in universal input files to suppress plotting because a graphics
interface is lacking.
```
sourcepath A list of the directories to search when a source command is given. The default

```
is the current directory and the standard ngspice library (/usr/local/lib/ngspice, or
whatever LIBPATH is #defined to in the ngspice source). The command
```
  set sourcepath = ( e:/ D:/ . c:/spice/examples )

```
will overwrite the default. The search sequence now is: current directory, e:/, d:/, current
directory (again due to .), c:/spice/examples. ’Current directory’ is depending on the
OS.
```
specwindow Windowing for commands spec (17.5.72) or fft (17.5.26). May be one of the

```
following: bartlet blackman cosine gaussian hamming hanning none rectangular
```
  triangle.
specwindoworder Integer value 2 - 8 (default 2), used by commands spec or fft.
spicepath The program to use for the aspice command. The default is /cad/bin/spice.
sqrnoise If set, noise data outputs will be given as V^2/Hz or A^2/Hz, otherwise as the usual
  V/√Hz or A/√Hz.
strict_errorhandling If set by the user, an error detected during circuit parsing will im
```
mediately lead ngspice to exit with exit code 1 (see 18.5). May be set in files spinit (16.5)
or .spiceinit (16.6) only.
```
subend The card to end subcircuits (normally .ends).
subinvoke The prefix to invoke subcircuits (normally X).
substart The card to begin subcircuits (normally .subckt).
term The mfb name of the current terminal.
ticmarks An integer value n, n tics (a small ’x’) will be set on your graph.
ticlist A list of integers, e.g. ( 4 14 24 ) to set tics (small ’x’) on your graph.

```

-----

```
units If this is degrees, then all the trig functions will use degrees instead of radians.
unixcom If a command isn’t defined, try to execute it as a UNIX command. Setting this option

```
has the effect of giving a rehash command, below. This is useful for people who want
to use ngnutmeg as a login shell.
```
wfont Set the font for the graphics plot in MS Windows. Typical fonts are courier, times,
  arial and all others found on your machine. Default is courier.
wfont_size The size of the windows font. The default depends on system settings.
width The width of the page for asciiplot and print col (see also 15.6.7).
win_console is set when ngspice runs in a console under Windows.
x11lineararcs Some X11 implementations have poor arc drawing. If you set this option,

```
ngspice will plot using an approximation to the curve using straight lines.
```
xbrushwidth Linewidth for grid, border and graph.
xfont Set the font for the graphics plot in X11 (Linux, Cygwin, etc.). Input format still has to

```
be checked.
```
xtrtol Set trtol, e.g. to 7, to avoid the default speed reduction (accuracy increase) for

```
XSPICE (see 16.9). Be aware of potential precision degradation or convergence issues
using this option.

## 17.8 Scripts

Expressions, functions, constants, commands, variables, vectors, and control structures may be
assembled into scripts within a .control ... .endc section of the input file. The script allows
to automate any ngspice task: simulations to perform, output data to analyze, repeat simulations
with modified parameters, assemble output plot vectors. The ngspice scripting language is not
very powerful, but well integrated into the simulation flow.

The ngspice script input file contains the usual circuit netlist, modelcards, and the actual script,
enclosed in a .control .. `.endc section. Ngspice is started in interactive mode with the`
input file on the command line (or sourced later with the source command). After reading the
input file the command sequence is immediately processed. Variables or vectors set by previous
commands may be referenced by the commands following them. Data can be stored, plotted or
grouped into new vectors for either plotting or other means of data evaluation.

The input file may contain only the .control .. `.endc section. To notify ngspice about this`
(not mandatory), the script may start with *ng_script in the first line.

### 17.8.1 Variables

Variables are defined and initialized with the set command (17.5). set output=10 defines
the variable output and sets it to the (real) number 10. Predefined variables, which are used
inside ngspice for specific purposes, are listed in Chapt. 17.7. Variables are accessible globally.


-----

The values of variables may be used in commands by writing $varname where the value of
the variable is to appear, e.g. $output. The special variable $$ refers to the process ID of the
program. With $< a line of input is read from the terminal. If a variable is assigned with to
with $&word, then word must be a vector (see below), and word’s numeric value is taken to be
the new value of the variable. If foo is a valid variable, and is of type list, then the expression
```
$foo[low-high] expands to a range of elements. Either the upper or lower index may be left

```
out, and in addition to slicing also reversing of a list is possible through $foo[len-0] (len
is the length of the list, the first valid index is always 1). Furthermore, the notation $?foo
evaluates to 1 if the variable foo is defined, 0 otherwise, and $#foo evaluates to the number of
elements in foo if it is a list, 1 if it is a number or string, and 0 if it is a Boolean variable.

### 17.8.2 Vectors

Ngspice and ngnutmeg data is in the form of vectors: time, voltage, etc. Each vector has a
type, and vectors can be operated on and combined algebraically in ways consistent with their
types. Vectors are normally created as a result of a transient or dc simulation. They are also
established when a data file is read in (see the load command 17.5.38), or they are created
with the let command 17.5.35 inside a script. If a variable x is assigned something of the form
```
$&word, then word has to be a vector, and the numeric value of word is transferred into the

```
variable x.

### 17.8.3 Commands

Commands have been described in Chapt. 17.5.

### 17.8.4 control structures

Control structures have been described in Chapt. 17.6. Some simple examples will be given
below.


-----

Control structure examples:
```
   Test sequences for ngspice control structures
  *vectors are used (except foreach)
  *start in interactive mode
  .control
  * test sequence for while, dowhile
    let loop = 0
    echo
    echo enter loop with "$&loop"
    dowhile loop < 3
     echo within dowhile loop "$&loop"
     let loop = loop + 1
    end
    echo after dowhile loop "$&loop"
    echo
    let loop = 0
    while loop < 3
     echo within while loop "$&loop"
     let loop = loop + 1
    end
    echo after while loop "$&loop"
    let loop = 3
    echo
    echo enter loop with "$&loop"
    dowhile loop < 3
     echo within dowhile loop "$&loop"
  $ output expected
     let loop = loop + 1
    end
    echo after dowhile loop "$&loop"
    echo
    let loop = 3
    while loop < 3
     echo within while loop "$&loop"
  $ no output expected
     let loop = loop + 1
    end
    echo after while loop "$&loop"

```

-----

Control structure examples (continued):
```
  * test for while, repeat, if, break
    let loop = 0
    while loop < 4
     let index = 0
     repeat
      let index = index + 1
      if index > 4
       break
      end
     end
     echo index "$&index" loop "$&loop"
     let loop = loop + 1
    end
  * test sequence for foreach
    echo
    foreach outvar 0 0.5 1 1.5
     echo parameters: $outvar $ foreach parameters are variables,
                     $ not vectors!
    end
  * test for if ... else ... end
    echo
    let loop = 0
    let index = 1
    dowhile loop < 10
     let index = index * 2
     if index < 128
      echo "$&index" lt 128
     else
      echo "$&index" ge 128
     end
     let loop = loop + 1
    end
  * simple test for label, goto
    echo
    let loop = 0
    label starthere
    echo start "$&loop"
    let loop = loop + 1
    if loop < 3
     goto starthere
    end
    echo end "$&loop"

```

-----

Control structure examples (continued):
```
  * test for label, nested goto
    echo
    let loop = 0
    label starthere1
    echo start nested "$&loop"
    let loop = loop + 1
    if loop < 3
     if loop < 3
      goto starthere1
     end
    end
    echo end "$&loop"
  * test for label, goto
    echo
    let index = 0
    label starthere2
    let loop = 0
    echo We are at start with index "$&index" and loop "$&loop"
    if index < 6
     label inhere
     let index = index + 1
     if loop < 3
      let loop = loop + 1
      if index > 1
       echo jump2
       goto starthere2
      end
     end
     echo jump
     goto inhere
    end
    echo We are at end with index "$&index" and loop "$&loop"

```

-----

Control structure examples (continued):
```
  * test goto in while loop
    let loop = 0
    if 1 $ outer loop to allow nested forward label ’endlabel ’
     while loop < 10
      if loop > 5
       echo jump
       goto endlabel
      end
      let loop = loop + 1
     end
     echo before $ never reached
     label endlabel
     echo after "$&loop"
    end
  * test for using variables, simple test for label, goto
    set loop = 0
    label starthe
    echo start $loop
    let loop = $loop + 1 $ expression needs vector at lhs
    set loop = "$&loop" $ convert vector contents to variable
    if $loop < 3
     goto starthe
    end
    echo end $loop
  .endc

### 17.8.5 Example script ’spectrum’

```
A typical example script named spectrum is delivered with the ngspice distribution. Even if
it is made obsolete by the internal spec command (see 17.5.72), and especially by the much
faster fft command (see 17.5.26), it is a good example for getting acquainted with the ngspice
(or nutmeg) post-processor language.

As a suitable input for spectrum you may run a ring-oscillator, delivered with ngspice in e.g.
test/bsim3soi/ring51_41.cir. For an adequate resolution a simulation time of 1µs is needed. A
small control script starts ngspice by loading the R.O. simulation data and executing spectrum.

Small script to start ngspice, read the simulation data and start spectrum:
```
  * test for script ’spectrum ’
  .control
   load ring51_41.out
   spectrum 10MEG 2500MEG 1MEG v(out25) v(out50)
  .endc

```

-----

-----

### 17.8.6 Example script for random numbers

Generation and test of random numbers with Gaussian distribution
```
  * agauss test in ngspice
  * generate a sequence of gaussian distributed random numbers.
  * test the distribution by sorting the numbers into
  * a histogram (buckets)
  .control
    define agauss(nom, avar, sig) (nom + avar/sig * sgauss(0))
    let mc_runs = 200
    let run = 0
    let no_buck = 8 $ number of buckets
    let bucket = unitvec(no_buck) $ each element contains 1
    let delta = 3e-11 $ width of each bucket, depends
                $ on avar and sig
    let lolimit = 1e-09 - 3*delta
    let hilimit = 1e-09 + 3*delta
    dowhile run < mc_runs
     let val = agauss(1e-09, 1e-10, 3) $ get the random number
     if (val < lolimit)
       let bucket[0] = bucket[0] + 1 $ ’lowest’ bucket
     end
     let part = 1
     dowhile part < (no_buck - 1)
      if ((val < (lolimit + part*delta)) &
  + (val > (lolimit + (part -1)*delta)))
       let bucket[part] = bucket[part] + 1
            break
      end
      let part = part + 1
     end
     if (val > hilimit)
  * ’highest ’ bucket
      let bucket[no_buck - 1] = bucket[no_buck - 1] + 1
     end
     let run = run + 1
    end
    let part = 0
    dowhile part < no_buck
     let value = bucket[part] - 1
     set value = "$&value"
  * print the bucket ’s contents
     echo $value
     let part = part + 1
    end
  .endc
  .end

```

-----

### 17.8.7 Parameter sweep

While there is no direct command to sweep a device parameter during simulation, you may use
a script to emulate such behavior. The example input file contains of an resistive divider with
R1 and R2, where R1 is swept from a start to a stop value inside of the control section, using
the alter command (see 17.5.3).

Input file with parameter sweep
```
   parameter sweep
  * resistive divider, R1 swept from start_r to stop_r
   VDD 1 0 DC 1
  R1 1 2 1k
  R2 2 0 1k
  .control
   let start_r = 1k
   let stop_r = 10k
   let delta_r = 1k
   let r_act = start_r
  * loop
   while r_act le stop_r
    alter r1 r_act
    op
    print v(2)
    let r_act = r_act + delta_r
   end
  .endc
  .end

### 17.8.8 Output redirection

```
The console outputs delivered by commands like print (17.5.47), echo (17.5.21), or others may
be redirected into a text file. ’print vec > filename’ will generate a new file or overwrite
an existing file named ’filename’, ’echo text >> filename’ will append the new data to
the file ’filename’. Output redirection may be mixed with commands like wrdata.


-----

Input file with output redirection > and >>
```
  ** MOSFET Gain Stage (AC):
  ** Benchmarking Implementation of BSIM4.0.0
  ** by Weidong Liu 5/16/2000.
  ** output redirection into file
  M1 3 2 0 0 N1 L=1u W=4u
   Rsource 1 2 100k
   Rload 3 vdd 25k
   Vdd vdd 0 1.8
   Vin 1 0 1.2 ac 0.1
  .control
  ac dec 10 100 1000Meg
   plot v(2) v(3)
   let flen = length(frequency) $ length of the vector
   let loopcounter = 0
   echo output test > text.txt $ start new file test.txt
  * loop
   while loopcounter lt flen
    let vout2 = v(2)[loopcounter] $ generate a single point
                      $ complex vector
    let vout2re = real(vout2) $ generate a single point
                      $ real vector
    let vout2im = imag(vout2) $ generate a single point
                      $ imaginary vector
    let vout3 = v(3)[loopcounter] $ generate a single
                      $ point complex vector
    let vout3re = real(vout3) $ generate a single point
                      $ real vector
    let vout3im = imag(vout3) $ generate a single point
                      $ imaginary vector
    let freq = frequency[loopcounter] $ generate a single point vector
    echo bbb "$&freq" "$&vout2re" "$&vout2im"
  + "$&vout3re" "$&vout3im" >> text.txt
                      $ append text and
                      $ data to file
                      $ (continued from line above)
    let loopcounter = loopcounter + 1
   end
  .endc
  .MODEL N1 NMOS LEVEL=14 VERSION=4.8.1 TNOM=27
  .end

```

-----

## 17.9 Scattering parameters (s-parameters)

### 17.9.1 Intro

A command line script, available from the ngspice distribution at examples/control_structs/sparam.cir, together with the command wrs2p (see Chapt. 17.5.90) allows to calculate, print
and plot the scattering parameters S11, S21, S12, and S22 of any two port circuit at varying
frequencies.

The printed output using wrs2p is a Touchstone® version 1 format file. The file follows the
[format according to The Touchstone File Format Specification, Version 2.0, available from here.](http://www.eda.org/ibis/touchstone_ver2.0/)
An example is given as number 13 on page 15 of that specification.

### 17.9.2 S-parameter measurement basics

S-parameters allow a two-port description not just by permuting I1, U1, I2, U2, but using a
superposition, leading to a power view of the port (We only look at two-ports here, because
multi-ports are not (yet?) implemented.).

You may start with the effective power, being negative or positive

_P = u_ _i_ (17.1)

_·_

The value of P may be the difference of two real numbers, with K being another real number.

_ui = P = a[2]_ _b[2]_ = (a+b)(a _b) = (a+b)(KK[−][1])(a_ _b) =_ _K(a_ + _b)_ �K[−][1](a _b)�_ (17.2)
_−_ _−_ _−_ _{_ _}_ _−_

Thus you get

_K[−][1]u = a_ + _b_ (17.3)

_Ki = a_ _b_ (17.4)
_−_

and finally

_a =_ _[u]_ [+] _[K][2][i]_ (17.5)

2K


_b =_ _[u]_ _[−]_ _[K][2][i]_ (17.6)

2K

By introducing the reference resistance Z0 := K[2] _> 0 we get finally the Heaviside transformation_

_a =_ _[u]_ [+] _[Z][0][i]_ _,_ _b =_ _[u]_ _[−]_ _[Z][0][i]_ (17.7)

2[√]Z0 2[√]Z0


-----

In case of our two-port we subject our variables to a Heaviside transformation

_a1 =_ _[U][1][ +]_ _[Z][0][I][1]_ _b1 =_ _[U][1][ −]_ _[Z][0][I][1]_ (17.8)

2[√]Z0 2[√]Z0


_a2 =_ _[U][2][ +]_ _[Z][0][I][2]_ _b2 =_ _[U][2][ −]_ _[Z][0][I][2]_ (17.9)

2[√]Z0 2[√]Z0


The s-matrix for a two-port then is

� _b1_
_b2_


�
(17.10)


� � _s11_ _s12_
=
_s21_ _s22_


�� _a1_
_a2_


Two obtain s11 we have to set a2 = 0. This is accomplished by loading the output port exactly
with the reference resistance Z0, which sinks a current I2 = −U2/Z0 from the port.


� _b1_
_s11 =_

_a1_


�


(17.11)
_a2=0_


_s11 =_ _[U][1][ −]_ _[Z][0][I][1]_ (17.12)

_U1 +_ _Z0I1_


Loading the input port from an ac source U0 via a resistor with resistance value Z0, we obtain
the relation

_U0 = Z0I1 +U1_ (17.13)

Entering this into 17.12, we get

_s11 =_ [2][U][1][ −][U][0] (17.14)

_U0_


For s21 we obtain similarly


� _b2_
_s21 =_

_a1_


�


(17.15)
_a2=0_


_s21 =_ _[U][2][ −]_ _[Z][0][I][2]_ = [2][U][2] (17.16)

_U1 +_ _Z0I1_ _U0_

Equations 17.14 and 17.16 now tell us how to measure s11 and s21: Measure U1 at the input port,
multiply by 2 using an E source, subtracting U0, which for simplicity is set to 1, and divide by
_U0. At the same time measure U2 at the output port, multiply by 2 and divide by U0. Biasing and_
measuring is done by subcircuit S_PARAM. To obtain s22 and s12, you have to exchange the
input and output ports of your two-port and do the same measurement again. This is achieved
by switching resistors from low (1mΩ) to high (1T Ω) and thus switching the input and output
ports.


-----

### 17.9.3 Usage

Copy and then edit s-param.cir. You will find this file in directory /examples/control_structs
of the ngspice distribution.

The reference resistance (often called characteristic impedance) for the measurements is added
as a parameter
```
.param Rbase=50

```
The bias voltages at the input and output ports of the circuit are set as parameters as well:
```
.param Vbias_in=1 Vbias_out=2

```
Place your circuit at the appropriate place in the input file, e.g. replacing the existing example
circuits. The input port of your circuit has two nodes in, 0. The output port has the two nodes
**out, 0. The bias voltages are connected to your circuit via the resistances of value Rbase at the**
input and output respectively. This may be of importance for the operating point calculations if
your circuit draws a large dc current.

Now edit the ac commands (see 17.5.1) according to the circuit provided, e.g.
```
ac lin 100 2.5MEG 250MEG $ use for Tschebyschef

```
Be careful to keep both ac lines in the .control ... .endc section the same and only change
both in equal measure!

Select the plot commands (lin/log, or smithgrid) or the ’write to file’ commands (write,
```
wrdata, or wrs2p) according to your needs.

```
Run ngspice in interactive mode
```
ngspice s-param.cir

## 17.10 MISCELLANEOUS

```
C-shell type quoting with ’ and ’, and backquote substitution may be used. Within single
quotes, no further substitution (like history substitution) is done, and within double quotes,
the words are kept together but further substitution is done. Any text between backquotes is
replaced by the result of executing the text as a command to the shell.
```
History substitutions, similar to C-shell history substitutions, are also available - see the

```
C-shell manual page for all of the details. The characters ~, @{, and @} have the same effects
as they do in the C-Shell, i.e., home directory and alternative expansion. It is possible to use the
wildcard characters *, ?, [, and ] also, but only if you unset noglob first. This makes them rather
useless for typing algebraic expressions, so you should set noglob again after you are done with
wildcard expansion. Note that the pattern [^abc] matches all characters except a, b, and c.

If X is being used, the cursor may be positioned at any point on the screen when the window
is up and characters typed at the keyboard are added to the window at that point. The window
may then be sent to a printer using the xpr(1) program.


-----

## 17.11 Bugs

When defining aliases like alias pdb plot db( !:1 - !:2 ) you must be careful to quote the
argument list substitutions in this manner. If you quote the whole argument it might not work
properly.

In a user-defined function, the arguments cannot be part of a name that uses the plot.vec syntax.
For example: define check(v(1)) cos(tran1.v(1)) does not work.


-----

