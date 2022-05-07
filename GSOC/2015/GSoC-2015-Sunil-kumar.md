# Support For analysis of Solar Energetic Particles

## Student Information

| Contact Field | Information |
| :-----------: | :---------- |
| Name | Sunil Kumar|
| Time zone | UTC +5:30 |
| IRC handle | sun_sam@irc.freenode.net |
| Github | sunilk747, Sunil Kumar |
| Blog | |

## Abstract
Currently sunpy does not have the functionality to process and analyze the SEPs data. There are some instruments ( ERNE, ACE, STEREO) available for the observation of SEPs. This project aims to add support of these instruments to sunpy. Doing so makes sunpy able to access more solar data, as well as adding more functionality to the existing SunPy.

## Project Background and Idea

The support of some instruments which are responsible for the observation of solar data are already present
in SunPy. Currently it lacks the support of instruments required for the observation SEPs data. In this
project we would add module for each instrument, so that more accurate data could be fetched and then we
would convert this data into lightcurve object. At the end we would add methods for each instrument module for
the visualization operation.

## Project Deliverable

1. A fully implemented class for each instrument.
1. Integration of Unified Downloader with the newly added instrument class.
1. Methods for the visualization of fetched data.
1. Successful tests for their implementation.
1. Corresponding documentation.

## Implementation

The first approach will be adding class for each instrument. These classes will be inherited from superclass `lightcurve.py`. These classes will include methods for parsing of downloaded files which are generally present in txt, csv or cdf format and then convert the fetched data into a light curve object. These classes will use `UnifiedDownloader` for downloading files. Then a module for each instrument will be added in `sunpy.instr` which will include the following methods:

* Methods for visualization operation such as visualization as time series, visualization as energy spectrum.
* Methods for numerical calculations such as calculation of intensity ratios of different particles and their      dependency on time and energy, simple average and energy channel binning by average.

## Timeline

**APRIL 27 -MAY 25(Community bonding period)**

Read documentation, practice code and get familiar with lightcurve module. Get the final idea about approach and project implementation after thoroughly discussing it with mentor.

**MAY 26 - JUNE 8(2 weeks)**

Define the class `ERNELightcurve`. Which will be one of the three instrument classes need to be added. This class will include methods for the conversion of downloaded data into lightcurve object.

**JUNE 9 - JUNE 21(2 weeks)**

Write classes for the remaining two instruments which would be similar to the first one.

**JUNE 22 - JULY 5(2 weeks)**

Add module for each instrument in `sunpy.instr` which will include  methods for performing the basic operations like calculation of intensity ratios of different particles, their dependency on time and energy and comparison with other lightcurves data.**JUNE 26 - JULY 3 (Midterm Evaluation).**

**JULY 6 - JULY 12(1 week)**

During this period of time I will add tests and make documentation.

**JULY 13 - JULY 19(1 week)**

I will use this time to get more familiar with the operation of Unified Downloader.

**JULY 20 - JULY 26(1 week)**

Integrate Unified Downloader with the new class making the new class able to download data using Unified
Downloader.

**JULY 27- AUGUST 10(2 week)**

Add tests, make documentations and make sure everything is working as planned.

**AUGUST 11- AUGUST 18 (1 weeks)**

Finalise everything, solve any bug that might arise, document all my work and make sure that all tests passes.

**AUGUST 18 - AUGUST 24(1 week)**

Buffer Time.

## Code Samples
Though not for SunPy, but I have added a error message for Astropy. Very soon I will submit my first PR for SunPy.

* [Error message](https://github.com/astropy/astropy/pull/3426)

## Additional Information

I am a second year undergraduate student at the International Institute of Information
Technology,Bhubaneswar. I am majoring in Computer Science and I am very much interested in Machine learning. For over one year I have been coding in python and I love this language as it is simple and easy to read. I have some knowledge of Scrapy a python based web crawling framework. I am an intermediate level programmer in C and C++. I am well acquainted with working on linux workstation. Since, I am new to opensource and haven't contributed to any opensource community in past, I don't have much experience of it. Through this GSoC program I would like to do some opensource contribution and hoping to learn some new things.

### Other Schedule Information

I suppose that I shall be able to devote major part of my time for the Implementation of this project. As of now I have no plans or vacations for this summer. I might have my exam in the month of July, but it will be over in two days, I will not be able to work for these two days. But I will make up things by putting extra time.

## Reference

1. [Solar Energetic Particles](https://en.wikipedia.org/wiki/Solar_energetic_particles)
1. [Lightcurve](http://docs.sunpy.org/en/stable/code_ref/lightcurve.html)
1. [Visualization](https://github.com/sunpy/sunpy/wiki/GSoC-2015-SEPproject)
