The [[SOCIS 2014 organization application page|SOCIS 2014]].

*Students*: You need to apply in the 
[SOCIS website](http://sophia.estec.esa.int/socis2014/) and also don't forget to 
add your application to this [[wiki|Socis-2014-students-applications]].  
Try to follow the [[application guidelines|GSoC-student-application-guidelines]] 
we set for the GSoC, you will get more chances to be selected if you follow them.

The ideas shown below are projects that we believe can be completed during the SOCIS 
programming period (** - **).  
The projects are sorted in order of interest to the SunPy community.  
Please join the #sunpy IRC channel ([web client](http://webchat.freenode.net/)) to 
talk with the SunPy community and do not hesitate to introduce yourself in any of our 
mailing list ([users](https://groups.google.com/forum/?fromgroups#!forum/sunpy), 
[developer](https://groups.google.com/forum/?fromgroups#!forum/sunpy-dev)).

## Integration of the HESPE Data Archive
* **Description**: The [HESPE Data Archive](http://hespe.eu/browser) gives access
to pre-processed science products from the RHESSI satellite. 
The data are organized by flare event and are available both as printable quicklook 
files (PNGs) that can be directly displayed in SunPy, and in their original data 
structures and formats (FITS) that may need some additional processing. 
Access is provided through a web interface (REST) that can be used from within SunPy. 
Each flare event can have hundreds of data products connected to it, which requires 
special attention when displaying the search results. 
The integration task includes: 
(1) basic integration of the HESPE search (with feedback to the HESPE project team,
if necessary); 
(2) basic integration of the RHESSI data products using existing SunPy structures; 
(3) optimizing the handling and presentation of the search, the search results 
(e.g. allowing to filter), and the data products themselves. 
The outcome should be two clients, command-line and GUI.

* **Requirements**: Knowledge of GUI design; Basic knowledge of working with web 
services (REST) and JSON is a plus.

* **Mentor**: Laszlo I. Etesi (HESPE data archive developer), Steven Christe (SunPy)

## Now module
* **Description**: [SolarMonitor.org](http://solarmonitor.org) provides a quick view
service to know how the sun looks now. 
Additionally it provides some other information useful for space weather as the 
current solar activity and flare forecasting.
The data it uses it comes from multitude of real-time data archive that differs from
the archived data.
By creating a `now` module in SunPy we will provide to the SunPy user to download, 
visualise and analise near real-time data.  
This module then could be used by SolarMonitor directly which it will help to advertise
worldwide SunPy capabilities.

`now` module will have to handle properly different datatypes (map, lightcurves) and
images.

* **Requirements**: N/A

* **Mentor**: David PS, Paul Higgins?, Eoin Carley? (SolarMonitor)

## Idea
* **Description**: The ...
* **Requirements**: Knowledge of ...
* **Mentor**: Mentor A, Mentor B

### List of Mentors
* Laszlo I. Etesi
* Steven Christe
* David PS