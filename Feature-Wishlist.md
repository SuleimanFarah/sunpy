* RHESSI clean imaging algorithm (could be brought in from PyAPES?) Maybe other imaging algorithms as well?
* solar differential rotation correction (some code already exists for this).
* Location aware image subtraction
* Spectrum object (may be developed in AstroPy)
* AIA response curves as a function of temperature
* cgs and mks constants in the constants module (similar structure to AstroPy)
* wavelength range object, can easily convert to other units, accepted by everything
* a goes object which can fetch GOES data and display it
* net module to grab eve data (all the different levels). Steve C already has some code for this.
* add masks to maps (could be done by using numpy.ma module see [this](http://docs.scipy.org/doc/numpy/reference/maskedarray.generic.html#rationale))
* solar and earth ephemeris information (sun as seen by Earth and in general for observatories such as STEREO). This is needed if the information is not included in FITS header files but is useful in general.
* add facility to make a histogram equalized color table which could be generated automatically based on data in a map. Example code for this can be found [here](http://stackoverflow.com/questions/5858902/histogram-equalization-of-matplotlib-color-tables)

## GUI
* MapCube animations
* Contour plotting / overlays
* VSO etc. downloader
* Replacement for MPL Tk Viewer

## Lightcurve object
* rebinning (count conserving)
* power spectra
* derivatives
* peak finding
* discrete average box car
* convolution/smoothing

## multiLightcurve object 
* correlation/time lag