# SOCIS 2014 Application

[SOCIS website](http://sophia.estec.esa.int/socis2014/)
Application deadline: April 15th

## Project Name

SunPy

## Project description

_Describe in a few word your open-source project, why you would like to participate
to SOCIS and what you hope to gain by participating._

SunPy has recenlty turn 3 years old.  Sunpy is a young open-source project which aims
to provide a complete framework in Python for solar, heliospheric, and space weather
data analysis.
We envision it as an alternate choice to the ''de facto'' standard library
[SolarSoft](http://www.mssl.ucl.ac.uk/surf/sswdoc/solarsoft/) (SSW) that is widely
used within the solar community.
SSW is based on the  [Interactive Data Language](http://www.ittvis.com/language/en-us/productsservices/idl.aspx) (IDL)
programming environment, which is propriety software, with costly recurring licensing fees.
Since SSW is built with IDL, it limits the access to solar data analysis to those
people and institutions who can afford the license fees and makes it difficult for
amateurs or institutions with limited resources to become involved.
Python is the perfect alternative to build a solar data analysis framework, as it
is freely available to everyone and is already being used as a scientific data analysis
environment in other science fields ([NumPy](http://numpy.scipy.org/),
[SciPy](http://scipy.org/), [Astropy](http://www.astropy.org/),
[yt]()) with many already-written scientific libraries available.
Additionally, it can be used interactively (Python command-line),
which is very close to how users already work with SSW in IDL.

Participating in ESA's Summer of Code in Space would not only help us expand SunPy
by incorporating new functionality, but it will also promote our efforts in the
solar physics community and thereby attract new contributors.

## Space relevance

_Describe your project´s connection with space activities._

The study of solar physics, space weather and other related sciences often
involves the use of multiple instruments.
Many of those instruments are in space, for example the
[Solar and Heliospheric Observatory](http://sohowww.nascom.nasa.gov/) (SoHO),
[Solar-Terrestrial RElations Observatory](http://stereo.gsfc.nasa.gov/) (STEREO),
[Cluster](http://sci.esa.int/cluster),
the
[Project for On Board Autonomy](http://www.esa.int/esaMI/Proba/index.html) (PROBA-2),
and the
[Solar Dynamics Observatory](http://www.nasa.gov/mission_pages/sdo/main/index.html) (SDO)
spacecraft.
Some are ground-based, for example, the [LOw Frequency ARray](http://www.lofar.org/)
radio telescope, which can be used for nowcasting and forecasting space weather.
The [study of space weather](http://www.esa-spaceweather.net/) has been identified
as being of critical importance as much modern infrastructure is dependent on
space-based assets.

Much solar, heliospheric and space weather data are available to everyone in near
real-time.
Large and important archives of these data going back many decades also exist.
However, the tools to reduce and analyse them are often based on privately held
analysis packages that require restrictive, and often expensive licenses.
This often puts a barrier between those wishing to analyse the data and the
science goals of ESA, and space science in general.

SunPy is removing that barrier by developing open source, freely available,
packages that enable ''anyone'' to analyze solar, heliospheric, and space weather data.
As an alternate to the Solarsoft/IDL environment, SunPy ''deals directly with solar,
heliospheric and space weather data, and so is directly relevant to activities in our
local space environment''.
We choose Python as our development language as it allows us to use many open source
and free packages already developed for other astronomical disciplines.
SunPy will allow anyone to take data from ESA's solar and helipsheric space missions
and perform their own analyses, free from any restriction, thus increasing awareness
of ESA's mission in the scientific community.
Free and open source technology for analyzing solar and heliospheric data will make
it easy for students to begin their scientific careers in space science, and will
make the existing open-source science community aware of solar, heliospheric and
space weather data.

## Website

[http://www.sunpy.org/](http://www.sunpy.org/)

## Software license(s)

All packages within SunPy will be distributed under the
[BSD 2-Clause](http://www.opensource.org/licenses/BSD-2-Clause) license.
If there is a need to use existing code distributed under an incompatible open-source
license, that package will be made available as a separate download.

## Project administrator

David Pérez-Suárez

## Administrator email contact

dps.helio [AT] gmail.com

## SOCIS ideas page

[SOCIS ideas page](https://github.com/sunpy/sunpy/wiki/SOCIS-2014-Ideas-Page)

## Criteria for selecting mentors

Each idea proposed has at least two mentors linked with it.
These mentors are experts in the given subject area, with many being developers of
the web services or other functionality being integrated.
As not all subject experts are Python programmers, the SunPy community will be
available to support Python questions.
All mentors are experienced users of solar data, with experience in data acquisition,
analysis or both.

## Disappearing mentor

Each project has two assigned mentors to it, this will cover the situations when
there are some unavailability by any of them (holidays, conferences, ...).
But in case of a disappearing mentor, the project administrator will be responsible
for finding a new one.
The SunPy project has grown enough so it is not difficult to find another mentor
that is familiar with the project (we have weekly teleconferences within the developers
to discuss the progress of the project and to keep everyone up to date).

## Disappearing student

The students will have the flexibility to accommodate his/her other duties as a
student with the project.
However students are expected to be in regular contact with the mentor assigned
and with the community.
In the case that the student does not show any progress, the administrator of
SunPy will study the specific case to solve any issues the student may have with
the project.
However, if the student completely disappears and if there is no reply after
efforts to contact him/her, then we will understand as s/he has broken the
agreement and we will contact the administration of SOCIS for further actions.
The student's progress will be evaluated and the project mentor will be responsible
for folding the existing code into the SunPy project.

## Interaction with students during and after the program

_How do you plan to encourage the students to interact with your project's community
before, during and after SOCIS? How are you going to ensure your students' continued
involvement with the project after SOCIS concludes?_

During the program, the students will be encouraged to actively participate in
community discussions through our mail list and/or forum.  We will also require
students to write weekly posts on his/her own blog and feature articles in the
project's [blog](http://www.sunpy.org/blog/) describing the status of their work.
This will give visibility to their work to all members of the project, and
beyond into the wider open-source community.
In addition, the SunPy project uses GitHub so that students can easily upload
code to project and GitHub also provides tools to track their progress.

We will do our best to make sure that the students enjoy their work experience,
so they feel part of the SunPy effort and the wider open-source/solar physics
community.
The best way to encourage students to continue with SunPy after SOCIS is for us
to ensure that their efforts earn a prominent place in the solar physics community.
We anticipate that an increasing openness in the solar physics community to new
approaches to data analysis and space science will ensure that SunPy will become
a useful and well-used tool.

It is worth to mention that our first SOCIS students has kept participating within
SunPy being a fundamental part of the project.
Thanks to such experience he has been hired as a summer student during the two
following summers (2012 and 2013) by European research institutes related with
space physics.

## Mailing list(s)

[Users](https://groups.google.com/forum/?hl=en#!forum/sunpy) and
[developers](https://groups.google.com/forum/?hl=en#!forum/sunpy-dev)

## Forum(s)

Mailing list.

## IRC channel(s)

 #sunpy at Freenode.net

## Additional notes

ESA Summer of Code 2013 will be recognized as the sponsor within the documentation
of the packages developed under this programme.
