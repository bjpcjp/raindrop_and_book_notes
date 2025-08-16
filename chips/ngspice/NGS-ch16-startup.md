# Chapter 16

 Starting ngspice

## 16.1 Introduction

Ngspice consists of the simulator and a front-end for data analysis and plotting. Input to the
simulator is a netlist file, including commands for circuit analysis and output control. Interactive
ngspice can plot data from a simulation on a PC or a workstation display.

Ngspice on Linux (and OSs like Cygwin, BCD, Solaris ...) uses the X Window System for
plotting (see Chapt. 18.3) if the environment variable DISPLAY is available. Otherwise, a console mode (non-graphical) interface is used. If you are using X on a workstation, the DISPLAY
variable should already be set; if you want to display graphics on a system different from the
one you are running ngspice or ngutmeg on, DISPLAY should be of the form machine:0.0. See
the appropriate documentation on the X Window System for more details.

The MS Windows versions of ngspice and ngnutmeg will have a native graphics interface (see
Chapt. 18.1).

The front-end may be run as a separate ‘stand-alone’ program under the name ngnutmeg. ngnutmeg is a subset of ngspice dedicated to data evaluation, still made available for historical
reasons. Ngnutmeg will read in the ‘raw’ data output file created by ngspice -r or by the write
command during an interactive ngspice session.

## 16.2 Where to obtain ngspice

