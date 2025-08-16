# Chapter 12

 Mixed-Mode and Behavioral Modeling with XSPICE

Ngspice implements XSPICE extensions for behavioral and mixed-mode (analog and digital)
modeling. In the XSPICE framework this is referred to as code level modeling. Behavioral
modeling may benefit dramatically because XSPICE offers a means to add analog functionality
programmed in C. Many examples (amplifiers, oscillators, filters ...) are presented in the following. Even more flexibility is available because you may define your own models and use them
in addition and in combination with all the already existing ngspice functionality. Digital and
mixed mode simulation is speeded up significantly by simulating the digital part in an event driven manner, in that state equations use only a few allowed states and are evaluated only during
switching, and not continuously in time and signal as in a pure analog simulator.

This chapter describes the predefined models available in ngspice, stemming from the original
XSPICE simulator or being added to enhance the usability. The instructions for writing new
code models are given in Chapt. 28.

To make use of the XSPICE extensions, you need to compile them in. Linux, CYGWIN,
MINGW and other users may add the flag --enable-xspice to their ./configure command and then recompile. The pre-built ngspice for Windows distribution has XSPICE already
enabled. For detailed compiling instructions see Chapt. 32.1.

## 12.1 Code Model Element & .MODEL Cards

### 12.1.1 Syntax

Ngspice includes a library of predefined ‘Code Models’ that can be placed within any circuit
description in a manner similar to that used to place standard device models. Code model instance cards always begin with the letter ‘A’, and always make use of a .MODEL card to describe
the code model desired. Section 28 of this document goes into greater detail as to how a code
model similar to the predefined models may be developed, but once any model is created and
linked into the simulator it may be placed using one instance card and one .MODEL card (note
here we conform to the SPICE custom of referring to a single logical line of information as a
‘card’). As an example, the following uses a predefined ‘gain’ code model taking as an input
some value on node 1, multiplies it by a gain of 5.0, and outputs the new value to node 2.


-----

Note that, by convention, input ports are specified first on code models. Output ports follow the
inputs.
```
  Example:
     a1 1 2 amp
     .model amp gain(gain=5.0)

```
In this example the numerical values picked up from single-ended (i.e. ground referenced)
input node 1 and output to single-ended output node 2 will be voltages, since in the Interface
Specification File for this code model (i.e., gain), the default port type is specified as a voltage
(more on this later). However, if you didn’t know this, the following modifications to the
instance card could be used to insure it:
```
  Example:
     a1 %v(1) %v(2) amp
     .model amp gain(gain=5.0)

```
The specification %v preceding the input and output node numbers of the instance card indicate
to the simulator that the inputs to the model should be single-ended voltage values. Other
possibilities exist, as described later.

Some of the other features of the instance and .MODEL cards are worth noting. Of particular
interest is the portion of the .MODEL card that specifies gain=5.0. This portion of the card
assigns a value to a parameter of the ‘gain’ model. There are other parameters that can be assigned values for this model, and in general code models will have several. In addition to numeric
values, code model parameters can take non-numeric values (such as TRUE and FALSE), and
even vector values. All of these topics will be discussed at length in the following pages. In
general, however, the instance and .MODEL cards that define a code model will follow the abstract form described below. This form illustrates that the number of inputs and outputs and the
number of parameters that can be specified is relatively open-ended and can be interpreted in a
variety of ways (note that angle-brackets ‘<’ and ‘>’ enclose optional inputs):


-----

```
  Example:
     AXXXXXXX <%v,%i,%vd,%id,%g,%gd,%h,%hd, or %d>
     + <[> <~><%v,%i,%vd,%id,%g,%gd,%h,%hd, or %d>
     + <NIN1 or +NIN1 -NIN1 or "null">
     + <~>...<NIN2.. <]> >
     + <%v,%i,%vd,%id,%g,%gd,%h,%hd,%d or %vnam>
     + <[> <~><%v,%i,%vd,%id,%g,%gd,%h,%hd,
         or %d><NOUT1 or +NOUT1 -NOUT1>
     + <~>...<NOUT2.. <]>>
     + MODELNAME
     .MODEL MODELNAME MODELTYPE
     + <( PARAMNAME1= <[> VAL1 <VAL2... <]>> PARAMNAME2..>)>

```
Square brackets ([ ]) are used to enclose vector input nodes. In addition, these brackets are used
to delineate vectors of parameters.

The literal string ‘null’, when included in a node list, is interpreted as no connection at that input
to the model. ‘Null’ is not allowed as the name of a model’s input or output if the model only
has one input or one output. Also, ‘null’ should only be used to indicate a missing connection
for a code model; use on other XSPICE component is not interpreted as a missing connection,
but will be interpreted as an actual node name.

The tilde, ‘~’, when prepended to a digital node name, specifies that the logical value of that
node be inverted prior to being passed to the code model. This allows for simple inversion of
input and output polarities of a digital model in order to handle logically equivalent cases and
others that frequently arise in digital system design. The following example defines a NAND
gate, one input of which is inverted:
```
     a1 [~1 2] 3 nand1
     .model nand1 d_nand (rise_delay=0.1 fall_delay=0.2)

```
The optional symbols %v, %i, %vd, etc. specify the type of port the simulator is to expect for
the subsequent port or port vector. The meaning of each symbol is given in Table 12.1.

The symbols described in Table 12.1 may be omitted if the default port type for the model is
desired. Note that non-default port types for multi-input or multi-output (vector) ports must be
specified by placing one of the symbols in front of EACH vector port. On the other hand, if all
ports of a vector port are to be declared as having the same non-default type, then a symbol may
be specified immediately prior to the opening bracket of the vector. The following examples
should make this clear:
```
  Example 1: - Specifies two differential voltage connections, one
         to nodes 1 & 2, and one to nodes 3 & 4.

```

-----

|Port Type Modifiers|Col2|
|---|---|
|Modifier|Interpretation|
|%v|represents a single-ended voltage port - one node name or number is expected for each port.|
|%i|represents a single-ended current port - one node name or number is expected for each port.|
|%g|represents a single-ended voltage-input, current-output (VCCS) port - one node name or number is expected for each port. This type of port is auto- matically an input/output.|
|%h|represents a single-ended current-input, voltage-output (CCVS) port - one node name or number is expected for each port. This type of port is auto- matically an input/output.|
|%d|represents a digital port - one node name or number is expected for each port. This type of port may be either an input or an output.|
|%vnam|represents the name of a voltage source, the current through which is taken as an input. This notation is provided primarily in order to allow models defined using SPICE2G6 syntax to operate properly in XSPICE.|
|%vd|represents a differential voltage port - two node names or numbers are ex- pected for each port.|
|%id|represents a differential current port - two node names or numbers are ex- pected for each port.|
|%gd|represents a differential VCCS port - two node names or numbers are expected for each port.|
|%hd|represents a differential CCVS port - two node names or numbers are expected for each port.|


Table 12.1: Port Type Modifiers


-----

```
    %vd [1 2 3 4]
  Example 2: - Specifies two single-ended connections to node 1 and
         at node 2, and one differential connection to
         nodes 3 & 4.
    %v [1 2 %vd 3 4]
  Example 3: - Identical to the previous example...parenthesis
         are added for additional clarity.
    %v [1 2 %vd(3 4)]
  Example 4: - Specifies that the node numbers are to be treated in the
         default fashion for the particular model.
         If this model had ‘%v” as a default for this
         port, then this notation would represent four single-ended
         voltage connections.
    [1 2 3 4]

```
The parameter names listed on the .MODEL card must be identical to those named in the code
model itself. The parameters for each predefined code model are described in detail in Sections
12.2 (analog), 12.3 (Hybrid, A/D) and 12.4 (digital) . The steps required in order to specify
parameters for user-defined models are described in Chapter 28.

### 12.1.2 Examples

The following is a list of instance card and associated .MODEL card examples showing use of
predefined models within an XSPICE deck:
```
  a1 1 2 amp
  .model amp gain(in_offset=0.1 gain=5.0 out_offset=-0.01)
  a2 %i[1 2] 3 sum1
  .model sum1 summer(in_offset=[0.1 -0.2] in_gain=[2.0 1.0]
  + out_gain=5.0 out_offset=-0.01)
  a21 %i[1 %vd(2 5) 7 10] 3 sum2
  .model sum2 summer(out_gain=10.0)
  a5 1 2 limit5
  .model limit5 limit(in_offset=0.1 gain=2.5
  + out_lower.limit=-5.0 out_upper_limit=5.0 limit_domain=0.10
  + fraction=FALSE)
  a7 2 %id(4 7) xfer.cntl1
  .model xfer_cntl1 pwl(x_array=[-2.0 -1.0 2.0 4.0 5.0]
  + y_array=[-0.2 -0.2 0.1 2.0 10.0]
  + input_domain=0.05 fraction=TRUE)
  a8 3 %gd(6 7) switch3
  .model switch3 aswitch(cntl_off=0.0 cntl_on=5.0 r_off=1e6
  + r_on=10.0 log=TRUE)

```

-----

### 12.1.3 Search path for file input

Several code models (filesource 12.2.8, d_source 12.4.21, d_state 12.4.18) call additional
files for supply of input data. A call to file="path/filename" (or input_file=, state_file=)
in the .model card will start a search sequence for finding the file. `path may be an absolute`
path. If path is omitted or is a relative path, filename is looked for according to the following
search list:
```
Infile_Path/<path/filename> (Infile_Path is the path of the input file *.sp containing the

```
netlist)
```
NGSPICE_INPUT_DIR/<path/filename> (where an additional path is set by the environmen
```
tal variable)
```
<path/filename> (where the search is relative to the current directory (OS dependent))

## 12.2 Analog Models

```
The following analog models are supplied with XSPICE. The descriptions included consist
of the model Interface Specification File and a description of the model’s operation. This is
followed by an example of a simulator-deck placement of the model, including the .MODEL
card and the specification of all available parameters.

### 12.2.1 Gain
```
  NAME_TABLE:
  C_Function_Name: cm_gain
  Spice_Model_Name: gain
  Description: "A simple gain block"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: no no
  Vector.Bounds: -   Null.Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset gain out_offset
  Description: "input offset" "gain" "output offset"
  Data_Type: real real real
  Default_Value: 0.0 1.0 0.0
  Limits: - -   Vector: no no no

```

-----

```
  Vector_Bounds: - -   Null_Allowed: yes yes yes

```
**Description: This function is a simple gain block with optional offsets on the input and the**
output. The input offset is added to the input, the sum is then multiplied by the gain, and
the result is produced by adding the output offset. This model will operate in DC, AC,
and Transient analysis modes.
```
  Example:
     a1 1 2 amp
     .model amp gain(in_offset=0.1 gain=5.0
     + out_offset=-0.01)

### 12.2.2 Summer
  NAME_TABLE:
  C_Function_Name: cm_summer
  Spice_Model_Name: summer
  Description: "A summer block"
  PORT_TABLE:
  Port Name: in out
  Description: "input vector" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: yes no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset in_gain
  Description: "input offset vector" "input gain vector"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: yes yes
  Vector_Bounds: in in
  Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_gain out_offset
  Description: "output gain" "output offset"
  Data_Type: real real

```

-----

```
  Default_Value: 1.0 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: This function is a summer block with 2-to-N input ports. Individual gains and**
offsets can be applied to each input and to the output. Each input is added to its respective
offset and then multiplied by its gain. The results are then summed, multiplied by the
output gain and added to the output offset. This model will operate in DC, AC, and
Transient analysis modes.

Example usage:
```
  a2 [1 2] 3 sum1
  .model sum1 summer(in_offset=[0.1 -0.2] in_gain=[2.0 1.0]
  + out_gain=5.0 out_offset=-0.01)

### 12.2.3 Multiplier
  NAME_TABLE:
  C_Function_Name: cm_mult
  Spice_Model_Name: mult
  Description: "multiplier block"
  PORT_TABLE:
  Port_Name: in out
  Description: "input vector" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset in_gain
  Description: "input offset vector" "input gain vector"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: yes yes
  Vector_Bounds: in in
  Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_gain out_offset
  Description: "output gain" "output offset"

```

-----

```
  Data_Type: real real
  Default_Value: 1.0 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: This function is a multiplier block with 2-to-N input ports. Individual gains and**
offsets can be applied to each input and to the output. Each input is added to its respective
offset and then multiplied by its gain. The results are multiplied along with the output
gain and are added to the output offset. This model will operate in DC, AC, and Transient
analysis modes. However, in ac analysis it is important to remember that results are
invalid unless only one input of the multiplier is connected to a node that i connected to
an AC signal (this is exemplified by the use of a multiplier to perform a potentiometer
function: one input is DC, the other carries the AC signal).
```
  Example SPICE Usage:
     a3 [1 2 3] 4 sigmult
     .model sigmult mult(in_offset=[0.1 0.1 -0.1]
     + in_gain=[10.0 10.0 10.0] out_gain=5.0 out_offset=0.05)

### 12.2.4 Divider
  NAME_TABLE:
  C_Function_Name: cm_divide
  Spice_Model_Name: divide
  Description: "divider block"
  PORT_TABLE:
  Port_Name: num den out
  Description: "numerator" "denominator" "output"
  Direction: in in out
  Default_Type: v v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: no no no
  PARAMETER_TABLE:
  Parameter_Name: num_offset num_gain
  Description: "numerator offset" "numerator gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```

-----

```
  PARAMETER_TABLE:
  Parameter_Name: den_offset den_gain
  Description: "denominator offset" "denominator gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: den_lower_limit
  Description: "denominator lower limit"
  Data_Type: real
  Default_Value: 1.0e-10
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: den_domain
  Description: "denominator smoothing domain"
  Data_Type: real
  Default_Value: 1.0e-10
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: fraction
  Description: "smoothing fraction/absolute value switch"
  Data_Type: boolean
  Default_Value: false
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: out_gain out_offset
  Description: "output gain" "output offset"
  Data_Type: real real
  Default_Value: 1.0 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: This function is a two-quadrant divider. It takes two inputs; num (numerator) and**
den (denominator). Divide offsets its inputs, multiplies them by their respective gains,


-----

divides the results, multiplies the quotient by the output gain, and offsets the result. The
denominator is limited to a value above zero via a user specified lower limit. This limit
is approached through a quadratic smoothing function, the domain of which may be specified as a fraction of the lower limit value (default), or as an absolute value. This model
will operate in DC, AC and Transient analysis modes. However, in ac analysis it is important to remember that results are invalid unless only one input of the divider is connected
to a node that is connected to an ac signal (this is exemplified by the use of the divider to
perform a potentiometer function: one input is dc, the other carries the ac signal).
```
  Example SPICE Usage:
  a4 1 2 4 divider
  .model divider divide(num_offset=0.1 num_gain=2.5 den_offset=-0.1
  + den_gain=5.0 den_lower.limit=1e-5 den_domain=1e-6
  + fraction=FALSE out_gain=1.0 out_offset=0.0)

