# Chapter 19

 ngspice as shared library or dynamic link library

ngspice may be compiled as a shared library. This allows adding ngspice to an application
that then gains control over the simulator. The shared module offers an interface that exports
functions controlling the simulator and callback functions for feedback.

So you may send an input ‘file’ with a netlist to ngspice, start the simulation in a separate thread,
read back simulation data at each time point, stop the simulator depending on some condition,
alter device or model parameters and then resume the simulation.

Shared ngspice does not have any user interface. The calling process is responsible for this. It
may offer a graphical user interface, add plotting capability or any other interactive element.
You may develop and optimize these user interface elements without a need to alter the ngspice
source code itself, using a console application or GUIs like gtk, Delphi, Qt or others.

## 19.1 Compile options

### 19.1.1 How to get the sources

Currently (as of ngspice-27 being the actual release), you will have to use the direct loading of
the sources from the git repository (see Chapt. 32.1.2).

### 19.1.2 Linux, MINGW, CYGWIN

Compilation is done as described in Chapts. 32.1 or 32.2.2. Use the configure option --with-ngshared
instead of --with-x or --with-wingui. In addition you might add (optionally) --enable-relpath
to avoid absolute paths when searching for code models. For MINGW you may edit compile_min.sh
accordingly and compile using this script in the MSYS2 window.

Other operation systems (Mac OS, BSD, ...) have not been tested so far. Your input is welcome!


-----

### 19.1.3 MS Visual Studio

Compilation is similar to what has been described in Chapt. 32.2.1. However, there is a dedicated project file coming with the source code to generate ngspice.dll. Go to the directory
```
visualc and start the project with double clicking on sharedspice.vcxproj.

## 19.2 Linking shared ngspice to a calling application

```
Basically there are two methods (as with all *.so, *.dll libraries). The caller may link to a (small)
library file during compiling/linking, and then immediately search for the shared library upon
being started. It is also possible to dynamically load the ngspice shared library at runtime using
the dlopen/LoadLibrary mechanisms.

### 19.2.1 Linking during creating the caller

While creating the ngspice shared lib, not only the *.so (*.dll) file is created, but also a small
library file, which just includes references to the exported symbols. Depending on the OS,
these may be called libngspice.dll.a, ngspice.lib. Linux and MINGW also allow linking to the
shared object itself. The shared object is not included into the executable component but is tied
to the execution.

### 19.2.2 Loading at runtime

dlopen (Linux) or LoadLibrary (MS Windows) will load libngspice.so or ngspice.dll into
the address space of the caller at runtime. The functions return a handle that may be used to
acquire the pointers to the functions exported by libngspice.so. Detaching ngspice at runtime
is equally possible (using dlclose/FreeLibrary), after the background thread has been stopped
and all callbacks have returned.

## 19.3 Shared ngspice API

The sources for the ngspice shared library API are contained in a single C file (sharedspice.c)
and a corresponding header file sharedspice.h. The type and function declarations are contained in sharedspice.h, which may be directly added to the calling application, if written in C
or C++.

### 19.3.1 structs and types defined for transporting data

pvector_info is returned by the exported function ngGet_Vec_Info (see 19.3.2.5). Addresses of
the vector name, type, real or complex data are transferred and may be read asynchronously
during or after the simulation.


-----

vector_info
```
   typedef struct vector_info {
     char *v_name; /* Same as so_vname */
     int v_type; /* Same as so_vtype */
     short v_flags; /* Flags (a combination of VF_*) */
     double *v_realdata; /* Real data */
     ngcomplex_t *v_compdata;/* Complex data */
     int v_length; /* Length of the vector */
  } vector_info, *pvector_info;

```
The next two structures are used by the callback function SendInitData (see 19.3.3.5). Each time
a new plot is generated during simulation, e.g. when a sequence of op, ac or tran is used, or
commands like linearize or fft are invoked, the function is called once by ngspice. Among
its parameters you find a pointer to a struct vecinfoall, which includes an array of vecinfo, one
for each vector. Pointers to the struct dvec, containing the vector, are included.

