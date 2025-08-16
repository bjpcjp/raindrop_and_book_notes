# Chapter 14

 Mixed-Level Simulation (ngspice with TCAD)

## 14.1 Cider

Ngspice implements mixed-level simulation through the merging of its code with CIDER (details see Chapt. 30).

CIDER is a mixed-level circuit and device simulator that provides a direct link between technology parameters and circuit performance. A mixed-level circuit and device simulator can provide greater simulation accuracy than a stand-alone circuit or device simulator by numerically
modeling the critical devices in a circuit. Compact models can be used for noncritical devices.

CIDER couples the latest version of SPICE3 (version 3F.2) [JOHN92] to a internal C-based
device simulator, DSIM. SPICE3 provides circuit analyses, compact models for semiconductor
devices, and an interactive user interface. DSIM provides accurate, one- and two-dimensional
numerical device models based on the solution of Poisson’s equation, and the electron and
hole current-continuity equations. DSIM incorporates many of the same basic physical models
found in the the Stanford two-dimensional device simulator PISCES [PINT85]. Input to CIDER
consists of a SPICE-like description of the circuit and its compact models, and PISCES-like
descriptions of the structures of numerically modeled devices. As a result, CIDER should seem
familiar to designers already accustomed to these two tools. For example, SPICE3F.2 input files
should run without modification, producing identical results.

CIDER is based on the mixed-level circuit and device simulator CODECS [MAYA88] and is a
replacement for this program. The basic algorithms of the two programs are the same. Some of
the differences between CIDER and CODECS are described below. The CIDER input format
has greater flexibility and allows increased access to physical model parameters. New physical
models have been added to allow simulation of state-of-the-art devices. These include transverse field mobility degradation [GATE90] that is important in scaled-down MOSFETs and a
polysilicon model for poly-emitter bipolar transistors. Temperature dependence has been included for most physical models over the range from -50°C to 150°C. The numerical models can
be used to simulate all the basic types of semiconductor devices: resistors, MOS capacitors, diodes, BJTs, JFETs and MOSFETs. BJTs and JFETs can be modeled with or without a substrate
contact. Support has been added for the management of device internal states. Post-processing
of device states can be performed using the NUTMEG user interface of SPICE3. Previously


-----

computed states can be loaded into the program to provide accurate initial guesses for subsequent analyses. Finally, numerous small bugs have been discovered and fixed, and the program
has been ported to a wider variety of computing platforms.

Berkeley tradition calls for the naming of new versions of programs by affixing a (number,
letter, number) triplet to the end of the program name. Under this scheme, CIDER should
instead be named CODECS2A.l. However, tradition has been broken in this case because major
incompatibilities exist between the two programs and because it was observed that the acronym
CODECS is already used in the analog design community to refer to coder-decoder circuits.

Details of the basic semiconductor equations and the physical models used by CIDER are not
provided in this manual. Unfortunately, no other single source exists that describes all of the
relevant background material. Comprehensive reviews of device simulation can be found in

[PINT90] and the book [SELB84]. CODECS and its inversion-layer mobility model are described in [MAYA88] and LGATE90], respectively. PISCES and its models are described in

[PINT85]. Temperature dependencies for the PISCES models used by CIDER are available in

[SOLL90].

## 14.2 GSS, Genius

For Linux users the cooperation of the TCAD software GSS with ngspice might be of interest,
[see http://ngspice.sourceforge.net/gss.html. This project is no longer maintained however, but](http://ngspice.sourceforge.net/gss.html)
[has moved into the Genius simulator, still available as open source cogenda genius.](http://www.cogenda.com/article/download)


-----

