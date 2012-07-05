The [SOCIS 2012 application page](https://github.com/sunpy/sunpy/wiki/SOCIS-2012)

The ideas shown below are based in little projects that we hope can be completed during the SOCIS programming period (1 Aug - 31 Oct 2012).  The projects are sorted in order of interest within the SunPy community.

## Spectrum Object
* **Description**: The SunPy project is built upon a number of object which hold data such as the map object (for image data), the lightcurve object (for time series data), and the spectrum object (for spectral data). The goal of this project is to design and implement the spectrum object for SunPy. This object will need to be able to display its data in a basic plot form. It will also need to be able to convert from data (e.g. counts) to physical quantities (e.g. photons) through knowledge of the detector response (usually describes with a matrix). A number of physical models are also necessary to interpret spectra. Coding up efficient forms of these models can also be part of this project if time allows.
* **Requirements**: 
* **Mentor**: Richard Schwartz

## Extending the capabilities of Map object
### Map Cube ordering
* **Description**: A map cube is an ordered set of two dimensional maps.  The ordering can be by image observation time, Fourier frequency, or energy.  The map cube object must be general enough to handle ordering by numerical quantities other than time.  The map cube object can also provide the basis for animation.  For example, in a set of time-ordered maps, running through them in time-order will animate a movie. Memory mapping...
* **Requirements**: 
* **Mentor**: Steven Christe

### Movies and Animation
* **Description**: The Sun is a dynamic object, and so the capability to visualize its dynamism is very important.  We require the ability to animate a map cube object, and to animate composites of maps.  The matplotlib package has an animation module that looks like it can provide much of the movie playing capability we need.
* **Requirements**: 
* **Mentor**: Jack Ireland

##  SDO Cutout Service 
* **Description**: As part of the Heliophysics Coverage Registry (HER) Lockheed Martin Solar and Astrophysics Laboratory provides a [cutout service](http://www.lmsal.com/get_aia_data/) to access SDO/AIA data. This service reduces bandwidth costs by allowing users to request subsamples of full Sun images. This service also connects to the HEK so that users can find cutouts that others have made reducing the number of cutouts which need to be created. This service provides an API. The goal of this project is to create an interface to this service in Python as well as a GUI tool to choose the area of the cutout.
* **Requirements**: Knowledge of web services preferred.
* **Mentor**: Joe Hourclé (with possible addition of subject matter expert Ankur Somani)

##  Plotman GUI 
* **Description**: The goal of this project is to develop a standardized interface to plots such as that of lightcurves, spectrograms, or images. Such a tool would provide basic functionality to interact with the plots contained therein such as overlaying multiple images or comparing light curves to each other. This GUI interface could be written in both Tkinter and PyQT.
* **Requirements**: Basic knowledge of GUI interface design.
* **Mentor**: Steven Christe

## SunPy and High School
* **Description**: Develop a one day course that introduces students to solar data analysis using SunPy.  Will involve working on multiple parts of SunPy (getting data, visualize it, extract profiles, gaussian fitting,...).  Knowledge of science required, as well as experience with Python programming. This project is meant for Python beginners and should be a quick project which will introduce the student to SunPy development. 
* **Requirements**: 
* **Mentor**: Steven Christe

## Porting of Critical software from SolarSoft
* **Description**: SolarSoft is a software suite developed for IDL which already contains critical routines which are necessary for any basic analysis of solar data. Many of these routines must be ported to Python. This project aims to develop the basic framework of SunPy (coordinate transformations and projections, ephemeris calculations, etc.) which is currently based on IDL.
* **Order list**:
8. Differential rotation of solar images. More than one possible input functions. [drot_map.pro](http://hesperia.gsfc.nasa.gov/ssw/gen/idl/maps/drot_map.pro)
1. ...
* **Requirements**: Knowledge of IDL is necessary.
* **Mentor**: Jack Ireland

## Prep-server
* **Description**: Prep-server is not part of sunpy, but its development will help to people to start to use it, as it will provide a service to reduce data remotely.
* **Requirements**: Java
* **Mentor**: Laszlo??

## Flux-conserving Image resampling algorithms
* **Description**: Digital image data are now commonly used throughout the field of solar physics. Many steps of image data analysis, including image co-alignment, perspective reprojection of the solar surface, and compensation for solar rotation, require re-sampling original telescope image data under a distorting coordinate transformation. The most common image re-sampling methods introduce significant, unnecessary flaws into the data. More correct techniques have been known in the computer graphics community for some time but remain little known within the solar community and hence deserve further presentation. Furthermore, image distortion under specialized coordinate transformations is a powerful analysis technique with applications well beyond image resizing and perspective compensation. The goal of this project is to implement fast, efficient, and flux-conserving coordinate transformation algorithms in SunPy. See [this paper](http://adsabs.harvard.edu/abs/2004SoPh..219....3D) for reference. An implementation in perl already [exists](http://pdl.perl.org/PDLdocs/Transform.html).
* **Requirements**: 
* **Mentor**: Craig DeForest


## JPEG 2000 in Python
* **Description**: [JPEG 2000](http://en.wikipedia.org/wiki/JPEG_2000) is an image compression standard which has been developed to supersede the JPEG standard. It is currently being used by the [http://wiki.helioviewer.org/wiki/Main_Page Helioviewer project] to provide high-fidelity images of solar data for purposes of browsing data quickly and with limited bandwidth. The first goal of this project is to write a wrapper around the [http://www.openjpeg.org/ OpenJPEG C library] in order to be able to open JPEG 2000 files from Python. Next, network code must be developed to hook into the [http://helioviewer.org/api Helioviewer API] to request and download data from their archives.
* **Requirements**: Knowledge of C is necessary.
* **Mentor**: Keith Hughitt

##  SDO JSOC Connector 
* **Description**: The Solar Data Observatory's [Joint Science Operations Center](http://jsoc.stanford.edu/) is the authoritative source for data from the Atmospheric Imaging Assembly (AIA) and Helioseismic and Magnetic Imager (HMI).  Although most AIA and HMI data is available through the VSO, the JSOC's Data Records Management System (DRMS) contains additional lower-level data, and can support more complex queries that are used in helioseismology.  A [RESTful webservice](http://jsoc.stanford.edu/jsocwiki/AjaxJsocConnect) is available to query the authoritative system, and a [C API](http://jsoc.stanford.edu/jsocwiki/JsocDataAccess) exists to talk to [a local DRMS instance](http://vso.stanford.edu/netdrms/), such as the [six mirrors in Europe](http://vso.stanford.edu/netdrms/site_codes.html).
* **Requirements**: Knowledge of C required.  Knowledge of web services (REST) preferred.
* **Mentor**: Joe Hourclé; (with possible addition of subject matter experts Art Amezcua and/or Igor Suárez Solá)<br/>


##  PyHelioviewer
* **Description**: [JHelioviewer](http://jhelioviewer.org/) is client software for the [Helioviewer Project](http://www.helioviewer.org/wiki), solar image visualization and data access project. JHelioviewer is a Java-based client that provides data browsing capabilities, image overlaying, and can quickly make movie of these images as a function of time. This project consists of porting the JHelioviewer client to Python and extending its capabilities.
* **Requirements**: 
* **Mentors**: 


### List of Mentors

* Steven Christe (NASA GSFC, USA)
* Keith Hughitt (NASA GSFC, USA)
* André Csillaghy (FHNW, CH)
* Laszlo Etesi (FHNW, CH)
* Jack Ireland (NASA GSFC, USA)
* Alex Young (NASA GSFC, USA)
* Joe Hourclé (NASA GSFC, USA)
* David Pérez-Suárez (TCD, Ireland)
* Richard Schwartz (NASA GSFC, USA)