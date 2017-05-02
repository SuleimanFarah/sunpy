### X-ray Synthesis Imaging

*Suggested Mentor(s):* [Shane Maloney](),

*Difficulty:* Intermediate/Advanced

*Astronomy knowledge needed:* Fourier Transform

*Programming skills:* Python

#### Description

X-ray synthesis imaging is dependent upon deconvolution algorithms to counteract
the sparse sampling in the Fourier plane. Synthesis imaging is often associated
with large radio interferometric arrays but has also been used in X-rays.
Specifically in the solar context in the past with Yohkoh/HXT, currently with
RHESSI and in the future with Solar Orbiter/STIX. Numerous algorithms with
different methodologies have been developed to solve this deconvolution problem.
The objective of this project would be to provide high-level access to
generalised algorithms such as:

* CLEAN
* Multiscale CLEAN
* MEM
* PIXON. 

This could be accomplished by creating pure python implementations (preferred),
creating wrappers around existing implementations or a combination of both. This
would facilitate the comparison of the existing methods as well as any new
methods, it would also allow for ensemble reconstructions in the future.

**Expected Outcomes**

At the conclusion of this project the community will have access to the image
reconstruction algorithms through FOSS in python.

Someone undertaking this project will specifically complete the following:
1. Create suitable representation for generalised visibilities 
1. Implement CLEAN
1. Integrate the resulting images with the existing SunPy `sunpy.map.Map` object
1. Investigate implementation of advanced method(s).

A successful proposal will demonstrate that the applicant has understood the
project and present tasks and timeline for the its completion .


### sunkit-image

*Suggested Mentor(s):* [Jack Ireland](https://github.com/wafels), [Stuart Mumford](http://github.com/Cadair)

*Difficulty:* Beginner

*Astronomy knowledge needed:* None

*Programming skills:* Python


In this project you would create the foundations of the 'sunkit-image' SunPy
affiliated package, a package to contain image processing routines and
functionality specific to the analysis of solar physics data.

#### Description

There have been various proposals for adding image processing and manipulation
code to the SunPy library. SunPy has decided that this functionality will
instead reside in an affiliated package, tentatively named 'sunkit-image'. This
project will setup this package and implement the initial functionality.

There is various functionality that should be added to 'sunkit-image' some of it
already developed, some of it not! This project should achieve some or all of
the following goals (roughly in this order):

1. Port the Multi-Scale Gaussian Normalisation code from [#1899](https://github.com/sunpy/sunpy/pull/1899).
2. Convert the [differential rotation code](https://github.com/sunpy/sunpy/blob/master/sunpy/physics/differential_rotation.py) in SunPy to use [`sunpy.coordinates`](https://github.com/sunpy/sunpy/tree/master/sunpy/map).
3. Implement image warping for solar differential rotation. [#1876](https://github.com/sunpy/sunpy/pull/1876).
4. Implement the [OCCULT-2 algorithm](http://arxiv.org/abs/1307.5046) for coronal loop tracing.
5. Implement running and base difference functionality and the persistence transform. See Figure 2 in [this paper](http://iopscience.iop.org/article/10.1088/0004-637X/736/2/102/pdf) for some ideas.

optional extras:

6. Refactor and write a Python wrapper for [FLCT](https://arxiv.org/abs/0712.4289) [code](http://solarmuri.ssl.berkeley.edu/overview/publicdownloads/software.html).
8. Implement image alignment using feature detection and tracking. [Example](http://scikit-image.org/docs/dev/auto_examples/features_detection/plot_brief.html)


**Expected Outcomes**

* Have copied in and documented and tested the MGN code.
* Have opened a PR to SunPy to convert the `sunpy.physics` module to use `sunpy.coordinates`.
* Have implemented the Map warping code.
* Have got the SunPy PR for coordinates in `sunpy.physics` merged.
* Have implemented OCCULT-2.


