# Chapter 2

 Circuit Description

## 2.1 General Structure and Conventions

### 2.1.1 Input file structure

The circuit to be analyzed is described to ngspice by a set of element instance lines, which
define the circuit topology and element instance values, and a set of control lines, which define
the model parameters and the run controls. All lines are assembled in an input file to be read by
ngspice. Two lines are essential:

  - The first line in the input file must be the title, which is the only comment line that does
not need any special character in the first place.

  - The last line must be .end.

The order of the remaining lines is arbitrary (except, of course, that continuation lines must
immediately follow the line being continued). This feature in the ngspice input language dates back to the punched card times where elements were written on separate cards (and cards
frequently fell off). Leading white spaces in a line are ignored, as well as empty lines.

The lines described in sections 2.1 to 2.12 are typically used in the core of the input file, outside
of a .control section (see 16.4.3). An exception is the .include includefile line (2.6)
that may be placed anywhere in the input file. The contents of includefile will be inserted
exactly in place of the .include line.

### 2.1.2 Circuit elements (device instances)

Each element in the circuit is a device instance specified by an instance line that contains:

  - the element instance name,

  - the circuit nodes to which the element is connected,

  - and the values of the parameters that determine the electrical characteristics of the element.


-----

The first letter of the element instance name specifies the element type. The format for the
ngspice element types is given in the following manual chapters. In the rest of the manual, the
strings XXXXXXX, YYYYYYY, and ZZZZZZZ denote arbitrary alphanumeric strings.

For example, a resistor instance name must begin with the letter R and can contain one or more
characters. Hence, R, R1, RSE, ROUT, and R3AC2ZY are valid resistor names. Details of each
type of device are supplied in a following section 3. Table 2.1 lists the element types available
in ngspice, sorted by their first letter.

First letter Element description Comments, links

12

analog (12.2)

A XSPICE code model

digital (12.4)
mixed signal (12.3)

B Behavioral (arbitrary) source 5.1

C Capacitor 3.2.5

D Diode 7

linear (4.2.2),
E Voltage-controlled voltage source (VCVS)
non-linear (5.2)

F Current-controlled current source (CCCs) linear (4.2.3)

linear (4.2.1),
G Voltage-controlled current source (VCCS)
non-linear (5.3)

H Current-controlled voltage source (CCVS) linear (4.2.4)

I Current source 4.1

J Junction field effect transistor (JFET) 9

K Coupled (Mutual) Inductors 3.2.11

L Inductor 3.2.9

11

M Metal oxide field effect transistor (MOSFET) BSIM3 (11.2.10)

BSIM4 (11.2.11)

N Numerical device for GSS 14.2

O Lossy transmission line 6.2

P Coupled multiconductor line (CPL) 6.4.2

Q Bipolar junction transistor (BJT) 8

R Resistor 3.2.1

S Switch (voltage-controlled) 3.2.14

T Lossless transmission line 6.1

U Uniformly distributed RC line 6.3

V Voltage source 4.1

W Switch (current-controlled) 3.2.14

X Subcircuit 2.4.3

Y Single lossy transmission line (TXL) 6.4.1

Z Metal semiconductor field effect transistor (MESFET) 10

Table 2.1: ngspice element types

|First letter|Element description|Comments, links|
|---|---|---|
|A|XSPICE code model|12 analog (12.2) digital (12.4) mixed signal (12.3)|
|B|Behavioral (arbitrary) source|5.1|
|C|Capacitor|3.2.5|
|D|Diode|7|
|E|Voltage-controlled voltage source (VCVS)|linear (4.2.2), non-linear (5.2)|
|F|Current-controlled current source (CCCs)|linear (4.2.3)|
|G|Voltage-controlled current source (VCCS)|linear (4.2.1), non-linear (5.3)|
|H|Current-controlled voltage source (CCVS)|linear (4.2.4)|
|I|Current source|4.1|
|J|Junction field effect transistor (JFET)|9|
|K|Coupled (Mutual) Inductors|3.2.11|
|L|Inductor|3.2.9|
|M|Metal oxide field effect transistor (MOSFET)|11 BSIM3 (11.2.10) BSIM4 (11.2.11)|
|N|Numerical device for GSS|14.2|
|O|Lossy transmission line|6.2|
|P|Coupled multiconductor line (CPL)|6.4.2|
|Q|Bipolar junction transistor (BJT)|8|
|R|Resistor|3.2.1|
|S|Switch (voltage-controlled)|3.2.14|
|T|Lossless transmission line|6.1|
|U|Uniformly distributed RC line|6.3|
|V|Voltage source|4.1|
|W|Switch (current-controlled)|3.2.14|
|X|Subcircuit|2.4.3|
|Y|Single lossy transmission line (TXL)|6.4.1|
|Z|Metal semiconductor field effect transistor (MESFET)|10|


