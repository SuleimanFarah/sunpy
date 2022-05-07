The [[SOCIS 2015 organization application page|SOCIS 2015]].

*Students*: Once SunPy is accepted as an mentoring organization, you need to apply in the
[SOCIS website](http://sophia.estec.esa.int/socis/) and also don't forget to
add your application to this [[wiki|SoCiS 2015 Student Applications]].
Try to follow the [[application guidelines|GSoC-student-application-guidelines]]
we set for the GSoC, you will get more chances to be selected if you follow them.

The ideas shown below are projects that we believe can be completed during the SOCIS
programming period (June - August).
The projects are sorted in order of interest to the SunPy community.
Please join the #sunpy IRC channel ([web client](http://webchat.freenode.net/)) to
talk with the SunPy community and do not hesitate to introduce yourself in any of our
mailing list ([users](https://groups.google.com/forum/?fromgroups#!forum/sunpy),
[developer](https://groups.google.com/forum/?fromgroups#!forum/sunpy-dev)).

## IRIS Integration
* **Description**: The [IRIS](http://iris.lmsal.com) observes the chromosphere and transition region
of the Sun with high spatial and time resolution. The primary goal of the Interface Region Imaging Spectrograph (IRIS) explorer is to understand how the solar atmosphere is energized. The IRIS mission produces data through
a slit-jaw imager which can take images of the Sun at various wavelengths as well as a line spectrograph which
rasters over an image to build up an image. This project aims to integrate IRIS data into SunPy. This includes the following tasks.

1. Integration of IRIS data search and querying
2. Adding the ability to read IRIS data files into their proper data objects
3. Developing a GUI data browser for fast inspection of data

* **Requirements**: Python and basic knowledge of GUI design.

* **Mentor**: Steven Christe (SunPy), Joel Allred (GSFC)

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


## Increase SunPy's Image processing capability, image alignment, rotation and warping.

* **Description**: A large amount of solar physics data analysis is image processing based. Features in [scikit-image](http://scikit-image.org/) such as feature detection and tracking as well as image warping and transformation. There are a few sub-projects under this project idea that could be tackled and expanded by a student.

** Looking into the differences between `sunpy.image.Crotate` and [`skimage.transform`](http://scikit-image.org/docs/0.9.x/api/skimage.transform.html) specifically the `AffineTransform` type code. The motivation for this is using scikit-image rather than maintaining our own C extension code would make the SunPy code base easier to maintain as well as providing more features. As part of this work a patch to [issue #741](https://github.com/sunpy/sunpy/issues/741) could be devised.

** Implement a fine alignment routine to be added to the `MapCube` API, to allow the stacking of various images. This is made possible by new features recently added to scikit-image https://github.com/scikit-image/scikit-image/pull/834

** The outer layers of the Sun do not rotate as a solid body, the equatorial regions rotate faster than the poles. When considering analysis of surface features on the Sun compensating for this rotation is essential. This project would involve finishing work already started on this and understanding the physical processes behind the computational algorithms.

* **Requirements**: Python

* **Difficulty**: Medium to Hard

* **Mentor**: Albert Shih, Jack Ireland, David Perez-Suarez

## HELIO - capabilities improvement

* **Description**: SunPy has already the capability to access to the Heliophysics Events Catalogue provided by the HELiophysics Integrated Observatory.  This catalogue provides access to different lists of events observed anywhere in the heliosphere.  However, HELIO offers a lot more web services of interest for the solar community.  Some of the services can provide information of when and where a planet or instrument where located, properties on features detected on the sun, or properties of some heliospheric observations; moreover it also allow the discovery of new data by a propagation model which simulates three different scenarios - Coronal Mass Ejections, High speed solar wind and Solar Energetic Particles events.

 This project would consist in the creation of an interface to access to HELIO services in a similar way that other services like HEK or VSO are accessible at the moment. HELIO uses VOTables as the standard to transfer the data, astropy provides support for reading such file format, therefore some understanding of astropy may be needed.

* **Requirements**: All the services from HELIO are through webservices (SOAP, REST), thus some understanding on that would be beneficial. VOTable parser provided from astropy will be used, so familiarization with such interface will be helpful.

* **Difficulty**: Medium

* **Mentors**: David Perez-Suarez, (Marco Soldati, Kevin Benson - HELIO)

## Idea
* **Description**: The ...
* **Requirements**: Knowledge of ...
* **Mentor**: Mentor A, Mentor B


### List of Mentors
* Steven Christe
* David PS
