SOCIS 2012 Projects 

**Image resampling algorithms**: Digital image data are now commonly used throughout the field of solar physics. Many steps of image data analysis, including image co-alignment, perspective reprojection of the solar surface, and compensation for solar rotation, require re-sampling original telescope image data under a distorting coordinate transformation. The most common image re-sampling methods introduce significant, unnecessary flaws into the data. More correct techniques have been known in the computer graphics community for some time but remain little known within the solar community and hence deserve further presentation. Furthermore, image distortion under specialized coordinate transformations is a powerful analysis technique with applications well beyond image resizing and perspective compensation. The goal of this project is to implement fast, efficient, and flux-conserving coordinate transformation algorithms in SunPy. See [this paper](http://adsabs.harvard.edu/abs/2004SoPh..219....3D) for reference.
Mentor: Craig DeForest?

**Spectrum Object**: The SunPy project is built upon a number of object which hold data such as the map object (for image data), the lightcurve object (for time series data), and the spectrum object (for spectral data). The goal of this project is to design and implement the spectrum object for SunPy. This object will need to be able to display its data in a basic plot form. It will also need to be able to convert from data (e.g. counts) to physical quantities (e.g. photons) through knowledge of the detector response (usually describes with a matrix). A number of physical models are also necessary to interpret spectra. Coding up efficient forms of these models can also be part of this project if time allows.
Mentor: Richard Schwartz?

**Light-curve object**:

**Map cube object**: A map cube is an ordered set of two dimensional maps.  The ordering can be by image observation time, Fourier frequency, or energy.  The map cube object must be general enough to handle ordering by numerical quantities other than time.  The map cube object can also provide the basis for animation.  For example, in a set of time-ordered maps, running through them in time-order will animate a movie.

**Movies and Animation**: The Sun is a dynamic object, and so the capability to visualize its dynamism is very important.  We require the ability to animate a map cube object, and to animate composites of the 

The matplotlib package has an animation module that looks like it can provide much of the movie playing capability we need in order

**Solarsoft Capabilities**: some basic capabilities in Solarsoft should be reproduced in SunPy.  For example, implementing a function that describes the latitudinal dependence of the rotation of the Sun is essential.