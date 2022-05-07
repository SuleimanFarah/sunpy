# Application for GSOC 2015

## Student Information

* **Name:** Rupak Kumar Das
* **Email:** rupak0577@gmail.com
* **Time-zone:** +0530 GMT
* **IRC Handle:** tars7297@irc.freenode.net
* **Github:** rupak0577
* **Blog:** <https://rupakgsoc2015.wordpress.com/>
* **Blog RSS feed:** <https://rupakgsoc2015.wordpress.com/feed/?tag=GSOC%2CPython>

## University Information

* **University:** Institute of Technical Education and Research
* **Major:** Computer Science and Engineering
* **Current year:** Second year
* **Graduation Date:** 2017
* **Degree:** Bachelor of Technology

## Project Proposal Information

**Proposal Title:** SunPy – Full support for IRIS, 4D Cubes implemented using Ginga as the GUI

### **Abstract:**

The satellite 'IRIS' and other telescopes use a 4D cube data structure to save their data. Currently, SunPy does not have support for this structure which this project aims to remedy.

This will be done in two phases -

**1)** A previous ESA summer project already implemented such a structure in SunPy. Though finished, it was not merged into the code base. This project will tweak the package so that it works with the latest version of SunPy, with some minor changes in the call API and some changes in the SunPy Map class to integrate the new module.

**2)** A GUI plugin to view and perform basic operations on 3D/4D data will be created for Ginga, which is a tool for viewing scientific image data using Python. A GUI called 'CRISPEX' , programmed in IDL, already exists for such purposes but this project will implement a GUI specifically for SunPy using Ginga, while using CRISPEX as a reference. Since it uses Qt as a backend for the GUI, the plugin will be created using PyQt and Python.

The primary goal will be to tweak and merge the cube class which will bring the support for IRIS, SST, EIS and every other 3D+ data format to SunPy with the secondary goal being the GUI.

## Software packages to be used

* **Language:** Python
* **GUI library:** PyQt
* **GUI Framework:** Ginga

## Deliverables

**1.** Integration of the cube module

**2.** Implementation of the GUI

**3.** Documentation for the changes

## Detailed Description

|Period|Description|
|------|-----------|
|Community Bonding Period (April 27 – May 25)|First priority is to integrate the Cube module so read documentation and source code relating to the Map,Cube and Spectra modules. Consult with mentors and have a complete idea of how the modules work and the required changes to be done before the integration. Then, read the documentation for Ginga and its plugin structure. Discuss with mentors for potential ideas about the GUI and its implementation.
|May 26 – June 9 (2 weeks)|Begin work on the Cube module, tweaking and adding required code for its integration.
|June 9 – June 16 (1 week)|Document changes and write required tests.
|June 17 – June 26 (1.3 weeks)|Update Map module along with Spectra module.
|June 27 – July 3 (1 week)|Finish incomplete work.Mid-term evaluation.
|July 4 – July 18 (2 weeks)|Begin work on the GUI plugin. Implement the basic functionality that is required from the plugin.
|July 19 – August 2 (2 weeks)|As per discussion with mentors, implement extra features from CRISPEX
|August 3 - August 9 (1 week)|Document code and write tests.
|August 10 - August 17 (1 week)|Integrate everything into SunPy and fix issues.
|August 17 - August 24 (1 week)|'Pencils-down' date. Finalize everything,fix bugs,improve documentation and make sure everything works.

## Code Samples

**1.** Wrote a test for stereo sources [#1267] (<https://github.com/sunpy/sunpy/pull/1267>)

**2.** Although not for SunPy, fixed a small issue for SciPy which was merged [#4407] (<https://github.com/scipy/scipy/pull/4407>)

## Commitment

Since I have no plans for the summer, I will dedicate the 3 months to completing this project. But I must inform that the classes for my next semester might start during the last week of July or the first week of August(the schedule has not been decided, though it generally starts in the first week of August) which falls within the period of GSoC. Therefore, though I will have less time to devote to the project, I will try my best to make up the lost time if the project demands it(due to less workload during the opening weeks). And if the project's goals are extended in any way and it isn't complete within the GsoC period, I will continue contributing until the everything is implemented.

## References

**1.** [IRIS and CRISPEX reference] (<http://iris.lmsal.com/itn26/>)

**2.** [Cubes module] (<https://github.com/sunpy/sunpy/pull/1078/files>)

**3.** [Ginga-sunpy plugin repo] (<https://github.com/sunpy/ginga-sunpy>)
