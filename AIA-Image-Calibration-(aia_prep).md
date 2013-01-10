# aiaprep Tests and IDL comparison

## Background
aia_prep is a SSWIDL routine that does the level 1 to level 1.5 conversion of aia fits files. In english this means it aligins and centres the Sun and updates the header. The SSWIDL code can be found [here:](https://github.com/sunpy/sunpy/wiki/SSWIDL---aia_prep.pro)
From that code aia_prep has the following purpose:
> "Perform image registration (rotation, translation, scaling) of Level 1 AIA images, and update the header information."

The goal of the conversion to SunPy is to produce identical results as the SSW version so there is no problem using code or images from either calibration routine.

## Technical bits
The aia_prep routine consits of an [affline transform](http://en.wikipedia.org/wiki/Affine_transformation) and header parameter updates. The affline transform centres the Sun to the origin in the image, rotates the image and rescales it so the pixels are all identical sizes for all wavelengths and times to compensate for any spacecraft movement.

The affline transform used in the SSWIDL routine is in the IDL [ROT](http://www.astro.washington.edu/docs/idl/cgi-bin/getpro/library32.html?ROT) routine. This uses a [bi-cubic convolution interpolation](http://en.wikipedia.org/wiki/Bicubic_interpolation#Bicubic_convolution_algorithm) method (by default in aia_prep.pro [with a interpolation parameter a = -0.5]). To maintain compatibility with the SSWIDL routine this method of interpolation for the affline transform was coded into a C-API extension and pushed into SunPy under the map.rotate() method in [PR #288](https://github.com/sunpy/sunpy/pull/288), along with support for the bilinear method supported with IDL's ROT.

The affline transform method in [scipy](http://docs.scipy.org/doc/scipy/reference/generated/scipy.ndimage.interpolation.affine_transform.html) is also supported, as a fall back in the case of no C-API extention, however this will not generate exactly the same results as the default SSWIDL aia_prep code.

## SunPy Conversion
SunPy uses `maps' as its primary data type for 2D data. So the SunPy equlavalent of aia_prep is designed to be used on maps, it has been developed to use the map attributes instead of raw fits header access. The affline transform code, as already mentioned is in map.rotate() with the C code under sunpy.image.Crotate. The actual aiaprep routine is under sunpy.instr.sdo.aia.aiaprep and will take a map and return a calibrated map. (Note: name change to aiaprep to better fit with Sunpy naming convention)

## Testing and SSWIDL Comparison
