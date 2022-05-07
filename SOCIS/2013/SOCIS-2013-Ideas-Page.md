The [SOCIS 2013 organization application page](https://github.com/sunpy/sunpy/wiki/SOCIS-2013)

Students: You need to apply in the [SOCIS website](http://sophia.estec.esa.int/socis2013/?q=node/11) and also don't forget to add your application to this [[wiki|Socis-2013-students-applications]].  Try to follow the [[application guidelines|GSoC-student-application-guidelines]] we set for the GSoC, you will get more chances to be selected if you follow them.

The ideas shown below are projects that we believe can be completed during the SOCIS programming period (1 Aug - 31 Oct 2012).  The projects are sorted in order of interest to the SunPy community.  Please join the #sunpy IRC channel ([web client](http://webchat.freenode.net/)) to talk with the SunPy community and do not hesitate to introduce yourself in any of our mailing list ([users](https://groups.google.com/forum/?fromgroups#!forum/sunpy), [developer](https://groups.google.com/forum/?fromgroups#!forum/sunpy-dev)).

## Spectrum Object

* **Description**: The SunPy project is built upon a number of objects which hold data such as the map object (for two-dimensional image data) and the lightcurve object (for time-ordered scalar data).  The third major object we require is the spectrum object, which is for data ordered by energy (or its equivalent, such as wavelength). The goal of this project is to design and implement the spectrum object for SunPy. This object will need to be able to display its data in a basic plot form. In addition, different sub-classes of the main spectrum object will also need to handle the various kinds of spectral data.  It will also need to be able to convert from data (e.g. counts) to physical quantities (e.g. photons) through knowledge of the detector response (for example, the detector response is typically described using a matrix). A number of physical models are also necessary to interpret spectra. Coding up efficient forms of these models can also be part of this project if time allows.
* **Requirements**: Basic knowledge of spectral data analysis is a plus.
* **Mentor**: David Pérez-Suárez and Peter Young

## Improvements in Image Processing for Map

* Description: Solar data requires a lot of image processing techniques, to reduce the data to a point where meaningful physical analysis can be performed. SunPy provides some basic data types, called maps, for different types of image data. Map is a data type designed to hold a 2D image, map has routines such as rotate, resample and superpixel to modify the image for analysis.
The map object is in the process of being refactored to be based on MapBase for ND maps and it's 2D derivative GenericMap. There are many improvements to the set of Map classes that could be implemented, Map's refactor has been undertaken with the goal of integrating Map with AstroPy NDdata.
The coordinate systems for Maps are based upon the FITS standard World Coordinate System (WCS), for which there are many default transformations and basic handling in AstroPy, as part of the refactoring of the Map classes it is planned that Map should be integrated with AstroPy to inherit the improved WCS and unit handling implemented in that package.
There are also some standard physical transformations that could be implemented such as a routine to compensate for limb darkening, or differential rotation.
It is envisaged that a student undertaking a project designed to improve SunPy's Map objects would lead the integration of SunPy with AstroPy and in the process integrate the WCS transformations in AstroPy with the current routines in SunPy. This would enable easy development of routines such as differential rotation compensation.

* Requirements: Some knowledge of or willingness to learn basic IDL maybe useful.

* Mentor: Stuart Mumford and Russell Hewett

### Movies and Animation

* **Description**: The Sun is a dynamic object, and so the capability to visualize its dynamism is very important.  We require the ability to animate a map cube object, and to animate composites of maps.  The matplotlib package has an animation module that looks like it can provide much of the movie playing capability we need.  This functionality is highly desirable in exploratory data analysis, and would be a major step forward in Sunpy functionality.
* **Requirements**: Basic knowledge of GUI design a plus.
* **Mentor**: Jack Ireland & Steven Christe

## Improvements to 3D Map classes

* Description: SunPy also implements a mapcube object that is designed to hold series of spatially aliged images, *e.g.* time-series. This object requires development to allow many desired features to be implemented, such as being able to sort the Maps in the cube by time or frequency or other units. As well as this it is desired that a image registration routine should be implemented to align the images in the cube to a very high degree of accuracy.
MapCube is currently implemented as a list of Map objects, further work is required to allow the conversion between a list of Maps and a 3D Map object, where all the data is contained in one 3D np.ndarray. This would allow for fast indexing of the data cube and better processing. This conversion however requires a high degree of homogeneity between the arrays so a single array can be created.
As well as MapCube SunPy also has a CompositeMap type which is designed to hold temporally aligned data. This data type requires a lot of work and improvement. Also improvements to MapCube should be made so it is possible to store a MapCube of ComposisteMaps

* Requirements: Knowledge of image processing and registration would be a plus.

* Mentors: Stuart Mumford and Russell Hewett

## Region of Interest object

* Description: a co-ordinate system aware object that describes a region in space, time and possibly energy.  Use cases: this could be passed to the HEK/HELIO to find all the features/events within that region of space/time.  It could be passed to the SDO cutout service to acquire SDO data.  Note that transforming from one co-ordinate system to another could result in non-rectangular regions of interest.  The TimeRange object could be used to store the time extent of the "region".  The region of interest object should also be derivable from the the main object classes - Map, LightCurve, MapCube, Spectrum.

* Mentors: Jack Ireland

## SunPy GUI

* **Description**: The goal of this project is to develop a standardized interface to plots such as that of lightcurves, spectrograms, or images. Such a tool would provide basic functionality to interact with the plots contained therein such as overlaying multiple images, comparing light curves to each other. Interfaces to common tasks could include searching the vso for data, background subtraction, creating profile cuts in images, fitting curves such as gaussians. A good example of a GUI interface for interacting with radio data is [ragview](http://hesperia.gsfc.nasa.gov/ssw/radio/ethz/idl/ragview/ragview.pro). This GUI interface should be written in using Tkinter. Additionally, this project will also include adding sunpy functionality through modifying the standard matplotlib window. For example, a button to change the default coordinate system used to display a map. If a mapcube is displayed, buttons to show the next image or the previous image.

* **Requirements**: Basic knowledge of GUI interface design.
* **Mentor**: Steven Christe

## PyOpenJPEG

* Description: JPEG 2000 is an advanced image standard that is useful in the storage and transfer of image data and associated image data.  OpenJPEG is an open-source implementation of the JPEG 2000 standard.  PyOpenJPEG is a partially complete Python wrapper around the OpenJPEG Library that allows users to read a JPEG2000 file into Python.  This project seeks to expose the full functionality of the OpenJPEG Library via Python, and so allow SunPy (and Python) users to read, manipulate and write JPEG 2000 files.

* One significant application of PyOpenJPEG is in the visualization of data from the Sun.  The JPEG 2000 image format forms the basis of the [Helioviewer Project](http://wiki.helioviewer.org/wiki/Main_Page), an effort to [visualize](http://www.helioviewer.org) [solar](http://www.jhelioviewer.org) and heliospheric data from multiple [sources](http://helioviewer.org/?date=2013-03-28T22:36:36.000Z&imageScale=38.727054&centerX=38.727054&centerY=0&imageLayers=%5BPROBA2,SWAP,SWAP,174,1,100%5D,%5BSDO,AIA,AIA,304,1,50%5D,%5BSOHO,LASCO,C2,white-light,1,100%5D,%5BSOHO,LASCO,C3,white-light,1,60%5D). Users of Helioviewer Project clients (see images below) can make and share images and [movies](http://www.youtube.com/watch?feature=player_embedded&v=4xESw6G8JdM) of solar features and events.  PyOpenJPEG would allow users of Python-based software to create images of solar data and other science products for use with Helioviewer Project clients, increasing the number and type of images available.

* Requirements: Python, C; some familiarity with Cython, JPEG 2000 standard and the OpenJPEG tools is a plus.

* References: <https://github.com/khughitt/pyopenjpeg>, <https://code.google.com/p/openjpeg/>

* Mentors: Jack Ireland (ADNET Systems, Inc./ NASA GSFC), Keith Hughitt (U. Maryland)

<BR>
_Screen capture of the http://www.helioviewer.org web application._
![Screen capture of the www.helioviewer.org web application.](http://blog.helioviewer.org/wp-content/uploads/2013/04/hv-Screenshot-from-2013-04-03-101858.png)

<BR>
_Screen capture of the [JHelioviewer](http://www.jhelioviewer.org) client application._
![Screen capture of the JHelioviewer client application.](http://blog.helioviewer.org/wp-content/uploads/2011/12/JHelioviewer_Screenshot-at-2011-12-15-133426.png)

##

* **Description**: A ...
* **Requirements**: Basic knowledge of ...
* **Mentor**: A and B

### List of Mentors

* Stuart Mumford
* Russell Hewett
* Keith Hughitt
* Jack Ireland
* David Pérez-Suárez
* Peter Young
* Steven Christe
