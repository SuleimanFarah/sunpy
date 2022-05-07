# Project: Add Time-dependent Instrument Response Function to IRISpy

Name: Kris Akira Stern

Affiliation: The Laboratory for Space Research (LSR) & the Department of Physics, University of Hong Kong (HKU)

Organization: Open Astronomy (Sunpy)

## Personal information

Time-zone: Hong Kong Standard Time (GMT+8)

Email: krisastern@gmail.com

Web site: <https://kakirastern.github.io/>

Realtime chat handle@protocol: krisastern@riot

github id: kakirastern

Link(s) to sample code as pull requests:

* Add Real World Coordinates from Sliced Out Axes of WCS to Extra_coords:
<https://github.com/sunpy/ndcube/pull/151>
* Set http user-agent when running Travis CI and AppVeyor: <https://github.com/astropy/astroquery/pull/1394>
* Add SDSS image cutout query tool: <https://github.com/astropy/astroquery/pull/1383>
* Update layout.html file in sphinx to add top menubar to astropy docs: <https://github.com/astropy/astropy-sphinx-theme/pull/4>
* To add top menubar to Astropy docs webpages: <https://github.com/astropy/astropy/pull/8440>
* Debug navbar code to fix logo broken link: <https://github.com/astropy/astropy-tutorials/pull/333>
* Try and add filter search warning when no results is returned: <https://github.com/astropy/astropy-tutorials/pull/344>
* Add MatImageWidget as preliminary work using Matplotlib as a backend: <https://github.com/astropy/astrowidgets/pull/77>

## Education

I am currently a PhD student pursuing her studies in the field of observational astrophysics at the University of Hong Kong (HKU). Previously, I have obtained my BSc degree in physics from the Chinese University of Hong Kong (CUHK) in 2012, and my MPhil degree in particle physics at the Hong Kong University of Science and Technology (HKUST) in 2016. My current research focus is mainly on late-state stellar evolution, with an emphasis on planetary nebulae (PNe). For my PhD studies, I rely on Python heavily for data reduction, analysis, and visualization. During my undergraduate years, my primary scientific programming languages were Fortran and some C/C++. Serendipitously, I started using Python after taking a Massive Open Online Course (MOOC) course offered by MIT during my master’s degree intended for personal enrichment, and have been a devoted user of this versatile computing language ever since.

## Interest in Open Astronomy

I am drawn to working with Open Astronomy, with Sunpy in particular, initially due to its relevance to my current studies in observational astrophysics. But of late I have taken a keen interest in volunteering my time to contribute to Open Astronomy and its sub-organizations on a regular basis, since around January 2019, originally to give back to the Open Astronomy I owe so much personal debt to due to my heavy reliance on it for my research. My interests grew ever since, and I would like to devote more of my time to help improving Open Astronomy by becoming a GSoC student, with the added bonus of being mentored by dedicated software developers who are experts in the field. In this way, I aim to improve in my coding skills and to broaden my computer programming knowledge which would surely be accelerated with professional and qualified guidance. I desire to contribute to Open Astronomy, Sunpy and its affiliates in particular, on a long term basis if circumstances allow. Moreover, this is the first time I apply to GSoC.

## Summary of proposal

This project is about adding a very practical functionality to the IRISpy package, which is built on top of Sunpy’s ndcube package. IRISpy provides functionality for the analysis of observations from NASA's Interface Region Imaging Spectrograph (IRIS) satellite which looks at the UV emission from the solar chromosphere. IRIS is a NASA Small Explorer Mission. The biggest component missing from this existing IRISpy package is the ability to interpolate the instrument response function as a function of time in accordance with some known degradation. The instrument response function relates the data numbers (DN) recorded by the CCD detectors to the physical intensity from the Sun. For this reason the IRIS team has developed a fitting algorithm based on calibration flights that is used to predict the response function as a function of time. A direct translation of this algorithm from its original language, IDL (Interactive Data Language), into Python has already been undertaken but requires more work before it can be merged and incorporated into IRISpy, in order to improve the original translation. The proposed new features will give scientists far greater power and capability to perform IRIS data analysis in Python as well as to make new discoveries regarding the energetics and dynamics of the solar chromosphere and transition region than previously could.