vecinfo
```
   typedef struct vecinfo
  {
    int number; /* number of vector, as position in the
                 linked list of vectors, starts with 0 */
    char *vecname; /* name of the actual vector */
    bool is_real; /* TRUE if the actual vector has real data */
    void *pdvec; /* a void pointer to struct dvec *d, the
                 actual vector */
    void *pdvecscale; /* a void pointer to struct dvec *ds,
                 the scale vector */
  } vecinfo, *pvecinfo;

```
vecinfoall
```
   typedef struct vecinfoall
  {
     /* the plot */
     char *name;
     char *title;
     char *date;
     char *type;
     int veccount;
     /* the data as an array of vecinfo with
       length equal to the number of vectors
       in the plot */
     pvecinfo *vecs;
  } vecinfoall, *pvecinfoall;

```

-----

The next two structures are used by the callback function SendData (see 19.3.3.4). Each time a
new data point (e.g. time value and simulation output value(s)) is added to the vector structure
of the current plot, the function SendData is called by ngspice, among its parameters the actual
pointer pvecvaluesall, which contains an array of pointers to pvecvalues, one for each vector.

vecvalues
```
   typedef struct vecvalues {
     char* name; /* name of a specific vector */
     double creal; /* actual data value */
     double cimag; /* actual data value */
     bool is_scale; /* if ’name’ is the scale vector */
     bool is_complex; /* if the data are complex numbers */
  } vecvalues, *pvecvalues;

```
Pointer vecvaluesall to be found as parameter to callback function SendData.

vecvaluesall
```
   typedef struct vecvaluesall {
     int veccount; /* number of vectors in plot */
     int vecindex; /* index of actual set of vectors, i.e.
                  the number of accepted data points */
     pvecvalues *vecsa; /* values of actual set of vectors,
                  indexed from 0 to veccount - 1 */
  } vecvaluesall, *pvecvaluesall;

### 19.3.2 Exported functions

```
The functions listed in this chapter are the (only) symbols exported by the shared library.

**19.3.2.1** **int ngSpice_Init(SendChar*, SendStat*, ControlledExit*, SendData*, SendInit-**
**Data*, BGThreadRunning*, void)**

After caller has loaded ngspice.dll, the simulator has to be initialized by calling ngSpice_Init(...).
Address pointers of several callback functions (see 19.3.3), which are to be defined in the caller,
are sent to ngspice.dll. The int return value is not used.

**Pointers to callback functions (details see 19.3.3):**

**SendChar* callback function for reading printf, fprintf, fputs (NULL allowed)**

**SendStat* callback function for reading status string and percent value (NULL allowed)**

**ControlledExit* callback function for transferring a flag to caller, generated by ngspice upon**
a call to function controlled_exit. May be used by caller to detach ngspice.dll, if dynamically loaded or to try any other recovery method, or to exit. (required)


-----

**SendData* callback function for sending an array of structs containing data values of all vec-**
tors in the current plot (simulation output) (NULL allowed)

**SendInitData* callback function for sending an array of structs containing info on all vectors**
in the current plot (immediately before simulation starts) (NULL allowed)

**BGThreadRunning* callback function for sending a boolean signal (true if thread is running)**
(NULL allowed)

**void* Using the void pointer, you may send the object address of the calling function (’self’ or**
’this’ pointer) to ngspice.dll. This pointer will be returned unmodified by any callback
function (see the *void pointers in Chapt. 19.3.3). Callback functions are to be defined
in the global section of the caller. Because they now have got the object address of the
calling function, they may direct their actions to the calling object.

**19.3.2.2** **int ngSpice_Init_Sync(GetVSRCData*, GetISRCData*, GetSyncData*, int*,**
**void*)**

see Chapt. 19.6.

**19.3.2.3** **int ngSpice_Command(char*)**

Send a valid command (see the control or interactive commands) from caller to ngspice.dll.
Will be executed immediately (as if in interactive mode). Some commands are rejected (e.g.
’plot’, because there is no graphics interface). Command ’quit’ will remove internal data, and
then send a notice to caller via ngexit(). The function returns a ’1’ upon error, otherwise ’0’.

**19.3.2.4** **bool ngSpice_running (void)**

