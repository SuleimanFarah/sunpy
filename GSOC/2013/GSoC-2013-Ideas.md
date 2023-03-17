## Improvements in Image Processing for Map

* Description: Solar data requires a lot of image processing techniques, to reduce the data to a point where meaningful physical analysis can be performed. SunPy provides some basic data types, called maps, for different types of image data. Map is a data type designed to hold a 2D image, map has routines such as rotate, resample and superpixel to modify the image for analysis. There are some more specific solar analysis routines that should be implemented in Map, such as a function that de-rotates the image, in solar coordinates, to compensate for the rotation of the Sun, and a routine that compensates for the observed dimming on the edge of the Sun.

* Requirements: Some knowledge of or willingness to learn basic IDL maybe useful.

* Mentor: Stuart Mumford and Russell Hewett

## Improvements to Mapcube and Image Registration

* Description: SunPy also implements a mapcube object that is designed to hold series of images, currently primarily time-series. This object requires development to allow many desired features to be implemented, such as being able to sort the Maps in the cube by time or frequency or other units. As well as this it is desired that a image registration routine should be implemented to align the images in the cube to a very high degree of accuracy.

* Requirements: Knowledge of image processing a registration would be a plus.

* Mentors: Stuart Mumford and Russell Hewett

## HELIO & HEK

* Description: SunPy has already the capability to access to the Heliophysics Event Knowledgebase.  This database provide a large list of events detected on SDO data.  However, there's room to improve what to do with the results, for example to overplot the contour of the feature requested on the images, or have more complicated queries.  Also, the HELiophisics Integrated Observatory has put together a list of services which allows the scientist to query them in order to discover data in the heliosphere.  For example, when found an event of interest in the Sun it can be propagated forward through the whole heliosphere, finding the adequate intervals where to look for data to measure the event in-situ.

* Requirements: All the services from HEK and HELIO are through webservices (SOAP, REST), thus some understanding on that would be beneficial.

* Mentors: David Perez-Suarez, Jack Ireland (ADNET Systems, Inc. / NASA GSFC)

## Spectroscopy object (EIS, CDS, SUMER)

* Description: Spectroscopy data are usually stored in 3 dimensional arrays (x,y, lambda; or time, y, lambda) with multiple windows (different spectral ranges).  The implementation of this data type on SunPy is essential as these datasets are the one which most information contain, like Intensity at different wavelengths, turbulence in the medium, and speed of the plasma.  Besides, other information such as temperature or electron density of the plasma can also be obtained.  The project will consist in finding the most appropriate class to handle this dataset, and how to make it to interoperate with other data objects like maps (overplot the images), time-series and spectra.

* Requirements: FITS dataformat file understanding, read EIS, CDS data docummentation (link?)

* Mentors: David Perez-Suarez, Stuart Mumford

## Database of local data

* Description: In solar physics the analysis of observational data plays a big role, and the size of the data files varies from few kB to TB for a whole day observation depending the instruments used.  Therefore, it is common that not all the downloaded data is stored in the same place.  This project aims to create a personal database which registers the local path where the data is saved, but also some other metadata (wavelength, provider, etc... ).  This will benefit the user on being able to choose a sub-set of the data stored locally and by saved on bandwidth if the data is requested again.

* Requirements: basic notion of databases (sqlite), willingness to understand the the data retrieval tools in sunpy (ie. VSO)

* Mentors: Florian Mayer, David Perez-Suarez

## PyOpenJPEG

* Description: JPEG 2000 is an advanced image standard that is useful in the storage and transfer of image data and associated image data.  OpenJPEG is an open-source implementation of the JPEG 2000 standard.  PyOpenJPEG is a partially complete Python wrapper around the OpenJPEG Library that allows users to read a JPEG2000 file into Python.  This project seeks to expose the full functionality of the OpenJPEG Library via Python, and so allow SunPy (and Python) users to read, manipulate and write JPEG 2000 files.

* One significant application of PyOpenJPEG is in the visualization of data from the Sun.  The JPEG 2000 image format forms the basis of the [Helioviewer Project](http://wiki.helioviewer.org/wiki/Main_Page), an effort to [visualize](http://www.helioviewer.org) [solar](http://www.jhelioviewer.org) and heliospheric data from multiple [sources](http://helioviewer.org/?date=2013-03-28T22:36:36.000Z&imageScale=38.727054&centerX=38.727054&centerY=0&imageLayers=%5BPROBA2,SWAP,SWAP,174,1,100%5D,%5BSDO,AIA,AIA,304,1,50%5D,%5BSOHO,LASCO,C2,white-light,1,100%5D,%5BSOHO,LASCO,C3,white-light,1,60%5D). Users of Helioviewer Project clients (see images below) can make and share images and [movies](http://www.youtube.com/watch?feature=player_embedded&v=4xESw6G8JdM) of solar features and events.  PyOpenJPEG would allow users of Python-based software to create images of solar data and other science products for use with Helioviewer Project clients, increasing the number and type of images available.

* Requirements: Python, Cython, C; some familiarity with JPEG 2000 standard and the OpenJPEG tools is a plus.

* References: <https://github.com/khughitt/pyopenjpeg>, <https://code.google.com/p/openjpeg/>

* Mentors: Jack Ireland (ADNET Systems, Inc./ NASA GSFC), Keith Hughitt (U. Maryland)

<BR>
_Screen capture of the http://www.helioviewer.org web application._
![Screen capture of the www.helioviewer.org web application.](http://blog.helioviewer.org/wp-content/uploads/2013/04/hv-Screenshot-from-2013-04-03-101858.png)

<BR>
_Screen capture of the [JHelioviewer](http://www.jhelioviewer.org) client application._
![Screen capture of the JHelioviewer client application.](http://blog.helioviewer.org/wp-content/uploads/2011/12/JHelioviewer_Screenshot-at-2011-12-15-133426.png)
