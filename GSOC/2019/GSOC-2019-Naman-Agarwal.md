#  HelioViewer Python API Wrapper
## Organisation: OpenAstronomy
## Sub-organisation: SunPy

## About Me
### Contact Information
- Name: Naman Agarwal
- Email: namanagarwal8968@gmail.com
- Time Zone: IST (UTC+5:30)
- Github Handle: [Naman9639](https://github.com/Naman9639)
- Chat Handle: naman9639

### Personal Background
Hello, I am Naman Agarwal, a third year undergraduate student at UIET Chandigarh, India. I'm pursuing a degree in Computer Science and Engineering. I have a very little experience with open source but I love programming a lot, particularly in Python. I am comfortable with a lot of programming languages but I specifically like Python because of its intuitive interface and very broad spectrum of usage from simple scripting to web applications and scientific uses. I use Ubuntu mainly for coding purposes and my favourite editor is Sublime Text.

### University Information
- **University:** [University Institute of Engineering and Technology, Chandigarh](http://uiet.puchd.ac.in/)
- **Major:** Computer Science and Engineering
- **Current Year:** 3rd Year (6th semester ongoing)
- **Expected Graduation Date:** 2020
- **Program:** Bachelor of Engineering (B.E) in Computer Science and Engineering

## PR links and Issues Worked on
- Merged:
    - [Instantiate map with array and WCS object](https://github.com/sunpy/sunpy/pull/2793)
    - [Ensure the HelioviewerClient uses Helioviewer API version 2 exclusively](https://github.com/sunpy/sunpy/pull/2801)
    - [ImageAnimatorWCS unit_x_axis and unit_y_axis follows image_axes](https://github.com/sunpy/sunpy/pull/2894)
    - [Links on sub-package are working](https://github.com/sunpy/sunpy/pull/2902)
    - [Add support to download header information from Helioviewer API](https://github.com/sunpy/sunpy/pull/2904)
    - [Simplified user access to the sourceID variable in the HelioviewerClient.](https://github.com/sunpy/sunpy/pull/2926)
- Open Issues:
    - [The purpose of the HelioviewerClient](https://github.com/sunpy/sunpy/issues/2860#)

## Project Proposal Information
**Mentors:** wafels, Stuart Mumford, Helioviewer Kirill

### Abstract
SunPy is a package for solar physics that is also used for solar data analysis. Helioviewer is a Public API that provides access to solar and heliospheric datasets to scientists, educators, developers, and the general public. Currently Sunpy has a `HelioviewerClient` that implements only a handful of functions like `getClosestImage`, `getJP2Image`, `getJP2Header` and `takeScreenshot`. There are a large number of function that are missing in Sunpy which are provided by the Helioviewer API. Thus there is a requirement for a **package the lightly wraps the Helioviewer API.** Since SunPy do not cover a lot of functions provided by the Helioviewer API this package should let the user create their own helioviewer.org like GUI in Python.

### Motivation

The Helioviewer API is quite extensive and it is difficult to cover all the functionlities provided by the API. In the current scenario, a user can only access the JPEG images and meta information of these files. Thus a low level wrapper can be implemented for all the API. One of the main aims of this module is the implement this as if will help the clients write fancy clients in python for the API.

### Deliverables

The following are the deliverables for the project:
- Implement a python wrapper for Helioviewer API.
- A **HelioviewerClient class** with the following methods:
    - getJP2Image
    - getJP2Header
    - getJPX
    - getJPXClosestToMidPoint
    - queueMovie
    - reQueueMovie
    - getMovieStatus
    - downloadMovie
    - playMovie
    - takeScreenshot
    - downloadScreenshot
    - checkYouTubeAuth
    - getYouTubeAuth
    - uploadMovieToYouTube
    - getUserVideos
    - getClosestImage
    - getDataSources
    - getTile
    - shortenURL
    - getNewsFeed
- Write tests and documentation

## Timeline & Deliverables
### Community Bonding Period (May 7 - May 26)
During the community bonding period I would get to know more about the codebase. I would try to get familiar with the Helioviewer API and some python http libraries like ```urllib``` and with context managers and decorators in python. I am familiar with a few modules in ```sunpy.net``` but would also have a look at the rest of the code base.

During this time I would also discuss with the mentors to know properly which all features should the package provide. Some time would also be given to study about writing tests using ```pytest```.

At the end of the Community Bonding Period, I aim to:
- Get familiar with sunpy codebase, in particular modules like net, util etc.
- Learn about ```pytest``` and **context managers**, **decorators** in detail.
- Get an overview of all the functionality that needs to be provided by the package.
___
### Coding Period Begins
___

### Week 1 (May 27 - June 2)
- Begin coding the HelioviewerClient class.
- Add documentation for the same.

### Week 2 - Week 3 (June 3 - June 16)
- Add code for 6 methods.
- Start working on the tests for these methods.

### Week 4 - Week 5 (June 17 - June 23)
The main aim would be to ensure that by the end of the first evaluation all the methods are working properly. This period will also server as a buffer period to complete any other pending tasks or issues.
- Complete the tests
- Add documentation for the code written till now.
___
### Phase 1 Evaluation
___

### Week 6 - Week 7 (June 25 - July 5)
- Add code for 6 methods.
- Start working on the tests for these methods.

### Week 8 (July 6 - July 12)
- Add documentation for the code
- Complete the tests for the methods.

### Week 9 (July 13 - July 21)
This period will also act as a buffer period for the second part of the project
- Complete any pending or left over tasks
___
### Phase 2 Evaluation
___

### Week 10 - Week 11 (July 23 - August 6)
- Add code for rest of the method
- Write tests for these methods.

### Week 12 - Week 13 (August 7 - August 25)
If things went fine till now, then I would be done with almost 90% of my target.
- Complete any left-over tasks
- Complete the documentation
- I would be in touch with the mentors and if there are any further issues or bugs that are left unresolved then I would work on them.
- Hopefully get the work merged with the master branch of SunPy
___
### Final Evaluation
___

### How I will successfully complete the project
I am confident of completing this project as the project suits my interests and I have a fairly good experience with python. I have previously worked on projects that have strict deadlines and have a good prior experience with open source.

I would push my work to the remote fork frequently so that the mentors can review my progress whenever required. I would always be in constant communication with my mentors to update them on my current progress and seek their guidance whenever I am stuck in any issue.

Even after GSoC ends, I will actively contribute to SunPy and be available if anyone has any questions regarding my code.

### Benefits to the Community:
The project offers several benefits to the community.
- It would facilitate anyone to create their own helioviewer.org like GUI in Python.
- It would allow the user to use the full power of helioviewer API.

## GSOC
### Have you participated previously in GSoC? When? With which project?
No, I have not participated in GSoC before.  This is the first time I am participating in GSoC.
### Are you also applying to other projects?
No, I am not applying to any other projects. This is the only project and SunPy is the only org that I am applying for.
### Commitment
I would not be involved in any other internship or work during the summers. Since, my vacations starts on May 20, I would be able to start early and try to complete the project well before the deadline.

My classes for the new semester would begin from August 1, but I would still be able to give at least 40 hours per week as there is less academic load during the first few weeks of the semester.

### Eligibility
Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact namanagarwal8968@gmail.com
