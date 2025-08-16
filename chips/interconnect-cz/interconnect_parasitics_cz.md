# EXACT Interconnect Parasitic Characterization

#### Application Examples


![](interconnect_parasitics_cz.pdf-0-0.png)

-----

![](interconnect_parasitics_cz.pdf-1-0.png)

## Introduction

###  EXACT delivers the most accurate interconnect models for

#### nanometer semiconductor processes and generates layout parameter extraction (LPE) rule files for leading full chip extraction tools 

###  EXACT’s powerful 3D field solvers support xCalibre, Calibre xRC,

#### Diva, Assura RCX, and Dracula LPE


**EXACT** **Application Examples**



- 2 

-----

![](interconnect_parasitics_cz.pdf-2-0.png)

## Introduction: Exact Flow

###  EXACT takes process information and produces LPE 

#### rule decks


**EXACT** **Application Examples**



- 3 

-----

![](interconnect_parasitics_cz.pdf-3-0.png)

## Introduction: Key Benefits

###  Powerful 3D solver supports non-planar semiconductor profiles

#### and dummies

###  3D field solver calculates interconnect capacitance models
  Intuitive and user-friendly graphical interface for process layer

#### description and test structure definition 

###  Standard mode of operation handles most conventional processes 
  Integrated scripting language provides custom LPE rule files for

#### other extraction tools

###  Powerful statistical analysis module option available to calculate

#### variations of capacitance


**EXACT** **Application Examples**



- 4 

-----

![](interconnect_parasitics_cz.pdf-4-0.png)

## Introduction: Ease of Use and Adoption

###  Easy to use, menu-driven graphical interface for process layer

#### definition

###  Menu-driven parameterized layout generator for test structure and

#### pattern generation 

###  Easy LPE rule generation with LISA™ scripting language
  Flexible architecture for fitting raw parasitic data into a wide range

#### of custom equations for xCalibre/Calibre xRC, and Assura-RCX/ Diva/Dracula LPE

###  Easy to understand extracted capacitance tables that facilitate the

#### analysis of effects on interconnect due to various process change or experiment

###  Automatic mesh and deck generation and submission to 3D field

#### solver


**EXACT** **Application Examples**



- 5 

-----

![](interconnect_parasitics_cz.pdf-5-1.png)

## Introduction: Importance of Accurate Parasitic Extraction

###  Parasitics now dominate circuit timing         

Source: SIA Roadmap 1997


![](interconnect_parasitics_cz.pdf-5-0.png)

**EXACT** **Application Examples**



- 6 

-----

![](interconnect_parasitics_cz.pdf-6-1.png)

## Introduction: Data Required for Deep Sub-Micron Designs

####  Lateral capacitance plot

##### versus spacing between two conducting lines

####  The figure shows that in this

##### simple case, the capacitance can vary by a factor of 4 between minimum spacing and only 1 micron away.

####  Typical foundry data above

##### would only provide the first point on this graph


![](interconnect_parasitics_cz.pdf-6-0.png)

**EXACT** **Application Examples**



- 7 

-----

![](interconnect_parasitics_cz.pdf-7-0.png)

## Introduction: Data Required for Deep Sub-Micron Designs (con’t)

###  What should the LPE Tool do if only the minimum spacing

#### coefficient data are provided... Guess? Ignore? Use the value for minimum spacing?

###  None of the above options are acceptable for deep sub-micron

#### technologies . An accurate value must be known for all geometries

###  Different widths of conductor and other geometries require different

#### capacitance coefficients

#####  E.g., A line over a line will result in a significantly different coefficient value

###### compared to a line over a ground plane.


**EXACT** **Application Examples**



- 8 

-----

![](interconnect_parasitics_cz.pdf-8-0.png)

## Introduction: Data Required for Deep Sub-Micron Designs (con’t)

###  Other typical configurations

##### 1/ Co-incident edges 2/ Cross overs 3/ Corners 4/ Proximity effects

###  EXACT can generate coefficients for ANY structure


**EXACT** **Application Examples**



- 9 

-----

![](interconnect_parasitics_cz.pdf-9-0.png)

## Workshop Summary

###  Getting started
  Defining a process flow

####  (i) Simple processing using the Interactive Tool
  (ii) Advanced process flow        

###  Defining and editing layout 
  Test structures        
  Defining the “Design of Experiments” (DOE)        
  Executing the experiments       
  Processing the data


**EXACT** **Application Examples**



- 10 

-----

![](interconnect_parasitics_cz.pdf-10-1.png)

## EXACT GUI

###  Type “EXACT” in a shell

#### window to display this EXACT G.U.I. 

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-10-0.png)


- 11 

-----

![](interconnect_parasitics_cz.pdf-11-0.png)