### 12.2.5 Limiter
  NAME_TABLE:
  C_Function_Name: cm_limit
  Spice_Model_Name: limit
  Description: "limit block"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset gain
  Description: "input offset" "gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_lower_limit out_upper_limit
  Description: "output lower limit" "output upper limit"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```

-----

```
  PARAMETER_TABLE:
  Parameter_Name: limit_range
  Description: "upper & lower smoothing range"
  Data_Type: real
  Default_Value: 1.0e-6
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: fraction
  Description: "smoothing fraction/absolute value switch"
  Data_Type: boolean
  Default_Value: FALSE
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The Limiter is a single input, single output function similar to the Gain Block.**
However, the output of the Limiter function is restricted to the range specified by the
output lower and upper limits. This model will operate in DC, AC and Transient analysis
modes. Note that the limit range is the value below the upper limit and above the lower
_limit at which smoothing of the output begins. For this model, then, the limit range_
represents the delta with respect to the output level at which smoothing occurs. Thus, for
an input gain of 2.0 and output limits of 1.0 and -1.0 volts, the output will begin to smooth
out at 0.9 volts, which occurs when the input value is at 0.4.
_±_ _±_
```
  Example SPICE Usage:
  a5 1 2 limit5
  .model limit5 limit(in_offset=0.1 gain=2.5 out_lower_limit=-5.0
  + out_upper_limit=5.0 limit_range=0.10 fraction=FALSE)

### 12.2.6 Controlled Limiter
  NAME_TABLE:
  C_Function_Name: cm_climit
  Spice_Model_Name: climit
  Description: "controlled limiter block"
  PORT_TABLE:
  Port_Name: in cntl_upper
  Description: "input" "upper lim. control input"
  Direction: in in
  Default_Type: v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id,vnam]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no

```

-----

```
  PORT_TABLE:
  Port_Name: cntl_lower out
  Description: "lower limit control input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset gain
  Description: "input offset" "gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: upper_delta lower_delta
  Description: "output upper delta" "output lower delta"
  Data_Type: real real
  Default_Value: 0.0 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: limit_range fraction
  Description: "upper & lower sm. range" "smoothing %/abs switch"
  Data_Type: real boolean
  Default_Value: 1.0e-6 FALSE
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The Controlled Limiter is a single input, single output function similar to the Gain**
Block. However, the output of the Limiter function is restricted to the range specified by
the output lower and upper limits. This model will operate in DC, AC, and Transient
analysis modes. Note that the limit range is the value below the cntl_upper limit and
_above the cntl_lower limit at which smoothing of the output begins (minimum positive_
value of voltage must exist between the cntl_upper input and the cntl_lower input at
all times). For this model, then, the limit range represents the delta with respect to the
_output level at which smoothing occurs. Thus, for an input gain of 2.0 and output limits_
of 1.0 and -1.0 volts, the output will begin to smooth out at 0.9 volts, which occurs
_±_
when the input value is at 0.4. Note also that the Controlled Limiter code tests the
_±_
input values of cntl_upper and cntl_lower to make sure that they are spaced far enough


-----

apart to guarantee the existence of a linear range between them. The range is calculated
as the difference between (cntl_upper _upper_delta_ _limit_range) and (cntl_lower +_
_−_ _−_
_lower_delta + limit_range) and must be greater than or equal to zero. Note that when_
the limit range is specified as a fractional value, the limit range used in the above is taken
as the calculated fraction of the difference between cntl_upper and cntl_lower. Still, the
potential exists for too great a limit range value to be specified for proper operation, in
which case the model will return an error message.
```
  Example SPICE Usage:
  a6 3 6 8 4 varlimit
  .
  .
  .model varlimit climit(in_offset=0.1 gain=2.5 upper_delta=0.0
  + lower_delta=0.0 limit_range=0.10 fraction=FALSE)

### 12.2.7 PWL Controlled Source
  NAME_TABLE:
  C_Function_Name: cm_pwl
  Spice_Model_Name: pwl
  Description: "piecewise linear controlled source"
  PORT_TABLE:
  Port_Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: x_array y_array
  Description: "x-element array" "y-element array"
  Data_Type: real real
  Default_Value: -   Limits: -   Vector: yes yes
  Vector_Bounds: [2 -] [2 -]
  Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: input_domain fraction
  Description: "input sm. domain" "smoothing %/abs switch"
  Data_Type: real boolean
  Default_Value: 0.01 TRUE
  Limits: [1e-12 0.5]   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```

-----

```
  STATIC_VAR_TABLE:
  Static_Var_Name: last_x_value
  Data_Type: pointer
  Description: "iteration holding variable for limiting"

```
**Description: The Piece-Wise Linear Controlled Source is a single input, single output function**
similar to the Gain Block. However, the output of the PWL Source is not necessarily linear for all values of input. Instead, it follows an I/O relationship specified by you via the
```
  x_array and y_array coordinates. This is detailed below.

```
The x_array and y_array values represent vectors of coordinate points on the x and
y axes, respectively. The x_array values are progressively increasing input coordinate
points, and the associated y_array values represent the outputs at those points. There
may be as few as two (x_array[n], y_array[n]) pairs specified, or as many as memory
and simulation speed allow. This permits you to very finely approximate a non-linear
function by capturing multiple input-output coordinate points.
Two aspects of the PWL Controlled Source warrant special attention. These are the handling of endpoints and the smoothing of the described transfer function near coordinate
points.
In order to fully specify outputs for values of in outside of the bounds of the PWL
function (i.e., less than x_array[0] or greater than x_array[n], where n is the largest
user-specified coordinate index), the PWL Controlled Source model extends the slope
found between the lowest two coordinate pairs and the highest two coordinate pairs.
This has the effect of making the transfer function completely linear for in less than
```
  x_array[0] and in greater than x_array[n]. It also has the potentially subtle effect of

```
unrealistically causing an output to reach a very large or small value for large inputs. You
should thus keep in mind that the PWL Source does not inherently provide a limiting
capability.
In order to diminish the potential for non-convergence of simulations when using the
PWL block, a form of smoothing around the x_array, y_array coordinate points is necessary. This is due to the iterative nature of the simulator and its reliance on smooth first
derivatives of transfer functions in order to arrive at a matrix solution. Consequently, the
```
  input_domain and fraction parameters are included to allow you some control over

```
the amount and nature of the smoothing performed.
```
  Fraction is a switch that is either TRUE or FALSE. When TRUE (the default setting),

```
the simulator assumes that the specified input domain value is to be interpreted as a fractional figure. Otherwise, it is interpreted as an absolute value. Thus, if fraction=TRUE
and input_domain=0.10, The simulator assumes that the smoothing radius about each
coordinate point is to be set equal to 10% of the length of either the x_array segment
above each coordinate point, or the x_array segment below each coordinate point. The
specific segment length chosen will be the smallest of these two for each coordinate point.
On the other hand, if fraction=FALSE and input=0.10, then the simulator will begin
smoothing the transfer function at 0.10 volts (or amperes) below each x_array coordinate and will continue the smoothing process for another 0.10 volts (or amperes) above
each x_array coordinate point. Since the overlap of smoothing domains is not allowed,
checking is done by the model to ensure that the specified input domain value is not excessive.
One subtle consequence of the use of the fraction=TRUE feature of the PWL Controlled Source is that, in certain cases, you may inadvertently create extreme smoothing


-----

of functions by choosing inappropriate coordinate value points. This can be demonstrated by considering a function described by three coordinate pairs, such as (-1,-1), (1,1),
and (2,1). In this case, with a 10% input_domain value specified (fraction=TRUE,
```
  input_domain=0.10), you would expect to see rounding occur between in=0.9 and
  in=1.1, and nowhere else. On the other hand, if you were to specify the same function

```
using the coordinate pairs (-100,-100), (1,1) and (201,1), you would find that rounding
occurs between in=-19 and in=21. Clearly in the latter case the smoothing might cause
an excessive divergence from the intended linearity above and below in=1.
```
  Example SPICE Usage:
  a7 2 4 xfer_cntl1
  .
  .
  .model xfer_cntl1 pwl(x_array=[-2.0 -1.0 2.0 4.0 5.0]
  + y_array=[-0.2 -0.2 0.1 2.0 10.0]
  + input_domain=0.05 fraction=TRUE)

### 12.2.8 Filesource
  NAME_TABLE:
  C_Function_Name: cm_filesource
  Spice_Model_Name: filesource
  Description: "File Source"
  PORT_TABLE:
  Port_Name: out
  Description: "output"
  Direction: out
  Default_Type: v
  Allowed_Types: [v,vd,i,id]
  Vector: yes
  Vector_Bounds: [1 -]
  Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: timeoffset timescale
  Description: "time offset" "timescale"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: timerelative amplstep
  Description: "relative time" "step amplitude"
  Data_Type: boolean boolean
  Default_Value: FALSE FALSE
  Limits: -   Vector: no no

```

-----

```
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: amploffset amplscale
  Description: "ampl offset" "amplscale"
  Data_Type: real real
  Default_Value: -   Limits: -   Vector: yes yes
  Vector_Bounds: [1 -] [1 -]
  Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: file
  Description: "file name"
  Data_Type: string
  Default_Value: "filesource.txt"
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The File Source is similar to the Piece-Wise Linear Source, except that the wa-**
veform data is read from a file instead of being taken from parameter vectors. The file
format is line oriented ASCII. ‘#’ and ‘;’ are comment characters; all characters from
a comment character until the end of the line are ignored. Each line consists of two or
more real values. The first value is the time; subsequent values correspond to the outputs.
Values are separated by spaces. Time values are absolute and must be monotonically increasing, unless timerelative is set to TRUE, in which case the values specify the interval
between two samples and must be positive. Waveforms may be scaled and shifted in the
time dimension by setting timescale and timeoffset.
Amplitudes can also be scaled and shifted using amplscale and amploffset. Amplitudes
are normally interpolated between two samples, unless amplstep is set to TRUE.

**Note: The file named by the parameter filename in file="filename" is sought after accor-**
ding to a search list described in12.1.3.
```
  Example SPICE Usage:
  a8 %vd([1 0 2 0]) filesrc
  .
  .
  .model filesrc filesource (file="sine.m" amploffset=[0 0] amplscale=[1 1]
  + timeoffset=0 timescale=1
  + timerelative=false amplstep=false)
  Example input file:
  # name: sine.m

```

-----

