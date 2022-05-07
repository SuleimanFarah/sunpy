This will be the first of a yearly series of in-person SunPy Coordination meetings. The purpose of this meeting is to

* plan for the next sunpy core release cycle
* coordinate development across all of the core subpackages
* coordinate development between SunPy and affiliated packages
* discuss long-term roadmap
* enable in-person development

The 2020 SunPy Coordination meeting took place from the 30th March - 3rd April 2020, it was an online only meeting.

Below is the running notes as taken during the week.

***

SunPy Coordination Meeting Notes
================================

## Agenda

### Monday, March 30

|Time (EDT, BST-5) | Title                                      | Speaker      | Moderator | Note Taker |
|---        | -----                                      | -------      | --------- | ---------- |
|09:00| **Project Updates**                              |              | Stuart    | Will       |
|     | Welcome + Introductions                          | Steven Christe
|     | **State of the Union: sunpy core**               | Stuart Mumford
|     | **State of the Union: subpackages**
|     | coordinates                                      | Albert Shih
|     | net                                              | Stuart Mumford
|     | visualization                                    | Daniel Ryan
|.    | sun                                              | Steven Christe
|.    | gallery                                          | Steven Christe
|     | **State of the Union: Affiliated Packages**
|     | radiospectra                                     | David Pérez-Suárez
|     | ndcube                                           | Daniel Ryan
|     | IRISPy/sunraster                                 | Daniel Ryan
|     | sunxspex                                         | Daniel Ryan/Laura Hayes/Shane Maloney
|     | fiasco                                           | Will Barnes
|     | pfsspy                                           | David Stansby
|     | **State of the Union: Infrastructure**
|     | Testing, CI, packaging, docs etc                 | Nabil Freij
|11:30| **Break**
|12:00| **Instrument and Affiliated Packages** || Will | Laura
|| aiapy: A Python Package for Analyzing Data from SDO/AIA     | Will Barnes
||Communication Between SunPy Developers and Instrument Teams  | Kevin Reardon, Bin Chen
|| Support for Solar Orbiter Data                              | David Stansby
|13:00| **Lunch**
|14:00| Affiliated Package Criteria / Review Process || Steve | David
|15:00| **Break**
|15:30| Spectral "Stuff" | Dan Ryan
|| IRIS / EIS / SPICE / Radiospectra                                         | Dan Ryan / Will Barnes
|17:00| **Adjourn**

### Tuesday, March 31

