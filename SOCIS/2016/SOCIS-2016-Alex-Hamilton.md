About Me
========

- **Name:**      Alex Hamilton
- **Studies**:   Astrophysics Masters from Queen Mary University of London,
Mathematics and Computer Science Student at the Open University,
Accepted into PhD in Solar Physics
- **GitHub**:    [Alex-Ian-Hamilton](http://github.com/Alex-Ian-Hamilton)
- **Languages**: English (native)

Background
========

I graduated from Queen Mary with a Masters in Astrophysics and I am starting a PhD in September.
I'm passionate about astronomy, science and technology with a specific focus in solar physics which is what has lead me to work with SunPy.
I have been a casual coder since working along with a child’s coding book on my dads old BBC micro, I then moved into basic web development and playing with JavaScript and finally started to get formal teaching in Object Oriented Programming in Java with the Open University.

My dissertation was based on extrapolation of coronal magnetic fields, it involved reading key scientific literature on the subject and implementing a simple mathematical model in Python (using SunPy) which I then evaluated both qualitatively using MayaVi visualization and quantitatively using the Titov-Demoulin Equilibrium model.
In 2015 I was funded by the ESA SoCiS program to develop the SolarBExtrapolation SunPy affiliated package, this is an API for the development and evaluation of magnetic field extrapolation routines.
My code can be found on GitHub:
<https://github.com/sunpy/solarbextrapolation>

In April 2016 I was accepted into a PhD position to study the statistical likelihood of superflares (as seen on on other stars) happening on the Sun.

My general interests include climbing, photography, computer gaming and anything sci-fi.

Previous Projects
========

Over the last 3 years I have had the opportunity to do two summer internships and the ESA SoCiS:

- **RAL (Rutherford Appleton Laboratory)**: investigating the LHC ATLAS detector conditions metadata usage,
- **NPL (the National Physical Laboratory)**: was mostly lab work, testing the qualitative performance of thermal (IR) imagers,
- **ESA SoCiS 2015**: developing the Solar B Extrapolation SunPy affiliated package which will be featured in the 2016 AAS SPD meeting.

All of these projects required that I plan and undertake independent work while collaborating with members of the departments and experts in the fields. Along with valuable coding, troubleshooting and documentation experience I was able to contribute useful insights into the fields for my supervisors.

I also helped on creation of the OpenAstronomy website, designed to promote the work done by 4 major open source astronomy projects.
<https://github.com/OpenAstronomy/openastronomy.github.io/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Aalex-ian-hamilton>

I am also a contributor to the SunPy library and would like the opportunity to have an active role in it's future development, which is why I have choose the Lightcurve Refactor project.

Project
=======

Much of the data collected by solar instruments is analysed as a time series, often of simple one-dimensional value such as the intensity of light observed though a given filter over time. When related too electromagnetic radiation the plot of intensity vs time is called a lightcurve.

In SunPy the lightcurve is one of the three major datatypes, used to store time series data but not necessarily light intensity as it have variants that store logical/Boolean values and SWO sunspot numbers.

As SunPy has moved to become unit-aware with the implementation of AstroPy quantities in SunPy 0.6, the lightcurve has become the only primary dataset that is not in-line with this support.

Likewise, with the development of the Universal Downloader (UniDown), the code that enables the download of lightcurve data files which is currently within the lightcurve class definition has become redundant.

Furthermore, due to the diverse nature of the file-formats used to store the data, the methods used to construct instrument specific lightcurves vary wildly in implementation and necessary parameters, making their use and documentation totally specific per instrument. This is unlike the SunPy Map class, which has a map factory that will create the instrument-specific maps from the source files transparently to the user, leading to a very streamlined interface for all map objects, independent of the data source.

Finally, a major missing piece of functionality is the ability to open multiple lightcurve files and combine these into one lightcurve covering the full given timeframe.

This project aims to refactor the code from the sunpy.lightcurve object to make it fall in line with the map class implementation and to fix those shortcomings.

## Implementation Decisions

### Time Series Implementation

Currently the lightcurve class is implemented using the Pandas Dataframe class, this is designed to store time series and includes much of the necessary time manipulation/selection method.
It has been suggested re-implementing using an AstroPy QTable based time-series, this would give native support for AstroPy Quantities and AstroPy Time objects, however AstroPy doesn’t currently have such a class and consultation with SunPy members has suggested continuing to use Pandas is ideal for this project. Note, there is a proposal for a suitable AstroPy time series class here:
<https://github.com/Cadair/astropy-APEs/blob/master/APE9.rst>

### Defining Instrument Source

Lightcurve data is stored in a variety of data formats, some with header information (such as fits files) that defines the instrument details, others simply don’t have this information, such as data stored in csv files. There needs to be a user-defined way to tell the constructor what source the data is from if it’s not available in the file, a source keyword argument would be a neat and consistent way to do this. This is defines in:

<https://github.com/sunpy/sunpy-SEP/blob/master/SEP-0007.md>

## Stages

The project will be split into 4 stages:

1. Defining a time series class based on the current use of pandas.
This object will be the parent to all future time series classes, which in present will generally be lighcurves, but in future could include time series of map or spectra objects.
2. Implementation of the lightcurve subclasses, this will include “non-light” time series data forms and will provide all the core functionality, including a Timeseries factory class that will be used to call individual instrument constructors when creating a lightcurve object.
3. Implementation of the individual instrument constructors, this will primarily involve taking the code already present in the lightcurve subclasses and simply refactoring it to fit with the new time series API.
4. Testing and documentation each of the subclasses behaves correctly and that the documentation is created to both show the implementation and general usage cases for each of the implemented lightcurves.

## Proposed timeline
### Week 1 / 2
Review the current lightcurve instrument classes and make a comprehensive list of all necessary features and methods. Primarily done here:

<https://github.com/sunpy/sunpy/issues/1520>

Consult with users about the API for Time Series class.
Implement the time series class (potential named Timeseries) class using Pandas ensuring Unit support.

### Week 3 / 4
Implement lightcurve and other Timeseries children classes to support all the current instrument classes.
This should include any methods unique to each instrument.

### Week 5 / 6
Implement a Timeseries factory class (similar to the MapFactory) that is able to take a variety of input parameters and call the relevant instrument constructor. Generally following:

<https://github.com/sunpy/sunpy-SEP/blob/master/SEP-0007.md>

### Week 7 / 8
Implementing and testing any data manipulation functionality: merging Timeseries, time truncation, sub-sampling/re-sampling, summing (1D Superpixels), chronologically sorting and unit manipulation.

### Week 9 / 10
Refining visualization code, there should be a general peek() method for Timeseries, however each subclass and even each of the instrument specific subclasses will need unique properties to make them easily legible. Much of this code is in the instrument subclasses, but some, like [EVE](http://docs.sunpy.org/en/stable/api/sunpy.lightcurve.EVELightCurve.html#sunpy.lightcurve.EVELightCurve) are not very legible by default.

### Week 11 / 12
Building unit tests that will check successful production of each Timeseries child class from sample data files (see [issue 211](https://github.com/sunpy/sunpy/issues/211)) and manual values where applicable.
Likewise units tests for merging Timeseries, time truncation, sub-sampling/re-sampling, summing (1D Superpixels), chronologically sorting and unit manipulation.

### Week 13 / 14
Building documentation within the code for Sphinx generated docs and creating example galleries to show the creation each type of Timeseries object and examples of the generic use, merging Timeseries, time truncation, sub-sampling/re-sampling, summing (1D Superpixels), chronologically sorting and unit manipulation.

Other Info
==========

## Available Platforms
I run Windows 10 x64, Windows 7, Mac OS X Yosemite and Ubuntu.

## Availability
I'm usually available from about 9 am to around 11 pm. My time zone is UTC +1 (British Summer Time - so 0800 to 2200 UTC).
