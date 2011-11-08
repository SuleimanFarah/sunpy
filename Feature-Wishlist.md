* RHESSI clean imaging algorithm (could be brought in from PyAPES?) Maybe other imaging algorithms as well?
* solar differential rotation correction
* Location aware image subtraction
* Spectrum object (may be developed in AstroPy)
* AIA response curves as a function of temperature
* cgs and mks constants in the constants module (similar structure to AstroPy)
* utility to convert from temperature in keV to Kelvin (easy!)
* wavelength range object, can easily convert to other units, accepted by everything
* a goes object which can fetch GOES data and display it
* net module to grab eve data (all the different levels)
* add masks to maps (could be done by using numpy.ma module see [this](http://docs.scipy.org/doc/numpy/reference/maskedarray.generic.html#rationale)