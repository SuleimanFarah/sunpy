# Space Weather forecasting using machine learning 

Main description is available at [the OA page for this project](https://openastronomy.org/gsoc/gsoc2019/#/projects?project=space_weather_forecasting_using_machine_learning).

## Prior Knowledge

There's no requirement on solar physics knowledge. You will learn a lot about
solar active regions and flares on the way. You will need to be familiar with
python, image processing and machine learning.

## The Data

[Sunspotter](http://sunspotter.org/) collected lot of data on two campaigns:
 - [All-clear](https://doi.org/10.5281/zenodo.1478965)
 - [14 years](https://doi.org/10.5281/zenodo.1478971)
 
Each dataset contains information about the date and location of each active
region used in the project and how it was classified by the volunteers. The
volunteers were simply asked which image from a set of two seemed more complex,
and by a [Elo rating system](https://en.wikipedia.org/wiki/Elo_rating_system)
provided a score.
 
The All-clear dataset was also used on a [comparison on flare forecasting](https://doi.org/10.3847/0004-637X/829/2/89).
 
 
## SunPy and Sunspotter

This project will use different aspects of SunPy:
  - [Fido to find and download data](http://docs.sunpy.org/en/stable/guide/acquiring_data/fido.html)
  - [Query solar features archives like HEK](http://docs.sunpy.org/en/stable/guide/acquiring_data/hek.html)
  - [Work with coordinates](http://docs.sunpy.org/en/stable/guide/units-coordinates.html)
  - [Visualise data](http://docs.sunpy.org/en/stable/guide/plotting.html)

while using them we may find new needs that the above is not covering and
hopefully we can improve them on the way.
For example, the idea about designing a SunPy search events mechanism based on the images using HEK or HELIO,
could provide information from the available catalogues about the images we are interested (how many spots 
had that active region? when did it flare? how long did it live? ... )

## Image processing

Both dataset have been obtained using [SMART](https://doi.org/10.1016/j.asr.2010.06.024)
as a segmentation algorithm. Then each image annotated with information of the
flaring activity a day or two days later.

You will need to have some background on image processing to understand whether
the segmentation may have affected the image shown to the volunteers. For example,
on the 14 years dataset, all images are scaled to the same size.

## Machine learning

This is where you can bring most of your knowledge! We want to train a model
using both these datasets and test it with data from SDO (There will be some
normalisation to do as SDO has better resolution). But you should be who suggests
which methods to try and when.

Essentially, it's believed that an active region has more chances to flare if
it looks more complex. Does this data show that?



# Expand the scope of solarbextrapolation

Main description is available at [the OA page for this project](https://openastronomy.org/gsoc/gsoc2019/#/projects?project=expand_the_scope_of_solarbextrapolation.).


