# Chapter 24

 Notes

## 24.1 Glossary

**card A logical SPICE input line. A card may be extended through the use of the ‘+’ sign in**
SPICE, thereby allowing it to take up multiple lines in a SPICE deck.

**code model A model of a device, function, component, etc. which is based solely on a C**
programming language-based function. In addition to the code models included with the
XSPICE option of the ngspice simulator, you can use code models that you develop for
circuit modeling.

**deck A collection of SPICE cards that together specify all input information required in order**
to perform an analysis. A ‘deck’ of ‘cards’ will in fact be contained within a file on the
host computer system.

**element card A single, logical line in an ngspice circuit deck that describes a circuit element.**
Circuit elements are connected to each other to form circuits (e.g., a logical card that
describes a resistor, such as R1 2 0 10K, is an element card).

**instance A unique occurrence of a circuit element. See ‘element card’, in which the instance**
```
  R1 is specified as a unique element (instance) in a hypothetical circuit description.

```
**macro A macro, in the context of this document, refers to a C language macro that supports the**
construction of user-defined models by simplifying input/output and parameter-passing
operations within the Model Definition File.

**.mod Refers to the Model Definition File in XSPICE. The file suffix reflects the file-name of**
the model definition file: cfunc.mod.

**.model Refers to a model card associated with an element card in ngspice. A model card allows**
for data defining an instance to be conveniently located in the ngspice deck such that the
general layout of the elements is more readable.

**Nutmeg The ngspice default post-processor. This provides a simple stand-alone simulator**
interface that can be used with the ngspice simulator to display and plot simulator raw
files.

**subcircuit A ‘device’ within an ngspice deck that is defined in terms of a group of element**
cards and that can be referenced in other parts of the ngspice deck through element cards.


-----

## 24.2 Acronyms and Abbreviations

**ATE Automatic Test Equipment**

**CAE Computer-Aided Engineering**

**CCCS Current Controlled Current Source.**

**CCVS Current Controlled Voltage Source.**

**FET Field Effect Transistor**

**IDD Interface Design Document**

**IFS Refers to the Interface Specification File. The abbreviation reflects the file name of the**
Interface Specification File: ifspec.ifs.

**MNA Modified Nodal Analysis**

**MOSFET Metal Oxide Semiconductor Field Effect Transistor**

**PWL Piece-Wise Linear**

**RAM Random Access Memory**

**ROM Read Only Memory**

**SDD Software Design Document**

**SI Simulator Interface**

**SPICE Simulation Program with Integrated Circuit Emphasis. This program was developed at**
the University of California at Berkeley and is the origin of ngspice.

**SPICE3 Version 3 of SPICE.**

**SRS Software Requirements Specification**

**SUM Software User’s Manual**

**UCB University of California at Berkeley**

**UDN User-Defined Node(s)**

**VCCS Voltage Controlled Current Source.**

**VCVS Voltage Controlled Voltage Source**

**XSPICE Extended SPICE; option to ngspice, integrating predefined or user defined code mo-**
dels for event-driven mixed-signal simulation.


-----

## 24.3 To Do

1. Review of Chapt. 1.3

2. hfet1,2 model descriptions

3. MOS level 9 description


-----

