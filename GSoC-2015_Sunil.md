#Support For analysis of Solar Energetic Particles

## Student Information

| Contact Field | Information |
| :-----------: | :---------- |
| Name | Sunil Kumar|
| Time zone | UTC +5:30 |
| IRC handle | sun_sam@irc.freenode.net |
| Github | sunilk747, Sunil Kumar |

##Abstract

Observing solar data for solar atmosphere is important for being able to learn more about solar material.The solar system is composed of solar materials.The study of solar atmospheric events gives us some in depth knowledge of solar system and we can learn a lot about its origin.One of such event is acceleration of solar Energetic particles(SEPs) during solar eruptions up to relativistic energies.As they pose serious threats to astronaut and spacecrafts ,so the study of acceleration and propagation of SEPs is important to minimize the risk factor.

SEPs can be observed with different instruments such as GOES,SOHO,ACE etc.The observations made are compared to other solar atmosphere observations such as solar X-Ray and radio bursts,changes in solar magnetic field and EUV and coronagraphs.The functionality to observe the other solar atmospheric event is already present in sunpy ,as of now there is no tool to analyze the SEP observations.

The main goal of this project is to add module for different instruments which are responsible for the observation of SEPs.

## Project Background and Idea

In sunpy there are many instruments (GOES,SOHO etc) for the observation of  solar data.The data for SEPs can be observed by various instruments .One of such instrument is ERNE(Energetic and Relativistic Nuclei and Electron).
Currently the sunpy doesn't contains the support of ERNE which is responsible for the SEPs observations. 

We would want to add a module for the ERNE in sunpy,enabling sunpy capable of SEPs observations.The core part of this project is to make sunpy able to fetch data for SEPs from various instrument's one of which is ERNE and use them for basic operations like visualization as time series,Visualization as energy spectrum etc.

## Project Deliverable

1. Adding a module for the new instrument's responsible for SEPs observation.
1. Adding functionality for the observation of SEPs.
1. Adding methods for fetching data from the new Instruments.
1. Adding methods in `lightcurve.py` to convert the fetched data(CSV or CDF file) into lightcurve object.
1. Adding methods for other basic operations.  

##  Implementation
1. The first approach will be adding a module for the new instrument and then a little tweaking in the `lightcurve.py` will add the capability of converting the fetched data file into lightcurve obejct.
1. Then addition of some methods for the comparision of the calculated data for SEP with other light curve data.
    
### Reference
1. https://en.wikipedia.org/wiki/Solar_energetic_particles
1. http://docs.sunpy.org/en/stable/code_ref/lightcurve.html