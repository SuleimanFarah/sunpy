# Organization: SunPy in OpenAstronomy

### Student Information

* Name: Agneet Chatterjee
* Time Zone: +0530 GMT
* IRC Handle: agneet42
* Github ID: agneet42
* Instant Messaging: Google Hangout(agneet257@gmail.com)

### University Information

* University: Jadavpur University, Kolkata.
* Major: Computer Science
* Current Year: Second Year
* Expected Graduation Date: 2019
* Programme: Bachelor of Engineering(B.E.) in Computer Science and Technology.

### Pull Requests

The following are the Pull requests, Issues (both open and closed) I contributed to:

1. **Updated Index.rst**(#2017) - DocFix to explicitly mention that Sunpy supports 2.7.  and     3.4x.
2. **Added Units Parameter**(#2027)- This PR dealt with adding a Units Parameter to the NDData being used in mapbase.py. As the Unit is instrument dependent it is to parsed from the FITS header in the factory for that particular instrument.
3. **Added Checking of size of data and frequency axis**(#2028) - A function check_dimensions was added to check the length( because data and freq_axis are 1D Arrays) of the two quantities and return an error accordingly.
4.**Removed extract_time**(#2029) - Removed the extract_time function as it dealt with things that weren't dates, as dates. The change was made in time.py and the calling object along with the functon was removed.
5. **Use of loggers in place of print**(#2050) - The aim of this PR is to replace the print() function with loggers as it provides more information to the user, also giving them the opportunity to  choose what they want to see.

### Work and Open Source Experience

Although I haven't really had much experience contributing to Open source Projects before, I have extensive experience in developing projects implementing scientific and mathematical ideas by using Python and its Libraries. I have avid interests in Machine(Deep) Learning, Natural Language Processing.

1. I have worked on Handwriting Recognition using LSTM's using TensorFlow. (link)
2. I have worked on AudioQA using TensorFlow and music21. (link)

Apart from the above projects, I am also proficient in C/C++/Java. Also, I have extensively worked with OpenCV.

### Operating System Experience

Currently, I use Debian Mint. I have previously used Ubuntu and Arch Linux as well and am also familiar with Git and SunPy workflow.

### Proposal Abstract

 I intend to work on the project - **sunkit-image**. The project aims at creating the foundation of a Sunpy affiliated package, ‘sunkit-image'. This package will contain image processing routines and functionalities specific to the analysis of solar physics data. As the project is about adding up a new package, the project aims at adding modules upon which this package can be built upon. They are:

1. _Porting the Multi-Scale Gaussian Normalisation code from [1899](https://github.com/sunpy/sunpy/pull/1899)_ : Multi-Scale Gaussian Normalisation for Solar Image Processing was presented by Huw Morgan and Miloslav Druckmüller([link](https://arxiv.org/abs/1403.6613)). A common approach of processing EUV images is simply to display the square root (or a gamma-curve transformation), or alternatively, the logarithm, of the original pixel values. MGN is a  very efficient process based on localised normalising of the data at many different spatial scales. The method reveals information at the finest scales whilst maintaining enough of the larger-scale information to provide context. It also intrinsically flattens noisy regions and can reveal structure in off-limb regions out to the edge of the field of view.

The pseudo-code has been implemented in #1899 has been mentioned above. There also has been another implementation of MGN by Eric Buchlin ([link](https://git.ias.u-psud.fr/ebuchlin/aia-movie/blob/master/medocimage/mgn.py)).  An interesting observation is that when the code in #1899 is run, it does not have lots of NAN's around the corner whilst the other implementation has lot's of NAN's floating around the corner  probably because the estimate for the width (swi) in the code is zero. The image used was an AIA_171_IMAGE.

The code in #1899 is a much more optimized version of the pseudo code as it reduces temporary arrays in memory without specific prodding. But, in #1899, Line 85 and 86 need to be replaced as the paper states of applying Arctan only to (k*Ci). Also, we need to figure out inconsistencies in the IDL code([link](http://eagle.imaps.aber.ac.uk/mgn.pro)) and the paper and report the same to the author/s, if any.

A few important issues need to be discussed with the mentors such as whether step 1 of the pseudo code should be in the MGN implementation(Replace spurious negative pixels with zero or local mean/median.) or not or should the the choice of how to replace pixels should be left up to the user before the data is input to the filter.  Once these issues are done, a little modification will be made to use Multiprocessing(from Pool) and then the code will be ready to be implemented. Finally new tests have to be created to ensure that our code runs as expected in the most optimised manner.

**Note**: Stuart Mumford, one of the mentors of this project also desired to have _Noise Adaptive Fuzzy Equalization_([link](https://link.springer.com/chapter/10.1007/978-3-319-07148-0_23)) implemented over the summer. NAFE was developed for visualization of high dynamic range (HDR) images produced by the Atmospheric Imaging Assembly (AIA) aboard the Solar Dynamics Observatory (SDO) spacecraft launched by NASA in 2010. This generalization of NAFE widens the usability of the NAFE method to HDR images with extreme brightness gradient and with significantly different parts. This type of images is typical for imaging of solar corona by means of white-light coronagraphs and during total solar eclipses however the method may have much wider field of usage even outside the solar research.

2. _Convert the differential rotation code in SunPy to use sunpy.coordinates_ : The differential code in [link](https://github.com/gbear605/sunpy/blob/90627796b73e66960b3b6bd2b06572b9d385d9ca/sunpy/physics/differential_rotation.py) has provided results such as:
![](https://github.com/agneet42/sunpy_images/blob/master/Diff_Rot.png)

The IDL code has been from [here](https://hesperia.gsfc.nasa.gov/ssw/gen/idl/solar/diff_rot.pro).

The code has a function/s like a diff_rot function which calculates differential rotation of the sun given a duration, latitude, a rotation type and a frame time. It uses astropy.units to take the inputs of duration and latitude where latitude is a heliographic coordinate latitude in Degrees and a rot_hpc function where variables x and y are used which are astropy.units.Quantites representing Helio-projective x and y co-ordinates in arcseconds, respectively.

The aim of this module is to ensure that the sunpy.coordinates functionality is used in all the co-ordinate conversion code. For example,  in rot_hpc, we need to check whether the input is a sunpy-coordinate and then convert it to heliographic co-ordinates. As all the new rotated co-ordinates are calculated in the heliographic co-ordinate system. Also, rot_hpc was named so to make it explicit that helioprojective co-ordinates are being input and returned. So the name too has to change to something less specific

 The sunpy.coordinates has been built off the [Thompson Paper(2006)](http://www.aanda.org/articles/aa/abs/2006/14/aa4262-05/aa4262-05.html)  of which I have had multiple read-throughs over the past few days. So, I have a detailed idea of modules and frames developed from it.
A few links that are good for a read are: A comparison of differential rotation measurements ([link](https://link.springer.com/article/10.1023%2FA%3A1005226402796) ) and A new inversion of solar rotational splitting data ([link](https://link.springer.com/article/10.1007%2FBF00154773))

3. _Implement image warping for solar differential rotation_: Image warping is the process of digitally manipulating an image such that any shapes portrayed in the image have been significantly distorted. Digital image data are now commonly used throughout the ﬁeld of solar physics.

Many steps of image data analysis, including image co-alignment, perspective reprojection of the solar surface, and compensation for solar rotation, require re-sampling original telescope image data under a distorting coordinate transformation.

The goal is to implement image warping for solar differential rotation. There can be different algorithms to implement image warping. There is something like an skimage.transform.warp which warps an image according to a given coordinate transformation.

4. _Implement the OCCULT-2 algorithm for coronal loop tracing_: This Algorithm has to be implemented from the paper Optimization of Curvilinear Tracing Applied to Solar Physics and Biophysics(Markus J. Aschwanden, Bart De Pontieu, and Eugene A. Katrukha.).

OCCULT-2 is a  developed version of Oriented Coronal Curved Loop Tracing(It approached the quality of visually and manually traced loops, detecting a total of 272 loop structures in the same Transition Region And Coronal Explorer image). While OCCULT-2 is an automated pattern recognition code that is particularly well suited to extract one-dimensional curvilinear features from two-dimensional digital images.

The OCCULT-2 algorithm has a few distinct parameters/functionalities:

1. Background suppression: The median, zmed, of an intensity image, zij = I0(xi , yi), is computed, and the low intensity values with zij < zmin are set to the base value, zin = zmed × qmed, with [med being a selectable control parameter, with a default value, qmed = 1.0, if applied, and qmed = 0, if ignored, while a range of 1 < ∼ qmed < ∼ 2.5 is found to be useful for noisy data.
2. Highpass and lowpass filtering: A lowpass filter with a boxcar smoothing constant, nsm1, smooths out the data noise while a highpass filter with a boxcar smoothing constant, nsm2, enhances the fine structure.
3. Initialization of loop structures: The code initializes the first structure to be traced from the position, (xa0, ya0 ), with the maximum brightness or flux intensity, f0a = I0(x0a , y0a ), in the original image, I0(x, y). Once the full loop has been traced, the area of the detected loop is erased to zero, and the next loop structure is initialized at the position, (x0a,y0a) .
4. Loop structure tracing: An initialized structure starting at its flux maximum position, (x0, y0), is then traced in the forward direction to the first end point of the loop and, then, in the opposite direction from the original starting point to the second endpoint. The two bi-directional segments are then combined into a single uni-directional 1D path, si = s(xi , yi), i = 1, ..., ns.

               A solar EUV image of an active region, recorded with the TRACE

![](https://github.com/agneet42/sunpy_images/blob/master/1111.png)

                    A bandpass-filtered (nsm1 = 5, nsm2 = 7) version of the original image rendered in the above figure is shown.

![](https://github.com/agneet42/sunpy_images/blob/master/2222.png)

5. _Implement running and base difference functionality and the persistence transform_ : This model will partially be built off this paper ( [link](http://iopscience.iop.org/article/10.1088/0004-637X/736/2/102/pdf) ) . The detailed analysis of a loop at the loop apex position +698 west and −243 south of the Sun center, which displays prominent oscillations is used for calculating the running and base difference functionalities. Five different differencing schemes are used to analyse a (10*30) pixel data stripe. The module aim is to obtain such results:

![](https://github.com/agneet42/sunpy_images/blob/master/Aschwanden_2011_ApJ_736_102.png)

The difference schemes are also mentioned along with the image/s.

### Post GSoC goals

1. _Writing a Python Wrapper for the FLCT Code_ : To be implemented off this paper ( [link](http://folk.uio.no/eamonms/viktor/flct_1.01-1/doc/flct_technique.pdf)) . This paper deals with a fast, efficient for performing Local Correlation Tracking. The FLCT Code currently has a C version. The aim is to write a Python Wrapper for the same. For this we'll need the [numpy.fft](https://docs.scipy.org/doc/numpy/reference/routines.fft.html) functionality as FLCT uses Fourier Transform in Step 2 of its pseudo-code. Also, help will be taken from the Python/C API Reference Manual for creating the Python Wrapper. ([link](https://docs.python.org/2/c-api/)).
2. _Implement image alignment using feature detection and tracking_ : To be implemented off this paper( [link](https://www.robots.ox.ac.uk/~vgg/rg/papers/CalonderLSF10.pdf) ) .  The BRIEF binary descriptor uses the fact that  that image patches could be effectively classified on the basis of a relatively small number of pairwise intensity comparisons. It simply  creates a bit vector out of the test responses, which are computed after having smoothed the image patch.
3. _Implementing NAFE_( as mentioned above ) .

### Software packages to be used

Matplotlib, SunPy, Scikit-Image, Scipy.

### How I propose to complete this project

 I have been contributing to SunPy since mid-February. Initally I spent my time lurking around the IRC and mostly getting to know about SunPy, by talking to the mentors. Then, I tried understanding the code-base of SunPy and how it implements its framework using python. Upon my one interaction with Cadair on this project ,I realised I needed to read up on a few papers upon which this project relies completely upon(mentioned above). I spent a lot of time studying the papers and the pseudo codes  and getting to understand its functionalities and figured out how one would approach the implementations in the most optimised manner. I would consult stackoverflow and the regular sources Google, Python, Scikit-image docs etc for solving the pre-processing step. Also, I would require the help of my mentor/s for understanding the very intricate Solar Physics details, which will help me implement my work in a more comprehensive way.

### Deliverables

An image processing module that will contain implementations of various image processing frameworks related to Solar Physics. To start off with it'll contain the implementation of Muti-Scale Gaussian Normalisation. Following it, will be changes in the Differential Rotation code to use sunpy.coordinates along with the Image Warping Functionality. This will be followed by the Implementation of the OCCULT-2 algorithm along with coding the base difference functionality. This will be 3 months of GSoC.
This will be followed by a post-GSoC Endeavour which will involve writing a Python Wrapper for the FLCT Code, followed lastly by the implementation of the BRIEF Binary Descriptor in the Solar Physics Domain.

### Benefits to the Community

This package will lay the foundations of a currently absent module in SunPy which explicitly deals with Image Processing Techniques. As an organisation, SunPy will diversify its domain. Also, the algorithms that will be dealt with here have never been implemented in Python and SunPy would be the very first one to do so. Also, this package would mean that users can deal with Image Processing on the same platform as other functionalities. All in all, this would make SunPy a very comprehensive tool, also opening its door to Computer Vision.

### Timeline

I would be writing documentation, tests and doctests along with writing the code for the module proposed in the project. This would make sure that mentors are able to understand my ideas lucidly, to ensure correctness and ease of maintainability. I would be opening PRs regularly so that SunPy developers can review my code and provide valuable feedback. I would also be pushing regularly to my own fork so that mentors can keep track of my progress.

_May 5 - May 30(Community Bonding Period)_:
 Discuss with the mentors on firstly, the changes to be made in the MGN implementation and whether any inconsistencies occur between the IDL Code and the paper, secondly get well-versed with sunpy.coordinates and it's various dependencies on other functionalities. Decide upon the best implementation of image warping in Differential Rotation Code and its scope and also the most optimised way to deal with the OCCULT-2 algorithm. Optimisation is a very important factor as we'll be dealing with numpy arrays here.

_May 30 - June 12(2 weeks)_:
 Setting up the package repository on GitHub and get the CI started. This period will be focused on porting the MGN code. Once, we have reports of any inconsistencies coming out from the community bonding period, the changes will be made in the code. Changes will be made in the code to ensure proper warnings are displayed when a nan value is encountered so the user is above of the same. Also, changes are to be made depending on whether spurious negative pixels are to be replaced as mentioned in the paper or left to the user. Multiprocessing will be added to the code. New tests are to be added.  All the steps, along with the assumptions(if any) will be documented.

_June 12 - June 25(2 weeks)_: This part will be dedicated to converting the differential rotation code to use sunpy.coordinates. The inputs need to be checked for sunpy coordinates and changed accordingly into heliographic co-ordinates. Tests will be added and will be documented. A PR will be opened to SunPy after making the above changes, such that sunpy.physics is modified to use sunpy.coordinates. If there are nans and infs in the map, a masked map is probably the best way to inform further code about what to do. This would move the handling of nans and infs on to numpy, and the user. In this case, there should be documentation in this code to explain to the user that masked maps are the best way forward.

_[4 day evaluation] June 25 - July 8 ( 2 weeks)_:
 This portion will deal with implementing Image Warping in the Differential Rotation Code that has been worked upon in the previous two weeks. This would involve the following steps:

1. Singular value padding: This carries out optimized re-sampling of a single pixel under an arbitrary coordinate transform in n dimensions, using the padded ellipse of transformation to approximate the input sampling area for each output pixel.
2. Optimization steps include Pre-Scaling and implementing each steps for all pixels in parallel.

Reference :[link](https://www.researchgate.net/publication/225223216_On_Re-sampling_of_Solar_Images)

Also, [skimage.transform.warp](http://scikit-image.org/docs/dev/api/skimage.transform.html#skimage.transform.warp) can be dealt with here.

_[4 day evaluation from July 24-28]July 8 - July 28(3 weeks)_:
 This section will be about implementing the OCCULT-2 Algorithm. This will be implemented by taking into care the different parameters upon which OCCULT-2 depends upon from Background Suppresion to High and Low Pass Filters to running the loop structure. As this will be implemented from scratch, we will be ensuring about proper outputs, about RunTime errors occuring(if any). The code will be tested upon different types of solar images, one from the TRACE spacecraft, one from the SDO spacecraft and one from a ground-based solar telescope. Different parameters will be dealt upon with such as Brightness Range, Minimum Curvature, Number of Long Loops etc.. Similarly as the paper states, the efficiency and accuracy of automated curvilinear tracing will be controlled by a number of tuning or control parameters to ensure accuracy of the code. All this will be properly documented

_July 28 - August 21(3 weeks)_: This timeframe will be dedicated to the implementing the 4 differencing schemes, i.e. the baseline difference, the one-sided running difference,  the symmetric running difference and the minimum running difference.

To discern the oscillating loop,the image has to be logarithmically scaled to intensify it. Then, we need to create time-slice plots with different time frames and then apply a high pass filter to our given region of interest before applying these differencing schemes. We might face a certain difficulty here as scikit-image might not be fine tuned for such high intensity images. Tests/docs to be added.

_August 21 - August 29(1 week)_: The final week. Would clean up code (make it PEP8 compliant), docs, fix/add tests if required. This can also serve as a buffer week and work on adding support for NAFE could be thought about. (on discussion with mentor).

_August 29 - September 5(1 week)_: Mentors submit final project reports to Google.

_September 6_: Final results of Google Summer of Code 2017 announced.

### Commitments

I don't have any other internships or work ( I don't plan on having any ) for the summer. I don't have any plans to go on vacation either.

My classes for the new semester will begin from the 31st of July, but I would still be able to give sufficient time for the project as the academic load is very less during the initial few weeks of the semester. I will be able to work 42 hours for the project per week before my classes start and 35-40 hours from thereafter.

Also, because my summer vacation starts from the 6th of May, I will start working on the project early so that I can try to complete the project well before the deadline ( around 2-3 weeks before the deadline ). This will also ensure that any extra unforeseen and time consuming challenges will be taken care of.
Also, I have not participated in Google Summer of Code before.

### Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact me at agneet257@gmail.com .
