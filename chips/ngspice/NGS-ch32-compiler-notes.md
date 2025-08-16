# Chapter 32

 Compilation notes

This file describes the procedures to install ngspice from sources.

## 32.1 Ngspice Installation under Linux (and other ’UNIXes’)

### 32.1.1 Prerequisites

Ngspice is written in C and thus a complete C compilation environment is needed. Almost any
UNIX comes with a complete C development environment. Ngspice is developed on GNU/Linux with gcc and GNU make.

The following software must be installed in your system to compile ngspice: bison, flex,
and X11 headers and libs.

The X11 headers and libraries are typically available in an X11 development package from your
Linux distribution.

If you want to compile the Git source you need additional software: autoconf, automake,
```
libtool, texinfo.

```
The following software may be needed when enabling additional features: readline, editline,
```
tcl/tk, blt.

```
If you want have high performance and accurate FFT’s you should install: fftw-3. Ngspice
configure script will find the library and will induce the build process to link against it.

### 32.1.2 Install from Git

This section describes how to install from source code taken direct from Git. This will give
you access to the most recent enhancements and corrections. However be careful as the code
in Git may be under development and thus still unstable. For user install instructions using
source from released distributions, please see the sections titled ’Install from tarball’ (32.1.3)
and ’Advanced Install’ (32.1.5).

[Download source from Git as described on the sourceforge ngspice Git page. Define and enter](http://sourceforge.net/scm/?type=git&group_id=38962)
a directory of your choice, e.g. /home/myname/software/. Download the complete ngspice
repository from Git, for example by anonymous access issuing the command


-----

```
  git clone git://git.code.sf.net/p/ngspice/ngspice

```
or via http protocol
```
  git clone http://git.code.sf.net/p/ngspice/ngspice

```
You will find the sources in directory /home/myname/software/ngspice. Now enter the
ngspice top level directory ngspice (where the installation instruction file INSTALL can be
found).

The project uses the GNU build process. You should be able to do the following:
```
$ ./autogen.sh
$ ./configure --enable-xspice --enable-cider
--disable-debug --with-readline=yes
$ make
$ sudo make install

```
See the section titled ’Advanced Install’ (32.1.5) for instructions about arguments that can be
passed to ./configure to customize the build and installation. The following arguments are
already used here and may be called sort of ‘standard’:
```
--enable-xspice Include the XSPICE extensions (see Chapt. 12 and 28)
--enable-cider Include CIDER numerical device simulator (see Chapt. 30)
--disable-debug No debugging information included (optimized and compact code)
--with-readline=yes Include an editor for the input command line (command history, backspace,

```
insert etc.). If readline is not available, editline may be used.
```
--enable-openmp Compile ngspice for multi-core processors. Paralleling is done by OpenMP

```
(see Chapt. 16.10), and is enabled for certain MOS models.

If a problem is found with the build process, please submit a report to the Ngspice development
team. Please provide information about your system and any ./configure arguments you
are using, together with any error messages. Ideally you would have tried to fix the problem
yourself first. If you have fixed the problem then the development team will love to hear from
you.

