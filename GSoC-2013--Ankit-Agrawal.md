##Image Processing routines for Map and MapCube in SunPy

##### This proposal is still in progress. Many things are yet to be added, especially the how part of the last two routines to be implemented.
// Please be critical and leave any comments/suggestions you have at any place this way along with thy. - Name.
### Contact and Username info:

***

Name : Ankit Agrawal  

Email : aaaagrawal@iitb.ac.in  

github : [ankit-maverick](https://github.com/ankit-maverick)  

IRC nick : AnkitAgrawal  

Skype : aaaagrawal  
  


### Personal Bio:

***

I am Ankit Agrawal, a third year student enrolled in a 5 year Dual Degree Program(B.Tech and Masters) in Electrical Engineering at IIT Bombay. My Masters specialization is in Communication and Signal Processing. I want to work on the idea of 'Implementing Image Processing Routines for Map and MapCube'. The relevant coursework that I have done in the past related to this project are Linear Algebra, Image Processing, Data Analysis and Interpretation and Computer Vision. Python is the programming language I am most confident with. I also know C++, Java, Matlab and R and have used them in various projects. I have been using many open source softwares for my daily programming purposes and have always felt the desire to contribute back to the open source community. The last few weeks have been very satisfying to me because of the learning curve I have ascended by writing good quality test-driven code in a community reviewed collaborative environment while contributing to some open source projects in Python. Becoming a part of development team of such open source projects requires time to gain trust in the code you write and the decisions you make. Google Summer of Code provides a perfect platform for someone like me to become a part of well established open source project.

### Contributions to Sunpy:

***

* Addition of tests to sunpy.map.map https://github.com/sunpy/sunpy/pull/439
* Minor fixes in documentation and map.peek() https://github.com/sunpy/sunpy/pull/438
* Bug filed https://github.com/sunpy/sunpy/issues/432

### Contributions to Image Processing package scikit-image:

***

### Related Projects
* Image Processing course : [Mini-project 1](http://home.iitb.ac.in/~aaaagrawal/projects/ip_project1.pdf) and [Mini-project 2](http://home.iitb.ac.in/~aaaagrawal/projects/ip_project2.pdf) based on the paper '[Undersampled Radial MRI with Multiple Coils. Iterative Image Reconstruction Using a Total Variation Constraint](http://www-mrsrl.stanford.edu/studygroup/2/Files/Block_2007_Undersampled.pdf)'
* Computer Vision Course Project : Parallel Tracking and Mapping in[Parallel Tracking and Mapping in 3D](https://github.com/ankit-maverick/ComputerVisionProject) 3D using Kinect based on [Parallel Tracking and Mapping for Small AR Workspaces](http://www.robots.ox.ac.uk/~lav/Papers/klein_murray_ismar2007/klein_murray_ismar2007.pdf)
* [Machine Learning and Data Analysis competitions on Kaggle](http://www.kaggle.com/users/43981/ankit-agrawal)

### Proposal Title

##### Implementation of Image Processing routines for Map and MapCube in SunPy

### Proposal Description:

***

A great percentage of analysis in Solar Physics is performed using Images. Hence Image Processing methods play a major role in Solar Data Analysis. Sunpy provides a data-type Map to hold such 2D images and a data-type MapCube, to store a list or series of Maps. This project focuses on implementing important Image Processing routines for the following tasks for the above two classes to improve existing solar image analysis capabilities in SunPy.  

* Sorting and Resampling Maps in a Mapcube and by time, frequency and other units
* Image Registration to align images in a Mapcube
* De-rotating images to compensate for Sun's rotation
* Compensate the observed dimming on the edge of the Sun.

  

### Implementation Timeline:

***

I don't have any other commitment during summer hence I will work the normal 40 hr/week throughout the summer. I will commit at least three times a week to ensure that my code is reviewed regularly by the mentors and I can work on the received feedback immediately. I will be available daily on IRC and weekly on Hangouts as my preferred means of communication. I will report my weekly progress on this blog.

##### Community Bonding Period (27th May - 16th June):
Reading papers mentioned in the reference to select the best possible algorithm for a particular task. Fixing bugs tagged with 0.3 milestone and adding tests to get familiar with the code-base as much as possible.

##### Week 1 and 2 (17th June - 30th June):
Sorting Maps in a Mapcube by time, frequency and other units. This would be implemented using standard sorting algorithms like Quicksort. Routines for Resampling Maps on z-axis.
 
##### Week 3, 4 and 5 (1st July - 21st July):
Implementing Image Registration methods to align the images in a MapCube with a high degree of accuracy. The basic steps in Image Registration are finding the features/keypoints in both the images, correspond/match the detected features in both the images, find the transformation between two images and then align the second image in first's co-ordinate frame.
 
##### Week 6 and Midterm Evaluation Period (22nd July - 2nd Aug):
Buffer period. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.
 
##### Week 7, 8 and 9 (3rd Aug - 23rd Aug):
Implementing a routine for de-rotating solar images in solar coordinates to compensate for the rotation of the Sun.
 
##### Week 10 and 11 (24th Aug - 6th Sep):
Implementing a routine that compensates for the observed dimming on the edge of the Sun.
 
##### Week 12 and Final Evaluation (7th Sep - 16th Sep):
Buffer period. Getting the code design reviewed by the community. Adding tests and documentation. Fixing bugs if any.  

### Reference:
[1](http://library.utia.cas.cz/prace/20030125.pdf) Image Registration Methods : A Survey
[2](http://profs.info.uaic.ro/~ancai/DIP/articole/Image%20Processing%20Techniques%20and%20Feature%20Recognition%20in%20Solar%20Physics.pdf) Image Processing Techniques and Feature Recognition in Solar Physics
[[3]](http://hesperia.gsfc.nasa.gov/ssw/gen/idl/solar/drot_nar.pro), [[4]](http://ssrt.iszf.irk.ru/~grechnev/idl/sunrot.pro) De-rotating Solar Images

***
Please mention any links/pointers/text you know that discuss the algorithms or concepts on tasks I am going to implement, especially on De-rotating images to compensate for Sun's rotation and Compensating the effect of Limb Darkening.