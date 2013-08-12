This page is designed to describe the data products for various types of imaging spectrographs so an idea of the requirements for a Map derivative data type can be derived.

When adding an instrumet please focus on the data produced, information such as resolution in all axes, imager type i.e. scanning or Fabry-Perot type etc.

## Hinode/EIS
EIS has 2 modes of working, known as slit and slot, and each of them has two widths 1 and 2 arcsecs for Slit, and ?? and ?? for slot.
### Slit
Both slit widths are used in the same way, which can be as raster or time series.  The difference on the data is that raster has a movement on the Solar-X axis while taking images, and the time series are normally static and take different exposures of the same location at different times - notice that time always changes with each exposure.

![raster example](http://star.arm.ac.uk/~dps/raster_exp.jpg)
![timeseries example](http://star.arm.ac.uk/~dps/ts_exp.jpg)

These images shows a raster on the left and a time-series on the right for a particular window.  On the raster, x = x(t), so each exposure happens at certain time.

EIS does not save all the data in a single block, just the windows selected as different blocks.  The spectral window can vary in a single file, but not the mode (raster, time-series).

There's also a what's called a fast raster which the slit moves between each exposure more than it's width, getting an image such ...
