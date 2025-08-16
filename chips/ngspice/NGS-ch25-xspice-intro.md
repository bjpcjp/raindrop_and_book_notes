# Chapter 25

 XSPICE Basics

## 25.1 ngspice with the XSPICE option

The XSPICE option allows you to add event-driven simulation capabilities to NGSPICE. NGSPICE now is the main software program that performs mathematical simulation of a circuit
specified by you, the user. It takes input in the form of commands and circuit descriptions and
produces output data (e.g. voltages, currents, digital states, and waveforms) that describe the
circuit’s behavior.

Plain NGSPICE is designed for analog simulation and is based exclusively on matrix solution
techniques. The XSPICE option adds even-driven simulation capabilities. Thus, designs that
contain significant portions of digital circuitry can be efficiently simulated together with analog
components. NGSPICE with XSPICE option also includes a ‘User-Defined Node’ capability
that allows event-driven simulations to be carried out with any type of data.

The XSPICE option has been developed by the Computer Science and Information Technology
Laboratory at Georgia Tech Research Institute of the Georgia Institute of Technology, Atlanta,
Georgia 30332 at around 1990 and enhanced by the NGSPICE team. The manual is based on
[the original XSPICE user’s manual, made available from Georgia Tech.](http://users.ece.gatech.edu/~mrichard/Xspice/)

In the following, the term ‘XSPICE’ may be read as ‘NGSPICE with XSPICE code model subsystem enabled’. You may enable the option by adding --enable-xspice to the
```
./configure command. The MS Windows distribution already contains the XSPICE option.

## 25.2 The XSPICE Code Model Subsystem

```
The new component of ngspice, the Code Model Subsystem, provides the tools needed to model
the various parts of your system. While NGSPICE is targeted primarily at integrated circuit (IC)
analysis, XSPICE includes features to model and simulate board-level and system-level designs
as well. The Code Model Subsystem is central to this new capability, providing XSPICE with
an extensive set of models to use in designs and allowing you to add your own models to this
model set.

The NGSPICE simulator at the core of XSPICE includes built-in models for discrete components commonly found within integrated circuits. These ‘model primitives’ include components


-----

such as resistors, capacitors, diodes, and transistors. The XSPICE Code Model Subsystem extends this set of primitives in two ways. First, it provides a library of over 40 additional primitives, including summers, integrators, digital gates, controlled oscillators, s-domain transfer
functions, and digital state machines. See Chapt. 12 for a description of the library entries.
Second, it adds a code model generator to ngspice that provides a set of programming utilities to make it easy for you to create your own models by writing them in the C programming
language.

The code models are generated upon compiling ngspice. They are stored in shared libraries,
which may be distributed independently from the ngspice sources. Upon runtime ngspice will
load the code model libraries and make the code model instances available for simulation.

## 25.3 XSPICE Top-Level Diagram

A top-level diagram of the XSPICE system integrated into ngspice is shown in Fig. 25.1.
The XSPICE Simulator is made up of the NGSPICE core, the event-driven algorithm, circuit
description syntax parser extensions, a loading routine for code models, and the Nutmeg user
interface. The XSPICE Code Model Subsystem consists of the Code Model Generator, 5 standard code model library sources with more than 40 code models, the sources for Node Type
Libraries, and all the interfaces to User-Defined Code Models and to User-Defined Node Types.

Figure 25.1: ngspice/XSPICE Top-Level Diagram


![](NGS-ch25-xspice-intro.pdf-1-0.png)

-----

