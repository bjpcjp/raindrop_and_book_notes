# Chapter 18

 Ngspice User Interfaces

ngspice offers a variety of user interfaces. For an overview (several screen shots) please have a
[look at the ngspice web page.](http://sourceforge.net/project/screenshots.php?group_id=38962)

## 18.1 MS Windows Graphical User Interface

If compiled properly (e.g. using the --with-wingui flag for ./configure under MINGW),
ngspice for Windows offers a simple graphical user interface. In fact this interface does not
offer much more for data input than a console would offer, e.g. command line inputs, command
history and program text output. First of all it applies the Windows api for data plotting. If you
run the sample input file given below, you will get an output as shown in Fig. 18.1.

Input file:
```
   ***** Single NMOS Transistor For BSIM3V3.1
   ***** general purpose check (Id-Vd) ***
  *
   *** circuit description ***
  m1 2 1 3 0 n1 L=0.6u W=10.0u
   vgs 1 0 3.5
   vds 2 0 3.5
   vss 3 0 0
  *
  .dc vds 0 3.5 0.05 vgs 0 3.5 0.5
  *
  .control
   run
   plot vss#branch
  .endc
  *
  * UCB parameters BSIM3v3.2
  .include ../Exam_BSIM3/Modelcards/modelcard.nmos
  .include ../Exam_BSIM3/Modelcards/modelcard.pmos
  *
  .end

```

-----

The GUI consists of an I/O port (lower window) and a graphics window, created by the plot
command.

Figure 18.1: MS Windows GUI

The output window displays messages issued by ngspice. You may scroll the window to get
more of the text. The input box (white box) may be activated by a mouse click to accept any
of the valid ngspice commends. The lower left output bar displays the actual input file. ngspice
progress during setup and simulation is shown in the progress window (--ready--). The Quit
button allow to interrupt ngspice. If ngspice is actively simulating, due to using only a single
thread, this interrupt has to wait until the window is accessible from within ngspice, e.g. during
an update of the progress window.

In the plot window there is the upper left button, which activated a drop down menu. You may
select to print the plot window shown (a very simple printer interface, to be improved), set
up any of the printers available on your computer, or issue a postscript file of the actual plot
window, either black&white or colored.


![](NGS-ch18-ngspice-ui.pdf-1-0.png)

-----

Instead of plotting with black background, you may set the background to any other color,
preferably to ‘white’ using the command shown below.

Input file modification for white background:
```
  .control
   run
  * white background
   set color0=white
  * black grid and text (only needed with X11, automatic with MS Win)
   set color1=black
  * wider grid and plot lines
   set xbrushwidth=2
   plot vss#branch
  .endc

```
Figure 18.2: Plotting with white background

## 18.2 MS Windows Console

If the --with-wingui flag for ./configure under MINGW is omitted (see 32.2.5) or console_debug or console_release is selected in the MS Visual Studio configuration manager, then
ngspice will compile without any internal graphical input or output capability. This may be useful if you apply ngspice in a pipe inside the MSYS window, or use it being called from another
program, and just generating output files from a given input. The plot (17.5.45) command will
not do and leads to an error message.


![](NGS-ch18-ngspice-ui.pdf-2-0.png)

-----

Only on the ngspice console binary in MS Windows input/output redirection is possible, if
ngspice is called (e.g. within a MSYS shell or from a shell script) like
```
$ ngspice < input.

```
This feature is used in the new CMC model test suite (to be described elsewhere), thus requires
a console binary.

You still may generate graphics output plots or prints by gnuplot (17.5.28), if installed properly
(18.7), or by selecting a suitable printing option (18.6).

## 18.3 Linux

The standard user interface is a console for input and the X11 graphics system for output with
the interactive plot (17.5.45) command. If ngspice is compiled with the –without-x flag for
./configure, a console application without graphical interface results. For more sophisticated
input user interfaces please have a look at Chapt. 18.8.

## 18.4 CygWin

The CygWin interface is similar to the Linux interface (18.3), i.e. console input and X11
graphics output. To avoid the warning of a missing graphical user interface, you have to start
the X11 window manager by issuing the commands
```
$ export DISPLAY=:0.0
$ xwin -multiwindow -clipboard &

```
inside of the CygWin window before starting ngspice.

## 18.5 Error handling

Error messages and error handling in ngspice have grown over the years, include a lot of ‘traditional’ behavior and thus are not very systematic and consistent.

Error messages may occur with the token ‘Error:’. Often the errors are non-recoverable and will
lead to exiting ngspice with error code 1. Sometimes, however, you will get an error message,
but ngspice will continue, and may either bail out later because the error has propagated into
the simulation, sometimes ngspice will continue, deliver wrong results and exit with error code
0 (no error detected!).

In addition ngspice may issue warning messages like ‘Warning: ...’. These should cover recoverable errors only.

So there is still work to be done to define a consistent error messaging, recovery or exiting. A
first step is the user definable variable strict_errorhandling. This variable may be set in files
spinit (16.5) or .spiceinit (16.6) to immediately stop ngspice, after an error is detected during
parsing the circuit. An error message is sent, the ngspice exit code is 1. This behavior deviates
from traditional SPICE error handling and thus is introduced as an option only.

XSPICE error messages are explained in Chapt. 29.


-----

## 18.6 Postscript printing options

[This info is compiled from Roger L. Traylor’s web page. All the commands and variables you](http://web.engr.oregonstate.edu/~traylor/ece391/ngspice_printing)
can set are described in Chapt. 17.5. The corresponding input file for the examples given below
is listed in Chapt. 21.1. Just add the .control section to this file and run in interactive mode
by
```
$ ngspice xspice_c1_print.cir

```
One way is to setup your printing like this:
```
.control
set hcopydevtype=postscript
op
run
plot vcc coll emit
hardcopy temp.ps vcc coll emit
.endc

```
Then print the postscript file temp.ps to a postscript printer.

You can add color traces to it if you wish:
```
  .control
  set hcopydevtype=postscript
  * allow color and set background color if set to value > 0
  set hcopypscolor=1
  *color0 is background color
  *color1 is the grid and text color
  *colors 2-15 are for the vectors
  set color0=rgb:f/f/f
  set color1=rgb:0/0/0
  op
  run
  hardcopy temp.ps vcc coll emit
  .endc

```
Then print the postscript file temp.ps to a postscript printer.

You can also direct your output directly to a designated printer (not available in MS Windows):
```
  .control
  set hcopydevtype=postscript
  *send output to the printer kec3112-clr
  set hcopydev=kec3112-clr
  hardcopy out.tmp vcc coll emit

```

-----

## 18.7 Gnuplot

[Install Gnuplot (on Linux available from the distribution, on Windows available here). On Win-](http://www.tatsuromatsuoka.com/gnuplot/Eng/winbin/)
dows expand the zip file to a directory of your choice, add the path <any directory>/gnuplot/bin
to the PATH variable, and go... The command to invoke Gnuplot (17.5.28) is limited however
to x/y plots (no polar etc.).

## 18.8 Integration with CAD software and ‘third party’ GUIs

In this chapter you will find some links and comments on GUIs for ngspice offered from other
projects and on the integration of ngspice into a circuit development flow. The data given rely
mostly on information available from the web and thus is out of our control. It also may be far
from complete. For a list of actual links with more than 20 entries please have a look at the
[ngspice web pages. Some open source tools are listed here. The GUIs MSEspice and GNUSpi-](http://ngspice.sourceforge.net/resources.html)
ceGUI help you to navigate the commands to need to perform your simulation. XCircuit and the
GEDA tools gschem and gnetlist offer integrating schematic capture and simulation. KiCAD
offers a complete design environment for electronic circuits.

### 18.8.1 KiCad

[KiCad is a cross platform and open source electronics design automation suite. Its schematic](http://kicad-pcb.org/)
editor Eeschema fully integrates shared ngspice (see Chapt. 19) as the simulation tool. Whereas
this feature is not yet part of the actual KiCad release, the code is already available in the master
branch, and also compiled as a nightly build for MS Windows.

### 18.8.2 GNU Spice GUI

[A GUI, to be found at http://sourceforge.net/projects/gspiceui/. It aids in viewing, modifying,](http://sourceforge.net/projects/gspiceui/)
and simulating SPICE CIRCUIT files.

### 18.8.3 XCircuit

[CYGWIN and especially Linux users may find XCircuit valuable to establish a development](http://opencircuitdesign.com/xcircuit/)
[flow including schematic capture and circuit simulation.](http://opencircuitdesign.com/xcircuit/tutorial/tutorial2.html)

### 18.8.4 GEDA

[The gEDA project is developing a full GPL‘d suite and toolkit of Electronic Design Automation](http://www.gpleda.org/)
tools for use with a Linux. Ngspice may be integrated into the development flow. Two web sites
offer tutorials using gschem and gnetlist with ngspice:

[http://geda.seul.org/wiki/geda:csygas](http://geda.seul.org/wiki/geda:csygas)

[http://geda.seul.org/wiki/geda:ngspice_and_gschem](http://geda.seul.org/wiki/geda:ngspice_and_gschem)


-----

### 18.8.5 MSEspice

[A graphical front end to ngspice, using the Free Pascal cross platform RAD environment](http://sourceforge.net/projects/mseuniverse/)
[MSEide+MSEgui.](http://mseide-msegui.sourceforge.net/)

### 18.8.6 GNU Octave

[GNU Octave is a high-level language, primarily intended for numerical computations. An](http://www.gnu.org/software/octave)
[interface to ngspice is available here.](https://www.dsprelated.com/showarticle/707.php)


-----

