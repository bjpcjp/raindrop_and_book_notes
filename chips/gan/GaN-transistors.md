## GaN Transistors for
 Efficient Power
 Conversion

###### SECOND EDITION

 Alex Lidow

 Johan Strydom

 Michael de Rooij

 David Reusch


![](GaN-transistors-power-conversion.pdf-0-0.png)

![](GaN-transistors-power-conversion.pdf-0-1.png)

-----

-----

### GaN TRANSISTORS FOR EFFICIENT POWER CONVERSION


-----

-----

### GaN TRANSISTORS FOR EFFICIENT POWER CONVERSION

##### Second Edition

###### Alex Lidow

 Johan Strydom

 Michael de Rooij

 David Reusch
_Efficient Power Conversion Corporation, El Segundo, California, USA_


-----

This edition first published 2015
 Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch

_Registered office_
John Wiley & Sons Ltd, The Atrium, Southern Gate, Chichester, West Sussex, PO19 8SQ, United Kingdom

For details of our global editorial offices, for customer services and for information about how to apply for permission to
reuse the copyr ight material in this book please see our website at [www.w iley.com.](http://www.wiley.com)

The right of the author to be identified as the author of this work has been asserted in accordance with the Copyright, Designs
and Patents Act 1988.

All rights reserved. No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or
by any means, electronic, mechanical, photocopying, recording or otherwise, except as permitted by the UK Copyright,
Designs and Patents Act 1988, without the prior permission of the publisher.

Wiley also publishes its books in a variety of electronic formats. Some content that appears in print may not be available in
electronic books.

Limit of Liability/Disclaimer of Warranty: While the publisher and author have used their best efforts in preparing this book,
they make no representations or warranties with respect to the accuracy or completeness of the contents of this book and
specifically disclaim any implied warranties of merchantability or fitness for a particular purpose. It is sold on the
understanding that the publisher is not engaged in rendering professional services and neither the publisher nor the author
shall be liable for damages arising herefrom. If professional advice or other expert assistance is required, the services of a
competent professional should be sought

**_Library of Congress Cataloging-in-Publication Data_**

Lidow, Alex.
GaN transistors for efficient power conversion / Alex Lidow, Johan Strydom, Michael de Rooij, David Reusch. – Second
edition.
1 online resource.
Includes bibliographical references and index.
Description based on print version record and CIP data provided by publisher; resource not viewed.
ISBN 978-1-118-84478-6 (ePub) – ISBN 978-1-118-84479-3 (Adobe PDF) – ISBN 978-1-118-84476-2 (cloth)
1. Field-effect transistors. 2. Gallium nitride. I. Title.
TK7871.95
621.3815[´]284–dc23
2014023079

A catalogue record for this book is available from the British Library.

ISBN: 978-1-118-84476-2

Set in 10/12 pt TimesLTStd-Roman by Thomson Digital, Noida, India

1 2015


-----

###### In memory of Eric Lidow, the original power conversion pioneer.


-----

-----

#### Contents

**Foreword** xiii

**Acknowledgments** xv

**1** **GaN Technology Overview** 1
1.1 Silicon Power MOSFETs 1976–2010 1
1.2 The GaN Journey Begins 2
1.3 Why Gallium Nitride? 2
_1.3.1_ _Band Gap (Eg)_ 3
_1.3.2_ _Critical Field (Ecrit)_ 3
_1.3.3_ _On-Resistance (RDS(on))_ 4
_1.3.4_ _The Two-Dimensional Electron Gas_ 4
1.4 The Basic GaN Transistor Structure 6
_1.4.1_ _Recessed Gate Enhancement-Mode Structure_ 7
_1.4.2_ _Implanted Gate Enhancement-Mode Structure_ 7
_1.4.3_ _pGaN Gate Enhancement-Mode Structure_ 8
_1.4.4_ _Cascode Hybrid Enhancement-Mode Structure_ 8
_1.4.5_ _Reverse Conduction in HEMT Transistors_ 10
1.5 Building a GaN Transistor 10
_1.5.1_ _Substrate Material Selection_ 10
_1.5.2_ _Growing the Heteroepitaxy_ 11
_1.5.3_ _Processing the Wafer_ 12
_1.5.4_ _Making Electrical Connection to the Outside World_ 14
1.6 Summary 14
References 17

**2** **GaN Transistor Electrical Characteristics** 19
2.1 Introduction 19
2.2 Key Device Parameters 19
_2.2.1_ _Breakdown Voltage (BVDSS) and Leakage Current (IDSS)_ 19
_2.2.2_ _On-Resistance (RDS(on))_ 24
_2.2.3_ _Threshold Voltage (VGS(th) or Vth)_ 26


-----

2.3 Capacitance and Charge 27
2.4 Reverse Conduction 31
2.5 Thermal Resistance 33
2.6 Transient Thermal Impedance 36
2.7 Summary 37
References 38

**3** **Driving GaN Transistors** 39
3.1 Introduction 39
3.2 Gate Drive Voltage 41
3.3 Bootstrapping and Floating Supplies 43
3.4 dv/dt Immunity 44
3.5 di/dt Immunity 47
3.6 Ground Bounce 48
3.7 Common Mode Current 50
3.8 Gate Driver Edge Rate 51
3.9 Driving Cascode GaN Devices 51
3.10 Summary 53
References 53

**4** **Layout Considerations for GaN Transistor Circuits** 55
4.1 Introduction 55
4.2 Minimizing Parasitic Inductance 55
4.3 Conventional Power Loop Designs 58
4.4 Optimizing the Power Loop 60
4.5 Paralleling GaN Transistors 61
_4.5.1_ _Paralleling GaN Transistors for a Single Switch_ 61
_4.5.2_ _Paralleling GaN Transistors for Half-Bridge Applications_ 65
4.6 Summary 69
References 69

**5** **Modeling and Measurement of GaN Transistors** 70
5.1 Introduction 70
5.2 Electrical Modeling 70
_5.2.1_ _Basic Modeling_ 70
_5.2.2_ _Limitations of Basic Modeling_ 73
_5.2.3_ _Limitations of Circuit Modeling_ 75
5.3 Thermal Modeling 76
_5.3.1_ _Improving Thermal Performance_ 77
_5.3.2_ _Modeling of Multiple Die_ 79
_5.3.3_ _Modeling of Complex Systems_ 82
5.4 Measuring GaN Transistor Performance 83
_5.4.1_ _Voltage Measurement Requirements_ 83
_5.4.2_ _Current Measurement Requirement_ 85
5.5 Summary 87
References 87


-----

**6** **Hard-Switching Topologies** 89
6.1 Introduction 89
6.2 Hard-Switching Loss Analysis 89
_6.2.1_ _Switching Losses_ 91
_6.2.2_ _Output Capacitance (COSS) Losses_ 96
_6.2.3_ _Gate Charge (QG) Losses_ 96
_6.2.4_ _Reverse Conduction Losses (PSD)_ 97
_6.2.5_ _Reverse Recovery (QRR) Losses_ 99
_6.2.6_ _Total Hard-Switching Losses_ 99
_6.2.7_ _Hard-Switching Figure of Merit_ 100
6.3 External Factors Impacting Hard-Switching Losses 101
_6.3.1_ _Impact of Common-Source Inductance_ 101
_6.3.2_ _Impact of High Frequency Power-Loop Inductance on_
_Device Losses_ 103
6.4 Reducing Body Diode Conduction Losses in GaN Transistors 106
6.5 Frequency Impact on Magnetics 109
_6.5.1_ _Transformers_ 109
_6.5.2_ _Inductors_ 110
6.6 Buck Converter Example 110
_6.6.1_ _Output Capacitance Losses_ 112
_6.6.2_ _Gate Losses (PG)_ 114
_6.6.3_ _Body Diode Conduction Losses (PSD)_ 117
_6.6.4_ _Switching Losses (Psw)_ 119
_6.6.5_ _Total Dynamic Losses (PDynamic)_ 120
_6.6.6_ _Conduction Losses (PConduction)_ 120
_6.6.7_ _Total Device Hard-Switching Losses (PHS)_ 121
_6.6.8_ _Inductor Losses (PL)_ 122
_6.6.9_ _Total Buck Converter Estimated Losses (PTotal)_ 122
_6.6.10_ _Buck Converter Loss Analysis Accounting for Common Source_
_Inductance_ 123
_6.6.11_ _Experimental Results for the Buck Converter_ 125
6.7 Summary 126
References 126

**7** **Resonant and Soft-Switching Converters** 128
7.1 Introduction 128
7.2 Resonant and Soft-Switching Techniques 128
_7.2.1_ _Zero-Voltage and Zero-Current Switching_ 128
_7.2.2_ _Resonant DC-DC Converters_ 129
_7.2.3_ _Resonant Network Combinations_ 130
_7.2.4_ _Resonant Network Operating Principles_ 131
_7.2.5_ _Resonant Switching Cells_ 132
_7.2.6_ _Soft-Switching DC-DC Converters_ 133
7.3 Key Device Parameters for Resonant and Soft-Switching Applications 133
_7.3.1_ _Output Charge (QOSS)_ 133
_7.3.2_ _Determining Output Charge from Manufacturers’ Datasheet_ 134


-----

_7.3.3_ _Comparing Output Charge of GaN Transistors and Si MOSFETs_ 135
_7.3.4_ _Gate Charge (QG)_ 136
_7.3.5_ _Determining Gate Charge for Resonant and Soft-Switching_
_Applications_ 136
_7.3.6_ _Comparing Gate Charge of GaN Transistors and Si MOSFETs_ 138
_7.3.7_ _Comparing Performance Metrics of GaN Transistors and Si_
_MOSFETs_ 138
7.4 High-Frequency Resonant Bus Converter Example 139
_7.4.1_ _Resonant GaN and Si Bus Converter Designs_ 142
_7.4.2_ _GaN and Si Device Comparison_ 143
_7.4.3_ _Zero-Voltage Switching Transition_ 144
_7.4.4_ _Efficiency and Power Loss Comparison_ 145
7.5 Summary 148
References 148

**8** **RF Performance** 150
8.1 Introduction 150
8.2 Differences Between RF and Switching Transistors 151
8.3 RF Basics 153
8.4 RF Transistor Metrics 154
_8.4.1_ _Determining the High-Frequency Characteristics_
_of RF FETs_ 155
_8.4.2_ _Pulse Testing for Thermal Considerations_ 156
_8.4.3_ _Analyzing the S-Parameters_ 158
8.5 Amplifier Design Using Small-Signal S-Parameters 161
_8.5.1_ _Conditionally Stable Bilateral Transistor Amplifier Design_ 161
8.6 Amplifier Design Example 162
_8.6.1_ _Matching and Bias Tee Network Design_ 165
_8.6.2_ _Experimental Verification_ 168
8.7 Summary 170
References 170

**9** **GaN Transistors for Space Applications** 172
9.1 Introduction 172
9.2 Failure Mechanisms 172
9.3 Standards for Radiation Exposure and Tolerance 173
9.4 Gamma Radiation Tolerance 173
9.5 Single-Event Effects (SEE) Testing 175
9.6 Performance Comparison between GaN Transistors and Rad-Hard Si
MOSFETs 176
9.7 Summary 177
References 177

**10** **Application Examples** 179
10.1 Introduction 179
10.2 Non-Isolated DC-DC Converters 179


-----

_10.2.1_ _12 VIN – 1.2 VOUT Buck Converter_ 180
_10.2.2_ _28 VIN – 3.3 VOUT Point-of-Load Module_ 184
_10.2.3_ _48 VIN – 12 VOUT Buck Converter with Parallel GaN Transistors for_
_High-Current Applications_ 185
10.3 Isolated DC-DC Converters 191
_10.3.1_ _Hard-Switching Intermediate Bus Converters_ 192
_10.3.2_ _A 400 V LLC Resonant Converter_ 203
10.4 Class-D Audio 204
_10.4.1_ _Total Harmonic Distortion (THD)_ 204
_10.4.2_ _Damping Factor (DF)_ 205
_10.4.3_ _Class-D Audio Amplifier Example_ 206
10.5 Envelope Tracking 208
_10.5.1_ _High-Frequency GaN Transistors_ 209
_10.5.2_ _Envelope Tracking Experimental Results_ 211
_10.5.3_ _Gate Driver Limitations_ 211
10.6 Highly Resonant Wireless Energy Transfer 214
_10.6.1_ _Design Considerations for Wireless Energy Transfer_ 216
_10.6.2_ _Wireless Energy Transfer Examples_ 217
_10.6.3_ _Summary of Design Considerations for Wireless Energy Transfer_ 224
10.7 LiDAR and Pulsed Laser Applications 224
10.8 Power Factor Correction (PFC) 226
10.9 Motor Drive and Photovoltaic Inverters 227
10.10 Summary 228
References 228

**11** **Replacing Silicon Power MOSFETs** 232
11.1 What Controls the Rate of Adoption? 232
11.2 New Capabilities Enabled by GaN Transistors 232
11.3 GaN Transistors are Easy to Use 233
11.4 Cost vs. Time 234
_11.4.1_ _Starting Material_ 234
_11.4.2_ _Epitaxial Growth_ 234
_11.4.3_ _Wafer Fabrication_ 235
_11.4.4_ _Test and Assembly_ 235
11.5 GaN Transistors are Reliable 235
11.6 Future Directions 236
11.7 Conclusion 237
References 237

**Appendix** 239

**Index** 246


-----

-----

#### Foreword

It is well established that the CMOS inverter and DRAM are the two basic building blocks of
digital signal processing. Decades of improving inverter switching speed and memory density
under Moore’s Law has unearthed numerous applications that were previously unimaginable.
Power processing is built upon two similar functional building blocks: power switches and
energy storage devices, such as the inductor and capacitor. The push for higher switching
frequencies has always been a major catalyst for performance improvement and size reduction.
Since its introduction in the mid-1970s, the power MOSFET, with its greater switching
speed, has replaced the bipolar transistor. To date, the power MOSFET has been perfected up to
its theoretical limit. Device switching losses can be reduced further with the help of softswitching techniques. However, its gate drive loss is still excessive, limiting the switching
frequency to the low hundreds of kilohertz in most applications.
The recent introduction of GaN, with much improved figures of merit, opens the door for
operating frequencies well into the megahertz range. A number of design examples are
illustrated in this book and other literatures, citing impressive power density improvements of a
factor of 5 or 10. However, I believe the potential contribution of GaN goes beyond the simple
measures of efficiency and power density. GaN has the potential to have a profound impact on
our design practice, including a possible paradigm shift.
Power electronics is interdisciplinary. The essential constituents of a power electronics
system are switches, energy storage devices, circuit topology, system packaging, electromagnetic interactions, thermal management, EMC/EMI, and manufacturing considerations.
When the switching frequency is low, these various constituents are loosely coupled. Current
design practices address these issues in piecemeal fashion. When a system is designed for a
much higher frequency, the components are arranged in close proximity, to minimize
undesirable parasitics. This invariably leads to unwanted electromagnetic coupling and thermal
interaction.
This increasing intricacy between components and circuits requires a more holistic
approach, concurrently taking into account all electrical, mechanical, electromagnetic and
thermal considerations. Furthermore, all operations should be executed correctly, both spatially
and temporally. These challenges prompt circuit designers to pursue a more integrated
approach. For power electronics, integration needs to take place at the functional level or
the subsystem level whenever feasible and practical. These integrated modules then serve as
the basic building blocks of further system integration. In this manner, customization can be
achieved using standardized building blocks, in much the same way as digital electronics


-----

systems. With the economy of scale in manufacturing, this will bring significant cost reduction
in power electronics equipment and unearth numerous new applications previously precluded
due to high cost.
GaN will create fertile ground for research and technological innovations for years to come.
Dr. Alex Lidow mentions in this book that it took thirty years for the power MOSFET to reach
its current state of maturity. While GaN is still in an early stage of development, a few technical
challenges require immediate attention. These issues are recognized by the authors and are
addressed in this book.

1. High dv/dt and high di/dt render most of the commercially available gate drive circuits
unsuitable for GaN devices, especially for the high-side switch. Chapter 3 offers many
important insights in the design of the gate drive circuit.
2. Device packaging and circuit layout are critical. The unwanted effects of parasitics need to
be contained. Soft-switching techniques can be very useful for this purpose. A number of
important issues related to packaging and layout are addressed in detail in Chapters 4–6.
3. High-frequency magnetic design is also critical. The choice of suitable magnetic materials
becomes rather limited when the switching frequency goes beyond 2–3 MHz. Additionally,
more creative high-frequency magnetics design practice should be explored. Several recent
publications suggest design practices that defy the conventional wisdom and practice,
yielding interesting results.
4. The impact of high frequency on EMI/EMC has yet to be explored.

Dr. Alex Lidow is a well-respected leader in the field. Alex has always been in the forefront
of technology and a trendsetter. While serving as the CEO of IR, he initiated GaN development
in the early 2000s. He also led the team in developing the first integrated DrMOS and
DirectFET[®], which are now commonly used to power the new generation of microprocessors
and many other applications.
This book is a gift to power electronics engineers. It offers a comprehensive view, from
device physics, characteristics, and modeling to device and circuit layout considerations and
gate drive design, with design considerations for both hard switching and soft switching.
Additionally, it further illustrates the utilization of GaN in a wide range of emerging
applications.
It is very gratifying to note that three of the four authors of this book are from CPES, joining
with Dr. Lidow in an effort to develop this new generation of wide-band-gap power switches –
presumably a game-changing device with a scale of impact yet to be defined.

Dr. Fred C. Lee
_Director, Center for Power Electronics Systems_
_University Distinguished Professor, Virginia Tech_


-----

#### Acknowledgments

The authors wish to acknowledge the many exceptional contributions towards the content of
this book from our colleagues Jianjun (Joe) Cao, Robert Beach, Alana Nakata, Guang Yuan
Zhao, Audrey Downes, Steve Colino, Bhasy Nair, Renee Yawger, Yanping Ma, Robert
Strittmatter, Stephen Tsang, Peter Cheng, Larry Chen, F.C. Liu, M.K. Chiang, Winnie Wong,
Chunhua Zhou, Seshadri Kolluri, Jiali Cao, Lorenzo Nourafchan, and Andrea Mirenda.
A special thank you is due to Joe Engle who, in addition to reviewing and editing all corners
of this work, put all the logistics together to make it happen. Joe also assembled an exceptional
group of graphic artists, all of whom worked with endless patience against difficult deadlines.
A note of gratitude to the editors and staff at Wiley who were instrumental in undertaking a
diligent review of the text and shepherding the book through the production process.
Finally, we would like to thank Archie Huang and Sue Lin for believing in GaN from the
beginning. Their vision and support will change the semiconductor industry forever.

Alex Lidow
Johan Strydom
Michael de Rooij
David Reusch
_Efficient Power Conversion Corporation_
_April 2014_


-----

-----

# 1

#### GaN Technology Overview

###### 1.1 Silicon Power MOSFETs 1976–2010

For over three decades, power management efficiency and cost have improved steadily as
innovations in power metal oxide silicon field effect transistor (MOSFET) structures,
technology, and circuit topologies have kept pace with the growing need for electrical power
in our daily lives. In the new millennium, however, the rate of improvement has slowed as the
silicon power MOSFET asymptotically approaches its theoretical bounds.
Power MOSFETs first appeared in 1976 as alternatives to bipolar transistors. These majoritycarrier devices were faster, more rugged, and had higher current gain than their minority-carrier
counterparts (for adiscussionofbasicsemiconductor physics,a goodreferenceis[1]).Asaresult,
switching power conversion became a commercial reality. Among the earliest high-volume
consumers of power MOSFETs were AC-DC switching power supplies for early desktop
computers, followed by variable-speed motor drives, fluorescent lights, DC-DC converters, and
thousands of other applications that populate our daily lives.
One of the first power MOSFETs was the IRF100 from International Rectifier Corporation,
introduced in November 1978. It boasted a 100V drain-source breakdown voltage and a 0.1 Ω
on-resistance (RDS(on)), the benchmark of the era. With a die size of over 40 mm[2], and a $34 price
tag, this product was not destined to supplant the venerable bipolar transistor immediately. Since
then, several manufacturers have developed many generations of power MOSFETs. Benchmarks
have been set, and subsequently surpassed, each year for 30-plus years. As of the date of writing,
the100 V benchmark arguablyis held byInfineonwith theBSC060N10NS3.In comparisonwith
the IRF100 MOSFET’s resistivity figure of merit (4 Ωmm[2]), the BSC060N10NS3 has a figure of
merit of 0.072 Ωmm[2]. That is almost at the theoretical limit for a silicon (Si) device [2].
There are still improvements to be made in power MOSFETs. For example, super-junction
devices and IGBTs have achieved conductivity improvements beyond the theoretical limits of a
simple vertical majority-carrier MOSFET. These innovations may continue for quite some time
and certainly will be able to leverage the low cost structure of the power MOSFET and the
know-how of a well-educated base of designers who, after many years, have learned to squeeze
every ounce of performance out of their power conversion circuits and systems.

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

###### 1.2 The GaN Journey Begins

Gallium nitride (GaN) high electron mobility transistor (HEMT) devices first appeared in about
2004 with depletion-mode radio frequency (RF) transistors made by Eudyna Corporation in
Japan. Using GaN on silicon carbide (SiC) substrates, Eudyna successfully produced transistors designed for the RF market [3]. The HEMT structure was based on the phenomenon first
described in 1975 by T. Mimura et al. [4], and in 1994 by M. A. Khan et al. [5], which demonstrated the unusually high electron mobility described as a two-dimensional electron gas in
the region of an aluminum gallium nitride (AlGaN) and GaN heterostructure interface.
Adapting this phenomenon to gallium nitride grown on silicon carbide, Eudyna was able
to produce benchmark power gain in the multi-gigahertz frequency range. In 2005, Nitronex
Corporation introduced the first depletion-mode RF HEMT device made with GaN grown on
silicon wafers using their SIGANTIC[] technology.
GaN RF transistors have continued to make inroads in RF applications, as several other
companies have entered the market. Acceptance outside of this application, however, has been
limited by device cost as well as the inconvenience of depletion-mode operation (normally
conducting and requires a negative voltage on the gate to turn the device off).
In June 2009, the Efficient Power Conversion Corporation (EPC) introduced the first
enhancement-mode GaN on silicon (eGaN[]) FETs designed specifically as power MOSFET
replacements (since eGaN FETs do not require a negative voltage to be turned off). At the
outset, these products were produced in high volume at low cost by using standard silicon
manufacturing technology and facilities. Since then, Matsushita, Transphorm, GaN Systems,
RFMD, Panasonic, HRL, and International Rectifier, among others, have announced their
intention to manufacture GaN transistors for the power conversion market.
Thebasicrequirementsforsemiconductorsusedinpowerconversionareefficiency,reliability,
controllability, and cost effectiveness. Without these attributes, a new device structure would not
be economically viable. There have been many new structures and materials considered as a
successor to silicon; some have been economic successes, others have seen limited or niche
acceptance. In the next section, we will look at the comparison between silicon, silicon carbide,
and gallium nitride as platform candidates to dominate the next generation of power transistors.

###### 1.3 Why Gallium Nitride?

Silicon has been a dominant material for power management since the late 1950s. The
advantages that silicon had over earlier semiconductors, such as germanium or selenium, could
be expressed in four key categories:

- silicon enabled new applications not possible with earlier materials

- silicon proved more reliable

- silicon was easier to use in many ways

- silicon devices cost less

All of these advantages stemmed from the basic physical properties of silicon, combined
with a huge investment in manufacturing infrastructure and engineering. Let’s look at some of
those basic properties and compare them with other successor candidates. Table 1.1 identifies
five key electrical properties of three semiconductor materials contending for the power
management market.


-----

**Table 1.1** Material properties of Silicon, GaN, and SiC

Parameter Silicon GaN SiC

Band Gap Eg eV 1.12 3.39 3.26
Critical Field ECrit MV/cm 0.23 3.3 2.2
Electron Mobility μn cm[2]/Vs 1400 1500 950
Permittivity εr 11.8 9 9.7
Thermal Conductivity λ W/cmK 1.5 1.3 3.8

One way of translating these basic crystal parameters into a comparison of device
performance is to calculate the best theoretical performance achievable for each of the three
candidates. For power devices, there are many characteristics that matter in the variety of power
conversion systems available today. Five of the most important are: conduction efficiency (onresistance), breakdown voltage, size, switching efficiency, and cost.
In the next section, the first four of the material characteristics in Table 1.1 will be reviewed,
leading to the conclusion that both SiC and GaN are capable of producing devices with superior
on-resistance, breakdown voltage, and a smaller-sized transistor compared to silicon. In
Chapter 2, we will look at how these material characteristics translate into superior switching
efficiency for a GaN transistor, and in Chapter 11, how a GaN transistor can also be produced at
a lower cost than a silicon MOSFET of equivalent performance.

###### 1.3.1 Band Gap (Eg)

The band gap of a semiconductor is related to the strength of the chemical bonds between the
atoms in the lattice. These stronger bonds mean that it is harder for an electron to jump from one
site to the next. Among the many consequences are lower intrinsic leakage currents and higher
operating temperatures for higher band gap semiconductors. Based on the data in Table 1.1,
GaN and SiC both have higher band gaps than silicon.

###### 1.3.2 Critical Field (Ecrit)

The stronger chemical bonds that cause the wider band gap also result in a higher critical
electric field needed to initiate impact ionization, thus causing avalanche breakdown. The
voltage at which a device breaks down can be approximated with the formula:

VBR 2 wdrift?Ecrit (1.1)
[1][=]

The breakdown voltage of a device (VBR), therefore, is proportional to the width of the drift
region (wdrift). In the case of SiC and GaN, the drift region can be 10 times smaller than in
silicon for the same breakdown voltage. In order to support this electric field, there need to be
carriers in the drift region that are depleted away at the point where the device reaches the
critical field. This is where there is a huge gain in devices with high critical fields. The number
of electrons (assuming an N-type semiconductor) between the two terminals can be calculated
using Poison’s equation:

q?ND  εo?εr?Ecrit/wdrift (1.2)


-----

In this equation q is the charge of the electron (1.610[�][19] coulombs), ND is the total number of
electrons in the volume, εo is the permittivity of a vacuum measured in farads per meter
(8.85410[�][12] F/m), and εr is the relative permittivity of the crystal compared to a vacuum. In its
simplest form under DC conditions, permittivity is the dielectric constant of the crystal.
Referring to Equation 1.2, it can be seen that if the critical field of the crystal is 10 times
higher, and from Equation 1.1, the electrical terminals can be 10 times closer together.
Therefore, the number of electrons, ND, in the drift region can be 100 times greater. This is the
basis for the ability of GaN and SiC to outperform silicon in power conversion.

###### 1.3.3 On-Resistance (RDS(on))


The theoretical on-resistance (measured in ohms (Ω)) of this majority-carrier device is therefore

RDS(on)  wdrift/q?μn?ND (1.3)


Where μn is the mobility of electrons. Combining Equations 1.1, 1.2, and 1.3 produces the
following relationship between breakdown voltage and on-resistance:

RDS(on)  4?V[2]BR[/][ε][o][?][ε][r][?][E][3]crit (1.4)


This equation can now be plotted as shown in Figure 1.1 for Si, SiC, and GaN. This plot is for
an ideal structure. Real semiconductors are not always ideal structures and so it is always a
challenge to achieve the theoretical limit. In the case of silicon MOSFETs, it took 30 years.

###### 1.3.4 The Two-Dimensional Electron Gas


The natural structure of crystalline gallium nitride is a hexagonal structure named “wurtzite”
(see Figure 1.2). Because this structure is very chemically stable, it is mechanically robust and

10[1]


10[0]

10[–1]


10[–2]

10[–3]


10[–4]

10[1] 10[2]


10[3] 10[4]


**Breakdown Voltage (V)**

**Figure 1.1** Theoretical on-resistance vs. blocking voltage capability for Si, SiC, and GaN based power
devices


-----

**Ga**

**N**

**Figure 1.2** Schematic of wurtzite GaN

can withstand high temperatures without decomposition. This crystal structure also gives GaN
piezoelectric properties that lead to its ability to achieve very high conductivity compared with
other semiconductor materials. Piezoelectricity in GaN is predominantly caused by the
displacement of charged elements in the crystal lattice. If the lattice is subjected to strain,
the deformation will cause a miniscule shift in the atoms in the lattice that generate an electric
field – the higher the strain, the greater the electric field. By growing a thin layer of AlGaN on
top of a GaN crystal, a strain is created at the interface that induces a compensating twodimensional electron gas (2DEG) as shown schematically in Figure 1.3 [6–8]. This 2DEG is
used to efficiently conduct electrons when an electric field is applied across it, as in Figure 1.4.
This 2DEG is highly conductive, in part due to the confinement of the electrons to a very
small region at the interface. This confinement increases the mobility of electrons from about
1000 cm[2]/V s in unstrained GaN to 1500–2000 cm[2]/V s in the 2DEG region. The high
 
concentration of electrons with very high mobility is the basis for the high electron mobility
transistor (HEMT), the primary subject of this book.

**AIGaN**

**GaN**

**Figure 1.3** Simplified cross section of a GaN/AlGaN heterostructure showing the formation of a 2DEG
due to the strain-induced polarization at the interface between the two materials


-----

**V**

**Current Flow**

**AIGaN**

**GaN**

**Figure 1.4** By applying a voltage to the 2DEG an electric current is induced in the crystal

###### 1.4 The Basic GaN Transistor Structure

The basic depletion-mode GaN transistor structure is shown in Figure 1.5. As with any power
FET, there are gate, source, and drain electrodes. The source and drain electrodes pierce
through the top AlGaN layer to form an ohmic contact with the underlying 2DEG. This creates
a short circuit between the source and the drain until the 2DEG “pool” of electrons is depleted,
and the semi-insulating GaN crystal can block the flow of current. In order to deplete the
2DEG, a gate electrode is placed on top of the AlGaN layer. When a negative voltage relative to
both drain and source electrodes is applied to the gate, the electrons in the 2DEG are depleted
out of the device. This type of transistor is called a depletion-mode, or d-mode, HEMT.
There are two common ways to produce a d-mode HEMT device. The initial transistors
introduced in 2004 had a Schottky gate electrode that was created by depositing a metal layer
directly on top of the AlGaN. The Schottky barrier was formed using metals such as Ni-Au or
Pt [9–11]. Depletion-mode devices have also been made using an insulating layer and metal
gate similar to a MOSFET [12]. Both types are shown in Figure 1.6.
In power conversion applications, d-mode devices are inconvenient because, at the startup of
a power converter, a negative bias must first be applied to the power devices. If this negative

**AIGaN**

**d-mode**
**Gate**

**Source** **Drain**

**GaN**

**Figure 1.5** By applying a negative voltage to the gate of the device, the electrons in the 2DEG are
depleted out of the device. This type of device is called a depletion-mode (d-mode) HEMT


-----

**AIGaN**


**Insulator** **AIGaN**


(a) (b)

**Figure 1.6** Cross section of a basic depletion-mode GaN HEMT with (a) Schottky gate, or (b) insulating
gate

bias is not applied first, a short circuit will result. An enhancement-mode (e-mode) device, on
the other hand, would not suffer this limitation. With zero bias on the gate, an e-mode device is
OFF (Figure 1.7(a)) and will not conduct current until a positive voltage is applied to the gate,
as illustrated in Figure 1.7(b).
There are four popular structures that have been used to create enhancement-mode devices:
recessed gate, implanted gate, pGaN gate, and cascode hybrid.

###### 1.4.1 Recessed Gate Enhancement-Mode Structure

The recessed gate structure has been discussed extensively in the literature [13] and is created
by thinning the AlGaN barrier layer above the 2DEG (see Figure 1.8). By making the AlGaN
barrier thinner, the amount of voltage generated by the piezoelectric field is reduced
proportionally. When the voltage generated is less than the built-in voltage of the Schottky
gate metal, the 2DEG is eliminated with zero bias on the gate. With positive bias, electrons are
attracted to the AlGaN interface and complete the circuit between source and drain.

###### 1.4.2 Implanted Gate Enhancement-Mode Structure

Shown in Figure 1.9(a) and (b) is a method for creating an enhancement-mode device by
implanting fluorine atoms in the AlGaN barrier layer [14]. These fluorine atoms create a
“trapped” negative charge in the AlGaN layer that depletes the 2DEG underneath. By adding a
Schottky gate on top, an enhancement-mode HEMT is created.

**AIGaN** **AIGaN**

**e-mode** **e-mode**
**Gate** **Gate**

**Source** **Drain** **Source** **Drain**

**GaN** **GaN**

(a) (b)

**Figure 1.7** (a) An enhancement-mode (e-mode) device depletes the 2DEG with zero volts on the gate.
(b) By applying a positive voltage to the gate, the electrons are attracted to the surface, re-establishing the
2DEG


-----

**Recess in AIGaN Barrier**

**Schottky**
**Gate**

**Source** **Drain**

**GaN**

**Figure 1.8** By etching away part of the AlGaN barrier layer a recessed gate e-mode transistor can be
fabricated


**Fluorine Atoms**
**AIGaN**

**Schottky**
**Gate**

**Drain** **Source**

**GaN** **GaN**

(a) (b)


**AIGaN**


**Figure 1.9** (a) By implanting fluorine atoms into the AlGaN barrier layer negative charges are trapped in
the barrier. (b) A Schottky gate now can be used to reconstruct the 2DEG when a positive voltage is applied

###### 1.4.3 pGaN Gate Enhancement-Mode Structure

The first enhancement-mode devices sold commercially had a positively charged (p-type) GaN
layer grown on top of the AlGaN barrier (see Figure 1.10) [15]. The positive charges in this
pGaN layer have a built-in voltage that is larger than the voltage generated by the piezoelectric
effect, thus depleting the electrons in the 2DEG and creating an enhancement-mode
structure [16].

###### 1.4.4 Cascode Hybrid Enhancement-Mode Structure

An alternative to building a single-chip enhancement-mode GaN transistor is to place an
enhancement-mode silicon MOSFET in series with a depletion-mode HEMT device [17,18] as
shown in Figure 1.11. In this circuit, the MOSFET is turned on with a positive voltage on the

**AIGaN**

**Metal**

**pGaN**

**Source** **Drain**

**GaN**

**Figure 1.10** By growing a p-type GaN layer on top of the AlGaN the 2DEG is depleted at zero volts on
the gate


-----

**Depletion-**
**Mode GaN**


**Enhancement-**
**Mode Silicon**
**MOSFET**


**Gate**


**Figure 1.11** Schematic of low-voltage enhancement-mode silicon MOSFET in series with a depletionmode GaN HEMT

gate when the depletion-mode GaN transistor’s gate voltage goes to near-zero volts and turns
on. Current can now pass through the depletion-mode GaN HEMT and the MOSFET, which is
connected in series with the GaN HEMT. When the voltage on the MOS gate is removed, a
negative voltage is created between the depletion-mode GaN transistor gate and its source
electrode, turning the GaN device off.
This type of solution for an enhancement-mode GaN “system” works well when the GaN
transistor has a relatively high on-resistance compared with the low voltage (usually 30 V
rated) silicon MOSFET. Since on-resistance increases with the device breakdown voltage,
cascode solutions are most effective when the GaN HEMT is high voltage and the MOSFET is
very low voltage. In Figure 1.12 is a chart showing the added on-resistance to the cascode
circuit by the enhancement-mode silicon MOSFET. A 600 V cascode device would only have
about 3% added on-resistance due to the low-voltage MOSFET. Conversely, as the desired
rated voltage goes down, and the on-resistance of the GaN transistor decreases, the MOSFET
contribution becomes more significant. For this reason, cascode solutions are only practical at
voltages higher than 200 V.

45%
40%
35%
30%
25%
20%
15%
10%
5%
0%

0 100 200 300 400 500 600 700


**Rated Voltage**

**Figure 1.12** At a higher voltage rating the low voltage MOSFET does not add significantly to the onresistance of the cascode transistor system


-----

**Forward Current Flow** **Reverse Current Flow**

(a) (b)

**Figure 1.13** Enhancement-mode HEMT transistors can conduct in either the forward or reverse
direction

###### 1.4.5 Reverse Conduction in HEMT Transistors

Enhancement-mode GaN transistors can also conduct in the reverse direction when the drain
voltage is higher than the gate voltage by at least VGS(th) (see Figure 1.13(b)). In this situation, the
2DEG is again restored under the gate electrode, and current can flow from source to drain.
Because the enhancement-mode HEMT has nominority carrier conduction,the device, operating
similar to a diode, will turn off instantly when the forward bias is removed between the gate and
drain electrodes. This characteristic is quite useful in certain power conversion circuits.
In the reverse direction, the cascode-connected transistor discussed in Section 1.4.4 conducts
in the same way as an enhancement-mode GaN HEMT, except that the diode of the MOSFET
is conducting the reverse current, which then has to flow through the GaN device. The forward
voltage drop of the MOSFET diode creates a slight positive voltage from gate to source in the
HEMT which, therefore, is turned on in the forward direction. The HEMT on-resistance is
added to the voltage drop of the MOSFET in this configuration. Unlike the enhancement-mode
GaN HEMT, the cascode-configured transistor does have a recovery time due to the injection
of minority carriers in the silicon-based MOSFET.

###### 1.5 Building a GaN Transistor

Building a GaN transistor starts with the process of growing the GaN/AlGaN heterostructure.
There are four different starting bases, or substrates, that have been commonly used in fabricating
GaNHEMTtransistors:bulkgalliumnitridecrystal,sapphire(Al2O3),siliconcarbide,andsilicon.

###### 1.5.1 Substrate Material Selection

The most obvious choice for a GaN HEMT starting material would be a GaN crystal. The first
attempts at growing GaN crystals were in the 1960s. Native defects from high nitrogen vacancy
concentrations rendered these early attempts unusable for semiconductor device fabrication.
Since then, progress has been made and small-diameter, high-quality GaN crystals are
becoming available, holding promise for use as a platform for active device fabrication.
Heteroepitaxy is a process whereby one type of crystal structure is grown on top of a
different crystal. Because GaN crystals have not been readily available, there has been much
work focused on growing GaN crystals on top of a more convenient platform such as sapphire,


-----

**Table 1.2** Some key properties of Al2O3, SiC, and Si [19]

Substrate Crystal Lattice Lattice Relative thermal
plane spacing Å mismatch % expansion
10[�][5] K[�][1]



Thermal
conductivity
W/cm K



Relative
Cost


Al2O3 (0001) 4.758 16.1 �1.9 0.42 Middle
6H-SiC (0001) 3.08 3.5 1.4 3.8 Highest
Si (111) 3.84 17 3 1.5 Lowest
�

silicon carbide, or more recently, silicon. The starting point for trying to grow on a dissimilar
crystal layer is to find a substrate with the appropriate physical properties.
Referring to Table 1.2, it can be seen that there are tradeoffs between any of the three listed
choices for a substrate material. For example, sapphire (Al2O3) has a 16.1% mismatch to a GaN
crystal lattice and has poor thermal conductivity. Thermal conductivity is especially important
in transistors for power conversion because they generate a significant amount of heat flux
during operation due to internal power dissipation. Silicon carbide (6H-SiC) substrate, on the
other hand, has a reasonably good lattice match and excellent thermal conductivity. The
disadvantage comes from the cost of the starting crystal substrate, which can be up to 100 times
the cost of a silicon substrate of the same diameter. Silicon is also not an ideal base for a GaN
heteroepitaxial structure due to the lattice mismatch and the mismatch of thermal expansion
coefficients. Silicon, however, is the least expensive material and there is a large and welldeveloped infrastructure to process devices on silicon substrates.
For these reasons, silicon carbide is commonly used for devices that require very high power
densities, such as linear RF applications; silicon is used for devices in more cost-sensitive
commercial applications such as DC-DC conversion, AC-DC conversion, and motion control.

###### 1.5.2 Growing the Heteroepitaxy

There are several types of technologies that have been used to grow GaN on different
substrates [20–23]. The two most promising are metal organic chemical vapor deposition
(MOCVD) and molecular beam epitaxy (MBE). MOCVD is faster and generally lower cost,
whereas MBE is capable of more uniform layers with very abrupt transitions between layers.
For GaN HEMT devices in power conversion applications, MOCVD is the dominant
technology owing to the cost advantages.
An MOCVD growth occurs in an inductively or radiantly heated reactor. A highly reactive
precursor gas is introduced into the chamber where the gas is “cracked” by the hot substrate and
reacts to form the desired compound. For GaN growth, the precursors are ammonia (NH3) and
trimethyl-gallium (TMG). For AlGaN growth, the precursors are trimethyl-aluminum (TMA)
or triethyl-aluminum (TEA). In addition to the precursors, carrier gases such as H2 and N2 are
used to enhance mixing and control the flow within the chamber. Temperatures in the range of
900–1100 °C are used for these growths.
A GaN heteroepitaxial structure involves at least four growth stages. Figure 1.14 illustrates
this process. The starting material (a), of either SiC or Si, is heated in the reaction chamber. A
layer of AlN is then grown (b) to create a seed layer that is hospitable to the AlGaN wurtzite
crystal structure. An AlGaN “buffer layer” (c) creates the transition to the GaN crystal (d).


-----

**GaN**


**AIGaN Buffer Layer**


**Substrate (Si or SiC)**


**AIN Seed Layer**


**AIN Seed Layer**


**Substrate (Si or SiC)**


**Substrate (Si or SiC)**


(a)

(b)

(c)


**AIGaN Barrier**


**GaN**


(d)

(e)


**AIGaN Buffer Layer**


**AIGaN Buffer Layer**


**AIN Seed Layer**


**AIN Seed Layer**


**Substrate (Si or SiC)** **Substrate (Si or SiC)**

**Figure 1.14** An illustration of the basic steps involved in creating a GaN heteroepitaxial structure (not
to scale)

**pGaN**
**AIGaN Barrier**


**GaN**


**AIGaN Buffer Layer**


**AIN Seed Layer**


**Substrate (Si or SiC)**


**Figure 1.15** An additional GaN layer, doped with p-type impurities can be added to the heteroepitaxy
process when producing an enhancement-mode device as illustrated in Figure 1.10

Finally, the thin AlGaN barrier (e) is grown on top of the GaN crystal to create the strain layer
that induces the 2DEG formation.
Earlier in this chapter, several methods of making enhancement-mode GaN transistors were
described. One method (pGaN enhancement-mode), illustrated in Figure 1.10, includes an
additional GaN layer grown on top of the AlGaN barrier. This layer is most commonly doped
with p-type impurities such as Mg or Fe. A cross section of this heteroepitaxy structure is
shown in Figure 1.15.

###### 1.5.3 Processing the Wafer

Fabricating an HEMT transistor from a heteroepitaxial substrate can be accomplished in variety
of sequential steps. One example of a simplified process for making an enhancement-mode
HEMT with a pGaN gate is shown in Figure 1.16. A cross section of a completed device using
this process is shown in Figure 1.17.


-----

**Source Metal** **Gate Metal** **Drain Metal**

**pGaN** **Insulating Material**
**AIGaN Barrier**

**GaN**


**AIGaN Buffer Layer**


(a)

(b)


**AIN Seed Layer**


**Substrate (Si or SiC)**


**Gate Metal**

**pGaN**


(f)


**AIGaN Barrier**

**GaN**

**AIGaN Buffer Layer**

**AIN Seed Layer**


**AIGaN Buffer Layer**


**Substrate (Si or SiC)**


**Metal 2** **Metal 2**


**Gate Metal**

**pGaN** **Insulating Material**
**AIGaN Barrier**

**GaN**


**Source Metal** **Gate Metal** **Drain Metal**

**pGaN** **Insulating Material**
**AIGaN Barrier**

**GaN**


**AIGaN Buffer Layer**


**AIGaN Buffer Layer**


**AIN Seed Layer**


**AIN Seed Layer**


**Substrate (Si or SiC)**


**Substrate (Si or SiC)**


(g)


(c)

**Source** **Gate Metal**
**Contact** **pGaN** **Insulating Material**
**Opening** **AIGaN Barrier**

**GaN**


**Drain**
**Contact**
**Opening**


**Passivation Layer**

**Metal 3** **Metal 3**


**AIGaN Buffer Layer**


**AIN Seed Layer**


**Substrate (Si or SiC)**


(d)

(e)


**Metal 2** **Metal 2**


**Source Metal** **Gate Metal** **Drain Metal**


25

2626


**AIGaN BarrierInsulating Material** **DrainMetal** **pGaN** **AIGaN BarrierInsulating Material**

**GaN** **GaN**

**AIGaN Buffer Layer** **AIGaN Buffer Layer**

**AIN Seed Layer** **AIN Seed Layer**


**Substrate (Si or SiC)**


(h)


**Figure 1.16** A typical process for fabricating an enhancement-mode GaN HEMT (not to scale) [24,25].
The process steps are as follows: (a) Deposit gate metal and define gate pattern using photoresist as a
protecting layer. (b) Etch the gate metal and pGaN crystal. (c) Deposit insulating material. (d) Create
contact openings to source, drain, and gate (gate contact not pictured). (e) Deposit first aluminum metal
layer and define metal pattern. (f) Deposit interlayer dielectric. (g) Cut vias between metal layers, form
tungsten via plug, deposit and define second aluminum metal layer. (h) Deposit and define third aluminum
layer and deposit final passivation layer


-----

![](GaN-transistors-power-conversion.pdf-31-0.png)

**Passivation**

**Metal 3**

**Metal 2** **Tungsten Via**

**Metal 1**

**Gates** **Drain** **Source**


**Figure 1.17** SEM micrograph of an enhancement-mode GaN HEMT made by Efficient Power
Conversion Corporation [24–26]

###### 1.5.4 Making Electrical Connection to the Outside World

Following the device fabrication, provisions are needed to make the electrical connection to the
electrodes of the device. There are two common ways of making connection to a power
transistor: (a) attach bond wires between metal pads on the device and metal posts in a plastic or
ceramic package, or (b) create contacts that can be soldered directly onto the device while still
in wafer form. As explored further in Chapter 3, GaN transistors are able to switch very quickly
and, therefore, are very sensitive to inductances in either the power loop or the gate-source
loop. Wire bonds have a significant amount of inductance and limit the ultimate capability of
the GaN device. Wire bonding also increases the possibility for poor bonds, which can reduce
the reliability of the final product [25–29]. It is for this reason that the preferred method for
making electrical connection is by soldering directly to contacts on the device. A common
process for making these contacts that can be soldered is shown in Figure 1.18. The solder bars
can either be a Pb-Sn composition or a lead-free composition of Ag-Cu-Sn.
Following solder bar formation, the completed wafer looks like the example in Figure 1.19.
The individual devices are singulated, and the final transistor may look like the example in
Figure 1.20. This device is now ready to be soldered onto a printed circuit board (PCB) or onto
a lead frame to be incorporated into a plastic molded package.

###### 1.6 Summary

In this chapter, a new platform for making switching power transistors using gallium nitride
grownontopof a silicon substrate was introduced.Enhancement-modetransistorshave in-circuit
characteristics very similar to power MOSFETs, but with improved switching speed, lower onresistance, and at a smaller size than their silicon predecessors. These new capabilities, married
with a step forward in chip-scale, high-density packaging, enable power conversion designers to
reduce power losses, reduce system size, improve efficiency, and ultimately reduce system costs.
Chapter 2 will connect these basic physical properties of GaN transistors to the electrical
characteristics most important in designing power conversion systems. These electrical
characteristics will be compared to state-of-the-art silicon MOSFETs, in order to illustrate
both the strong similarities and the subtle differences. In Chapters 3–10, these same electrical


-----

**Metal 3** **Metal 3**


**Silicon Substrate**


(a)

(b)

(c)

(d)


**Silicon Substrate**


(e)

(f)

(g)


**Silicon Substrate**


**Silicon Substrate**


**Silicon Substrate**


**Figure 1.18** A typical process for creating solder bars on an enhancement-mode GaN HEMT (not to
scale). The basic process steps are as follows: (a) The finished wafer with openings in the passivation.
Metal layer 3 is partially exposed. (b) Photopolyimide is deposited and removed in the area where the
solder is desired. (c) An under-bump metal is deposited to create an interface between the aluminum top
metal and the solderable material. (d) Photoresist is used to define where the solder will be plated. (e)
Copper and solder are plated in the opening. (f) The photoresist is removed and the under-bump metal is
etched. (g) The solderable metal is reflowed to form elongated solder bars

characteristics will be related to circuit and system performance in such a way as to give the
designer the tools to get the maximum performance from GaN transistors.
Finally, in Chapter 11 we discuss the “why, when, and how” that GaN transistors will
displace MOSFETs. Included is a discussion of cost trajectories, reliability, and technology
directions for the years 2014 through 2020.
These are the early years of a great new technology.


**Silicon Substrate**


-----

![](GaN-transistors-power-conversion.pdf-33-0.png)

**Figure 1.19** A completed 150 mm diameter enhancement-mode GaN HEMT wafer

**Drain Contacts**

**Substrate**

**Gate**

**Source Contacts**

**Figure 1.20** A finished device with solder bars in land grid array (LGA). This device measures
approximately 4 mm × 1.6 mm


![](GaN-transistors-power-conversion.pdf-33-0.png)

-----

###### References

1. Sze, S.M. (1981) Physics of Semiconductor Devices, 2nd edn, John Wiley and Sons, Hoboken, NJ.
2. Baliga, B.J. (1996) Power Semiconductor Devices, PWS Publishing Company, Boston, MA, p. 373.
3. Mitani, E., Haematsu, H., Yokogawa, S. et al. “Mass production of high voltage GaAs and GaN devices,” CS
_Mantech Conference, Vancouver B.C., Canada, Apr. 24–27, 2006._
4. Mimura, T., Tokoyama, N., Kusakawa, H. et al. “GaAs MOSFET for low-power high-speed logic applications,”
_37th Device Research Conference, University of Colorado, Boulder, CO, 25–27 June 1979._
5. Khan, M.Asif, Kuznia, J.N., and Olson, D.T. High electron mobility transistor based on a GaN-AlxGa1�x;N
heterojunction. Applied Physics Letters, 65 (9), 1121–1123 29.
6. Bykhovski, A., Gelmont, B., and Shur, M. (1993) The influence of the strain induced electric field on the charge
distribution in GaNAlNGaN structure. Journal of Applied Physics, 74, 6734.
7. Yu, E., Sullivan, G., Asbeck, P. et al. (1997) Measurement of piezoelectrically induced charge in GaN/AlGaN
heterostructure field-effect transistors. Applied Physics Letters, 71, 2794.
8. Asbeck, P., Yu, E., Lau, S. et al. (1997) Piezoelectric charge densities in AlGaN/GaN HFETs. Electronics Letters,
**33, 1230.**
9. Liu, Q.Z. and Lau, S.S. (1998) A Review of the Metal-GaN contact technology. Solid-State Electronics,
**42 (5)**
10. Javorka, P., Alam, A., Wolter, M. et al. (2002) AlGaN/GaN HEMTs on (111) silicon substrates. IEEE Electron
_Device Letters, 23 (1)_
11. Liu, Q.Z., Yu, L.S., Lau, S.S. et al. (1997) Thermally stable PtSi Schottky contact on n-GaN. Applied Physics
_Letters, 70 (1)_
12. Kordos, P., Heidelberger, G., Bernát, J.̌ _et al. (2005) High-power SiO2/AlGaN/GaN metal-oxide-semiconductor_
heterostructure field-effect transistors. Applied Physics Letters, 87.
13. Lanford, W.B., Tanaka, T., Otoki, Y., and Adesida, I. (2005) Recessed-gate enhancement-mode GaN HEMT with
high threshold voltage. Electronics Letters, 41 (7)
14. Cai, Y., Zhou, Y., Lau, K.M., and Chen, K.J. (2006) Control of threshold voltage of AlGaN/GaN HEMTs by
fluoride-based plasma treatment: from depletion-mode to enhancement-mode. IEEE Transactions on Electron
_Devices, 53 (9)_
15. Davis, S., “Enhancement-mode GaN MOSFET Delivers Impressive Performance,” Power Electronics Technology
(March 2010)
16. Hu, X., Simin, G., Yang, J. et al. (2000) Enhancement-mode AIGaN/GaN HFET with selectively grown pn
junction gate. Electronics Letters, 36 (8)
17. Murphy, M., (10 Mar 2009) “Cascode circuit employing a depletion-mode,” GaN-based FET, US Patent No.
7,501,670 B2.
18. Huang, X., Liu, Z., Li, Q., and Lee, F.C. (2013) Evaluation and application of 600V GaN HEMT in cascode
structure,” Proceedings of the 28th Annual IEEE Applied Power Electronics Conference (APEC), Long Beach,
CA., March 2013.
19. Strite, S. and Morkoç, H. (1992) GaN, AlN, and InN: a review. Journal of Vacuum Science and Technology, B,
**10 (4)**
20. Nakamura, Shuji. (1991) GaN growth using GaN buffer layer. Japanese Journal of Applied Physics,
**30 (10A)**
21. Nakamura, S., Iwasa, N., Senoh, M., and Mukai, T. (1992) Hole compensation mechanism of p-type GaN films.
_Journal of Applied Physics, 31, 1258._
22. Amano, H., Sawaki, N., Akasaki, I., and Toyoda, Y. (1986) Metalorganic vapor phase epitaxial growth of a high
quality GaN film using an AlN buffer layer. Applied Physics Letters, 48, 353.
23. Hughes, W.C., Rowland, W.H. Jr., Johnson, M.A.L. et al. (1995) Molecular beam epitaxy growth and properties of
GaN films on GaN/SiC substrates. Journal of Vacuum Science and Technology, B, 13 (4)
24. Lidow, A., Beach, R., Nakata, A. et al. (26 March 2013) “Enhancement Mode GaN HEMT Device
and Method for Fabricating the Same,” U.S. Patent 8,404,508.
25. Lidow, A., Beach, R., Nakata, A. et al. (8 Jan. 2013) Compensated Gate MOSFET and Method for Fabricating the
Same,” U.S. Patent No. 8,350,294.
26. Lidow, A., Strydom, J., de Rooij, M., and Ma, Y. (2012) GaN Transistors for Efficient Power Conversion, 1st edn,
Power Conversion Press, El Segundo, p. 9.


-----

27. Harman, G. (2010) Wire Bonding in Microelectronics, 3rd edn, McGraw-Hill Companies Inc., New York.
28. Coucoulas, A. (1970) Compliant bonding,” Proceedings 1970 IEEE 20th Electronic Components Conference,
Washington, D.C. pp. 380–389.
29. Heleine, T.L., Murcko, R.M., and Wang, S.C. (1991) A wire bond reliability model,” Proceedings of the 41st
Electronic Components and Technology Conference, Atlanta, GA, 1991.


-----

# 2

#### GaN Transistor Electrical Characteristics

###### 2.1 Introduction

In this chapter, the basic physical properties of GaN transistors discussed in Chapter 1 will be
connected to electrical characteristics that are important when developing power conversion
circuits and systems. These electrical characteristics will be compared to state-of-the-art silicon
power MOSFETs in order to explore both their similarities and their differences. Understanding these similarities and differences is fundamental to understanding the extent to which
existing power conversion systems can be improved by GaN-based technologies.

###### 2.2 Key Device Parameters

The key operating parameters should give the designer most of the information necessary to
design a system with predictable results. For a power-switching transistor, the most basic
parameters are: breakdown voltage between source and drain electrodes (BVDSS), on-resistance (RDS(on)), and threshold voltage (VGS(th)). These three characteristics are enough to get a
device to function in a circuit. In order to understand how this device will work when switched
on and off, capacitances and reverse-conduction characteristics need to be added. Also, the
amount of heat that can be extracted from a device is necessary for developing a full
understanding of device and circuit performance. How all of these basic parameters vary
over all the operating conditions of a power conversion system is the subject of this chapter.

###### 2.2.1 Breakdown Voltage (BVDSS) and Leakage Current (IDSS)

The breakdown voltage between the source and drain terminals of a GaN HEMT is determined
by several factors [1] including: the fundamental ECrit of GaN discussed in Chapter 1; the specific
designofthedevice;thespecificsoftheheterostructure;theinternalinsulatinglayersinthedevice
structure above the gate, source, and drain electrodes; and the underlying substrate material
properties. A semiconductor transistor will break down and conduct current (or potentially
destroy itself) when the critical electric field of any of the constituent materials is exceeded.

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

(a)


(b)


**Figure 2.1** An illustration of (a) a basic enhancement-mode GaN transistor with reverse bias applied,
and (b) a depletion-mode transistor with the gate turned off and reverse bias applied

To visualize these electric fields in an HEMT transistor, a good starting point is the structure
illustrated in Figure 2.1. Applied from drain to source is a voltage such that the transistor is
reverse biased. In an enhancement-mode transistor, the transistor is turned off by shorting the
gate to the source. In a depletion-mode device, there would need to be a negative bias from the
gate to source electrodes to keep the HEMT from conducting current.
A simple two-dimensional analysis of the structure in Figure 2.1(a), shown in Figure 2.2,
illustrates the electric fields at any point in the device. Higher electric fields, where the contour
lines are closest together, develop near the drain and gate electrodes. When these fields, at any
location in the device structure, exceed ECrit, the device will break down and conduct current.
Breakdown can also occur between the metal busing layers in the device. For example,
Figure 1.17 showed an enhancement-mode HEMT with three levels of metal used to
consolidate drain current and source current and bring them to the outside of the device
where they can be connected into a circuit. When the device is reverse biased, sometimes called
the “blocking state,” one of these layers may be connected to the source potential while an
adjacent layer – or perhaps a higher or lower layer in the stack – might be at drain potential. If
the ECrit of the dielectric material separating these two layers is exceeded, breakdown will
occur. This can be prevented by either increasing the separation of the layers, or by switching to
an insulating layer with a higher ECrit.

**Source**
**Drain**
**Gate**

**Figure 2.2** The device in Figure 2.1(a) showing the electric fields when voltage is applied from drain to
source


![](GaN-transistors-power-conversion.pdf-37-0.png)

**Source**
**Drain**
**Gate**


-----

If a HEMT device goes into breakdown, either from exceeding the ECrit of the GaN or of an
insulating layer, the effect tends to be destructive. In the case where the insulating layers exceed
their capacity for blocking voltage, a physical rupture of the dielectric material will develop.
The closer the electric field approaches to ECrit (insulator), the sooner the rupture will occur. This
effect is called “time-dependent dielectric failure” and is discussed extensively in the
literature [2]. When the GaN layer exceeds ECrit (GaN), a different mechanism causes device
failure. When breakdown occurs in the GaN or Al GaN regions, the electrons generated can
destroy the 2DEG, causing the device on-resistance to increase greatly [3].
When a transistor of any kind is in the blocking state, there is still a small amount of “leakage
current” (IDSS) that will flow between terminals. In the case of an HEMT device, the leakage
current can flow from the drain to the source electrodes, from the drain to the gate electrodes, or
from the drain to the substrate. The sum of these three leakage currents will be the total IDSS
measured between drain and source in a circuit.
These three components of leakage current are shown in Figure 2.3 and are measured on an
enhancement-mode HEMT with a breakdown voltage above 700 V. In this example, the
substrate material is silicon (Si) and is connected to source potential. The current has been
normalized to a 1 mm-wide gate structure.
When designing a power conversion system, IDSS can become a significant source of power
loss. For example, if a 100 V device has 100 μA IDSS leakage current, the overall power
dissipation due to the leakage current would be 10 mW. In certain applications requiring very
low standby power, this amount of loss could become unacceptable.
The drain-to-source leakage current (IDSS) also varies with temperature. Figure 2.4 shows a
family of curves from a sample of enhancement-mode transistors with 1 meter gate width,
showing leakage current measured at various temperatures. Figure 2.4(a) traces an individual
device at various temperatures as a function of VDS. Figure 2.4(b) compares leakage current
measurements of six different devices of the same part type plotted against the inverse
temperature to illustrate device-to-device variation. Despite the fact that these devices were


1.E-03

1.E-04

1.E-05

1.E-06

1.E-07

1.E-08

1.E-09

1.E-10

1.E-11


0 100 200 300 400 500 600 700 800


**Bias Voltage (V)**

**Figure 2.3** There are three main sources of current that add up to the total leakage current between drain
and source terminals; drain-gate leakage, drain-source leakage, and drain-substrate leakage


-----

1.E-03

1.E-04


1.E-03

1.E-04


1.E-07

2.2 2.45 2.7 2.95 3.2 3.45

**1000/T (Kelvin)**


1.E-05

1.E-06


1.E-07

1.E-08

0 50 100 150


25C

50C

75C

100C

125C

150C


1.E-05

1.E-06


Device 1

Device 2

Device 3

Device 4

Device 5

Device 6


**VDS (V)**


(a) (b)

**Figure 2.4** IDSS over temperature for an EPC2001 enhancement-mode GaN transistor: (a) IDSS vs.
temperature for an individual device, and (b) IDSS (Measured at VDS = 50 V) for six different devices
showing device-to-device variation


selected to cover a wide range of drain-to-source leakage current, the slope of these
measurements for each device gives a consistent activation energy of EA = �0.4 eV. The
activation energy for this commercial device lies between values reported in the literature of
0.2 eV due to surface related traps [4,5], and 0.99 eV due to a temperature-assisted tunneling
� �
mechanism [4].
Typically, commercial transistors are described using a datasheet. These datasheets vary
from supplier to supplier and do not always follow consistent conventions for measurements
leading to the numbers listed in the data sheet tables. For BVDSS and IDSS, there are several
relevant sections of a datasheet that can be analyzed to deduce device behavior and compare
parts from different manufacturers.
In Tables 2.1 and 2.2 are examples of data from two different manufacturers of GaN
transistors, Efficient Power Conversion Corporation (EPC) and Transphorm. Table 2.1 gives
the specifications for an enhancement-mode transistor from EPC with a nominal maximum
drain-source voltage (VDS) of 100 V, and Table 2.2 shows the corresponding specifications for
a cascode-configured GaN transistor from Transphorm with a nominal maximum VDS of

**Table2.1** Data fromanEfficient Power Conversion EPC2001datasheet showingsections relating toIDSS
and BVDSS [6]


Maximum Ratings

VDS Drain-to-source voltage (continuous) 100 V
Drain-to-source voltage (up to 10,000 5 ms pulses at 125 °C) 120 V


Parameter Test Conditions Min Typical Max Unit

Static Characteristics (Tj = 25 °C, unless otherwise stated)
BVDSS Drain-to-source voltage VGS = 0 V, ID = 300 μA 100 — — V
IDSS Drain source leakage VDS = 80 V, VGS = 0 V — 100 250 μA


-----

**Table 2.2** Data from a Transphorm cascode TPH3006PD datasheet showing sections relating to IDSS
and BVDSS [7]

Symbol Parameter Limit Value Unit

Absolute maximum ratings (TC = 25 °C unless otherwise stated)
VDSS Drain-to-source voltage 600 V
VTDS Transient drain-to-source voltage[a] 750 V

Symbol Parameter Min Typical Max Unit Test Conditions

Static Characteristics (TC = 25 °C, unless otherwise stated)
IDSS Drain-to-source leakage — 2.5 90 μA VDS = 600 V, VGS = 0 V,
current, TJ = 25°C TJ = 25 °C
IDSS Drain-to-source leakage — 20 — μA VDS = 600 V, VGS = 0 V,
current, TJ = 150 °C TJ = 150 °C

_a For 1 μsec, duty cycle D = 0.1._

600 V. In both cases, there is also a specification for a transient voltage capability above the
maximum VDS. This transient capability means that, for short periods of time, the devices can
withstand higher voltages than their respective rated maximums. This type of rating is a sign of
the relative immaturity of the technology. In the case of a mature 100 V Si MOSFET shown in
Table 2.3, there are no transient over-voltage ratings. Instead, an avalanche capability is
specified, giving the user license to take the device into full drain-source breakdown with a
certain amount of energy (specified in millijoules). Whereas MOSFET users rarely take
advantage of this avalanche capability, over time, and with improved device design, GaN
transistors will also mature to the point where they can be used in avalanche without
catastrophic failure.
Tables 2.1 and 2.2 also list the static (DC) IDSS characteristics for their respective devices.
In each case, the test conditions are slightly different. The EPC2001 gives the IDSS at 80 V and
the ID at BVDSS, both at 25 °C, whereas the TPH3006PD lists the IDSS at maximum VDS at both

**Table 2.3** Data from an Infineon BSC060N10NS3 G datasheet for an Si MOSFET showing sections
relating to IDSS and BVDSS and avalanche energy [8]

Parameter Symbol Test Conditons Value Unit

Maximum Ratings (TJ = 25 °C, unless otherwise specified)
Avalanche energy, single EAS ID = 50 A, RGS = 25 Ω 230 mJ
pulse

Static Characteristics
Drain-source breakdown V(BR)DSS VGS = 0 V, ID = 1 mA 100 — — V
voltage

Zero gate voltage drain IDSS VDS = 100 V, VGS = 0 V, — 0.01 1 μA
current TJ = 25 °C

VDS = 100 V, VGS = 0 V, — 10 100 μA
TJ = 125 °C


-----

**Components of RDS(on)**

**Source Metal** **Drain Metal**

**Gate**

**RC** **AlGaN Barrier** **RC**

**R2DEG (Gate)** **GaN** **R2DEG**

**Figure 2.5** Cross section of a GaN HEMT, showing the major components of RDS(on)

25 °C and 150 °C. The silicon MOSFET, BSC060N10NS3G from Infineon, has specifications
for BVDSS and IDSS under yet a third set of test conditions.

###### 2.2.2 On-Resistance (RDS(on))

The on-resistance of a transistor is the sum of all the resistance elements that make up the device.
Figure 2.5 shows the major elements that contribute to the RDS(on) of the device. The source and
drain metals have to connect to the 2DEG through the AlGaN barrier. This component of
resistance is called the contact resistance (RC). Electrons then flow in the 2DEG with a resistance
R2DEG. This resistance is determined by the mobility of the electrons (μ2DEG), the number of
electrons created by the 2DEG (N2DEG), the distance the electrons have to travel (L2DEG), the
width of the 2DEG (W2DEG), and the universal charge constant, q (1.6  10[�][19] coulombs). This
resistance can be described by the following formula [9]:

R2DEG  L2DEG/(q  μ2DEG  N2DEG  W2DEG) (2.1)

As discussed in Chapter 1, the number of electrons in the 2DEG will depend on the amount
of strain induced by the AlGaN barrier. However, under the gate electrode, this 2DEG could
have a lower concentration than in the region between the gate and drain electrodes. This
electron concentration depends on the type of gate (recessed gate, MOS, Schottky, or pGaN),
the particular process used, and the heterostructure deployed. It also depends on the voltage
applied to the gate. A fully enhanced gate will have a higher electron concentration than a
partially enhanced gate. A good approximation of the resistance of the transistor shown in
Figure 2.5 can then be calculated as follows:

RHEMT  2  RC  R2DEG  R2DEG(Gate) (2.2)

Additional parasitic resistance (Rparasitic) can come in the form of metal resistance from the
multiple metal buses that conduct the current from the individual source and drain electrodes
to the terminals of the transistor. In the case of a cascode device, the resistance of the external
Si MOSFET would also need to be added to the total resistance of the transistor.
In a power conversion circuit, the conduction losses of the transistor are quite significant and
therefore the device is typically used either fully turned on, or fully turned off. For this reason, a


-----

key parameter for specifying any power transistor is the on-resistance, RDS(on), and can be
defined as:

RDS(on)  RHEMT(Fully Enhanced)  Rparasitic (2.3)


Each of these components of RDS(on) will vary with temperature. The metal layers typically
are made of combinations of copper and aluminum and have resistivity temperature
coefficients in the range of 3.8 10[�][3]/°C [10] for copper, to 3.9 10[�][3]/°C [11] for aluminum.
 
In contrast, a 2DEG’s resistivity temperature coefficient is significantly higher in the range
of 1.310[�][2]/°C [12,13], and the contact resistance, RC, has a temperature coefficient in
the range of 4.710[�][3]/°C [12]. The transistor’s RDS(on), as a function of temperature, would
be expected to be somewhere in between these numbers and can be approximated as:

RDS(on)(t)  Rparasitic(t)  (2 ? RC(t))  (R2DEG  R2DEG(Gate))(t) (2.4)


The final temperature variation of RDS(on) will depend on the design of the device: how much
of the RDS(on) comes from 2DEG, contact resistance, or parasitic metal resistance. Devices in
commercial use, however, demonstrate a variation of RDS(on) with temperature that is
somewhat less than silicon MOSFETs as shown in Figure 2.9. The 100 V-rated enhancement-mode GaN HEMT in this example has a temperature coefficient of approximately
6.5 10[�][3]/°C compared with the Si MOSFET’s temperature coefficient of 20 10[�][3]/°C. For
 
devices designed for higher BVDSS, the 2DEG will be a greater fraction of the total RDS(on)
and, since the temperature coefficient of the 2DEG is higher than that of the parasitic elements
and the contact resistance, the temperature coefficient will be higher (see Figure 2.6).

2.2
2.1
2
1.9
1.8
1.7
1.6
1.5
1.4
1.3
1.2
1.1
1
0.9 GaN FET
0.8 MOSFET B
0.7
0.6

–50 –25 0 25 50 75 100 125 150

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
||||||||Ga|N FET||
|||||||MO|MO|SFET B||
|||||||||||


**Junction Temperature (ºC)**

**Figure 2.6** Normalized RDS(on) vs. temperature for a 100 V enhancement-mode GaN transistor
(EPC2001) compared with an Si power MOSFET with similar ratings [6,8]


-----

20

18

16

14

12

10

8

6

4

2


**RDS(on) vs. VGS for Various Current** **RDS(on) vs. VGS for Various Temperature**

20

ID = 10 A 25°C
ID = 20 A 125°C
ID = 40 A
ID = 80 A 15 ID = 25 A


10

5


0
2 2.5 3 3.5 4 4.5 5 5.5


0
2 2.5 3 3.5 4 4.5 5 5.5

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|||||||ID ID|= 10 A = 20 A||
|||||||ID ID|= 40 A = 80 A||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||

|Col1|Col2|Col3|Col4|Col5|ID|Col7|25°C 125°C = 25 A|
|---|---|---|---|---|---|---|---|
||||||||25°C 125°C|
|||||||ID|= 25 A|
|||||||||
|||||||||
|||||||||


**VGS – Gate-to-Source Voltage (V)** **VGS – Gate-to-Source Voltage (V)**

(a) (b)

**Figure 2.7** Two graphs of the RDS(on) of an enhancement-mode GaN HEMT (EPC2001) as a function of
gate voltage for various drain currents (a) and at various temperatures (b) [6]


Equation 2.2 breaks down the resistance of the 2DEG into two components, the 2DEG
between the drain and gate and the 2DEG under the gate. The resistance of the 2DEG under the
gate changes from a very high value when the device is in the off state, to a very low value when
the device is in the on-state. This transition depends on the specific design of the gate and has a
significant impact on device performance in a switching circuit.
In Figure 2.7 is a graph of the RDS(on) of an enhancement-mode GaN HEMT as a
function of gate-to-source voltage for various drain currents (ID) and at various temperatures.
In this example, the resistance of the gate 2DEG rapidly decreases until it is fully enhanced
at about VGS = 4 V. Beyond that voltage there is only a nominal decrease in overall device
RDS(on).
The datasheets for enhancement-mode GaN HEMT devices typically specify this onresistance with a fully enhanced gate and at the maximum rated DC current. Table 2.4 gives
data from a datasheet for a 100 V-rated enhancement-mode transistor specifying a maximum
RDS(on) of 7 mΩ with 5 V on the gate at 25 °C. Table 2.5 gives data from a datasheet for a 600 Vrated cascode transistor specifying a maximum RDS(on) of 180 mΩ at 25 °C. Also indicated in
this datasheet is the typical RDS(on) of 330 mΩ at 175 °C. Both measurements are with 8 V on
the gate.

###### 2.2.3 Threshold Voltage (VGS(th) or Vth)


For a power device, the threshold voltage is the voltage required to be applied to the gate-tosource to begin conducting current in the device. In other words, the threshold voltage defines

**Table 2.4** Data from an Efficient Power Conversion EPC2001 datasheet showing the section relating
to RDS(on) [6]


Parameter Test Conditions Min Typ Max Unit

Static Characteristics (TJ = 25 °C, unless otherwise stated)
RDS(on) Drain-source On-Resistance VGS = 5 V, ID = 25 A — 5.6 7 mΩ


-----

**Table 2.5** Data from a Transphorm cascode TPH3006PD datasheet showing the section relating
to RDS(on) [7]

Symbol Parameter Min Typical Max Unit Test Conditions

Electrical Characteristics (TC = 25 °C, unless otherwise stated)
Static
RDS(on) Drain-source On-Resistance — 0.15 0.18 Ω VGS = 8 V, ID = 11 A,
TJ = 25 °C TJ = 25 °C
RDS(on) Drain-source On-Resistance — 0.33 — Ω VGS = 8 V, ID = 11 A,
TJ = 175 °C TJ = 175 °C

the voltage below which the device is off. An enhancement-mode or cascode device has a
positive threshold voltage, and a depletion-mode device has a negative threshold voltage.
For a GaN power device, the threshold voltage is when the 2DEG underneath the gate is fully
depleted by the voltage generated by the gate electrode [14]. This occurs when the voltage of
the gate balances the voltage generated by the piezoelectric strain in the AlGaN/GaN barrier.
This voltage has two components, the voltage applied externally to the gate (defined as Vth),
plus the built-in voltage due to the specifics of the gate metallurgy. In the case of a Schottky
gate device, this built-in voltage is the Schottky barrier height [15] of the gate metal on top
of the AlGaN barrier. In the case of a MOS HEMT device, it is the voltage generated by the
gate metal across the insulator as well as the AlGaN barrier. In the case of a pGaN gate, it is
the voltage generated by the built-in field caused by a p-type semiconductor material next to an
n-type material.
Because the strain in the AlGaN barrier is relatively constant with temperature, as are the
voltages generated by the internal metallurgy, the threshold voltage in a GaN HEMT is
relatively constant with temperature as shown in Figure 2.8. The threshold voltage of a cascode
device, however, would track the change in threshold of the Si MOSFET in series with the GaN
d-mode HEMT, and will decline with increasing temperature.
Table 2.6 shows data from the datasheet of a 100 V-rated enhancement-mode GaN HEMT.
The typical value of 1.4 V is measured at 5 mA, a small amount of current compared with the
25 A DC rating for this same transistor.
Table 2.7 presents data from a 600 V-rated cascode transistor. In this case the Vth is specified
at 1 mA, which is a small value compared with the 17 A DC rating. No information is given on
the change of this device’s threshold voltage as a function of temperature. Figure 2.9, however,
shows a graph of the threshold voltage versus temperature for a 100 V Infineon
BSC060N10NS3 [8] power MOSFET. The Vth for this silicon device drops about 38%
from about 2.75 V to about 2 V, when temperature changes from 25 °C to 125 °C compared
with a nominal 3% increase in the enhancement-mode GaN transistor.

###### 2.3 Capacitance and Charge

A transistor’s capacitance is a significant factor in determining the energy that will be lost in the
device during a transition from the on-state to the off-state, or vice versa. The capacitance (C)
determines the amount of charge (Q) that needs to be supplied to various terminals of the device
to change the voltage across those terminals (Q = C V). The faster this charge is supplied, the

faster the device will change voltage.


-----

1.2


1.15

1.1


1.05

1


0.95

0.9


0.85

0.8

–20 0 20 40 60 80 100 120

|I = 3 D|Col2|mA|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||I = 3 D|mA|||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||


**TJ – Junction Temperature (°C )**

**Figure 2.8** EPC2010 normalized threshold voltage vs. temperature showing only a 3% change over the
normal operating range of this device


**Table 2.6** Data from an Efficient Power Conversion EPC2001 datasheet showing the section relating
to Vth [6]

Parameter Test Conditions Min Typ Max Unit


Static Characteristics (TJ = 25 °C, unless otherwise stated)
VGS(th) Gate threshold voltage VDS = VGS, ID = 5 mA 0.7 1.4 2.5 V

**Table 2.7** Data from a Transphorm cascode TPH3006PD datasheet showing the section relating to Vth [7]


Symbol Parameter Min Typical Max Unit Test Conditions

Electrical Characteristics (TC = 25 °C, unless otherwise stated)
VGS(th) Gate threshold voltage 1.35 1.8 2.35 V VDS = VGS, ID = 1 mA


There are three main elements of capacitance related to a FET: (1) gate-to-source capacitance
(CGS), (2) gate-to-drain capacitance (CGD), and (3) drain-to-source capacitance (CDS). Figure 2.10 illustrates the physical origin of each of these capacitances. Occasionally designers
need to look just at the total capacitance seen at either the input terminals (CISS = CGD + CGS),
or output terminals (COSS = CGD + CDS).
These capacitances are a function of the voltage applied to various terminals. Figure 2.11
shows how the values change for an enhancement-mode HEMT, as the voltage from drain-tosource increases. The reason for the drop in capacitance as VDS increases is that the free
electrons in the GaN are depleted. For example, the initial step down in COSS is caused by the
depletion of the 2DEG near the surface. Higher VDS values extend the depletion region laterally


-----

4


3.5

3


2.5

2


1.5

1


0.5

0
–60 –20 20 60 100 140 180

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||
|||||||||||||
|||||||||||||
|||||||900|μA|||||
|||||||||||||
|||||90 μ|A|||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||


Tj (ºC)

**Figure 2.9** Data from an Infineon BSC060N10NS3 G datasheet showing the change in Vth vs.
temperature [8]


from the field plate edge to the drain, further depleting the 2DEG and eliminating its capacitive
component.
The result of integrating the capacitance between two terminals across the range of voltage
applied to the same terminals is the amount of charge (Q) that is stored in the capacitor. Since
current-integrated-over-time equals charge, it is often very convenient to look at the amount
of charge necessary to change the voltage across various terminals in the GaN HEMT.
Figure 2.12 shows the amount of gate charge, QG, that must be supplied to increase the
voltage from gate-to-source to the desired voltage. QG is the integrated value of CISS from
the starting voltage on the gate to the ending voltage. Referring to Figure 2.12, it can be seen
that about 5 nC is needed to achieve 5 V on the gate, a value that will ensure that the device is

**CGD**


**GaN** **D**

**Figure 2.10** Schematic of GaN transistor capacitive sources

|C GS S G|Col2|C DS|Col4|
|---|---|---|---|
|||||


-----

1

0.8


0.6

0.4


0.2

0

|Col1|Col2|Col3|Col4|C = C GD+ C OSS SD C = C GD+ C ISS GS|
|---|---|---|---|---|
|||||C = C GD+ C OSS SD C = C GD+ C ISS GS|
|||||C = C RSS GD|
||||||
||||||
||||||
||||||


0 50 100 150 200


**VDS – Drain-to-Source Voltage (V)**

**Figure 2.11** EPC2010 capacitance vs. drain-source voltage [16]


fully turned on. If the gate drive is capable of supplying 1 A of current, it will take about 5 ns
to achieve this voltage.
The QGD and QGS are also specified separately because they impact the voltage- and currentswitching transition speeds, respectively. Also, the ratio of these two values, QGD/QGS, called
the Miller ratio, is often an important metric to determine the point at which a device might turn
on due to a voltage transient applied across the drain and source. The Miller ratio will be
discussed in greater detail in Chapter 3.

5


4

3


2

1


0
0 1 2 3 4 5 6

**QG – Gate Charge (nC)**

|I = 12 A D V = 100 D|Col2|V|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||I = 12 A D V = 100 D|V|||||
||||||||
||||||||
||||||||
||||||||


**Figure 2.12** EPC2010 gate charge vs. gate voltage [16]


-----

**Table 2.8** Data from an Efficient Power Conversion EPC2001 datasheet showing the section relating to
capacitance and charge [6]

Parameter Test Conditions Min Typ Max Unit

Dynamic Characteristics (TJ = 25 °C, unless otherwise stated)
CISS Input capacitance VDS = 50 V, VGS = 0 V 850 950 pF
C0SS Output capacitance 450 525
CRSS Reverse transfer capacitance 20 30
QG Total gate charge (VGS = 5 V) VDS = 50 V, ID = 25 A 8 10 nC
QGD Gate-to-drain charge 2.2 2.7
QGS Gate-to-source charge 2.3 2.8
Q0SS Output charge VDS = 50 V, VGS = 0 V 35 40

The capacitances and charges for an enhancement-mode GaN HEMT are shown in Table 2.8.
The gate-to-drain charge, and its corresponding capacitance CRSS (or CGD), will change with
drain-to-source voltage. In this example, the values are given at 50 V, which is half the rated
BVDSS. This convention is used because, historically, the operating point for transistors in
power conversion designs was about half the maximum rated voltage to provide safety margins
for overshoot caused during switching transients.

###### 2.4 Reverse Conduction

VSD is the voltage drop across the device when voltage is applied from source-to-drain.
This is the reverse direction from the normal forward FET conduction. In an Si MOSFET,
there is a p-n junction that forms a diode from the body of the channel to the drain of the
transistor. It is, therefore, called a body-drain diode. As discussed in Chapter 1, enhancement-mode GaN HEMT transistors do not have a p-n diode, but they do conduct in a way
similar to a diode in the reverse direction. Figure 2.13 shows how this “body diode” forward
voltage drop varies with source-drain current. It should be noted that, because this body
diode is formed by turning on the 2DEG in the reverse direction using the drain-gate voltage
to enhance the channel, if the gate voltage is lowered below 0 V, the forward drop will
increase proportionately. For example, if the gate drive of a circuit turns off the GaN HEMT
by applying a negative 1 V to the gate, the VSD at 0.5 A will be 2.8 V instead of 1.8 V
with 0 VGS.
Because the reverse conduction in a GaN transistor is due to the turning on of the 2DEG, the
forward voltage drop will change with temperature in much the same way as the RDS(on)
changes with temperature in forward conduction. In an Si MOSFET, the reverse conduction is
due to a p-n junction diode. Contrary to a GaN HEMT, the diode forward drop goes down with
temperature in the Si MOSFET.
The voltage drop across an enhancement-mode GaN HEMT rated at 100 V when conducting
in the reverse direction is shown in Table 2.9 [6].
For a cascode device, the reverse-conduction mechanism is somewhat different. The body
diode of the Si MOSFET is conducting in series with the depletion-mode HEMT. The voltage
across the MOSFET body diode helps to further enhance the depletion-mode HEMT, but the
channel of the HEMT is now in series with the Si diode, and the voltage drop is the sum of the
two. The reverse conduction is therefore a combination of the MOSFET diode and a depletion

-----

60

50


40

30


20

10


0
0 0.5 1 1.5 2 2.5 3 3.5 4 4.5

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||25°C 125°C||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||


**VSD – Source-to-Drain Voltage (V)**

**Figure 2.13** EPC2010 body-diode forward drop vs. source-drain current and temperature [16]


**Table2.9** ExcerptfromanEfficientPowerConversionEPC2001datasheetshowingthesectionrelatingto
the voltage drop when the transistor is conducting in the reverse direction [6]

Parameter Min Typical Max Unit Test Conditions


Electrical Characteristics (TC = 25 °C, unless otherwise stated)
VSD Source-drain forward — 1.75 — V IS = 0.5 A, VGS = 0 V, T = 25 °C
voltage — 1.8 — V IS = 0.5A, VGS = 0V, T = 125 °C

mode GaN HEMT, and could have either a positive or negative temperature coefficient to the
VSD depending on the specifics of the cascode design.
There is one other charge element, QRR, which does not directly relate to a device
capacitance in an enhancement-mode GaN HEMT. This is the amount of charge dissipated
when a body diode is turned off. This charge comes from the minority carriers left over during
diode conduction in a MOSFET. Because there are no minority carriers involved in conduction
in an enhancement-mode GaN HEMT, there are no reverse recovery losses. Therefore, QRR is
zero, which is a significant advantage compared with power MOSFETs, and will be discussed
in greater detail in Chapters 3 and 6.
A cascode transistor, however, does have the stored charge that has to be swept out of the
MOSFET before the diode from the series-connected Si MOSFET turns off, as shown in
Table 2.10. Because the cascode MOSFET is a low-voltage device, the amount of stored charge
is small compared to a comparable 600 V MOSFET. To illustrate this difference, Table 2.11
gives data from an Infineon 650 V CoolMOS[TM] datasheet [17]. This CoolMOS[TM] MOSFET
has a maximum RDS(on) of 130 mΩ. In comparison, the Transphorm cascode device has a
maximum RDS(on) of 180 mΩ – about 50% higher. Nevertheless, the MOSFET has a stored
charge, Qrr, that is more than 100 times greater than the cascode GaN transistor.


-----

**Table 2.10** Data from a Transphorm cascode TPH3006PD datasheet showing the section relating to
conduction in the reverse direction [7]

Symbol Parameter Min Typical Max Unit Test Conditions

Electrical Characteristics (TC = 25 °C, unless otherwise stated)
Reverse Operation
IS Reverse current — — 11 A VGS = 0 V, TJ = 100 °C
VSD Reverse voltage — 3.8 4.7 V VGS = 0 V, IS = 11 A, TJ = 25 °C
VSD Reverse voltage — 2.3 2.6 V VGS = 0 V, IS = 5.5 A, TJ = 25 °C
trr Reverse recovery — 30 — ns IS = 11 A, VDD = 480 V, di/dt =
time 450 A/μs, TJ = 25 °C
Qrr Reverse recovery — 54 — nC
charge

**Table2.11** DatafromanInfineon650 VCoolMOS[TM]datasheetshowingthesectionrelatingtoconduction
in the reverse direction [17]

Parameter Symbol Values Unit Note/Test Conditions

Min Typical Max

Diode forward voltage VSD — 0.8 — V VGS = 0 V, IF = 44 A,
TJ = 25 °C
Reverse recovery time trr — 630 — ns VR = 400 V, IF = 15 A,
diF/dt = 55 A/μs
Reverse recovery charge Qrr — 6.4 — μC VR = 400 V, IF = 15 A,
diF/dt = 55 A/μs
Peak reverse recovery Irrm — 20 — A VR = 400 V, IF = 15 A,
current diF/dt = 55 A/μs

###### 2.5 Thermal Resistance

The power consumed in a device during operation is dissipated in the form of heat. It is
therefore important to understand the ability of a device to transfer the heat to the surrounding
environment. Devices interface to their environment through a variety of packaged and
“package-less” formats, but the specifications for the transfer of heat have two of the same
component elements: junction-to-case thermal resistance (RθJC) and junction-to-ambient
thermal resistance (RθJA). In the case of a double-sided device that can be cooled from the
top and the bottom surfaces, a third parameter, junction-to-board (RθJB), needs to be added to
the list.
Figure 2.14 illustrates the first of these two thermal resistance parameters for a conventional
single-sided device. In a single-sided device, the transistor is mounted onto a copper leadframe.
This leadframe can be connected to a larger heatsink using thermal interface material, such as
thermal grease, to improve the interface contact efficiency if the surfaces are not perfectly flat.
The RθJC for this configuration would be the thermal resistance from the top die surface in
contact with the leadframe through the copper leadframe or “case” – the larger the area of the


-----

Solder

**Active Device**

Thermal Interface

**Copper Leadframe** Material

###### Heatsink

**Ambient**

**Figure 2.14** Cross section of a transistor mounted in a typical package including a copper leadframe or
“case”

transistor, the lower this resistance. The thicker the substrate or the case, the longer the thermal
path to the heatsink, and the higher RθJC will become. The heat flux then has to be transferred
into the environment. The parameter that describes this is RθJA, which includes the junction-tocase resistance and makes an assumption about the area of the back surface that is exposed to
the ambient environment.
Figure 2.15 gives a simple schematic model describing the thermal resistance in steady state
for the structure shown in Figure 2.14. The figure shows the thermal resistance broken down by
location in the structure starting from the junction to the bottom of the leadframe (RθJC), the
thermal resistance through the thermal interface material (RθTIM), and the thermal resistance
from the interface with the heatsink to the ambient (RθSA). The sum of these three is the thermal
resistance from the junction to the ambient (RθJA).
Table 2.10 shows data from a previously cited MOSFET datasheet (BSC060N10NS3G).
In this example, there are two values given for RθJA: the first value is for the resistance of the
back surface of the package radiating into the environment without an added heatsink, and
the second value makes the assumption there is a 6 cm[2] cooling layer of 70 μm thick copper
embedded in an FR4 printed circuit board (PCB) acting as the heatsink.

RΘJA

RΘJC RΘTIM RΘSA

Power Ambient


Heatsink
Temp
(TS)


Ambient
Temp
(TA)


Junction
Temp
(TJ)


Case
Temp
(TC)


**Figure 2.15** Steady-state thermal resistance schematic model for the physical device structure given in
Figure 2.14


-----

**RΘJA** **Silicon Substrate** **RΘJA**

**RΘJC**

**Active GaN Device Region**

**RΘJA** **Solder Bars** **RΘJB** **RΘJA**

**Copper Traces**

**RΘJA**

**Printed Circuit Board**

**Figure 2.16** Side view of a LGA device mounted to a printed circuit board illustrating the three basic
components of thermal resistance

Figure 2.16 illustrates all three thermal parameters in the case of the land grid array (LGA)
format device first shown in Figure 1.20 of Chapter 1. In this example, the HEMT is
mounted with the active transistor facing the PCB and separated by the solder bars that form
the device terminals. RθJC is still defined as the resistance from the active surface of the die to
the case. For a GaN HEMT in an LGA format, the case is the surface of the bare Si substrate
(facing upwards in this illustration). The new thermal parameter, RθJB, is the thermal
resistance from the active surface of the transistor, through the solder bars to the copper
traces on the PCB. The third thermal parameter, RθJA is the thermal resistance standardized
to a specific PCB area (typically one square inch) with no heatsink, and gives an estimate of
the overall thermal resistance between junction and ambient for this case. This differs from
RθJB, as it also includes the specific PCB-to-ambient thermal resistance, RθBA, in series, as
well as some direct case-to-ambient thermal resistance, RθCA, due to radiation and
convection.
The data in Tables 2.12 and 2.13 show that the resistance between the junction and the
ambient, RθJA, is the largest resistor and could therefore limit the amount of heat the device
can dissipate. For this reason, it is common to add a heatsink to the device to facilitate heat
removal. Figure 2.17 shows an assembly of two GaN HEMT devices with the addition of a
heatsink and thermal interface material. The overall system thermal resistance is now the

**Table 2.12** Data from an Infineon BSC060N10NS3 G datasheet for an Si MOSFET showing sections
relating to steady state thermal resistance [8]

Parameter Symbol Test Conditions Values Unit

Min Typical Max

Thermal Characteristics
Thermal resistance, junction-case RθJC — — — 1 K/W
Thermal resistance, junction-ambient RθJA Minimal footprint — — 62
6 ms cooling area — — 50


**Silicon Substrate**

**RΘJC**


-----

**Table 2.13** Data from an EPC2010 datasheet showing the basic steady state thermal parameters [16]

Thermal Characteristics

Typical

RθJC Thermal resistance, junction-to-case 1.8 °C/W
RθJB Thermal resistance, junction-to-board 16 °C/W
RθJA Thermal resistance, junction-to-ambient[1] 56 °C/W

Note 1: RθJA is determined with the device mounted on one square inch of copper pad, single layer 2 oz.
[copper on FR4 board. For details, see http://epc-co.com/epc/documents/product-training/Appnote_](http://epc-co.com/epc/documents/product-training/Appnote_Thermal_Performance_of_eGaN_FETs.pdf)
[Thermal_Performance_of_eGaN_FETs.pdf.](http://epc-co.com/epc/documents/product-training/Appnote_Thermal_Performance_of_eGaN_FETs.pdf)

**Heatsink**

**Thermal Interface Material**

**Silicon Substrate** **Silicon Substrate**

**Active GaN Device Region** **Active GaN Device Region**

Metal 3 Metal 3 Metal 3 Metal 3 Metal 3 Metal 3 Metal 3 Metal 3

**Solder Bars** **Solder Bars**

**Copper** **Copper**
**Traces** **Traces**

**Printed Circuit Board**

**Figure 2.17** Side view of two LGA devices mounted to a printed circuit board and connected to a
heatsink via thermal interface material

sum of the parallel resistances of all the paths illustrated including the thermal resistance of
the thermal interface material and the heatsink. This system can be modeled using a simple
resistor network [18].

###### 2.6 Transient Thermal Impedance

Rarely is a transistor used in steady state with a continuous DC flow of current through the
device. In order to give designers a measure of the thermal impact of a shorter pulse, or a
repetitive pulse of various duty cycles, datasheets also have a transient thermal impedance
graph, such as the one shown in Figure 2.18 [16].

|Col1|Metal 3|
|---|---|

|M|etal 3|Col3|Metal 3|Col5|Metal|
|---|---|---|---|---|---|

|Col1|Metal 3|
|---|---|

|Me|tal 3|Col3|Metal 3|Col5|Metal|
|---|---|---|---|---|---|


**Silicon Substrate**


**Active GaN Device Region**


**Active GaN Device Region**


-----

**Normalized Maximum Transient Thermal Impedance**


1

0.1


**Duty Factors:**


0.01

0.001


0.0001 **J** **DM** **θJB** **θJB** **B**

10[–5] 10[–4] 10[–3] 10[–2] 10[–1] 1 10 100

**tp, Rectangular Pulse Duration, Seconds**

|0.5|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|Col27|Col28|Col29|Col30|Col31|Col32|Col33|Col34|Col35|Col36|Col37|Col38|Col39|Col40|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0.2 0.1||||||||||||||||||||||||||||||||||||||||
|0.05|||||||||||||||||||||||||||P|DM||||||||||||
|0.02||||||||||||||||||||||||||||||||||||||||
|0.01||||||||||||||||||||||||||||||||t 1|t|||||||
||||||Sin|gl|e|P|ul|se|||||||||||N||ot|e|s:||||||||2|||||||
|||||||||||||||||||||||D|ut|y|F|ac|tor: D|=|t1|/|t 2|||||||||
|||||||||||||||||||||||P|ea|k|T|J =|PDM|x|Z θ|J|B|x|R θJB||+|TB||||


**Figure 2.18** Transient thermal response curve for the EPC2010 eGaN FET [16]


To illustrate how these data in the graph can be used, take the example of the EPC2010 [16]
mounted on a PCB without a heatsink on the back. If the circuit pulses the part with a 10 W
instantaneous pulse (PDM) at a 10% duty cycle, and the pulses are 100 μs long, and the board is
sufficient to absorb the heat with little temperature impact, the effective thermal resistance and
junction temperature rise would be as shown below. The effective junction-to-board temperature can be given by Equation 2.5, with the normalized thermal impedance ZθJB determined
from Figure 2.18 for a duty cycle of 10%:

RθJB(effective)  RθJB  ZθJB  16 °C/W  0.1  1.6 °C/W (2.5)

ΔTJ  PDM  RθJB(effective)  10W  1.6 °C/W  16 °C (2.6)


Note the need to add to the ΔTJ in Equation 2.6 any rise in the temperature of the surface of the
PCB to get a more accurate gauge of the actual rise in device temperature.

###### 2.7 Summary


In this chapter, the basic electrical and thermal characteristics of GaN transistors were
discussed and related to the physical and design characteristics of the devices.
The three characteristics that make a device function in a circuit are: breakdown voltage
between source and drain electrodes (BVDSS), on-resistance (RDS(on)), and threshold voltage
(VGS(th)). Capacitance and reverse-conduction characteristics were discussed to show how a
power device will work when switched on and off. However, to develop a more complete
understanding of device and circuit performance, the characteristics and specifications
associated with the amount of heat that can be extracted from a device were also discussed.
The next two chapters are about circuit and layout techniques for GaN transistors. With a
step-function improvement in switching speed and power density, designers need to take extra
care to properly drive the gate of the device and reduce parasitic elements in the surrounding
circuits.


-----

###### References

1. Lu, B., Piner, E.L., and Palacios, T. (2010) Breakdown mechanism in AlGaN/GaN HEMTs on Si substrate,
Proceedings of the Device Research Conference (DRC), pp. 193–194.
2. McPherson, J.W. (1998) Underlying physics of the thermochemical Emodel in describing low-field timedependent dielectric breakdown in SiO2 thin films. Journal of Applied Physics, 84 (3).
3. Joh, J. and del Alamo, J.A. (2008) Critical voltage for electrical degradation of GaN high-electron mobility
transistors. IEEE Electron Device Letters, 29 (4).
4. Arulkumaran, S., Egawa, T., Ishikawa, H., and Jimbo, T. (2003) Temperature dependence of gate-leakage current
in AlGaN/GaN high-electron-mobility transistors. Applied Physics Letters, 82 (18).
5. Tan, W.S., Houston, P.A., Parbrook, P.J. et al. (2002) Gate leakage effects and breakdown voltage in metal organic
vapor phase epitaxy AlGaN/GaN heterostructure field-effect transistors. Applied Physics Letters, 80 (17).
6. Efficient Power Conversion Corporation, “EPC2001 – Enhancement-mode Power Transistor,” EPC2001 data[sheet, March 2011 [Revised Jan. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2001_-](http://epc-co.com/epc/documents/datasheets/EPC2001_datasheet.pdf)
[datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2001_datasheet.pdf)
7. Transphorm, “GaN Power Low-loss Switch,” TPH3006PD datasheet, 27 March 2013.
8. Infineon, “OptiMOS[TM] Power-Transistor,” BSC060N10NS3 G datasheet, 21 Oct. 2009.
9. Sze, S.M. (1981) Physics of Semiconductor Devices, 2nd edn, John Wiley and Sons, Hoboken, NJ, pp. 31.
10. Giancoli, Douglas. (2009) [1984]. 25. Electric Currents and Resistance, in: Physics for Scientists and Engineers
_with Modern Physics, 4th edn (ed. Phillips Jocelyn), Prentice Hall, Upper Saddle River, New Jersey, p. 658._
11. Serway, R.A. (1998) Principles of Physics, in Fort Worth, 2nd edn, Saunders College Pub, Texas, London, p. 602.
12. Cuerdo, R., Pedros, J., Navarro, A. et al. (2008) High temperature assessment of nitride-based devices. Journal of
_Materials Science-Materials in Electronics, 19 (2), pp. 189–193._
13. Vitanov, S., Palankovski, V., Maroldt, S., and Quay, R. (2010) High-temperature modeling of AlGaN/GaN
HEMTs. Solid-State Electronics, 54, 1105–1112.
14. Rashmi, Abhinav Kranti, Haldar, S., and Gupta, R.S. (2002) An accurate charge control model for spontaneous and
piezoelectric polarization dependent two-dimensional electron gas sheet charge density of lattice-mismatched.
_Solid-State Electronics, 46, 621–630._
15. Liu, Q.Z. and Lau, S.S. (1998) A review of the metal-GaN contact technology. Solid-State Electronics, 42 (5).
16. Efficient Power Conversion Corporation, “EPC2010 – Enhancement-mode Power Transistor,” EPC2010 data[sheet, July 2011 [Revised Feb. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2010_-](http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet.pdf)
[datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet.pdf)
17. Infineon, “CoolMOS[TM] Power-Transistor,” IPL65R130C7 datasheet, April 2013.
18. Strydom, J. (May 2012) “The eGaN[] FET–Silicon Power Shoot-Out Volume 8: Envelope Tracking,” Power
Electronics Technology.


-----

# 3

#### Driving GaN Transistors

###### 3.1 Introd uction

This c hapter discusses the basic techniqu es for using GaN trans istors in high performanc e
powe r con version circu its. GaN transisto rs general ly b ehave like powe r MO SFETs, but at
much higher switch ing speeds a nd powe r densi ties. A good unders tanding of these similarit ies
and differences is fundam ental to understandi ng by how much ex isting powe r c onversion
systems can be imp roved by using GaN-ba sed device techno logies. The n ext three chapters
highlight the benefi ts of GaN technology, desig n techni ques for maxi mum performanc e, and
ways to avoid common pitfall s that can result from the new GaN performanc e capabilit ies.
Techn iques to be addressed include :

- how to drive a GaN trans istor

- how to layout a high-effi ciency GaN transistor circu it

- how to model and meas ure, both therm ally and elect rically, a high powe r-dens ity GaN
trans istor-bas ed circu it.

To understand the differences in, and opport unities offer ed by these faster swi tching d evices,
the alte rnative GaN transist or structure s need to be c onsidered individua lly. Two of the
structure s shown in Chap ter 1 will be examined: enhancem ent-mode trans istors using a p-G aN
type gate, an d the two-tr ansistor cascode config uration. The gate electrodes of both types of
structure s have very high input impedance, and contr ol of the device is therefore accom plished
by supplying or remo ving a certain amount of charge from the gate e lectrode.
Table 3.1 gives definiti ons of the vario us charge compo nents that will be used to examine the
switch ing proper ties of GaN and MO SFET device s. In Figure 3.1(a), these defin itions are used
to segment transist or switch ing into four region s: (1) the charge requi red to bring the gate
electrode up to de vice thres hold, (2) the charge required to complete the curren t rise transition
time (tCR ) and reach the plat eau voltage (V pl), (3) the c harge requi red to complete the voltage
fall trans ition time (tVF ), and (4) the charge supplied to drive the gate to the stead y-state
gate voltage. In Figure 3.1(b) a gate charge curve for a GaN transistor is shown with the various
gate charges.

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

**Table 3.1** Gate charge components and their definitions

Gate Charge Definitions
Components


QGS Charge required to increase gate voltage from zero to the plateau voltage.
QGS1 Charge required to increase gate voltage from zero to the threshold voltage of the device.
QGS2 Charge required to commutate the device current.

QGS = QGS1 + QGS2
QGD Charge required to commutate the device voltage, at which point the device enters the
linear region.
QG Total gate charge required to drive a device from zero to rated gate voltage, including QGD


**VBUS**

**IL**


**Vth**


**tCR** **tVF** **t**

(a) Four regions of transistor switching

|Col1|Col2|P on I DS V GSV V DS DR V pl t t|
|---|---|---|
||||
|t||V DS|
||||
||||
||t|t|


5


4.5

4


3.5

3


2.5

2


1.5

1


0.5

0

0 2 4 6 8 10

**QG - Gate Charge (nC)**

|Col1|(a) Fou|Col3|ur regions|Col5|of transist|Col7|tor switchin|ng|g|
|---|---|---|---|---|---|---|---|---|---|
||I = 25 A D|||||||||
||V = 50 V DS||Q GD|||||||
|Q||||||||||
|GS||||||||||
|Q GS Q GS1|||2||||V pl|||
|||||||||||
|||||||||||
|||||||V||||
|||||||th||||
|||||||||||
||||||||Q G|||
|||||||||||
|||||||||||


(b) Gate charge curve for a GaN transistor
**is shown with the various gate charges**

**Figure 3.1** Gate charge vs. gate voltage showing different gate charge components for an EPC2010 GaN
transistor [1]


To better understand why GaN transistors switch so much faster than MOSFETs, these two
transistor technologies can be compared quantitatively using figures of merit (FOM). As
mentioned in Chapter 1, the theoretical on-resistance versus blocking voltage of a GaN
transistor is at least three orders of magnitude lower than that of silicon [2], and the


-----

100

10

1

0.1


100

10

1

0.1

1 10 100 1000 1 10 100 1000
**RDS(on)(mΩ)** **RDS(on)(mΩ)**

(a) (b)


**Figure 3.2** On-resistance vs. total gate charge comparison for Si- and GaN-based power devices
showing (a) 40 V and 200 V, and (b) 100 V and 600 V devices

first-generation production devices were already beyond the silicon limit [3]. In general, these
smaller devices have less capacitance when compared to silicon MOSFETs. Although more
specialized FOMs will be discussed in the Chapters 6 and 7, the RDS(on) × QG product is
commonly used for comparing different MOSFET technologies. Using this FOM to compare
GaN to silicon (Figure 3.2) shows an improvement of three to seven times.

###### 3.2 Gate Drive Voltage

Both enhancement-mode and cascode GaN transistors have maximum voltage limits that can
be applied to the gate electrode with respect to the source. For a cascode device, such as the
TPH3006PD [4], this maximum voltage is ±18 V. For an enhancement-mode device, such as
the EPC2010, this maximum voltage is +6 V/ 5 V. (Note that different technologies and
�
different manufacturers will rate their devices differently.) Exceeding these limits may damage
devices permanently, and therefore must be avoided. Fortunately, the amount of gate voltage
required to drive the device to the on-state is significantly lower than the maximum voltage
allowed. With very fast switching speed, however, care must be taken to avoid overshoot that
might inadvertently take the gates above the maximum voltage limit. For the enhancementmode transistor, the device RDS(on) is specified in the datasheet at a recommended 5 VGS, which
is 1 V below the absolute maximum rating.
Because of this relatively tight requirement, we will discuss the gate drive requirements for
an enhancement-mode GaN device first, with the understanding that the same basic principles
apply to a transistor in a cascode configuration.
Itispossibletodrivetheseenhancement-modedeviceswithgatevoltagesaslowas4 Vwithout
a significant increase in RDS(on), as shown by the rectangular box area in Figure 3.3. Furthermore,
it is recommended to keep the gate driver voltage below 5.25 V to allow enough margin between
the gate voltage and the absolute maximum gate voltage. These recommended gate voltage limits
can be readily achieved by near-critical damping of the gate drive turn-on power loop.
The gate driver, the transistor, the gate drive bypass capacitor (CVDD), and the inductance of
the interconnections between them (LG), form an LCR-series resonant tank as shown in Figure
3.4(a). This equivalent resistance value includes the transistor gate resistance (RG), gate drive
pull-up resistance (RSource), the high-frequency interconnect resistance between the


-----

20

18

16

14

12

10

8

6

4

2


20

15


10

5


0 0
2 2.5 3 3.5 4 4.5 5 5.5 2 2.5 3 3.5 4 4.5 5 5.5

**VGS – Gate-to-Source Voltage (V)** **VGS – Gate-to-Source Voltage (V)**

**Figure 3.3** Two graphs of the RDS(on) of an enhancement-mode GaN HEMT (EPC2001) as a function of
gate voltage for various drain currents (a) and at various temperatures (b) showing the recommended gate
drive voltage range (boxed area) [6]

|Col1|Col2|Col3|Col4|Col5|I|Col7|= 10 A|Col9|
|---|---|---|---|---|---|---|---|---|
|||||||I|= 10 A||
|||||||D ID|= 20 A||
|||||||ID ID|= 40 A = 80 A||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||

|Col1|Col2|Col3|Col4|Col5|ID =|Col7|25˚C 125˚C 25 A|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||25˚C 125˚C||
|||||||ID =|25 A||
||||||||||
||||||||||
||||||||||


components, as well as the equivalent series resistance (ESR) of the gate driver supply
capacitor. To critically damp this loop, the overall gate loop resistance RG(eq) (RG(eq) = RG
+ RSource) must be larger than the value given in Equation 3.1. This is achieved by minimizing
the gate loop inductance (LG) (layout techniques for minimal gate inductance will be discussed
in Chapter 4) and adjusting the series gate resistance to limit overshoot. The resultant damped
gate voltage turn-on [5] is shown in Figure 3.5.


RG(eq) 


r4LffiffiffiffiffiffiffiffiG

CGS


(3.1)


For the gate drive voltage falling edge, the minus 5 V minimum does not present any
practical limitations. It is, therefore, possible to drive the GaN transistor faster at turn-off and
allow some negative ringing. Furthermore, the gate drive turn-off power loop, shown in Figure
3.4(b), will have smaller inductance, as this loop does not include the gate drive bypass
capacitor. However, care should still be taken to avoid subsequent positive gate voltage ringing
beyond the gate threshold of the device, as this will cause the device to turn on again. Figure 3.5
shows an under-damped turn-off with the subsequent positive ringing of less than half a volt.

Gate Drive Gate Drive


RG LG RG LG

CVDD CVDD

RSinkN CGS RSinkN CGS

|DD|Col2|Gate Drive R Source R SinkN|Col4|R G L G C GS|
|---|---|---|---|---|
||||||
||||||
||||||

|VDD|Col2|Gate Drive R Source R SinkN|R G L G C GS|
|---|---|---|---|
||D|||
|||||


(a) (b)

**Figure 3.4** Resonant loop formed between the gate driver and eGaN FET during (a) turn-on and (b) turnoff


-----

6 V

5.25V

Recommended Gate Drive Voltage Range

4 V

1.4 V Vth

0 V Some Undershoot Allowed

–1 V

**Figure 3.5** Example of an enhancement-mode transistor gate drive voltage showing a critically damped
voltage rise and a slightly under-damped voltage fall

Since the turn-on and turn-off damping requirements are different, the minimum gate loop
resistance values will also differ. These differences are best addressed by separating the pull-up
and pull-down gate driver resistances at the driver output (creating two separate driver outputs),
thus allowing the use of two separate gate resistors to independently adjust the turn-on and turnoff gate loop damping.

###### 3.3 Bootstrapping and Floating Supplies

The limited gate drive supply voltage range for the enhancement-mode GaN transistor also has
an impact on the generation of a floating high-side supply for half-bridge applications. An
almost ubiquitous solution for generating this supply is the use of a bootstrap circuit as shown
in Figure 3.6. This circuit operates by charging the floating high-side supply capacitor (CBoot)

VDD

**+**

DBoot

**–**

**+**

CBoot

**–**

**–**

VSD

**+**

**Figure 3.6** Half-bridge circuit with bootstrap supply showing impact of low-side diode conduction


![](GaN-transistors-power-conversion.pdf-60-0.png)

Maximum Gate Voltage Rating

Recommended Gate Drive Voltage Range

Vth

Some Undershoot Allowed


-----

|Col1|UVLO & Clamp Level Shift D Boot UVLO|HB C Boot HOH HOL HS VDD LOH LOL VSS|Col4|
|---|---|---|---|
|||||
|||LOH LOL||
|||VSS||
|||||


**Figure 3.7** Block diagram of a half-bridge GaN transistor driver with integrated high-side supply
regulation [7]

during the on-state of the low-side device from the fixed low-side supply through a high-speed
bootstrap diode (DBoot). During the high side on state, the bootstrap diode blocks the full bus
voltage, and the floating capacitor supplies the required gate drive energy at the voltage of the
bootstrap capacitor.
In practice, the bootstrap capacitor is charged to the low-side supply voltage minus the drop
across the bootstrap diode, typically around a half a volt, resulting in a lower high-side supply
voltage. When the bootstrap capacitor is fully charged, the diode will block current and end
the charging period. However, due to the body diode drop of the GaN transistor, prolonged
diode conduction of the low-side device will cause the bootstrap supply to charge up to the lowside bus voltage (VDD) plus the reverse conduction voltage drop (VSD) – minus the bootstrap
diode, which altogether could be higher that the maximum allowable gate voltage.
There are three common ways to avoid overcharging the bootstrap capacitor, which
increases the likelihood of over-voltage on the high-side transistor gate:

1. Minimize diode conduction by reducing the dead-time to less than a few nanoseconds
between the turn-on and turn-off of the two transistors.
2. Place an external Schottky diode across the low-side transistor to limit the diode drop. This
option will be discussed in more detail in Chapter 6.
3. In applications where the switching of the half-bridge devices are not complementary
(prolonged dead-time), use a high-side regulator with a discrete solution using a series
voltage regulator, or an integrated gate driver IC as shown in Figures 3.7 and 3.8 [7,8].

###### 3.4 dv/dt Immunity

GaN power devices are exposed to significantly higher voltage and current slew rates, which
can impact the performance of the transistor. These conditions need to be understood well in
order to fully utilize the technology.


-----

|Col1|Gate Drive Regulator V DD|Col3|
|---|---|---|
||||
||||
||||


**Figure 3.8** Block diagram of a single GaN transistor driver with integrated supply regulation [8]

A high, positive-voltage slew rate (dv/dt) on the drain of an off-state device can occur in both
hard- and soft-switching applications, and is characterized by a quick charging of the device’s
capacitances as depicted in Figure 3.9. During this dv/dt event, the drain-source capacitance
(CDS) is charged. Concurrently, the gate-drain (CGD) and gate-source (CGS) capacitors in series
also are charged. The concern is that, unless addressed, the charging current through the CGD
capacitor will flow through and charge CGS beyond Vth and turn the device on. This event,
sometimes called Miller turn-on, can be very dissipative.
Such unintended turn-on can be avoided by supplying an alternative parallel path across CGS
through which the CGD charging current can then flow. With the addition of a gate driver pulldown keeping the device off, some of the current flowing through CGD can be diverted from
CGS through the series gate resistor (RG) to the gate driver pull-down resistor (RSink). This

High dv/dt Event

GaN Transistor

CGD

Gate Drive CDS

RG

RSink CGS

Keep < Vth

High dv/dt Current Paths

**Figure 3.9** Effect of dv/dt on a device in the off state and requirements for avoiding Miller-induced
shoot-through


-----

1.4

dV/dt Sensitive

1.2
EPC2016


1

0.8


0.6

0.4


0.2

0
0 20 40 60 80 100

|dV/dt S|ensitive|Col3|Col4|Col5|
|---|---|---|---|---|
|||EPC2016|||
||||||
||||||
||||||
||||dV/dt|Immune|
||||||


**Drain-to-Source Voltage VDS (V)**


**Figure 3.10** Example of Miller charge ratio vs. drain-to-source voltage using an EPC2016 [10]

additional path allows the efficient operation of devices that would otherwise be sensitive to
dv/dt turn-on.
To determine the dv/dt susceptibility of a power device, a Miller charge ratio (QGD/QGS1), as
function of drain-to-source voltage, needs to be evaluated. A Miller ratio of less than one will
guarantee dv/dt immunity [9]. GaN transistors, like MOSFETs, are typically operated up to
80% of rated voltage. At these higher voltages, the Miller charge ratio should preferably remain
at less than one, but for most commercial devices this is not the case. As an example, the Miller
charge ratio versus drain-to-source voltage for a 100 V-rated part, EPC2016, is plotted in
Figure 3.10. As illustrated, the ratio increases above one at about 40 V, and therefore, requires
at least some pull-down resistor circuit to keep the device off at higher voltages.
For complementary switching applications (e.g. a half-bridge circuit where one or the other
switch is always on), it is possible to improve the dv/dt immunity of the device artificially
through adjustment of the dead-time between the switching devices. From the gate waveform
shown in Figure 3.5, it can be seen that the gate drive voltage briefly becomes negative at turnoff due to the slightly under-damped resonance within the gate loop. By adjusting the turn-on
timing of the complementary switch to coincide with this negative voltage dip of the device’s
gate voltage, the effective charge needed to induce Miller turn-on is increased significantly.
Although only applicable when the timing between devices is fixed, this technique allows for
an increase in dv/dt switching speed, as well as the use of marginal Miller-ratio devices without
fear of dv/dt induced turn-on.
Figure 3.11 shows two cases where a device with marginal Miller ratio is turned off and then
subjected to a high dv/dt, as induced by the complementary switch turn-on. The solid line in the
drain voltage curve shows a dv/dt-induced turn-on with a characteristic “knee” where the drain
voltage rise time is self-limited due to dv/dt turn-on. In contrast, by turning on the complementary device during the gate voltage dip (dotted line VDS), dv/dt turn-on is avoided and
higher dv/dt edge rates are achieved.


-----

VGS dv/dt Induced

Turn-On

VDS

VDS

No Induced Turn-On

Vth

0

**Figure 3.11** Improvement of dv/dt turn-on immunity through controlled gate timing using underdamped gate turn-off

###### 3.5 di/dt Immunity

A rising current through an off-state device, as shown in Figure 3.12, will induce a step voltage
across the common-source inductance (CSI). The CSI is the inductance on the source side of a
device that is common to both the power loop (drain-to-source current) and the gate drive loop
(gate-to-source current). This positive voltage step will induce an opposing voltage across CGS.
For a rising current, this causes the gate voltage to be driven to a negative value and with
insufficient damping of the off-state gate loop LCR resonant tank, this initial negative voltage

D

GaN Transistor Drain Current

Gate Drive CGD

G RG CDS

Opposing
Voltage Induced

CGS _ Across Gate

+

RSink S

LCR Resonant Tank + Positive di/dt Generates

Voltage Across CSI

Gate Current CSI –

**Figure 3.12** Impact of a positive di/dt of an off-state device with common-source inductance


-----

0


Sudden Damping of Ringing

Under-Damped Ringing Above
Threshold Voltage Causing
Shoot-Through

di/dt Due to
Complementary Device
Turn-On


**Figure 3.13** di/dt-induced turn-on (shoot-through) of an off-state device with under-damped gate turnoff power loop

step across the gate could induce positive ringing and cause an unintended turn-on and shootthrough as shown in Figure 3.13.
It is possible to avoid this type of di/dt turn-on by sufficiently damping the gate turn-off loop,
although some level of undershoot may be preferred, as described in the dv/dt immunity case
above. However, increasing the gate turn-off power loop damping through an increase in gate
pull-down resistance would negatively impact dv/dt immunity. Thus, adjusting gate resistance
alone for devices with marginal Miller charge ratios may not be enough to avoid di/dt and/or
dv/dt turn-on.
A better solution is to limit the size of the CSI through improved packaging and device
layout. This is accomplished by separating the gate and power loops to as close to the GaN
device as possible, and minimizing the internal source inductance of the GaN device, which
will remain common to both loops. (This will be discussed in more detail in Chapter 4.)
Reducing CSI is also beneficial for hard-switching performance, and will be discussed in
Chapter 6.

###### 3.6 Ground Bounce

Ground bounce is a common phenomenon in the world of high-speed logic [11,12]. The
concept is that high voltage slew rates across capacitors generate large current pulses of short
duration. Conceptually, these current pulses generate pairs of dynamic voltage pulses across
any layout inductances at the rising and falling edges of the current pulse. These ground
bounces can lead to unintended switching and degraded performance, and can potentially
damage devices. An idealized example in Figure 3.14(a) shows the gate drive in close
proximity to the GaN transistor to minimize common-source inductance. By tying the gate
drive return directly to the source of the GaN device, the source-side layout inductance is
pushed outside the gate drive loop. Any voltage pulses across this source inductance will cause
the logic and controller ground to “bounce” relative to the source of the power device (and thus
the “ground” of the gate driver). If these pulses are large enough, they can change the logic state
of the gate driver input, and thus, negatively impact a GaN power device.


-----

Logic
Output


(a)

Gate Drive

(b)

|Col1|Gate Drive|Col3|
|---|---|---|
||||
||||


**Figure 3.14** Inductance between the gate drive and the power ground causes a “bounce” of the gate
driver ground. (a) Tying controller to power ground (b) Tying controller to gate driver ground

The best way to avoid ground bounce is to place the controller on the same ground as the gate
driver, as shown in Figure 3.14(b), something that may not be practical with multiple low-side
switching devices. In those cases, there are two ways to address ground bounce as shown in
Figure 3.15. First, the ground bounce noise can be filtered out by placing a small RC low-pass

|Col1|Gate Drive|Col3|
|---|---|---|
||||
||||

|Col1|Col2|
|---|---|
|||
||S|
|||


(a)


(b)

|The best way to avoid ground bounce is to place the controller on the same ground as the gate iver, as shown in Figure 3.14(b), something that may not be practical with multiple low-side witching devices. In those cases, there are two ways to address ground bounce as shown in gure 3.15. First, the ground bounce noise can be filtered out by placing a small RC low-pass|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|Gate Drive Gate Drive D I DS Shift Level S Logic Logic Output Ou Vtpu t S (a) (b)|||||||||
||||||Gate Drive||||
||||hift||||||
||||Level S||||||
||||||||||
||||||||||


**Figure 3.15** Solutions for filtering out ground “bounce” noise from gate drive input. (a) RC filter and
(b) level-shifter or isolator


-----

filter (LPF) between the controller and the gate driver. There is a tradeoff between too much
filtering causing significant delay and pulse width distortion due to variation in the gate driver
input thresholds, or not enough filtering maintaining susceptibility to logic glitches. The
second alternative solution is to use a level-shifter or isolator between the controller and
the gate driver. This approach effectively treats the low-side gate driver the same way as the
floating high-side driver. Although a level-shifter increases complexity and component count,
it does have the added advantage of improving the gate driver propagation delay matching
between the high side and low side.

###### 3.7 Common Mode Current

Another mechanism for generating logic glitches is common mode current through the levelshifter or isolator. This can happen to the high-side device in a half-bridge application during
high positive or negative switch-node dv/dt. For a positive dv/dt event, as shown in Figure 3.16,
thehighvoltageslewrateacrosstheisolatorcapacitancecausesthegenerationofacommonmode
current flowing in the loops, as shown. The common mode current causes ground bounce within
the level-shifter and can cause changes in logic state if the common mode current is large enough.
With GaN transistors, the slew rates are likely to be hundreds of volts per nanosecond. This
issue will need to be addressed to avoid becoming a limiting factor on circuit performance
and, since this is a level-shifter issue, it is common to all GaN device applications that have a
high-side floating device. Resolution requires minimizing floating high-side-to-ground capacitance as well as increasing dv/dt immunity within the level-shifter. High-side-to-ground
capacitance can be minimized by avoiding PCB layout overlap between ground and the high
side, selecting components with low inherent capacitance, and limiting the size of the high-side
copper area.

###### VDD

Level Shifter

Logic
Output

Common Mode
Current Paths

**Figure 3.16** High speed switching causes large common mode current across level-shifter and bootstrap
diode capacitance


-----

Gate Driver Power Loop

**Figure 3.17** Schematic of GaN transistor and driver showing gate drive power loop

###### 3.8 Gate Driver Edge Rate

As GaN devices continue to improve, their relative capacitances and figures of merit will
continue to decrease. This means that the required resistance for damping in the equation
described earlier (Equation 3.1) will increase with decreasing die size (higher RDS(on)) and also
with improvements in GaN technology. It also means that the gate charge time will decrease
with decreasing gate capacitance, and the resulting decrease in theoretical switching time. To
achieve this, however, the actual gate driver rise time must become even faster. This requires
the minimization of the gate drive loop inductance as well as the gate driver power loop, as
shown in Figure 3.17. Implementation means that the gate driver packaging inductance must be
minimized through the use of chip-scale packaging, or similar low inductance packaging, and
the integration of some of the VDD bus capacitance, CVDD, within the driver. Furthermore, the
gate drive and the high-speed GaN device need to be closely connected, while the interconnection impedance is minimized. This interconnection would require complementing pinouts and packaging options for both the gate driver and GaN transistor.

###### 3.9 Driving Cascode GaN Devices

Cascode devices have a number of unique driving requirements. One of the main characteristics of the cascode device is the fact that it is a hybrid design with two discrete devices, a
depletion-mode GaN transistor in-series with a MOSFET, each made on dissimilar processes
that require external connections.
Driving the cascode device through the MOSFET gate has a number of advantages and
disadvantages compared to an enhancement-mode device.
Some advantages are as follows:

- The cascode device gate terminal is that of a MOSFET. It has the same MOSFET gate
voltage ratings and can be driven, in concept, with traditional MOSFET drivers. It doesn’t
necessarily need as much attention to avoid gate overshoot.

- Turning off the GaN transistor with a positive current is self-commutating, once the
MOSFET turns off. In other words, the load current itself is responsible for generating
the necessary depletion-mode gate voltage to turn the device off through charging up the
MOSFET output capacitance. The higher the load current, the faster this switching occurs,
thus resulting in a turn-off energy that is largely load current independent.


-----

Source

**Figure 3.18** Schematic of cascode GaN device showing parasitic inductances and the different highfrequency loops between transistors

Some disadvantages are as follows:

- There are two loops where common inductance is important. Referring to Figure 3.18,
there is the common-source inductance (LCSI), similar to a single enhancement-mode
device, and the common cascode inductance (LCCI) in the loop between the MOSFET and
the depletion-mode GaN transistor. Both of these loops will negatively impact switching
speed.

- The use of two discrete devices means the interconnect parasitics are larger than for a single
enhancement-mode device. As with most parasitics, this can be addressed through higher
levels of package integration and complexity [13].

- The turn-on speed of the device is limited by the speed of the low-voltage silicon MOSFET
and the CSI between the driver and MOSFET. One method to address both of these issues is
to integrate the MOSFET and driver into a single module using a low-voltage LDMOS
process [14].

- The size of the entire cascode device is at least twice that of the enhancement-mode GaN
transistor.

- The addition of a lower-voltage series MOSFET device negatively impacts the resultant
RDS(on) of the cascode device. This impact decreases with increasing device voltage rating,
as was shown in Figure 1.12. This makes the cascode structure less suitable for lowervoltage applications.

Another of the concerns with using a cascode structure is the static voltage sharing during the
off-state, and the dynamic voltage sharing at turn-off and turn-on. For static sharing, the
depletion-mode GaN transistor and MOSFET devices must have similar IDS leakage currents.
If they are not well matched, the drain-to-source voltage drop across the MOSFET will either
keep increasing or decreasing. If it keeps increasing, the low-voltage MOSFET’s maximum
voltage will be reached, at which point its IDS will start increasing due to avalanche breakdown,
until equilibrium is reached. The voltage across the depletion-mode GaN FET gate-to-source
will then be equal to the MOSFET’s rated breakdown voltage. On the other hand, if
the MOSFET leakage current is higher than the depletion-mode transistor, the MOSFET

|Enhancement-Mode Depletion- Silicon MOSF ET L Mode GaN CCI Drain Gate Cascode Loop Power Loop Gate Loop L CSI Cascode Package|Enhancement-Mode Depletion- Silicon MOSF ET L Mode GaN CCI Drain Gate Cascode Loop Power Loop Gate Loop L CSI Cascode Package|Col3|
|---|---|---|


-----

drain -to-source v oltage will collapse to near zero, at whi ch point the GaN device starts to turn
on, increasing its leakag e curren t, and restoring drain leakag e equilibri um.
Dynami cally, the total o utput cap acitance charge ratio between the MOSF ET and the
deplet ion-mode GaN transist or should be sim ilar to the rati o of thei r rated drain voltages. What
compl icates matters is the non-l inear ity of these capaci tances, coup led wi th the addit ional
parasiti c induct ances between the d evices. The se facto rs can generat e signifi cant voltages
durin g cu rrent rise and fall intervals . It may even be possible under certain circumst ances to
dynam ically over-volta ge the source -to-gate of the deplet ion-mode GaN trans istor.

###### 3.10 Summary

In this chapte r the drive r considerat ions for high- speed GaN trans istors were addres sed,
includ ing the follow ing:

- Gate power loop inductance minimization: The gate driver should be designed to minimize the
inductance between the VDD supply capacitor and the actual gate driver power devices (sink
and source devices). This will minimize gate driver rise time and maximize driver di/dt.

- Gro und bounce immunity: The gate driver desig n shoul d be made wi th the assumptio n that
the drive r ground and the contr oller ground can differ significan tly, and the input logi c pin
must be immune to noise -induced changes in logic state.

- Hi gh dv/dt immuni ty for high- side drive rs: Log ic-isolators or level -shifter s used to transfer
the control logi c signa l to the float ing high-side de vice need to be immune to high dv/dt rise
and fall times wi thout changi ng the logic state.

- Opt imized drive r p ackaging and pin-out: The gate drive and high- speed GaN device need to
be close ly connect ed with the inte rconnec tion imp edance minim ized. This requires pin-o uts
and packagi ng options that compleme nt the GaN trans istor.

- Se parate control of the turn- on and turn-off: Fo r a gene ral purpose GaN driver, the speed of
the drive r needs to be mat ched to the size and speed of the device being d riven. This
flexi bility requi res a low-res istance gate driver with the option of addit ional exter nal
resi stors. Furthe rmore, to adjus t both the turn-on and turn- off separately, it is preferred
to have separa te pins for turn-o ff and turn- on.

- Reg ulation of gate drive suppl y voltage: Fo r enhancem ent-mode transist ors in parti cular,
both low-sid e drive rs, and especi ally high-side drive rs, nee d to regul ate the gate drive suppl y
voltage to avoid an over-voltage condition on the transistor gate.

The next chapter will focus on layout techniques and ways to minimize the parasitic
inductances that have increased importance due to the higher switching speed of GaN
transistors.

###### References

1. Efficient Power Conversion Corporation, “EPC2010 – Enhancement-mode Power Transistor,” EPC2010 datasheet, March 2011 [Revised Feb. 2013]. Available from [http://epc-co.com/epc/documents/datasheets/EPC2010_](http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet.pdf)
[datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet.pdf)
2. Baliga, B.J. (1989) Power semiconductor device figure-of-merit for high frequency applications. IEEE Electron
_Device Letters, 10, 455–457._
3. Beach, R. “Master the fundamentals of your gallium-nitride power transistors,” Electronic Design Europe, 29 April
29, 2010.


-----

4. Transphorm, “ TPH3006PD – GaN Power Low-loss Switch,” Transform datasheet, 27 March 2013.
5. Reusch, D., Gilham, D., Su, Y., and Lee, F. (2012) “Gallium nitride based 3D integrated non-isolated point of load
module,” in _Applied Power Electronics Conference and Exposition (APEC), 2012, Twenty-Seventh Annual IEEE,_
Orlando, FL, Feb. 2012, pp. 38–45.
6. Efficient Power Conversion Corporation, “ EPC2001 – Enhancement-mode Power Transistor,” EPC2001 datasheet, March 2011 [Revised Jan. 2013]. Available from [http://epc-co.com/epc/documents/datasheets/EPC2001_](http://epc-co.com/epc/documents/datasheets/EPC2001_datasheet.pdf)
[datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2001_datasheet.pdf)
7. Texas Instruments, “LM5113 5 A, 100 V Half-Bridge Gate Driver for Enhancement Mode GaN GETs,” LM5113
datasheet, June 2011 [Revised April 2013].
8. Texas Instruments, “4-A and 6-A High-Speed 5-V Drive, Optimized Single-Gate Driver,” UCC27611 datasheet,
Dec. 2012.
9. Wu, T. _Cdv/dt Induced Turn-On In Synchronous Buck Regulators, white paper, International Rectifier_
Corporation.
10. EPC Corporation, “ EPC2016 – Enhancement-mode Power Transistor,” EPC2016 datasheet, Sep. 2013 [Revised
Sept. 2013].
11. King, P. “Ground Bounce Basics and Best Practices,” Agilent Technologies, Available from [http://www.home](http://www.home.agilent.com/upload/cmc_upload/All/Ground_Bounce.pdf)
[.agilent.com/upload/cmc_upload/All/Ground_Bounce.pdf.](http://www.home.agilent.com/upload/cmc_upload/All/Ground_Bounce.pdf)
12. Fairchild Semiconductor, “Understanding and Minimizing Ground Bounce,” Appl. Note AN-640, Available from

[http://www.fairchildsemi.com/an/AN/AN-640.pdf.](http://www.fairchildsemi.com/an/AN/AN-640.pdf)
13. Patterson, G. “GaN Switching for Efficient Converters,” _Power Electronics Europe, Issue 5, 2013, pp. 18 –21,_
Available from [http://www.power-mag.com/pdf/issuearchive/63.pdf.](http://www.power-mag.com/pdf/issuearchive/63.pdf)
14. Roberts, J. and Klowak, G. “GaN Transistors – Drive Control, Thermal Management, and Isolation,” Power
Electronics Magazine, Feb. 2013, Available from [http://powerelectronics.com/gan-transistors/gan-transistors-](http://powerelectronics.com/gan-transistors/gan-transistors-drive-control-thermal-management-and-isolation)
[drive-control-thermal-management-and-isolation. pp. 24–28.](http://powerelectronics.com/gan-transistors/gan-transistors-drive-control-thermal-management-and-isolation)


-----

# 4

#### Layout Considerations for GaN Transistor Circuits

###### 4.1 Introd uction

The previ ous cha pter discussed the drive r requireme nts for GaN trans istors, which are capabl e
of much higher switch ing speeds than Si MO SFETs. The faste r switch ing speeds also magnify
the impact o f parasi tic inductances on perfor mance. As GaN mat ures and becom es capable of
even higher switch ing speeds, the minimizat ion of parasitic s will be even more crit ical to fully
utilizin g GaN trans istors. In this chapte r, the focus will be on layout techni ques and ways to
minim ize these parasiti cs. In subseq uent chapte rs, the imp act of these parasi tics will be
quanti fied along with their relat ive imp ortance for perfor mance in va rious application s.
For a half-brid ge configurat ion, which is used in about 90% of powe r con verters, there are
two main power loops to consi der: (1) the high-freque ncy power loop formed by the two power
switch ing device s along wi th the high- freque ncy bus capaci tor, and (2) the gate drive loop
formed by the gate drive r, power device, and high-freque ncy gate d rive capaci tor. The common
source inductance (C SI) is defin ed by the part of the loop inductance that is comm on to both
gate loop and power loop. It is repres ented by the inductance shown in Figure 4.1 where the
powe r and gate loops coinci de.

###### 4.2 Minim izing Parasitic Induct ance

The minimizat ion of all parasitic inductances is vita l when consi derin g the layout of high-speed
powe r device s. It is not possi ble to reduce all compo nents of inductance equally, and therefore
they must be addres sed in order of importan ce, starting with common source inductance, then
powe r loop inductanc e, and, last ly, gate loop inductance. The importan ce of CSI was discussed
in Cha pter 3, but the actual layout imp lementat ion varie s wi th the p ackaging of GaN
transist ors. Chap ter 6 will furt her quanti fy the impact of CSI on circuit perfor mance .
For high-voltage PQFN (Power Quad Flat No lead) MOSFET packages, the need for a separate
gate-return source pin is well known [1], and is implemented in high-voltage GaN PQFN
structures [2,3]. When these separate pins areavailable, the gate drive loop andthepower loop are

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

Power Loop

Common Source
Inductance

Gate Loops

**Figure 4.1** Schematic of a half-bridge power stage showing power and gate drive loops with common
source inductance defined by where the loops coincide

separated within the package and must not be connected externally. As stated in the previous gate
driver chapter, the reduction in common source inductance comes at the expense of external
source inductance, pushed outside the gate loop. This external inductance can lead to increased
ground bounce due to the improved speed of the device once CSI is removed [4].
Enhancement-mode transistors are available in a wafer level chip-scale package (WLCSP)
with terminals in a land grid array (LGA). Some of these devices do not offer a separate gatereturn source pin, but rather a number of very low inductance LGA solder bars, as shown in
Figure 4.2. These parts can be treated in the same way as one provided with a dedicated gatereturn pin or bar, by allocating the source pads closest to the gate to act as the “star” connection
point forboth gate loopandpower loop. The layoutof thegate andpower loopsarethen separated
by having the currents flow in opposite or orthogonal directions, as shown in Figure 4.2.

Source

Gate Return

Gate

Drain

**Figure 4.2** GaN transistor in an LGA format showing the direction of device current flow that minimizes
common-source inductance

|V DD|Col2|V Bus P|Col4|
|---|---|---|---|
|||||
|||||
|C|||C|


![](GaN-transistors-power-conversion.pdf-73-0.png)

-----

Inductive Loop A-B

A

w

B


Vertical
Interconnect

h

Conductor Thickness < h
w ≫ h


**Figure 4.3** Theoretical parallel plate transmission line with end termination forming an inductive loop

Both of the remaining inductance loops can be minimized in a similar manner. While
minimizing the inductance of the individual elements that make up the loop (i.e. capacitor ESL,
device lead inductance, PCB interconnect inductance) is important, the designer must also
focus on minimizing the total loop inductance. Because the inductance of the loop is
determined by the magnetic energy that is stored within, it is possible to further minimize
the overall loop inductance by using the coupling between adjacent conductors to induce
magnetic field self-cancellation. For such a coupled structure, consider a theoretical parallel
plate transmission line with end terminations as shown in Figure 4.3. The inductance from A to
B in this loop is given by equation 4.1.

LA-B  μR ? μ0 ? (h?l)/w (4.1)

In this equation μ0 is the permeability of free air, and μR is the relative permeability of the PCB
material. It shows that the inductance is proportional to the cross-sectional area of the loop
(h × l) and is inversely proportional to the width of the conductors, w. To form this loop, the
current has to flow in opposite directions in the two adjacent layers, which causes magnetic
field self-cancellation and reduces the inductance. The loop inductance will increase linearly
with an increase in conductor spacing (h). It is therefore recommended to make all highfrequency loops as short and wide as possible, with the return path directly adjacent and as
close as possible.
It should be noted that Equation 4.1 does not include the vertical interconnection between the
layers, or even require that there be one. This approach, therefore, can be implemented on any
incremental loop inductance, provided that there are two equal and opposing currents in
adjacent layers that form the area of the loop. It is especially useful for LGA devices, as shown
in Figure 4.4.
By interleaving the drain and source terminals on one side of the device, a number of
small loops with opposing currents are generated that will decrease the overall inductance
through magnetic field self-cancellation. This is not only true for the PCB traces shown in
Figure 4.4(a), but also for the vertical LGA solder bars and the interlayer connection vias
shown in Figure 4.4(b). With multiple small magnetic field canceling loops formed, the total
magnetic energy, and therefore inductance, is significantly reduced [5]. A further reduction in
partial loop inductance is possible by bringing both drain and source currents out on both sides
of the device from the centerline and duplicating the magnetic field cancellation effect.
This works by reducing the current in each conductor, thus further reducing the energy stored,
and the shorter current path yields a lower inductance as previously discussed.


-----

|LGA GaN Transistor Drain Vias|Col2|Vias|Col4|Col5|Col6|Drain|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
||||||||||||


Source

|Copper Traces (a)|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|LGA GaN Transistor|||||||||||
||||||||||||
|PCB|||||||||||


(b)

**Figure 4.4** LGA GaN transistor mounted on a PCB showing alternating current flow (a) top view (b)
side view

###### 4.3 Conventional Power Loop Designs

To see how this inductance minimization is realized in an actual layout, two conventional
approaches to power loops are presented for comparison. These two approaches will be called
“lateral” and “vertical” respectively. The lateral layout places the input capacitors and devices
on the same side of the PCB, in close proximity to minimize the size of the high-frequency
power loop. The high-frequency loop for this design is contained on the same side of the PCB
and is considered a lateral power loop as a result of the power loop flowing laterally on a single
PCB layer. An example of the lateral layout using an LGA transistor design is shown in
Figure 4.5 with the high-frequency loop highlighted.
While minimizing the physical size of the loop is important for reducing parasitic inductance, the design of the inner layers is also critical. For the lateral power loop design, the first
inner layer serves as a “shield layer.” This layer has a critical role in shielding the circuit from
the fields generated by the high-frequency power loop. The power loop generates a magnetic
field that induces a current in the shield layer that flows in the opposite direction from the power
loop. The current in the shield layer generates a magnetic field to counteract the original power
loop’s magnetic field. The end result is a cancellation of magnetic fields that translates into a
reduction in parasitic power loop inductance.


-----

![](GaN-transistors-power-conversion.pdf-76-1.png)

**Figure 4.5** Conventional lateral power loop for LGA GaN transistor-based converter: (a) top view
(b) side view

Having a complete shield plane in close proximity to the power loop yields the lowest power
loop inductance. For the lateral power loop design, the high-frequency loop inductance shows
little dependence on board thickness because the power loop is completely contained on the top
layer. The lateral design, however, is very dependent on the distance from the power loop to the
shield layer contained on the first inner layer [6].
The second conventional layout, shown in Figure 4.6, places the input capacitors and
transistors on opposite sides of the PCB, with the capacitors located directly underneath the
devices to minimize the physical loop size. This layout is called a vertical power loop because

**Figure 4.6** Conventional vertical power loop for LGA transistor-based converter: (a) top view (b)
bottom view (c) side view


![](GaN-transistors-power-conversion.pdf-76-0.png)

-----

the loop is connected vertically through the PCB using vias. The LGA transistor design of
Figure 4.6 has the vertical power loop highlighted.
For this design, there is no shield layer due to the vertical structure. The vertical power loop
uses a magnetic field self-cancellation method (with currents flowing in opposite directions) to
reduce inductance, as opposed to the use of a shield plane. For the PCB layout, the board
thickness is generally much thinner than the horizontal length of the traces on the top and
bottom side of the board. As the board thickness decreases, the area of the loop shrinks
significantly when compared to the lateral power loop, and the current that is flowing in
opposing directions on the top and bottom layers begins to provide magnetic field selfcancellation. For a vertical power loop to be most effective, the board thickness must be
minimized.

###### 4.4 Optimizing the Power Loop

An improved layout technique that provides the benefits of reduced loop size, magnetic
field self-cancellation, consistent inductance independent of board thickness, a single-sided
component PCB design, yielding high efficiency for a multilayer structure, is shown in
Figure 4.7. The design utilizes the first inner layer, shown in Figure 4.7(b), as the power loop
return path. This return path is located directly underneath the top layer’s power loop, shown in
Figure 4.7(a), allowing for the smallest physical loop size combined with magnetic field selfcancellation. The side view (Figure 4.7(c)) illustrates the concept of creating a low profile
magnetic field self-canceling loop in a multilayer PCB structure.
The characteristics of the conventional and optimal designs are compared in Table 4.1.

**Figure 4.7** Optimum power loop for LGA transistor-based converter: (a) top view (b) top view of inner
layer 1 (c) side view


![](GaN-transistors-power-conversion.pdf-77-0.png)

-----

**Table 4.1** Characteristics of conventional and optimal power loop designs

Lateral loop Vertical loop Optimal loop

Single-sided PCB capability Yes No Yes
Magnetic field self-cancellation No Yes Yes
Inductance independent of board thickness Yes No Yes
Shield layer required Yes No No

This improved layout places the input capacitors in close proximity to the top device, with
the positive input voltage terminals located next to the drain connections of the top transistor.
The GaN devices are located in the same arrangement as the lateral and vertical power loop
cases. Located between the two transistors is a series of interleaved inductor node and ground
vias arranged to match the LGA fingers. The interleaved inductor node and ground vias are
duplicated on the bottom side of the synchronous rectifier.
These interleaved vias provide three advantages:

- The interleaving of the vias with current flowing in opposing direction reduces magnetic
energy storage and helps generate magnetic field cancellation. This results in reduced eddy
and proximity effects, reducing AC conduction losses.

- The vias located in between the two transistors provide a shorter high-frequency loop
inductance path, leading to lower parasitic inductance.

- The vias located beneath the lower transistor reduces resistance and accompanying
conduction losses during the transistor freewheeling period.

In Chapter 10, some comparative results for these different power loops in a hard-switching
buck converter application will demonstrate the significant efficiency improvement that can be
achieved through proper layout.

###### 4.5 Paralleling GaN Transistors

The layout considerations presented above assume that a single GaN device will be used per
switching element. For higher power applications, it may be necessary to place multiple
transistors in parallel, and have them behave like a single device. Alternatively, multiple
devices for a switching element may be required in more complex structures such as a halfbridge, where additional current paths need to be considered.

###### 4.5.1 Paralleling GaN Transistors for a Single Switch

Figure 4.8 shows an example with three parallel devices with their interconnections between
them, indicated as series resistor and inductor elements. To achieve the best possible overall
resistance matching, the drains and sources of each of the devices are connected in a diagonal
symmetry such that any additional resistance mismatch in the drain paths are mirrored and
compensated for in the source paths. This configuration is typically used in hot-swap and
similar slow switching applications where DC and low frequency current sharing is critical.
The reason that this implementation cannot be used for fast-switching converters becomes
clear when considering where to place the gate driver return connection. Choosing a
geometrically symmetrical point – for example “E” in Figure 4.8 – results in a significant


-----

Drain

**A**

**B**

**C**

Gate

Source

Gate Return **D** **E** **F**

**Figure 4.8** Schematic diagram showing three parallel devices with interconnect parasitics. The three
drain current paths (dashed lines) are designed for matched drain-to-source impedance. Positive commonsource inductance circled in dotted oval and negative CSI circled in solid oval

mismatch in CSI between the loops (dotted circles and solid circle respectively). At high
speeds, CSI is the most important parasitic element, so any high-speed layout must solve the
CSI symmetry issue.
The requirement for symmetry, in order to place GaN devices in parallel efficiently, is
illustrated conceptually in Figure 4.9. Symmetry of the power loops, the CSI components, as
well as the gate loop inductances is key to effectively paralleling GaN transistors. Even with
improved symmetry, the CSI when using multiple devices will be higher than for a single
device as the gate return connection point will be pushed further away.

Gate

Gate Return Source

Drain

**Figure 4.9** Conceptual schematic diagram showing three parallel devices with interconnect parasitics
designed for complete symmetry. Common-source inductance circled in dotted oval and drain current
paths shown in dashed lines


-----

A layout with complete symmetry can be challenging. When considering the priority of these
different parasitic components, the need for symmetry in CSI is foremost. Second would be the
power loop (or, for a single switching element, the common drain-to-source inductance outside
the transformer). Last is the gate drive loop inductance, as the gate drive speed and power
always will be lower than that of the switching device itself. Following the above requirements
for complete symmetry and applying the magnetic field self-canceling approach through
interleaved vias and opposing currents in neighboring PCB layers, it is possible to generate an
adequate solution using LGA GaN transistors, as shown in Figure 4.10.

Gate
Resistors

Interleaved Drain
/Source Vias

(a) Top Layer

Gate-Return Source Plane

Direction of Gate Current out of Devices

(b) Second Layer (First Inner Layer)

**Figure 4.10** Layout for four parallel LGA GaN devices

|Gate Resistors|Col2|
|---|---|
|Resistors||
|||
|||
|||


-----

(c) Third layer (Last Inner Layer)

Power Source Plane

Direction of Source Current out of Devices

(d) Bottom Layer

**Figure 4.10** Layout for four parallel LGA GaN devices (Continued)

One advantage that GaN transistors have over MOSFETs when placing them in parallel is
a positive temperature coefficient in the transfer characteristic over the whole gate voltage
range. This means that even during transition, the saturation or triode region of GaN
transistors will share current to some extent due to the negative temperature feedback effect.
Thus, if one device carries too much current it will heat up relative to the other devices, its
on-resistance and plateau voltage will go up, and thus the current in the device is reduced


-----

automatically. In a MOSFET during parallel switching, the reduction of threshold voltage
with increasing temperature can cause the current to increase, and thus an imbalance between
devices can occur.
The key elements that have been integrated in a design with four GaN transistors connected
in parallel to generate a single switching element can be summarized as follows:

- On the top layer, the devices are placed in a row, with four being the maximum number one
would place in parallel before mirroring this design around another axis.

- All the devices have their drain and source terminals extending on both sides of the device to
minimize drain and source inductance. These traces are then connected immediately down
to all the subsequent PCB layers through a number of parallel and interleaved vias to further
reduce inductance as much as possible.

- The gate of each of the devices is connected through separate pull-up and pull-down
resistors, one per device. This allows for independent adjustment of the device switching
speed as needed.

- On the second layer, the gate-return source connection is made directly to all the source vias
and is not externally connected to any other part of the power circuit. This minimizes the CSI
and isolates the gate drive from the power loop.

- On the third layer, both pull-up and pull down gate driver outputs are bused across to each of
the devices, and then through the vias up to the gate resistors on the top layer. Thus, the gatereturn path on layer two is sandwiched between the gate drive conductors on both adjacent
layers.

- The power loop drain connection is also made on the third layer. The drain current flows up
towards the devices before distributing laterally in both directions from the drain vias to the
top layer.

- On the bottom layer, the power loop source connection is made. The source current flows
down, away from the devices, after distributing laterally in both directions once through the
source vias from the top layer. The third and bottom layers are adjacent, and the drain and
source currents in these layers are of equal and opposite magnitude, allowing for magnetic
field self-cancellation and minimizing loop inductance.

###### 4.5.2 Paralleling GaN Transistors for Half-Bridge Applications

For paralleling devices in half-bridge applications, the above layout approach may work, but it
does not provide an optimal solution due to some practical limitations. To form a half-bridge,
consider another switching element with multiple parallel devices placed in mirror image
below that of Figure 4.10. This will result in a layout with gate drivers on opposite edges of the
power device layout. This configuration is not suitable for a single half-bridge gate driver, but
could be implemented with a separate floating gate driver for each group of parallel devices, as
long as a suitable symmetrical layout for bringing out the switch node can be achieved.
Alternatively, the other switching element should be mirrored along the left or right side of the
layout as shown in Figure 4.10. This would result in a single gate driver along the top edge of
the layout, but the high-frequency power loop will run left to right (or right to left), resulting in a
mismatch in common-source inductance similar to the equivalent circuit shown in Figure 4.8.
Although both above approaches are possible, a better alternative would be to place in
parallel complete half-bridge power loops, rather than individual devices. A conceptual


-----

Low Frequency Current Path

Power Power
Loop Loop

Gate
Current

Gate
Current

**Figure 4.11** Schematic diagram showing two parallel half-bridge power loops with common gate
driver. High-frequency current paths are shown in dashed lines for power loops and dotted lines for
gate drive loops. Low-frequency current path are shown in dash-dot lines. Common-source inductance
indicated in ovals

schematic for two such loops is shown in Figure 4.11. At first glance this may seem
counterintuitive, as this solution will result in larger inductances between the DC supply
terminals, but these additional inductances do not carry any high-frequency currents. Following the same order of layout requirements as before, a complete half-bridge layout with four
parallel power loops is shown in Figure 4.12. An example comparing these paralleling
approaches and verifying the performance advantage of the parallel loop approach is shown
in Chapter 10.


-----

(a) Top layers


(b) Second layer


(c) Third layer (d) Bottom layer

**Figure 4.12** Suggested layout for a half-bridge converter with four parallel devices per switch in a
parallel power loop layout


-----

As before, the different key elements that have been integrated in the four parallel power
loop design for a half-bridge are summarized as follows, with reference to Figure 4.12:

- On the top layer, the optimum layout from Figure 4.7 is mirrored in both the x- and y-axes
with the single gate driver placed in the center of the layout that drives all eight devices.

- The gate of each of the devices is connected through separate pull-up and pull-down
resistors, one per device. This allows for independent adjustment of the device switching
speed as needed.

- On the second layer, the gate-return source connections are made directly to just one set of
the source vias, and are not connected to any other part of the power circuit (note the two
separate ground planes). This minimizes the CSI, isolates the gate drive from the power
loop, and keeps the gate loop inductances symmetrical.

- Also, on the second layer are the power loop ground returns that form the basis of the
optimal layout. The arrows show the flow of the high-frequency power loop current from the
source of the bottom device towards the ceramic high-frequency bus capacitor.

- On the third layer, both pull-up and pull-down gate driver outputs are bused upwards and
downwards to each of the devices, and then through the vias up to the gate resistors on the
top layer. The high-side gate-return path on layer two is sandwiched between the gate drive
conductors on the adjacent layers.

- The switch-node connection is also made on the third layer. The low-frequency switch-node
current flows down from the devices on either side before combining towards an inductance
element (not shown).

- On the bottom layer, the low-side gate return connection is made in an adjacent layer to the
low-side gate driver outputs on layer three, thus preserving the loop magnetic field canceling
effects. The low-frequency, or DC-current positive bus connections are made on this layer as
well.

The actual implementation in Figure 4.13 shows how compact the parallel loop layout
can be.

**Figure 4.13** Half-bridge converter with four parallel devices per switch in a parallel power loop layout


![](GaN-transistors-power-conversion.pdf-85-0.png)

-----

###### 4.6 Summ ary

In this chapter, layout parasitics that are impor tant when using G aN transistors w er e
discussed; namely the common-source inductance, the high-frequency power loop inductance, and the gate loop inductance. A num ber of methods to minimize these i mportant
parasiti cs were reviewed, s tarti ng wit h t he mo st basic s ingle transistor, through a com pl e te
half-bridge configurat ion and, finally, looking at t he placement of multiple devices in
parallel to behave as a singl e device f or both a s ingle-switching element and a half-bridge
appl ication.
The next step is to understand the actual behavi or of these device s in-circui t. This requires
not simply measuring circuit elements accurately, but also good elect rical and thermal
model ing approxi mations of a spects that cannot be measured direc tly. The se wi ll be discussed
in Cha pter 5.

###### References

1. Infineon, “ThinPAK 8X8 New High Voltage SMD-Package, ” Version 1.0, April 2010. Available from [http://www.](http://www.infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?folderId=db3a304314dca38901152836c5a412ab&fileId=db3a304327b897500127f6946a286519)
[infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?](http://www.infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?folderId=db3a304314dca38901152836c5a412ab&fileId=db3a304327b897500127f6946a286519)
[folderId=db3a304314dca38901152836c5a412ab&fileId=db3a304327b897500127f6946a286519.](http://www.infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?folderId=db3a304314dca38901152836c5a412ab&fileId=db3a304327b897500127f6946a286519)
2. Zhou, L., Wu., Y.F., and Mishra, U. (2013) True-bridgeless totem-pole PFC based on GaN HEMTs,” _PCIM Europe_
_2013, pp. 1017–1022._
3. Efficient Power Conversion Corporation, “eGaN FETs in high performance DC-DC conversion,” _EDN Innovation_
_Awards Conference and Awards, Shanghai, China, 2011, p. 28. Available from_ [http://epc-co.com/epc/documents/](http://epc-co.com/epc/documents/presentations/EDN_Innovation_Conference_120111.pdf)
[presentations/EDN_Innovation_Conference_120111.pdf.](http://epc-co.com/epc/documents/presentations/EDN_Innovation_Conference_120111.pdf)
4. Di rect Energy, Inc., “ The dest ructiv e effects of Ke l vin l eaded package s in high speed, hi gh frequency operatio n,”
Fort Col lins, Colorado, T ech No te 920 0-0002-1, 1998. Avail able from [ww w. dir ecte denergy.com/i ndex.](http://www.directedenergy.com/index.php?option=com_joomdoc&task=document.download&path=ixysrf%2Fapplication-notes%2Fde-series-fast-power-mosfet)
[ph p?optio n=com_jo omdoc &t ask=doc um ent.do w nlo ad&path=ixysrf%2Fappl ication -notes%2F th e-destructi ve-](http://www.directedenergy.com/index.php?option=com_joomdoc&task=document.download&path=ixysrf%2Fapplication-notes%2Fde-series-fast-power-mosfet)
[effects- of-kelvin- leaded-packages-in- high-sp eed-high-frequency-operation.](http://www.directedenergy.com/index.php?option=com_joomdoc&task=document.download&path=ixysrf%2Fapplication-notes%2Fde-series-fast-power-mosfet)
5. Krausse, G.J. “DE-Series fast power MOSFET, an introduction,” Directed Energy, Inc., Fort Collins, Colorado, Tech
Note 9300-002 Rev 3, 2002. Available from [www.directedenergy.com/index.php?option=com_joomdoc&task=](http://www.directedenergy.com/index.php?option=com_joomdoc&task=document.download&path=ixysrf%2Fapplication-notes%2Fde-series-fast-power-mosfet)
[document.download&path=ixysrf%2Fapplication-notes%2Fde-series-fast-power-mosfet.](http://www.directedenergy.com/index.php?option=com_joomdoc&task=document.download&path=ixysrf%2Fapplication-notes%2Fde-series-fast-power-mosfet)
6. Reusch, D. and Strydom, J. (16–21 March 2013) “Understanding the effect of PCB layout on circuit performance
in a high frequency gallium nitride based point of load converter,” OT Twenty-Eighth Annual IEEE Applied Power
_Electronics Conference and Exposition (APEC), Long Beach, CA, pp. 649–655._


-----

# 5

#### Modeling and Measurement of GaN Transistors

###### 5.1 Introd uction

The previ ous chapte r focuse d on the layout parasi tics that are importan t when using GaN
transist ors, and show ed methods of minim izing these parasiti cs for layout s wi th vario us levels
of complexit y. In this chapte r, the focus will be on how best to understand and predi ct the actual
in-circui t behavi or of the GaN trans istors once the layout has been compl eted. Althoug h
measu rement and modeling are very d ifferent, they compleme nt each other when atte mpting to
better unders tand real- world behavi or. The initial discu ssion will focus on the elect rical and
thermal model ing of GaN transistors, and conclude with discussi on of the requi rements and
limitati ons when direc tly meas uring in-circui t behavi or.

###### 5.2 Electric al Modeling

Accurate electrical modeling of in-circuit GaN transistor behavior can be challenging. Apart from
the active device characteristics, there is an additional need to model the high-frequency parasitic
elements, such as layout inductance and skin and proximity effects. Most of these parasitics are
package-dependent and cannot be modeled readily within a generic GaN transistor model. Also,
cascode structures require not just an accurate model of both the active elements, but also a highfrequency model including all parasitic interconnect elements between the two devices.
Althoug h enhan cement-m ode device s are made to operat e similarly to silicon MOSFETs,
they cannot be readily model ed with traditi onal ph ysics-base d MOS FET models, such as
BSIM3 [1], as the physics of the GaN transisto r is signifi cantly different . A wi dely available
model [2] for en hancement- mode GaN transist ors and the methodol ogy used in its develo pment will be discussed in the foll owing secti on.

###### 5.2.1 Basic Modeling

SPICE models use an equiva lent circu it for a device, consi sting of vario us building blocks such
as curren t source s, resistor s, cap acitors, and inductors to emul ate the actual in-circui t device

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

G_EXT


D_EXT
D_EXT

RG CGD (VGS1 VDS) RD

G_EXT

G D

CGS (VGS,VDS) ID (VGS,VDS) CGS (VGS,VDS)

S

RS

S_EXT

S_EXT

**Figure 5.1** Equivalent circuit implemented by the GaN transistor model in [2]

|Col1|Col2|Col3|R )|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||I (V GS,V DS) D||
||||D||I (V GS,V DS) D||
||||||||
||||S||||
||||S||||


behavior. The cross section of the device structure in reference [2] and shown in Figure 1.16,
will be the basis for the model discussed throughout this section.
The basic equivalent circuit for an enhancement mode GaN transistor is shown in Figure 5.1.
The main components are: a voltage-controlled current source ID, capacitors, CGD, CGS, and
CDS, and the termination resistors, RS, RD, and RG. The DC characteristics of the device depend
on the voltage-controlled current source and the equivalent circuit resistances, while the AC
characteristics also depend on the parasitic capacitors that vary with the bias conditions of the
device. Thus, the equivalent circuit components are as follows:

1. Drain current (ID) is a non-linear function of voltages at internal nodes D, G, and S.
For VD > VS: ID > 0 and for VD < VS: ID < 0
2. Gate-source capacitance (CGS) is a non-linear function of voltages at internal nodes D, G,
and S.
3. Gate-drain capacitance (CGD) is a non-linear function of voltages at internal nodes D, G,
and S.
4. Output capacitance (COSS) is a non-linear function of voltages at internal nodes D and S.
5. Drain termination resistance (RD) is a constant resistance that depends on the device and
package termination resistances.
6. Source termination resistance (RS) is a constant resistance that depends on the device and
package termination resistances.
7. Gate termination resistance (RG) is a constant resistance that depends on the device and
package termination resistances.

The DC current–voltage models for the GaN transistor can be similar to MOSFET
models [1]. In the current model, the non-linear current response is the result of saturation
current that is gate-to-source voltage-dependent, with a drain-to-source voltage-dependent
shaping function. For the GaN transistor model, various parameters were obtained by fitting
the output curves from a large number of devices. The temperature dependence of the


-----

100

80


60

40


20

0
0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||25°C 125°C||||||||
|||||||||||
|||||||||||
|VD|VD|S=3 V||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
||||||||||||
|||||||||VG V|S = 5 = 4||
|||||||||G VG|S S = 3||
|||||||||VG|S = 2||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||


0.5 1 1.5 2 2.5 3 3.5 4 4.5

**VGS – Gate-to-Source Voltage (V)**


100

90

80

70

60

50

40

30

20

10


0.2 0.4 0.6 0.8 1 1.2 1.4 1.6 1.8 2

**VDS – Drain-to-Source Voltage (V)**


0
0


**Figure 5.2** Transfer and output curves for EPC2001 device model


current–voltage characteristics were also included. Figure 5.2 shows an example of the
device’s transfer and output characteristics.
Unlike the silicon power MOSFET, enhancement-mode GaN transistors do not have a
conventional body diode. As discussed in Chapter 1, the channel under the gate can be
enhanced in either the forward or reverse direction, which gives rise to an electrical
characteristic similar to the MOSFET body diode. The SPICE model accounts for this by
having two parallel current sources connected in opposing orientation. Figure 5.3 shows the
forward versus reverse output curves of an EPC2001 part.
The three capacitances in the equivalent circuit shown in Figure 5.1 are comprised of several
elements that depend on the underlying device geometry, and vary based on the physics of the

25

Gate Tied to Source Gate Tied to Drain

20

15

10


5

0


–5

–10

–15

–20

–25

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||Gate T|ied to S|ource|||Gate|Tied to|Drain|||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||


–2.5  –2   –1.5  –1   –0.5   0    0.5   1   1.5   2   2.5


**Drain-to-Source Voltage VDS (A)**

**Figure 5.3** Forward and reverse current as function of drain-to-source voltage showing the symmetric
nature of the device


-----

**Figure 5.4** Schematic cross section of a device showing locations of various capacitances. Some of the
metal layers are omitted for simplicity

device. These elements consist of both the constant metal-to-metal capacitance and the voltagedependent capacitances associated with the 2DEG in the channel layer; and are shown in
Figure 5.4. For modeling purposes, the substrate is shorted to the source and the various
substrate capacitances are assigned to the source terminal. All these separate parasitic
capacitances are modeled through two equivalent lumped-capacitance components for each
of the three equivalent circuit capacitors: one constant capacitor and one non-linear voltagedependent capacitor, thus yielding six equivalent capacitors overall. The non-linear equivalent
capacitors are modeled using semi-empirical fits to measured values. Rather than using highorder polynomials, the models employ sum of sigmoid (or Fermi) functions. These functions
provide a close fit to the data, and have better stability and convergence properties during
simulation.

###### 5.2.2 Limitations of Basic Modeling

The equivalent circuit models only account for the capacitive elements of the device’s
frequency-dependent behavior. In many cases, silicon power MOSFET models also include
packaging inductance to accurately represent the high-frequency terminal characteristics of the
packaged device. These inductances can be significant with respect to the overall non-device
layout inductances, and thus cannot be omitted. As a result, and in most cases, these equivalent
MOSFET circuits will give representative modeling results, even when layout parasitics are
omitted.
For the LGA enhancement-mode GaN transistor with virtually no packaging inductance,
layout inductance is dominant, and the way in which the layout interacts with the resultant
packaging inductance is shown in Figure 5.5. Since this cannot be taken into account on a
device-model level, parasitic inductance needs to be added as an additional component for
accurate system modeling.


-----

Vias Drain

|LGA GaN Transistor Drain Vias|Col2|Vias|Col4|Col5|Col6|Drain|Col8|n|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
||||||||||||


Source


(a)


Copper
Traces


(b)


**Figure 5.5** Impact of device termination on packaging and layout inductance through changes in PCB
layout (a) dual-sided termination with flux cancellation (b) single-sided termination with no flux
cancellation

A simulation model example with parasitic layout inductance included is shown in
Figure 5.6. This model can be used to match the switch-node waveform of a GaN transistor-based buck converter to the experimental results of a simple power stage [3].
The simulation data can then be compared to the experimentally measured waveform shown
in Figure 5.7. There is good correlation between the results, and in particular the ringing
frequency, which is dependent on the parasitic inductances and non-linear device capacitance.

LLOOP

.param LG 1nH

100pH .step param CSI list 100pH 500pH 1000pH

LD_U2 VBUS .param dt 5ns

+

100pH

.tran 0 (.05u+TP) (TP) – .param VBUS = 60

RHOH GProbeH GateH EPC2001U2 (VBUS) .param VOUT = 30.param ton = 1000n

VgateH +– DHOL2 LG_U2(LG) RPCB_U21 LCSI_U2(CSI) .param TP = 2000n.param IL = 10

MyD

VSW LBUCK OUT

Upper Gate Driver 10µH ILOAD

CBUCK

.model myd d (Vfwd = 0.1 Ron = 0.67)) 1µF (IL)

VgateL RLOH2 LG_U1GProbeL GateL1 U1 EPC2001 device voltageTheoretical .lc I(LBUCK) = 8.5A.lc V(OUT) = 30V

+– DLOL (LG) RPCB_U1 LCSI_U1

MyD (CSI) Practical measurement

across bottom device

Lower Gate Driver

**Figure 5.6** LTSPICE schematic of a buck converter power stage with layout parasitics included


![](GaN-transistors-power-conversion.pdf-91-0.png)

LLOOP

100pH

LD_U2 VBUS

+

100pH

–

U2 (VBUS)

GProbeH GateH

EPC2001

1
RPCB_U2 LCSI_U2

(CSI)


![](GaN-transistors-power-conversion.pdf-91-1.png)

LBUCK

VSW

10µH

CBUCK

1µF

U1 Theoretical

GProbeL GateL EPC2001 device voltage

1
RPCB_U1

LCSI_U1
(CSI)


![](GaN-transistors-power-conversion.pdf-91-2.png)

.param LG 1nH
.step param CSI list 100pH 500pH 1000pH
.param dt 5ns

.param VBUS = 60
.param VOUT = 30
.param ton = 1000n
.param TP = 2000n
.param IL = 10

OUT

ILOAD


-----

![](GaN-transistors-power-conversion.pdf-92-0.png)

**Figure 5.7** Switch node voltage versus time obtained for a 28 V to 3.3 V buck at 15 A. (a) simulation
data (b) measured data [3]

From this simulation, the in-circuit power loop inductance can be estimated to be about 400 pH.
The voltage overshoot damping rate is dependent on the skin and proximity effect losses at the
ringing frequency. To approximate this, a parallel damping resistance of 1 Ω is placed across
each of the parasitic inductance elements. The choice of this resistance value will depend on the
frequency of oscillation, as SPICE is incapable of directly modeling this frequency-dependent
resistance component.

###### 5.2.3 Limitations of Circuit Modeling

The circuit modeling results will only be as good as the accuracy and complexity of the circuit
model used. To best illustrate this point, simulations with varying levels of complexity were
made, and the efficiency results for each simulation were calculated versus load current and
compared against an actual experimental result as shown in Figure 5.8. The simulated converter
efficiency was calculated by measuring the steady-state input and output power, and integrating these over a sufficiently large number of switching cycles.


-----

100

95


90

85


80

75


70

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
||||||||||||||||
||||||Sim Sim|ulation ulation|of Sc Includ|hemat ing L|ic Ele ayout|ments R and|L||||
||||||||||||||||
||||||Sim Sim|ulation ulation|with Includi|R, L a ng R a|nd Add nd L, A|ing G dding|ate Dr Core a|iver Lo nd Gate|sses Drive|Losses|
||||||||||||||||
||||||Exp|erime|ntal D|ata|||||||
||||||||||||||||


0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15


**Output Current (A)**

**Figure 5.8** Comparison of simulated and measured efficiency for a 12 V to 1.2 V buck converter for
varying levels of model complexity


First, by building a simulation circuit without the required layout resistances and inductances
(purely the equivalent schematic elements), the resultant efficiency is over 5% higher than
experimental results. With these parasitic impedance components included, this error drops to
about 2% higher at heavy load. Then, with both the inductor core and the gate drive losses
added to the simulated input power, there is excellent correlation between simulated and
experimental results.

###### 5.3 Thermal Modeling


In general, the thermal modeling of GaN transistors is no different than that of MOSFET
devices. For high-voltage parts, traditional through-hole and PQFN-type packages typically
are used. These plastic over-molded packages are thermally insulated on the one side, with
the main direction of heat removal down through the case of the device. For such devices,
heat flow is mainly one-dimensional as described in Chapter 2. For package-less devices,
such as the LGA GaN transistors, the devices are flipped upside down and the back surface –
the “case” – of the device is mounted away from the PCB. This arrangement is thermally
similar to other “flipped” devices, such as wafer-level chip-scale packages and DirectFET[]

MOSFETs [4], and has two distinct thermal heat dissipation paths, as shown in Figure 5.9
and described travelling:

1. down through the LGA pads, solder bars and into the PCB
2. up through the back of the die (case). If a heatsink is used, the heat passes through a thermal
interface material and through the top-side heatsink. Without a heatsink, a small amount of
heat can still flow through the top of the die, but only by means of radiation and convection.

The electrically equivalent thermal resistance model for each of these two mounting
approaches with a single device is shown in Figure 5.10. For the electrically equivalent
circuits, the heat flux generated within the part is modeled through an equivalent power-loss


-----

Double-Sided Cooling


Convection/
Radiation Only

RθCA

RθJC

RθJB


RθSA


RθTIM

|Col1|A|Col3|Col4|aterial|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
|R|θJC||Silicon Substrate|R||θJC|
|||||gion R|||
||Copper Traces||||||


RθJC Silicon Substrate RθJC


Printed Circuit Board


(a) (b)

**Figure 5.9** Thermal diagram of board-mounted LGA GaN transistor showing thermal paths (a) without
and (b) with heatsink

current source. In both approaches, the two thermal paths are in parallel, effectively lowering
the overall thermal resistance to ambient and improving the power-handling capability. Plastic
over-molded packaged devices can also be modeled, using Figure 5.10(a), for large case-toambient temperature deltas where radiation and convection heat flow become significant.

###### 5.3.1 Improving Thermal Performance

For traditional PQFN-packaged devices, the thermal resistance down through the PCB
becomes the limiting factor, as this is the main heat flow path. This can be improved through

Double-Sided
Cooling


Convection/
Radiation Only


RθCA

RθJC


Case Temp (TC)


RθSA
Heat Sink Temp (TS)

RθTIM

Case Temp (TC)


Junction Temp (TJ)

Board Temp (TB)

Ambient (TA)


Power Junction Temp (TJ) Power
Loss Loss

RθJB

Board Temp (TB)

RθBA

Ambient (TA)


RθJC

RθJB

RθBA


(a) (b)

**Figure 5.10** Electrically equivalent circuit thermal models of the LGA GaN transistor (a) without and
(b) with heatsink


-----

|Thermal Vias PQFN|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
|||||||||||||||PCB|
|Heatsink|||||||||||||||


**Figure 5.11** Thermal diagram of board-mounted PQFN device with thermal vias and opposite side
heatsink to improve thermal performance

the addition of multiple thermal vias, allowing improved heat flow through the PCB [5]. On the
opposite side, a heatsink typically is added to reduce PCB-to-ambient thermal resistance as
shown in Figure 5.11.
For the LGA GaN transistor, thermal resistance improvements to both thermal heat paths can
also be made, as shown in Figure 5.12. First, the PCB-to-ambient thermal resistance can be
reduced through the addition of thermal vias (similar to the PQFN case), but with the thermal
vias connecting to internal and external copper layers to spread the heat laterally. Second, the
thermal interface material (TIM) resistance can be reduced:

1. by reducing the thickness of the device-to-heatsink interface: typically some form of spacer
between heatsink and devices is required together with a TIM, as any mounting force
applied to the heatsink cannot be transferred to the device for fear of cracking. This spacer
determines the minimum distance between the heatsink and the GaN devices.


PCB

|Spacer|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||LGA||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||


Thermal Interface Material Copper Heat Spreading

**Figure 5.12** Thermal diagram of board-mounted LGA GaN transistors with dual-sided cooling showing
top-side heatsink and thermal vias with heat spreading through PCB


-----

Perimeter of die adds additional surface area

**Part** **Die Area** **Perimeter**
**Number** **(mm[2])** **Area (mm[2])**

EPC2001

6.70 7.86

EPC2015

EPC2007

1.85 3.82

EPC2014

EPC2010 5.80 7.10

EPC2012 1.57 3.60

**Figure 5.13** Diagram of an LGA GaN transistor showing the die surface area and area of die perimeter

2. by placing the thermal interface material on all sides of the devices and not just the top
(case): this reduces thermal resistance, as the surface area of the device perimeter side walls
is larger than the top surface, as shown in Figure 5.13.

Further improvements are possible by utilizing dual-sided heatsinking, forced-air cooling,
and through the use of exotic PCB materials, such as direct bonded copper (DBC) [6], or
insulated metal substrate (IMS). Regardless of the thermal solution used, it is possible to model
the overall thermal system using an electrically equivalent circuit thermal model. Some values
for the device thermal resistances (RθJC, RθJB) are given in the datasheet; some resistances are
configuration-specific, such as the PCB-to-ambient thermal resistance RθBA. Values for the
thermal resistance of the heatsink and thermal interface material can be extracted from their
datasheets, whereas the thermal resistance for convection and radiation are configuration- and
size-dependent, as well as temperature- and orientation-dependent. Furthermore, considering
multiple devices and heat sources within a configuration increases the overall complexity of
the model.

###### 5.3.2 Modeling of Multiple Die

Due to the complexity of multiple heat sources, it is necessary to determine the components of
thermal resistance beforehand. One method for estimating thermal resistance requires initial
temperature calibration of the heat-generating transistors. This is done by utilizing a known
relationship between junction temperature and on-resistance. Placing a device in a controlled
thermal chamber and monitoring the RDS(on) versus temperature yields such a relationship,
as shown in Figure 5.14. With the exact relationship between temperature and on-resistance
for each device known, the system can be heated such that the in-circuit on-resistance can
be monitored.
Consider an example of two devices mounted on the same board without heatsink cooling as
shown in Figure 5.15. With their on-resistance as a function of temperature known, these
devices can be heated by passing a known current through both devices and measuring their incircuit on-resistance. The board temperature, as close as possible to each device, also can be
measured using a thermal infrared camera. The results of these measurements are shown in
Figure 5.16. If there were no heat flowing through the top (case) of the devices, then the


-----

1.8

1.6


1.4

1.2


1

Normalized to 25 °C

0.8
–20 0 20 40 60 80 100 120 140

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||I|= 6A D V = 5 GS|V||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||Norma|lized to|25 °C||


**TJ-Junction Temperature (°C)**

**Figure 5.14** Normalized on-resistance vs. temperature for an LGA GaN transistor [7]


estimated junction temperature, based on the measured PCB temperature and device thermal
resistance, would match that of the measured junction temperature. Figure 5.16, however,
shows that this is not the case, and that the amount of heat flowing through the top is increasing
with temperature, as expected for a radiating device.
With the junction, board, and ambient temperatures known, as well as the device thermal
resistances and power losses, an electrically equivalent circuit thermal model can be constructed by first calculating the amount of heat flux down into the PCB from each device. The
resultant thermal model with estimated thermal resistance values is shown in Figure 5.17
(values were chosen to yield a symmetrical system). The total resistance split between the
spreading resistances (RθSP1 and RθSP2) and the PCB-to-ambient resistance (RθBA) is determined by the temperature difference between the measured PCB temperatures at the two
devices. This example also shows that a significant fraction of the total losses are dissipated
through the case, even though no heatsink was attached. From the results in Figure 5.17, the
following determinations can be made:

RθCA1 RθCA2

RθJC1 Device 1 Device 2 RθJC2

RθJB1 RθJB2


RθJC1 Device 1


RθBA

**Figure 5.15** Thermal diagram of two board-mounted LGA GaN transistors without heatsink


Device 2 RθJC2


-----

75

70

65

60

55

50

45

40 Device 1 Junction Temp.

Device 2 Junction Temp.

35

Device 1 PCB Temp.

30

Device 2 PCB Temp.

25

20

0.2 0.3 0.4 0.5 0.6 0.7

|Col1|Col2|co o lin|Col4|g|Col6|Col7|
|---|---|---|---|---|---|---|
||o|to p -sid e|||||
||u m in g n||||||
|e|m p a ss||||||
|ju n ctio n t|||||||
|E st.|||||||
||||||ction Temp.||
|||||Device 1 Jun|ction Tem||
|||||Device 2 Jun|ction Tem|p.|
|||||Device 1 PC|B Temp.||
|||||Device 2 PC|B Temp.||
||||||||
||||||||


**Power Dissipation in Each Device (W)**

**Figure 5.16** Measured device junction and PCB temperature vs. power dissipation for the two LGA
GaN transistors [7] mounted on a PCB [8]


1. The thermal resistance of the top surface (case) of the LGA GaN transistor to the ambient air
with no airflow (RθBA1 and RθBA2) is about 120°C/W, at around 70°C, but varies with case
temperature.
2. The thermal spreading resistance between the two transistors mounted next to each other on
the PCB (RθSP1 and RθSP2) is about 10°C/W.
3. The thermal resistance through the PCB-to-ambient (RθBA) is about 60°C/W in still air.
4. The effective junction-to-ambient thermal resistances for each of the devices is between
69°C/W and 74°C/W, due to the thermal interaction of the two devices. With only one
device dissipating heat, the effective thermal resistance decreases to about 50°C/W.

0.335 W 0.335 W


TA


27°C


(a) (b)

**Figure 5.17** Electrically equivalent circuit thermal model of the LGA GaN transistor PCB with two
devices, no heatsink, and only convection cooling: (a) parameters (b) resultant values


-----

With the thermal resistance model complete, the system thermal performance can be
estimated for varying operating conditions.

###### 5.3.3 Modeling of Complex Systems

More complex systems with additional non-device-related losses can be addressed in a similar
fashion as for two devices. For example, consider an envelope tracking buck converter
with the thermal diagram shown in Figure 5.18. (This converter will be discussed in detail in
Chapter 10.) To improve the thermal performance, a 15 mm square, 9.5 mm tall finned heatsink
was added above the LGA GaN transistors. A forced airflow of 200 linear feet per minute
(LFM) was used across both PCB and heatsink. In order to ensure adequate clearance between
the heatsink and the 30 mil thick LGA device, the heatsink was attached to the board using Gap
Pad[] GP 1500 (60 mils/1.5 mm thick) [9] as spacer over half the heatsink area, while the area
covering the GaN transistors was filled using two layers of Sarcon 30x-m [10]. The two layers
have a total thickness of 60 mils (1.5 mm) and are able to conform around the die when
compressed. This allows the die to conduct heat from the sidewalls as well as from the top
surface (case). The heatsink was offset to barely cover the devices such that the temperature
of the PCB directly adjacent to the devices could be measured using an infrared camera.
A complete discussion on the component loss breakdown is given in [11].
The electrically equivalent circuit thermal model for this example is shown in Figure 5.19(a),
with the resultant thermal resistance values and temperatures for full-load operation shown in
Figure 5.19(b). Thermal resistance values for the heatsink and devices were taken from their
datasheets, while the TIM thermal resistance was estimated based on the die contact area and
material thickness. For the PCB spreading resistance, the values from Figure 5.17 were used,
since the board layout was almost identical. With the loss breakdown known, the PCB-toambient resistance was adjusted until good correlation with the measured PCB temperature was
achieved. This resulted in a PCB-to-ambient thermal resistance (not including spreading
resistance) of about 5°C/W for this forced-air cooling condition, and is significantly lower that
for the still-air example.

RϴSA

Additional RϴCTIM1 RϴCTIM2
Non-Device RϴJC1 Device 1 Device 2 RϴJC2
Losses
RϴJB1 RϴJB2

RϴSP1 RϴSP2

RϴBA

**Figure 5.18** Thermal diagram of two board-mounted LGA GaN transistors with heatsink cooling on a
PCB with additional non-device losses

|R ϴCTIM1 R ϴCTIM2 Additional Non-Device R ϴJC1 Device 1 Device 2 R ϴJC2 Losses R ϴJB1 R ϴJB2|Col2|
|---|---|
|||
|||


-----

Device 1Loss TJ1 TJ2 RθθJB2JC2 Device 2Loss

TB1 RθSP1 RθSP2 TB2

Other
Loss

RθBA

TA


0.52 W


TA


20°C


(a) (b)

**Figure 5.19** Electrically equivalent circuit thermal model of the LGA GaN transistor-based buck
converter with heatsink and forced-air cooling: (a) parameters (b) resultant values at full load

###### 5.4 Measuring GaN Transistor Performance

The increase in switching speed offered by GaN transistors with their accompanying faster
di/dt and dv/dt, requires a proportional increase in the bandwidth of the measurement equipment
used. First-generation GaN transistors were generating speeds close to the limit of the present
oscilloscope and probe technology, making it likely that the GaN power transistor revolution will
be accompanied by a corresponding step change in measurement technology. To determine the
extent of these requirements, each different measurement will be evaluated in turn.

###### 5.4.1 Voltage Measurement Requirements

To determine the requirements for voltage measurement of the high dv/dt switching waveforms, it is necessary to relate the fidelity requirements of switching waveforms with the
bandwidth (BW) requirements of the oscilloscope and accompanying probes. The relationship
between rise time and bandwidth is typically given by Equation 5.1, and is based on a number
of assumptions [12].

0.35
trise(10%�90%)  BW�3dB (5.1)

The resultant rise time from Equation 5.1 assumes that measuring an infinitely fast rising edge
will yield the given measured rise time. This does not mean that a waveform with this actual
rise time will be represented accurately on an oscilloscope. To yield an accurate representation
of the waveform rise time, a rule of thumb is that a bandwidth between three and five times that
of Equation 5.1 is required [12].

k ? 0.35
BW�3dB  trise(10%−90%), k is between 3 and 5 (5.2)


-----

Thus, for a waveform with a 1 ns rise time, Equation 5.2 would require an overall bandwidth of
between 1.1 GHz to 1.8 GHz. However, the oscilloscope alone cannot measure the switching
waveforms. A voltage probe, with its own associated bandwidth limitations, is also required.
For such a cascade system, the effective rise time is given by the root-mean-square (RMS) of
separate component rise times. This can be expressed in terms of component bandwidths as in
Equation 5.3 [13]:

1
BW�3dB  sffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi (5.3)

1 1

BW[2]�3dB,Scope BW[2]�3dB,Probe


The oscilloscope and probe each need to have a bandwidth in excess of the overall required
bandwidth. Although oscilloscope bandwidths in excess of 2 GHz are readily available,
voltage probe capabilities are limited, and they decrease with increasing voltage range.
Table 5.1 shows voltage probes suitable for GaN transistor measurement and their related
voltage and rise-time capability. Higher-bandwidth passive and active probes are available,
but these are limited to a maximum voltage of about 15 V, which is too low for most GaN
transistor applications.
At these high frequencies and voltages, having sufficient rise-time capability alone isn’t
enough to make useful voltage measurements. It is also important to place the probe as close to
the required measurement point as possible while generating an inductive loop that is as small
as possible. A practical example to achieve this is shown in Figure 5.20. The probe loop needs
to be minimized for two reasons:

1. The high impedance of the probe, coupled with the fast-changing currents (and associated
magnetic fields), will induce noise in the probe, through electromagnetic induction. This
can be mitigated by limiting the loop area and choosing the loop orientation to avoid flux
coupling.
2. The probe impedance in series with the loop inductance forms an LC resonant tank that not
only reduces bandwidth, but also generates oscillations not present in the actual measurement [14], as the probe gain becomes more than unity at resonance. The impact of a given
loop inductance is more pronounced in a probe with higher capacitance. In short, if the
waveform being measured has a fast enough rise time to contain within its Fourier spectrum
the probe loop resonant frequency, then the probe itself will oscillate.

**Table 5.1** Voltage probes and their associated voltage, bandwidth, and minimum rise time

Attenuation Input Bandwidth Maximum Rise time
impedance voltage (Equation 5.2)

High-end passive 10:1 10 MΩ/ 500 MHz 300 V 2.1–3.5 ns
probe ∼10 pF

LeCroy PP065 100:1 5 kΩ/2 pF 1 GHz 30 V 1.1–1.8 ns
Tektronix TPP1000 10:1 10 MΩ/<4 pF 1 GHz 300 V 1.1–1.8 ns
Tektronix TPP0850 50:1 40 MΩ/1.8 pF 800 MHz 2500 V 1.3–2.2 ns

*Assuming oscilloscope bandwidth high enough not to impact performance.


-----

Minimize loop

Place probe tip
on probe pad

Probe pads close to device under test

**Figure 5.20** Practical high-frequency voltage measurement with minimal probe loop inductance

Figure 5.20 shows that the probe needs to be placed as close to the device under test as
possible. To show the impact of probe position requires a simulation. Using the available
SPICE models for the LGA GaN transistors, a buck converter simulation with layout
parasitics was created as shown in Figure 5.21. The switch-node-to-ground voltage
waveform (an estimation of a practical voltage measurement), with the actual voltage
across the active device, is shown in Figure 5.22. It clearly shows that the “measured”
voltage has much smaller ringing than is actually seen across the active device. In practice,
the ringing may be higher or lower, depending on the parasitic inductance and the direction
of the changing current. Secondly, there is a measured initial bump in the voltage rise time
that is due to the induced voltage drop across the parasitic inductance within the measurement loop. From the active device’s drain current – also shown in Figure 5.22 – the bump
coincides with the current rising in the device. Thus, although this added bump adds
uncertainty to the voltage rise time and shape, it indirectly does add information about the
current rise time.

###### 5.4.2 Current Measurement Requirement

As with voltage measurement, the current measurement bandwidth is determined by the risetime requirement. For a typical rise time of 2 ns (as shown in the simulation results in
Figure 5.22), a practical current measurement bandwidth (using Equation 5.2) of more than
500 MHz is required. This is well beyond the capability for traditional current probes, such as
Hall element [15] and Rogowski coils [16,17], which have bandwidths of 50 MHz or less. This
leaves the option of using current-sense resistors or coaxial current shunts, some of which have

|Col1|Do not use probe groun lead Us clip to gro op|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||||


-----

.tran 0 (.05u+TP) (TP)

RHOH GProbeH GateH

VgateH 2

+ DHOL LG_U2
– (LG)

MyD

Upper Gate Driver

.model myd d (Vfwd = 0.1 Ron = 0.67))


.param LG 1nH
.step param CSI list 100pH 500pH 1000pH
.param dt 5ns

.param VBUS = 60
.param VOUT = 30
.param ton = 1000n
.param TP = 2000n
.param IL = 10

LBUCK
OUT

µH ILOAD

CBUCK

1µF (IL)

.lc I(LBUCK) = 8.5A

Theoreticaldevice voltage .lc V(OUT) = 30V

Practical measurement
across bottom device

|LLOOP .param LG 1n|Col2|
|---|---|
|.param LG 1 100pH .step param LD_U2 VBUS .param dt 5n DrainH + .tran 0 (.05u+TP) (TP) 100pH – .param VBUS U2 (VBUS) .param VOU RHOH GProbeH GateH EPC2001 .param ton = VgateH + DH2 OL LG_U2 1 LCSI_U2 . .p pa ar ra am m T ILP = = 1 SourceH – (LG) RPCB_U2 (CSI) MyD LBUCK VSW OUT Upper Gate Driver 10µH I CBUCK DrainL model myd d (Vfwd = 0.1 Ron = 0.67)) 1µF VgateL RLOH GProbeLGateL U EP1 C2001 T deh ve io cr ee vti oca ltal ge . .l lc c I V(L ( + DL2 OL LG (L_ GU )1 RPC1 B_U1 SourceL – LCSI_U1 MyD (CSI) Practical meas across bottom Lower Gate Driver||
|RLOH VgateL 2 + DLOL – MyD Lower Gate Driver||
|||


**Figure 5.21** LTSPICE simulation created to show impact of probe location on practical voltage
measurement

bandwidths up to 2 GHz [18]. Sufficient bandwidth, however, is only one of the criteria for
accurate current measurement.
In most cases, the bandwidth of the sensing resistor or shunt is limited by the corner
frequency made between the resistance and the parasitic series inductance. For a given series
inductance, the bandwidth can be improved by increasing the value of the sense resistance, but
this comes at the cost of increased voltage drop and power loss. This effect can be seen for
a selection of coaxial shunts in Table 5.2. Thus, to measure a 20 A current pulse similar to the

V(vsw) V(Drain L, Source L) tx(U1: drainin)

88V 32A

80V Probe Voltage Across Measurement Nodes 28A

72V 24A

64V 20A

56V GaN Transistor 16A

Drain Current

48V 12A

Theoretical Device Voltage

40V 8A

32V 4A

24V 0A

16V –4A

8V –8A

0V Bump in Measured Voltage –12A

Yields di/dt Interval Information

–8V –16A
0ns 2ns 4ns 6ns 8ns 10ns 12ns 14ns 16ns 18ns 20ns

|Col1|Col2|Col3|Col4|Col5|Col6|Probe V|oltage Acr|oss Meas|urement N|odes|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||
|||||||||||||
|GaN|Transistor|||||||||||
|Drain|Current|||||||||||
||||||||T|heoretical|Device Vol|tage||
|||||||||||||
|||||||||||||
|||||||||||||
|||||||||||||
||||||B|ump in|Measured|Voltage||||
||||||Y|ields di/|dt Interval|Informati|on|||
|||||||||||||


**Figure 5.22** SPICE simulation results showing impact of probe location on practical voltage
measurement


-----

**Table 5.2** Selection of high bandwidth coaxial shunts [18]

Model Resistance (mΩ) Bandwidth (MHz) Voltage drop at 20 A (V) Rise time (ns)

SDN-414-01 10 400 0.2 1
SDN-414-025 25 1200 0.5 0.3
SDN-414-05 50 2000 1.0 0.18
SDN-414-10 100 2000 2.0 0.18

one shown in Figure 5.22, the bandwidth requirement implies that the 10 mΩ shunt could not
be used, and a minimum shunt voltage drop of 0.5 V would have to be induced. This may be
excessive for a low-voltage application.
Furthermore, the main advantage of a coaxial current shunt compared with sense resistors is
the reduction of parasitic inductance between the measurement nodes, increasing measurement
bandwidth. Due to their size and shape, coaxial shunts add a larger amount of inductance to the
overall circuit, and any significant increase in power loop inductance will adversely affect
switching operation. One method is to place a large number of shunt resistors in parallel to
reduce the overall inductance [19], but this still requires a significant reduction in switching
speed to achieve meaningful current waveform measurements.
In summary, with present technology, it is practically impossible to measure the GaN
transistor current in circuit without adversely affecting its dynamic performance.

###### 5.5 Summary

In this chapter, the basic techniques for modeling and measuring GaN transistors in highperformance power conversion circuits were discussed. The next chapter will explore how the
superior properties of GaN transistors yield significant performance improvements in hardswitching applications.

###### References

1. Liu, W., Jin, X., Xi, X. et al. (2005) “BSIM3v3.3 MOSFET Model, User’s manual,” Dept. of Electrical Engineering
[and Computer Sciences, University of California, Berkeley. Available from http://www-device.eecs.berkeley.edu/](http://www-device.eecs.berkeley.edu/~bsim/Files/BSIM3/ftpv330/Mod_doc/b3v33manu.tar)
[∼bsim/Files/BSIM3/ftpv330/Mod_doc/b3v33manu.tar.](http://www-device.eecs.berkeley.edu/~bsim/Files/BSIM3/ftpv330/Mod_doc/b3v33manu.tar)
2. Efficient Power Conversion Corporation, Appl. Note AN005, “Circuit simulation using EPC device models,”
[Available from http://epc-co.com/epc/documents/product-training/Circuit_Simulations_Using_Device_Models](http://epc-co.com/epc/documents/product-training/Circuit_Simulations_Using_Device_Models.pdf)
[.pdf.](http://epc-co.com/epc/documents/product-training/Circuit_Simulations_Using_Device_Models.pdf)
3. Efficient Power Conversion Corporation, “Demonstration board EPC9107 quick start guide,” Available from

[http://epc-co.com/epc/Products/DemoBoards/EPC9107.aspx.](http://epc-co.com/epc/Products/DemoBoards/EPC9107.aspx)
4. International Rectifier, Appl. Note, AN-1059, “DirectFET[] technology thermal model and rating calculator,” Sep.
[2010, Available from http://www.irf.com/technical-info/appnotes/an-1059.pdf.](http://www.irf.com/technical-info/appnotes/an-1059.pdf)
5. Infineon, Appl. Note AN 2012-04, “ThinPAK 8X8 New High Voltage SMD-Package,” version 1.0, April 2010,
[Available from http://www.infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?folderId=db3a304314dca3890115-](http://www.infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?folderId=db3a304314dca38901152836c5a412ab&fileId=db3a304327b897500127f6946a286519)
[2836c5a412ab&fileId=db3a304327b897500127f6946a286519.](http://www.infineon.com/dgdl/Infineon+ThinPAK+8x8.pdf?folderId=db3a304314dca38901152836c5a412ab&fileId=db3a304327b897500127f6946a286519)
6. Reusch, D. “High frequency, high power density integrated point of load and bus converters,” Ph.D. dissertation,
[Virginia Tech, Blacksburg, VA, 2012. Available from http://scholar.lib.vt.edu/theses/available/etd-04162012-](http://scholar.lib.vt.edu/theses/available/etd-04162012-151740/)
[151740/.](http://scholar.lib.vt.edu/theses/available/etd-04162012-151740/)
7. Efficient Power Conversion Corporation, “EPC2007 – Enhancement-mode Power Transistor,” EPC2007 datasheet,
[Sep. 2011 [Revised July 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2007_datasheet](http://epc-co.com/epc/documents/datasheets/EPC2007_datasheet.pdf)
[.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2007_datasheet.pdf)


-----

8. Efficient Power Conversion Corporation, “Demonstration board EPC9006 quick start guide,” Available from

[http://epc-co.com/epc/Products/DemoBoards/EPC9006.aspx.](http://epc-co.com/epc/Products/DemoBoards/EPC9006.aspx)
9. Bergquist Company, “Gap pad GP1500 thermally conductive, un-reinforced gap filling material,” Gap Pad[] 1500
[datasheet PDS_GP_1500_12.08. Available from http://www.bergquistcompany.com/pdfs/dataSheets/PDS_GP_](http://www.bergquistcompany.com/pdfs/dataSheets/PDS_GP_1500_12.08_E.pdf)
[1500_12.08_E.pdf.](http://www.bergquistcompany.com/pdfs/dataSheets/PDS_GP_1500_12.08_E.pdf)
10. Fuji Polymer Industries Co. Ltd., Fujipoly[], “Sarcon[] XR-m Highly Thermal Conductive and Non-Flammable
[Silicone Gel Sheets,” datasheet, [14 Jul. 2009]. Available from http://www.fujipoly.com/usa/assets/files/](http://www.fujipoly.com/usa/assets/files/2010_data_sheets/090930_Sarcon%20XR-m%20technical%20info.pdf)
[2010_data_sheets/090930_Sarcon%20XR-m%20technical%20info.pdf.](http://www.fujipoly.com/usa/assets/files/2010_data_sheets/090930_Sarcon%20XR-m%20technical%20info.pdf)
11. Strydom, J., de Rooij, M., and Lidow, A. “Gallium nitride transistor packaging advances and thermal modeling,”
_[EDN China, Sep. 2012. Available from http://epc-co.com/epc/documents/product-training/Gallium%20Nitride%](http://epc-co.com/epc/documents/product-training/Gallium%20Nitride%20Transistor%20Packaging%20Advances.pdf)_
[20Transistor%20Packaging%20Advances.pdf.](http://epc-co.com/epc/documents/product-training/Gallium%20Nitride%20Transistor%20Packaging%20Advances.pdf)
12. Tektronix Corporation, “Understanding oscilloscope bandwidth, rise time and signal fidelity,” Technical
[brief no. 55W-18024-0, Available from http://www.electron.frba.utn.edu.ar/∼jcecconi/Bibliografia/06%20-%](http://www.electron.frba.utn.edu.ar/~jcecconi/Bibliografia/06%20-%20Osciloscopios%20de%20Almacenamiento%20Digital/Understanding_Oscilloscope_BW_RiseT_And_Signal_Fidelity.pdf)
[20Osciloscopios%20de%20Almacenamiento%20Digital/Understanding_Oscilloscope_BW_RiseT_And_Signal_](http://www.electron.frba.utn.edu.ar/~jcecconi/Bibliografia/06%20-%20Osciloscopios%20de%20Almacenamiento%20Digital/Understanding_Oscilloscope_BW_RiseT_And_Signal_Fidelity.pdf)
[Fidelity.pdf.](http://www.electron.frba.utn.edu.ar/~jcecconi/Bibliografia/06%20-%20Osciloscopios%20de%20Almacenamiento%20Digital/Understanding_Oscilloscope_BW_RiseT_And_Signal_Fidelity.pdf)
[13. SDE Consulting, T.J. Sobering, Technote 2, “Bandwidth and rise time,” May 1999 [Revised Nov. 18, 2002] http://](http://www.k-state.edu/ksuedl/publications/Technote%202%20-%20Bandwidth%20and%20Risetime.pdf)
[www.k-state.edu/ksuedl/publications/Technote%202%20-%20Bandwidth%20and%20Risetime.pdf.](http://www.k-state.edu/ksuedl/publications/Technote%202%20-%20Bandwidth%20and%20Risetime.pdf)
[14. Teledyne LeCroy, “Passive probe ground lead effects,” June 2013. Available from http://teledynelecroy.com/doc/](http://teledynelecroy.com/doc/passive-probe-ground-lead-effects#pdf)
[passive-probe-ground-lead-effects#pdf.](http://teledynelecroy.com/doc/passive-probe-ground-lead-effects#pdf)
15. Teledyne Leroy, “Current probes,” Available from [http://teledynelecroy.com/probes/probeseries.aspx?](http://teledynelecroy.com/probes/probeseries.aspx?mseries=426)
[mseries=426.](http://teledynelecroy.com/probes/probeseries.aspx?mseries=426)
[16. Power Electronic Measurement, “CWT-current probes,” 2013. Available from http://www.pemuk.com/products/](http://www.pemuk.com/products/cwt-current-probe.aspx)
[cwt-current-probe.aspx.](http://www.pemuk.com/products/cwt-current-probe.aspx)
17. Athena Energy Corp, “200 A/50 MHz Rogowski Coil Current probe, Athena Energy Corp current probe,”
[datasheet. Available from http://ecbiz122.inmotionhosting.com/∼athena18/wp-content/uploads/2012/03/Rogow-](http://ecbiz122.inmotionhosting.com/~athena18/wp-content/uploads/2012/03/Rogowski_Specifications.pdf)
[ski_Specifications.pdf.](http://ecbiz122.inmotionhosting.com/~athena18/wp-content/uploads/2012/03/Rogowski_Specifications.pdf)
[18. T & M Research Products, “SDN series co-axial current shunts,” datasheet. Available from http://www](http://www.tandmresearch.com/)
[.tandmresearch.com/.](http://www.tandmresearch.com/)
19. Danilovic, M. et al. (Sept. 2011) “Evaluation of the switching characteristics of a gallium-nitride transistor,”
_Energy Conversion Congress and Exposition, ECCE 2011, Phoenix, AZ, pp. 2681–2688._


-----

# 6

#### Hard-Switching Topologies

###### 6.1 Introd uction

In hard-s witching converters, the trans istors are turne d on and off rapid ly, while there is voltage
across – and curren t throu gh – the drain and source of the device . These switching transitions
lead to signifi cant p ower losses durin g the switch ing event. The mai n met rics of any converter
perfor mance are: (a) efficiency, where higher is bett er, (b) size, where smaller is bett er, and (c)
cost, where lower is better. Effici ency can be incre ased through imp rovemen ts in the switching
(dynam ic) and conduct ion (static) charact eristics of the device s, there by allowi ng higher
switch ing freque ncies to be used. This, in turn, leads to a size reduct ion, which also can lead to
lower cost. In this chapte r, hard-s witching topol ogies will be revie wed and we will look at how
the superi or proper ties of GaN trans istors yiel d signifi cant perfor mance imp rovem ents.
Table 6.1 provi des defin itions for term s used in hard-switchi ng loss analys is discu ssions in
this chapte r.

###### 6.2 Ha rd-Switching Loss Analysis

To drive the frequency higher in a hard-s witchi ng convert er, powe r d evices must have very low
dynam ic losses. The domi nant compo nent of these loss es is the hard-swi tching “ e vent” where,
in a turn-on switch ing transition, curren t flows throug h the device before the voltage across that
device comm utates to zero as show n in Figure 6.1(a) [1,2]. The revers e sequenc e occurs when
the device turns off, as shown in Figure 6.1(b).
The trans itions of curren t and voltage wi thin the device are not the only loss contr ibutors as
there are other directly and indirectly related compon ents. These addit ional factors are: output
capaci tance losses (POSS), gate c harge losses (P G), reverse conduction losses (P SD ), and revers e
recover y loss es (PRR ).
The output capacitance losses (POSS) are associated with the output capacitance of the device.
The charging or discharging of this capacitor requires energy of which half is dissipated in the
resistance in the current path of the capacitor in normal, positive current operation of the converter.
Gate charge losses (PG ) are similar to the output capaci tance loss es in that the energy
required to charge the gate-to-source capacitance is dissipated in the resistance of the current
path of the capacitance.

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

**Table 6.1** Definitions used in hard-switching loss analysis

Definitions of terms used in hard-switching loss analysis

Vth Gate threshold voltage (at QGS1)
VDR Gate driver on-state output voltage
Vpl Gate plateau voltage (at QGD)
Vpl(op) Plateau voltage at the operating condition current
tCR Rise time for current in the transistor
tCF Fall time for current in the transistor
tVR Rise time for voltage across the transistor
tVF Fall time for voltage across the transistor
tSD Reverse diode conduction time
tZVS Zero voltage switching transition time
teff Effective dead-time between transistor switching
Pon Power losses due to the turn-on switching transition
Poff Power losses due to the turn-off switching transition
PCOSS Power losses due to output charge QOSS
PG Power losses due to gate charge QG
PSD Power losses due to the forward drop of the body diode
PRR Power losses due to the reverse recovery charge of the body diode (MOSFET
and Cascode transistors only)
PSW Total power losses during switching transitions
PDynamic Power loss due to dynamic loss components in the transistor
PConduction Power loss due to static conduction loss in the transistor
fSW Switching frequency
QGS1 Charge required to increase gate voltage from zero to the stated threshold voltage of the
device.
QGS2 Charge required to increase gate voltage from the stated threshold voltage of the device to
the plateau voltage (current conduction interval)
QGS Charge required to increase gate voltage to the plateau voltage (complete current transition)
QGS = QGS1 + QGS2
QGD Charge required into the gate to change the drain voltage down from the blocking state to
near zero, at which point the device enters the linear region. (constant current region)
QG Total gate charge required to drive a device from zero to rated gate voltage (fully
enhanced)
QGS(op) Charge required to increase gate voltage to the operating plateau voltage
QG(op) Total gate charge required to drive a device from zero to rated gate voltage based on the
operating conditions
gm Transconductance of the transistor

In most converters, an anti-parallel diode is present across the drain-to-source terminals of
the device. In some cases, it is inherent to the device structure, such as in MOSFETs. In cascode
GaN transistors, there is a body diode in the Si MOSFET. In the case of enhancement-mode
GaN transistors, as explained in Chapter 1, there is a mechanism to conduct reverse current
when the device is off, allowing operation similar to a diode. Since diode conduction is a
function of the switching transient, they are included in the hard-switching loss calculation.
These losses are defined as reverse conduction losses (PSD).


-----

**VBUS**

**IL**


**VBUS**

**IDS** **IL** **IDS**


**VDS**


**VDS** **VGS** **VDR** **VDR** **VGS**

**Vpl** **Vpl**

**Vth** **Vth**

**tCR** **tVF** **t** **tVR** **tCF**

(a) Turn-On (b) Turn-Off


**t**

|Col1|Col2|P on I DS V GSV V DS DR V pl t t|
|---|---|---|
||||
|t||V DS|
||||
||||
||t|t|

|Col1|Col2|P off V|Col4|
|---|---|---|---|
|||||
|I DS V GS||||
|||||
|||||
|||||


**Figure 6.1** Idealized switching waveforms used for calculating switching loss (a) turn-on (b) turn-off

Reverse recovery losses (PRR) are based on the amount of charge required to turn off the
body diode, and are only present in MOSFET and cascode GaN transistors, because enhancement-mode GaN transistors have no reverse recovered charge.
Next, the details of each of the loss mechanisms will be presented, plus the means to
determine each of the losses.

###### 6.2.1 Switching Losses

The switching power loss can be determined graphically from Figure 6.1, by summing the
voltage transition power losses (PVt) and the current transition power losses (PCt) using the
following equation:

Psw  PVt  PCt

(6.1)
 [1][=]2 ? VBUS ? IL ? (txR  txF) ? fsw

Where txR and txF are the switching commutation times as seen in Figure 6.1, VBUS is the
voltage across the device during the off-state, and IDS is the on-state drain-to-source current,
and where one parameter (either voltage or current) is always in transition while the other is
fixed. This leads to the factor of 1/2 in Equation 6.1. The switching times (txR and txF) are not
given in the circuit and need to be determined from the gate charge (QG) characteristics of
device based on the circuit operating conditions.
GaN transistors are driven in a similar manner to MOSFETs. The gate electrodes have very
high input impedance, and control of the device is accomplished by supplying or removing a
certain amount of charge to/from the gate electrode. Transistor switching can be segmented into
four regions, as shown in Figure 6.2: (1) the charge required to transition the drain-to-source
voltage (QGD), (2) the charge required to bring the gate electrode up to device threshold (QGS1),
(3) the charge required to transition the current from zero to the load current (QGS2), and (4) the
incremental additional charge to overdrive the gate (QG (QGS1 + QGS2 + QGD)).
�


-----

5


~0 VDS 10 VDS 20 VDS 30 VDS

IDS = 33 A

Vpl

Vth

QGS1 QGS2 QGD

0 2 4 6 8 10 12


4.5

4


3.5

3


2.5

2


1.5

1


0.5

0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
|I = 3 DS|I = 3 DS||3 A||||||||
||||||||||||
||||||||||||
|V|||||||||||
|pl|||||||||||
||||||||||||
|V th|||||||||||
||||||||||||
||||||||||||
||||||||||||
|Q GS1|||Q Q GS2||GD||||||


**QG – Gate Charge (nC)**

**Figure 6.2** Impact of drain-source voltage and drain current on gate charge and gate voltage for
EPC2015 [3]


**6.2.1.1** **Miller Charge (QGD): The Voltage Transition Period**

The voltage commutation period of a traditional hard-switching commutation is based on the
Miller charge. The Miller charge is characterized by the plateau voltage on the gate waveform
and can be used to determine the switching losses during the voltage transition period. At turnon, the period begins after the current has fully transitioned, and is complete when the drain-tosource voltage has reaches zero. The reverse process occurs for turn-off. The larger the voltage
swing, the longer it will take for the transition, and the higher the losses. Figure 6.2 is a graph of
the measured gate voltage as a function of gate charge, highlighting the impact of various drainto-source voltages.
In general, the time (t) it takes to charge a capacitor to a specific charge (Q) is given by:


t [Q] (6.2)

I

Where I is the current used to charge the capacitor.
QGD for any given drain-to-source voltage can be calculated using Equation 6.3 [2] if the
function of CRSS(vDS) is known.


VBUS


QGD  CRSS v DS ? dvDS (6.3)
∫0

Alternatively, the CRSS(vDS) function can be captured from the graph provided in device
datasheets. It can be seen from Figure 6.3 that all the devices capacitances have a non-linear
relationship with drain-to-source voltage.


-----

1.8

1.6

1.4

1.2

1


0.8

0.6

0.4

0.2

0
0 10 20 30

|Col1|Col2|Col3|Col4|COSS = CGD + CSD|Col6|
|---|---|---|---|---|---|
|||||COSS = CGD + CSD||
|||||CISS = CGD + CGS CRSS = CGD||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||


**VDS – Drain-to-Source Voltage (V)**

**Figure 6.3** Device capacitances as a function of drain-to-source voltage for EPC2015 [3]


Substituting Equation 6.2 into Equation 6.1 for the voltage transition only, and using a linear
approximation for the gate voltage and current transitions, the power losses during the voltage
transition can then be approximated with Equation 6.4.

PVt ≅ [V][BUS][ ?][ I][L] ? tVx ? fsw
2

(6.4)
 [V][BUS][ ?][ I][L] ? [Q][GD] ? fsw
2 IG


As can be seen in Equation 6.4, the gate current appears in the power loss equation. The
current into the gate thus affects the transition time, and increasing the gate current will reduce
this time. However, gate driver impedance and gate circuit inductance may limit this gate
current and therefore the transition period.
The gate current (IGvon) during the turn-on voltage transition period (tVF) can be estimated as:

IGvon  [V][DR]R[ �]Gon[V][PL] (6.5a)


Where VDR is the gate driver on-state output voltage.
The gate current (IGvoff) during the turn-off voltage transition period (tVR) can be estimated
as:

IGvoff  R[V]Goff[PL] (6.5b)


The gate currents IGvon and IGvoff can be equated to IG in Equation 6.4 to determine the
voltage transition power loss.


-----

**6.2.1.2** **Gate Charge (QGS2): The Current Transition Period**

The charge that determines the current transition time is QGS2. It can be used to calculate the
switching losses during this period. For turn-on, the period begins after the gate voltage reaches
the threshold voltage and current begins to flow. It is complete when the drain-to-source
voltage begins to transition. For turn-off, the sequence occurs in reverse. The larger the current
swing, the longer it will take for the transition, and power losses will increase. Figure 6.4 shows
a graph of the measured gate voltage as a function of gate charge for various current levels. The
higher the drain current, the longer the period lasts.
The relationship between the gate voltage and drain current is highly non-linear and
therefore requires a graphical technique to estimate QGS2.
The typical datasheet provides information for only one switching condition, but it can be
used to determine the QGS2 needed for the loss calculations. The plateau voltage in Figure 6.4
needs to be noted, as well as QGS for the same conditions. In this example, IDS is 33 A and the
plateau voltage is about 2.3 V. The threshold voltage for these devices is about 1.4 V, giving an
estimated value of QGS1 of 2 nC, and QGS2 of about 1 nC at this drain current. In Figure 6.5 we
have highlighted this same operating condition. If we do this same calculation at 100 A, the
plateau voltage changes to 2.8 V, and QGS1 is unchanged, but QGS2 increases to 2 nC.
In general, QGS1 can be calculated using Equation 6.6:


QGS1  �QVGSpl �


? Vth (6.6)


Since QGS and Vpl both vary proportionally with current and drain-source voltage, their ratio
is virtually constant. Therefore, QGS1 is a fixed value regardless of operating conditions.
The QGS(op), which is the QGS at the operating value of IDS, can also be calculated for the
operating conditions by reading off the plateau voltage Vpl(op) from the transfer characteristic

5


4.5

4


3.5

3


2.5

2


1.5

1


0.5

0

|V = 2|Col2|Col3|0 V|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
||V = 2||0 V|||||||
|DS|DS|||||||||
|||||||||||
|Q GS||||||||||
|V||||||||||
|||||||||||
|V pl33 pl16|||||||33 A|||
|||||||||||
|V th||||||16|A|||
|||||||10 mA||||
|||||||||||
|||||||||||
|Q GS1|||Q GS2|||||||


0 2 4 6 8 10 12


**QG – Gate Charge (nC)**

**Figure 6.4** Impact of drain current on the gate plateau voltage for EPC2015 [3]


-----

150

100


50

IDS
Vpl = 2.3 V


0
0 0.5 1 1.5 2 2.5 3 3.5 4 4.5

**VGS – Gate-to-Source Voltage (V)**

|V DS|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|||25°C 125°C|||||||||
||V DS|= 3 V|||||||||
||||||||||||
|||||||||V = 2 pl at 1|.8 V 00 A||
|||||||||V = 2 pl at 3|.3 V 3 V||
|||V th|||||||||


**Figure 6.5** Transfer characteristic for EPC2015 [3]

graph, as shown in Figure 6.5, and using Equation 6.7:


QGS op  [] �QVGSpl �


? Vpl op  (6.7)


With QGS(op) and QGS1 determined, QSG2 can be calculated using Equation 6.8:

QGS2  QGS op  [�] [Q]GS1 (6.8)


Substituting Equation 6.2 into Equation 6.1 for the current transition only, the losses can be
approximated using Equation 6.9.

Pct ≅ [V][BUS][ ?][ I][DS] ? tCx ? fsw
2

(6.9)
 [V][BUS][ ?][ I][DS] ? [Q][GS2] ? fsw
2 IG


The gate current again appears in the power loss equation. Thus, the current into the gate
affects the transition time, and increasing the gate current will reduce this time.
The gate current during the current turn-on and turn-off transition periods can be estimated
as:

VDR � �Vpl 2 Vth�

IGcon  RGon (6.10a)


IGcoff 


�Vpl  Vth�

2

(6.10b)
RGoff


-----

The gate currents IGcon and IGcoff can be equated to IG in Equation 6.9 to determine the
current transition power loss.
Using Equations 6.4, 6.5a, 6.9, and 6.10a, the total device turn-on loss then can be
determined using Equation 6.11:


Pon  PVt  PCt


2


QGD QGS2

[V][BUS][ ?][ I][DS][ ?][ f][sw][ ?][ R][Gon] ?
 2 664VDR � Vpl  VDR � �Vpl 2 Vth�


3

775 (6.11)


Similarly using Equations 6.4, 6.5b, 6.9, and 6.10b, the total turn-off power loss (Poff) can be
determined using Equation 6.12:


Poff  PVt  PCt


2


QGD QGS2

[V][BUS][ ?][ I][DS][ ?][ f][sw][ ?][ R][Goff] ?
 2 664 Vpl  �Vpl  Vth�

2


3

775 (6.12)


The total switching losses can now be summarized as the sum of Pon and Poff:

Psw  Pon  Poff (6.13)

###### 6.2.2 Output Capacitance (COSS) Losses

The power loss due to the output capacitance can be calculated for the specific working voltage
using the Equation 6.14:

POSS  fsw ? EOSS

VBUS (6.14)

 fsw ? vDS ? COSS v DS ? dvDS

0

∫


The COSS(vDS) function can be captured from the graph typically provided in the datasheet
for the part being analyzed. The topology and operating conditions will determine whether
POSS losses are present. As an example, self-commutation transitions have zero POSS losses, but
only if the load current is sufficient to completely charge COSS to VBUS or discharge to zero, and
if the time to complete the self-commutation transition is much longer than the current
transition time of the device itself.

###### 6.2.3 Gate Charge (QG) Losses

The power loss associated with the gate charge is calculated as follows:

PG  QG ? VDR ? fsw (6.15)


-----

The gate power losses become an important consideration at higher frequencies and at lower
output power levels. It is important to note that all the gate energy is supplied during the
charging phase, half of which is consumed, and during the discharge phase the remaining half
of the energy is then consumed.

###### 6.2.4 Reverse Conduction Losses (PSD)

Reverse or diode conduction occurs when the current in the device turning on goes through the
body diode before the switch conducts the current, and is as a result of dead-time between when
one device turns off and when the next device turns on. Reverse conduction follows a selfcommutation transition and will only occur if the timing between the transitions is longer than
needed to establish zero-voltage switching (ZVS) as shown in Figure 6.6.
The power loss due to the reverse conduction voltage through the body diode is given by the
following equation:

PSD  VSD ? IDS ? tSD ? fsw (6.16)

The reverse conduction time (tSD) needs to be determined from the operating conditions as it
is dependent on load current, supply voltage and device parameters. To do this, a definition of
effective dead-time is needed.
The time from when the gate voltage of the device reaches the turn-off plateau voltage to
when the other device’s load current commutates from the diode will be defined as the effective

Q1 Turn-Off

VBUS

Q2 Turn-On

###### 0 (a)

Partial Time
ZVS

Shoot-Through

(b)
ZVS

(c)
ZVS + Diode Conduction

**Figure 6.6** Switch-node voltage commutation with the same load current for various dead-times:
(a) partial ZVS, (b) ZVS, and (c) ZVS plus diode conduction

|V BUS|Col2|Q1 Turn-Off Q2 Turn-On|Col4|
|---|---|---|---|
|||||
|||||
|||0 (a) Partial ZVS|Tim|
|oot-Through||||
|||||


-----

V VBUS eff

VGS_Q1 VGS_Q2

tSD

**Figure 6.7** Effective dead-time definition for turn-on


###### t

|Col1|t|Col3|Col4|
|---|---|---|---|
|V BUS|t eff t SD||V GS_|
|||||
|||||


dead-time (shown in Figure 6.7). Although they are related, this definition differs from the
dead-time generated by the gate drive command signals. Also shown in Figure 6.7 is the
definition of reverse conduction time (tSD), which starts when the diode starts to conduct, and
ends when the device itself turns on and conducts the current through the transistor channel.
The effective dead-time for the ZVS interval needs to be determined next, and then the diode
conduction losses can be calculated. To establish ZVS, the external current must have sufficient
energy to fully commutate the voltage, and the timing of the second device gate turn-on
threshold occurs at the instant the voltage reaches zero across device Q2 (see the solid line
labeled VGS_Q2 in Figure 6.7). The output charge is used to determine the ZVS transition time,
together with the turn-off current (Iturn-off) of device Q1. The output charge can be calculated
using Equation 6.17:

VBUS

QOSS  0 COSS v DS ? dvDS (6.17)
∫

The output capacitances of transistors Q1 and Q2 need to be considered together to correctly
determine the ZVS transition time by using Equation 6.18:

tZVS  [Q][OSS][_][Q1]ITurn-off[ ][ Q][OSS][_][Q2] (6.18)

where Iturn-off is the current in the conducting device at the time of turn-off. The reverse
conduction time can then be determined by subtracting the ZVS time from the effective deadtime, chosen for the operation of the converter.

tSD  teff � tZVS (6.19)

A zero result for Equation 6.19 indicates that a ZVS transition has occurred.


-----

A positive time result for Equation 6.19 indicates that diode conduction and the associated
losses can be determined using Equation 6.16.
A negative reverse conduction time means that the converter is operating in partial ZVS
mode. In this case, a hard-switching event is established with associated losses, but occurs at
lower voltage than the bus voltage. There is no reverse recovery loss, regardless of whether the
device is a MOSFET or a GaN transistor, as no diode is conducting. The switch-node voltage
when Q2 turns on (VPZVS) can be determined by calculating the amount of charge transferred at
the effective time relative to the total charge in the circuit using Equation 6.20:

VPZVS  Q[I][Turn-off]OSS_Q1[ ?] [ t][eff] Q[ ?]OSS[ V][BUS]_Q2 (6.20)

In the case of partial ZVS, during the self-commutation time, the loss analysis must be
treated the same as the ZVS case but at a reduced time.

###### 6.2.5 Reverse Recovery (QRR) Losses

The body diode reverse recovery losses occur when the body diode transitions from the on-state
to the off-state. Enhancement-mode GaN transistors, unlike standard power MOSFETs or
cascode GaN devices, have no minority carriers to be stored in a junction, and therefore have no
reverse recovery charge. As discussed in Chapter 2, cascode GaN transistors have a small
amount of reverse recovery due to the small series-connected silicon power MOSFET.
The diode reverse recovery power loss can be calculated from the recovery charge and the
bus voltage using Equation 6.21:

PRR  ERR ? fsw (6.21)
 QRR ? VBUS ? fsw

The reverse recovery charge is provided in device datasheets at typical operating conditions,
but it may prove inaccurate when operating conditions for the converter have large deviations
from those given in the datasheet. Unfortunately there is no simple means to correctly calculate
the QRR.

###### 6.2.6 Total Hard-Switching Losses

The total dynamic power loss is the sum of the individual components:

PDYN  (Psw  POSS  PG  PSD  PRR) (6.22)

Owing to the GaN transistor’s lower QSG2 and QGD, Psw is much lower than a comparable
power MOSFET. The output capacitance for all types of GaN transistors is smaller than
MOSFETs of comparable RDS(on), making POSS relatively low. Both gate drive voltages and
gate charge are also lower, making PG lower. Finally, due to the reverse current conduction
mechanism, enhancement-mode GaN transistors have a higher VSD when compared with the
body diode forward voltage of a MOSFET, whereas cascode-connected GaN transistors have
comparable forward drop. This characteristic of an enhancement-mode GaN transistor has the
potential to increase the power loss PSD and is influenced by the total reverse conduction time, a


-----

condition that can be controlled by the time that the rectifier switch is acting like a diode [4].
Enhancement-mode GaN transistors have zero reverse recovery, making the final term in
Equation 6.22 zero (or small in the case of a cascode device).
Overall, the dynamic power losses of GaN transistors are significantly lower than power
MOSFETs and enable power converters using hard-switching topologies to be more efficient
and smaller. Now let’s look at a simple figure of merit that can be used to estimate circuit
performance and compare expected results between technologies and products within the same
technology [5–8].

###### 6.2.7 Hard-Switching Figure of Merit

Before a hard-switching figure of merit (FOMHS) can be defined, we need to work through all the
components that contribute to switching losses and determine which of those factors can quickly
be extracted from a datasheet and are relevant enough to be compared. From Equation 6.22, it can
be seen that there are five factors that need to be analyzed for inclusion in the FOMHS.
The output capacitance losses are less dominant than switching losses in lower-voltage,
hard-switching converters, and these can be omitted from the FOMHS comparison. Gate-related
losses can also be omitted as they are very small compared to other losses. Reverse conduction
losses depend on operating conditions and can be mitigated by control techniques to correctly
adjust for effective dead-time. Hence, reverse conduction losses will also be omitted from the
FOMHS. Lastly, the reverse recovery losses, although highly relevant for the comparison
between different technologies, results in a complex and time-consuming process to correctly
analyze. Enhancement-mode and cascode GaN transistors both have relatively low losses and
so PRR will also be omitted from FOMHS.
The FOMHS must be proportional to the power loss contribution from both the conduction
and switching loss components, and is summarized in Equation 6.23 [9].

FOMHS  Q GD  QGS2 ? RDS(on) (6.23)

For a given technology, a lower value of FOMHS indicates lower power loss proportional to:

pffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi
PTotal ∝ FOMHS (6.24)

where the total device power loss is the sum of the conduction losses and the dynamic losses
and is given by Equation 6.25 and 6.26:

PTotal  PConduction  PDYN (6.25)

and:

PConduction  I[2]DS[_]RMS [?][ R]DS(on) (6.26)

The FOMHS can be plotted on a graph with RDS(on) on the x-axis and the charge-related terms
(QGS2 + QGD) on the y-axis as shown in Figure 6.8.
From Figure 6.8 it can be seen that 200 V GaN transistors have a similar FOMHS to 40 V Si
MOSFETs, and 600 V GaN transistors have a similar FOMHS to 100 V MOSFETs.


-----

30

3


30

3


0.3


0.3


0.03 0.03

1 10 100 1000 1 10 100 1000

**RDS(on) (mΩ)** **RDS(on) (mΩ)**


(a) (b)

**Figure 6.8** Comparison of hard-switching FOMHS between GaN transistors and silicon MOSFETs at
various voltages: (a) 40 V and 200 V, (b) 100 V and 600 V


###### 6.3 External Factors Impacting Hard-Switching Losses

In the previous section, a detailed analysis of the derivation of hard-switching losses was
presented. In practical applications, this picture is somewhat incomplete as there are additional
factors that can further impact hard-switching losses, such as common-source inductance
(CSI) (LS) and loop inductance (LLoop). These factors appear in practical circuits with physical
limitations brought on by device size, device parasitics, and circuit layout parasitics. Their
impact on hard-switching losses will be presented in this section.


###### 6.3.1 Impact of Common-Source Inductance

The two main inductances, CSI and high-frequency loop inductance, are shown in Figure 6.9
for a half-bridge configuration.


LLoop


VBUS


Cout Rload

Gate
Driver LS2

**Figure 6.9** Power loop (LLoop) and source inductance (LS1 and LS2) in a half bridge configuration


-----

VBUS

t CR

IDS IL

Impact of
CSI VDS VGS

Vpl
Vth

Time

**Figure 6.10** Effect of common-source inductance on the gate voltage

The impact of common source inductance on gate drive performance has been discussed in
Chapter 3. In this section, its impact will be quantified for the hard-switching current transition.
During a current transition event, the voltage generated across the common source
inductance will oppose the gate voltage, thereby reducing the gate current used to charge
the gate capacitance. This effectively lengthens the current transition period as shown in
Figure 6.10.
An analysis of the gate circuit shown in Figure 6.11 can be used to determine the amount of
time by which the current transition is lengthened. Because a full analysis reveals terms with
exponential and sinusoidal components, some simplifying assumptions need to be made.
The first simplifying assumption is that the voltage induced across the CSI can be regarded
as a voltage source in phase with the gate voltage, and thus will only impact the magnitude of
the voltage in the gate circuit. The second assumption ignores the impact of the gate circuit
inductance. In Chapter 4, it was shown that this inductance contributes negligibly to circuit

ID

VDD

Gate
Driver

Q1

+ RG –

+ VGS–

IG +

LS VLS

–

**Figure 6.11** Gate circuit loop including common-source inductance

|t t|Col2|Col3|Col4|
|---|---|---|---|
|t t CR_CSI VF t CR I I L DS Impact of CSI V V DS GS||||
||t CR I DS Impact of CSI V DS|||
|||V DS|V GS|
|||||
|||||

|Gate Driver|Col2|Col3|
|---|---|---|
||||


-----

switching performance. The third assumption is that the external drain current is constant
during the transition.
Neglecting the gate driver voltage drop, as it can be included as part of the gate resistance, the
Kirchhoff voltage loop in the gate circuit is given by:

VDD  VRG  VGS  VLS (6.27)

The gate and drain currents can then be added to yield:

VDD  IG ? RG  VGS  [L]tCR[S][ ?]_[ I]CSI[DS] (6.28)

Where the gate circuit current is given by:

IG  tCRQGS2_CSI  tCRC_GSCSI ? I ?DS gm (6.29)

Where tCR_CSI is the current rise interval time, shown on Figure 6.10.
Combining Equations 6.28 and 6.29, tCR_CSI can be determined:


tCR_CSI  VDDI �DSVGS


CGS
gm


�LS ? gm  RG� (6.30)

CGS


From Equation 6.30, the equivalent common-source inductance resistance (RCSI) can be
extracted as:

RCSI  [L]C[S][ ?]GS[ g][m] (6.31)

It can be deduced from the resistance in Equation 6.31 that the impact of CSI on the gate
circuit resistance is large, given that the device input capacitance is already small. The value of
LS, therefore, will need to become very small to minimize the impact of CSI. For example,
100 pH of CSI in a MOSFET circuit with CGS of 2900 pF, and gm = 60 S results in 2 Ω
equivalent resistance. The same 100 pH CSI in an equivalent GaN transistor circuit with CGS of
only 850 pF, and gm = 60 S, results in a 7 Ω equivalent resistance.
Equation 6.31 can be used to estimate the current transition time, including the influence of
the CSI. It can simply be added to the RG term in Equations 6.11 and 6.12 for the QGS2
component only.
As an example, a 1 MHz converter was evaluated with a fixed loop inductance and the CSI
was varied, with the results shown in Figure 6.12. It is notable how quickly the losses increase
as a function of CSI.

###### 6.3.2 Impact of High Frequency Power-Loop Inductance on Device Losses

Another factor that impacts hard-switching losses is the high-frequency power loop inductance
that impacts the commutation of voltage and current between the switching devices. This is the


-----

5.5

5.0


4.5

4.0


3.5

3.0

0.0 0.2 0.4 0.6 0.8 1.0

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||L S||||
||||||
||||||


**Parasitic Inductance (nH)**

**Figure 6.12** Effect of common-source inductance on power loss [24,25,26] (VBUS = 12 V, VOUT =
1.2 V, IOUT = 20 A, fSW = 1 MHz, control FET is EPC2015 [3], synchronous rectifier FET is EPC2015 [3]


inductance encompassed by the bus supply as well as the devices connected to this bus as
shown in Figure 6.9. Component parasitic inductance and physical layout inductance elements
all contribute to the total loop inductance.
The power loop inductance has two main negative effects on the switch during turn-off: it
slows the transition and it increases the voltage across the drain and source. During device turnon, the loop inductance reduces the device drain-to-source voltage, which decreases losses.
However, the sum of the two negative effects and the positive effect has a net negative result,
which means that the loop inductance will increase losses in the circuit as can be seen in
Figure 6.13.
Using the circuit conditions of Figure 6.12, and by adding as little as 1 nH of CSI, losses can
increase 50% over an ideal case. This is due to the negative impact of CSI on both turn-on and
turn-off switching transitions. Adding 3 nH of loop inductance increases loss by 30% over the
ideal case as shown in Figure 6.13. The smaller relative increase in loss is the result of the
partial savings at turn-on from high frequency loop inductance.
Understanding the impact of parasitic inductance on performance, GaN transistor designers
have to make the reduction of package inductance a high priority. Since all of the connections
of a lateral enhancement-mode HEMT transistor are contained on the same side of the die, the
die can be mounted directly to the PCB, minimizing the total inductance to the internal busing
and external solder bumps. To further decrease inductance, the drain and source connections
can be arranged in an interleaved land grid array, providing multiple parallel connections to the
PCB from the die [10].
To illustrate the impact of loop inductance, different layouts with similar CSI and different
loop inductances were compared. The impact of loop inductance on efficiency for various
layout variations in a buck converter operating at 1 MHz is shown in Figure 6.14, where the CSI
was kept at the minimum achievable level. An increase in the high-frequency loop inductance
from around 0.4 nH to 2.9 nH decreases efficiency by over 4%.


-----

4.5

4.3


4.0

3.8


3.5

3.3


3.0

0.0 0.5 1.0 1.5 2.0 2.5 3.0

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||L Loop||||
|||||||
|||||||
|||||||


**Parasitic Inductance (nH)**

**Figure 6.13** Effect of loop inductance on power loss [24,25,26] (VBUS = 12 V, VOUT = 1.2 V, IOUT =
20 A, fSW = 1 MHz, control FET is EPC2015 [3], synchronous rectifier FET is EPC2015 [3]


With these higher switching speeds, even small values of high-frequency loop inductance
can increase the voltage overshoot. Decreasing this inductance therefore results in lower
voltage overshoot, increased input voltage capability, and reduced electromagnetic interference (EMI). Figure 6.15 shows the drain-to-source voltage waveforms for a design with a

91


90

89


88

87


86

85


84

83


2 4 6 8 10 12 14 16 18 20 22 24


**Figure 6.14** Impact of high-frequency loop inductance on efficiency for designs with similar commonsource inductance (VBUS = 12 V, VOUT = 1.2 V, IOUT = 20 A, fSW = 1 MHz, control FET is EPC2015 [3]
synchronous rectifier FET is EPC2015, control MOSFET is BSZ097N04LSG [11], synchronous rectifier
MOSFET is BSZ040N04LSG) [12]

|Col1|Col2|Col3|Col4|Col5|Col6|40|V Ga|n Tran|sistor|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
||||||||||L Loo 0.4n|p H|
||||||||||L Loo 1.0|p nH|
||||||||||L||
||||||||||Loo 1.6 n|p H|
|||||40 V|MOSF|ET|||L||
||||||||||||
||||||||||Loo 2.9|p nH|
|4 6 8 10 12 14 16 18 20 22 2 Output Current (A) act of high-frequency loop inductance on efficiency for designs with simil (V = 12 V, V = 1.2 V, I = 20 A, f = 1 MHz, control FET is E BUS OUT OUT SW ier FET is EPC2015, control MOSFET is BSZ097N04LSG [11], synchron 040N04LSG) [12]|||||||||||


-----

![](GaN-transistors-power-conversion.pdf-123-0.png)

ΔVDS = 24 V

**VIN = 12 V** **VIN = 12 V**

ΔVDS = 15 V

**3 V/Div** **20 ns/Div** **3 V/Div** **20 ns/Div**


(a) (b)

**Figure 6.15** Synchronous rectifier switching waveforms of designs with (a) LLoop ≈ 1.6 nH and
(b) LLoop ≈ 0.4 nH (VBUS = 12 V, VOUT = 1.2 V, IOUT = 20 A, fSW = 1 MHz, L = 150 nH, control FET
is EPC2015 [3] synchronous rectifier FET is EPC2015)


high-frequency loop inductance of 1.6 nH compared with 0.4 nH. The voltage overshoot is
reduced from 100% of the input voltage to 25%, respectively.

###### 6.4 Reducing Body Diode Conduction Losses in GaN Transistors


Figure 6.16 shows the forward voltage drop of both a MOSFET and a typical enhancementmode GaN transistor. There is about 1.5 V difference between the two devices and, as the
temperature increases, it can go as high as 2 V. This graph, however, does not account for

MOSFET

25°C
125°C

+QRR

EnhancementMode GaN
Transistor

25°C
125°C

+ Zero QRR

0 0.5 1 1.5 2 2.5 3 3.5 4 4.5

**VSD – Source-to-Drain Voltage (V)**

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||MOS||FET||||||||
|||||||||||||
|||||25°C 125°C||||||||
|||||||||||||
||+|Q RR||||||||||
|||||||||Enha Mo||ncem de Ga|ent- N|
|||||||||Tr||ansisto|r|
|||||||||||||
|||||||||||25°C||
|||||||||||125°|C|
|||||||||||||
|||||||||+ Z||ero QR|R|


**Figure 6.16** Reverse transfer characteristics of 100 V MOSFET (typical) and enhancement-mode GaN
transistor (typical)


-----

dynamic behavior, where in the case of the enhancement-mode GaN transistor, there is no
reverse recovery (QRR = 0), in addition to lower output capacitance.
In Section 6.2.4, it was shown that optimal timing between the transistors can yield very low
losses under specific conditions. Those conditions are dynamic, and depend on operating
conditions such as load current and voltage, supply voltage and duty cycle. For most circuits, it
is not practical to have a circuit that can actively control the dead-time to the precision needed
to absolutely minimize losses. However, a simple anti-parallel Schottky diode can be
connected with the GaN transistor to improve the efficiency of the body diode with less
reliance on precise dead-time control.
One of the most critical requirements for the addition of the anti-parallel Schottky diode is
the minimization of the connection inductance between the two devices. This comes down to
three factors: the parasitic inductance between the drain and source of the GaN transistor, the
parasitic inductance of the Schottky diode, and the layout inductance connecting the GaN
transistor to the Schottky diode. The low parasitic inductance of the GaN transistors with LGA
packages makes the addition of an external Schottky diode simple and efficient.
Using the definition of effective dead-time from Figure 6.7, the power losses associated with
the diode conduction as a function of effective dead-time are shown in Figure 6.17 for a typical
GaN transistor and equivalent MOSFET. It can be seen that, due to the lower forward voltage
drop of the MOSFET, the losses as a function of the effective dead-time increase at a lower rate
than that for a GaN transistor.
The addition of an anti-parallel Schottky diode to the GaN transistor synchronous rectifier
will reduce the conduction voltage during the diode conduction period as shown in Figure 6.18.

7


6

5


4

3


2

1


0


–20 0 20 40 60 80 100


**Effective Dead-Time (ns)**

ZVS GaN Transistor
ZVS MOSFET

**Figure 6.17** GaN transistor and MOSFET comparison of the impact of effective dead-time on power
loss of the synchronous rectifier device in a buck converter operating with VBUS = 48 V, IOUT = 16 A,
fsw = 1 MHz

|Col1|Shoot-T|hrough|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||||||||
|||Di|ode Conduc|tion|||
||Partial ZVS||||G a N|T ra n s is to r|
||||||||
||||||M|O S F E T|
||||||||
|20 0 20 40 60 80 1 Effective Dead-Time (ns)|||||||


-----

7

6


5

4


3

2


1


0

–20 0 20 40 60 80 100

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
||E C_Diode|||||||
||||Di|ode Condu|ction||o r|
|||||||G a|N T ra n s is t|
|||||||||
|||||||||
|||||||||
||||||G a N|T ra n s is to r|+ S c h o ttk y|
|20 0 20 40 60 80 1||||||||


**Effective Dead-Time (ns)**

**Figure 6.18** Comparison of the impact of effective dead-time on the power loss of an enhancementmode GaN transistor-based buck converter operating with VBUS = 48 V, IOUT = 16 A, fsw = 1 MHz with
and without an anti-parallel Schottky diode


However, the addition of an anti-parallel Schottky diode does add some output capacitance
with an associated increase in output capacitance loss.
A buck converter was tested with various effective dead-times and the effect of adding an
anti-parallel Schottky diode was measured. The results shown in Figure 6.19 were obtained

90


89

88


87

86


85

84


83 w/o Schottky

w/ Shottky

82
2 4 6 8 10 12 14 16 18 20 22 24 26 28

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||||
||||||||||||||||
|||||||||||Ga T DE|N Trans ≈2. AD|istor 5 ns|||
|||||||||||Ga T DE|N Trans ≈5 AD|istor ns|||
||||||||||||||||
|||||||||||Ga T DE|N Trans ≈10 AD|istor ns|||
|||||||||||Si T DE|MOSFE ≈2. AD|T 5 ns|||
||||||||ky||||||||
||||||||||||||||
||||||w/o|Schott|ky||||||||
||||||||||||||||
||||||w/ S|hottky|||||||||
||||||||||||||||
||||||||||||||||


**Output Current (A)**

**Figure 6.19** Experimental verification of the impact of adding an anti-parallel Schottky diode to an
enhancement-mode transistor in a buck converter with VBUS = 12 V, VOUT = 1.2 V, fsw = 1 MHz


-----

with the converter operating with a VBUS of 12 V, output voltage of 1.2 V, output current of
16 A, and operating at a switching frequency of 1 MHz.

###### 6.5 Frequency Impact on Magnetics

Magnetic components such as transformers and inductors account for the other large
contributor to power loss in switching power converters.

###### 6.5.1 Transformers

Consider a magnetic core with a specific cross-sectional core area and specific winding
window area. The core-area product is commonly used to design magnetic structures [13] and
directly relates to the volume of the core. A constant core-area product results in similar losses
and, consequently, converter efficiencies for a given operating frequency.
As the switching frequency is increased over a practical range for a given material, the core
losses will decrease at a higher rate than the increase in frequency. This is due to the nonlinearity of these losses as a function of the core flux density [14,15], an effect that can be used
to an advantage in a converter using GaN transistors, compared with one using Si MOSFETs. It
may be beneficial to consider magnetic materials with lower core loss density as the frequency
is increased.
As an example, consider what happens when the switching frequency is increased from
300 kHz to 500 kHz. The core cross-sectional area of the 300 kHz design can be decreased to
the point where there is the same flux density as the 500 kHz design. This results in a core crosssectional area that is 60% of the 300 kHz design, as shown in Figure 6.20. Additional effects
from this new core design are:

1. The magnetic core volume has decreased to approximately 60% of the original value.
2. The core losses per unit volume may have increased, but this depends upon the core material
and the switching frequency.
3. The winding volume and mean length-per-turn has also been reduced to approximately 85–
90% (depending on the length-to-width(l/w) ratio). This results in a lower DC winding
resistance and resulting copper wire conduction losses.

l ~0.77•l

w w

y **_B_** **_B_** ~0.7 7•y

2•l + 2•y + 4•w 1.54•l + 1.54•y + 4•w


500 kHz


300 kHz


Mean Length of Turn


**Figure 6.20** Cross-sectional view of two equivalent transformer structures (constant flux density) for
different switching frequencies


-----

4. The AC winding resistance per unit length has increased, due to reduced skin depth, and
depending on the design and conductor thickness. Furthermore, the AC winding resistance
change is proportional to the decrease in DC winding resistance.

Typically, (1) is greater than (2) and (3) is greater than (4) and, therefore, the transformer will
yield a higher efficiency at 500 kHz than at 300 kHz. The extent by which the frequency can be
increased is material-dependent; as the material is pushed beyond its intended operating
frequency range, any real benefit from increasing the frequency will become negated. An
alternative core material may result in higher frequency capability, but at a reduced improvement gain. In the multi-MHz frequency range, many core materials are operating at their upper
limit, and, in some cases, air-core approaches may need to be investigated.

###### 6.5.2 Inductors

In the case of inductors, the impact of the change in magnetic size is similar to the transformer,
but due to a slightly different mechanism. The core material in a transformer will experience a
full flux swing due to the voltage excitation but, in the case of an inductor, the current in the
winding has a DC component to it. This means that the flux excitation and associated losses are
proportionately lower than those of a transformer for the same frequency. However, the
inductor conduction losses will be higher due to the DC component. Using the same analysis as
for the transformer, a more efficient inductor will again result at higher frequencies because (1)
is greater than (2) and (3) is greater than (4). The same upper frequency operating limits apply
to the inductor as for the transformer.

###### 6.6 Buck Converter Example

The analyses of the previous five sections can now be applied to an actual converter. A buck
converter was chosen because it provides a simple circuit that includes a hard-switching device
and a transistor acting as a synchronous rectifier, as shown in Figure 6.21. Since most of the

VBUS

+

Positive
Current

Gate Commutation

|Gate|Col2|
|---|---|
|Dri|ver|


–


Q1 LBuck VOUT

+

Q2

COUT

Gate RLoad
Driver

Negative
Current
Commutation

–

**Figure 6.21** Basic buck converter circuit

|Col1|Col2|
|---|---|
|||
|||


-----

dynamic losses are related to the input voltage, and to the ratio between the input voltage and
output voltage, this basic rule applies: the higher the input voltage and the greater the ratio
between the input and output voltage, the greater the benefits derived from using GaN
transistors.
In this example, a buck converter is used, operating at 1 MHz and delivering 20 A at 1.2 V
into the load with a supply of 12 V. The hard-switching loss analysis is based on the
EPC2015 [3] for both the control switch (Q1) and the synchronous rectifier (Q2). The
buck inductor value is 300 nH for continuous-conduction mode operation, and both devices
are driven with an external turn-on gate resistance of 2 Ω, and turn-off gate resistance of 0.5 Ω.
The calculated losses will be compared with experimental measurements.
The buck converter has two switching events, defined relative to the control switch, as turnon (where the switch-node voltage will rise to the bus voltage) and turn-off (where the switchnode voltage falls to zero). Since there are two transistors involved in this design, four
conditions need to be analyzed: the turn-on and turn-off events for each of the transistors, as
shown in Figure 6.22. The turn-off switching transient is defined as self-commutation. The
current (IBuck) in the buck inductor (LBuck) at the time Q1 is turned off will discharge the output
capacitance, without Q2 being turned on, and hence reduces the switch-node voltage on its
own. The turn-on switching transient is defined as forced commutation. Regardless of the
current in the buck inductor at the time Q2 is turned off, the switch-node voltage must be forced
to the bus voltage when Q1 turns on.
An analysis of the buck converter is required before calculating device losses:


**Q1 Turn-Off**
**Q2 Turn-On**
**Self Communication**


**Q1 Turn-On**
**Q2 Turn-Off**
**Forced Communication**


VBUS
VSW

Iturn_OFF

IRipple ILoad

IBuck

Iturn_ON

time

1/fSW

**Figure 6.22** Buck converter waveforms

|V V BUS|Col2|t OFF I turn_OFF|t ON I V SW I Load I Buck|Col5|
|---|---|---|---|---|
|le|||||
|||I turn_ON|I Buck||
||||||
|||||tim|


-----

The control switch duty cycle (D) is given by [16,17,18]:

D [V][OUT]

VBus

[1.2]

12
0.1 10%
 


(6.32)


Using this duty cycle, the peak-to-peak ripple current in the inductor can be calculated:

? D
 
IRipple  [V][Bus]fsw[ �] ? L[V][OUT]Buck


12 1.2 ? 0.1
 � 

1 ? 10[6] ? 300 ? 10[�][9]

3.6 A



(6.33)


Using the load current in the inductor and Equation 6.33, the turn-on current (rising transition
of the switch node) can be calculated using:

ITurn-on  ILoad � [I][Ripple]2


20
 � [3.6]
2
18.2 A



(6.34)


The corresponding turn-off (falling transition of the switch node) current of the control switch
is given by:

ITurn-off  ILoad  [I][Ripple]2


20 [3.6]
 
2
21.8 A



(6.35)


The operating mode of the buck converter results in positive current commutation for the
control switch, and negative current commutation for the synchronous rectifier (diode
conduction operation). The effective dead-time is set to 5 ns for both transitions. Due to
the ripple current, the current-related losses for the control switch will need to be determined
independently from the synchronous rectifier.
Given all these conditions, Table 6.2 highlights parameters that need to be calculated for the
complete loss analysis.

###### 6.6.1 Output Capacitance Losses

POSS losses will be analyzed first. Since COSS is only dependent on the input voltage, both the
control switch and synchronous rectifier can be analyzed simultaneously. From the
EPC2015 [3] datasheet, the COSS as a function of drain-to-source voltage can be used to


-----

**Table 6.2** Loss analysis parameters

Transition state Control Switch Synchronous Rectifier


Turn-off Turn-on Turn-on Turn-off

Commutation Self Forced Diode Diode
Effective dead-time Fixed at 5 ns Fixed at 5 ns Fixed at 5 ns Fixed at 5 ns
POSS No Yes No Induced in control FET
PG Yes (1/2 PG) Yes (1/2 PG) Yes (1/2 PG) Yes (1/2 PG)
PSD No No Diode conduction Diode conduction
PRR No No No No
Pon N/A Yes Small (from diode) N/A
Poff Yes N/A N/A Small (to diode)


determine EOSS as a function of drain-to-source voltage using Equation 6.14, and as plotted in
Figure 6.23.


VBUS

EOSS  vDS ? COSS v DS ? dvDS

0

∫

12

 vDS ? COSS v DS ? dvDS

0

∫

80.6 nJ



(6.36)


Since there are two devices and only one transition that creates EOSS losses, the total EOSS
will be 161 nJ, and is dissipated in the control switch only. Therefore at 1 MHz, the POSS is
161 mW.


1400

1200


0.6

0.5


1000

800


0.4

0.3


600

400


0.2


200

0


0.1

0

0 5 10 15 20 25 30 35 40

|Col1|C OSS|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
||E OSS|||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||


**VDS (V)**

**Figure 6.23** COSS and EOSS as a function of drain-to-source voltage for the EPC2015 [3]


-----

###### 6.6.2 Gate Losses (PG)

The magnitude of the gate losses is small in comparison to switching losses, but the values for
QGS2 and QGD need to be determined for later use in the switching loss calculations.
Both devices incur gate losses. The drain current will affect the total gate charge such that the
values differ for the control switch and synchronous rectifier. In the case of the control switch,
the total gate charge includes QGD as the device experiences a voltage transition. The
synchronous rectifier, however, has no QGD component as it always switches from diode
conduction.
Before QGS can be determined for the specific operating condition, the value of the plateau
voltage must be read from the device transfer characteristic graph (extracted from the
EPC2015 [3] datasheet), and as shown in Figure 6.24, with Vpl = 2.3 V at IDS =33 A and
Vpl(op) = 2.2 V at IDS = 20 A.
The value for QGS can now be determined using Equation 6.7 and the EPC2015 [3]
datasheet, which is QGS = 3 nC. The QGS(op) value for the buck example then can be
calculated:


QGS op  [] �QVGSpl �


? Vpl op 


� 3 �


2.3


? 2.2


(6.37)


2.87 nC



150

100


50

33 A
20 A

2.3 V
2.2 V

0
0.5 1 1.5 2 2.5 3 3.5 4 4.5

|V D|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||25˚C 125˚C||||||||
||V D|=3 V S||||||||
|||||||||||
|||||||||||
||||||||2.3 V 2.2 V|||
|||||||||||
|||||||||||


**VGS – Gate-to-Source Voltage (V)**

**Figure 6.24** Transfer characteristic for EPC2015 [3] with Vpl_ds (at 33 A) and Vpl (at 20 A) shown


-----

Using the same method and Equation 6.6, and the typical value given in the datasheet for Vth as
1.4 V, QGS1 results in:


QGS1  �QVGSpl �


? Vth


� 3 �


2.3


? 1.4


1.83 nC


QGS2 can then be calculated using Equation 6.8, which yields:


(6.38)

(6.39)


QGS2  QGS op  [�] [Q]GS1
2.87 1.83
 �


1.04 nC


The value of QGD cannot be linearly approximated, so in this case, it needs to be determined
from the CRSS capacitance. From the EPC2015 [3] datasheet, the CRSS as a function of drain-tosource voltage can be used to determine QGD as a function of drain-to-source voltage using
Equation 6.3. This result has been plotted in Figure 6.25, and the value of QGD at 12 V is
1.94 nC.
Knowing both QGS2 and QGD, it is possible to estimate QG(op). Once the device has fully
turned on, the slope of the QG graph will always be the same, regardless of the voltage or
current to which the device is switching. The slope can be determined from the datasheet for the


250

200


4.0

3.5


150

100


3.0

2.5


2.0

1.5


50

0

|Col1|C RSS Q GD|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||
||||||||||||


0 5 10 15 20 25 30 35 40


1.0

0.5


0.0


**VDS (V)**

**Figure 6.25** CRSS and QGD as a function of drain-to-source voltage for the EPC2015 [3]


-----

region between the plateau voltage and the final gate voltage (5 V) using Equation 6.40 for the
datasheet-provided conditions:

 
mQGslope  [Q][G][ �]VDR[Q] �[GS][ ]V[ Q]pl [GD]


 

[10.5][ �] [3][ ][ 2.5]

5 2.3
�

1.85 [nC][.]
 V


(6.40)


Using the slope (mQGslope) the QG(op) for each of the operating conditions can be determined.
First, for the control switch:


QG op  [][ Q]� GS op  [][ Q]GD�  m� QGslope ? V� DR � Vpl��

1.04 1.94 1.85 ? 5 2.2
     � 


10 nC


and for the synchronous rectifier:


QG op  [][ Q]� GS op  [][ Q]GD�  m� QGslope ? V� DR � Vpl��

1.04 0 1.85 ? 5 2.2
     � 


(6.41)

(6.42)


8.1 nC


The new calculated values for QGS, QGD, and QG are plotted as a function of gate-to-source
voltage in Figure 6.26 together with the plot given in the datasheet. Figure 6.26 shows the gate
charge difference between the control switch and synchronous rectifier.


5

4


3

2


1

0


8.1 nC 10 nC 10.5 nC

Control Sw

Sync. Rect.

mQGslope

Datasheet

20 V, 33 A

12 V, 20 A

0 V, 20 A

0 2 4 6 8 10 12

|Col1|Con|trol Sw|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
||S|ync. Rect.||||||
|||||||||
||||||||m QGslope|
|||||20 V, 33 A||Datasheet||
|||||20 V, 33 A||||
|||||12 V, 20 A 0 V, 20 A||||
|||||||||


**Gate Charge QG** **(nC)**

**Figure 6.26** QG as a function of gate-to-source voltage for the EPC2015 [3] plotted with the datasheet
value and re-plotted for the two cases of the example


-----

The gate power now can be determined using Equation 6.15. For the control switch:


PG  QG ? VDR ? fsw

10 nC ? 5 V ? 1 ? 10[6]


50 mW



and for the synchronous rectifier:


PG  QG ? VDR ? fsw

8.1 nC ? 5 V ? 1 ? 10[6]



(6.43)

(6.44)


40 mW


###### 6.6.3 Body Diode Conduction Losses (PSD)


Only the synchronous rectifier device incurs diode conduction, which is a function of the
effective dead-time. This dead-time needs to be either selected or determined for each case. For
this example, a fixed value of 5 ns will be selected, and the amount of diode conduction time
calculated. The two cases that need to be analyzed are for turn-off (falling switching-node
voltage) and turn-on (rising switch-node voltage).

**6.6.3.1** **Turn-Off Transient Diode Conduction Losses**


Since the turn-off transition is self-commutating, the buck inductor current at the time of turnoff and the total output charge for both devices need to be determined. The turn-off current has
already been calculated using Equation 6.35 and ITurn-off = 21.8 A. Next, the QOSS for the
devices need to be determined. This can be done using Equation 6.17, the results of which are
plotted in Figure 6.27. The value for QOSS at 12 V is 14 nC.


1400

1200


35

30


1000

800


25

20


600

400


15

10


200

0


5

0

0 5 10 15 20 25 30 35 40

|Col1|C OSS|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
||Q OSS|||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||


**VDS (V)**

**Figure 6.27** COSS and QOSS as a function of drain-to-source voltage for the EPC2015 [3]


-----

The QOSS for the converter is used to determine the effective dead-time using Equation 6.45.

tFall  [Q]I[OSS]off



[2][ ?][ 14 nC]

21.8 A
1.28 ns



(6.45)


It is extremely important to include the QOSS of both devices in Equation 6.45. If both devices
are the same, QOSS simply doubles. If both devices are not the same, each device’s QOSS needs
to be determined independently for the same voltage condition and added together, and the the
total QOSS is used to calculate the fall-time. Furthermore, if the circuit includes a Schottky
diode across the synchronous rectifier, it too must be included in the QOSS calculation. The falltime is determined to be 1.28 ns. Having chosen 5 ns effective dead-time, the diode conduction
time will be:


tDiode  teff � tFall

5 1.28
 �


(6.46)


3.72 ns


It is important to note that a negative result for tDiode would mean that the converter is
operating in the partial ZVS region, which should be avoided due to the high losses.
Next, the voltage drop across the body diode needs to be determined. Again, the datasheet is
referenced for the drain current value. From Figure 6.28, it can be seen that, at 21.8 A, the
voltage drop for diode conduction is 2.25 V. This value should be similar to the plateau voltage
in the case of an enhancement-mode GaN transistor only.


150

100


50

|Col1|Col2|Col3|C|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||25°C 125°|C|||||||
|||||||||||
|||||||||||
||||21.8 A|||2.25 V||||
|||||||||||
|2.2||V|18.2 A|||||||


0 0.5 1 1.5 2 2.5 3 3.5 4 4.5


**VSD – Source-to-Drain Voltage (V)**

**Figure 6.28** Reverse current conduction for the EPC2015 [3]


-----

Now the turn-off reverse conduction losses can be calculated using Equation 6.16:

PSD  VSD ? IDS ? tSD ? fsw

2.25 ? 21.8 ? 3.72 ? 10[�][9] ? 1 ? 10[6]


182 mW


**6.6.3.2** **Turn-On Transient Diode Conduction Losses**


(6.47)


Since this transition is forced-commutating, the buck inductor current at the time of turn-on
needs to be determined. In this case, the diode will conduct nearly instantaneously after the
synchronous rectifier Q2 is turned off and will keep conducting until the control switch is
turned on. This is due to the buck inductor’s current keeping the diode in the conduction state.
Thus, the diode conduction time is equal to the effective dead-time, which is 5 ns for this
example. The turn-on current has already been calculated using the Equation 6.34 as 18.2 A.
Using this current and the datasheet graph in Figure 6.28, the voltage drop for the diode is
2.2 V.
Now the turn-on reverse conduction losses can be calculated using Equation 6.16:


PSD  VSD ? IDS ? tSD ? fsw

2.2 ? 18.2 ? 5 ? 10[�][9] ? 1 ? 10[6]


200 mW


###### 6.6.4 Switching Losses (Psw)


(6.48)


The losses for the control switch and synchronous rectifier will be determined separately.

**6.6.4.1** **Control Switch Dynamic Losses**

The control switch experiences both hard turn-on and turn-off losses. Since all the components
have already been determined, Equations 6.11 and 6.12 can be used to determine the switching
power losses.


2

QGD QGS2
Pon  [V][BUS][ ?][ I][DS]2[ ?][ f][sw][ ?][ R][Gon] ? 664VDR � Vpl  VDR � �Vpl 2 Vth�


3

775


2

1.94 1.04

[12][ ?][ 18.2][ ?][ 10][6][ ?][ 2] ?
 2 6645 � 2.2 [] 5 �2.2  1.4�

�
2

223 mW



3

775


(6.49)


-----

2


3

775


QGD QGS2
Poff  [V][Bus][ ?][ I][DS][ ?]2[ f][sw][ ?][ R][Goff] ? 664 Vpl  �Vpl  Vth�

2


2

1.94 1.04

[12][ ?][ 21.8][ ?][ 10][6][ ?][ 0.5] ?
 2 6642.25 [] �2.25  1.4�

2


3

775


(6.50)


94 mW


**6.6.4.2** **Synchronous Rectifier Dynamic Losses**

The synchronous rectifier’s switching losses are small because it only switches to and from a
diode voltage drop (see Table 6.2). Equations 6.11 and 6.12, therefore, can be used to calculate
the switching power losses with VBUS equated to VSD.


2

QGD QGS2
Pon  [V][BUS][ ?][ I][DS]2[ ?][ f][sw][ ?][ R][Gon] ? 664VDR � Vpl  VDR � �Vpl 2 Vth�


3

775


2

0 1.04

[2.25][ ?][ 21.8][ ?][ 10][6][ ?][ 2] ?
 2 6645 � 2.25 [] 5 �2.25  1.4�

�
2


(6.51)

(6.52)


16 mW



2


3

775

3


QGD QGS2
Poff  [V][BUS][ ?][ I][DS][ ?]2[ f][sw][ ?][ R][Goff] ? 664 Vpl  �Vpl  Vth�775

2

2 3

0 1.04

[2.2][ ?][ 18.2][ ?][ 10][6][ ?][ 0.5] ?
 2 6642.2 [] �2.2  1.4�775

2


6 mW


###### 6.6.5 Total Dynamic Losses (PDynamic)

With all the dynamic loss components calculated, they can be summarized and added together
to yield the total dynamic loss, which is given in Table 6.3.

###### 6.6.6 Conduction Losses (PConduction)

All that remains to be calculated for the total hard-switching device losses are the conduction
losses (PConduction). The conduction time for each device is based on the duty cycle. The duty


-----

**Table 6.3** Buck converter example total dynamic loss

Loss Characteristic (mW) Control Switch Synchronous Rectifier

Turn-off Turn-on Turn-on Turn-off

POSS 0 161 0 0
PG 25 25 20 20
PSD 0 0 182 200
PRR 0 0 0 0
Pon N/A 223 16 N/A
Poff 94 N/A N/A 6
Total Power Loss 528 444

cycle (D) for the control switch already has been calculated using Equation 6.32 and is 10%.
The duty cycle for the synchronous rectifier (DSync) can be determined from the control switch
duty cycle using Equation 6.53:
DSync  1 � D

1 0.1
 �

(6.53)

0.9


90%


The conduction losses (PConduction) for the control switch can then be calculated using Equation
6.54, where the equation for the RMS of the current is given in [19]:


PConduction  I[2]Load []


I[2]Ripple!
12


? RDS on  [?][ D]


�20[2] [3.6][2]�

 

12

128 mW



? 3.2 ? 10[�][3] ? 0.1


and for the synchronous rectifier:

PConduction  I[2]Load []


I[2]Ripple!
12


? RDS on  [?][ D]Sync


(6.54)

(6.55)


� �

20[2] [3.6][2]
 

12


? 3.2 ? 10[�][3] ? 0.9


1155 mW


###### 6.6.7 Total Device Hard-Switching Losses (PHS)

The total device hard-switching losses (PHS) can be calculated by adding the conduction
(PConduction) and dynamic (PDYN) components together.


-----

For the control switch:

For the synchronous rectifier:

###### 6.6.8 Inductor Losses (PL)


PHS  PDYN  PConduction

0.528 0.128
 

656 mW


PHS  PDYN  PConduction

0.444 1.155
 

1599 mW



(6.56)

(6.57)


The final loss component is the inductor loss (PL). The inductor used for this example is the
SLC1175-301ME [20], which has the following parameters: DC resistance (DCR) = 0.24 mΩ,
ACR (at 1 MHz) = 0.24 mΩ, inductance 300 nH. The difference between DCR and ACR
cannot be neglected for switching frequencies in the multi-MHz region. The manufacturer also
provides a core loss calculator on its website [21], which will be utilized in this example.
Alternative methods can be used to determined core losses that include referencing the
manufacturers’ core losses as a function of flux density and frequency.
Using the core loss calculator, the loss (Pcore) was given as 51 mW at 1 MHz with a 3.6 A
ripple current:


PL  I[2]Load [?][ DCR][ ]


I[2]Ripple
? ACR  PCore
12


20[2] ? 240[�][6] 3.6[2][ 3.6][2] ? 240[�][6] 0.051
  

12


(6.58)


147 mW


###### 6.6.9 Total Buck Converter Estimated Losses (PTotal)

Adding all the loss components together yields the total estimated power loss for the buck
converter example:

PTotal  PControl  PSync  PL

656 1599 147 (6.59)
  

2402 mW


This results in an estimated efficiency for the converter of 90.9%, which excludes control
circuit power.


-----

###### 6.6.10 Buck Converter Loss Analysis Accounting for Common Source Inductance

Ignoring the effect of CSI can lead to an artificially low loss prediction. Therefore, in this
section, the switching losses will be recalculated to include the effect of CSI. By the very nature
of CSI, it is impossible to measure without significant perturbation of the circuit.
CSI can be estimated using a commercial parametric extraction simulation program [22] that
can compute the inductance from the layout and the device design. This would require
knowledge of the internal design of the device that would seldom be made available.
Alternatively, CSI can be estimated using circuit simulation software and using an ideal
switch in the simulation. In the simulation, CSI can be added and waveforms compared with
measured waveforms until enough correlation is found. For this calculation, a value of 110 pH
will be used as a reasonable approximation.
Equation 6.31 can be used to determine the equivalent gate circuit resistance introduced by
the CSI. This resistance will be used in conjunction with Equations 6.11 and 6.12 to determine
the CSI-impacted losses. Note that CSI only impacts the current transition interval, and
therefore Equations 6.11 and 6.12 need to be adjusted so that RCSI is only added to RG for the
QGS2 interval.
To calculate RCSI, the value of CGS and transconductance (gm) at the operating conditions are
required. First, the transconductance can be determined using the small signal model for a
MOSFET [23] given in Equation 6.60.


gm  V2pl ? � IDSVth

2 ? 20

2.2 1.4
�
50 S



(6.60)


Next CGS needs to be determined. This value can be derived from QGS, which yields a timeequivalent capacitance, by reading off the values at the plateau voltage:

CGS  [Q]V[GS]pl



[2.87]

2.2
1.3 nF


The equivalent CSI impedance (RCSI) was then calculated using Equation 6.31 as:

RCSI  [L]C[S][ ?]GS[ g][m]

[110][ ?][ 10][�][12][ ?][ 50]

1.3 ? 10[�][9]

 4.22 Ω


(6.61)

(6.62)


-----

**6.6.10.1** **Control Switch Dynamic Losses Including the Effect of CSI**

The control switch turn-on and turn-off losses, adjusted for CSI, can be determined by updating
Equations 6.11 and 6.12 as follows:


2


3


QGD ? RGon 
Pon  [V][Bus][ ?][ I]2[DS][ ?][ f][sw] ? 664VDR � Vpl  [Q]V[GS2]DR �[ ?][ R]�[Gon]Vpl[ ] 2[ R] V[CSI]th�775


2

1.94 ? 2
 

 [12][ ?][ 18.2]2 [ ?][ 10][6] ? 6645 � 2.2 [][ 1.04]5 �[ ?]2.2[ 2][ ] [ 4.22] 1.4�

�
2


3

775


373 mW


2 3

QGD ? RGof f � �
Poff  [V][Bus][ ?][ I]2[DS][ ?][ f][sw] ? 664 Vpl  [Q][GS2]�[ ?]V[ R]pl [Gof f] V[ ]th[ R]� [CSI] 775

2

2 3

1.94 ? 0.5
 

[12][ ?][ 21.8][ ?][ 10][6] ? [1.04][ ?][ 0.5][ ][ 4.22]
 2 664 2.25  �2.25  1.4� 775

2


(6.63)

(6.64)


409 mW


Note the degree to which turn-off losses are affected by CSI: from 94 mW to 409 mW for the
control switch.

**6.6.10.2** **Synchronous Rectifier Dynamic Losses Including the Effect of CSI**

The synchronous rectifier also experiences both hard turn-on and turn-off losses. Since all the
components have already been determined, Equations 6.11 and 6.12 can be used to calculate
the switching energy losses. In the case of turn-on, the rectifier switch only turns on with the
diode voltage drop across it, hence VBUS is equated to VSD at turn-off (ITurn-off).


2


3

775


Pon  [V][BUS][ ?][ I]2[DS][ ?][ f][sw] ? 664QVGDDR ? � RVGonpl  [Q]V[GS2]DR �[ ?][ R]�[Gon]Vpl[ ] 2[ R] V[CSI]th�


2


3


(6.65)


0 ? 2
 

[2.25][ ?][ 18.2][ ?][ 10][6] ?
 2 6645 � 2.25 [][ 1.04]5 �[ ?]2.25[ 2][ ] [ 4.22] 1.4�775

�
2

84 mW



-----

2

QGD ? RGoff 
Poff  [V][BUS][ ?][ I]2[DS][ ?][ f][sw] ? 664 Vpl  [Q][GS2]�[ ?]V[ R]pl [Goff] V[ ]th[ R]� [CSI]

2


3

775


2

0 ? 0.5
 

[2.2][ ?][ 18.2][ ?][ 10][6] ?
 2 664 2.2 [][ 1.04]�[ ?]2.2[ 0.5]  1.4[ ][ 4.22]�

2


3

775


(6.66)


55 mW


Substituting these values for those in Table 6.3 and then recalculating, the total power loss
increased by 582 mW to 2.95 W. The buck converter efficiency was reduced from 90.9% to
88.9%, which is 2.0% lower due to the inclusion of CSI.


###### 6.6.11 Experimental Results for the Buck Converter

Based on the buck converter example, a practical version was designed and tested. The buck
converter was operated and measured at various load currents up to the maximum rating. The
dead-time was set at 5 ns. Measurements taken for the converter include the controller power
and charge pump regulator for the controller IC, which accounts for as much as 152 mW of
power loss in the measurements. The measured efficiency for the buck converter when
operating at 12 VBUS, as shown in Figure 6.29 (third trace from the top), is about 88.1% at 20 A
load. This compares very well with the estimate of 88.4%. Figure 6.29 also shows the
calculated efficiency results without compensating for CSI or controller consumption (top


94

92


90

88


86

84


82


80
4 6 8 10 12 14 16 18 20

**Output Current (A)**

**Figure 6.29** Calculated and measured efficiency results of the GaN transistor-based (EPC2015 [3]) buck
converter operating at 12 V input and compared against a comparable MOSFET converter with control
switch is BSC097N04LSG [11] and synchronous rectifier is BSC0400N04LSG [12]

|Col1|Col2|C|alculatio|n|E|xample|Points|Col9|
|---|---|---|---|---|---|---|---|---|
|Calc|ulation w|ith CSI|& Contro|l|||||
||||||||||
||Measu GaN Tr|red 40 V ansistor|||||||
|||Mea|sured 4|0 V|||||
|||M|OSFET||||||
||||||||||
||||||||||


-----

trace), and with compensating for CSI and controller power consumption (dashed trace above
measured results).
Figure 6.29 also shows the results of an equivalent MOSFET-based converter, operating
under the same conditions (bottom trace). In this case, the GaN transistor-based converter
efficiency exceeds that of the MOSFET converter by several percentage points.

###### 6.7 Summary

In Chapter 6, the mechanism and key factors that contribute to hard-switching losses have been
discussed. The analytical tools needed to calculate losses from the greatest contributors were
developed and used in a concrete example. The calculations agreed with the actual measured
results from a circuit built to these same specifications.
In the next chapter, soft-switching and resonant-switching techniques will be discussed.

###### References

1. Vishay (Dec. 2004) “Power MOSFET Basics: Understanding Gate Charge and Using it to Assess Switching
Performance,”, Appl. Note AN608.
2. On-Semiconductor (April 2012) “MOSFET Gate-Charge Origin and its Applications,” Appl. Note AND9083/D.
3. Efficient Power Conversion Corporation “EPC2015 – Enhancement-mode Power Transistor,” EPC2015 datasheet,
[March 2011 [Revised Jan. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2015_datasheet](http://epc-co.com/epc/documents/datasheets/EPC2015_datasheet.pdf)
[.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2015_datasheet.pdf)
4. Strydom, Johan, “The eGaN FET-Silicon Power Shoot-Out: 1: Comparing Figure of Merit (FOM),” Power
_[Electronics Technology, Sept. 1, 2010, Available from http://powerelectronics.com/power_semiconductors/](http://powerelectronics.com/power_semiconductors/power_mosfets/fom-useful-method-compare-201009/)_
[power_mosfets/fom-useful-method-compare-201009/.](http://powerelectronics.com/power_semiconductors/power_mosfets/fom-useful-method-compare-201009/)
5. Huang, A.Q. (2004) New unipolar switching power device figures of merit. IEEE Electron Device Letters, 25,
298–301.
6. Kim, I.-J.Il.-Jung., Matsumoto, S., Sakai, T., and Yachi, T. (1995) “New power device figure-of-merit for high
frequency applications,” in Proc. Int. Symp. Power Semiconductor Devices ICs, Yokohama, Japan, pp. 309–314.
7. Baliga, B.J. (1989) Power semiconductor device figure-of-merit for high frequency applications. IEEE Electron
_Device Letters, 10, 455–457._
8. Ying, Y. (2008) Device selection criteria – based on loss modeling and Figure of Merit, M.S. thesis, Virginia Tech.
9. Reusch, D., “Improving System Performance with eGaN[] FETs in DC-DC Applications,” 46th International
Symposium on Microelectronics, iMAPS 2 October 2013.
10. Reusch, D., Gilham, D., Su, Y., and Lee, F. (Feb. 2012) “Gallium nitride based 3D integrated non-isolated point of
load module,” in Applied Power Electronics Conference and Exposition (APEC), 2012 Twenty-Seventh Annual
IEEE, Orlando, FL, pp. 38–45.
11. Infineon (March 18 2010) “OptiMOS[TM] 3 Power-Transistor,” BSZ097N04 datasheet.
12. Infineon (Nov. 5 2009) “OptiMOS[TM] 3 Power-Transistor,” BSZ040N04 datasheet.
13. Colonel, W. and McLyman, T. (2004) Transformer and Inductor Design Handbook, CRC Press.
14. Steinmetz, C.P. (1892) On the law of hysteresis. AIEE Transactions, 9, 3–64. Reprinted under the title “A
Steinmetz contribution to the AC power revolution,” introduction by Brittain, J.E. (1984) Proceedings of the IEEE,
**72 (2), 196–221.**
15. Reinert, J., Brockmeyer, A., and De Doncker, R.W. (2001) Calculation of losses in ferro- and ferrimagnetic
materials based on the modified Steinmetz equation. IEEE Transactions on Industry Applications, 37 (4),
1055–1061.
16. Hauke, B. (2012) “Basic Calculation of a Buck Converter’s Power Stage,” Texas Application Report SLVA477A –
December 2011– Revised August.
17. Ejury, J. (January 2013) “Buck Converter Design,” Infineon Design Note DN 2013-01 V1.0.
18. Schelle, D. and Castorena, J. (Jure 2006) Buck-converter design demystified, Power Electronics Technology, pp.
[46–53. Available from http://powerelectronics.com/dc-dc-converters/buck-converter-design-demystified.](http://powerelectronics.com/dc-dc-converters/buck-converter-design-demystified)
19. Erickson, R.W. and Maksimovic, D. (January 2001)́ _Fundamentals of Power Electronics, 2nd edn, Springer._
[20. SLC1175-301ME datasheet http://www.coilcraft.com/pdfs/slc1175.pdf.](http://www.coilcraft.com/pdfs/slc1175.pdf)


-----

[21. Coilcraft, “Coilcraft Core and conductor loss calculator,” [Updated July 20, 2012]. Available from http://www](http://www.coilcraft.com/apps/loss/loss_1.cfm)
[.coilcraft.com/apps/loss/loss_1.cfm.](http://www.coilcraft.com/apps/loss/loss_1.cfm)
[22. Ansys, “Ansys Q3D Extractor,” Available from http://www.ansys.com/Products/Simulation+Technology/Elec-](http://www.ansys.com/Products/Simulation+Technology/Electromagnetics/Signal+Integrity/ANSYS+Q3D+Extractor)
[tromagnetics/Signal+Integrity/ANSYS+Q3D+Extractor.](http://www.ansys.com/Products/Simulation+Technology/Electromagnetics/Signal+Integrity/ANSYS+Q3D+Extractor)
23. Cartwright, K.V. (2009) Derivation of the exact transconductance of a FET without calculus. The Technology
_Interface Journal, 10 (1)_
24. Reusch, D. (2012) “High frequency, high power density integrated point of load and bus converters,” Ph.D.
[dissertation, Virginia Tech, Blacksburg, VA, Available from http://scholar.lib.vt.edu/theses/available/etd-](http://scholar.lib.vt.edu/theses/available/etd-04162012-151740/)
[04162012-151740/.](http://scholar.lib.vt.edu/theses/available/etd-04162012-151740/)
25. Reusch, D., “eGaN[] FET-Silicon Power Shoot-Out Vol. 13, Part 1: Impact Of Parasitics,” Power Electronics
_[Technology, March 2013, Available from http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-](http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-out-vol-13-part-2-optimal-pcb-layout#!.)_
[shoot-out-vol-13-part-1-impact-parasitics#!.](http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-out-vol-13-part-2-optimal-pcb-layout#!.)
26. Reusch, D., “eGaN[] FET-Silicon Power Shoot-Out Vol. 13, Part 2: Optimal PCB Layout,” Power Electronics
_[Technology, April 2013, Available from http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-](http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-out-vol-13-part-2-optimal-pcb-layout#!.)_
[shoot-out-vol-13-part-2-optimal-pcb-layout#!.](http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-out-vol-13-part-2-optimal-pcb-layout#!.)


-----

# 7

#### Resonant and Soft-Switching Converters

###### 7.1 Introd uction

The previ ous chapte r addres sed the ap plication of GaN transistors in hard-s witching p ower
convert ers, and we demon strated the benefi ts that GaN trans istors provide – as c ompared to
state-of- the-art sil icon power MOSF ETs. In this chapter, we discuss the fundamenta ls of
resona nt and soft-swit ching appli cations and evalua te the superior perfor mance capabi lities of
GaN trans istors over silicon MOS FETs in these appli cations. The chapte r wi ll conclu de with a
design ex ample compa ring GaN trans istors and Si MO SFETs in a n isol ated, high- freque ncy
48 V intermed iate bus convert er (IBC) with a 12 V output, utilizing a resonant topol ogy
operat ing at 1.2 MHz.

###### 7.2 Reson ant and Sof t-Switching Techniques

Resonant and soft -switch ing techni ques can imp rove perfor mance in con verters by reduci ng
switch ing-relat ed loss es compa red to convent ional hard-swi tching converters. This is accom plished by creat ing operat ing cond itions where the transist or does not en counter sim ultaneous
high vo ltage and high curren t during the switching commu tation. The re are many different
resona nt and soft -switching technique s [1 –4] and the tw o c onditions in commo n are zerovoltage switch ing (ZVS) and zero-cu rrent switch ing (Z CS).

###### 7.2.1 Zer o-Voltage and Zer o-Current Switching

Zero-vol tage switch ing is used to elim inate the turn-o n comm utation loss es in a switch ing
device . ZVS is achiev ed when the transistor d rain-to-source voltage is reduced to zero before
turning on . To reduce the drain-to- source voltage across the trans istor in the maj ority of
resona nt and soft -switching topolo gies, the device output charge (QOSS ) must be remo ved by
conduct ing curren t from source to drain throu gh the output capacitance (COSS) unti l the drainto-source voltage reaches zero. The switch ing trajector y o f a tradi tional hard-s witching and
ZVS, soft-switching, turn-on transition is shown in Figure 7.1(a), where the x-axis, VDS,

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

Hard Switching Hard Switching
**IDS** Transition **IDS** Transition

Finish Start

**IDS**

**COSS**
**VDS**

ZVS Transition Start ZCS Transition Finish

**VDS** **VDS**

(a) (b)

**Figure 7.1** Ideal switching transition for (a) zero-voltage switching turn-on transition (b) zero-current
switching turn-off transition

represents switch voltage, and the y-axis, IDS, represents switch current. For the hard-switching
transition, first the current rises to the load current, then the voltage falls to zero. This results in
large values of voltage and current being commutated simultaneously in the transistor,
generating loss as well as incurring EOSS losses as discussed in Chapter 6. For the ZVS
transition, before the transistor current rises to the load current, a negative current drives the
drain-to-source voltage to zero, creating a soft turn-on condition. The device does not
commutate high voltage and high current simultaneously, reducing the turn-on commutation
losses in the device to zero, and eliminating EOSS losses.
While ZVS erases turn-on commutation losses, it does not reduce the turn-off commutation
losses. ZCS provides soft commutation during device turn-off, as shown in Figure 7.1(b). For the
hard-switching turn-off transition, also shown in Figure 7.1(b), first the voltage rises to the bus
voltage, and then the current falls to zero. This results in large values of voltage and current being
commutated simultaneously in the transistor, generating losses. ZCS occurs when the transistor
drain-to-source current is reduced to zero and before turning off. To achieve ZCS, the current is
shaped as a sinusoidal pulse using a resonant network. When the switch current resonates to zero,
the device can turn off with ZCS. During a ZCS turn-off transition, large values of voltage and
current are not commutated simultaneously in the transistor, virtually eliminating the turn-off
losses in the transistor. For ZCS resonant converters, the hard-switching turn-on commutation
remains, and the turn-on switching transition and EOSS losses are dissipated in the device.
For resonant and soft-switching topologies to operate under ZVS and ZCS, passive networks
are required to shape the transistor’s voltage and current. Often, the addition of passive resonant
components can be avoided by utilizing the parasitics internal to the device and in-circuit
elements such as package and PCB inductances. This allows the parasitics that diminished hardswitching converter performance to be used effectively to achieve soft-switching commutations
in resonant and soft-switching converters. For the majority of resonant and soft-switching
DC-DC power converters, zero-voltage switching is preferred to zero-current switching due to
the reduction of the EOSS losses, which are incurred only during the turn-on switching transition.

###### 7.2.2 Resonant DC-DC Converters

The traditional approach for resonant converters used for DC-DC power conversion is shown
in Figure 7.2. The input voltage source, VIN, connects to a switching network, which outputs a

|Hard Switching Transition|Col2|
|---|---|
|Finish ZVS Transition Start||
|ZVS Transition||
|||


-----

**+**

VIN Switch Resonant Rectifier Load

**–** Network Network Network

**Figure 7.2** Resonant DC-DC converter block diagram consisting of switch network, resonant network,
and rectifier network

pulsed waveform to the resonant network. The resonant network then shapes the voltage or
current to achieve soft-switching in the switching network’s power devices. Following the
resonant network is the rectifier network, which rectifies and filters the voltage and current to
deliver DC power to the load.

###### 7.2.3 Resonant Network Combinations

The most basic resonant networks consist of a series network, where the load is connected in
series with the resonant capacitance (CS), as shown in Figure 7.3(a), a parallel network, where
the load is connected in parallel with the resonant capacitance (CP), as shown in Figure 7.3(b),
or a combination of the series and parallel networks, also known as a series-parallel network, as
shown in Figure 7.3(c). Another popular resonant network is the LLC, where the parallel
capacitance (CP) of the series parallel network is replaced with a parallel inductor (LP), and LR
and CS are rearranged, as shown in Figure 7.3(d). These different resonant networks can
operate with ZVS or ZCS and can provide unique benefits, while having disadvantages when
compared to traditional hard-switching converters [1–3,5,6]. There are also less common

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|+ –|Switch Network||Resonant Network||Rectifier Network||Load|
|||||||||
|||||||||


LR

LR


CS LR

(a) (b)


CS


CS


LR


(c) (d)

**Figure 7.3** DC-DC converter resonant networks (a) series LC (b) parallel LC (c) series-parallel LCC (d)
LLC


-----

resonant network topologies as well as multi-element resonant networks that can be employed
as resonant tanks [5,7,8].

###### 7.2.4 Resonant Network Operating Principles

In this section, the basic operation of a common resonant configuration – the series-resonant
network, shown in Figure 7.3(a) – will be discussed. This series-resonant network allows for
either ZVS or ZCS to occur in the switching network transistors, reducing either turn-on or turnoff commutation losses. The magnitude of the impedance of the series network can be given by:


qffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi
jZSRNj [] R[2]  X L � XC[2] 


sffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi� 1 �2

R[2]  ω ? LR � ω ? CS


(7.1)


XL  ω ? LR (7.2)

1
XC  ω ? CS (7.3)

where XL and XC are the reactances of the inductor and capacitor respectively, R is the
equivalent load resistance, ZSRN is the magnitude of the impedance of the series-resonant
network, and ω is the angular frequency of the resonant network. The standard frequency
common to DC-DC converters is given by:

f  [ω] (7.4)
2 ? π

where f is frequency measured in hertz.
The magnitude of the impedance plot for a series-resonant network is shown in Figure 7.4.
The resonant frequency is the point where the network transitions from appearing capacitive to
inductive. The resonant frequency provides the minimum impedance and is given by:

1
f0  2 ? π ? pffiffiffiffiffiffiffiffiffiffiffiffiffiffiLR ? CS (7.5)


IZSRNI

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
||1 ω·|C S|||||||||||ω·|L|R|||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||


**fO** **f**

**Figure 7.4** Impedance plot of series-resonant network


-----

ZVS Hard Hard ZCS

VDS Turn-On Turn-Off VDS Turn-On Turn-Off
IDS IDS

t t

(a) (b)

**Figure 7.5** Operation of series-resonant converter transistor (a) above the resonant frequency (b) below
the resonant frequency

The turn-on commutation of a transistor connected to a series-resonant network operating
above the resonant frequency will switch under ZVS. Operation above the resonant frequency
makes the resonant tank appear inductive, as shown in Figure 7.4. For an inductive load, the
current lags the voltage, as shown in Figure 7.5(a). The inductive-resonant tank produces a
negative current in the device before turn-on, discharging the transistor output charge and
allowing for a soft ZVS turn-on commutation. For operation above the resonant frequency, there
will be voltage and current in the device at turn-off, leading to a hard turn-off commutation.
For operation below the resonant frequency, the transistor will turn off under ZCS. For a
series-resonant converter, operation below the resonant frequency makes the resonant tank
appear capacitive, as shown in Figure 7.4. For a capacitive load, the current leads the voltage, as
shown in Figure 7.5(b). The capacitive-resonant tank produces a negative current in the device
before turn-off, allowing for a soft ZCS turn-off commutation. For operation below the
resonant frequency, there will be voltage and current in the device at turn-on, leading to a hard
turn-on commutation and EOSS losses.

###### 7.2.5 Resonant Switching Cells

The best performance is achieved for traditional resonant converters operating close to the
resonant frequency, yet output regulation is achieved by varying the switching frequency. The
further the operating frequency is moved from the resonant point to maintain regulation, the
more the performance of the resonant converter suffers from higher circulating energy and
component stresses [1–8].
To apply the principles of resonant power conversion to pulse width modulated (PWM)
converters, another family of resonant converters was developed [1,9]. These quasi-resonant
(QR) cells are commonly seen in DC-DC power conversion and combine a resonant network
with a single transistor to create a ZVS or ZCS device. They can be applied to traditional nonisolated topologies like the buck converter discussed in Chapter 6 [1,3,4], as well as to various
other topologies and applications. The resonant cells use the same concept of shaping of the
voltage and or current to achieve soft-switching as the traditional resonant networks. (Later in
this chapter there will be a design example to demonstrate the use of a QR cell in a GaN-based
resonant converter.) The ZVS QR cell, shown in Figure 7.6(a), places a resonant capacitor, CR,
in parallel with the transistor and a resonant inductor in series with the capacitor-switch
network, while the ZCS QR cell, shown in Figure 7.6(b), places the resonant capacitor in
parallel with the series combination of the resonant inductor-switch network.


-----

SZVS LR SZCS LR

CR CR

(a) (b)

**Figure 7.6** Quasi-resonant switching cells (a) ZVS (b) ZCS

###### 7.2.6 Soft-Switching DC-DC Converters

Soft-switching converters can be seen as a hybrid between hard-switching PWM converters
and frequency-controlled resonant converters. Soft-switching converters employ resonant
techniques for a portion of the operating period to achieve a soft device commutation,
with the remaining period operating as a PWM converter [2,3]. This allows for transistor
soft commutation while reducing the higher circulating energy and device stresses associated
with resonant converters, as well as offering PWM control for output regulation.

###### 7.3 Key Device Parameters for Resonant and Soft-Switching Applications

In resonant and soft-switching applications, the switching-related losses are minimized by
using techniques to achieve ZVS and ZCS. With the reduction of switching losses, the QGD and
QGS2 terms that dominated losses in hard-switching applications are no longer the critical
device parameters determining in-circuit performance. The two device parameters key to high
performance in resonant and soft-switching applications are device output charge, QOSS, and
gate charge, QG.

###### 7.3.1 Output Charge (QOSS)

Output charge has a large impact on the performance of resonant and soft-switching converters
as it directly impacts the energy required to achieve ZVS. A reduction in energy can result in
reduced ZVS transition times and currents, providing both a longer power delivery period and
lower RMS currents in high-frequency resonant and soft-switching converters. In a ZCS
topology, the energy of the output capacitance (EOSS) is dissipated when the transistor turns on
in the same manner as a hard-switching commutation.
Before a ZVS transition can occur, the output capacitance must be discharged, bringing the
drain-to-source voltage of the transistor to zero volts before turning on the transistor. The time
required to achieve ZVS is given by:

tZVS  [C][OSS TR]IZVS [][ V]DS  [Q]IZVS[OSS] (7.6)

where tZVS is the time required to discharge the output capacitance, COSS(TR) is the time-related
output capacitance, VDS is the transistor drain-to-source voltage, IZVS is the soft-switching


-----

**Table 7.1** Data from an Efficient Power Conversion EPC2001 datasheet showing transistor capacitances
and associated charges [10]

Parameter Test conditions Min Typical Max Unit

Dynamic characteristics (Tj = 25 °C unless otherwise stated)
CISS Input capacitance VDS = 50V, VGS = 0 V — 850 950 pF
COSS Output capacitance — 450 525
CRSS Reverse transfer capacitance — 20 30
QG Total gate charge (VGS = 5 V) VDS = 50 V, ID = 25 A — 8 10 nC
QGD Gate-to-drain charge — 2.2 2.7
QGS Gate-to-source charge — 2.3 2.8
QOSS Output charge VDS = 50 V, VGS = 0 V — 35 40
QRR Source-drain recovery charge — 0 0

_All measurements were done with substrate shorted to source._

current used to discharge the transistor’s output capacitance, and QOSS is the output charge of
the transistor.

###### 7.3.2 Determining Output Charge from Manufacturers’ Datasheet

To properly design a ZVS transition, the values of COSS and QOSS at the proper in-circuit
operating conditions are critical. Values for COSS and QOSS are generally given for a single
drain-to-source operating voltage in manufacturers’ datasheets as shown in Table 7.1 for a
100 V EPC2001 [10] enhancement-mode GaN transistor, and Table 7.2 for a 100 V silicon
MOSFET from Infineon, the BSC060N10NS3G [11].
The single output charge and capacitance point given in manufacturers’ datasheets does not
provide enough information to properly design for a wide range of operating conditions. The
output capacitance of both GaN transistors and MOSFETs is highly non-linear, and the output
charge varies with drain-to-source voltage. Figure 7.7 shows the capacitance curves for the
100 V EPC2001 [10] and the 100 V BSC060N10NS3G [11] MOSFET, where it can be seen

**Table 7.2** Data from an Infineon BSC060N10NS3G datasheet showing transistor capacitances and
associated charges [11]

Parameter Test conditions Min Typical Max Unit

Dynamic characteristics
CISS Input capacitance VGS = 0 V, VDS = 50 V, — 3700 4900 pF
COSS Output capacitance f = 1 MHz — 650 860
CRSS Reverse transfer — 25 —
capacitance

QGS Gate-to-source charge VDD = 50 V, ID = 25 A, VGS = 0 — 15 — nC
QGD Gate-to-drain charge to 10 V — 9 —
QSW Switching charge — 13 —
QG Gate charge total — 51 68
QPlateau Gate plateau voltage — 4.2 — V
QOSS Output charge VDD = 50 V, VGS = 0 V — 68 91 nC


-----

1.4

1.2

1


10[4]

|Col1|C (0 V) ≈1.35 nF OSS|
|---|---|


0.8

0.6 COSS (50 V) ≈0.45 nF

0.4

0.2

0 0 10 20 30 40 50 60 70 80 90 100

|Col1|C (50 V)≈ 0.45 nF OSS|
|---|---|


10[0]
0 20 40 60 80
VDS (V)


**VDS Drain-to-Source Voltage (V)** VDS

(a) (b)


![](GaN-transistors-power-conversion.pdf-152-0.png)

10[4]

Ciss

10[3] Coss

10[2] Crss COSS(50 V) ≈0.65 nF

10[1]

10[0]
0 20 40 60 80
VDS (V)


**Figure 7.7** Capacitance curves of (a) EPC2001 GaN transistor [10] (b) BSC060N10NS3G Si MOSFET

[11]

that the output capacitance changes by factors of three and six, respectively, for GaN transistors
and Si MOSFETs from 0 V to 50 V.
The output charge and effective time-related capacitance for a transistor at any given voltage
can be calculated from the manufacturers’ datasheets in the same manner as the hard switching
converters discussed in Chapter 6:


VDS

QOSS V DS  COSS V DS ? dVDS (7.7)
∫0


 
COSS TR [V]DS  [Q][OSS][ V][DS] (7.8)
VDS

where VDS is the drain-to-source operating voltage of the transistor.
The output charge for the EPC2001 [10] GaN transistor and BSC060N10NS3G [11] Si
MOSFET are calculated and plotted in Figure 7.8 using Equation 7.7 for drain-to-source
voltages varied from 0 V to the maximum voltage listed in the manufacturers’ datasheets. The
GaN transistor, with a similar on-resistance, offers a significant reduction in output charge over
the entire voltage range.


###### 7.3.3 Comparing Output Charge of GaN Transistors and Si MOSFETs

To compare the output charge figure of merit between GaN and MOSFET technologies in
resonant and soft-switching applications, the product of the on-resistance and output charge for
state-of-the-art 40 V, 100 V, 200 V, and 600 V GaN and Si MOSFETs are plotted in Figure 7.9.
The GaN devices offer a significant reduction in output charge FOM, with the gains increasing
as voltage increases. The reduction in FOM allows the circuit designer to reduce the transistor
conduction losses, shorten the ZVS transition, or reduce the ZVS current, all of which would
lower converter loss and improve efficiency. These benefits will be demonstrated experimentally in the design example later in this chapter.


-----

100

90

80

70

60

50

40

30

20

10


0

0 20 40 60 80 100

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
|1|00 V Si MOS|FET|||
||||||
||||||
||||||
||||||
|||100 V GaN|Transistor||
||||||
||||||


**VDS - Drain-to-Source Voltage (V)**

**Figure 7.8** Output charge for varying drain-to-source voltages for 100 V EPC2001 GaN transistor and
100 V BSC060N10NS3G Si MOSFET


###### 7.3.4 Gate Charge (QG)

The frequency capability of resonant and soft-switching topologies are also significantly
impacted by the gate charge, QG. The gate charge is the amount of charge required to fully turn
on or off the transistor. Voltage source drivers are employed for the vast majority of DC-DC
converters. This voltage source appears in series with the input capacitance of the transistor and
has an effective resistance equal to the sum of the gate driver circuit’s internal and external
resistance and the internal gate resistance of the transistor. The gate charge is dissipated each
switching cycle, resulting in a gate drive loss equal to:


PG  QG ? VDR ? fsw (7.9)

where VDR is the gate drive voltage and fsw is the switching frequency.
Looking beyond the gate drive power loss, the gate driving speed also has a large impact on
the performance of high-frequency resonant and soft-switching converters. The switching
period is inversely proportional to switching frequency and, as frequencies increase, the gate
rising and falling speeds can become limitations to the minimum switching time. The design
example at the end of this chapter will illustrate this issue and show how GaN technology can
offer superior performance in high-frequency DC-DC converters compared to Si MOSFETs.


###### 7.3.5 Determining Gate Charge for Resonant and Soft-Switching Applications

To enable users to calculate gate charge, manufacturers supply a gate charge curve similar to
Figure 7.10 for the 100 V EPC2001 [10] GaN transistor. The gate charge, QG, is given for a
hard-switching transition and not directly applicable to resonant and soft-switching applications. The definition of charges QGS1, QGS2, QG, QGD, and QGS are given in Chapters 3 and 6.
For a ZVS application, the voltage commutation period occurs before the device turns on, and
the Miller plateau region as well as the accompanying charge, QGD, are eliminated from the


-----

200

20


2

0.2


(a)


200

20


2


0.2

1 10 100 1000


**RDS(on) (mΩ)**


(b)

**Figure 7.9** Output charge figure of merit comparison between GaN and Si devices


total gate charge. The gate charge for ZVS topology can be given by:

QG_ZVS  QG � QGD (7.10)


where QG is the gate charge of a hard-switching application, and QGD is the gate-to-drain
charge.
For a ZCS transition, the current commutation period occurs before device turn-off, and the
QGS2 period is eliminated. While this reduces switching commutation losses, it does not


-----

5


4.5

4


3.5

3


2.5

2


1.5

1


0.5

0

0 2 4 6 8 10

|I = 25 A D|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||I = 25 A D||||||||||
||V = 50 V DS|||Q GD|||||||
|Q|||||||||||
|GS|||||||||||
|Q GS Q GS1||||2||||V pl|||
||||||||||||
||||||||||||
||||||||V th||||
||||||||||||
||||||||||||
|||||||||Q G|||
||||||||||||
||||||||||||


**QG Gate Charge (nC)**

**Figure 7.10** Gate charge curve for a 100 V EPC2001 GaN transistor [10]


significantly impact the total gate charge as the slopes of the QGS2 period and the QG period
following the QGD region are generally similar.

QG_ZCS  QG (7.11)


###### 7.3.6 Comparing Gate Charge of GaN Transistors and Si MOSFETs

The gate charge figure of merit comparison for state-of-the-art 40 V, 100 V, 200 V, and 600 V
GaN and Si MOSFETs is plotted in Figure 7.11. The GaN devices offer a significant reduction
in gate charge FOM, with the gains increasing as voltage increases. The reduction in FOM
allows the circuit designer to reduce the gate drive losses and shorten the gate drive transition
period, leading to lower converter loss and improved efficiency.


###### 7.3.7 Comparing Performance Metrics of GaN Transistors and Si MOSFETs

There are many different resonant and soft-switching techniques, and therefore distilling a
single FOM for the wide variety of topologies into a simple metric is not practical. As discussed
earlier, for resonant and soft-switching applications, the output charge, QOSS, and gate charge,
QG, are the dominating device parameters. To allow designers to simply compare different
devices to determine the technology providing the best relative in-circuit performance for
resonant and soft-switching applications, a practical soft-switching FOM is:


FOMSS  (QOSS  QG) ? RDS on  (7.12)

The comparison of this soft-switching FOM for 40 V, 100 V, 200 V, and 600 V GaN and
Si MOSFETs is plotted in Figure 7.12. The GaN technology offers a significant FOM reduction
for all voltages, indicating significant performance improvements in high-frequency


-----

100

10


0.1

100


0.1


1 10 100 1000

**RDS(on) (mΩ)**

(b)


**Figure 7.11** Gate charge figure of merit comparison between GaN and Si devices

soft-switching applications. The benefits of replacing an Si MOSFET with an enhancementmode GaN transistor in a high-frequency resonant converter will be quantified next.


###### 7.4 High-Frequency Resonant Bus Converter Example

Distributed power systems are prevalent in telecommunications, networking, and high-end
server applications, and generally utilize a 48 V bus voltage adopted from the telecom industry.
The traditional distributed power architecture (DPA), shown in Figure 7.13(a), employs a


-----

300

30


3

0.3


300

30


3

0.3

1 10 100 1000

**RDS(on) (mΩ)**


**Figure 7.12** Soft-switching figure of merit comparison for GaN and Si devices

number of 48 V isolated hard-switching point-of-load (POL) converters to power the end loads.
However, having a large number of regulated and isolated POLs, significantly increases the
cost, volume, and complexity of the system. To simplify design and improve performance, the
intermediate bus architecture (IBA) has been widely adopted [12,13]. A popular IBA approach,
shown in Figure 7.13(b), employs a lower number of 48 V isolated bus converters that satisfy
isolation requirements and supply an intermediate 12 V bus voltage. With the final regulation to
the loads provided by smaller, more efficient, non-isolated POL buck converters, the bus
converters can be operated as unregulated DC/DC transformers, improving efficiency and
reducing cost.
The unregulated bus converter, also known as a DCX, or DC/DC transformer, can provide
the highest efficiency by being designed to deliver power close to 100% of the operating


-----

**Distributed Power Architecture (DPA)** **Intermediate Bus Architecture (IBA)**


AC input: 90 – 265 V


AC/DC
Front End

|AC/DC Front End|Col2|
|---|---|
|||

|AC/DC Front End|Col2|
|---|---|
|||

|AC/DC Front End|Col2|
|---|---|
|||

|AC/DC Front End|Col2|
|---|---|
|||

|8 V|Col2|Bu|Col4|
|---|---|---|---|
|Isolated DC/DC||Isolated DC/DC||
|||||

|Isolated DC/DC|Col2|
|---|---|
|||


1.2 V


AC input: 90 – 265 V

AC/DC AC/DC
Front End Front End

Bus


48 V


5 V


Bus

Isolated
DC/DC

3.3 V


48 V

12 V


(a) POL POL POL

|V|Col2|
|---|---|
|POL||
|||

|POL|Col2|
|---|---|
|||

|POL|Col2|
|---|---|
|||


5 V


3.3 V 1.2 V

(b)


**Figure 7.13** (a) Traditional distributed power architecture (b) Intermediate bus architecture

period, something not possible for a regulated converter that requires the converter to vary the
power-delivery period to provide a regulated output voltage for various input voltages. The
majority of today’s bus converters use traditional hard-switching bridge topologies, which, due
to large switching related losses, are forced to operate at lower frequencies where the bulky
isolation transformer and output inductors occupy a large portion of board area. In an effort to
improve power density and performance, the operating frequency can be increased through the
use of resonant and soft-switching converters [14–17], shrinking passive components, and
improving performance [18].
An experiment was undertaken to verify the superiority of enhancement-mode GaN
transistors over Si MOSFETs in this application. The subject design was a high-frequency
resonant converter, 48 V to 12 V unregulated isolated bus converter operating at a switching
frequency of 1.2 MHz, and an output power of up to 400 W. The topology, shown in
Figure 7.14, employs a soft-switching technique to achieve ZVS for the primary devices,


VGS(Q2,Q4)
VGS(S2)
VGS(Q1,Q3) D
VGS(S1)

IPRIM ILM

VDS(Q1) tZVS VIN

I Lk1

t0 t1 t2 t3


LK1


S1

S2


VIN

48 V

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||D||||
||||||
|LM|t ZVS||||
||||V IN||
||||||
||t t t 2t 0 1 3||||


**Figure 7.14** High-frequency resonant bus converter schematic and key waveforms


-----

and a resonant approach to achieve ZCS in the secondary devices as well as to limit the turn-off
current in the primary devices [14].
Referring to Figure 7.14, it can be seen that the leakage inductance (LK1) during the power
delivery period, t0–t1, resonates with a small output capacitance (CO). With proper timing, this
results in ZCS for the secondary-side device (S1), and significantly reduces turn-off current in
the primary-side devices (Q1, Q3). Since the topology is an unregulated bus converter, the
circuit can always operate at the optimal operating point (the resonant frequency), providing
the highest efficiency. The ZVS transition begins at the end of the power delivery period. For
t1–t2, the magnetizing current of the transformer is used to charge and discharge the output
capacitances of the devices, setting up a ZVS turn-on transition for devices Q2, Q4, and S2. If
the ZVS transition period is too long, the body diode of the devices Q2 and Q4 will turn on and
conduct current as seen in period t2–t3. At time t3, this operation is repeated for the other
switching leg with the current flowing through switches Q2, Q4, and S2, and leakage inductance
LK2, delivering power to the load while providing flux balancing in the transformer.

###### 7.4.1 Resonant GaN and Si Bus Converter Designs

To obtain a direct comparison in performance between GaN transistors and Si MOSFETs in an
isolated converter, having identical layouts and using the same topology are critical. Isolated
DC-DC converter performance is heavily dependent on topology selection, PCB layout,
number of PCB inner layers, copper weight of inner layers, and design of the transformer. To
accurately compare the performance of GaN and Si in a high-frequency resonant bus converter
application, the same circuit topology was used and a similar layout was maintained for both
designs.
Two bus converters, shown in Figure 7.15, were built based on the schematic in Figure 7.14,
to operate at a switching frequency of 1.2 MHz. Both PCBs were constructed with 12 layers
and two-ounce copper thickness for all layers. To accurately compare only device performance,
these converters both had the same transformer core material, core shape, and winding
arrangement, designed from [18]. The placement of the primary-side input capacitors and
secondary resonant capacitors were similar for the two designs to ensure similar parasitic
inductances for the primary and secondary loops, with the only differences being those

**Figure 7.15** 48 V to 12 V bus converters operating at a switching frequency of 1.2 MHz constructed
with (a) silicon MOSFETs (b) gallium nitride transistors


![](GaN-transistors-power-conversion.pdf-159-0.png)

-----

**Table 7.3** Device comparison between GaN and Si devices for primary devices for VIN = 48 V,
VOUT = 12 V

GaN transistor [10] Si MOSFET [19]

Voltage rating (VDSS) 100 V 80 V
RDS(on) 5.6 mΩ at 5 V 5.2 mΩ at 8 V[a]

QG 5.8 nC at 5 V 25.9 nC at 8 V[a]

QGD at VIN 2.2 nC 8.1 nC[a]

QOSS at VIN 35 nC 62 nC[a]

QG × RDS(on) 32.5 pCΩ 134.7 pCΩ 4.14 × reduction
QOSS × RDS(on) 196 pCΩ 322.4 pCΩ 1.64 × reduction
FOMSS (QOSS + QG) × RDS(on) 228.5 pCΩ 457.1 pCΩ 2.00 × reduction

_a Calculated from manufacturers datasheet curves._

introduced by the different packages of the Si MOSFETs and GaN transistors. It can be seen
that by using GaN transistors with smaller size for the same on-resistance the active footprint
area shrank significantly, reducing the power stage size by 30% compared to the Si MOSFET
design.

###### 7.4.2 GaN and Si Device Comparison

To obtain a direct comparison in performance between GaN transistors and Si MOSFETs in the
high-frequency resonant bus converter application, GaN and Si devices with similar onresistance were selected. Comparisons of the key parameters for the GaN transistors and
Si MOSFETs are shown in Tables 7.3 and 7.4 for the primary and secondary devices
respectively. The soft-switching FOM for the GaN devices ((QOSS + QG) × RDS(on)) is reduced
by over a factor of two for both the primary and secondary devices, leading to proportionally
shorter resonant transition periods and increased power delivery periods. The GaN transistor
provides additional performance improvements in the form of reduced Miller charge, QGD,
further reducing the turn-off switching losses incurred in the primary devices. As a further

**Table 7.4** Device comparison between GaN and Si for secondary devices for VIN = 48 V, VOUT = 12 V

Parameter GaN transistor [20] Si MOSFET [21] FOM ratio

Voltage rating (VDSS) 40 V 40 V
RDS(on) 3.2 mΩ at 5 V 2.9 mΩ at 5 V[a]

QG 8.3 nC at 5 V 27.5 nC at 5 V[a]

QGD at 20 V 2.2 nC 6.5 nC
QOSS at 20 V 18.5 nC 40 nC
QG × RDS(on) 26.6 pCΩ 79.8 pCΩ 3.00 × reduction
QOSS × RDS(on) 59.2 pCΩ 116 pGΩ 1.96 × reduction
FOMSS (QOSS + QG) 85.8 pCΩ 195.8 pCΩ 2.28 × reduction
× RDS(on)

_a Calculated from manufacturers’ datasheet curves._


-----

advantage, the LGA packaging of the GaN transistor has lower parasitic package inductance
compared to the traditional Si MOSFET package (TDSON-8). When putting all these benefits
together, efficient multi-MHz switching frequencies can be obtained through the use of
advanced topologies combined with low-loss GaN transistors.

###### 7.4.3 Zero-Voltage Switching Transition

The experimental waveforms for the ZVS transition period are shown in Figure 7.16 for the GaN
and Si designs. By replacing a Si MOSFET with a GaN transistor, the ZVS transition period is
reduced from 87 ns to 42 ns as a result of the reduced output charge enabled by GaN technology.
Looking at the gate waveforms, it can also be seen that the gate drive speed for the GaN transistor
is significantly faster than the Si MOSFET counterpart even when driven with a lower gate drive
voltage, providing both a longer power delivery period and reduced gate losses. The Si MOSFET
takes almost100 ns to reach its steady-state gate voltage; this is over 10 timeslongerthan the GaN
device, and reflects the gate charge reduction enabled by GaN technologies.
The power delivery period for a half cycle is shown in Figure 7.17 for the GaN- and Si-based
resonant bus converters. The effective duty cycles, D, which represent the power delivery
period for each half cycle for the GaN and Si designs, were measured to be 42% and 34%,
respectively. The soft-switching FOM from Equation 7.12 predicts the duty cycle gains,with a
50% reduction of the soft-switching FOM translating into a 50% reduction in the dead-time,
including the ZVS transition and gate charging periods.
As the power delivery periods increase in duration, the circulating energy and resonant
currents decrease, reducing the conduction losses in the resonant converter. For the resonant

**Figure 7.16** ZVS switching transitions for primary side GaN transistor and Si MOSFET designs at
fsw = 1.2 MHz, VIN = 48 V, and IOUT = 26 A


![](GaN-transistors-power-conversion.pdf-161-0.png)

-----

![](GaN-transistors-power-conversion.pdf-162-0.png)

**Figure 7.17** Switching waveforms showing effective duty cycle for primary side GaN transistor and
Si MOSFET designs at fsw = 1.2 MHz, VIN = 48 V, and IOUT = 26 A

converter used in this design, the conduction losses, related to the resonant converters RMS
current, IRES, are inversely proportional to effective duty cycle, D, by:


IRES ∝


1
pffiffiffiffi (7.13)
_D_


For this design example, the increased duty cycle provided by GaN devices can reduce the
conduction losses in the devices, transformer, PCB, and components by almost 20%.

###### 7.4.4 Efficiency and Power Loss Comparison

The comparison in efficiency and power loss between the two designs operating at 1.2 MHz are
shown in Figure 7.18. The GaN transistor-based converter offers a 1% improvement in peak
efficiency over its Si MOSFET counterpart, resulting in about a 25% decrease in power loss.
Since it is typical for bus converter designs to be thermally limited by losses under full load for
a fixed converter size, the reduction in power loss translates directly into higher output power
handling capability. For a design capable of dissipating 14 W, the GaN transistor converter can
increase the output power capability by up to 65 W while maintaining the same total converter
loss when compared to the benchmark Si MOSFET design. Assuming a 12 W maximum power
loss for both designs, the output power of the GaN transistor based converter increases by
55 W, from 270 W to 325 W.
The loss breakdown for the 1.2 MHz designs at output currents of 2.5 A and 20 A is shown in
Figure 7.19, which leads to the conclusion that the GaN technology improves efficiency for all


-----

98

1.2 MHz GaN Transistor 10 W

97 12 W 14 W

96

95

1.2 MHz MOSFET

94

93

92

91

90

0 5 10 15 20 25 30 35 40


24
22
20

1.2 MHz MOSFET

18
16
14
12
10
8

1.2 MHz GaN Transistor

6
4
2

0 5 10 15 20 25 30 35 40


**Output Current (A)**

**Figure 7.18** Experimental comparison between a GaN transistor and an Si MOSFET-based resonant bus
converters (VIN = 48 V, VOUT = 12 V, fsw = 1.2 MHz)


12

10


8

6


4

2


0

|Gate Drive|Col2|
|---|---|
|Transfomer Core Conduction +||
|Turn Off||
|||
|||
|||


GaN
Transistor
2.5 A


MOSFET GaN
2.5 A Transistor
20 A


MOSFET
20 A


**Figure 7.19** Loss breakdown of a GaN transistor and Si MOSFET-based resonant bus converter
(VIN = 48 V, VOUT = 12 V, fsw = 1.2 MHz)


-----

load conditions. At lower currents, the gate driving losses dominate the transistor-related
losses, and the GaN device’s lower gate charge enables substantially reduced drive loss. At
high currents, the conduction loss dominates total power loss, and the GaN-based converter’s
shorter ZVS dead-time and gate charging time provides lower conduction losses proportional
to the effective duty cycle. The one area where the Si-based design offers lower loss is in the
transformer core. The longer power delivery period provided by the GaN-based design
increases the transformer flux density, leading to higher core loss, but the increase in
transformer core loss is more than offset at lower currents by the gate drive loss savings,
and at high currents by the combination of conduction and gate loss savings.
From the results at 1.2 MHz, it can be seen that the Si MOSFET converter is approaching its
frequency limit because the ZVS transition time and gate charging time are becoming a
significant portion of the overall period. To compare the frequency improvements possible
with GaN transistors over Si MOSFETs, the converter frequency was reduced to 800 kHz for
the Si MOSFET design, while increasing the eGaN transistor design to 1.6 MHz. In both cases,
the core structure remained the same and was not optimized for the different operating
frequencies. The efficiency and loss comparisons between the designs are shown in Figure 7.20,

98

1.6 MHz GaN Transistor 10 W

97 12 W 14 W

96

95

0.8 MHz MOSFET

94

93

92

91


90

0 5 10 15 20 25 30 35 40

**Output Current (A)**

24
22
20
18
16
14
12

0.8 MHz MOSFET

10
8

1.6 MHz GaN Transistor

6
4
2

0 5 10 15 20 25 30 35 40


**Output Current (A)**

**Figure 7.20** Comparison between fSW = 1.6 MHz GaN transistor and fsw = 800 kHz Si MOSFET-based
VIN = 48 V, VOUT = 12 V resonant bus converter


-----

with the GaN transistor-based design offering a 0.9% peak efficiency improvement and less
power loss up to an output current of 29 A. The sharp drop-off in efficiency at currents above
20 A for the GaN transistor-based converter is a result of increased AC transformer winding
losses, and an effective duty cycle reduction. Conversely, the flattening out of the efficiency for
the 800 kHz Si MOSFET design was a result of reduced AC transformer winding losses and a
higher effective duty cycle at the lower frequency.

###### 7.5 Summary

It was shown in previous chapters that enhancement-mode GaN transistors have a distinct
advantage over silicon MOSFETs in hard-switching applications due to reduced QGD and
QGS2, both of which are critical in hard-switching applications, but have little impact in
resonant and soft-switching converters. In this chapter, the benefits of GaN technology as
applied to resonant and soft-switching applications have been discussed, and the in-circuit
superiority of GaN transistors demonstrated in a 48 V bus converter operating at 1.2 MHz. This
chapter also discussed a simple soft-switching FOM that allows designers to quickly compare
device technologies for use in resonant and soft-switching applications. The soft-switching
FOM is made up of the two parameters most critical for resonant and soft-switching
applications: output charge, QOSS, and gate charge, QG.
In the next chapter we will explore the performance of GaN transistors designed for power
conversion at RF frequencies.

###### References

1. Lee, F.C. (1989) High-Frequency Resonant, Quasi-Resonant, and Multi-Resonant Converters, Virginia Power
Electronics Center, Blacksburg, VA.
2. Lee, F.C. (1989) High-Frequency Resonant and Soft-Switching PWM Converters, Virginia Power Electronics
Center, Blacksburg, VA.
3. Erickson, R.W. and Maksimovic, D. (2001)́ _Fundamental of Power Electronics, Kluwer, Norwell, MA._
4. Kazimierczuk, M.K. and Czarkowski, D. (2011) Resonant Power Converters, John Wiley & Sons, NJ.
5. Yang, B. (2003) Topology investigation for front end DC/DC power conversion for distributed power system,
Ph.D. dissertation, Virginia Tech, Blacksburg, VA.
6. Vorperian, V. (1984) Analysis of resonant converters, Ph.D. dissertation, California Inst. Technol., Pasadena, CA.
7. Severns, R.P. (1992) Topologies for three-element resonant converters. IEEE Transactions, Power Electron, 7 (1),
89–98.
8. Fu, D. (2010) Topology investigation and system optimization of resonant converters, Ph.D. dissertation, Virginia
Polytechnic Inst. State Univ., Blacksburg, VA.
9. Liu, K.H. and Lee, F.C. (Nov. 1984) Resonant Switches – a Unified Approach to Improved Performances of
Switching Converters, IEEE International Telecommunications Energy Conference, pp. 334–341.
10. Efficient Power Conversion Corporation, EPC2001 – Enhancement-mode Power Transistor, EPC2001 datasheet,
[March 2011 [Revised Jan. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2001_data-](http://epc-co.com/epc/documents/datasheets/EPC2001_datasheet.pdf)
[sheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2001_datasheet.pdf)
11. Infineon (21 Oct. 2009) OptiMOS[TM] Power-Transistor, BSC060N10NS3 G datasheet.
12. Schlecht, M. (11 Sep. 2007) “High Efficiency Power Converter,” U.S. Patent 7,269,034.
13. White, R.V. (9–13 Feb. 2003) “Emerging on-Board power architectures,” Applied Power Electronics Conference
and Exposition (APEC) 2003, Eighteenth Annual IEEE, Miami Beach, FL, vol. 2, pp. 799–804.
14. Ren, Y., Xu, M., Sun, J. and Lee, F.C. (2005) A family of high power density unregulated bus converters. IEEE
_Transactions, Power Electron, 20 (5), 1045–1054._
15. Ren, Y. (April 2005) High frequency, high efficiency two-stage approach for future microprocessors, Ph.D.
Dissertation, Virginia Tech, Blacksburg, VA.


-----

16. Ren, Y., Lee, F.C. and Xu, M. (27 March 2007) Power Converters Having Capacitor Resonant With Transformer
Leakage Inductance, U.S. Patent 7,196,914.
17. Vinciarelli, P. (5 Dec. 2006) Point of load sine amplitude converters and methods, U.S. Patent 7,145,786.
18. Reusch, D. (2012) High frequency, high power density integrated point of load and bus converters, Ph.D.
Dissertation, Virginia Polytechnic Inst. State Univ., VA.
19. Infineon (22 Oct. 2009) OptiMOS[TM]3 Power-Transistor, BSC057N08NS3G datasheet.
20. Efficient Power Conversion Corporation, EPC2015 – Enhancement-mode Power Transistor, EPC2015 datasheet,
[March 2011 [Revised Jan. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2015_data-](http://epc-co.com/epc/documents/datasheets/EPC2015_datasheet.pdf)
[sheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2015_datasheet.pdf)
21. Infineon (22 Oct. 2009) OptiMOS[TM]3 Power-Transistor, BSCO27N04LSG datasheet.


-----

# 8

#### RF Performance

###### 8.1 Introd uction

Th e m ain focus to this po int i n t he book has been the switching cap abilitie s of G aN tran si stors. Now,
the R F c apab ilities o f t hese same GaN t ransistors and, in particu la r, en hance ment-mode transistors
will be ex am ined, high lig hting spec ific R F app li c ations that can ben efit fr om t he ir a doption.
High electron mobili ty transist ors (HEM T), using GaN as a semi conductor material, are
available from Cr ee, Nitron ex, NX P, Integ ra, RFM D, and TriQ uint, among others. These
transist ors are all depletion- mode, whi ch is not as limiting for RF powe r ampl ifiers as it is for
switch ing con verters. This is becau se the potent ial of device failure upon powe r up, due to the
short con dition, can be mitiga ted easily in the RF design, which is not the case for a swi tching
convert er. Depl etion-mo de transistors requi re additional circu itry for gate circuit biasing, due
to the negati ve gate voltage requireme nts to regul ate the drain current, which is also viewed as a
disadv antage in cases where enhancem ent-mode devices are an option .
The main alternative today for GaN RF trans istors operat ing in the range of 500 MH z to
3 GHz is the laterall y diff used meta l oxide semiconduc tor (L DMOS) FET made using silicon.
Compar ed to LDMOS transistors, GaN is well-s uited for RF transistors for many of the same
reason s as for switch ing appli cations [1 –3]. GaN transistors exhibit superi or RF performanc e
over LDMO S in general, most notably with respec t to powe r den sity [4], frequency range
(bandwid th) [1,5], and noise figure. This leads to improvem ents in RF power capabi lity [2,6]
with trans istors being speci fied over a very wide freque ncy range [7]. In addit ion, the lower
input and output capacitances lead to higher impedance s that allow for higher drain effi ciencies
and reduced impedan ce trans formation ratios required for matching. Both these facto rs lead to
improvem ents in ampl ifier efficiency, size reduction, and ultima tely cost.
When used in pulsed-R F applicati ons, the bias circu it will also need to be operat ional before
main powe r and RF are applied, to prevent starting wi th very high curren ts that can potent ially
damag e the circu it. Therefor e, RF circuits can be nefit from using enhan cement-m ode
transist ors for many of the same reasons as in switching converters.
The measurement and performance metrics used for RF transistors differ significantly from
switching devices. These metrics will be presented, along with their relevance, and guidance on
how to measure and use them.

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

**Table 8.1** Definitions of terms used in RF analysis and design

VGSQ RF circuit gate voltage quiescent bias point
IDQ Drain current in the transistor at the quiescent operating point
PDQ Power losses at the quiescent operating point
PDC DC power delivered to the RF transistor
PRFout Output RF power
ηD Drain efficiency – the ratio of PRFou/PDC
s11 Input port reflection coefficient: the percentage of the input incident wave that is reflected back
from the input port
s12 Reverse gain: the percentage of the output port incident wave that is reflected to the input port
s21 Forward gain: the percentage of the input port incident wave that is reflected to the output port
s22 Output port reflection coefficient: the percentage of the output incident wave that is reflected
back from the output port
K Rollett stability factor
CS The source-side stability circle center on a Smith chart
CL The load-side stability circle center on a Smith chart
CA Constant available gain circle center on a Smith chart
RS The source-side stability circle radius on a Smith chart
RL The load-side stability circle radius on a Smith chart
RA The radius of the constant available gain circle on a Smith chart
Γin Input reflection coefficient of the transistor
Γout Output reflection coefficient of the transistor
ΓS Input-side matching reflection coefficient
ΓL Output-side matching reflection coefficient
GT Transducer power gain
GTU Unilateral transducer power gain
U Unilateral figure of merit
gu Normalized unilateral transducer gain
GA Available gain
GMSG Maximum stable gain of the transistor
X Matching network series reactance
B Matching network shunt susceptance

###### 8.2 Differences Between RF and Switching Transistors

The main difference between switching transistors and RF transistors is that RF transistors are
designed to work best in the linear region of the transfer characteristic to maximize RF power
gain and minimize RF signal distortion. Switching devices are designed to work best in the onstate and transition states to minimize losses [8–14]. For performance comparison, RF devices
have different evaluation metrics [1] from switching devices, among which are power gain,
linearity or 1 dB compression [8], and drain efficiency. The power gain determines how much
the transistor amplifies the input signal with power. The 1 dB compression point determines the
maximum output power that the transistor can deliver without distorting the signal. The drain
efficiency determines how efficient the transistor is at amplifying.


-----

IDS


Output Signal Current

Transfer Characteristic

Bias IDQ
Point

VGS

Input Signal Voltage

VGSQ

**Figure 8.1** Transfer characteristic for an enhancement-mode transistor showing the bias point and input
voltage signal with corresponding output current

Typically, RF devices are biased to an operating point onto which the RF signal is superimposed. To bias the transistor, a drain-to-source current is established such that the voltage
remains at the supply voltage. Figure 8.1 illustrates this concept, using the transistor transfer
characteristic. The bias voltage and current are named quiescent points and denoted as VGSQ and
IDQ respectively, and typically are provided in datasheets for baseline performance reporting.
The bias point will be associated with losses (PDQ = IDQVSupply), and as such, RF devices
have a higher operating power (PDQ) loss ratio with respect to power delivered (PRFout),
compared to switching devices. The ratio PRFout/PDC is referred to as drain efficiency (ηD)
where PRFout is the output RF power and PDC is the DC power delivered to the transistor. When
employing an RF FET as a Class A amplifier, this power loss ratio reaches a theoretical
maximum of 50%, but as discussed in earlier chapters, a switching converter can have
efficiencies as high as 98%. This means that the thermal dissipation of an RF device is
significantly higher than equivalently sized switching devices, and necessitates that RF
transistors have the ability to efficiently dissipate heat to the environment. Figure 8.2 shows
the difference between a packaged RF FET (left) and a chip-scale switching FET (right), both
with similar drain voltage and current ratings.
Another key difference between RF devices and switching devices is in how they are
characterized. RF transistors are characterized as part of a transmission line in terms of incident
and reflected waves, whereas switching devices are characterized in terms of energy commutation. This opens up many new terms and definitions unfamiliar to many power circuit
designers. The common metric used to characterize RF devices are the s-parameters, which
represent a measure of incident, reflection, and transmission of electromagnetic waves.
S-parameters will also be used in this chapter to characterize the enhancement-mode GaN
transistor originally designed for switching converter applications.

|Output Signal Curr Transfer Characteristic Bias Point|Col2|Col3|Col4|
|---|---|---|---|
|||||
|||||
|||V GS Input Signal Voltage||


-----

(a)

**Figure 8.2** (a) An RF-packaged FET [15] and (b) the equivalent chip-scale switching FET [19], with
similar voltage and current rating

###### 8.3 RF Basics

Before delving into RF transistor measurement and analysis, some basics need to be reviewed.
In this chapter, all discussions will be limited to two-port networks, as this is sufficient to
describe a transistor. Figure 8.3 shows the basic diagram for a two-port network showing the
incident waves, denoted a1 and a2, and reflected waves denoted b1 and b2. Any incident wave at
a port can be reflected to either of the ports. For example, an incident wave on port 1 (a1) can
reflect from port 1 (b1) and/or port 2 (b2).
An s-parameter is defined as the ratio between reflected (b1 and b2) and incident (a1 and a2)
waves and is given by Equation 8.1.

snm  a[b]m[n] (8.1)

And snm is a complex number with the general form:

snm  Re(snm)  i ? J m s nm (8.2)

In this chapter, port 1 will be designated as the input port, or gate, and port 2 as the output
port, or drain.
From the s-parameters, it is possible to derive useful characteristics of the two-port network
such as impedance, gain, and isolation. (The methodology is described in detail in [8].)


![](GaN-transistors-power-conversion.pdf-170-0.png)

Chip-Scale
Switching FET

(b)

Packaged RF FET


a1

b1


a2

b2

|Col1|Two-Port Network|Col3|
|---|---|---|


**Figure 8.3** Two-port network with (a) incident waves and (b) reflected waves


-----

ZS I1 I2

+

+ +

Two-Port

VS ZIN V1 Network V2

– –

–

**Figure 8.4** A two-port network with source and load


+

–

|Z S + + Z V IN 1 – –|Two-Port Network|+ V Z 2 O UT –|
|---|---|---|


Figure 8.4 shows the two-port network connected to a load and source, and gives the input and
output impedance for those ports.
The Smith chart is a useful tool [8], which simplifies the conversion of s-parameters into
impedances, and will be extensively used in this chapter.

###### 8.4 RF Transistor Metrics

The main metric for RF transistor performance evaluation is RF power gain. Maximum power
gain is defined by the limit of linear performance for a transistor. Table 8.2 shows data from the
Nitronex NPT1012 datasheet [7] showing the key RF metrics for the depletion-mode GaN-onsilicon HEMT under certain operating conditions.
RF power gain is a measure of how much power is increased or decreased by when incident
on a port. Mathematically it is expressed as:

G [P][out] (8.3)

Pin

Gain can also be expressed logarithmically, with units of decibel (dB) as follows:

� �

G dB 10 ? log [P][out] (8.4)
  
Pin

**Table 8.2** Data from Nitronex NPT1012 datasheet [7] showing the Key RF metrics for the transistor

Operating
Conditions

VDS = 28V, IDQ = 225mA, TC = 25°C, Measured in Nitronex Test Fixture

**Symbol** **Parameter** **Min** **Typ** **Max** **Units**

P3dB Average Output Power at 3 dB Gain Compression 43 44   - dBm

P1dB Average Output Power at 1 dB Gain Compression   - 43   - dBm

GSS Small Signal Gain 12 13   - dB

η 57 65    - %

VSWR 10:1 VSWR at all phase angles No damage to the device

Key Metric

|Symbol|Parameter|Min|Typ|Max|Units|
|---|---|---|---|---|---|
|P3dB|Average Output Power at 3 dB Gain Compression|43|44|-|dBm|
|P1dB|Average Output Power at 1 dB Gain Compression|-|43|-|dBm|
|GSS|Small Signal Gain|12|13|-|dB|
|η||57|65|-|%|
|VSWR|10:1 VSWR at all phase angles|No damage to the device||||
|||||||


-----

Ideal Response

POUT (dBm) Gain (dB)

X
Y
X-1

Measured Measured
Output Gain

Y-1

1 dB
Compression
Point (P1 dB)

1 dB
Compression
Point (P1 dB)

PIN (dBm) PIN (dBm)

(a) (b)

**Figure 8.5** Graphical representation of the definition of linearity based on (a) the 1 dB compression
point and (b), linearity on the gain graph

Using the definition of gain, linearity can be defined for the amplifier as having a fixed gain
value and is characterized by the linear relationship between the input power and the output
power.At its limit,thereisalossingainduetoamplificationsaturation.Linearityisalsoknownas
linear dynamic range with its limit being the 1 dB compression point [8]. For an RF transistor, the
gain will be a constant as a function of input power until it exceeds a specific value. The 1 dB
compression point is defined as the point when the measured amplifier output power (dB)
deviates by 1 dB from the ideal predicted power, and is shown in Figure 8.5. Figure 8.5(a) is the
output power as a function of the input power, and Figure 8.5(b) shows the same result for gain as
a function of input power. Above a specific input power level, the gain will begin to decrease and
the output power will no longer be a linear function of the input power.
Typically, the linearity of a transistor is provided in a datasheet at a specific frequency and
bias condition. Power gain is given over a frequency range, based on a specific bias setting.
Small-signal s-parameters can be used to design a Class A RF power amplifier, but large-signal
s-parameters are needed to predict power performance.

###### 8.4.1 Determining the High-Frequency Characteristics of RF FETs

To determine the RF characteristics of a transistor requires a few steps. The procedure starts
with s-parameter measurements of the device itself. The s-parameters are used to test for
stability and to identify if the device is unilateral (negligible reverse gain) or bilateral (reverse
gain is high enough to affect stability). Once the stability criteria have been determined, an
amplifier can be designed, typically a Class A or Class AB.
Small-signal s-parameters are measured using a vector network analyzer (VNA) with the
transistor under specific bias conditions. Several measurements may be required to determine
the bias conditions that yield the highest performance metrics.
To measure the RF characteristics requires that the device be mounted to a test fixture.
The test fixture will need to be calibrated using a set of standards to obtain the device-only
s-parameters. The thru-reflect-line (TRL) [16] and short-open-load-thru (SOLT) methods are
the most popular methods of calibration. The calibration process and accuracy between the two
methods is well documented in [17,18].


-----

914 355
All Dimensions in µm

914

Device Outline

149

Gate Circuit Drain Circuit
Reference Plane e Plane Reference Plane

**Figure 8.6** Reference plane design for RF connection to the EPC8009 [19] FET

Figure 8.6 shows a reference plane design suitable for the EPC8009 [19] enhancement-mode
switching FET that can be used to test its RF characteristics. Due to the small size of this device
and its connections, a reducing taper microstrip is required to make the connection. The taper’s
interface to the 50 Ω microstrip transmission line in this example is based on a 30 mil thick,
one-once copper, Rogers 4350 substrate [20].

###### 8.4.2 Pulse Testing for Thermal Considerations

It has already been mentioned that RF devices have a high ratio of power dissipation to power
output, and therefore require substantial cooling. In the case where power dissipation exceeds
the capability of the device, pulsed-mode testing can be employed.
Most RF amplifiers are operated with a continuous RF signal and bias. This is known as
continuous wave (CW) operation. Pulse testing is used to lower the average power dissipation
in the device. The bias pulse and pulsed RF signal used in pulse testing are shown in Figure 8.7.
It is important to maintain the drain bias current stable during the on-state of the pulse as
changes can cause inaccurate measurements. This is difficult to achieve, particularly for
Class A amplifiers, as the drain current will increase in response to an increase in RF power
without any means to differentiate between what is the bias component and what is the RF

tPulse

Bias Pulse

Pulsed RF

Time

**Figure 8.7** Bias pulse and pulsed RF signal for pulsed RF testing

|Col1|Col2|Bias Pulse|
|---|---|---|


-----

Bias

To VNA

Tee

Chnl 1

D.U.T

RF Fixture Board

**Figure 8.8** Schematic block diagram for transistor bias control under pulsed RF testing

component. In addition, rapid changes in gate voltage can lead to unwanted ringing of the drain
and can cause bias instability and oscillations. The choice of bias tees for pulse testing is also
critical because the frequency response of the bias tees must satisfy both RF and bias
requirements.
A dedicated pulse controller similar to the schematic block diagram shown in Figure 8.8 can
be used for RF testing FETs. Using an isolation amplifier, the drain current is measured and
used with a proportional-integral (PI) controller to regulate the gate voltage to maintain the
drain current. The PI controller is also controlled by the gate pulse to avoid rapid gate
transitions.
For higher power RF measurements, the pulse controller can be adapted such that gate
voltage can be fed to a second device while the drain bias current for the second device is not
measured by the controller [21]. The first device will not be exposed to RF thereby providing a
stable reference for the device under RF testing. This setup is shown in Figure 8.9.


PI
Controller


To Drain
Bias Supply

Control FET
Drain
Current

To Drain
Bias Control
Circuit


To Drain
Bias DUT
Circuit


To Gate Bias
DUT Circuit

To Gate Bias
Control
Circuit


**Figure 8.9** Power RF testing using the pulse controller having a reference device and a device under test


-----

###### 8.4.3 Analyzing the S-Parameters

With the ability to measure the s-parameters, the data now needs to be analyzed so that an
amplifier can be designed from it. The procedure involves checking for stability issues and
determining the input and output reflection coefficients for the device.

**8.4.3.1** **Test for Stability**

It is important to determine whether the device is conditionally or unconditionally stable. An
unconditionally stable device will remain stable (will not oscillate) regardless of the impedance
presented to its gate or drain. The test for unconditional stability is given by the Rollett stability
factor (K) [22]:


and

where


K [1][ �] j[s][11]j2 � js22j2  Δj j2 1 (8.5)
 

2 ? s12 ? s21
j j

Δ (8.6)
j j [][ 1]

Δ  s11 ? s22 � s12 ? s21 (8.7)


If this stability criterion for either K or |Δ| cannot be satisfied, then the transistor will be
defined as conditionally stable. This means that any design using the transistor must avoid the
unstable region. Stability circle plots on a Smith chart [8] are used to determine where the
unstable regions are located. The stability circles are given by the following equations:

� �*
CS  [s][11]js11[ �]j2 �[Δ][ ?]j j[ s]Δ[ *]222 (8.8)

s12 ? s21
RS  js11j j2 � j jΔj 2 (8.9)


� �*
11
CL  [s][22]js22[ �]j2 �[Δ][ ?]j j[ s]Δ[ *]2 (8.10)

s12 ? s21
RL  js22j j2 � j jΔj 2 (8.11)

The superscript asterisk (*) denotes the complex conjugate of the parameter, also known as the
reflection of the parameter. Using Equation 8.2 as an example, the complex conjugate for snm is
given as:

snm[*]  Re(snm) � i ? J m s nm (8.12)


-----

Unstable
Region


Load Stability Circle

Source Stability Circle


**Figure 8.10** Stability circle plot showing unstable regions for both source and load ports

The unstable region falls inside the stability circle, as shown for example in Figure 8.10 (for a
tutorial on the use of Smith Charts see reference [8]).

**8.4.3.2** **Transistor Input and Output Reflection**

The RF transistor will ultimately be placed in an amplifier circuit with input and output
matching networks that transform the standard source impedance (Z0) and standard load
impedance (Z0) to desired values (ΓS and ΓL), as shown in Figure 8.11. Matching networks will
be discussed in detail later in this chapter.
Although they share the same nomenclature, the transistor input and output reflection
coefficients are not simply given by s11 and s22 (reflection coefficients) as one might expect, but
are given by Γin and Γout for the input (gate circuit) and output (drain circuit) respectively. This

Z0

Input Output
Matching Matching Z0

GS G0 GL

ΓS ΓIN ΓOUT ΓL

**Figure 8.11** Basic amplifier structure with input and output matching with reflection coefficients for the
FET and matching networks

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||Input Matching||||Output Matching||
||G S||G 0||G L||

|Col1|G 0|Col3|
|---|---|---|


-----

is due to the effect of the transmission coefficients s12 and s21 cross influencing the input and
output by way of the load and source impedances. This can be seen in the equations for the
transistor input and output reflection [8], where the load network impacts the input reflection,
and the source network impacts the output reflection:

Γin  s11  [s]1[12] �[ ?][ s]s22[21] ?[ ?] Γ[ Γ]L[L] (8.13)

Γout  s22  [s]1[12] �[ ?][ s]s11[21] ?[ ?] Γ[ Γ]S[S] (8.14)


**8.4.3.3** **Transducer Gain**

Transducer power gain (GT) is defined as the ratio of power delivered to the load to the power
available from the source. From Figure 8.11, it can be seen that there are multiple gain
components which are: gain of the source side matching GS, gain of the transistor G0, and gain
of the load side matching GL. Together, these components make up the transducer gain (GT),
which can be determined using the following equations:

GT  GS ? G0 ? GL (8.15)


and written using s-parameters:


GS  j1 �1 �ΓinjΓ ?S Γj2Sj2 (8.16)


G0  sj 21j2 (8.17)

GL  j1 �1 �ΓoutjΓ ?L Γj2 Lj2 (8.18)

**8.4.3.4** **Unilateral/Bilateral Transistor Test**

A unilateral transistor is defined as one where s12 is very small relative to s21 [8,23]. Since a
value of zero for s12 is not physically possible, we can perform a test to determine if a transistor
can be regarded as unilateral or bilateral. Using Equations 8.16 and 8.18 and substituting Γin
and Γout with s11 and s22 respectively, a unilateral transducer gain (GTU) for Equation 8.15 can
be derived. The ratio of the transducer gain to the unilateral transducer gain can be used to
determine the normalized unilateral transducer gain as follows:

gu  G[G]TU[T] (8.19)

which is bounded as follows:

1 1
(8.20)
1 U 1 U
  [2][ <][ g][u][ <] � [2]


-----

where U is the unilateral figure of merit and given by the following equation:

s11 [?][ s]12 [?][ s]21 [?][ s]22
U  �1j � jjs11j j2�j ? 1j� �j jjs22jj2� (8.21)

A transistor can be regarded as unilateral if gu is within 10% of unity, otherwise it is considered
bilateral. Also, a unilateral transistor will always be stable by definition, as the device
effectively does not have a feedback mechanism. A unilateral amplifier design is simplified
greatly as Γin and Γout (Equations 8.13 and 8.14) can be reduced to s11 and s22, respectively. The
unilateral solution will not be covered in this book, as the procedure to design an amplifier
using a bilateral transistor also can be adapted for a unilateral transistor.

###### 8.5 Amplifier Design Using Small-Signal S-Parameters

The essence of an amplifier design is to determine the input (ΓS) and output (ΓL) reflection
coefficients for the matching networks of the transistor. The basis for the design can be
maximum gain, or a specific gain that is within the capability of the transistor.
The example here assumes a bilateral transistor, and the procedure followed will be based on
a specific gain requirement. The unique solution for an unconditionally stable transistor that
yields the maximum transducer gain (GTmax) can also be determined using this procedure. The
specific maximum transducer gain needs to be determined to know its gain limit. For an
unconditionally stable transistor, the maximum transducer gain is given by:

� pffiffiffiffiffiffiffiffiffiffiffiffiffiffi�
GTmax  jj[s]s[21]12jj ? K � K[2] � 1 (8.22)

The unconditionally stable transistor maximum transducer gain amplifier solution is
defined as a conjugately matched amplifier, where the matching networks are designed to
have zero reflection. It will be the complex conjugate of the transistor ports and can be
written in the form:

Γin  Γ[*]S (8.23)

Γout  Γ[*]L (8.24)

###### 8.5.1 Conditionally Stable Bilateral Transistor Amplifier Design

The design of an amplifier using a conditionally stable bilateral transistor can involve plotting
many gain circles to find an acceptable solution. In this section, we will present a simpler
method based on conjugately matching one port of the transistor, and mismatching the other
port. The solution can then be adjusted to find a solution where both input (ΓS) and output (ΓL)
reflection coefficients fall within the stable operating regions. The design procedure will make
use of constant gain circles where an arbitrary gain value and reflection coefficient for that port
are chosen, and the equations solved to find the other port’s reflection coefficient. Amplifier
design using feedback networks will not be covered.


-----

**8.5.1.1** **Available Gain**

The amplifier will be designed using the available gain (GA) approach [11], so that the output
network will be conjugately matched with the transistor and the input network mismatched
with the transistor. The approach will reduce the amount of reflected power being transmitted
back to the input via s12 due to any output mismatch. A mismatch on the input results in a
significantly lower reflection magnitude than it would if the output were mismatched.
Available gain (GA) is defined as the ratio of the power available from the amplifier to the
power available from the source. Substituting Equation 8.24 into Equation 8.18, Equation 8.13
into 8.16, and solving for Equation 8.15 under these conditions yields:

GA  j1 �1 �s11jΓ ?S Γj2Sj2 [?][ s]j [21]j2 ? 1 � j1Γoutj2 (8.25)

where the unknown is ΓS, which will be chosen based on a specific gain requirement for the
amplifier. The output will be conjugately matched using the constant available gain circle, GA.
The normalized available power gain (gA) is given by:

gA  js[G]21[A]j2 (8.26)

**8.5.1.2** **Constant Available Gain Circles**

Using the available gain, constant available gain circles can be derived [11] and are
summarized as follows:


RA 


� �*
22
CA  1[g] [A][ ?] g[ s]A ?[11] s�[ �]j 11[Δ]j2[ ?] �[ s][ *]j jΔ 2� (8.27)

qffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi1 � 2 ? K ? sj 12 ? s21j [?][ g]A [][ s]j 12 [?][ s]21j2 ? g2A

1  gA ? s�j 11j2 � j jΔ 2� (8.28)


A specific available gain is chosen and the gain circle is plotted. The gain circle gives all
possible values for the input reflection coefficient (ΓS) that will yield this gain. For each value
of (ΓS), a value for (ΓL) can be determined, and a circle of (ΓL) can be calculated using
Equations 8.14 and 8.24. A range of values where both (ΓS) and (ΓL) fall outside their
respective stability circles, and that also lie inside the unity circle of the Smith chart, will yield a
stable amplifier design. The best choice would be based on values that lie furthest from the
stability circles.

###### 8.6 Amplifier Design Example

Next, an amplifier will be designed using an enhancement-mode GaN transistor [19], and the
available gain approach. In this example, the s-parameters have been measured using the
reference planes shown in Figure 8.6 and will operate at 500 MHz.


-----

At 500 MHz, VDSQ = 30 V and IDQ = 500 mA, the enhancement-mode GaN transistor
(EPC8009 [19]) has the following s-parameter values:

s11  �0.926 �i ? 0.157, js11j  0.939
s22  �0.658 �i ? 0.46, js22j  0.803
s12  �0.002 i ? 0.013, js12j  0.013
s21  5.280 i ? 4.042, js21j  6.65

From the s-parameters, it can be determined whether the transistor is unilateral or bilateral
using Equations 8.20 and 8.21.

s11 [?][ s]12 [?][ s]21 [?][ s]22
U  �1j � jjs11j j2�j ? 1j� �j jjs22jj2�



[0.926][ ?][ 0.013][ ?][ 6.65][ ?][ 0.803]
 �1 0.926[2]� ? 1� 0.803[2]�
� �

1.534


and
1 1
1 U 1 U
  [2][ <][ g][u][ <] � [2]

1 1
1 1.534 1 1.534
  [2][ <][ g][u][ <] � [2]

0.156 < gu < 3.5


(8.29)

(8.30)


From the result, it is clear that neither unilateral FOM boundary is within 10% of unity, and
therefore, the transistor is considered bilateral.
Next, we need to decide whether the transistor is conditionally or unconditionally stable
using Equations 8.5–8.7.

Δ  s11 ? s22 � s12 ? s21
0.926 i ? 0.157 ? 0.658 i ? 0.46 0.002 i ? 0.013 ? 5.280 i ? 4.042 (8.31)
 � �  � �  ��    
0.6 i ? 0.472
 � 

and
Δ (8.32)
j j [][ 0.763]

with the Rollett stability factor


K [1][ �] j[s][11]j2 � js22j2  Δj j2


2 ? s12 ? s21
j j

1 0.939[2] 0.803[2] 0.763[2]
� � 


2 ? 0.002 i ? 0.013 ? 5.280 i ? 4.042
�j    j
0.326



(8.33)


-----

Unstable
Region Load
Stability
Circle


Source
Stability
Circle


ΓL ΓL Trajectory
Based on GA

ΓS

50 Ω
GA Circle


**Figure 8.12** Stability circles for EPC8009 [19] at 500 MHz with VDSQ = 30 V and IDQ = 500 mA
together with the available gain circle of 23 dB and load reflection coefficient ΓL trajectory

The unconditional stability of K  1 and |Δ|  1 has not been met for this transistor due to K.
Therefore, the device is conditionally stable and the stability circles can be plotted to determine
the unstable regions.
The stability circles can be calculated using Equations 8.8–8.11, and are shown in
Figure 8.12 with the unstable regions shaded. The amplifier design for (ΓS) and (ΓL) need
to avoid these regions. As the transistor is conditionally stable, we need to determine a suitable
gain that will yield an amplifier that will not oscillate (is always stable). Before we can select a
working gain we need to determine the maximum stable gain of the transistor using the
following equation:


GMSG  jj[s]s[21]12jj

[6.65]

0.013
520.3 27.2 dB
 


(8.34)


The maximum stable gain is a simple method to determine the stable gain limit of the transistor;
however, it may not yield a workable solution. For this example, a design gain of 200 = 23 dB
is selected.
Next, using the gain value selected, the available gain circle is plotted as shown in
Figure 8.12, which reveals all values of ΓS that will yield a gain of 23 dB. Next, a specific
value for (ΓS) can be selected and, using Equations 8.14 and 8.24, a value for ΓL can be
determined. Both ΓS and ΓL must lie outside the unstable regions of the stability circles. The
trajectory of ΓL, based on the available gain circle, has been plotted in Figure 8.12 to make it


-----

easier to observe if a solution exists. If there are points where both the GA circle and the ΓL
trajectory lie outside the stability circles and also lie inside the unity Smith chart, then a
workable solution exists.
The reflection coefficients at 500 MHz are:

ΓS  �0.604 � i ? 0.167
ΓL  �0.557  i ? 0.458

Using these reflection coefficients, the amplifier matching networks can be designed. These
reflection coefficients are usually provided in the datasheets of RF components over a range of
frequencies.

###### 8.6.1 Matching and Bias Tee Network Design

Figure 8.13 shows a block diagram for the RF amplifier design. To accommodate a small
heatsink for the transistor, a 50 Ω transmission line 12.25 mm long for the gate circuit and
14 mm long for the drain circuit needs to be added to bring out the terminals before connection
to the bias tees and matching networks. The impact of both the transmission lines and bias tees
on the reflection coefficients will need to be calculated for adjustment prior to calculating the
matching network.
The 50 Ω transmission line rotates the selected impedance (reflection coefficient) around the
center of the Smith chart to a new location, since only the phase component changes and not the
characteristic impedance. Given that this is the transmission line, the direction of rotation is
counter-clockwise. The angle of rotation will depend on the length of the transmission line,
transmission line design, and the frequency of operation. The derivation for the electrical angle
based on a microstrip is given in [24]. In this example, the electrical phase is 12.46° for the gate
transmission line, and 14.24° for the drain transmission line. The rotation on the Smith chart is
twice the electrical angle.
The bias tee circuits are used to provide the quiescent supply to the transistor. It must be
designed so as to not affect the RF characteristics of the circuit, yet it needs to adequately
provide the required bias conditions. The bias tee circuit for the amplifier consists of a secondorder passive filter (DC pass – AC block) as shown in Figure 8.14. The impact on the RF circuit

Bias
Tee

Z0 Matching

Z0 _l_ Z0

Matching ΓL _L_

|Bi T|as ee|
|---|---|

|Col1|Z 0|
|---|---|
|||

|Bi T|as ee|
|---|---|


**Figure 8.13** Block diagram of the complete amplifier design that includes transmission lines, bias tees,
and matching networks


-----

RF
Input
50 Ω


Drain
Bias
Supply

RF
Output
50 Ω


**Figure 8.14** Amplifier schematic showing transmission lines, bias tees and matching networks


can be determined as the series combination of the two passive elements, shunting the RF
signal at the point of connection. Since the amplifier will be pulsed, additional design
considerations need to be made to ensure stable pulse operation of the transistor with
some useful design tips given in [25].
The selected bias tee components have the following electrical properties at 500 MHz:

LBin  48.4 nH, ESR  16 Ω
CBin  100 pF
LBout  240.8 nH, ESR  126 Ω
CBout  10 nF


Using the bias tee network values, the calculated input and output reflection coefficients, and
the effect of the transmission lines, the new reflection coefficients (ΓS) and (ΓL) can be
determined. In this example, the results are:

ΓS  �0.543 � i ? 0.414  10.45 Ω, 19.65 pF (at 500 MHz)
ΓL  �0.707  i ? 0.13  8.26 Ω, 1.41 nH (at 500 MHz)


The original reflection coefficients, impact of the transmission lines, and bias tees are shown
in Figure 8.15, with the new reflection coefficients that are used to design the matching
networks.
The design of the matching network is to convert the reflection coefficients to that of the load
and the source impedances. In this design example, the source and load impedances are 50 Ω.
For the case where the transistor resistance is less than the source impedance (Z0), the matching
network will take the form shown in Figure 8.16.
The matching network design has two solutions: (a) where X is capacitive and B is inductive,
(b) where X is inductive and B is capacitive. The preferred solution is (a), as it acts as a highfrequency pass with low-frequency filtering, and is desirable because the transistor has a higher
gain in the lower frequencies and any unwanted signal can easily corrupt the amplifier. The


-----

ΓL +
Txline

ΓS

ΓL + Txline
+ 50 Ω
Bias Tee ΓS +

Txline

ΓS + Txline
+
Bias Tee

**Figure 8.15** Amplifier design of reflection coefficients showing impact of transmission lines, bias tees,
and matching network trajectories for each port are also shown

solution for the matching network design for the schematic of Figure 8.16 is given in [8] and
repeated in Equations 8.35 and 8.36:


B
 


rffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiZ0 � RL

RL (8.35)

Z0


pffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi
X   RL ? Z 0 � RL � XL (8.36)

Since a DC block is required for both the RF input and output, and this function can be
integrated into the matching network, the case with the negative values for X and B in
Equations 8.35 and 8.36 can be calculated for the matching networks as follows.

_i•X_

_i•B_

ΓS or ΓL
Z
0

**Figure 8.16** Matching network configuration for the amplifier


-----

For the gate circuit the matching network:


r


ffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi50 10.45
�
10.45


Bin  � 50

 �0.039 S  8.18 nH  LinM


(8.37)


Xin  �pffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi10.45 ? 50 � 10.45 � 16.2 (8.38)
 �36.53 Ω  8.71 pF  CinM

and for the drain circuit the matching network:


r


ffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi50 8.26
�
8.26


Bout  � 50

 �0.045 S  7.08 nH  LoutM


(8.39)


Xout  �pffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffiffi8.26 ? 50 � 8.26  4.42 (8.40)
 �14.14 Ω  22.51 pF  CoutM

The matching network solution trajectories for these solutions have been plotted in
Figure 8.15.

###### 8.6.2 Experimental Verification

Based on the design example, a 500 MHz RF amplifier was designed and tested using the
EPC8009 [19] eGaN FET. The drain bias current was set to 250 mA and 500 mA, and the drain
bias voltage at 30 V. The amplifier was tested in pulse mode with a pulse duration of 240 μs and
a repetition rate of 10 Hz. The amplifier was tested using a vector network analyzer with
an additional RF amplifier to boost the input RF power to the amplifier, and loaded with a
20 W-capable, 30 dB RF attenuator. An RF power-in to power-out sweep was performed.
Figure 8.17 shows the 1 dB compression point for this amplifier at both bias current settings.
Figure 8.18 shows the gain and drain efficiency for the amplifier as a function of output
power.
It can be seen from the experimental results that the EPC8009 with 500 mA-drain bias
current has a 1 dB compression point at 40.6 dBm (11.6 W) output power, where the power
gain is 20.6 dB with drain efficiency of 57.4%. At a drain bias current of 250 mA, the device has
a 1 dB compression at 38.4 dBm (6.96 W) output power, where the power gain is 19.3 dB with
drain efficiency of 45.9%.
Having determined the RF performance of the GaN transistor, it may be compared to stateof-the-art LDMOS FETs with similar characteristics. Since the GaN FET was designed as a
switching device, and not an RF device, the comparison focuses on the differences pertinent to
RF designs. The metrics compared are power gain, linearity (1 dB compression,) and drain
efficiency at the same frequency of operation. The LDMOS devices selected for comparison
are [26,27] based on comparable power capabilities at 500 MHz. The comparison data between
the GaN transistor and LDMOS FETs are given in Table 8.3.


-----

43

41

39

37

35

33

31

29

27

25

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||
|||M M|eas. 50 eas. 25|0 mA 0 mA||||||||||
|||Id|eal 500|mA||||||||||
|||Id|eal 250|mA||||||||||
|||||||||||||B||
|||||||||||1 d||B||
|||||||||||Compr Poi||ession nts||
|||||||||||||||
|||||||||||||||
|||||||||||||||
|||||||||||||||


2 4 6 8 10 12 14 16 18 20 22


**Input Power (dBm)**

**Figure 8.17** Measured 1 dB compression points for the EPC8009-based RF amplifier with 30 V drain
bias voltage and 250 mA and 500 mA drain bias currents while operating at 500 MHz


From Table 8.3, it can be seen that the GaN FET has a higher gain than the LDMOS while
operating at a higher voltage with comparable drain efficiency despite the higher bias power.
The capacitances of the GaN transistor are also significantly lower than the LDMOS FETs,
ensuring lower matching impedance conversion.


22.0

21.6


70

60


21.2

20.8


50

40


20.4

20.0


30

20


19.6


10


19.2 0

25 27 29 31 33 35 37 39 41 43

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||||||
|||Gain|500 mA||||||||||
|||Gain|250 mA||||||||||
|||Drain Drain|Eff. 500 Eff. 250|mA mA|||||||||
||||||||||||||
||||||||||||||
||||||||||C|1 dB ompressio|n||
|||||||||||Points|||
||||||||||||||


**Output Power (dBm)**

**Figure 8.18** Measured gain and drain efficiency for the EPC8009-based RF amplifier with 30 V drain
bias voltage and 250 mA and 500 mA drain bias currents while operating at 500 MHz


-----

**Table 8.3** Comparison between GaN transistors and LDMOS FET at 500 MHz

Parameter GaN transistor [19] GaN transistor [19] LDMOS LDMOS
(500 mA) (250 mA) FET [26] FET [27]

Output power (W) 11.6 6.96 15 8
1 dB gain (dB) 20.6 19.3 14 13
Drain efficiency (%) 57.4 45.9 55 60
Rated voltage (V) 65 65 40 40
Bias voltage (V) 30 30 12.5 12.5
Bias current (mA) 500 250 150 150

###### 8.7 Summary

In this chapter, the key metrics and a methodology for an RF amplifier design were presented
and compared against an actual amplifier. The design was based on the EPC8009 eGaN FET,
which was not originally designed to be an RF device. Despite this, the results show excellent
RF characteristics with stable gain in excess of 20 dB, and a drain efficiency approaching 60%
at the 1 dB compression point. The GaN transistor was compared against two LDMOS FETs
with similar RF characteristics, and it was seen that the GaN transistor yields a higher gain than
the LDMOS FETs, as well as comparable drain efficiency. Many LDMOS devices are
internally matched to enhance their RF performance around a specific frequency. This reduces
the usable bandwidth to a few tens of MHz, whereas an LDMOS FET designed for broadband
applications can have an operating bandwidth around 100 MHz. GaN transistors, designed as
power switching transistors are not internally matched and, as a result, the higher impedances
enable the device to span a bandwidth of as much as 3 GHz.
It was also demonstrated that, despite being designed as a switching device, the GaN transistor
can easily be connected to a RF circuit using reference planes and microstrip tapers. This allows
for more compact designs than possible with packaged LDMOS devices. The lack of a package,
however, may present thermal limitations that can be overcome by design. The more compact
layout and lack of package can also lead to cost reductions and system size reduction.
The enhancement-mode switching GaN transistor paves the way for reduced cost RF applicationsandisideallysuitedforapplicationssuchasMRIsystems.GaNtransistorscanalsoofferhigher
blockingvoltagethanLDMOS, whichcanincreasethevoltagestandingwaveratiocapabilityand
increase an amplifier’s ability to absorb RF energy due to impedance mismatching.
In the next chapter, the capability of certain GaN transistors in space applications will be
reviewed. Once again, GaN FETs outperform their aging silicon counterparts in the most
demanding of environments.

###### References

1. White, D. and Wilcox, G. (2012) New GaN FETs, Amplifiers and Switches Offer System Engineers a Way to
Reduce RF Board Space and System Prime Power, white paper, TriQuint, September.
2. Inoue, K., Sano, S., Tateno, Y. et al. (2010) Development of gallium nitride high electron mobility transistors for
cellular base stations. SEI Technical Review, 71, 88–93.
3. “Gallium Nitride (GaN) Microwave Transistor Technology For Radar Applications,” white paper, Aethercomm,
Dec. 2007.


-----

4. Murphy, M. (2011) “NXP goes with GaN,” Compound Semiconductor, Aug./Sep., pp. 23–26.
5. “GaN devices set benchmarks for power and bandwidth,” Microwave Product Digest, Feb. 2012, Available from

[www.mpdigest.com.](http://www.mpdigest.com)
6. Ishida, T. (2011) GaN HEMT technologies for space and radio applications. Microwave Journal, 54 (8), 57–63.
7. Nitronex (April 2013) Gallium Nitride 28V, 25W RF Power Transistor, NPT1012 datasheet, NDS-025 Rev. 3.
[Available from www.nitronex.com/NPT1012_Product_Page.html.](http://www.nitronex.com/NPT1012_Product_Page.html)
8. Pozar, D.M. (2005) Microwave Engineering, 3rd edn, J. Wiley.
9. Gonzales, G. (1997) Microwave Transistor Amplifiers, 2nd edn, Prentice Hall.
10. Hejhall, R.C. (1993) RF Small Signal Design Using Two-Port Parameters, Motorola, Appl. Note AN215A.
11. Payne, K. (2008) Practical RF Amplifier Design Using the Available Gain Procedure and the Advanced Design
System EM/Circuit Co-Simulation Capability, white paper, 5990-3356EN, Agilent Technologies, Available from,
[www.agilent.com.](http://www.agilent.com)
12. Lidow, A., Strydom, J., Rooij, M.de., and Ma, Y. (2012) GaN Transistors for Efficient Power Conversion, 1st edn,
Power Conversion Press, El Segundo.
13. Strydom, J. (Oct. 2012) “eGaN[] FET- Silicon Power Shoot-Out Volume 11: Optimizing FET On-Resistance,”
_[Power Electronics Technology, Available from http://powerelectronics.com/discrete-semis/gan_transistors/egan-](http://powerelectronics.com/discrete-semis/gan_transistors/egan-fet-silicon-power-shoot-out-volume-11-optimizing-fet-on-resistance-1001/)_
[fet-silicon-power-shoot-out-volume-11-optimizing-fet-on-resistance-1001/.](http://powerelectronics.com/discrete-semis/gan_transistors/egan-fet-silicon-power-shoot-out-volume-11-optimizing-fet-on-resistance-1001/)
14. de Rooij, M. and Strydom, J. (June 2012) “eGaN[] FET-Silicon Power Shoot-Out Volume 9: Low Power Wireless
[Energy Converters,” Power Electronics Technology. Available from http://powerelectronics.com/discrete-power-](http://powerelectronics.com/discrete-power-semis/egan-fet-silicon-shoot-out-vol-9-wireless-power-converters)
[semis/egan-fet-silicon-shoot-out-vol-9-wireless-power-converters.](http://powerelectronics.com/discrete-power-semis/egan-fet-silicon-shoot-out-vol-9-wireless-power-converters)
[15. Cree, GaN HEMT RF FET, CGH55015, datasheet. Available from http://www.cree.com/RF/Products/SBand-](http://www.cree.com/RF/Products/SBand-XBand-CBand/Packaged-Discrete-Transistors/CGH55015F2-P2)
[XBand-CBand/Packaged-Discrete-Transistors/CGH55015F2-P2.](http://www.cree.com/RF/Products/SBand-XBand-CBand/Packaged-Discrete-Transistors/CGH55015F2-P2)
16. Engen, G.F. and Hoer, C.A. (December 1979) “Thru-reflect-line: an improved technique for calibrating the dual
six-port automatic network analyzer,” IEEE Trans. Microwave Theory and Techniques.
17. Agilent, Network Analysis Applying the 8510 TRL Calibration for Non-Coaxial Measurements Product Note
8510-8A.
18. Fleury, J. and Bernard, O. (2001) Designing and Characterizing TRL Fixture Calibration Standards for Device
Modeling, Applied Microwave & Wireless Technical Note 13, pp. 26–55.
19. Efficient Power Conversion Corporation (2013) “EPC8009 – Enhancement-mode Power Transistor,” EPC8009
[datasheet, Sept. Available from http://epc-co.com/epc/documents/datasheets/EPC8009_datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC8009_datasheet.pdf)
[20. Rogers Corporation (2014) Rogers 4350 Laminates, datasheet. Available from http://www.rogerscorp.com/acm/](http://www.rogerscorp.com/acm/products/55/RO4350B-Laminates.aspx)
[products/55/RO4350B-Laminates.aspx.](http://www.rogerscorp.com/acm/products/55/RO4350B-Laminates.aspx)
21. de Rooij, M.A. and Strydom, J.T. (Sep. 2013) Method for Bias Control of a Class A Power RF Amplifier, U.S.
patent pending.
22. Rollett, J.M. (1962) Stability and power-gain invariants of linear two ports. IRE Transactions on Circuit Theory,
**9 (1), 29–32.**
23. Orfanidis,S.J.(2014) _ElectromagneticWavesandAntennas,Availablefrom_ [http://www.ece.rutgers.edu/∼orfanidi/ewa/.](http://www.ece.rutgers.edu/~orfanidi/ewa/)
24. Bahl, I.J. and Trivedi, D.K. (1977) A designer’s guide to microstrip line. Microwaves, May 1977, 174–182.
25. Baylis, C., Dunleavy, L., and Clausen, W. (2006) Design of bias tees for a pulsed-bias, pulsed-RF test system using
accurate component models. Microwave Journal, 49 (10), 68–75.
[26. STMicroelectronics, PD55015 – RF Power Transistor, datasheet, Aug. 2011. Available from http://www.st.com/](http://www.st.com/web/en/resource/technical/document/datasheet/CD00128612.pdf)
[web/en/resource/technical/document/datasheet/CD00128612.pdf.](http://www.st.com/web/en/resource/technical/document/datasheet/CD00128612.pdf)
27. Freescale Semiconductor, RF Power Field Effect Transistor, MRF1518N datasheet, [Rev. 11 June 2009] Available
[from http://www.freescale.com/files/rf_if/doc/data_sheet/MRF1518N.pdf.](http://www.freescale.com/files/rf_if/doc/data_sheet/MRF1518N.pdf)


-----

# 9

#### GaN Transistors for Space Applications

###### 9.1 Introd uction

Radiat ion in space is generat ed by many source s withi n and outside of our solar syst em. This
radiation comes in the form of gamm a rays, e nergetic electrons, proto ns, and heavie r ions,
which are all known to cause damag e in semi conduct ors. Over the years, sil icon-based device s
have been well charact erize d und er vario us radia tion condit ions, vulner abilities have been
identifi ed and, to some extent mitiga ted through design and proces s improvem ents. NASA has
published guidelines to help desig ners of satel lite syst ems consi stently desig n for the different
enviro nments en countered in vario us earth o rbits [1].
In this chapte r, we will look at the research on GaN capabi lities under expo sure to different
types of radiation with a particula r focus on GaN trans istors used in power co nversion. We wi ll
then look at actual measurem ents of comm ercial grade enhancem ent mode GaN transistors and
compa re thei r capabi lity against radia tion -resistant silicon powe r MO SFETs.

###### 9.2 Failure Mechanis ms

An energet ic parti cle can cause damag e to a semiconduc tor in three prim ary ways : (1) it can
cause traps in no n-condu cting layers, (2) it can cause physical damag e to the crystal
(displacem ent damage) or the interface between the crysta l and a Schott ky barrier, and (3)
it can creat e a cloud of e lectron –hole pairs that will cause the device to mom entarily conduct
(and possi bly burn out in the process) [2].
Power MOSF ETs, in particula r, are vulner able to radia tion in two ways. First, gamm a
(electron) radiation can cause positive ly charged (hole ) traps to develo p in the thin gate
oxide [2,3]. The addition of positive charges between the gate elect rode and the channel
reduces the thres hold voltage of the n-chann el power MO SFET. The second maj or v ulnerability stems from energet ic particles that can fully penetrate the semi conductor device. These
particles cause the single event effects (SEE), and the failures are known as single event upset
(SEU).

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

In order to understand how these same radiation effects impact the electrical performance of
GaN transistors, we need to consider Schottky-based depletion-mode devices (Figure 1.6(a) in
Chapter 1), MOS-based depletion-mode devices (Figure 1.6(b) in Chapter 1), and pGaN-based
enhancement-mode devices (Figure 1.7 in Chapter 1). All three of these structures use an
AlGaN/GaN barrier to generate the 2DEG, but have different gate structures that can lead to
different vulnerabilities when exposed to radiation. Cascode-configured GaN transistors will
not be considered in this chapter because their behavior would be influenced significantly by
the silicon MOSFET’s radiation tolerance.

###### 9.3 Standards for Radiation Exposure and Tolerance

The NASA guidelines for transistors [1] set the standard set for a “Rad Hard” device as the
ability to withstand a total incident dose (TID) between 200 kRad(Si) and 1 MRad(Si), and
an SEU threshold linear energy transfer (LET) of 80–150 MeV mg[�][1] cm[�][2]. A “Rad” is
defined as the mean energy absorbed per unit mass of irradiated material at the point of
interest [3].

1 Rad 100 ergs/g


A Rad(Si) would be a measure of absorption in a silicon crystal. In order to maintain
comparisons with silicon power MOSFETs, most researchers have elected to use Rad(Si) to
report their results for GaN devices.
LET is a measure of the energy deposited by an incident particle (the “stopping power”) per
unit of track length. A heavier ion, such as Au, would have a higher LET for the same energy
than a lighter ion, such as a proton.

###### 9.4 Gamma Radiation Tolerance

The common approach to measuring device tolerance to gamma radiation is to use the decay
radiation from a Cobalt-60 ([60]Co) source. Using this method, testing of depletion-mode
Schottky gate transistors designed for RF applications has been reported in [4] and [5],
where the results showed no degradation when exposed to up to 600 MRads(Si), and
are consistent with results for silicon JFETs [2]. This is not surprising because there are
no oxides in the gate structure that can trap charge, and thereby modulate the threshold
voltage.
To date, no measurements have been reported for MOS-gated GaN HEMT transistors. There
is no reason to believe that their behavior would be significantly different from the behavior of
silicon power MOSFETs. Gamma radiation-induced trapping in the insulating gate will cause a
negative shift in threshold voltage that could lead to circuit failure.
Enhancement-mode pGaN HEMT transistors have been tested extensively [6,8] with
favorable results. In these tests, the devices had either drain-to-source bias during testing,
or gate-to-source bias. By exposing devices to radiation while applying bias on each of the
transistor terminals, the in-circuit performance in a high radiation environment can be
projected. Figure 9.1 is a graph showing the progression of drain-to-source leakage current
and threshold voltage of several devices tested up to 1 MRad(Si).


-----

1000

100


10


1

2.500

|0|EPC1015 Gate and Drain – Source Leakage Current|
|---|---|
|||
|||
|||


0 5E+05 1E+06

**Radiation Dose**


(a)


IGSS after VDS
IGSS after VDS
IGSS after VDS
IDSS after VDS
IDSS after VDS
IDSS after VDS
IGSS after VGS
IGSS after VGS
IGSS after VGS
IDSS after VGS
IDSS after VGS
IDSS after VGS

VTH after VDS

VTH after VDS

VTH after VDS

VTH after VGS

VTH after VGS

VTH after VGS


2.300

2.100


1.900

1.700


1.500

1.300


1.100

.900


.700


**EPC1015 Threshold Voltage**

0 5E+05 1E+06


**Radiation Dose**

(b)

**Figure 9.1** (a) Drain-source leakage current (IDSS), and (b) Threshold voltage of EPC1015 eGaN FETs
after exposure to 1 × 10[6] Rad(Si). Devices with 5 V gate-source bias during testing are shown as solid
lines. Devices with 80 V drain-source bias during testing are shown as dotted lines [6]


-----

###### 9.5 Single-Event Effects (SEE) Testing

As with gamma radiation testing, there has been significant research on SEE in Schottky gate
RF HEMT transistors [7,8], but no MOS gate HEMT device testing has been reported. In the
case of a cascode GaN transistor, the reaction to single event radiation would be determined by
the combination of the silicon MOSFET and the GaN transistor in their series configuration.
Enhancement-mode pGaN gated devices have also had extensive testing [6,9,10].
Failures under SEE testing of power transistors fall into two categories: single event burnout
(SEB) and single event gate rupture (SEGR). SEGR is unlikely in a Schottky gate or pGaN gate
HEMT device because there are no insulating gate layers that would be the source of failure.
The Schottky gate and pGaN gate devices showed remarkable resistance to SEE radiation. In
reference [7], Schottky gate devices showed slow degradation of IDSS when irradiated with
bromine ions at 39 LET. Abrupt failures (SEB) were observed in these devices with 70 V drainto-source bias at a LET of 60 MeV mg[�][1] cm[�][2]. Schottky gate transistors in reference [8] also
showed no degradation when exposed to lesser levels of SEE radiation from FE, O, and C
atoms. Reference [10] also showed excellent SEE tolerance with the main failure mechanism
being the increase of IDSS leakage, the rate of which scaled with the LET and drain-to-source
voltage.
The highest level of SEE capability for a GaN HEMT was reported in references [9,11].
Tests showed eGaN FET devices capable of withstanding 1 × 10[13] cm[�][2] Au atoms at a LET of
87.2 MeV mg[�][1] cm[�][2] with full-rated voltage applied to 40 V or 100 V rated transistors. The
200 V rated eGaN FETs survived up to 190 V bias and, at that voltage, failures were a result of a
slow increase in IDSS. An example of the stability of devices under Au bombardment is shown
in Figure 9.2. The basic failure mechanism is the physical displacement of atoms in the crystal
due to the large momentum transfer from the incident heavy ions.


1.E-04

1.E-05


**EPC8003, VDS 100 V, VGS 0 V**
**85.4 LET Au**


1.E-06


1.E-07
1 12 23 34 45 56 67 78 89 100 111 122 133 144 155 166 177 188 199

**Figure 9.2** IDSS and IGSS progression for MGN8903 GaN transistor during single event testing with
110[6] ions/cm[2] Au at 85.4 LET and biased at 100 VDSS [11]


-----

**Table 9.1** Comparison of key electrical 200 V rated commercial MOSFET (IPB107N20N3 G) [12] and a
comparably rated rad-hard MOSFET (IRHN57250SE) [13]

IPB107N20N3G IRHN57250SE Units Performance Ratio

Rad tolerant No Yes
BVDSS 200 200 V 1.0
RDS(on) 0.011 0.06 Ω 5.5
QG 161 132 nC 0.8
QGS 23 45 nC 2.0
QGD 8 60 nC 7.5
QGRDS(on) 1.8 7.9 nCΩ 4.5
(QOSS + QG)RDS(on) 2.6 11.2 nCΩ 4.3
QGDRDS(on) 0.09 3.6 nCΩ 41

###### 9.6 Performance Comparison between GaN Transistors and Rad-Hard Si MOSFETs

Schottky gate and pGaN gate HEMT transistors can tolerate high doses of radiation without
significant performance degradation, and without the need for any changes to the device design
or fabrication process. In the case of the enhancement-mode GaN devices, as shown in
Chapters 3–7, they significantly outperform state-of-the-art commercial power MOSFETs.
Unlike GaN transistors, power MOSFETs designed to operate in high-radiation environments
do not have dynamic switching performance comparable to commercial MOSFETs. Significant compromises in device geometries and fabrication process are needed to harden the final
product [3]. Illustrating these significant compromises required of rad-hard MOSFET users,
Table 9.1 compares a state-of-the art commercial power MOSFET with a comparable

**Table 9.2** Comparison of key electrical parameters and radiation tolerance between a 200 V rated
enhancement-mode GaN HEMT (EPC2010) [14] and a comparably rated rad-hard MOSFET
(IRHN57250SE) [13]

EPC2010 IRHN57250SE Units Performance Method
Ratio

BVDSS 200 200 V
RDS(on) 0.025 0.06 Ω 2 : 1
QG 7.5 132 nC 18 : 1
QGS 2 45 nC 23 : 1
QGD 2.6 60 nC 23 : 1
QGRDS(on) 0.19 7.9 nCΩ 42 : 1
(QOSS + QG)RDS(on) 1.12 11.2 nCΩ 10 : 1
QGDRDS(on) 0.065 3.6 nCΩ 55 : 1
Demonstrated SEE SOA 190 200 V 1 : 1 MIL-STD750E
at 84 LET (VG = 0 V) Method 1080
Demonstrated TID >1000 100 kRad(Si) >10 : 1 MIL-STD750E
capability Method 1019


-----

radiation-tolerant version [12,13]. The last two rows in the table compare the soft-switching
figures of merit (FOM) and the hard-switching FOM first discussed in Chapter 6 and 7,
respectively. The latest commercial MOSFET are 4–5 times superior to the rad-hard MOSFET
in these two key measures of device performance in switching converters.
Moving on to radiation-tolerant transistors, Table 9.2 compares the performance of a 200 V
enhancement-mode GaN HEMT [14] and a 200 V rad-hard MOSFET [13,15]. The GaN
HEMT has comparable SEE capability, 10 times the gamma radiation tolerance (TID), a hardswitching FOM (RDS(on)  QGD) 50 times superior, and a soft-switching FOM (RDS(on) 
(QG + QOSS)) 10 times superior to the comparable rad-hard MOSFET. Any power conversion
system would operate with significantly lower losses and higher gamma radiation tolerance
using these enhancement-mode GaN transistors.

###### 9.7 Summary

GaN transistors have been tested under heavy ion bombardment and gamma irradiation. These
devices demonstrate readiness for use in the most stringent of radiation environments and far
exceed the capabilities of silicon power MOSFETs. The problem that designers encounter with
silicon MOSFETs is that they must choose between radiation tolerance and electrical
performance. Commercial MOSFETs have thick gate oxides and so trap a lot of charge,
resulting in large shifts in the threshold voltage and eventual failure at relatively low total-dose
exposure. The radiation-hardened MOSFETs available have FOMs several times worse than
their commercial counterparts, leading to either low efficiency or large size (due to the low
switching frequency). Enhancement-mode GaN transistors give designers a new capability
with electrical performance superior to the cutting-edge Si MOSFETs, and radiation tolerance
at least as high as the best rad-hard power MOSFETs available. These GaN transistors bring a
combination of electrical and radiation performance that establishes a new state of the art.
The tools and techniques discussed in Chapters 3–7 lay the foundation for the applications
that are discussed in Chapter 10. The applications selected are among the first to widely use
GaN transistors for power conversion.

###### References

1. Space Radiation Effects on Electronic Components in Low Earth Orbit, NASA Practice No. PD-ED-1258.
2. Messenger, G.C. and Ash, M.S. (1986) The Effects of Radiation on Electronic Systems, Van Nostrand Reinhold
Company, New York, NY.
3. Ma, T.P. and Dressendorfer, P.V. (1989) Ionizing Radiation Effects in MOS Devices and Circuits, John Wiley and
Sons, Inc., New York.
4. Aktas, O., Kuliev, A., Kumar, V. et al. (2004) [60]Co gamma radiation effects on DC, RF, and pulsed I–V
characteristics of AlGaN/GaN HEMTs. Solid-State Electronics, 48, 471–475.
5. McClory, J.W. (2008) The Effect Of Radiation on the Electrical Properties of Aluminum Gallium Nitride/Gallium
Nitride Heterostructures, Ph.D. dissertation, The Air Force Institute of Technology, Wright-Patterson Air Force
Base, Ohio, June.
6. Lidow, A., Witcher, J.B., and Smalley, K. (March 2011) Enhancement mode gallium nitride (eGaN[]) FET
characteristics under long-term stress, GOMAC Tech Conference, Orlando Florida.
7. Bazzoli, S., Girard, S., Ferlet-Cavrois, V. et al. (2007) SEE sensitivity of a COTS GaN transistor and silicon
MOSFETs, 9th European Conference on Radiation and Its Effects on Components and Systems, RADECS 2007.
8. Sonia, G., Brunner, F., Denker, A. et al. (2006) Proton and heavy ion irradiation effects on AlGaN/GaN HFET
devices. IEEE Transactions on Nuclear Science, 53 (6)
9. Lidow, A. and Smalley, K. (2012) Radiation tolerant enhancement mode gallium nitride (eGaN[]) FET characteristics, GOMAC Tech Conference, Las Vegas, Nevada, March 2012.


-----

10. Lidow, A., Strydom, J., and Rearwin, M. (2014) Radiation tolerant enhancement mode gallium nitride (eGaN[])
FETs for high-frequency DC-DC conversion, GOMAC Tech Conference, Charleston, South Carolina, April 2014.
11. Kuboyama, S., Maru, A., Shindou, H. et al. (2011) Single-event damages caused by heavy ions observed in
AlGaN/GaN HEMTs. IEEE Transactions on Nuclear Science, 58 (6)
12. Infineon (July 2011) “OptiMOS[TM]3 Power Transistor,” IPB107N20N3 G datasheet.
13. International Rectifier (Dec. 2011) “Radiation hardened power MOSFET surface mount (SMD-1),”
IRHN57250SE.
14. Efficient Power Conversion Corporation “EPC2010 – Enhancement-mode Power Transistor,” EPC2010 datasheet,
[Jul. 2011 [Revised Feb. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet](http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet.pdf)
[.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2010_datasheet.pdf)
15. Strydom, J., Lidow, A., and Goti, T. (2013) Radiation Tolerant enhancement mode gallium nitride (eGaN[]) FETs
in DC-DC converters, GOMAC Tech Conference, Las Vegas, Nevada, March 2013.


-----

# 10

#### Application Examples

###### 10.1 Introduction

This chapte r presen ts some applic ation examp les where GaN trans istors are alrea dy making
inroa ds. As presen ted in the previ ous chapte rs, these inroads stem direc tly from the GaN
transist or ’s relative imp rovement in figures o f merit (FOM ) over the silicon MO SFET, be it in
hard-s witch or soft-swit ching applicati ons. GaN transist ors offer the potential to improve
perfor mance over the aging popula tion of Si MO SFETs, en abling a n ew generat ion of power
convert ers that offer higher freque ncies, efficiencies, and densities than ev er before .

###### 10.2 Non-Isolated DC-DC Conv erters

Non-iso lated, point -of-load (P OL) convert ers are found in compu ters, telecomm unication
systems, handhel d elect ronics, and many other applicati ons. The y are perhaps the most
comm on way to convert from on e DC volta ge to a diff erent DC voltage. With the everincre asing powe r demands of moder n technologi es, combined with the desire for smaller size
and lower powe r consum ption, POL convert er desig ns must drive toward higher power
densi ty, efficiency, and trans ient respon se capabi lity in order to meet these evolvi ng system
deman ds.
The majority of POLs are non-isolat ed step- down buck convert ers, often wi th a large stepdown rati o from as much as 60 V input to below 1 V output . The most straightforw ard way to
improve p ower densi ty and transient respon se c apability is to incre ase switching freque ncy.
This enable s a volume reduct ion in the pa ssive compo nents, as well as a faster react ion time to
transient spikes of voltage and curren t from the source or the load. The pract ical issue with
today ’ s sil icon-based solution s is that incre asing switch ing freque ncy _decreas es_ e fficiency as a
result of higher switch ing loss es in the aging powe r MOS FETs, thus limit ing these solution s to
the range of a couple hundred kilo hertz to a megah ertz. GaN trans istors great ly reli eve this
const raint by easily operat ing well above these freque ncies without loss of system efficiency .
Shown in Figure 10.1 are the effi ciencies and power losses of GaN transistors and
Si MO SFETs when applied in 1.2 VOUT buck convert ers for va rious input vo ltages at switching
frequencies of 500 kHz and 1 MHz. As frequency and voltage increase, so do the gains offered
by GaN transistors. For a 12 VIN design operating at 1 MHz, GaN transistors can improve

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

100

95

90

85

80

75

70

65

60

55

50

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||40 V|GaN|Tran||sistor|||||||
|||||||||||100 V Trans|GaN istor||
||||||||||||||
|40 MO||V Si SFET|||||||||||
||||||||||||||
|I||V = OUT = 1|1.2 V 0 A||||||||||
|||OUT|||||||||||
||||||||||||||
||||500 k|Hz|||80 V MOS|Si FET|||||
||||||||||||||
||||1 MH|z|||||||||
||||||||||||||

|Col1|Col2|Col3|Col4|Hz|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||500 k 1 MHz|Hz||||||||
|||||||||||||
|||||||80 MO|V Si SFET|||||
|||V OUT|= 1.2|||||||||
|||I = OUT|10 A|||||||||
|4||0 V S|i|||||||||
|M||OSF|ET|||||||||
|4||0 V G|aN T|ransist|or||100 Tra|V Ga nsisto|N r|||


10 15 20 25 30 35 40 45 50 55 60 65

**Input Voltage (V)**

(a)


12

10


8

6


4

2


0

10 15 20 25 30 35 40 45 50 55 60 65

**Input Voltage (V)**

(b)


**Figure 10.1** (a) Efficiency and (b) power loss comparisons for GaN transistors and Si MOSFETs
in a synchronous buck converter (VOUT = 1.2 V, IOUT = 10 A, 40 V GaN transistors: control device:
EPC2015 synchronous rectifier: EPC2015, 40 V MOSFETS: control device: BSZ097N04LSG synchronous rectifier: BSZ040N04LSG,100 V GaN transistors: control device: EPC2001, synchronous
rectifier: EPC2001, 80 V MOSFETS: control device: BSZ123N08NS3G, synchronous rectifier:
BSZ123N08NS3G)

efficiency by around 3%. For a 60 VIN design at 1 MHz, GaN transistors can improve efficiency
by around 18%. This section will demonstrate the advantages offered by GaN transistors in
common POL applications ranging from 60 VIN to 12 VIN.


###### 10.2.1 12 VIN – 1.2 VOUT Buck Converter

In this section, a POL converter designed for one of the most common requirements will be
discussed, 12 VIN and 1.2 VOUT. This is both a cost-sensitive and an efficiency-sensitive highvolume application. In Chapters 4 and 6, the importance of minimizing parasitics and providing
an optimal layout for GaN transistors was discussed, In this section, these techniques will be
applied to a converter operating at 1 MHz to yield a benchmark efficiency.
To compare the performance of the optimal power loop discussed in Chapter 4 (Section 4.4)
with conventional lateral or vertical layouts, four separate designs were created. The overall
thickness of the board and the distance between the top layer and the first inner layer in the
board (inner layer distance) varies as illustrated in Figure 10.2. The component layouts
remained unchanged from those used earlier in Section 4.4. All designs have four layers with
two-ounce copper thickness, and their variables are given in Table 10.1.


Board
Thickness


Top Layer

Inner Layer 1

Inner Layer 2

Bottom Layer


![](GaN-transistors-power-conversion.pdf-197-0.png)

Inner Layer
Distance


**Figure 10.2** PCB cross-section drawing of board thickness and inner layer distance


-----

**Table 10.1** Board variables for layout comparison

Board thickness (mils) First inner layer distance (mils)


Design 1 31 4
Design 2 31 12
Design 3 62 4
Design 4 62 26


Simulated values of the high-frequency loop inductance for varying board thicknesses and
inner layer distance are presented in Figure 10.3. From the data, it can be seen that for the lateral
power loop the board thickness has little impact on the high-frequency loop inductance, while
the inner layer distance (the distance from the power loop to the shield layer) significantly
impacts the inductance. For the vertical power loop, the inner layer distance has very little
impact on the inductance of the design, while the board thickness significantly increases the
inductance by as much as 80% when the board thickness is doubled from 31 to 62 mils (0.8 mm
to 1.5 mm).
For the optimal layout, the design shares the traits of the lateral power loop by showing little
dependence on board thickness and a strong dependence on inner layer distance. This design
provides a significant reduction in loop inductance by the removal of the shield layer and a
reduced physical size of the power loop, traits similar to the vertical power loop design.
Combining the strengths of both conventional designs, and limiting the weaknesses, this design
provides a significant reduction in inductance compared to the best lateral and vertical power
loops.
The power loss for the four board thicknesses and the three different loop layouts is shown in
Figure 10.4. From this data, it can be seen that, for similar parasitic inductances, the power loss
of the lateral loop is higher than the vertical loop. This increased loss in the lateral power loop

2.2


2


1.8

1.6

1.4

1.2

1


0.8

0.6

0.4

0.2

|Inner Layer D|Col2|istance|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||Inner Layer D|istance|||||
||4|mils|||||
||1|2 mils||Vertical Po Loop|wer||
||2|6 mils|||||
|||||||Lateral|
|||||||Power Loop|
||||||||
|||O||ptimal Powe|r Loop||
||||||||
||||||||


20 30 40 50 60 70


**Board Thickness (mil)**

**Figure 10.3** Simulated high-frequency loop inductance values for lateral, vertical, and optimal power
loops with different board thickness and inner layer distance


-----

4


3.9

3.8

3.7

3.6

3.5

3.4

3.3

3.2

3.1

3

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|||Lateral Loo|Power p||||||
||||||||||
||||||Ve|rtical P|ower||
|||||||Loop|||
||||||||||
||||||||||
|||Optima|l Powe|r|||||
|||Lo|op||||||
||||||||||


0.2 0.4 0.6 0.8 1 1.2 1.4 1.6 1.8 2


**High Frequency Loop Inductance (nH)**

**Figure 10.4** Power loss plot for lateral, vertical, and optimal power loop designs. (VIN = 12 V,
VOUT = 1.2 V, IOUT = 20 A, fsw = 1 MHz, L = 300 nH, control device: EPC2015, synchronous rectifier:
EPC2015)


can be attributed to the additional loss in the shield layer due to eddy currents, which is not
required in the vertical or optimal power loop.
The voltage overshoot for the different designs is shown in Figure 10.5. As loop inductance
increases up to 1.4 nH, so does the voltage overshoot. Beyond 1.4 nH, the voltage overshoot
does not significantly increase. This can be explained by Figure 10.6 that shows the measured
switching speed of the different designs. As the loop inductance increases, the dv/dt of the

100


90

80


70

60


50

40


30


20

0.2 0.4 0.6 0.8 1 1.2 1.4 1.6 1.8 2

**High Frequency Loop Inductance (nH)**

**Figure 10.5** Measured voltage overshoot vs. loop inductance (VIN = 12 V, VOUT = 1.2 V, IOUT = 20 A,
fsw = 1 MHz, L = 300 nH, control device: EPC2015, synchronous rectifier: EPC2015)

|Col1|Col2|Lateral|Power|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
|||Lo|op||||||
|||||V|ertical|Power|||
||||||Loo|p|||
||||||||||
||Opt|imal P|ower||||||
|||Loop|||||||
||||||||||


-----

10

9

8

7

6

5

4

3

2

1


0

0.2 0.4 0.6 0.8 1 1.2 1.4 1.6 1.8 2

**High Frequency Loop Inductance (nH)**

**Figure 10.6** Measured device switching speed vs. loop inductance (VIN = 12 V, VOUT = 1.2 V,
IOUT = 20 A, fsw = 1 MHz, L = 300 nH, control device: EPC2015, synchronous rectifier: EPC2015)

|Col1|Col2|Opti|mal Pow|er|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||Loop||||||
|||||Later|al Powe|r|||
|||||L|oop||||
||||||||||
||||Vertica|l Powe|r||||
||||L|oop|||||
||||||||||
||||||||||
||||||||||


device decreases significantly. This results in higher power loss, but helps limit voltage
overshoot. For the two vertical loop designs with the highest loop inductance, the switching
speed is reduced by over 60% when compared to all the other designs.
Shown in Figure 10.7 are the efficiency results of design 1 (Table 10.1) for the three GaN
transistor based designs compared to a silicon implementation utilizing a vertical power loop
with the smallest commercial package, a 3 × 3 mm TSDSON-8. For the Si MOSFET design,


91

90

89

88

87

86

85

84

83


2 4 6 8 10 12 14 16 18 20 22 24 26


**Figure 10.7** Efficiency comparisons for design 1 in Table 10.1 (VIN = 12 V, VOUT = 1.2 V, fsw = 1 MHz,
L = 300 nH, GaN transistors: control device: EPC2015, synchronous rectifier: EPC2015, MOSFETs:
control device: BSZ097N04LSG, synchronous rectifier: BSZ040N04LSG)

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|4|0 V|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
||||||||||GaN|Transi|stor|
||||||||||O De|ptimal sign 1||
||||||||||Ve De|rtical sign|1|
||||40|V MO|SFET||||L|atera|l|
||||Vert|ical D|esign|1|||D|esign|1|
|||||||||||||
|||||||||||||
|2 4 6 8 10 12 14 16 18 20 22 24 2 Output Current (A) ency comparisons for design 1 in Table 10.1 (V = 12 V, V = 1.2 IN OUT||||||||||||


-----

Si MOSFET
Si MOSFET

GaN
Transistor
Optimal
Layout

**3 V/Div** **20 ns/Div** **3 V/Div** **20 ns/Div**

(a) (b)

**Figure 10.8** Synchronous rectifier switching waveforms of (a) GaN transistor-based conventional
layout vs. Si MOSFET (b) GaN transistor-based optimal layout vs. Si MOSFET design (VIN = 12 V,
VOUT = 1.2 V, IOUT = 20 A, fsw = 1 MHz, L = 300 nH, GaN transistors: control device: EPC2015, synchronous rectifier: EPC2015, MOSFETs: control device: BSZ097N04LSG, synchronous rectifier:
BSZ040N04LS G)

the high-frequency loop inductance was measured to be around 2 nH, compared to 1 nH for a
similar power loop using GaN transistors. This is due to the large packaging inductance of the
Si MOSFET dominating the loop design. As a result of the superior FOM and packaging of the
GaN transistors, all of the power loop structures outperform the Si MOSFET benchmark
design. With the optimal power loop, the GaN transistor designs can be improved even further,
achieving almost 3% full load and 3.5% peak efficiency improvements.
For the different GaN transistor designs, the optimal power loop provides a 0.8% and 1% full
load efficiency improvement over the vertical and lateral power loops, respectively. For all of
the designs outlined in Table 10.1, the optimal layout provides the highest efficiency and
lowest device voltage overshoot.
The switching waveforms for the GaN transistor and Si MOSFET benchmark-based
conventional (lateral/vertical) and optimal layouts are shown in Figure 10.8(a) and (b),
respectively. Both GaN transistor-based designs offer significant switching speed gains
when compared to the Si MOSFET benchmark. For GaN transistors with a conventional
layout, the high switching speed, combined with a traditional PCB layout loop inductance,
results in a large voltage spike. The optimal layout GaN transistor design with minimized loop
inductance offers a 500% increase in switching speed and a 40% reduction in voltage overshoot
compared to the MOSFET benchmark.

###### 10.2.2 28 VIN – 3.3 VOUT Point-of-Load Module

With the reduced voltage overshoot and high efficiency achievable with the optimal GaN
transistor layout, a converter can handle much higher input voltages using lower voltage-rated
devices. In this section, the exceptional performance of another common format of POL
converter will be reviewed: 28 VIN – 3.3 VOUT operating at 1 MHz with a 15 A maximum
output current. The entire circuit is shown in Figure 10.9(a) and occupies an area of 0.25 in[2]

(0.4 cm[2]). The peak overshoot at full load and at 28 V input is around 3 V, as illustrated in the
oscillogram of Figure 10.9(b), easily allowing the use of 40 V GaN transistors. As shown in


![](GaN-transistors-power-conversion.pdf-201-0.png)

Si MOSFET

GaN
Transistor
Optimal
Layout

**3 V/Div** **20 ns/Div**


![](GaN-transistors-power-conversion.pdf-201-1.png)

GaN Transistor Conventional Layout

Si MOSFET

**3 V/Div** **20 ns/Div**


-----

![](GaN-transistors-power-conversion.pdf-202-0.png)

VIN=28 V IOUT=15 A

~1.1ns Rise Time at 15 A

**5 V/Div** **20 ns/Div**


(a) (b)

**Figure 10.9** (a) Photo of a GaN transistor-based POL module (b) Synchronous rectifier switching
waveform (VIN = 28 V, VOUT = 3.3 V, IOUT = 15 A, fsw = 1 MHz, GaN transistors: control device:
EPC2015, synchronous rectifier: EPC2015)


![](GaN-transistors-power-conversion.pdf-202-0.png)

97
96
95
94
93
92
91
90
89
88
87
86
85
84
83

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
||||||||||||||||12 V|IN||
||||||||||||||||19 V|IN||
||||||||||||||||24 V|IN||
||||||||||||||||28 V|IN||
|||||||||||||||||||


0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16
**Output Current (A)**


**Figure 10.10** Efficiency of GaN-based POL module (VOUT = 3.3 V, fsw = 1 MHz, GaN transistors:
control device: EPC2015, synchronous rectifier: EPC2015)

Figure 10.10, this design demonstrates efficiency above 96% for a 12 V-input and over 93% for
a 28 V input.


###### 10.2.3 48 VIN – 12 VOUT Buck Converter with Parallel GaN Transistors for High-Current Applications

Common to many computer servers is a 48 V power distribution bus. In many cases there is a
secondary distribution bus at 12 V (more on this in Section 10.3). As a result, there is a large
need for DC-DC converters that step down from 48 VIN to 12 VOUT. Many of these systems
require isolation between the input and output, and those isolated converters will be discussed


-----

in Section 10.3. For systems that do not require isolation, GaN-transistor-based buck
converters can deliver lower cost, greater power density, higher conversion efficiency, and
faster transient response while achieving greater output current capability with minimal
degradation in performance. Such designs will be considered in this section.
In Section 4.5, techniques for effectively paralleling high-speed GaN transistors were
discussed. In this section, the impact of in-circuit parasitics on performance and a comparison
of PCB layouts will be examined for a 48 V to 12 V, 480 W, 40 A buck converter operating at a
switching frequency of 300 kHz. High-performance GaN transistors operated in parallel can
achieve higher frequency and power with substantially higher efficiency than Si MOSFETs.
The ability to effectively parallel high-performance GaN transistors enables a variety of highcurrent, high-frequency applications.
The objective of paralleling devices is to combine multiple devices so that they can operate
as a single device with lower on-resistance, enabling higher power-handling capability. To
effectively parallel devices, each device in a switch cluster should equally share current
dynamically, and equally divide switching-related losses in steady state. The introduction of
imbalanced in-circuit parasitics between parallel devices leads to uneven power sharing and
degraded electrical and thermal performance, limiting the effectiveness of paralleling [1]. For
high-speed devices such as GaN transistors, the increased switching speeds amplify the impact
of parasitic mismatches [2].
In a GaN transistor-based buck converter, common source inductance (LS) and highfrequency loop inductance (LLoop) have been shown to impact switching speeds and performance significantly, as presented in Section 6.3. For paralleling GaN transistors, these parasitics
must be minimized and balanced to ensure proper parallel operation. Figure 10.11(a) shows the
impact of parasitic imbalance in the high-frequency loop inductance for two parallel GaN
transistors operating at 48 V with various common source inductances. As the difference
between the high-frequency loop inductance increases between the parallel devices, so does
the difference in dynamic current between them, causing electrical and thermal performance
degradation. As the common source inductance decreases, higher switching speeds can be
achieved and the sharing issues become more pronounced.


45

40

35

30

25

20

15

10

5

0


5

0

0 0.2 0.4 0.6 0.8 1 1.2 0 0.1 0.2 0.3 0.4 0.5

**Loop Inductance Difference (nH)** **Common Source Difference (nH)**

(a) (b)


45

40

35

30

25

20

15

10

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
||||||LS=0.10nH|
||||||LS=0.15nH L=0.20nH|
||||||S L=0.25nH|
||||||S|
||||||L=0.50nH|
||||||S|
|||||||
|||||||

|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|||||L=0.3nH D|
|||||L=0.5nH D|
|||||L=0.7nH D L=0.9nH|
|||||D|
||||||
||||||
||||||
||||||


**Figure 10.11** Impact of (a) high-frequency loop inductance (b) common source inductance parasitic
imbalance on transistor dynamic current sharing for a VIN = 48 V, IOUT = 25 A, GaN transistor-based
buck converter with two devices operating in parallel (GaN transistors: EPC 2001)


-----

Figure 10.11(b) shows the dynamic current difference resulting from parasitic imbalance in
the common source inductance for two parallel GaN transistors operating at 48 V with various
high-frequency loop inductances. Similar to loop inductance imbalance, as common source
inductance varies, current sharing worsens. This trend is magnified as loop inductance
decreases and capable switching speeds increase.
To improve the parallel performance of high-speed GaN devices, the parasitic imbalance
contributed by the PCB layout must be minimized. Two different parallel layouts will be
reviewed, each based on an optimal layout, and an assessment given of their ability to provide
parallel performance similar to the optimal single transistor design. Each half-bridge design
contains four devices in parallel for the control switch (T1–4) and the synchronous rectifier
(SR1–4). The design was tested in a buck converter configuration operating with input of 48 V
and output of 12 V with a switching frequency of 300 kHz. In total, eight 100-V EPC2001 GaN
transistors were used to achieve an output power up to 480 W and an output current of up to
40 A.
The first parallel design is shown in Figure 10.12(a) using the paralleling layout techniques
shown in Figure 4.8 in Section 4.5. In this layout the four GaN transistors are located in close
proximity to operate as a “single” power device, with a single high-frequency power loop as
shown in Figure 4.10. As mentioned in Section 4.5, this layout may not be the best design for
paralleling a large number of GaN transistors. The drawbacks of this layout are that the devices
will have imbalanced parasitics, leading to current sharing and thermal issues.
The second parallel design is shown in Figure 10.12(b) and utilizes four distributed highfrequency power loops as was shown in Figure 4.12. This design is expected to provide the
lowest overall parasitics for each device pair and, most importantly, provide the best balancing
of the parasitic elements, ensuring proper parallel operation.
The switch-node voltage waveforms of the synchronous rectifiers for the two designs are
shown in Figure 10.13. The switch-node waveforms for the single high-frequency power loop
design are shown in Figure 10.13(a), the voltage transitions for the innermost and outermost
devices show an almost 2 ns switching time difference, which equates to about 25% of the total
switching time. The voltages were measured using the techniques described in Section 5.4
(specifically Figure 5.20) with individual connection pads for each of the devices. This voltage
difference demonstrates the parasitic imbalance in this PCB layout, which leads to inefficient
paralleling, resulting in current sharing and thermal issues.
The switch-node waveforms for the symmetrical four high-frequency power loop design are
shown in Figure 10.13(b). The voltage transitions for the devices are almost identical,

**Figure 10.12** Four parallel transistor GaN layouts with (a) single high-frequency power loop (b) four
distributed high-frequency power loops


![](GaN-transistors-power-conversion.pdf-204-0.png)

-----

![](GaN-transistors-power-conversion.pdf-205-0.png)

SR1

SR4

**10 V/Div** **5 ns/Div**


(a)

SR4

SR1

**10 V/Div10 V/Div** **5 ns/Div5 ns/Div**

(b)

**Figure 10.13** Switching waveforms of parallel GaN transistors for (a) single high-frequency power
loop (b) four distributed high-frequency power loop designs (VIN = 48 V, VOUT = 12 V, IOUT = 30 A,
fsw = 300 kHz, L = 3.3 μH, GaN transistors control device/synchronous rectifier: 100 V EPC2001)

demonstrating this layout’s ability to balance the parasitics well, thus improving overall
performance by offering better electrical and thermal performance.
The thermal evaluation of the two designs, shown in Figure 10.14, demonstrates the thermal
imbalance of the single high-frequency loop design. Figure 10.14(a) shows that a hot spot will
develop on the devices handling a greatest portion of the power as a result of the parasitic
imbalance. The control switch located closest to the input capacitors, T1, has a maximum
temperature more than 10 °C higher than the control switch device located furthest away from
the input capacitors, T4. For the four distributed power loop design, shown in Figure 10.14(b),
there is a very good thermal balance, with negligible difference in temperature between
devices.


![](GaN-transistors-power-conversion.pdf-205-0.png)

SR4

SR1

**10 V/Div10 V/Div** **5 ns/Div5 ns/Div**


-----

![](GaN-transistors-power-conversion.pdf-206-0.png)

T1 T3

SR1 SR3

T1-4 SR1-4 SRT2 2 SRT4 4


(a) (b)

**Figure 10.14** Thermal measurements of parallel GaN transistors layouts with a (a) single highfrequency power loop (b) four distributed high-frequency power loops (VIN = 48 V, VOUT = 12 V,
IOUT = 30 A, fsw = 300 kHz, L = 3.3 μH, GaN transistors: control device/synchronous rectifier: 100 V
EPC2001)

By offering lower individual parasitics and better parasitic balance, the four high-frequency
loop design is more effective at paralleling. This results in better electrical and thermal
performance, as shown in Figure 10.15. The distributed high-frequency loop design offers a
0.2% gain in efficiency at 40 A, and has an almost constant 10 °C improvement in the
maximum transistor temperature.
The switching waveforms for an optimal PCB design using a single GaN transistor, two
parallel GaN transistors, and four parallel GaN transistors are shown in Figure 10.16. The
parallel designs operate like a single device with lower resistance and slower switching speed in
proportion to the number of devices connected in parallel.
The ability of GaN transistors to increase switching frequencies and achieve higher power
handling through the effective paralleling methods discussed in this section allows for the
exploration of new opportunities in popular applications such as the intermediate bus
architecture (IBA), whose power architecture will be discussed in the next section. Traditionally, IBAs have required isolation to not only provide user safety, but also to reduce the power
handled by the primary devices as the primary current is reduced by the effective turns ratio of
the transformer. A growing number of applications are removing the isolation requirement,
enabling the bulky transformer and complex control circuits to be removed. High-performance
GaN devices, operated in parallel, can handle the higher frequency and power with substantially higher efficiency than Si MOSFETs. Shown in Figure 10.17 is the efficiency comparison
between the 300 kHz parallel buck converter and published performance of state-of-the-art
eighth-brick Si MOSFET-based bus converters. The GaN transistor-based solution offers a


-----

97


96.5

96


95.5

95


94.5

110

100

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
||||4 P|arallel|GaN T||ransis|tors|||
||||||||||||
||||||||Conven Loop Optima|tional Si Design l Four L|ngle oop||
||||||||D|esign|||
||||||||||||


90

80

70

60

50

40

30


2 6 10 14 18 22 26 30 34 38 42
**Output Current (A)**

(a)

Conventional Single
Loop Design

Optimal Four Loop
Design

2 6 10 14 18 22 26 30 34 38

|Col1|Col2|Col3|Col4|(a)|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
||||||C|onventio Loop D|nal Single esign|||
||||||O|ptimal F Des|our Loop ign|||
|||||||||||
|||||||||||


**Output Current (A)**


(b)

**Figure 10.15** (a) Efficiency and (b) thermal comparison for conventional and optimal parallel GaN
transistor designs (VIN = 48 V, VOUT = 12 V, fsw = 300 kHz, L = 3.3 μH, control switch: 4× EPC2001,
synchronous rectifier: 4× EPC2001)


gain of over 2% in peak efficiency and a 50% improvement in power density over the
traditional Si brick converter, assuming a constant power loss limitation.
This section demonstrated the advantages offered by GaN transistors in non-isolated, pointof-load applications ranging from 60 VIN to 12 VIN. These converters are commonly found in
computers, telecommunication systems, handheld electronics, and many other applications. As
shown, GaN transistors enable smaller size and lower power consumption. The increased
switching frequency also enables faster transient response. These new capabilities are
necessary for meeting the demands for next-generation digital loads.


-----

![](GaN-transistors-power-conversion.pdf-208-0.png)

**1x GaN Transistor**

**2x GaN Transistor**

**4x GaN Transistor**

**10 V/Div** **5 ns/Div**


(a) (b)

**Figure 10.16** Switching waveforms of optimal layout with 1, 2, and 4 parallel GaN transistors
(VIN = 48 V, VOUT = 12 V, IOUT = 30 A/(number of GaN transistors) fsw = 300 kHz, L = 3.3 μH, GaN
transistors: control device/synchronous rectifier: 100 V EPC2001)


![](GaN-transistors-power-conversion.pdf-208-0.png)

**1x GaN Transistor**

**2x GaN Transistor**

**4x GaN Transistor**

**10 V/Div** **200 ns/Div**


98

97


96

95


94

93


92

|Col1|Col2|Col3|300 k|Hz eGa|N FET B|uck IBC|Col8|14|W|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||1 Is|50 kHz olated I|Si BC||||||
||I|245 kH solated|z Si IBC|||||||
|||||||||||
|||||||||||


2 6 10 14 18 22 26 30 34 38 42
**Output Current (A)**


**Figure 10.17** Efficiency comparison for conventional Si-based isolated brick DC-DC converter and a
GaN transistor non-isolated design for a fully regulated IBC (VIN = 48 V, VOUT = 12 V)

###### 10.3 Isolated DC-DC Converters


Isolated DC-DC converters are widely used in computing and telecommunication systems as
part of the IBA approach. They are available in a variety of standard sizes, input and output
voltage ranges, and topologies as shown in Figure 10.18. Their modularity, power density,
reliability, and versatility have simplified the isolated power supply market. Since the size of
these “brick” converters is strictly defined, designers are continually innovating ways to
increase their output power density. Although these ideas are numerous and varied, they are all
related to system efficiency. Consider an eighth-brick converter as an example: an eighth-brick
converter must have a dimension of 0.9 inches (2.3 cm) by 2.3 inches (5.8 cm).


-----

48 V±10% 36 V–55 V 36 V–60 V 36 V–75 V

Bus Bus
Converter Converter

Nominal
9.6 V/12 V Regulated 12 V
5:1/4:1

POL POL POL

|Bus Converter|Col2|
|---|---|
|||

|Bus Converter|Col2|
|---|---|
|||

|POL|Col2|
|---|---|
|||

|POL|Col2|
|---|---|
|||

|POL|Col2|
|---|---|
|||


5 V


3.3 V 1.2 V


**Figure 10.18** IBA showing voltage ranges for bus converters

Although there are numerous input and output voltage configurations, topologies, and output
range tolerances (regulated, semi-regulated, and unregulated), they all have a maximum power
loss at full power between 12 W and 14 W. This is a physical limit based on the fixed volume of
the converter and the method of heat extraction. Thus, for an eighth-brick converter that is 90%
efficient (η = 0.9) at full load, the maximum output power (assuming 14 W losses) can be
calculated using the following equation:

η 0.90
POUTMAX  PMAXLOSS ? 1 � η [][ 14 W][ ?] 1 � 0.90 [][ 126 W] (10.1)

If the efficiency can be improved by just 2%, then the output power can be increased to 160 W,
an improvement of 28%. Lower losses of the GaN transistor allow for this increase in output
power.

###### 10.3.1 Hard-Switching Intermediate Bus Converters

The majority of bus converters today use traditional hard-switching bridge topologies
operating in the relatively low frequency range of 150–250 kHz in order to maximize
efficiency. At these lower switching frequencies, the isolation transformer and output inductor
are very bulky and occupy a large portion of the board area. To improve the power density of
the converter, the operating frequency must be increased to process more power through the
inductor and transformer. However, as the switching frequency increases for silicon-based
converters, losses from the MOSFET body diode conduction, reverse recovery, and transistor
switching losses increase, thus limiting the output power capability of the converter. These
losses have forced power density improvements to come from changes in design optimization
and topology, rather than increases in transistor switching frequencies. Fortunately, with the
advent of GaN transistors, designers have the opportunity to overcome the limitations of the
silicon switching device. The lower switching losses and the absence of any reverse recovery
charge of GaN transistors enable higher operating frequencies for higher output power density.


-----

**10.3.1.1** **Eighth-Brick Converter Using GaN Transistors**

To illustrate the improvements that GaN transistors offer in this application, a high-switchingfrequency GaN transistor-based eighth-brick bus converter was constructed. For the eighthbrick converter, a full-bridge primary-side converter with a full-bridge synchronous rectifier
was chosen as shown in Figure 10.19. The actual converter is shown in Figure 10.20 and
compared side by side to a silicon-based converter. To the skilled designer, the significant
amount of “green” space (unfilled PCB area) in the GaN-based converter could be exploited
further to improve efficiency.
Efficiency results for the GaN transistor-based converter compared to the same MOSFETbased brick converter are shown in Figure 10.21. Despite the GaN transistor converter
operating at 33% higher frequency, it is able to produce 15% more output power for the
same power loss. As the GaN transistor-based converter has not been optimized in either
topology, thermal design or switching frequency, further improvement is possible.
Since this initial GaN transistor-based brick comparison, topological developments for even
higher power MOSFET-based eighth-brick converters have continued to squeeze more
performance out of MOSFET-based systems. In Figure 10.22, the output power of three
different generations of regulator eighth-brick converters are plotted versus their switching
frequency. What is clear from this figure is the continuing downward trend in switching
frequency as well as an increase in overall converter loss (given in brackets below each point).
This overall increased converter loss places additional strain on the thermal design of these
converters, which require complex thermal derating curves. Based on FOM advantages and
comparisons of many different topologies, it is assured the GaN transistors will outperform
MOSFETs in each and every hard-switching intermediate bus converter.

**10.3.1.2** **Isolated PoE-PSE Converters**

The power over Ethernet (PoE) standard has been evolving over the last few years. The
main focus is the systematic increase of power with each new class and type. According to
the IEEE 802.3 standard on PoE [3], the power source equipment (PSE) requires an output
voltage of 44–57 V for PoE type 1, and 50–57 V for PoE type 2 (PoE+). It also has to be
capable of delivering 15.4 W (type 1) or 25.5 W (type 2) per port on the PSE Ethernet
switch. For the PSE, the output requires some form of regulation, but tight regulation is not
required. There is also an increase in minimum voltage to account for the increase in
maximum line droop with the increased power level. With 24, 36, or even 48 ports per
Ethernet switch being typical, the total PSE supply power requirement can be as high as
1.2 kW. This drives the need for the higher efficiency and higher power density converters
achievable with GaN.
It is difficult to remove more than 35 W of losses from a typical PoE-PSE half-brick
converter, even with significant airflow or base plate. In Figure 10.23, the resultant output
power that is achievable in a half-brick is plotted versus the required minimum full load
efficiency. Since most commercial half-brick PSE converters already have about 95%
efficiency, even one-half of one percent efficiency improvement is important and can increase
output power by as much as 100 W. As with other brick converters, the most important aspect is
cost per watt ($/W), thus, by increasing brick efficiency and therefore output power with GaN
transistors, the price of the module per watt is reduced.


-----

![](GaN-transistors-power-conversion.pdf-211-0.png)

-----

![](GaN-transistors-power-conversion.pdf-212-0.png)

**SecondarySecondarySecondary** **Trans-Trans-Trans-**

**Side SRSide SRSide SR** **formerformerformer**

**PrimaryPrimaryPrimary**

**Output**

**Side HBSide HBSide HB**

**InductorInductorInductor**

MOSFET Based Brick MOSFET Based Brick
(Top View) (a) (Bottom View)

**PrimaryPrimaryPrimary** **Trans-Trans-**
**Side FBSide FB** **formerformer**

**SecondarySecondary** **Output**
**Side SRSide SR** **InductorInductor**

Primary Side FB


GaN Transistor Based Brick GaN Transistor Based Brick
(Top View) (Bottom View)

(b)

**Figure 10.20** Comparison between the 48 V to 12 V GaN transistor-based eighth-brick converter and
comparable silicon-based converter (a) MOSFET top view (b) MOSFET bottom view (c) GaN transistor
top view (d) GaN transistor bottom view (scale in inches)


96

94


92

90


88

86


84

|Col1|Col2|Col3|Col4|Col5|37|5 kHz G|aN Tra|nsistor|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||250 kH|z MOSF|ET||
||||||||||
|||||||||nsistor nsistor|
|||||36 48|V MOSFE V MOSFE|T 36 T 48|V GaN Tra V GaN Tra|nsistor nsistor|
|||||60|V MOSFE|T 60|V GaN Tra|nsistor|
||||||||||


0 2 4 6 8 10 12 14 16 18

**Output Current (A)**

**Figure 10.21** Efficiency comparison between a GaN transistor and MOSFET-based eighth-brick
converter


-----

500
GaN Transistor
Gen 1

400

at 12 W Loss

300


GaN Transistor
Gen 1

at 16.8 W Loss

MOSFET
Gen 2

MOSFET
Gen 3


200


(16.8 W Loss)

100

0 50 100 150 200 250 300 350

|Col1|Col2|Col3|Gen 1|1 GaN|N Transisto Gen 1|
|---|---|---|---|---|---|
|||a|t 12 W Lo|ss at 16.|8 W Loss|
|||MOSFET||MO|SFET|
|||Gen 1 (12 W Los|s) (13.5|G W Loss) (1|en 2 MO G 6.8 W Los|


**Rated Output Power (W)**


**Figure 10.22** Switching frequency vs. rated output power for different generation MOSFET-based
eighth-brick converters with comparison to GaN transistor-based converter (converter losses at rated
power given in brackets)

It is difficult to compare half-brick PoE-PSE converters because there are a significant
number of variations between current commercial designs. Each manufacturer’s advances in
topology, materials, construction, layout, and other innovations have allowed ever-greater
output power and enabled them to differentiate themselves in the market. With each generation
of power supply, an increase in output power level is achieved as each manufacturer improves
their design in terms of structure, layout, and topology.
A two-phase, interleaved converter design with single-stage conversion was selected for this
GaN transistor demonstration. The design goal was to deliberately push the operating
frequency much higher than current commercial systems to show that GaN transistors could
enable someone skilled in power supply design to develop state-of-the-art next-generation
products with increased efficiency and output power.


97

96

95

94

93

92

91

88

|7|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|
|---|---|---|---|---|---|---|---|---|---|---|---|
|||||G|aN Tr|ansisto|r Conv|erter||||
||C|ommer|cial H|alf-||||||||
||B|rick PS|E Con|verters||||||||
|||||||||||||
|||||||||||||
||||||Minimu|m Re|quired|Efficien|cy|||
|||||No|minal|Half-B|rick Fu|ll Load|Efficie|ncy||
|||||||||||||


0 100 200 300 400 500 600 700 800 900 1000
**Output Power (W)**

**Figure 10.23** Minimum required efficiency for a half-brick converter to achieve the specific output
power (assuming a maximum power loss of 35 W)


-----

For larger brick sizes, such as the half-brick, the resultant output power levels and overall
converter losses are high enough that multiple power devices are usually required for each
switch, both from a thermal requirement and from a minimum available RDS(on) (largest die
size) perspective. Thus, if the converter is split into two converters (each for half the power), the
overall power device count is not affected. The added cost and size of using an increased
number of inductors and transformers is also small, as these components are smaller, and an
interleaving of the power converters generally allows for a reduction in the required output
capacitance. Furthermore, the size and height restrictions of the bricks mean that a single highpower transformer is height limited with a less optimal magnetic path-length than two smaller
transformer cores. The remaining differences, gate drive and control, are likely the determining
factors.
For 48–53 V GaN transistor-based half-brick PSE converter, a phase-shifted full-bridge
(PSFB) converter with a full-bridge synchronous rectifier (FBSR) topology was chosen, as
shown in Figure 10.24 (a more complete schematic is shown in Figure 10.25). Not only does
the interleaving of two phases avoid the complexity associated with paralleling devices, but the
use of two separate converters conceptually allows for phase shedding to improve light-load
efficiency. Efficiency results, showing that light-load efficiency can be improved by at least 2%
for one- and two-phase operation, are plotted in Figure 10.26. Each converter operates at a
250 kHz device switching frequency, resulting in an output ripple frequency of 1 MHz.
Figure 10.27 shows that, with the increase in switching frequency and the relatively small
GaN transistor device size, two of these converters can be constructed within the available
volume constraints. The choice of transformer turns ratio (4:7) means that, at 60 VIN, the
secondary-side winding voltage (not including switching spike) would be about 105 V, and
therefore, 200 V-devices were used on the secondary side with 100 V-devices on the primary
side. Unlike conventional brick designs, the magnetic components are not integrated within the
main PCB, but are separate PCBs. Not only does this reduce the number of layers required for
the main PCB, but it also allows the use of conventional surface-mount inductors for the output


L


53 V/6 A


36 V–60 V

|Col1|C Drive in Gate|Col3|
|---|---|---|

|36 V–60 V C out Drive Drive Drive C Drive in Gate Gate Gate Gate EPC2001 EPC2010 Controller Isolation Feedback|Col2|Gate Drive|C out|
|---|---|---|---|
|||||


Isolation

**Figure 10.24** A 350 W fully regulated, phase-shifted, full-bridge (PSFB) topology, with full-bridge
synchronous rectification (FBSR) using GaN transistors (two 250 kHz converters interleaved for the halfbrick design)


-----

![](GaN-transistors-power-conversion.pdf-215-0.png)

-----

98

97

96

95

94

93

92

91

90

89

88

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
||||||||||
|||38|||||Phase||
||||38|V Two Pha|se|38 V Single|Phase||
||||48|V Two Pha|se|48 V Single 60 V Single|Phase Phase||
|||60|60|V Two Pha|se||||
||||||||||


0 2 4 6 8 10 12 14
**Output Current (A)**


**Figure 10.26** GaN transistor-based, half-brick PSE converter efficiency results showing both singlephase (half the converter powered down) and normal two-phase operation

**Output Output**

**SecondarySecondarySecondary**
**Side FBSRSide FBSRSide FBSR** **InductorInductor** **TransformerTransformer**

**Primary Primary**

**Output CapacitorsOutput CapacitorsOutput Capacitors**

**Side HBSide HB**

**InputInputInput** **Micro** **BiasBiasBias** **CTsCTsCTs**

**Capacitors Capacitors** **ControllerControllerController** **SupplySupplySupply**


**SecondarySecondarySecondary**
**Side FBSRSide FBSRSide FBSR**


![](GaN-transistors-power-conversion.pdf-216-0.png)

**Output Output**
**InductorInductor** **TransformerTransformer**

**Output CapacitorsOutput CapacitorsOutput Capacitors**

**BiasBiasBias** **CTsCTsCTs**

**SupplySupplySupply**

**Output Output** **CapacitorsCapacitorsCapacitors**

**Output Output Output** **TransformerTransformerTransformer**

**InductorInductor**


MOSFET Based Brick
(Top View)


![](GaN-transistors-power-conversion.pdf-216-0.png)

**SecondarySecondarySecondary**
**Side FBSRSide FBSRSide FBSR**

**Primary Primary**
**Side HBSide HB**

**InputInputInput** **Micro**

**Capacitors Capacitors** **ControllerControllerController**

**PrimaryPrimaryPrimary**

**Side HB Side HB**

**SecondarySecondarySecondary**
**Side FBSRSide FBSRSide FBSR**


MOSFET Based Brick
(Bottom View)


(a) (b)

**Figure 10.27** GaN transistor-based 48 V to 53 V, half-brick PSE converter (a) top view (b) bottom view
(scale in inches)


-----

**Table 10.2** Comparison of commercial half-brick PSE converters


Device switching
frequency (kHz)
(estimated[a])


Output
ripple
(kHz)


Output
voltage
(V)/power
(W)


Conversion Parallel
stages converters
per stage


Datasheet
frequency
(kHz)


Converter A 53/400 2 1/2 300/300 150[a] 300
Converter B 50/600 2 2/2 120/240 120[a] n/a
Converter C 53/424 1 1 270 135 270
Converter D 54/550 1 1 275 138 275
Converter E 54/550 1 1 140 140 280
GaN 53.5/700 1 2 250 250 **1000**
transistor
prototype

_a Frequency estimated based on data sheet graphs._

filters. The converter was constructed using an eight-layer, two-ounce copper thickness per
layer PCB. The transformer windings were created by laminating two eight-layer PCBs
together (in parallel) within the winding window.
The GaN transistor-based half-brick PSE converter can be compared with similar 48–53 V
fully regulated commercial half-brick converters. These commercial converters span a range of
topologies and configurations as listed in Table 10.2. To emphasize how the GaN transistorbased prototype compares to these converters, two products (B and D in Table 10.2) have been
selected to highlight the overall results.
Converter D is a conventional single-stage, single-transformer converter with a similar
topology to the GaN transistor-based converter (although the GaN transistor prototype has two
parallel converters). The efficiency and power loss comparisons in Figures 10.28 and 10.29
show the light-load efficiency advantage that is possible with a lower switching frequency.
Losses can be improved at light load through careful design of the core losses and leakage
inductance. In the GaN transistor-based converter, the core was designed to minimize leakage
inductance and switch at 75% higher switching frequency, resulting in lower light-load
efficiency produced by additional magnetic losses. As the load increases, the benefits of
GaN transistors become apparent, with the efficiencies becoming similar at about 50% load and
the GaN transistor-based prototype producing 25% more power at full load for a similar total
converter loss.
The second commercial half-brick, Converter B, used for comparison has a two-stage
approach. Although the two-stage approach is different from the GaN transistor approach, both
have the output power split into two separate converters, operating in parallel. The advantages
of the two-stage approach is that it allows efficiency optimization of the unregulated isolation
stage since it operates at a fixed duty cycle and voltage, regardless of converter input voltage.
In addition, the controlled input and output voltages allow the use of lower voltage rated
devices with better FOMs. The disadvantages are additional conduction losses for the two
stages, and increased complexity and component count.
The efficiency comparison between the GaN transistor prototype and the two-stage
converter is shown in Figure 10.30. This clearly shows the optimization process that has
gone into Converter B as the peak efficiency is achieved at the nominal input of 48 V. The


-----

98

97

96

95

94

93

92

91

90

89

88

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||250|kHz GaN T|ransistor||
|140|kHz MOSFE|T||||700 W||
|||||55|0 W|||
|||||||||
|||||||||
|||||||||
||||38 V|GaN Transist|or 38 V|MOSFET||
||||48 V 60 V|GaN Transist GaN Transist|or 48 V or 60 V|MOSFET MOSFET||
|||||||||
|||||||||


0 2 4 6 8 10 12 14

**Output Current (A)**

**Figure 10.28** Efficiency comparison between half-brick PSE converters showing a GaN transistorbased prototype vs. Converter D – a commercial MOSFET-based solution


distinctions in topology are highlighted best by comparing the 38 V (low-line) input voltage
results: Since the two-stage circuit employs a boost regulation stage, this is actually a worstcase condition (conduction loss increased, with no appreciable reduction in switching loss),
while for the traditional single-stage approach, low-line is the best case, as switching loss is
minimized. The two-stage converter’s power losses at low-line reach almost 50 W, about

35


30

25


20

15


10

5


0

|Col1|Col2|Col3|140 kHz M|OSFET|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|||||25|0 kHz GaN|Transistor||
|||||||||
|||||||||
||||38 V 48 V|GaN Transisto GaN Transisto|r 38 V r 48 V|MOSFET MOSFET||
||||60 V|GaN Transisto|r 60 V|MOSFET||
|||||||||


0 2 4 6 8 10 12 14

**Output Current (A)**

**Figure 10.29** Power loss comparison between half-brick PSE converters showing a GaN transistorbased prototype vs. Converter D


-----

98

97

96

95

94

93

92

91

90

89

88

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
|||||250 kH|z GaN FET|Transistor||
|||||||700 W||
||||||600 W|||
||||12|0 kHz MOS|FET|||
|||||||||
|||||||||
||||38 V|GaN Transist|or 38 V|MOSFET||
||||48 V|GaN Transist|or 48 V 75 V|MOSFET MOSFET||
||||60 V|GaN Transist|or|||
|||||||||


0 2 4 6 8 10 12 14


**Output Current (A)**

**Figure 10.30** Efficiency comparison between half-brick PSE converters showing a GaN transistorbased prototype vs. Converter B – a two-stage MOSFET-based solution


double that of the GaN transistor converter under the same conditions, with the 75 V (high-line)
input losses 15% higher than the GaN transistor converter, as shown in Figure 10.31.
With the emergence of GaN transistors, designers have the opportunity to overcome the
limitations of the aging silicon MOSFET and reverse the backward trend of reducing switching
frequency in hard-switching applications to increase the output power density of fixed

50

45

120 kHz MOSFET

40

35

30

25

20

250 kHz eGaN Transistor

15

38 V GaN Transistor 38 V MOSFET

10


5

0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
||||120||kHz MOSF|ET||
|||||||||
|||||||||
|||||||||
|||||||||
||||||25|0 kHz eGaN|Transistor|
|||||38|V GaN Transi|stor 38|V MOSFET|
|||||48|V GaN Transi|stor 48|V MOSFET|
||||60|60|V GaN Transi|stor 75|V MOSFET|
|||||||||


0 2 4 6 8 10 12 14

**Output Current (A)**

**Figure 10.31** Power loss comparison between half-brick PSE converters showing a GaN transistorbased prototype vs. Converter B


-----

S1

S2


VIN


4:1

CR LR CO

LM

**Figure 10.32** LLC resonant converter

|IN + _|Q 1 4: C R L R Q 2 L M|
|---|---|

|Col1|Col2|
|---|---|


form-factor bus converters. The designer can rely upon the lower losses and higher switching
frequency capability of the GaN transistor to accomplish much higher power density bus
converters.

###### 10.3.2 A 400 V LLC Resonant Converter

The LLC resonant converter, shown in Figure 10.32, is a popular topology in 400 V DC-DC
front-end converters. The LLC converter offers reduced switching loss by providing ZVS, and
reduced current at turn-off in the primary-side devices, and ZCS on the secondary devices [4,5].
These benefits are similar to the resonant 48 V topology discussed in Chapter 7. The reduction
in switching losses makes the LLC resonant converter suitable for high-switching frequencies.
The main advantages of GaN transistors in high-frequency LLC resonant converters are (a)
the reduced gate charge, providing lower gate drive losses, and (b) the reduced output charge
that enables a reduction in ZVS dead-time or required ZVS current. To evaluate the
performance improvements possible with GaN transistors in higher voltage resonant applications, the characteristics of 600 V GaN cascode transistors and Si MOSFETs are compared in
Table 10.3.
From Table 10.3, it can be seen that high-voltage GaN transistors offer a significant
reduction in the key FOMs for resonant converters as discussed in Chapter 7. The GaN

**Table 10.3** Device comparison between GaN transistor (TPH3006PS) and Si MOSFET (FCP190N60E)
primary-side devices for 400 V LLC resonant converter

Parameter GaN transistor[a] Si MOSFET[b] FOM ratio

Voltage rating (VDSS) 600 V 600 V
RDS(on) 150 mΩ at 8 V 160 mΩ at 10 V
QG 9.3 nC at 8 V[a] 63 nC at 10 V
QOSS at 480 V 52.8 nC[a] 85.4 nC[b]

QGRDS(on) 1395 pCΩ 10,080 pCΩ 7.23 × reduction
QOSSRDS(on) 7920 pCΩ 13,664 pCΩ 1.73 × reduction
FOMSS (QOSS + QG)RDS(on) 9315 pCΩ 23,744 pCΩ 2.55 × reduction

_a All values calculated from TPH3006PS datasheet and [6]._
_b All values calculated from FCP190N60E datasheet._


-----

transistor delivers an improvement of more than seven times in gate charge FOM over the Si
MOSFET, resulting in lower gate driving losses in high-frequency designs. The GaN transistor
has a 1.73 times improvement in output charge FOM over the Si MOSFET, resulting in lower
conduction losses offered by reduced ZVS transition times and lower ZVS currents. The
resonant- and soft-switching FOMSS is around 2.55 times lower for a GaN transistor than for an
Si MOSFET, and this will correlate directly into lower losses and improved high-frequency
LLC performance [7]. For a 400 VIN to 12 VOUT, 300 W LLC converter, operating at 1 MHz,
GaN transistors demonstrated a 1% gain in full-load efficiency and an almost 5% gain at 15%
load when compared to state-of-the-art Si MOSFETs [8].
This section has shown the value of GaN transistors in isolated DC-DC converters which are
widely used in computing and telecommunication systems as part of the IBA approach. Since
the size of these “brick” converters is strictly defined, an increase in efficiency brought about
with the use of GaN transistors will significantly increase efficiency, output power, and system
power density.

###### 10.4 Class-D Audio

Class-D audio amplifiers using GaN transistors, which have lower conduction losses, faster
switching speed and zero reverse recovery losses, provide an efficiency improvement over
MOSFETs. In addition, the higher efficiency can, in many cases, eliminate bulky and expensive
heatsinksthataddtosystemcostsandsize.Beyondimprovedefficiency,however,GaNtransistors
provideimprovedsonicquality,criticalinaudioapplications.Sincetheactualsoundinterpretation
can be subjective, the use of measurable quantities such as total harmonic distortion (THD) and
damping factor (DF) are used to validate the improvements provided by GaN transistors.

###### 10.4.1 Total Harmonic Distortion (THD)

Class-D audio amplifiers are buck converters that operate with both positive and negative
currents and a wide-ranging duty cycle. The switching-node voltage will either commutate at
the turn-off of one device, or at the turn-on of the other, as shown in Figure 10.33 for a
sinusoidal output. The variability in device commutation, which is due to the polarity of the

Sinusoidal Waveform

HS Rising and without Dead-Time
Falling Edges Distortion

High Side Dead-Time

HS

Both Falling Edges/ZVS

LS

LS Rising and

Low Side Dead-Time

Falling Edges

**Figure 10.33** Distortion of a sinusoidal output due to changes in output pulse width with duty cycle and
current

|Sinusoidal Waveform HS Rising and without Dead-Time Falling Edges Distortion|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
||||Both Falling|Edges/ZVS||
|LS Rising and Falling Edges||||||


-----

+V

0


–V


Crossover
Decreasing Distortion
Dead-Time

|Col1|Col2|Col3|Col4|Decreasing Dead-Time|Col6|
|---|---|---|---|---|---|
||Decreasing Dead-Time|||Crossover Distortion||
|||||||


0% 50% 100%


**PWM Input Modulation Index**

**Figure 10.34** Theoretical Class-D converter input-to-output relationship showing crossover distortion
regions

device current, results in crossover distortion, as shown in Figure 10.34. To put the impact of
distortions on audio quality into perspective, a 0.01% THD corresponds to a 10 mV error on a
100 VDC bus, or 0.25 ns change in pulse width at a switching frequency of 400 kHz [9].
To minimize this distortion, the amount of dead-time must be minimized. With the slower Si
MOSFET, this value is typically no less than 25 ns [10]. Using GaN transistors, these deadtimes can be readily reduced to around 5 ns, thus offering a significant reduction in open loop
THD. Other important factors that affect THD are body diode reverse recovery, switch-node
ringing and overshoot, device turn-on and turn-off delay, and finite rise and fall times [9]. For
each and every one of these factors, the GaN transistor offers a reduction that directly relates to
a corresponding decrease in THD.


###### 10.4.2 Damping Factor (DF)

Another important performance parameter in Class-D audio is damping factor. This is the ratio
of the speaker, or load impedance (ZLoad), to the Class-D amplifier output, or source impedance
(ZSource), and mathematically can be written as:


DF [Z][Load] (10.2)

ZSource

A higher damping factor is better. As the speaker and amplifier form a voltage divider network,
any significant variation in the output voltage due to changes in output current will cause
distortion, with a higher damping factor minimizing distortion. Although the damping factor is
determined mainly by the passive filter components and control loop gain, using a switching
device with lower on-resistance will improve the damping factor directly. Since Class-D is a
hard-switching converter, the optimum die size is a tradeoff between conduction and switching
losses. Selecting the optimum die size GaN transistors will result in a lower on-resistance


-----

device with both lower switching loss and lower conduction loss than a similarly optimized
MOSFET [11]. Thus, the resulting GaN-based amplifier will have with a better damping factor.

###### 10.4.3 Class-D Audio Amplifier Example

Using GaN transistors in Class-D amplifiers offers an improvement in THD, DF, and efficiency
over MOSFET designs. To illustrate some of these advantages, a 150 W into 8 Ω, or 250 W into
4 Ω, stereo Class-D amplifier, using two bridge-tied load (BTL) outputs from a ±27 V split
supply, was built for one channel as shown in Figure 10.35 [12]. A photo of the complete
converter is shown in Figure 10.36.
The total harmonic distortion plus noise (THD+N), which includes the impact of noise floor,
is shown in Figure 10.37. The light-load THD+N is dominated by noise related to the

+HV

–HV

Input Processing and Drivers

**Figure 10.35** Diagram for a single channel of a BTL Class-D amplifier with split supply (±HV)

**Figure 10.36** Complete Class-D converter showing output power stage and half-bridge circuits
including GaN transistors and gate drivers. No heatsink is required up to 250 W into 4 Ω per channel


![](GaN-transistors-power-conversion.pdf-223-0.png)

-----

1

0.5


dx = 120.3W dy = 0.02461%


0.2

0.1

0.05


0.02767


0.02

0.01

0.005


0.00306


0.002 Power Stage Distortion

0.001

60m 100m 200m 500m 1 2 5.079 10 20 125.4

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|Col27|Col28|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
||||||||||||||||||||||Outp|ut Fi|lter|D|is|tor|tion|
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||N|oise Fl|oor||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||
||||||||||||||||||||||Po|wer|St|ag|e|Di|stortion|
|||||||||||||||||||||||||||||


**Output Power (W)**

**Figure 10.37** THD+N vs. output power at 1 kHz, ±27 V supply, into 8 Ω load. The minimum THD+N
is 0.003% at 5 W, and 0.028% at 125 W


pre-amplifier and control loop rather than the GaN transistor-based power stage. Similarly,
heavy-load THD+N is dominated by the distortion in the passive output filters, as they are not
compensated for within the feedback control loop.
To determine the dynamic noise ratio (DNR) of the GaN transistor amplifier stage, the preamplifier volume is turned down during measurement to minimize its noise impact. The
resultant DNR is 110 dB when referenced against a full-load power of 168 W [12].
Since the GaN transistor switch-node commutation occurs in around 1–2 ns, and the nominal
dead-time is set to around 5 ns, it is possible to achieve these THD results without cross
conduction (shoot-through). The resultant power stage efficiency, including output filter, is
around 96% @ 150 W into 8 Ω and 91.5% @ 250 W into 4 Ω, as shown in Figure 10.38, and
enables the converter to operate without heatsink over the entire load range.

100


90

80

70

60

50

40

30

20

10

0


0 50 100 150 200 250 300

**Output Power (W)**

|Col1|Col2|Col3|4Ω|Col5|8Ω|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||No Heatsi|nk Required|
|||||||
|||||||


**Figure 10.38** Power stage efficiency vs. output power into 4 Ω and 8 Ω loads


-----

Lower conduction losses, faster switching speed, and zero reverse recovery losses made
possible by high switching-speed GaN transistors result in a step forward in designing Class-D
audio amplifiers with superior audio performance.

###### 10.5 Envelope Tracking


The concept of envelope tracking (ET) for RF power amplifiers is not new. As global
communication demands continue to increase, the efficiency of the mobile infrastructure
struggles to keep up. The continuous drive to boost cell phone battery life, base station energy
efficiency, and output power from very costly RF transmitters has placed the spotlight on ET as
the means to improve RF power amplifier (PA) system efficiency. There are many papers on
the basics and advantages of envelope tracking [13–17]. The key parameter on which to
concentrate is a PA’s peak-to-average power ratio (PAPR) requirements [13]. This PAPR has
increased continuously as a means of squeezing more digital bandwidth out of RF amplifiers.
As shown in Figure 10.39, it is possible to achieve peak PA efficiencies as high as 65% with a
fixed supply, but given PAPRs as high as 10, such as used in 4G LTE networks, the average
efficiency is likely to be lower than 25%. Through modulation of the PA supply voltage, this
can be improved to over 50%, essentially doubling the efficiency and reducing by two-thirds
the power losses. This not only reduces power consumption, but also lowers the cost of
operation, cooling requirements, and system size [18].
In practice, however, the wide bandwidth of the envelope signal (a 4G LTE signal requires a
modulation bandwidth of 20 MHz [19]) makes the tracking implementation difficult due to a
degradation of efficiency of the modulating power supply with increasing bandwidths and
switching frequency [20]. Thus, developing a high-frequency, high-efficiency modulator is
required for realizing a practical ET solution. With the commercial availability of highperformance GaN transistors, a high-frequency high-efficiency envelope tracking power
delivery system is now viable. Previous high-frequency buck converters using GaN transistors [21] realized impressive high-frequency buck converter efficiency results, as shown in
Figure 10.40. Similar work [22] shows improvement of 20–30% in buck converter efficiency
using GaN transistors versus silicon MOSFETs. Despite the excellent high-frequency

Envelope Tracking Supply


70

60

50

40

30

20

10

0

|Col1|Col2|Col3|Col4|Aver|age P|ower|Pea|k Pow|er|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
||Energy dis as he|sipated at||||||||
|||||||||||
|||||||||||
|||||||||||
|||||O Pro|utput babili|ty||||


**Output Power (dBm)**

**Figure 10.39** Conceptual PA efficiency vs. output power for fixed supply and ET operation


-----

98

97

96

95

94

93

92

91

90


EPC2007

8

6

4 MHz Efficiency

4

1 MHz Efficiency

4 MHz Losses 2

1 MHz Losses

0

0 50 100 150 200 250 300 350


16

14

12

10

|Col1|Col2|Col3|Col4|Col5|E|PC2001|Col8|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
||||EPC2|007||||
|||||||||
|||||||4 MHz E|fficiency|
|||||||1 MHz E 4 MHz L|fficiency osses|
|||||||1 MHz L|osses|


**Output Power (W)**

**Figure 10.40** Efficiency and loss results for EPC2001 and EPC2007 GaN transistor buck demonstrators
operating both at 45 VIN, 22 VOUT [21]


performance, the device active area in these early implementations was relatively large and not
optimal for base station applications. A more practical ET solution requires lower power levels
per phase at much higher frequencies. This need for smaller active area GaN transistors was
addressed through the development devices that are one order of magnitude smaller (higher
RDS(on)) than the devices used in [21,22].

###### 10.5.1 High-Frequency GaN Transistors


To support ET supplies requires devices with lower capacitance and higher on-resistance. Not
only does this require an excellent hard-switching FOM, but also layout and package
characteristics that maximize in-circuit performance. Such devices are available as wafer
level chip scale packaged (WLCSP) GaN transistors [23] with the device pin-out shown in
Figure 10.41. The FOMHS in Figure 10.42 shows that the 65 V rated EPC8005 [24] compares
favorably with similar on-resistance state-of-the-art 30 V MOSFETs. From Figure 10.42, it can
be seen that the EPC8005 has about half the FOMHS of MOSFETs, while its voltage rating is
more than double. For reference, the 100 V GaN transistors used in [21] are comparable to the
best 30 V MOSFETs.

**Source**
**Source**

**Substrate**

**Drain**

**Figure 10.41** The EPC8000 GaN transistor-series WLCSP die showing the bump side with pin-out
locations


![](GaN-transistors-power-conversion.pdf-226-0.png)

**Source**
**Source**

**Substrate**

**Drain**


-----

50

45

40

35

30

25

20

15

10


5 GS2

0 QGD

**Figure 10.42** Hard-switching FOM comparison between GaN transistors and similar BGA Si
MOSFETs

|230 mΩ|Col2|Col3|24 mΩ|Col5|Col6|90 mΩ|Col8|200 mΩ|Col10|71 mΩ|
|---|---|---|---|---|---|---|---|---|---|---|
|||||||30 V||BGA|||
||||||||30 V|BGA|||
||||||||MOSF|ETS||Q GS2|
||||||||||||
||65 V GaN|||100 V GaN|||||||
||FET|||FET||||Q GS2|||
||||||||||||
|||||||||||Q GD|
||||Q GS2|||Q|||||
|||||||GS2||Q GD|||
|Q GS2|||Q GD|||Q GD|||||
|Q GD|||||||||||


Although a significantly better FOMHS is important, these devices also have a number of
features that further improve in-circuit performance. These can be summarized as follows:

1. Complete dv/dt immunity: As discussed in Chapter 3, an important metric for dv/dt
immunity is the Miller ratio, which is an indicator of how susceptible gates are to turning
back on at high dv/dt [25]. The Miller ratio (QGD/QGS1) is reduced to below 0.4, well below
the requirement of 1.0.
2. Reduced QGD: As noted in Section 6.2.1.1, QGD is the main device parameter that
determines switching losses. It has been reduced to almost half that of a similarly scaled
GaN transistor used for higher power DC-DC converters, and, as we learned in Section
6.2.1.1, this is the main device parameter that determines voltage-related switching losses.
3. Separate gate return (source) connection: The separate source connection for the gate drive
circuit limits the common source inductance to inside the device itself. As discussed in
Chapters 4 and 6, the reduction in common source inductance is critical to high-frequency
switching performance.
4. Wider parallel gate drive connections: The wider connections for the gate circuit connection
significantly reduce the inductance of the connection to the gate circuit. Furthermore,
placing the gate and separate gate return terminals parallel to each other allows for lowinductance PCB interconnection to the driver. This is accomplished by routing both return
terminals through wide conductors on adjacent PCB layers as shown in Figure 10.42,
following the optimum loop layout design first presented in Chapter 4 [26].
5. Parallel drain and source connections, orthogonal to gate loop: As with the gate drive
connections above, parallel connection pads allow wide interconnection traces for improved
PCB layout with minimized power loop inductance. The orthogonal layout of these two
loops also reduces the interaction of the gate circuit current with the drain circuit current.

The half-bridge layout in Figure 10.43 shows that gate loop (a) and power loop (b) currents
(arrows) flow in opposite directions on adjacent layers, to help reduce the overall loop
inductances through magnetic flux cancellation, as discussed in Chapter 4. Furthermore, these


-----

Vias to Next Layer To BUS Caps Vias to Next Layer

Supply Switch
Node To Gate


Top Gate


Gate
Current
Orthogonal
to Drain
Current


FET Outline FET Outline


Bottom
Gate


Ground

|To BUS Caps Supply Vias to Next Layer|Col2|
|---|---|
|Supply Drain Sub Return Gate op Gate Gate Source S T Outline Return Drain Sub ottom Gate ate Gate Source S||
||Drain Sub Return Gate Gate Source S|
|T Outline||
|||
||Return Drain Sub Gate Gate Source S|
|ottom ate||

|Optimum Power Loop Return as to Next Layer|Col2|
|---|---|
|||
|Drain Sub Return Gate Gate Source S||
|||
|Drain Sub Return Gate Gate Source S||


(a) Top (Component) Layer (b) First Inner Layer

**Figure 10.43** Optimal layout design for a half-bridge topology using an EPC8000-series GaN transistor.
(a) top (component) layer and (b) first inner layer

traces are kept as wide as possible, while the interlayer distance between these layers is
minimized, both of which will further reduce loop inductance.

###### 10.5.2 Envelope Tracking Experimental Results

To demonstrate the capability of GaN transistors in ET applications, a 10 MHz-buck converter
operating at a fixed input of 42 V and an output voltage of 20 V was constructed, as shown in
Figure 10.44. The turn-on switching waveform for the 10 MHz-buck converter is shown in
Figure 10.45. A significant bump in the rise time can be seen during the current commutation
interval, while the dv/dt interval shows a slew rate as high as 75 V/ns, resulting in an overall rise
time of around 1 ns. The efficiency curve, shown in Figure 10.46, indicates a peak efficiency of
89% at an output power of 35 W.

###### 10.5.3 Gate Driver Limitations

Analysis of the power loss breakdown of this converter [27] shows that a significant portion of
the overall converter losses can be attributed to the gate driver and related components, as
shown in Figure 10.47. The most significant of these are the internal gate driver IC (presented
in Chapter 3) capacitance between the high-side floating driver and ground (which is connected

**Figure 10.44** PhotooftheevaluationboardshowingtheEPC8005[24]devicesandLM5113gatedriver[47]


![](GaN-transistors-power-conversion.pdf-228-0.png)

-----

![](GaN-transistors-power-conversion.pdf-229-0.png)

No Measureable
Overshoot

dv/dt Interval

di/dt Interval

Rise Time ~1.0 ns


Measure
Value
Status


P1: duty (C2) P2: freq (C3) P3: rise (C3)


2 ns/div and 10V/div

**Figure 10.45** Hard-switching switch node waveform of the EPC8005 [24] showing rising edge rise-time
of around 1 ns (fsw = 10 MHz, VIN = 42 V, VOUT = 20 V, Iout = 1 A)


90

85


6

5


80

75


4

3


70

65

|Col1|Col2|Col3|Col4|Col5|10 MHz|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
||||||||EP|C8005|


0 5 10 15 20 25 30 35 40


2

1


**Output Power (W)**

**Figure 10.46** Efficiency vs. output power for a hard-switching GaN transistor-based (EPC8005 [24])
buck converter (fsw = 10 MHz, VIN = 42 V, VOUT = 20 V)


-----

5

4


3

2


1

0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|
|---|---|---|---|---|---|---|---|---|---|---|
|||||||||C o n|d u c tio n||
|||||||||S|w itc h in g||
||||||||||||
|||||||G a|te C h a rg|e a n d|M a C g O S n S e|tic s|
|||||||G|a te D riv|e r R e|la te d L o|s s e s|


0 4 8 12 16 20 24 28 32 36 40


**Output Power (W)**

**Figure 10.47** Breakdown of estimated loss components for a hard-switching GaN transistor-based buck
converter showing impact of the gate driver on overall losses (fsw = 10 MHz, VIN = 42 V, VOUT = 20 V)

in parallel with the lower device COSS, and the associated losses were discussed in Chapter 6),
and the reverse recovery losses of the bootstrap diode used to generate the floating high-side
power supply. With improvements in the gate driver design and bootstrap diode, these
additional driver-related losses can be mitigated, with the potential converter efficiency
approaching that shown in Figure 10.48.


95

90


6

5


85

80


4

3


75

70


2

1


65 0

0 5 10 15 20 25 30 35 40

|Col1|Col2|Col3|Col4|Calculate|d Poten|tial Effic|iency|
|---|---|---|---|---|---|---|---|
|||||||||
|||||||||
|||||a te D ri|v e r L o s|s e s||
|||R e d|u c tio n in|G||||
|||||||||


**Output Power (W)**

**Figure 10.48** GaN transistor-based buck converter efficiency and power loss vs. output power
showing actual results (dashed lines) and calculated values based on potential improvements in driver
capacitance, bootstrap diode recovery, and internal driver switching losses (fsw = 10 MHz, VIN = 42 V,
VOUT = 20 V)


-----

Gallium nitride is an enabling technology for both ET converters and wide bandwidth RF
power amplifier designs.

###### 10.6 Highly Resonant Wireless Energy Transfer

Wireless energy transfer enables the remote powering and charging of the myriad of battery
powered devices that have infiltrated our daily lives. Recent advances in the basic technology
of wireless energy transfer lead to the promise of widespread adoption as the means of charging
our cell phones, tablets, and laptops, with the likelihood that this expansion will continue into
our homes as a replacement for the ubiquitous wall socket and extension cord. Although most
charging applications today are low power, less than 50 W, the technology does allow for
higher power levels into several kW. For example, auto manufacturers are already commercializing electric vehicle charging using wireless energy transfer [60].
Two main wireless standards have emerged, the Wireless Power Consortium (WPC) [28],
characterized by tight coupling and alignment between the source and device units, and the
Alliance for Wireless Power (A4WP) [29], characterized by loose coupling between the source
and device units. The discussion in this section will focus on the loosely coupled 6.78 MHz
unlicensed industrial, scientific and medical (ISM) band wireless energy transfer solution based
on the A4WP standard. This loosely coupled approach eliminates the need for close alignment
between the sending and receiving units. Cell phones can be charged while remaining in the
user’s pocket. Tablets can be charged by being placed anywhere on a desktop equipped with a
thin sending coil. Conceivably, transmitting coils could be located in floor tile in order to power
common household appliances. Electric vehicles can be charged by simply driving over a
charging mat located on the floor of the garage.
Non-communication operation in the 6.78 MHz ISM band is governed by regulatory
standards for intentional radiators, which places restrictions on the radiated energy. Of
particular importance to wireless energy transmission is the bandwidth limit of ±15 kHz
for the carrier [30]. This limits designers to topologies that can operate with a fixed frequency,
and any amplitude modulation must be limited to within the bandwidth restrictions and system
component tolerances.
The mobile energy market further places demands on the design of a wireless energy transfer
system,including: low profile forboth thesourceanddeviceunits, high energyefficiency,ease of
use, high robustness to changes in operating conditions, such as load and coupling variations,
and in some cases, being lightweight. These requirements yield a few candidate topologies that
can be considered for wireless energy transfer: voltage-mode Class-D (VMCD) [31–33], currentmode Class-D (CMCD) [32,33], single-ended Class-E (SECE) [33], and the differential-mode
Class-E (DMCE) [34]. The benefits that GaN transistors bring to wireless energy transfersystems
using the VMCD and SECE approaches will be the focus of the next section. To simplify the
discussion, large variations in spacing and alignment between the source and device units,
and immunity to unexpected conditions such as solid metal or magnetic material proximity
will be excluded.
The wireless energy transfer system architecture is centered on the use of flat spiral coils to
generate a magnetic field that is used to transfer the energy from the source to the device. This
structure forms a transformer with low coupling coefficient, as shown in Figure 10.49. The
equivalent circuit can be used to design the system based on physical design parameters and
can be used to predict the performance of the wireless energy transfer system.


-----

Coil Set

Lsrc Ldev

Rs Lk Lk Rd


a:1


Ideal
Transformer

**Figure 10.49** Wireless energy transfer coils (left) with equivalent transformer circuit (right)

This transformer has a leakage inductance (Lk) that can be significantly larger than the
magnetizing inductance (Lm). An analysis of the transformer model under these conditions
reveals that the primary-side leakage inductance almost solely determines the efficiency of
energy transfer to the secondary side [35]. To overcome the leakage inductance, use is made of
resonance to increase the voltage across the leakage inductance, and hence the magnetizing
inductance [29,36,37], with a resulting increase in power delivery.
To simplify the discussion, a schematic reduction to a single element, ZLoad, will be
considered as shown in Figure 10.50, where ZLoad represents the DC-load resistance (RLoad),
DC-smoothing capacitor (Cout), rectifier, device matching (Cdevs, Cdevp, Ldevs), device coil
(Ldev), and source coil (Lsrc).
The subsequent design and discussions of the various topologies will assume this equivalent
circuit represented by ZLoad. Only losses associated with this portion of the circuit will be
considered for overall system efficiency, but not in the evaluation of the performance
comparison between the various topologies.

Cdevs Ldevs

Lsrc Ldev Cdevp Cout

Rload Zload

Coil Set

**Figure 10.50** Single element reduction of the wireless energy transfer system that includes the source
coil, device coil, device matching, rectifier, DC capacitor, and load resistor

|Col1|L L src dev|L C devs devs C C out devp R|
|---|---|---|


-----

###### 10.6.1 Design Considerations for Wireless Energy Transfer

Based on the wireless energy transfer system requirements, the main power circuit needs to be
efficient enough to not require a heatsink. The loss calculations and measurements will focus
on both active and passive components. For passive elements, such as inductors and capacitors,
equivalent series-resistance values at 6.78 MHz will be determined either from s-parameter
data provided by the manufacturer or by measurement. For the active devices, the losses will
include the energy required to drive the gate.
A traditional voltage-mode Class-D wireless energy transfer system is the simplest
topology and has been demonstrated previously with load power up to 15 W [38,39].
The circuit for this approach is shown in Figure 10.51 along with the ideal waveforms.
Owing to the high switching frequency and device COSS, the load ZLoad and Cs must be tuned
to be inductive at 6.78 MHz, and therefore, enable ZVS and corresponding reduction in
COSS losses.
The matching circuit (Lmat and Cmat) also functions to increase the voltage to the loadresonant circuit (Cs and ZLoad), which can be advantageous when limits are placed on the
input voltage magnitude, given that the average voltage at the output of the amplifier
(switch-node) is half the supply voltage (VDD). However, the matching inductor will carry
the full current of the load, and therefore will have high associated losses. Furthermore, the
circuit is sensitive to load resistance variation, which can be due to load or coupling changes,
as the matching network becomes an integral part of the tuned-resonant circuit. This can shift
the ideal operating inductance point needed to maintain proper ZVS. Another disadvantage
of the voltage-mode Class-D topology is the need for a high-side gate driver. Using the
bootstrap supply approach has limits for the maximum input capacitance of the devices, as
the low-side device on-time is very short for charging the bootstrap capacitor, and the
capacitance of the bootstrap circuit itself can even contribute to discharging the bootstrap
capacitor, as discussed in Section 10.5.3.

VDD

Q2

Lmat CS V/I

VDD

Q1 Cmat ZLoad VDS ID

50% Time

Ideal Waveforms

(a) (b)

**Figure 10.51** (a) Traditional voltage-mode Class-D wireless energy circuit (b) with ideal waveforms


-----

###### 10.6.2 Wireless Energy Transfer Examples

In this section, two alternative topologies suitable for wireless energy transfer using GaN
transistors will be analyzed: (1) a ZVS voltage-mode Class-D and, (2) a single-ended Class-E.
The target is 30 W load power without the need for forced air-cooling or a heatsink. Both
amplifier topologies fall under a sub-class of resonant converters and, as such, comparison
between devices will follow the similar metrics discussed in Chapter 7.

**10.6.2.1** **ZVS Voltage Mode Class-D Amplifier Example**

In this section, a variation to the traditional voltage-mode Class-D amplifier suitable for
wireless energy transfer is introduced, the ZVS VMCD [40]. The schematic and ideal
waveforms for this topology are shown in Figure 10.52.
The ZVS voltage-mode Class-D converter works by adding a non-resonant L-C tank circuit
(LZVS and CZVS) to the output of the amplifier that operates as a no-load buck converter. The
function of this tank circuit is to absorb the COSS of the devices by providing a current that will
allow the circuit to self-commutate the switch-node with the necessary dead-time between the
gate signals.
The load can then be tuned to appear resistive at 6.78 MHz, which may even be slightly
capacitive as long as the ZVS tank can yield sufficient current to maintain ZVS for the devices.
The circuit allows for greater manufacturing variation of the load coils and their tuning, yet can
maintain a high-energy transfer characteristic. The theoretical waveforms for the switching
devices of the ZVS VMCD amplifier are shown in Figure 10.53(b) and the two components are
split out for the ZVS tank circuit and the resonant load circuit in Figure 10.53(a). Load
variations have only a minimal impact on the ZVS tank circuit as long as the deviations remain
well below the peak current in LZVS. The ZVS VMCD, therefore, always ensures proper
switching for the devices, and hence, maintains low losses.

VDD

Q2

CS V/I

LZVS VDD

Q1 CZVS Zload VDS I


ZVS Tank

|V/I V DS I D|Col2|
|---|---|
|V DS||
|||


50% Time

Ideal Waveforms


(a) (b)

**Figure 10.52** (a) ZVS voltage-mode Class-D wireless energy circuit (b) with ideal waveforms


-----

V/I V/I


VDS
VDD


ILoad VDD

VDS ID

Time

50% Time
50%

|V DS I D|Col2|
|---|---|
|V DS||
|||


(a) (b)

**Figure 10.53** (a) ZVS voltage-mode Class-D circuit ideal operating waveforms (b) and component
waveforms


A ZVS Class-D wireless transfer system was built using enhancement-mode GaN transistors [41], and tested using the same coil set [42] that was used in [38,39], making it possible to
compare performance with other versions of the wireless energy transfer systems. Values of
300 nH for LZVS and 1 μF for CZVS were chosen with corresponding dead-time of 3.2 ns at 36 V
input. The coil set was tuned to resonance with Cs at 6.78 MHz. The measured system
efficiency (input supply to output load), including gate power is shown in Figure 10.54 for a
35.4 Ω load and 23.6 Ω load. The system efficiency peaks at 83.7%, at just above 35 W load
power.
Because it is very difficult to accurately determine the breakdown of losses in the system, the
best method to show the performance of GaN transistors is to use thermal imaging. Figure 10.55
shows a thermal image of the devices operating with 35 W load, alongside a photograph of the
setup. No heatsink or forced air-cooling was used.
From the thermal image, it can be seen that the gate driver is the hottest component, at around
59 °C, and the GaN transistors are around 50 °C.
To show the benefit of using GaN transistors compared with MOSFETs in a ZVS voltagemode Class-D wireless energy transfer system, we need to examine their performance in the

84

82

80

78

76

74 35.4 Ω Load

72 23.6 Ω Load

70

68

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||35.4|Ω Load|||
|||||||23.6|Ω Load|||
|||||||||||
|||||||||||


0 5 10 15 20 25 30 35 40


**Output Power (W)**

**Figure 10.54** Measured efficiency for the ZVS voltage-mode Class-D wireless energy transfer system


-----

![](GaN-transistors-power-conversion.pdf-236-0.png)

LM5113TM

EPC2007


(a) (b)

**Figure 10.55** Thermal image (b) of the ZVS voltage-mode Class-D wireless energy transfer system
operating at 35 W load power alongside a photograph (a) of the setup. Parts shown are: GaN Transistor
(EPC2007 [41]) and GaN transistor driver (LM5113TM [47])


circuit, rather than comparing total system performance. There are two main reasons: (1) the
device COSS is absorbed into the circuit, and its impact will become diminished overall, and (2)
the losses in the balance of the system, represented by ZLoad, dominate the system performance.
The GaN transistor accounts for less than 2% of the system efficiency at 30 W.
For the ZVS voltage-mode Class-D topology, the MOSFET chosen for comparison is the
FDMC8622 [51], which has a similar QOSS value, and the same voltage rating as the EPC2007
tested [41]. Regardless of whether a MOSFET is selected based on similar RDS(on) or QOSS, the
results will show similar differences.
The ZVS voltage-mode Class-D topology falls under the soft-switching converter category,
and so a soft-switching FOM comparison will be made between the devices as shown in
Figure 10.56. The converter is constrained by COSS due to circulating energy, and therefore any

350

300 QOSS•RDS(on)

QG•RDS(on)

250

200

150

100


50

0


GaN Transistor Si MOSFET
BVDSS = 100 V BVDSS = 100 V
QOSS = 8.9 nC at 40 V QOSS = 7.3 nC at 40 V
QG = 2.1 nC at 5 V QG = 5.2 nC at 10 V

**Figure 10.56** FOM comparison between the GaN transistor and MOSFET suitable for the ZVS voltagemode Class-D wireless energy transfer circuit. Parts shown are: GaN transistor (EPC2007 [41]) and
MOSFET (FDMC8622 [51])


-----

devices with lower FOMSS will yield lower losses and gate power. In the case of the GaN
transistor, it will always have a lower RDS(on) for the same COSS, and a significantly lower QG.
In addition, the Class-D circuit is limited when using a bootstrap supply to drive the high-side
device. This is due to the short on-period of the lower device at 6.78 MHz, and the gate charge
requirements for the high-side device. Furthermore, the capacitance of the bootstrap diode can
cause some discharge of the bootstrap supply capacitor during the switching transition.
An analysis was made of the ZVS voltage-mode Class-D circuit based on the circuit shown
in Figure 10.52. The initial LTSPICE simulation of the full circuit was verified against the
experimental results. The model used for the MOSFET [51] was provided by the manufacturer.
Based on the soft-switching FOM, gate power has been included in the FET power and is
shown in Figure 10.57. The simulation revealed that, by excluding the gate power, there is no
appreciable difference in system efficiency between the GaN transistor version and MOSFET
version. This is due to the way in which COSS is absorbed, and the tradeoff between RDS(on) and
the timing and magnitude of the ZVS tank circuit impact.
The difference between the GaN transistor and the MOSFET is based on gate power
consumption and reveals that GaN transistors will have a larger impact on converter efficiency
at lower output power levels. The total device power difference is near constant at around
900 mW over the entire load power range.
In the case of the voltage mode Class-D, with a half-bridge topology, providing the gate
drive signal to the upper device requires some form of level shifting circuit. Wireless energy
transfer systems typically have power levels below 30 W, so isolation circuits are not an option
as they increase system cost and complexity. A bootstrap supply works well, but it must be
designed to operate at the high frequency. The gate charge requirements, gate driver parasitic
elements, and gate driver energy requirements for the upper device circuit mean that all the
energy requirements for the upper transistor must be transferred in the short charging time
available. Given that MOSFETs have as high as four times the gate charge requirements of

1600

1400

1200

1000


800

600

400

200

0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
|||||MOSF|ET||||
|||||GaN T|ransistor||||
||||||||||
||||||||||
||||||||||
||||||||||


0 5 10 15 20 25 30 35

**Load Power (W)**

**Figure 10.57** Total FET power (including gate power) for the ZVS voltage-mode Class-D circuit
comparison between the GaN transistor and MOSFET. Parts shown are: GaN transistor (EPC2007 [41])
and MOSFET (FDMC8622 [51])


-----

GaN transistors, MOSFETs will reach an upper frequency operating limit at a significantly
lower frequency than GaN devices.

**10.6.2.2** **Single-Ended Class-E Example**

The next amplifier that will be investigated is the single-ended Class-E. The schematic and
ideal waveforms for this topology are shown in Figure 10.58. The design of a Class-E amplifier
is well documented [32–34,43–46] and, for this example, requires the load inductance of ZLoad
to be resonated by Cs to yield only the resistive portion of ZLoad. This, in turn, defines the
supply voltage (VDD) needed for a specific load power specification.
In the case of wireless energy transfer using a Class-E amplifier, the design must be based
initially on the highest coupling coefficient and lowest load resistance for the load. This will
ensure that the amplifier will always operate with manageable power dissipation in the device
with any load and coupling variation. Operating with a load resistance below the design point
will significantly increase the power losses generated in the device. The Class-E amplifier
experiences losses in the RF choke (LRFck), the device (Q1), and the extra inductor (Le). The
device experiences very low losses at the turn-on event with both zero current and zero voltage
present under ideal operating conditions. The turn-off event occurs as a ZVS event. Deviations
from the ideal operating point, due to load resistance changes, can quickly induce high
switching losses resulting from incomplete voltage- or current-resonant transitions in the
matching network (Le and Csh). The choice of device must have a lower or equal COSS than the
required shunt capacitance (Csh) from the design equations. If the design requires a shunt
capacitance that is smaller than COSS, the design cannot be realized.
A single-ended Class-E wireless transfer system was built using GaN transistors [50], and
tested using the same coil set [42] as was used for the ZVS Class-D example. The design used
the classic Sokal equations [48] with the quality factor set to infinity [49] for simplification
purposes. Operation at 6.78 MHz is low enough to make this a valid assumption. A value of
360 nH for Le and 150 pF for Csh was chosen for operation up to 30 V input. The coil set was
tuned to resonance with Cs at 6.78 MHz. The measured system efficiency (input supply to

VDD

LRFck

Le Cs V/I

3.56 x VDD

Q1 Csh Zload VDS ID IZVS

50% time

Ideal Waveforms

(a) (b)

**Figure 10.58** (a) Single-ended Class-E wireless energy circuit (b) with ideal waveforms


-----

84

83


82

81


80

79


78

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
|||||||||||
||||G|||||CD||
|||||G|aN Transis|tor –23.6|Ω ZVS-VM|CD||
||||G|G|aN Transis|tor –20.5|Ω Single CE|||
|||||||||||
|||||||||||


0 5 10 15 20 25 30 35 40


**Output Power (W)**

**Figure 10.59** Measured efficiency for the single-ended Class-E wireless energy transfer system with the
performance of the ZVS-VMCD for comparison


output load), including gate power, is shown in Figure 10.59 for a 20.5 Ω load. The system
efficiency peaks at 82.5%, with a load power of just above 30 W. The performance of the ZVS
voltage-mode Class-D system is also shown on Figure 10.59 for comparison.
Figure 10.60 shows the thermal image of the devices operating with 30 W load alongside a
photograph of the setup. No heatsink or forced air-cooling was used.
From the thermal image, it can be seen that the device is the hottest component, at around
44 °C, and that the gate driver is around 35 °C. Compared to the ZVS voltage-mode case, the
gate driver is driving only a single device, which accounts for the large difference in
temperature compared with the ZVS Class-D design.
Again, we can show the benefit of using GaN transistors over MOSFETs in a single-ended
Class-E wireless energy transfer system in the same way as for the ZVS voltage-mode Class-D.
For the single-ended Class-E topology, the MOSFET chosen for comparison is the
FDMC86248 [52], which has a similar QOSS value, but is rated at 150 V, whereas the
EPC2012 is rated at 200 V [50]. Regardless of whether a MOSFET is selected based on
similar RDS(on) or QOSS, the results will show similar differences.

LM5113TM


![](GaN-transistors-power-conversion.pdf-239-0.png)

EPC2012
(a) (b)

**Figure 10.60** Thermal image (b) of the GaN-based single-ended Class-E wireless energy transfer
system operating at 30 W load power with (a) photograph of the setup


-----

1000
900

800

700
600

500

400

300

200

100
0

|Q •R|Col2|Col3|
|---|---|---|
||Q •R||
||OSS DS(on) Q •R G DS(on)||
||||
||||
||||
||||
||||
||||
||||
||||


GaN Transistor Si MOSFET
BVDSS = 200 V BVDSS = 150 V
QOSS = 11.6 nC at 100 V QOSS = 13.2 nC at 100 V
QG = 1.5 nC at 5 V QG = 6.4 nC at 10 V

**Figure 10.61** FOM comparison between the GaN transistor and MOSFET suitable for the single-ended
Class-E wireless energy transfer circuit. Parts shown are: GaN transistor (EPC2012 [50]) and MOSFET
(FDMC86248 [52])


The single-ended Class-E topology falls under the soft-switching converter category and so a
soft-switching figure of merit comparison will be made between the devices as shown in
Figure 10.61.
An analysis was made of the single-ended Class-E circuit, based on the circuit shown in
Figure 10.60. The initial LTSPICE simulation of the full circuit was verified against the
experimental results. The model used for the MOSFET [52] in the equivalent simulation was
provided by the manufacturer. Based on the soft-switching FOM, gate power has been included
in the FET power as shown in Figure 10.62. The simulation revealed that, by excluding the gate

800

700

600

500

Si MOSFET

400

GaN Transistor

300

200

100


0

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|
|---|---|---|---|---|---|---|---|---|
||||||||||
||||||||||
||||||||||
|||||Si MO|SFET||||
|||||GaN T|ransistor||||
||||||||||
||||||||||
||||||||||


0 5 10 15 20 25 30 35


**Load Power (W)**

**Figure 10.62** Total FET power (including gate power) for the single-ended Class-E circuit comparison
between the GaN transistor and MOSFET. Parts shown are: GaN transistor (EPC2012 [50]) and MOSFET
(FDMC86248 [52])


-----

power, there is no appreciable difference in system efficiency between the GaN FET version
and the MOSFET version. This can be attributed to both RDS(on) and QOSS being similar, and
the COSS being absorbed into the matching circuit.
The difference between the GaN transistor and the MOSFET is again based on gate power
consumption and reveals that GaN transistors will have a larger impact on converter efficiency
at lower output power levels. The total device power difference is near constant at around
430 mW over the entire load power range. This is due to the very small difference in RDS(on)
between the devices and the differences in COSS current. The GaN transistor has a lower QOSS,
and therefore lower current flowing in the device relative to the external capacitor Csh.
Alternatively, if using equivalent COSS devices for comparison between the MOSFET and the
GaN transistor, the conduction losses of the GaN transistor will be lower, as the RDS(on) of the
GaN transistor will be lower than for the MOSFET.

###### 10.6.3 Summary of Design Considerations for Wireless Energy Transfer

In this section, highly resonant, loosely coupled wireless energy transfer systems were
demonstrated using GaN transistors in ZVS voltage-mode Class-D and single-ended ClassE topologies. It was shown that at low power output, up to 30 W, GaN transistors show a
significant improvement in conversion efficiency, largely due to lower gate drive power
consumption. At higher output power the advantages of GaN would be even more pronounced.
In the case of the voltage mode Cass-D amplifier, with a half-bridge topology, the lower gate
charge allows a bootstrap supply to be used at a much higher frequency than comparable
MOSFETs, thereby enabling wireless energy conversion at even higher frequencies such as
the 13.56 MHz wireless power transfer standard. Furthermore, the lower gate charge also
leads to lower power dissipation in the gate driver itself, thereby eliminating the need for
heatsinks.

###### 10.7 LiDAR and Pulsed Laser Applications

Another application for which the unique properties of GaN transistors are ideally suited is
pulsed laser applications such as LiDAR (light distancing and ranging). LiDAR uses pulsed
lasers to rapidly create a three-dimensional image of a surrounding area. This technique is
widely used for geographic mapping functions such as those used by Google Maps. The higher
switching speed of GaN transistors drive superior resolution and response time that enable
LiDAR applications to go beyond simple mapping functions to applications such as real-time
motion detection for video gaming, computers that no longer require touch screens, and fully
autonomous vehicles.
In LiDAR, as well as other pulsed laser applications, the need exists for the generation of
either very short duration current pulses, or finite pulses with accurate constant amplitude and
pulse width. In both cases, the generation of a fast rising and falling edge is essential. The high
speed switching of GaN devices is ideally suited for this application. LiDAR, in particular,
needs shorter and shorter duration pulses at higher power, as spatial resolution is directly
related to the pulse width:

ΔR  [c] (10.3)
2 [Δ][t]


-----

In Equation 10.3, ΔR is the spatial resolution, c is the speed of light, and Δt is the full width
of the light pulse, measured at half the maximum amplitude – also known as full width at half
maximum (FWHM). Thus, the spatial resolution is equal to half the distance from leading to
trailing edge of the light pulse as it travels at the speed of light (about 0.3 m per ns).
Furthermore, since LiDAR systems rely on the often faint reflection of the light returning
to the detector to be above the background light levels, increasingly-higher-power laser pulses
are required to improve performance.
To understand the practical constraints of pulsed laser applications, consider the simple
pulsed laser drive circuit shown in Figure 10.63 [53]. The laser diode is in series with a
switching device and the voltage source or capacitance energy storage. At the switching device
turn-on, the current will be zero and the initial rate of current increase will be limited by the
overall loop inductance as determined by Equation 10.4.

di
(10.4)
dt [][ V][Supply]L[ �]Loop[V][Diode]

In this equation [di]dt [is the maximum current slew rate, V][Supply][ is the DC supply voltage, V][Diode]
is the laser diode operating voltage drop, and LLoop is the overall loop inductance formed
between the supply, laser diode, and switching device. To maximize the current slew rate, the
overall loop inductance needs to be minimized. This is done through the use of low-inductive
package laser diodes [54], and low inductance switching devices, for which the use of the
enhancement mode LGA package GaN transistors are ideally suited. Furthermore, high-speed
GaN transistors can significantly increase switching speeds, further minimizing the achievable
pulse width.
As an example of the capabilities of GaN transistors for pulsed laser applications, the
current pulse waveforms for a laser diode using GaN transistors, compared to a similar result
using silicon MOSFETs, are shown in Figure 10.64. Comparing the rising edges of these
waveforms, it can be seen that the GaN transistors are capable of switching 400 A in less than
50 ns (>8 A/ns), compared to the MOSFET switching 300 A in less than 70 ns (>4.3 A/ns).
Not only are the GaN transistors able to almost double the current slew rate, but they

Optional Current
Limiting Resistor

Loop Inductance

###### +

Laser Diode + Supply Voltage

###### –

VDiode –
VSupply

Pulse
Input

Optional Current
Sense

**Figure 10.63** Simple pulsed laser drive circuit implementation. Pulsed current path shown as dashed
line


-----

![](GaN-transistors-power-conversion.pdf-243-0.png)

TeK Run Trig’ d

Ch 1 Rise
48.87 ns

Ch 4 Rise
66.96 ns

Ch 1 + Width
2.043 µs

Ch 1 Ampl
408.0 A

Ch1 100A Ch4 100A M 400ns A Ext 800mV

T 10.00 %


**Figure 10.64** Laser diode current pulses using silicon MOSFET and GaN transistor respectively

are also able to increase the overall current capability by virtue of a lower device onresistance, enabling significant performance improvements in LiDAR and other pulsed laser
applications.

###### 10.8 Power Factor Correction (PFC)

PFC circuits are required in modern power supplies to maximize real power and minimize
THD, to improve the efficiency of the power grid. The conventional PFC boost rectifier, shown
in Figure 10.65(a), is prevalent in current designs. To improve PFC performance, bridgeless
topologies are being considered to eliminate one diode from the current conduction path,
reducing power loss [55]. To enable improved PFC topologies, better performing devices are
required. The bridgeless totem pole PFC boost rectifier, shown in Figure 10.65(b), is a
promising topology, but its operation has been limited by the high reverse recovery of
traditional Si MOSFETs [56]. GaN transistors have zero reverse recovery and thus make
an ideal choice for this topology.
GaN transistors can improve performance in both conventional and bridgeless PFC boost
rectifier configurations by reducing the switching losses related to hard-switching as discussed
in Chapter 6. For a similar RDS(on) device, GaN transistors offer significantly lower QG, thereby
reducing gate drive losses, significantly lower QGD and QGS2, reducing voltage and current
commutation losses, lower EOSS, reducing capacitive turn-on losses, and significantly lower
QRR, reducing reverse recovery losses. To evaluate the performance improvements possible
with GaN transistors in higher voltage resonant applications, the characteristics of 600 V GaN
cascode transistors and Si MOSFETs are compared in Table 10.4.
From Table 10.4, it can be seen that high-voltage GaN transistors offer a large reduction in
the key FOMs for hard-switching converters as discussed in Section 6.2. The GaN transistor
has an over seven times improvement in gate charge FOM over the Si MOSFET, resulting in
lower gate driving losses in high-frequency designs. The hard-switching FOMHS is almost
eight times lower for a GaN transistor than an Si MOSFET, and this will translate directly into


-----

VAC

VAC


LB DB

QB

(a)

(b)


RL

RL

|L B Q 1 C Q 2|D 1 C B D 2|
|---|---|


**Figure 10.65** (a) Conventional PFC boost rectifier (b) bridgeless totem pole PFC boost rectifier

lower losses and improved high-frequency PFC performance. For a 230 VAC_IN to 400VOUT,
1500 W conventional PFC converter operating at 500kHz, GaN transistors have demonstrated a
1% gain in full load efficiency and a 0.25% gain at 20% load when compared to state-of-the-art Si
MOSFETs. This leads to a reduction in full-load power loss from 42 W to 26 W [57]. For the
bridgeless totem-pole PFC rectifier shown in Figure 10.65, efficiencies over 98.5% were
achieved with GaN transistors for a 230VAC_IN to 400VOUT converter operating at 50 kHz [56].

**Table 10.4** Device comparison between GaN transistor (TPH3006PS) and Si MOSFET (FCP190N60E)

Parameter GaN transistor[a] Si MOSFET[b] FOM ratio

Voltage Rating (VDSS) 600 V 600 V
RDS(on) 150 mΩ at 8 V 160 mΩ at 10 V
QG 9.3 nC at 8 V[a] 63 nC at 10 V
QGD at 380 V 3.2 nC[a] 24 nC
QGS2 at 10 A 0.5 nC[a] 3.3 nC[b]

EOSS at 380 V 4.0 μJ[a] 5.5 μJ
QRR 54 nC 4800 nC
QGRDS(on) 1395 pCΩ 10,080 pCΩ 7.23 × reduction
FOMHS (QGD + QGS2)RDS(on) 555 pCΩ 4368 pCΩ 7.87 × reduction

_a All values calculated from TPH3006PS datasheet and [6]._
_b All values calculated from FCP190N60E datasheet._


-----

**Table10.5** DevicecomparisonbetweenaGaNtransistor(TPH3006PS),anSiMOSFET(FCP190N60E),
and an Si IGBT (STGB20V60DF)

Parameter GaN Transistor[a] Si MOSFET[b] Si IGBT[c]

Voltage rating (VDSS) 600 V 600 V 600 V
RDS(on) 150 mΩ at 8 V 160 mΩ at 10 V 150 mΩ at 15 V, 10 A[c]

QG 9.3 nC at 8 V[a] 63 nC at 10 V 116 nC at 15 V
QGD at 380 V 3.2 nC[a] 24 nC (QGC) 45 nC[c]

QGS2 at 10 A 0.5 nC[a] 3.3 nC[b] (QGE2) 3.8 nC[c]

QGRDS(on) 1395 pCΩ 10,080 pCΩ 17,400 pCΩ
FOMHS (QGD + QGS2)RDS(on) 555 pCΩ 4368 pCΩ 7320 pCΩ

_a All values calculated from TPH3006PS datasheet and [6]._
_b All values calculated from FCP190N60E datasheet._
_c All values calculated from STGB20V60DF datasheet._

###### 10.9 Motor Drive and Photovoltaic Inverters

Voltage inverters are prevalent in applications such as motor drives and photovoltaic (PV)
inverters to provide DC-AC power conversion. Again, GaN transistors can outperform Si
MOSFETs and IGBTs in inverter applications by providing faster switching speeds. A
comparison of device performance between GaN transistors, Si MOSFETs, and Si IGBT’s
can be seen in Table 10.5. The benefits of GaN transistors were demonstrated in a 4 kW, 50 kHz
PV inverter, where the GaN transistor-based design was able to achieve higher efficiency than a
16 kHz IGBT-based solution, with the higher frequency, allowing for an almost 45% reduction
in converter volume [58]. In motor drive applications, GaN transistors have demonstrated
improved system performance in a 2.2 kW motor drive system where the GaN transistors
operated at 100 kHz, an over six-fold increase over the 15 kHz IGBT-based design, while
providing a 2% increase in efficiency [59].

###### 10.10 Summary

Highlighted in this chapter were existing applications, such as point-of-load converters, ClassD audio amplification, motor drives, and power factor correction, which benefit from the
superior performance of GaN transistors compared with their silicon MOSFET and IGBT
counterparts. Additionally, GaN transistors enable applications that are not possible with the
aging silicon transistor technology. These emerging applications include envelope tracking,
wireless power transfer, and LiDAR, just to name a few. Improvements in switching losses are
complemented by improvements in gate drive losses and layout parasitics to demonstrate that
GaN can outperform silicon in almost any power conversion application.
In the final chapter, key factors that determine the displacement rate of GaN technology into
the world of silicon transistors will be considered.

###### References

1. International Rectifier, J. B. Forsythe, “Paralleling of Power MOSFETs for High Power Output,” Appl. Note.
[Available from http://www.irf.com/technical-info/appnotes/para.pdf.](http://www.irf.com/technical-info/appnotes/para.pdf)


-----

2. Wu, Y.F. (2013) “Paralleling high-speed GaN power HEMTs for quadrupled power output,” Twenty-Eighth
Annual IEEE Applied Power Electronics Conference and Exposition (APEC), Long Beach, CA, 16–21 March
2013, pp. 649–655.
[3. IEEE 802.3 at[TM]-2009 Ethernet standard, Available from http://standards.ieee.org/about/get/802/802.3.html.](http://standards.ieee.org/about/get/802/802.3.html)
4. Lu, B., Liu, W., Liang, Y., Lee, F.C., and Wyk, J.D. (2006) “Optimal design methodology for LLC resonant
converter,” Applied Power Electronics Conference and Exposition (APEC) 2006 Twenty-First Annual IEEE,
Dallas, TX, 2006, pp. 533–538.
5. Yang, B., Lee, F.C., Zhang, A.J., and Huang, G. (2002) “LLC resonant converter for front end DC/DC
conversion,” Applied Power Electronics Conference and Exposition (APEC) 2002 Seventeenth Annual IEEE,
Dallas, TX, 2002, pp. 1108–1112.
6. Mishra, U. and Wu, Y. (2013) “Latest high voltage GaN devices for inverters,” PCIM Europe 2013, pp. 724–729.
7. Briere, M. (2013) “The Status of 600 V GaN on Si-based Power Device Development at International Rectifier,”
PCIM Europe 2013, pp. 735–742.
8. Huang, X., Liu, Z., Li, Q., and Lee, F.C. (2013) “Evaluation and application of 600 V GaN HEMT in cascode
structure,” Applied Power Electronics Conference and Exposition (APEC) 2012 Twenty-Seventh Annual IEEE,
Orlando, FL, 2012, pp. 1279–1286.
9. International Rectifier Corporation, “Class-D Amplifier Design Basics II,” Rev. 1, 19 Feb. 2009. Available from

[http://www.irf.com/product-info/audio/classdtutorial2.pdf.](http://www.irf.com/product-info/audio/classdtutorial2.pdf)
10. International Rectifier Corporation, “Protected digital audio amplifier,” IRF2092 datasheet, 2007 [Revised 18 Oct.
[2010]. Available from http://www.irf.com/product-info/datasheets/data/irs2092.pdf.](http://www.irf.com/product-info/datasheets/data/irs2092.pdf)
11. J. Strydom, “eGaN[] FET- Silicon Power Shoot-Out Volume 11: Optimizing FET On-Resistance,” Power
_[Electronics Technology, Oct. 2012. Available from http://powerelectronics.com/discrete-semis/gan_transistors/](http://powerelectronics.com/discrete-semis/gan_transistors/egan-fet-silicon-power-shoot-out-volume-11-optimizing-fet-on-resistance-1001/)_
[egan-fet-silicon-power-shoot-out-volume-11-optimizing-fet-on-resistance-1001/.](http://powerelectronics.com/discrete-semis/gan_transistors/egan-fet-silicon-power-shoot-out-volume-11-optimizing-fet-on-resistance-1001/)
12. Efficient Power Conversion Corporation, “Development board EPC9106 quick start guide – 150 W/8 Ω class-D
[amplifier,” Available from http://epc-co.com/epc/documents/guides/EPC9106_qsg.pdf.](http://epc-co.com/epc/documents/guides/EPC9106_qsg.pdf)
13. Wimpenny, G. (Jan. 2012) “Understand and characterize envelope-tracking power amplifiers,” EE Times Magazine.
[14. OpenET alliance, “Introduction to envelope tracking,” Available from www.open-et.org/Intro-to-ET-pa-712.php.](http://www.open-et.org/Intro-to-ET-pa-712.php)
15. Staudinger, J., Gilsdorf, B., Newman, D., Norris, G., Sadowniczak, G., Sherman, R., and Quach, T. (2000) High
efficiency CDMA RF power amplifier using dynamic envelope tracking technique. IEEE Microwave Symposium
_Digest, 2, 873–876._
16. Baker, S. (14 July 2011) “Applying envelope tracking to high-efficiency power amplifiers for handset and
[Infrastructure transmitters,” Cambridge Wireless Radio SIG, Available from http://www.cambridgewireless.co.uk/](http://www.cambridgewireless.co.uk/Presentation/Steven%20Baker.pdf)
[Presentation/Steven%20Baker.pdf.](http://www.cambridgewireless.co.uk/Presentation/Steven%20Baker.pdf)
17. Chan, K. (Jan. 2010) “GC5325 Envelope Tracking,” Texas Instruments, Application Report SLWA058.
18. Hendy, J. (2009) Transmitter power efficiency. Broadcast Engineering Magazine, 51 (11), 8–13.
19. Vasic, M., Garcia, O., Oliver, J.A., Alou, P., and Cobos, J.A. (2012) Survey of architectures and optimizations foŕ
wide bandwidth envelope amplifier, Power Electronics and Motion Control Conference, EPE/PEMC 4–6 Sep.
2012, pp. LS8d.1–1-LS8d.1-7.
20. Jeong, J. and Kimball, D.F. (2009) Wideband envelope-tracking power amplifier with reduced bandwidth power
supply waveform. IEEE Transactions on Microwave Theory and Techniques, 52 1381–1384.
21. Strydom, J.T. (April 2012) “eGaN[] FET- Silicon Power Shoot-Out Volume 8: Envelope Tracking,” Power
_[Electronics Magazine, Available from http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-](http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-out-volume-8-envelope-trackingShootout)_
[out-volume-8-envelope-trackingShootout 8.](http://powerelectronics.com/gan-transistors/egan-fet-silicon-power-shoot-out-volume-8-envelope-trackingShootout)
22. Cucak, D., Vasic, M., Garcia, O., Oliver, J.A., Alou, P., and Cobos, J.A. (2012)́ “Application of eGaN FETs
for highly efficient radio frequency power amplifier,” Integrated Power Electronics Systems, CIPS March 2012,
pp. 1–6.
23. Efficient Power Conversion Corporation, Appl. Note AN015, “Introducing a Family of eGaN FETs for Multi[Megahertz Hard Switching Applications,” Available from http://epc-co.com/epc/documents/product-training/](http://epc-co.com/epc/documents/product-training/AN015 eGaN FETs for Multi-Megahertz Applications.pdf)
[AN015 eGaN FETs for Multi-Megahertz Applications.pdf.](http://epc-co.com/epc/documents/product-training/AN015 eGaN FETs for Multi-Megahertz Applications.pdf)
24. Efficient Power Conversion Corporation, “EPC8005 – Enhancement-mode Power Transistor,” EPC8005 data[sheet, Sep. 2013 [Revised Sept. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC8005_-](http://epc-co.com/epc/documents/datasheets/EPC8005_datasheet.pdf)
[datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC8005_datasheet.pdf)
25. Wu, T., “Cdv/dt induced turn-on in synchronous buck regulators,” white paper, International Rectifier Corporation.
26. Reusch, D. and Strydom, J. (2014) Understanding the effect of PCB layout on circuit performance in a high frequency
gallium nitride-based point of load converter. Power Electronics, IEEE Transactions, 29 (4), 2008–2015.


-----

27. Strydom, J. and Reusch, D. (2014) “Design and evaluation of a 10 MHz gallium nitride-based 42 V DC-DC
converter,” Applied Power Electronics Conference (APEC) 2014 Twenty-Ninth Annual IEEE Session T30, Fort
Worth, TX, 16–20 March 2014.
[28. http://www.wirelesspowerconsortium.com/](http://www.wirelesspowerconsortium.com/)
29. Tseng, R., von Novak, B., Shevde, S., and Grajski, K.A. (2013) “Introduction to the alliance for wireless power
loosely-coupled wireless power transfer system specification version 1.0,” IEEE Wireless Power Transfer
Conference 2013, Technologies, Systems and Applications, May 15–16, 2013.
30. “Industrial, Scientific, and Medical Equipment,” FCC regulation: CFR 2010, title 47, vol. 1, Part 18. Available from

[http://www.ecfr.gov/cgi-bin/text-idx?SID=abcb16dbad4883038a13c0a1a0e28df0&node=47:1.0.1.1.18&rgn=div5.](http://www.ecfr.gov/cgi-bin/text-idx?SID=abcb16dbad4883038a13c0a1a0e28df0&node=47:1.0.1.1.18&rgn=div5)
31. El-Hamamsy, S.-A. (1994) Design of high-efficiency RF class-D power amplifier. IEEE Transactions on Power
_Electronics, 9 (3), 297–308._
32. Hung, T.-P. (Jan. 2008) “High efficiency switching-mode amplifiers for wireless communication systems,” Ph.D.
dissertation, University of California, San Diego, CA.
33. Choi, D.K. (March 2001) “High efficiency switched-mode power amplifiers for wireless communications,” Ph.D.
dissertation, University of California, Santa Barbara, CA.
34. Gerrits, T., Duarte, J.L., and Hendrix, M.A.M. (2010) “Third harmonic filtered 13.56 MHz push-pull class-E power
amplifier,” IEEE Energy Conversion Congress and Exposition (ECCE) conference, September 2010, pp. 742–749.
35. Siddabattula, K.,“Wireless Power System Design Component and Magnetics Selection,” Texas Instruments,
presentation. Available from [http://e2e.ti.com/support/power_management/wireless_power/m/mediagallery/](http://e2e.ti.com/support/power_management/wireless_power/m/mediagallery/526153.aspx)
[526153.aspx.](http://e2e.ti.com/support/power_management/wireless_power/m/mediagallery/526153.aspx)
36. Kurs, A., Karalis, A., Moffatt, R., Joannopoulos, J.D., Fisher, P., and Soljacič, M. (2007) Wireless power transfeŕ
via strongly coupled magnetic resonances. Science Magazine, 317 (5834), 83–86.
37. Qualcomm (Sep. 2011) Wireless power transfer enabling the mobile charging ecosystem. Darnell Power Forum.
38. de Rooij, M.A. and Strydom, J.T. (2012) eGaN[] FET–silicon shoot-out Vol. 9: wireless power converters. Power
_[Electronics Technology, 22–27. Available from http://powerelectronics.com/discrete-power-semis/egan-fet-](http://powerelectronics.com/discrete-power-semis/egan-fet-silicon-shoot-out-vol-9-wireless-power-converters)_
[silicon-shoot-out-vol-9-wireless-power-converters.](http://powerelectronics.com/discrete-power-semis/egan-fet-silicon-shoot-out-vol-9-wireless-power-converters)
39. De Rooij, M.A. and Strydom, J.T. (2012) eGaN[] FETs in low power wireless energy converters. Electro-Chemical
_Society Transactions on GaN Power Transistors and Converters, 50 (3), 377–388._
40. de Rooij, M.A. and Strydom, J.T. (August (2013)) “High Efficiency Voltage Mode Class-D topology,” U.S. patent
pending.
41. Efficient Power Conversion Corporation, “EPC2007 – Enhancement-mode Power Transistor,” EPC2007 data[sheet, Sep. 2011 [Revised Jul. 2013]. Available from http://epc-co.com/epc/documents/datasheets/EPC2007_](http://epc-co.com/epc/documents/datasheets/EPC2007_datasheet.pdf)
[datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2007_datasheet.pdf)
[42. Witricty Corp., coil set part numbers 190-000037-01 and 190-000038-01, Available from www.witricity.com.](http://www.witricity.com)
43. Raab, F.H. (1977) Idealized operation of the class-E tuned power amplifier. IEEE Transactions on Circuits and
_Systems, 24 (12), 725–735._
44. Kazimierczuk, M. (1984) Collector amplitude modulation of the class-E tuned power amplifier. IEEE Transactions
_on Circuits and Systems, 31 (6), 543–549._
45. Chen, K. and Peroulis, D. (2011) Design of highly efficient broadband class-E power amplifier using synthesized
low-pass matching networks. IEEE Transactions on Microwave Theory and Techniques, 59 (12), 3162–3173.
46. Chen, W., Chinga, R.A., Yoshida, S., Lin, J., Chen, C., and Lo, W. (2012) “A 25.6 W 13.56 MHz wireless power
transfer system with a 94% efficiency GaN class-E power amplifier,” IEEE MTT-S International Microwave
Symposium Digest (MTT), June 2012, pp. 1–3.
47. Texas Instruments, “LM5113 5A, 100V Half-Bridge Gate Driver for Enhancement Mode GaN GETs,” LM5113
datasheet, June 2011 [Revised Apr. 2013].
48. Sokal, N.O. and Sokal, A.D. (1975) Class-E – A new class of high-efficiency tuned single-ended switching power
amplifiers. IEEE Journal of Solid-State Circuits, SC-10 (3), 168–176.
49. Sokal, N.O. (2001) Class-E RF power amplifiers. QEX Magazine, (204), 9–20.
50. Efficient Power Conversion Corporation, “EPC2012 – Enhancement-mode Power Transistor,” EPC2012 datasheet,
[Aug.2011[RevisedOct.2012].Availablefromhttp://epc-co.com/epc/documents/datasheets/EPC2012_datasheet.pdf.](http://epc-co.com/epc/documents/datasheets/EPC2012_datasheet.pdf)
51. Fairchild Semiconductor, “FDMC8622–100 V N-Channel Shielded Gate Power Trench[] MOSFET,” FDMC8622
[datasheet, Rev. C5, Oct. 2013. Available from http://www.fairchildsemi.com/pf/FD/FDMC8622.html.](http://www.fairchildsemi.com/pf/FD/FDMC8622.html)
52. Fairchild Semiconductor, “FDMC86248�150 V N-Channel Shielded Gate Power Trench[] MOSFET,”
[FDMC86248 datasheet, Rev. C3, Sept. 2012. Available from http://www.fairchildsemi.com/pf/FD/FDMC86248](http://www.fairchildsemi.com/pf/FD/FDMC86248.html)
[.html.](http://www.fairchildsemi.com/pf/FD/FDMC86248.html)


-----

53. IXYS-Colorado, “PCO-7120 Laser Diode Driver Module,” Installation and operation notes, Available from

[http://www.ixysrf.com/index.php?option=com_joomdoc&task=document.download&path=dei-scientific/operating-](http://www.ixysrf.com/index.php?option=com_joomdoc&task=document.download&path=dei-scientific/operating-manuals/PCO-7120_Manual_RevA.pdf)
[manuals/PCO-7120_Manual_RevA.pdf.](http://www.ixysrf.com/index.php?option=com_joomdoc&task=document.download&path=dei-scientific/operating-manuals/PCO-7120_Manual_RevA.pdf)
[54. PicoLAS, Application Note # 02: “Impedance of Laser Diodes, Inductive Behaviour,” Available from http://www](http://www.lasercomponents.com/fileadmin/user_upload/home/Datasheets/lc/veroeffentlichung/treiberelektronik-pulslaserdioden.pdf)
[.lasercomponents.com/fileadmin/user_upload/home/Datasheets/lc/veroeffentlichung/treiberelektronik-pulslaserdioden](http://www.lasercomponents.com/fileadmin/user_upload/home/Datasheets/lc/veroeffentlichung/treiberelektronik-pulslaserdioden.pdf)
[.pdf.](http://www.lasercomponents.com/fileadmin/user_upload/home/Datasheets/lc/veroeffentlichung/treiberelektronik-pulslaserdioden.pdf)
55. Huber, L., Jang, Y., and Jovanovic, M.M. (2007) Performance evaluation of bridgeless PFC boost rectifiers,”
Applied Power Electronics Conference and Exposition (APEC), 2007 Twenty-Second Annual IEEE, Anaheim,
CA, pp. 165–171.
56. Zhou, L., Wu, Y.F., and Mishra, U. (2013) “True-bridgeless totem-pole PFC ased on GaN HEMTs,” PCIM Europe
2013, pp. 1017–1022.
57. Wu, Y.F., Gritters, J., Shen, L., Smith, R.P., McKay, J., Barr, R., and Birkhan, R. (2013) “Performance and
robustness of first generation 600 V GaN-on-Si power transistors,” IEEE Workshop on Wide Bandgap Power
Devices and Applications.
58. Blake, C. (April 2013) “GaN power devices slash size, raise efficiency of 4 kW solar inverter,” How2Power Today,
exclusive technology feature.
59. Wu, Y.F., Kebort, D., Guerrero, J., Yea, S., Honea, J., Shirabe, K., and Kang, J. (2012) “High-frequency, GaN
diode-free motor drive inverter with pure sine wave output,” PCIM Europe 2012, pp. 76–83.
[60. Charged, Electric Vehicles Magazine, Available from http://chargedevs.com/features/whats-wireless-ev-charging/,](http://chargedevs.com/features/whats-wireless-ev-charging/)
issue 9-Aug 2013, [accessed Jan. 2014].


-----

# 11

#### Replacing Silicon Power MOSFETs

###### 11.1 What Controls the Rate of Adoption ?

The silicon power MOSF ET journ ey, spanni ng more than 3 0 years, taught us that there are four
key variables contro lling the adopti on rate of a d isruptive powe r management techno logy [1].

1. Does it enable signi ficant ne w capabilit ies?
2. Is it easy to use?
3. Is it _very_ cost effective for the user?
4. Is it reliable?

In the next few sectio ns, and using the informat ion from the previ ous chapte rs, the readiness
of the GaN trans istor to repla ce the sil icon power MO SFET, based on these four criteria, will be
reviewed.

###### 11.2 New Capabilities Enabled by GaN Trans istors

The most signi ficant new capa bilities enable d by GaN transistors stem from the disrup tive
improvem ent in switch ing speed (see Figure 11.1). As discu ssed in Cha pter 1, GaN transistors
also have a much higher crit ical electric fiel d capa bility than sil icon, which enable s this new
class of device s to withstand much great er volt age from drain to source, with much less penalty
in on-resist ance. This capabi lity, couple d with higher electron mobi lity and innova tive device
packagi ng, has created a class of devices that are signi ficantly smaller and faster than their
silicon predeces sors.
As GaN trans istors gain wi der accept ance as the succes sor to the power MOSFET, designers
have been able to leverage the incre ased switch ing perfor mance to improve powe r con version
system efficiency, size, and cost. Exa mined in Chapter s 6 –8 wer e the adva ntages of GaN
transist ors in hard- and resonant-s witchi ng topol ogies from h undreds of kHz up to hundred s of
MHz, and even RF amplifie rs into the mul ti-GHz range. Chapter 9 explor ed the except ional
capabi lities of enhan cement-m ode transist ors to withst and large amounts of radia tion exposur e.

_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

![](GaN-transistors-power-conversion.pdf-250-0.png)

**Figure 11.1** Switching speed comparison between a GaN transistor (EPC2015) and a MOSFET
(BSZ040N04) in a buck converter switching at 1 MHz with a VIN = 12 V, VOUT = 1.2 V, IOUT = 20 A

In Chapter 10, early-adopter applications such as wireless power transfer, envelope tracking,
LiDAR, power factor correction, and Class-D audio were described in detail and compared
against state-of-the-art power MOSFETs in the same circuit topologies. In all the examples,
GaN transistor technology can shrink system size, enhance system efficiency, and increase
power density.

###### 11.3 GaN Transistors are Easy to Use

How easy a device is to use depends on the skill of the user, the degree of difficulty of the circuit
under development, how different the device is compared with devices that are within the
experience of the user, and the tools available to help the user apply the device. GaN transistors
are very similar in their behavior to existing power MOSFETs and, therefore, users can greatly
leverage their past design experience.
One key difference, relatively high frequency response, is both a step function improvement
over any prior silicon device and an added consideration for the user when designing a circuit.
As described in Chapter 4, small amounts of stray parasitic inductance can cause increased
power losses and a large overshoot in the gate-to-source voltage that could potentially damage
devices.
On the other hand, there are several characteristics that render these devices easier to use
than their silicon predecessors. For example, the threshold voltage is virtually independent of
temperature over a wide range for enhancement-mode devices (cascode devices have a
threshold voltage set by a silicon MOSFET and, therefore, have the same dependence on
temperature as a MOSFET), and the on-resistance also has a significantly lower temperature
coefficient than silicon.
User-friendly tools can make a big difference to how easy it is to apply a new type of device.
SPICE device models, as well as thermal models, are widely available for user download [2].
Pre-assembled circuit kits are available from GaN transistor manufacturers such as Efficient
Power Conversion Corporation, Transphorm, and GaN Systems. In addition, ICs designed
specifically to drive GaN transistors, make the designer’s job easier by compressing designs,


-----

and thus reducing common source and power loop inductances. Driver ICs can also manage the
higher speeds needed to switch the transistors with minimum power loss, but without excessive
overshoot or dead-time. Finally, as the user base expands, there will be many experienced
designers able to turn ideas into products quickly using the state-of-the-art GaN transistors.

###### 11.4 Cost vs. Time

Cost comparisons between products of different technologies can be difficult. In addition, costs
are not always reflected in product prices if there is an imbalance between supply and demand
in the consuming market. Since the GaN transistor is primarily a replacement for the mature,
but aged, power MOSFET, that is the most meaningful cost comparison.
The basic elements of product cost are:

- starting material

- epitaxial growth

- wafer fabrication

- test and assembly.

Other elements that contribute to costs such as yield, engineering costs, packing and
shipping costs, and general overhead costs are assumed to be similar between the technologies
for the purpose of this analysis.

###### 11.4.1 Starting Material

Today, GaN transistors are produced on 150 mm substrates with a migration to 200 mm
diameter likely in the near future. Power MOSFETs are produced on anything from 100 mm
through 200 mm substrates by the many manufacturers in this business. Because the most costcompetitive GaN transistors use standard silicon substrates, there is no cost penalty compared
with power MOSFETs fabricated on similar diameter starting material. In fact, there is little
cost difference per unit area between 150 mm and 200 mm silicon wafers and, therefore, as far
as starting material is concerned, there is no real cost difference per wafer. If one considers the
fact that the GaN transistor has less device area than a silicon device with similar currentcarrying capability, then the cost per function is lower for GaN transistors than for comparable
Si MOSFETs.

###### 11.4.2 Epitaxial Growth

Silicon epitaxial growth is a mature technology with many companies making highly efficient
and automated machines. MOCVD GaN equipment is available from at least two sources,
Veeco in the US, and Aixtron in Germany. Both make capable and reliable machines whose
primary use has been the growth of GaN epitaxy used in the fabrication of LEDs. None of the
machines are optimized for GaN on silicon epitaxy, nor do they have levels of automation that
are common on silicon machines. As a result, GaN epitaxy on silicon is significantly more
expensive than silicon epitaxy today. But this is not fundamental. Processing times and
temperatures, wafer diameter, materials costs, and machine productivity are all on a fast track
of improvement and there is no fundamental limit preventing costs from being similar to silicon
epitaxial costs. Within the next few years, assuming widespread adoption of GaN transistors as


-----

a replacement for silicon power MOSFETs, it is expected that the cost of the GaN epitaxy will
approach that of silicon epitaxy.

###### 11.4.3 Wafer Fabrication

The simple structure of a GaN transistor, depicted in Chapter 1, is not difficult to build in a
standard low-cost silicon wafer fabrication facility. Processing temperatures are similar to
silicon BCDMOS, and cross-contamination can be managed easily. Today, GaN transistors are
processed in standard silicon wafer fabrication facilities side-by-side with silicon ICs and
power MOSFETs. In addition, the simple GaN transistor structure has many fewer processing
steps than a comparable state-of-the-art power MOSFET. As GaN transistor volumes grow, the
cost should become less than that of a leading-edge power MOSFET. The cascode GaN
transistor’s cost, however, is the sum of the cost of a GaN transistor and a silicon MOSFET, and
therefore, may remain higher than the wafer fabrication costs of either a monolithic GaN
transistor or a silicon MOSFET.

###### 11.4.4 Test and Assembly

Although in the assembly process, there are significant differences favoring the cost structure
of GaN transistors, the testing costs are equivalent.
Silicon power MOSFETs need a surrounding package, typically made of a copper
leadframe, some aluminum, gold, or copper wires, all in a molded epoxy envelope. Connections need to be made to the top and bottom of the vertical silicon device; the plastic molding is
needed to keep moisture from penetrating the active device, and there needs to be a means of
getting the heat out of the part. Traditional power MOSFET packages such as the SO8, TO220,
or DPAK, add cost, parasitic inductance, electrical and thermal resistance, and increase
reliability and quality risks to the product. As discussed in Chapters 1–4, GaN transistors
with a rated voltage of 200 V or less come in an LGA (WLCSP) format and can be used as a
“flip chip” without compromising the electrical, thermal, or reliability characteristics. Assembly costs for these devices, therefore, would be lower than their MOSFET counterparts.
Cascode devices discussed in Chapters 1, 2 and 10 are in more traditional power packages such
as TO-220 or PQFN package styles, and, as a result of the dual-chip packaging required to
accommodate both a GaN transistor and a MOSFET, are expected to cost somewhat more than
a MOSFET to assemble.
Table 11.1 summarizes the cost comparison and anticipates that costs for GaN transistors
will be lower in the case of a monolithic enhancement-mode transistor, and somewhat higher
for a cascode transistor. This comparison, however, does not take into account any differences
in yields. Manufacturing yields of GaN transistors are already close enough to MOSFET yields
such that, when considered in conjunction with the relative die size comparison presented in
Chapter 1, GaN transistors will most likely cost less to manufacture within a few years.

###### 11.5 GaN Transistors are Reliable

The cumulative reliability information available on silicon power MOSFETs is staggering.
Many years of work have been devoted to understanding failure mechanisms, controlling and
refining processes, and designing products that have distinguished themselves as the highly
reliable backbone of any power conversion system. GaN transistors are just a few years into this


-----

**Table 11.1** Summary of the cost difference between GaN transistor costs compared with silicon power
transistorsin2013andasanticipatedin2016.(a)monolithicenhancement-modetransistors,and(b)cascode
GaN transistors

Monolithic enhancement-mode Cascode GaN

2013 2016 2013 2016

Starting material lower lower Starting material same same
Epi growth higher same Epi growth higher same
Wafer fab same lower Wafer fab higher higher
Assembly lower lower Assembly higher higher
Overall higher lower Overall higher higher

journey. Results to date are excellent. Manufacturers have published results from their
qualification tests [3–7], and devices have been applied successfully to many RF and power
applications with good results. Some GaN transistors have also proved reliable under harsh
radiation exposure as discussed in Chapter 9. Reliability testing is rapidly demonstrating that
GaN technology is robust under a wide range of accelerated life-test conditions.

###### 11.6 Future Directions

The GaN technology journey is just beginning. There are profound improvements that can be
made in basic device performance as measured by figures of merit, Miller ratio, RDS(on) × area,
and cost. Still, we are far away from theoretical performance limits. It is quite reasonable to
expect factors of two or more reductions in the key figures of merit every two to four years.
Perhaps the greatest opportunity for GaN technology to impact the performance of power
conversion systems comes from the intrinsic ability to integrate both power-level and signallevel devices on the same substrate. As an example, Figure 11.2 is a top view of a monolithic
full-bridge power device in development. GaN technology, much like silicon-on-insulator
(SOI) technology, has no significant parasitic interaction between components, allowing
designers to easily develop monolithic power systems on a single chip.

**Figure 11.2** Monolithic full-bridge power device from EPC


![](GaN-transistors-power-conversion.pdf-253-0.png)

-----

###### 11.7 Conclusion

In the late 1970s, power MOSFET pioneers believed that they had a technology that would
displace bipolar transistors completely. Thirty-plus years later, plenty of applications remain
that prefer bipolar transistors over power MOSFETs, but the size of the power MOSFET
market is many times larger than the bipolar market. This is due to all the new applications and
new markets enabled by that breakthrough technology. Today, GaN technology is at that same
threshold. Like the power MOSFET of 1976, GaN manufacturers are at the beginning of an
exciting journey with new products and breakthrough capabilities almost monthly [8].
The power MOSFET is not dead, but it is nearing the end of the road for major improvements
in performance and cost. As more and more GaN transistor-based designs come to market and
GaN-on-silicon epitaxial growth technology matures, this technology will most probably
become dominant over the next decade due to its large advantages in both performance and cost
– advantage gaps that promise to widen as we quickly climb the learning curve.

###### References

1. Lidow, A. (2010) “Is it the end of the road for silicon in power management?” CIPS 2010 Conference, Nuremburg,
Germany, March 2010.
[2. Efficient Power Conversion Corporation, eGaN FET SPICE Models, Available from http://epc-co.com/epc/](http://epc-co.com/epc/DesignSupportbr/Device models.aspx)
[DesignSupportbr/Device models.aspx.](http://epc-co.com/epc/DesignSupportbr/Device models.aspx)
3. Yanping, Ma (2011) “EPC GaN Transistor Application Readiness: Phase One Testing,” reliability report, Available
[from http://epc-co.com/epc/documents/product-training/EPC_relreport_030510_finalfinal.pdf.](http://epc-co.com/epc/documents/product-training/EPC_Phase_Five_Rel_Report.pdf)
4. Yanping, Ma (2011) “EPC GaN Transistor Application Readiness: Phase Two Testing,” reliability report, Available
[from http://epc-co.com/epc/documents/product-training/EPC_Phase_Two_Rel_Report.pdf.](http://epc-co.com/epc/documents/product-training/EPC_Phase_Five_Rel_Report.pdf)
5. Yanping, Ma (2011) “EPC GaN Transistor Application Readiness: Phase Three Testing,” reliability report,
[Available from http://epc-co.com/epc/documents/product-training/EPC_Phase_Three_Rel_Report.pdf.](http://epc-co.com/epc/documents/product-training/EPC_Phase_Five_Rel_Report.pdf)
6. Yanping, Ma (2011) “EPC eGaN FETs Transistor Application Readiness: Phase Four Testing,” reliability report,
[Available from http://epc-co.com/epc/documents/product-training/EPC_Phase_Four_Rel_Report.pdf.](http://epc-co.com/epc/documents/product-training/EPC_Phase_Five_Rel_Report.pdf)
7. Yanping, Ma (2011) “EPC eGaN FETs Transistor Application Readiness: Phase Five Testing,” reliability report,
[Available from http://epc-co.com/epc/documents/product-training/EPC_Phase_Five_Rel_Report.pdf.](http://epc-co.com/epc/documents/product-training/EPC_Phase_Five_Rel_Report.pdf.)

8. Pitcher, G. (27 January, 2009) “Power to change – how GaN might revolutionize embedded power device design,”
_[New Electronics, Available from http://www.newelectronics.co.uk/electronics-technology/power-for-change/16806/.](http://www.newelectronics.co.uk/electronics-technology/power-for-change/16806/)_


-----

-----

###### Appendix Glossary of Terms


![](GaN-transistors-power-conversion.pdf-256-0.png)

-----

![](GaN-transistors-power-conversion.pdf-257-0.png)

-----

![](GaN-transistors-power-conversion.pdf-258-0.png)

-----

![](GaN-transistors-power-conversion.pdf-259-0.png)

-----

![](GaN-transistors-power-conversion.pdf-260-0.png)

-----

![](GaN-transistors-power-conversion.pdf-261-0.png)

-----

![](GaN-transistors-power-conversion.pdf-262-0.png)

-----

###### Index


A
Adoption rate, 232
Aixtron, 234
Aluminum gallium nitride (AlGaN), 2, 5–8, 10,
11, 24, 27
Aluminum nitride (AlN), 11
Anti-parallel diode, 90
Assembly process, 235
Available gain (GA ), 151, 162, 164, 165

B
B (Matching network shunt susceptance), 151
Bandgap energy, 3
Bias Tee, 157, 165–167
Bipolar transistor (BJT), 1, 237
Body diode, 31, 32, 44, 72, 90, 99, 118, 142,
205
Body diode losses, 32, 90, 106
Bootstrap diode, 44, 213, 220
Brick converter, 191, 193, 195, 196, 200, 204
Buck converter, 74, 75, 82, 104, 107, 108,
110, 111, 122, 125, 179, 187, 189,
212, 217, 233
Bus converter, 140, 142, 148, 192, 203
BVDSS (Drain-source breakdown voltage), 1

C
Capacitance, 19, 27, 28, 32, 50, 51, 71, 73, 93, 96,
107, 111, 134
Cascode, 7, 9, 22, 27, 31, 32, 39, 41
Circuit simulation, 123
CISS (Input capacitance), 28, 31, 93, 134
Class-A amplifier, 152, 155, 156
Class-D audio amplifier, 204, 206, 208
Common source inductance (CSI), 47, 55, 56,
101, 102
Commutation time, 91, 99
Compression points, 151, 155, 168–170
Conduction losses, 24, 61, 98, 100, 109, 120, 144,
145, 200, 204, 208, 224


Control FET, 104–106, 157
Core losses, 109, 122, 200
COSS (output capacitance), 31, 96, 134
Cost, 1, 11, 14, 15, 86, 170, 197, 208, 220, 234,
235, 237
Critical electric field (EBR), 3, 19, 232
CRSS (Reverse transfer capacitance), 31, 134
Current commutation, 110, 112, 137, 211,
226

D
DC-DC converter, 1, 129, 131, 133, 136, 179,
185, 191, 204, 210
Dead-time, 44, 97, 98, 107, 112, 113, 119, 125
Depletion mode, 2, 6, 9, 52, 53, 150, 173
Device characteristics, 70
di/dt, 33, 47, 48, 53, 83, 212
Dielectric, 4, 13, 20, 21
Diode recovery charge (QRR), 32, 99, 106, 226,
227
DirectFET, 76
d-mode, 6, 27
Drain efficiency (ηD), 151, 152, 168– 170
Drain-source breakdown voltage (BVDSS), 1, 23
Drain-source leakage current (IDSS ), 174
Drift region, 3, 4
Dual-sided cooling, 78
Duty cycle, 23, 37, 107, 112, 120, 121, 144, 145,
147, 148, 200, 204
dv/dt, 46, 47, 50, 53, 183, 210 –212
Dynamic losses, 89, 100, 111, 119, 120, 124

E
EBR (Critical electric field), 3, 19, 232
Effective dead-time between transistor switching
(teff ), 90, 98, 99, 118
Efficiency, 1–3, 14, 33, 60, 75, 107, 125, 145,
150
Efficient power conversion corporation (EPC), 2,
14, 22, 233, 236


_GaN Transistors for Efficient Power Conversion, Second Edition._
Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch.
© Alex Lidow, Johan Strydom, Michael de Rooij, and David Reusch. Published 2015 by John Wiley & Sons, Ltd.
Companion Website: [http://www.wiley.com/go/gan_transistors](http://www.wiley.com/go/gan_transistors)


-----

eGaN FET, 2, 37, 168, 170, 174, 175
Eighth brick, 189, 191, 193–195, 198
Electrically equivalent circuit thermal model, 77,
79–83
Electron mobility (μ), 2, 3
EMI (electromagnetic interference), 105
Enhancement mode (e-mode), 2, 7–10, 12, 13, 21,
27, 41, 52, 70, 99, 106, 107, 156, 162, 163,
170, 173, 176, 177, 225
GaN transistor, 10, 12, 20, 22, 25, 27, 43, 91,
106, 118, 134, 152, 177, 218
Envelope tracking, 82, 208, 228, 233
Epitaxial growth, 234, 237
Equivalent circuit, 65, 70–72, 83, 214
Eudyna, 2

F
Fall time, 53, 90, 118, 205
Fall time for current (tCF), 90
Fall time for voltage (tVF), 39, 90, 93
FET drivers, 152, 159, 223
Field plate, 13, 29
Figure of merit (FOM), 1, 100, 137, 223
Forward gain (s21), 151, 158, 160, 163
FR4, 34, 36
fSW (Switching frequency), 90, 91, 93, 104, 107,
109, 117, 119, 124, 136, 182, 185, 192, 193,
197, 200, 203, 208, 212, 213
Full-bridge, 193, 194, 236

G
Gallium nitride (GaN), 2, 5, 8, 48
Gamma irradiation, 177
Gamma radiation, 173, 175, 177
GaN on silicon, 2, 234, 237
Gate-drain charge (QGD), 30, 40, 90, 92, 96,
100, 114–116, 124, 134, 143, 177,
210, 228
Gate drive, 30, 31, 41, 48
Gate drive loop inductance (LG), 41, 42, 51
Gate driver on-state output voltage (VDR),
90, 93, 95, 96, 116, 117, 119, 120,
124, 136
Gate plateau voltage (VPL), 39, 90, 93–96, 116,
120, 124, 125
Gate resistance (RG), 41, 42, 45, 48, 71, 103, 111,
123, 136
Gate-source charge (QGS), 30, 40, 94, 114
gm (Transconductance), 90, 103, 123


Ground bounce, 48–50, 56
GT (Transducer power gain), 151, 160
GTU (Unilateral transducer power gain), 151,
160

H
Half-brick, 193, 196, 197, 199–202
Half-bridge, 43, 44, 50, 55, 65, 68, 69, 101, 206,
211, 224
converter, 67, 68
Hard-switching, 48, 61, 89, 90, 92, 99–102
figure of merit, 100
Heatsink, 33–35, 76–79, 82, 216, 217
Heavy ion bombardment, 177
HEMT (High electron mobility transistors), 2, 5,
8, 10, 14, 19, 21, 24
Heterostructure, 2, 5, 19, 24
High efficiency, 39, 60, 184, 208
High electron mobility transistor (HEMT), 2, 5

I
IBC (Intermediate bus converter), 128, 191
Infineon, 1, 23, 24, 27, 29, 35, 134
Input capacitance (CISS), 28, 29, 31, 93, 103, 134,
136, 216
Input reflection coefficient (Γin), 151, 159–161
Input side matching reflection coefficient (ΓS),
151, 159, 161, 162, 164, 166
Interleaving, 57, 61, 197
Intermediate bus converter (IBC), 128, 191–193
Isolated DC-DC converter, 142, 191, 204

J
Junction gate field-effect transistor (JFET),
173
Junction temperature, 37, 79, 80
Junction-to-ambient thermal resistance (RθJA), 33,
36, 81
Junction-to-board thermal resistance (RθJB),
36
Junction-to-case thermal resistance (RθJC), 36

K
K (Rollett stability factor), 151, 158, 163

L
Land grid array (LGA), 16, 35, 56
LDMOS, 52, 150, 168, 170
Lead inductance, 57
LET (Linear energy transfer), 173, 175, 176


-----

LG (Gate drive loop inductance), 63
LGA (Land Grid Array), 104
LiDAR, 224–226, 228, 233
Linear energy transfer (LET), 173, 175, 176
LLC resonant converter, 130, 203, 204
LM5113, 198
LTSPICE, 74, 86, 220, 223

M
Magnetic field self-cancellation, 57, 60, 61, 65
Magnetics, 109, 213
Matching network, 159, 161, 165–168, 221
series reactance (X), 151, 166, 167
shunt susceptance (B), 151
Maximum stable gain (GMSG), 151, 164
Miller charge, 92, 143
Miller charge ratio (QGD/QGS), 46
Miller turn-on, 45, 46
Monolithic enhancement mode, 236
Monolithic full-bridge, 236
MOSFET, 1, 2, 9, 10, 23–25, 31
Motor drive, 1, 228

N
NASA, 172, 173
Nitronex, 2, 150, 154
Non-isolated DC-DC Converter, 179
Normalized unilateral transducer gain (gu), 151,
160, 161, 163

O
On-resistance (RDS(on)), 1, 4, 19, 25, 37
Operating temperature, 3
Output characteristics, 72
Output charge (QOSS), 31, 90, 128, 133, 138,
148
Output port reflection coefficient (s22), 151, 159,
160, 163
Output reflection coefficient (Γout), 151, 159–161,
164–166
Output RF power (PRFout), 151, 152
Output ripple, 197, 200
Output side matching reflection coefficient (ΓL),
151
Output side matching reflection coefficient (ΓL),
151, 159, 161, 162, 164–166

P
Package inductance, 104, 144
Paralleling, 61, 62, 65, 66, 186, 189, 197


Parasitic inductance, 52, 53, 55, 58, 61, 73, 75, 85,
87, 104, 107, 142, 181, 233, 235
PConduction (Power loss due to static conduction
loss), 90, 100, 120–122
PCOSS (Power losses due to output charge QOSS),
89, 90
PDC (DC power delivered to the RF transistor),
151, 152
PDQ (Power losses at the quiescent operating
point), 151
PDynamic (Power loss due to dynamic loss
components), 90, 120
PG (Power losses due to gate charge QG), 89, 90,
96, 99, 113, 117
pGaN Gate enhancement-mode structure, 7, 8, 12,
13, 173, 175
Photovoltaic inverter, 228
Plateau voltage at the operating condition current
(VPL(op)), 90, 94, 114
Point-of-load converter (POL), 140, 179, 180,
184, 192, 228
Pon (power losses due to the turn on switching
transition), 90, 96, 113, 119, 121, 124
Power factor correction, 226, 228, 233
Power loop, 14, 41, 48, 51, 55, 59, 60, 65, 68,
181, 182, 187, 210
inductance, 55, 58, 69, 75, 87, 103, 104, 210,
234
Power over ethernet (PoE), 193
PQFN package, 55, 76, 78, 235
PRFout (Output RF power), 151, 152
PRR (Power losses due to the reverse recovery
charge of the body diode), 89–91, 99, 100
PSD (Power losses due to the forward drop of the
body diode), 89, 90, 97, 99, 113, 117, 119,
121
PSW (Total power losses during switching
transitions), 90, 91, 96, 99, 119
Pulse width distortion, 50
PWM (Pulse width modulation), 110, 132, 133,
205

Q
QG (Total gate charge required to drive a device
from zero to rated gate voltage), 40, 41, 90,
114, 136, 138
QGD (Charge required into the gate to bring the
drain voltage down from stated drain
voltage to near zero), 30, 46, 114, 115,
137, 210


-----

QG(op) (Total gate charge required to drive a
device from zero to rated gate voltage based
on the operating conditions), 90, 115, 116
QGS (Charge required to increase gate voltage to
the plateau voltage), 30, 90, 94, 114
QGS1 (Charge required to increase gate voltage
from zero to the stated threshold voltage of
the device), 40, 46, 91, 94, 95, 210
QGS2 (Charge required to increase gate voltage
from the stated threshold voltage of the
device to the plateau voltage), 40, 90, 91, 94,
103, 115, 136, 137, 148, 226
QGS(op) (Charge required to increase gate voltage
to the operating plateau voltage), 90, 94, 95,
114
QRR (Diode recovery charge), 32, 99, 107, 226

R
Rad-hard Si MOSFET, 176
Radiation hardened, 177
Radiation resistance, 172
Radiation tolerance, 173, 176
RA (Radius of the constant available gain circle on
a Smith chart), 151, 162
RDS(on) (On-resistance), 1, 4, 19, 24, 25, 37
Rectifier, 2, 100, 107, 111, 112, 118, 124, 185,
189, 227
Reliability, 15, 191, 236
Resonant converter, 129, 132, 141, 203, 217
Resonant tank, 41, 47, 84, 132
Reverse conduction, 10, 19, 31, 97, 98, 100, 119
Reverse diode conduction time (tSD), 90, 97, 98
Reverse gain (S12), 151, 155
Reverse recovery charge (QRR), 33, 99, 192
Reverse transfer capacitance (CRSS), 31, 134
RF circuit gate quiescent bias point (VGSQ), 151,
152
RF power gain, 151, 154
RF transistor, 2, 150–152, 154, 155, 159
RG (Gate resistance), 41, 42, 48, 103, 111, 136
Ripple, 112, 122
Rise time for current (tCR), 90
Rise time for voltage (tVR), 90, 93
RθJA(Junction-to-ambient thermal resistance),
33, 81
RθJB (Junction-to-board thermal resistance), 36,
37
RθJC (Junction-to-case thermal resistance), 33,
36
Rollett stability factor (K), 151, 158, 163


S
s11 (Input port reflection coefficient), 160
s12 (Reverse gain), 151, 155, 160, 162
s21 (Forward gain), 151, 160
s22 (Output port reflection coefficient), 151, 160,
161
Schottky, 6–8, 24, 27, 44, 107, 108, 118, 173,
175, 176
Shoot-through, 45, 48, 97, 107, 207
Silicon carbide (SiC), 2–4, 10, 11
Silicon-on-insulator (SOI), 236
Simulations, 74, 75, 123, 223
Single event burnout (SEB), 175
Single-event effects (SEE), 175
Single event gate rupture (SEGR), 175
Smith chart, 154, 158, 159, 165
Soft-switching, 45, 128–130, 133, 135, 138, 140,
143, 177, 179, 204, 219, 223
figure of merit, 140, 223
Solder bar, 14–16, 35, 56, 57
S-parameters, 152–155, 158, 160, 161, 163,
216
SPICE models, 70, 72, 85
Stability, 73, 155, 158, 159, 164
Stability circle, 158, 159, 164
Switching efficiency, 3
Switching energy, 124
Switching figure of merit (FOM), 100, 140, 223
Switching frequency (fSW), 90, 109, 132, 141,
142, 179, 186, 190, 192, 193, 196, 197, 200,
203, 205, 208, 216
Switching losses, 91, 92, 94, 101, 119, 121, 133,
192, 203, 205, 226
Synchronous rectifier, 104–106, 110, 112, 116,
119–121, 124, 184, 185, 193

T
tCF (Fall time for current), 90
tCR (Rise time for current), 39, 90
teff (Effective dead-time between transistor
switching), 90
Temperature coefficient, 25, 32, 64, 233
Thermal interface material, 33–36, 76,
78, 79
Thermal limit, 170
Thermal resistance, 33–37, 76–82, 235
junction-to-ambient (RθJA), 33, 81
junction-to-board (RθJB), 33, 37
junction-to-case (RθJC), 33
TJ (junction temperature), 37, 80


-----

Total gate charge (QG), 41, 90, 114, 136, 138
Total incident dose (TID), 173
Total power losses during switching transitions
(PSW), 90, 91, 96, 99, 119
Transconductance (gm), 90, 103, 123
Transducer power gain (GT), 151, 160
Transient response, 179, 186, 190
Transient thermal impedance, 36
Triquint, 150
tSD (Reverse diode conduction time), 90, 97, 98
tVF (Fall time for voltage across the transistor), 39,
90, 93
tVR (Rise time for voltage across the transistor),
90, 93
Two-dimensional electron gas (2DEG), 2, 4
Two-port network, 153, 154
Two-stage converter, 200, 201
tZVS (Zero voltage switching transition time), 90,
133

U
Unilateral figure of merit (U), 151, 161
Unilateral transducer power gain (GTU), 151,
160

V
VDR (Gate driver on-state output voltage), 90, 93
Veeco, 234


VGSQ (RF circuit quiescent bias point), 151, 152
Vias, 13, 57, 61, 63, 78
Voltage overshoot, 75, 105, 182–184
Voltage probes, 84
Voltage ringing, 42
VPL (Gate plateau voltage), 39, 90, 93–96, 116,
120, 124–125
VPL(op) (Plateau voltage at the operating condition
current), 90, 94, 114

W
Wafer fabrication, 235
Wafer level chip-scale package, 56
Wide band gap semiconductor, 3
Wireless energy transfer, 214–219, 221–224

X
X (Matching network series reactance), 151, 166,
167

Z
Zero-current switching (ZCS), 128–133, 137, 142,
203
Zero-voltage switching (ZVS), 97–99, 128, 129,
132–136, 142, 144, 147, 203, 204, 216–222,
224
Zero voltage switching transition time (tZVS),
90, 133


-----

