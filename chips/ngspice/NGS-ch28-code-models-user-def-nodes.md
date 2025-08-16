# Chapter 28

 Code Models and User-Defined Nodes

The following sections explain the steps required to create code models and User-Defined Nodes
(UDNs), store them in shared libraries and load them into the simulator at runtime. The ngspice
simulator already includes XSPICE libraries of predefined models and node types that span the
analog and digital domains. These have been detailed earlier in this document (see Sections
12.2, 12.3, and 12.4). However, the real power of the XSPICE is in its support for extending
these libraries with new models written by users. ngspice includes an XSPICE code model
generator. Adding code models to ngspice will require a model definition plus some simple file
operations, which are explained in this chapter.

The original manual cited an XSPICE ‘Code Model Toolkit’ that enabled one to define new
models and node data types to be passed between them offline, independent from ngspice.
[Whereas this Toolkit is still available in the original source code distribution at the XSPICE](http://users.ece.gatech.edu/~mrichard/Xspice/)
[web page, it is neither required nor supported any more.](http://users.ece.gatech.edu/~mrichard/Xspice/)

So we make use of the existing XSPICE infrastructure provided with ngspice to create new
code models. With an ’intelligent’ copy and paste, and the many available code models serving
as a guide you will be quickly able to create your own models. You have to have a compiler
(gcc) available under Linux, MS Windows (Cygwin, MINGW), maybe also for other OSs,
including supporting software (Flex, Bison, and the autotools if you start from Git sources).
The compilation procedures for ngspice are described in detail in Chapt. 32. Adding a code
model may then require defining the functionality, interface, and eventually user defined nodes.
Compiling into a shared library is only a simple ’make’, loading the shared lib(s) into ngspice is
done by the ngspice command codemodel... (see Chapt. 17.5.11). This will allow you to either
add some code model to an existing library, or you may generate a new library with your own
code models. The latter is of interest if you want to distribute your code models independently
from the ngspice sources or executables.

These new code models are handled by ngspice in a manner analogous to its treating of SPICE
devices and XSPICE Predefined Code Models. The basic steps required to create sources for
new code models or User-Defined Nodes, compile them and load them into ngspice are similar. They consist of 1) creating the code model or UserDefined Node (UDN) directory and
its associated model or data files, 2) inform ngspice about the code model or UDN directories
that have to be compiled and linked into ngspice, 3) compile them into a shared lib, and 4)
load them into the ngspice simulator upon runtime. All code models finally reside in dynamically linkable shared libraries (*.cm), which in fact are .so files under Linux or dlls under MS
Windows. Currently we have 5 of them (analog.cm, digital.cm, spice2poly.cm, xtradev.cm,


-----

xtraevt.cm). Upon start up of ngspice they are dynamically loaded into the simulator by the
ngspice codemodel command (which is located in file spinit (see Chapt. 16.5) for the standard code models). Once you have added your new code model into one of these libraries (or
have created a new library file, e.g. my-own.cm), instances of the model can be placed into
any simulator deck that describes a circuit of interest and simulated along with all of the other
components in that circuit.

A quick entry to get a new code model has already been presented in Chapt. 26.3. You may
find the details of the XSPICE language in Chapt. 28.6 ff.

## 28.1 Code Model Data Type Definitions

There are several data types that you can incorporate into a model. These have already been
used extensively in the code model library included with the simulator. They are detailed below:

**Boolean_t** The Boolean type is an enumerated type that can take on values of FALSE (integer
value 0) or TRUE (integer value 1). Alternative names for these enumerations are MIF FALSE
and MIF TRUE, respectively.

**Complex_t** The Complex type is a structure composed of two double values. The first of
these is the .real type, and the second is the .imag type. Typically these values are accessed as
shown:

For complex value ‘data’, the real portion is ‘data.real’, and the imaginary portion is ‘data.imag’.

**Digital_State_t** The Digital State type is an enumerated value that can be either ZERO (integer value 0), ONE (integer value 1), or UNKNOWN (integer value 2).

**Digital_Strength_t** The Digital Strength type is an enumerated value that can be either
STRONG (integer value 0), RESISTIVE (integer value 1), HI IMPEDANCE (integer value
2) or UNDETERMINED (integer value 3).

**Digital_t** The Digital type is a composite of the Digital_State_t and Digital_Strength_t enumerated data types. The actual variable names within the Digital type are .state and .strength
and are accessed as shown below:

For Digital_t value ‘data’, the state portion is ‘data.state’, and the strength portion is ‘data.strength’.

## 28.2 Creating Code Models

The following description deals with extending one of the five existing code model libraries.
Adding a new library is described in Chapt. 28.4. The first step in creating a new code model
within XSPICE is to create a model directory inside of the selected library directory. The new
directory name is the name of the new code model. As an example you may add a directory
**d_counter to the library directory digital.**


-----

```
  cd ngspice/src/xspice/icm/digital
  mkdir d_counter

```
Into this new directory you copy the following template files:

  - Interface Specification File (ifspec.ifs)

  - Model Definition File (cfunc.mod)

You may choose existing files that are similar to the new code model you intend to integrate.
The template Interface Specification File (ifspec.ifs) is edited to define the model’s inputs, outputs, parameters, etc (see Chapt. 28.6). You then edit the template Model Definition File
(cfunc.mod) to include the C-language source code that defines the model behavior (see Chapt.
28.7). As a final step you have to notify ngspice of the new code model. You have to edit the
file modpath.lst that resides in the library directory ngspice/src/xspice/icm/digital. Just add
the entry d_counter to this file.

The Interface Specification File is a text file that describes, in a tabular format, information
needed for the code model to be properly interpreted by the simulator when it is placed with
other circuit components into a SPICE deck. This information includes such things as the
parameter names, parameter default values, and the name of the model itself. The specific
format presented to you in the Interface Specification File template must be followed exactly,
but is quite straightforward. A detailed description of the required syntax, along with numerous
examples, is included in Section 28.6.

The Model Definition File contains a C programming language function definition. This function
specifies the operations to be performed within the model on the data passed to it by the simulator. Special macros are provided that allow the function to retrieve input data and return output
data. Similarly, macros are provided to allow for such things as storage of information between iteration time-points and sending of error messages. Section 28.7 describes the form and
function of the Model Definition File in detail and lists the support macros provided within the
simulator for use in code models.

To allow compiling and linking (see Chapt. 28.5) you have at least to adapt the names of the
functions inside of the two copied files to get unique function and model names. If for example
you have chosen ifspec.ifs and cfunc.mod from model d_fdiv as your template, simply replace
all entries d_fdiv by d_counter inside of the two files.

## 28.3 Creating User-Defined Nodes

In addition to providing the capability of adding new models to the simulator, a facility exists
that allows node types other than those found in standard SPICE to be created. Models may be
constructed that pass information back and forth via these nodes. Such models are constructed
in the manner described in the previous sections, with appropriate changes to the Interface
Specification and Model Definition Files.

Because of the need of electrical engineers to have ready access to both digital and analog
simulation capabilities, the digital node type is provided as a built-in node type along with
standard SPICE analog nodes. For digital nodes, extensive support is provided in the form


-----

of macros and functions so that you can treat this node type as a standard type analogous to
standard SPICE analog nodes when creating and using code models. In addition to analog and
```
digital nodes, the node types real and int are also provided with the simulator. These were

```
created using the User-Defined Node (UDN) creation facilities described below and may serve
as a template for further node types.

The first step in creating a new node type within XSPICE is to set up a node type directory
along with the appropriate template files needed.
```
  cd ngspice/src/xspice/icm/xtraevt
  mkdir <directory name>

```
<directory name> should be the name of the new type to be defined. Copy file udnfunc.c
from /icm/xtraevt/int into the new directory. Edit this file according to the new type you want
to create.

Notify ngspice about this new UDN directory by editing
ngspice/src/xspice/icm/xtraevt/udnpath.lst. Add a new line containing <directory name>.
For compiling and linking see Chapt. 28.5.

The UDN Definition File contains a set of C language functions. These functions perform
operations such as allocating space for data structures, initializing them, and comparing them to
each other. Section 28.8 describes the form and function of the User-Defined Node Definition
File in detail and includes an example UDN Definition File.

## 28.4 Adding a new code model library