-----

### 2.1.3 Some naming conventions

Fields on a line are separated by one or more blanks, a comma, an equal (=) sign, or a left or
right parenthesis; extra spaces are ignored. A line may be continued by entering a ‘+’ (plus) in
column 1 of the following line; ngspice continues reading beginning with column 2. A name
field must begin with a letter (A through Z) and cannot contain any delimiters. A number field
may be an integer field (12, -44), a floating point field (3.14159), either an integer or floating
point number followed by an integer exponent (1e-14, 2.65e3), or either an integer or a floating
point number followed by one of the following scale factors:

Suffix Name Factor

T Tera 10[12]

G Giga 10[9]

Meg Mega 10[6]

K Kilo 10[3]

mil Mil 25.4 10[−][6]
_×_

m milli 10[−][3]

u micro 10[−][6]

n nano 10[−][9]

p pico 10[−][12]

f femto 10[−][15]

Table 2.2: Ngspice scale factors

Letters immediately following a number that are not scale factors are ignored, and letters immediately following a scale factor are ignored. Hence, 10, 10V, 10Volts, and 10Hz all represent
the same number, and M, MA, MSec, and MMhos all represent the same scale factor. Note that
1000, 1000.0, 1000Hz, 1e3, 1.0e3, 1kHz, and 1k all represent the same number. Note that ‘M’
or ‘m’ denote ‘milli’, i.e. 10[−][3]. Suffix meg has to be used for 10[6].

Nodes names may be arbitrary character strings and are case insensitive, if ngspice is used in
batch mode (16.4.1). If in interactive (16.4.2) or control (16.4.3) mode, node names may either
be plain numbers or arbitrary character strings, not starting with a number. The ground node
must be named ‘0’ (zero). For compatibility reason gnd is accepted as ground node, and will
internally be treated as a global node and be converted to ‘0’. Each circuit has to have a ground
_node (gnd or 0)! Note the difference in ngspice where the nodes are treated as character strings_
and not evaluated as numbers, thus ‘0’ and 00 are distinct nodes in ngspice but not in SPICE2.

Ngspice requires that the following topological constraints are satisfied:

  - The circuit cannot contain a loop of voltage sources and/or inductors and cannot contain
a cut-set of current sources and/or capacitors.

  - Each node in the circuit must have a dc path to ground.

  - Every node must have at least two connections except for transmission line nodes (to
permit unterminated transmission lines) and MOSFET substrate nodes (which have two
internal connections anyway).

|Suffix|Name|Factor|
|---|---|---|
|T|Tera|1012|
|G|Giga|109|
|Meg|Mega|106|
|K|Kilo|103|
|mil|Mil|25.4 10−6 ×|
|m|milli|10−3|
|u|micro|10−6|
|n|nano|10−9|
|p|pico|10−12|
|f|femto|10−15|


-----

## 2.2 Basic lines

### 2.2.1 .TITLE line

Examples:
```
   POWER AMPLIFIER CIRCUIT
  * additional lines following
   *...
   Test of CAM cell
  * additional lines following
   *...

```
The title line must be the first in the input file. Its contents are printed verbatim as the heading
for each section of output.

As an alternative you may place a .TITLE <any title> line anywhere in your input deck.
The first line of your input deck will be overridden by the contents of this line following the
.TITLE statement.

