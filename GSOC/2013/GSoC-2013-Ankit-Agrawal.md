## SunPy : Implementation of Image Processing routines for Map and MapCube

## Contact and Username info

Name : Ankit Agrawal
github : [ankit-maverick](https://github.com/ankit-maverick)
IRC nick : AnkitAgrawal
Blog : <http://sunpythonic.blogspot.com>

## Proposal Title

### SunPy : Implementation of Image Processing routines for Map and MapCube

## Personal Bio

I am Ankit Agrawal, a third year student enrolled in a 5 year Dual Degree Program(B.Tech and Masters) in Electrical Engineering at IIT Bombay. My Masters specialization is in Communication and Signal Processing. I want to work on the idea of 'Implementation of Image Processing Routines for Map and MapCube'. The relevant coursework that I have done in the past related to this project are Linear Algebra, Image Processing, Data Analysis and Interpretation and Computer Vision. Python is the programming language I am most confident with. I also know C++, Java, Matlab and R and have used them in various projects.

I have been using many open source software for my daily programming purposes and have always felt the desire to contribute back to the open source community. The last few weeks have been very satisfying to me because of the learning curve I have ascended by writing good quality test-driven code in a collaborative environment while contributing to some open source projects in Python. Becoming a part of development team of such open source projects requires time to gain trust in the code you write and the decisions you make. Google Summer of Code provides a perfect platform for someone like me to become a part of well established open source project.

I have been interested in Astronomy since last two and a half years at my university. In the last two semesters, I have found my interest Image Processing and Computer Vision and want to pursue my Masters(next two years) in the same. Solar physics involves a great deal of analysis on Solar Images which makes the use of Image Processing techniques very prominent. Because of the above reasons, I would like to become a part of core development team of SunPy and contribute to the Image Processing needs of the library in future.

## Proposal Abstract

A great percentage of analysis in Solar Physics is performed using Images. Hence Image Processing methods play a major role in Solar Data Analysis. Sunpy provides a data-type Map to hold such 2D images and a data-type MapCube, to store a list or series of Maps. This project focuses on implementing important Image Processing routines for the above two classes to improve existing solar image analysis capabilities in SunPy.

## Related Project Experience

* Image Processing course : [Mini-project 1](http://home.iitb.ac.in/~aaaagrawal/projects/ip_project1.pdf) and [Mini-project 2](http://home.iitb.ac.in/~aaaagrawal/projects/ip_project2.pdf) based on the paper '[Undersampled Radial MRI with Multiple Coils. Iterative Image Reconstruction Using a Total Variation Constraint](http://www-mrsrl.stanford.edu/studygroup/2/Files/Block_2007_Undersampled.pdf)'
* Computer Vision Course Project(WIP) : [Parallel Tracking and Mapping in 3D](https://github.com/ankit-maverick/ComputerVisionProject) using Kinect based on [Parallel Tracking and Mapping for Small AR Workspaces](http://www.robots.ox.ac.uk/~lav/Papers/klein_murray_ismar2007/klein_murray_ismar2007.pdf)
* Implementation of [Search Engine features](https://github.com/ankit-maverick/InformationRetrievalassignment) : Predicting Similar Queries, Query Auto-completion, Spell checker using 20M query data from AOL
* Machine Learning and Data Analysis competitions on [Kaggle](http://www.kaggle.com/users/43981/ankit-agrawal)

## Contributions to Sunpy

* Addition of tests to sunpy.map.map <https://github.com/sunpy/sunpy/pull/439>
* Minor fixes in documentation and map.peek() <https://github.com/sunpy/sunpy/pull/438>
* Bug filed <https://github.com/sunpy/sunpy/issues/432>

## Contributions to Image Processing package scikit-image

* Basic Pixelwise Image Transforms(WIP) <https://github.com/scikit-image/scikit-image/pull/505>
* Upsampling and Downsampling of Images(Downsampling similar to superpixel() in sunpy.map.map)(WIP) <https://github.com/scikit-image/scikit-image/pull/511>

## Proposal Detailed Description

### Deliverables

By the end of the summer, I intend to have delivered routines for the following tasks in Map and MapCube class:

* Sorting Maps in a MapCube and by time, frequency and other units
* Resampling Maps in a Mapcube along the z-axis.
* Image Registration to align images in a Mapcube.
* De-rotating images to compensate for Sun's rotation.
* Compensate the observed dimming on the edge of the Sun.
* Constructing Synoptic Maps from a MapCube.

### Commitment and Communication

I don't have any other commitment during summer hence I will work the normal 40 hr/week throughout the summer. I will commit at least four times a week to ensure that my code is reviewed regularly by the mentors and I can work on the received feedback immediately. I will be available daily on IRC and weekly on Hangouts as my preferred means of communication. I will reply to mails within 12 hrs of their reception. I will report my weekly progress [on this blog](http://sunpythonic.blogspot.in/).

### Implementation Timeline

##### Community Bonding Period (27th May - 16th June)

* Reading papers mentioned in the reference and discussing implementation details and possible ideas with the mentors to finalize the best possible algorithm for a particular task.
* Fixing bugs tagged with 0.3 milestone and adding tests to get familiar with the code-base as much as possible.

##### Week 1 (17th June - 23rd June)

Sorting Maps in a Mapcube by time, frequency and other units. This would be implemented using standard sorting algorithms like Quicksort.

##### Week 2 (24th June - 30th June)

Adding a method for resampling Maps in MapCube along z-axis by a factor.

##### Week 3, 4 and 5 (1st July - 21st July)

Implementing Image Registration methods to align the images in a MapCube with a high degree of accuracy. The basic steps while implementation would be to -

* deshake the series of Maps in Mapcube using Sun's center as the reference
* find the features/keypoints in both the images
* correspond/match the detected features in both the images
* find the transformation between two images and then align the second image in first's coordinate frame.
A reasonable first implementation would be completed in two weeks with scipy.ndimage as the base library followed by improvements and optimizations in the next week to achieve high accuracy.

##### Week 6 and Midterm Evaluation Period (22nd July - 2nd Aug)

Buffer period. Finishing off any previous incomplete work. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.

##### Week 7, 8 and 9 (3rd Aug - 23rd Aug)

Implementing a routine for de-rotating solar images in solar coordinates to compensate for the rotation of the Sun as mentioned in [4] and [5] in reference section. Related issue : <https://github.com/sunpy/sunpy/issues/358>

##### Week 10 (24th Aug - 30th Aug)

Adding a routine that compensates for the observed dimming on the edge of the Sun using the Limb Darkening equation.

##### Week 11 (31st Aug - 6th Sep)

Implementing a method for generating Synoptic Maps from MapCubes as described in [7] and  [8] of reference section.

##### Week 12 and Final Evaluation (7th Sep - 16th Sep)

Buffer period. Finishing off any previous incomplete work. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.

##### Post GSoC

Implementing more Image Processing ideas that I get or get suggested by the community.

## Reference

[(1)](http://library.utia.cas.cz/prace/20030125.pdf) Image Registration Methods : A Survey

[(2)] (<http://szeliski.org/Book/drafts/SzeliskiBook_20100903_draft.pdf>) Computer Vision by Richard Szeliski : Chapter 6 , Pg. no. 309, Feature based Alignment

[(3)](http://profs.info.uaic.ro/~ancai/DIP/articole/Image%20Processing%20Techniques%20and%20Feature%20Recognition%20in%20Solar%20Physics.pdf) Image Processing Techniques and Feature Recognition in Solar Physics

[(4)](http://hesperia.gsfc.nasa.gov/ssw/gen/idl/solar/drot_nar.pro), [(5)](http://ssrt.iszf.irk.ru/~grechnev/idl/sunrot.pro) De-rotating Solar Images

[(6)](http://astrowww.phys.uvic.ca/~tatum/stellatm/atm6.pdf) Limb Darkening

[(7)](http://sun.stanford.edu/synop/), [(8)](http://solar.physics.montana.edu/nuggets/2002/020215/020215.html) Synoptic Maps
