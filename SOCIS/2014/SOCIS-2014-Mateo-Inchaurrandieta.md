About Me
========
- Name: Mateo Inchaurrandieta
- Email: mateo.inchaurrandieta (at) gmail (dot) com
- Studies: First Year Computer Science at [University College London](http://www.cs.ucl.ac.uk)
- GitHub: mateoi
- IRC: mateoi
- Languages: English (native), Spanish (native)

Background
==========
I first started programming when I was 13, when I found an old TI-83 that no one claimed. I wrote Snake and Pacman clones, but coding in TI-BASIC was horrible, slow and prone to errors. A couple of years after that I discovered Python, and the incredible ease and elegance it offered. After that I learnt C, but didn't appreciate its power until much later - in high school, I took a CS course in Java, and in college I've studied C, Haskell and Java. I also know OCaml, Scala, and I'm teaching myself Perl. After Perl I plan on going on to Lisp. My main interests are functional programming, cryptography and quantum computing.

I'm familiar with git and the Linux shell. I have never contributed to an open source project before, because I was daunted and frankly a bit intimidated by some communities. I'm glad to have discovered SunPy - everybody here seems very nice and I look forward to working with you!

Outside programming, my interests are football (american and otherwise) and cooking.

Project
=======
My intention is to design and implement a spectrum object for SunPy.
The generic spectrum object will simply generalize the capabilities of its inheriting subclasses - optimizations and handling of specific types of spectral data will be part of these subclasses. I plan on using matplotlib for plotting and displaying charts (unless for some reason we should use something else), and NumPy for numerical computation. As I was going through the source code, I was excited to see NumPy being used extensively - I've used it on some minor projects and I love it!

##Proposed timeline
###Week 1 / 2
Define and document an interface - what the class can do and what it can't. Research about the problem and how it can be solved best, as well as caveats and possible pitfalls. Get acquainted with the structure and style of the whole source and with the specifics of the more relevant parts.

###Week 3 / 4
Write unit tests and outline the implementation of the various functions needed. Decide and document relevant data formatting, if any - for a possible file I/O capability? Research about the physical characteristics and limitations of the detectors used. Also define interactions and interfacing with the Map and Lightcurve objects for display and data analysis purposes.

###Week 5 / 6
Begin implementing the backend code, continue writing unit tests. Get more familiar with the code that this object will interact with and its features and bugs.

###Week 7 / 8
Begin writing relevant documentation and debugging written code, continue coding. By the second half of the block, start interacting with Map and Lightcurve objects.

###Week 9 / 10
Finalize display properties and complete  major features. By the end of this block, the code should be in a more or less working state. Begin cleanup, continue debugging, testing and writing documentation.

###Week 11 / 12
Clean code, optimize subroutines, test and debug.

###Week 13 / 14
Final code submission. Allow these two weeks to work on any outstanding bugs / errors that may have arisen.

###Beyond the project
I intend to remain part of the SunPy community after the summer, maintaining and developing.

###All stages
At all stages I plan to work closely with the whole community in general and my mentors in particular. I will keep them informed of my current work package and progress, and ask for reviews and feedback. I think criticism and advice are very useful and I always try to understand it and follow it.

Past Projects
=============
I'm currently working for a small, three-person team developing an Android app for an art gallery. It involves writing the code for static tablets that display video and audio about different pieces, and the files can be managed remotely from a desktop computer using a simple UI we wrote. Also, there is an Arduino-based ultrasound and motion sensor to attract passerby by playing audio snippets and to record usage statistics (i.e. percentage of people who interact with the tablet). I am in charge of the Arduino development, on top of being the project leader so having to manage internal communication, deadlines, deliverables, as well as communicating with the client to find out her requirements and proposing solutions. We fully intend to release the source code under the GPL once we're finished.

Some of my past projects can be found on my GitHub page [here](https://github.com/mateoi).

Other Info
==========
##Available Platforms
I run Linux Mint 16 KDE, 64-bit and Windows 7, 64 bit.

##Availability
I'm usually available from about 9 am to around 11 pm. My time zone is UTC +1 (British Summer Time / West Africa Time - so 0800 to 2200 UTC), but I will probably change that to UTC -5 (Canada/US/Mexico Central Daylight Time - so 1400 to 0400 UTC). I might take a week or so off, when I will have full internet access but little or no coding will take place.

##Sunpy Contributions
* [Solution](https://github.com/sunpy/sunpy/pull/967) for [Issue 960](https://github.com/sunpy/sunpy/issues/960)
* PEP-8 fixes: #986
