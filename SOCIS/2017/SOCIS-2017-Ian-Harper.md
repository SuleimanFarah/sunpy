Profile
========
- Name: Ian Harper
- Email: harperi@tcd.ie
- GitHub: [IanMichaelHarper](https://github.com/IanMichaelHarper)

Bio
==========
I'm a final year theoretical physics student at Trinity College Dublin. I have just completed my final year. I have worked extensively in Python, particularly in the packages Numpy, Scipy and Matplotlib. I have worked with image reconstruction in the past using singular value decomposition to deconstruct and re-assemble an image to take up less space with minimal loss of image quality.
      I've worked in other languages in the past such as C++ and Processing.js, and I have knowledge of Java, Javascript and HTML. During the summer of 2016 I worked on a physics project at University College Dublin called Social Physics: A Model of Opinion Dynamics. I used processing.js to write a web applet to simulate the effects of opinion dynamics. I also used Matlab to run simulations of a fortran source file to extrapolate data from the opinion system

Proposal
========
I want to work on developing the sunkit-image package. I hope to achieve the following goals:

1. Port the Multi-Scale Gaussian Normalisation code from [#1899](https://github.com/sunpy/sunpy/pull/1899).
2. Convert the [differential rotation code](https://github.com/sunpy/sunpy/blob/master/sunpy/physics/differential_rotation.py) in SunPy to use [`sunpy.coordinates`](https://github.com/sunpy/sunpy/tree/master/sunpy/map).
3. Implement image warping for solar differential rotation. [#1876](https://github.com/sunpy/sunpy/pull/1876).
4. Implement the [OCCULT-2 algorithm](http://arxiv.org/abs/1307.5046) for coronal loop tracing.
5. Implement running and base difference functionality and the persistence transform.
And if time permits, I want to
6. Refactor and write a Python wrapper for [FLCT](https://arxiv.org/abs/0712.4289) [code](http://solarmuri.ssl.berkeley.edu/overview/publicdownloads/software.html).
7. Implement image alignment using feature detection and tracking. [Example](http://scikit-image.org/docs/dev/auto_examples/features_detection/plot_brief.html)

Timeline
========
- Week 1: Study the image processing features of sunpy and plan how to implement the relevant code
- Week 2/3: Study the MGN code and code it.
- Week 4/5: Study solar differential rotation and the differential rotation code. Change to sunpy coordinates.
- Week 6: Start Implementing the image warping algorithm for solar differential rotation. Test and review.
- Week 7/8: Study coronal loop tracing and implement the OCCULT-2 algorithm
- Week 9/10: Study how to calculate running and base difference functionality and implement it with the persistence transform.
- Week 11: Test, debug, clean and optimise code, along with documentation.
- Week 12: Work on refactoring and writing the Python wrapper. Try implement image alignment.

Extra info
==========
- Availability: From 9:00 to 23:00. (UTC-4).
