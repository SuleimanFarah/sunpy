The formal application can be found [here](https://google-melange.appspot.com/gsoc/proposal/review/google/gsoc2013/mattbates/7001#).

## Proposal Title

#### SunPy : Local Database of Queried Data, Extending PyOpenJPEG, or Spectroscopy Data

## Personal Bio

I am a freshman at Virginia Commonwealth University in Richmond, Virginia aiming for a B.S. in Computer Science. I've never contributed to an open source project other than SunPy and am looking forward to this helping me find my place in open source software. The majority of my experience comes from video games I've created and coding competitions that I've participated in. I believe my experience in developing games is especially relevant to the proposed project as having a local database is an idea used frequently in games with online play. While the my knowledge is greatest in Java and C++, python is my next strongest language and I should have no trouble using it.

Solar physics has been an interest of mine for a long time, but one that I have never been fortunate enough to invest into. I've taken all of the available physics and astronomy courses available in high school and my first year in university and am looking forward to do my own independent learning in the subject. I chose the database idea because of my limited knowledge on the subject, but I plan on using this summer's time to learn more about solar physics and continue contributing to SunPy.

## Local Database

## Proposal Abstract

In solar physics the analysis of observational data plays a big role, and the size of the data files varies from few kB to TB for a whole day observation depending the instruments used. Therefore, it is common that not all the downloaded data is storage in the same place. This project aims to create a personal database which registers the local path where the data is saved, but also some other metadata (wavelength, provider, etc... ). This will benefit the user on being able to choose a sub-set of the data stored locally and by saved on bandwidth if the data is requested again.

## Proposal Detailed Description

I don't have any other commitment during summer hence I will work the normal 40 hr/week throughout the summer. I plan on implementing things such as tunable capacity and local data compression. I will regularly blog about (among other projects of mine) the problems that I encounter and my achievements in working with SunPy. This will be implemented without changing the net interface at all if possible.

##### Week 1 and 2 (17th June - 30th June)

Storage and retrieval of data and metadata on disk.

##### Week 3, 4 and 5 (1st July - 21st July)

Adding capacity limits and prioritization of data due to things such as size and frequency of query.

##### Week 6 and Midterm Evaluation Period (22nd July - 2nd Aug)

Buffer period. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.

##### Week 7, 8 and 9 (3rd Aug - 23rd Aug)

Adding compression of local data, possibly by stripping unimportant or small amounts of re-query-able data or metadata, or simple .rar/.zip archiving.

##### Week 10 and 11 (24th Aug - 6th Sep)

Possibly restructuring how test cases are handled, including them by default into the stored data and querying for them like all other data.

##### Week 12 and Final Evaluation (7th Sep - 16th Sep)

Buffer period. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.

## PyOpenJPEG

## Proposal Abstract

JPEG 2000 is an advanced image standard that is useful in the storage and transfer of image data and associated image data. OpenJPEG is an open-source implementation of the JPEG 2000 standard. PyOpenJPEG is a partially complete Python wrapper around the OpenJPEG Library that allows users to read a JPEG2000 file into Python. This project seeks to expose the full functionality of the OpenJPEG Library via Python, and so allow SunPy (and Python) users to read, manipulate and write JPEG 2000 files.

## Proposal Detailed Description

One significant application of PyOpenJPEG is in the visualization of data from the Sun. The JPEG 2000 image format forms the basis of the Helioviewer Project, an effort to visualize solar and heliospheric data from multiple sources. Users of Helioviewer Project clients (see images below) can make and share images and movies of solar features and events. PyOpenJPEG would allow users of Python-based software to create images of solar data and other science products for use with Helioviewer Project clients, increasing the number and type of images available.

##### Week 1

Analyze the current PyOpenJPEG implementation and determine what additions or modifications should be made, with attention to not only what is available in OpenJPEG but how the current library in implemented.

##### Week 2, 3

Implement the designs

##### Week 4

Reanalyze the current library, it's implementation and other possible additions or modifications

##### Week 5, 6, and Midterm Evaluation Period

Commit the new changes and additions to the library

##### Remaining time

Update projects that implement PyOpenJPEG(SunPy) to take advantage of the new utility of PyOpenJPEG and repeat the analysis/implementation/update-projects cycle for the end goal of an easy to use and powerful python implementation of the OpenJPEG

## Spectroscopy Objects

## Proposal Abstract

SunPy currently does not have the capabilities to easily manage spectroscopy data, this project with implement new classes to manage this data and it's interactions with the many already implemented features that SunPy includes.

## Proposal Detailed Description

Spectroscopy data are usually stored in 3 dimensional arrays (x,y, lambda; or time, y, lambda) with multiple windows (different spectral ranges). The implementation of this data type on SunPy is essential as these datasets are the one which most information contain, like intensity at different wavelengths, turbulence in the medium, and speed of the plasma. Besides, other information such as temperature or electron density of the plasma can also be obtained. The project will consist in finding the most appropiate class to handle this dataset, and how to make it to interoperate with other data objects like maps (overplot the images), time-series and spectra.

##### Week 1

Understand how this problem is currently solved and design a class that can be implemented with the least change

##### Weeks 2, 3

Implement a basic class that has the appropriate interface and can store data in either the (x,y,lambda) format or the (time,y,lambda) format

##### Weeks 4, 5, 6

Allow data to be read from the VSO web client into a spectroscopy data object and test the functions with the real data

##### Weeks 7, 8

Create an interface between the spectroscopy data object and the current SunPy projects objects such as Map.

##### Weeks 9, 10

Work to allow further information to be obtained from the information, such as temperature or electron density of the plasma.

##### Weeks 11, 12

Buffer period to be used to finish previous milestones or if time allows complete more things relevant to the project.

## Contributions to SunPy

* [split(int) function added to time_range](https://github.com/sunpy/sunpy/pull/428)

## Code Samples

* My current group project in C++, showing knowledge many things including working with external libraries: [Terraria Clone](https://github.com/rmbreak/terraria-clone)
* My past project in Java, showing web interactions relevant to the projects: [Zombies!](http://www.mediafire.com/download.php?4o1q659fbw85l28)
* My group mobile app hackathon project working with Dominion Enterprises' Boats.com API, showing knowledge using databases: [Boat Thing](https://github.com/dominionenterprises/dmm-hacku)

Thanks to [Ankit Agrawal](https://github.com/sunpy/sunpy/wiki/GSoC-2013--Ankit-Agrawal) for the help setting up this page
