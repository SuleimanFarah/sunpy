# Metadata only searches with Fido

## Student Information

* Name - Shivansh Mishra
* University - Delhi Technological University (Formerly Delhi College of Engineering)
* About Me - I am an engineering undergraduate student and I am in general interested in open source contribution as I want to give something back to the community, I am always looking for an opportunity to learn something new everyday. Contributing to Astropy has taught me many python tips and tricks. I consider GSoC 2020 as an opportunity that can teach me a lot of things in a short time span.
* Contacts
  * Email - [dHoneysh@gmail.com](mailto:dHoneysh@gmail.com)
  * GitHub - [www.github.com/Dshivansh](www.github.com/Dshivansh)

## Experience as a programmer

* Editor - I prefer using Vim and sometimes when I need all the bells and whistles I use pycharm. I love Vim because it is highly customisable and I can program it to do pretty much anything that I want . I use pycharm mainly for debugging purposes because I don’t like the interface of **pdb**as I cannot see the values of all the variables at all the time.
* Experience in programming - I have some experience in python as well as in C++, I have a strong base in data structures and algorithms. I am also well versed in python and built quite a few projects with python like :
  * Signature recognition - I have built a classifier that uses Convolution neural network as well as XGBoost in order to differentiate forged signatures from genuine signatures.
  * Playlist transfer - When I switched my music streaming platform from spotify to YouTube-Music, I wrote a script in python to create all my spotify playlist in YouTube-Music, now I can transfer almost any spotify playlist to YouTube Music.
  * Notifier - It is a python script that scraped my college’s website at a regular interval and notified the college student’s on telegram if the college put some notice on it.
* Experience with python - I consider myself an intermediate level of python programmer. Since Python is an interpreted language and it is dynamically typed I can do many things with python like creating a class at run time and using it in my code that is practically not possible in many of the languages, list and dictionary comprehension are also some of the features that I miss on other programming language. Metaclass is so far the most advanced feature that I have used in python.
* Experience with Git and Version Control - I know all the basic features of git. I consider myself a beginner when it comes to git, besides git I don’t have any experience with other version-control systems.

## Project Details

### Abstract

---

FIDO ( Federated Internet Data Obtainer) is a unified interface provided by sunpy that is used for searching and fetching of solar physics data irrespective of the underlying client or web service through which data is obtained.

This project will attempt to standardise the response from various clients that back Fido. It will also aim at allowing users to pass various metadata queries thus enabling them to control what can be displayed.

### Detailed Description

---

