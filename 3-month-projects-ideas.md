The list of projects below will be changing as they are being taken by someone or made obsolete by the project.  Please, let us know if you are working on any of these 3-month projects so we can aknowledge your institution for the contribution.

## Project A
**Abstract**

**Requirements**

**Expected Outcomes**

**Idea from:**

**Possible mentors/help by**

***

## IRIS Integration
**Abstract**: The [IRIS](http://iris.lmsal.com) observes the chromosphere and transition region
of the Sun with high spatial and time resolution. The primary goal of the Interface Region Imaging Spectrograph (IRIS) explorer is to understand how the solar atmosphere is energized. The IRIS mission produces data through
a slit-jaw imager which can take images of the Sun at various wavelengths as well as a line spectrograph which
rasters over an image to build up an image. This project aims to integrate IRIS data into SunPy. This includes the following tasks.

1. Integration of IRIS data search and querying
2. Adding the ability to read IRIS data files into their proper data objects
3. Developing a data browser module in the existing SUnPy GUI for fast inspection of IRIS data 

**Requirements**: Python and basic knowledge of GUI design. 

**Expected Outcomes**: IRIS Mapcube class, IRIS Spectrum class, GUI data browser module

**Idea from:**: Steven Christe (NASA GSFC, SunPy)

* **Mentor**: Steven Christe (NASA GSFC, SunPy), Joel Allred (NASA GSFC)


## Lightcurve Refactor

**Description**:
The `Lightcurve` class is one of the three core datatypes in SunPy, along with Map and Spectra.
`Lightcurve` is designed to read in, process and store meta data related to solar physics time series data.
Currently, `Lightcurve` uses the pandas library as its underlying data structure, however, this is subject to change in the future.

Much like the `map` submodule, `lightcurve` needs to be able to read in various supported data formats (such as FITS, ascii and others in the future), store their meta data and give users easy and unified access to this metadata independently of the original source of the data.

As currently implemented (as of 0.5) the `lightcurve` module performs three core tasks:

1. Download the raw data
1. Read this data into a pandas dataframe
1. store the meta data obtained with the data.

As of the SunPy 0.6 release the first stage will be moved out of `lightcurve` and into the `net` subpackage as part of the [`UnifiedDownloader`](https://github.com/sunpy/sunpy/pull/1088) (name subject to change) Pull Request.
This leaves `lightcurve` in a similar position to `map` where the data acquisition is not part of the core data type and is managed separately.

This project will complete the following tasks:

1. Become familiar with the `UnifiedDownloader` code, if it has not been accepted into the SunPy codebase, complete the remaining tasks for this to be achieved.
1. Re-write any new lightcurve sources that were not included in the `UnifiedDownloader` code as sources for `UnifiedDownloader`.
1. Write a factory class for `lightcurve` similar to the `sunpy.map.Map` class. This class will be a generic constructor for `lightcurve` allowing the user to instantiate any one of the many subclasses of `GenericLightcurve` present in `sunpy.lightcurve.sources`. The API design for the factory class is here: https://github.com/sunpy/sunpy-SEP/pull/6
1. Design and develop a robust method of dealing with lightcurve meta data, which can handle joining different parts of timeseries from different files, each with their own meta data. (See [#1122](https://github.com/sunpy/sunpy/issues/1122))

**Requirements**

Familiarity with Python. 

**Expected Outcomes**

1. New `Lightcurve` factory class.
1. Correct handling of meta data in join and split operations.

**Possible mentors**

Stuart Mumford, Dan Ryan, Andrew Inglis, Jack Ireland


## Improvements to the SunPy Database

The `database` module provides functionality to users to manage collections of files on disk in a way not reliant upon folder structure and file name.
The database allows users to find files on disk by either physical parameters, such as wavelength and time or properties of the instrument such as name and spacecraft. It also allows more complex queries by enabling searches of the raw meta data associated with the files.

The improvements to the database functionality that would be implemented by this project include:

1. Integration of the new `UnifiedDownloader` code into the database search, to replace the direct VSO integration current present. (The [VSO](http://vso1.nascom.nasa.gov/) is a repository of solar physics data, SunPy's VSO API has been wrapped by `UnifiedDownloader`.)
1. Support for relative paths in the database module [#783](https://github.com/sunpy/sunpy/issues/783) to allow a centralised database with multiple users, all referencing a central file store mounted with different absolute paths on each client.
1. Supporting all data supported by the `sunpy.lightcurve` module in the database. The major hurdle here is the lack of standardisation in the file used by this data.

There are various other maintenance tasks which need undertaking (https://github.com/sunpy/sunpy/labels/Database) which would be a good way for someone interested in this project to familiarise themselves with the codebase.

**Requirements**

Familiarity with Python, knowledge of database design would be advantageous.

**Possible mentors**

Stuart Mumford, Steven Christe.

## Support for analysis of Solar Energetic Particles
**Description**

SunPy is able to read lightcurve from different sources (GOES x-ray, Lyra, Norh,...), however these are not all.
SoHO/ERNE (Energetic and Relativistic Nuclei and Electron experiment on board SoHO) measures
one of the important effects in Space Weather, [Solar Energetic Particles](https://en.wikipedia.org/wiki/Solar_energetic_particles) (SEP).
The data of such instrument (as for GOES particle measurements) comes as plaintext csv files with header information.
This project should be able to read these in as a lightcurve object and allow to perform the basic operations used
when such data is analysed: eg. energy ranges binning, visualisation, ...

**Requirements** None.

**Possible mentors** David PS (or other SunPy member), Timo Laitinen and/or Silvia Dalla (University of Central Lancashire)

## Integrating ChiantiPy and SunPy

**Description**:

The [CHIANTI](http://www.chiantidatabase.org/) atomic physics database is a valuable resource for solar physics. The CHIANTI database holds a large amount of information on the physical properties of different elements in different ionisation states and enabled the calculation of various parameters from this information. Using CHIANTI it is possible to calculate the spectra of various types of solar plasma (e.g., flare, quiet sun, etc.) from the observed elemental abundances and ionisation states.
These synthetic spectra are essential for comparing to the data observed by various instruments to calculate the response functions of the instruments and to compare to the properties of observed plasma to allow the calculation of physical parameters such as temperature.

Currently, no SunPy code uses the Python interface to the CHIANTI database [ChiantiPy](http://chiantipy.sourceforge.net/). This project would develop the routines to be included in SunPy to use ChiantiPy for various physical calculations desired. The first potential use of ChiantiPy in SunPy is in the `sunpy.instr.goes` module, where currently data tables calculated using CHIANTI are downloaded from the Solar Software (SSW) distribution, these data tables should be created using SunPy.

Other potential application of ChiantiPy in SunPy include:

1. Conversion of ChiantiPy spectra objects to SunPy Spectra objects.

**Requirements**:

**Expected Outcomes**: This project would facilitate SunPy becoming independent from Solar SoftWare (SSW) in producing and maintaining files required by the sunpy.instr.goes module for determining the thermodynamic properties of the emitting plasma observed by GOES.  It would also allow SunPy users to calculate spectra and exclusively through Python without relying on SSW.

**Possible mentors** Daniel Ryan

## ChiantiPy GUI Spectral Explorer

### Description

The goal of this project is to provide a graphical user interface to enable a user to explore observed spectra and compare it with theoretical spectra.  The basis for the theoretical spectra is the CHIANTI atomic database for astrophysical spectroscopy that was first released in 1997.  Programmatic access to the database, which is freely available, is provided by the ChiantiPy package -- a pure python package.  It is highly object oriented with each ion, such as Fe XVII, being the basic object.  Higher level objects are often assembled from a collection of ions, such as when calculating a spectrum.  ChiantiPy uses the CHIANTI database to calculate line and continuum intensities as a function of temperature, electron density. This can be done for a set of elemental abundances in CHIANTI or for a user provided set of elemental abundances.  At present, if a user wants to compare CHIANTI theoretical spectra it must be done on a case-by-case basis.  A GUI explorer, written in Python and preferably PyQt or Wx based, will provide an integrated tool to import observed spectra and plot them alongside theoretical spectra.  It will further allow the user to understand what spectra lines contribute to various spectral line profile, how the predicted spectra vary as a function of temperature and density.

It will be necessary to develop techniques to import observed spectra from a variety sources.  Typical sources are in FITS files, HDF5 files, or csv files.  It will also be important to allow users import their data through modules of their own.

* Requirements:  Python, a basic understand of astrophysical spectroscopy

* Mentors:  Ken Dere

## IRIS Integration
**Abstract**: The [IRIS](http://iris.lmsal.com) observes the chromosphere and transition region
of the Sun with high spatial and time resolution. The primary goal of the Interface Region Imaging Spectrograph (IRIS) explorer is to understand how the solar atmosphere is energized. The IRIS mission produces data through
a slit-jaw imager which can take images of the Sun at various wavelengths as well as a line spectrograph which
rasters over an image to build up an image. This project aims to integrate IRIS data into SunPy. This includes the following tasks.

1. Integration of IRIS data search and querying
2. Adding the ability to read IRIS data files into their proper data objects
3. Developing a data browser module in the existing SUnPy GUI for fast inspection of IRIS data 

**Requirements**: Python and basic knowledge of GUI design. 

**Expected Outcomes**: IRIS Mapcube class, IRIS Spectrum class, GUI data browser module

**Idea from:**: Steven Christe (NASA GSFC, SunPy)

* **Mentor**: Steven Christe (NASA GSFC, SunPy), Joel Allred (NASA GSFC)

## Integration of the HESPE Data Archive
* **Description**: The [HESPE Data Archive](http://hespe.eu/browser) gives access
to pre-processed science products from the RHESSI satellite. 
The data are organized by flare event and are available both as printable quicklook 
files (PNGs) that can be directly displayed in SunPy, and in their original data 
structures and formats (FITS) that may need some additional processing. 
Access is provided through a web interface (REST) that can be used from within SunPy. 
Each flare event can have hundreds of data products connected to it, which requires 
special attention when displaying the search results. 
The integration task includes: 
(1) basic integration of the HESPE search (with feedback to the HESPE project team,
if necessary); 
(2) basic integration of the RHESSI data products using existing SunPy structures; 
(3) optimizing the handling and presentation of the search, the search results 
(e.g. allowing to filter), and the data products themselves. 
The outcome should be two clients, command-line and GUI.

* **Requirements**: Knowledge of GUI design; Basic knowledge of working with web 
services (REST) and JSON is a plus.

* **Mentor**: Laszlo I. Etesi (HESPE data archive developer), Steven Christe (SunPy)

## HELIO - capabilities improvement

### Description:

SunPy has already the capability to access to the Heliophysics Events Catalogue provided by the HELiophysics Integrated Observatory.  This catalogue provides access to different lists of events observed anywhere in the heliosphere.  However, HELIO offers a lot more web services of interest for the solar community.  Some of the services can provide information of when and where a planet or instrument where located, properties on features detected on the sun, or properties of some heliospheric observations; moreover it also allow the discovery of new data by a propagation model which simulates three different scenarios - Coronal Mass Ejections, High speed solar wind and Solar Energetic Particles events.

This project would consist in the creation of an interface to access to HELIO services in a similar way that other services like HEK or VSO are accessible at the moment. HELIO uses VOTables as the standard to transfer the data, astropy provides support for reading such file format, therefore some understanding of astropy may be needed.   

* Requirements: All the services from HELIO are through webservices (SOAP, REST), thus some understanding on that would be beneficial. VOTable parser provided from astropy will be used, so familiarization with such interface will be helpful.

* Difficulty: Medium

* Mentors: David Perez-Suarez, (Marco Soldati, Kevin Benson - HELIO)

## Feature Tracking / Detection

Framework and algorithms for detecting features in the solar atmosphere / magnetic fields on the solar surface.

Detection algorithms:

* Thresholding
* Clumping
* Downhill
* Curve

Tracking and property extraction using labelling and similar. 

## HEK searching and overlays in Ginga

Query the HEK both manually and automatically from ginga and overlay the results on the images

## Downloader integration with Database and Ginga

Replace the VSO integration in the database module with the Unified Downloader and then integrate full querying in a Ginga plugin.

## Refactor and Factory Spectrogram

Build a Spectra() factory and refactor the whole `sunpy.spectra` module to pull it inline with Map and LightCurve.

## Interface to get heliospheric data from CDAweb

CDAWEB provides as [SOAP interface](http://cdaweb.gsfc.nasa.gov/WebServices/SOAP/) which could be used
within SunPy to download insitu data.