```
  # two output ports
  # column 1: time
  # columns 2, 3: values
   0 0 1
   3.90625e-09 0.02454122852291229 0.9996988186962042
   7.8125e-09 0.04906767432741801 0.9987954562051724
   1.171875e-08 0.07356456359966743 0.9972904566786902
   ...

### 12.2.9 multi_input_pwl block
  NAME_TABLE:
  C_Function_Name: cm_multi_input_pwl
  Spice_Model_Name: multi_input_pwl
  Description: "multi_input_pwl block"
  PORT_TABLE:
  Port_Name: in out
  Description: "input array" "output"
  Direction: in out
  Default_Type: vd vd
  Allowed_Types: [vd,id] [vd,id]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: x y
  Description: "x array" "y array"
  Data_Type: real real
  Default_Value: 0.0 0.0
  Limits: -   Vector: yes yes
  Vector_Bounds: [2 -] [2 -]
  Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: model
  Description: "model type"
  Data_Type: string
  Default_Value: "and"
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: Multi-input gate voltage controlled voltage source that supports and or or gating.**
The x’s and y’s represent the piecewise linear variation of output (y) as a function of input
(x). The type of gate is selectable by the parameter model. In case the model is and, the
smallest input determines the output value (i.e. the and function). In case the model is or,


-----

the largest input determines the output value (i.e. the or function). The inverse of these
functions (i.e. nand and nor) is constructed by complementing the y array.
```
  Example SPICE Usage:
  a82 [1 0 2 0 3 0] 7 0 pwlm
  .
  .
  .model pwlm multi_input_pwl((x=[-2.0 -1.0 2.0 4.0 5.0]
  + y=[-0.2 -0.2 0.1 2.0 10.0]
  + model="and")

### 12.2.10 Analog Switch
  NAME_TABLE:
  C_Function_Name: cm_aswitch
  Spice_Model_Name: aswitch
  Description: "analog switch"
  PORT_TABLE:
  Port Name: cntl_in out
  Description: "input" "resistive output"
  Direction: in out
  Default_Type: v gd
  Allowed_Types: [v,vd,i,id] [gd]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: cntl_off cntl_on
  Description: "control ‘off’ value" "control ‘on’ value"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: r_off log
  Description: "off resistance" "log/linear switch"
  Data_Type: real boolean
  Default_Value: 1.0e12 TRUE
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: r_on
  Description: "on resistance"
  Data_Type: real

```

-----

```
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The Analog Switch is a resistor that varies either logarithmically or linearly be-**
tween specified values of a controlling input voltage or current. Note that the input is
not internally limited. Therefore, if the controlling signal exceeds the specified OFF state
or ON state value, the resistance may become excessively large or excessively small (in
the case of logarithmic dependence), or may become negative (in the case of linear dependence). For the experienced user, these excursions may prove valuable for modeling
certain devices, but in most cases you are advised to add limiting of the controlling input
if the possibility of excessive control value variation exists.
```
  Example SPICE Usage:
  a8 3 %gd(6 7) switch3
  .
  .
  .model switch3 aswitch(cntl_off=0.0 cntl_on=5.0 r_off=1e6
  + r_on=10.0 log=TRUE)

### 12.2.11 Zener Diode
  NAME_TABLE:
  C_Function_Name: cm_zener
  Spice_Model_Name: zener
  Description: "zener diode"
  PORT_TABLE:
  Port Name: z
  Description: "zener"
  Direction: inout
  Default_Type: gd
  Allowed_Types: [gd]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: v_breakdown i_breakdown
  Description: "breakdown voltage" "breakdown current"
  Data_Type: real real
  Default_Value: - 2.0e-2
  Limits: [1.0e-6 1.0e6] [1.0e-9 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no yes
  PARAMETER_TABLE:
  Parameter_Name: i_sat n_forward

```

-----

```
  Description: "saturation current" "forward emission coefficient"
  Data_Type: real real
  Default_Value: 1.0e-12 1.0
  Limits: [1.0e-15 -] [0.1 10]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: limit_switch
  Description: "switch for on-board limiting (convergence aid)"
  Data_Type: boolean
  Default_Value: FALSE
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  STATIC_VAR_TABLE:
  Static_Var_Name: previous_voltage
  Data_Type: pointer
  Description: "iteration holding variable for limiting"

```
**Description: The Zener Diode models the DC characteristics of most zeners. This model**
differs from the Diode/Rectifier by providing a user-defined dynamic resistance in the
reverse breakdown region. The forward characteristic is defined by only a single point,
since most data sheets for zener diodes do not give detailed characteristics in the forward
region.
The first three parameters define the DC characteristics of the zener in the breakdown
region and are usually explicitly given on the data sheet.
The saturation current refers to the relatively constant reverse current that is produced
when the voltage across the zener is negative, but breakdown has not been reached. The
reverse leakage current determines the slight increase in reverse current as the voltage
across the zener becomes more negative. It is modeled as a resistance parallel to the
zener with value v breakdown / i rev.
Note that the limit switch parameter engages an internal limiting function for the zener.
This can, in some cases, prevent the simulator from converging to an unrealistic solution
if the voltage across or current into the device is excessive. If use of this feature fails to
yield acceptable results, the convlimit option should be tried (add the following statement
to the SPICE input deck: .options convlimit)
```
  Example SPICE Usage:
  a9 3 4 vref10
  .
  .
  .model vref10 zener(v_breakdown=10.0 i_breakdown=0.02
  + r_breakdown=1.0 i_rev=1e-6 i_sat=1e-12)

### 12.2.12 Current Limiter
  NAME_TABLE:

```

-----

```
C_Function_Name: cm_ilimit
Spice_Model_Name: ilimit
Description: "current limiter block"
PORT_TABLE:
Port Name: in pos_pwr
Description: "input" "positive power supply"
Direction: in inout
Default_Type: v g
Allowed_Types: [v,vd] [g,gd]
Vector: no no
Vector_Bounds: - Null_Allowed: no yes
PORT_TABLE:
Port Name: neg_pwr out
Description: "negative power supply" "output"
Direction: inout inout
Default_Type: g g
Allowed_Types: [g,gd] [g,gd]
Vector: no no
Vector_Bounds: - Null_Allowed: yes no
PARAMETER_TABLE:
Parameter_Name: in_offset gain
Description: "input offset" "gain"
Data_Type: real real
Default_Value: 0.0 1.0
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: r_out_source r_out_sink
Description: "sourcing resistance" "sinking resistance"
Data_Type: real real
Default_Value: 1.0 1.0
Limits: [1.0e-9 1.0e9] [1.0e-9 1.0e9]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: i_limit_source
Description: "current sourcing limit"
Data_Type: real
Default_Value: Limits: [1.0e-12 -]
Vector: no
Vector_Bounds: Null_Allowed: yes

```

-----

```
  PARAMETER_TABLE:
  Parameter_Name: i_limit_sink
  Description: "current sinking limit"
  Data_Type: real
  Default_Value:   Limits: [1.0e-12 -]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: v_pwr_range i_source_range
  Description: "upper & lower power "sourcing current
             supply smoothing range" smoothing range"
  Data_Type: real real
  Default_Value: 1.0e-6 1.0e-9
  Limits: [1.0e-15 -] [1.0e-15 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: i_sink_range
  Description: "sinking current smoothing range"
  Data_Type: real
  Default_Value: 1.0e-9
  Limits: [1.0e-15 -]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: r_out_domain
  Description: "internal/external voltage delta smoothing range"
  Data_Type: real
  Default_Value: 1.0e-9
  Limits: [1.0e-15 -]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The Current Limiter models the behavior of an operational amplifier or compa-**
rator device at a high level of abstraction. All of its pins act as inputs; three of the four
also act as outputs. The model takes as input a voltage value from the in connector. It
then applies an offset and a gain, and derives from it an equivalent internal voltage (veq),
which it limits to fall between pos_pwr and neg_pwr. If veq is greater than the output
voltage seen on the out connector, a sourcing current will flow from the output pin. Conversely, if the voltage is less than vout, a sinking current will flow into the output pin.
Depending on the polarity of the current flow, either a sourcing or a sinking resistance
value (r_out_source, r_out_sink) is applied to govern the vout/i_out relationship.
The chosen resistance will continue to control the output current until it reaches a maximum value specified by either i_limit_source or i_limit_sink. The latter mimics


-----

the current limiting behavior of many operational amplifier output stages.
During all operation, the output current is reflected either in the pos_pwr connector current or the neg_pwr current, depending on the polarity of i_out. Thus, realistic power
consumption as seen in the supply rails is included in the model.
The user-specified smoothing parameters relate to model operation as follows: v_pwr_range
controls the voltage below vpos_pwr and above vneg_pwr inputs beyond which veq =
_gain(vin+vof fset) is smoothed; i_source_range specifies the current below i_limit_source_
at which smoothing begins, as well as specifying the current increment above i_out=0.0
at which i_pos_pwr begins to transition to zero; i_sink_range serves the same purpose with respect to i_limit_sink and i_neg_pwr that i_source_range serves for
```
  i_limit_source and i_pos_pwr; r_out_domain specifies the incremental value above

```
and below (veq-vout)=0.0 at which r_out will be set to r_out_source and r_out_sink,
respectively. For values of (veq-vout) less than r_out_domain and greater than -r_out_domain,
```
  r_out is interpolated smoothly between r_out_source and r_out_sink.
  Example SPICE Usage:
  a10 3 10 20 4 amp3
  .
  .
  .model amp3 ilimit(in_offset=0.0 gain=16.0 r_out_source=1.0
  + r_out_sink=1.0 i_limit_source=1e-3
  + i_limit_sink=10e-3 v_pwr_range=0.2
  + i_source_range=1e-6 i_sink_range=1e-6
  + r_out_domain=1e-6)

### 12.2.13 Hysteresis Block
  NAME_TABLE:
  C_Function_Name: cm_hyst
  Spice_Model_Name: hyst
  Description: "hysteresis block"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_low in_high
  Description: "input low value" "input high value"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: - 
```

-----

```
  Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: hyst out_lower_limit
  Description: "hysteresis" "output lower limit"
  Data_Type: real real
  Default_Value: 0.1 0.0
  Limits: [0.0 -]   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_upper_limit input_domain
  Description: "output upper limit" "input smoothing domain"
  Data_Type: real real
  Default_Value: 1.0 0.01
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: fraction
  Description: "smoothing fraction/absolute value switch"
  Data_Type: boolean
  Default_Value: TRUE
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The Hysteresis block is a simple buffer stage that provides hysteresis of the output**
with respect to the input. The in low and in high parameter values specify the center
voltage or current inputs about which the hysteresis effect operates. The output values
are limited to out lower limit and out upper limit. The value of hyst is added to the in
low and in high points in order to specify the points at which the slope of the hysteresis
function would normally change abruptly as the input transitions from a low to a high
value. Likewise, the value of hyst is subtracted from the in high and in low values in
order to specify the points at which the slope of the hysteresis function would normally
change abruptly as the input transitions from a high to a low value. In fact, the slope of the
hysteresis function is never allowed to change abruptly but is smoothly varied whenever
the input domain smoothing parameter is set greater than zero.
```
  Example SPICE Usage:
  a11 1 2 schmitt1
  .
  .
  .model schmitt1 hyst(in_low=0.7 in_high=2.4 hyst=0.5
  + out_lower_limit=0.5 out_upper_limit=3.0
  + input_domain=0.01 fraction=TRUE)

```

-----

### 12.2.14 Differentiator
```
  NAME_TABLE:
  C_Function_Name: cm_d_dt
  Spice_Model_Name: d_dt
  Description: "time-derivative block"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: gain out_offset
  Description: "gain" "output offset"
  Data_Type: real real
  Default_Value: 1.0 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_lower_limit out_upper_limit
  Description: "output lower limit" "output upper limit"
  Data_Type: real real
  Default_Value: -   Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: limit_range
  Description: "upper & lower limit smoothing range"
  Data_Type: real
  Default_Value: 1.0e-6
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The Differentiator block is a simple derivative stage that approximates the time**
derivative of an input signal by calculating the incremental slope of that signal since the
previous time point. The block also includes gain and output offset parameters to allow
for tailoring of the required signal, and output upper and lower limits to prevent convergence errors resulting from excessively large output values. The incremental value of
output below the output upper limit and above the output lower limit at which smoothing


-----

begins is specified via the limit range parameter. In AC analysis, the value returned is
equal to the radian frequency of analysis multiplied by the gain.
Note that since truncation error checking is not included in the d_dt block, it is not recommended that the model be used to provide an integration function through the use
of a feedback loop. Such an arrangement could produce erroneous results. Instead, you
should make use of the "integrate" model, which does include truncation error checking
for enhanced accuracy.
```
  Example SPICE Usage:
  a12 7 12 slope_gen
  .
  .
  .model slope_gen d_dt(out_offset=0.0 gain=1.0
  + out_lower_limit=1e-12 out_upper_limit=1e12
  + limit_range=1e-9)

### 12.2.15 Integrator
  NAME_TABLE:
  C_Function_Name: cm_int
  Spice_Model_Name: int
  Description: "time-integration block"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset gain
  Description: "input offset" "gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_lower_limit out_upper_limit
  Description: "output lower limit" "output upper limit"
  Data_Type: real real
  Default_Value: -   Limits: -   Vector: no no
  Vector_Bounds: - 
```

-----

```
  Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: limit_range
  Description: "upper & lower limit smoothing range"
  Data_Type: real
  Default_Value: 1.0e-6
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: out_ic
  Description: "output initial condition"
  Data_Type: real
  Default_Value: 0.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The Integrator block is a simple integration stage that approximates the integral**
with respect to time of an input signal. The block also includes gain and input offset
parameters to allow for tailoring of the required signal, and output upper and lower limits
to prevent convergence errors resulting from excessively large output values. Note that
these limits specify integrator behavior similar to that found in an operational amplifierbased integration stage, in that once a limit is reached, additional storage does not occur.
Thus, the input of a negative value to an integrator that is currently driving at the out
upper limit level will immediately cause a drop in the output, regardless of how long
the integrator was previously summing positive inputs. The incremental value of output
below the output upper limit and above the output lower limit at which smoothing begins
is specified via the limit range parameter. In AC analysis, the value returned is equal to
the gain divided by the radian frequency of analysis.
Note that truncation error checking is included in the int block. This should provide
for a more accurate simulation of the time integration function, since the model will
inherently request smaller time increments between simulation points if truncation errors
would otherwise be excessive.
```
  Example SPICE Usage:
  a13 7 12 time_count
  .
  .
  .model time_count int(in_offset=0.0 gain=1.0
  + out_lower_limit=-1e12 out_upper_limit=1e12
  + limit_range=1e-9 out_ic=0.0)

### 12.2.16 S-Domain Transfer Function
  NAME_TABLE:

```

-----

```
C_Function_Name: cm_s_xfer
Spice_Model_Name: s_xfer
Description: "s-domain transfer function"
PORT_TABLE:
Port Name: in out
Description: "input" "output"
Direction: in out
Default_Type: v v
Allowed_Types: [v,vd,i,id] [v,vd,i,id]
Vector: no no
Vector_Bounds: - Null_Allowed: no no
PARAMETER_TABLE:
Parameter_Name: in_offset gain
Description: "input offset" "gain"
Data_Type: real real
Default_Value: 0.0 1.0
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: num_coeff
Description: "numerator polynomial coefficients"
Data_Type: real
Default_Value: Limits: Vector: yes
Vector_Bounds: [1 -]
Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: den_coeff
Description: "denominator polynomial coefficients"
Data_Type: real
Default_Value: Limits: Vector: yes
Vector_Bounds: [1 -]
Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: int_ic
Description: "integrator stage initial conditions"
Data_Type: real
Default_Value: 0.0
Limits: Vector: yes
Vector_Bounds: den_coeff
Null_Allowed: yes

```

-----

```
  PARAMETER_TABLE:
  Parameter_Name: denormalized_freq
  Description: "denorm. corner freq.(radians) for 1 rad/s coeffs"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The s-domain transfer function is a single input, single output transfer function**
in the Laplace transform variable ‘s’ that allows for flexible modulation of the frequency
domain characteristics of a signal. Ac and transient simulations are supported. The code
model may be configured to produce an arbitrary s-domain transfer function with the
following restrictions:
```
  1. The degree of the numerator polynomial cannot exceed that
    of the denominator polynomial in the variable "s".
  2. The coefficients for a polynomial must be stated
    explicitly. That is, if a coefficient is zero, it must be
    included as an input to the num coeff or den coeff vector.

```
The order of the coefficient parameters is from that associated with the highest-powered term
decreasing to that of the lowest. Thus, for the coefficient parameters specified below, the equation in ‘s’ is shown:
```
  .model filter s_xfer(gain=0.139713
  + num_coeff=[1.0 0.0 0.7464102]
  + den_coeff=[1.0 0.998942 0.001170077]
  + int_ic=[0 0])
          ...specifies a transfer function of the form...

```
_N(s) = 0.139713_ _s[2]+0.7464102_

_·_ _s[2]+0.998942s+0.00117077_

The s-domain transfer function includes gain and in_offset (input offset) parameters to allow
for tailoring of the required signal. There are no limits on the internal signal values or on
the output value of the s-domain transfer function, so you are cautioned to specify gain and
coefficient values that will not cause the model to produce excessively large values. In AC
analysis, the value returned is equal to the real and imaginary components of the total s-domain
transfer function at each frequency of interest.

The denormalized_freq term allows you to specify coefficients for a normalized filter (i.e. one
in which the frequency of interest is 1 rad/s). Once these coefficients are included, specifying
the denormalized frequency value ‘shifts’ the corner frequency to the actual one of interest. As
an example, the following transfer function describes a Chebyshev low-pass filter with a corner
(pass-band) frequency of 1 rad/s:


_N(s) = 0.139713_ 1.0

_·_ _s[2]+1.09773s+1.10251_


-----

In order to define an s_xfer model for the above, but with the corner frequency equal to 1500
rad/s (9425 Hz), the following instance and model lines would be needed:
```
  a12 node1 node2 cheby1
  .model cheby1 s_xfer(num_coeff=[1] den_coeff=[1 1.09773 1.10251]
  + int_ic=[0 0] denormalized_freq=1500)

```
In the above, you add the normalized coefficients and scale the filter through the use of the
denormalized freq parameter. Similar results could have been achieved by performing the denormalization prior to specification of the coefficients, and setting denormalized freq to the
value 1.0 (or not specifying the frequency, as the default is 1.0 rad/s) Note in the above that
frequencies are always specified as radians/second.

Truncation error checking is included in the s-domain transfer block. This should provide for
more accurate simulations, since the model will inherently request smaller time increments
between simulation points if truncation errors would otherwise be excessive.

The int_ic parameter is an array that must be of size one less as the array of values specified for
the den_coeff parameter. Even if a 0 start value is required, you have to add the specific int_ic
vector to the set of coefficients (see the examples above and below).
```
  Example SPICE Usage:
  a14 9 22 cheby_LP_3kHz
  .
  .
  .model cheby_LP_3kHz s_xfer(in_offset=0.0 gain=1.0 int_ic=[0 0]
  + num_coeff=[1.0]
  + den_coeff=[1.0 1.42562 1.51620])

### 12.2.17 Slew Rate Block
  NAME_TABLE:
  C_Function_Name: cm_slew
  Spice_Model_Name: slew
  Description: "A simple slew rate follower block"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_slope
  Description: "maximum rising slope value"
  Data_Type: real
  Default_Value: 1.0e9

```

-----

```
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: fall_slope
  Description: "maximum falling slope value"
  Data_Type: real
  Default_Value: 1.0e9
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: range
  Description: "smoothing range"
  Data_Type: real
  Default_Value: 0.1
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: This function is a simple slew rate block that limits the absolute slope of the**
output with respect to time to some maximum or value. The actual slew rate effects of
over-driving an amplifier circuit can thus be accurately modeled by cascading the amplifier with this model. The units used to describe the maximum rising and falling slope
values are expressed in volts or amperes per second. Thus a desired slew rate of 0.5 V/µs
will be expressed as 0.5e+6, etc.
The slew rate block will continue to raise or lower its output until the difference between
the input and the output values is zero. Thereafter, it will resume following the input signal, unless the slope again exceeds its rise or fall slope limits. The range input specifies
a smoothing region above or below the input value. Whenever the model is slewing and
the output comes to within the input + or - the range value, the partial derivative of the
output with respect to the input will begin to smoothly transition from 0.0 to 1.0. When
the model is no longer slewing (output = input), dout/din will equal 1.0.
```
  Example SPICE Usage:
  a15 1 2 slew1
  .model slew1 slew(rise_slope=0.5e6 fall_slope=0.5e6)

### 12.2.18 Inductive Coupling
  NAME_TABLE:
  C_Function_Name: cm_lcouple
  Spice_Model_Name: lcouple
  Description: "inductive coupling (for use with ’core’ model)"
  PORT_TABLE:

```

-----

```
  Port_Name: l mmf_out
  Description: "inductor" "mmf output (in ampere-turns)"
  Direction: inout inout
  Default_Type: hd hd
  Allowed_Types: [h,hd] [hd]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: num_turns
  Description: "number of inductor turns"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: This function is a conceptual model that is used as a building block to create a**
wide variety of inductive and magnetic circuit models. This function is normally used in
conjunction with the core model, but can also be used with resistors, hysteresis blocks,
etc. to build up systems that mock the behavior of linear and nonlinear components.
The lcouple takes as an input (on the ‘l’ port), a current. This current value is multiplied
by the num_turns value, N, to produce an output value (a voltage value that appears on the
```
  mmf_out port). The mmf_out acts similar to a magnetomotive force in a magnetic circuit;