A group of code models may be assembled into a library. A new library is a means to distribute
new code models, independently from the existing ones. This is the way to generate a new code
model library:
```
  cd ngspice/src/xspice/icm/
  mkdir <directory name>

```
<directory name> is the name of the new library. Copy empty files modpath.lst and udnpath.lst
into this directory.

Edit file ngspice/src/xspice/icm/GNUmakefile.in, add <directory name> to the end of line
10, which starts with CMDIRS = ... .

That’s all you have to do about a new library! Of course it is empty right now, so you have to
define at least one code model according to the procedure described in Chapt. 28.2.

## 28.5 Compiling and loading the new code model (library)

Compiling is now as simple as issuing the commands


-----

```
  cd ngspice/release
  make
  sudo make install

```
if you have installed ngspice according to Chapt. 32.1.4. This procedure will install the code
model libraries into a directory <prefix>/lib/spice/, e.g. C:/Spice/lib/spice/ for standard Windows install or /usr/local/lib/spice/ for Linux.

Thus the code model libraries are not linked into ngspice at compile time, but may be loaded
at runtime using the codemodel command (see Chapt. 17.5.11). This is done automatically
for the predefined code model libraries upon starting ngspice. The appropriate commands are
provided in the start up file spinit (see Chapt. 16.5). So if you have added a new code model
inside of one of the existing libraries, nothing has to be done, you will have immediate access
to your new model.

If you have generated a new code model library, e.g. new_lib.cm, then you have to add the line
```
  @XSPICEINIT@ codemodel @prefix@/@libname@/spice/new_lib.cm

```
to spinit.in in ngspice/src. This will create a new spinit if ngspice is recompiled from scratch.

To avoid the need for recompilation of ngspice, you also may directly edit the file spinit by
adding the line
```
  codemodel C:/Spice/lib/spice/new_lib.cm

```
(OS MS Windows) or the appropriate Linux equivalent. Upon starting ngspice, the new library
will be loaded and you have access to the new code model(s). The codemodel command has to
be executed upon start-up of ngspice, so that the model information is available as soon as the
circuit is parsed. Failing to do so will lead to an error message of a model missing. So spinit
(or .spiceinit for personal code model libraries) is the correct place for codemodel.

## 28.6 Interface Specification File

The Interface Specification (IFS) file is a text file that describes the model’s naming information, its expected input and output ports, its expected parameters, and any variables within the
model that are to be used for storage of data across an entire simulation. These four types
of data are described to the simulator in IFS file sections labeled NAME_TABLE, PORT_TABLE,
```
PARAMETER_TABLE and STATIC_VAR_TABLE, respectively. An example IFS file is given below.

```
The example is followed by detailed descriptions of each of the entries, what they signify, and
what values are acceptable for them. Keywords are case insensitive.
```
  NAME_TABLE:
  C_Function_Name: ucm_xfer
  Spice_Model_Name: xfer
  Description: "arbitrary transfer function"
  PORT_TABLE:

```

-----

```
Port_Name: in out
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
STATIC_VAR_TABLE:
Static_Var_Name: x
Data_Type: pointer
Description: "x-coefficient array"

```

-----

### 28.6.1 The Name Table

The name table is introduced by the Name_Table: keyword. It defines the code model’s C
function name, the name used on a .MODEL card, and an optional textual description. The
following sections define the valid fields that may be specified in the Name Table.

**28.6.1.1** **C Function Name**

The C function name is a valid C identifier that is the name of the function for the code model. It
is introduced by the C_Function_Name: keyword followed by a valid C identifier. To reduce
the chance of name conflicts, it is recommended that user-written code model names use the
prefix ucm_ for this entry. Thus, in the example given above, the model name is xfer, but the C
function is ucm_xfer. Note that when you subsequently write the model function in the Model
Definition File, this name must agree with that of the function (i.e., ucm_xfer), or an error will
result in the linking step.

**28.6.1.2** **SPICE Model Name**

The SPICE model name is a valid SPICE identifier that will be used on SPICE .MODEL cards to
refer to this code model. It may or may not be the same as the C function name. It is introduced
by the Spice_Model_Name: keyword followed by a valid SPICE identifier.

**Description** The description string is used to describe the purpose and function of the code
model. It is introduced by the Description: keyword followed by a C string literal.

### 28.6.2 The Port Table

The port table is introduced by the Port_Table: keyword. It defines the set of valid ports
available to the code model. The following sections define the valid fields that may be specified
in the port table.

**28.6.2.1** **Port Name**

The port name is a valid SPICE identifier. It is introduced by the Port_Name: keyword followed by the name of the port. Note that this port name will be used to obtain and return input
and output values within the model function. This will be discussed in more detail in the next
section.

**28.6.2.2** **Description**

The description string is used to describe the purpose and function of the code model. It is
introduced by the Description: keyword followed by a C string literal.


-----

|Default Types|Col2|Col3|
|---|---|---|
|Type|Description|Valid Directions|
|d|digital|in or out|
|g|conductance (VCCS)|inout|
|gd|differential conductance (VCCS)|inout|
|h|resistance (CCVS)|inout|
|hd|differential resistance (CCVS)|inout|
|i|current|in or out|
|id|differential current|in or out|
|v|voltage|in or out|
|vd|differential voltage|in or out|
|<identifier>|user-defined type|in or out|


Table 28.1: Port Types

**28.6.2.3** **Direction**

The direction of a port specifies the data flow direction through the port. A direction must be
one of n, out, or inout. It is introduced by the Direction: keyword followed by a valid
direction value.

**28.6.2.4** **Default Type**

The Default_Type field specifies the type of a port. These types are identical to those used to
define the port types on a SPICE deck instance card (see Table 12.1), but without the percent
sign (%) preceding them. Table 28.1 summarizes the allowable types.

**28.6.2.5** **Allowed Types**

