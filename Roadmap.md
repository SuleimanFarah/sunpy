This page contains the major features desired in every release, general feature requests should like in the issue tracker. This is for milestones that link together to achieve milestones later on. SunPy makes use of the following schema for versioning http://semver.org/.

# Future Releases

## Release 0.8 (Updated 03/2017)
* 80%+ test coverage
* Fido Downloader interface
* deprecation of sunpy.wcs
* timeseries

## Release 0.9

* Final version to support Python 2.7

## Post-0.9 Tentatively called 1.0

Core:
* Remove: lightcurve, wcs and all functions deprecated in either 0.9 or 0.8.
* The spectra affiliated package has had a couple of releases.
* First version to support 3.x+ only. (we might be able to have min 3.6 here).
* Integrate Astropy time into the code base, through parse_time() and the `TimeRange` object.1

Extras:
* Finish Fido, i.e database integration and automatic caching of results.


## Long Term Goals (1.0 or 2.0)
* Have a generalised coordinate system representation shared by *all* data types, i.e. Astropy Generalised WCS or HyperMap coordinate system.
* Complete integration of all core data types, i.e. slice a Map to get a Lightcurve
* Complete integration with Astropy, i.e. All code supports units, and a generalised coordinate system.
* Make the Fido interface a unified API for all downloaders and the database. For transparent caching of searches and data.
* Codebase is PEP8 as much as possible and cleaned up where possible.

# Previous Releases

## Release 0.6
* 80%+ Test coverage
* Functions should accept astropy quantities
* Replace our pixel to world transformation functions with Astropy.wcs
* Enable storing of lightcurve data in the database.

## Release 0.7

Top priority features (blocking):
* LightCurves!
 - FIDO - Unified downloader: Unifies acquisition of data. A requirement for the Lightcurve factory.
 - Lightcurve factory: Improved support for existing and well-used SunPy datatype.
 - Plotting normalization.
* Full support for Python 3.x
 - Python 3.x has many new features useful for scientific computing.
 - All major packages in the SciPy stack are Python 3.2>= compliant.

Other high priority features (non-blocking):
* Include high quality solar ephemeris library.
* Integrate Astropy coordinates.
* Transformation of images under solar differential rotation.
* 85%+ Test coverage.