```
when the lcouple is connected to the core model, or to some other resistive device, a
current will flow. This current value (which is modulated by whatever the lcouple is
connected to) is then used by the lcouple to calculate a voltage ‘seen’ at the l port. The
voltage is a function of the derivative with respect to time of the current value seen at
```
  mmf_out.

```
The most common use for lcouples will be as a building block in the construction of
transformer models. To create a transformer with a single input and a single output, you
would require two lcouple models plus one core model. The process of building up
such a transformer is described under the description of the core model, below.
```
  Example SPICE Usage:
  a150 (7 0) (9 10) lcouple1
  .model lcouple1 lcouple(num_turns=10.0)

### 12.2.19 Magnetic Core
  NAME_TABLE:
  C_Function_Name: cm_core
  Spice_Model_Name: core
  Description: "magnetic core"
  PORT_TABLE:
  Port_Name: mc
  Description: "magnetic core"

```

-----

```
Direction: inout
Default_Type: gd
Allowed_Types: [g,gd]
Vector: no
Vector_Bounds: Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: H_array B_array
Description: "magnetic field array" "flux density array"
Data_Type: real real
Default_Value: - Limits: - Vector: yes yes
Vector_Bounds: [2 -] [2 -]
Null_Allowed: no no
PARAMETER_TABLE:
Parameter_Name: area length
Description: "cross-sectional area" "core length"
Data_Type: real real
Default_Value: - Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: no no
PARAMETER_TABLE:
Parameter_Name: input_domain
Description: "input sm. domain"
Data_Type: real
Default_Value: 0.01
Limits: [1e-12 0.5]
Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: fraction
Description: "smoothing fraction/abs switch"
Data_Type: boolean
Default_Value: TRUE
Limits: Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: mode
Description: "mode switch (1 = pwl, 2 = hyst)"
Data_Type: int
Default_Value: 1
Limits: [1 2]

```

-----

```
  Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: in_low in_high
  Description: "input low value" "input high value"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: hyst out_lower_limit
  Description: "hysteresis" "output lower limit"
  Data_Type: real real
  Default_Value: 0.1 0.0
  Limits: [0 -]   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: out_upper_limit
  Description: "output upper limit"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: This function is a conceptual model that is used as a building block to create**
a wide variety of inductive and magnetic circuit models. This function is almost always
expected to be used in conjunction with the lcouple model to build up systems that mock
the behavior of linear and nonlinear magnetic components. There are two fundamental
modes of operation for the core model. These are the pwl mode (which is the default, and
which is the most likely to be of use to you) and the hysteresis mode. These are detailed
below.

PWL Mode (mode = 1)

The core model in PWL mode takes as input a voltage that it treats as a magnetomotive force
(mmf) value. This value is divided by the total effective length of the core to produce a value
for the Magnetic Field Intensity, H. This value of H is then used to find the corresponding Flux
Density, B, using the piecewise linear relationship described by you in the H array / B array
coordinate pairs. B is then multiplied by the cross-sectional area of the core to find the Flux
value, which is output as a current. The pertinent mathematical equations are listed below:


-----

H = mmf =L, where L = Length

Here H, the Magnetic Field Intensity, is expressed in ampere-turns/meter.

B = f (H)

The B value is derived from a piecewise linear transfer function described to the model via
the (H_array[],B_array[]) parameter coordinate pairs. This transfer function does not include
hysteretic effects; for that, you would need to substitute a HYST model for the core.

_φ = BA, where A = Area_

The final current allowed to flow through the core is equal to φ . This value in turn is used by
the "lcouple" code model to obtain a value for the voltage reflected back across its terminals to
the driving electrical circuit.

The following example code shows the use of two lcouple models and one core model to
produce a simple primary/secondary transformer.
```
  Example SPICE Usage:
  a1 (2 0) (3 0) primary
  .model primary lcouple (num_turns = 155)
  a2 (3 4) iron_core
  .model iron_core core (H_array = [-1000 -500 -375 -250 -188 -125 -63 0
  + 63 125 188 250 375 500 1000]
  + B_array = [-3.13e-3 -2.63e-3 -2.33e-3 -1.93e-3
  + -1.5e-3 -6.25e-4 -2.5e-4 0 2.5e-4
  + 6.25e-4 1.5e-3 1.93e-3 2.33e-3
  + 2.63e-3 3.13e-3]
  + area = 0.01 length = 0.01)
  a3 (5 0) (4 0) secondary
  .model secondary lcouple (num_turns = 310)

```
HYSTERESIS Mode (mode = 2)

The core model in HYSTERESIS mode takes as input a voltage that it treats as a magnetomotive
force (mmf) value. This value is used as input to the equivalent of a hysteresis code model block.
The parameters defining the input low and high values, the output low and high values, and the
amount of hysteresis are as in that model. The output from this mode, as in PWL mode, is a
current value that is seen across the mc port. An example of the core model used in this fashion
is shown below:
```
  Example SPICE Usage:
  a1 (2 0) (3 0) primary
  .model primary lcouple (num_turns = 155)
  a2 (3 4) iron_core
  .model iron_core core (mode = 2 in_low=-7.0 in_high=7.0
  + out_lower_limit=-2.5e-4 out_upper_limit=2.5e-4
  + hyst = 2.3 )
  a3 (5 0) (4 0) secondary
  .model secondary lcouple (num_turns = 310)

```

-----

_One final note to be made about the two core model nodes is that certain parameters are avai-_
_lable in one mode, but not in the other. In particular, the in_low, in_high, out_lower_limit,_
out_upper_limit, and hysteresis parameters are not available in PWL mode. Likewise, the
H_array, B_array, area, and length values are unavailable in HYSTERESIS mode. The input
domain and fraction parameters are common to both modes (though their behavior is somewhat
different; for explanation of the input domain and fraction values for the HYSTERESIS mode,
you should refer to the hysteresis code model discussion).

### 12.2.20 Controlled Sine Wave Oscillator
```
  NAME_TABLE:
  C_Function_Name: cm_sine
  Spice_Model_Name: sine
  Description: "controlled sine wave oscillator"
  PORT_TABLE:
  Port Name: cntl_in out
  Description: "control input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: cntl_array freq_array
  Description: "control array" "frequency array"
  Data_Type: real real
  Default_Value: 0.0 1.0e3
  Limits: - [0 -]
  Vector: yes yes
  Vector_Bounds: [2 -] cntl_array
  Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: out_low out_high
  Description: "output peak low value" "output peak high value"
  Data_Type: real real
  Default_Value: -1.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: This function is a controlled sine wave oscillator with parametrizable values of**
low and high peak output. It takes an input voltage or current value. This value is used as
the independent variable in the piecewise linear curve described by the coordinate points
of the cntl array and freq array pairs. From the curve, a frequency value is determined,
and the oscillator will output a sine wave at that frequency. From the above, it is easy
to see that array sizes of 2 for both the cntl array and the freq array will yield a linear


-----

variation of the frequency with respect to the control input. Any sizes greater than 2 will
yield a piecewise linear transfer characteristic. For more detail, refer to the description of
the piecewise linear controlled source, which uses a similar method to derive an output
value given a control input.
```
  Example SPICE Usage:
  asine 1 2 in_sine
  .model in_sine sine(cntl_array = [-1 0 5 6]
  + freq_array=[10 10 1000 1000] out_low = -5.0
  + out_high = 5.0)

### 12.2.21 Controlled Triangle Wave Oscillator
  NAME_TABLE:
  C_Function_Name: cm_triangle
  Spice_Model_Name: triangle
  Description: "controlled triangle wave oscillator"
  PORT_TABLE:
  Port Name: cntl_in out
  Description: "control input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: cntl_array freq_array
  Description: "control array" "frequency array"
  Data_Type: real real
  Default_Value: 0.0 1.0e3
  Limits: - [0 -]
  Vector: yes yes
  Vector_Bounds: [2 -] cntl_array
  Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: out_low out_high
  Description: "output peak low value" "output peak high value"
  Data_Type: real real
  Default_Value: -1.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: duty_cycle
  Description: "rise time duty cycle"
  Data_Type: real

```

-----

```
  Default_Value: 0.5
  Limits: [1e-10 0.999999999]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: This function is a controlled triangle/ramp wave oscillator with parametrizable**
values of low and high peak output and rise time duty cycle. It takes an input voltage or
current value. This value is used as the independent variable in the piecewise linear curve
described by the coordinate points of the cntl_array and freq_array pairs.
From the curve, a frequency value is determined, and the oscillator will output a triangle
wave at that frequency. From the above, it is easy to see that array sizes of 2 for both the
cntl_array and the freq_array will yield a linear variation of the frequency with respect to
the control input. Any sizes greater than 2 will yield a piecewise linear transfer characteristic. For more detail, refer to the description of the piecewise linear controlled source,
which uses a similar method to derive an output value given a control input.
```
  Example SPICE Usage:
  ain 1 2 ramp1
  .model ramp1 triangle(cntl_array = [-1 0 5 6]
  + freq_array=[10 10 1000 1000] out_low = -5.0
  + out_high = 5.0 duty_cycle = 0.9)

### 12.2.22 Controlled Square Wave Oscillator
  NAME_TABLE:
  C_Function_Name: cm_square
  Spice_Model_Name: square
  Description: "controlled square wave oscillator"
  PORT_TABLE:
  Port Name: cntl_in out
  Description: "control input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: cntl_array freq_array
  Description: "control array" "frequency array"
  Data_Type: real real
  Default_Value: 0.0 1.0e3
  Limits: - [0 -]
  Vector: yes yes
  Vector_Bounds: [2 -] cntl_array
  Null_Allowed: no no
  PARAMETER_TABLE:

```

-----

```
  Parameter_Name: out_low out_high
  Description: "output peak low value" "output peak high value"
  Data_Type: real real
  Default_Value: -1.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER.TABLE:
  Parameter_Name: duty_cycle rise_time
  Description: "duty cycle" "output rise time"
  Data_Type: real real
  Default_Value: 0.5 1.0e-9
  Limits: [1e-6 0.999999]   Vector: no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: fall_time
  Description: "output fall time"
  Data_Type: real
  Default_Value: 1.0e-9
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: This function is a controlled square wave oscillator with parametrizable values**
of low and high peak output, duty cycle, rise time, and fall time. It takes an input voltage
or current value. This value is used as the independent variable in the piecewise linear
curve described by the coordinate points of the cntl_array and freq_array pairs. From the
curve, a frequency value is determined, and the oscillator will output a square wave at
that frequency.
From the above, it is easy to see that array sizes of 2 for both the cntl_array and the
freq_array will yield a linear variation of the frequency with respect to the control input.
Any sizes greater than 2 will yield a piecewise linear transfer characteristic. For more
detail, refer to the description of the piecewise linear controlled source, which uses a
similar method to derive an output value given a control input.
```
  Example SPICE Usage:
  ain 1 2 pulse1
  .model pulse1 square(cntl_array = [-1 0 5 6]
  + freq_array=[10 10 1000 1000] out_low = 0.0
  + out_high = 4.5 duty_cycle = 0.2
  + rise_time = 1e-6 fall_time = 2e-6)

### 12.2.23 Controlled One-Shot
  NAME_TABLE:

```

-----

```
C_Function_Name: cm_oneshot
Spice_Model_Name: oneshot
Description: "controlled one-shot"
PORT_TABLE:
Port Name: clk cntl_in
Description: "clock input" "control input"
Direction: in in
Default_Type: v v
Allowed_Types: [v,vd,i,id] [v,vd,i,id]
Vector: no no
Vector_Bounds: - Null_Allowed: no yes
PORT_TABLE:
Port Name: clear out
Description: "clear signal" "output"
Direction: in out
Default_Type: v v
Allowed_Types: [v,vd,i,id] [v,vd,i,id]
Vector: no no
Vector_Bounds: - Null_Allowed: yes no
PARAMETER_TABLE:
Parameter_Name: clk_trig retrig
Description: "clock trigger value" "retrigger switch"
Data_Type: real boolean
Default_Value: 0.5 FALSE
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: no yes
PARAMETER_TABLE:
Parameter_Name: pos_edge_trig
Description: "positive/negative edge trigger switch"
Data_Type: boolean
Default_Value: TRUE
Limits: Vector: no
Vector_Bounds: Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: cntl_array pw_array
Description: "control array" "pulse width array"
Data_Type: real real
Default_Value: 0.0 1.0e-6
Limits: - [0.00 -]
Vector: yes yes
Vector_Bounds: - cntl_array
Null_Allowed: yes yes

```

-----

```
  PARAMETER_TABLE:
  Parameter_Name: out_low out_high
  Description: "output low value" "output high value"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: fall_time rise_time
  Description: "output fall time" "output rise time"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay
  Description: "output delay from trigger"
  Data_Type: real
  Default_Value: 1.0e-9
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: fall_delay
  Description: "output delay from pw"
  Data_Type: real
  Default_Value: 1.0e-9
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: This function is a controlled oneshot with parametrizable values of low and high**
peak output, input trigger value level, delay, and output rise and fall times. It takes an
input voltage or current value. This value is used as the independent variable in the
piecewise linear curve described by the coordinate points of the cntl_array and pw_array
pairs. From the curve, a pulse width value is determined. The one-shot will output a
pulse of that width, triggered by the clock signal (rising or falling edge), delayed by the
delay value, and with specified rise and fall times. A positive slope on the clear input will
immediately terminate the pulse, which resets with its fall time.
From the above, it is easy to see that array sizes of 2 for both the cntl_array and the
pw_array will yield a linear variation of the pulse width with respect to the control input.
Any sizes greater than 2 will yield a piecewise linear transfer characteristic. For more


-----

