# **Developing Sunkit-Image**

# **Organisation:** Sunpy in Open Astronomy

### Student Information

#### Personal Details

* **Name:** Vatsalya Chaubey
* **Email:** [vc13@iitbbs.ac.in](vc13@iitbbs.ac.in)
* **GitHub:** [vatch123](https://github.com/vatch123)
* **Riot.im:** vatch123

#### Education

* **Institution:** [Indian Institute of Technology, Bhubaneswar](http://www.iitbbs.ac.in)
* **Major:** Electronics and Communication Engineering
* **Current Academic Year:** Sophomore (4th semester)
* **Expected Graduation Year:** 2021

#### Personal Background

I am a sophomore year undergraduate with a deep interest in image processing, computer vision and machine learning. I have been using python for the past one year and have developed a great liking towards the language. I mostly use Ubuntu 18.04 as my operating system and visual studio code as my editor. I am fairly accustomed to Git and GitHub as I have been using it since the last year.

#### Programming Experience

* As per sunpy's GSoC requirement, I have opened a pull request in sunkit-image which implements the [Fourier Normalizing Radial Gradient Filter](https://github.com/sunpy/sunkit-image/pull/17).
* I have also made a critical [comment](https://github.com/sunpy/sunkit-image/issues/1#issuecomment-472108908) on the Multi scale Gaussian Normalization issue which would be essential in resolving that issue.
* I have been using python for most of my projects. Being a computer vision enthusiast most of my projects involve convolutional neural networks. Some of them are [Hindi Handwritten Character Recognition](https://github.com/vatch123/Hindi-Handwritten-Character-Recognition), [Facial Keypoints Recognition](https://github.com/vatch123/Facial-Keypoint-Detection), [MNIST Digit Recognition](https://github.com/vatch123/MNIST).
* I also made a working [Mp3 player](https://github.com/vatch123/Mp3-player) using Python's Tkinter and pygame libraries.
* I am not shy of working with new technologies and have extensively worked with C++ and Java for the last three years. I have built an android [app](https://github.com/vatch123/InstiApp) for the student community of our institute.

#### Open Source Experience

The [pull request](https://github.com/sunpy/sunkit-image/pull/17) which I made in ```sunkit-image``` was the first time when I contributed to a community outside my institution. I have just started with open source project development but I am sure this lack of experience will not be a hindrance. I have ample experience working with Git and GitHub as I have been using it for collaborative projects for the past year. This lack of experience further excites me to learn something new and inspires me to work hard towards a particular problem.

------

### Project: Develop sunkit-image

**Mentors:** [Nabil Freji](https://github.com/nabobalis), [Jack Ireland](https://github.com/wafels)

#### Abstract

This project aims at developing various image processing algorithms and manipulation routines to sunkit-image, an affiliated python package of Sunpy. The analysis of solar images is of paramount to the heliophysics community. Such analysis reveals various factors which affect the Sun and which in turn affect everything here, on Earth. Moreover, the surge in the popularity of python for various data analysis and scientific computing tasks during the past few years makes the need for such a library in python hard to overlook. This project aims at bringing the various solar image processing algorithms under the umbrella of one library.

#### My Motivation

I have always been fascinated by astronomy, the stars and the night sky. It was, for this reason, I joined the astronomy club of my institute. So when I came across Open Astronomy organisation I was immediately attracted. On exploring more in the organisation I came across this project. I chose this project especially because it combines both of my interests - image processing and astronomy. I started working on it by January end, way before the GSoC organisations were declared. I was so attached to this project that I hardly searched for any other projects when the final list of organisations was declared. With this project, I want to become part of the Open Astronomy community and remain a contributor in the long term.

#### My Goals

There are four major tasks along with some optional tasks which need to be done during the GSoC coding period. If everything goes according to the timeline which I have proposed, a little below, I will have enough time to complete the primary tasks and also get my hands dirty on some of the optional ones. The four principal tasks are:

* **Implement the [normalizing-radial-graded filter (NRGF)](http://adsabs.harvard.edu/abs/2006SoPh..236..263M).**

  *Overview*
  There is a sharp decrease in the brightness as one moves radially away from the surface of the sun. This makes it extremely difficult to visualise the coronal density structures because those fine structures are almost washed out from the view. A good algorithm is required to get rid of that radial gradient and one such is the **Normalizing Radial Graded Filter.** In NRGF, the part of the image above the solar surface is divided into various circular rings known as ```bins```. Now, for each bin, the mean and standard deviation of brightness is calculated. These values are then used to normalise every pixel within that bin. This procedure is again repeated for other bins.

  *Deliverables*
  A working [implementation](https://github.com/sunpy/sunkit-image/blob/2e80992ae424a7b4c97343f8e7de4ac11211c8fc/sunkit_image/offlimb_enhance.py#L205), written by [Jack](https://github.com/wafels) is already present in the library which only requires a few more tests and examples. I have already written some tests as part of my [FNRGF pull request](https://github.com/sunpy/sunkit-image/pull/17) and will add some more robust tests. Then a comparison is also to be made among the IDL versions [1](https://hesperia.gsfc.nasa.gov/ssw/packages/nrl/idl/nrlgen/display/nrgf.pro), [2](http://www.heliodocs.com/php/xdoc_print.php?file=$SSW/packages/corimp/idl/nrgf_corimp.pro) and the one written by Jack.

* **Port the Multi-Scale Gaussian Normalisation (MGN) code from [#1899](https://github.com/sunpy/sunpy/pull/1899).**

  *Overview*
  Any solar image contains information distributed over a very wide range of spatial scales. This information is mostly hidden. Processing such an image to retrieve back that hidden information is very important. **Multi-scale Gaussian Normalisation** effectively reduces noises locally revealing the hidden features. It finds the local mean and local standard deviation by convolving the image with a Gaussian kernel. The pixel values are then normalised using them. This process is repeated at different scales i.e. using different widths of the Gaussian kernel. Finally, all the images are combined taking a weighted average. This method is quite effective at bringing those hidden features.

  *Deliverables*
  [Stuart Mumford](https://github.com/Cadair) had originally written a [implementation](https://github.com/sunpy/sunpy/pull/1899) of this algorithm as part of the ```sunpy.image```. That implementation had some differences from the original paper which needs to be resolved. I have already identified those differences and mentioned them in [my comment](https://github.com/sunpy/sunkit-image/issues/1#issuecomment-472108908) on that issue. The only thing left is to rectify them and write some tests. There exists [one more implementation](https://git.ias.u-psud.fr/ebuchlin/aia-movie/blob/master/medocimage/mgn.py) written by [Eric Buchlin](https://github.com/ebuchlin) which applies some novel techniques to the original algorithm. The need and usefulness of those changes have to be validated and if found useful should be incorporated. Some more details and my initial attempt is mentioned in this [gist](https://gist.github.com/vatch123/2a77bb68c414463d7c6efdedc59b121a).

* **Implement the [OCCULT-2 algorithm](http://arxiv.org/abs/1307.5046) for coronal loop tracing.**

  *Overview*
  Coronal loops form the basic structure of the lower corona and transition region of the Sun.  The population of coronal loops can be directly linked with the solar cycle; it is for this reason coronal loops are often found with sunspots at their footprints. So detecting them becomes extremely important. **OCCULT-2** is used to trace magnetized loops from images of the solar corona. There are four major steps in which this algorithm works. First is background suppression in which the pixels having intensities below a certain value are set to median intensity values. It is essentially a method to suppress the detection of background structures. The second step is feature enhancement by passing through a bandpass filter. The third step is the main part where the coronal loop is actually detected. Here we begin at the point having maximum flux intensity and then move based on the direction of the ridge with maximum flux. The final step is to remove the tracked loop such that it is not detected again.

  *Deliverables*
  Implement Oriented Coronal CUrved Loop Tracing (OCCULT) -2 algorithm after comparing the various IDL versions of the code present. This algorithm needs to be implemented from scratch in ```sunkit-image``` seeking inspiration from the paper and the IDL codes [1](https://hesperia.gsfc.nasa.gov/ssw/packages/mjastereo/idl/tracing_auto.pro), [2](https://hesperia.gsfc.nasa.gov/ssw/packages/mjastereo/idl/tracing_auto2.pro), [3](https://hesperia.gsfc.nasa.gov/ssw/packages/mjastereo/idl/tracing_direction.pro), [4](https://hesperia.gsfc.nasa.gov/ssw/packages/mjastereo/idl/tracing_step.pro). This algorithm will be implemented in various sub-routines, each sub-routine corresponding to one of the four steps. I have written a [gist](https://gist.github.com/vatch123/00c38687bfae80a7d8d68794cc2a51e6) describing the above four steps.

* **Implement the [soft morphological filtering of solar images](https://www.aanda.org/articles/aa/pdf/2006/38/aa4852-06.pdf)**

  *Overview*
  **Soft Morphological Transform** is an image processing algorithm which aims at reducing the cosmic ray hits in an image taken by LASCO by training a genetic algorithm on a noisy dataset. This is like training a machine learning model to learn the weight matrices which will be used to perform a particular transformation.

  *Deliverables*
  [Astroscrappy](https://github.com/astropy/astroscrappy) already contains a routine which minimizes the cosmic ray hits in an image. Though the algorithm followed in astroscrappy is not the one mentioned in the [paper](https://www.aanda.org/articles/aa/pdf/2006/38/aa4852-06.pdf). We need to perform thorough testing on that module, if the code written is working for solar data then only tests would be added; if not the entire algorithm would be written from scratch following the paper. Implementing a well-documented algorithm along with complete test coverage. The IDL source code and the training dataset is not available. The training dataset needs to be replicated and the source code needs to be found out.

The optional tasks are:

* Refactor and write a python wrapper for Fourier Local Correlation Tracking [(FLCT)](https://arxiv.org/pdf/0712.4289.pdf).
* Implement image alignment using feature detection and tracking, taking these examples [1](https://github.com/scikit-image/skimage-demos/blob/master/pano/pano.ipynb),[2](http://scikit-image.org/docs/dev/auto_examples/features_detection/plot_brief.html) as inspiration.
* Complete my [pull request]((https://github.com/sunpy/sunkit-image/pull/17)) on Fourier Normalizing Radial Gradient Filter such that it gets merged by the end of the coding period.

#### Timeline

| Time period |      My work plan   |
| ----------- | ------------------- |
|     May 6 - May 27        |  <ul><li>Read the documentation again make myself familiar with all functionalities already present.</li><li>Read all the research papers to get myself familiar with the algorithms which are to be implemented.</li><li>Read and understand all the IDL codes. Read IDL documnetation.</li><li>Develop a pseudocode for the primary tasks.</li><li> Discuss with mentors about the potential discrepancies between the implementation already present and the IDL codes like in the case of MGN.</li><li>Learn about how to write image tests, which will be useful later.</li></ul>  |
|    27 May - 03 June <br> (1 weeks)   |  <ul><li>Complete the implementation of NRGF.</li><li>Write the tests and examples for the algorithm.</li></ul>    |
|       4 June - 9 June <br> (1 week)      |  <ul><li>Rectify the differences between Stuart's Code and the paper.</li><li>Write the tests and examples.</li><li>Go through Eric's Code and incorporate the good changes.</li></ul>    |
|     10 June - 23 June<br>(2 week)        | <ul><li>Write the initial version of the OCCULT-2 algorithm.</li></ul>    |
|       24 June - 26 June      | Phase 1 Evaluation     |
|       24 June - 30 June<br>(1 weeks)  | <ul><li>Complete the OCCULT-2 implementation.</li><li>Finish the testing and documentation of the algorithm.</li></ul>       |
| 1 July - 21  July <br> (3 weeks)   |  <ul><li>Implement the soft morphological transform.</li><li>Test it thorughly along with documentation and examples.</li></ul>|
|    22 July - 26 July <br> (5 days) | Phase 2 Evaluation and **Review Period** <br><ul><li>These five days are as a backup if things don't go according to the plan.</li><li>Complete the remaining tasks which may not be completed till now.</li><li>Make sure all the primary tasks are taken care of.</li></ul>|
|  27 July - 9 August<br>(2 weeks)|<ul><li>Write a python wrapper for the FLCT code.</li></ul> |
|10 August - 16 August <br>(1 week)| <ul><li>Implement image alignment using feature detection and tracking.</li></ul>|
|17 August - 19 August <br> (3 days)|<ul><li>Complete the pull request on Fourier Normalizing Radial Gradient Filter. Write the tests and examples for it.</li></ul>|
|  20 August - 25 August <br> (6 days)| <ul><li>Wrap up everything, make sure everything is working.</li><li>Implement the resampling of solar images, if time permits.</li></ul>|

#### Software Packages Required

* **Numpy:** It will be used throughout the project for performing various operations on the image.
* **Matplotlib:** It will be used to plot various plots and maps.
* **Sunpy:** Various modules like ```sunpy.map``` and ```sunpy.coordinates``` will be used.
* **Astropy:** This will be mainly used for its ```units``` modules.
* **Scipy:** This will be mainly used for simple image manipulation routines like ```scipy.ndimage.filters.gaussian_filter```.

------

### Will I be able to complete the project?

**Yes**, I am very sure I will be able to successfully complete the project. I have been working on this project since the last month and have gained an understanding of how things progress in ```sunkit-image```. My interest in this particular project is also a big driving force for me. I like to challenge myself and I know this project will be a great mix of opportunities and challenges. I will strictly adhere to the timeline which I have proposed. During the entire three months, I would be in frequent contact with my mentors seeking their guidance at the time of need and providing them with information about the progress of my work. In my timeline, I have proposed a review period and time to implement optional features; if things don't go according to the plan I will use that time to complete to the four principal objectives. I truly believe with my skillset, my willingness to learn and work hard; I am suited for this project.

### How will this benefit the community?

During recent years the amount of visual data collected from the sun has increased many folds. Such a huge amount of data requires quick and accurate analysis which cannot be done manually. Secondly, analysis of those data only with the naked eye is not reliable. So a dedicated image processing library is required. After this project ends, ```sunkit-image``` will have the necessary basic features required in such a library. Most of the solar image processing code is written in IDL which is difficult to master. Moving it to a user-friendly language like python would be a great help to the community. Most of the heliophysicists don't want to be bombarded with details of implementation of these algorithms rather they want to use these algorithms as easily as possible without writing much code. So shipping these algorithms as a condensed package would be of great help to them. They would be able to concentrate on the deriving conclusions from the results of these algorithms rather than diving into implementation details of them.

------

### GSoC and I

This is my first attempt at GSoC. I have not participated before. I am applying only to this project - "Developing sunkit-image". I have no other priorities, vacation plans or internships during the summer. I will be able to devote 35 hours of work every week. There may be a few days (two or three) when I might not work as I would be travelling between my college and home. But this will be informed well in advance to my mentors and I will take some extra measures to make up for the lost time. My classes for next semester will begin on 16th July 2019, but I will still be able to devote the same amount of time as there the workload is very light at the beginning of the semester. I am also eligible to receive payments from Google.

----
For any further details or queries, please contact me at [vc13@iitbbs.ac.in](vc13@iitbbs.ac.in).
