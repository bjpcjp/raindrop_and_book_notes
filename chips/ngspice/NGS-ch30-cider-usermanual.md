# Chapter 30

 CIDER User’s Manual

The CIDER User’s Manual that follows is derived from the original manual being part of the
[PhD thesis from David A. Gates from UC Berkeley. Unfortunately the manual here is not yet](http://www.eecs.berkeley.edu/Pubs/TechRpts/1993/2382.html)
complete, so please refer to the thesis for detailed information. Literature on CODECS, the
[predecessor of CIDER, is available here from UCB: TechRpt ERL-90-96 and TechRpt ERL-](http://www.eecs.berkeley.edu/Pubs/TechRpts/1990/1611.html)
[88-71.](http://www.eecs.berkeley.edu/Pubs/TechRpts/1988/1118.htmlTechRpt )

## 30.1 SPECIFICATION

Overview of numerical-device specification

The input to CIDER consists of a SPICE-like description of a circuit, its analyses and its compact device models, and PISCES-like descriptions of numerically analyzed device models. For
a description of the SPICE input format, consult the SPICE3 Users Manual [JOHN92].

To simulate devices numerically, two types of input must be added to the input file. The first
is a model description in which the common characteristics of a device class are collected. In
the case of numerical models, this provides all the information needed to construct a device
cross-section, such as, for example, the doping profile. The second type of input consists of one
or more element lines that specify instances of a numerical model, describe their connection to
the rest of the circuit, and provide additional element-specific information such as device layout
dimensions ans initial bias information.

The format of a numerical device model description differs from the standard approach used
for SPICE3 compact models. It begins the same way with one line containing the .MODEL
keyword followed by the name of the model, device type and modeling level. However, instead
of providing a single long list of parameters and their values, numerical model parameters are
grouped onto cards. Each type of card has its own set of valid parameters. In all cases, the
relative ordering of different types of cards is unimportant. However, for cards of the same type
(such as mesh-specification cards), their order in the input file can be important in determining
the device structure.

Each card begins on a separate line of the input file. In order to let CIDER know that card
lines are continuations of a numerical model description, each must begin with the continuation
character ‘+’. If there are too many parameters on a given card to allow it fit on a single line,
the card can be continued by adding a second ‘+’ to the beginning of the next line. However,
the name and value of a parameter should always appear on the same line.


-----

Several features are provided to make the numerical model format more convenient.

Blank space can follow the initial ‘+’ to separate it from the name of a card or the card continuation ‘+’. Blank lines are also permitted, as long as they also begin with an initial ‘+’.
Parentheses and commas can be used to visually group or separate parameter definitions. In
addition, while it is common to add an equal sign between a parameter and its value, this is not
strictly necessary.

The name of any card can be abbreviated, provided that the abbreviation is unique. Parameter
name abbreviations can also be used if they are unique in the list of a card’s parameters. Numeric
parameter values are treated identically as in SPICE3, so exponential notation, engineering
scale factors and units can be attached to parameter values: tau=10ns, nc=3.0e19cm^-3. In
SPICE3, the value of a FLAG model parameter is changed to TRUE simply by listing its name
on the model line. In CIDER, the value of a numerical model FLAG parameter can be turned
back to FALSE by preceding it by a caret ‘^’. This minimizes the amount of input change
needed when features such as debugging are turned on and off. In certain cases it is necessary
to include file names in the input description and these names may contain capital letters. If
the file name is part of an element line, the inout parser will convert these capitals to lowercase
letters. To protect capitalization at any time, simply enclose the string in double quotes ‘”’.

The remainder of this manual describes how numerically analyzed elements and models can be
used in CIDER simulations. The manual consists of three parts. First, all of the model cards and
their parameters are described. This is followed by a section describing the three basic types of
numerical models and their corresponding element lines. In the final section, several complete
examples of CIDER simulations are presented.

Several conventions are used in the card descriptions. In the card synopses, the name of a
card is followed by a list of parameter classes. Each class is represented by a section in the
card parameter table, in the same order as it appears in the synopsis line. Classes that contain
optional parameters are surrounded by brackets: [...]. Sometimes it only makes sense for a
single parameter to take effect. (For example, a material can not simultaneously be both Si
and SiO2.) In such cases, the various choices are listed sequentially, separated by colons. The
same parameter often has a number of different acceptable names, some of which are listed in
the parameter tables.[1] These aliases are separated by vertical bars: ‘|’. Finally, in the card
examples, the model continuation pluses have been removed from the card lines for clarity’s
sake.

### 30.1.1 Examples

The model description for a two-dimensional numerical diode might look something like what
follows. This example demonstrates many of the features of the input format described above.
Notice how the .MODEL line and the leading pluses form a border around the model description:

1Some of the possibilities are not listed in order to shorten the lengths of the parameter tables. This makes
the use of parameter abbreviations somewhat troublesome since an unlisted parameter may abbreviate to the same
name as one that is listed. CIDER will produce a warning when this occurs. Many of the undocumented parameter
names are the PISCES names for the same parameters. The adventurous soul can discover these names by delving
through the ‘cards’ directory of the source code distribution looking for the C parameter tables.


-----

Example: Numerical diode
```
  .MODEL M_NUMERICAL NUPD LEVEL=2
  + cardnamel numberl=val1 (number2 val2), (number3 = val3)
  + cardname2 numberl=val1 string1 = name1
  +
  + cardname3 numberl=val1, flag1, ^flag2
  + + number2=val2, flag3

```
The element line for an instance of this model might look something like the following. Double
quotes are used to protect the file name from decapitalization:
```
  dl 1 2 M_NUMERICAL area=lOOpm^2 ic.file = "diode.IC"

## 30.2 BOUNDARY, INTERFACE

```
Specify properties of a domain boundary or the interface between two boundaries.

SYNOPSIS
```
   boundary domain [bounding -box] [properties]
   interface domain neighbor [bounding -box] [properties]

### 30.2.1 DESCRIPTION

```
The boundary and interface cards are used to set surface physics parameters along the boundary
of a specified domain. Normally, the parameters apply to the entire boundary, but there are two
ways to restrict the area of interest. If a neighboring domain is also specified, the parameters
are only set on the interface between the two domains. In addition, if a bounding box is given,
only that portion of the boundary or interface inside the bounding box will be set.

If a semiconductor-insulator interface is specified, then an estimate of the width of any inversion
or accumulation layer that may form at the interface can be provided. If the surface mobility
model (cf. models card) is enabled, then the model will apply to all semiconductor portions of
the device within this estimated distance of the interface. If a point lies within the estimated
layer width of more than one interface, it belong to the interface specified first in the input file.
If the layer width given is less than or equal to zero, it is automatically replaced by an estimate
calculated from the doping near the interface. As a consequence, if the doping varies so will the
layer width estimate.

Each edge of the bounding box can be specified in terms of its location or its mesh-index in the
relevant dimension, or defaulted to the respective boundary of the simulation mesh.


-----

### 30.2.2 PARAMETERS

Name Type Description Units

Domain Integer ID number of primary domain

Neighbor Integer ID number of neighboring domain

X.Low Real Lowest X location of bounding box _µm_

: IX.Low Integer Lowest X mesh-index of bounding box

X.High Real Highest X location of bounding box _µm_

: IX.High Integer Highest X mesh-index of bounding box

Y.Low Real Lowest Y location of bounding box _µm_

: IY.Low Integer Lowest Y mesh-index of bounding box

Y.High Real Highest Y location of bounding box _µm_

: IY.High Integer Highest Y mesh-index of bounding box

Qf Real Fixed interface charge _C/cm[2]_

SN Real Surface recombination velocity - electrons _cm/s_

SP Real Surface recombination velocity - holes _cm/s_

Layer.Width Real Width of surface layer _µm_

### 30.2.3 EXAMPLES

The following shows how the surface recombination velocities at an Si-SiO2 interface might be
set:
```
   interface dom=l neigh=2 sn=l.Oe4 sp=l.Oe4

```
In a MOSFET with a 2.0µm gate width and 0.1µm source and drain overlap, the surface channel
can be restricted to the region between the metallurgical junctions and within 100 A[˙] (0.01 µm)
of the interface:
```
   interface dom=l neigh=2 x.l=l.l x.h=2.9 layer.w=0.01

```
The inversion layer width in the previous example can be automatically determined by setting
the estimate to 0.0:
```
   interface dom=l neigh=% x.l=l.l x.h=2.9 layer.w=0.0

## 30.3 COMMENT

```
Add explanatory comments to a device definition.

SYNOPSIS
```
   comment [text]
  * [text]
  $ [text]
  # [text]

```
|Name|Type|Description|Units|
|---|---|---|---|
|Domain|Integer|ID number of primary domain||
|Neighbor|Integer|ID number of neighboring domain||
|X.Low : IX.Low X.High : IX.High Y.Low : IY.Low Y.High : IY.High|Real Integer Real Integer Real Integer Real Integer|Lowest X location of bounding box Lowest X mesh-index of bounding box Highest X location of bounding box Highest X mesh-index of bounding box Lowest Y location of bounding box Lowest Y mesh-index of bounding box Highest Y location of bounding box Highest Y mesh-index of bounding box|µm µm µm µm|
|Qf|Real|Fixed interface charge|C/cm2|
|SN|Real|Surface recombination velocity - electrons|cm/s|
|SP|Real|Surface recombination velocity - holes|cm/s|
|Layer.Width|Real|Width of surface layer|µm|


-----

### 30.3.1 DESCRIPTION

Annotations can be added to a device definition using the comment card. All text on a comment
card is ignored. Several popular commenting characters are also supported as aliases: ‘*’ from
SPICE, ‘$’ from PISCES, and ‘#’ from Linux shell scripts.

### 30.3.2 EXAMPLES

A SPICE-like comment is followed by a PISCES-like comment and shell script comment:
```
  * CIDER and SPICE would ignore this input line
  $ CIDER and PISCES would ignore this, but SPICE wouldn’t
  # CIDER and Linux Shell scripts would ignore this input line

## 30.4 CONTACT

```
Specify properties of an electrode

SYNOPSIS
```
   contact number [workfunction]

### 30.4.1 DESCRIPTION

```
The properties of an electrode can be set using the contact card. The only changeable property is
the work-function of the electrode material and this only affects contacts made to an insulating
material. All contacts to semiconductor material are assumed to be ohmic in nature.

### 30.4.2 PARAMETERS

Name Type Description

Number Integer ID number of the electrode

Work-function Real Work-function of electrode material. ( eV )

### 30.4.3 EXAMPLES

The following shows how the work-function of the gate contact of a MOSFET might be changed
to a value appropriate for a P+ polysilicon gate:
```
   contact num=2 workf=5.29

```
|Name|Type|Description|
|---|---|---|
|Number|Integer|ID number of the electrode|
|Work-function|Real|Work-function of electrode material. ( eV )|


-----

### 30.4.4 SEE ALSO

electrode, material

## 30.5 DOMAIN, REGION

Identify material-type for section of a device

SYNOPSIS
```
   domain number material [position]
   region number material [position]

### 30.5.1 DESCRIPTION

```
A device is divided into one or more rectilinear domains, each of which has a unique identification number and is composed of a particular material.

Domain (aka region) cards are used to build up domains by associating a material type with a
box-shaped section of the device. A single domain may be the union of multiple boxes. When
multiple domain cards overlap in space, the one occurring last in the input file will determine
the ID number and material type of the overlapped region.

Each edge of a domain box can be specified in terms of its location or mesh-index in the relevant
dimension, or defaulted to the respective boundary of the simulation mesh.

### 30.5.2 PARAMETERS

Name Type Description

Number Integer ID number of this domain

Material Integer ID number of material used by this domain

X.Low Real Lowest X location of domain box, ( µm )

: IX.Low Integer Lowest X mesh-index of domain box

X.High Real Highest X location of domain box, ( µm )

: IX-High Integer Highest X mesh-index of domain box

Y.Low Real Lowest Y location of domain box, ( µm )

: IY.Low Integer Lowest Y mesh-index of domain box

Y.High Real Highest Y location of domain box, ( µm )

: IY.High Integer Highest Y mesh-index of domain box

### 30.5.3 EXAMPLES

Create a 4.0 pm wide by 2.0 pm high domain out of material #1:
```
   domain num=l material=l x.l=O.O x.h=4.0 y.l=O.O y.h=2.0

```
|Name|Type|Description|
|---|---|---|
|Number|Integer|ID number of this domain|
|Material|Integer|ID number of material used by this domain|
|X.Low : IX.Low X.High : IX-High Y.Low : IY.Low Y.High : IY.High|Real Integer Real Integer Real Integer Real Integer|Lowest X location of domain box, ( µm ) Lowest X mesh-index of domain box Highest X location of domain box, ( µm ) Highest X mesh-index of domain box Lowest Y location of domain box, ( µm ) Lowest Y mesh-index of domain box Highest Y location of domain box, ( µm ) Highest Y mesh-index of domain box|


-----

The next example defines the two domains that would be typical of a planar MOSFET simulation. One occupies all of the mesh below y = 0 and the other occupies the mesh above y = 0.
Because the x values are left unspecified, the low and high x boundaries default to the edges of
the mesh:
```
   domain n=l m=l y.l=O.O
   domain n=2 m=2 y.h=O.O

### 30.5.4 SEE ALSO

```
x.mesh, material

## 30.6 DOPING

Add dopant to regions of a device

SYNOPSIS
```
   doping [domains] profile -type [lateral -profile -type] [axis]
     [impurity -type1 [constant -box] [profile -specifications]

### 30.6.1 DESCRIPTION

```
Doping cards are used to add impurities to the various domains of a device. Initially each
domain is dopant-free. Each new doping card creates a new doping profile that defines the
dopant concentration as a function of position. The doping at a particular location is then the
sum over all profiles of the concentration values at that position. Each profile can be restricted
to a subset of a device’s domains by supplying a list of the desired domains.

Otherwise, all domains are doped by each profile.

A profile has uniform concentration inside the constant box. Outside this region, it varies according to the primary an lateral profile shapes. In 1D devices the lateral shape is unused and in 2D
devices the y-axis is the default axis for the primary profile. Several analytic functions can be
used to define the primary profile shape. Alternatively, empirical or simulated profile data can
be extracted from a file. For the analytic profiles, the doping is the product of a profile function
(e.g. Gaussian) and a reference concentration, which is either the constant concentration of a
uniform profile, or the peak concentration for any of the other functions. If concentration data
is used instead take from an ASCII file containing a list of location-concentration pairs or a
SUPREM3 exported file, the name of the file must be provided. If necessary, the final concentration at a point is then found by multiplying the primary profile concentration by the value of
the lateral profile function at that point. Empirical profiles must first be normalized by the value
at 0.0 to provide a usable profile functions. Alternatively, the second dimension can be included
by assigning the same concentration to all points equidistant from the edges of the constant box.
The contours of the profile are the circular.


-----

![](NGS-ch30-cider-usermanual.pdf-7-0.png)

Figure 30.1: 1D doping profiles with location > 0.

Unless otherwise specified, the added impurities are assumes to be N type. However, the name
of a specific dopant species is needed when extracting concentration information for that impurity from a SUPREM3 exported file.

Several parameters are used to adjust the basic shape of a profile functions so that the final,
constructed profile, matches the doping profile in the real device. The constant box region
should coincide with a region of constant concentration in the device. For uniform profiles its
boundaries default to the mesh boundaries. For the other profiles the constant box starts as a
point and only acquires width or height if both the appropriate edges are specified. The location
of the peak of the primary profile can be moved away from the edge of the constant box. A
positive location places the peak outside the constant box (cf. Fig. 30.1), and a negative value
puts it inside the constant box (cf. Fig. 30.2). The concentration in the constant box is then
equal to the value of the profile when it intersects the edge of the constant box. The argument
of the profile function is a distance expressed in terms of the characteristic length (by default
equal to 1µm). The longer this length, the more gradually the profile will change. For example,
in Fig. 30.1 and Fig. 30.2, the profiles marked (a) have characteristic lengths twice those of the
profiles marked (b). The location and characteristic length for the lateral profile are multiplied
by the lateral ratio. This allows the use of different length scales for the primary and lateral
profiles. For rotated profiles, this scaling is taken into account, and the profile contours are
elliptical rather than circular.


-----

![](NGS-ch30-cider-usermanual.pdf-8-0.png)

Figure 30.2: 1D doping profiles with location < 0.


-----

### 30.6.2 PARAMETERS

Name Type Description

Domains Int List List of domains to dope

Uniform : Flag Primary profile type

Linear :

Erfc :

Exponential :

Suprem3 :

Ascii :

Ascii Suprem3

InFile String Name of Suprem3, Ascii or Ascii Suprem3 input file

Lat.Rotate : Flag Lateral profile type

Lat.Unif :

Lat.Lin :

Lat.Gauss :

Lat.Erfc :

Lat.Exp

X.Axis:Y.Axis Flag Primary profile direction

N.Type : P.Type : Flag Impurity type

Donor : Acceptor :

Phosphorus :

Arsenic :

Antimony :

Boron

X.Low Real Lowest X location of constant box, (µm)

X.High Real Highest X location of constant box, (µm)

Y.Low Real Lowest Y location of constant box, (µm)

Y.High Real Highest Y location of constant box, (µm)

Conic | Peak.conic Real Dopant concentration, (cm[−][3])

Location | Range Real Location of profile edge/peak, (µm)

Char.Length Real Characteristic length of profile, (µm)

Ratio.Lat Real Ratio of lateral to primary distances

### 30.6.3 EXAMPLES

This first example adds a uniform background P-type doping of 1.0 10[16]cm[−][3] to an entire
_×_
device:
```
   doping uniform p.type conc=l.0el6

```
A Gaussian implantation with rotated lateral falloff, such as might be used for a MOSFET
source, is then added:
```
   doping gauss lat.rotate n.type conc=l.0el9
  + x.l=0.0 x.h=0.5 y.l=0.0 y.h=0.2 ratio=0.7

```
|Name|Type|Description|
|---|---|---|
|Domains|Int List|List of domains to dope|
|Uniform : Linear : Erfc : Exponential : Suprem3 : Ascii : Ascii Suprem3 InFile|Flag String|Primary profile type Name of Suprem3, Ascii or Ascii Suprem3 input file|
|Lat.Rotate : Lat.Unif : Lat.Lin : Lat.Gauss : Lat.Erfc : Lat.Exp|Flag|Lateral profile type|
|X.Axis:Y.Axis|Flag|Primary profile direction|
|N.Type : P.Type : Donor : Acceptor : Phosphorus : Arsenic : Antimony : Boron|Flag|Impurity type|
|X.Low X.High Y.Low Y.High|Real Real Real Real|Lowest X location of constant box, (µm) Highest X location of constant box, (µm) Lowest Y location of constant box, (µm) Highest Y location of constant box, (µm)|
|Conic | Peak.conic Location | Range Char.Length Ratio.Lat|Real Real Real Real|Dopant concentration, (cm−3) Location of profile edge/peak, (µm) Characteristic length of profile, (µm) Ratio of lateral to primary distances|


-----

Alternatively, an error-function falloff could be used:
```
   doping gauss lat.erfc conc=l.0el9
  + x.l=0.0 x.h=0.5 y.l=0.0 y.h=0.2 ratio=0.7

```
Finally, the MOSFET channel implant is extracted from an ASCII-format SUPREM3 file. The
lateral profile is uniform, so that the implant is confined between X = 1µm and X = 3µm. The
profile begins at Y = 0µm (the high Y value defaults equal to the low Y value):
```
   doping ascii suprem3 infile=implant.s3 lat.unif boron
  + x.l=1.0 x.h=3.0 y.l=0.0

### 30.6.4 SEE ALSO

```
domain, mobility, contact, boundary

## 30.7 ELECTRODE

Set location of a contact to the device

SYNOPSIS
```
   electrode [number] [position]

### 30.7.1 DESCRIPTION

```
Each device has several electrodes that are used to connect the device to the rest of the circuit.
The number of electrodes depends on the type of device. For example, a MOSFET needs 4
electrodes. A particular electrode can be identified by its position in the list of circuit nodes
on the device element line. For example, the drain node of a MOSFET is electrode number 1,
while the bulk node is electrode number 4. Electrodes for which an ID number has not been
specified are assigned values sequentially in the order they appear in the input file.

For lD devices, the positions of two of the electrodes are predefined to be at the ends of the
simulation mesh. The first electrode is at the low end of the mesh, and the last electrode is at
the high end. The position of the special lD BJT base contact is set on the options card. Thus,
electrode cards are used exclusively for 2D devices.

Each card associates a portion of the simulation mesh with a particular electrode. In contrast to
domains, which are specified only in terms of boxes, electrodes can also be specified in terms of
line segments. Boxes and segments for the same electrode do not have to overlap. If they don’t,
it is assumed that the electrode is wired together outside the area covered by the simulation
mesh. However, pieces of different electrodes must not overlap, since this would represent
a short circuit. Each electrode box or segment can be specified in terms of the locations or
mesh-indices of its boundaries. A missing value defaults to the corresponding mesh boundary.


-----

### 30.7.2 PARAMETERS

Name Type Description

Number Integer ID number of this domain

X.Low Real Lowest X location of electrode, (µm)

: IX.Low Integer Lowest X mesh-index of electrode

X.High Real Highest X location of electrode, (µm)

: IX.High Integer Highest X mesh-index of electrode

Y.Low Real Lowest Y location of electrode, (µm)

: IY.Low Integer Lowest Y mesh-index of electrode

Y.High Real Highest Y location of electrode, (µm)

: IY.High Integer Highest Y mesh-index of electrode

### 30.7.3 EXAMPLES

The following shows how the four contacts of a MOSFET might be specified:
```
  * DRAIN
   electrode x.l=0.0 x.h=0.5 y.l=0.0 y.h=0.0
  * GATE
   electrode x.l=1.0 x.h=3.0 iy.l=0 iy.h=0
  * SOURCE
   electrode x.l=3.0 x.h=4.0 y.l=0.0 y.h=0.0
  * BULK
   electrode x.l=0.0 x.h=4.0 y.l=2.0 y.h=2.0

```
The numbering option can be used when specifying bipolar transistors with dual base contacts:
```
  * EMITTER
   electrode num=3 x.l=1.0 x.h=2.0 y.l=0.0 y.h=0.0
  * BASE
   electrode num=2 x.l=0.0 x.h=0.5 y.l=0.0 y.h=0.0
   electrode num=2 x.l=2.5 x.h=3.0 y.l=0.0 y.h=0.0
  * COLLECTOR
   electrode num=1 x.l=0.0 x.h=3.0 y.l=1.0 y.h=1.0

### 30.7.4 SEE ALSO

```
domain, contact

## 30.8 END

Terminate processing of a device definition

|Name|Type|Description|
|---|---|---|
|Number|Integer|ID number of this domain|
|X.Low|Real|Lowest X location of electrode, (µm)|
|: IX.Low|Integer|Lowest X mesh-index of electrode|
|X.High|Real|Highest X location of electrode, (µm)|
|: IX.High|Integer|Highest X mesh-index of electrode|
|Y.Low|Real|Lowest Y location of electrode, (µm)|
|: IY.Low|Integer|Lowest Y mesh-index of electrode|
|Y.High|Real|Highest Y location of electrode, (µm)|
|: IY.High|Integer|Highest Y mesh-index of electrode|


-----

SYNOPSIS
```
   end

### 30.8.1 DESCRIPTION

```
The end card stops processing of a device definition. It may appear anywhere within a definition.
Subsequent continuation lines of the definition will be ignored. If no end card is supplied, all
the cards will be processed.

## 30.9 MATERIAL

Specify physical properties of a material

SYNOPSIS
```
   material number type [physical -constants]

### 30.9.1 DESCRIPTION

```
The material card is used to create an entry in the list of materials used in a device. Each entry
needs a unique identification number and the type of the material. Default values are assigned
to the physical properties of the material. Most material parameters are accessible either here
or on the mobility or contact cards. However, some parameters remain inaccessible (e.g.
the ionization coefficient parameters). Parameters for most physical effect models are collected
here. Mobility parameters are handled separately by the mobility card. Properties of electrode
materials are set using the contact card.


-----

### 30.9.2 PARAMETERS

Name

Number

Semiconductor : Silicon

: Polysilicon : GaAs

: Insulator : Oxide

: Nitride

Affinity

Permittivity

Nc

Nv

Eg

dEg.dT

Eg.Tref

dEg.dN

Eg.Nref

dEg.dP

Eg.Pref

TN

SRH.Nref

TP

SRH.Pref

CN

CP

ARichN

ARichP

### 30.9.3 EXAMPLES


_◦[cm]K[2]2_ [)]

|Name|Type|Description|
|---|---|---|
|Number|Integer|ID number of this material|
|Semiconductor : Silicon : Polysilicon : GaAs : Insulator : Oxide : Nitride|Flag|Type of this material|
|Affinity|Real|Electron affinity (eV)|
|Permittivity|Real|Dielectric permittivity (F/cm)|
|Nc|Real|Conduction band density (cm−3)|
|Nv|Real|Valence band density (cm−3)|
|Eg|Real|Energy band gap (eV)|
|dEg.dT|Real|Bandgap narrowing with temperature (eV/◦K)|
|Eg.Tref|Real|Bandgap reference temperature, ( °K )|
|dEg.dN|Real|Bandgap narrowing with N doping, (eV/cm−3)|
|Eg.Nref|Real|Bandgap reference concentration - N type, (cm−3)|
|dEg.dP|Real|Bandgap narrowing with P doping, (eV/cm−3)|
|Eg.Pref|Real|Bandgap reference concentration - P type, (cm−3)|
|TN|Real|SRH lifetime - electrons, (sec)|
|SRH.Nref|Real|SRH reference concentration - electrons (cm−3)|
|TP|Real|SRH lifetime - holes, (sec)|
|SRH.Pref|Real|SRH reference concentration - holes (cm−3)|
|CN|Real|Auger coefficient - electrons (cm6/sec)|
|CP|Real|Auger coefficient - holes (cm6/sec)|
|ARichN|Real|Richardson constant - electrons, ( A/cm2) ◦K2|
|ARichP|Real|Richardson constant - holes, ( A/cm2) ◦K2|


Set the type of material #1 to silicon, then adjust the values of the temperature-dependent bandgap model parameters:
```
   material num=1 silicon eg=1.12 deg.dt=4.7e-4 eg.tref=640.0

```
The recombination lifetimes can be set to extremely short values to simulate imperfect semiconductor material:
```
   material num=2 silicon tn=1ps tp=1ps

### 30.9.4 SEE ALSO

```
domain, mobility, contact, boundary


-----

## 30.10 METHOD

Choose types and parameters of numerical methods

SYNOPSIS
```
   method [types] [parameters]

### 30.10.1 DESCRIPTION

```
The method card controls which numerical methods are used during a simulation and the parameters of these methods. Most of these methods are optimizations that reduce run time, but
may sacrifice accuracy or reliable convergence.

For majority-carrier devices such as MOSFETs, one carrier simulations can be used to save
simulation time. The systems of equations in AC analysis may be solved using either direct or
successive-over-relaxation techniques. Successive-over-relaxation is faster, but at high frequencies, it may fail to converge or may converge to the wrong answer. In some cases, it is desirable
to obtain AC parameters as functions of DC bias conditions. If necessary, a one-point AC analysis is performed at a predefined frequency in order to obtain these small-signal parameters. The
default for this frequency is 1 Hz. The Jacobian matrix for DC and transient analyses can be
simplified by ignoring the derivatives of the mobility with respect to the solution variables. However, the resulting analysis may have convergence problems. Additionally, if they are ignored
during AC analyses, incorrect results may be obtained.

A damped Newton method is used as the primary solution technique for the device-level partial
differential equations. This algorithm is based on an iterative loop that terminates when the error
in the solution is small enough or the iteration limit is reached. Error tolerances are used when
determining if the error is ‘small enough’. The tolerances are expressed in terms of an absolute,
solution-independent error and a relative, solution-dependent error. The absolute-error limit can
be set on this card. The relative error is computed by multiplying the size of the solution by the
circuit level SPICE parameter RELTOL.

### 30.10.2 Parameters

Name Type Description

OneCarrier Flag Solve for majority carriers only

AC analysis String AC analysis method, ( either DIRECT or SOR)

NoMobDeriv Flag Ignore mobility derivatives

Frequency Real AC analysis frequency, ( Hz )

ItLim Integer Newton iteration limit

DevTol Real Maximum residual error in device equations

### 30.10.3 Examples

Use one carrier simulation for a MOSFET, and choose direct method AC analysis to ensure
accurate, high frequency results:

|Name|Type|Description|
|---|---|---|
|OneCarrier|Flag|Solve for majority carriers only|
|AC analysis|String|AC analysis method, ( either DIRECT or SOR)|
|NoMobDeriv|Flag|Ignore mobility derivatives|
|Frequency|Real|AC analysis frequency, ( Hz )|
|ItLim|Integer|Newton iteration limit|
|DevTol|Real|Maximum residual error in device equations|


-----

```
   method onec ac.an=direct

```
Tolerate no more than 10[−][10] as the absolute error in device-level equations, and perform no
more than 15 Newton iterations in any one loop:
```
   method devtol=1e-10 itlim=15

## 30.11 Mobility

```
Specify types and parameters of mobility models

SYNOPSIS
```
   mobility material [carrier] [parameters] [models] [initialize]

### 30.11.1 Description

```
The mobility model is one of the most complicated models of a material’s physical properties.
As a result, separate cards are needed to set up this model for a given material.

Mobile carriers in a device are divided into a number of different classes, each of which has
different mobility modeling. There are three levels of division. First, electrons and holes are
obviously handled separately. Second, carriers in surface inversion or accumulation layers are
treated differently than carriers in the bulk. Finally, bulk carriers can be either majority or
minority carriers.

For surface carriers, the normal-field mobility degradation model has three user-modifiable parameters. For bulk carriers, the ionized impurity scattering model has four controllable parameters. Different sets of parameters are maintained for each of the four bulk carrier types:
majority-electron, minority-electron, majority-hole and minority-hole. Velocity saturation modeling can be applied to both surface and bulk carriers. However, only two sets of parameters
are maintained: one for electrons and one for holes. These must be changed on a majority
carrier card (i.e. when the majority flag is set).

Several models for the physical effects are available, along with appropriate default values.
Initially, a universal set of default parameters usable with all models is provided. These can be
overridden by defaults specific to a particular model by setting the initialization flag. These can
then be changed directly on the card itself. The bulk ionized impurity models are the CaugheyThomas (CT) model and the Scharfetter-Gummel (SG) model [CAUG671, [SCHA69]. Three
alternative sets of defaults are available for the Caughey-Thomas expression. They are the Arora
(AR) parameters for Si [AROR82], the University of Florida (UF) parameters for minority
carriers in Si [SOLL90], and a set of parameters appropriate for GaAs (GA). The velocitysaturation models are the Caughey-Thomas (CT) and Scharfetter-Gummel (SG) models for Si,
and the PISCES model for GaAs (GA). There is also a set of Arora (AR) parameters for the
Caughey-Thomas model.


-----

### 30.11.2 Parameters

Name Type Description

Material Integer ID number of material

Electron : Hole Flag Mobile carrier

Majority : Minority Flag Mobile carrier type

MUS Real Maximum surface mobility, ( cm2/Vs )

EC.A Real Surface mobility 1st-order critical field, ( V/cm )

EC.B Real Real Surface mobility 2nd-order critical field, ( V2/cm2 )

MuMax Real Maximum bulk mobility, ( cm2/Vs )

MuMin Real Minimum bulk mobility, ( cm2/Vs)

NtRef Real Ionized impurity reference concentration, ( cm-3 )

NtExp Real Ionized impurity exponent

Vsat Real Saturation velocity, ( cm/s )

Vwarm Real Warm carrier reference velocity, ( cm/s )

ConcModel String Ionized impurity model, ( CT, AR, UF, SG, Dr GA )

FieldModel String Velocity saturation model, ( CT, AR, SG, or GA )

Init Flag Copy model-specific defaults

### 30.11.3 Examples

The following set of cards completely updates the bulk mobility parameters for material #1:
```
   mobility mat=l concmod=sg fieldmod=sg
   mobility mat=l elec major mumax=1000.0 mumin=l00.0
  + ntref=l.0el6 ntexp=0.8 vsat=l.0e7 vwarm=3.0e6
   mobility mat=l elec minor mumax=1000.0 mumin=200.O
  + ntref=l.0el7 ntexp=0.9
   mobility mat=l hole major mumax=500.0 mumin=50.0
  + ntref=l.0el6 ntexp=0.7 vsat=8.0e6 vwarm=l.0e6
   mobility mat=l hole minor mumax=500.0 mumin=150.0
  + ntref=l.0el7 ntexp=0.8

```
The electron surface mobility is changed by the following:
```
   mobility mat=l elec mus=800.0 ec.a=3.0e5 ec.b=9.0e5

```
Finally, the default Scharfetter-Gummel parameters can be used in Si with the GaAs velocitysaturation model (even though it doesn’t make physical sense!):
```
   mobility mat=l init elec major fieldmodel=sg
   mobility mat=l init hole major fieldmodel=sg
   mobility mat=l fieldmodel=ga

### 30.11.4 SEE ALSO

```
material

|Name|Type|Description|
|---|---|---|
|Material|Integer|ID number of material|
|Electron : Hole Majority : Minority|Flag Flag|Mobile carrier Mobile carrier type|
|MUS EC.A EC.B|Real Real Real|Maximum surface mobility, ( cm2/Vs ) Surface mobility 1st-order critical field, ( V/cm ) Real Surface mobility 2nd-order critical field, ( V2/cm2 )|
|MuMax MuMin NtRef NtExp|Real Real Real Real|Maximum bulk mobility, ( cm2/Vs ) Minimum bulk mobility, ( cm2/Vs) Ionized impurity reference concentration, ( cm-3 ) Ionized impurity exponent|
|Vsat Vwarm|Real Real|Saturation velocity, ( cm/s ) Warm carrier reference velocity, ( cm/s )|
|ConcModel FieldModel Init|String String Flag|Ionized impurity model, ( CT, AR, UF, SG, Dr GA ) Velocity saturation model, ( CT, AR, SG, or GA ) Copy model-specific defaults|


-----

### 30.11.5 BUGS

The surface mobility model does not include temperature-dependence for the transverse-field
parameters. Those parameters will need to be adjusted by hand.

## 30.12 MODELS

Specify which physical models should be simulated

SYNOPSIS
```
   models [model flags]

### 30.12.1 DESCRIPTION

```
The models card indicates which physical effects should be modeled during a simulation. Initially, none of the effects are included. A flag can be set false by preceding by a caret.

### 30.12.2 Parameters

Name Type Description

BGN Flag Bandgap narrowing

SRH Flag Shockley-Reed-Hall recombination

ConcTau Flag Concentration-dependent SRH lifetimes

Auger Flag Auger recombination

Avalanche Flag Local avalanche generation

TempMob Flag Temperature-dependent mobility

ConcMob Flag Concentration-dependent mobility

FieldMob Flag Lateral-field-dependent mobility

TransMob Flag Transverse-field-dependent surface mobility

SurfMob Flag Activate surface mobility model

### 30.12.3 Examples

Turn on bandgap narrowing, and all of the generation-recombination effects:
```
   models bgn srh conctau auger aval

```
Amend the first card by turning on lateral- and transverse-field-dependent mobility in surface
charge layers, and lateral-field-dependent mobility in the bulk. Also, this line turns avalanche
generation modeling off.
```
   models surfmob transmob fieldmob ^aval

```
|Name|Type|Description|
|---|---|---|
|BGN SRH ConcTau Auger Avalanche TempMob ConcMob FieldMob TransMob SurfMob|Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag|Bandgap narrowing Shockley-Reed-Hall recombination Concentration-dependent SRH lifetimes Auger recombination Local avalanche generation Temperature-dependent mobility Concentration-dependent mobility Lateral-field-dependent mobility Transverse-field-dependent surface mobility Activate surface mobility model|


-----

### 30.12.4 See also

material, mobility

### 30.12.5 Bugs

The local avalanche generation model for 2D devices does not compute the necessary contributions to the device-level Jacobian matrix. If this model is used, it may cause convergence
difficulties and it will cause AC analyses to produce incorrect results.

## 30.13 OPTIONS

Provide optional device-specific information

SYNOPSIS
```
   options [device -type] [initial -state] [dimensions]
     [measurement -temperature]

### 30.13.1 DESCRIPTION

```
The options card functions as a catch-all for various information related to the circuit-device
interface. The type of a device can be specified here, but will be defaulted if none is given.
Device type is used primarily to determine how to limit the changes in voltage between the
terminals of a device. It also helps determine what kind of boundary conditions are used as
defaults for the device electrodes.

A previously calculated state, stored in the named initial-conditions file, can be loaded at the
beginning of an analysis. If it is necessary for each instance of a numerical model to start in a
different state, then the unique flag can be used to generate unique filenames for each instance
by appending the instance name to the given filename. This is the same method used by CIDER
to generate unique filenames when the states are originally saved. If a particular state file does
not fit. this pattern, the filename can be entered directly on the instance line.

Mask dimension defaults can be set so that device sizes can be specified in terms of area or
width. Dimensions for the special lD BJT base contact can also be controlled. The measurement
temperature of material parameters, normally taken to be the circuit default, can be overridden.


-----

### 30.13.2 Parameters

Name Type Description

Resistor Flag Resistor

: Capacitor Flag Capacitor

: Diode Flag Diode

: Bipolar|BJT Flag Bipolar transistor

: MOSFET Flag MOS field-effect transistor

: JFET Flag Junction field-effect transistor

: MESFET Flag MES field-effect transistor

IC.File String Initial-conditions filename

Unique Flag Append instance name to filename

DefA Real Default Mask Area, (m²)

DefW Real Default Mask Width, (m)

DefL Real Default Mask Length, (m)

Base.Area Real lD BJT base area relative to emitter area

Base.Length Real Real lD BJT base contact length, (µm)

Base.Depth Real lD BJT base contact depth, (µm)

TNom Real Nominal measurement temperature, (°C)

### 30.13.3 Examples

Normally, a ’numos’ device model is used for MOSFET devices. However, it can be changed
into a bipolar-with-substrate-contact model, by specifying a bipolar structure using the other
cards, and indicating the device-structure type as shown here. The default length is set to 1.0
µm so that when mask area is specified on the element line it can be divided by this default to
obtain the device width.
```
   options bipolar defl=1.0

```
Specify that a 1D BJT has base area 1/10th that of the emitter, has an effective depth of 0.2 µm
and a length between the internal and external base contacts
```
   options base.area=0.1 base.depth=0.2 base.len=1.5

```
If a circuit contains two instances of a bipolar transistor model named ’q1’ and ’q2’, the following line tells the simulator to look for initial conditions in the ’OP1.q2’, respectively. The
period in the middle of the names is added automatically:
```
   options unique ic.file="OP1"

### 30.13.4 See also

```
numd, nbjt, numos

|Name|Type|Description|
|---|---|---|
|Resistor : Capacitor : Diode : Bipolar|BJT : MOSFET : JFET : MESFET|Flag Flag Flag Flag Flag Flag Flag|Resistor Capacitor Diode Bipolar transistor MOS field-effect transistor Junction field-effect transistor MES field-effect transistor|
|IC.File Unique|String Flag|Initial-conditions filename Append instance name to filename|
|DefA DefW DefL Base.Area Base.Length Base.Depth|Real Real Real Real Real Real|Default Mask Area, (m²) Default Mask Width, (m) Default Mask Length, (m) lD BJT base area relative to emitter area Real lD BJT base contact length, (µm) lD BJT base contact depth, (µm)|
|TNom|Real|Nominal measurement temperature, (°C)|


-----

## 30.14 OUTPUT

Identify information to be printed or saved

SYNOPSIS
```
   output [debugging -flags] [general -info] [saved-solutions]

### 30.14.1 DESCRIPTION

```
The output card is used to control the amount of information that is either presented to or saved
for the user. Three types of information are available. Debugging information is available as
a means to monitor program execution. This is useful during long simulations when one is
unsure about whether the program has become trapped at some stage of the simulation. General
information about a device such as material parameters and resource usage can be obtained.
Finally, information about the internal and external states of a device is available. Since this
data is best interpreted using a post-processor, a facility is available for saving device solutions
in auxiliary output files. Solution filenames are automatically generated by the simulator. If the
named file already exists, the file will be overwritten. A filename unique to a particular circuit
or run can be generated by providing a root filename. This root name will be added onto the
beginning of the automatically generated name. This feature can be used to store solutions in
a directory other than the current one by specifying the root filename as the path of the desired
directory. Solutions are only saved for those devices that specify the ‘save’ parameter on their
instance lines.

The various physical values that can be saved are named below. By default, the following values
are saved: the doping, the electron and hole concentrations, the potential, the electric field, the
electron and hole current densities, and the displacement current density. Values can be added
to or deleted from this list by turning the appropriate flag on or off. For vector-valued quantities
in two dimensions, both the X and Y components are saved. The vector magnitude can be
obtained during post-processing.

Saved solutions can be used in conjunction with the options card and instance lines to reuse
previously calculated solutions as initial guesses for new solutions.For example, it is typical to
initialize the device to a known state prior to beginning any DC transfer curve or operating point
analysis. This state is an ideal candidate to be saved for later use when it is known that many
analyses will be performed on a particular device structure.


-----

### 30.14.2 Parameters

Name Type Description

All.Debug Flag Debug all analyses

OP.Debug Flag .OP analyses

DC.Debug Flag .DC analyses

TRAN.Debug Flag .TRAN analyses

AC.Debug Flag .AC analyses

PZ.Debug Flag .PZ analyses

Material Flag Physical material information

Statistics | Resources Flag Resource usage information

RootFile String Root of output file names

Psi Flag Potential ( V )

Equ.Psi Flag Equilibrium potential ( V )

Vac.Psi Flag Vacuum potential ( V )

Doping Flag Net doping ( cm³ )

N.Conc Flag Electron concentration ( cm³ )

P.Conc Flag Hole concentration ( cm³ )

PhiN Flag Electron quasi-fermi potential ( V )

PhiP Flag Hole quasi-fermi potential ( V )

PhiC Flag Conduction band potential ( V )

PhiV Flag Valence band potential ( V )

E.Field Flag Electric field ( V/cm )

JC Flag Conduction current density ( A/cm² )

JD Flag Displacement current density ( A/cm² )

JN Flag Electron current density ( A/cm² )

JP Flag Hole current density ( A/cm² )

JT Flag Total current density ( A/cm² )

Unet Flag Net recombination ( 1/cm³ s )

MuN Flag Electron mobility (low-field) ( cm²/Vs )

MuP Flag Hole mobility (low-field) ( cm²/Vs )

### 30.14.3 Examples

The following example activates all potentially valuable diagnostic output:
```
   output all.debug mater stat

```
Energy band diagrams generally contain the potential, the quasi-fermi levels, the energies and
the vacuum energy. The following example enables saving of the r values needed to make
energy band diagrams:
```
   output phin phjp phic phiv vac.psi

```
Sometimes it is desirable to save certain key solutions, and then reload them for use in subsequent simulations. In such cases only the essential values ( Ψ, n, and p ) need to be saved. This
example turns off the nonessential default values (and indicates the essential ones explicitly):

|Name|Type|Description|
|---|---|---|
|All.Debug OP.Debug DC.Debug TRAN.Debug AC.Debug PZ.Debug|Flag Flag Flag Flag Flag Flag|Debug all analyses .OP analyses .DC analyses .TRAN analyses .AC analyses .PZ analyses|
|Material Statistics | Resources|Flag Flag|Physical material information Resource usage information|
|RootFile Psi Equ.Psi Vac.Psi Doping N.Conc P.Conc PhiN PhiP PhiC PhiV E.Field JC JD JN JP JT Unet MuN MuP|String Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag Flag|Root of output file names Potential ( V ) Equilibrium potential ( V ) Vacuum potential ( V ) Net doping ( cm³ ) Electron concentration ( cm³ ) Hole concentration ( cm³ ) Electron quasi-fermi potential ( V ) Hole quasi-fermi potential ( V ) Conduction band potential ( V ) Valence band potential ( V ) Electric field ( V/cm ) Conduction current density ( A/cm² ) Displacement current density ( A/cm² ) Electron current density ( A/cm² ) Hole current density ( A/cm² ) Total current density ( A/cm² ) Net recombination ( 1/cm³ s ) Electron mobility (low-field) ( cm²/Vs ) Hole mobility (low-field) ( cm²/Vs )|


-----

```
   output psi n.conc p.conc ^e.f ^jn ^jp ^jd

### 30.14.4 SEE ALSO

```
options, numd, nbjt, numos

## 30.15 TITLE

Provide a label for this device’s output

SYNOPSIS
```
   title [text]

### 30.15.1 DESCRIPTION

```
The title card provides a label for use as a heading in various output files. The text can be any
length, but titles that fit on a single line will produce more aesthetically pleasing output.

### 30.15.2 EXAMPLES

Set the title for a minimum gate length NMOSFET in a 1.0µm BiCMOS process
```
   title L=1.0um NMOS Device, 1.0um BiCMOS Process

### 30.15.3 BUGS

```
The title is currently treated like a comment.

## 30.16 X.MESH, Y.MESH

Define locations of lines and nodes in a mesh

SYNOPSIS
```
  x.mesh position numbering -method [spacing -parameters]
  y.mesh position numbering -method [spacing -parameters]

```

-----

### 30.16.1 DESCRIPTION

The domains of a device are discretized onto a rectangular finite-difference mesh using x.mesh
cards for 1D devices, or x.mesh and y.mesh cards for 2D devices. Both uniform and nonuniform meshes can be specified.

A typical mesh for a 2D device is shown in Fig. 30.3.

Figure 30.3: Typical mesh for 2D devices

The mesh is divided into intervals by the reference lines. The other lines in each interval are
automatically generated by CIDER using the mesh spacing parameters. In general, each new
mesh card adds one reference line and multiple automatic lines to the mesh. Conceptually, a 1D
mesh is similar to a 2D mesh except that there are no reference or automatic lines needed in the
second dimension.

The location of a reference line in the mesh must either be given explicitly (using Location) or
defined implicitly relative to the location of the previous reference line (by using Width). (If the
first card in either direction is specified using Width, an initial reference line is automatically
generated at location 0.0.) The line number of the reference line can be given explicitly, in
which case the automatic lines are evenly spaced within the interval, and the number of lines
is determined from the difference between the current line number and that of the previous
reference line. However, if the interval width is given, then the line number is interpreted
directly as the number of additional lines to add to the mesh.

For a nonuniformly spaced interval, the number of automatic lines has to be determined using
the mesh spacing parameters. Nonuniform spacing is triggered by providing a desired ratio for
the lengths of the spaces between adjacent pairs of lines. This ratio should always be greater
than one, indicating the ratio of larger spaces to smaller spaces. In addition to the ratio, one
or both of the space widths at the ends of the interval must be provided. If only one is given,


![](NGS-ch30-cider-usermanual.pdf-23-0.png)

-----

it will be the smallest space and the largest space will be at the opposite end of the interval.
If both are given, the largest space will be in the middle of the interval. In certain cases it is
desirable to limit the growth of space widths in order to control the solution accuracy. This can
be accomplished by specifying a maximum space size, but this option is only available when
one of the two end lengths is given. Note that once the number of new lines is determined
using the desired ratio, the actual spacing ratio may be adjusted so that the spaces exactly fill
the interval.

### 30.16.2 Parameters

Name Type Description

Location Real Location of this mesh line, ( µm )

:Width Real Width between this and previous mesh lines, ( µm )

Number | Node Integer Number of this mesh line

:Ratio Real Ratio of sizes of adjacent spaces

H.Start | H1 Real Space size at start of interval, ( µm )

H.End | H2 Real Space size at end of interval, ( µm )

H.Max | H3 Real Maximum space size inside interval, ( µm )

### 30.16.3 EXAMPLES

A 50 node, uniform mesh for a 5 µm long semiconductor resistor can be specified as:
```
  x.mesh loc=0.0 n=1
  x.mesh loc=5.0 n=50

```
An accurate mesh for a 1D diode needs fine spacing near the junction. In this example, the
junction is assumed to be 0.75 µm deep. The spacing near the diode ends is limited to a maximum of 0.1 µm:
```
  x.mesh w=0.75 h.e=0.001 h.m=0.l ratio=1.5
  x.mesh w=2.25 h.s=0.001 h.m=0.l ratio=1.5

```
The vertical mesh spacing of a MOSFET can generally be specified as uniform through the gate
oxide, very fine for the surface inversion layer, moderate down to the so source/drain junction
depth, and then increasing all the way to the bulk contact:
```
  y.mesh loc=-0.04 node=1
  y.mesh loc=0.0 node=6
  y.mesh width=0.5 h.start=0.001 h.max=.05 ratio=2.0
  y.mesh width=2.5 h.start=0.05 ratio=2.0

### 30.16.4 SEE ALSO

```
domain

|Name|Type|Description|
|---|---|---|
|Location :Width|Real Real|Location of this mesh line, ( µm ) Width between this and previous mesh lines, ( µm )|
|Number | Node :Ratio|Integer Real|Number of this mesh line Ratio of sizes of adjacent spaces|
|H.Start | H1 H.End | H2 H.Max | H3|Real Real Real|Space size at start of interval, ( µm ) Space size at end of interval, ( µm ) Maximum space size inside interval, ( µm )|


-----

## 30.17 NUMD

Diode / two-terminal numerical models and elements

SYNOPSIS Model:
```
  .MODEL model-name NUMD [level]
  + ...

```
SYNOPSIS Element:
```
   DXXXXXXX nl n2 model-name [geometry] [temperature] [initial -condition

```
SYNOPSIS Output:
```
  .SAVE [small-signal values]

### 30.17.1 DESCRIPTION

```
NUMD is the name for a diode numerical model. In addition, this same model can be used
to simulate other two-terminal structures such as semiconductor resistors and MOS capacitors.
See the options card for more information on how to customize the device type.

Both 1D and 2D devices are supported. These correspond to the LEVEL=l and LEVEL=2
models, respectively. If left unspecified, it is assumed that the device is one-dimensional.

All numerical two-terminal element names begin with the letter ‘D. The element name is then
followed by the names of the positive (n1) and negative (n2) nodes. After this must come the
name of the model used for the element. The remaining information can come in any order. The
layout dimensions of an element are specified relative to the geometry of a default device. For
1D devices, the default device has an area of 1m², and for 2D devices, the default device has
a width of 1 m. However, these defaults can be overridden on an options card. The operating
temperature of a device can be set independently from that of the rest of the circuit in order to
simulate non-isothermal circuit operation. Finally, the name of a file containing an initial state
for the device can be specified. Remember that if the filename contains capital letters, they
must be protected by surrounding the filename with double quotes. Alternatively, the device
can be placed in an OFF state (thermal equilibrium) at the beginning of the analysis. For more
information on the use of initial conditions, see the NGSPICE User’s Manual, Chapt. 7.1.

In addition to the element input parameters, there are output-only parameters that can be shown
using the NGSPICE show command (17.5.67) or captured using the save/.SAVE (17.5.58/15.6.1)
command. These parameters are the elements of the indefinite conductance (G), capacitance
(C), and admittance (Y) matrices where Y = G + jωC. By default, the parameters are computed at 1 Hz. Each element is accessed using the name of the matrix (g, c or y) followed by the
node indices of the output terminal and the input terminal (e.g. g11). Beware that names are
case-sensitive for save/show, so lower-case letters must be used.


-----

### 30.17.2 Parameters

Name Type Description

Level Integer Dimensionality of numerical model

Area Real Multiplicative area factor

W Real Multiplicative width factor

Temp Real Element operating temperature

IC.File String Initial-conditions filename

Off Flag Device initially in OFF state

gIJ Flag Conductance element Gi j, ( Ω )

cIJ Flag Capacitance element Ci j, ( F )

yIJ Flag Admittance element Yi j, ( Ω )

### 30.17.3 EXAMPLES

A one-dimensional numerical switching-diode element/model pair with an area twice that of
the default device (which has a size of l µm x 1 µm) can be specified using:
```
   DSWITCH 1 2 M_SWITCH_DIODE AREA=2
  .MODEL M_SWITCH_DIODE NUMD
  + options defa=1p ...
  + ...

```
A two-dimensional two-terminal MOS capacitor with a width of 20 µm and an initial condition
of 3 V is created by:
```
   DMOSCAP 11 12 M_MOSCAP W=20um IC=3v
  .MODEL M_MOSCAP NUMD LEVEL=2
  + options moscap defw=1m
  + ...

```
The next example shows how both the width and area factors can be used to create a power
diode with area twice that of a 6µm-wide device (i.e. a 12µm-wide device). The device is
assumed to be operating at a temperature of 100°C:
```
  D1 POSN NEGN POWERMOD AREA=2 W=6um TEMP=100.0
  .MODEL POWERMOD NUMD LEVEL=2
  + ...

```
This example saves all the small-signal parameters of the previous diode:
```
  .SAVE @d1[g11] @d1[g12] @d1[g21] @d1[g22]
  .SAVE @d1[c11] @d1[c12] @d1[c21] @d1[c22]
  .SAVE @d1[y11] @d1[y12] @d1[y21] @d1[y22]

```
|Name|Type|Description|
|---|---|---|
|Level|Integer|Dimensionality of numerical model|
|Area W|Real Real|Multiplicative area factor Multiplicative width factor|
|Temp|Real|Element operating temperature|
|IC.File Off|String Flag|Initial-conditions filename Device initially in OFF state|
|gIJ cIJ yIJ|Flag Flag Flag|Conductance element G , ( Ω) i j Capacitance element C , ( F ) i j Admittance element Y , ( Ω) i j|


-----

### 30.17.4 SEE ALSO

options, output

### 30.17.5 BUGS

Convergence problems may be experienced when simulating MOS capacitors due to singularities in the current-continuity equations.

## 30.18 NBJT

Bipolar / three-terminal numerical models and elements

SYNOPSIS Model:
```
  .MODEL model-name NBJT [level]
  + ...

```
SYNOPSIS Element:
```
   QXXXXXXX nl n2 n3 model-name [geometry]
  + [temperature] [initial -conditions]

```
SYNOPSIS Output:
```
  .SAVE [small-signal values]

### 30.18.1 DESCRIPTION

```
NBJT is the name for a bipolar transistor numerical model. In addition, the 2D model can be
used to simulate other three-terminal structures such as a JFET or MESFET. However, the 1D
model is customized with a special base contact, and cannot be used for other purposes. See the
options card for more information on how to customize the device type and setup the 1D base
contact.

Both 1”and 2D devices are supported. These correspond to the LEVEL=l and models, respectively. If left unspecified, it is assumed that the device is one-dimensional.

All numerical three-terminal element names begin with the letter ’Q’. If the device is a bipolar
transistor, then the nodes are specified in the order: collector (nl), base (n2), emitter (n3). For
a JFET or MESFET, the node order is: drain (n1), gate (n2), source (n3). After this must come
the name of the model used for the element. The remaining information can come in any order.
The layout dimensions of an element are specified relative to the geometry of a default device.
For the 1D BJT, the default device has an area of lm², and for 2D devices, the default device has
a width of lm. In addition, it is assumed that the default 1D BJT has a base contact with area
equal to the emitter area, length of 1µm and a depth automatically determined from the device
doping profile. However, all these defaults can be overridden on an options card.


-----

The operating temperature of a device can be set independently from the rest of that of the circuit
in order to simulate non-isothermal circuit operation. Finally, the name of a file containing an
initial state for the device can be specified. Remember that if the filename contains capital
letters, they must be protected by surrounding the filename with double quotes. Alternatively,
the device can be placed in an OFF state (thermal equilibrium) at the beginning of the analysis.
For more information on the use of initial conditions, see the NGSPICE User’s Manual.

In addition to the element input parameters, there are output-only parameters that can be shown
using the SPICE show command or captured using the save/.SAVE command. These parameters are the elements of the indefinite conductance (G), capacitance (C), and admittance (Y)
matrices where Y = G + jωC. By default, the parameters are computed at 1Hz. Each element
is accessed using the name of the matrix (g, c or y) followed by the node indices of the output
terminal and the input terminal (e.g. g11). Beware that parameter names are case-sensitive for
```
save/show, so lower-case letters must be used.

### 30.18.2 Parameters

```
Name Type Description

Level Integer Dimensionality of numerical model

Area Real Multiplicative area factor

W Real Multiplicative width factor

Temp Real Element operating temperature

IC.File String Initial-conditions filename

Off Flag Device initially in OFF state

gIJ Flag Conductance element Gi j, ( Ω )

cIJ Flag Capacitance element Ci j, ( F )

yIJ Flag Admittance element Yi j, ( Ω )

### 30.18.3 EXAMPLES

A one-dimensional numerical bipolar transistor with an emitter stripe 4 times as wide as the
default device is created using:
```
  Q2 1 2 3 M_BJT AREA=4

```
This example saves the output conductance (go), transconductance (gm) and input conductance
(gpi) of the previous transistor in that order:
```
  .SAVE @q2[g11] @q2[g12] @q2[g22]

```
The second example is for a two-dimensional JFET with a width of 5pm and initial conditions
obtained from file IC.jfet:
```
   QJ1 11 12 13 M_JFET W=5um IC.FILE="IC.jfet"
  .MODEL M_JFET NBJT LEVEL=2
  + options jfet
  + ...

```
|Name|Type|Description|
|---|---|---|
|Level|Integer|Dimensionality of numerical model|
|Area W|Real Real|Multiplicative area factor Multiplicative width factor|
|Temp|Real|Element operating temperature|
|IC.File Off|String Flag|Initial-conditions filename Device initially in OFF state|
|gIJ cIJ yIJ|Flag Flag Flag|Conductance element G , ( Ω) i j Capacitance element C , ( F ) i j Admittance element Y , ( Ω) i j|


-----

A final example shows how to use symmetry to simulate half of a 2D BJT, avoiding having the
user double the area of each instance:
```
  Q2 NC2 NB2 NE2 BJTMOD AREA=1
  Q3 NC3 NB3 NE3 BJTMOD AREA=1
  .MODEL BJTMOD NBJT LEVEL=2
  + options defw=2um
  + * Define half of the device now
  + ...

### 30.18.4 SEE ALSO

```
options, output

### 30.18.5 BUGS

MESFETs cannot be simulated properly yet because Schottky contacts have not been implemented.

## 30.19 NUMOS

MOSFET / four-terminal numerical models and elements

SYNOPSIS Model:
```
  .MODEL model-name NUMOS [level]
  + ...

```
SYNOPSIS Element:
```
   MXXXXXXX nl n2 n3 n4 model-name [geometry]
  + [temperature] [initial -conditions]

```
SYNOPSIS Output:
```
  .SAVE [small-signal values]

### 30.19.1 DESCRIPTION

```
NUMOS is the name for a MOSFET numerical model. In addition, the 2D model can be used
to simulate other four-terminal structures such as integrated bipolar and JFET devices with
substrate contacts. However, silicon controlled rectifiers (SCRs) cannot be simulated because
of the snapback in the transfer characteristic. See the options card for more information on
how to customize the device type. The LEVEL parameter of two- and three-terminal devices is


-----

not needed, because only 2D devices are supported. However, it will accepted and ignored if
provided.

All numerical four-terminal element names begin with the letter ‘M’. If the device is a MOSFET,
or JFET with a bulk contact, then the nodes are specified in the order: drain (n1), gate (n2),
source (n3), bulk (n4). If the device is a BJT, the node order is: collector (n1), base (n2),
emitter (n3), substrate (n4). After this must come the name of the model 1used for the element.
The remaining information can come in any order. The layout dimensions of an element are
specified relative to the geometry of a default device. The default device has a width of lm.
However, this default can be overridden on an options card. In addition, the element line will
accept a length parameter, L, but does not use it in any calculations. This is provided to enable
somewhat greater compatibility between numerical MOSFET models and the standard SPICE3
compact MOSFET models.

The operating temperature of a device can be set independently from that of the rest of the circuit
in order to simulate non-isothermal circuit operation. Finally, the name of a file containing an
initial state for the device can be specified. Remember that if the filename contains capital
letters, they must be protected by surrounding the filename with double quotes. Alternatively,
the device can be placed in an OFF state (thermal equilibrium) at the beginning of the analysis.
For more information on the use of initial conditions, see the NGSPICE User’s Manual.

In addition to the element input parameters, there are output-only parameters that can be shown
using the SPICE show command or captured using the save/.SAVE command.

These parameters are the elements of the indefinite conductance (G), capacitance (C), and admittance (Y) matrices where Y = G + jωC. By default, the parameters are computed at 1 Hz.
Each element is accessed using the name of the matrix (g, c or y) followed by the node indices of the output terminal and the input terminal (e.g. g11). Beware that parameter names are
case-sensitive for save/show, so lower-case letters must be used.

### 30.19.2 Parameters

Name Type Description

Level Integer Dimensionality of numerical model

Area Real Multiplicative area factor

W Real Multiplicative width factor

L Real Unused length factor

Temp Real Element operating temperature

IC.File String Initial-conditions filename

Off Flag Device initially in OFF state

gIJ Flag Conductance element Gi j, ( Ω )

cIJ Flag Capacitance element Ci j, ( F )

yIJ Flag Admittance element Yi j, ( Ω )

### 30.19.3 EXAMPLES

A numerical MOSFET with a gate width of 5µm and length of 1µm is described below. However, the model can only be used for lµm length devices, so the length parameter is redundant.
The device is initially biased near its threshold by taking an initial state from the file NM1.vth.

|Name|Type|Description|
|---|---|---|
|Level|Integer|Dimensionality of numerical model|
|Area W L|Real Real Real|Multiplicative area factor Multiplicative width factor Unused length factor|
|Temp|Real|Element operating temperature|
|IC.File Off|String Flag|Initial-conditions filename Device initially in OFF state|
|gIJ cIJ yIJ|Flag Flag Flag|Conductance element G , ( Ω) i j Capacitance element C , ( F ) i j Admittance element Y , ( Ω) i j|


-----

```
  M1 1 2 3 4 M_NMOS_1UM W=5um L=1um IC.FILE="NM1.vth"
  .MODEL MNMOS_1UM NUMOS
  + * Description of a lum device
  + ...

```
This example saves the definite admittance matrix of the previous MOSFET where the source
terminal (3) is used as the reference. (The definite admittance matrix is formed by deleting the
third row and column from the indefinite admittance matrix.)
```
  .SAVE @m1[y11] @m1[y12] @ml[y14]
  .SAVE @m1[y21] @m1[y22] @ml[y24]
  .SAVE @m1[y41] @m1[y42] @ml[y44]

```
Bipolar transistors are usually specified in terms of their area relative to a unit device. The
following example creates a unit-sized device:
```
   MQ1 NC NB NE NS N_BJT
  .MODEL M_BJT NUMOS LEVEL=2
  + options bipolar defw=5um
  + ...

### 30.19.4 SEE ALSO

```
options, output

## 30.20 Cider examples

[The original Cider User’s manual, in its Appendix A, lists a lot of examples, starting at page](http://www.eecs.berkeley.edu/Pubs/TechRpts/1993/2382.html)
226. We do not reproduce these pages here, but ask you to refer to the original document. If
[you experience any difficulties downloading it, please send a note to the ngspice users’ mailing](http://sourceforge.net/mailarchive/forum.php?forum_name=ngspice-users)
[list.](http://sourceforge.net/mailarchive/forum.php?forum_name=ngspice-users)


-----

