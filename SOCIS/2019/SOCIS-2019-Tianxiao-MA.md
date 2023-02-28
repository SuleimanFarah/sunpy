# Expand the Scope of Solarbextrapolation

Tianxiao MA
April 2019

## 1 Student Information

### 1.1 Background

- Name: Tianxiao MA
- University: Swiss Federal Institute of Technology Lausanne (EPFL)
- Major: Master student in Physics
- GitHub: TianxiaoMA
- Contact information: tianxiao.ma@epfl.ch

### 1.2 Previous Experience

In the last two year, I have finished two projects about computational physics and spaces craft operation:

1. Microscopic Study of Surface Adhesion in Friction Problem: Developed numerical tool by means of Discrete Element Method and Finite Element Method in Python and C++ to simulate and study microscopic contact evolution and friction mechanism
2. Simulation of spacecraft's interplanetary travel: Designed and simulated a spacecraft's interplanetary trajectory in the solar system.

In the first project, I implemented different integration schemes, such as Leapfrog and Velocity Verlet, and boundary conditions, such as rigid boundaries and periodic boundaries, to simulate the evolution of friction mechanism.  Along with this project, I acquire an insight into different numerical methods of the computational physics simulation.  In the second project, I got some exposure to coordinate transformations in the solar system, such as Heliocentric Earth ecliptic system, Heliocentric Aries ecliptic system and Heliocentric Earth equatorial system.
I also helped on the fix of some small bugs in the source code of the package of Solarbextrapolation, they can be found [here](https://github.com/sunpy/solarbextrapolation/pull/24).

## 2 Project

### 2.1 Introduction

The research of structure and evolution of the magnetic field in solar Corona has been an important task over past decades. By imposing different magnetograms as boundary conditions in a finite or semi-finite scheme, the coronal magnetic field can be reconstructed from the Laplace equation:

∇**B** = ∇<sup>2</sup>φ = 0

where **B** is the magnetic field and φ is the magnetic scalar potential function.

Solarbextrapolation is a Python API for extrapolation and reconstruction of the coronal magnetic field, which could be evaluated both quantitatively, such as extrapolation by the Green's Function Methods, and qualitatively, such as visualization of 3D field extrapolation.

However, a few features can be improved in the package, for example:

1. **Limited extrapolation region and lack of support for coordinate transformation**

    Solarbextrapolation currently solves the differential equation in normal Cartesian coordinates by implementing classical Shmidt method, which only works for small areas of the solar surface (about an active region).  A more general approach is necessary for magnetic field extrapolations over larger areas of the Sun, for example, the Potential Field Source Surface (PFSS) model. Additionally, the data of the boundary condition may in different coordinate systems,  all  of  which  are  widely  used  in  Solar  physics,  a  coordinate  transformation  will enhance Solarbextrapolation's compatibility in solar magnetic field extrapolation.

2. **Development of better visualization methods**

    Solarbextrapolation currently visualizes the 3D magnetic field extrapolation interactively using MayaVi package, which is non-universal library in scientific Python community and sometimes hard to code right.  It could be replaced by other commonly used and easily-implemented visualization libraries in Python.

3. **The lack of extrapolators for different magnetic field models**

    The current model of the magnetic field extrapolation in Solarbextrapolation is based on Potential Fields model and Laplace equation. However, some advanced model, such as Linear Force-free Field model, Nonlinear Force-free Field model, and Non-force-free Fields, have been developed and numerically simulated by other researchers over the past decades, which could also be included in the package.

### 2.2 Implementation

As discussed above, a few features of the package could be developed. Generally, the project will be
split into 3 parts to improve them respectively, and the major focus will be the development of the
support for coordinate transformation:

1. **Enlarge extrapolation region by PFSS model and add support for different coordinate systems.**

    Some numerical solvers of PFSS model have been developed by other researchers. The natural coordinates for these solvers to represent the curved solar surface are spherical coordinates (_r_, _θ_, _φ_) rather Cartesian coordinates.  So, a coordinate transformation between Cartesian coordinates and spherical coordinates is required when adding the PFSS model to the package.

    Besides, Astropy and Sunpy provide a convenient API for coordinate transformation.

    Specifically, three main steps to finish this goal are as follows:

- **Set up a prototype of PFSS solver in normal spherical coordinates**

    The first step is going to add the transformer between Cartesian coordinates, spherical
coordinates, and other commonly used coordinates. Then a PFSS solver is going to be
constructed and tested in these coordinates to ensure it can extrapolate magnetic field
correctly.

- **Test the solver in Stonyhurst Heliographic coordinates**

    After being checked in the first step, the PFSS solver is going to include a new feature to support data in Stonyhurst Heliographic coordinates, because Stonyhurst Heliographic coordinates are closely related to Heliocentric Earth Equatorial (HEEQ) coordinates like the relationship between Cartesian coordinates and spherical coordinates:

    X<sub>HEEQ</sub> = _r_ cos _θ_ cos _φ_

    Y<sub>HEEQ</sub> = _r_ cos _θ_ sin _φ_       (2)

    Z<sub>HEEQ</sub> = _r_ sin _φ_

    where _r_ is the distance, _θ_ is latitude, _φ_ is longitude.

- **Add coordinate transformation to the package**

    When steps above are finished, a coordinate transformation between different coordinates can be added to the package by using Astropy and Sunpy. Normally Stonyhurst Heliographic coordinates will be used as reference coordinate of data fed into the PFSS solver. But converters between difference coordinates will be added to the class of input and output of the solver if users expect input and output in different coordinates.

2. **Develop a better visualization**

    Function visualize currently uses package MayaVi to generate interactive 3D plots of the magnetic field.  If time allows, some other commonly used packages will be included to improve the visualization framework and user experience. For example, Matplotlib has become a functional plotting tool which is prevalent in the scientific Python community.

    Ipyvolume is another Python library to visualize 3d volumes in the Jupyter notebook, with minimal configuration and effort. Pros and cons are as follows:

    (a)  Matplotlib:
        *Pro:
            * Prevalent in scientific Python community and installed by default by Anaconda;
            *Easily-implemented
        * Con:
            *Less functional in 3D plotting
    (b)  Ipyvolume
        * Pro:
            *Easily-implemented with simple API for users to change some properties of plot
            * Capable of multi-volume rendering
            *Potential to support different language (for example C++)
        * Con:
            * Needs extra dependency

## 3. Include advanced models in the package

Some advanced models, such as Nonlinear Force-free model have been developed in the research.  If time allows, new methods will be included in Class PotentialExtrapolator to extrapolate magnetic field according to these models.

## 3 Proposed Timeline

- Week 0 (Before Jun 24):
  - Get familiar with the structure and source code of Solarbextrapolation
  - Review literature on PFSS model and existing code
  - Communicate with mentors to determine the function and position of methods that will be added to the package
- Week 1 - 2 ( Jun 24 - Jul 7):
  - Review literature on coordinate transformation and data storage
  - Communicate with mentors for the code structure of PFSS solver which is going to be added to the package
  - Write a method of coordinate transformation to convert Cartesian coordinates to spherical coordinates in class PotentialExtrapolator
  - Write a method to convert output data of the solver back to Cartesian coordinates in class Map3D
- Week 3 - 4 ( Jul 8 - Jul 21):
  - Test the code of the converter
  - Document the code of the converter
  - Add PFSS solver to class PotentialExtrapolator and replace current extrapolator
- Week 5 - 6 ( Jul 22 - Aug 4):
  - Test the correctness of the PFSS solver in spherical coordinates with existing results
  - Optimize performance of the PFSS solver by Cython and numba
  - Document the code of the PFSS solver
- Week 7 - 8 (Aug 5 - Aug 18):
  - Renovate the input and output of PFSS solver to support the data in Stonyhurst Heliographic coordinates
  - Test the PFSS solver with the data in Stonyhurst Heliographic coordinates
  - Document the code of new input and output
- Week 9 - 10 (Aug 19 - Sept 1):
  - Implement Astropy and Sunpy to add a new method in class PotentialExtrapolator, which will convert objects in different coordinates to Stonyhurst Heliographic coordinates
  - Implement Astropy and Sunpy to add a new method in class Map3D, which will convert output data to objects in different coordinates
  - Test the code of the coordinate transformers
  - Document the code of the transformers
- Week 11 - 12 (Sept 2 - Sept 15):
  - Communicate with mentors to determine the libraries to be used in function Visualise and the default coordinates of the input data in function Visualize
  - Renovate function Visualise with new library
  - Test the code of new function Visualise
- Week 13 (Sept 16 - Sept 22)
  - Add coordinate transformer to function Visualize to support data in different coordinates
  - Finish the documentation and evaluate the code

## 4 Other Info

### 4.1 Availability

I am usually online from 9 am to 10 pm. My time zone is UTC +2.

### 4.2 Available Platforms

I usually work on Windows 10 Home x64 and sometimes test code on Ubuntu 18.04 (WSL).