.TITLE line example:
```
   ******************************
  * additional lines following
   *...
  .TITLE Test of CAM cell
  * additional lines following
   *...

```
will internally be replaced by

Internal input deck:
```
   Test of CAM cell
  * additional lines following
   *...
  *TITLE Test of CAM cell
  * additional lines following
   *...

### 2.2.2 .END Line

```
Examples:
```
  .end

```
The .end line must always be the last in the input file. Note that the period is an integral part
of the name.


-----

### 2.2.3 Comments

General Form:
```
  * <any comment >

```
Examples:
```
  * RF=1K Gain should be 100
  * Check open-loop gain and phase margin

```
The asterisk in the first column indicates that this line is a comment line. Comment lines may
be placed anywhere in the circuit description.

### 2.2.4 End-of-line comments

General Form:
```
  <any command > $ <any comment >

```
Examples:
```
   RF2=1K $ Gain should be 100
  C1=10p $ Check open-loop gain and phase margin
  .param n1=1 //new value

```
ngspice supports comments that begin with double characters ‘$ ’ (dollar plus space) or ‘//’.
For readability you should precede each comment character with a space. ngspice will accept
the single character ‘$’.

Please note that in .control sections the ‘;’ character means ‘continuation’ and can be used
to put more than one statement on a line.

## 2.3 .MODEL Device Models

General form:
```
  .model mname type(pname1=pval1 pname2=pval2 ... )

```
Examples:
```
  .model MOD1 npn (bf=50 is=1e-13 vbf=50)

```

-----

|Code|Model Type|
|---|---|
|R|Semiconductor resistor model|
|C|Semiconductor capacitor model|
|L|Inductor model|
|SW|Voltage controlled switch|
|CSW|Current controlled switch|
|URC|Uniform distributed RC model|
|LTRA|Lossy transmission line model|
|D|Diode model|
|NPN|NPN BJT model|
|PNP|PNP BJT model|
|NJF|N-channel JFET model|
|PJF|P-channel JFET model|
|NMOS|N-channel MOSFET model|
|PMOS|P-channel MOSFET model|
|NMF|N-channel MESFET model|
|PMF|P-channel MESFET model|


Table 2.3: Ngspice model types

Most simple circuit elements typically require only a few parameter values. However, some devices (semiconductor devices in particular) that are included in ngspice require many parameter
values. Often, many devices in a circuit are defined by the same set of device model parameters.
For these reasons, a set of device model parameters is defined on a separate .model line and
assigned a unique model name. The device element lines in ngspice then refer to the model
name.

For these more complex device types, each device element line contains the device name, the
nodes the device is connected to, and the device model name. In addition, other optional parameters may be specified for some devices: geometric factors and an initial condition (see the
following section on Transistors (8 to 11) and Diodes (7) for more details). mname in the above
is the model name, and type is one of the following fifteen types:

Parameter values are defined by appending the parameter name followed by an equal sign and
the parameter value. Model parameters that are not given a value are assigned the default values
given below for each model type. Models are listed in the section on each device along with
the description of device element lines. Model parameters and their default values are given in
Chapt. 31.

## 2.4 .SUBCKT Subcircuits

A subcircuit that consists of ngspice elements can be defined and referenced in a fashion similar
to device models. Subcircuits are the way ngspice implements hierarchical modeling, but this is
not entirely true because each subcircuit instance is flattened during parsing, and thus ngspice
is not a hierarchical simulator.

The subcircuit is defined in the input deck by a grouping of element cards delimited by the
```
.subckt and the .ends cards (or the keywords defined by the substart and subend options

```

-----

(see 17.7)); the program then automatically inserts the defined group of elements wherever the
subcircuit is referenced. Instances of subcircuits within a larger circuit are defined through the
use of an instance card that begins with the letter ‘X’. A complete example of all three of these
cards follows:

