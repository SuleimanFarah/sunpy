The formal application can be found [here](https://google-melange.appspot.com/gsoc/proposal/review/google/gsoc2013/mattbates/7001#). 

## Proposal Title :

#### SunPy : Local Database of Queried Data

## Personal Bio :

I am a freshman at Virginia Commonwealth University in Richmond, Virginia aiming for a B.S. in Computer Science. I've never contributed to an open source project other than SunPy and am looking forward to this helping me find my place in open source software. The majority of my experience comes from video games I've created and coding competitions that I've participated in. I believe my experience in developing games is especially relevant to the proposed project as having a local database is an idea used frequently in games with online play. While the my knowledge is greatest in Java and C++, python is my next strongest language and I should have no trouble using it.

Solar physics has been an interest of mine for a long time, but one that I have never been fortunate enough to invest into. I've taken all of the available physics and astronomy courses available in high school and my first year in university and am looking forward to do my own independent learning in the subject. I chose the database idea because of my limited knowledge on the subject, but I plan on using this summer's time to learn more about solar physics and continue contributing to SunPy.

## Proposal Abstract :

In solar physics the analysis of observational data plays a big role, and the size of the data files varies from few kB to TB for a whole day observation depending the instruments used. Therefore, it is common that not all the downloaded data is storage in the same place. This project aims to create a personal database which registers the local path where the data is saved, but also some other metadata (wavelength, provider, etc... ). This will benefit the user on being able to choose a sub-set of the data stored locally and by saved on bandwidth if the data is requested again.

## Proposal Detailed Description 

I don't have any other commitment during summer hence I will work the normal 40 hr/week throughout the summer. I plan on implementing things such as tunable capacity and local data compression. I will regularly blog about (among other projects of mine) the problems that I encounter and my achievements in working with SunPy.

##### Week 1 and 2 (17th June - 30th June):
Storage and retrieval of data and metadata on disk.
 
##### Week 3, 4 and 5 (1st July - 21st July):
Adding capacity limits and prioritization of data due to things such as size and frequency of query.
 
##### Week 6 and Midterm Evaluation Period (22nd July - 2nd Aug):
Buffer period. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.
 
##### Week 7, 8 and 9 (3rd Aug - 23rd Aug):
Adding compression of local data, possibly by stripping unimportant or small amounts of re-query-able data or metadata, or simple .rar/.zip archiving.
 
##### Week 10 and 11 (24th Aug - 6th Sep):
Possibly restructuring how test cases are handled, including them by default into the stored data and querying for them like all other data.
 
##### Week 12 and Final Evaluation (7th Sep - 16th Sep):
Buffer period. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.  

## Contributions to Sunpy :

* split(int) function added to time_range 

Thanks to [Ankit Agrawal](https://github.com/sunpy/sunpy/wiki/GSoC-2013--Ankit-Agrawal) for the help setting up this page