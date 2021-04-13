<hr>
Find the LaTex/submitted version of the proposal
<a href="https://github.com/devanshshukla99/GSoC-2021/blob/main/Tex/gsoc.pdf">here</a>.
<hr>
<br>

# 3D Plotting
## Basic Information

<b>Name</b>: Devansh Shukla<br>
<b>Academic Program</b>: Integrated Master of Science in Physics<br>
<b>Institution</b>: Sardar Vallabhbhai National Institute of Technology, Surat, India (<a href='https://www.svnit.ac.in'>svnit.ac.in</a>) <br>
<b>GitHub</b>: @devanshshukla99 <br>
<b>Matrix</b>: @devanshshukla99:matrix.org <br>
<b>E-Mail</b>: <a href="mailto:devanshshukla99@gmail.com">devanshshukla99@gmail.com</a> <br>
<b>Contact No.</b>: +91 9826887954 <br>
<b>Location</b>: Sagar, MP, India 470002 <br>
<b>TimeZone</b>: IST | UTC +5:30 <br>

<hr>

## Education

<b>Current Affiliation</b>: Sardar Vallabhbhai National Institude of Technology, Surat, India <br>
<b>Academic Program</b>: Integrated Master of Science in Physics. <br>
<b>CGPA</b>: 9.71/10 <br>
<b>Expected Year of Graduation</b>: 2023 <br>
My Resume is available at <a href="https://github.com/devanshshukla99/devanshshukla99/blob/master/cv/cv_devanshshukla99.pdf"> Curriculum vitae </a> <br>

<hr>

## Experience in Programming

### Software Skills
<b>Languages</b>: Python, C <br>
<b>Platforms</b>: Linux, Windows <br>
<b>Source Control</b>: git <br>
<b>Softwares & Tools</b>: LaTeX, conda, WxMaxima, Mathematica, +.

## Open Source Experience

### SAS-RFI

- Developed a Python program for Radio Frequency Interference Scan at Sardar Vallabhbhai National Institute of Technology, Surat, India.
- <a href="https://github.com/devanshshukla99/SAS">github.com/devanshshukla99/SAS</a> 

### Juno

-  Developed a python program for straight-forward terminal-based socket communication with 128-bit
AES encryption.
- <a href="https://github.com/devanshshukla99/Juno-ReDesign-Sockets-Communication/">github.com/devanshshukla99/Juno-ReDesign-Sockets-Communication/</a>

### Chromos

- Package for getting colored text output in Python.
- <a href="https://github.com/devanshshukla99/Chromos">github.com/devanshshukla99/Chromos</a>

<hr>

## SunPy

## Why did I choose this Project: SunPy?
I have been very interested in the Astrophysics and Cosmology domain for a long time. SunPy specifically
caught my eye due to my course, Intro. to Space Physics, which included a seminar on Sun-spots in which I
utilized SunPy to generate AIA and HMI Image of the Sun, thereby showing the correlation of sunspots and
magnetic field; I have been reading about SunPy since then, slowly learning about the incredible community.
I choosed this project since it brings out the best of both worlds, some Solar Physics and some Programming; for
me, it looked like a natural choice in my career to learn and hopefully contribute positively to the community;
more specifically, next subsection points to some reasons and benefits of such a project; of course, I’m open
to finding more in the future.

## Benefits of 3D Plotting in SunPy
- Super helpful when combining visualizations of multiple objects, for example combining HMI with AIA Image or adding a LASCO Map.
- Moreover, PFSSPy, a dependent of SunPy, which calculates the Potential-Field Source-surface model for
computing the coronal magnetic field features, has an exciting attribute, which can overlap field over the
image. One of the best use-cases of 3D plotting in SunPy.
- Suitable for intuitive understanding and visualization.
- Looks super cool.

## What have other people contributed to this project previously?

Presently, PR #4591 by Dr. David Stansby(@dstansby) provides a foundation for the project. It’s basically
a proof-of-concept; it takes a sunpy.map.Map object, converts it to Heliocentric-Inertial Coordinate system,
creates a mesh and finally plots in PyVista.

## My Contributions

<b>PR #5193</b>: Under Review <br>

- Adds support for file-handlers and file-type in Map and TimeSeries.
- <a href="https://github.com/sunpy/sunpy/pull/5193">https://github.com/sunpy/sunpy/pull/5193</a>

<b>Issue #3303</b>: Currently Working

- Create a Test or a function to report status on all remote servers SunPy pings during a test run.
- Thinking about using a pytest plugin, pytest-vcr, to intercept the requests with a flag, but its likely to change.
- <a href="https://github.com/sunpy/sunpy/issues/3303">https://github.com/sunpy/sunpy/issues/3303</a>

<hr>

## Abstract
SunPy currently uses Matplotlib for plots and has limited support for 3D plots owing to PR #4591 .
The project’s goal is to pack PR #4591 into a new package, independent of SunPy, and develop a complete
API initially interfacing with PyVista but general enough for other backends like plotly too.
SunPy has excellent support for 2D plots with Matplotlib, but 3D support is missing; through 3D backing, one
can easily combine visualizations of multiple objects such as overlapping HMI on a AIA image in 3D; it’ll be a
gem for intuitiveness. Moreover, PFSSPy, a dependent package of SunPy, which calculates the Potential-Field
Source-surface model for computing the coronal magnetic field features, has an exciting attribute, which can
overlap field over the image; this’ll precisely be the best use case for 3D support in SunPy. I believe the project
is evenly balanced between writing, testing and documenting code

