The [SOCIS 2013 organization application page](https://github.com/sunpy/sunpy/wiki/SOCIS-2013)

Students: You need to apply in the [SOCIS website](http://sophia.estec.esa.int/socis2013/?q=node/11) and also don't forget to add your application to this [[wiki|Socis-2013-students-applications]].  Try to follow the [[application guidelines|GSoC-student-application-guidelines]] we set for the GSoC, you will get more chances to be selected if you follow them.

The ideas shown below are projects that we believe can be completed during the SOCIS programming period (1 Aug - 31 Oct 2012).  The projects are sorted in order of interest to the SunPy community.  Please join the #sunpy IRC channel ([web client](http://webchat.freenode.net/)) to talk with the SunPy community and do not hesitate to introduce yourself in any of our mailing list ([users](https://groups.google.com/forum/?fromgroups#!forum/sunpy), [developer](https://groups.google.com/forum/?fromgroups#!forum/sunpy-dev)).

## Spectrum Object
* **Description**: The SunPy project is built upon a number of objects which hold data such as the map object (for two-dimensional image data) and the lightcurve object (for time-ordered scalar data).  The third major object we require is the spectrum object, which is for data ordered by energy (or its equivalent, such as wavelength). The goal of this project is to design and implement the spectrum object for SunPy. This object will need to be able to display its data in a basic plot form. In addition, different sub-classes of the main spectrum object will also need to handle the various kinds of spectral data.  It will also need to be able to convert from data (e.g. counts) to physical quantities (e.g. photons) through knowledge of the detector response (for example, the detector response is typically described using a matrix). A number of physical models are also necessary to interpret spectra. Coding up efficient forms of these models can also be part of this project if time allows.
* **Requirements**: Basic knowledge of spectral data analysis a plus.
* **Mentor**: David Pérez-Suárez and ?

## Improvements in Image Processing for Map.

* Description: Solar data requires a lot of image processing techniques, to reduce the data to a point where meaningful physical analysis can be performed. SunPy provides some basic data types, called maps, for different types of image data. Map is a data type designed to hold a 2D image, map has routines such as rotate, resample and superpixel to modify the image for analysis. 
The map object is in the process of being refacotred to be based on MapBase for ND maps and it's 2D derivative GenericMap. There are many improvements to the set of Map classes that could be implmemnted, Map's refactor has been undertaken with the goal of integrating Map with AstroPy NDdata.
The coordinate systems for Maps are based upon the FITS standard World Coordinate System (WCS), for which there are many default transformations and basic handaling in AstroPy, as part of the refactoring of the Map classes it is planned that Map should be integrated with AstroPy to inherit the improved WCS and unit handaling implemented in that package.
There are also some standard physical transformations that could be implemented such as a routine to compensate for limb darkening, or differential rotation.
It is invisaged that a student undertaking a project designed to improve SunPy's Map objects would lead the integration of SunPy with AstroPy and in the process integrate the WCS transformations in AstroPy with the current routines in SunPy. This would enable easy development of routines such as differential rotation compensation. 

* Requirements: Some knowledge of or willingness to learn basic IDL maybe useful.

* Mentor: Stuart Mumford and Russell Hewett

## Region of Interest object
* Description: a co-ordinate system aware object that describes a region in space and time.  Use cases: this could be passed to the HEK/HELIO to find all the features/events within that region of space/time.  It could be passed to the SDO cutout service to acquire SDO data.  Note that transforming from one co-ordinate system to another could result in non-rectangular regions of interest.  The TimeRange object could be used to store the time extent of the "region".

* Mentors: Jack Ireland and ?

## Improvements to Mapcube and Image Registration.

* Description: SunPy also implements a mapcube object that is designed to hold series of images, currently primarily time-series. This object requires development to allow many desired features to be implemented, such as being able to sort the Maps in the cube by time or frequency or other units. As well as this it is desired that a image registration routine should be implemented to align the images in the cube to a very high degree of accuracy.

* Requirements: Knowledge of image processing a registration would be a plus.

* Mentors: Stuart Mumford and Russell Hewett

## AAA
* **Description**: A ...
* **Requirements**: Basic knowledge of ...
* **Mentor**: A and B


### List of Mentors

* Stuart Mumford
* Russell Hewett
* Jack Ireland
* David Pérez-Suárez