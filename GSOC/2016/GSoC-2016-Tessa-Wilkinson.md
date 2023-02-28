# GSOC 2016 Application

## Organization: Open Astronomy

## Suborganization: Sunpy

### Student Information

* Name: Tessa D. Wilkinson
* Email: [tessadwilkinson@gmail.com](mailto:tessadwilkinson@gmail.com)
* Time-zone: PST
* IRC Handle: tessa /  tdw
* Github/BitBucket username: [tdwilkinson](https://github.com/tdwilkinson)
* Blog: [blogspot](http://tdwilkinson.blogspot.com/)
* Blog RSS feed: <http://tdwilkinson.blogspot.com/feeds/posts/default?alt=rss>
* PR link(s):

1. [Create Citation File #1712](https://github.com/sunpy/sunpy/issues/1712) Resolved in pull request [#1723](https://github.com/sunpy/sunpy/pull/1723#issuecomment-203786254)

2. [Spectrogram log y axis #291](https://github.com/sunpy/sunpy/issues/291) This involved looking into my local Sunpy/sunpy/spectra/spectrogram.py. I feel confident in how to add a log y axis to a plot. The frequency (y axis) is ‘stretched' in the spectrogram class to rebin the frequency to be linear. I am working on testing a simple keyword and if statement  combination to make this axis log, otherwise, I think this will also need to be rebinned to become log scale.

### University Information

* University: University of Washington
* Major: Astronomy and Physics
* Current year: Senior
* Graduation Date: June 2016
* Degree: Bachelor

### Background / Bio

I am an undergraduate at the University of Washington. In June 2016, I will be graduating with a dual Major in Astronomy and Physics. My goal is to be a stellar research scientist, and to explore the connection between what we observe on the sun (heliophysics) and how it relates to what we see in other stars (astrophysics). On top of my astronomy coursework, I have taken a space plasma physics course covering the energetic particles from the Sun to the Earth, where I received a more in depth study of solar physics. As such, I feel prepared to discuss solar coronal processes that will be discussed as a part of this project.

Summary of technical skills and research experience:

Experience with GitHub version control

* [Mdwarf_Eqw](https://github.com/tdwilkinson/Mdwarf_Eqw) - my senior thesis project to measure equivalent widths in M dwarf spectra and the mean flux of line indices
* [Stellar_analysis](https://github.com/tdwilkinson/Stellar_analysis) - a partnership project in a computer science class to use Kepler data to make a color magnitude diagram, and then determine types of stars within the dataset

About 2 years of python experience.

Mostly scripting work:

* Comfortable using Numpy, matplotlib
* Familiar with some Scipy, Astropy, Pandas
* Learning SunPy, ChiantiPy
* Some knowledge / experience in object oriented python

Astronomy Research (with visual stellar spectra):

* Used IRAF to obtain radial velocity measurements from eclipsing binaries spectra
* Used IRAF and Python analysis to get the tilt angle of slowly rotating K giants
* Used IRAF and Python analysis to measure equivalent widths of ha spectral lines in M dwarf spectra, and other line indices in order to find correlations in activity with metallicity

### Project Proposal Information

* Proposal Title:  Implementing AIA response functions in SunPy
* Suggested Mentor(s): Drew Leonard, Will Barnes

Abstract:

Solar physics uses the CHIANTI atomic physics database to obtain properties about various elements and ionisation states. By using observed elemental abundances and ionization states, one can use CHIANTI to obtain synthetic spectra of solar plasma of various features which informs a response function used by the observational instruments themselves. This response function is vital to understanding observations.

The Atmospheric Imaging Assembly (AIA) is a multi-wavelength imager on the Solar Dynamics Observatory, specifically looking at the solar corona to understand magnetic processes.

This project aims to use SunPy to infer plasma properties like temperature and density by
developing the routines necessary to calculate two response functions for the AIA using python and ChiantiPy:
Wavelength response functions: calculate the amount of flux per wavelength measured by AIA
Temperature response functions: calculate the sensitivity of light from the plasma per temperature measured by AIA

Optional additions if time allows:

* Generalisation of the code to produce response functions using arbitrary values of physical parameters (elemental abundances, etc.).
* Calculation of response functions for other instruments.
* Conversion of ChiantiPy spectra objects to SunPy Spectra objects.

### Project Goals

An astronomer using SDO data from the AIA instrument may care to know the response function of the observational instruments. Currently, default wavelength and temperature response functions are available through an idl library SolarSoftWare (SSW). I propose to implement an AIA response function into Sunpy while integrating ChiantiPy, making it more accessible to the solar python community.
I will:

* Utilize CHIANTI and ChiantiPy to develop a spectral contribution function by using intensityRatio to show relative emissivity per line, or mspectrum to get spectral line intensities as a function of wavelength.
* Assess instrument wavelength response and develop a wavelength response function using effective area vs wavelength of the strongest emission lines present in the solar feature.
* Develop an emissivity spectral structure based on plasma properties without utilizing SSW.  Essentially, I will be rewriting the idl  function aia_get_response() and all it encompases.
* Use the spectral contribution function developed with CHIANTI to develop a temperature response function
* Close the SunPy pull request: [SDO/AIA response function #1663](https://github.com/sunpy/sunpy/issues/1663) (directly related to this project.

### Deliverables

* Project Goal: A single set of temperature and wavelength response functions for AIA  (bonus goal for arbitrary plasma conditions).
* A SunPy AIA response module that includes temperature and wavelength response functions that will utilize ChiantiPy and the CHIANTI database.
* Combine temperature response functions with DEM function from CHIANTI to predict count rates for typical solar features.

### Detailed Description

 Community Bonding Period
 April 22, 2016 - May 22, 2016

* Become familiar with SunPy and ChiantiPy coding environments. Find the best packages to use for each definition.
* Discuss with mentors a concrete plan of action for developing the code.  Discuss features that are vital and the best ways of implementing them.
* Read SunPy and ChiantiPy documentation.
* Get an idea for challenges that may arise while implementing code.

Week 1 -2 (May 23, 2016)

* Construct a Sunpy AIA response module that will be used to return data structures. The program files will include classes and program files. This will allow for an organized work flow as I develop the each part of the program.
* Implement documentation.
* Implement channel keywords.
* Design initial tests for class (strive for test-oriented design).

Week 2-3 (June 6, 2016)

* Calculate effective area from filter information.
* Develop instrument response function which may include making a wavelength grid for the desired calculation region.
* Discuss with mentors the instrument response function. Possibly compare to other known responses for other instruments or for specific channels.

Week 4-5 (June 20, 2016)

* Develop AIA instrument response per effective area data that would return the wavelength response.
* Discuss with mentors the plot of wavelength response for each channel.
* Complete Midterm Evaluations.

Week 6-8 (July 4th, 2016)

* Develop emissivity function that uses Chianti line lists to create a model spectrum .
* Develop temperature response using Chianti model.
* Discuss with mentors the response for each channel using a plot showing a function of wavelength and temperature.

Week 9-10 (July 25, 2016)

* Improve code for functionality.
* Share with mentors to ask for feature requests that may not have been prioritized for the first half of the project.
* Push code to Sunpy.

Week 11-12 (August 8, 2016)

* At this time, try to generalise the code to produce response functions using arbitrary values of physical parameters.
* Add optional additionals as time allows.
* Resolve merge conflicts (if applicable).

Week 13-14 (August 22, 2016)

* Final weeks: Tidy up code, write more tests, improve documentation and submit code sample after final polishing.
* Final mentor evaluations.

Week 15 (August 29, 2016)

* Final student evaluations, Results announced.

### GSoC

Have you participated previously in GSoC? when? with which project?

* I have not participated in a GSoC project in the past.

Are you also applying to other projects?

* No, this is my project of interest.

Commitment

* The week of June 6-10th is my finals week on campus, and I'll be graduating on June 11th. Expect less progress and communication during this time, and an increase in progress and communication afterwards.

Other comments

* As a beginning stellar astronomer, any feedback on this proposal, whether accepted or not by Google Summer of Code, would be very much appreciated.

***