If you need updating your local source code tree from Git, just enter ngspice directory and
issue the command
```
  git pull
git pull will deny to overwrite modified files in your working directory. To drop your local

```
changes first, you can run
```
  git reset --hard

```
To learn more about Git, which can be both powerful and difficult to master, please consult
[http://git-scm.com/, especially: http://git-scm.com/documentation, which has pointers to docu-](http://git-scm.com/)
mentation and tutorials.


-----

### 32.1.3 Install from a tarball, e.g. ngspice-rework-27.tgz

This covers installation from a tarball (for example ngspice-rework-27.tgz, to be found at
http://sourceforge.net/projects/ngspice/files/). After downloading the tar ball to a local directory unpack it using:
```
$ tar -zxvf ngspice-rework-27.tgz

```
Now change directories in to the top-level source directory (where this text from the INSTALL
file can be found).

You should be able to do:
```
$ ./configure --enable-xspice --disable-debug --with-readline=yes
$ make
$ sudo make install

```
The default install dir is /usr/local/bin

See the section titled ’Advanced Install’ (32.1.5) for instructions about arguments that can be
passed to ./configure to customize the build and installation.

### 32.1.4 Compilation using an user defined directory tree for object files

The procedures described above will store the *.o files (output of the compilation step) into the
directories where the sources (*.c) are located. This may not be the best option if you want for
example to maintain a debug version and in parallel a release version of ngspice (./configure
```
--disable-debug). So if you intend to create a separate object file tree like ngspice/ngbuil
```
d/release, you may do the following, starting from the default directory ngspice:
```
mkdir -p release
cd release
../configure --enable-xspice --disable-debug --with-readline=yes <more options>
make install

```
This will create an object file directory tree, similar to the source file directory tree, the object
files are now separated from the source files. For the debug version, you may do the same
as described above, replacing ’release’ by ’debug’, and obtain another separated object file
directory tree. If you already have run ./configure in ngspice, you have to do a maintainerclean, before the above procedure will work.

### 32.1.5 Advanced Install

Some extra options can be provided to ./configure. To get all available options do:
```
$ ./configure --help

```
Some of these options are generic to the GNU build process that is used by Ngspice, other are
specific to Ngspice.

The following sections provide some guidance and descriptions for many, but not all, of these
options.


-----

**32.1.5.1** **Options Specific to Using Ngspice**
```
--enable-openmp Compile ngspice for multi-core processors. Paralleling is done by OpenMP

```
(see Chapt. 16.10).
```
--enable-xspice Enable XSPICE enhancements, yielding a mixed signal simulator integra
```
ted into ngspice with codemodel dynamic loading support. See Chapt. 12 and section II for
details.
```
--with-readline=yes Enable GNU readline support for the command line interface.
--enable-cider Cider is a mixed-level simulator that couples Spice3 and DSIM to simulate

```
devices from their technological parameters. This part of the simulator is not compiled by
default.
```
--enable-adms ADMS is an experimental model compiler that translates Verilog-A compact

```
models into C code that can be compiled into ngspice. This is still experimental, but working
with some limitations to the models (e.g. no noise models). If you want to use it, please refer
[to the ADMS section on ngspice web site .](http://ngspice.sourceforge.net/admshowto.html)
```
--with-editline=yes Enables the use of the BSD editline library (libedit).

```
[See http://www.thrysoee.dk/editline/.](http://www.thrysoee.dk/editline/)
```
--without-x Disable the X-Windows graphical system. Compile without needing X headers

```
and X libraries. The plot command (17.5.45) is now disabled. You may use Gnuplot (17.5.28)
instead.
```
--with-tcl=tcldir When configured with this option the tcl module ‘tclspice’ is compiled

```
and installed instead of plain ngspice.
```
--with-ngshared This option will create a shared library (*.so in Linux) or dynamic link

```
library (*.dll) instead of plain ngspice.
```
--enable-relpath This options introduces a search path for spinit relative to the calling exe
```
cutable (ngspice or the caller using the ngspice shared library) as ../share/ngspice. In spinit
the search path for code models is also set as relative as ../lib.

The following options are seldom used today, not tested, some may even no longer be implemented.
```
--enable-capbypass Bypass calculation of cbd/cbs in the mosfets if the vbs/vbd voltages are

```
unchanged.
```
--enable-capzerobypass Bypass all the cbd/cbs calculations if Czero is zero. This is ena
```
bled by default since rework-18.
```
--enable-cluster Clustering code for distributed simulation. This is a contribution never

```
tested. This code comes from TCLspice implementation and is implemented for transient analysis only.
```
--enable-expdevices Enable experimental devices. This option is used by developers to

```
mask devices under development. Almost useless for users.
```
--enable-experimental This enables some experimental code. Specifically it enables: *

```
support for altering options in interactive mode by adding the interactive keyword ’options’. *
The ability to save and load snapshots: adds interactive keywords ’savesnap’ and ’loadsnap’.
```
--enable-help Force building nghelp. This is deprecated.

```

-----

```
--enable-newpred Enable the NEWPRED symbol in the code.
--enable-newtrunc Enable the newtrunc option
--enable-ndev Enable NDEV interface, (experimental) A TCP/IP interface to external device

```
[simulator such as GSS. For more information, please visit the homepage of GSS at http://gss-](http://gss-tcad.sourceforge.net)
[tcad.sourceforge.net](http://gss-tcad.sourceforge.net)
```
--enable-nodelimiting Experimental damping scheme
--enable-nobypass Don’t bypass recalculations of slowly changing variables
--enable-nosqrt Use always log/exp for non-linear capacitances --enable-predictor

```
Enable a predictor method for convergence
```
--enable-sense2 Use spice2 sensitivity analysis
--enable-xgraph Compile the Xgraph plotting program. Xgraph is a plotting package for

```
X11 and was once very popular.

**32.1.5.2** **Options Useful for Debugging Ngspice**
```
--disable-debug This option will remove the ’-g’ option passed to the compiler. This speeds

```
up execution time, creates a small executable, and is recommended for normal use. If you want
to run ngspice in a debugger (e.g. gdb), you should not select this option.

The following options are seldom used today, not tested, some may even no longer be implemented.
```
--enable-ansi Configure will try to find an option for your compiler so that it expects ansi-C.
--enable-asdebug Debug sensitivity code *ASDEBUG*.
--enable-blktmsdebug Debug distortion code *BLOCKTIMES*
--enable-checkergcc Option for compilation with checkergcc.
--enable-cpdebug Enable ngspice shell code debug.
--enable-ftedebug Enable ngspice frontend debug.
--enable-gc Enable the Boehm-Weiser Conservative Garbage Collector.
--enable-pzdebug Debug pole/zero code.
--enable-sensdebug Debug sensitivity code *SENSDEBUG*.
--enable-smltmsdebug Debug distortion code *SMALLTIMES*
--enable-smoketest Enable smoketest compile.
--enable-stepdebug Turns on debugging of convergence steps in transient analysis

### 32.1.6 Compilers and Options

```
Some systems require unusual options for compilation or linking that the configure script does
not know about. You can give configure initial values for variables by setting them in the
environment. Using a Bourne-compatible shell, you can do that on the command line like this:
```
CC=c89

```

-----

```
CFLAGS=-O2
LIBS=-lposix
./configure

```
Or on systems that have the env program, you can do it like this:
```
env CPPFLAGS=-I/usr/local/include
LDFLAGS=-s
./configure

### 32.1.7 Compiling For Multiple Architectures

```
You can compile the package for more than one kind of computer at the same time, by placing the object files for each architecture in their own directory. To do this, you must use a
version of make that supports the VPATH variable, such as GNU make. cd to the directory
where you want the object files and executables to go and run the configure script. configure
automatically checks for the source code in the directory that configure is in and in ‘..’.

If you have to use a make that does not supports the VPATH variable, you have to compile the
package for one architecture at a time in the source code directory. After you have installed the
package for one architecture, use make distclean before reconfiguring for another architecture.

### 32.1.8 Installation Names

By default, make install will install the package’s files in /usr/local/bin, /usr/local/man, etc.
You can specify an installation prefix other than /usr/local by giving configure the option –
prefix=PATH.

You can specify separate installation prefixes for architecture-specific files and architectureindependent files. If you give configure the option –exec-prefix=PATH, the package will use
PATH as the prefix for installing programs and libraries. Documentation and other data files
will still use the regular prefix.

In addition, if you use an unusual directory layout you can give options like –bindir=PATH
to specify different values for particular kinds of files. Run configure –help for a list of the
directories you can set and what kinds of files go in them.

If the package supports it, you can cause programs to be installed with an extra prefix or suffix on their names by giving configure the option –program-prefix=PREFIX or –programsuffix=SUFFIX.

When installed on MinGW with MSYS alternative paths are not fully supported. See ‘How to
make ngspice with MINGW and MSYS’ below for details.

### 32.1.9 Optional Features

Some packages pay attention to –enable-FEATURE options to configure, where FEATURE
indicates an optional part of the package. They may also pay attention to –with-PACKAGE


-----

options, where PACKAGE is something like gnu-as or ‘x’ (for the X Window System). The
README should mention any –enable- and –with- options that the package recognizes.

For packages that use the X Window System, configure can usually find the X include and
library files automatically, but if it doesn’t, you can use the configure options –x-includes=DIR
and –x-libraries=DIR to specify their locations.

### 32.1.10 Specifying the System Type

There may be some features configure can not figure out automatically, but needs to determine
by the type of host the package will run on. Usually configure can figure that out, but if it
prints a message saying it can not guess the host type, give it the –host=TYPE option. TYPE
can either be a short name for the system type, such as ‘sun4’, or a canonical name with three
fields: CPU-COMPANY-SYSTEM

See the file config.sub for the possible values of each field. If config.sub isn’t included in this
package, then this package doesn’t need to know the host type.

If you are building compiler tools for cross-compiling, you can also use the –target=TYPE
option to select the type of system they will produce code for and the –build=TYPE option to
select the type of system on which you are compiling the package.

### 32.1.11 Sharing Defaults

If you want to set default values for configure scripts to share, you can create a site shell
script called config.site that gives default values for variables like CC, cache_file, and prefix.
configure looks for PREFIX/share/config.site if it exists, then PREFIX/etc/config.site if it
exists. Or, you can set the CONFIG_SITE environment variable to the location of the site
script. A warning: not all configure scripts look for a site script.

### 32.1.12 Operation Controls

configure recognizes the following options to control how it operates.
```
--cache-file=FILE Use and save the results of the tests in FILE instead of ./config.cache.

```
Set FILE to /dev/null to disable caching, for debugging configure.
```
--help Print a summary of the options to configure, and exit.
--quiet --silent -q Do not print messages saying which checks are being made. To sup
```
press all normal output, redirect it to /dev/null (any error messages will still be shown).
```
--srcdir=DIR Look for the package’s source code in directory DIR. Usually configure can

```
determine that directory automatically.
```
--version Print the version of Autoconf used to generate the configure script, and exit.

```
configure also accepts some other, not widely useful, options.


-----

## 32.2 Ngspice Compilation under Windows OS

### 32.2.1 Compile ngspice with MS Visual Studio 2015 or 2017

ngspice may be compiled with MS Visual Studio 2015 or 2017. A free version is offered by
Microsoft with the Visual Studio Community Edition. XSPICE project files are located in
visualc/XSPICE and are automatically invoked if you start the build procedure.

CIDER and XSPICE are included, as well as the code models for XSPICE (*.cm). Verilog-A
models compiled with ADMS however are not available.

After compilation the executable, code models and initialization files are available in directory
C: as C:\Spice, C:\Spice64 etc., as described in the installation tree below. A true Windows
installer is however not yet available. The ’home’ directory for Windows OS (ngspice/visualc)
with its files vngspice.sln (project starter) and vngspice.vcxproj (project contents) allows to
compile and link ngspice with MS Visual Studio.

/visualc/src/include/ngspice contains a dedicated config.h file with the preprocessor definitions required to properly compile the code.

Install Microsoft Visual Studio 2017. The MS Visual Studio Community Edition (which is
[available at no cost from https://www.visualstudio.com/) is fully adequate. It will generate a 32](https://www.visualstudio.com/)
bit Release with or without OpenMP support and a Debug version of ngspice, using the Win32
flag. In addition you may select a console version without graphics interface. The same is
available for 64 bit (flag x64). Standard for every day use are the ReleaseOMP variants for 32
or 64 bit.

Compilation of the ngspice and XSPICE codes requires the installation of FLEX and BISON.
[They may be downloaded as Windows executables from winflexbison. Please unzip the zip](https://sourceforge.net/projects/winflexbison/files/win_flex_bison-latest.zip/download)
file and copy its content into a directory named flex-bison at the same level as the ngspice
directory.

**Procedure:**

[Download ngspice. You may obtain a snapshot from ngspice git page at SourceForge, where](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/)
you will find on top of the page a link named ’Download Snapshot’. On the left you may select
any of the branches which are of interest. Branch ’master’ is the most mature code selection,
branch ’scope-inpcom-16’ is an actual development branch. Another approach is to install ’git’
[from git for Windows and installing ngspice source code with the command](https://git-for-windows.github.io/)
```
  git clone git://git.code.sf.net/p/ngspice/ngspice

```
as described in chapter 32.1.2.

Go to directory /ngspice/visualc.

Start MS Visual Studio by double click on vngspice.sln. After MS Visual Studio opens,
select the debug or release version (with or without OpenMP support) by checking Build,
Configuration-Manager, Debug, Release or ReleaseOMP. Start making ngspice.exe by
selecting Build and Build Solution. The executable will be created and stored in visualc/vngspice/<configuration.platform>. Object files will be stored to visualc/vngspice/<configuration.platform>/o

A simplified installation tree is created in parallel:


-----

```
C:\Spice\
 bin\
  ngspice.exe
  vcomp14xx.dll
 lib\
  ngspice\
    analog.cm
    digital.cm
    spice2poly.cm
    extradev.cm
    extravt.cm
    table.cm
 share\
  ngspice\
    scripts\
     spinit

```
Table 32.1: ngspice Visual Studio installation tree under MS Windows

The exact directory names depend on the configuration and platform you have selected (C:\Spice,
C:\Spice64, C:\Spiced, C:\Spice64d). If you intend to install ngspice into another directory,
e.g. D:\MySpice, you may simply copy the contents from C:\Spice to the new location. This
becomes possible because the paths to the code models or spinit are set relative to ngspice.exe.
As an alternative you may edit make-install-vngspice.bat and alter the following entries from:
```
set dst=c:\Spice
set dst=c:\Spice64

```
to
```
set dst=D:\MySpice
set dst=D:\MySpice64

```
To use the FFTW-3 library for a ’calibrated’ fast Fourier analysis with the fft command
(see 17.5.26), download the precompiled MS Windows FFTW distribution (either 32 bit or 64
[bit) from http://www.fftw.org/install/windows.html. Extract at least the files fftw3.h, libfftw3-](http://www.fftw.org/install/windows.html)
3.def, and libfftw3-3.dll to directory ../../fftw-3.3.4-dll32 (from 32 bit fftw3 for ngspice 32
bit), or to directory ../../fftw-3.3.4-dll64 (from 64 bit fftw3 for ngspice 64 bit). So both directories are at the same level as the ngspice directory. Then select the MS VC++ project
file visualc/vngspice-fftw.vcxproj for starting VC++, select the appropriate configuration and
platform, and off you go. This is how the installed directory tree looks like:


-----

```
D:\MySpiceSources\
 ngspice\
  visualc\
  ...
 flex-bison\
  ...
 fftw-3.3.4-dll32\
  ...
 fftw-3.3.4-dll64\
  ...

```
Table 32.2: ngspice source tree under MS Windows

If you use the debugging features of Visual Studio, ngspice is started with a special spinit file
located in visualc\vngspice\share\ngspice\scripts. Your user-defined start-up commands are
best addressed in a .spiceinit file located in C:\users\<username>.

For compiling ngspice as a dll (shared library) there is a dedicated project file coming with the
source code to generate ngspice.dll. Go to the directory visualc and start the project with
double clicking on sharedspice.vcxproj.

### 32.2.2 How to make ngspice with MINGW and MSYS

Creating ngspice with MINGW is a straight forward procedure, if you have MSYS/MINGW
installed properly. Unfortunately the installation is rather tedious because you will need several
enhancements to the standard install, especially if you want to include XSPICE. Some links
are given below that describe the procedures. The default installation location of ngspice is the
Windows path C:\spice. The install path can be altered by passing --prefix=NEWPATH as an
argument to ./configure during the build process.

Put the install path you desire inside "", e.g. "D:/NewSpice". Be careful to use forward slashes
‘/’, not backward slashes ‘\’ (something still to be fixed). Then add --prefix="D:/NewSpice"
as an argument to ./configure in the normal way.

The procedure of compiling a distribution (for example, the most recent stable distribution from
the ngspice website, e.g. ngspice-27.tar.gz), is as follows:
```
$ cd ngspice
$ cd release
$ ../configure --with-wingui ...and other options
$ make
$ make install

```
The useful options to ../configure are:
```
--enable-xspice (this requires FLEX and BISON available in MSYS, see below).
--enable-cider
--disable-debug (-O2 optimization, no debug information)

```
An option to make is


-----

```
-j8

```
If you have a processor with 4 real (or 8 logical) cores, this will speed up compilation considerably.

A complete ngspice (release version, no debug info, optimized executable) may be made available just by
```
$ cd ngspice
$ ./compile_min.sh

```
If you want to compile the Git source you need additional software packages autoconf, auto[make, libtool, available from the MSYS distribution and git, available for example here.](https://git-for-windows.github.io/)

[Download source from Git as described on the sourceforge ngspice Git page. Define and enter](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/)
a directory of your choice, e.g. /d/spice/. Download the complete ngspice repository from Git,
for example by anonymous access issuing the command
```
  git clone git://git.code.sf.net/p/ngspice/ngspice

```
You will find the sources in directory /d/spice/ngspice/. Now enter the ngspice top level
directory ngspice. This is the procedure for compilation:
```
$ cd ngspice
$ ./autogen.sh
$ mkdir release
$ cd release
$ ../configure --with-wingui ...and other options
$ make -j8
$ make install

```
The user defined build tree saves the object files, instead of putting them into the source tree, in
a release (and a debug) tree. Please see Chapt. 32.1.4 for instructions.

If you need updating your local source code tree from Git, just enter ngspice directory and
issue the command
```
  git pull
git pull will deny to overwrite modified files in your working directory. To drop your local

```
changes first, you can run
```
  git reset --hard

```
To learn more about Git, which can be both powerful and difficult to master, please consult
[http://git-scm.com/, especially: http://git-scm.com/documentation, which has pointers to docu-](http://git-scm.com/)
mentation and tutorials.

[MINGW and MSYS can be downloaded from http://www.mingw.org/. The making of the code](http://www.mingw.org/)
models *.cm for XSPICE and one of the ngspice parsers require the installation of BISON and


-----

FLEX to MSYS. A typical installation was tested with: bison-2.0-MSYS.tar.gz flex-2.5.4a1-bin.zip libiconv-1.9.2-1-bin.zip libintl-0.14.4-bin.zip

Bison 2.0 is now superseded by newer releases
[(Bison 2.4)](https://sourceforge.net/projects/mingw/files/MSYS/Extension/bison/)

[The last three are from GnuWin.](https://sourceforge.net/projects/gnuwin32/files/)

You may also look at

[http://www.mingw.org/wiki/HOWTO_Install_the_MinGW_GCC_Compiler_Suite](http://www.mingw.org/wiki/HOWTO_Install_the_MinGW_GCC_Compiler_Suite)

[http://www.mingw.org/wiki/MSYS](http://www.mingw.org/wiki/MSYS )

[http://www.mingw.org/wiki/HOWTO_Create_an_MSYS_Build_Environment.](http://www.mingw.org/wiki/HOWTO_Create_an_MSYS_Build_Environment)

### 32.2.3 64 Bit executables with MINGW-w64

**Procedure:**

Install MSYS or preferently the newer MSYS2, plus bison, flex, auto tools, perl, libiconv,
libintl

Install MINGW-w64, activate OpenMP support

[See either http://mingw-w64.org/ or http://tdm-gcc.tdragon.net/](http://mingw-w64.org/)

(allows to generate both 32 or 64 bit executables by setting flag -m32 or -m64)

Set path to compiler in msys/xx/etc/fstab (e.g. c:/MinGW64 /mingw), if not set automatically
as in MSYS2.

Start compiling with

./compile_min.sh or ./compile_min.sh 64

Options used in the script:

–adms and –enable-adms ADMS is an experimental model compiler that translates VerilogA compact models into C code that can be compiled into ngspice. This is still experimental,
but working with some limitations to the models (e.g. no noise models). If you want to use it,
[please refer to the ADMS section on ngspice web site .](http://ngspice.sourceforge.net/admshowto.html)

CIDER, XSPICE, and OpenMP may be selected at will.

–disable-debug will give O2 optimization (versus O0 for debug) and removes all debugging
info.

The install script will copy all files to C:\Spice or C:\Spice64, the code models for XSPICE
will be stored in C:\Spice\lib\spice or C:\Spice64\lib\spice respectively.

make install will create a directory tree as shown below:


-----

```
C:\Spice\
 bin\
  ngspice.exe
  nghelp.exe
  ngmakeidx.exe
  ngnutmeg.exe
  cmpp.exe
 lib\
  ngspice\
    analog.cm
    digital.cm
    spice2poly.cm
    extradev.cm
    extravt.cm
 share\
  info\
    dir
    ngspice.info
    ngspice.info-1
    ..
    ngspice.info-10
  man\
    man1\
     ngmultidec.1
     ngnutmeg.1
     ngsconvert.1
     ngspice.1
  ngspice\
    helpdir\
     ngspice.idx
     ngspice.txt
    scripts\
     ciderinit
     devaxis
     devload
     setplot
     spectrum
     spinit

```
Table 32.3: ngspice standard installation tree under MS Windows

The ./configure flag --enable-relpath may be useful if the install path (e.g. C:\Spice64) is
only preliminary, because a Windows installer is preferred. Then all search paths for spinit and
code models are made relative to the executable (either ngspice.exe or the caller to ngspice.dll),
see 32.1.5.

For compiling ngspice as a dll (shared library) use the configure option --with-ngshared
instead of --with-x or --with-wingui. In addition you might add (optionally) --enable-relpath
to avoid absolute paths when searching for code models. You may edit compile_min.sh ac

-----

cordingly and compile using this script in the MSYS2 window.

### 32.2.4 make ngspice with pure CYGWIN

The procedure of compiling is the same as with Linux (see Chapt. 32.1). After you have moved
to the ngspice directory, the following command sequence may do the work for you:
```
$ ./autogen.sh
$ mkdir release-cyg
$ cd release-cyg
$ ../configure --with-x --disable-debug --with-readline=yes --enable-xspice
--enable-pss --enable-cider --enable-openmp
$ make clean 2>&1 | tee make_clean.log
$ make 2>&1 -j8 | tee make.log
$ make install 2>&1 | tee make_install.log

```
The (optional) statement -j8 (or -jn, n is the number of logical cores available) will speed up
compilation considerably.

The CYGWIN console executable you have been creating is an X11 application. This is a not
a Windows native environment. So you have to add an X11 graphics interface by installing the
XServer from the CYGWIN project. Before starting ngspice, you have to start the XServer by
the following commands within the CYGWIN window:
```
$ export DISPLAY=:0.0
$ xwin -multiwindow -clipboard &

```
If you don’t have libdl.a you may need to link libcygwin.a to libdl.a symbolically, for example:
```
$ cd /lib $ ln -s libcygwin.a libdl.a.

### 32.2.5 ngspice mingw or cygwin console executable w/o graphics

```
If you omit the configure flag –with-wingui or –with-x, you will obtain a console application
without graphics interface.
```
  ./configure --enable-xspice --enable-cider --enable-openmp
   --disable-debug CFLAGS=-m32 LDFLAGS=-m32 prefix=C:/Spice

```
is an example for TDM mingw, 32 Bit ngspice console. No graphics interface is provided. A
warning message will be issued upon starting ngspice. However, you may invoke Gnuplot for
plotting (see 17.5.28).

### 32.2.6 ngspice for MS Windows, cross compiled from Linux

The ngspice main directory contains two scripts that provide cross compiling ngspice.exe or ngspice.dll from a Linux setup. For details and prerequisites please have a look at cross-compile.sh
or cross-compile-shared.sh.


-----

## 32.3 Reporting errors

Setting up ngspice is a complex task. The source code contains over 1500 files. ngspice should
run on various operating systems. Therefore errors may be found, some still evolving from the
original spice3f5 code, others introduced during the ongoing code enhancements.

If you happen to experience an error during compilation of ngspice, please send a report to the
development team. Ngspice is hosted on sourceforge, the preferred place to post a bug report is
[the ngspice bug tracker. We would prefer to have your bug tested against the actual source code](http://sourceforge.net/tracker/?group_id=38962&atid=423915)
available at Git, but of course a report using the most recent ngspice release is welcome! Please
provide the following information with your report: Ngspice version, Operating system, Small
input file to reproduce the bug (if to report a runtime error), Actual output versus the expected
output.


-----