Checks if ngspice is running in its background thread (returning ’true’).

**19.3.2.5** **pvector_info ngGet_Vec_Info(char*)**

uses the name of a vector (may be in the form ’vectorname’ or <plotname>.vectorname) as
parameter and returns a pointer to a vector_info struct. The caller may then directly assess the
vector data (but better should not modify them).

**19.3.2.6** **int ngSpice_Circ(char**)**

sends an array of null-terminated char* to ngspice.dll. Each char* contains a single line of a
circuit (Each line is like it is found in an input file *.sp.). The last entry to char** has to be
NULL. Upon receiving the array, ngspice.dll will immediately parse the input and set up the
circuit structure (as if the circuit is loaded from a file by the ’source’ command). The function
returns a ’1’ upon error, otherwise ’0’.


-----

**19.3.2.7** **char* ngSpice_CurPlot(void)**

returns to the caller a pointer to the name of the current plot. For a definition of the term ’plot’
see Chapt. 17.3.

**19.3.2.8** **char** ngSpice_AllPlots(void)**

returns to the caller a pointer to an array of all plots (listed by their typename).

**19.3.2.9** **char** ngSpice_AllVecs(char*)**

returns to the caller a pointer to an array of all vector names in the plot named by the string in
the argument.

**19.3.2.10** **bool ngSpice_SetBkpt(double)**

see Chapt. 19.6.

### 19.3.3 Callback functions

Callback functions are a means to return data from ngspice to the caller. These functions are
defined as global functions in the caller, so to be reachable by the C-coded ngspice. They are
declared according to the typedefs given below. ngspice receives their addresses from the caller
upon initialization with the ngSpice_Init(...) function (see 19.3.2.1). If the caller will not make
use of a callback, it may send NULL instead of the address (except for ControlledExit, which
is always required).

If ngspice is run in the background thread (19.4.2), the callback functions (defined in the caller)
also are called from within that thread. One has to be carefully judging how this behavior might
influence the caller, where now you have the primary and the background thread running in
parallel. So make the callback function thread safe. The integer identification number is only
used if you run several shared libraries in parallel (see Chapt. 19.6). Three additional callback
function are described in Chapt. 19.6.3.

**19.3.3.1** **typedef int (SendChar)(char*, int, void*)**

**char* string to be sent to caller output**

**int identification number of calling ngspice shared lib (default is 0, see Chapt. 19.6)**

**void* return pointer received from caller during initialization, e.g. pointer to object having sent**
the request

Sending output from stdout, stderr to caller. ngspice printf, fprintf, fputs, fputc functions are
redirected to this function. The char* string is generated by assembling the print outputs of
the above mentioned functions according to the following rules: The string commences with


-----

‘stdout ’, if directed to stdout by ngspice (with ‘stderr ’ respectively); all tokens are assembled in sequence, taking the printf format specifiers into account, until ‘\n’ is hit. If set
```
addescape is given in .spiceinit, the escape character \ is added to any character from $[]\"

```
found in the string.

Each callback function has a void pointer as the last parameter. This is useful in object oriented
programming. You may have sent the this (or self) pointer of the caller’s class object to ngspice.dll during calling ngSpice_Init (19.3.2.1). The pointer is returned unmodified by each
callback, so the callback function may identify the class object that has initialized ngspice.dll.

**19.3.3.2** **typedef int (SendStat)(char*, int, void*)**

**char* simulation status and value (in percent) to be sent to caller**

**int identification number of calling ngspice shared lib (default is 0, see Chapt. 19.6)**

**void* return pointer received from caller**

sending simulation status to caller, e.g. the string tran 34.5%.

**19.3.3.3** **typedef int (ControlledExit)(int, bool, bool, int, void*)**

**int exit status**

**bool if true: immediate unloading dll, if false: just set flag, unload is done when function has**
returned

**bool if true: exit upon ’quit’, if false: exit due to ngspice.dll error**

**int identification number of calling ngspice shared lib (default is 0, see Chapt. 19.6)**

**void* return pointer received from caller**

asking for a reaction after controlled exit.

