# Project Proposal
# Project: 3D Plotting in SunPy

### Personal Information
---
- Applicant (Full) Name: Amarjit Singh Gaba
- Timezone: UTC+1:00 (BST)
- Email: asinghgaba@gmail.com
- Github: [@asinghgaba](https://github.com/asinghgaba)
- Location: Cardiff, Wales, United Kingdom

### University Information
---
- University: [Cardiff University](https://www.cardiff.ac.uk)
- Location: Cardiff, Wales, United Kingdom
- Major: Mathematics, Operational Research, and Statistics
- Current Academic Year: First
- Anticipated Graduation: July, 2023
- Degree: Bachelor of Science (BSc)


## Open Source Background and Programming Experience
---
- Programming Language: Python, C++ (Basic Knowledge)
  
- I have done summer research with School of Chemistry, Cardiff University. The topic of my project was [‘Developing Analytical Tools for Molecular Dynamics Simulations’](https://drive.google.com/file/d/1jRh4YQszBku2Y5_J0ezBUVXCnON9e_zW/view?usp=sharing), in this I developed a functionality for [ASE (Atomic Simulation Environment, Python)](https://wiki.fysik.dtu.dk/ase/) to plot diffusion coefficient for Molecular Dynamics Simulations. 
  
- I am currently developing a Python Package, [FractPy](https://github.com/asinghgaba/fractpy) which will be used for plotting Fractals, mainly focussing on using Newtons Method to generate it for a given function. I plan to upload it to PyPi by the end of April. 
  
- I have taken Computing for Mathematics course in my University, in which I learned not only programming but other as important concepts like documentation, testing, referencing, and writing a paper.

- Open Source Contributions: I joined Github this year, so don’t have much experience in open source, but I have been learning a lot since then and have contributed to the following repositories:

    - SunPy

        - Added rigid rotation model to `diff_rot()` ([PR 5132](https://github.com/sunpy/sunpy/pull/5132))(Merged)
        - GenericMap now passes docstrings to its subclasses ([PR 5122](https://github.com/sunpy/sunpy/pull/5122))(Open)
  
    - Other repositories:

        - PyBaMM

            - Remove `simplification` and other associated tests ([PR](https://github.com/pybamm-team/PyBaMM/pull/1369))(Merged)

        - PyMC3

            - Update .pre-commit-config.yaml and removed unused imports ([PR](https://github.com/pymc-devs/pymc3/pull/4455))(Closed)

        - [Sorting-Algorithms-Visualizer](https://github.com/LucasPilla/Sorting-Algorithms-Visualizer)

            - Improved Wiki by adding GIFs
  

Open source communities provide great opportunities, and I hope to develop more and more skills, and get inspiration from amazing people out there.


## Project
---


- Why did you choose this project?
  
I have always been interested in visualising data, seeing information instead of reading them makes it more intuitive and natural. And you know things get astounding when you combine visualisation and solar data (that too in 3D!!), so choosing this project was a no-brainer for me. Moreover, my experience in SunPy so far has been lovely, the community is friendly, and you get to learn a lot from the high level discussions.

- What have other people done on this idea?

 A demo code has been written in [PR #4591](https://github.com/sunpy/sunpy/pull/4591), which is essentially the base structure of how the package is going to be like. What the code does is take a `sunny.map.Map` object and converts its coordinates (in whatever frame) to cartesian system, and then makes a `pyvista` mesh, which can then be easily plotted. 


### **Synopsis**
---

In this project what we want at the end is a Python package which can plot different datasets used in SunPy in 3D. Being able to plot in 3D would enhance and improve visual communication, by being more realistic. However, as discussed in [#3997](https://github.com/sunpy/sunpy/issues/3997), there are certain assumptions made by projecting the data in 3D, that we have to keep in mind.

Essentially what we are trying to achieve in this project is:
- Developing code to transform the coordinates of different types of datasets (i.e., images, maps, magnetic field lines) into cartesian form which is easier to plot in 3D.
- Trying different libraries for 3D plotting (starting with PyVista)
- Writing tests for the code (As discussed in [PR #4591](https://github.com/sunpy/sunpy/pull/4591) image comparison tests can be tricky in PyVista, but is possible).
- Writing documentation along with examples.


### **Tasks**
---

- **Transforming Coordinates to Cartesian form**

For this task I will need to study different datasets in SunPy and AstroPy that can be plotted in 3D. After this I will need to study different coordinate systems and understand what assumptions might be required to project them in 3D cartesian form. After building this theoretical knowledge I will develop code for the transformation. 
I will start with plotting maps, and then when the initial API is ready I will work on other datasets.
I will also need to add the functionality for combining visualisation of multiple objects (like maps and magnetic field lines) which can make 3D plot more useful. For this I will need to make sure that different objects perfectly align with their respective coordinates.


- **Plotting the coordinates**

After converting the coordinates I will need to plot them in 3D. For PyVista, as shown in the demo code ([PR#4591](https://github.com/sunpy/sunpy/pull/4591)), I will have to create PyVista `mesh` which can then be easily plotted. It is also worth trying out different 3D visualisation libraries as the installation of PyVista can require multiple dependencies (such as VTK), so I will be trying `matplotlib` and `plotly` as well, and see which one would better suit for the project.


- **Tests and Documentation**

After developing a working code I’ll write tests for image comparisons and all the other code. For documentation I will write it in a format which would make the API easy to use: Tutorial, How-to, Explanation, and References.

In tutorial I will show the basic idea behind the API, and how it can be super useful.

For How-to I’ll show examples for each feature that will be provided with this API, and how to make the most out of them.

In explanation I will explain what method I employed for the API, and what assumptions were made. The explanation section will be useful for further development.

Finally, the References which would include code references, and bibliography. 


### **Timeline**
---

- **Community Bonding Period (May 17, 2021 - June 7, 2021)**

I will spend this time to get to know the community and interact with the mentors. I also happen to have exams in this period (more specifically on May 24, June 3, June 7, and June 9), so will have to spend some time studying for it. But for the rest of the time I will be researching about the different datasets and coordinate systems in SunPy and AstroPy, and also try some pseudo code to see how would the transformation work for different coordinate frames. By doing this I will be getting more familiar with SunPy library, and will raise potential issues. I will also discuss different datasets that can be plotted in 3D with my mentors.


- **Phase 1 (June 7, 2021 - July 16, 2021)**

    - *June 7, 2021 - June 14, 2021*
    
    Write the code for transforming coordinate system to cartesian form. I will be start with the `Map`  object first. I will be using the structure from PR #4591. 

    - *June 15, 2021 - June 18, 2021*

    I will be trying different python libraries for 3D plotting. I will however, start with PyVista.

    - *June 19, 2021 - June 29, 2021*

    I will write the tests and documentation (in the above mentioned format) for the API.

    - *June 29, 2021 - July 7, 2021*

    My sister is getting married, so I won’t be available during this time period. (I understand the time period is long, but brown weddings aren't a one day event lol!)

    - *July 8, 2021 - July 12, 2021*

    I will be testing the API, and make sure that it works perfectly with the `Map` datasets. I will also be writing tests and documentation if left any.

---

**Evaluation 1 (July 12, 2021 - July 16, 2021)**

---

- **Phase 2 (July 17, 2021 - August 23, 2021)**

    - *July 17, 2021 - July 31, 2021*

    I will be working on to develop the code to support more datasets, starting with magnetic lines, and AstroPy coordinates. Moreover, the functionality to plot multiple objects.

    - *August 1, 2021 - August 5, 2021*

    I plan to prepare the API for the first pre-release.

    - *August 5, 2021 - August 16, 2021*

    I plan to keep this period for slack, in case some problem comes up and  also for adding final touches to the API.

---

**Final Evaluation (August 16, 2021 - August 23, 2021)**

---
<br>


### **Availability**
---
As stated above, there are 2 occasions when I might not be available, on my exams, and on my sister’s wedding, but other than that I am available full time. 
I won’t be doing any Summer Internship neither going for any trip, so can commit full time to this project, around ~40 hours per week, but if more needed I am more than happy to do that.
After my exams on June 9, 2021, my academic semester would be officially over and won’t start until September.


## GSoC
---

- **Have you participated previously in GSoC? When? Which project?**

No, I haven’t participated previously. This is my first time taking part in GSoC.

- **Are you also applying to other projects?**

No, this is the only proposal I am submitting.

- **How much time do you plan to invest in the project before, during, and after the Summer of Code?**

During the coding period I can easily put in ~40 hours per week, as I don’t have any summer internships. After the Summer of Code, I’ll continue to work on the API, and get it integrated to SunPy as soon as possible. I can’t wait to see how that’ll turn out!

- **Are you eligible to receive payments from Google?**

Yes, I am eligible.