## Description/timeline

Stage 1: Community Bonding (May 7 - 27, 2019)

* Plan to spend time bonding with mentor(s) and others in the Sunpy community more deeply, both from continued engagement with the organization through sustained and meaningful contributions with more issues and PR’s, and also through regular communication via GitHub, riot, and maybe email. I have already communicated with my potential mentor(s) regarding the proposed GSoC project idea, and will continue my interactions with him/them in this period. I have plans to study the respective ndcube and IRISpy code bases more thoroughly and carefully during this time in order to gain familiarity with it to facilitate the proposed work on it.

Stage 2: Coding in the 1st Month (May 28, 2019 - June 24, 2019)

* Weeks 1-2: Work on the “Time-dependent IRIS effective areas” issue at <https://github.com/sunpy/irispy/issues/27> to enable time-dependent effective areas (which are derived using get_iris_response() in the iris_tools) in the same way that it has been done in SSW, an example of which can be found at <https://sohowww.nascom.nasa.gov/solarsoft/iris/idl/lmsal/util/iris_get_response.pro> .
* Weeks 3-4: Start work on the “Add time-dependent iris_response function” issue at <https://github.com/sunpy/irispy/pull/102> to rewrite the time-dependent instrument function response code to be more efficient and Python-friendly. Some preliminary work has already been carried out in that PR, even though the work is still in-progress. Tasks include making it more efficient and compliant with the Python language.

Stage 3: Evaluation (June 25 - 29, 2019)

* Milestones expected to have reached:
  * The “Time-dependent IRIS effective areas” issue must have been adequately dealt with. (That is, PR should have been opened and work must be carried out to the stage where it is almost ready-for-a-final-review or merged on GitHub.)
  * Substantial work must have begun on rewriting the time-dependent instrument function, and at least a third of the work have should have be completed.

Stage 4: Coding in the 2nd Month (June 30, 2019 - July 22, 2019)

* Weeks 5-6: Continue rewriting the time-dependent instrument function response code, at least two thirds of progress should have been made.
* Weeks 7-8: Continue rewriting the time-dependent instrument function response code, expecting most of the work to be completed by the end of these two weeks.

Stage 5: Evaluation (July 23 - 27, 2019)

* Milestones expected to have reached:
  * Have some basic but solid ideas about how the benchmarking between the old IDL code and the new Python code can be carried out.
  * Have some basic but solid ideas about how to test the new code.

Stage 6: Coding in the 3rd Month (July 28, 2019 - August 19, 2019)

* Weeks 9: Perform formal benchmarking between the results the new code produces and those found using the original IDL code.
* Weeks 10-11: Write tests for the Python version to be incorporated into the code base.
* Week 12: Update intensity conversion methods between instrument and physical units that correct for the time observations were taken.

Stage 7: Students Submit Code and Final Evaluations (August 20 - 27, 2019)

* Expected outcomes to have attained:
  * An improved function for deriving the time-dependent IRIS response function written entirely in Python.
  * Reliably maintained this new software in terms of benchmarking and unit tests.
  * The new software must be incorporated into the existing methods and functions in IRISpy that depend on the instrument response function.

## Challenge task

If time permits, will plan to also work on the relevant online documentation or a tutorial to complete at least the basic instructions to be used as a manual for the new feature.

## Schedule availability

I expect to devote at least 5 to 8 hours per day on the project from Monday to Saturday every week, while taking the Sundays off for down time during the coding period. Moreover, I have not planned to take any vacation off during GSoC, and do not expect to be on leave for extended periods of time for the entire duration of the program, in order to give the project the much needed undivided attention conducive to a successful outcome.