Example:
```
  * The following is the instance card:
  *
   xdiv1 10 7 0 vdivide
  * The following are the subcircuit definition cards:
  *
  .subckt vdivide 1 2 3
  r1 1 2 10K
  r2 2 3 5K
  .ends

```
The above specifies a subcircuit with ports numbered ‘1’, ‘2’ and ‘3’:

  - Resistor ‘R1’ is connected from port ‘1’ to port ‘2’, and has value 10 kOhms.

  - Resistor ‘R2’ is connected from port ‘2’ to port ‘3’, and has value 5 kOhms.

The instance card, when placed in an ngspice deck, will cause subcircuit port ‘1’ to be equated
to circuit node ‘10’, while port ‘2’ will be equated to node ‘7’ and port ‘3’ will equated to node
‘0’.

There is no limit on the size or complexity of subcircuits, and subcircuits may contain other
subcircuits. An example of subcircuit usage is given in Chapt. 21.6.

### 2.4.1 .SUBCKT Line

General form:
```
  .SUBCKT subnam N1 <N2 N3 ...>

```
Examples:
```
  .SUBCKT OPAMP 1 2 3 4

```
A circuit definition is begun with a .SUBCKT line. subnam is the subcircuit name, and N1, N2,
... are the external nodes, which cannot be zero. The group of element lines that immediately
follow the .SUBCKT line define the subcircuit. The last line in a subcircuit definition is the
```
.ENDS line (see below). Control lines may not appear within a subcircuit definition; however,

```
subcircuit definitions may contain anything else, including other subcircuit definitions, device
models, and subcircuit calls (see below). Note that any device models or subcircuit definitions
included as part of a subcircuit definition are strictly local (i.e., such models and definitions


-----

are not known outside the subcircuit definition). Also, any element nodes not included on the
```
.SUBCKT line are strictly local, with the exception of 0 (ground) that is always global. If you

```
use parameters, the .SUBCKT line will be extended (see 2.8.3).

### 2.4.2 .ENDS Line

General form:
```
  .ENDS <SUBNAM >

```
Examples:
```
  .ENDS OPAMP

```
The .ENDS line must be the last one for any subcircuit definition. The subcircuit name, if
included, indicates which subcircuit definition is being terminated; if omitted, all subcircuits
being defined are terminated. The name is needed only when nested subcircuit definitions are
being made.

### 2.4.3 Subcircuit Calls

General form:
```
   XYYYYYYY N1 <N2 N3 ...> SUBNAM

```
Examples:
```
  X1 2 4 17 3 1 MULTI

```
Subcircuits are used in ngspice by specifying pseudo-elements beginning with the letter X,
followed by the circuit nodes to be used in expanding the subcircuit. If you use parameters, the
subcircuit call will be modified (see 2.8.3).

## 2.5 .GLOBAL

General form:
```
  .GLOBAL nodename

```
Examples:
```
  .GLOBAL gnd vcc

```

-----

Nodes defined in the .GLOBAL statement are available to all circuit and subcircuit blocks independently from any circuit hierarchy. After parsing the circuit, these nodes are accessible from
top level.

## 2.6 .INCLUDE

General form:
```
  .INCLUDE filename

```
Examples:
```
  .INCLUDE /users/spice/common/bsim3-param.mod

```
Frequently, portions of circuit descriptions will be reused in several input files, particularly with
common models and subcircuits. In any ngspice input file, the .INCLUDE line may be used to
copy some other file as if that second file appeared in place of the .INCLUDE line in the original
file.

There is no restriction on the file name imposed by ngspice beyond those imposed by the local
operating system.

## 2.7 .LIB

General form:
```
  .LIB filename libname

```
Examples:
```
  .LIB /users/spice/common/mosfets.lib mos1

```
The .LIB statement allows to include library descriptions into the input file. Inside the *.lib
file a library libname will be selected. The statements of each library inside the *.lib file are
enclosed in .LIB libname <...> .ENDL statements.

If the compatibility mode (16.13) is set to ’ps’ by set ngbehavior=ps (17.7) in spinit (16.5)
or .spiceinit (16.6), then a simplified syntax .LIB filename is available: a warning is issued
and filename is simply included as described in Chapt. 2.6.

## 2.8 .PARAM Parametric netlists

