# [SunPy] sunkit-image and Integration with sunpy

## Personal Info
* Name: Akhoury Shauryam
* Email: akhouryshauryam@gmail.com
* GitHub: @Satan-Claws
* LinkedIn: https://www.linkedin.com/in/akhoury-shauryam-a87195221/
* CV: https://drive.google.com/file/d/1J4UAjaHdOQLooYzPFiG7SPnT4MjmfEZk/view?usp=sharing
* University: Chennai Mathematical Institute, India
* Time Zone: GMT +5:30

I am Akhoury Shauryam a final year undergraduate student at Chennai Mathematical Institute from India. I am pursuing my degree my B.Sc (Hons) in Mathematics and Computer Science. After my graduation in May, I plan to start higher studies for my Master's Degree in Computer Science in August. 

## GSOC Experience 
* **Have you participated in GSoC previously?** I haven't, this is my first time applying to a GSoC Organization.
* **Are you also applying to other projects?** Yes, I will be applying to another SunPy project: Scraper rewrite
* **Are you eligible to receive payments from Google?** Yes, I am eligible.
* **How much time do you plan to invest in the project before, during, an after the Summer of Code?** Before the Summer of Code, I'll be able to spend around 18 hour as expected, but during the coding period, all my attention will be upon the project, hence I can give up and above 21 hours a week (3 hours daily). I won't have any other commitments during the time period. And after Summer of Code, I plan to look into bug fixes within my domain, and help people out starting with SunPy. 

## Programming Experience 
* **What is your experience with programming?** I have been programming since 2015, and have had internships during my studies that involved Python, Julia and C++. And as my dual major focuses on Computer Science, I have experience in Theoretical CS as well as rigorous programming through my courses. I've followed Competitive Programming ever since my 1st year and have taken a few courses that had dev projects.
I am experienced with GitHub and Linux as I've needed both during my Courses, Internships and Personal Projects. 
* **What is your experience in Python** I'd say Python is my favorite language so far, I've been using it since 2018 and I've had multiple projects which involved Python. A lot of my courses are ML focused so I had to learn some advanced Python. And 2 of my previous Internships were solely based on it. This semester I also worked on developing a tool to verify properties of a given feed forward network, all of it in Python. I have experience in both dev work and data analytics using Python. I'm linking the Python solo project I had the most fun during https://github.com/Satan-Claws/Project-Val-Recolor.
* **What is your experience with open source software?** Open Source to me feels like an amazing concept where someone has an idea and people interested in it contribute further to it and it is all available to the whole wide world. In the recent years, I've been using more and more Open Source as I learned more and more about Git. And I believe it being Open gives everyone an opportunity to learn and contribute with the community. As for my contributions to Open Source, I worked with Nordic Earth System in Summer of 2022 for analysis of satellite data for an open source project. Further, during Sep-Nov of 2022, I setup and contributed to NISTTests.jl under XKDR, a WIP Julia Library to calculate how precise a Linear Regression model is. Both of these internships helped me more learn about Git and Open Source through a practical approach. For more information, please refer to my CV.

## Contributions to SunPy
* Fixed #6615 through PR #6791 which adds fixes in the docs along with removing `.svg` files from pre-commit since `.svg` files were throwing errors.
* Assisted in PR #6835 which adds example for`mplcairo`  blending.
* Opened issue #6808 "Installing a clean fork with docs dependencies does not succeed on Windows" where installing dev version of `sunpy` pulled `sunkit-image` but that in return pulled an older version of `sunpy` and hence created an error. It was fixed in #6810

## Project Details
* **Why this project?** I have always been interested in Astrophysics since my School years and SunPy to me feels like a possible way for me to contribute to the field using my own expertise. 
* **What do you want to achieve and what excites you about the project?** I hope to be able to fix the issue at hand and improve the performance if possible. I have worked with different codebases in the past but not of this size, I expect it'll be a learning experience for me and I learn more about the Open Source practices on such a large project. 
* **Why are you suited to work on this project?** I have worked with `AstroPy` and `SunPy`, and recently looked into how `sunkit-image` works. I have great problem solving skills and a lot of experience working with Python and Object Oriented Programming. I have worked on a few issues @sunpy successfully. And I like to work hard, especially on challenging problems.
* **How would you implement the project?** Firstly I'll discuss with the mentors as to what Data Structure will suit us best and why. From that I'll figure out what each function does through the in-code documentation and attempt to fix it with the given specifications. I'll make a list of all functions that need refactoring and start with the low hanging fruits, and with that learned experience tackle the rest. I have worked with `Sphinx` before so I'll add the example gallery as needed after refactoring the `coalignment` module. I plan to regularly test for bottlenecks apart from a dedicated period for it, to gain knowledge on what needs changing. I have laid out a plan below.
* **What do you wish to gain from Google Summer of Code?** The primary thing I wish to gain from Google Summer of Code is experience. I want to learn how I can contribute better a large codebase. During the few issues and bug fixes along with looking at how the code works, I learned different practices that such a large codebase needs to follow. I hope I'll be able to be contribute/help and through it gain more knowledge.

## Development Schedule:
### Community Bonding Period (May 4 - May 28):
#### During this period I'll be discussing the topic with the mentors. I will cover all the pre-requisites required and figure out details about regular updates and meeting schedule. In this phase I'll also fine tune the project timeline after discussions to keep the project smooth. 
#### I already have a working development enviornment, so I'll familarize myself more with `sunkit-image` and figure out what functions I need to refactor.
---
####  Coding Period Begins (May 29):

#### Week 1 (May 29 - June 5)
*  Decide wether to use `NDcube` or `sunpy.map.Map` and modify a few function accordingly.
#### Week 2 (June 5 - June 12)
* Continue to modify functions with the needed specifications.
#### Week 3 (June 12 - June 19)
* Start refactoring the `coalignment` module.
#### Week 4 (June 19 - June 26)
* Complete refactoring the `coalignment` module.
#### Week 5 (June 26 - July 3)
* Modify upwards of 50% of the needed functions for First Evaluation.
#### Week 6 (July 3 - July 10)
* Work on coalignment and persistence transform example to gallery.
- - -
#### First Evaluation (July 14)
- - -
#### Week 7 (July 14 - July 21)
* Look into getting consistent input types accross functions.
#### Week 8 (July 21 - July 28)
* Finish modification for all functions in `sunkit-image`.
#### Week 9 (July 28 - August 4)
* Profile performance of the current functions to find bottle necks.
#### Week 10 (August 4 - August 11)
* Improve performance wherever possible.
#### Week 11 (August 11 - August 21)
* Finalize the working model and evaluate things that need fixing/commenting. 
#### Final Week (August 21 - August 28)
* Wrap up the final functioning project for submission.
---
#### Final Evaluation (August 28)
---