# If you are looking for final projects please [see here](http://openastronomy.org/gsoc/).

These projects are work-in-progress ideas what have not yet made the jump to final projects.
The list of projects below will be changing as they are being taken by someone or made obsolete by the project as it moves on.

## Project Template
**Abstract**

**Requirements**

**Expected Outcomes**

**Idea from:**

**Possible mentors/help by**

***

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

## Refactor and Factory Spectrogram
Build a Spectra() factory and refactor the whole `sunpy.spectra` module to pull it inline with Map and LightCurve.

## Interface to get heliospheric data from CDAweb
CDAWEB provides as [SOAP interface](http://cdaweb.gsfc.nasa.gov/WebServices/SOAP/) which could be used
within SunPy to download insitu data.

## GUI to use LCT tools
### Abstract:
Abstract
The Local Correlation Tracking (LCT, November & Simon, 1988) technique is a robust method used to study the dynamics of structures in a time series of images. By tracking pixel displacements, using a correlation window, LCT can determine proper motions and generate flow maps of horizontal velocities. This procedure is used to study the dynamics of plasma in the solar photosphere at different spatial scales, e.g the analysis of granular and supergranular convective cells, meridional flows, etc.

### Description:
A widget implemented in Python was developed. It generates a user-friendly graphical user interface (GUI) to control various parameters for the process of calculating flow maps of proper motions for a series of filtergrams (data cube). Our purpose is to implement this tool in Sunpy and to improve it with some more options, i.e. masks, statistics, histograms, contours and multi-plots. Although an initial version is already developed, our proposal is to focus on the efficient integration of the code in the  SunPy libraries. The code (without widget files yet) is https://github.com/Hypnus1803/flow_maps

### Requerimets:
Python and basic knowledge of GUI designe (qt4,pyqt4)

### Expected Outcomes:
* To integate efficiently the code in SunPy libraries.

### Idea from :
Jose Iván Campos Rozo (National Astronomical Observatory, National University of Colombia)
### Mentor:s
* Jose Iván Campos Rozo (National Astronomical Observatory, National University of Colombia)
* Santiago Vargas Domínguez(National Astronomical Observatory, National University of Colombia)
* David Pérez Suárez.