Ngspice allows for the definition of parametric attributes in the netlists. This is an enhancement
of the ngspice front-end that adds arithmetic functionality to the circuit description language.


-----

### 2.8.1 .param line

General form:
```
  .param <ident> = <expr> <ident> = <expr> ...

```
Examples:
```
  .param pippo=5
  .param po=6 pp=7.8 pap={AGAUSS(pippo, 1, 1.67)}
  .param pippp={pippo + pp}
  .param p={pp}
  .param pop=’pp+p’

```
This line assigns numerical values to identifiers. More than one assignment per line is possible
using a separating space. Parameter identifier names must begin with an alphabetic character.
The other characters must be either alphabetic, a number, or ! `# $ % [ ] _ as special cha-`
racters. The variables time, temper, and hertz (see 5.1.1) are not valid identifier names. Other
restrictions on naming conventions apply as well, see 2.8.6.

The .param lines inside subcircuits are copied per call, like any other line. All assignments
are executed sequentially through the expanded circuit. Before its first use, a parameter name
must have been assigned a value. Expressions defining a parameter should be put within braces
```
{p+p2}, or alternatively within single quotes ’AGAUSS(pippo, 1, 1.67)’. An assignment

```
cannot be self-referential, something like .param pip = ’pip+3’ will not work.

The current ngspice version does not always need quotes or braces in expressions, especially
when spaces are used sparingly. However, it is recommended to do so, as the following examples demonstrate.
```
  .param a = 123 * 3 b = sqrt(9) $ doesn’t work, a <= 123
  .param a = ’123 * 3’ b = sqrt(9) $ ok.
  .param c = a + 123 $ won’t work
  .param c = ’a + 123’ $ ok.
  .param c = a+123 $ ok.

### 2.8.2 Brace expressions in circuit elements:

```
General form:
```
  { <expr> }

```
Examples:

These are allowed in .model lines and in device lines. A SPICE number is a floating point
number with an optional scaling suffix, immediately glued to the numeric tokens (see Chapt.
2.8.5). Brace expressions ({..}) cannot be used to parametrize node names or parts of names.


-----

All identifiers used within an <expr> must have known values at the time when the line is
evaluated, else an error is flagged.

### 2.8.3 Subcircuit parameters

General form:
```
  .subckt <identn> node node ... <ident >=<value> <ident >=<value> ...

```
Examples:
```
  .subckt myfilter in out rval=100k cval=100nF
<identn> is the name of the subcircuit given by the user. node is an integer number or an

```
identifier, for one of the external nodes. The first <ident>=<value> introduces an optional
section of the line. Each <ident> is a formal parameter, and each <value> is either a SPICE
number or a brace expression. Inside the .subckt ... .ends context, each formal parameter
may be used like any identifier that was defined on a .param control line. The <value> parts
are supposed to be default values of the parameters. However, in the current version of, they
are not used and each invocation of the subcircuit must supply the _exact_ number of actual
parameters.

The syntax of a subcircuit call (invocation) is:

General form:
```
  X<name> node node ... <identn> <ident >=<value> <ident >=<value> ...

```
Examples:
```
  X1 input output myfilter rval=1k cval=1n

```
Here <name> is the symbolic name given to that instance of the subcircuit, <identn> is the
name of a subcircuit defined beforehand. node node ... is the list of actual nodes where the
subcircuit is connected. <value> is either a SPICE number or a brace expression { <expr> }
. The sequence of <value> items on the X line must exactly match the number and the order of
formal parameters of the subcircuit.


-----

Subcircuit example with parameters:
```
  * Param-example
  .param amplitude= 1V
  *
  .subckt myfilter in out rval=100k cval=100nF
  Ra in p1 {2*rval}
  Rb p1 out {2*rval}
  C1 p1 0 {2*cval}
  Ca in p2 {cval}
  Cb p2 out {cval}
  R1 p2 0 {rval}
  .ends myfilter
  *
  X1 input output myfilter rval=1k cval=1n
  V1 input 0 AC {amplitude}
  .end

### 2.8.4 Symbol scope

```
_All subcircuit and model names are considered global and must be unique. The .param symbols_
that are defined outside of any .subckt ... .ends section are global. Inside such a section, the
pertaining params: symbols and any .param assignments are considered local: they mask any
global identical names, until the .ends line is encountered. You cannot reassign to a global
number inside a .subckt, a local copy is created instead. Scope nesting works up to a level of
10. For example, if the main circuit calls A that has a formal parameter xx, A calls B that has a
param. xx, and B calls C that also has a formal param. xx, there will be three versions of ‘xx’
in the symbol table but only the most local one - belonging to C - is visible.

