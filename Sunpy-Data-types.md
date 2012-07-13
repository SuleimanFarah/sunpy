The road Sunpy has been following is to create three data-types:

1. [Map-class](http://sunpy.readthedocs.org/en/latest/guide/maps.html) to display normal 2D solar images (solar x - solar y);

![Sunpy map](http://www.sunpy.org/v1/wp-content/uploads/2012/01/sunpy_matplotlib_animation-300x257.png)

2. [Light curve class](http://sunpy.readthedocs.org/en/latest/reference/lightcurve.html) to manipulate 1D data, where one parameter meassured is for example intensity that changes with time;

3. Spectra class.

The latest is probably the most complicated, as it does not have a simple structure and it's instrument dependant. Plus, from the same data can either be treated as a map or a light curve. Look for example the following image, which is how the two types of slit data from Hinode/EIS or SOHO/CDS looks like, they are known raster and timeseries spectra.

![raster example](http://star.arm.ac.uk/~dps/raster_exp.jpg)
![timeseries example](http://star.arm.ac.uk/~dps/ts_exp.jpg)

Both contains three dimensions, Solar Y and wavelength are common.  The third one on the raster is Solar-X whereas in the timeseries is time.  If the wavelength dimension is either fitted or averaged, then we get an image that could be treated as a map (with solar-X or time) similar to either a solar-map, or a radio dynamic spectra.  On the other hand, each "pixel" on the Y-X, Y-t dimension contains a light curve like object.

Also, it's important to consider that whoever uses this data would be interested in fitting the wavelength dimension and extract the intensity, the width and the position of the lines having three map-like objects for each spectral line.
