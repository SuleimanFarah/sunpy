
# Develop sunkit-image

## Organisation: OpenAstronomy

## Sub-organisation: SunPy

## About me

### Contact Information

* **Name**: Himanshu

* **Time Zone**: IST (UTC+5:30)

* **Chat handle**: himanshukgp

* **Github id**: [himanshukgp](https://github.com/himanshukgp)

* **Email**: [hs80941@gmail.com](mailto:hs80941@gmail.com)

* **Blog**: [wordpress/himanshukgp](https://himanshukgp.wordpress.com/)

### Personal Background

Hello, I am Himanshu, a second year undergraduate student at IIT Kharagpur, India. I'm pursuing a degree in Mathematics and Computing. I love python as it is very intuitive and easy. I work on Ubuntu 16.04 LTS with sublime as editor.

### Education

* **University**: [Indian Institute of Technology, Kharagpur](http://www.iitkgp.ac.in/)
* **Major**: Integrated MS Course in Mathematics and Computing
* **Current Year**: 2nd year (4th semester ongoing)
* **Expected Graduation cum Post-graduation**: 2021

### Links to Pull Requests

Here are some of my contributions to SunPy :

* `Merged`[Map Save Test][2]: Wrote a missing **test** for save method of Map.
* `Merged`[Migrate to hypothesis.strategies.datetimes][3]:

* `Merged`[Decorator to append and/or prepend doc strings][4]: Sometimes we have to add same documentation at multiple points, we can use a decorator which will add a common docstring.
* `Merged` [Adding  python setup.py test --figure-only][5]: This PR adds support to the flag --figure-only. This flag along with **`python setup.py test`** triggers only those tests that create figures.

## About

Project: **Develop sunkit-image**

Mentors: [Stuart Mumford](http://github.com/Cadair),  [Jack Ireland](https://github.com/wafels), [Nabil Freij](https://github.com/nabobalis), [Monica Bobra](https://github.com/mbobra)

## Abstract

This project is to create foundations of the **sunkit-image** a **Sunpy** affiliated package, to contain **image processing** routines and functionality specific to the analysis of solar physics data. The plan of this project is to complete implementations of **MGN, NRGF, OCCULT-2** and **deforest**. Three of these have already been implemented, which have to be fine tuned, **tested**, **documented** and merged into main sunkit-image repository. We have optional extras upon which we can work if time permits and everything goes as planned. It includes implementation of [Soft Morphological Filtering](https://www.aanda.org/articles/aa/pdf/2006/38/aa4852-06.pdf), Refactor and write a Python wrapper for [FLCT](https://arxiv.org/pdf/0712.4289.pdf) code and Implement image alignment using feature detection and tracking.
<br/>

## Problems and Motivation

1. **NRGF**

   We want to visualise the large scale structure of the corona which are studied through white light and polarized brightness (pB) observations. In these images, there is a sharp decrease in brightness of coronal loop with increasing coronal height (radial gradient). Normalizing Radial Graded Filter (NRGF) solves this problem. This algorithm can be directly applied on a `pB` image. White light which contains contribution from F corona, stray light and instruments which need to be removed. This removal of background is done by creating a background image which is subtracted from the desired image.

   While applying NRGF first segment the corona into narrow and `concentric circular regions` called `bins`. Then we calculate mean and deviation of intensity for each segment. Finally at every point on a segment, its mean intensity value is subtracted (thus removing the sharp radial gradient in brightness) from its value and then the result is divided by deviation (to remove radially decreasing brightness contrast). In this way intensity at each point is calculated and we get our final image. This has been implemented by [Wafels](https://github.com/wafels) in [this PR](https://github.com/sunpy/sunkit-image/pull/8). This is now a part of main repository. There is no exact IDL version of this implementation. We will have to decide how to confirm about the results we get from this implementation. We have to add tests, documentation and examples as well. We can also look into its optimization if time permits.
<br/>

2. **MGN**

   Multiscale Gaussian Normalization which we will have in Sunkit-image is based on [this paper](https://link.springer.com/content/pdf/10.1007%2Fs11207-014-0523-9.pdf). In paper an AIA image pre-processed using aia-prep has been used as example. The EUV image is mostly dark and only the active region of Sun is visible. We want to process the image to show more details in quiet sun and off-limb regions. A quick and easy way is to take square root or log of each pixel in the image. Here we will process the image with MGN algorithm. Following is a brief explanation of the algorithm.

   For each pixel in the image we calculate local mean and deviation of intensity values using kernels (weighted by the Gaussian function centred on the pixel).  Then we subtract mean from its intensity value and divide that from its deviation. Then an arctan transformation is applied over all the pixels. These two processes are separately done for n-different values of 2D Gaussian kernel width. A global gamma-transformed image C_g is also created. Then we calculate final processed image by taking a weighted mean among all these images. Gamma transformed image has been given a larger weight in the paper. One last thing is that all these have been shown on an EUV image in the paper but this can be applied as well on other images that we have, like in the result section MGN applied on a LASCO image has been shown in the paper.

   This algorithm has been fully implemented by [Cadair](http://github.com/Cadair) in [this PR](https://github.com/sunpy/sunpy/pull/1899), we also have few examples of this code being run on AIA images. We want to port this implementation to main branch and add tests and documentations.  There is also another implementation [here](https://git.ias.u-psud.fr/ebuchlin/aia-movie/blob/master/medocimage/mgn.py) by [Ebuchlin](https://github.com/ebuchlin). We have to compare both methods and maybe both can exist within this package. There are few differences in the algorithm suggested in paper and IDL version.  We have to carefully spot the algorithmic differences among paper, its IDL version and the two python implementations. After we have successfully implemented this algorithm with all the tests we can even try to compare its result to other algorithms like NRGF on an image (like LASCO), though this is just minor detail to look at when we write examples.
<br/>

3. **OCCULT-2**

   OCCULT-2 is an optimization of Oriental Coronal CUrved Loop Tracing(OCCULT) algorithm. This is used to trace magnetized loops from images of the solar corona. We have to implement this algorithm and write tests and documentations. We also have to look for a known implementation for comparison and validation. We can start by looking at [this](https://hesperia.gsfc.nasa.gov/ssw/packages/mjastereo/idl/tracing_auto.pro) IDL implementation. We have to discuss how we are going to store the traced curve which will actually be a list of pixel locations. Then we will plot it over the actual image and visualise working of our algorithm. I have tried to explain the algorithm below.

    Simply put in our implementation we first enhance the features by using band pass filter and then we trace required curve and finally erase it. OCCULT-2 has few advantages over OCCULT algorithm. OCCULT employed five control parameters while OCCULT-2 uses only `two free parameters` the low-pass filter and the minimum curvature radius to control the output. `Noise` is also handled by using a control factor which ignores faint structures below the base level. Thus, the new version of the code offers a `simpler choice` of control parameters for users. Following are the steps involved in implementing OCCULT-2.

   **Background Suppression**: The median of the intensity values of all the pixels is taken and low intensity values which are less than this median value is set to a base value z<sub>min</sub> = z<sub>med</sub> × q<sub>med</sub>, with q<sub>med</sub> being a selectable control parameter. The median value is a good estimate if content in the given image is limited to less than 50%. This new method is more efficient and flexible in suppressing faint background structures.

   **High-pass and Low-pass filtering**: A low-pass filter smoothes the data while a high pass filter enhances the fine structures within the image. It has been recommended in the paper to use a filter combination of n<sub>sm2</sub> = n<sub>sm1</sub> + 2 which yields the best result, where n<sub>sm1</sub> and n<sub>sm2</sub> represent boxcar smoothing constant for low pass and high pass respectively. So, we can calculate band pass filter using only one of n<sub>sm1</sub> or n<sub>sm2</sub>.

   **Initialization and formation of Loop structure**: The loop is initialised from the `brightest point` in the image, from there we move to first end point and then again from the starting point to other end point. Then we put these two paths as 1 curved path. After the curve is traced area of the loop is erased to zero. Then we repeat the entire process with the residual image until entire image is zeroed out or maximum number of curve traced is reached or when there is no more increase in detected structures with time. The purpose of taking brightest point first is that most dominant curves are traced first.

   **Erasing of traced curve**: Once a full loop has been traced, the loop area is set to zero within a half width of w = (n<sub>sm2</sub>/2 − 1), so that the area of a former detected loop is not used in the detection of subsequent loops. However, crossing loops can still be connected over a gap.
<br/>

4. **IMAGE RESAMPLING (DEFOREST)**

   Many steps of image data analysis, including image co-alignment, perspective reprojection of the solar surface, and compensation for solar rotation, require re-sampling original telescope image data under a distorting `coordinate transformation`. Image resampling is the process to convert an image from one coordinate system to other. As the coordinates are different so input and output will have different grid. An inverse mapping function is applied to the output grid, projecting it onto the input. The result is a `resampling grid`, specifying the locations at which the input is to be resampled. The input image is sampled at these points and the values are assigned to their respective output pixels.

   Re-sampling can be done using `direct interpolation` but this method is not very efficient. In [this paper](https://link.springer.com/content/pdf/10.1023/B:SOLA.0000021743.24248.b0.pdf) an optimised method using the padded ellipse of transformation to approximate the input sampling area for each output pixel, has been proposed. We have to update
 [this PR](https://github.com/astrofrog/reproject/pull/52) by [rubendv](https://github.com/rubendv) to the Astropy [image resampling](https://reproject.readthedocs.io/en/stable/) library. <br/><br/>
<br/><br/>

## Timeline

| Time Period        | Plan           |
| ----------- | ------------- |
| April 23, 2018 - May 14, 2018 **(Community Bonding Period)**      |   <ul><li>Read and understand previous works on image in sunpy repository including rescale and transform.</li><li>**Talk to mentors about details of image testing methods to be used.**</li><li>Work on pseudo code for OCCULT-2 which has not been implemented as of yet.</li><li>Work upon the details of implementation, decide where various utilities can live.</li><li>Discuss on how we update deforest algorithm.</li></ul>|
| | **Part 1 starts** |
| May 15, 2018 - May 21, 2018 <br/> ( 1 week ) | <ul><li>Work to setup `CI` and `documentation` running.</li><li>Port the already implemented codes of MGN to main repository.</li><li>Check if it is in line with the `original algorithm` as suggested in the paper.</li><li>Figure out how [IDL](http://eagle.imaps.aber.ac.uk/mgn.pro) version is different from the [paper](https://link.springer.com/content/pdf/10.1007%2Fs11207-014-0523-9.pdf).</li></ul> |
| May 21, 2018 -  June 3, 2018 <br/>( 2 weeks ) | <ul><li>Work on already implemented and merged NRGF in main repository.</li><li>Decide how it should be rewritten if needed.</li><li>Work upon time `optimization` using Cython if time permits.</li><li>Decide upon the testing routine to be used and start writing image tests using the same.</li></ul> |
|Jun 4,2018 - June 17, 2018 <br/>( 2 weeks )| <ul><li>Complete writing `tests for MGN and NRGF`, resolve errors if any which cause test errors.</li><li>Write detailed documentation and implementing examples.</li><li>This period can act as buffer.</li><li>Write functions and utilities for OCCULT-2 algorithm if time permits.</li></ul>|
||**Part 2 starts**|
|Jun 18,2018 - July 1, 2018 <br/>( 2 weeks )|<ul><li>MGN and NRGF should be merged.</li><li>Implement all the utility functions for OCCULT-2.</li><li>Write tests if time permits.</li></ul>|
|July 2,2018 - July 8, 2018 <br/>( 1 week )|<ul><li>Complete OCCULT-2 tests and docs and well explained examples for users.</li><li>This week can as buffer if OCCULT-2 is not completed in previous 2 weeks.</li><li>Start working on deforest algorithm.</li></ul>|
|July 9,2018 - July 22, 2018 <br/>( 2 weeks )|<ul><li>Port the implementation of `image resampling`.</li><li>Discuss finer details of updating the implementation.</li></ul>|
|July 23, 2018 - Aug 5,2018 <br/>( 2 weeks )|<ul><li>Write tests and documentation for deforest implementation.</li><li>This period can be buffer for deforest implementation and testing.</li><li>Work on optional extras (soft morphological filtering).</li></ul>|
|Aug 6, 2018 - Aug 14, 2018 <br/>(1 week )|<ul><li>Work on any leftover tasks which were stuck before.</li><li>Write tests and docs for soft morphological filtering if implemented.</li></ul>|

### Software packages to be used

**Language:** Python, Cython

**Libraries and modules:** astropy, pytest

## How I propose to complete the project

I previously had some exposure to Image processing tasks during a winter workshop organised in my college. I have grown a lot of interest in this field thereafter. There are lots of materials available online and I will approach to my mentor if I am stuck for long on a given problem. I also plan to discuss new implementation details with my mentors beforehand.

I will push to my pull requests regularly to keep my mentors updated on my work and blog every week as well. I will be available all the time for reviews and answer questions regarding my implementation.  I will also clearly explain everything in documentation so that it is easy to understand in future. We know that sunkit-image is in its very nascent stage so I am very excited about how much we can do in future and interesting things I'll get to learn in the process.

I will also be available in future for any questioning related to my work.

## Benefits to the community

 This project will add MGN, NRGF, OCCULT-2 and Image resampling in Sunkit-Image. We will also have CI and documentation up and running. We will also get some **testing routine** as we have in **Sunpy.** We will have tools to extract coronal loops and extract hidden features in white image through MGN.
 We have few libraries for image processing in sunpy itself. Their is a huge scope on this topic. There are numerous more algorithms which we can implement and fine tune to be available for users. This project will provide a base for sunkit-image for all future works.

## GSoC

### Have you participated previously in GSoC? When? Under which project?

No, I have **not** participated in GSoC before. This is the first time I am participating in GSoC.

### Are you also applying to other projects?

**No** ,This is the **only project** and **SunPy is the only organization** that I have applied for.

### Commitments

I don't have any other internship or work during this summer. I have no plans for any vacations either.

My classes start from 16th of July, even after my classes start I can give about 35 hours a week on this project, as I have around 21 hours of class time every week in my college and there is very less academic pressure during beginning of the course. Also I have  proposed this time mostly for  extras upon which I can keep working even after the program ends.

I have my exams for this semester from 19th April to 27th April so I will be unavailable during this period. I'll start work on preparing detailed layout of OCCULT-2 during first half of April itself to make up for this lost time and then I can discuss more of details with mentors in May during community bonding period. I will have my vacations from **28th of April to 15th of July**. Apart from above mentioned involvements I am free to work on my project but if I get any emergency situation I'll communicate to my mentors and improvise.

### Eligibility

Yes, I am eligible to receive payments from Google.

[2]: https://github.com/sunpy/sunpy/pull/2365
[3]:https://github.com/sunpy/sunpy/pull/2368
[4]: https://github.com/sunpy/sunpy/pull/2386
[5]:https://github.com/sunpy/sunpy/pull/2557