### 2.8.5 Syntax of expressions
```
  <expr> ( optional parts within [...] )

```
An expression may be one of:
```
  <atom> where <atom> is either a spice number or an identifier
  <unary-operator > <atom>
  <function -name> ( <expr> [, <expr> ...] )
  <atom> <binary-operator > <expr>
  ( <expr> )

```
As expected, atoms, built-in function calls and stuff within parentheses are evaluated before
the other operators. The operators are evaluated following a list of precedence close to the one
of the C language. For equal precedence binary ops, evaluation goes left to right. Functions
operate on real values only!


-----

|Operator|Alias|Precedence|Description|
|---|---|---|---|
|-||1|unary -|
|!||1|unary not|
|**|^|2|power, like pwr|
|*||3|multiply|
|/||3|divide|
|%||3|modulo|
|\||3|integer divide|
|+||4|add|
|-||4|subtract|
|==||5|equality|
|!=|<>|5|non-equal|
|<=||5|less or equal|
|>=||5|greater or equal|
|<||5|less than|
|>||5|greater than|
|&&||6|boolean and|
|||||7|boolean or|
|c?x:y||8|ternary operator|


The number zero is used to represent boolean False. Any other number represents boolean True.
The result of logical operators is 1 or 0. An example input file is shown below:

Example input file with logical operators:
```
  * Logical operators
   v1or 1 0 {1 || 0}
   v1and 2 0 {1 && 0}
   v1not 3 0 {! 1}
   v1mod 4 0 {5 % 3}
   v1div 5 0 {5 \ 3}
   v0not 6 0 {! 0}
  .control
  op
   print allv
  .endc
  .end

```

-----

