About Me
========
- Name: Alex Hamilton
- Email: a (dot) i (dot) hamilton (at) se11 (dot) qmul (dot) ac (dot) uk
- Studies: 4th Year Astrophysics Masters at Queen Mary University of London, Ongoing Mathematics and Computer Science Student at the Open University
GitHub: Alex-Ian-Hamilton
- Languages: English (native)

Background
========
An Astrophysics Masters student at Queen Mary, I am passionate about astronomy, science and technology with a specific focus in solar physics where I plan to do a PhD.
I have been a casual coder since working along with a child’s coding book on my dads old BBC micro, I then moved into basic web development and playing with JavaScript and finally started to get formal teaching Object Oriented Programming in Java with the Open University.

My project this year is based on coronal magnetic field, it involved reading key scientific literature on the subject and implementing a simple version in Python (using SunPy) which I then evaluated both qualitatively using MayaVi visualisation and quantitatively using the Titov-Demoulin Equilibrium model. I have never contributed to an Open Source project and consider this to be the perfect opportunity for me to take what I have learnt and use it to implement tools that everyone can use.

My general interests include climbing, photography, computer gaming and anything sci-fi.
 
Project
========
he solar Corona is an area of very active research and yet the 3D magnetic field can’t be directly mapped except for rare exceptional cases, it can only be inferred by using photospheric magnetograms to extrapolate using the Non-Linear Force-Free Field (NLFFF) equations.
This area of research involves several major families of routine, implemented on different (coding) platforms by different scientists making generally incremental changes.

The goal of this project is to implement an API for easy creation, updating and distribution of NLFFF extrapolation models within SunPy using a new object class that would contain the extrapolator code and take a magnetogram map as one of its constructor arguments.
This would ideally be implemented in a way similar to astropy.modeling, and would enable users to either implement in Python, or hook into custom non-python code.

Extrapolations could then be evaluated to one of the semi-analytical solution fields, such as the Titov-Demoulin Equilibrium model and visualised using MayaVi.


##Proposed timeline
###Week 1 / 2
Implement generic extrapolation frame work for potential field extrapolation. Including:
- User API: allows running any of the pre-defined algorithms using user-defined data/parameters
- Dev API: for developing custom extrapolation routines

###Week 3 / 4
Write TD testing framework
- generating TD field from initial parameters
- calculating "figures of merit" to compare the two vector fields

###Week 5 / 6
Update all code to Cython for improved performance. Specifically:
- pre-implemented extrapolation code
- TD generating code

###Week 7 / 8
Write examples of verifying the potential field extrapolation with the testing framework.
- using TD model with various parameters
- implementing Gaussian test boundary data that should produce intuitive fields

###Week 9 / 10
Write field MayaVi visualisation framework.
- ability to overlay extrapolated and original vector fields with streamlines and boundary data
- ensure user configurability
- consider possible functions mlab might which to implement

###Week 11 / 12
Test and document use of using external extrapolation using dev API, i.e. 3rd party Fortran and C++.
- getting some real world code to demonstrate, like T. Wiegelmann's C++
- communicate with code authors to see if any would be willing to licence code for use

###Week 13 / 14
Complete documentation and 3rd party user testing.

Other Info
==========
##Available Platforms
I run Windows 10 Preview x64, Windows 8.1 x64/x86, Windows 7, Mac OS X Yosemite. 

I can also run Linux if required.

##Availability
I'm usually available from about 9 am to around 11 pm. My time zone is UTC +1 (British Summer Time - so 0800 to 2200 UTC).