detail, refer to the description of the piecewise linear controlled source, which uses a
similar method to derive an output value given a control input.
```
  Example SPICE Usage:
  ain 1 2 3 4 pulse2
  .model pulse2 oneshot(cntl_array = [-1 0 10 11]
  + pw_array=[1e-6 1e-6 1e-4 1e-4]
  + clk_trig = 0.9 pos_edge_trig = FALSE
  + out_low = 0.0 out_high = 4.5
  + rise_delay = 20.0-9 fall_delay = 35.0e-9)

### 12.2.24 Capacitance Meter
  NAME_TABLE:
  C_Function_Name: cm_cmeter
  Spice_Model_Name: cmeter
  Description: "capacitance meter"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: gain
  Description: "gain"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The capacitance meter is a sensing device that is attached to a circuit node and**
produces as an output a scaled value equal to the total capacitance seen on its input multiplied by the gain parameter. This model is primarily intended as a building block for
other models that must sense a capacitance value and alter their behavior based upon it.
```
  Example SPICE Usage:
  atest1 1 2 ctest
  .model ctest cmeter(gain=1.0e12)

### 12.2.25 Inductance Meter
  NAME_TABLE:

```

-----

```
  C_Function_Name: cm_lmeter
  Spice_Model_Name: lmeter
  Description: "inductance meter"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v v
  Allowed_Types: [v,vd,i,id] [v,vd,i,id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: gain
  Description: "gain"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The inductance meter is a sensing device that is attached to a circuit node and**
produces as an output a scaled value equal to the total inductance seen on its input multiplied by the gain parameter. This model is primarily intended as a building block for
other models that must sense an inductance value and alter their behavior based upon it.
```
  Example SPICE Usage:
  atest2 1 2 ltest
  .model ltest lmeter(gain=1.0e6)

### 12.2.26 Memristor
  NAME_TABLE:
  C_Function_Name: cm_memristor
  Spice_Model_Name: memristor
  Description: "Memristor Interface"
  PORT_TABLE:
  Port_Name: memris
  Description: "memristor terminals"
  Direction: inout
  Default_Type: gd
  Allowed_Types: [gd]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: rmin rmax

```

-----

```
  Description: "minimum resistance" "maximum resistance"
  Data_Type: real real
  Default_Value: 10.0 10000.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rinit vt
  Description: "initial resistance" "threshold"
  Data_Type: real real
  Default_Value: 7000.0 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: alpha beta
  Description: "model parameter 1" "model parameter 2"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: no no

```
**Description: The memristor is a two-terminal resistor with memory, whose resistance depends**
on the time integral of the voltage across its terminals. rmin and rmax provide the lower
and upper limits of the resistance, rinit is its starting value (no voltage applied so far).
The voltage has to be above a threshold vt to become effective in changing the resistance.
alpha and beta are two model parameters. The memristor code model is derived from a
SPICE subcircuit published in [23].
```
  Example SPICE Usage:
  amen 1 2 memr
  .model memr memristor (rmin=1k rmax=10k rinit=7k
  + alpha=0 beta=2e13 vt=1.6)

### 12.2.27 2D table model
  NAME_TABLE:
  C_Function_Name: cm_table2D
  Spice_Model_Name: table2D
  Description: "2D table model"
  PORT_TABLE:
  Port_Name: inx iny out
  Description: "inputx" "inputy" "output"
  Direction: in in out

```

-----

```
  Default_Type: v v i
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id,vnam] [v,vd,i,id]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: no no no
  PARAMETER_TABLE:
  Parameter_Name: order verbose
  Description: "order" "verbose"
  Data_Type: int int
  Default_Value: 3 0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: offset gain
  Description: "offset" "gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: file
  Description: "file name"
  Data_Type: string
  Default_Value: "2D-table-model.txt"
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The 2D table model reads a matrix from file "file name" (default 2D-table-**
model.txt) which has x columns and y rows. Each x,y pair, addressed by inx and iny,
yields an output value out. Linear interpolation is used for out, eno (essentially non
oscillating) interpolation for its derivatives. Parameters offset (default 0) and gain (default 1) modify the output table values according to of fset + _gain out. Parameter order_
(default 3) influences the calculation of the derivatives. Parameter verbose (default 0)
yields test outputs, if set to 1 or 2. The table format is shown below. Be careful to include
the data point inx = 0, iny = 0 into your table, because ngspice uses these during .OP
computations. The x horizontal and y vertical address values have to increase monotonically. The usage example consists of two input voltages referenced to ground and a
current source output with two floating nodes.
```
  Table Example:
  * table source
  * number of columns (x)

```

-----

```
  8
  * number of rows (y)
  9
  * x horizontal (column) address values (real numbers)
  -1 0 1 2 3 4 5 6
  * y vertical (row) address values (real numbers)
  -0.6 0 0.6 1.2 1.8 2.4 3.0 3.6 4.2
  * table with output data (horizontally addressed by x, vertically by y)
  1 0.9 0.8 0.7 0.6 0.5 0.4 0.3
  1 1 1 1 1 1 1 1
  1 1.2 1.4 1.6 1.8 2 2.2 2.4
  1 1.5 2 2.5 3 3.5 4 4.5
  1 2 3 4 5 6 7 8
  1 2.5 4 5.5 7 8.5 10 11.5
  1 3 5 7 9 11 13 15
  1 3.5 6 8.5 11 13.5 16 18.5
  1 4 7 10 13 16 19 22
  Example SPICE Usage:
  atab inx iny %id(out1 out2) tabmod
  .model tabmod table2d (offset=0.0 gain=1 order=3 file="table-simple.txt")

### 12.2.28 3D table model
  NAME_TABLE:
  C_Function_Name: cm_table3D
  Spice_Model_Name: table3D
  Description: "3D table model"
  PORT_TABLE:
  Port_Name: inx iny inz
  Description: "inputx" "inputy" "inputz"
  Direction: in in in
  Default_Type: v v v
  Allowed_Types: [v,vd,i,id,vnam] [v,vd,i,id,vnam] [v,vd,i,id,vnam]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: no no no
  PORT_TABLE:
  Port_Name: out
  Description: "output"
  Direction: out
  Default_Type: i
  Allowed_Types: [v,vd,i,id]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: order verbose
  Description: "order" "verbose"

```

-----

```
  Data_Type: int int
  Default_Value: 3 0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: offset gain
  Description: "offset" "gain"
  Data_Type: real real
  Default_Value: 0.0 1.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: file
  Description: "file name"
  Data_Type: string
  Default_Value: "3D-table-model.txt"
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The 3D table model reads a matrix from file "file name" (default 3D-table-**
model.txt) which has x columns, y rows per table and z tables. Each x,y,z triple, addressed by inx, iny, and inz, yields an output value out. Linear interpolation is used
for out, eno (essentially non oscillating) interpolation for its derivatives. Parameters
```
  offset (default 0) and gain (default 1) modify the output table values according to

```
_o f fset + gain out. Parameter order (default 3) influences the calculation of the deri-_
vatives. Parameter verbose (default 0) yields test outputs, if set to 1 or 2. The table
format is shown below. Be careful to include the data point inx = 0, iny = 0, inz = 0 into
your table, because ngspice needs these to for the .OP calculation. The x horizontal, y
vertical, and z table address values have to increase monotonically. The usage example
simulates a NMOS transistor with independent drain, gate and bulk nodes, referenced to
source. Parameter gain may be used to emulate transistor width, with respect to the table
transistor.
```
  Table Example:
  * 3D table for nmos bsim 4, W=10um, L=0.13um
  *x
  39
  *y
  39
  *z
  11
  *x (drain voltage)

```

-----

```
  -0.1 -0.05 0 0.05 0.1 0.15 0.2 0.25 ...
  *y (gate voltage)
  -0.1 -0.05 0 0.05 0.1 0.15 0.2 0.25 ...
  *z (substrate voltage)
  -1.8 -1.6 -1.4 -1.2 -1 -0.8 -0.6 -0.4 -0.2 0 0.2
  *table -1.8
  -4.50688E-10 -4.50613E-10 -4.50601E-10 -4.50599E-10 ...
  -4.49622E-10 -4.49267E-10 -4.4921E-10 -4.49202E-10 ...
  -4.50672E-10 -4.49099E-10 -4.48838E-10 -4.48795E-10 ...
  -4.55575E-10 -4.4953E-10 -4.48435E-10 -4.48217E-10 ...
  ...
  *table -1.6
  -3.10015E-10 -3.09767E-10 -3.0973E-10 -3.09724E-10 ...
  -3.09748E-10 -3.08524E-10 -3.08339E-10 -3.08312E-10 ...
  ...
  *table -1.4
  -2.04848E-10 -2.04008E-10 -2.03882E-10 ...
  -2.07275E-10 -2.03117E-10 -2.02491E-10 ...
  ...
  Example SPICE Usage:
  amos1 %vd(d s) %vd(g s) %vd(b s) %id(d s) mostable1
  .model mostable1 table3d (offset=0.0 gain=0.5 order=3
  + verbose=1 file="table-3D-bsim4n.txt")

## 12.3 Hybrid Models

```
The following hybrid models are supplied with XSPICE. The descriptions included below consist of the model Interface Specification File and a description of the model’s operation. This
is followed by an example of a simulator-deck placement of the model, including the .MODEL
card and the specification of all available parameters.

A note should be made with respect to the use of hybrid models for other than simple digital-toanalog and analog-to-digital translations. The hybrid models represented in this section address
that specific need, but in the development of user-defined nodes you may find a need to translate
not only between digital and analog nodes, but also between real and digital, real and int, etc.
In most cases such translations will not need to be as involved or as detailed as shown in the
following.

### 12.3.1 Digital-to-Analog Node Bridge
```
  NAME_TABLE:
  C_Function_Name: cm_dac_bridge
  Spice_Model_Name: dac_bridge
  Description: "digital-to-analog node bridge"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"

```

-----

```
  Direction: in out
  Default_Type: d v
  Allowed_Types: [d] [v,vd,i,id,d]
  Vector: yes yes
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: out_low
  Description: "0-valued analog output"
  Data_Type: real
  Default_Value: 0.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: out_high
  Description: "1-valued analog output"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: out_undef input_load
  Description: "U-valued analog output" "input load (F)"
  Data_Type: real real
  Default_Value: 0.5 1.0e-12
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: t_rise t_fall
  Description: "rise time 0->1" "fall time 1->0"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The dac_bridge is the first of two node bridge devices designed to allow for**
the ready transfer of digital information to analog values and back again. The second
device is the adc_bridge (which takes an analog value and maps it to a digital one).The
```
  dac_bridge takes as input a digital value from a digital node. This value by definition

```
may take on only one of the values ‘0’, ‘1’ or ‘U’. The dac_bridge then outputs the value


-----

```
  out_low, out_high or out_undef, or ramps linearly toward one of these ‘final’ values

```
from its current analog output level. The speed at which this ramping occurs depends
on the values of t_rise and t_fall. These parameters are interpreted by the model
such that the rise or fall slope generated is always constant. Note that the dac_bridge
_includes test code in its cfunc.mod file for determining the presence of the out_undef para-_
_meter. If this parameter is not specified by you, and if out_high and out_low values are_
_specified, then out_undef is assigned the value of the arithmetic mean of out_high and_
```
  out_low. This simplifies coding of output buffers, where typically a logic family will

```
include an out_low and out_high voltage, but not an out_undef value. This model
also posts an input load value (in farads) based on the parameter input load.
```
  Example SPICE Usage:
  abridge1 [7] [2] dac1
  .model dac1 dac_bridge(out_low = 0.7 out_high = 3.5 out_undef = 2.2
  + input_load = 5.0e-12 t_rise = 50e-9
  + t_fall = 20e-9)

### 12.3.2 Analog-to-Digital Node Bridge
  NAME_TABLE:
  C_Function_Name: cm_adc_bridge
  Spice_Model_Name: adc_bridge
  Description: "analog-to-digital node bridge"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: v d
  Allowed_Types: [v,vd,i,id,d] [d]
  Vector: yes yes
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_low
  Description: "maximum 0-valued analog input"
  Data_Type: real
  Default_Value: 1.0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: in_high
  Description: "minimum 1-valued analog input"
  Data_Type: real
  Default_Value: 2.0
  Limits:   Vector: no

```

-----

```
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The adc_bridge is one of two node bridge devices designed to allow for the**
ready transfer of analog information to digital values and back again. The second device
is the dac_bridge (which takes a digital value and maps it to an analog one). The
```
  adc_bridge takes as input an analog value from an analog node. This value by definition

```
may be in the form of a voltage, or a current. If the input value is less than or equal to
in_low, then a digital output value of ‘0’ is generated. If the input is greater than or equal
to in_high, a digital output value of ‘1’ is generated. If neither of these is true, then
a digital ‘UNKNOWN’ value is output. Note that unlike the case of the dac_bridge,
no ramping time or delay is associated with the adc_bridge. Rather, the continuous
ramping of the input value provides for any associated delays in the digitized signal.
```
  Example SPICE Usage:
  abridge2 [1] [8] adc_buff
  .model adc_buff adc_bridge(in_low = 0.3 in_high = 3.5)

### 12.3.3 Controlled Digital Oscillator
  NAME_TABLE:
  C_Function_Name: cm_d_osc
  Spice_Model_Name: d_osc
  Description: "controlled digital oscillator"
  PORT_TABLE:
  Port Name: cntl_in out
  Description: "control input" "output"
  Direction: in out
  Default_Type: v d
  Allowed_Types: [v,vd,i,id] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: cntl_array freq_array
  Description: "control array" "frequency array"
  Data_Type: real real
  Default_Value: 0.0 1.0e6
  Limits: - [0 -]

```

-----

```
  Vector: yes yes
  Vector_Bounds: [2 -] cntl_array
  Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: duty_cycle init_phase
  Description: "duty cycle" "initial phase of output"
  Data_Type: real real
  Default_Value: 0.5 0
  Limits: [1e-6 0.999999] [-180.0 +360.0]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1e-9 1e-9
  Limits: [0 -] [0 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The digital oscillator is a hybrid model that accepts as input a voltage or current.**
This input is compared to the voltage-to-frequency transfer characteristic specified by the
```
  cntl_array/freq_array coordinate pairs, and a frequency is obtained that represents

```
a linear interpolation or extrapolation based on those pairs. A digital time-varying signal
is then produced with this fundamental frequency.
The output waveform, which is the equivalent of a digital clock signal, has rise and fall
delays that can be specified independently. In addition, the duty cycle and the phase of
the waveform are also variable and can be set by you.
```
  Example SPICE Usage:
  a5 1 8 var_clock
  .model var_clock d_osc(cntl_array = [-2 -1 1 2]
  + freq_array = [1e3 1e3 10e3 10e3]
  + duty_cycle = 0.4 init_phase = 180.0
  + rise_delay = 10e-9 fall_delay=8e-9)

### 12.3.4 Node bridge from digital to real with enable
  NAME_TABLE:
  Spice_Model_Name: d_to_real
  C_Function_Name: ucm_d_to_real
  Description: "Node bridge from digital to real with enable"
  PORT_TABLE:
  Port_Name: in enable out
  Description: "input" "enable" "output"
  Direction: in in out

```

-----

```
  Default_Type: d d real
  Allowed_Types: [d] [d] [real]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: no yes no
  PARAMETER_TABLE:
  Parameter_Name: zero one delay
  Description: "value for 0" "value for 1" "delay"
  Data_Type: real real real
  Default_Value: 0.0 1.0 1e-9
  Limits: - - [1e-15 -]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: yes yes yes

### 12.3.5 A Z**-1 block working on real data
  NAME_TABLE:
  Spice_Model_Name: real_delay
  C_Function_Name: ucm_real_delay
  Description: "A Z ** -1 block working on real data"
  PORT_TABLE:
  Port_Name: in clk out
  Description: "input" "clock" "output"
  Direction: in in out
  Default_Type: real d real
  Allowed_Types: [real] [d] [real]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: no no no
  PARAMETER_TABLE:
  Parameter_Name: delay
  Description: "delay from clk to out"
  Data_Type: real
  Default_Value: 1e-9
  Limits: [1e-15 -]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes

 12.3.6 A gain block for event-driven real data
  NAME_TABLE:
  Spice_Model_Name: real_gain
  C_Function_Name: ucm_real_gain
  Description: "A gain block for event-driven real data"
  PORT_TABLE:
  Port_Name: in out

```

-----

```
  Description: "input" "output"
  Direction: in out
  Default_Type: real real
  Allowed_Types: [real] [real]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: in_offset gain out_offset
  Description: "input offset" "gain" "output offset"
  Data_Type: real real real
  Default_Value: 0.0 1.0 0.0
  Limits: - -   Vector: no no no
  Vector_Bounds: - -   Null_Allowed: yes yes yes
  PARAMETER_TABLE:
  Parameter_Name: delay ic
  Description: "delay" "initial condition"
  Data_Type: real real
  Default_Value: 1.0e-9 0.0
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

### 12.3.7 Node bridge from real to analog voltage
  NAME_TABLE:
  Spice_Model_Name: real_to_v
  C_Function_Name: ucm_real_to_v
  Description: "Node bridge from real to analog voltage"
  PORT_TABLE:
  Port_Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: real v
  Allowed_Types: [real] [v, vd, i, id]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: gain transition_time
  Description: "gain" "output transition time"
  Data_Type: real real
  Default_Value: 1.0 1e-9
  Limits: - [1e-15 -]
  Vector: no no

```

-----

```
  Vector_Bounds: -   Null_Allowed: yes yes

## 12.4 Digital Models

```
The following digital models are supplied with XSPICE. The descriptions included below consist of an example model Interface Specification File and a description of the model’s operation. This is followed by an example of a simulator-deck placement of the model, including the
```
.MODEL card and the specification of all available parameters. Note that these models have not

```
been finalized at this time.

Some information common to all digital models and/or digital nodes is included here. The following are general rules that should make working with digital nodes and models more straightforward:

1. All digital nodes are initialized to ZERO at the start of a simulation (i.e., when INIT=TRUE).
This means that a model need not post an explicit value to an output node upon initialization if its output would normally be a ZERO (although posting such would certainly
cause no harm).

2. Digital nodes may have one out of twelve possible node values. See 12.5.1 for details.

3. Digital models typically have defined their rise and fall delays for their output signals. A
capacitive input load value may be defined as well to determine a load-dependent delay,
but is currently not used in any code model (see 28.7.1.4).

4. Several commands are available for outputting data, e.g. eprint, edisplay, and eprvcd.
Digital inputs may be read from files. Please see Chapt. 12.5.4 for more details.

5. Hybrid models (see Chapt. 12.3) provide an interface between the digital event driven
world and the analog world of ngspice to enable true mixed mode simulation.

### 12.4.1 Buffer
```
  NAME_TABLE:
  C_Function_Name: cm_d_buffer
  Spice_Model_Name: d_buffer
  Description: "digital one-bit-wide buffer"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:

```

-----

```
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The buffer is a single-input, single-output digital buffer that produces as output**
a time-delayed copy of its input. The delays associated with an output rise and those
associated with an output fall may be different. The model also posts an input load value
(in farads) based on the parameter input load. The output of this model does not, however,
respond to the total loading it sees on its output; it will always drive the output strongly
with the specified delays.
```
  Example SPICE Usage:
  a6 1 8 buff1
  .model buff1 d_buffer(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.2 Inverter
  NAME_TABLE:
  C_Function_Name: cm_d_inverter
  Spice_Model_Name: d_inverter
  Description: "digital one-bit-wide inverter"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"

```

-----

```
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The inverter is a single-input, single-output digital inverter that produces as out-**
put an inverted, time-delayed copy of its input. The delays associated with an output rise
and those associated with an output fall may be specified independently. The model also
posts an input load value (in farads) based on the parameter input load. The output of this
model does not, however, respond to the total loading it sees on its output; it will always
drive the output strongly with the specified delays.
```
  Example SPICE Usage:
  a6 1 8 inv1
  .model inv1 d_inverter(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.3 And
  NAME_TABLE:
  C_Function_Name: cm_d_and
  Spice_Model_Name: d_and
  Description: "digital ‘and’ gate"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9

```

-----

```
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital and gate is an n-input, single-output and gate that produces an active**
‘1’ value if, and only if, all of its inputs are also ‘1’ values. If ANY of the inputs is a
‘0’, the output will also be a ‘0’; if neither of these conditions holds, the output will be
unknown. The delays associated with an output rise and those associated with an output
fall may be specified independently. The model also posts an input load value (in farads)
based on the parameter input load. The output of this model does not, however, respond
to the total loading it sees on its output; it will always drive the output strongly with the
specified delays.
```
  Example SPICE Usage:
  a6 [1 2] 8 and1
  .model and1 d_and(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.4 Nand
  NAME_TABLE:
  C_Function_Name: cm_d_nand
  Spice_Model_Name: d_nand
  Description: "digital ‘nand’ gate"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9

```

-----

```
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital nand gate is an n-input, single-output nand gate that produces an**
active ‘0’ value if and only if all of its inputs are ‘1’ values. If ANY of the inputs is a ‘0’,
the output will be a ‘1’; if neither of these conditions holds, the output will be unknown.
The delays associated with an output rise and those associated with an output fall may be
specified independently. The model also posts an input load value (in farads) based on
the parameter input load. The output of this model does not, however, respond to the total
loading it sees on its output; it will always drive the output strongly with the specified
delays.
```
  Example SPICE Usage:
  a6 [1 2 3] 8 nand1
  .model nand1 d_nand(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.5 Or
  NAME_TABLE:
  C_Function_Name: cm_d_or
  Spice_Model_Name: d_or
  Description: "digital ‘or’ gate"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9

```

-----

```
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital or gate is an n-input, single-output or gate that produces an active**
‘1’ value if at least one of its inputs is a ‘1’ value. The gate produces a ‘0’ value if
all inputs are ‘0’; if neither of these two conditions holds, the output is unknown. The
delays associated with an output rise and those associated with an output fall may be
specified independently. The model also posts an input load value (in farads) based on
the parameter input load. The output of this model does not, however, respond to the total
loading it sees on its output; it will always drive the output strongly with the specified
delays.
```
  Example SPICE Usage:
  a6 [1 2 3] 8 or1
  .model or1 d_or(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.6 Nor
  NAME_TABLE:
  C_Function_Name: cm_d_nor
  Spice_Model_Name: d_nor
  Description: "digital ‘nor’ gate"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9

```

-----

```
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital nor gate is an n-input, single-output nor gate that produces an active**
‘0’ value if at least one of its inputs is a ‘1’ value. The gate produces a ‘0’ value if
all inputs are ‘0’; if neither of these two conditions holds, the output is unknown. The
delays associated with an output rise and those associated with an output fall may be
specified independently. The model also posts an input load value (in farads) based on
the parameter input load. The output of this model does not, however, respond to the total
loading it sees on its output; it will always drive the output strongly with the specified
delays.
```
  Example SPICE Usage:
  anor12 [1 2 3 4] 8 nor12
  .model nor12 d_or(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.7 Xor
  NAME_TABLE:
  C_Function_Name: cm_d_xor
  Spice_Model_Name: d_xor
  Description: "digital exclusive-or gate"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9

```

-----

```
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital xor gate is an n-input, single-output xor gate that produces an active**
‘1’ value if an odd number of its inputs are also ‘1’ values. The delays associated with an
output rise and those associated with an output fall may be specified independently.
The model also posts an input load value (in farads) based on the parameter input load.
The output of this model does not, however, respond to the total loading it sees on its
output; it will always drive the output strongly with the specified delays. Note also that
to maintain the technology-independence of the model, any UNKNOWN input, or any
floating input causes the output to also go UNKNOWN.
```
  Example SPICE Usage:
  a9 [1 2] 8 xor3
  .model xor3 d_xor(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.8 Xnor
  NAME_TABLE:
  C_Function_Name: cm_d_xnor
  Spice_Model_Name: d_xnor
  Description: "digital exclusive-nor gate"
  PORT_TABLE:
  Port Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [2 -]   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9

```

-----

```
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital xnor gate is an n-input, single-output xnor gate that produces an**
active ‘0’ value if an odd number of its inputs are also ‘1’ values. It produces a ‘1’ output
when an even number of ‘1’ values occurs on its inputs. The delays associated with an
output rise and those associated with an output fall may be specified independently. The
model also posts an input load value (in farads) based on the parameter input load. The
output of this model does not, however, respond to the total loading it sees on its output; it
will always drive the output strongly with the specified delays. Note also that to maintain
the technology-independence of the model, any UNKNOWN input, or any floating input
causes the output to also go UNKNOWN.
```
  Example SPICE Usage:
  a9 [1 2] 8 xnor3
  .model xnor3 d_xnor(rise_delay = 0.5e-9 fall_delay = 0.3e-9
  + input_load = 0.5e-12)

### 12.4.9 Tristate
  NAME_TABLE:
  C_Function_Name: cm_d_tristate
  Spice_Model_Name: d_tristate
  Description: "digital tristate buffer"
  PORT_TABLE:
  Port Name: in enable out
  Description: "input" "enable" "output"
  Direction: in in out
  Default_Type: d d d
  Allowed_Types: [d] [d] [d]
  Vector: no no no
  Vector_Bounds: - -   Null_Allowed: no no no
  PARAMETER_TABLE:
  Parameter_Name: delay
  Description: "delay"
  Data_Type: real

```

-----

```
  Default_Value: 1.0e-9
  Limits: [1.0e-12 -]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: enable_load
  Description: "enable load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital tristate is a simple tristate gate that can be configured to allow for**
open-collector behavior, as well as standard tristate behavior. The state seen on the input
line is reflected in the output. The state seen on the enable line determines the strength of
the output. Thus, a ONE forces the output to its state with a STRONG strength. A ZERO
forces the output to go to a HI_IMPEDANCE strength. The delays associated with an
output state or strength change cannot be specified independently, nor may they be specified independently for rise or fall conditions; other gate models may be used to provide
such delays if needed. The model posts input and enable load values (in farads) based
on the parameters input load and enable. The output of this model does not, however,
respond to the total loading it sees on its output; it will always drive the output with the
specified delay. Note also that to maintain the technology-independence of the model,
any UNKNOWN input, or any floating input causes the output to also go UNKNOWN.
Likewise, any UNKNOWN input on the enable line causes the output to go to an UNDETERMINED strength value.
```
  Example SPICE Usage:
  a9 1 2 8 tri7
  .model tri7 d_tristate(delay = 0.5e-9 input_load = 0.5e-12
  + enable_load = 0.5e-12)

### 12.4.10 Pullup
  NAME_TABLE:
  C_Function_Name: cm_d_pullup

```

-----

```
  Spice_Model_Name: d_pullup
  Description: "digital pullup resistor"
  PORT_TABLE:
  Port Name: out
  Description: "output"
  Direction: out
  Default_Type: d
  Allowed_Types: [d]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: load
  Description: "load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital pullup resistor is a device that emulates the behavior of an analog**
resistance value tied to a high voltage level. The pullup may be used in conjunction
with tristate buffers to provide open-collector wired or constructs, or any other logical
constructs that rely on a resistive pullup common to many tristated output devices. The
model posts an input load value (in farads) based on the parameter load.
```
  Example SPICE Usage:
  a2 9 pullup1
  .model pullup1 d_pullup(load = 20.0e-12)

### 12.4.11 Pulldown
  NAME_TABLE:
  C_Function_Name: cm_d_pulldown
  Spice_Model_Name: d_pulldown
  Description: "digital pulldown resistor"
  PORT_TABLE:
  Port Name: out
  Description: "output"
  Direction: out
  Default_Type: d
  Allowed_Types: [d]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: load

```

-----

```
  Description: "load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital pulldown resistor is a device that emulates the behavior of an analog**
resistance value tied to a low voltage level. The pulldown may be used in conjunction
with tristate buffers to provide open-collector wired or constructs, or any other logical
constructs that rely on a resistive pulldown common to many tristated output devices.
The model posts an input load value (in farads) based on the parameter load.
```
  Example SPICE Usage:
  a4 9 pulldown1
  .model pulldown1 d_pulldown(load = 20.0e-12)

### 12.4.12 D Flip Flop
  NAME_TABLE:
  C_Function_Name: cm_d_dff
  Spice_Model_Name: d_dff
  Description: "digital d-type flip flop"
  PORT_TABLE:
  Port Name: data clk
  Description: "input data" "clock"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PORT_TABLE:
  Port Name: set reset
  Description: "asynch. set" "asynch. reset"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PORT_TABLE:
  Port Name: out Nout
  Description: "data output" "inverted data output"
  Direction: out out
  Default_Type: d d
  Allowed_Types: [d] [d]

```

-----

```
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: clk_delay set_delay
Description: "delay from clk" "delay from set"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: reset_delay ic
Description: "delay from reset" "output initial state"
Data_Type: real int
Default_Value: 1.0e-9 0
Limits: [1.0e-12 -] [0 2]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: data_load clk_load
Description: "data load value (F)" "clk load value (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: set_load reset_load
Description: "set load value (F)" "reset load (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector.Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: rise_delay fall_delay
Description: "rise delay" "fall delay"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes

```

-----

**Description: The digital d-type flip flop is a one-bit, edge-triggered storage element that will**
store data whenever the clk input line transitions from low to high (ZERO to ONE). In
addition, asynchronous set and reset signals exist, and each of the three methods of changing the stored output of the d_dff have separate load values and delays associated with
them. Additionally, you may specify separate rise and fall delay values that are added to
those specified for the input lines; these allow for more faithful reproduction of the output
characteristics of different IC fabrication technologies.
Note that any UNKNOWN input on the set or reset lines immediately results in an
UNKNOWN output.
```
  Example SPICE Usage:
  a7 1 2 3 4 5 6 flop1
  .model flop1 d_dff(clk_delay = 13.0e-9 set_delay = 25.0e-9
  + reset_delay = 27.0e-9 ic = 2 rise_delay = 10.0e-9
  + fall_delay = 3e-9)

### 12.4.13 JK Flip Flop
  NAME_TABLE:
  C_Function_Name: cm_d_jkff
  Spice_Model_Name: d_jkff
  Description: "digital jk-type flip flop"
  PORT_TABLE:
  Port Name: j k
  Description: "j input" "k input"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PORT_TABLE:
  Port Name: clk
  Description: "clock"
  Direction: in
  Default_Type: d
  Allowed_Types: [d]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PORT_TABLE:
  Port Name: set reset
  Description: "asynchronous set" "asynchronous reset"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: - 
```

-----

```
Null_Allowed: yes yes
PORT_TABLE:
Port Name: out Nout
Description: "data output" "inverted data output"
Direction: out out
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: clk_delay set_delay
Description: "delay from clk" "delay from set"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: reset_delay ic
Description: "delay from reset" "output initial state"
Data_Type: real int
Default_Value: 1.0e-9 0
Limits: [1.0e-12 -] [0 2]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: jk_load clk_load
Description: "j,k load values (F)" "clk load value (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: set_load reset_load
Description: "set load value (F)" "reset load (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: rise_delay fall_delay

```

-----

```
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The digital jk-type flip flop is a one-bit, edge-triggered storage element that will**
store data whenever the clk input line transitions from low to high (ZERO to ONE).
In addition, asynchronous set and reset signals exist, and each of the three methods of
changing the stored output of the d_jkff have separate load values and delays associated
with them. Additionally, you may specify separate rise and fall delay values that are
added to those specified for the input lines; these allow for more faithful reproduction of
the output characteristics of different IC fabrication technologies.
Note that any UNKNOWN inputs other than j or k cause the output to go UNKNOWN
automatically.
```
  Example SPICE Usage:
  a8 1 2 3 4 5 6 7 flop2
  .model flop2 d_jkff(clk_delay = 13.0e-9 set_delay = 25.0e-9
  + reset_delay = 27.0e-9 ic = 2 rise_delay = 10.0e-9
  + fall_delay = 3e-9)

### 12.4.14 Toggle Flip Flop
  NAME_TABLE:
  C_Function_Name: cm_d_tff
  Spice_Model_Name: d_tff
  Description: "digital toggle flip flop"
  PORT_TABLE:
  Port Name: t clk
  Description: "toggle input" "clock"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PORT_TABLE:
  Port Name: set reset
  Description: "set" "reset"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```

-----

```
PORT.TABLE:
Port Name: out Nout
Description: "data output" "inverted data output"
Direction: out out
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: clk_delay set_delay
Description: "delay from clk" "delay from set"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: reset_delay ic
Description: "delay from reset" "output initial state"
Data_Type: real int
Default_Value: 1.0e-9 0
Limits: [1.0e-12 -] [0 2]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: t_load clk_load
Description: "toggle load value (F)" "clk load value (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: set_load reset_load
Description: "set load value (F)" "reset load (F)"
Data_Type: real real
Default.Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: rise_delay fall_delay
Description: "rise delay" "fall delay"

```

-----

```
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The digital toggle-type flip flop is a one-bit, edge-triggered storage element that**
will toggle its current state whenever the clk input line transitions from low to high (ZERO
to ONE). In addition, asynchronous set and reset signals exist, and each of the three methods of changing the stored output of the d_tff have separate load values and delays
associated with them. Additionally, you may specify separate rise and fall delay values
that are added to those specified for the input lines; these allow for more faithful reproduction of the output characteristics of different IC fabrication technologies.
Note that any UNKNOWN inputs other than t immediately cause the output to go UNKNOWN.
```
  Example SPICE Usage:
  a8 2 12 4 5 6 3 flop3
  .model flop3 d_tff(clk_delay = 13.0e-9 set_delay = 25.0e-9
  + reset_delay = 27.0e-9 ic = 2 rise_delay = 10.0e-9
  + fall_delay = 3e-9 t_load = 0.2e-12)

### 12.4.15 Set-Reset Flip Flop
  NAME_TABLE:
  C_Function_Name: cm_d_srff
  Spice_Model_Name: d_srff
  Description: "digital set-reset flip flop"
  PORT_TABLE:
  Port Name: s r
  Description: "set input" "reset input"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PORT_TABLE:
  Port Name: clk
  Description: "clock"
  Direction: in
  Default_Type: d
  Allowed_Types: [d]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PORT_TABLE:
  Port Name: set reset

```

-----

```
Description: "asynchronous set" "asynchronous reset"
Direction: in in
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PORT_TABLE:
Port Name: out Nout
Description: "data output" "inverted data output"
Direction: out out
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: clk_delay set_delay
Description: "delay from clk" "delay from set"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: reset_delay ic
Description: "delay from reset" "output initial state"
Data_Type: real int
Default_Value: 1.0e-9 0
Limits: [1.0e-12 -] [0 2]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: sr_load clk_load
Description: "set/reset loads (F)" "clk load value (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12
Limits: - Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: set_load reset_load
Description: "set load value (F)" "reset load (F)"
Data_Type: real real
Default_Value: 1.0e-12 1.0e-12

```

-----

```
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The digital sr-type flip flop is a one-bit, edge-triggered storage element that will**
store data whenever the clk input line transitions from low to high (ZERO to ONE). The
value stored (i.e., the out value) will depend on the s and r input pin values, and will be:
```
  out=ONE if s=ONE and r=ZERO;
  out=ZERO if s=ZERO and r=ONE;
  out=previous value if s=ZERO and r=ZERO;
  out=UNKNOWN if s=ONE and r=ONE;

```
In addition, asynchronous set and reset signals exist, and each of the three methods of changing
the stored output of the d_srff have separate load values and delays associated with them. You
may also specify separate rise and fall delay values that are added to those specified for the
input lines; these allow for more faithful reproduction of the output characteristics of different
IC fabrication technologies.

Note that any UNKNOWN inputs other than s and r immediately cause the output to go UNKNOWN.

Example SPICE Usage:
```
  a8 2 12 4 5 6 3 14 flop7
  .model flop7 d_srff(clk_delay = 13.0e-9 set_delay = 25.0e-9
  + reset_delay = 27.0e-9 ic = 2 rise_delay = 10.0e-9
  + fall_delay = 3e-9)

### 12.4.16 D Latch
  NAME_TABLE:
  C_Function_Name: cm_d_dlatch
  Spice_Model_Name: d_dlatch
  Description: "digital d-type latch"
  PORT_TABLE:
  Port Name: data enable
  Description: "input data" "enable input"
  Direction: in in

```

-----

```
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds: - Null_Allowed: no no
PORT_TABLE:
Port Name: set reset
Description: "set" "reset"
Direction: in in
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PORT_TABLE:
Port Name: out Nout
Description: "data output" "inverter data output"
Direction: out out
Default_Type: d d
Allowed_Types: [d] [d]
Vector: no no
Vector_Bounds: - Null_Allowed: no no
PARAMETER_TABLE:
Parameter_Name: data_delay
Description: "delay from data"
Data_Type: real
Default_Value: 1.0e-9
Limits: [1.0e-12 -]
Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: enable_delay set_delay
Description: "delay from enable" "delay from SET"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: reset_delay ic
Description: "delay from RESET" "output initial state"
Data_Type: real boolean
Default_Value: 1.0e-9 0
Limits: [1.0e-12 -] Vector: no no

```

-----

```
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: data_load enable_load
  Description: "data load (F)" "enable load value (F)"
  Data_Type: real real
  Default_Value: 1.0e-12 1.0e-12
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: set_load reset_load
  Description: "set load value (F)" "reset load (F)"
  Data_Type: real real
  Default_Value: 1.0e-12 1.0e-12
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The digital d-type latch is a one-bit, level-sensitive storage element that will out-**
put the value on the data line whenever the enable input line is high (ONE). The value on
the data line is stored (i.e., held on the out line) whenever the enable line is low (ZERO).
In addition, asynchronous set and reset signals exist, and each of the four methods of
changing the stored output of the d_dlatch (i.e., data changing with enable=ONE, enable
changing to ONE from ZERO with a new value on data, raising set and raising reset) have
separate delays associated with them. You may also specify separate rise and fall delay
values that are added to those specified for the input lines; these allow for more faithful
reproduction of the output characteristics of different IC fabrication technologies.
Note that any UNKNOWN inputs other than on the data line when enable=ZERO immediately cause the output to go UNKNOWN.
```
  Example SPICE Usage:
  a4 12 4 5 6 3 14 latch1
  .model latch1 d_dlatch(data_delay = 13.0e-9 enable_delay = 22.0e-9
  + set_delay = 25.0e-9
  + reset_delay = 27.0e-9 ic = 2
  + rise_delay = 10.0e-9 fall_delay = 3e-9)

```

-----

### 12.4.17 Set-Reset Latch
```
  NAME_TABLE:
  C_Function_Name: cm_d_srlatch
  Spice_Model_Name: d_srlatch
  Description: "digital sr-type latch"
  PORT_TABLE:
  Port Name: s r
  Description: "set" "reset"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PORT_TABLE:
  Port Name: enable
  Description: "enable"
  Direction: in
  Default_Type: d
  Allowed_Types: [d]
  Vector: no
  Vector_Bounds:   Null_Allowed: no
  PORT_TABLE:
  Port Name: set reset
  Description: "set" "reset"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PORT_TABLE:
  Port Name: out Nout
  Description: "data output" "inverted data output"
  Direction: out out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: sr_delay
  Description: "delay from s or r input change"
  Data_Type: real
  Default_Value: 1.0e-9
  Limits: [1.0e-12 -]
  Vector: no

```

-----

```
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: enable_delay set_delay
  Description: "delay from enable" "delay from SET"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: reset_delay ic
  Description: "delay from RESET" "output initial state"
  Data_Type: real boolean
  Default_Value: 1.0e-9 0
  Limits: [1.0e-12 -]   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: sr_load enable_load
  Description: "s & r input loads (F)" "enable load value (F)"
  Data_Type: real real
  Default_Value: 1.0e-12 1.0e-12
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: set_load reset_load
  Description: "set load value (F)" "reset load (F)"
  Data_Type: real real
  Default_Value: 1.0e-12 1.0e-12
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes

```
**Description: The digital sr-type latch is a one-bit, level-sensitive storage element that will**


-----

output the value dictated by the state of the s and r pins whenever the enable input line
is high (ONE). This value is stored (i.e., held on the out line) whenever the enable line is
low (ZERO). The particular value chosen is as shown below:
```
  s=ZERO, r=ZERO => out=current value (i.e., not change in output)
    s=ZERO, r=ONE => out=ZERO
    s=ONE, r=ZERO => out=ONE
    s=ONE, r=ONE => out=UNKNOWN

```
Asynchronous set and reset signals exist, and each of the four methods of changing the stored output of the d srlatch (i.e., s/r combination changing with enable=ONE, enable changing
to ONE from ZERO with an output-changing combination of s and r, raising set and raising
reset) have separate delays associated with them. You may also specify separate rise and fall
delay values that are added to those specified for the input lines; these allow for more faithful
reproduction of the output characteristics of different IC fabrication technologies.

Note that any UNKNOWN inputs other than on the s and r lines when enable=ZERO immediately cause the output to go UNKNOWN.
```
  Example SPICE Usage:
  a4 12 4 5 6 3 14 16 latch2
  .model latch2 d_srlatch(sr_delay = 13.0e-9 enable_delay = 22.0e-9
  + set_delay = 25.0e-9
  + reset_delay = 27.0e-9 ic = 2
  + rise_delay = 10.0e-9 fall_delay = 3e-9)

### 12.4.18 State Machine
  NAME_TABLE:
  C_Function_Name: cm_d_state
  Spice_Model_Name: d_state
  Description: "digital state machine"
  PORT_TABLE:
  Port Name: in clk
  Description: "input" "clock"
  Direction: in in
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes no
  Vector_Bounds: [1 -]   Null_Allowed: yes no
  PORT_TABLE:
  Port Name: reset out
  Description: "reset" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]

```

-----

```
Vector: no yes
Vector_Bounds: - [1 -]
Null_Allowed: yes no
PARAMETER_TABLE:
Parameter_Name: clk_delay reset_delay
Description: "delay from CLK" "delay from RESET"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE: Parameter_Name: state_file
Description: "state transition specification file name"
Data_Type: string
Default_Value: "state.txt"
Limits: Vector: no
Vector_Bounds: Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: reset_state
Description: "default state on RESET & at DC"
Data_Type: int
Default_Value: 0
Limits: Vector: no
Vector_Bounds: Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: input_load
Description: "input loading capacitance (F)"
Data_Type: real
Default_Value: 1.0e-12
Limits: Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: clk_load
Description: "clock loading capacitance (F)"
Data_Type: real
Default_Value: 1.0e-12
Limits: Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:

```

-----

```
  Parameter_Name: reset_load
  Description: "reset loading capacitance (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital state machine provides for straightforward descriptions of clocked**
combinational logic blocks with a variable number of inputs and outputs and with an
unlimited number of possible states. The model can be configured to behave as virtually
any type of counter or clocked combinational logic block and can be used to replace very
large digital circuit schematics with an identically functional but faster representation.
The d state model is configured through the use of a state definition file (state.in) that
resides in a directory of your choosing. The file defines all states to be understood by the
model, plus input bit combinations that trigger changes in state. An example state.in file
is shown below:
```
  ----------- begin file ------------  * This is an example state.in file. This file
  * defines a simple 2-bit counter with one input. The
  * value of this input determines whether the counter counts
  * up (in = 1) or down (in = 0).
  0 0s 0s 0 -> 3
       1 -> 1
  1 0s 1z 0 -> 0
       1 -> 2
  2 1z 0s 0 -> 1
       1 -> 3
  3 1z 1z 0 -> 2
  3 1z 1z 1 -> 0
  ------------------ end file --------------
```
Several attributes of the above file structure should be noted. First, all lines in the file must be
_one of four types. These are:_

1. A comment, beginning with a ‘*’ in the first column.

2. A header line, which is a complete description of the current state, the outputs corresponding to that state, an input value, and the state that the model will assume should that
input be encountered. The first line of a state definition must always be a header line.

3. A continuation line, which is a partial description of a state, consisting of an input value
and the state that the model will assume should that input be encountered. Note that
continuation lines may only be used after the initial header line definition for a state.

4. A line containing nothing but white-spaces (space, form-feed, newline, carriage return,
tab, vertical tab).


-----

A line that is not one of the above will cause a file-loading error. Note that in the example
shown, whitespace (any combination of blanks, tabs, commas) is used to separate values, and
that the character -> is used to underline the state transition implied by the input preceding it.
This particular character is not critical in of itself, and can be replaced with any other character
or non-broken combination of characters that you prefer (e.g. ==>, >>, ‘:’, resolves_to, etc.)

The order of the output and input bits in the file is important; the first column is always interpreted to refer to the ‘zeroth’ bit of input and output. Thus, in the file above, the output from
state 1 sets out[0] to 0s, and out[1] to 1z.

The state numbers need not be in any particular order, but a state definition (which consists of
the sum total of all lines that define the state, its outputs, and all methods by which a state can
be exited) must be made on contiguous line numbers; a state definition cannot be broken into
sub-blocks and distributed randomly throughout the file. On the other hand, the state definition
can be broken up by as many comment lines as you desire.

Header files may be used throughout the state.in file, and continuation lines can be discarded
completely if you so choose: continuation lines are primarily provided as a convenience.
```
  Example SPICE Usage:
  a4 [2 3 4 5] 1 12 [22 23 24 25 26 27 28 29] state1
  .model state1 d_state(clk_delay = 13.0e-9 reset_delay = 27.0e-9
  + state_file = "newstate.txt" reset_state = 2)

```
**Note: The file named by the parameter filename in state_file="filename" is sought after**
according to a search list described in12.1.3.

### 12.4.19 Frequency Divider
```
  NAME_TABLE:
  C_Function_Name: cm_d_fdiv
  Spice_Model_Name: d_fdiv
  Description: "digital frequency divider"
  PORT_TABLE:
  Port Name: freq_in freq_out
  Description: "frequency input" "frequency output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: no no
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: div_factor high_cycles
  Description: "divide factor" "# of cycles for high out"
  Data_Type: int int
  Default_Value: 2 1
  Limits: [1 -] [1 div_factor-1]
  Vector: no no

```

-----

```
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: i_count
  Description: "divider initial count value"
  Data_Type: int
  Default_Value: 0
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: yes yes
  Vector_Bounds: in in
  Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: freq_in_load
  Description: "freq_in load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital frequency divider is a programmable step-down divider that accepts**
an arbitrary divisor (div_factor), a duty-cycle term (high_cycles), and an initial count
value (i_count). The generated output is synchronized to the rising edges of the input
signal. Rise delay and fall delay on the outputs may also be specified independently.
```
  Example SPICE Usage:
  a4 3 7 divider
  .model divider d_fdiv(div_factor = 5 high_cycles = 3
  + i_count = 4 rise_delay = 23e-9
  + fall_delay = 9e-9)

### 12.4.20 RAM
  NAME_TABLE:
  C_Function_Name: cm_d_ram
  Spice_Model_Name: d_ram
  Description: "digital random-access memory"
  PORT_TABLE:

```

-----

```
Port Name: data_in data_out
Description: "data input line(s)" "data output line(s)"
Direction: in out
Default_Type: d d
Allowed_Types: [d] [d]
Vector: yes yes
Vector_Bounds: [1 -] data_in
Null_Allowed: no no
PORT_TABLE:
Port Name: address write_en
Description: "address input line(s)" "write enable line"
Direction: in in
Default_Type: d d
Allowed_Types: [d] [d]
Vector: yes no
Vector_Bounds: [1 -] Null_Allowed: no no
PORT_TABLE:
Port Name: select
Description: "chip select line(s)"
Direction: in
Default_Type: d
Allowed_Types: [d]
Vector: yes
Vector_Bounds: [1 16]
Null_Allowed: no
PARAMETER_TABLE:
Parameter_Name: select_value
Description: "decimal active value for select line comparison"
Data_Type: int
Default_Value: 1
Limits: [0 32767]
Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: ic
Description: "initial bit state @ dc"
Data_Type: int
Default_Value: 2
Limits: [0 2]
Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: read_delay
Description: "read delay from address/select/write.en active"
Data_Type: real

```

-----

```
  Default_Value: 100.0e-9
  Limits: [1.0e-12 -]
  Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: data_load address_load
  Description: "data_in load value (F)" "addr. load value (F)"
  Data_Type: real real
  Default_Value: 1.0e-12 1.0e-12
  Limits: -   Vector: no no
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: select_load
  Description: "select load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes
  PARAMETER_TABLE:
  Parameter_Name: enable_load
  Description: "enable line load value (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: yes

```
**Description: The digital RAM is an M-wide, N-deep random access memory element with**
programmable select lines, tristated data out lines, and a single write/~read line. The
width of the RAM words (M) is set through the use of the word width parameter. The
depth of the RAM (N) is set by the number of address lines input to the device. The value
of N is related to the number of address input lines (P) by the following equation:

2[P] = N

There is no reset line into the device. However, an initial value for all bits may be specified
by setting the ic parameter to either 0 or 1. In reading a word from the ram, the read delay
value is invoked, and output will not appear until that delay has been satisfied. Separate
rise and fall delays are not supported for this device.
Note that UNKNOWN inputs on the address lines are not allowed during a write. In the
event that an address line does indeed go unknown during a write, the entire contents
_of the ram will be set to unknown. This is in contrast to the data in lines being set to_
unknown during a write; in that case, only the selected word will be corrupted, and this is


-----

corrected once the data lines settle back to a known value. Note that protection is added
to the write en line such that extended UNKNOWN values on that line are interpreted as
ZERO values. This is the equivalent of a read operation and will not corrupt the contents
of the RAM. A similar mechanism exists for the select lines. If they are unknown, then it
is assumed that the chip is not selected.
Detailed timing-checking routines are not provided in this model, other than for the enable
delay and select delay restrictions on read operations. You are advised, therefore, to
carefully check the timing into and out of the RAM for correct read and write cycle
times, setup and hold times, etc. for the particular device they are attempting to model.
```
  Example SPICE Usage:
  a4 [3 4 5 6] [3 4 5 6] [12 13 14 15 16 17 18 19] 30 [22 23 24] ram2
  .model ram2 d_ram(select_value = 2 ic = 2 read_delay = 80e-9)

### 12.4.21 Digital Source
  NAME_TABLE:
  C_Function_Name: cm_d_source
  Spice_Model_Name: d_source
  Description: "digital signal source"
  PORT_TABLE:
  Port Name: out
  Description: "output"
  Direction: out
  Default_Type: d
  Allowed_Types: [d]
  Vector: yes
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: input_file
  Description: "digital input vector filename"
  Data_Type: string
  Default_Value: "source.txt"
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: no
  PARAMETER_TABLE:
  Parameter_Name: input_load
  Description: "input loading capacitance (F)"
  Data_Type: real
  Default_Value: 1.0e-12
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: no

```

-----

**Description: The digital source provides for straightforward descriptions of digital signal vec-**
tors in a tabular format. The model reads input from the input file and, at the times
specified in the file, generates the inputs along with the strengths listed. The format of
the input file is as shown below. Note that comment lines are delineated through the use
of a single ‘*’ character in the first column of a line. This is similar to the way the SPICE
program handles comments.
```
  * T c n n n . . .
  * i l o o o . . .
  * m o d d d . . .
  * e c e e e . . .
  * k a b c . . .
  0.0000 Uu Uu Us Uu . . .
  1.234e-9 0s 1s 1s 0z . . .
  1.376e-9 0s 0s 1s 0z . . .
  2.5e-7 1s 0s 1s 0z . . .
  2.5006e-7 1s 1s 1s 0z . . .
  5.0e-7 0s 1s 1s 0z . . .

```
Note that in the example shown, whitespace (any combination of blanks, tabs, commas) is used
to separate the time and state/strength tokens. The order of the input columns is important; the
first column is always interpreted to mean ‘time’. The second through the N’th columns map
to the out[0] through out[N-2] output nodes. A non-commented line that does not contain
enough tokens to completely define all outputs for the digital source will cause an error. Also,
time values must increase monotonically or an error will result in reading the source file.

Errors will also occur if a line exists in source.txt that is neither a comment nor vector line.
The only exception to this is in the case of a line that is completely blank; this is treated as
a comment (note that such lines often occur at the end of text within a file; ignoring these in
particular prevents nuisance errors on the part of the simulator).
```
  Example SPICE Usage:
  a3 [2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17] input_vector
  .model input_vector d_source(input_file = "source_simple.text")

```
**Note: The file named by the parameter filename in input_file="filename" is sought after**
according to a search list described in12.1.3.

### 12.4.22 LUT
```
  NAME_TABLE:
  C_Function_Name: cm_d_lut
  Spice_Model_Name: d_lut
  Description: "digital n-input look-up table gate"
  PORT_TABLE:
  Port_Name: in out
  Description: "input" "output"
  Direction: in out

```

-----

```
Default_Type: d d
Allowed_Types: [d] [d]
Vector: yes no
Vector_Bounds: [1 -] Null_Allowed: no no
PARAMETER_TABLE:
Parameter_Name: rise_delay fall_delay
Description: "rise delay" "fall delay"
Data_Type: real real
Default_Value: 1.0e-9 1.0e-9
Limits: [1.0e-12 -] [1.0e-12 -]
Vector: no no
Vector_Bounds: - Null_Allowed: yes yes
PARAMETER_TABLE:
Parameter_Name: input_load
Description: "input load value (F)"
Data_Type: real
Default_Value: 1.0e-12
Limits: Vector: no
Vector_Bounds: Null_Allowed: yes
PARAMETER_TABLE:
Parameter_Name: table_values
Description: "lookup table values"
Data_Type: string
Default_Value: "0"
Limits: Vector: no
Vector_Bounds: Null_Allowed: no

```

-----

**Description: The lookup table provides a way to map any arbitrary n-input, 1-output combi-**
national logic block to XSPICE. The inputs are mapped to the output using a string of length
2^n. The string may contain values "0", "1" or "X", corresponding to an output of low, high,
or unknown, respectively. The outputs are only mapped for inputs which are valid logic levels. Any unknown bit in the input vector will always produce an unknown output. The first
character of the string table_values corresponds to all inputs value zero, and the last (2^n)
character corresponds to all inputs value one, with the first signal in the input vector being the
least significant bit. For example, a 2-input lookup table representing the function (A * B)
(that is, A AND B), with input vector [A B] can be constructed with a table_values string of
"0001"; function (~A * B) with input vector [A B] can be constructed with a table_values
string of "0010". The delays associated with an output rise and those associated with an output
fall may be specified independently. The model also posts an input load value (in farads) based
on the parameter input_load. The output of this model does not respond to the total loading
it sees on the output; it will always drive the output strongly with the specified delays.
```
  Example SPICE Usage:
  * LUT encoding 3-bit parity function
  a4 [1 2 3] 5 lut_pty3_1
  .model lut_pty3_1 d_lut(table_values = "01101001"
  + input_load 2.0e-12)

### 12.4.23 General LUT
  NAME_TABLE:
  C_Function_Name: cm_d_genlut
  Spice_Model_Name: d_genlut
  Description: "digital n-input x m-output look-up table gate"
  PORT_TABLE:
  Port_Name: in out
  Description: "input" "output"
  Direction: in out
  Default_Type: d d
  Allowed_Types: [d] [d]
  Vector: yes yes
  Vector_Bounds: -   Null_Allowed: no no
  PARAMETER_TABLE:
  Parameter_Name: rise_delay fall_delay
  Description: "rise delay" "fall delay"
  Data_Type: real real
  Default_Value: 1.0e-9 1.0e-9
  Limits: [1.0e-12 -] [1.0e-12 -]
  Vector: yes yes
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: input_load input_delay
  Description: "input load value (F)" "input delay"

```

-----

```
  Data_Type: real real
  Default_Value: 1.0e-12 0.0
  Limits: -   Vector: yes yes
  Vector_Bounds: -   Null_Allowed: yes yes
  PARAMETER_TABLE:
  Parameter_Name: table_values
  Description: "lookup table values"
  Data_Type: string
  Default_Value: "0"
  Limits:   Vector: no
  Vector_Bounds:   Null_Allowed: no

```
**Description: The lookup table provides a way to map any arbitrary n-input, m-output combi-**
national logic block to XSPICE. The inputs are mapped to the output using a string of length m

- (2^n). The string may contain values "0", "1", "X", or "Z", corresponding to an output of low,
high, unknown, or high-impedance, respectively. The outputs are only mapped for inputs which
are valid logic levels. Any unknown bit in the input vector will always produce an unknown
output. The character string is in groups of (2^n) characters, one group corresponding to each
output pin, in order. The first character of a group in the string table_values corresponds to
all inputs value zero, and the last (2^n) character in the group corresponds to all inputs value
one, with the first signal in the input vector being the least significant bit. For example, a 2-input
lookup table representing the function (A * B) (that is, A AND B), with input vector [A B] can
be constructed with a table_values string of "0001"; function (~A * B) with input vector
```
[A B] can be constructed with a "table_values" string of "0010". The delays associated with

```
each output pin’s rise and those associated with each output pin’s fall may be specified independently. The model also posts independent input load values per input pin (in farads) based on
the parameter input_load. The parameter input_delay provides a way to specify additional
delay between each input pin and the output. This delay is added to the rise- or fall-time of the
output. The output of this model does not respond to the total loading it sees on the output; it
will always drive the output strongly with the specified delays.
```
  Example SPICE Usage:
  * LUT encoding 3-bit parity function
  a4 [1 2 3] [5] lut_pty3_1
  .model lut_pty3_1 d_genlut(table_values = "01101001"
  + input_load [2.0e-12])
  * LUT encoding a tristate inverter function (en in out)
  a2 [1 2] [3] lut_triinv_1
  .model lut_triinv_1 d_genlut(table_values = "Z1Z0")
  * LUT encoding a half-adder function (A B Carry Sum)
  a8 [1 2] [3 4] lut_halfadd_1
  .model lut_halfadd_1 d_genlut(table_values = "00010110"
  + rise_delay [ 1.5e-9 1.0e-9 ] fall_delay [ 1.5e-9 1.0e-9 ])

```

-----

## 12.5 Predefined Node Types for event driven simulation

The following pre-written node types are included with the XSPICE simulator. These should
provide you not only with valuable event-driven modeling capabilities, but also with examples
to use for guidance in creating new UDN (user defined node) types. You may access these node
data by the plot (17.5.45) or eprint (17.5.24) commands.

### 12.5.1 Digital Node Type

The ‘digital’ node type is directly built into the simulator. 12 digital node values are available.
They are described by a two character string (the state/strength token). The first character (0,
1, or U) gives the state of the node (logic zero, logic one, or unknown logic state). The second
character (s, r, z, u) gives the "strength" of the logic state (strong, resistive, hi-impedance, or
undetermined). So these are the values we have: 0s, 1s, Us, 0r, 1r, Ur, 0z, 1z, Uz, 0u, 1u, Uu.

### 12.5.2 Real Node Type

The ‘real’ node type provides for event-driven simulation with double-precision floating point
data. This type is useful for evaluating sampled-data filters and systems. The type implements
all optional functions for User-Defined Nodes, including inversion and node resolution. For
inversion, the sign of the value is reversed. For node resolution, the resultant value at a node is
the sum of all values output to that node. The node is implemented as a user defined node in
ngspice/src/xspice/icm/xtraevt/real.

### 12.5.3 Int Node Type

The ‘int’ node type provides for event-driven simulation with integer data. This type is useful
for evaluating round-off error effects in sampled-data systems. The type implements all optional
functions for User-Defined Nodes, including inversion and node resolution. For inversion, the
sign of the integer value is reversed. For node resolution, the resultant value at a node is the
sum of all values output to that node. The node is implemented as a user defined node in
ngspice/src/xspice/icm/xtraevt/int.

### 12.5.4 (Digital) Input/Output

The analog code models use the standard (analog) nodes provided by ngspice and thus are using
all the commands for sourcing, storing, printing, and plotting data.

I/O for event nodes (digital, real, int, and UDNs) is offered by the following tools: For output
you may use the plot (17.5.45) or eprint (17.5.24) commands, as well as edisplay (17.5.23)
[and eprvcd (17.5.25). The latter writes all node data to a VCD file (a digital standard interface)](http://en.wikipedia.org/wiki/Value_change_dump)
[that may be analysed by viewers like gtkwave. For input, you may create a test bench with](http://gtkwave.sourceforge.net/)
existing code models (oscillator (12.3.3), frequency divider (12.4.19), state machine (12.4.18)
[etc.). Reading data from a file is offered by d_source (12.4.21). Some comments and hints have](https://sourceforge.net/p/ngspice/discussion/ngspice-tips/thread/3e193172/)
been provided by Sdaau. You may also use the analog input from file, (filesource 12.2.8) and
convert its analog input to the digital type by the adc_bridge (12.3.2). If you want reading


-----

[data from a VCD file, please have a look at ngspice tips and examples forum and apply a python](http://en.wikipedia.org/wiki/Value_change_dump)
script provided by Sdaau to translate the VCD data to d_source or filesource input.


-----

