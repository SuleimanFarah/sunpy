But briefly regarding the IRIS class discussed in the GSOC project idea, there are two type of data that IRIS produces: images from the slit-jaw imager, and 2D spectra from the spectrograph.
There is already quite a bit of support of general image data in SunPy, so the first things to do is build upon that to make and IRISMapSequence where we can store images from given observing campaign in some kind of cube with the appropriate meta data handling.
The next step, is an IRISRaster or IRISSpectra object which can read in and store IRIS spectra from a given observing campaign from multiple files and handling the  metadata appropriately.
As I mentioned, I have already started work on this but it is still quite a way from being merge-able into SunPy.
Handling this data is much more complicated than images because the data itself is more complicated.
IRIS observed spectra in several different wavelength ranges, or spectral windows.  For a given spectral window, there are several dimensions: spatial distance along the slit, wavelength, time, raster position, raster scan number.
Some of these are not actually different dimensions but different coordinate systems for the same axis.
A
For example, one raster position corresponds to one time.
If you have several raster scans (where the slit is stepped across the field of view left to right, taking spectra at each point, then jumps back to the leftmost position, that's one scan), they are also associated with time and raster position.
Once we have an object that can handle IRIS spectra, then we want to be able to view and analyze the IRIS spectra and images together.  So we need an IRISObservation object which allows us to link the slit-jaw images from different passbands, to regions of the spectra in different spectral windows.
17:04There has been nothing done so far in trying to create such an object as we don't yet have IRISMap or IRISRaster objects.