## Goals
- Convert code from PR #4591 into a new package under SunPy org, and understand it down it a fiber.
- Add infrastructure to plot astropy coordinate object.
- Add infrastructure to support other data types, too, like for SOHO, RHESSI, etc.
- Hoping for 90%, targeting 100% code-coverage. Benchmarks and extra optimizations, if possible.
- Documentation for the whole project.

## Time Commitment

I plan to fully commit and immerse into the project, with a minimum investment of 20hr/week and with an
average of 25hr/week.
Honestly, I am not a big fan of assessing based on time investment; my priority would be to make and follow
weekly task schedules, with some buffer time for unforeseeable circumstances and additional tests.

## Timeline
I have attached a thorough timeline of the proposed project. Regarding my commitments, I’ll have my course
classes from August 10, so I’ve shifted some of the workload to July.
I plan to to publish a weekly blog for the project with all relevant details to help future developers and users; I
believe this would be critical in the long run.

- May 17, 2021 - May 24, 2021
    - Familiarize with the code and the community.
    - Since I am already familiar with the dev env and test systems used in SunPy so I’ll quickly go through it again just in-case, and will focus more on the code and how it all is integrated together.
    - Create a separate package with PR #4591 as foundation and set-up all necessary workflows.

- May 24, 2021 - June 1, 2021
    - During this time, I’ll discuss with my mentors and come with more specific details about the project, like how the public face of the API should behave, etc.
    - I’ll learn and try to solve the challenges I’m already aware-of in the project, see subsection V.IV
    - Learn more about dependencies like AstroPy, plotly, MPL, PyVista and see how their API is designed.

- May 24, 2021 - June 1, 2021
    - Plan for the API.
    - Throughly understand and test the existing code.
    - Continue learning about the dependencies.

- June 7, 2021 - June 14, 2021
    - Define tests and documentation for the existing code.
    - Discuss & Work on the API.

- June 14, 2021 - June 21, 2021
    - Add code for plotting sunpy.map.Map
    - Work on the API.
    - Crush the bugs along the way.

- June 21, 2021 - June 28, 2021
    - Add tests and documentation, hoping to achieve 75%+ code coverage.
    - Check the Integration with SunPy. – Waypoint - 1 Check

- June 21, 2021 - June 28, 2021
    - Crush the bugs.
    - Add tests and documentation, hoping to achieve 90%+ targeting 100% code coverage.
    - Finalizing the API.

- June 28, 2021 - July 5, 2021
    - Gather Feedback.
    - Finalizing the API for the evaluation.
    - Crush the Bugs.

- July 5, 2021 - July 12, 2021
    - Finalizing the API for the evaluation.
    - Plan for plotting astropy coordinates in 3D infrastructure.
    - Buffer time.

- July 12, 2021 - July 16, 2021
    - Buffer time, for incorporating required changes as per feedback.
    - More debugging.

- June 16, 2021 - July 23, 2021
    - Work on infrastructure for plotting astropy coordinates in 3D.
    - Discuss on adding infrastructure for other data type.

- July 23, 2021 - July 30, 2021
    - Test infrastructure for plotting astropy coordinates in 3D.
    - Plan infrastructure for other data type, SOHO, EUV, RHEISSI, tbd.
    - Buffer time to crush bugs.

- July 30, 2021 - August 6, 2021
    - Work on adding infrastructure for other data type, SOHO, EUV etc, tbd.
    - Add tests and documentations, hoping to achieve 75%+.

- August 6, 2021 - August 13, 2021
    - Work on support of pyvista for jupyter-notebook.
    - Crush the bugs.
    - Finalize the API.

- August 13, 2021 - August 20, 2021
    - Add tests and documentations, hoping to achieve 90%+ targeting 100% code coverage.
    - Finalize the API, prepare for the pre-release.
    - Crush the bugs.
    - Check Documentation for mistakes/typos/bugs.

- August 13, 2021 - August 16, 2021
    - Finalize the API, incorporate the feedback from additional review.
    - Crush the bugs.
    - Gather feedback.

- August 16, 2021 - August 23, 2021
    - Pre-Release.
    - Crush the Bugs.

- August 23, 2021 -
    - Maintain support and work on improving the performance and stuff.
    - Keep crushing the bugs.

## Probable Issues/Challenges

- The API will initially depend upon pyvista, which works on VTK, unfortunately Read the Docs doesn’t
support a headless-display, but this need to be investigated after reply from @cadair suggesting a possible
solution.
- As of now, whenever I run pyvista from Jupyter Notebook it bugs out crashing the notebook, I’m not sure
if this is a wide-spread or localised issue

<hr>

## GSoC Info

### Have you participated previously in GSoC?

This is the first time I'm applying to a project.

### Are you also applying to other projects?

This is the only proposal I'm submitting.

### How much time do you plan to invest in the project before, after and during Summer of Code?

- Before - 20hrs/week.
- During - 25hrs/week.
- After - 15hrs/week.

### Are you eligible to receive payments from Google?

Yes, I am eligible.
<br>
