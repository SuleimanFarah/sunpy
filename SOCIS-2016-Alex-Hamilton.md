About Me
========
- Name: Alex Hamilton
- Studies: 4th Year Astrophysics Masters at Queen Mary University of London, Ongoing Mathematics and Computer Science Student at the Open University
- GitHub: [Alex-Ian-Hamilton](http://github.com/Alex-Ian-Hamilton)
- Languages: English (native)

Background
========
An Astrophysics Masters student at Queen Mary, and starting a PhD at Hull University in September I am passionate about astronomy, science and technology with a specific focus in solar physics.
I have been a casual coder since working along with a child’s coding book on my dads old BBC micro, I then moved into basic web development and playing with JavaScript and finally started to get formal teaching Object Oriented Programming in Java with the Open University.

My university project this year is based on coronal magnetic field, it involved reading key scientific literature on the subject and implementing a simple version in Python (using SunPy) which I then evaluated both qualitatively using MayaVi visualisation and quantitatively using the Titov-Demoulin Equilibrium model. I have never contributed to an Open Source project and consider this to be the perfect opportunity for me to take what I have learnt and use it to implement tools that everyone can use.

My general interests include climbing, photography, computer gaming and anything sci-fi.

Previous Projects
========
Over the last 3 years I have had the opportunity to do two summer internships and the ESA SoCiS:
 -  RAL was investigating the LHC ATLAS detector metadata usage,
 -  NPL (the National Physical Laboratory) was mostly lab work, testing the qualitative performance of thermal (IR) imagers,
 -  ESA SoCiS 2015, I coded the Solar B Extrapolation SunPy Affiliated Package which will be featured in the 2016 AAS SPD meeting

All of these projects required that I plan and undertake independent work while collaborating with members of the departments and experts in the fields. Along with valuable coding, troubleshooting and documentation experience I was able to contribute useful insights into the fields for my supervisors.

I also helped on creation of the OpenAstronomy website, designed to promote the work done by 4 major open source astronomy projects.
https://github.com/OpenAstronomy/openastronomy.github.io/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Aalex-ian-hamilton

I am also a regular contributor to the SunPy library.

Project
========
Much of the data collected by solar instruments is analysed as a time series, often of simple one-dimensional value such as the intensity of light observed though a given filter over time. When related too electromagnetic radiation the plot of intensity vs time is called a lightcurve.
In SunPy the lightcurve is one of the three major datatypes, used to store time series data but not necessarily light intensity as it have variants that store logical/Boolean values and SWO sunspot numbers.
As SunPy has moved to become unit-aware with the implementation of astropy quantities in SunPy 0.6, the lightcurve has become the only primary dataset that is not in-line with this support.
Likewise, with the development of the Universal Downloader (UniDown), the code that enables the download of lightcurve data files which is currently within the lightcurve class definition has become redundant.
Furthermore, due to the diverse nature of the file-formats used to store the data, the methods used to construct instrument specific lightcurves vary wildly in implementation and necessary parameters, making their use and documentation totally specific per instrument. This is unlike the SunPy Map class, which has a map factory that will create the instrument-specific maps from the source files transparently to the user, leading to a very streamlined interface for all map objects, independent of the data source.
Finally, a major missing piece of functionality is the ability to open multiple lightcurve files and combine these into one lightcurve covering the full given timeframe.
This project aims to refactor the code from the sunpy.lightcurve object to make it fall in line with the map class implementation and to fix those shortcomings.

Implementation Decisions
There are some major decisions that need to be considered when implementing this project.
Currently the lightcurve class is implemented using the Pandas Dataframe class, this is designed to store time series and includes much of the necessary time manipulation/selection method, however these are not designed to store scientific data and which have limited time precisions and no ability to implement astropy quantities.
Ideally the basic SunPy time series would be implemented using an astropy time series class, such as proposed here:
https://github.com/Cadair/astropy-APEs/blob/master/APE9.rst
However as this is yet to be implemented it can be implemented using an astropy table with a column for date/time data.
Note: as far as I’m aware you can’t organise a table using an astropy time column.

The project will be split into 3 stages:
1
Defining a time-series class API that includes methods for combining, cropping/truncating and resampling??? The time series data.
This object will be the parent to all future time series classes, which in present will generally be lighcurves, but in future could include time series of map or spectra objects.
The syntax for manipulating the time series is potentially to be taken from the current Pandas-based implementation.
2
Implementation of the lightcurve subclasses, this will include “non-light” time series data forms and will provide all the core functionality, including a timeseries factory class that will be used to call individual instrument constructors when creating a lightcurve object.
3
Implementation of the individual instrument constructors, this will primarily involve taking the code already present in the lightcurve subclasses and simply refactoring it to fit with the new time series API.
4
Testing and documentation each of the subclasses behaves correctly and that the documentation is created to both show the implementation and general usage cases for each of the implemented lightcurves.

##Proposed timeline
###Week 1 / 2

###Week 3 / 4

###Week 5 / 6

###Week 7 / 8

###Week 9 / 10

###Week 11 / 12

###Week 13 / 14

Other Info
==========
##Available Platforms
I run Windows 10 Preview x64, Windows 8.1 x64/x86, Windows 7, Mac OS X Yosemite and Ubuntu. 

##Availability
I'm usually available from about 9 am to around 11 pm. My time zone is UTC +1 (British Summer Time - so 0800 to 2200 UTC).