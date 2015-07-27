This page contains the major features desired in every release, general feature requests should like in the issue tracker. This is for milestones that link together to achieve milestones later on.

## Release 0.6
* 80%+ Test coverage
* Functions should accept astropy quantities
* Replace our pixel to world transformation functions with Astropy.wcs
* Enable storing of lightcurve data in the database.

## Release 0.7

* FIDO - Unified downloader.
 - Unifies acquisition of data. A requirement for the Lightcurve factory.
* Lightcurve factory.
 - Improved support for existing and well-used SunPy datatype.
* Full support for Python 3.x
 - Python 3.x has many new features useful for scientific computing.
 - All major packages in the SciPy stack are Python 3.2>= compliant.
* Include high quality solar ephemeris library.
* Integrate Astropy coordinates.
* Transformation of images under solar differential rotation.
* 85%+ Test coverage.

## Release 0.8
* 90%+ test coverage
* Refactor plotting functions outside of core datatypes
* Integrate Astropy time object into parse_time() and the Time Range object

## Release 0.9

## Release 1.0
* Have a generalised coordinate system representation shared by *all* data types, i.e. Astropy Generalised WCS or HyperMap coordinate system.
* Complete integration of all core data types, i.e. slice a Map to get a Lightcurve
* Complete integration with Astropy, i.e. All code supports units, and a generalised coordinate system.