|Built-in function|Notes|
|---|---|
|sqr(x)|y = x * x|
|sqrt(x)|y = sqrt(x)|
|sin(x), cos(x), tan(x)||
|sinh(x), cosh(x), tanh(x)||
|asin(x), acos(x), atan(x)||
|asinh(x), acosh(x), atanh(x)||
|arctan(x)|atan(x), kept for compatibility|
|exp(x)||
|ln(x), log(x)||
|abs(x)||
|nint(x)|Nearest integer, half integers towards even|
|int(x)|Nearest integer rounded towards 0|
|floor(x)|Nearest integer rounded towards -∞|
|ceil(x)|Nearest integer rounded towards +∞|
|pow(x,y)|x raised to the power of y (pow from C runtime library)|
|pwr(x,y)|pow(fabs(x), y)|
|min(x, y)||
|max(x, y)||
|sgn(x)|1.0 for x > 0, 0.0 for x == 0, -1.0 for x < 0|
|ternary_fcn(x, y, z)|x ? y : z|
|gauss(nom, rvar, sigma)|nominal value plus variation drawn from Gaussian distribution with mean 0 and standard deviation rvar (relative to nominal), divided by sigma|
|agauss(nom, avar, sigma)|nominal value plus variation drawn from Gaussian distribution with mean 0 and standard deviation avar (absolute), divided by sigma|
|unif(nom, rvar)|nominal value plus relative variation (to nominal) uniformly distributed between +/-rvar|
|aunif(nom, avar)|nominal value plus absolute variation uniformly distributed between +/-avar|
|limit(nom, avar)|nominal value +/-avar, depending on random number in [-1, 1[ being > 0 or < 0|


The scaling suffixes (any decorative alphanumeric string may follow):

suffix value

g 1e9

meg 1e6

k 1e3

m 1e-3

u 1e-6

n 1e-9

p 1e-12

f 1e-15

Note: there are intentional redundancies in expression syntax, e.g. x^y, x**y and pwr(x,y)
all have nearly the same result.

|suffix|value|
|---|---|
|g|1e9|
|meg|1e6|
|k|1e3|
|m|1e-3|
|u|1e-6|
|n|1e-9|
|p|1e-12|
|f|1e-15|


-----

### 2.8.6 Reserved words

In addition to the above function names and to the verbose operators ( not and or div mod
), other words are reserved and cannot be used as parameter names: or, defined, sqr, sqrt,
```
sin, cos, exp, ln, log, log10, arctan, abs, pwr, time, temper, hertz.

### 2.8.7 Alternative syntax

```
The & sign is tolerated to provide some ‘historical’ parameter notation: & as the first character
of a line is equivalent to: .param.

Inside a line, the notation &(....) is equivalent to {....}, and &identifier means the same
thing as {identifier} .

Comments in the style of C++ line trailers (//) are detected and erased.

Warning: this is not possible in embedded .control parts of a source file, these lines are
outside of this scope.

Confusion may arise in ngspice because of its multiple numerical expression features. The
```
.param lines and the brace expressions (see Chapt. 2.9) are evaluated in the front-end, that

```
is, just after the subcircuit expansion. (Technically, the X lines are kept as comments in the
expanded circuit so that the actual parameters can be correctly substituted). Therefore, after the
netlist expansion and before the internal data setup, all number attributes in the circuit are known
constants. However, there are circuit elements in Spice that accept arithmetic expressions not
evaluated at this point, but only later during circuit analysis. These are the arbitrary current
and voltage sources (B-sources, 5), as well as E- and G-sources and R-, L-, or C-devices.
The syntactic difference is that ‘compile-time’ expressions are within braces, but ‘run-time’
expressions have no braces. To make things more complicated, the back-end ngspice scripting
language accepts arithmetic/logic expressions that operate only on its own scalar or vector data
sets (17.2). Please see Chapt. 2.13.

It would be desirable to have the same expression syntax, operator and function set, and precedence rules, for the three contexts mentioned above. In the current Numparam implementation,
that goal is not achieved.

## 2.9 .FUNC

This keyword defines a function. The syntax of the expression is the same as for a .param
(2.8.5).


-----

General form:
```
  .func <ident> { <expr> }
  .func <ident> = { <expr> }

```
Examples:
```
  .func icos(x) {cos(x) - 1}
  .func f(x,y) {x*y}
  .func foo(a,b) = {a + b}
.func will initiate a replacement operation. After reading the input files, and before parameters

```
are evaluated, all occurrences of the icos(x) function will be replaced by cos(x)-1. All
occurrences of f(x,y) will be replaced by x*y. Function statements may be nested to a depth
of t.b.d..

## 2.10 .CSPARAM

Create a constant vector (see 17.8.2) from a parameter in plot (17.3) const.

General form:
```
  .csparam <ident> = <expr>

```
Examples:
```
  .param pippo=5
  .param pp=6
  .csparam pippp={pippo + pp}
  .param p={pp}
  .csparam pap=’pp+p’

```
In the example shown, vectors pippp, and pap are added to the constants that already reside
in plot const, having length one and real values. These vectors are generated during circuit
parsing and thus cannot be changed later (same as with ordinary parameters). They may be used
in ngspice scripts and .control sections (see Chapt. 17).

The use of .csparam is still experimental and has to be tested. A simple usage is shown below.
```
  * test csparam
  .param TEMPS = 27
  .csparam newt = {3*TEMPS}
  .csparam mytemp = ’2 + TEMPS’
  .control
  echo $&newt $&mytemp
  .endc
  .end

```

-----

## 2.11 .TEMP

Sets the circuit temperature in degrees Celsius.

General form:
```
  .temp value

```
Examples:
```
  .temp 27

```
This card overrides the circuit temperature given in an .option line (15.1.1).

## 2.12 .IF Condition-Controlled Netlist

A simple .IF-.ELSE(IF) block allows condition-controlling of the netlist. boolean expression
is any expression according to Chapt. 2.8.5 that evaluates parameters and returns a boolean 1
or 0. The netlist block in between the .if ... .endif statements may contain device instances or
```
.model cards that are selected according to the logic condition.

```

-----

General form:
```
  .if(boolean expression)
   ...
  .elseif(boolean expression)
   ...
  .else
   ...
  .endif

```
Example 1:
```
  * device instance in IF-ELSE block
  .param ok=0 ok2=1
  v1 1 0 1
  R1 1 0 2
  .if (ok && ok2)
   R11 1 0 2
  .else
   R11 1 0 0.5 $ <-- selected
  .endif

```
Example 2:
```
  * .model in IF-ELSE block
  .param m0=0 m1=1
  M1 1 2 3 4 N1 W=1 L=0.5
  .if(m0==1)
  .model N1 NMOS level=49 Version=3.1
  .elseif(m1==1)
  .model N1 NMOS level=49 Version=3.2.4 $ <-- selected
  .else
  .model N1 NMOS level=49 Version=3.3.0
  .endif

```
For now this is a very restricted version of an .IF-.ELSE(IF) block, so several netlist components are currently not supported within the .IF-.ENDIF block: .SUBCKT, .INC, .LIB, and
```
.PARAM. Nesting of .IF-.ELSE(IF) blocks is not possible. Only one .elseif is allowed per

```
block.


-----

## 2.13 Parameters, functions, expressions, and command scripts

In ngspice there are several ways to describe functional dependencies. In fact there are three
independent function parsers, being active before, during, and after the simulation. So it might
be due to have a few words on their interdependence.

### 2.13.1 Parameters

Parameters (Chapt. 2.8.1) and functions, either defined within the .param statement or with
the .func statement (Chapt. 2.9) are evaluated before any simulation is started, that is during
the setup of the input and the circuit. Therefore these statements may not contain any simulation output (voltage or current vectors), because it is simply not yet available. The syntax is
described in Chapt. 2.8.5. During the circuit setup all functions are evaluated, all parameters
are replaced by their resulting numerical values. Thus it will not be possible to get feedback
from a later stage (during or after simulation) to change any of the parameters.

### 2.13.2 Nonlinear sources

During the simulation, the B source (Chapt. 5) and their associated E and G sources, as well
as some devices (R, C, L) may contain expressions. These expressions may contain parameters
from above (evaluated immediately upon ngspice start up), numerical data, predefined functions, but also node voltages and branch currents resulting from the simulation. The source or
device values are continuously updated during the simulation. Therefore the sources are powerful tools to define non-linear behavior, you may even create new ‘devices’ by yourself.
Unfortunately the expression syntax (see Chapt. 5.1) and the predefined functions may deviate
from the ones for parameters listed in 2.8.1.

### 2.13.3 Control commands, Command scripts

Commands, as described in detail in Chapt. 17.5, may be used interactively, but also as a command script enclosed in .control ... `.endc lines. The scripts may contain expressions`
(see Chapt. 17.2). The expressions may work upon simulation output vectors (of node voltages, branch currents), as well as upon predefined or user defined vectors and variables, and are
invoked after the simulation. Parameters from 2.8.1 defined by the .param statement are not
allowed in these expressions. However you may define such parameters with .csparam (2.10).
Again the expression syntax (see Chapt. 17.2) will deviate from the one for parameters or B
sources listed in 2.8.1 and 5.1.

If you want to use parameters from 2.8.1 inside your control script, you may use .csparam
(2.10) or apply a trick by defining a voltage source with the parameter as its value, and then
have it available as a vector (e.g. after a transient simulation) with a then constant output (the
parameter). A feedback from here back into parameters (2.13.1) is never possible. Also you
cannot access non-linear sources of the preceding simulation. However you may start a first
simulation inside your control script, then evaluate its output using expressions, change some of
the element or model parameters with the alter and altermod statements (see Chapt. 17.5.3)
and then automatically start a new simulation.


-----

Expressions and scripting are powerful tools within ngspice, and we will enhance the examples
given in Chapt. 21 continuously to describe these features.


-----