|Time (EDT) | Title                                      | Speaker      | Moderator | Note Taker |
|---        | -----                                      | -------      | --------- | ---------- |
|09:00|   **Adding/Removing Features in the Core Package** |            | Danny     |  Laura   |
|| The roadmap repo | Steven Christe
||The Scope of the Core Package: revisiting [#2483](https://github.com/sunpy/sunpy/issues/2483)
|| Should we move the instrument subpackage out of sunpy core?| Will Barnes
|| Should we move the Helioviewer code out of sunpy core?     | Jack Ireland
|| CompositeMap: Improve or Remove? see [#2150](https://github.com/sunpy/sunpy/issues/2150)          | Jack Ireland
|11:00|                 **Break**
|11:30|            **SunPy Map and NDCube**
|| NDCube 2.0          | Dan Ryan
|| Map based on NDCube | Stuart Mumford
|| Map / NDCube metadata and plotting
|13:00|                  **Lunch**
|14:00| **Project Planning**
|| Vision Statement
|| SunPy v3.0 Roadmap Discussion
|| Recording Authorship (see [#3650](https://github.com/sunpy/sunpy/issues/3650))
|15:00-15:30|                    **Break**
|| Consistently Gathering User Information               | Steven Christe
||Python in Heliophysics (PyHC) Projects                 | Jack Ireland, Daniel Ryan
|17:00|                      **Adjourn**

### Wednesday, April 1

|Time (EDT) | Title                                      | Speaker      | Moderator | Note Taker |
|---        | -----                                      | -------      | --------- | ---------- |
|09:00| **Workflows, Infrastructure and Tooling** || Stuart | Danny
|| Policies and Workflows for Maintaining the Core Package
|| Release schedule and deprecations
|| The State of our CI         | Stuart Mumford, Nabil Freij
|| Places to Make Use of `setuptools` Entry Points | Stuart Mumford
|| Dependencies: Do we have too many? What versions of them should we support? | Stuart Mumford|
|11:00| **Break**
|11:30| **Community** || Will | Nabil
|| Survey of computational tools in solar physics. |Monica Bobra, Stuart Mumford
|| Communication tools review and new ones.        |Stuart Mumford, Sophie Murray, Laura Hayes
|| Review of current communication platforms.
|| Ensuring things happen on GitHub.
|| What new tools could / should we be using.
|13:00-14:00| **Lunch**
| | **Growing the Community** || Monica | Monica
|| More users, more contributors. |Laura Hayes (?), Will Barnes, Stuart Mumford
|| User to contributor.
|| A Solar physics Python summer school.
|15:00-15:30|                  **Break**
|15:30| **Overflow / Breakouts**
| | Pandas dataframe vs. AstroPy Tables
| | Sprint planning
|17:00| **Adjourn**

### Thursday and Friday, April 2 and 3

Hack days. List topics here.

* Retemplating Affiliated Packages in the post-astropy-helpers Era
* sunpy core Issue Triage
* sunkit-dem
* pytest-mpl
* Remove all warnings from the test suite
* Remove all warnings from the documentation
* Remove all warnings from the examples
* Import times for subpackages
* Profiling and performance optimizations
* Supporting velocities in the coordinates framework
* RA/Dec. coordinate frame with an observer origin
* Mock some online tests. See [sunpy#2874](https://github.com/sunpy/sunpy/issues/2874)
* ndcube
* sunraster
* sunxspex
* fiasco
* [Affiliated package review process](https://demo.codimd.org/915T9iRaRWqoAEZC6IJgZw#)

If need be, any topics not covered on the first three days could bleed into
these two days as well.

# Notes

## Monday

### State of the Union

* In the last month
  * 1 release
  * 36 contributors
* In the last year:
  * ~250 issues opened, ~160 issues closed
  * Addition of maintainers
  * Release of 1.0
  * Removal of `astropy-helpers`
    * [New template for affiliated pacakges](https://github.com/sunpy/package-template) generated from [OpenAstronomy's](https://github.com/OpenAstronomy/packaging-guide) (made by Tom and Stuart). that Sunspex has been the first one to benefit from it.
    * Infrastructure takes *a lot* of time
* Need a package template maintainer!

### Core Package

#### Subpackages

* Coordinates (Albert)
  * framework for working with solar physics coordinates
  * sits on top of astropy coordinates framework
  * several new frames added in 1.1
  * ability to address frames with multiple names in astropy v4.0 -- is this a good idea?
  * corrections included in 1.0
    * correct for light travel time
    * query JPL horizons
    * great agreement with *The Astronomical Almanac*
  * additions in 1.1
    * new coordinate frames
    * debugging with logger -- underutilized, but very useful!
    * testing against SPICE
  * Plans for 2.0
    * Coordinate metaframe for differential rotation
      * This should replace the current "warp" functionality
      * Is there a good "ground truth" for this? not for images...
    * Modified approach to Carrington coordinates
      * Account for light travel time
      * Enables image alignment
  * Cool picture of dragged longitude lines should be added to the gallery! [see an example on our guide](https://docs.sunpy.org/en/latest/code_ref/coordinates/rotatedsunframe.html#grid-overlay-on-a-map)
    * Doing so is part of an open issue: [sunpy#3766](https://github.com/sunpy/sunpy/issues/3766)
  * Eventually this will be wrapped by a higher-level function
  * Challenges
    * Verifying accuracy to high precision
    * Coordinates provided by external sources may be innacurate! (e.g. JPL, AIA, SUVI, HMI)
  * A new paper should be written (follow on to [Bill Thompsons paper](https://ui.adsabs.harvard.edu/abs/2006A%26A...449..791T/abstract)) that describes new frames as well as compares accuracy between different implementations and lays out some best practices.
  * Supporting velocities in the coordinates framework
    * works!
    * not well advertised
  * Summarize differencesize differences
  * A doc page on coordinates explaining differences and issues found would go a long way to help users understand differences that they might come across.
* net (Stuart)
  * post-1.0 use of parfive for parallel downloads, nice progress bars
  * better ways to hook into Fido
  * potential GSoC project on standardizing metadata queries
  * more interaction with VSO team! helps to close feedback loop
* visualisation (Dan)
  * Several different animators in `sunpy.visualization` -- lines, images, w/ WCS
  * Animator classes moving to ndcube
  * WIP PR to ndcube plotting from Stuart
  * Integration with notebooks is not great
    * But this is challenging!
    * Outside the scope of this effort
* sun (Steve)
  * Provide generally useful constants, models
  * Most constants comes from astropy as they are good at keeping things up to date!
  * Models of interior (e.g. density as a function of radius)
  * New vision: `sunpy.datasets` supersedes `sunpy.sun.models`
    * Physical models based on data
    * Canonical models (e.g. a VAL atmosphere, CHIANTI DEMS for QS and ARs)
    * Should these datasets be on Zenodo?
  * `sunpy.sun.sun` is scheduled for removal in 2.1 (maybe 2.0?)
* gallery (Steve)
  * Still exists!
  * Many failing examples though

#### Affiliated Packages

* radiospectra (David PS)
  * Used to exist in sunpy, moved out of core post-1.0
  * Functionality for opening radio spectra, working with Callysto data
  * Useful for making time-frequency diagrams
  * Long term plan: use other spectral tools instead
  * Use ndcube, but maybe not sunraster?
* ndcube (Dan)
  * Version 1.3.0 released on Friday (27th March) :tada:
  * NDCube has 3 Main functionalities:
    * slicing/indexing
    * visualisation tools
    * coordinate transformations
  * 1.3.0 now includes a new class - `NDCollection`
    * An unordered collection of `NDCubes`
    * `NDCubes` do not have to represent same physical property
    * Can designate aligned axes for collection slicing
    * SunPy use case `MapCollection`, e.g. wavelength collection
  * Next major milestone is Version 2.0. Roadmap:
    * incl. support for gWCS
    * remove sunpy dependency (e.g. visualisation)
    * arithmetic operations (e.g. add NDCubes together, divide NDCube by scaler etc.)
    * resampling
    * write method (save NDCubes to FITS etc.)
* IRISpy/sunraster (Dan)
  * IRISpy/sunraster development currently in flux
  * IRISpy has data classes for IRIS specific data (mainly based on NDCube) and has calibration routines on the spectrogram classes
  * Future directions:
    * LMSAL/IRIS team take more authority on IRISpy (Nabil joining team!)
    * IRISpy repo to become a generalized slit-spectrogram package -> **sunraster**
    * idea such that sunraster can support SoLO/SPICE
    * IRISpy can inherit from sunraster
    * sunraster v0.1 expected in coming months
    * plan for IRISpy (from IRIS team?) to be on gitlab
  * Word on the street - IRIS team will continue development of python tools for IRIS specific data analysis
* sunxspex (Dan, Laura, Shane)
  * X-ray solar spectral data analysis in python (inherent from IDL OSPEX)
  * Very early days
  * Needed for data from instruments such as RHESSI/FERMI/NuStar/FOXSI
  * Strategy at the moment:
    * directly translate from SSW to create benchmark tests
    * Refactor to python style
  * Plan to submit proposal to HDEE call
  * Open primary PRs:
    * thick/thin target code
    * ChiantiThermalSpectrum (i.e. f_vth.pro in IDL)
* fiasco (Will)
  * tool to interface with CHIANTI atomic database
  * no huge updates - however some speed-ups to contribution function calculations and how data is pulled from database
  * still no formal release of package (still under Will's github)
  * one major motivation - can compute AIA response functions with fiasco and aiapy (i.e. can calculate the contribution of FeXVIII to AIA 94 angstrom see <https://gist.github.com/wtbarnes/474c57eca93f242221a0b0475f69cf30>)
  * motivating use cases really help
* pfsspy (David S)
  * global magnetic field modeling of Sun (global pfss)
  * currently on v0.4.3
  * looking forward
    * save coordinate-aware lines
    * 0.5 use `sunpy.map.Map` as input/output
    * 0.6 use NDCube for vector field
  * potential for a HDEE call for a generalized extrapolation package - with pfsspy being part of this
  * maybe break up the calculation and plotting functionality - version 0.5 won't include visualisation (I think?). plot_coord works!
  * David will make a blog post on sunpy

#### Other discussions

* Infrastructure: Testing/CI (Nabil)
  * package template has changed
  * talk to Nabil if you have other packages that you want a package to be re-templated
  * 0.9 test suites - read the docs/travis/circle CI used to be very slow - now with Azure much quicker
  * 100% mock coverages of all - most don't need to be online tests
  * discrepency of CI on master to other packages needs to be addressed
  * why do we run things on circle?
    * quick and easy to use
    * good artifact support uploads for docs/figure tests
    * by using more than one service provider get more stuff for free :dollar:
  * automated release pipeline - triggered on a tag
  * warnings on tests will now be errors (David's PR almost there)

* aiapy (Will Barnes)
  * Overview
    * Developed at Lockhead, started early 2019
    * Current status: CI passing, 90% test coverage, documentation exists
    * Publicly hosted on gitlab under LMSAL organisation
    * 20 open issues, 120 commits, 6 contributors
    * Continuous integration on GitLab pipelines
    * First release out very very soon (maybe today!)
  * Quick tour
    * Can update pointing information from external metadata, fix FITS observer location keywords
    * Correct for instrument degredation
    * 'aiaprep' functionality
    * Includes AIA wavelength response functions and PSF functions
  * Lessons learned
    * Very simple package, builing on other packages where possible
    * Took a lot of time and effort to build the infrastructure
    * *Very* important to have a sunpy developer in the room, to communicate existing functionality in other packages
    * Not helpful to pigeon-hole people between SunPy team and instrument teams
  * Moving forward
    * 0.1 release soon
    * v0.2 - temperature response functions
    * Please send feedback!
  * General discussion
    * Should sunpy keep `AIAMap` etc.?
    * As a minimum, where a external package exists, we should heavily reference it where appropriate in docs
    * General discussion about
* Support for Solar Obiter data (David S)
  * Solar orbiter is next big space-based solar mission
  * Nominal science begins late 2021
  * Instrument teams currently writing software
  * Should SunPy host (in docs) a mapping of instruments > python packages?
  * How can we make sure there are SunPy developers being consulted as new python packages are being written?
* Communication Between SunPy Developers and Instrument Teams (Kevin, Bin)
  * A SunPy instrumentaiton working group exists, a forum (ie. chat) to exchange SunPy and instrument team knowledge
* Affiliated Package Criteria / Review Process
  * General summary about affiliated
  * Actions:
    * Encourange external packages to apply for affiliate status
    * Add a contact link to the mailing list on the affiliated package page
    * Allow negotiation with important packages that for some reason cannot meet affiliated package requirements. Perhaps offer "provisional" affiliated status.

#### Spectral stuff: IRIS / EIS / SPICE / radiospectra / EVE (Dan, Will, James)

##### Objectives

* What are the common requirements of spectral data types?
* What instruments can use sunraster?
* Should sunraster be further abstracted?
* How can solar data types be made to work with astropy spectral tools?

##### Notes

* Spectral Instruments

  * Slit Spectrographs (wavelength, space, space / time, stokes)
    * IRIS
    * SPICE
    * EIS
    * CDS
    * SUMER

  * F-P (space, space, wavelength, time, stokes)
    * IBIS
    * CRISP

  * Radio spectra (wavelength, time)
    * ALMA
    * LOFAR
    * Callisto

  * X ray spectra
    * RHESSI
    * FERMI
    * MinXSS

  * Irradiance spectrographs (wavelength, time)
    * SDO/EVE
    * SORCE/SOLSTICE
    * UARS/SOLSTICE
    * TIMED/SEE
    * TSIS

  * More available on [LISIRD](https://lasp.colorado.edu/lisird/)
    * James Mason and Doug Lindholm putting in an HDEE proposal to build a python interface with LaTiS, which is the backend API to access LISIRD; plan to tie it into Fido analagous to JSOC, VSO

* Requirements

Generic functionality:

* slicing
* resampling
* combining, extending or arithmetic
* Ability supply model to class and have it fit the spectrum in every pixel and return another NDCube-like object with the result.
  * X-ray vs. other wavelengths: count-space vs. photon-space
  * Possible X-ray solution: have photon-model and detector response matrix into single astropy model. That way the above functionality would still work.
  * Radio spectra: May want to fit in 2D, not just 1-D spectrum, i.e. fitting in 2-D intensity-space. Requires a 2-D model.
* "Image" deconvolution?
* Simultaneous fitting of multi-instrument or multi-detector data with single source.
  * Can NDCollection provide an API/interface for this?
    * E.g. Fitting both FOXSI/NuSTAR telescopes simultaneously.
    * Fitting EIS/IRIS/SPICE looking at same region of Sun simultaneously.
* Provide option to attach detector response matrix to class that isn't used in fitting if None?
  * Probably X-ray only.
* For this work we need to extend astropy modelset fitting to non-linear fitters.
  * May be able to get a joint SunPy-AstroPy NumFOCUS grant ($5,000) for someone to do that.
  * Do we know of any candidates for that work?

Dynamic spectra:

Slit spectrographs:

sunraster:

* Easier access to axes type information.
* Exposure time correction, based on exposure time as an extra coord (along one axis).
* Assume a time extra coord, lat, lon and wave.
* Where is slit axis vs raster axis.

methods:

* Line fitting alonge each spectra in each pixel. Models like gaussian, etc
* Handle applying response functions
* For X ray response function type operations might be convolved with the fitting (fit in count space).

-

* NDCube support for multiple extra time axes.

## Tuesday

### Adding / Removing Features from core

* Roadmap Repo - <https://github.com/sunpy/roadmap>
  * broad issue rather than specific (i.e. with implementation) issue that can be added as sunpy repo issue.
  * the would feed into issue on sunpy core issue tracker, issue tracker on sunpy core at the moment is very busy
  * place for people to have discussions e.g. 'maybe AIAMap should be removed' - and then chat about it, can become community accepted or not.
  * concern that people wont see it - the community is target audience
  * visability and education about it has to happen if we want to start using it
  * this together with SEP repo may be too much? however there is a gap between sunpy core repo and SEP repo. i.e. can you have meta discussion on core?
  * we need to think of the roadmap for the SunPy project rather than sunpy core.
  * generally agreed that need another place to discuss higher level topics - however everyone not convinced that it should be in the roadmap repo (potentially with the SEP or another place other than github)

* Scope of Core Package
  * parts of sunpy package grew but then get neglected/unused (e.g. instr)
  * what should be under core library/or rather not be under core library?
  * suggestions of what people shouldn't be in sunpy core:
    * iris instr/entire instr
    * however we have instr specific subclasses - where do we draw the line? - this is for i/o & meta so maybe ok
    * aiaprep
  * sunpy isn't really a data analysis package, so shouldn't derive data (e.g. some things in instr to calculate things)
  * however some people have aspirations to have some data analysis within sunpy, such as standard data analysis for magnetogram data
  * distinction that data analysis tools are generic to data type rather than data source?
  * instrument specific things should be done by instrument packages but the framework exists in sunpy - e.g. map ?
  * could we move instrument package back in - i.e. include aiapy in sunpy.instr?
  * much instrument specific functionality added in early days of sunpy which has then funelled into sunpy.instr.
  * suggestions from Will:
            *throw out whole sunpy.instr
            * move all functions that download data to net
            *how do we phase it out and where does it go?
            * what do we do with new instrument specific contributions?
  * what can go?
    * `aia.py` - aiaprep - already in aiapy, lets deprecate then remove - decided! We need to really communitate to the community, need to make decision about what goes in/out of sunpy.
    * `fermi.py` - only used at the moment in sunpy.timeseries. Should live in instr package as useful
    * `goes.py` - the worst offender, out of the scope of core. Calculates the temperature/emission measure/irradiance from GOES two channel data. It is very useful but should live in instr package. The `get_goes_event_list` should go as can get through HEK client
    * `iris.py` - useful until something else exists, for example when sunraster/irispy exists. It currently reads a SJI raster into map sequence. We should not be recommending to users to use this. Cannot depreciate until something else exists as a stable release.
    * `lyra.py` - identifies bad sections of data (lytaf events), data-manipulation.
      * Danny will contact the lyra team to see if they want to take ownership
    * `rhessi.py` - parts the used net can be moved, backprojection works but could be incl. in instr package
  * how about moving instr to its own package - this would be a good idea if we get package template working well!

* Should Helioviewer code be moved out of sunpy core?
  * in core: uses Helioviewer API, one gallery example, requires use of glymur (JPEG2000 reader)
  * Jack suggests taking it out and making a Helioviewer package, its not really core sunpy, its less code for sunpy to maintain and Helioviewer project will develop client independent of sunpy
  * However its nice to get Helioviewer images at the moment - will the new package allow this?
  * What about the JPEG 2000 functionality within sunpy? Helioviewer to add that functionality as a plug in?
  * Good idea to remove but will still want access functionality maybe through Fido?
  * Overall - want Helioviewer access through Fido and want sunpy to have different support for reading different formats (jpeg2000, hdf5) for map - then doesn't matter where Helioviewer is

* CompositeMap : Improve or Remove?
  * at the moment - accepts lists of maps, overplots them and some ability to manipulate each layer
  * Doesn't use WCS axis currently (!)
  * Suggestion from Jack:
    * replace with extensive matplotlib tutorial on how to overplot multiple maps
  * What it *could* do - temporally aligned data and holds those as a bunch of unordered maps which can then be rectificed to the same grid (using reproject) or plot contours on one. The composite map container could work out spatial extents etc or calculate WCS thangs etc.
  * Alot of people want this (or assume it already exists!) - should it be on the roadmap?
  * However at the moment, what CompositeMap does at the moment can be removed and replaced with examples - and can be removed from 2.
  * A scope needs to be written on what a future improved version should be and look like. Maybe a GSOC project for implementing such scope.

### Map + NDCube

So, ndcube 2.0 yeah, go for it, heheh, at the end of the notes there's a link to... some discussion points. Stuart? ist that the link at the bottom? ...

* Many implementations of cubes in python
  * NDCube started on 2018 with a GSoC student. (History, a brief summary)
    * Some basic funtionality
    * iterations over the years. Released a version
    * IRISpy (now sunraster) uses it as well as some DKIST and EISPy
    * NDCube 2. to be released in the future (somethings may end on astropy)
    * Unified interface for wcs that's been integrated into astropy.
      * slicing on astropy/wcs objects (now it's in astropy)
  * Changes that need to happen on NDCube and map
    * Map inherit to ndcube and sunpy depend of ndcube (before NDcube 2.0)
    * Strategy to release (full release cycle, doing it backwards compatible,...)
  * NDdata and NDcube
    * slicing a cube with WCS is a generic functionality that any data type will use. Independent of the data type.
    * Minimise the code / encourage different data type with similar API.
    * Map will become a specific from a more generic.
    * NDcube doesn't offer at the moment all the functionality that map has, but map could add on top of it.
  * API change for map
    * use of slice implies pixel units (like array), real world coordinates through functions. The pixel unit Quantity is not used and is implicit since slice is being used
    * Keep a function like `submap` or rename it as `crop` which it makes more sense from a data agnostic view. `submap` could be a wrapper of crop.
      * You define a region (in wc) which may not fit with pixels, then that would be transformed into pixel coordinates to the closest value.
      * Map was a ndarray when we had a slicing option, then moved to data, then is now the point to move it to nddata? there will be a `.data` which is where the array is kept. Now map is subclass of `nddata`. We turned-off the slicing.
      * Inconsistency? We had units everywhere except in this case. This is like a numpy array, wher e you use the items of the array.
      * `crop` could take px units though we may not want to encourage people to do that. The `[]` would do that.
      * `.crop()` input is a wc object or set of quantities. A tuple of quantity objects, that are related with the axis.
      * Can we have only wcs instead of both? The fact that ndcube has to accept quantities as not all are wcs. The map version could enforce to take only wcs.
      * No objections to rename map into crop.
      * Why was`cropbycoords` -> to `crop`? bycoords was a bit redundant.
    * Return type of `plot`
      * `ndcube` returns the axis object, `map` returns the image.
      * You can provide your axis for both. `map.plot` creates the wcs axis at the moment.
      * Get the axis or the plot object?
      * Concerns about the return type, but there's an easy fix where we could add  something extra to the `ndcube.plot`
    * map.save - map.write
      * we have only a `.save` where nddata has a `.write`. And we should inherit it (and make it work!)
      * No objections.
    * APE14 WCS changes
      * ape14 is a... python api to... representations of WCS. astropy.wcs and gwcs conforms to ape14. NDCube 2 does too. All the magic below works.
      * map is currently no fully. Rotate doesn't exist on ape14. Rotation matrix is not expose, it's an implementation detail.
      * wcs papers do 2 things:
        * define how the transformation between world and data models. (how we do it matematically)
        * It defines a serialisation on how to do these transformations
      * map metadata model
      * map relies on the serialisation of the data to keywords.
      * resample, superpixel have a equivalent that can be implemented on ncube
      * rotate does not (sticky problem) - it's not a concept that maps to a pij.
      * It requires to detach the metadata from the fits header and re-plan the whole of it.
      * It doesn't forces us to address this, but will make it doable in the future.
      * Plan for NDCube 2 to have a reprojec method. Get a WCS and reproject it on there.
        * NDCube then will implement resample and superpixel and then call reproject.
        * map could do something similar. get a new wcs for the place, rotate and mathematically could be done as flux conserv. In the future we could reimplement that in the future. (most certainly change the results).
        * If the origin of the coordinate system changes reproject can't do the transformation, you need a 3 points (??).
        * `map1.reproject(map2.wcs)` if they are on-disk or same origin it will allign.
    * CompositeMap (way forward if we keep it)
      * NDCollection with additions that plot in the way you want.
      * Other stuff like Boundingbox that may live on NDCollection.
      * Handy to have a composite map where to use the contours and three images of different instruments. People find it useful, but no the discussion at this moment.
      * Coallignment, there are different ways to do it. regrid is something that ndcollections to do. People may want to do image coallignment (as two features) and header information is not good.
      * We should keep the names different or consistent between co-allignment, regriding,...
    * mapsequence
      * NDSequence
      * Should we get rid of it? mapsquence doesn't have a wcs on the time sequence.
      * Eventually we could have a map with more than 2d.
      * Many uses for it! (adds your here!)
        * you can still do world2pixel to them,...
        * track features,...
    * What to remove fro the map api
      * get rid of `max`, `min`, `std`,... It's under `.data.min`
      * `shift`: moves the wcs. It should be kept in NDCube... as resamples is. Modifies the wcs in some way.
      * it won't require a call to reproject as resample or superpixel
    * Draw methods
      * rectangle/limb/grid
      * where would they go?
      * Should they be plotting methods and not map methods? For the general user seems it is.
      * Move it to visualisation? or example?
      * ax.grid will work, so we can also customise the axis that is returned that knows the concept for the limb too.
      * Solution? change the return type of `.plot` that uses map as a projection.
      * We can keep long deprecation cycles for this changes. In any case it should be documented properly
      * Enforce wcs axis in map, so plot is meaningful.

    * peek
      * Intentions behind peek? quick way to see the plot without writing a lot of commands. Another intention: A class or object that includes a lot of details (like a graphical analog of print). Albert want to make it as the later. An inspection command.
      * It can have a basic visualisation, intentionally not using a colour map,... facilitating inspection but not science.
      * Keep a clear distintion of `peek` as for `plot` where many think that it's the best it can be done. They do the same thing, but `peek` is looking a bit better.
      * Not really thought on NDCube how to visualise.
      * We need to be really carefull to what we remove as `peek` is now a visual wrapup. But since it looks like a better version of `plot` why will the users care more?
      * Other names like `inspect`, `report` or something else may help people to separate the understanding of what that does.
      * Quicklook™ can be used for a new version of peek

WIP notes doc for things to discuss: <https://demo.codimd.org/zW5o71J8Szis1LpRfJk8Vw?both>

### Vision Statement

A vision statement describes the future of that we want to enable. The mission statement says what we are doing to achieve that vision or make it happen.

Steve provided the following suggestion for the SunPy's project vision statement

* A diverse and inclusive scientific community that is supported by and supportive of open source software projects that enable scientific discovery

The discussion led to the following things that are missing and should be added to the vision statement.  with the

* Too broad and similar to NumFocus, we should mention solar
* Need to mention open development, does this need to be defined? Open development is software developed for and by the community. Cannot have this without open source. Everyone has an equal opportunity to contribute.
* Refer to reproducible science.

Have to be careful that the vision statement should not                                                                                                                                         have to be explained.

Here is a link to a google doc for future drafts and gathering comments.
<https://docs.google.com/document/d/1kYsVqGNMnAj2DCYVi1juC4T3fDk4scAmZoi7v_KTWS0/edit?usp=sharing>

### Recording Authorship

* Movement in progress to remove ``__author__`` and ``__email__`` from .py files.  But this has not received enough discussion or consensus.
* Two purposes convolved in recording contributions under ``__author__`` in .py files:
  * Credit to the people who contributed;
  * Maintainers and users know who to contact about specific code.
* Agreed that people should be given credit for contributing to SunPy.  The question is where and how.  2 ideas:
  * In the .py files as ``__author__``:
    * Advantages:
      * Lives and moves with code more nautrally.
  * In another file (e.g. .rst)
    * Advantages:
      * Searchable
      * Isn't deleted if .py file deleted
      * Easier to link to on websites
      * A more natural way to record non-code contributions.  (e.g. someone who developed features elsewhere to support that code.)
* No consensus agreed, although majority in favor of .rst option.
* Future PRs should not remove ``__author__`` from .py files until this is resolved.

### Sunpy v3.0 Roadmap Discussion

* 2.0 in 2 months - what can be deprecated? aiaprep as aiapy will be released tomorrow(?), instr package needs more discussion and documentation of what it means
* Danny has some funding for NDCube work - but reproject is prioritized rather than map implementation
* Jack has PyHC funding to do 1D spectrum object, potentially with NDCube as a basis - through NumFocus find some coders to do that
* SunPy should push our use cases for specutils! They are not prioritizing sunpy at the moment, we need to make some noise in that space
* **v3.0 scheduled for May 2021**
  * instr package and removing other core items in scope of v3.0
  * NDCube in v3.0
    * Danny and Stuart will work on this with some outside people to play with it - Jack and Laura
  * Do we want spectral object *something* for 3.0 (this roadmap is not specific to core) e.g. EIS, IRIS, sunraster, sunxspex, radiospectra. What can we work on to coordinate these efforts? are there base objects we want released for 3.0? lets use the current IRISpy riot channel for these discussions.
    * rastering spectrograph
    * 1D spectra
    * X-ray stuff (sunxspex)
  * Make code more compatible with tools like dask for more scalable analysis. Need better support for out of core datasets e.g. do dask-like operations on map methods such as rotate on mapcube/mapsequence. Will to look into this with reproject with some use cases/examples and talk to Tom
  * Would like to have someone to take on affiliation packages - such as implement a review criteria, process, listing on website, infrastructure things e.g. package template, making it more accessible to people, and having better docs to make it more use friendly, infrastructure to automatically update template.
    * Community roles should be filled which will help with this

### Python in Heliophysics (PyHC) Projects - actually more like HDEE

* Nobody knows ...
* Jacks project - *Supporting and extending SunPy for the heliophysics community*
  * Experiment how the HDEE and PyHC funding will work with NumFocus
  * 4 main goals:
    * A 1D spectral data object
    * A heliophysical coordinate system - for PyHC to bring some other coordinate systems used in heliophysics that are not in Astropy
    * Learning by examples - add more examples that demonstrate SunPy and PyHC functionality. These examples would go in the PyHC gallery.
    * Ensuring code quality - i.e. tests etc. (panel were excited about this aspect of the proposal)
  * Progress slow due to money not being passed on to the people that need it. Overall:
    * SunPy 1.1 now contains Geocentric Solar Ecliptic (GSE) and Mean Geocentric Earth Equatorial (GEI) coordinate frames
    * Bridge to SpacePy coordinate systems (how we code things and how spacepy codes things)
    * Lots of dicussion on spectral object but no final design but we should *not make perfect enemy of the good*
      * Maybe the extent should just be a reader such different files could be read and returns a specutils object?
    * No new examples made to date. Something like learn.astropy.org would be great
    * Proposal suggests using pytest-cov, codecov, python-api-inspect - are there any other tools we should be using? flake-8

* Danny's project - *Further developement for NDCube 2.0*
  * Priorities:
    * Support for gWCS (8-14)
    * Resampling - so the work on reproject
  * Other efforts
    * Remove sunpy dependency - want to do this at the same time that sunpy depends on NDCube
    * Write method

## Wednesday

### Workflows, Infrastructure and Tooling

#### Policies and Workflows for Maintaining the Core Package

* Standards for new code:
  * PEP8 (PEP8 SPEAKS BOT used)
  * Docstrings must follow numpydoc format
  * test
  * peer review
  * changelog
* Standards for existing code:
  * Daily scheduled runs of CI
* Pre-commit is a set of tools/packages that works on repo. Can install locally.
  * Runs when you do ``git commit`` and returns a report of which tools pass and fail.
  * Runs tool on entirety of files touched by commit, not just changes.
  * If any fail, code is not committed. Instead the user can make changes to address issues, re-git add, and then try committing again.
  * Some tools change code for you and changes are available in staging area.
  * For master repo, if pre-commit hook fails, CI fails.
  * To install see SunPy dev docs: <https://docs.sunpy.org/en/latest/dev_guide/code_standards.html#formatting>
* Git commits encouraged to be squashed is number of commits excessive for changes made.
  * Rules of thumb: PR of less than 50 lines of changes shouldn't be more than ~2 commits.
  * Package maintainers should consider this and make judgement calls when reviewing PRs.
  * PRs should be one commit per significant working change.
  * Maintainers should be wary of asking inexperienced contributors to ``git rebase`` and be willing to help them or do it for them.
  * GitHub will include co-authors in the case of squashed commits including multiple authors.  Not a git feature.
* If PR needed to be backported handled by bot if contributors/maintainers add the backport label.
* By default new PRs are milestoned to next major release.

#### Release schedule and deprecations

* 2 planned releases per year
* 1st release shall be LTS
* Support each LTS for 1 year
* Question: Should we support old LTS releases with a few months overlap with latest one?
  * Friendlier for users.
  * More developer effort required.
  * Albert's proposal: When new LTS released (e.g. 2.0) support 1.0 for a couple more months but drop support for old non-LTS releases, e.g. 1.1.
  * **Consensus: Add a month's overlap support for previous LTS releases**
* All effort will be amde to provide at least one LTS of deprecation warnings.
  * "All effort" allows for subset of cases where this isn't possible.
* Proposal: Should we be more like Django in how we lay out our user & developer docs, i.e. easy access to docs for old/unsupported versions.
  * Nabil champions this model.  Stuart agrees.
  * Docs include release schedule.
* Release Process.
  * All PRs merged onto release branch, e.g. 1.1
  * Wait for CI to pass on commit.
  * Create git tag locally, push, and wait for CI to pass.  Release automatically pushed to PyPi
  * Conda bot will update the recipe with a PR.  When PR emerged on feedstock repo.
    * PR updates version number, hash of PyPI file, and retemplate any changes to feedstock recipes
    * Does not change dependency list.  Must change this on PR manually. (Can be done on GitHub directly.)
  * Will: This is great when all goes well.  Hard to debug for inexperienced people if things go wrong because so abstracted.
  * To learn how to do this for your own package, see <https://openastronomy-azure-pipelines.readthedocs.io/en/latest/>

#### The State of our CI

* CircleCI (aka Circle): one of sunpy's current continuous integration
* Azure pipelines: sunpy's other current continuous integration
* CircleCI and Azure do the same job but sunpy uses both in order to get more free builds. (circleCI: 5; Azure: 10).  So we are limited to 15 free builds
* Azure also automatically uploads releases to PyPi if branch is GitHub tagged.
* ReadTheDocs (RTD)
  * For SunPy, RTD runs on all branches but not set to "public" on Readthedocs by default.
  * Archived branches not rebuilt.
  * Can/Must set branches to Active/Inactive on RTD.
  * If a new version of the sphinx theme, it trigger a rebuild of all sunpy's "subprojects" listed on RTD.
* Tox: a generic virtualenv with list of dependencies for testing.
  * Set up in tox.ini
  * Like a bash script that runs pytest.
  * There is a tox in the sunpy template.
  * ``python setup.py --test`` replaced by tox.
  * See sunpy dev guide to see more about testing locally using pytest or tox.
* Why does CI fail?
    1. Upstream breaks
        * E.g. there was a bug in astropy reproject.
        * Solution 1: Report upstream issue and tell PyPi to ignore specific dependency versions or set a minimum dependency version
        * Solution 2: Also pin max version of dependency.
            * Stuart against this but puts more burden on us to report/fix bugs in dependencies ahead of time.
            * His solution: we should test against master branch of our dependencies, not just stable versions
    2. Server of CI breaks.
        * Circle might pass but Azure might fail same test.
        * No proper solution.
        * Must mock online tests to pass and occasionally test online.

#### Places to Make Use of setuptools Entry Points

#### Dependencies: Do we have too many? What versions of them should we support?

* Can we remove scipy and pandas from core dependencies?
  * These have discouraged other packages from depending on sunpy because of the large compiled libraries that come with them.
  * pandas only used in TimeSeries
    * Passionate debate to be had as to whether we switch TimeSeries to astropy Table
  * scipy only used in rotate and parse_time.  Could this be an optional dependency and an error message ask the user to install scipy when they try using these functions.
* No need to restrict gallery's dependencies.

### Survey of computational tools in solar physics

* Sent a survey about sunpy/python to the users.
* 364 people, 35 countries, 75% from US, UK, Germany, India, Japan
* Paper published in Solar Physics (link in slides).
* The board is super important, they tell us what to do. Do not anger the board.
* Most users to respond are staff/faculty or researchers.
* Most are space-based (boo) researchers with ground-based (yay) second.
* Most do not have any formal programming training but younger cohorts have.
* People who write their own software tend not to have any more training than those who don't.
* IDL is the most "used" overall language, but python is a close send.
* Python to IDL use case is 2-1 for students where as its the opposite for facility
* <50% of people who use Python use sunpy.
* In astronomy, python is the most popular among all groups, only for students was that the case for solar physics.
* ~75% cited scientific software but only ~40% do it routinely.

### Review of current communication platforms

* Google group is old and could be replaced with discourse (<https://sunpy.discourse.group/>)?
  * Could this turn off people? What about the current people on the mailing list and who like it use it as a mailing list?
  * Could expand to cover all python solar physics instead of just sunpy as discourse allows subgroups.
* We need to advertise sunpy more via the blog, social media with the idea of getting a more friendly welcoming face (like astropy have done over the last few years)
* Expand our blog to have nice tutorials or more community information aka the face of sunpy.
* Need to make sure we don’t have or keep an anti-IDL sheen we might have. Unhelpful.
* Add maybe an ask sunpy room on riot? Re purpose the off topic or add a new one? Will be fixed by matrix in the future (alleged, like they will fix server performance).
  * We want to encourage however we can, more questions and open discussion from users.

### Ensuring things happen on GitHub

* Should keep more information and design choices we make in meetings or in chats on GitHub to document why we do things. Be it the wiki, issues, projects or whatever.
* Weekly meetings should have notes or be recorded.

### Growing the community

* Should we gather user data?
  * Should we have an opt-in feature to send diagnostics (e.g when you first import SunPy)?
  * Ubuntu example
  * There are some ethical challenges:
    * detecting first install is not trivial,
    * we need to think about where to send the data (set up our own surver?),
    * we need to think about how to make the information public without giving away personally identifiable information,
    * should we send an empty ping for an opt-out
    * we should talk to NumFOCUS and other projects about it from a legal perspective
  * If we tell people that we are gathering this user data to obtain funding, we should be tell people how we are using this funding
* Gather statistics on who is hitting on SunPy.org or who is querying our documentation
* If we are trying to increase our contributor base, we should have a better way for users to ask questions. Here are some suggestions to increase our contributor base or help our users:
  * Should we doing SunPy seminars
  * YouTube video tutorials
  * Some kind of mentor/mentee system
  * Office hours
  * If we don't provide SunPy/Python help then people will ask their supervisors and if their supervisors know IDL then they will use IDL
  * Create documentation on how to get instrument groups to contribute to SunPy
  * We need to create a better distinction between SunPy core versus other affiliated packages and the modular nature of using Python
* We need to get more feedback from our users
* Summer School benefits:
  * Introducing people to the community
  * More immersive
  * How to obtain funding for this? Who will instruct?
  * Attaching this school to something like SPD (to minimize travel)
