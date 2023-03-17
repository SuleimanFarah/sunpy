#   GSOC 2019
#   Project Proposal

##   Project Title : Feature and Event Objects in SunPy

* Name : Sarthak Jain
* Organisation : OpenAstronomy
* Sub-organisation : SunPy
* Mentors : [Stuart Mumford](https://github.com/cadair), [Jack Ireland](https://github.com/wafels), [David Pérez-Suárez](https://github.com/dpshelio)

###   Personal Info
* Country : India
* Github Profile : [jain8844](http://github.com/jains8844)
* Email : jains8844@gmail.com
* Time Zone : Indian Standard Time(UTC+5:30)
* Link to the Sample Pull Request : [#3026](https://github.com/sunpy/sunpy/pull/3026) [open]

###   Education
* University : [Indian Institute of Technology Indore](http://iiti.ac.in)
* Department : Computer Science & Engineering
* Year of Study : First Year

####   Open Source Background
* Programming Languages : Python, C++, Java(Basic Knowledge) and a knowledge of Django Framework
* Started Programming with Competitive Programming
* Studied Python during Intermediate Classes
* Contributions to Other Repos
  * Imdb_Portal
    * [Python tkinter GUI](https://github.com/NJACKWinterOfCode/IMDB_Portal/pull/20)
* Independent Projects
  * [xlab-project](https://github.com/jains8844/xlab-project)
  * Developed a Django based Web Application for the Discipline of Civil Engineering, IIT Indore.

I believe that the selected project suits to my knowledge of Python and I will be able to complete the project in the given time.

####   Interest in OpenAstronomy

In my Intermediate Classes, I was told that Python is one of the best languages to develop applications and scripts because of its clarity, readability and versatility. As said by the Creator,

> " The joy of coding Python should be in seeing short, concise, readable classes that express a lot of action in a small amount of clear code -- not in reams of trivial code that bores the reader to death. "

Along with this, Astronomy is a subject to interest to me. The project SunPy thereby interests me to learn a lot about Astronomy.


###   Abstract
The Sun displays many different features and events (FEs). These are detected and described either automatically by algorithm, or by visual inspection by human, or by a combination of both. There are many different repositories of these FEs online. SunPy provides access to two large FE repositories, the Heliophysics Event Knowledgebase (HEK) and the Helio Event Catalogue (HEC).

The aim of this project is to create a SunPy object that normalizes input from both the HEK and HEC and creates a SunPy FE object. The SunPy FE object should take advantage of existing SunPy capabilities such as SunPy spatial coordinates and SunPy time. This will make FE data much more useful to SunPy users.

The SunPy FE object should interact intuitively with existing SunPy objects such as the SunPy maps and timeseries. For example, it should be simple for a FE with a spatial extent property to be overplotted on SunPy map; similarly, it should be simple for a FE with a temporal duration to be overplotted on a SunPy timeseries.

##   Synopsis

These are the following things that I have planned to be done under this project :

1. Implementing the Feature and Event Class as described in the project description.
2. Writing appropriate functions in Sunpy Maps and TimeSeries for the interaction of a Feature and Event class object with these SunPy objects.
3. Making changes with the existing ``` HEKClient ``` and ``` HECClient ``` classes so that the output provided by these classes is in terms of appropriate Astropy and SunPy Quantities.

The above mentioned tasks would be implemented in the following ways :

### 1. The Feature and Event (``` FE ```) Class

This would be a basic Python class which would take the information regarding a single event returned by the HEK or HEC client respectively as an input and return an ``` FE ``` object corresponding to the entered event details. The instance variables of the class would specify the properties of the events in their respective Astropy Quantities. A basic implementation of the ``` FE ``` class can be seen in this [gist](https://gist.github.com/jains8844/fc55cb2c4c6bafa3e336f5ab3b4e2c8f). The code written can be implemented for all the variables mentioned on the [page](http://lmsal.com/hek/VOEvent_Spec.html) based on their datatypes. A similar thing can be done for the HECClient.

Since the information of a single event is contained as an object of subclasses of Astropy ``` Row ``` class, there would be a need to write specific functions in those subclasses to return the event information in the form of a ``` dictionary ```, or a ``` list ``` or simply a ``` Row object ``` too.

### 2. Interaction of the ``` FE ``` object with SunPy objects such as Maps, TimeSeries etc.

Once the Feature and Event class is implemented, what is needed is to write specific functions in the existing SunPy objects for intuitive interaction of the ``` FE ``` object with those objects.

####   Interaction of FE Object with SunPy Maps :

The information obtained from the HEK/ HEC clients can be used to implement certain features in SunPy Maps. The features observed were :

*   Overplotting the event boundaries on a SunPy Map :  &nbsp; Since the HEK client provides only the information regarding the event and not any file/ image displaying the event information, the overplotting feature would provide user a choice either the images of sun during the event can be extracted from the ``` Fido ``` library implemented in ``` sunpy.net ``` or the user may request an overplotting over an existing image.

 For the overplotting over an existing image, the [example](https://docs.sunpy.org/en/latest/generated/gallery/plotting/overplot_hek_polygon.html) mentioned in SunPy Documentation can be implemented. In the other case, the overplotting function would communicate with the Fido module and download required images based on the Time and the Instrument used to observe the event. The downloaded files can be plotted over a map where the event boundary can be overplotted based on the same [example](https://docs.sunpy.org/en/latest/generated/gallery/plotting/overplot_hek_polygon.html) mentioned.

*   Plotting the bounding rectangle as a submap :   &nbsp; This function would also give the user a choice either to input an existing data file or download data. The boundind rectangle can be found by lower left and the top right coordinates returned by the HEKClient as ``` boundbox_c1ll ```, ``` boundbox_c2ll ``` and ``` boundbox_c1ur ```, ``` boundbox_c2ur ``` respecrively. These coordinates would be used to plot a submap from the actual plot of a map using the [example](https://docs.sunpy.org/en/latest/generated/gallery/map/submaps_and_cropping.html) in the SunPy Documentation.

*   Extracting the data from the map that corresponds to the overlapping region :   &nbsp; As mentioned, the function corresponding to this would aim at extracting the overlapping region on the map (either the bounding rectangle or the bounding polygon) and return the data corresponding to that region in the map.

*   Usage of ``` FE ``` object in SunPy Map modules :   This would support the use of ``` FE ``` object as parameter in SunPy Map. The implementation behind this would be to fetch ``` Fido ``` responses based on the HEK/HEC data stored in the ``` FE ``` object and generate a map based on that data stored in ``` Fits ``` file.

These were the few things as thought regarding the interaction of FE object with SunPy Maps. Other ideas would also be implemented based on the advice of the Mentors.

####   Interaction of FE Object with SunPy TimeSeries :

SunPy TimeSeries is a 1-Dimensional data that plots the variation of features like intensity, wavelength etc. with respect to Time over a plot. Instruments like GOES, XRS generate 1-Dimensional data rather than capturing the images of sun during that Event. This the information received from the HEK/ HEC Clients corresponding to these Instruments would be helpful in generating certain TimeSeries Plots. The ideas regarding the interaction of SunPy TimeSeries with ``` FE ``` object is mentioned as :

*   Plotting a TimeSeries corresponding to the responses from HEK/ HEC Client :   &nbsp; This feature would fetch the Fido responses from the Observation Instrument for the given time range and plot the data from those files as a TimeSeries plot. This can either be done as a separate member function in the Feature and Event Class or can also be done in the SunPy TimeSeries module so as to support the usage of ``` FE ``` object in SunPy TimeSeries.

*   Overplotting the HEK/ HEC Client response over a TimeSeries :   &nbsp; This feature would be helpful for the events like Flare where the event has a certain ``` Peaktime ``` at which the event features reach a peak value. The implementation would be based on the [example](https://docs.sunpy.org/en/latest/generated/gallery/time_series/goes_hek_m25.html) in SunPy Documentation.

Other ideas would also be implemented based on the Mentors' Advice.

###   Interaction of FE Object with SunPy ROI :

Since the current ROI Package is under development, the functions for its interaction with ``` FE ``` object would be implemented once the package is developed.

### 3. Changes with HEK/ HEC Clients so as to return responses in the correct datatype

This would aim at changing with the responses fetched from the HEK/HEC servers to be returned as proper Astropy Quantities. I have made a sample [gist](https://gist.github.com/jains8844/ea3159e80bf272d58e85dba55138d7de#file-hek-py-L75) for this. This would be implemented as separate functions that would change the datatypes accordingly.

##   Project Plan

###   Community Bonding Period (May 6 - May 27)

I have my summer vacations starting from May 5. Further I do not have any plans for the vacations. So I will work completely on the project in the Community Bonding Period. I would get in touch with the mentors and SunPy Codebase. I will go through the whole documentation again so as to add the feature I missed out. Also, I will be learning about writing tests using pytest, PEP8 Style Coding. Further I will develop a basic prototype for the Feature and Event Class.

At the end of the Community Bonding Period, I would aim to :

* Get familiar with SunPy's Codebase and the respective Mentors.
* Learn about testing code with pytest and SunPy testing guide and the also the PEP8 Style for writing code.
* Gather more information related to the project from the websites of HEK and HEC Clients.
* Develop a basic prototype for the Feature and Event Class.

###   Coding Period Starts

#### Week 1 (May 27 - June 2)

* Write the basic Feature and Event(```  FE ```) class.
* Gather information regarding the datatype of each information returned by HEK and HEC Clients.

#### Week 2 - Week 3 (June 3 - June 16)

* Writing specific functions to convert the information common to all the events in a single client to their respective Astropy Quantities/ SunPy Datatypes.
* Writing some functions to convert optional information.

#### Week 4 - Week 5 (June 17 - June 23)

* Completing all the functions required to parse the clients information into their respective Astropy Quantities/ SunPy Datatypes.
* Wrapping up all the functions together to develop a basic working template of ``` FE ``` class with data members.
* Beginning the work on interaction of ``` FE ``` object with SunPy Packages.

***
###   Phase 1 Evaluation
***

#### Week 6 - Week 7 (June 25 - July 5)

* Working on the interaction of the ``` FE ``` object with SunPy Maps.
* Writing specific functions in the ``` FE ``` class for implementation on features like overplotting, creatind submap or downloading specific data from ``` Fido ```.
* Writing specific functions in SunPy Maps for the support of use of ``` FE ``` object in the package.

#### Week 8 (July 6 - July 12)

* Working in the interaction of the ``` FE ``` object with SunPy TimeSeries.
* Writing specific functions for overplotting, adding the feature for querying the ``` Fido ``` for the data and checking whether the data is 1-Dimensional or 2-Dimensional.

#### Week 9(July 13 - July 21)

* Writing specific functions in SunPy TimeSeries for the support of use of ``` FE ``` object in the package.
* Checking of the SunPy ROI package is developed. If not, writing specific functions for the features which have been implemented in the ROI package.
* Wrapping up all the functions together to fully develop the Sunpy Feature and Event Class.

***
### Phase 2 Evaluation
***

#### Week 10 (July 23 - July 29)

* Modifying the HEK and HEC Clients which would return information as Astropy Quantities rather than strings stored in the Table returned. This might done by using the functions predefined for the ``` FE ``` class or by writing a set of separate functions.

#### Week 11 - Week 12 (July 30 - August 14)

* Writing tests for everything implemented so far.
* Checking whether everything works fine.
* Writing up the developer documentation.
* Sending a PR for all the work done.

#### Week 13(August 15 - August 25)

* Completing the documentation for the features implemented.
* Writing up gallery examples for the new functions added.
* Discuss about any shortcomings with the mentors.
* Complete the leftover tasks if any.

***
### Final Evaluation
***

##   GSOC

####   Have you participated previously in GSoC? When? With which project?
No, this is the first time I am participating in Google Summer of Code.

####   Are you also applying to other projects?
No, OpenAstronomy(SunPy) is the only organisation I am applying to.

####   Are you eligible to receive payments from Google?
Yes, I am eligible to receive payments from Google.

####   How much time do you plan to invest in the project before, during, and after the Summer of Code?
I have my Summer Vacations in the month of May, June and till Mid July. I am not pursuing any kind of internship during this time nor do I have any plan for the vacations. So, I will be able to give at least 40hrs a week. After the vacations, I will be able to give at least 30hrs a week.

####   Will you continue contributing to SunPy after the Summer of Code too ?
Yes, I will keep contributing to SunPy after the Summer of Code too.
