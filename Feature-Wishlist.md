* RHESSI clean imaging algorithm (could be brought in from PyAPES?) Maybe other imaging algorithms as well?
* Location aware image subtraction
* AIA response curves as a function of temperature
* wavelength range object, can easily convert to other units, accepted by everything
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