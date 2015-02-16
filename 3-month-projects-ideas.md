The list of projects below will be changing as they are being taken by someone or made obsolete by the project.  Please, let us know if you are working on any of these 3-month projects so we can aknowledge your institution for the contribution.

## Project A
**Abstract**

**Requirements**

**Expected Outcomes**

**Idea from:**

**Possible mentors/help by**


***

## Integrating ChiantiPy and SunPy
* **Description**: The CHIANTI atomic physics database is a valuable resource for solar physics.  It allows the spectra of various types of solar plasma (e.g., flare, quiet sun, etc.) to be calculated from their abundances, ionisation states, etc.  This is essential to understand instrument response functions, spectral observations, and so on.
Currently, ChiantiPy and SunPy are incompatible due to issues such as licenses.  This project would involve development an interface between these two packages so that CHIANTI can be used by solar physicists through SunPy.

* **Requirements**:

* **Expected Outcomes**: This project would facilitate SunPy becoming independent from Solar SoftWare (SSW) in producing and maintaining files required by the sunpy.instr.goes module for determining the thermodynamic properties of the emitting plasma observed by GOES.  It would also allow SunPy users to calculate spectra and exclusively through python without relying on SSW.

**Idea from:** Daniel Ryan

**Possible mentors/help by**

***

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

## Now module
* **Description**: [SolarMonitor.org](http://solarmonitor.org) provides a quick view
service to know how the sun looks now. 
Additionally it provides some other information useful for space weather as the 
current solar activity and flare forecasting.
The data it uses it comes from multitude of real-time data archive that differs from
the archived data.
By creating a `now` module in SunPy we will provide to the SunPy user to download, 
visualise and analise near real-time data.  
This module then could be used by SolarMonitor directly which it will help to advertise
worldwide SunPy capabilities.

`now` module will have to handle properly different datatypes (map, lightcurves) and
images.

* **Requirements**: N/A

* **Mentor**: David PS (SunPy), Paul Higgins?, Eoin Carley? (SolarMonitor)

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

## Support for analysis of Solar Energetic Particles
* **Description** SunPy is able to read lightcurve from different sources (GOES x-ray, Lyra, Norh,...), however these are not all.
SoHO/ERNE (Energetic and Relativistic Nuclei and Electron experiment on board SoHO) measures
one of the important effects in Space Weather, [Solar Energetic Particles](https://en.wikipedia.org/wiki/Solar_energetic_particles) (SEP).
The data of such instrument (as for GOES particle measurements) comes as plaintext csv files with header information.
This project should be able to read these in as a lightcurve object and allow to perform the basic operations used
when such data is analysed: eg. energy ranges binning, visualisation, ...

* **Requirements** N/A, but familiarise with the lightcurves object will be needed.

* **Possible mentors/help by** David PS (or other SunPy member), Timo Laitinen and/or Silvia Dalla (University of Central Lancashire)
