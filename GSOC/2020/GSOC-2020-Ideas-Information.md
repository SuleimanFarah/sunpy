# Space Weather forecasting using linear algebra

Main description is available at [the OA page for this project](https://openastronomy.org/gsoc/gsoc2020/#/projects?project=space_weather_forecasting_using_linear_algebra).

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
and by an [Elo rating system](https://en.wikipedia.org/wiki/Elo_rating_system)
provided a score.
 
The All-clear dataset was also used on a [comparison on flare forecasting](https://doi.org/10.3847/0004-637X/829/2/89).
 
 
## SunPy and Sunspotter

This project will use different aspects of SunPy:
  - [Fido to find and download data](http://docs.sunpy.org/en/latest/guide/acquiring_data/fido.html)
  - [Query solar features archives like HEK](http://docs.sunpy.org/en/latest/guide/acquiring_data/hek.html)
  - [Work with coordinates](http://docs.sunpy.org/en/latest/guide/units-coordinates.html)
  - [Visualise data](http://docs.sunpy.org/en/latest/guide/plotting.html)
  - [Work with Astropy's data tables](https://docs.astropy.org/en/latest/table/index.html)

while using them we may find new needs that the above is not covering and
hopefully we can improve them on the way.
For example, we will need to: 
- match catalogues (join tables) when the fields are
  not exactly with the same value (i.e., allowing to specify what counts as a
  match. This could be within the same field or comparing different ones as
  [topcat does](http://www.star.bris.ac.uk/~mbt/topcat/sun253/pairMatch.html));
- expand `hek2vso` (or any catalogue!) to any data archive and not only
  downloading the data used for the detection but flexible to any (e.g., hek
  provides a flare detection that was observed with AIA but we want also to
  download HMI and goes for that time);
- define a dictionary of names between different catalogues so that the same
  `features.attribute` can be used on different catalogue searches (e.g., a `flare` 
  is translated as `FL` in hek and as the different flare tables on HELIO).
  
The efforts on this project will also complement the [Fido metadata
project](https://openastronomy.org/gsoc/gsoc2020/#/projects?project=fido) with
tools and uses cases, and to the region of interest class as to add information
obtained from the catalogues (how many spots had that active region? when did it
flare? how long did it live? ... ).

## Image processing

Both dataset have been obtained using
[SMART](https://doi.org/10.1016/j.asr.2010.06.024) (check the 
[original code](https://github.com/TCDSolar/SMART) and a 
[python implementation](https://github.com/TCDSolar/SMARTPython)) as a segmentation
algorithm. Then each image annotated with information of the flaring activity a
day or two days later.

You will need to have some background on image processing to understand whether
the segmentation may have affected the image shown to the volunteers. For example,
on the 14 years dataset, all images are scaled to the same size.

## Machine learning

This is where you can bring most of your knowledge! We want to train a model
using both these datasets and test it with data from SDO (There will be some
normalisation to do as SDO has better resolution). But you should be who suggests
which methods to try and when.

Essentially, it's believed that an active region has more chances to flare if
it looks more complex. Does this data show that? Remember, ELO rating has already
be calculated, and whether the ARs flared is on the dataset.

Whatever we obtain (positive or negative results) we will publish the results!
However, if early on we find that this new classification doesn't provide any
extra information, we can work on other characteristics provided by the same
catalogue or adding other sources.

## Possible ideas

- Extract the dates, coordinates and file names from the database and obtain the
  segments directly from the fits files;
- Recreate the Elo ratting in python and/or compare with other ratings (e.g.,
  [Glicko's](https://en.wikipedia.org/wiki/Glicko_rating_system),
  [Bradley-Terry's](https://en.wikipedia.org/wiki/Bradley%E2%80%93Terry_model))
- Graph classification scheme vs flares (data available on the database);
- Unsupervised clustering on the images and or AR properties as detected by SMART;
- Neural Network model to produce a classification based on the database ranking.

