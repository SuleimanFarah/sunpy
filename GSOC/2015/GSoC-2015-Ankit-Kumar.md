### Sub-organization: SunPy

### 1. Student Information

* **Name:** Ankit Kumar
* **Time Zone:** +0530 GMT
* **IRC Handle:**
* **Github ID:** ankitkmr
* **Instant Messaging information:** Google Hangout (ankitkmr.iitk@gmail.com)
* **HomePage:** <http://home.iitk.ac.in/~ankitkmr/>
* **Blog:** <http://home.iitk.ac.in/~ankitkmr/blog/>
* **Blog RSS:**  <http://feed43.com/sunpygsoc2015.xml>

***

### Education

I completed my primary and secondary education from Delhi Public School, Maruti Kunj [April 1997 - March 2010]. Some of the teachers in School were really amazing. They would show videos, organize discussion sessions, lab demonstrations and what not! They made studying real fun. From their I went to Delhi Public School R.K Puram for my Senior High School.

Currently, I am a third year undergraduate studying Materials Science and Engineering at Indian Institute of Technology, Kanpur. I will graduate from here in April, 2016.

### 2. University Information

* **University:** Indian Institute of Technology Kanpur
* **Major:** Material Science and Engineering
* **Current Year:** Third Year
* **Expected Graduation Date:** 2016
* **Degree:** Bachelor of Technology (B.Tech)

### 3. Some of my bragging rights:

* Secured **All India Rank 5112** among more than 5,20,000 students in IIT-JEE 2012
* Was among **top 1%** in All India Engineering Entrance Examination 2012
* Awarded the prestigious **Kishore Vaigyanik Protsahan Yojna(KVPY)** fellowship by the Department of Science and Technology,Government of India in the year 2012

### 4. Work and Open Source Experience:

Although I haven't really had much experience contributing to Open source Projects, I have extensive experience in developing projects implementing scientific and mathematical ideas by using Python and its Libraries.