A port must specify the types it is allowed to assume. An allowed type value must be a list of
type names (a blank or comma separated list of names delimited by square brackets, e.g. [v vd
```
i id] or [d]). The type names must be taken from those listed in Table 28.1.

```
**28.6.2.6** **Vector**

A port that is a vector can be thought of as a bus. The Vector field is introduced with the
```
Vector: keyword followed by a Boolean value: YES, TRUE, NO or FALSE.

```
The values YES and TRUE are equivalent and specify that this port is a vector. Likewise, NO
and FALSE specify that the port is not a vector. Vector ports must have a corresponding vector
bounds field that specifies valid sizes of the vector port.

**28.6.2.7** **Vector Bounds**

If a port is a vector, limits on its size must be specified in the vector bounds field. The Vector
Bounds field specifies the upper and lower bounds on the size of a vector. The Vector Bounds


-----

field is usually introduced by the Vector_Bounds: keyword followed by a range of integers
(e.g. ‘[1 7]’ or ‘[3, 20]’). The lower bound of the vector specifies the minimum number of
elements in the vector; the upper bound specifies the maximum number of elements. If the
range is unconstrained, or the associated port is not a vector, the vector bounds may be specified
by a hyphen (‘-’). Using the hyphen convention, partial constraints on the vector bound may be
defined (e.g., ‘[2, -]’ indicates that the least number of port elements allowed is two, but there
is no maximum number).

**28.6.2.8** **Null Allowed**

In some cases, it is desirable to permit a port to remain unconnected to any electrical node in
a circuit. The Null_Allowed field specifies whether this constitutes an error for a particular
port. The Null_Allowed field is introduced by the ‘Null_Allowed:’ keyword and is followed
by a boolean constant: ‘YES’, ‘TRUE’, ‘NO’ or ‘FALSE’. The values ‘YES’ and ‘TRUE’ are
equivalent and specify that it is legal to leave this port unconnected. ‘NO’ or ‘FALSE’ specify
that the port must be connected.

### 28.6.3 The Parameter Table

The parameter table is introduced by the Parameter_Table: keyword. It defines the set of
valid parameters available to the code model. The following sections define the valid fields that
may be specified in the parameter table.

**28.6.3.1** **Parameter Name**

A parameter name is a valid SPICE identifier that will be used on SPICE .MODEL cards to
refer to this parameter. It is introduced by the Parameter_Name: keyword followed by a valid
SPICE identifier.

**28.6.3.2** **Description**

The description string is used to describe the purpose and function of the parameter. It is
introduced by the ‘Description:’ keyword followed by a string literal.

**28.6.3.3** **Data Type**

The parameter’s data type is specified by the Data Type field. The Data Type field is introduced
by the keyword ‘Data_Type:’ and is followed by a valid data type. Valid data types include
boolean, complex, int, real, and string.

**28.6.3.4** **Null Allowed**

The Null_Allowed field is introduced by the ‘Null_Allowed:’ keyword and is followed by a
boolean literal. A value of ‘TRUE’ or ‘YES’ specify that it is valid for the corresponding SPICE
```
.MODEL card to omit a value for this parameter. If the parameter is omitted, the default value

```

-----

is used. If there is no default value, an undefined value is passed to the code model, and the
```
PARAM_NULL( ) macro will return a value of ‘TRUE’ so that defaulting can be handled within

```
the model itself. If the value of Null_Allowed is ‘FALSE’ or ‘NO’, then the simulator will
flag an error if the SPICE .MODEL card omits a value for this parameter.

**28.6.3.5** **Default Value**

If the Null_Allowed field specifies ‘TRUE’ for this parameter, then a default value may be
specified. This value is supplied for the parameter in the event that the SPICE .MODEL card
does not supply a value for the parameter. The default value must be of the correct type. The
Default Value field is introduced by the ‘Default_Value:’ keyword and is followed by a
numeric, boolean, complex, or string literal, as appropriate.

**28.6.3.6** **Limits**

Integer and real parameters may be constrained to accept a limited range of values. The following range syntax is used whenever such a range of values is required. A range is specified
by a square bracket followed by a value representing a lower bound separated by space from
another value representing an upper bound and terminated with a closing square bracket (e.g.”[0
10]”). The lower and upper bounds are inclusive. Either the lower or the upper bound may be
replaced by a hyphen (‘-’) to indicate that the bound is unconstrained (e.g. ‘[10 -]’ is read
as ‘the range of values greater than or equal to 10’). For a totally unconstrained range, a single
hyphen with no surrounding brackets may be used. The parameter value limit is introduced by
the ‘Limits:’ keyword and is followed by a range.

**28.6.3.7** **Vector**

The Vector field is used to specify whether a parameter is a vector or a scalar. Like the PORT
TABLE Vector field, it is introduced by the ‘Vector:’ keyword and followed by a boolean
value. ‘TRUE’ or ‘YES’ specify that the parameter is a vector. ‘FALSE’ or ‘NO’ specify that it
is a scalar.

**28.6.3.8** **Vector Bounds**

The valid sizes for a vector parameter are specified in the same manner as are port sizes (see
Section 28.6.2.7). However, in place of using a numeric range to specify valid vector bounds it
is also possible to specify the name of a port. When a parameter’s vector bounds are specified
in this way, the size of the vector parameter must be the same as the associated vector port.

### 28.6.4 Static Variable Table

The Static Variable table is introduced by the ‘Static_Var_Table:’ keyword. It defines the
set of valid static variables available to the code model. These are variables whose values are
retained between successive invocations of the code model by the simulator. The following
sections define the valid fields that may be specified in the Static Variable Table.


-----

**28.6.4.1** **Name**

The Static variable name is a valid C identifier that will be used in the code model to refer to
this static variable. It is introduced by the ‘Static_Var_Name:’ keyword followed by a valid
C identifier.

**28.6.4.2** **Description**

The description string is used to describe the purpose and function of the static variable. It is
introduced by the ‘Description:’ keyword followed by a string literal.

**28.6.4.3** **Data Type**

The static variable’s data type is specified by the Data Type field. The Data Type field is introduced by the keyword Data_Type: and is followed by a valid data type. Valid data types
include boolean, complex, int, real, string and pointer.

Note that pointer types are used to specify vector values; in such cases, the allocation of memory
for vectors must be handled by the code model through the use of the malloc() or calloc() C
function. Such allocation must only occur during the initialization cycle of the model (which
is identified in the code model by testing the INIT macro for a value of TRUE). Otherwise,
memory will be unnecessarily allocated each time the model is called.

Following is an example of the method used to allocate memory to be referenced by a static
pointer variable ‘x’ and subsequently use the allocated memory. The example assumes that the
value of ‘size’ is at least 2, else an error would result. The references to STATIC_VAR(x) that
appear in the example illustrate how to set the value of, and then access, a static variable named
‘x’. In order to use the variable ‘x’ in this manner, it must be declared in the Static Variable
Table of the code model’s Interface Specification File.
```
  /* Define local pointer variable */
   double *local.x;
  /* Allocate storage to be referenced by the static variable x. */
  /* Do this only if this is the initial call of the code model. */
  if (INIT == TRUE) {
     STATIC_VAR(x) = calloc(size, sizeof(double));
  }
  /* Assign the value from the static pointer value to the local */
  /* pointer variable. */
   local_x = STATIC_VAR(x);
  /* Assign values to first two members of the array */
   local_x[0] = 1.234;
   local_x[1] = 5.678;

```

-----

## 28.7 Model Definition File

The Model Definition File is a C source code file that defines a code model’s behavior given
input values that are passed to it by the simulator. The file itself is always given the name
cfunc.mod. In order to allow for maximum flexibility, passing of input, output, and simulatorspecific information is handled through accessor macros, which are described below. In addition, certain predefined library functions (e.g. smoothing interpolators, complex arithmetic
routines) are included in the simulator in order to ease the burden of the code model programmer. These are also described below.

### 28.7.1 Macros

The use of the accessor macros is illustrated in the following example. Note that the argument
to most accessor macros is the name of a parameter or port as defined in the Interface Specification File. Note also that all accessor macros except ‘ARGS’ resolve to an lvalue (C language
terminology for something that can be assigned a value). Accessor macros do not implement
expressions or assignments.
```
   void code.model(ARGS) /* private structure accessed by
                  accessor macros */
  {
  /* The following code fragments are intended to show how
    information in the argument list is accessed. The reader
    should not attempt to relate one fragment to another.
    Consider each fragment as a separate example.
  */
    double p,/* variable for use in the following code fragments */
       x, /* variable for use in the following code fragments */
       y; /* variable for use in the following code fragments */
    int i, /* indexing variable for use in the following */
       j; /* indexing variable for use in the following */
    UDN_Example_Type *a_ptr, /* A pointer used to access a
                      User-Defined Node type */
              *y_ptr; /* A pointer used to access a
                      User-Defined Node type */
    /* Initializing and outputting a User-Defined Node result */
    if(INIT) {
      OUTPUT(y) = malloc(sizeof(user.defined.struct));
      y_ptr = OUTPUT(y);
      y_ptr->component1 = 0.0;
      y_ptr->component2 = 0.0;
    }

```

-----

```
  else {
    y_ptr = OUTPUT(y);
    y_ptr->component1 = x1;
    y_ptr->component2 = x2;
  }
  /* Determining analysis type */
  if(ANALYSIS == AC) {
    /* Perform AC analysis -dependent operations here */
  }
  /* Accessing a parameter value from the .model card */
  p = PARAM(gain);
  /* Accessing a vector parameter from the .model card */
  for(i = 0; i < PARAM_SIZE(in_offset); i++)
    p = PARAM(in_offset[i]);
  /* Accessing the value of a simple real-valued input */
  x = INPUT(a);
  /* Accessing a vector input and checking for null port */
  if( ! PORT_NULL(a))
    for(i = 0; i < PORT_SIZE(a); i++)
     x = INPUT(a[i]);
  /* Accessing a digital input */
  x = INPUT(a);
  /* Accessing the value of a User-Defined Node input...
*/
  /* This node type includes two elements in its definition. */
  a_ptr = INPUT(a);
  x = a_ptr->component1;
  y = a_ptr->component2;
  /* Outputting a simple real-valued result */
  OUTPUT(out1) = 0.0;
  /* Outputting a vector result and checking for null */
  if( ! PORT_NULL(a))
    for(i = 0; i < PORT.SIZE(a); i++)
     OUTPUT(a[i]) = 0.0;
  /* Outputting the partial of output out1 w.r.t. input a */
  PARTIAL(out1,a) = PARAM(gain);
 /* Outputting the partial of output out2(i) w.r.t. input b(j) */

```

-----

```
    for(i = 0; i < PORT_SIZE(out2); i++) {
      for(j = 0; j < PORT_SIZE(b); j++) {
        PARTIAL(out2[i],b[j]) = 0.0;
      }
    }
    /* Outputting gain from input c to output out3 in an
     AC analysis */
    complex_gain_real = 1.0;
    complex_gain_imag = 0.0;
    AC_GAIN(out3,c) = complex_gain;
    /* Outputting a digital result */
    OUTPUT_STATE(out4) = ONE;
    /* Outputting the delay for a digital or user-defined output */
    OUTPUT_DELAY(out5) = 1.0e-9;
  }

```
**28.7.1.1** **Macro Definitions**

The full set of accessor macros is listed below. Arguments shown in parenthesis are examples
only. Explanations of the accessor macros are provided in the subsections below.
```
  Circuit Data:
     ARGS
     CALL_TYPE
     INIT
     ANALYSIS
     FIRST_TIMEPOINT
     TIME
     T(n)
     RAD_FREQ
     TEMPERATURE
  Parameter Data:
     PARAM(gain)
     PARAM_SIZE(gain)
     PARAM_NULL(gain)
  Port Data:
     PORT_SIZE(a)
     PORT_NULL(a)
     LOAD(a)
     TOTAL_LOAD(a)
  Input Data:
     INPUT(a)
     INPUT_STATE(a)
     INPUT_STRENGTH(a)

```

-----

```
  Output Data:
     OUTPUT(y)
     OUTPUT_CHANGED(a)
     OUTPUT_DELAY(y)
     OUTPUT_STATE(a)
     OUTPUT_STRENGTH(a)
  Partial Derivatives:
     PARTIAL(y,a)
  AC Gains:
     AC_GAIN(y,a)
  Static Variable:
     STATIC_VAR(x)

```
**28.7.1.2** **Circuit Data**
```
  ARGS
  CALL_TYPE
  INIT
  ANALYSIS
  FIRST_TIMEPOINT
  TIME
  T(n)
  RAD_FREQ
  TEMPERATURE

```
**ARGS is a macro that is passed in the argument list of every code model. It is there to provide**
a way of referencing each model to all of the remaining macro values. It must be present
in the argument list of every code model; it must also be the only argument present in the
argument list of every code model.

**CALL_TYPE is a macro that returns one of two possible symbolic constants. These are**
EVENT and ANALOG. Testing may be performed by a model using CALL TYPE to
determine whether it is being called by the analog simulator or the event-driven simulator. This will, in general, only be of value to a hybrid model such as the adc bridge or the
dac bridge.

**INIT is an integer (int) that takes the value 1 or 0 depending on whether this is the first call to**
the code model instance or not, respectively.

**ANALYSIS is an enumerated integer that takes values of DC, AC, or TRANSIENT.**

**FIRST TIMEPOINT is an integer that takes the value 1 or 0 depending on whether this is the**
first call for this instance at the current analysis step (i.e., time-point) or not, respectively.

**TIME is a double representing the current analysis time in a transient analysis. T(n) is a double**
vector giving the analysis time for a specified time-point in a transient analysis, where n
takes the value 0 or 1. T(0) is equal to TIME. T(1) is the last accepted time-point. (T(0) T(1)) is the time-step (i.e., the delta-time value) associated with the current time.

**RAD_FREQ is a double representing the current analysis frequency in an AC analysis expres-**
sed in units of radians per second.


-----

**TEMPERATURE is a double representing the current analysis temperature.**

**28.7.1.3** **Parameter Data**
```
  PARAM(gain)
  PARAM_SIZE(gain)
  PARAM_NULL(gain)

```
**PARAM(gain) resolves to the value of the scalar (i.e., non-vector) parameter ‘gain’ that was**
defined in the Interface Specification File tables. The type of ‘gain’ is the type given in
the ifspec.ifs file. The same accessor macro can be used regardless of type. If ‘gain’ is a
string, then PARAM(gain) would resolve to a pointer. PARAM(gain[n]) resolves to the
value of the nth element of a vector parameter ‘gain’.

**PARAM_SIZE(gain) resolves to an integer (int) representing the size of the ‘gain’ vector**
(which was dynamically determined when the SPICE deck was read). PARAM_SIZE(gain)
is undefined if ‘gain’ is a scalar.

**PARAM_NULL(gain) resolves to an integer with value 0 or 1 depending on whether a value**
was specified for gain, or whether the value is defaulted, respectively.

**28.7.1.4** **Port Data**
```
  PORT_SIZE(a)
  PORT_NULL(a)
  LOAD(a)
  TOTAL_LOAD(a)

```
**PORT_SIZE(a) resolves to an integer (int) representing the size of the ‘a’ port (which was**
dynamically determined when the SPICE deck was read). PORT_SIZE(a) is undefined if
gain is a scalar.

**PORT_NULL(a) resolves to an integer (int) with value 0 or 1 depending on whether the SPICE**
deck has a node specified for this port, or has specified that the port is null, respectively.

**LOAD(a) is used in a digital model to post a capacitive load value to a particular input or output**
port during the INIT pass of the simulator. All values posted for a particular event-driven
node using the LOAD() macro are summed, producing a total load value.

**TOTAL_LOAD(a) returns a double value that represents the total capacitive load seen on a**
specified node to which a digital code model is connected. This information may be used
after the INIT pass by the code model to modify the delays it posts with its output states
and strengths. Note that this macro can also be used by non-digital event-driven code
models (see LOAD(), above).


-----

**28.7.1.5** **Input Data**
```
  INPUT(a)
  INPUT_STATE(a)
  INPUT_STRENGTH(a)

```
**INPUT(a) resolves to the value of the scalar input a that was defined in the Interface Specifi-**
cation File tables (a can be either a scalar port or a port value from a vector; in the latter
case, the notation used would be a[i], where i is the index value for the port). The
type of a is the type given in the ifspec.ifs file. The same accessor macro can be used
regardless of type.

**INPUT_STATE(a) resolves to the state value defined for digital node types. These will be one**
of the symbolic constants ZERO, ONE, or UNKNOWN.

**INPUT_STRENGTH(a) resolves to the strength with which a digital input node is being dri-**
ven. This is determined by a resolution algorithm that looks at all outputs to a node and
determines its final driven strength. This value in turn is passed to a code model when
requested by this macro. Possible strength values are:
1. STRONG
2. RESISTIVE
3. HI_IMPEDANCE
4. UNDETERMINED

**28.7.1.6** **Output Data**
```
  OUTPUT(y)
  OUTPUT_CHANGED(a)
  OUTPUT_DELAY(y)
  OUTPUT_STATE(a)
  OUTPUT_STRENGTH(a)

```
**OUTPUT(y) resolves to the value of the scalar output ‘y’ that was defined in the Interface**
Specification File tables. The type of ‘y’ is the type given in the ifspec.ifs file. The same
accessor macro can be used regardless of type. If ‘y’ is a vector, then OUTPUT(y) would
resolve to a pointer.

**OUTPUT_CHANGED(a) may be assigned one of two values for any particular output from**
a digital code model. If assigned the value TRUE (the default), then an output state,
strength and delay must be posted by the model during the call. If, on the other hand, no
change has occurred during that pass, the OUTPUT_CHANGED(a) value for an output
can be set to FALSE. In this case, no state, strength or delay values need subsequently
be posted by the model. Remember that this macro applies to a single output port. If a
model has multiple outputs that have not changed, OUTPUT_CHANGED(a) must be set
to FALSE for each of them.

**OUTPUT_DELAY(y) may be assigned a double value representing a delay associated with**
a particular digital or User-Defined Node output port. Note that this macro must be set
for each digital or User-Defined Node output from a model during each pass, unless the


-----

OUTPUT_CHANGED(a) macro is invoked (see above). Note also that a non-zero value
must be assigned to OUTPUT_DELAY(). Assigning a value of zero (or a negative value)
will cause an error.

**OUTPUT_STATE(a) may be assigned a state value for a digital output node. Valid values are**
ZERO, ONE, and UNKNOWN. This is the normal way of posting an output state from a
digital code model.

**OUTPUT_STRENGTH(a) may be assigned a strength value for a digital output node. This**
is the normal way of posting an output strength from a digital code model. Valid values
are:
1. STRONG
2. RESISTIVE
3. HI_IMPEDANCE
4. UNDETERMINED

**28.7.1.7** **Partial Derivatives**
```
  PARTIAL(y,a)
  PARTIAL(y[n],a)
  PARTIAL(y,a[m])
  PARTIAL(y[n],a[m])

```
**PARTIAL(y,a) resolves to the value of the partial derivative of scalar output ‘y’ with respect**
to scalar input ‘a’. The type is always double since partial derivatives are only defined for
nodes with real valued quantities (i.e., analog nodes).

The remaining uses of PARTIAL are shown for the cases in which either the output, the input,
or both are vectors.

Partial derivatives are required by the simulator to allow it to solve the non-linear equations
that describe circuit behavior for analog nodes. Since coding of partial derivatives can become
difficult and error-prone for complex analog models, you may wish to consider using the cm
analog auto partial() code model support function instead of using this macro.

**28.7.1.8** **AC Gains**
```
  AC_GAIN(y,a)
  AC_GAIN(y[n],a)
  AC_GAIN(y,a[m])
  AC_GAIN(y[n],a[m])

```
**AC_GAIN(y,a) resolves to the value of the AC analysis gain of scalar output ‘y’ from scalar**
input ‘a’. The type is always a structure (Complex_t) defined in the standard code model
header file:
```
  typedef struct Complex_s {
  double real; /* The real part of the complex number */
  double imag; /* The imaginary part of the complex number */
  }Complex_t;

```

-----

The remaining uses of AC_GAIN are shown for the cases in which either the output, the input,
or both are vectors.

**28.7.1.9** **Static Variables**
```
  STATIC_VAR(x)

```
**STATIC_VAR(x) resolves to an lvalue or a pointer that is assigned the value of some scalar**
code model result or state defined in the Interface Spec File tables, or a pointer to a value
or a vector of values. The type of ‘x’ is the type given in the Interface Specification
File. The same accessor macro can be used regardless of type since it simply resolves
to an lvalue. If ‘x’ is a vector, then STATIC_VAR(x) would resolve to a pointer. In this
case, the code model is responsible for allocating storage for the vector and assigning the
pointer to the allocated storage to STATIC_VAR(x).

**28.7.1.10** **Accessor Macros**

Table 28.3 describes the accessor macros available to the Model Definition File programmer and
their C types. The PARAM and STATIC_VAR macros, whose types are labeled CD (context
dependent), return the type defined in the Interface Specification File. Arguments listed with
‘[i]’ take an optional square bracket delimited index if the corresponding port or parameter is a
vector. The index may be any C expression - possibly involving calls to other accessor macros
(e.g.,” OUTPUT(out[PORT_SIZE(out)-1])”)

|Name|Type|Args|Description|
|---|---|---|---|
|AC_GAIN|Complex_t|y[i],x[i]|AC gain of output y with respect to input x.|
|ANALYSIS|enum|<none>|Type of analysis: DC, AC, TRANSIENT.|
|ARGS|Mif_Private_t|<none>|Standard argument to all code model function.|
|CALL_TYPE|enum|<none>|Type of model evaluation call: ANALOG or EVENT.|
|INIT|Boolean_t|<none>|Is this the first call to the model?|
|INPUT|double or void*|name[i]|Value of analog input port, or value of structure pointer for User-Defined Node port.|
|INPUT_STATE|enum|name[i]|State of a digital input: ZERO, ONE, or UNKNOWN.|
|INPUT_STRENGHT|enum|name[i]|Strength of digital input: STRONG, RESISTIVE, HI IMPEDANCE, or UNDETERMINED.|
|INPUT_TYPE|char*|name[i]|The port type of the input.|
|LOAD|double|name[i]|The digital load value placed on a port by this model.|


-----

Table 28.3: Accessor macros

|MESSAGE|char*|name[i]|A message output by a model on an event-driven node.|
|---|---|---|---|
|OUTPUT|double or void*|name[i]|Value of the analog output port or value of structure pointer for User-Defined Node port.|
|OUTPUT_CHANGED|Boolean_t|name[i]|Has a new value been assigned to this event-driven output by the model?|
|OUTPUT_DELAY|double|name[i]|Delay in seconds for an event-driven output.|
|OUTPUT_STATE|enum|name[i]|State of a digital output: ZERO, ONE, or UNKNOWN.|
|OUTPUT_STRENGTH|enum|name[i]|Strength of digital output: STRONG, RESISTIVE, HI_IMPEDANCE, or UNDETERMINED.|
|OUTPUT_TYPE|char*|name[i]|The port type of the output.|
|PARAM|CD|name[i]|Value of the parameter.|
|PARAM_NULL|Boolean_t|name[i]|Was the parameter not included on the SPICE .model card ?|
|PARAM_SIZE|int|name|Size of parameter vector.|
|PARTIAL|double|y[i],x[i]|Partial derivative of output y with respect to input x.|
|PORT_NULL|Mif_Boolean_t|name|Has this port been specified as unconnected?|
|PORT_SIZE|int|name|Size of port vector.|
|RAD_FREQ|double|<none>|Current analysis frequency in radians per second.|
|STATIC_VAR|CD|name|Value of a static variable.|
|STATIC_VAR_SIZE|int|name|Size of static var vector (currently unused).|
|T(n)|int|index|Current and previous analysis times (T(0) = TIME = current analysis time, T(1) = previous analysis time).|
|TEMPERATURE|double|<none>|Current analysis temperature.|
|TIME|double|<none>|Current analysis time (same as T(0)).|
|TOTAL_LOAD|double|name[i]|The total of all loads on the node attached to this event driven port.|


-----

### 28.7.2 Function Library

**28.7.2.1** **Overview**

Aside from the accessor macros, the simulator also provides a library of functions callable from
within code models. The header file containing prototypes to these functions is automatically
inserted into the Model Definition File for you. The complete list of available functions follows:
```
  Smoothing Functions:
     void cm_smooth_corner
     void cm_smooth_discontinuity
     double cm_smooth_pwl
  Model State Storage Functions:
     void cm_analog_alloc
     void cm_event_alloc
     void *cm_analog_get_ptr
     void *cm_event_get_ptr
  Integration and Convergence Functions:
     int cm_analog_integrate
     int cm_analog_converge
     void cm_analog_not_converged
     void cm_analog_auto_partial
     double cm_analog_ramp_factor
  Message Handling Functions:
     char *cm_message_get_errmsg
     void cm_message_send
  Breakpoint Handling Functions:
     int cm_analog_set_temp_bkpt
     int cm_analog_set_perm_bkpt
     int cm_event_queue
  Special Purpose Functions:
     void cm_climit_fcn
     double cm_netlist_get_c
     double cm_netlist_get_l
     char *cm_get_path
  Complex Math Functions:
     complex_t cm_complex_set
     complex_t cm_complex_add
     complex_t cm_complex_sub
     complex_t cm_complex_mult
     complex_t cm_complex_div

```
**28.7.2.2** **Smoothing Functions**
```
  void
  cm_smooth_corner(x_input, x_center, y_center, domain,
           lower_slope, upper_slope, y_output, dy_dx)

```

-----

```
     double x_input; /* The value of the x input */
     double x_center; /* The x intercept of the two slopes */
     double y_center; /* The y intercept of the two slopes */
     double domain; /* The smoothing domain */
     double lower_slope; /* The lower slope */
     double upper_slope; /* The upper slope */
     double *y_output; /* The smoothed y output */
     double *dy_dx; /* The partial of y wrt x */
  void
  cm_smooth_discontinuity(x_input, x_lower, y_lower, x_upper, y_upper
               y_output, dy_dx)
     double x_input; /* The x value at which to compute y */
     double x_lower; /* The x value of the lower corner */
     double y_lower; /* The y value of the lower corner */
     double x_upper; /* The x value of the upper corner */
     double y_upper; /* The y value of the upper corner */
     double *y_output; /* The computed smoothed y value */
     double *dy_dx; /* The partial of y wrt x */
  double
  cm_smooth_pwl(x_input, x, y, size, input_domain, dout_din)
     double x_input; /* The x input value */
     double *x; /* The vector of x values */
     double *y; /* The vector of y values */
     int size; /* The size of the xy vectors */
     double input_domain; /* The smoothing domain */
     double *dout_din; /* The partial of the output wrt the input */
cm_smooth_corner() automates smoothing between two arbitrarily-sloped lines that meet

```
at a single center point. You specify the center point (x_center, y_center), plus a domain (x-valued delta) above and below x_center. This defines a smoothing region about the
center point. Then, the slopes of the meeting lines outside of this smoothing region are specified (lower_slope, upper_slope). The function then interpolates a smoothly-varying output
(*y_output) and its derivative (*dy_dx) for the x_input value. This function helps to automate the smoothing of piecewise-linear functions, for example. Such smoothing aids the
simulator in achieving convergence.
```
cm_smooth_discontinuity() allows you to obtain a smoothly-transitioning output (*y_output)

```
that varies between two static values (y_lower, y_upper) as an independent variable (x_input)
transitions between two values (x_lower, x_upper). This function is useful in interpolating
between resistances or voltage levels that change abruptly between two values.
```
cm_smooth_pwl() duplicates much of the functionality of the predefined pwl code model. The

```
cm smooth pwl() takes an input value plus x-coordinate and y-coordinate vector values along
with the total number of coordinate points used to describe the piecewise linear transfer function
and returns the interpolated or extrapolated value of the output based on that transfer function.


-----

More detail is available by looking at the description of the pwl code model. Note that the
output value is the function’s returned value.

**28.7.2.3** **Model State Storage Functions**
```
  void cm_analog_alloc(tag, size)
     int tag; /* The user-specified tag for this block of memory */
     int size; /* The number of bytes to allocate */
  void cm_event_alloc(tag, size)
     int tag; /* The user-specified tag for the memory block */
     int size; /* The number of bytes to be allocated */
  void *cm_analog_get_ptr(tag, timepoint)
     int tag; /* The user-specified tag for this block of memory */
     int timepoint; /* The timepoint of interest - 0=current 1=previous */
  void *cm_event_get_ptr(tag, timepoint)
     int tag; /* The user-specified tag for the memory block */
     int timepoint; /* The timepoint - 0=current, 1=previous */
cm_analog_alloc() and cm_event_alloc() allow you to allocate storage space for analog

```
and event-driven model state information. The storage space is not static, but rather represents
a storage vector of two values that rotate with each accepted simulator time-point evaluation.
This is explained more fully below. The ‘tag’ parameter allows you to specify an integer tag
when allocating space. This allows more than one rotational storage location per model to be
allocated. The ‘size’ parameter specifies the size in bytes of the storage (computed by the C
language sizeof() operator). Both cm_analog_alloc() and cm_event_alloc() will not return pointers to the allocated space, as has been available (and buggy) from the original XSPICE
code. cm_analog_alloc() should be used by an analog model; cm_event_alloc() should
be used by an event-driven model.
```
*cm_analog_get_ptr() and *cm_event_get_ptr() retrieve the pointer location of the ro
```
tational storage space previously allocated by cm_analog_alloc() or cm_event_alloc().
**Important notice: These functions must be called only after all memory allocation (all calls to**
```
cm_analog_alloc() or cm_event_alloc()) have been done. All pointers returned between

```
calls to memory allocation will become obsolete (point to freed memory because of an internal
realloc). The functions take the integer ‘tag’ used to allocate the space, and an integer from 0 to
1 that specifies the time-point with which the desired state variable is associated (e.g. timepoint
= 0 will retrieve the address of storage for the current time-point; timepoint = 1 will retrieve
the address of storage for the last accepted time-point). Note that once a model is exited,
**storage to the current time-point state storage location (i.e., timepoint = 0) will, upon the**
**next time-point iteration, be rotated to the previous location (i.e., timepoint = 1). When**
rotation is done, a copy of the old ‘timepoint = 0’ storage value is placed in the new ‘timepoint
= 0’ storage location. Thus, if a value does not change for a particular iteration, specific writing


-----

to ‘timepoint = 0’ storage is not required. These features allow a model coder to constantly
know which piece of state information is being dealt with within the model function at each
time-point.

**28.7.2.4** **Integration and Convergence Functions**
```
  int cm_analog_integrate(integrand, integral, partial)
     double integrand; /* The integrand */
     double *integral; /* The current and returned value of integral */
     double *partial; /* The partial derivative of integral wrt integrand */
  int cm_analog_converge(state)
     double *state; /* The state to be converged */
  void cm_analog_not_converged()
  void cm_analog_auto_partial()
  double cm_ramp_factor()
cm_analog_integrate() takes as input the integrand (the input to the integrator) and produ
```
ces as output the integral value and the partial of the integral with respect to the integrand. The
integration itself is with respect to time, and the pointer to the integral value must have been
previously allocated using cm_analog_alloc() and *cm_analog_get_ptr(). This is required because of the need for the integrate routine itself to have access to previously-computed
values of the integral.
```
cm_analog_converge() takes as an input the address of a state variable that was previously

```
allocated using cm_analog_alloc() and *cm_analog_get_ptr(). The function itself serves
to notify the simulator that for each time-step taken, that variable must be iterated upon until it
converges.
```
cm_analog_not_converged() is a function that can and should be called by an analog model

```
whenever it performs internal limiting of one or more of its inputs to aid in reaching convergence. This causes the simulator to call the model again at the current time-point and continue
solving the circuit matrix. A new time-point will not be attempted until the code model returns
without calling the cm_analog_not_converged() function. For circuits that have trouble reaching a converged state (often due to multiple inputs changing too quickly for the model to
react in a reasonable fashion), the use of this function is virtually mandatory.
```
cm_analog_auto_partial() may be called at the end of a code model function in lieu of

```
calculating the values of partial derivatives explicitly in the function. When this function is called, no values should be assigned to the PARTIAL macro since these values will be computed
automatically by the simulator. The automatic calculation of partial derivatives can save considerable time in designing and coding a model, since manual computation of partial derivatives
can become very complex and error-prone for some models. However, the automatic evaluation
may also increase simulation run time significantly. Function cm_analog_auto_partial()
causes the model to be called N additional times (for a model with N inputs) with each input
varied by a small amount (1e-6 for voltage inputs and 1e-12 for current inputs). The values


-----

of the partial derivatives of the outputs with respect to the inputs are then approximated by the
simulator through divided difference calculations.
```
cm_analog_ramp_factor() will then return a value from 0.0 to 1.0 that indicates whether

```
or not a ramp time value requested in the SPICE analysis deck (with the use of .option
```
ramptime=<duration>) has elapsed. If the RAMPTIME option is used, then cm_analog_ramp_factor

```
returns a 0.0 value during the DC operating point solution and a value that is between 0.0 and
1.0 during the ramp. A 1.0 value is returned after the ramp is over or if the RAMPTIME option is not used. This value is intended as a multiplication factor to be used with all model
outputs that would ordinarily experience a ‘power-up’ transition. Currently, all sources within
the simulator are automatically ramped to the ‘final’ time-zero value if a RAMPTIME option is
specified.

**28.7.2.5** **Message Handling Functions**
```
  char *cm_message_get_errmsg()
  int cm_message_send(char *msg)
  char *msg; /* The message to output. */
*cm_message_get_errmsg() is a function designed to be used with other library functions

```
to provide a way for models to handle error situations. More specifically, whenever a library
function that returns type int is executed from a model, it will return an integer value, n. If this
value is not equal to zero (0), then an error condition has occurred (likewise, functions that return pointers will return a NULL value if an error has occurred). At that point, the model can invoke *cm_message_get_errmsg to obtain a pointer to an error message. This can then in turn
be displayed to the user or passed to the simulator interface through the cm_message_send()
function. The C code required for this is as follows:
```
  err = cm_analog_integrate(in, &out, &dout_din);
  if (err) {
     cm_message_send(cm_message_get_errmsg());
  }
  else { ...
cm_message_send() sends messages to either the standard output screen or to the simulator

```
interface, depending on which is in use.

**28.7.2.6** **Breakpoint Handling Functions**
```
  int cm_analog_set_perm_bkpt(time)
     double time; /* The time of the breakpoint to be set */
  int cm_analog_set_temp_bkpt(time)
     double time; /* The time of the breakpoint to be set */
  int cm_event_queue(time)
     double time; /* The time of the event to be queued */

```

-----

```
cm_analog_set_perm_bkpt() takes as input a time value. This value is posted to the analog

```
simulator algorithm and is used to force the simulator to choose that value as a breakpoint at
some time in the future. The simulator may choose as the next time-point a value less than the
input, but not greater. Also, regardless of how many time-points pass before the breakpoint is
reached, it will not be removed from posting. Thus, a breakpoint is guaranteed at the passed
time value. Note that a breakpoint may also be set for a time prior to the current time, but this
will result in an error if the posted breakpoint is prior to the last accepted time (i.e., T(1)).
```
cm_analog_set_temp_bkpt() takes as input a time value. This value is posted to the simu
```
lator and is used to force the simulator, for the next time-step only, to not exceed the passed
time value. The simulator may choose as the next time-point a value less than the input, but not
greater. In addition, once the next time-step is chosen, the posted value is removed regardless
of whether it caused the break at the given time-point. This function is useful in the event that
a time-point needs to be retracted after its first posting in order to recalculate a new breakpoint
based on new input data (for controlled oscillators, controlled one-shots, etc), since temporary
breakpoints automatically ‘go away’ if not reposted each time-step. Note that a breakpoint may
also be set for a time prior to the current time, but this will result in an error if the posted
breakpoint is prior to the last accepted time (i.e., T(1)).
```
cm_event_queue() is similar to cm_analog_set_perm_bkpt(), but functions with event
```
driven models. When invoked, this function causes the model to be queued for calling at the
specified time. All other details applicable to cm_analog_set_perm_bkpt() apply to this
function as well.

**28.7.2.7** **Special Purpose Functions**
```
  void
  cm_climit_fcn(in, in_offset, cntl_upper, cntl_lower, lower_delta, upper_delta,
          limit_range, gain, fraction, out_final, pout_pin_final,
          pout_pcntl_lower_final, pout_pcntl_upper_final)
     double in; /* The input value */
     double in-offset; /* The input offset */
     double cntl_upper; /* The upper control input value */
     double cntl_lower; /* The lower control input value */
     double lower_delta; /* The delta from control to limit value */
     double upper_delta; /* The delta from control to limit value */
     double limit_range; /* The limiting range */
     double gain; /* The gain from input to output */
     int percent; /* The fraction vs. absolute range flag */
     double *out_final; /* The output value */
     double *pout_pin_final; /* The partial of output wrt input */
     double *pout_pcntl_lower_final; /* The partial of output wrt lower
                       control input */
     double *pout_pcntl_upper:final; /* The partial of output wrt upper
                       control input */
  double cm_netlist_get_c()

```

-----

```
  double cm_netlist_get_l()
  char* cm_get_path()
cm_climit_fcn() is a very specific function that mimics the behavior of the climit code model

```
(see the Predefined Models section). In brief, the cm_climit_fcn() takes as input an in value,
an offset, and controlling upper and lower values. Parameter values include delta values for
the controlling inputs, a smoothing range, gain, and fraction switch values. Outputs include
the final value, plus the partial derivatives of the output with respect to signal input, and both
control inputs. These all operate identically to the similarly-named inputs and parameters of the
climit model.

The function performs a limit on the in value, holding it to within some delta of the controlling inputs, and handling smoothing, etc. The cm_climit_fcn() was originally used in the
ilimit code model to handle much of the primary limiting in that model, and can be used by a
code model developer to take care of limiting in larger models that require it. See the detailed
description of the climit model for more in-depth description.
```
cm_netlist_get_c() and cm_netlist_get_l() functions search the analog circuitry to

```
which their input is connected, and total the capacitance or inductance, respectively, found
at that node. The functions, as they are currently written, assume they are called by a model
that has only one single-ended analog input port.
```
cm_get_path() fetches the path of the first netlist input file found on the ngspice command

```
line or in the source command, which ngspice saves to the global variable Infile_Path.

**28.7.2.8** **Complex Math Functions**
```
  Complex_t cm_complex_set (real_part, imag_part)
     double real_part; /* The real part of the complex number */
     double imag_part; /* The imaginary part of the complex number */
  Complex_t cm_complex_add (x, y)
     Complex_t x; /* The first operand of x + y */
     Complex_t y; /* The second operand of x + y */
  Complex_t cm_complex_sub (x, y)
     Complex_t x; /* The first operand of x - y */
     Complex_t y; /* The second operand of x - y */
  Complex_t cm_complex_mult (x, y)
     Complex_t x; /* The first operand of x * y */
     Complex_t y; /* The second operand of x * y */
  Complex_t cm_complex_div (x, y)
     Complex_t x; /* The first operand of x / y */

```

-----

```
     Complex_t y; /* The second operand of x / y */
cm_complex_set() takes as input two doubles, and converts these to a Complex_t. The first

```
double is taken as the real part, and the second is taken as the imaginary part of the resulting
complex value.
```
cm_complex_add(), cm_complex_sub(), cm_complex_mult(), and cm_complex_div()

```
each take two complex values as inputs and return the result of a complex addition, subtraction,
multiplication, or division, respectively.

## 28.8 User-Defined Node Definition File

The User-Defined Node Definition File (udnfunc.c) defines the C functions that implement
basic operations on user-defined nodes such as data structure creation, initialization, copying,
and comparison. Unlike the Model Definition File that uses the Code Model Preprocessor to
translate Accessor Macros, the User-Defined Node Definition file is a pure C language file. This
file uses macros to isolate you from data structure definitions, but the macros are defined in a
standard header file (EVTudn.h), and translations are performed by the standard C Preprocessor.

When you create a directory for a new User-Defined Node, e.g. /ngspice/src/xspice/icm/xtraevt/new_
add a new User-Defined Node Definition File udnfunc.c (see the example in Chapt. 28.8.3),
and place a structure of type ’Evt_Udn_Info_t’ at its bottom.

This structure contains the type name for the node, a description string, and pointers to each
of the functions that define the node. This structure is complete except for a text string that
describes the node type. This string is stubbed out and may be edited by you if desired.


-----

### 28.8.1 Macros

Name Type Description

MALLOCED_PTR void * Assign pointer to allocated structure
to this macro

STRUCT_PTR void * A pointer to a structure of the defined
type

STRUCT_PTR_1 void * A pointer to a structure of the defined
type

STRUCT_PTR_2 void * A pointer to a structure of the defined
type

EQUAL Mif_Boolean_t Assign TRUE or FALSE to this macro
according to the results of structure
comparison

INPUT_STRUCT_PTR void * A pointer to a structure of the defined
type

OUTPUT_STRUCT_PTR void * A pointer to a structure of the defined
type

INPUT_STRUCT_PTR_ARRAY void ** An array of pointers to structures of
the defined type

INPUT_STRUCT_PTR_ARRAY_SIZE int The size of the array

STRUCT_MEMBER_ID char * A string naming some part of the
structure

PLOT_VAL double The value of the specified structure
member for plotting purposes

PRINT_VAL char * The value of the specified structure
member for printing purposes

Table 28.4: User-Defined Node Macros

You must code the functions described in the following section using the macros appropriate
for the particular function. You may elect whether not to provide the optional functions.

It is an error to use a macro not defined for a function. Note that a review of the sample
directories for the real and int UDN types will make the function usage clearer.

The macros used in the User-Defined Node Definition File to access and assign data values
are defined in Table 28.4. The translations of the macros and of macros used in the function
[argument lists are defined in the Interface Diesign Document for the XSPICE Simulator.](http://users.ece.gatech.edu/~mrichard/Xspice/XSpice_InterfaceDesignDoc_Sep92.pdf)

### 28.8.2 Function Library

The functions (required and optional) that define a User-Defined Node are listed below. For
optional functions not used, the pointer in the Evt_Udn_Info_t structure can be changed to
NULL.

Required functions:

|Name|Type|Description|
|---|---|---|
|MALLOCED_PTR|void *|Assign pointer to allocated structure to this macro|
|STRUCT_PTR|void *|A pointer to a structure of the defined type|
|STRUCT_PTR_1|void *|A pointer to a structure of the defined type|
|STRUCT_PTR_2|void *|A pointer to a structure of the defined type|
|EQUAL|Mif_Boolean_t|Assign TRUE or FALSE to this macro according to the results of structure comparison|
|INPUT_STRUCT_PTR|void *|A pointer to a structure of the defined type|
|OUTPUT_STRUCT_PTR|void *|A pointer to a structure of the defined type|
|INPUT_STRUCT_PTR_ARRAY|void **|An array of pointers to structures of the defined type|
|INPUT_STRUCT_PTR_ARRAY_SIZE|int|The size of the array|
|STRUCT_MEMBER_ID|char *|A string naming some part of the structure|
|PLOT_VAL|double|The value of the specified structure member for plotting purposes|
|PRINT_VAL|char *|The value of the specified structure member for printing purposes|


-----

```
  create Allocate data structure used as inputs and outputs to
         code models.
  initialize Set structure to appropriate initial value for first use as
         model input.
  copy Make a copy of the contents into created but possibly
         uninitialized structure.
  compare Determine if two structures are equal in value.

```
Optional functions:
```
  dismantle Free allocations inside structure (but not structure itself).
  invert Invert logical value of structure.
  resolve Determine the resultant when multiple outputs are connected
         to a node.
  plot_val Output a real value for specified structure component for
         plotting purposes.
  print_val Output a string value for specified structure component for
         printing.
  ipc_val Output a binary representation of the structure suitable
         for sending over the IPC channel.

```
The required actions for each of these functions are described in the following subsections. In
each function, you have to replace the XXX with the node type name specified. The macros
used in implementing the functions are described in a later section.

**28.8.2.1** **Function udn_XXX_create**

Allocate space for the data structure defined for the User-Defined Node to pass data between
models. Then assign pointer created by the storage allocator (e.g. malloc) to MALLOCED_PTR.

**28.8.2.2** **Function udn_XXX_initialize**

Assign STRUCT_PTR to a pointer variable of defined type and then initialize the value of the
structure.


-----

**28.8.2.3** **Function udn_XXX_compare**

Assign STRUCT_PTR_1 and STRUCT_PTR_2 to pointer variables of the defined type. Compare the two structures and assign either TRUE or FALSE to EQUAL.

**28.8.2.4** **Function udn_XXX_copy**

Assign INPUT_STRUCT_PTR and OUTPUT_STRUCT_PTR to pointer variables of the defined type and then copy the elements of the input structure to the output structure.

**28.8.2.5** **Function udn_XXX_dismantle**

Assign STRUCT_PTR to a pointer variable of defined type and then free any allocated substructures (but not the structure itself!). If there are no substructures, the body of this function
may be left null.

**28.8.2.6** **Function udn_XXX_invert**

Assign STRUCT_PTR to a pointer variable of the defined type, and then invert the logical value
of the structure.

**28.8.2.7** **Function udn_XXX_resolve**

Assign INPUT_STRUCT_PTR_ARRAY to a variable declared as an array of pointers of the
defined type - e.g.:
```
  <type> **struct_array;
  struct_array = INPUT_STRUCT_PTR_ARRAY;

```
Then, the number of elements in the array may be determined from the integer valued INPUT_STRUCT_PTR_ARRAY_SIZE macro.

Assign OUTPUT_STRUCT_PTR to a pointer variable of the defined type. Scan through the
array of structures, compute the resolved value, and assign it into the output structure.

**28.8.2.8** **Function udn_XXX_plot_val**

Assign STRUCT_PTR to a pointer variable of the defined type. Then, access the member of
the structure specified by the string in STRUCT_MEMBER_ID and assign some real valued
quantity for this member to PLOT_VALUE.

**28.8.2.9** **Function udn_XXX_print_val**

Assign STRUCT_PTR to a pointer variable of the defined type. Then, access the member of
the structure specified by the string in STRUCT_MEMBER_ID and assign some string valued
quantity for this member to PRINT_VALUE.

If the string is not static, a new string should be allocated on each call. Do not free the allocated
strings.


-----

**28.8.2.10** **Function udn_XXX_ipc_val**

Use STRUCT_PTR to access the value of the node data. Assign to IPC_VAL a binary representation of the data. Typically this can be accomplished by simply assigning STRUCT_PTR
to IPC_VAL.

Assign to IPC_VAL_SIZE an integer representing the size of the binary data in bytes.

### 28.8.3 Example UDN Definition File

The following is an example UDN Definition File that is included with the XSPICE system. It
illustrates the definition of the functions described above for a User-Defined Node type int (for
```
integer node type), to be found in file /ngspice/src/xspice/icm/xtraevt/int/udnfunc.c.
  #include <stdio.h>
  #include "ngspice/cm.h"
  #include "ngspice/evtudn.h"
   void *tmalloc(size_t);
  #define TMALLOC(t,n) (t*) tmalloc(sizeof(t)*(size_t)(n))
  /* macro to ignore unused variables and parameters */
  #define NG_IGNORE(x) (void)x
  /* ************************************************* */
   static void udn_int_create(CREATE_ARGS)
  {
     /* Malloc space for an int */
     MALLOCED_PTR = TMALLOC(int, 1);
  }
  /* ************************************************* */
   static void udn_int_dismantle(DISMANTLE_ARGS)
  {
     NG_IGNORE(STRUCT_PTR);
     /* Do nothing. There are no internally malloc’ed
       things to dismantle */
  }
  /* ************************************************* */
   static void udn_int_initialize(INITIALIZE_ARGS)
  {
     int *int_struct = (int *) STRUCT_PTR;
     /* Initialize to zero */

```

-----

```
  *int_struct = 0;
}
/* ************************************************* */
static void udn_int_invert(INVERT_ARGS)
{
  int *int_struct = (int *) STRUCT_PTR;
  /* Invert the state */
  *int_struct = -(*int_struct);
}
/* ************************************************* */
static void udn_int_copy(COPY_ARGS)
{
  int *int_from_struct = (int *) INPUT_STRUCT_PTR;
  int *int_to_struct = (int *) OUTPUT_STRUCT_PTR;
  /* Copy the structure */
  *int_to_struct = *int_from_struct;
}
/* ************************************************* */
static void udn_int_resolve(RESOLVE_ARGS)
{
  int **array = (int**)INPUT_STRUCT_PTR_ARRAY;
  int *out = (int *) OUTPUT_STRUCT_PTR;
  int num_struct = INPUT_STRUCT_PTR_ARRAY_SIZE;
  int sum;
  int i;
  /* Sum the values */
  for(i = 0, sum = 0; i < num_struct; i++)
     sum += *(array[i]);
  /* Assign the result */
  *out = sum;
}
/* ************************************************* */
static void udn_int_compare(COMPARE_ARGS)
{
  int *int_struct1 = (int *) STRUCT_PTR_1;

```

-----

```
  int *int_struct2 = (int *) STRUCT_PTR_2;
  /* Compare the structures */
  if((*int_struct1) == (*int_struct2))
     EQUAL = TRUE;
  else
     EQUAL = FALSE;
}
/* ************************************************* */
static void udn_int_plot_val(PLOT_VAL_ARGS)
{
  int *int_struct = (int *) STRUCT_PTR;
  NG_IGNORE(STRUCT_MEMBER_ID);
  /* Output a value for the int struct */
  PLOT_VAL = *int_struct;
}
/* ************************************************* */
static void udn_int_print_val(PRINT_VAL_ARGS)
{
  int *int_struct = (int *) STRUCT_PTR;
  NG_IGNORE(STRUCT_MEMBER_ID);
  /* Allocate space for the printed value */
  PRINT_VAL = TMALLOC(char, 30);
  /* Print the value into the string */
  sprintf(PRINT_VAL, "%8d", *int_struct);
}
/* ************************************************* */
static void udn_int_ipc_val(IPC_VAL_ARGS)
{
  /* Simply return the structure and its size */
  IPC_VAL = STRUCT_PTR;
  IPC_VAL_SIZE = sizeof(int);
}
Evt_Udn_Info_t udn_int_info = {
  "int",
  "integer valued data",
  udn_int_create,

```

-----

```
  udn_int_dismantle,
  udn_int_initialize,
  udn_int_invert,
  udn_int_copy,
  udn_int_resolve,
  udn_int_compare,
  udn_int_plot_val,
  udn_int_print_val,
  udn_int_ipc_val
};

```

-----

