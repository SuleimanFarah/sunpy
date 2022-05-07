### Organization: OpenAstronomy

### Sub-Organization: SunPy

### 1. Student Information

* Name: Sudarshan Konge
* Time  Zone: +0530 GMT
* IRC Handle: Hieronymous
* Github ID: [sudk1896](https://github.com/sudk1896)
* Instant Messaging: Google Hangout (sudk1896@gmail.com)
* Blog: [My Blog.](https://sudonymousblog.wordpress.com/)
* RSS Feed: [RSS feed](https://sudonymousblog.wordpress.com/feed/)

### 2. Education

Currently, I'm a third year undergraduate enrolled in Computer Science & Engineering at Birla Institute of Technology & Science, Pilani, Hyderabad Campus.
I would graduate in July 2017.

### 3. University Information

* University: [BITS Pilani, Hyderabad](http://www.bits-pilani.ac.in/hyderabad/)
* Major: Computer Science & Engineering
* Current year: 3rd
* Graduation date: July 2017
* Degree: Bachelor of Engineering (Honors)

### 4. Pull Requests

The following are the Pull requests, Issues (both open and closed) I contributed to.

* Added test and fits file for ``HIMap`` ([#1598](https://github.com/sunpy/sunpy/pull/1598)). The title explains the contribution aptly.
* Preliminary version of ``Unified Downloader``/``Fido`` Docs ([#1623](https://github.com/sunpy/sunpy/pull/1623)). This PR dealt with compiling the documentation for Unidown, now affectionately called Fido.
* Fixed tests for ``EVE``,``GOES`` and ``LET`` ([#1667](https://github.com/sunpy/sunpy/pull/1667)). This PR dealt with fixing tests in ``/dataretriever/sources`` for ``EVE``, ``LET`` and ``GOES`` clients.
* Implemented ``XRT`` Client. ([#1652](https://github.com/sunpy/sunpy/pull/1652)). A preliminary ``XRT`` Client which can download ``XRT`` data. Some design issues have still not been discussed. It is in development.
* ``SWAPClient`` Implementation. ([#1680](https://github.com/sunpy/sunpy/pull/1680)). This is the implementation of SWAPClient along with tests. It is almost complete.
* Possible error in ``GOESClient``. ([#1692](https://github.com/sunpy/sunpy/pull/1692)). I raised an issue with the ``GOESClient`` implementation, highlighting an error in its logic. This PR rectifies it along with requisite tests.
* Raised an issue with the scraper in ``sunpy.util`` ([#1619](https://github.com/sunpy/sunpy/issues/1619). While testing a query for STEREO in ``Fido``, I reported an issue with the scraper.
* Added ``Fido`` test to all clients ([#1705](https://github.com/sunpy/sunpy/pull/1705)). The title is self-explanatory.

I use a Linux Mint machine for development now and have been using it for the past 3 years. I am also familiar with Git and SunPy workflow.

### 5. Proposal abstract

I intend to work on the project - Real time data access and visualisation tools. This would involve building an in-house SunPy module to get real time data from different sources , using ``Fido`` and build new clients for ones unavailable. Real-time archives are archives which provide current data and normal full-time archives provide historical (previous year,month etc) data. Custom Fido clients for the following [sources](https://docs.google.com/spreadsheets/d/1JizSdVKzKu_yFHXg4Bad5xcFREedcw7MhWwVto7L9kw/edit?pref=2&pli=1#gid=0) would also be implemented.
 Few of the features that this project aims to add to SunPy are,

* Overlay of Active Regions on top of Solar Images ([``Solar Monitor``](http://solarmonitor.org/)).
* GOES X-ray flux with Active Regions on the flares detected ([SolarSoft Latest Events](http://www.lmsal.com/solarsoft/last_events/)).
* Latest features observed available from HEK on top of a map ([isolsearch](http://www.lmsal.com/hek/hek_isolsearch.html)).

Specifically, Taking an example, We would first download latest, real-time SWAP data using a ``SWAPClient`` in ``Fido`` and download latest real-time data from [NOAA.gov](http://www.swpc.noaa.gov/products/solar-region-summary) and other sources for the text data about Regions with sunspots and H-alpha plages without spots. General purpose clients on the lines of ``Fido`` would be designed to obtain data for both. In this way, user can specify a time or a timerange and download  the required data. Then, once we have both the data, we would use a custom-made plot (make requisite changes to way Maps, LCs are plotted) to overlay the text/tabular data over the image and get plots similar to ![SWAP Plot](https://github.com/sudk1896/SunPy-plot-images/blob/master/swap_00174_fd_20160304_052101.png)]. In case of LightCurves, We would take GOES X-ray data from a ``Fido`` client that we would build (this would download fits data) and fetch data to get Active Regions number on the flares detected, to get a plot like this, Image courtesy - [David P.S.](https://github.com/dpshelio) - ![](https://github.com/sudk1896/SunPy-plot-images/blob/master/GOES_and_flares.jpg). GOES currently downloads only irradiance data, we would implement ``Fido`` client to download soft x-ray imager data and to fetch energy particles data.

I would divide this project nicely, in 2-3 modular parts.

* Fetching and Downloading data. This would involve writing custom clients using ``Fido`` interface to download the fits data and write a similar client to download text/html data (from different sources).
* Pre-processing data. The data in form of text/html that we download, would not be in the format that we require. Most of the information is in form of tables which are garbled along with other unnecessary data that we don’t require. I would create a parser with a separate logic for each source which would extract the tables we want and we could then conveniently manipulate the tables using ``astropy.ascii``.
* Plotting. We would use ``matplotlib`` to overlay the data obtained from the table along with the fits data to create the plots.
Fetching and downloading data should be simple (due to ``Fido``). The main challenges that we would face is most probably in the second step of pre-processing data. Since every source would have its own way in which data is structured we would have to implement a parser with a custom logic for each source. We would use the ``Table`` provided in ``astropy.ascii`` to store the tabular data in the text/html files. Also, the different sources from which we would obtain textual/html data haven’t been decided so far. More might be scrapped/added in the future.

I would be adding the requisite documentation in form of doc-strings, clearly explaining the utility of the module. I am already familiar with the SunPy docs conventions, One of my PRs dealt with building documentation. If time permits, I would also add doc-tests.

### 6. Software packages to be used

``matplotlib``, ``astropy``, ``beautifulsoup``(maybe),``scipy``

### 7. How I propose to complete this project

I have been contributing to SunPy since December. I spent the month of November lurking around the IRC and mostly getting to know about SunPy, by talking to Cadair. Upon my interactions, I came to infer, that among the major and current to-dos in SunPy, would be to integrate the ``unidown`` branch into master. It is time for ``Fido`` to come into limelight. I spent a lot of time studying the unidown code-base and getting to understand its functionalities. Most of my pull requests deal with ``Fido/unidown``. I am very comfortable/familiar with ``Fido`` now.
I would consult stackoverflow and the regular sources Google, Python docs etc for solving the pre-processing step. I would require the help of my mentor for plotting, since it is a bit subtle and does require a rudimentary understanding of a some minor Solar Physics details (Which parameters are required for overlaying data over maps and specific questions such as these).

### 8. Deliverables

A visualization module(like net,instr etc) which would mimic the functionality of [``SolarSoft latest events``](http://www.lmsal.com/solarsoft/last_events/) , [``Solar Monitor``](http://solarmonitor.org/) and similar entities. This would include a parser to parse html/text data, custom plotting functions to overlay the html/text data over Maps,LCs. We intend to build a separate visualization module (like Fido, instr etc) which would provide a set of tools for drawing up the required plots. We would also implement all Fido clients listed [``here``](https://drive.google.com/open?id=1JizSdVKzKu_yFHXg4Bad5xcFREedcw7MhWwVto7L9kw), in total of about 8-9 clients.

### 9. Benefits to The Community

Currently, If users want to get information about Solar events such as flare information, active regions and ``ACE Real time Solar Wind data``, they would have to go to [``Solar Monitor``](http://solarmonitor.org/), [``Solarsoft latest events``](http://www.lmsal.com/solarsoft/last_events/) and other similar websites to get the requisite information. On top of it, to get plots between a particular time, a user would have to manually enter the timerange and navigate through the entire site, through pop-up style windows to see the interactive plots, something like this,![](https://github.com/sudk1896/SunPy-plot-images/blob/master/GOES-X-ray.png)

With this module, Users would have the option of either seeing the real-time(latest data) or querying for a specific time/timerange to the module, which would generate the plots for them (Yes, we are doing it ``Fido`` style). This would replace the need for SunPy users to explicitly use websites such as ``SolarMonitor`` and this would provide the base for the development of a full-fledged visualization tool within SunPy in the future.

## 10. Timeline

Note: I would be writing documentation, tests and doctests along with writing the code for the module proposed in the project. This would make sure that mentors are able to understand my ideas lucidly, to ensure correctness  and ease of maintainability. **I would be opening PRs regularly so that SunPy developers can review my code and provide valuable feedback. I would also be pushing regularly to my own fork so that mentors can keep track of my progress.**

### 22nd April - 23rd May (Community bonding period)

Get familiar with the plotting aspects of the project. More specifically look through and understand [David P.S's](https://github.com/dpshelio/smpy) implementation of overlaying data over Maps to get Active Regions' numbers. If Unidown still hasn't been merged into master, work on it to do so. Study different sources of data for which custom parser logic would be written. Decide different approaches to store the tabular data (from the parsers), like ``astropy.ascii`` vs python dict. Investigate alternatives and choose the most efficient. Discuss with mentor about how the API/Interface for the visualization module would look like.

### 23rd May - 20th June (4 weeks)

This part would deal with implementing all the Fido clients [``here``](https://drive.google.com/open?id=1JizSdVKzKu_yFHXg4Bad5xcFREedcw7MhWwVto7L9kw).
This would deal with implementing instrument-wise ``Fido`` clients. The list of instruments supported would be SWAP, XRT , GONG (Magnetogram, Intensity, FarSide, H-alpha), GOESClient for soft x-ray imager and energy particles which haven't been implemented yet, ACE Client , Global H-alpha Network Kanzelhohe bbso ,SOLIS VSM and STEREO clients for SECCHI, euvi, cor2, hi_1 and hi_2 instruments. The basic problem that we are trying to solve here is this, There are multiple sources of data and we need to fetch data which is real or near real time, taking the hypothetical example, SWAP has two sources of data [PROBA2](http://proba2.oma.be/swap/data/bsd/) and [VSO](http://sdac.virtualsolar.org/cgi/search) (VSO currently doesn't support SWAP),just for example's sake, So we need to decide which source to query for the required real-time data. There may be multiple sources of data, our ``Fido`` clients, clever as they are, would decide which one to select, to obtain the latest/(near)real-time data.
Documentation and requisite tests would also be added.

* Implement SWAP, XRT clients, ACE Client (1 week)
* GONG (Magnetogram, Intensity, FarSide, H-alpha) and GOESClient (2 weeks).
* Global H-alpha Network, SOLIS VSM (1 week).

### 20th June - 27th June (1 week, Mid-Term evaluation)

Implement STEREO clients for SECCHI, euvi, cor2, hi_1 and hi_2 instruments.

```
davidps: Are you not doing anything this week?

Hieronymous: I thought mid-term review week was supposed to be empty, my mistake, I have shifted the timeline a bit now.
```

### 27th June - 18th July (3 weeks)

Write a generic parser, to get text/tabular data for SWPC and other sources. This parser would enable users to parse/mine the requisite data regarding Active Regions, electron flux etc in the form of some suitable data structure ,``astropy.ascii Table`` or a simple ``Python dict``. To be discussed and investigated over the course of the project. The more efficient one would be selected. Currently only one source has been decided - [Solar Region Summary](http://www.swpc.noaa.gov/products/solar-region-summary), more will be added in the future. This parser would be a part of ``sunpy.util``.

The undecided (ones to be added later on) sources would present a challenge, since we might end up parsing html pages instead of normal text files, the process of extracting data from an html page is different from that of a normal text file (I would have to use ``beautifulsoup`` for an html page).

```
davidps: AIA or HMI won't provide data in ascii format.
You could just say other sources.
```

### 18th July - 15th August (4 weeks)

Implement the plotting part of the project. This would deal with delivering the final three products of the idea

* Overlay of Active Regions on top of solar images. ( 2 weeks)
* GOES X-ray flux with active regions number on the flares detected (1 week)
* latest features observed available from HEK on top of a map (1 week)
This part would deal with overlaying the tabular data that we obtained from the parser over the corresponding solar images to produce the plots proposed. Custom plotting functions would be built for getting each type of plot.

I'm already looking into [David P.S. 's](https://github.com/dpshelio) implementation of [Solar monitor batch](https://github.com/dpshelio/smpy), this module overlays Active Region numbers on SunPy Maps. I wouldn't base my work on this module, but it would help me understand how to overlay the text/tabular data over Maps, LCs to get the plots we want. It is very rudimentary, I would have to understand how plotting works (specifically how SolarMonitor plots the way it does) and how to integrate our meta-data (from the tables) and add requisite features (AR numbers etc) to the plot. This would also involve the use of ``Fido`` and the parser we built, I would ensure both of them work correctly for this to function in the intended way. The tests for this module would involve making sure ``Fido``, the parser and the plot functions, all of them work fluidly, in the intended way to get our required plots.

```
DavidPS: Do you foresee any difficulty that you will have to overcome
         in these 4 weeks? Viusalisation is normally easy to do, but
         hard to make it look perfect. Think on things that makes you
         dedicate 4 weeks for this task and not just 4 days and tell
         us about it.
```

### 15th August - 23rd August (1 week)

The final week. Would clean up code (make it PEP8 compliant), docs, fix/add tests if required. This can also serve as a buffer week and work on adding support for Helio-Hfc could also be added (on discussion with mentor).

### 23rd August - 29th August (1 week)

Mentors submit final project reports to Google.

### 30th August

Final results of Google Summer of Code 2016 announced.

## 11. Commitments

I would be interning elsewhere from 30th May - July 18th. The office timings are from UTC 4:30 A.M - UTC 11:30 A.M. The time difference shouldn't be a problem, I would get off my internship when SunPy developers would wake up, so I can communicate with my mentors without any problems. The initial part of my project (Implementing Fido clients during this period) is something I have familiarity with, having 2 PRs already related to them **(#1680, #1652)**. My familiarity with Fido/Unidown should compensate here. Nevertheless, I would be able to devote 6-7 hours on weekdays and as many as I want on weekends. This way, I would be able to devote the required minimum of ~35-40 hours for Summer of Code.

I **won't** be multi-tasking, I would reserve 6-7 hours of uninterrupted time, every weekday (during the initial 6 weeks of my other internship) and program during that time (I would be entirely free on weekends, no hurdles there). Any extra time, if required would be devoted to Summer of Code. Upon discussions with the mentor, I have decided that this amount of time would be **more than sufficient** to meet the deadlines comfortably. Again, my familiarity with Fido helps me in this case.

I'm free after 18th of July and can devote time as I see fit after that. My classes begin from first week of August, it would be my final year. Having finished all discipline courses by end of this academic year, my academic load would be extremely minimal.
I don't have any logistical issues, I have 24/7 access to high-speed internet and won't be travelling anywhere during the internship period.

* I have **not** participated in GSoC before.
* I am **not** applying to any other organization except SunPy.

## 12. About Me

Hello there, I'm Sudarshan, I go by the nick Hieronymous on IRC. I'm currently in my pre-final year of under-graduate studies. I'm pursuing a Bachelors degree in Computer Science from [BITS Hyderabad](http://www.bits-pilani.ac.in/hyderabad/).

My interests are programming, problem-solving, algorithms and very recently Open Source. My introduction to programming was rather late. I started programming for the first time in my life, in my first year of college. And it was in Python, a happy co-incidence. I remember having read ``Python for Scientists - O'Reilly`` and having totally fallen head over heels for the almost prosaic and pseudo-code like syntax of Python. I also program and am fairly proficient in C++, although I use it only for algorithmic problem solving.

My interest in Open Source is rather recent. I started contributing regularly from December'15. I liked hanging around on the IRC, trying to get to know SunPy's mission, better. I'm fascinated by how Software Engineering forms the very backbone of SunPy and how proficient and better the SunPy developers are at programming than me, when software engineering isn't even their job, I have lots to learn!
The thing I like most about Python is how easily you can hack/prototype things, with such smooth ease. Interning with SunPy would strengthen my skills in Python and also make me a better developer.

When I’m not programming, I [read](https://www.goodreads.com/user/show/38044206-sudarshan) and also lift weights in the gymnasium. I lift 3 times a week in the mornings.

## 13. Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanation of any approach/feature feel free to contact me at sudk1896@gmail.com and I shall be happy to reply.

```
DavidPS: Pay attention in some capitalisation of some words and
         check the PDF looks good before uploading.
         For the rest the application looks very good.
         Good luck!
```
