Goran Cetušić |  Short bio
------------- | -------------
![Avatar](https://github.com/gcetusic/gcetusic.github.io/blob/master/images/avatar.jpg) | My academic and programming career started with my enrollment as a Bachelor student at the Faculty of Electrical Engineering and Computing in Zagreb. During that time I've been involved in various activities like lecturing student courses, organizing events and projects, leading several of them as the section leader of the Electrical Engineering student club. I got my first job as a network administrator at a small firm and where I started to learn some real programming in Python. Before finishing my Bachelor studies, I got an internship position as an Openlab summer student at CERN where I worked on process accounting software for their batch cluster. After a year working as a Linux administrator and contributing to several open source projects, I'm now a dedicated Python and Django developer, juggling my responsibilities as a Masters student in Telecommunications and Informatics, currently working on my thesis on Linux network simulators and various other interests like machine learning and bioinformatics, often "wasting" my time on Coursera.
**Education**  | <a href="http://www.fer.hr"><img src="https://github.com/gcetusic/gcetusic.github.io/blob/master/images/fer.gif"></a> Faculty of Electrical Engineering and Computing, University of Zagreb <br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Telecommunication and Informatics, Master studies
**Contacts**  | <a href="mailto:goran.cetusic@gmail.com"><img src="https://github.com/gcetusic/gcetusic.github.io/blob/master/images/gmail-small.png"></a> <a href="https://github.com/gcetusic"><img src="https://github.com/gcetusic/gcetusic.github.io/blob/master/images/octocat-icon.png"></a>
**Curiculum vitae** | <https://github.com/gcetusic/gcetusic.github.io/blob/master/docs/gcetusic_en.pdf>

# The Programmer

A Linux enthusiast every since in 2006 someone installed Ubuntu on my laptop at a yearly Linux InstallFest. Since then I've taken over the organization of the same installfest for a couple of years and even organized and lectured two Linux courses at my college. After writing (mostly) bad C code in Gedit, I've switched to Python and Komodo Edit and it's been kind to me ever since. Except for that time when Komodo Edit deleted 300 lines of code...I'm using Sublime now, with all the benefits of its lint plugins.
***
After spending some time writing more bad code and making rookie mistakes, suddenly I realized I actually have something interesting to show to other developers. Python has served me well in this but I still have a lot to learn. For example, after doing web development for a couple of years, while trying to work around badly written Django code, I've implemented my own Python metaclass, probably the most abstract thing I've done in a programming language. Here are examples of some of the projects I've worked on (for a more complete list, please view my GitHub page, some are under NDA and closed sourced)

* <https://github.com/stormpath/stormpath-sdk-python/> - a flexible user managagement API
* <https://github.com/gcetusic/psacct-collector> - process accounting software developed during CERN internship
* <https://github.com/gcetusic/IMUNES> - a powerful network simulator

# <img src="https://raw.githubusercontent.com/sunpy/sunpy/master/doc/logo/favicon.ico"> The Project

### Lightcurve Refactor

The `Lightcurve` class is one of the three core datatypes in SunPy, along with Map and Spectra.
`Lightcurve` is designed to read in, process and store meta data related to solar physics time series data.
Currently, `Lightcurve` uses the pandas library as its underlying data structure, however, this is subject to change in the future.

Much like the `map` submodule, `lightcurve` needs to be able to read in various supported data formats (such as FITS, ascii and others in the future), store their meta data and give users Beginner and unified access to this metadata independently of the original source of the data.

As currently implemented (as of 0.5) the `lightcurve` module performs three core tasks:

1. Download the raw data
1. Read this data into a pandas dataframe
1. store the meta data obtained with the data.

As of the SunPy 0.6 release the first stage will be moved out of `lightcurve` and into the `net` subpackage as part of the [`UnifiedDownloader`](https://github.com/sunpy/sunpy/pull/1088) (name subject to change) Pull Request.
This leaves `lightcurve` in a similar position to `map` where the data acquisition is not part of the core data type and is managed separately.
Therefore, enabling the implementation of a factory class like `Map`
for the lightcurve module.
***
**Expected Outcomes**

1. Become familiar with the `UnifiedDownloader` code, if it has not been accepted into the SunPy codebase, complete the remaining tasks for this to be achieved.
2. Re-write any new lightcurve sources that were not included in the `UnifiedDownloader` code as sources for `UnifiedDownloader`.
3. Write a factory class for `lightcurve` similar to the `sunpy.map.Map` class. This class will be a generic constructor for `lightcurve` allowing the user to instantiate any one of the many subclasses of `GenericLightcurve` present in `sunpy.lightcurve.sources`. The API design for the factory class is here: <https://github.com/sunpy/sunpy-SEP/pull/6>
4. Design and develop a robust method of dealing with lightcurve meta data, which can handle joining different parts of timeseries from different files, each with their own meta data. (See [#1122](https://github.com/sunpy/sunpy/issues/1122))

## Timeline

##### Community Bonding period (27th April - 25th May)

* Getting more familiar with the codebase
* Defining specification for project
* Researching the physics behind sunpy and lightcurve

##### Week 1 (25th May - 31st May)

* Basic LightCurve class refactor and code cleanup
* Designing factory class for LightCurve

##### Weeks 2 and 3 (1st June - 14th June)

* Refactor of all sources related files

##### Week 4 (15th June - 21st June)

* Syncing sources refactor with UnifiedDownloader branch

##### Week 5 (22nd June - 28th June)

* Resolving LightCurve related issues on Github
* Evaluating, fixing and closing

##### Week 6 (29th June - 5th July)

* Midterm evaluation
* Resolving any design problems
* Maintenance and codebase improvements

##### Weeks 7 and 8 (6th July - 19th July)

* Dealing with merging of LightCurve metadata
* Fixing any showstoppers not caused by Lightcurve refactor

##### Weeks 9 and 10 (20th July - 2nd August)

* Removing pandas library from SunPy
* Implementing custom data storage structures

##### Week 11 (3rd August - 9th August)

* Buffer Period for completing any incomplete work
* Fixing any showstoppers not caused by Lightcurve refactor

##### Week 12 - Pencils Down Date (10th August - 16th August)

* Making sure there's good test coverage and documentation
* Final syncing of GSOC project (mostly merges)

##### Endterm Evaluation (17th August - 23rd August)

## Schedule information

During the first 4-5 weeks I would have to work on my masters thesis parallel to GSOC. It's my last year as a student and the deadline for turning it in is the end of June. Even though I would be able to devote at least 4 hrs a day during the period between the start of GSOC and the end of June I would start coding by the beginning of May (during the community bonding period) to get a head start.
