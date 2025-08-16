# Chapter 13

 Verilog A Device models

## 13.1 Introduction

[The ngspice-adms interface will implement extra HICUM level0 and level2 (HICUM model](http://www.iee.et.tu-dresden.de/iee/eb/hic_new/hic_intro.html)
[web page), MEXTRAM(MEXTRAM model web page), EKV(EKV model web page) and](http://www.iee.et.tu-dresden.de/iee/eb/hic_new/hic_intro.html)
[PSP(NXP MOS model 9 web page) models written in Verilog-A behavior language.](http://www.nxp.com/models/mos_models/model9/index.html)

## 13.2 adms

To compile Verilog-A compact models into ngspice-ready C models the the program admsXml
[is required. Details of this software are described in adms home page.](http://mot-adms.sourceforge.net)

## 13.3 How to integrate a Verilog-A model into ngspice

### 13.3.1 How to setup a *.va model for ngspice

The root entry for new Verilog-A models is \src\spicelib\devices\adms. Below the modelname entry the Verilog-A code should reside in folder admsva
(e.g.: ngspice\src\spicelib\devices\adms\ekv\admsva\ekv.va). The file extension is fixed
to .va.

Certain files must modified to create the interface to ngspice - see the guideline README.adms
in the ngspice root.

### 13.3.2 Adding admsXml to your build environment

To facilitate the installation of adms, a source code package has been assembled for use with ng[spice, available as a zip file for download. It is based on adms source code from the subversion](http://ngspice.sourceforge.net/adms2/adms-svn-ngspice-src.zip)
repository downloaded on August 1st, 2010, and has been slightly modified (see ChangeLog).

Under OS Linux (tested with SUSE 11.2, 64 bit) you may expand the zip file and run
```
./autogen_lin.sh, followed by ’make’ and ’make install’.

```

-----

Under OS CYGWIN (tested with actual CYGWIN on MS Windows 7, 64 bit), please use
```
./autogen_cyg.sh, followed by ’make’ and ’make install’.

```
Under OS MINGW, a direct compilation would require the additional installation of perl module
XML-LibXML, which is not as straightforward as it should be. However you may start with a
CYGWIN compile as described above. If you then go to your MSYS window, cd to the adms
top directory and start ./mingw-compile.sh, you will obtain admsXml.exe, copied to MSYS
/bin, and you are ready to go. To facilitate installation under MS Windows, a admsXml.exe
[zipped binary is available. Just copy it to MSYS /bin directory and start working on your verilog](http://ngspice.sourceforge.net/adms2/adms-admsXml-Win32-bin.zip)
models.

A short test of a successful installation is:
```
$ admsXml -v
$ [usage..] release name="admsXml" version="2.3.0" date="Aug 4 2010"
time="10:24:18"

```
Compilation of admsXml with MS Visual Studio is not possible, because the source code has
variable declarations not only at the top of a block, but deliberately also in the following lines.
This is ok by the C99 standard, but not supported by MS Visual Studio.


-----

