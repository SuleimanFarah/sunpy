### Organization: OpenAstronomy

### Sub-Organization: SunPy

### 1. Student Information

* Name: Sudarshan Konge	
* Time 	Zone: +0530 GMT
* IRC Handle: Hieronymous	
* Github ID: [sudk1896](https://github.com/sudk1896)	
* Instant Messaging: Google Hangout (sudk1896@gmail.com)	
* Blog: [My Blog.](https://sudonymousblog.wordpress.com/)

### 2. Education
Currently, I'm a third year undergraduate enrolled in Computer Science & Engineering at Birla Institute of Technology & Science, Pilani, Hyderabad Campus.
I would graduate in July 2017.

### 3. University Information
	
* University: [BITS Pilani, Hyderabad](http://www.bits-pilani.ac.in/hyderabad/)
* Major: Computer Science & Engineering
* Current year: 3rd
* Graduation date: July 2017
* Degree: B.E(Hons.)

### Work and Open Source Experience.
The following are the Pull requests, Issues (both open and closed) I contributed to.

* Added test and fits file for ``HIMap`` ([#1598](https://github.com/sunpy/sunpy/pull/1598)). The title explains the contribution aptly.
* Preliminary version of ``Unified Downloader``/``Fido`` Docs ([#1623](https://github.com/sunpy/sunpy/pull/1623)). This PR dealt with compiling the documentation for Unidown, now affectionately called Fido.
* Fixed tests for ``EVE``,``GOES`` and ``LET`` ([#1667](https://github.com/sunpy/sunpy/pull/1667)). This PR dealt with fixing tests in ``/dataretriever/sources`` for ``EVE``, ``LET`` and ``GOES`` clients.
* Implemented ``XRT`` Client. ([#1652](https://github.com/sunpy/sunpy/pull/1652)). A preliminary ``XRT`` Client which can download ``XRT`` data. Some design issues have still not been discussed. It is in development.
* ``SWAPClient`` Implementation. ([#1680](https://github.com/sunpy/sunpy/pull/1680)). This is the implementation of SWAPClient along with tests. It is almost complete.
* Possible error in ``GOESClient``. ([#1692](https://github.com/sunpy/sunpy/pull/1692)). I raised an issue with the ``GOESClient`` implementation, highlighting an error in its logic. This PR rectifies it along with requisite tests.
* Raised an issue with the scraper in ``sunpy.util`` ([#1619](https://github.com/sunpy/sunpy/issues/1619). While testing a query for STEREO in ``Fido``, I reported an issue with the scraper.

I use a Linux Mint machine for development.

### Proposal abstract.
I intend to work on the project - Real time data access and visualisation tools. This would involve building an in-house SunPy module to get real time data from different sources , using ``Fido`` and build new clients for ones unavailable. Real-time archives are archives which provide current data and normal full-time archives provide historical (previous year,month etc) data. Custom Fido clients for the following [sources](https://docs.google.com/spreadsheets/d/1JizSdVKzKu_yFHXg4Bad5xcFREedcw7MhWwVto7L9kw/edit?pref=2&pli=1#gid=0) would also be implemented.
 Few of the features that this project aims to add to SunPy are,

* Overlay of Active Regions on top of Solar Images ([``Solar Monitor``](http://solarmonitor.org/)).
* GOES X-ray flux with Active Regions on the flares detected ([SolarSoft Latest Events](http://www.lmsal.com/solarsoft/last_events/)).
* Latest features observed available from HEK on top of a map ([isolsearch](http://www.lmsal.com/hek/hek_isolsearch.html)).

Specifically, Taking an example, We would first download latest, real-time SWAP data using a ``SWAPClient`` in ``Fido`` and download latest real-time data from [NOAA.gov](http://www.swpc.noaa.gov/products/solar-region-summary) and other sources for the text data about Regions with sunspots and H-alpha plages without spots. General purpose clients on the lines of ``Fido`` would be designed to obtain data for both. In this way, user can specify a time or a timerange and download  the required data. Then, once we have both the data, we would use a custom-made plot (make requisite changes to way Maps, LCs are plotted) to overlay the text/tabular data over the image and get plots similar to ![SWAP Plot](https://github.com/sudk1896/SunPy-plot-images/blob/master/swap_00174_fd_20160304_052101.png)]. In case of LightCurves, We would take GOES X-ray data from a ``Fido`` client that we would build (this would download fits data) and fetch data to get Active Regions number on the flares detected, to get a plot like this, Image courtesy - [David P.S.](https://github.com/dpshelio) - ![](https://github.com/sudk1896/SunPy-plot-images/blob/master/GOES_and_flares.jpg). GOES currently downloads only irradiance data, we would implement ``Fido`` client to download soft x-ray imager data and to fetch energy particles data.

I would divide this project nicely, in 2-3 modular parts. 

* Fetching and Downloading data. This would involve writing custom clients using ``Fido`` interface to download the fits data and write a similar client to download text/html data (from different sources).
* Pre-processing data. The data in form of text/html that we download, would not be in the format that we require. Most of the information is in form of tables which are garbled along with other unnecessary data that we don’t require. I would create a custom-made parser for each source which would extract the tables we want and we could then conveniently manipulate the tables using ``astropy.ascii`` . The parser would most probably be a part of ``sunpy.util``.
* Plotting. We would use ``matplotlib`` to overlay the data obtained from the table along with the fits data to create the plots.
Fetching and downloading data should be simple (due to ``Fido``). The main challenges that we would face is most probably in the second step of pre-processing data. Since every source would have its own way in which data is structured we would have to implement a parser with a custom logic for each source. We would use the ``Table`` provided in ``astropy.ascii`` to store the tabular data in the text/html files. Also, the different sources from which we would obtain textual/html data haven’t been decided so far. More might be scrapped/added in the future.

I would be adding the requisite documentation in form of doc-strings, clearly explaining the utility of the module. I am already familiar with the SunPy docs conventions, One of my PRs dealt with building documentation. If time permits, I would also add doc-tests. 

### Software packages to be used:
``matplotlib``, ``astropy``, ``beautifulsoup``(maybe),``scipy``

### How I propose to complete this project:
I have been contributing to SunPy since December. I spent the month of November lurking around the IRC and mostly getting to know about SunPy, by talking to Cadair. Upon my interactions, I came to infer, that among the major and current to-dos in SunPy, would be to integrate the ``unidown`` branch into master. It is time for ``Fido`` to come into limelight. I spent a lot of time studying the unidown code-base and getting to understand its functionalities. Most of my pull requests deal with ``Fido/unidown``. I am very comfortable/familiar with ``Fido`` now.
I would consult stackoverflow and the regular sources Google, Python docs etc for solving the pre-processing step. I would require the help of my mentor for plotting, since it is a bit subtle and does require a rudimentary understanding of a some minor Solar Physics details (Which parameters are required for overlaying data over maps and specific questions such as these).

### Deliverables
A visualization module which would mimic the functionality of [``SolarSoft latest events``](http://www.lmsal.com/solarsoft/last_events/) , [``Solar Monitor``](http://solarmonitor.org/) and similar entitiies. This would include a parser to parse html/text data, custom plotting functions to overlay the html/text data over Maps,LCs. We intend to build a seperate visualization module (like Fido, instr etc) which would provide a set of tools for drawing up the required plots. We would also implement all Fido clients listed [``here``](https://drive.google.com/open?id=1JizSdVKzKu_yFHXg4Bad5xcFREedcw7MhWwVto7L9kw), in total of about 9 clients.

### Benefits to The Community.
Currently, If users want to get information about Solar events such as flare information, active regions and ``ACE Real time Solar Wind data``, they would have to go to [``Solar Monitor``](http://solarmonitor.org/), [``Solarsoft latest events``](http://www.lmsal.com/solarsoft/last_events/) and other similar websites to get the requisite information. On top of it, to get plots between a particular time, a user would have to manually enter the timerange and navigate through the entire site, through pop-up style windows to see the interactive plots, something like this,![](https://github.com/sudk1896/SunPy-plot-images/blob/master/GOES-X-ray.png)

With this module, Users would have the option of either seeing the real-time(latest data) or querying for a specific time/timerange to the module, which would generate the plots for them (Yes, we are doing it ``Fido`` style). This would replace the need for SunPy users to explicitly use websites such as ``SolarMonitor`` and this would provide the base for the development of a full-fledged visualization tool within SunPy in the future. Which I aim to continue to contribute to.

### Timeline

Note: I would be writing documentation and tests along with writing the code for the module proposed in the project. This would make sure that mentors are able to understand my ideas lucidly, to ensure correctness  and ease of maintainability.

### 22nd April - 23rd May
Community bonding period. I would get familiar with the plotting aspects of the project and also study the different sources of data for which we would be writing our custom parsers.

### 23rd May - 20th June (4 weeks)
This part would deal with implementing all the Fido clients [``here``](https://drive.google.com/open?id=1JizSdVKzKu_yFHXg4Bad5xcFREedcw7MhWwVto7L9kw).
This would deal with implementing instrument-wise ``Fido`` clients. The list of instruments supported would be SWAP, XRT , GONG (Magnetogram, Intensity, FarSide, H-alpha), GOESClient for soft x-ray imager and energy particles which haven't been implemented yet, ACE Client , Global H-alpha Network Kanzelhohe bbso and SOLIS VSM.
Documentation and requisite tests would also be added.
* Implement SWAP, XRT clients, ACE Client (1 week)
* GONG (Magnetogram, Intensity, FarSide, H-alpha) and GOESClient (2 weeks).
* Global H-alpha Network, SOLIS VSM (1 week).

### 20th June - 27th June 
Mid-term evaluation. 
 