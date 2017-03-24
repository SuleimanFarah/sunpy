### Organization: OpenAstronomy

### Sub-Organization: SunPy

### 1. Student Information

* Name: Ankit Baruah 
* Time  Zone: +0530 GMT
* IRC Handle: abit2 
* Github ID: [abit2](https://github.com/abit2)  
* Instant Messaging: Google Hangout (ankit.baruah1@gmail.com)  

### 2. Education
Currently, I'm a third year undergraduate enrolled in Computer Science & Engineering at Indian Institute of Technology, Kharagpur, West Bengal.
I would graduate in July 2018.

### 3. University Information
  
* University: [IIT Kharagpur, West Bengal](http://www.iitkgp.ac.in/)
* Major: Computer Science & Engineering
* Current year: 3rd
* Graduation date: July 2018
* Degree: Bachelor of Engineering (Honors)

### 4. Pull Requests
The following are the Pull requests, Issues (both open and closed) I contributed to.

* Added function to truncate the 3D cube with index, slice, and operation and or operation, the axis specifies
  the coordinate to truncate. Axis can be time/raster_position, slit_axis.
  ([#8](https://github.com/sunpy/irispy/pull/8))  
* Added tests for ``irispy/iris_tools.py`` as ``irispy/tests/test_iris_tools.py``and removed bugs in    ``irispy/spectrograph.py`` and ``irispy/iris_tools.py``. This increased the coverage of the project by +10.50%
  ([#4](https://github.com/sunpy/irispy/pull/4)).
* Added tests for ``irispy/iris_spectrograph.py`` as ``irispy/tests/test_iris_spectrograph.py``. This increased 
  the coverage of the project by +20.08% ([#7](https://github.com/sunpy/irispy/pull/7)).
* Added HDU index and test for ``sunpy/database/tables.py`` ([#1952](https://github.com/sunpy/sunpy/pull/1952)). Solves the issue of reverse mapping from DatabaseEntry -> HDU.
* Changes made to support the new NDData API by removing the old compatibility layer. Changes were made in ``sunpy/map/mapbase.py`` ([#1929](https://github.com/sunpy/sunpy/pull/1929)). This PR made the Map class which uses NDData as base class support the new API.
* Docs to make the user be able to see the custom meta keywords that are accepted, it will help when creating custom SunPy maps (i.e. from a 2D array). Changes were made in ``sunpy/map/mapbase.py``, ``sunpy/map/sources/hinode.py``, ``sunpy/map/sources/rhessi.py``, ``sunpy/map/sources/sdo.py``, ``sunpy/map/sources/soho.py``, ``sunpy/map/sources/stereo.py``, ``sunpy/map/sources/trace.py`` and ``sunpy/map/sources/yohkoh.py`` . ([#1940](https://github.com/sunpy/sunpy/pull/1940)).
* A helper function that would return the data and the header of that particular HDU. ``sunpy/database/database.py`` ([#1981](https://github.com/sunpy/sunpy/pull/1981)). This PR makes the reverse mapping from DatabaseEntry -> HDU possible.
* Changes made to ``sunpy/net/vso/vso.py`` , makes it possible for the VSOClient to check the online endpoint. ([#1916](https://github.com/sunpy/sunpy/pull/1916)). 
 
I use a Linux Ubuntu machine for development now and have been using it for the past 3 years. I am also familiar with Git, SunPy and IRISPy workflow.

### 5. Proposal abstract.

IRIS(Interface Region Imaging Spectrograph) mission's main goal is to understand energy transport in the sun's atmosphere. There are two modes in which IRIS operates; sit-and-stare at one location, or operate in a scanning mode, where the instrument rasters across the field of view, observing different spatial locations. There are two types of data produced SJI(Slit jaw Imager) and SG(Spectrograph). 
This would involve implementing 
* IRISRaster class(to read and anlyse IRIS spectra) and 
* IRISSJIMap (to read and analyse slit-jaw-images). 

The IRISPy will be developed as an affiliated package to Sunpy. The IRISRaster class would involve reading data from fits file and storing data in the IRISRaster object in a cubes where there are four dimensions spectral_axis, slit axis, raster_position or time (they are parallel to each other).

The IRISSJIMap will be built upon the mapcubed PR ([#1947](https://github.com/sunpy/sunpy/pull/1947)) of Sunpy. It would require to create a subclass and abstract this subclass, for now Mapcubed PR will be the base class but it may change depending on future discussions. This would enable us to use different analysis tools of sunpy if it already exists or develop our own.

Some of the different analysis tools that are going to be implemented are -
* Visualisation of the current data with movies and images.
* Truncate the data using criteria applied to dimension(s) with a single command.
* Different calibration tools for the data.
* Implementing different analysis tools ([link](https://github.com/sunpy/irispy/wiki/List-of-Required-Desired-IRIS-Analysis-Tools-in-Python)).

Visualisation of IRISSJIMap will look similar to - ![IRISSJIMap Plot](https://github.com/abit2/Irispy-plot-images/blob/master/IRISMap.png)]

Plot of IRISRaster's at a particular time or raster position will be - ![IRISRaster plot](https://github.com/abit2/Irispy-plot-images/blob/master/IRISRaster.png)

After the two classes have been implemented with all the tools for analysis, an IRISObservation container class needs to be developed to allow users to easily associate and analyse the co-temporal slit-jaw images and spectra. 


### 6. Software packages to be used:

``matplotlib``, ``astropy``, ``sunpy``, ``xarray``, ``numpy``.

### 7. How I propose to complete this project:

I have been working on IRISpy (which is the repository for the IRIS Data Class) with ([DanRyan](https://github.com/DanRyanIrish)) since late February 2017, before that I have contributed to Sunpy since October 2016. I have had a few teleconferences with Dan and Stuart(Cadair) and also one with the IRIS team where we discussed the possible solutions to the challenges of the complicated IRIS data. I have become familiar with the IRIS data, the present code of IRISRaster and the use of Xarray. I have made contributions to the IRISpy repository, my PR's are ([#8](https://github.com/sunpy/irispy/pull/8)),([#7](https://github.com/sunpy/irispy/pull/7)),([#4](https://github.com/sunpy/irispy/pull/4)) the last two being tests for ``iris_tools`` and ``spectrograph``. The ([#8](https://github.com/sunpy/irispy/pull/8)) PR show my familiarity with the Xarray, this PR implements a tool that helps to truncate the data by it's axis, slice or index.

IRISpy can use Sunpy's already existing modules to implement different tools and functionalities.
The visualisation tools can use the ``sunpy.visualization`` package, the downloading of fits files can use sunpy.net package, similarly different calibration, shift's and rotation tools can be used by the IRISpy to develop it's own tools.

If we move forward with the mapcubed class I will refer to the sunpycube repository code as it is implemented for quite similar data as IRIS.
I would consult stackoverflow and the regular sources Google, Python docs etc for solving the pre-processing step.
I have been working on IRISpy for a while and after having a conference with the IRIS team I have come to understand it's vision.



### 8. Deliverables

IRISPy(sunpy affiliated package) that would have two classes IRISRaster and IRISSJIMap. This would have different tools for visualisation (plotting, movies), tools for calibrating the data and tools to analyse and associate the coordinate system.
After the two classes have been implemented a IRISObservation class will be developed that will enable the user to associate the SJI image and spectra data.
A package that has tools that can help users to understand and do analysis of the IRIS SG and SJI data.


### 9. Benefits to The Community.

Currently, If users want to study about Solar events such as flares, energy distribution through the layers, how they are filtered through the atmosphere, then understanding the chromosphere and TR(Transition Region) is a foundational necessity for explaining the corona and heliosphere.
This would require the users to use IDL, which they find difficult use and understand, unlike the modern programming languages. The IRISpy would help users to quickly understand how to use and develop on the IRISpy package as most users are familiar with one or more modern programming languages.
Users can employ the abstracted tools to truncate, visualise and calibrate the data. This will prevent doing all this manually. This enables users to do better analysis without dealing with errors in code.
The support of different python packages that can help users develop their own analysis tools easily is a very useful advantage.

## 10. Timeline

Note: I would be writing documentation, tests and doctests along with writing the code for the module proposed in the project. This would make sure that mentors are able to understand my ideas lucidly, to ensure correctness and ease of maintainability. **I would be opening PRs regularly so that IRISPy/SunPy developers can review my code and provide valuable feedback. I would also be pushing regularly to my own fork so that mentors can keep track of my progress.**


### 4th May - 30th May (Community bonding period)

Get more familiar with the IRISPy data. More specifically look through and understand the implementation of ([ehsteve](https://github.com/ehsteve) Mapcubed PR ([#1947](https://github.com/sunpy/sunpy/pull/1947)). Study on how to approach the implementation of the IRISSJIMap class the best possible way. Discuss with the mentors on what functionalities and tools are to be implemented and different approaches to implement the different classes and choose the most efficient approach. Deciding the best possible way to start developing the IRISObservation. Making changes that are required in the mapcubed PR.

If possible, I would also start coding in this phase, so that I get a head-start.

### 30th May - 26th June (4 weeks)

This part would deal with implementing of the IRISSJIMap class. This would deal with making a class that can read fits file and store the data with wcs and headers. The visualisation of data would be the next priority where the use of sunpy map class functions will be used where all the visualisation tools will be abstracted. Implementing different tools for this class where if there is functionality available in sunpy then the tool will be abstracted else the functionality will be developed by me.
Presently it will be implemented on Mapcubed PR which has been merged in the IRISPy project, it may change depending on the future discussions.
The problem we are trying to solve is that there is a series of maps in a SJI file which would require a class that can store the wcs, meta and data, and also has necessary tools for analysis and visualisation. The IRISSJIMap class would solve this problem and enable users to do different operations like analysis and visualisation.

Implement IRISSJIMap (1 week)
Implement Visualisation and other tools for analysis (3 weeks)

### 26th June - 30th June (5 days, Phase 1 evaluation)

I would specifically concentrate on writing tests, documentation and fixing bugs.


### 30th June - 24th July (3 weeks, 2 days)

Improving on the present code of IRISRaster class. This would involve implementing different tools for visualisation and analysis. This would involve implementing different functionalities like truncating data, plotting, making movies and having different calibration tools like residual wavelength calibration, converting DN to some physical units. The class is presently being implemented using xarray, may change depending on the needs of the project to be discussed in the course of the project.
This would enable user to create the raster objects with raster files and make analysis on the data using the tools provided. 

There is a list of desired functionalities ([link](https://github.com/sunpy/irispy/wiki/Requirements%5CWishlist-for-an-IRIS-Raster-Object)) this desired requirements will be met.

### 24th July - 28th July (4 days, Phase 2 evaluation)

Writing tests, documentation and fixing bugs. Discussing with mentors about the implementation of IRISObservation class, tools.

### 28th July - 21st August (3 weeks)

Developing the IRISObservation class. This would require to convert the present 2nd level data to 3rd level data which will be storing the SJI and the SG data.
This would require this class to combine raster and SG data. It would be able to open 3 level fits files and  enable users to view the data of his/her choice. This makes it possible to analyse slit-jaw images and spectra and explore there association. The approach of implementing this class has not yet been decided, the implementation details will be discussed in the future meetings and chats with the mentors. 

### 21st August - 29th August (1 week Students submit their final work product and their final mentor evaluation)
Clean up code, Improve documentation and resolve merge conflicts (if any)

### 29th August - 5th September (1 week)
Mentors submit final project reports to Google. 

### 6th September
Final results of Google Summer of Code 2016 announced.

## 11. Commitments

I would be interning elsewhere from 10th May - July 10th. The office timings are from UTC 4:30 A.M - UTC 11:30 A.M. The time difference shouldn't be a problem, I would get off my internship when SunPy and IRISPy developers would wake up, so I can communicate with my mentors without any problems.
In the initial part of my project (Implementing the IRISSJIMap class) my familiarity with the Sunpy Maps and IRIS data helps me here. I have made two PR's to Map in Sunpy **(#1929, #1940)**. In the second part (Implementing the IRISRaster class) I am familiar with the present code and have added tests and corrected a few bugs in IRISPy PR's **(#4, #7)** and have started adding functionalities to the IRISRaster class in PR **#8**. My familiarity with the two classes should compensate here.
Nevertheless, I would be able to devote 6-7 hours on weekdays and as many as I want on weekends. This way, I would be able to devote the required minimum of ~35-40 hours for Summer of Code. 

I **won't** be multi-tasking, I would reserve 6-7 hours of uninterrupted time, every weekday (during the initial 8 weeks of my other internship) and program during that time (I would be entirely free on weekends, no hurdles there). Any extra time, if required would be devoted to Summer of Code.

I'm free after 10th of July and can devote time as I see fit after that.Having finished all discipline courses by end of this academic year, my academic stress would be extremely minimal.

During this entire interval I will have no issues for I have 24/7 access to high-speed internet and access to my work space.

* I have **not** participated in GSoC before.
* I am **not** applying to any other organisation except SunPy.
* I am **not** applying to any other projects.

## 12. Eligibility
Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanation of any approach/feature feel free to contact me at ankit.baruah1@gmail.com and I shall be happy to reply.
