## A [ginga](http://ejeschke.github.io/ginga/) based data explorer / database browser

### Description:

In IDL, there are two major sources of GUIs for exploring solar data, Solarsoft packages and CRISPEX. Both are using IDL's widget system whose back-end is Motif and make ugly GUIs. Exploring solar data for interesting events and extracting important information is important for being able to do research.

Currently, such a GUI program does not exist for Python. However, with the current capabilities of [Ginga](https://github.com/ejeschke/ginga), it offers a very good base. It allows us to expand to meet the requirements for solar data. Ginga has already several features such as FITS support and several plugins that allow basic analysis of data. It also supports several back-ends.

Ginga is designed to use a plugin system. This enables SunPy specific plugins to be written that can be installed by any user. We would want to create several plugins that would allow Ginga to be widely spread throughout the solar community.

#

We would want a plugin that uses SunPy's database explorer module and supporting Solar coordinates using AstroPy's WCS module.
Further, we want to expand other Ginga plugins like the slit plugin to work on 3D data to produce x-y plots.

* Requirements: Python, Qt/GTK (depending on back-end choice)

* Difficulty: Medium to Hard

* Mentor: Stuart Mumford, Steven Christe

## Re-implementation of `sunpy.wcs` as `sunpy.coordinates` using `astropy.coordinates`

### Description

Coordinates for solar image data are described in [Thompson, W. (2009)](http://adsabs.harvard.edu/abs/2006A%26A...449..791T). Currently a subset of these systems and transformation are implemented in `sunpy.wcs`. Astropy, a core package for astronomy, has a flexible spatial coordinates package in `astropy.coordinates`. However, this package is currently in the planning phase of a large re-design, which will make it even more applicable for use for solar coordinate data. Astropy Proposal for Enhancement (APE) number 5 [APE5](https://github.com/astropy/astropy-APEs/pull/6) describes the proposed API. It is anticipated that this code will form part of the Astropy 0.4 release scheduled for June/July 2014, and therefore be implemented well before this point.

This project involves using the `CoordinateFrame` and `CoordinateRepresentation` framework described in [APE5](https://github.com/astropy/astropy-APEs/pull/6) to implement Helio-Projective and Helio-Centric `CoordinateFrames` that can be transformed into Cartesian, Spherical and Cylindrical representations and between each other using the bi-directional transformation graph in `astropy.coordinates`. This project will involve collaboration with the astropy project and potentially pushing patches upstream.

Extensions to this project would be to implement transformations from solar coordinates to other celestial coordinates as supported by astropy. As well as work on integrating `astropy.units` into the SunPy code base.

* Requirements: Python

* Difficulty: Medium

* Mentor: Stuart Mumford, Steven Christe

## LightCurve refactor

### Description

Lightcurves are a major datatype in solar physics.  A lightcurve is a time-ordered list of scalar measurements.  A typical lightcurve consists of observation times, and measurements taken at that time.  These measurements could be numeric, such as the amount of soft X-ray flux from the Sun (arising from GOES data), or some kind of string, for example, the Mt. Wilson classification of an active region as a function of time. The current LightCurve object implementation uses the pandas library, since pandas has very many useful capabilities for handling time-ordered data.  However, the current implementation needs to be considered in the light of the astropy Time module and the astropy Table module.

As well as the integration of astropy into the lightcurve module, it is important to create a `Lightcurve` factory class, like `Map()` see [[LightCurve Refactor Proposal]] for details on the proposed factory implementation. There are more challenges faced by the `Lightcurve` factory than by the `Map` factory, due to the diverse nature of the Lightcurve data files both for retrieval from online sources and parsing of the CSV files. Having the `Lightcurve` API follow that of `Map` is a fundamental step towards uniting the data types in the core library.

* Requirements: Knowledge of, or willingness to learn, the pandas and astropy libraries

* Difficulty: Medium

* Mentor: J. Ireland, A. R. Inglis, Stuart Mumford

## Increase SunPy's Image processing capability, image alignment, rotation and warping

### Description

A large amount of solar physics data analysis is image processing based. Features in [scikit-image](http://scikit-image.org/) such as feature detection and tracking as well as image warping and transformation. There are a few sub-projects under this project idea that could be tackled and expanded by a student.

* Looking into the differences between `sunpy.image.Crotate` and [`skimage.transform`](http://scikit-image.org/docs/0.9.x/api/skimage.transform.html) specifically the `AffineTransform` type code. The motivation for this is using scikit-image rather than maintaining our own C extension code would make the SunPy code base easier to maintain as well as providing more features. As part of this work a patch to [issue #741](https://github.com/sunpy/sunpy/issues/741) could be devised.

* Implement a fine alignment routine to be added to the `MapCube` API, to allow the stacking of various images. This is made possible by new features recently added to scikit-image <https://github.com/scikit-image/scikit-image/pull/834>

* The outer layers of the Sun do not rotate as a solid body, the equatorial regions rotate faster than the poles. When considering analysis of surface features on the Sun compensating for this rotation is essential. This project would involve finishing work already started on this and understanding the physical processes behind the computational algorithms.

* Requirements: Python

* Difficulty: Medium to Hard

* Mentor: Albert Shih, David Perez-Suarez

## Implement various differential rotation routines in SunPy

## HELIO - capabilities improvement

### Description

SunPy has already the capability to access to the Heliophysics Events Catalogue provided by the HELiophysics Integrated Observatory.  This catalogue provides access to different lists of events observed anywhere in the heliosphere.  However, HELIO offers a lot more web services of interest for the solar community.  Some of the services can provide information of when and where a planet or instrument where located, properties on features detected on the sun, or properties of some heliospheric observations; moreover it also allow the discovery of new data by a propagation model which simulates three different scenarios - Coronal Mass Ejections, High speed solar wind and Solar Energetic Particles events.

This project would consist in the creation of an interface to access to HELIO services in a similar way that other services like HEK or VSO are accessible at the moment. HELIO uses VOTables as the standard to transfer the data, astropy provides support for reading such file format, therefore some understanding of astropy may be needed.

* Requirements: All the services from HELIO are through webservices (SOAP, REST), thus some understanding on that would be beneficial. VOTable parser provided from astropy will be used, so familiarization with such interface will be helpful.

* Difficulty: Medium

* Mentors: David Perez-Suarez, (Marco Soldati, Kevin Benson - HELIO)

## Spectroscopy object (EIS, CDS, SUMER)

### Description

Spectroscopy data are usually stored in 3 dimensional arrays (x,y, lambda; or time, y, lambda) with multiple windows (different spectral ranges).  The implementation of this data type on SunPy is essential as these datasets are the one which most information contain, like Intensity at different wavelengths, turbulence in the medium, and speed of the plasma.  Besides, other information such as temperature or electron density of the plasma can also be obtained.  The project will consist in work over the hypermap class and the astropy efforts to be able to handle this dataset, and to make it to interoperate with other data objects like maps (overplot the images), time-series and spectra.

* Requirements: FITS dataformat file understanding, read EIS, CDS data documentation (link?)

* Difficulty: Hard

* Mentors: David Perez-Suarez, Albert Shih
