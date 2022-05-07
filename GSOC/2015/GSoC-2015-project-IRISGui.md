### IRIS, 4D Cubes and GUI

*Suggested Mentors:* [Steven Christe](http://github.com/ehsteve) (NASA GSFC, SunPy), [Nabil Freij](https://github.com/nabobalis) (Sheffield University)

*Difficulty:* Intermediate to Expert

*Astronomy knowledge needed:* None

*Programming skills:* Python and basic knowledge of GUI design.

#### Description

Recently, a new Sun observing satellite was launched, called [IRIS](http://iris.lmsal.com).
It performs high-resolution, multi-wavelength observations of the solar atmosphere.
As a result, the data is saved out as 4D cubes. These cubes have the following structure, [Time, Wavelength, Spatial].
This format is also used by other ground and space-based telescopes.

Traditionally (which is a powerful thing in astronomy), data analysis is done using a programming language called IDL.
Using this language, a GUI was created called [CRISPEX](http://folk.uio.no/gregal/crispex/) and is used to do simple but effective analysis.

This project aims to create a smaller scale version that uses [Ginga](http://ejeschke.github.io/ginga/) as a backend.
Ginga is a file viewer that was created with astrophysics in mind.
It allows basic manipulation of FIT files, which are the standard data container in astrophysics.
A Python plugin will be created and integrated into Ginga, allowing the user to open 3D/4D datasets and perform basic analysis, such as, slit extraction.

To achieve this, a previous ESA summer project created a cube class.
While it was finished, it was never integrated into SunPy.
The code was created to hold and manipulate complex datatypes.
It is similar in style to the SunPy Map Class and follows that convention.
It however, has extra features enabling specific data formats to be extracted that the user requires, for example, a spectrum.
The student will need to become familiar with this code, as small tweaks need to occur before it is added to SunPy.

Finally, the plugin will be created using Python.
However, a background in QT would ideally be needed but it is not necessary.
Ginga uses multiple backends for the GUI but we plan to use QT.

Plugin Features:

1. Open FITS file and call the correct SunPy Map or Cube class.
1. Solar coordinate integration.
1. Perform slit extraction with the ability to choose a time and/or wavelength range.

Sunpy Feature:

1. Full IRIS support.