**19.3.3.4** **typedef int (SendData)(pvecvaluesall, int, int, void***

**vecvaluesall* pointer to array of structs containing actual values from all vectors**

**int number of structs (one per vector)**

**int identification number of calling ngspice shared lib (default is 0, see Chapt. 19.6)**

**void* return pointer received from caller**

send back actual vector data.


-----

**19.3.3.5** **typedef int (SendInitData)(pvecinfoall, int, void*)**

**vecinfoall* pointer to array of structs containing data from all vectors right after initialization**

**int identification number of calling ngspice shared lib (default is 0, see Chapt. 19.6)**

**void* return pointer received from caller**

send back initialization vector data.

**19.3.3.6** **typedef int (BGThreadRunning)(bool, int, void*)**

**bool true if background thread is running**

**int identification number of calling ngspice shared lib (default is 0, see Chapt. 19.6)**

**void* return pointer received from caller**

indicate if background thread is running

## 19.4 General remarks on using the API

### 19.4.1 Loading a netlist

Basically the input to shared ngspice is the same as if you would start a ngspice batch job, e.g.
you enter a netlist and the simulation command (any .dot analysis command like .tran, .op,
or .dc etc. as found in Chapt. 15.3), as well as suitable options.

Typically you should not include a .control section in your input file. Any script described
in a .control section for standard ngspice should better be emulated by the caller and be sent
directly to ngspice.dll. Start the simulation according to Chapt. 19.4.2 in an extra thread.

As an alternative, only the netlist has to be entered (without analysis command), then you may
use any interactive command as listed in Chapt. 17.5 (except for the plot command).

The ‘typical usage’ examples given below are excerpted from a caller written in C.

**19.4.1.1** **Loading from file**

As with interactive ngspice, you may use the ngspice internal command source (17.5.71) to
load a complete netlist from a file.

Typical usage:
```
   ngSpice_Command("source ../examples/adder_mos.cir");

```

-----

**19.4.1.2** **Loading line by line**

As with interactive ngspice, you may use the ngspice internal command circbyline (17.5.10) to
send a netlist line by line to the ngspice circuit parser.

Typical usage:
```
   ngSpice_Command("circbyline fail test");
   ngSpice_Command("circbyline V1 1 0 1");
   ngSpice_Command("circbyline R1 1 0 1");
   ngSpice_Command("circbyline .dc V1 0 1 0.1");
   ngSpice_Command("circbyline .end");

```
The first line is a title line, which will be ignored during circuit parsing. As soon as the line
```
.end has been sent to ngspice, circuit parsing commences.

```
**19.4.1.3** **Loading as a string array**

Typical usage:
```
   circarray = (char**)malloc(sizeof(char*) * 7);
   circarray[0] = strdup("test array");
   circarray[1] = strdup("V1 1 0 1");
   circarray[2] = strdup("R1 1 2 1");
   circarray[3] = strdup("C1 2 0 1 ic=0");
   circarray[4] = strdup(".tran 10u 3 uic");
   circarray[5] = strdup(".end");
   circarray[6] = NULL;
   ngSpice_Circ(circarray);

```
An array of char pointers is malloc’d, each netlist line is then copied to the array. strdup will
care for the memory allocation. The first entry to the array is a title line, the last entry has to
contain NULL. ngSpice_Circ(circarray); sends the array to ngspice, where circuit parsing is
started immediately. Don’t forget to free the array after sending it, to avoid a memory leak.

### 19.4.2 Running the simulation

The following commands are used to start the simulator in its own thread, halt the simulation
and resume it again. The extra (background) thread enables the caller to continue with other
tasks in the main thread, e.g. watching its own event loop. Of course you have to take care
that the caller will not exit before ngspice is finished, otherwise you immediately will loose all
data. After having halted the simulator by suspending the background thread, you may assess
data, change ngspice parameters, or read output data using the caller’s main thread, before you
resume simulation using a background thread again. While the background thread is running,
ngspice will reject any other command sent by ngSpice_Command.


-----

Typical usage:
```
   ngSpice_Command("bg_run");
   ...
   ngSpice_Command("bg_halt");
   ...
   ngSpice_Command("bg_resume");

```
Basically you may send the commands ’run’ or ’resume’ (no prefix bg_), starting ngspice within
the main thread. The caller then has to wait until ngspice returns from simulation. A command
’halt’ is not available then.

After simulation is finished (test with callback 19.3.3.6), you may send other commands from
Chapt. 17.5, emulating any .control script. These commands are executed in the main thread,
which should be okay because execution time is typically short.

### 19.4.3 Accessing data

**19.4.3.1** **Synchronous access**

The callback functions SendInitData (19.3.3.5) and SendData (19.3.3.4) allow access to simulator output data synchronized with the simulation progress.

Each time a new plot is generated during simulation, e.g. when a sequence of op, ac and tran is
used or commands like linearize or fft are invoked, the callback SendInitData is called by
ngspice. Immediately after setting up the vector structure of the new plot, the function is called
once. Its parameter is a pointer to the structure vecinfoall (19.3.1), which contains an array of
structures vecinfo, one for each vector in the actual plot. You may simply use vecname to get
the name of any vector. This time the vectors are still empty, but pointers to the vector structure
are available.

Each time a new data point (e.g. time value and simulation output value(s)) is added to the
vector structure of the current plot, the function SendData is called by ngspice. This allows
you to immediately access the simulation output synchronized with the simulation time, e.g.
to interface it to a runtime plot or to use it for some controlled simulation by stopping the
simulation based on a condition, altering parameters and resume the simulation. SendData
returns a structure vecvaluesall as parameter, which contains an array of structures vecvalues,
one for each vector.

Some code to demonstrate the callback function usage is referenced below (19.5).

**19.4.3.2** **Asynchronous access**

During simulation, while the background thread is running, or after it is finished, you may
use the functions ngSpice_CurPlot (19.3.2.7), ngSpice_AllPlots (19.3.2.8), ngSpice_AllVecs
(19.3.2.9) to retrieve information about vectors available, and function ngGet_Vec_Info (19.3.2.5)
to obtain data from a vector and its corresponding scale vector. The timing of the caller and the
simulation progress are independent from each other and not synchronized.

Again some code to demonstrate the callback function usage is referenced below (19.5).


-----

### 19.4.4 Altering model or device parameters

After halting ngspice by stopping the background thread (19.4.2), nearly all ngspice commands
are available. Especially alter (17.5.3) and altermod (17.5.4) may be used to change device
or model parameters. After the modification, the simulation may be resumed immediately.
Changes to a circuit netlist, however, are not possible. You would need to load a complete new
netlist (19.4.1) and restart the simulation from the beginning.

### 19.4.5 Output

After the simulation is finished, use the ngspice commands write (17.5.89) or wrdata (17.5.88)
to output data to a file as usual, use the print command (17.5.47) to retrieve data via callback
**SendChar (19.3.3.1), or refer to accessing the data as described in Chapt. 19.4.3.**

Typical usage:
```
   ngSpice_Command("write testout.raw V(2)");
   ngSpice_Command("print V(2)");

### 19.4.6 Error handling

```
There are several occasions where standard ngspice suffers from an error, cannot recover internally and then exits. If this is happening to the shared module this would mean that the
parent application, the caller, is also forced to exit. Therefore (if not suffering from a segfault) ngspice.dll will call the function controlled_exit as usual, this now calls the callback
function ’ControlledExit’ (19.3.3.3), which hands over the request for exiting to the caller. The
caller now has the task to handle the exit code for ngspice.

If ngspice has been linked at runtime by dlopen/LoadLibrary (see 19.2.2), the callback may
close all threads, and then detach ngspice.dll by invoking dlclose/FreeLibrary. The caller
may then restart ngspice by another loading and initialization (19.3.2.1).

If ngspice is included during linking the caller (see 19.2.1), there is not yet a good and general
solution to error handling, if the error is non-recoverable from inside ngspice.

## 19.5 Example applications

Three executables (coming with source code) serve as examples for controlling ngspice. These
are not meant to be ‘production’ programs, but just give some commented example usages of
the interface.

ng_start.exe is a MS Windows application loading ngspice.dll dynamically. All functions
and callbacks of the interface are assessed. The source code, generated with Turbo Delphi
[2006, may be found here, the binaries compiled for 32 Bit are here.](http://ngspice.sourceforge.net/ngspice-shared-lib/ng_dll_src_delphi.7z)

Two console applications, compilable with Linux, CYGWIN, MINGW or MS Visual Studio,
[are available here, demonstrating either linking upon start-up or loading shared ngspice dyna-](http://ngspice.sourceforge.net/ngspice-shared-lib/ngspice_cb.7z)
mically at runtime. A simple feedback loop is shown in tests 3 and 4, where a device parameter
is changed upon having an output vector value crossing a limit.


-----

## 19.6 ngspice parallel

The following chapter describes an offer to the advanced user and developer community. If you
are interested in evaluating the parallel and synchronized operation of several ngspice instances,
this may be one way to go. However, no ready to use implementation is available. You will
find a toolbox and some hints how to use it. Parallelization and synchronization is your task by
developing a suitable caller! And of course another major input has to come from partitioning
the circuit into suitable, loosely coupled pieces, each with its own netlist, one netlist per ngspice
instance. And you have to define the coupling between the circuit blocks. Both are not provided
by ngspice, but are again your responsibility. Both are under active research, and the toolbox
described below is an offer to join that research.

### 19.6.1 Go parallel!

A simple way to run several invocations of ngspice in parallel for transient simulation is to define
a caller that loads two or more ngspice shared libraries. There is one prerequisite however
to do so: the shared libraries have to have different names. So compile ngspice shared lib
(see 19.1), then copy and rename the library file, e.g. ngspice.dll may become ngspice1.dll,
ngspice2.dll etc. Then dynamically load ngspice1.dll, retrieve its address, initialize it by
calling ngSpice_init() (see 19.3.2.1), then continue initialization by calling ngSpice_init_Sync()
(see 19.6.2.1). An integer identification number may be sent during this step to later uniquely
identify each invocation of the shared library, e.g. by having any callback use this identifier.
Repeat the sequence with ngspice2.dll and so on.

Inter-process communication and synchronization is now done by using three callback functions. To understand their interdependence, it might be useful to have a look at the transient
simulation sequence as defined in the ngspice source file dctran.c. The following listing includes the shared library option (It differs somewhat from standard procedure) and disregards
XSPICE.

1. initialization

2. calculation of operating point

3. next time step: set new breakpoints (VSRC, ISRC, TRA, LTRA)

4. send simulation data to output, callback function SendData* datfcn

5. check for autostop and other end conditions

6. check for interrupting simulation (e.g. by bg_halt)

7. breakpoint handling (e.g. enforce breakpoint, set new small cktdelta if directly after the
breakpoint)

8. calling ngspice internal function sharedsync() that invokes callback function GetSyn**cData* getsync with location flag loc = 0**

9. save the previous states

10. start endless loop


-----

11. save cktdelta to olddelta, set new time point by adding cktdelta to ckttime

12. new iteration of circuit at new time point, which uses callback functions GetVSRCData*
**getvdat and GetISRCData* getidat to retrieve external voltage or current inputs, returns**
redostep=0, if converged, redostep=1 if not converged

13. if not converged, divide cktdelta by 8

14. check for truncation error with all non-linear devices, if necessary create a new (smaller)
cktdelta to limit the error, optionally change integration order

15. calling ngspice internal function sharedsync() that invokes callback function GetSyn**cData* getsync with location flag loc = 1: as a result either goto 3 (next time step) or to**
10 (loop start), depending on ngspice and user data, see the next paragraph.

The code of the synchronization procedure is handled in the ngspice internal function sharedsync() and its companion user defined callback function GetSyncData* getsync. The actual
setup is as follows:

If no synchronization is asked for (GetSyncData* set to NULL), program control jumps to ’next
time step’ (3) if redostep==0, or subtracts olddelta from ckttime and jumps to ’loop start’ (9) if
redostep <> 0. This is the standard ngspice behavior.

If GetSyncData* has been set to a valid address by ngSpice_Init_Sync(), the callback function
**getsync is involved. If redostep <> 0, olddelta is subtracted from ckttime, getsync is called,**
either the cktdelta time suggested by ngspice is kept or the user provides his own deltatime,
and the program execution jumps to (9) for redoing the last step with the new deltatime. The
return value of getsync is not used. If redostep == 0, getsync is called. The user may keep
the deltatime suggested by ngspice or define a new value. If the user sets the return value of
**getsync to 0, the program execution then jumps to ’next time step’ (3). If the return value of**
**getsync is 1, olddelta is subtracted from ckttime, and the program execution jumps to (9) for**
redoing the last step with the new deltatime. Typically the user provided deltatime should be
smaller than the value suggested by ngspice.

### 19.6.2 Additional exported functions

The following functions (exported or callback) are designed to support the parallel action of
several ngspice invocations. They may be useful, however, also when only a single library
is loaded into a caller, if you want to use external voltage or current sources or ’play’ with
advancing simulation time.

**19.6.2.1** **int ngSpice_Init_Sync(GetVSRCData*, GetISRCData*, GetSyncData*, int*,**
**void*)**

**Pointers to callback functions (details see 19.3.3):**

**GetVSRCData* callback function for retrieving a voltage source value from caller (NULL**
allowed)


-----

**GetISRCData* callback function for retrieving a current source value from caller (NULL al-**
lowed)

**GetSyncData* callback function for synchronization (NULL allowed)**

**More pointers**

**int* pointer to integer unique to this shared library (defaults to 0)**

**void* pointer to user-defined data, will not be modified, but handed over back to caller during**
Callback, e.g. address of calling object. If NULL is sent here, userdata info from ngSpice_Init() will be kept, otherwise userdata will be overridden by new value from here.

**19.6.2.2** **bool ngSpice_SetBkpt(double)**

Sets a breakpoint in ngspice, a time point that the simulator is enforced to hit during the transient
simulation. After the breakpoint time has been hit, the next delta time starts with a small value
and is ramped up again. A breakpoint should be set only when the background thread in ngspice
is not running (before the simulation has started, or after the simulation has been paused by
bg_halt). The time sent to ngspice should be larger than the current time (which is either 0
before start or given by the callback GetSyncData (19.6.3.3). Several breakpoints may be set.

### 19.6.3 Additional callback functions

**19.6.3.1** **typedef int (GetVSRCData)(double*, double, char*, int, void*)**

**double* return voltage value**

**double actual time**

**char* node name**

**int identification number of calling ngspice shared lib**

**void* return pointer received from caller**

Ask for a VSRC EXTERNAL voltage value. The independent voltage source (see Chapt. 4.1)
with EXTERNAL option allows to set a voltage value to the node defined in the netlist and
named here at the time returned by the simulator.

**19.6.3.2** **typedef int (GetISRCData)(double*, double, char*, int, void*)**

**double* return current value**

**double actual time**

**char* node name**

**int identification number of calling ngspice shared lib**


-----

**void* return pointer received from caller**

Ask for ISRC EXTERNAL value. The independent current source (see Chapt. 4.1) with EXTERNAL option allows to set a current value to the node defined by the netlist and named here
at the time returned by the simulator.

**19.6.3.3** **typedef int (GetSyncData)(double, double*, double, int, void*)**

**double actual time (ckt->CKTtime)**

**double* delta time (ckt->CKTdelta)**

**double old delta time (olddelta)**

**int identification number of calling ngspice shared lib**

**int location of call for synchronization in dctran.c**

**void* return pointer received from caller**

Ask for new delta time depending on synchronization requirements. See 19.6.1 for an explanation.

### 19.6.4 Parallel ngspice example

[A first example is available as a compacted 7z archive. It contains the source code of a control-](http://ngspice.sourceforge.net/ngspice-shared-lib/ngspice_sync_win.7z)
ling application, as well as its compiled executable and ngspice.dll (for MS Windows). As the
input circuit an inverter chain has been divided into three parts. Three ngspice shared libraries
are loaded, each simulates one partition of the circuit. Interconnections between the partitions
are provided via a callback function. The simulation time is synchronized among the three
ngspice invocations by another callback function.


-----

