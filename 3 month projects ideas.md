The list of projects below will be changing as they are being taken by someone or made obsolete by the project.  Please, let us know if you are working on any of these 3-month projects so we can aknowledge your institution for the contribution.

## Project A
**Abstract**

**Requirements**

**Expected Outcomes**

**Idea from:**

**Possible mentors/help by**



***

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