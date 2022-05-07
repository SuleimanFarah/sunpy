The [[SOCIS 2014 organization application page|SOCIS 2014]].

*Students*: You need to apply in the
[SOCIS website](http://sophia.estec.esa.int/socis2014/) and also don't forget to
add your application to this [[wiki|SoCiS 2014 Student Applications]].
Try to follow the [[application guidelines|GSoC-student-application-guidelines]]
we set for the GSoC, you will get more chances to be selected if you follow them.

The ideas shown below are projects that we believe can be completed during the SOCIS
programming period (** - **).
The projects are sorted in order of interest to the SunPy community.
Please join the #sunpy IRC channel ([web client](http://webchat.freenode.net/)) to
talk with the SunPy community and do not hesitate to introduce yourself in any of our
mailing list ([users](https://groups.google.com/forum/?fromgroups#!forum/sunpy),
[developer](https://groups.google.com/forum/?fromgroups#!forum/sunpy-dev)).

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

## Spectrum Object
* **Description**: The SunPy project is built upon a number of objects which hold
data such as the map object (for two-dimensional image data) and the lightcurve
object (for time-ordered scalar data).
The third major object we require is the spectrum object, which is for data ordered
by energy (or its equivalent, such as wavelength).
The goal of this project is to design and implement the spectrum object for SunPy.
This object will need to be able to display its data in a basic plot form.
In addition, different sub-classes of the main spectrum object will also need to
handle the various kinds of spectral data.
It will also need to be able to convert from data (e.g. counts) to physical
quantities (e.g. photons) through knowledge of the detector response (for example,
the detector response is typically described using a matrix).
A number of physical models are also necessary to interpret spectra.
Coding up efficient forms of these models can also be part of this project if time allows.

* **Requirements**: Basic knowledge of spectral data analysis is a plus.

* **Mentor**: David PS(SunPy) and Peter Young?(EIS)

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
* Laszlo I. Etesi
* Steven Christe
* David PS
