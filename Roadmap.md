## Release 0.5 (June 2014)
Summary of this release: This release will continue integration with Astropy. Major refactor for light curve and addition of observation-based map classes.
* 70%+ Test coverage
* Functions should accept astropy quantities
* LightCurve Refactor, downloading function should be removed
* First cut at SunPy Gallery implemented

## Release 0.6
* 80%+ Test coverage
* Include high quality solar ephemeris library
* Re-factor of WCS into an object-oriented approach. For example, define an observer object which gives distance from Sun, heliographic longitude and latitude, etc.
* Refactor plotting functions outside of core datatypes
* database should integrate with light curve data
* Integrate Astropy time object into parse_time() and the Time Range object
* Convert to numpy standard for accessing data in image arrays (see [link](http://docs.scipy.org/doc/numpy/reference/internals.html#internal-organization-of-numpy-arrays))
* Create observation Map classes
* Integrate astropy coordinates

## Release 0.7
* Full support for Python 3.x

## Release 0.8

## Release 0.9

## Release 1.0
* Have a generalised coordinate system representation shared by *all* data types, i.e. Astropy Generalised WCS or HyperMap coordinate system.
* Complete integration of all core data types, i.e. slice a Map to get a Lightcurve
* Complete integration with Astropy, i.e. All code supports units, and a generalised coordinate system.