## A [ginga](http://ejeschke.github.io/ginga/) based data explorer / database browser 

* Description: 

In IDL, there are two major sources of GUIs for exploring solar data, Solarsoft packages and CRISPEX. Both are using IDL's widget system whose back-end is Motif and as such make ugly GUIs. Exploring solar data for interesting events and extracting the information required is important for being able to publish papers. 

Currently, a GUI program does not fully exist for Python. However, with the release of Ginga, it offers a very good base to expand further to meet the requirements for solar data. Ginga has already several features such as FITS support and several plugins that allow basic analysis of data. It also supports several back-ends. 

Ginga is designed to use a plugin system. This enables SunPy specific plugins to be written that can be installed by any user. We would want to create several plugins that would allow Ginga to be widely spread throughout the solar community.

We would want a plugin that uses SunPy's database explorer module and supporting Solar coordinates using AstroPy's WCS module.  
Further, we want to expand other Ginga plugins to work on 3D data among other items.

* Requirements: Python, QT/GTK (depending on back-end choice) 

* Mentor: Nabil Freij, Stuart Mumford

## Astropy integration

* Description: 
Astropy is a core package for astronomy. A lot of the code in astropy is diectly applicable to SunPy. This project's aim is to tighten the integration between astropy and SunPy. This includes making SunPy support `astropy.units` everywhere in the code base where it is applicable. Designing and building a new version of `sunpy.coords` that is based on `astropy.coordinates`. This project will involve a lot of interaction with the Astropy project and probably some development on that code base.

* Requirements: Python

* Mentor: Stuart Mumford, (Steven Christe?)

## LightCurve refactor

* Description: 

Lightcurves are a major datatype in solar physics.  A lightcurve is a time-ordered list of scalar measurements.  A typical lightcurve consists of observation times, and measurements taken at that time.  These measurements could be numeric, such as the amount of soft X-ray flux from the Sun (arising from GOES data), or some kind of string, for example, the Mt. Wilson classification of an active region as a function of time. The current LightCurve object implementation uses the pandas library, since pandas has very many useful capabilities for handling time-ordered data.  However, the current implementation needs to be considered in the light of the astropy Time module and the astropy Table module.

As well as the integration of astropy into the lightcurve module, it is important to create a `Lightcurve` facotry class, like `Map()` see [[LightCurve Refactor Proposal]] for deatils on the proposed factory implementation. There are more challenges faced by the `Lightcurve` factory than by the `Map` factory, due to the diverse nature of the Lightcurve data files both for retreival from online sources and parsing of the CSV files. Having the `Lightcurve` API follow that of `Map` is a fundamental set towards uniting the data types in the core library.



* Requirements: Knowledge of the pandas and astropy libraries

* Mentor: J. Ireland, A. R. Inglis, Stuart Mumford



## spectrogram refactor

* Description: 

* Requirements: Some knowledge of...

* Mentor: 
## Idea A

* Description: 

* Requirements: Some knowledge of...

* Mentor: 

## Idea B

* Description: 

* Requirements: Some knowledge of...

* Mentor: 