[The actual distribution of ngspice may be downloaded from the ngspice download web page.](http://sourceforge.net/projects/ngspice/files/)
The installation for Linux or MS Windows is described in the file INSTALL to be found in
the top level directory. You may also have a look at Chapt. 32 of this manual for compiling
instructions.

If you want to check out the source code that is actually under development, you may have a
look at the ngspice source code repository, which is stored using the Git Source Code Mana[gement (SCM) tool. The Git repository may be browsed on the Git web page, also useful for](http://sourceforge.net/scm/?type=git&group_id=38962)
downloading individual files. You may however download (or clone) the complete repository
including all source code trees from the console window (Linux, CYGWIN or MSYS/MINGW)
by issuing the command (in a single line)


-----

```
git clone git://git.code.sf.net/p/ngspice/ngspice

```
You need to have Git installed, which is available for all three OSs. The whole source tree
is then available in <current directory>/ngspice. Compilation and local installation is again
described in INSTALL (or Chapt. 32). If you later want to update your files and download the
recent changes from sourceforge into your local repository, cd into the ngspice directory and
just type
```
git pull

```
git pull will deny to overwrite modified files in your working directory. To drop your local
changes first, you can run
```
git reset --hard

```
To learn more about git, which can be both powerful and difficult to master, please consult
[http://git-scm.com/, especially: http://git-scm.com/documentation, which has pointers to docu-](http://git-scm.com/)
mentation and tutorials.

## 16.3 Command line options for starting ngspice and ngnut- meg

Command Synopsis:
```
   ngspice [ -o logfile] [ -r rawfile] [ -b ] [ -i ] [ input files ]
   ngnutmeg [ - ] [ datafile ... ]

```
Options are:


-----

|Option|Long option|Meaning|
|---|---|---|
|-||Don’t try to load the default data file ("rawspice.raw") if no other files are given (ngnutmeg only).|
|-n|--no-spiceinit|Don’t try to source the file .spiceinit upon start-up. Normally ngspice and ngnutmeg try to find the file in the current directory, and if it is not found then in the user’s home directory (obsolete).|
|-t TERM|--terminal=TERM|The program is being run on a terminal with mfb name term (obsolete).|
|-b|--batch|Run in batch mode. Ngspice reads the default input source (e.g. keyboard) or reads the given input file and performs the analyses specified; output is either Spice2-like line-printer plots ("ascii plots") or a ngspice rawfile. See the following section for details. Note that if the input source is not a terminal (e.g. using the IO redirection notation of "<") ngspice defaults to batch mode (-i overrides). This option is valid for ngspice only.|
|-s|--server|Run in server mode. This is like batch mode, except that a temporary rawfile is used and then written to the standard output, preceded by a line with a single "@", after the simulation is done. This mode is used by the ngspice daemon. This option is valid for ngspice only. Example for using pipes from the console window: cat adder.cir|ngspice -s|more|
|-i|--interactive|Run in interactive mode. This is useful if the standard input is not a terminal but interactive mode is desired. Command completion is not available unless the standard input is a terminal, however. This option is valid for ngspice only.|
|-r FILE|--rawfile=FILE|Use rawfile as the default file into which the results of the simulation are saved. This option is valid for ngspice only.|
|-p|--pipe|Allow a program (e.g., xcircuit) to act as a GUI frontend for ngspice through a pipe. Thus ngspice will assume that the input pipe is a tty and allows to run in interactive mode.|
|-o FILE|--output=FILE|All logs generated during a batch run (-b) will be saved in outfile.|
|-h|--help|A short help statement of the command line syntax.|
|-v|--version|Prints a version information.|
|-a|--autorun|Start simulation immediately, as if a control section .control run .endc had been added to the input file.|
||--soa-log=FILE|output from Safe Operating Area (SOA) check|


Further arguments to ngspice are taken to be ngspice input files, which are read and saved (if
running in batch mode then they are run immediately). Ngspice accepts Spice3 (and also most
Spice2) input files, and outputs ASCII plots, Fourier analyses, and node printouts as specified
in .plot, .four, and .print cards. If an out parameter is given on a .width card (15.6.7),


-----

the effect is the same as set width = .... Since ngspice ASCII plots do not use multiple ranges,
however, if vectors together on a .plot card have different ranges they do not provide as much
information as they do in a scalable graphics plot.

For ngnutmeg, further arguments are taken to be data files in binary or ASCII raw file format
(generated with -r in batch mode or the write (see 17.5.89) command) that are loaded into ngnutmeg. If the file is in binary format, it may be only partially completed (useful for examining
output before the simulation is finished). One file may contain any number of data sets from
different analyses.

## 16.4 Starting options

### 16.4.1 Batch mode

Let’s take as an example the Four-Bit binary adder MOS circuit shown in Chapt. 21.6, stored
in a file adder-mos.cir. You may start the simulation immediately by calling
```
ngspice -b -r adder.raw -o adder.log adder-mos.cir

```
ngspice will start, simulate according to the .tran command and store the output data in a
rawfile adder.raw. Comments, warnings and infos go to log file adder.log. Commands for batch
mode operation are described in Chapt. 15.

### 16.4.2 Interactive mode

If you call
```
ngspice

```
ngspice will start, load spinit (16.5) and .spiceinit (16.6, if available), and then waits for your
manual input. Any of the commands described in 17.5 may be chosen, but many of them are
useful only after a circuit has been loaded by
```
ngspice 1 -> source adder-mos.cir

```
others require the simulation being done already (e.g. plot):
```
ngspice 2 ->run
ngspice 3 ->plot allv

```
If you call ngspice from the command line with a circuit file as parameter:
```
ngspice adder-mos.cir

```
ngspice will start, load the circuit file, parse the circuit (same circuit file as above, containing
only dot commands (see Chapt. 15) for analysis and output control). ngspice then just waits for
your input. You may start the simulation by issuing the run command. Following completion
of the simulation you may analyze the data by any of the commands given in Chapt. 17.5.


-----

### 16.4.3 Control mode (Interactive mode with control file or control section)

If you add the following control section to your input file adder-mos.cir, you may call
```
ngspice adder-mos.cir

```
from the command line and see ngspice starting, simulating and then plotting immediately.

Control section:
```
  * ADDER - 4 BIT ALL-NAND-GATE BINARY ADDER
  .control
   unset askquit
   save vcc#branch
   run
   plot vcc#branch
   rusage all
  .endc

```
Any suitable command listed in Chapt. 17.5 may be added to the control section, as well as
control structures described in Chapt. 17.6. Batch-like behavior may be obtained by changing
the control section to

Control section with batch-like behavior:
```
  * ADDER - 4 BIT ALL-NAND-GATE BINARY ADDER
  .control
   unset askquit
   save vcc#branch
   run
   write adder.raw vcc#branch
   quit
  .endc

```
If you put this control section into a file, say adder-start.sp, you may just add the line
```
.include adder-start.sp

```
to your input file adder-mos.cir to obtain the batch-like behavior. In the following example
the line .tran ... from the input file is overridden by the tran command given in the control
section.

Control section overriding the .tran command:
```
  * ADDER - 4 BIT ALL-NAND-GATE BINARY ADDER
  .control
   unset askquit
   save vcc#branch
   tran 1n 500n
   plot vcc#branch
   rusage all
  .endc

```

-----

The commands within the .control section are executed in the order they are listed and only
**after the circuit has been read in and parsed. If you want to have a command being executed**
**before circuit parsing, you may use the prefix pre_ (17.5.46) to the command.**

A warning is due however: If your circuit file contains such a control section (.control ...
```
.endc), you should not start ngspice in batch mode (with -b as parameter). The outcome may

```
be unpredictable!

## 16.5 Standard configuration file spinit

At startup ngspice reads its configuration file spinit. spinit may be found in a path relative to
the location of the ngspice executable
..\share\ngspice\scripts. The path may be overridden by setting the environmental variable
SPICE_SCRIPTS to a path where spinit is located. Ngspice for Windows will additionally
search for spinit in the directory where ngspice.exe resides. If spinit is not found a warning
message is issued, but ngspice continues.

Standard spinit contents:
```
  * Standard ngspice init file
   alias exit quit
   alias acct rusage all
  ** set the number of threads in openmp
  ** default (if compiled with --enable-openmp) is: 2
   set num_threads=4
  if $?sharedmode
    unset interactive
    unset moremode
   else
    set interactive
    set x11lineararcs
   end
   strcmp __flag $program "ngspice"
  if $__flag = 0
   codemodel ../lib/spice/spice2poly.cm
   codemodel ../lib/spice/analog.cm
   codemodel ../lib/spice/digital.cm
   codemodel ../lib/spice/xtradev.cm
   codemodel ../lib/spice/xtraevt.cm
   codemodel ../lib/spice/table.cm
   end
   unset __flag

```
spinit contains a script, made of commands from Chapt. 17.5, that is run upon start up of


-----

ngspice. Aliases (name equivalences) can be set. The asterisk ‘*’ comments out a line. If used
by ngspice, spinit will then load the XSPICE code models from a path relative to the current
directory where the ngspice executable resides. You may also define absolute paths.

If the standard path for the libraries (see standard spinit above or /usr/local/lib/spice under CYGWIN and Linux) is not adequate, you can add the ./configure options --prefix=/usr
```
--libdir=/usr/lib64 to set the codemodel search path to /usr/lib64/spice. Besides the

```
standard lib only lib64 is acknowledged.

Special care has to be taken when using the ngspice shared library. If you apply ngspice.dll
under Windows OS, the standard is to use relative paths for the code models as shown above.
However, the path is relative to the calling program, not to the dll. This is fine when ngspice.dll
and the calling program reside in the same directory. If ngspice.dll is placed in a different
directory, please check Chapt. 32.2.

The Linux shared library ... t.b.d.

## 16.6 User defined configuration file .spiceinit

In addition to spinit you may define a (personal) file .spiceinit and put it into the current directory or in your home directory. The typical search sequence for .spiceinit is: current directory, HOME (Linux) and then USERPROFILE (Windows). USERPROFILE is typically
C:\Users\<User name>. This file will be read in and executed after spinit, but before any
other input file is read. It may contain further scripts, set variables, or issue commands from
Chapt.17.5 to override commands given in spinit. For example set filetype=ascii will
yield ASCII output in the output data file (rawfile), instead of the compact binary format that is
used by default. set ngdebug will yield a lot of additional debug output. Any other contents
of the script, e.g. plotting preferences, may be included here also. If the command line option
```
-n is used upon ngspice start up, this file will be ignored.

```
.spiceinit may contain:
```
  * User defined ngspice init file
   set filetype=ascii
  *set ngdebug
   set numthreads = 8
  *set outputpath=C:\Spice64\out

## 16.7 Environmental variables

### 16.7.1 Ngspice specific variables
SPICE_LIB_DIR default: /usr/local/share/ngspice (Linux, CYGWIN), C:\Spice\share\ngspice

```
(Windows)
```
SPICE_EXEC_DIR default: /usr/local/bin (Linux, CYGWIN), C:\Spice\bin (Windows)
SPICE_BUGADDR default: http://ngspice.sourceforge.net/bugrep.html

```
Where to send bug reports on ngspice.


-----

```
SPICE_EDITOR default: vi (Linux, CYGWIN), notepad.exe (MINGW, Visual Studio)

```
Set the editor called in the edit command. Always overrides the EDITOR env. variable.
```
SPICE_ASCIIRAWFILE default: 0

```
Format of the rawfile. 0 for binary, and 1 for ascii.
```
SPICE_NEWS default: $SPICE_LIB_DIR/news

```
A file that is copied verbatim to stdout when ngspice starts in interactive mode.
```
SPICE_HELP_DIR default: $SPICE_LIB_DIR/helpdir

```
Help directory, not used in Windows mode
```
SPICE_HOST default: empty string

```
Used in the rspice command (probably obsolete, to be documented)
```
SPICE_SCRIPTS default: $SPICE_LIB_DIR/scripts

```
In this directory the spinit file will be searched.
```
SPICE_PATH default: $SPICE_EXEC_DIR/ngspice

```
Used in the aspice command (probably obsolete, to be documented)
```
NGSPICE_MEAS_PRECISION default: 5

```
Sets the number of digits if output values are printed by the meas(ure) command.
```
SPICE_NO_DATASEG_CHECK default: undefined

```
If defined, will suppress memory resource info (probably obsolete, not used on Windows
or where the /proc information system is available.)
```
NGSPICE_INPUT_DIR default: undefined

```
If defined, using a valid directory name, will add the given directory to the search path
when looking for input files (*.cir, *.inc, *.lib).

### 16.7.2 Common environment variables
```
TERM LINES COLS DISPLAY HOME PATH EDITOR SHELL POSIXLY_CORRECT

## 16.8 Memory usage

```
Ngspice started with batch option (-b) and rawfile output (-r rawfile) will store all simulation
data immediately into the rawfile without keeping them in memory. Thus very large circuits
may be simulated, the memory requested upon ngspice start up will depend on the circuit size,
but will not increase during simulation.

If you start ngspice in interactive mode or interactively with control section, all data will be kept
in memory, to be available for later evaluation. A large circuit may outgrow even Gigabytes of
memory. The same may happen after a very long simulation run with many vectors and many
time steps to be stored. Issuing the save <nodes> command will help to reduce memory
requirements by saving only the data defined by the command. You may alos choose option
INTERP (15.1.4) to reduce memory usage.


-----

## 16.9 Simulation time

Simulating large circuits may take an considerable amount of CPU time. If this is of importance,
you should compile ngspice with the flags for optimum speed, set during configuring ngspice
compilation. Under Linux, MINGW, and CYGWIN you should select the following option to
disable the debug mode, which slows down ngspice:
```
./configure --disable-debug

```
Adding --disable-debug will set the -O2 optimization flag for compiling and linking.

Under MS Visual Studio, you will have to select the release version, which includes optimization for speed.

If you have selected XSPICE (see Chapt. 12 and II) as part of your compilation configuration
(by adding the option --enable-xspice to your ./configure command), the value of trtol
(see 15.1.4) is set internally to 1 (instead of default 7) for higher precision if XSPICE code
model ’A’ devices included in the circuit. This may double or even triple the CPU time needed
for any transient simulation, because the amount of time steps and thus iteration steps is more
than doubled. For MS Visual Studio compilation there is currently no simple way to exclude
XSPICE during compilation.

You may enforce higher speed during XSPICE usage by setting the variable xtrtol in your
.spiceinit initialization file or in the .control section in front of the tran command (via set
```
xtrtol=2 using the set command 17.5.60) and override the above trtol reduction. Beware

```
however of precision or convergence issues if you use XSPICE ’A’ devices, especially if xtrtol
is set to values larger than 2.

If your circuit comprises mostly of MOS transistors, and you have a multi-core processor at
hand, you may benefit from OpenMP parallel processing, as described next (16.10).

## 16.10 Ngspice on multi-core processors using OpenMP

### 16.10.1 Introduction

Today’s computers typically come with CPUs having more than one core. It will thus be useful
to enhance ngspice to make use of such multi-core processors.

Using circuits comprising mostly of transistors and e.g. the BSIM3 model, around 2/3 of the
CPU time is spent in evaluating the model equations (e.g. in the BSIM3Load() function). The
same happens with other advanced transistor models. Thus this function should be paralleled, if
possible. Resulting from that the parallel processing has to be within a dedicated device model.
Interestingly solving the matrix takes only about 10% of the CPU time, so paralleling the matrix
solver is of secondary interest here!

A recent publication [1] has described a way to exactly do that using OpenMP, which is available
on many platforms and is easy to use, especially if you want to parallel processing of a for-loop.

To explain the implemented approach BSIM3 version 3.3.0 model was chosen, located in the
BSIM3 directory, as the first example. The BSIM3load() function in b3ld.c contains two nested
for-loops using linked lists (models and instances, e.g. individual transistors). Unfortunately


-----

Table 16.1: OpenMP performance
```
          Threads CPU time [s] CPU time [s]
                 Windows Linux
        1 (standard) 167 165
         1 (OpenMP) 174 167
           2 110 110
           3 95 94-120
           4 83 107
           6 94 90
           8 93 91

```
OpenMP requires a loop with an integer index. So in file B3set.c an array is defined, filled with
pointers to all instances of BSIM3 and stored in model->BSIM3InstanceArray.

BSIM3load() is now a wrapper function, calling the for-loop, which runs through functions
BSIM3LoadOMP(), once per instance. Inside BSIM3LoadOMP() the model equations are calculated.

Typically need it is needed to synchronize the activities, in that storing the results into the
matrix has to be guarded. The trick offered by the authors now is that the storage is moved out
of the BSIM3LoadOMP() function. Inside BSIM3LoadOMP() the updated data are stored in
extra locations locally per instance, defined in bsim3def.h. Only after the complete for-loop
is exercised, the update to the matrix is done in an extra function BSIM3LoadRhsMat() in the
main thread after the paralleled loop. No extra synchronization is required.

Then the thread programming needed is only a single line!!
```
#pragma omp parallel for

```
introducing the for-loop over the device instances.

This of course is made possible only thanks to the OpenMP guys and the clever trick on no
synchronization introduced by the above cited authors.

The time-measuring function getrusage() used with Linux or Cygwin to determine the CPU
time usage (with the rusage option enabled) counts tics from every core, adds them up, and
thus reports a CPU time value enlarged by a factor of 8 if 8 threads have been chosen. So now
ngspice is forced to use ftime for time measuring if OpenMP is selected.

### 16.10.2 Some results

Some results on an inverter chain with 627 CMOS inverters, running for 200ns, compiled with
Visual Studio professional 2008 on Windows 7 (full optimization) or gcc 4.4, SUSE Linux 11.2,
-O2, on a i7 860 machine with four real cores (and 4 virtuals using hyperthreading) are shown
in table 16.1.

So we see a ngspice speed up of nearly a factor of two! Even on an older notebook with a dual
core processor, more than 1.5x improvement using two threads was attained. Similar results are
to be expected from BSIM4.

|Threads|CPU time [s]|CPU time [s]|
|---|---|---|
||Windows|Linux|
|1 (standard)|167|165|
|1 (OpenMP)|174|167|
|2|110|110|
|3|95|94-120|
|4|83|107|
|6|94|90|
|8|93|91|


-----

### 16.10.3 Usage

To state it clearly: OpenMP is installed inside the model equations of a particular model. So for
the moment it is available only in BSIM3 version 3.3.0, not in version 3.2.4 nor in any other
BSIM3 model, in BSIM4 versions 4.6.5 or 4.8, not in any other BSIM4 model, and in B4SOI,
version 4.3.1, not in any other SOI model. Older parameter files of version 4.6.x (x any number
up to 5) are accepted, you have to check for compatibility.

Under Linux you may run
```
./autogen.sh
./configure ... --enable-openmp
make install

```
The same has been tested under MS Windows with CYGWIN and MINGW as well and delivers similar results.

Under MS Windows with Visual Studio Professional you have to place an additional preprocessor flag USE_OMP, and then enable /openmp. Visual Studio Express allone is not sufficient
due to lack of OpenMP support. But OpenMP is provided after installation of the Microsoft
SDK version 7.1. Even Visual Studio Professional lacks debugging support for OpenMP.

The number of threads has to be set manually by placing
```
set num_threads=4

```
into spinit or .spiceinit or in the control section of the SPICE input file. If OpenMP is enabled,
but num_threads not set, a default value num_threads=2 is set internally.

If you run a circuit, please keep in mind to select BSIM3 (levels 8, 49) version 3.3.0 (11.2.10),
by placing this version number into your parameter files, BSIM4 (levels 14, 54) version 4.6.5
or 4.8 (11.2.11), or B4SOI (levels 10, 58) version 4.3.1 (11.2.13).

If you run ./configure without --enable-openmp (or without USE_OMP preprocessor flag under MS Windows), you will get the standard, not paralleled BSIM3 and BSIM4 model, as has
been available from Berkeley. If OpenMP is selected and the number of threads set to 1, there
will be only a very slight CPU time disadvantage (typ. 3%) compared to the standard, non
OpenMP build.

### 16.10.4 Literature

[1] R.K. Perng, T.-H. Weng, and K.-C. Li: "On Performance Enhancement of Circuit Simulation
Using Multithreaded Techniques", IEEE International Conference on Computational Science
and Engineering, 2009, pp. 158-165

## 16.11 Server mode option -s

A program may write the SPICE input to the console. This output is redirected to ngspice via
‘|’. ngspice called with the -s option writes its output to the console, which again is redirected
to a receiving program by ‘|’. In the following simple example cat reads the input file and


-----

prints it content to the console, which is redirected to ngspice by a first pipe, ngspice transfers
its output (similar to a raw file, see below) to less via another pipe.

Example command line:
```
   cat input.cir|ngspice -s|less

```
Under MS Windows you will need to compile ngspice as a console application (see Chapt.
32.2.5) for this server mode usage.

Example input file:
```
   test -s
  v1 1 0 1
  r1 1 0 2k
  .options filetype=ascii
  .save i(v1)
  .dc v1 -1 1 0.5
  .end

```
If you start ngspice console with
```
  ngspice -s

```
you may type in the above circuit line by line (not to forget the first line, which is a title and
will be ignored). If you close your input with ctrl Z, and return, you will get the following
output (this is valid for MINGW only) on the console, like a raw file:
```
  Circuit: test -s
  Doing analysis at TEMP = 27.000000 and TNOM = 27.000000
  Title: test -s
  Date: Sun Jan 15 18:57:13 2012
  Plotname: DC transfer characteristic
  Flags: real
  No. Variables: 2
  No. Points: 0
  Variables:
  No. of Data Columns : 2
  0 v(v-sweep) voltage
  1 i(v1) current
  Values:
  0 -1.000000000000000e+000
    5.000000000000000e-004
  1 -5.000000000000000e-001
    2.500000000000000e-004
  2 0.000000000000000e+000
    0.000000000000000e+000

```

-----

```
  3 5.000000000000000e-001
   -2.500000000000000e-004
  4 1.000000000000000e+000
   -5.000000000000000e-004
  @@@ 122 5

```
The number 5 of the last line @@@ 122 5 shows the number of data points, which is missing in
the above line No. `Points:` `0 because at the time of writing to the console it has not yet`
been available.
```
ctrl Z is not usable here in Linux, a patch to install ctrl D instead is being evaluated.

## 16.12 Ngspice control via input, output fifos

```
The following bash script (under Linux)

- launches ngspice in another thread.

- writes some commands in ngspice input

- reads the output and prints them on the console.


-----

Example:
```
   #!/usr/bin/env bash
   NGSPICE_COMMAND="ngspice"
  rm input.fifo
  rm output.fifo
   mkfifo input.fifo
   mkfifo output.fifo
   $NGSPICE_COMMAND -p -i <input.fifo >output.fifo &
   exec 3>input.fifo
   echo "I can write to input.fifo"
   echo "Start processing..."
   echo ""
   echo "source circuit.cir" >&3
   echo "unset askquit" >&3
   echo "set nobreak" >&3
   echo "tran 0.01ms 0.1ms">&3
   echo "print n0" >&3
   echo "quit" >&3
   echo "Try to open output.fifo ..."
   exec 4<output.fifo
   echo "I can read from output.fifo"
   echo "Ready to read..."
   while read output
  do
      echo $output
   done <&4
   exec 3>&   exec 4>&   echo "End processing"

```
The input file for SPICE is:


-----

Circuit.cir:
```
  * Circuit.cir
  V1 n0 0 SIN(0 10 1kHz)
  C1 n1 n0 3.3nF
  R1 0 n1 1k
  .end

## 16.13 Compatibility

```
ngspice is a direct derivative of spice3f5 from UC Berkeley and thus inherits all of the commands available in its predecessor. Thanks to the open source policy of UCB (original spice3
[from 1994 is still available here), several commercial variants have sprung off, either being more](http://embedded.eecs.berkeley.edu/pubs/downloads/spice/index.htm)
dedicated to IC design or more concentrating on simulating discrete and board level electronics.
None of the commercial and almost none of the freely downloadable SPICE providers publishes
the source code. All of them have proceeded with the development, by adding functionality, or
by adding a more dedicated user interface. Some have kept the original SPICE syntax for their
netlist description, others have quickly changed some if not many of the commands, functions
and procedures. Thus it is difficult, if not impossible, to offer a simulator that acknowledges
all of these netlist dialects. ngspice includes some features that enhance compatibility that are
included automatically. This selection may be controlled to some extend by setting the compatibility mode. Others may be invoked by the user by small additions to the netlist input file.
Some of them are listed in this chapter, some will be integrated into ngspice at a later stage,
others will be added if they are reported by users.

### 16.13.1 Compatibility mode

The variable (17.7) ngbehavior sets the compatibility mode. ’all’ is set as the default value.
```
’spice3’ as invoked by the command
  set ngbehavior=spice3

```
in spinit or .spiceinit will disable some of the advanced ngspice features. ’ps’ will enable
including a library by a simple .lib <lib_filename> statement that is not compatible to the
more comfortable library handling described in Chapt. 2.7.

### 16.13.2 Missing functions

You may add one or more function definitions to your input file, as listed below.
```
  .func LIMIT(x,a,b) {min(max(x, a), b)}
  .func PWR(x,a) {abs(x) ** a}
  .func PWRS(x,a) {sgn(x) * PWR(x,a)}
  .func stp(x) {u(x)}

```

-----

### 16.13.3 Devices

**16.13.3.1** **E Source with LAPLACE**

see Chapt. 5.2.5.

**16.13.3.2** **VSwitch**

The VSwitch
```
  S1 2 3 11 0 SW
  .MODEL SW VSWITCH(VON=5V VOFF=0V RON=0.1 ROFF=100K)

```
may become
```
  a1 %v(11) %gd(2 3) sw
  .MODEL SW aswitch(cntl_off=0.0 cntl_on=5.0 r_off=1e5
  + r_on=0.1 log=TRUE)

```
The XSPICE option has to be enabled.

### 16.13.4 Controls and commands

**16.13.4.1** **.lib**

The ngspice .lib command (see 2.7) requires two parameters, a file name followed by a library
name. If no library name is given, the line
```
  .lib filename

```
should be replaced by
```
  .inc filename

```
Alternatively, the compatibility mode (16.13.1) may be set to ’ps’.

**16.13.4.2** **.step**

Repeated analysis in ngspice if offered by a short script inside of a .control section (see
Chapt. 17.8.7) added to the input file. A simple application (multiple dc sweeps) is shown
below.


-----

Input file with parameter sweep
```
   parameter sweep
  * resistive divider, R1 swept from start_r to stop_r
  * replaces .STEP R1 1k 10k 1k
  R1 1 2 1k
  R2 2 0 1k
   VDD 1 0 DC 1
  .dc VDD 0 1 .1
  .control
   let start_r = 1k
   let stop_r = 10k
   let delta_r = 1k
   let r_act = start_r
  * loop
   while r_act le stop_r
    alter r1 r_act
    run
    write dc-sweep.out v(2)
    set appendwrite
    let r_act = r_act + delta_r
   end
   plot dc1.v(2) dc2.v(2) dc3.v(2) dc4.v(2) dc5.v(2)
  + dc6.v(2) dc7.v(2) dc8.v(2) dc9.v(2) dc10.v(2)
  .endc
  .end

## 16.14 Tests

```
The ngspice distribution is accompanied by a suite of test input and output files, located in the
directory ngspice/tests. Originally this suite was meant to see if ngspice with all models was
made and installed properly. It is started by
```
$ make check

```
from within your compilation and development shell. A sequence of simulations is thus started,
its outputs compared to given output files by comparisons string by string. This feature is
momentarily used only to check for the BSIM3 model (11.2.10) and the XSPICE extension
(12). Several other input files located in directory ngspice/tests may serve as light-weight
examples for invoking devices and simple circuits.

Today’s very complex device models (BSIM4 (see 11.2.11), HiSIM (see 11.2.15) and others)
require a different strategy for verification. Under development for ngspice is the CMC Regression test by Colin McAndrew, which accompanies every new model. These tests cover a large


-----

range of different DC, AC and noise simulations with different geometry ranges and operating
conditions and are more meaningful the transient simulations with their step size dependencies.
A major advantage is the scalability of the diff comparisons, which check for equality within a
given tolerance. A set of Perl modules cares for input, output and comparisons of the models.
Currently BSIM3, BSIM4, BSIMSOI4, HiSIM, and HiSIM_HV models implement the new
test. You may invoke it by running the command given above or by
```
$ make -i check 2>&1 | tee results
-i will make make to ignore any errors, tee will provide console output as well as printing to

```
file ’results’. Be aware that under MS Windows you will need the console binary (see 32.2.5)
to run the CMC tests, and you have to have Perl installed!

## 16.15 Reporting bugs and errors

Ngspice is a complex piece of software. The source code contains over 1500 files. Various
models and simulation procedures are provided, some of them not used and tested intensively.
Therefore errors may be found, some still evolving from the original spice3f5 code, others
introduced during the ongoing code enhancements.

If you happen to experience an error during the usage of ngspice, please send a report to the
development team. Ngspice is hosted on sourceforge, the preferred place to post a bug report is
[the ngspice bug tracker. We would prefer to have your bug tested against the actual source code](http://sourceforge.net/tracker/?group_id=38962&atid=423915)
available at Git, but of course a report using the most recent ngspice release is welcome! Please
provide the following information with your report:

Ngspice version

Operating system

Small input file to reproduce the bug

Actual output versus the expected output


-----

