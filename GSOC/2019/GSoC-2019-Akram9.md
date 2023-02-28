## Organization: OpenAstronomy

## Sub-organization: SunPy

***

# Feature and Event Objects in SunPy

## Personal Information

Name: Md Akramul Haque

Email: haquemdakramul@gmail.com, haquemdakramul@hotmail.com

GitHub username: Akram9

IRC nick: akram9

University: Aligarh Muslim University, Aligarh

Degree: Bachelor of Technology

Course: Mechanical Engineering

Year in course: 3rd

Time zone: UTC +0530
***

## Background

A third-year mechanical engineering student, I grudgingly came across programming and Python about five years ago in school, and after getting a hang of it, programming stuck with me. I came across open source about two years back, but never properly contributed. Being more interested in changing my laptop's OS, I destroyed its hard drive distro-hopping, the last one being FreeBSD. From then on, I have been using WSL on Windows 10, occasionally testing some distros in the back. Apart from my operating system, most of what I use is open source.

As for astronomy, I am more interested in physics than engineering, and actually plan to turn my career towards it eventually. Taking my shift to physics seriously, I came across SunPy and PlasmaPy, and chose SunPy to start with. This is the first time I have contributed to an open source project, apart from just reporting issues. In SunPy, I find an opportunity to use and increase my abilities, which I believe will be quite helpful for me in the long run, while also contributing to a community project that impacts many people worldwide.

I go for a swim occasionally; I like analog watches, Mazda and Alistair MacLean.
***

## Experience

Although I am not new to programming, and I have a basic idea of C++, C and FORTRAN too, this is my first time contributing to a project. From my first year in college, I have been programming in Python, mainly solving engineering and math problems. I had collaborated with a senior friend to plot toy-models for a Chaos project he has been working on, ending up creating a tkinter application with matplotlib to plot out graphs which required a root equation, a kernel and desired number of iterations.

It has been about a month and a half since I started contributing to SunPy. The PRs I have opened yet:

* [#3000](https://github.com/sunpy/sunpy/pull/3000): Tests for animator class
* [#2986](https://github.com/sunpy/sunpy/pull/2986): Improve scaling of animator and adding aspect keyword to lineanimator
* [#3010](https://github.com/sunpy/sunpy/pull/3010): Fixed missing positional argument while calling function
* [#2938](https://github.com/sunpy/sunpy/pull/2938): Modified /sunpy/instr/goes.py so that 'hek' is imported only in the function that uses it

***

## Abstract

The sun, made of gas and plasma, rotates differentially – having different speeds at different locations. This sort of rotation highly influences the massive magnetic fields surrounding it. The uneven turning and twisting of these magnetic fields cause lots of events and features to form up the surface of the sun. These features and events are studied to know more about our star. SunPy provides access to two big repositories that host related information – the HEK and HEC. Users can download data from these sources and use SunPy's built-in capabilities to make analyses on the data.

The objective of this project is to make it easy for the users to use SunPy features on the aforementioned features and events data by creating a SunPy object that extracts data from HEC/HEK, does mathematical manipulations on it, and gives an output in an appropriate fashion using existing SunPy objects like plots, series and animations.

The following are the intended functions of the F/E object:

**1. Record input from user**
The F/E object takes input form the user about the data set to be used, and any other information, which may be specific to the data set. It may also take input about the type of output – a table as output or some sort of a plot or an animation (to be discussed).

**2. Retrieve data from the internet**
The F/E object should depend on sunpy/net to download data from the HEC/HEK repositories as per the input. The user can specify information about the data or, like in the example in the docs – use saved data in SunPy.

**3. Make use of SunPy specific datatypes**
If the data has different units in use, convert these to SunPy specific ones for compatibility, and for easy use by the user.

**4. Modify the data**
The data may be, as required, modified per any algorithm – like normalization, standardization, etc.

**5. Output the data**
As per the type of input, the modified data can be discriminated for an appropriate output – as an astropy table, as a plot, as an animation, a timeseries, etc. The discrimination can be done by the F/E class or may be specified by the user.

From the user's point of view, the F/E object should be able to take input of the qualities of the data and the type of output, and give an output that may be further used by SunPy objects – like an overplotted sunpy Map object can be yet modified for visualization, or saved to create an animation with other pictures.
***

## Project Timeline

**Bonding Period**
During this period, I intend to get an insight into HEK, HEC and their relation to solar physics research. Apart from that, the importance they have in interacting with other SunPy object and classes. Also, I would like to learn more on the objects that can be bonded with the F/E object.
Part of this time should be spent on deciding the features of the F/E object and its implementation along with all the SunPy objects that it will communicate with. I also intend to decide with the mentors on the basic design of an F/E object.

**Week 1 – May 27 to June 3**
Finalize the basic design of the object and start its implementation.
This week will see slow activity as I may have an exam or two and I will spend one day travelling.

**Week 2 – June 4 to June 10**
Implement the design primitively – the object developed should be able to give a desired output for a particular input.

**Week 3/4 – June 11 to June 24**
Finish on the implementation of the decided design.
Decide on an API structure and start its implementation.
Start writing tests for the code developed up to this point.

**Phase 1 Evaluation – June 24 to June 28**
***

**Week 5/6 – June 25 to July 8**
Implement the API, add methods to the F/E object, implement the desired mathematical operations in the object (if any)– normalization, standardization, etc.
A working model of the F/E object is to be created and implemented.

**Week 7/8 – July 9 to July 22**
Finish with adding methods to object and continue writing tests for the F/E object.

**Phase 2 Evaluation – July 22 to July 26**
***

**Week 9/10 – July 23 to August 5**
Finish with tests for the object and modify the code (as required).
I will be off for about two days here.

**Week 11/12 – August 6 to August 19**
Examples and documentation to be completed in this time.
I will be off for two days again.

**Final submission week – August 19 to August 26**
***

## GSoC

* I have never participated in GSoC before.
* I am not applying for any other project. In SunPy, this is the only project I am applying for.
* I am eligible to receive payments and stuff from Google.

### Commitments

I can commit north of 35h/week during the first two months of the duration. I don't have any other commitments, internships or vacations. But over the duration of GSoC, I will not be able to work for a total of about a week due to college and travelling. I expect to make up for that in the first two months of the project.
The last third of the project-time I will be in college, so my work time will change, though I will be able to give about 4-5 hours a day during the weekdays with the whole of the weekend to compensate for any losses.

### Extra Info

Although I program mainly using WSL on Windows 10, I can shift to Linux if required.
If I am not able to complete my objectives in time, I may skip either the documentation or examples from the project and finish them after the project duration.
Before the project starts, I will keep on contributing, though not very consistently because of college. After the project, I intend to stick with SunPy, OpenAstronomy, as this will be important to me.
