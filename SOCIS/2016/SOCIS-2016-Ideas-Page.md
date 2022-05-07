### Lightcurve Refactor

*Suggested Mentor(s):* [Stuart Mumford](http://github.com/Cadair), [Dan Ryan](https://github.com/DanRyanIrish), [Andrew Inglis](https://github.com/aringlis), [Jack Ireland](https://github.com/wafels)

*Difficulty:* Beginner

*Astronomy knowledge needed:* None

*Programming skills:* Python

#### Description
The `Lightcurve` class is one of the three core datatypes in SunPy, along with Map and Spectra.
`Lightcurve` is designed to read in, process and store meta data related to solar physics time series data.
Currently, `Lightcurve` uses the pandas library as its underlying data structure, however, this is subject to change in the future.

Much like the `map` submodule, `lightcurve` needs to be able to read in various supported data formats (such as FITS, ascii and others in the future), store their meta data and give users unified access to this metadata independently of the original source of the data.

As currently implemented (as of 0.6) the `lightcurve` module performs three core tasks:

1. Download the raw data
1. Read this data into a pandas dataframe
1. store the meta data obtained with the data.

As of the SunPy 0.7 release the first stage will be moved out of `lightcurve` and into the `net` subpackage as part of the [`UnifiedDownloader`](https://github.com/sunpy/sunpy/pull/1300) Pull Request.
This leaves `lightcurve` in a similar position to `map` where the data acquisition is not part of the core data type and is managed separately.

The objective of this project is to re-implement the core of the lightcurve submodule, such that it no longer contains the code to download data from the internet. The lightcurve module should be able to open file from disk that have been downloaded using the new UnifiedDownloader submodule. The lightcurve factory must be able to read files from multiple sources some of which will be able to be auto-detcted and some which will not. The lightcurve module must also be able to combine multiple files into a single timeseries.

**Expected Outcomes**

Someone under taking this project will complete the following tasks:

1. Become familiar with the `UnifiedDownloader` code, if it has not been accepted into the SunPy codebase, complete the remaining tasks for this to be achieved.
1. Write a factory class for `lightcurve` similar to the `sunpy.map.Map` class. This class will be a generic constructor for `lightcurve` allowing the user to instantiate any one of the many subclasses of `GenericLightcurve` present in `sunpy.lightcurve.sources`. The API design for the factory class is in [SEP 7](https://github.com/sunpy/sunpy-SEP/blob/master/SEP-0007.md).
1. Design and develop a robust method of dealing with lightcurve meta data, which can handle joining different parts of timeseries from different files, each with their own meta data. (See [#1122](https://github.com/sunpy/sunpy/issues/1122))


A successful proposal for this project will demonstrate that the applicant has understood the mechanism behind the `Map` factory as already implemented in SunPy and presents a timeline of what things need to change in Lightcurve to mirror the design of `Map` and follow the design for Lightcurve in [SEP 7](https://github.com/sunpy/sunpy-SEP/blob/master/SEP-0007.md).


### GUI to use LCT tools
*Suggested Mentor(s):* [Jose Iván Campos Rozo](https://github.com/Hypnus1803) (National Astronomical Observatory, National University of Colombia), Santiago Vargas Domínguez (National Astronomical Observatory, National University of Colombia), [David Pérez Suárez](https://github.com/dpshelio).

*Difficulty:* Intermediate

*Astronomy knowledge needed:* None

*Programming skills:* Python, basic knowledge of qt4, pyqt4, qt designer

#### Description:
The Local Correlation Tracking (LCT, November & Simon, 1988) technique is a robust method used to study the dynamics of structures in a time series of images. By tracking pixel displacements, using a correlation window, LCT can determine proper motions and generate flow maps of horizontal velocities. This procedure is used to study the dynamics of plasma in the solar photosphere at different spatial scales, e.g the analysis of granular and supergranular convective cells, meridional flows, etc. A widget implemented in Python was developed. It generates a user-friendly graphical user interface (GUI) to control various parameters for the process of calculating flow maps of proper motions for a series of filtergrams (data cube). Our purpose is to implement this tool in Sunpy using its structure and to improve it with some more options, i.e. masks, statistics, histograms, contours and multi-plots. Although an initial version is already developed, our proposal is to focus on the efficient integration of the code in the  SunPy libraries. The code (without widget files yet) is https://github.com/Hypnus1803/flow_maps

*Expected Outcomes:* To integate efficiently the code in SunPy libraries.

### SunPy Gallery, Docs, Website Upgrades

*Suggested Mentor(s):* [Stuart Mumford](http://github.com/Cadair), [Steven Christe](https://github.com/ehsteve),

*Difficulty:* Beginner

*Astronomy knowledge needed:* None

*Programming skills:* Python

#### Description
The SunPy documentation need some love. The purpose of the

**Expected Outcomes**

Someone under taking this project will complete the following tasks:

1. Research and implement a gallery of SunPy examples which support jupyter notebooks.
2. Update the docs (insert tasks).
   1. Net documentation need to be refactored.
3. Update the website (insert tasks).

A successful proposal for this project will demonstrate that the applicant has understood the task and presents a timeline of what things need to change to be implemented.
