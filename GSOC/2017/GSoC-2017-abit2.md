### Organization: OpenAstronomy

### Sub-Organization: SunPy

### 1. Student Information

* Name: Ankit Baruah
* Time  Zone: +0530 GMT
* IRC Handle: abit2
* Github ID: [abit2](https://github.com/abit2)
* Instant Messaging: Google Hangout (ankit.baruah1@gmail.com)
* Blog: [https://medium.com/@ankit_b](https://medium.com/@ankit_b)

### 2. Education

Currently, I'm a third year undergraduate enrolled in Computer Science & Engineering at Indian Institute of Technology, Kharagpur, West Bengal.

Courses taken (related to computer science) - Algorithms / Data Structures, Software Engineering, Discrete Structures, Formal Language and Automata Theory, Probability and Statistics, Compilers and Compiler's Lab, Computer Architecture, Computer Architecture Lab, *Operating Systems Theory and Lab*, *Networks Theory and Lab*, *Database and Management System*.

*italic* => ongoing

I will graduate in July 2018.

### 3. University Information

* University: [IIT Kharagpur, West Bengal](http://www.iitkgp.ac.in/)
* Major: Computer Science & Engineering
* Current year: 3rd
* Graduation date: July 2018
* Degree: Bachelor of Engineering (Honors)

### 4. Pull Requests

The following are the Pull requests, Issues (both open and closed) I contributed to.

  **IRISPY :**

* Added function to truncate the 3D cube with index, slice, and operation and or operation, the axis specifies
  the coordinate to truncate. Axis can be time/raster_position, slit_axis.
  ([#8](https://github.com/sunpy/irispy/pull/8))
* Added tests for ``irispy/iris_tools.py`` as ``irispy/tests/test_iris_tools.py``and removed bugs in    ``irispy/spectrograph.py`` and ``irispy/iris_tools.py``. This increased the coverage of the project by +10.50%
  ([#4](https://github.com/sunpy/irispy/pull/4)).
* Added tests for ``irispy/iris_spectrograph.py`` as ``irispy/tests/test_iris_spectrograph.py``. This increased
  the coverage of the project by +20.08% ([#7](https://github.com/sunpy/irispy/pull/7)).

**SUNPY :**

* Added HDU index and test for ``sunpy/database/tables.py`` ([#1952](https://github.com/sunpy/sunpy/pull/1952)). Solves the issue of reverse mapping from DatabaseEntry -> HDU.
* Changes made to support the new NDData API by removing the old compatibility layer. Changes were made in ``sunpy/map/mapbase.py`` ([#1929](https://github.com/sunpy/sunpy/pull/1929)). This PR made the Map class which uses NDData as base class support the new API.
* Docs to make the user be able to see the custom meta keywords that are accepted, it will help when creating custom SunPy maps (i.e. from a 2D array). Changes were made in ``sunpy/map/mapbase.py``, ``sunpy/map/sources/hinode.py``, ``sunpy/map/sources/rhessi.py``, ``sunpy/map/sources/sdo.py``, ``sunpy/map/sources/soho.py``, ``sunpy/map/sources/stereo.py``, ``sunpy/map/sources/trace.py`` and ``sunpy/map/sources/yohkoh.py`` . ([#1940](https://github.com/sunpy/sunpy/pull/1940)).
* A helper function that will return the data and the header of that particular HDU. ``sunpy/database/database.py`` ([#1981](https://github.com/sunpy/sunpy/pull/1981)). This PR makes the reverse mapping from DatabaseEntry -> HDU possible.
* Changes made to ``sunpy/net/vso/vso.py`` , makes it possible for the VSOClient to check the online endpoint. ([#1916](https://github.com/sunpy/sunpy/pull/1916)).

I use a Linux Ubuntu machine for development now and have been using it for the past 3 years. I am also familiar with Git, SunPy and IRISPy workflow.

### 5. Proposal abstract

IRIS (Interface Region Imaging Spectrometer) is a science satellite  designed to study energy transport in the solar atmosphere at high spatial, temporal and spectral resolution.  IRIS has two instruments.  The first is a slit-spectrograph which measures the intensity of ultraviolet light from the Sun as a function of its wavelength and produces 2D spectra via a narrow slit in several spectral windows/wavelength ranges.  The second is a slit jaw imager which takes 2D context images of the regions from which  the spectra are measured.  Therefore,to handle this data using Python, two basic classes are required:

* IRISRaster class (to read and anlyse IRIS spectra) and
* IRISSJI class (to read and analyse slit-jaw-images).

The IRISPy will be developed as an affiliated package to Sunpy. The IRISRaster class will involve reading data from fits file and storing data in the IRISRaster object in a cubes where there are four dimensions wavelength, position along slit, raster position and time.

The IRISSJI class will be built upon the sunpycube package of sunpy. It will require to create a subclass and abstract this subclass, for now sunpy will be the base class but it may change depending on future discussions. This will enable us to use different analysis tools for iris data using sunpy tools as base.

Some of the different analysis tools that are going to be implemented are -

* Visualisation of the current data with movies and images.
* Truncate the data using criteria applied to dimension(s) with a single command.
* Different calibration tools for the data.
* Implementing different analysis tools ([link](https://github.com/sunpy/irispy/wiki/List-of-Required-Desired-IRIS-Analysis-Tools-in-Python)).

Visualisation of IRISSJI using sunpycube here each frame represents a position in space, with solar-x and solar-y axis. This is just a initial testing animation- ![IRISSJI Plot](https://github.com/abit2/Irispy-plot-images/blob/master/IRISMap.png)]

Implementation of this two classes will enable users to manipulate and fit the data, select regions of interest, and visualise the data. This is the purpose of developing these classes.

After the two classes have been implemented with all the tools for analysis, an IRISObservation container class will to be developed to allow users to easily associate and analyse the co-temporal slit-jaw images and spectra.

### 6. Software packages to be used

``matplotlib``, ``astropy``, ``sunpy``, ``sunpycube``, ``xarray``, ``numpy``.

### 7. How I propose to complete this project

Since February, I have been working on IRISpy (the Python IRIS data analysis package) with its founders, Dan Ryan, Stuart Mumford, and Steven Christe.  I attend weekly development telecons with the IRISpy team and the IRIS instrument team and have thus become familiar with the compexity of the IRIS data, the current code base, and current dependencies, such as Xarray.  I have made contributions to the IRISpy repository, my PR's are ([#8](https://github.com/sunpy/irispy/pull/8)),([#7](https://github.com/sunpy/irispy/pull/7)),([#4](https://github.com/sunpy/irispy/pull/4)) the last two being tests for ``iris_tools`` and ``spectrograph``. The ([#8](https://github.com/sunpy/irispy/pull/8)) PR show my familiarity with the Xarray, this PR implements a tool that helps to truncate the data by it's axis, slice or index.

IRISpy can use Sunpy's already existing modules to implement different tools and functionalities.
The visualisation tools can use the ``sunpy.visualization`` package, the downloading of fits files can use ```sunpy.net``` package.  Additionally SunPy contains several useful tools for manipulating IRIS data, e.g. derotation. Meanwhile, the sunpycube package can be used as a basis for an IRISSJI object.

I will consult stackoverflow and the regular sources Google, Python docs etc for solving the pre-processing step.

### 8. Deliverables

IRISpy will have two basic data classes: IRISRaster and IRISSJI.  These will have different tools for visualisation (plotting, movies), tools for calibrating the data and tools to analyse and associate the coordinate system.
After the two classes have been implemented a IRISObservation class will be developed that will enable the user to associate the SJI image and spectra data.
A package that has tools that can help users to understand and do analysis of the IRIS SG and SJI data.

### 9. Benefits to The Community

There is increasing demand for Python support for IRIS data analysis.  Current software is written in the IDL language which requires expensive licenses which not everyone can afford.  Moreover, the younger generation of scientists are increasingly trained in Python rather than IDL.  It is therefore increasingly important to develop IRIS data analysis tools in Python to broaden the IRIS's user-base and add to the fascinating discoveries about the solar atmosphere already made using IRIS.  This is why the IRIS instrument team are supporting the IRISpy team with their advice and expertise on the workings of the instrument and the functionalities required by users.  However, the IRISpy effort is currently short of software developers. I would therefore play a crucial role making IRISpy a working, open source package.  Hence I will be playing a role in increasing our scientific understanding of the Sun and its atmosphere.

## 10. Timeline

Note: I will be writing documentation, tests and doctests along with writing the code for the module proposed in the project. This would make sure that mentors are able to understand my ideas lucidly, to ensure correctness and ease of maintainability. **I will be opening PRs regularly so that IRISPy/SunPy developers can review my code and provide valuable feedback and I will be pushing regularly to my own fork so that mentors can keep track of my progress.**

### 4th May - 30th May (Community bonding period)

Get more familiar with the IRISPy data. Read and understand the code of sunpycube package. Study how to approach the implementation of the IRISSJI and IRISRaster class, decide the best possible way. Discuss with the mentors on what functionalities and tools are to be implemented. Deciding the best possible way to start developing the IRISObservation.

If possible, I will also start coding in this phase, so that I get a head-start.

### 30th May - 26th June (4 weeks)

This part will deal with implementing of the IRISSJI class. I will initially be making the necessary changes in the sunpycube repository to support the development of IRISSJI class. This will deal with making a class that can read fits file and store the data with wcs and headers. The visualisation of data will be the next priority, sunpycube's visualisation tools can be used. Implementing different tools for this class, if there is functionality available in sunpy or sunpycube then the tool will be abstracted else the functionality will be developed by me.

Presently it will be implemented on sunpycube package, it may change depending on the future discussions.

The problem we are trying to solve is that there is a series of maps in a SJI file which requires a class that can store the wcs, meta and data, and also has necessary tools for analysis and visualisation. The IRISSJI class will solve this problem and enable users to do different operations like analysis and visualisation.

Making changes in the sunpycube (atmost 1 week). I think I will save 2-3 days here.

Making the class of IRISSJI with init and preprocessing the data and a few basic functions (1 week).

Implementing the tools for analysis like changing to physical units, calibration and truncting the data. The list of desired tools will be discussed with the mentors. (1 weeks).

Visualisation, animation and calibration tools. These will require some assistance from my mentors as visualisation seems to be a bit tricky to calibrate. (1 week)

### 26th June - 30th June (5 days, Phase 1 evaluation)

I will specifically concentrate on writing tests, documentation and fixing bugs.
I shall write documentation, examples and write tests for the functions and class that I have still to write for (I will mostly be writing tests, documentation and fixing bugs as I write them).

### 30th June - 24th July (3 weeks, 2 days)

Improving on the present code of IRISRaster class. This will involve implementing different tools for visualisation and analysis. This will involve implementing different functionalities like truncating data, plotting, making movies and having different calibration tools like residual wavelength calibration, converting DN to some physical units. The class is presently being implemented using Xarray, may change depending on the needs of the project to be discussed in the course of the project.
This will enable user to create the raster objects with raster files and make analysis on the data using the tools provided.

The wishlist of the functionalities for IRIS-Raster Object will include function that will enable users to truncate data and calibrate. The requirements of different tools will be given by the IRIS team in the ([link](https://github.com/sunpy/irispy/wiki/Requirements%5CWishlist-for-an-IRIS-Raster-Object)).

Improving on the present code like supporting the sit and stare observation (atmost 3-4 days, If we use the present code to develop).

Writing tools for calibration, tools to convert to physical unit, rotation. (8-10 days).

Visualisation and animation tools for analysis. This will require help of mentors to know if there is need for calibration.(9-10 days).

### 24th July - 28th July (4 days, Phase 2 evaluation)

Writing tests, documentation and fixing bugs. Discussing with mentors about the implementation of IRISObservation class, tools.

### 28th July - 21st August (3 weeks)

Developing the IRISObservation class. This will require to store both SJI and raster in this class.
It will be able to open 3 level fits files and enable users to view the data of his/her choice. This makes it possible to analyse slit-jaw images and spectra and explore there association. The approach of implementing this class has not yet been decided, the implementation details will be discussed in the future meetings and chats with the mentors.

Implementing a class to store the IRISSJI and IRISRaster object. Also able to open 3 level IRIS fits file. (10 days).

Developing tools and abstracting the already present functions of the IRISRaster and IRISSJI class.(3-4 days).

Developing the tools for associating and analysing the level 3 data. (1 week)

### 21st August - 29th August (1 week Students submit their final work product and their final mentor evaluation)

Clean up code, Improve documentation and resolve merge conflicts (if any)

### 29th August - 5th September (1 week)

Mentors submit final project reports to Google.

### 6th September

Final results of Google Summer of Code 2016 announced.

## 11. Commitments

I will be interning elsewhere from 10th May - July 10th. The office timings are from UTC 4:30 A.M - UTC 11:30 A.M. The time difference shouldn't be a problem, I will get off my internship when SunPy and IRISPy developers will wake up, so I can communicate with my mentors without any problems.
In the initial part of my project (Implementing the IRISSJI class) my familiarity with the Sunpy Maps and IRIS data helps me here. I have made two PR's to Map in Sunpy **(#1929, #1940)**. In the second part (Implementing the IRISRaster class) I am familiar with the present code and have added tests and corrected a few bugs in IRISPy PR's **(#4, #7)** and have started adding functionalities to the IRISRaster class in PR **#8**. My familiarity with the two classes should compensate here.

I will devote 5-6 hours during weekdays and during weekends 7-8 hours to the project. If required more time will be devoted to the project in the weekends. I will not be taking any vacations in summer. This way, I will be able to devote the required minimum of ~35-40 hours for Summer of Code.

I'm free after 10th of July and can devote time as I see fit after that.Having finished all discipline courses by end of this academic year, my academic stress will be extremely minimal.

During this entire summer I will have no issues for I have 24/7 access to high-speed internet and access to my work space.

* I have **not** participated in GSoC before.
* I am **not** applying to any other organisation except SunPy.
* I am **not** applying to any other projects.

## 12. Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanation of any approach/feature feel free to contact me at ankit.baruah1@gmail.com and I shall be happy to reply.
