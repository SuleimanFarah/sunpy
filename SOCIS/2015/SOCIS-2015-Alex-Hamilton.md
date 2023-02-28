About Me
========

- Name: Alex Hamilton
- Studies: 4th Year Astrophysics Masters at Queen Mary University of London, Ongoing Mathematics and Computer Science Student at the Open University
- GitHub: [Alex-Ian-Hamilton](http://github.com/Alex-Ian-Hamilton)
- Languages: English (native)

Background
========

An Astrophysics Masters student at Queen Mary, I am passionate about astronomy, science and technology with a specific focus in solar physics where I plan to do a PhD.
I have been a casual coder since working along with a child's coding book on my dads old BBC micro, I then moved into basic web development and playing with JavaScript and finally started to get formal teaching Object Oriented Programming in Java with the Open University.

My university project this year is based on coronal magnetic field, it involved reading key scientific literature on the subject and implementing a simple version in Python (using SunPy) which I then evaluated both qualitatively using MayaVi visualisation and quantitatively using the Titov-Demoulin Equilibrium model. I have never contributed to an Open Source project and consider this to be the perfect opportunity for me to take what I have learnt and use it to implement tools that everyone can use.

My general interests include climbing, photography, computer gaming and anything sci-fi.

Previous Projects
========

Over the last 2 years I have had the opportunity to do two summer internships:

- RAL was investigating the LHC ATLAS detector metadata usage,
- NPL (the National Physical Laboratory) was mostly lab work, testing the qualitative performance of thermal (IR) imagers,

Both of these projects required that I plan and undertake independent work while collaborating with members of the departments and experts in the fields. Along with valuable coding, troubleshooting and documentation experience I was able to contribute useful insights into the fields for my supervisors.

I also helped on creation of the OpenAstronomy website, designed to promote the work done by 4 major open source astronomy projects.
<https://github.com/OpenAstronomy/openastronomy.github.io/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Aalex-ian-hamilton>

Project
========

The solar Corona is an area of very active research and yet the 3D magnetic field can't be directly mapped except for rare exceptional cases, it can only be inferred by using photospheric magnetograms to extrapolate the magnetic field above.
Basic potential field extrapolations use the Greens Function method, modelling the magnetic field at each point as the integral sum of contributions from each point in the photosphere. An example can be seen in figure 1.

Fig 1: Potential Field Extrapolation from dummy Gaussian boundary data.
![potential field extrapolation over example data](http://i.imgur.com/i0bk2g9.jpg)

More advanced routines use the assumption that the low density plasma in the corona is force-free, where the Lorentz force is equal to zero. The field is the described by:

(&nabla; &times; **B**) = &alpha;**B**       and       **B** &sdot; &nabla; &alpha; = 0

Where alpha is a function of position, leading to a non-linear problem. Simplifications can include using a constant &alpha; to make a linear problem, or setting &alpha; = 0 which leads to the current free potential field.

The Non-Linear Force-Free Field (NLFFF) produce the best results (Wiegelmann et al. [2004]) and can be solved using a number of different numerical methods, for example using optimization method of Wheatland et al. [2000]. The field involves several major families of routine that stem from the different solution methods, these are often implemented on different (coding) platforms by different scientists making generally incremental changes.

The goal of this project is to implement an API for easy creation, updating, distribution and analysis of NLFFF extrapolation models within SunPy using a new object class that would contain the extrapolator code and take a magnetogram map as one of its constructor arguments.
This would ideally be implemented in a way similar to astropy.modeling, and would enable users to either implement in Python, or hook into custom non-python code.

Extrapolations could then be evaluated in two ways:

- Qualitatively: by visualising the field over an active region using MayaVi (see fig 2 below).
- Quantitatively: using semi-analytical solution fields, such as the Titov-Demoulin Equilibrium model and comparing the extrapolated and model fields using various metrics, such as the figures of merit from Wiegelmann et al (2006).

Fig 2: Potential Field Extrapolation, overlaid on the (a) AIA and (b) (c) HMI boundary data.
![potential field extrapolation over genuine data](http://i.imgur.com/hGKvwdL.jpg)

## Proposed timeline
### Week 1 / 2
Implement generic extrapolation framework for potential field extrapolation. Including:

- User API: allows running any of the pre-defined algorithms using user-defined data/parameters
- Dev API: for developing custom extrapolation routines

Additionally, communicate with code authors to see if any would be willing to licence code for use

### Week 3 / 4
Write TD model based testing framework

- generating TD field from initial parameters
- calculating "figures of merit" to compare the two vector fields

### Week 5 / 6
Update all code to Cython for improved performance. Specifically:

- pre-implemented extrapolation algorithm/s
- TD model: code for generating the TD field

### Week 7 / 8
Write examples of verifying the potential field extrapolation with the testing framework.

- using TD model with various parameters
- implementing Gaussian test boundary data that should produce intuitive fields

### Week 9 / 10
Write field MayaVi visualisation framework.

- ability to overlay extrapolated and original vector fields with streamlines and boundary data
- ensure user configurability
- consider possible functions mlab might which to implement to at functionality to the MayaVi API

### Week 11 / 12
Test and document use of using external extrapolation using dev API, i.e. 3rd party Fortran and C++.

- getting some real world code to demonstrate, like T. Wiegelmann's C++
- further communication with code authors RE code licences

### Week 13 / 14
Complete documentation and 3rd party user testing.

Other Info
==========

## Available Platforms
I run Windows 10 Preview x64, Windows 8.1 x64/x86, Windows 7, Mac OS X Yosemite.

I can also run Linux if required.

## Availability
I'm usually available from about 9 am to around 11 pm. My time zone is UTC +1 (British Summer Time - so 0800 to 2200 UTC).
