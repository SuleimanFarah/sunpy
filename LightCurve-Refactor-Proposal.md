# A Proposal to Refactor LightCurve

## Abstract:
We all knew this day was coming, LightCurve cannot escape the spotlight any longer. 
LightCurve moves away from conditional dispatch to a Factory based creation system so that it behaves like Map.

## Reasoning:
This proposal makes an API change, which will move LightCurve to follow the API of the Map submodule. This will provide end users a consistent interface submodules and allow for cleaner and easier to read code for developers, much like the map refactor did for the map submodule.

## Relevant PR’s:
PR [#729](https://github.com/sunpy/sunpy/pull/729) The update to the base factory class, currently used for Map.

## Implementation:
A factory instance (as proposed in #729) called LightCurve will be available in the top level of the `sunpy.lightcurve` which will allow creation of all registered LightCurve subclasses with the following API:

```Python
def LightCurve(filename=None, source=None, dates=None, *kwargs):
    """
    Parameters
    ----------------
    filename: string or File
        A file to read.
    source: string or iterable of strings
        A string identifier for a registered subclass, matched by that subclasses `_is_source_for` method.
    dates: DateTime instance or iterable of.
        The time range to create the lightcurve in between.
    
    All other keywords are passed to subclass
    """
```

### Examples:
* my_lc = LightCurve(source=’goes’, dates=[datemin,datemax])
* my_lc = LIghtCurve(source=’goes’, dates=datetime)#Downloads a standard amount of time?
* my_lc = LightCurve(source=’goes’, filename.csv)
* my_lc = LightCurve(filename.fits)
* my_lc = LightCurve(url) # autodetect
* my_lc = LightCurve(source=’goes’, url)
* my_lc = LightCurve(source=’lyra’, dates=[min,max], events=[x,y,z])
* my_goes, my_lyra = LightCurve(source=[‘goes’,’lyra’], dates=[min,max])

### LightCurve parsing order:

1. URL -> resolve to file
    1. Filename:
        1. Attempt to read with `sunpy.io`: (Like `Map()`)
            1. Parse metadata to `_is_source_for` and find relevant subclass
            1. Create that LightCurve.
        1. Match ‘source’ flag to subclass and get subclass to read file:
            1. return data, meta pair, create instance.
        1. fail.
1. Daterange:
    1. Match ‘source’ flag to subclass and get URI
    1. Download data (support multiple files)
    1. Attempt read with `sunpy.io`, parse (data, meta) to subclass `__init__`.
    1. Attempt to read with subclass.
    1. fail
1. Other kwargs are processed and passed to subclass class method for returning `(data, meta)`.

### Required class methods:

1. parse specific data files that cannot be read by the `sunpy.io` module, i.e. CSV or ASCII files.
1. Parse input to the LightCurve factory such as date range and return a file download URI.
1. Provide a `_is_source_for` which if possible auto detects the data type from a (data, meta) pair, and also matches string names for the subclass i.e. 'goes' or 'lyra', which will be passed into the factory to specify type for download etc.

## Backwards Compatibility:
None, due to the current implementation of LightCurve it will be very hard to maintain backwards compatibility. It may be possible to implement a `.create()` method that calls the Factory, however I would not recommend it.

#Notes:

* Make a check that the index column of the LightCurve is actually a time.
* Since there is no standard for storing time-series data (FITS files have a standard) then we can expect that each instrument subclass will be highly tailored to however the data is stored.
* Do we still want to use pandas time-series to store the data?