* I built a set of scripts that used panda, numpy, scipy, matplotlib, QSTK to perform algorithmic trading, price-timeseries chart plotting. [Algo_Trading](https://github.com/ankitkmr/Algo_Trading_Software)

* I also  implemented a grain strain measurement software based on Electron BackScattering Diffraction (EBSD) maps last semester using Python, numpy, scipy and matplotlibs for my Mechanical Properties Lab. It would read in grain data from EBSD files, store them and correlate them to data points in second EBSD file, recognize closed grains and calculate grain strain [Grain Strain Measurement](https://github.com/ankitkmr/Grain_Strain_Measurement)

* In Current semester as well I am heading the development of SaaS project, a cloud based extractive metallurgy simulation by using Python for module development of all the ore processing units, Bootstrap for frontend and Python web micro-framework flask for backend. [Extractive Metallurgy (currently being developed this semester as part of a course)](https://github.com/ankitkmr/Extractive_Metallurgy)

You may find my software source code here: <https://github.com/ankitkmr>

Apart from the above projects, I am also proficient in C/C++ and have done quite a lot of sport programming.

**Operating System Experience:** Currently, I use Mac OSx. Also I have used Ubuntu and Windows for a few years back.

***

### 5. Sunpy - Support for analysis of Solar Energetic Particles

### 6. Proposal Abstract:
The SEP data is typically available as plaintext files with header information, with columns representing energies and particle elements, while the rows represent time. Also CDF files are used in some occasions. This projects implements a common class SEPLightCurve and implements three subclass (ERNELightCurve, ACELightCurve, STEREOLightCurve) of this class for the three type of instruments that provide SEP data.This project then reads in SEP data as a lightcurve object and allows to perform the basic operations specified in sunpy.instr for given new instruments, when the data is analysed. It also allows various visualization and comparison methods using python libraries such as scipy, numpy, matplotlib, datetime and also pandas dataframe. These basic operations include:

* Visualisation as time series, including changing the time or energy resolution. The SEP observations often suffer from low count-rates, and averaging over energy or time is needed.

* Visualisation as energy spectrum. Combination of energies and integration over time is important also in this case.

* Visualisation of intensity ratios of different particle species. These ratios and their energy- and time-dependence is important for understanding the mechanisms behind the SEP acceleration for different SEP events.

* Ability of comparing the SEP observations with other light-curve type data, such as X-ray and in-situ observations (magnetic field and solar wind propecties near the spacecraft).

Towards the end it also adds capability for solar event recognition and response for few popularly monitored solar events.

### 7. Software packages to be used

* **Language:** Python
* **Libraries and modules:** pandas, datetime, scipy, numpy, matplotlib

### 8. How I will successfully complete the project:

I consider myself a quick learner who finds ways out of difficulties. I have been an active user of Stack Overflow in the past and know where to go for various programming related questions. Having selected a project that both fits my skill set and excites me very much, I am confident to complete it on time. Also the fact that I have had done various projects in the past requiring similar nature of working with pandas timeseries and visualizations, I have a good grasp on the implementation intricacies of this project.

I will work on the project regularly and update mentors with my status as well as discuss further plan of action regularly. I will also push code on github on a regular basis. Also I will ensure that my commit messages and comments are insightful to any future reader of my code.

I will spend some time on the project before the coding period begins so that I can start being productive as soon as coding period begins. I have started understanding the structure of LightCurve, UnifiedDownloader. I'll spend more time on it once it has been updated more in future. I will fully understand it and experiment with it before the coding period begins. I'll also remain available for any queries regarding my code well after successful completion of project.

### 9. Deliverables

* SEPLightCurve class in lightcurve module
* ERNELightCurve, ACELightCurve and STEREOLightCurve as a subclass of SEPLightCurve
* Analytical Tools to analyze the data downloaded from the above three instruments.
* A Suite of interactive and Intuitive Visualization methods to visualize and compare SEP data with various other solar weather parameters
* Solar Event Recognition and Response Capability

### 10. Benefits to Community
In this age, everything we do and everywhere we go we remain connected. Connected to world, to our data, to public data and to the community at large. This connectedness is a result of the hundreds of satellites orbiting the Earth, constantly being exposed to solar weather, its phenomenon and components.

Solar Energetic Particles (SEPs) are accelerated during solar eruptions up to relativistic energies. They propagate from the Sun to the heliosphere, and arriving near Earth they pose a danger to astronauts and spacecraft and satellites. Thus, it is important to understand their acceleration and propagation mechanisms, so that we can mitigate the Space Weather risk they pose.

SEPs are observed with several instruments onboard several spacecraft, such as GOES, SOHO, ACE, and the two STEREO spacecraft. The timing and evolution of the SEP observations are compared to observations of solar X-ray and radio bursts, changes in solar magnetic field and EUV observations, and coronagraphs, and to the solar wind and magnetic field properties at the observing spacecraft. However, while many of these other observations can already be accessed with SunPy, **there is as of now no tool to analyze the SEP observations.**

### 11. Proposal Detailed Description/Timeline:

**The approximate timeline I planned :** (To estimate the amount of work that can be done in summers though it may change during the project [based on advice from mentors])

**NOTE:** Official Documentation writing, Testing and test additions for all the code written will be done along with code development to ensure consistency, semantic and functional correctness.

**{27 April - 25} May Community Bonding Period**

**Pre-Work:**

Read documentation and development guide, practice examples and get familiar with lightcurve module, sunpy.instr.goes, sunpy.lightcurve.sources.goes file, Unified Downloader PR, Maps class. Get the final idea about approach.
Discuss and create a list of each ‘X' vs ‘Y' visualization to be implemented during the project and sort out project implementation and additional feature that should be added after thoroughly discussing it with mentor.

**I  {25 May - 21 June} ( 4 weeks) (This I believe will be the bulk of the initial task and might take unto a month or so)**

Read in SEP data as light curve object from the remote plaintext file or CDF file for the given time range from the given of the possible instruments - SOHO/ERNE, ACE, STEREO, GOES .

This would mean implementing instrument-wise (ACE, STEREO, SOHO/ERNE) subclass of SEPLightCurve subclass of LightCurve class and implementing import methods for import of Data from the respective remote-files/URLs for all the different instruments in their respective sunpy.lightcurve.sources module  eg SOHO/ERNE, Stereo, ACE.

As of now the lightcurve class reads in data and stores it as pandas.DataFrame type so we can assume to read in data and convert it to pandas.DataFrame.

* Implement ERNELightCurve in sunpy.lightcurve.SEPlightcurve.sources.ERNE  **( 2 weeks)**
* Implement ACELightCurve in sunpy.lightcurve.SEPlightcurve.sources.ACE    **( 1 week )**
* Implement STEREOLightCurve in sunpy.lightcurve.SEPlightcurve.sources.STEREO **( 1 week )**

{26 June - 3 July }  Mid Term Evaluation

**II  {22 June -  9 July} (2.5 weeks)**

Correspondingly add the analytical functions to sunpy.instr module for each of the three new instruments that'll help analyze the data retrieved from the instrument. Also goes.py might need some new analyzing functions (thats up for discussion with mentor later)

* add analytical functions to sunpy.instr module for analyzing data from above three instruments

* First set of visualizations: Implement Visualization of data as Time Series e.g. Number of Particles belonging to a particular energy channel vs Time. Implementing event-handling/interactivity features in matplotlib plots. Implement averaging option of data for plots and also curve fitting (optional) of plot to assist data plot coherence during plot resolution change.

Add more possible simultaneous plots of data available from different sources.

matplotlib, scipy, DataFrame.plot(), datetime, matplotlib.axes.Axes for interactive resolution changing and zooming and panning of plots

**III {9 July -  15 July} ( 1 weeks)**

Second Set of Visualization: Implement Visualization as Energy Spectrum i.e number of particles vs energy. Implement feature to plot number of particles corresponding to particular energy bin (user defined widths ) vs energy bins. This I suggest to implement using two approaches: i) Simple plot and ii) Histograms (useful in case of non-uniform energy bin width)
The channels are usually more or less logarithmically spaced. This could be improved by taking into account the spectrum in the weighing and calculating also the weighted energy point. So implement channel energy-bin-width weight calculations.

Again curve fitting for plot coherence and curve integration feature for calculating total energy flux etc using scipy can be added.

scipy, matplotlib

**IV {16 July - 29 July }(2 weeks)**

Implement Compatibility in data download with Unified Downloader. Also make SEPLightCurve data querying and fetch conform to UnifiedDownloaderFactory class methods. But I plan to do this after mid term evaluation date and till then wait for more changes that may come to it.

**V  {29 July - 4 August} (1 weeks)**

Third Set of Visualization: Implement Visualization of elemental intensity ratios (with respect to user selected intensity) i.e Intensity ratio plot of particles of particular energy vs time. Implement more features revealing energy- and time-dependence of data.

**VI  {5 August - 11 August }(1 weeks)**

Time Series visualization of SEP data vs other data. e.g. Xray, Solar Wind Properties, Magnetic Properties. In case of more types of data visual comparisons in addition to the list decide in the beginning, will be decided after discussion with mentor during this time.

**VII  {12 August - 17 August} (In case I end up completing before the deadlines and time permits)**

I'd like to suggest/add a new feature. (This will be optional and added with further discussion with mentor):

Event Recognition and Response Mechanism : I plan to at least start the development of events recognition and corresponding response for a few sample popularly monitored events in the solar weather.

The approach here is to not just build tools but build features for a larger system sunpy.  A long shot might be developing a registeration mechanism where we can register for events. But a more realistic would be direct implementation for recognition of and response to a few popularly monitored events so that they can be recognized and responded to appropriately.

**17 August:  Suggested 'pencils down' date. Take a week to scrub code, write tests, improve documentation, etc.**

**{17 August - 21 August }( 1 week ):**

Make sure that the tests are holistic, documentation complete and code well structured and organized.

**21 August: Firm 'pencils down' date. Mentors, students and organization administrators can begin submitting final evaluations to Google.**

**28 August: Final evaluation deadline**

### 12. Link to a patch/code sample:

I patched SunPy issue **[#798](https://github.com/sunpy/sunpy/issues/798)** : Pandas dataframe values return as numpy.datetime64 objects in local time zone. parse_time does not understand these objects.

My PR is here **[PR #1344](https://github.com/sunpy/sunpy/pull/1344)** : Adds support for numpy.datetime64 and strings with timezone info. Some details about my PR :-

* It added support for to parse time_string of type numpy.datetime64 in parse_time function.
* It also added support for parsing time_string of type string with timezone information attached in the end in parse_time function
* I also added test cases for my patch in the test_time.py file in accordance with sunpy development guide.

It is yet to be merged.

***

### 13. Motivation:

I have always been interested in astronomy, solar systems, planets. To add to interests, Physics and Programming have always been my favorite subjects. Physics because it helps me to understand the world around me through an objective thought system and Programming because it is empowering. I was introduced to programming in my first year of college and software development in my third semester. I took an online course that semester which taught Algorithmic Trading and it involved writing scripts which interacted with data in different files, manipulated it and presented it in different forms. I had already learnt Python the previous summer and applying it in this completely non-convention way ( and the ease with which I could do it) blew my mind. That is where I can point and say that I loved Python and Development. It helped me to build tools for all the amazing scientific theories that I had read and actually use them. That was amazing. I also ended up making a few python games using simplegui as a part of online course offered by Rice University. And It was cool to have my friends/blockmates to play the pingpong game that I coded. Oh I can't tell how awesome I felt back then !! And as it was I ended up doing all my major development projects afterwards in Python only.

### 14. Schedule:

I do not have any other internship or involvements(and I am not planning to have any) for the Summer 2015. I may go on vacation (for 3-4 days) but that will be either before the coding period begins or after the coding period ends. In case it clashes with the coding period, I'll ensure that I complete that weeks work in advance before going away (which won't be for more than a week in any case)

I have classes during last two weeks of coding period but since the academic load is very less in the beginning of semester, I will be able to spare at least 30-35 hours for the project per week. Also, to be on a safer side, I will begin early (Since our institute summer vacation starts from 1 May) and try to complete the project around 1-3 weeks before the deadline.

Also I haven't applied to any other organization except SunPy.

### 15. Eligibility:
Yes, I am eligible to receive payments from Google.
For any queries, clarifications or further explanation of any approach/feature feel free to contact me at **ankitkmr.iitk@gmail.com** and I shall be happy to reply.