## 5 Stages of EXACT

###  EXACT takes you through the 5 stages sequentially:

####  STAGE 1 Process Stage: Define the process 
  STAGE 2 Layout Stage: Define or load the test structure mask layouts 
  STAGE 3 Design of Experiments Stage: Select which experiments 
  STAGE 4 Run Stage: Run the experiments using the 3D process

##### simulator and field solver

####  STAGE 5 Analysis Stage: Write or import a script to process all the data     


**EXACT** **Application Examples**



- 12 

-----

![](interconnect_parasitics_cz.pdf-12-1.png)

## Define the Process Flow: Standard Mode

###  The Standard Mode option

#### allows quick “interactive” creation of a simple process flow 

###  This creates simple

#### “planar” structures

###  Click “OK” when finished


![](interconnect_parasitics_cz.pdf-12-0.png)

**EXACT** **Application Examples**



- 13 

-----

![](interconnect_parasitics_cz.pdf-13-0.png)

## Define the Process Flow: Advanced Mode

###  The Advanced Mode option allows the use of realistic

#### photolithography, deposition or etching to create the test structures:

###  In the Advanced mode users can: 

#### i. create their own process flow    ii. edit a previous process flow from the interactive (from the Standard

##### Mode) builder   

#### iii. edit a CLEVER input deck 

###  We shall only deal with the Standard Mode option in this workshop


**EXACT** **Application Examples**



- 14 

-----

![](interconnect_parasitics_cz.pdf-14-1.png)

## Process Preview with the Internal Viewer of EXACT

####  Having entered the

##### process via the Standard Mode, the  process verification is made possible using the “process preview” button in the process GUI 


![](interconnect_parasitics_cz.pdf-14-0.png)

**EXACT** **Application Examples**



- 15 

-----

![](interconnect_parasitics_cz.pdf-15-0.png)

## Layout Stage

###  After having entered the process the test structure specific to which

#### required capacitance coefficient are then loaded into EXACT

  Standard generic test structures will be provided for various Extraction

##### (LPE) Tools 

####  Load test structures using the layout GUI
  The layout GUI also allows user to create their own test structures

##### using the “more options” mode of EXACT layout GUI 


**EXACT** **Application Examples**



- 16 

-----

![](interconnect_parasitics_cz.pdf-16-1.png)

## Example of a Layout Test Structure 

###  An example of a layout test

#### structure is shown here

###  From the test structure

#### capacitances such as near body capacitance (the capacitance between two wires of the same process layer) are easily obtained


![](interconnect_parasitics_cz.pdf-16-0.png)

**EXACT** **Application Examples**



- 17 

-----

![](interconnect_parasitics_cz.pdf-17-1.png)

## Loading a Layout

####  Click “Layout...” to bring up

##### the Layout Editor Window

####  Click on load layout to load

##### in a layout

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-17-0.png)


- 18 

-----

![](interconnect_parasitics_cz.pdf-18-1.png)

## Loading a Layout

####  This figure shows the layout

##### One Array that has been loaded into the layout GUI

####  All of the layout definition is

##### also shown

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-18-0.png)


- 19 

-----

![](interconnect_parasitics_cz.pdf-19-1.png)

## Creating a Layout: More Choices

####  By clicking on the “more choices”

##### button in the layout GUI users have the ability to create a layout 

####  User defined layout: “layers” and

##### “wires” button are added to allow you to define any kind of layout


![](interconnect_parasitics_cz.pdf-19-0.png)

**EXACT** **Application Examples**



- 20 

-----

![](interconnect_parasitics_cz.pdf-20-1.png)

## Layout: Combination Selection

####  Which process layers are assigned

##### to which layout layers is performed via the combination selection in the layout GUI 

####  Select these by clicking on “Select”
  You may not be interested in all of

##### them 

####  For example, you may not be

##### interested in calculating the capacitance between Metal 4 and the substrate because they are very far apart

####  You can select such combination

##### individually, or use the automatic selection


![](interconnect_parasitics_cz.pdf-20-0.png)

**EXACT** **Application Examples**



- 21 

-----

![](interconnect_parasitics_cz.pdf-21-1.png)

## Layout: Preview

####  Any layout loaded into the layout

##### GUI, or created in the GUI, can be viewed together with any dynamic properties it possesses

####  Test structures in EXACT are

##### defined using an interactive menu. Slide bars allow users to observe the effects of layout changes on the parameterized structure

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-21-0.png)


- 22 

-----

![](interconnect_parasitics_cz.pdf-22-0.png)

## Layout: Preview

###  To see each structure click on “preview”
  For plane view, click “plan” 
  To see a cross-sectional view “side”    
  This gives a cutline using the user definable co-ordinates in the 2D

