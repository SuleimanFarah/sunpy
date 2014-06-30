## Release 0.5 (June 2014)
Summary of this release: This release will continue integration with Astropy. Major refactor for light curve and addition of observation-based map classes.
* 70%+ Test coverage
* Functions should accept astropy quantities
* LightCurve Refactor, downloading function should be removed
* First cut at SunPy Gallery implemented

## Release 0.6
* 80%+ Test coverage
* Integrate Astropy coordinates
* Include high quality solar ephemeris library
* Replace our pixel to world transformation functions with Astropy.wcs
* database should integrate with light curve data

## Release 0.7
* Full support for Python 3.x
* Integrate Astropy time object into parse_time() and the Time Range object

## Release 0.8
* Refactor plotting functions outside of core datatypes

## Release 0.9

## Release 1.0
* Have a generalised coordinate system representation shared by *all* data types, i.e. Astropy Generalised WCS or HyperMap coordinate system.
* Complete integration of all core data types, i.e. slice a Map to get a Lightcurve
* Complete integration with Astropy, i.e. All code supports units, and a generalised coordinate system.