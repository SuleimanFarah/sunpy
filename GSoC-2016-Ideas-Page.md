---
layout: default
title:  "Ideas for SunPy"
show_main: false
ideas_team: SunPy core package
---

### Improvements to the SunPy Database

*Suggested Mentor(s):* [Stuart Mumford](http://github.com/Cadair), [Steven Christe](http://github.com/ehsteve)

*Difficulty:* Beginner

*Astronomy knowledge needed:* None

*Programming skills:* Python, some database knowledge would be helpful, but not required.

#### Description
The `database` module provides functionality to users to manage collections of files on disk in a way not reliant upon folder structure and file name.
The database allows users to find files on disk by either physical parameters, such as wavelength and time or properties of the instrument such as name and spacecraft.
It also allows more complex queries by enabling searches of the raw meta data associated with the files.

The improvements to the database functionality that would be implemented by this project include:

1. Integration of the new `UnifiedDownloader` code into the database search, to replace the direct VSO integration current present. (The [VSO](http://vso1.nascom.nasa.gov/) is a repository of solar physics data, SunPy's VSO API has been wrapped by `UnifiedDownloader`.)
1. Support for relative paths in the database module [#783](https://github.com/sunpy/sunpy/issues/783) to allow a centralised database with multiple users, all referencing a central file store mounted with different absolute paths on each client.
1. Supporting all data supported by the `sunpy.lightcurve` module in the database. The major hurdle here is the lack of standardisation in the file used by this data.

There are various other maintenance tasks which need undertaking (https://github.com/sunpy/sunpy/labels/Database) which would be a good way for someone interested in this project to familiarise themselves with the codebase.

### Integrating ChiantiPy and SunPy

*Suggested Mentor(s):* [Dan Ryan](https://github.com/DanRyanIrish), [Ken Dere](http://sourceforge.net/u/kdere/profile/)

*Difficulty:* Beginner

*Astronomy knowledge needed:* Some knowledge of spectra.

*Programming skills:* Python.

####Description

The [CHIANTI](http://www.chiantidatabase.org/) atomic physics database is a valuable resource for solar physics. The CHIANTI database holds a large amount of information on the physical properties of different elements in different ionisation states and enabled the calculation of various parameters from this information. Using CHIANTI it is possible to calculate the spectra of various types of solar plasma (e.g., flare, quiet sun, etc.) from the observed elemental abundances and ionisation states.
These synthetic spectra are essential for comparing to the data observed by various instruments to calculate the response functions of the instruments and to compare to the properties of observed plasma to allow the calculation of physical parameters such as temperature.

Currently, no SunPy code uses the Python interface to the CHIANTI database [ChiantiPy](http://chiantipy.sourceforge.net/). This project would develop the routines to be included in SunPy to use ChiantiPy for various physical calculations desired. The first potential use of ChiantiPy in SunPy is in the `sunpy.instr.goes` module, where currently data tables calculated using CHIANTI are downloaded from the Solar Software (SSW) distribution, these data tables should be created using SunPy.

Other potential application of ChiantiPy in SunPy include:

1. Conversion of ChiantiPy spectra objects to SunPy Spectra objects.
1. Calculation of AIA temperature response functions from ChiantiPy
   contribution functions.

**Expected Outcomes**: This project would facilitate SunPy becoming independent from Solar SoftWare (SSW) in producing and maintaining files required by the sunpy.instr.goes module for determining the thermodynamic properties of the emitting plasma observed by GOES.  It would also allow SunPy users to calculate spectra and exclusively through Python without relying on SSW.


### Lightcurve Refactor

*Suggested Mentor(s):* [Stuart Mumford](http://github.com/Cadair), [Dan Ryan](https://github.com/DanRyanIrish), [Andrew Inglis](https://github.com/aringlis), [Jack Ireland](https://github.com/wafels)

*Difficulty:* Intermediate

*Astronomy knowledge needed:* None

*Programming skills:* Python

#### Description
The `Lightcurve` class is one of the three core datatypes in SunPy, along with Map and Spectra.
`Lightcurve` is designed to read in, process and store meta data related to solar physics time series data.
Currently, `Lightcurve` uses the pandas library as its underlying data structure, however, this is subject to change in the future.

Much like the `map` submodule, `lightcurve` needs to be able to read in various supported data formats (such as FITS, ascii and others in the future), store their meta data and give users Beginner and unified access to this metadata independently of the original source of the data.

As currently implemented (as of 0.5) the `lightcurve` module performs three core tasks:

1. Download the raw data
1. Read this data into a pandas dataframe
1. store the meta data obtained with the data.

As of the SunPy 0.6 release the first stage will be moved out of `lightcurve` and into the `net` subpackage as part of the [`UnifiedDownloader`](https://github.com/sunpy/sunpy/pull/1088) (name subject to change) Pull Request.
This leaves `lightcurve` in a similar position to `map` where the data acquisition is not part of the core data type and is managed separately.
Therefore, enabling the implementation of a factory class like `Map`
for the lightcurve module.

**Expected Outcomes**

Someone under taking this project will complete the following tasks:

1. Become familiar with the `UnifiedDownloader` code, if it has not been accepted into the SunPy codebase, complete the remaining tasks for this to be achieved.
1. Re-write any new lightcurve sources that were not included in the `UnifiedDownloader` code as sources for `UnifiedDownloader`.
1. Write a factory class for `lightcurve` similar to the `sunpy.map.Map` class. This class will be a generic constructor for `lightcurve` allowing the user to instantiate any one of the many subclasses of `GenericLightcurve` present in `sunpy.lightcurve.sources`. The API design for the factory class is here: https://github.com/sunpy/sunpy-SEP/pull/6
1. Design and develop a robust method of dealing with lightcurve meta data, which can handle joining different parts of timeseries from different files, each with their own meta data. (See [#1122](https://github.com/sunpy/sunpy/issues/1122))



## For ChiantiPy


## GUI to use LCT tools
*Suggested Mentor(s):* [Jose Iván Campos Rozo](https://github.com/Hypnus1803) (National Astronomical Observatory, National University of Colombia), Santiago Vargas Domínguez (National Astronomical Observatory, National University of Colombia), [David Pérez Suárez](https://github.com/dpshelio).

*Difficulty:* Intermediate

*Astronomy knowledge needed:* None

*Programming skills:* Python, basic knowledge of qt4, pyqt4, qt designer

### Description:
The Local Correlation Tracking (LCT, November & Simon, 1988) technique is a robust method used to study the dynamics of structures in a time series of images. By tracking pixel displacements, using a correlation window, LCT can determine proper motions and generate flow maps of horizontal velocities. This procedure is used to study the dynamics of plasma in the solar photosphere at different spatial scales, e.g the analysis of granular and supergranular convective cells, meridional flows, etc. A widget implemented in Python was developed. It generates a user-friendly graphical user interface (GUI) to control various parameters for the process of calculating flow maps of proper motions for a series of filtergrams (data cube). Our purpose is to implement this tool in Sunpy using its structure and to improve it with some more options, i.e. masks, statistics, histograms, contours and multi-plots. Although an initial version is already developed, our proposal is to focus on the efficient integration of the code in the  SunPy libraries. The code (without widget files yet) is https://github.com/Hypnus1803/flow_maps

*Expected Outcomes:* To integate efficiently the code in SunPy libraries. 


### Implement x support for y

*Suggested Mentor(s):* [Name Surname](http://github.com/my_username)

*Difficulty:* Beginner, Intermediate or Expert

*Astronomy knowledge needed:* none (or some background)

*Programming skills:* Python, C, Julia, Java, super powers

#### Description

The [_y_](http://docs.xproject.org/en/stable/y/index.html) class is
powerful but ...

### Implement m support for n

*Suggested Mentor(s):* [Nombre Apellido](http://github.com/mi_usuario)

*Difficulty:* Beginner, Intermediate or Expert

*Astronomy knowledge needed:* none (or some background)

*Programming skills:* Python, C, Julia, Java, super powers

#### Description

The [_n_](http://docs.xproject.org/en/stable/y/index.html) class is
super powerful but ...