#### Cutline box 

###  To visualize the effect of varying the layout parameters, move

#### sliders               

###  When in 2D or 3D mode use the sliders to vary the parameters


**EXACT** **Application Examples**



- 23 

-----

![](interconnect_parasitics_cz.pdf-23-1.png)

## Field Solver

####  Some control of the field solver attributes is given to the user. This figure

##### shows the Field Solver GUI

####  Use this window in EXACT to define the accuracy of the simulation using

##### the “tolerance” and the “accuracy level” buttons 


![](interconnect_parasitics_cz.pdf-23-0.png)

**EXACT** **Application Examples**



- 24 

-----

![](interconnect_parasitics_cz.pdf-24-1.png)

## Output

####  Next we must define where the data that EXACT generates is to be stored, the

##### output GUI, allows this to be done

####  User defined database location where all the files will be stored
  Structure files can also be saved in order to be visualized using TonyPlot


![](interconnect_parasitics_cz.pdf-24-0.png)

**EXACT** **Application Examples**



- 25 

-----

![](interconnect_parasitics_cz.pdf-25-1.png)

## DOE

####  The design of experiments stage is

##### entered by clicking on the DOE button 

####  Click “DOE...” to bring up DOE window
  Use the DOE window to select the

##### variable ranges and sample points  

####  Flexible design of experiment.

##### (full factorial, stepped, ccc)

####  Ability to change design parameters as

##### well as process parameters


![](interconnect_parasitics_cz.pdf-25-0.png)

**EXACT** **Application Examples**



- 26 

-----

![](interconnect_parasitics_cz.pdf-26-1.png)

## Running Simulations

####  After having finished setting up the simulation experiments, we can run them by

##### clicking on the run button. The Run GUI open up is shown in this figure

####  We can can follow the running of the experiment 
  At any stage in the execute window, click on view log shows the exact process

##### flow being executed for that particular job (see figure on the following page)


![](interconnect_parasitics_cz.pdf-26-0.png)

**EXACT** **Application Examples**



- 27 

-----

![](interconnect_parasitics_cz.pdf-27-1.png)

## Run

####  At any moment in the run window,

##### click the View Log… button for any of the experiments to visualize the exact process flow being executed for that particular job

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-27-0.png)


- 28 

-----

![](interconnect_parasitics_cz.pdf-28-1.png)

## Analysis Stage

####  Once the experiments have been

##### simulated, click on the analysis window

####  We provide scripts to plot all the

##### data (CSV and TonyPlot format)

####  The user must now write scripts to

##### format data to LPE tools specific format. We provide templates for Diva™, XCalibre™, and HIPEX

####  Direct link to SPAYN

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-28-0.png)


- 29 

-----

![](interconnect_parasitics_cz.pdf-29-1.png)

## Analysis: Script

###  Load a script file (written

#### in LISA) 

###  In this example a script

#### has been loaded into the Analysis Stage

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-29-0.png)


- 30 

-----

![](interconnect_parasitics_cz.pdf-30-1.png)

## Analysis: Script Output

###  Mentor Graphics

#### xCalibre™/Calibre xRC™ rule file generated by EXACT using the associated script file

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-30-0.png)


- 31 

-----

![](interconnect_parasitics_cz.pdf-31-1.png)

## Filed Solver Results

####  Field solver results and fitted

##### equation for the structure on the left

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-31-0.png)


- 32 

-----

![](interconnect_parasitics_cz.pdf-32-0.png)

## Automatic Models

###  Exact can automate the generation of parameters for use in Hipex
  Define a process (in either Standard or Advanced mode)
  Select the Model->Hipex menu
  Exact will load a set of pre-defined layouts that it needs, and run a

#### series of simulations and perform equation fitting to generate the Hipex parameters, all automatically

###  You can override the default for the variables used
  Exact saves a LISA file for HIPEX, and saves all of its own project

#### files


**EXACT** **Application Examples**



- 33 

-----

![](interconnect_parasitics_cz.pdf-33-1.png)

## Model HIPEX Output

###  Extract from a

#### HIPEXscript generated with ‘Model Hipex’

**EXACT** **Application Examples**


![](interconnect_parasitics_cz.pdf-33-0.png)


- 34 

-----

![](interconnect_parasitics_cz.pdf-34-0.png)

## Summary

###  Today we have shown you how simple it is to use “EXACT”

####  To create or use existing test structures using a real process flow     
  Either realistic or simple 3D processing can be used     
  Set up and run a design of experiments using a 3D field solver     
  Process the data for LPE tools   

###  EXACT (will) increases the accuracy of full chip parasitic extraction   
  EXACT can be used in conjunction with ANY full chip extraction

#### tool


**EXACT** **Application Examples**



- 35 

-----

