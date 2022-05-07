# SoCiS 2017 - Proposal

## Idea

X-ray VIsibility Synthesis ImagiNg or Xray-VISION

## Self introduction

### Basic informations

**Name:** Gábor Péterffy

**University:** Eötvös Loránd University, Hungary

**Field of study:** Physics

**Level:** Physics MSc II. semester

### Skills, background

I am a Physics MSc student who is interested in computational physics. My current student scientific research is in the field of material physics (I am developing a new more efficient 2D edge dislocation simulation toolkit), but I was always interested in other fields as well.

Well known programming languages, toolkits, etc...:

* python (and several important libraries like scipy, numpy, matplotlib, plotly, etc...)
* c++
* c
* OpenCl
* Qt
* Bash
* Java

For my everyday work I use Arch Linux. I have now more than 8 years experience with programming and I countinously train myself in this field beside the university. I am required to use python everyday because of the university. Some courses required to get to know to anaconda and jupyter notebook as well. I also had signal processing courses and laboratories before. I am also experienced with git and svn.

Previously I took part first in SOCIS 2014 where I was selected by Marble. I created a feature to be able to place panorama placemarks and view them just like in Google Earth. My blog entry about it is [here](http://pgabor.blogspot.com/2014/09/socis-2014-is-over.html).

I also took part in GSOC 2015, selected again by Marble. That summer I worked on to port Marble to Android and my task was to develop a basic user interface with navigation. More can be found about it on my GSOC [blog](http://pgabor.blogspot.com).

## Technical details about the proposal

### Background of the problem

During synthesis measurements it is not always possible to create a baseline graph where the baselines are following a regular pattern (this can be caused by e.g. malfunctioning equipment, interference, ...). These gaps are easily result in uninterpretable maps. The aim is to provide algorithms which can compensate the side effects as much as possible. [Reference.](http://adsabs.harvard.edu/abs/1974A%26AS...15..417H)

For this, several algorithms and techniques have been created: Model fitting, interpolation procedure, CLEAN, Multiscale CLEAN, MEM, PIXON 1,2, ...

### Concept

Tasks in order:

1. Creating a new package for synthesis tools and algorithms:  e.g. _SunPy synthesis_ (based on the current structure of the API)
1. Developing tools to be capable to display the data before any modification
1. Implementing the iterative CLEAN method (with proper documentation as it in the coding guide line) in the way like it is described in 4 points in the original article
1. Integrating the result images with `sunpy.map.Map`
1. Creating tests for the algorithm
1. Investigating an other method
1. Implementing it
1. Creating test cases

The 6-8. points are optional and can be repeated as many times as the coding period enables it.

### Dependencies

For the above outlined package at least one numerical scientific library would be needed (eg. scipy), but because it is already part of the dependencies of SunPy it does not cause any overhead.

## Timing

Because I am new to the code base of SunPy I would like to spend the first week with playing around with it, making little experiments, etc.

* **Week 2:** Start to work on the misc part of the task
* **Week 3-4:** Start to work on the implementation of CLEAN
* **Week 5-6:** Creating test cases, validating the results, updating the documentation with several examples
* **Week 7:** Start to investigate a new algorithm
* **Week 8-9:** Implement it
* **Week 10:** Creating test cases and validating the results
* **Week 11-12:** Buffer weeks - in case of something unexpected happens during the previous weeks. If everything is fine a new algorithm at least have to be started.

### Before known occupations

* In middle July I will be on a vacation for less then one week.
* I am going to be on a conference at the beginning of August for one week.