1. **Standardize the response object returned from all the clients:**

    Most of the work related to this task has already been done by P.R. [#3770](https://github.com/sunpy/sunpy/pull/3770), in this P.R. the (**VSOCLIENT**) and (**JSOCCLIENT**) implements the **Abstract Base Class(ABC) named BaseQueryResponse** thus outputting the response as **QueryResponse Object** and this object in turn act as an input to **UnifiedResponse class** which creates **UnifiedResponse object** which is returned from fido.search().

    However, the implementation of BaseQueryResponse ABC is not done for HEKClient. I plan to implement **BaseQueryResponse ABC** for these clients too thus making them output QueryResponse.

* Implementation in HEKClient - HEK module uses **_download** function to return the output as **HEKTable**which in turn inherits Astropy. Table, I will Implement the  **BaseQueryResponse ABC** for HEK module so that we  can get the output as **OueryResponseObject**which in turn will be passed to **UnifiedResponse Class**to get UnifiedResponse output.

2. **Ability to specify the metadata to be Displayed:**

    The way I am thinking of solving this problem is by creating method named **meta_data_table** which needs to be implemented inside **UnifiedResponse** and this method will return the object which will be encapsulate the Astropy.Table returned from various clients, This object will also contain the **dictionary of metadata columns** whose values will be the index of the **Astropy.Table** that contains such metadata. This will ensure the speedy accessing of the Astropy.Table based on the metadata to be displayed rather than Iterating through the whole list of Astropy.Table.

3. **Returning and Inspecting metadata only queries:**

    By the time of implementing this task all the Clients would have implemented the **BaseQueryResponse ABC,**so all we need to do is implement function that will be using **dispatchfirst**to identify which all client objects can handle the requested metadata searches and according to them an object will be returned that will encapsulate the underlying Astropy.table of the respective clients.

    I will also implement various functions that will help in manipulating the metadata response post search.

### Timeline

---

**Community bonding period(May 4 -  June 1):**

This period of around 1 month will be spent to read the api documentation of various clients and Fido codebase in-depth and to understand the complex workings of Fido.

This time period will also be used to solve some of the issues related to the project that does not directly affect the implementation of the current project like [#3336](https://github.com/sunpy/sunpy/issues/3336), [#3735](https://github.com/sunpy/sunpy/issues/3735), [#3734](https://github.com/sunpy/sunpy/issues/3734).

**June 2 - June 14 (2 weeks):**

Implementing **BaseQueryResponse ABC**for HEKClient.

**June 15 - June 21 (1 week):**

Implementing a container class for manipulating the metadata to be displayed.

**June 22 - July 5 (2 weeks):**

Implementing the _can_handle_query function to register the various queries that can be handled by the clients.

Implementing dispatch first kind of function to identify which client can handle which type of metadata query.

**July 6 - July 12 (1 week):**

Implementing the **repr** function for the metadata object to display it in human-readable form.

**July 13 - July 26 (2 weeks):**

Implementing a cache for Fido so that rerunning the script multiple times does not cause the rerunning of the whole function of fido.search(), thus speeding up the testing process.

This will be implemented by using sqlite in which the response can be stored as a dictionary, once the size of the database exceeds a certain limit we will start to remove the object in it starting from the one that is accessed the least amount of time.

**July 27 - August 8 (2 weeks):**

Implement the object that will encapsulate the Astropy.Table of the various client’s response.

Implement various functions to manipulate these objects, in order to interact with the metadata post search. These functions can provide a functionality like filtering out wavelength greater than threshold from the metadata available, these functions can also provide functionality like conversion of units, like if a particular column of the has the temperature as Fahrenheit and we want to display the metadata as Kelvin then these functions can be used to convert the values.

**August 9 - August 21 (2 weeks):**

These two weeks will serve as a buffer period in case earlier steps of the proposal require more time, unforeseen difficulties arise, etc. If everything runs smoothly and the buffer period is unnecessary, then work on implementing additional features for the Fido.

**August 22 - August 24:**

Write documentation for all previous code and add any tests I may have missed during the main coding period. Look for potential bugs and fix any that arise.If everything runs smoothly and the buffer period is unnecessary, then work on resolving as many old issues related to Fido as possible and also try to port the old clients to Fido that were not added.

### Contribution

---

[Add .items() to Table and Row](https://github.com/astropy/astropy/pull/9780) - Merged

[Include Rankine in imperial units and equivalencies](https://github.com/astropy/astropy/pull/9916) - Merged

[Angle parsing: allow NESW](https://github.com/astropy/astropy/pull/9859) - Merged

[Functional units in CDS tables](https://github.com/astropy/astropy/pull/9971) - Merged

### Miscellaneous

---

#### **Q. Have you participated previously in GSoC? When? With which project?**

I have not participated in GSoC before. This is the first time that I would be participating in GSoC.

**Q. Are you also applying to other projects?**

No. I am not applying in any other projects, earlier I was applying for n-way matcher project in astropy but that was dropped due to COVID-19.

**Commitments?**

I don’t have any internships or other projects to do in summer. I won’t be even having any classes in June and July, so I can fully commit my time to the project. I can easily commit 40 - 45 hours a week to my project.

**Eligibility?**

Yes, I’m eligible to receive payments from Google.
