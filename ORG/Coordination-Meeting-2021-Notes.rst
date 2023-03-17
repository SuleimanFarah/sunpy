SunPy Coordination Meeting 2021 Notes
=====================================

Monday 28th Jun
===============

Notes taken by David S

Recap of last coordination meeting (2020) - Nabil
-------------------------------------------------

- 3 full working days
- Planned to be in person, but went online
- Held between 1.1 and 2.0 releases
- Day 1: project updates
  - Discussed NDCube 2, now much closer to being finished
  - Hashed out the scope of different sub-packages
  - Decided to start implementing `sunkit-instruments`
- Day 2: Core package and future planning
  - Came up with mission statement (this needs to be revived)
  - Hashed out the affliated package system
- Day 3: infrastructure and community
  - Discussed survey of computational tools in solar physics
    - Desire to redo this, but took a lot of work first time round!
  - Discussed how to grow the community surrounding SunPy
- Overall very tiring, but productive and fun meeting!
- We struggled to document stuff that needed follow on actions after the meeting ended

SunPy in the last year - Stuart
-------------------------------

- To sunpy core:
  - ~500 PRs merged
  - 21 contributors
  - ~300 issues closed
  - ~250 issues opened
- Major changes:
  - Map has coordinate aware image alignment
  - Change tracking on metadata
  - Metadata only searches
  - `sunpy-instr` moved to `sunkit-instruments`
  - JSOC cutout support
  - `assume_spherical_screen` for making off-limb coordinates 3D
- Sponsored packages are mostly seeing lots of activity :smile:
- Lots of good student projects run - 2 GSOC students in 2020, 2 students in 2021 currently ongoing, and 1 Outreachy student

sunpy core subpackage updates - Will
------------------------------------

- Removals:
  - `sunpy.instr`, moved to `sunkit-instruments`
    - Intended partly as an 'incubator' for code without necccesarily putting code in a new package
    - Perhaps we need to avertise the intentions of `sunkit-instruments` more widely?
  - `sunpy.roi`, no direct replacement
  - `sunpy.cm`, moved to `sunpy.visualisation.colormaps`
- `sunpy.coordinates`:
  - Added `RotatedSunFrame`
  - Added `assume_spherical_screen`
  - Formal support for velocities in coordinates
- `sunpy.net`
  - Added search attribute discovery
  - JSOC cutout service access
  - Unified data and metadata search
- `sunpy.map`
  - Interactive quicklook
  - New map sources for HMI/MDI synoptic maps and Solar Orbiter EUI
  - Lots of new functionality for automatically overplotting maps in different coordinate systems
  - Added `draw_quadrange` to draw a polygon along lines of constant coordinates
- `sunpy.timeseries`
  - Support for GOES netcdf files
  - Support for new NOAA JSON files
  - `TimeSeriesFactory` refactor
  - Possibly replace our underlying data structure?
- And lots of other updates to other sub-packages

Communications update
---------------------

- Sophie will be stepping down from doing comms, thanks a lot for all the service!
- Lots of cancelled conferences to start with in 2020, then lots of Zoom over-saturation :sleeping:
- Lots of enthusiasm out there for sunpy (especially from early career folks)
- Biggest tweets are either project updates or individuals using sunpy for a fun visualisation
- Some of those early career scientists may be turned off getting more involved because their supervisors advise them it's not the best use of their time.  Or code dev isn't directly related to their basic research.  Can we change that mindset?  Promote benefits more to supervisors?
- Discussion:
  - Big need to get users to communicate issues and feature requests that they have for sunpy
  - We should encourage problem solving to happen in a public forum (ie. Discourse, github issues, mailing list, chat channel)
  - Need to make sure that we don't have too many different channels of communication!
  - Hopefully the discourse will be a good new way to source examples and issues
  - Can use this to source tweet material :bird:
  - Important to try and talk about SunPy as a wider project, instead of just the sunpy core package
- Discourse update from Stuart:
  - Discourse is a forum website
  - astropy have paid for a hosted openastronomy discourse
  - There is a sunpy sub-forum within the openastronomy site  <https://community.openastronomy.org/c/sunpy/5>
  - General discussion was had about how to structure the discourse in relation to sunpy/openastronomy
- If anyone is interested in doing communications in the future for the project, please drop Stuart a line!
- We are separating our docs and gallery into many packages, we should combine them somehow.
- Overhauling the docs will take a lot of person-power, which would almost certainly require dedicated funding

Documentation overhaul - Nabil
------------------------------

- The landing page looks overbearing, with a straight table of contents and small blurb
- General feedback that Nabil has heard and remembered:
  - Hard to find stuff
  - Sections that the docs are split into are poorly laid out
  - Gallery organisation doesn't make sense
    - Overlapping
  - Not as useful as astropy's combined narrative/API layout
  - Getting feedback is difficult; suggestions:
    - Have an easy way for people to post suggestions to discourse
    - Run user groups
  - Examples of good documentation:
    - django
      - Tells users *how* the documentation is organised, straight away on the landing page
      - Has "Getting started" instead of "User guide"
    - xarray
      - Have a "How do I?" page
- We will use the pydata theme eventually

Tuesday 29th Jun
================

Notes taken by Dan Ryan, Laura Hayes

Metadata in Map - David Stansby
-------------------------------

- Map--data, meta, plot_settings

- What is the metadata?
  - `.meta` is a dict of FITS metadata
  - Abstract layer creates a standard API for extracting the metadata independent of how it's stored in the FITS meta dictionaries
- Sunpy edits metadata internally (e.g. correcting known errors or inconsistencies with FITS standard for specific instruments)
- No way to see this edit history until 3.0
- Issues
  - Still not possible to distinguish between types of changes, e.g. untrusted values, added values, overwritten, etc.
  - No abstraction layer for writing metadata
- David's suggestion solution
  - Add setters to the meta abstraction layer, e.g. `m.observer_coord = observer_coord`
  - Create objects from the FITS metadata. Then ignore the FITS metadata.
  - This way Map would not carry FITS metadata around, just Python objects.
  - `Map` is glued to the assumption that `.meta` is a FITS header

Discussion

- Dan's suggest: Create Meta objects, e.g. `map.meta.observer` rather than `map.observer`.  Create mixins for different sets of metadata specific to e.g. axes' physical types, instruments, etc.
- Stuart: Three parts of the metadata issue
  - User API (`.meta.`)
  - Serialization of metadata
  - ?
- Will/David suggestion: Separate coordinate info, i.e. WCS, from other metadata
- Stuart: deserialization largely already done my Map, but work would be needed to make thagt permanent, rather than a view into the FITS meta.
- Dan: Should we only allow Map to write to FITS if the WCS is a FITS-WCS type?

Metadata:

- Should we have a longer discussion about metadata on Friday? Stuart has notes.
- Albert: What is our responsibility to keep metadata (i.e. don't throw it out)? For example, another pipeline might need to use another observer coordinate etc.
- Carrying around "unknown/untrusted" meta is fine unless you do something like rotate.

How do we rebase map onto ndcube 2.0? - Dan Ryan/Stuart Mumford
---------------------------------------------------------------

**Meta Discussion continued..**

- Danny demonstrates that sunraster has a MetaData object
  - has generic defined instrument, detector, observer locaton.
  - Then can have object specific meta (e.g. spectrogram etc)
  - Then instrument specific that has metadata that inherits from the MetaData ABCs
  - everything on data object level is generic, and then everything instrument specific is on the metadata object
- Stuart: User-facing API for sunpy would be similar to this, but the implementation would be different
- Should the properties be elevated up so that they can be accessed on the class (e.g. do my_map.observer rather than my_map.meta.observer)
  - its a namespacing issue rather than anything else (too in the weeds - let's move on)

**NDCube** :tada:

- Want by end of today - general agreement on a proposed SEP for a proposed API change to Map to use NDCube.
- ndcube provides standard API for generated ND astronomical/solar data
  - 3 data classes (NDCube, NDCubeSequence (ordered collection of NDCubes), NDCollection (unordered collection of NDCubes))
  - 3 primary functionality (slicing, transforming, visualizations)

- NDCube 2.0
  - Adoption of astropy WCS API (APE14) which means that slicing of WCS object is upstreamed to astropy.
  - Standard API for any WCS objects (FITS-WCS, gWCS)
  - Lots of breaking changes to facilitate this adoption
  - Benefits:
    - NDCube now agnostic to WCS-type
    - upstreams several NDCube features (slicing WCS)
    - Brings API into APE-14 in certain naming conventions
  - What is is new?
    - Global Coords  e.g. a scalar time object (if you slice an axis along a time dimension how do you deal with that coordinate? this now allows for this)
    - ExtraCoords class - allows tabular/array-based coordinates. Can also serve as a secondary set of coordinate transformations
      - Because ExtraCoords can now be converted to a WCS, enables unification of NDCube cropping (crop by coord/extra coord)
    - brings nomenclature in line with APE-14 pixel-> array index
    - pluggable visualization suite (plotter - i.e. can use matplotlib/pyvista etc). .plot still works on .plotter.plot() for quicklook
  - Status of 2.0
    - confirm NDCube crop works properly
    - tidy up and documentation for users and developers to subclass NDCube
    - Very close

- NDCube 2+
  - NDCube reproject and resample (GSOC student currently working on this)
  - Arithmetic operations - add/multiple maps/NDCubes

**Mapping Map on NDCube**

- What does map currently do?
  - read data, metadata parser (not within scope of NDCube)
  - Standard data access API, Visualization, cropping (all remit of what NDCube can provide!)

- Why should we do this?
  - NDCube provides standard API for all sunpy data types
  - provides additional features that map does not (e.g. slicing with python slicing notation (more intuitive) - upstream this)
  - can easily extend to higher dimensions (e.g. sequence of maps in a MapCube (NDCubeSequence))
  - easily subclassable

- Can NDCubes be saved? Its on the roadmap but doesn't yet work  - lets address this later.

- Mapping
        *Equivalent functionalities
            * `.data`, `.mask`, `.wcs`, `.meta`, `.dimensions` (Map is `PixelPair` NDCube is `Quantity` and assumes you know ordering), `.plot`
            *`.submap` vs `.crop` or `crop_by_values` (just a rename but functionality exists)
            * access real world coords of all pixels
        *Non-equivalent functionalities
            * `.uncertainty` (NDCube does but Map currently doesn't (but it kinda does as it inherents from NDData but its not supported in Map)), `.axis_array_physical_types` (list of tupes of strings describing axes), `.peek` (in Map not in NDCube)
            *slicing
            * superpixel in Map not yet in NDCube (resample/reproject in development)

- can NDCubes slicing support affine (every Nth) slicing? - No
  - limited to contiguous chunks of data (you could mask every Nth column etc but can't do with standard slicing API)

**Proposed Rebasing Strategy**

- For rebasing Map - NDCube can provide:
  - data access,
  - slicing/cropping,
  - coord transforms,
  - data inspection,
  - visualization
  - *reproject/resample* (in future)
  - *arithetic operations* (in future)

- What does NDCube still need to do?
  - NDCube SEP to define API
  - Release of 2.0
  - What else does NDCube need to do before Map can inherit from NDCube?

- Map API changes due to NDCube
  - Submap to be replaced by crop
    - crop by pixel values ->  index [i: j]
    - crop by values -> `.crop_by_values` values astropy quantities (100*u.arcsec etc)
    - crop by coordinates -> `.crop` takes SkyCoords
  - Plotting
    - .plot -> return value changes from AxesImage to WCSSubAxes
    - Objections?
      - Will: would be `map.plotter.plot()` - should we alias to `map.plot()`? Yes (Danny says no :P (But agrees he's outvoted :) )
      - Stuart: Break up plot - i.e. have something like plotter.imshow? enable users to build up layer by layer, and then `.plot` would use `plotter.imshow` with extra title, grid etc.
      - should only alias `.plot` and then rest by ``.plotter.draw_limb` etc.
      - Albert: Should it really return entire Axes (i.e. objects to returning WCSSubAxes), however as Will notes that its very handy that the WCSAxes is returned for setting up axes for then doing more nitty gritty things.
      - Should `.plot` just be more like `.peek`?
  - NDCube has fully APE-14 ordering nomenclature: array order (row major), pixel (column major), world order (column major)
    - should we remove PixelPair?

**More general discussion about NDCube**

- Could timeseries has inherit from NDCube?
  - in essence yes
- Can all the different data types just be NDCubes - but we have to be careful about physical axes
- Is representing IRIS data in a Map within the scope of Map?
- Is a 2D image the scope of Map - what sorts of dimensionality do we want to support of Map.
- The information specific to the physical axes type could just be contained within the metadata and then the data can be any dimension

**Questions from Matt:**

- What is is timescale of release of NDCube 2.0?
  - within next 8-10 weeks as an absolute max (Stuart)

- How does NDCube handle memory? PUNCH will be using pretty big data arrays (from many images to one)
  - Short answer is it does not, it doesn't currently manipulate data in any way (the upcoming reproject PR will change this)
  - However suggestion for larger than memory data is to load the data into a Dask array - Will has done this before with Dask and NDCube for AIA analysis.

- Is parent class NDData getting updated?
  - at moment it does very little, has some mixins. But basic form is very stable, not changing and very light.
  - NDData may one day become NDCube - if anything NDData will become closer to NDCube.
  - NDCube is flowing back upstream :tada:

- Saving doesn't actually work at the moment?
  - There is an aspiration but nothing properly in the works yet.
  - serializers for gwcs isn't implemented yet which is the limitation.
  - PUNCH team (or anyone) can write their own though, using assumptions and what you know about the data.

- Indexing - how is it ordered?
  - Row major (numpy) ordered vs Cartesian (WCS) ordered.
  - Since 8-14 nomenclature:
    - World - world-ordered
    - Pixel - pixel-ordered
    - Array order (row major) same as C- python
  - NDCube is built around being WCS compliant

- PUNCH will have secondary header arrays - as some images will have what is good/bad in data array and information about how image is made from multiple images
  - are they the same dimension as data array and described by a WCS? not entirely sure yet.

- can you carry some extra non-standard information?
  - NDCube makes no assumptions about the metadata objects, you can create a very complicated metadata (e.g. a dictionary of dictionaries or whatever you like) and NDCube doesn't care and will carry it around.
  - Can create multiple NDCubes and put them into an NDCollection.
  - If the information is a data-array like then you would probably want another NDCube that can then be put together as a NDCollection.

- do you change the metadata when you do something to the data?
  - No, but the WCS is!

Wednesday 30th Jun
==================

## Affiliated Packages

### Overview

- Not coordinate meeting :-)
- Sponsored and affliated package outside scope of core but part of the great sunpy escosystem
- Sponsored - maintained by SunPy
- Affiliated - maintained by others
- Create and applied reivew criteria to all sponsored and some affilated packages
- Criteria
  - Functionality
  - Integration
  - Documentation
  - Testing
  - Duplication
  - Community
- Traffic light review system accepted, provisional, not-acccpeted?
- No submissions from outside the project - why?
- What more can be done to get more instrument teams on board?
- Tweaks to the review process
- Formal role - Affilated Package Liaison
- What is the benefit of being an affilated package in general and for the maintainer?
  - Stamp of approval certain standand and will work with sunpy
  - Premotion of affiliated packages

- Punch plans on being affliated packages but may have some duplication so how will that work?
  - pipeline code may have some duplication would that fail the the duplication
  - frozen requiments on older packages what would happen - would it go from pass to fail status?
- STIX plans to have separate packages for pipeline 'stixcore' and user facing 'stixpy' which aims to be sunpy affliated
- Pipeline instrumemt code maybe a special case?
- Going through the review process does not transfer control of development - still held by repo owners
- Yearly re-review
- Goal is to help improve, not shame or demand
- Heliopy standards - not clear on web page
  - <https://heliopython.org/>
  - <https://zenodo.org/record/2529131#.YNyRI5NKhA4>
- List of know packages or software for calibration python or otherwise
- Ultimate goal is to provide a better end user experience (scientists and developers) - through standards, documentation, etc
- How can this be supported in the sense of time to do re-reviews etc - and should try and grow at the moment if can't support what currently have?
- How to incourage conrtibutions especially from first time committers
- Advertise sunkit-instra as incubator for instrument specific code?
- Need to run sunkit-instra through review process sponsored or affiliated?

### Candidate Affiliated Packages

### Improvements

## Conditions for Writing New Fido Clients

Fido is unified data searcher and fetcher.
Clients in Core

- VSO
- JSOC
- HEK
- HEC
- EVE
- GBM
- GONG
- XRS
- LYRA
- NOAAIndices
- NOAAPredict
- NoRH
- RHESSI
- SRS
- SUVI

Client a foot

- RFS
- XWAVES
- DKIST
- Solar Orbiter
- Others?

Community can now write their own clients using sunpy infrastructure

Problems

- Some clients overlapt with VSO.  Which should be used?
  - We can't explain the difference.
  - Time needs to be spent to figure this out.  Not done though
- When people have problems with data, they come to sunpy, but we don't usually have the correct contacts to get it fixed upstream.
  - e.g. SRS
- Insufficient communication with data maintainers.
  - Sometimes data changes but we don't find out until our tests break.

Solutions?

- Remove all clients from core outside VSO and JSOC
  - Creation of sunkit-clients package?
  - Dan: Isn't data access at the hear of the point of sunpy core?  Unless Fido is moved out of sunpy (some good arguments as potentially useful beyond solar physics) shouldn't clients also be in core?
  - Stuart: If Fido moved out, VSO and JSOC clients should remain in sunpy as they are solar.
  - Matt West: PUNCH going to distribute their data through VSO.  This will automatically be available through sunpy's VSO client.
  - Fido returns SUVI data from SUVI nad VSO clients.  They are different.  Not known why.
  - SUVI team didn't want level 2 to be distributed as it wasn't considered science quality.  Sunpy didn't know this.
  - Stuart: Given VSO works with teams to get their data indexed, should we drop the SUVI client?  Thus SUVI data only available through VSO client.
  - Shane: Supports removing SUVI client.  But it could be useful when VSO is down.
  - Stuart/Laura: Move clients that are served by VSO as well out of core.  Move them to sunkit-instruments?
  - David S: Agrees that we shouldn't put clients in core that are served by VSO.
- Clients served by VSO.  These could be removed from core?
  - XRS
  - LYRA (will be)
  - GONG
  - SUVI
  - NoRH (intended, but has been for a long time)
- Dan: If these clients are moved out of core, how will users know about them?  Is a point of sunpy core to make data access easy and discoverable?
- Stuart: Even if making clients opt-in/move them out of core, Fido still has value:
  - API is the same
  - Can search multiple sources simultaneously
- Chris B: What about defining default clients for each instrument.  If users want it from a different source, they can explicitly ask to call a different client.
- Stuart: Can we just provide more information on where the data in the search results come from?  So users can make a more informed decision about which results to download.
- David S: Agrees that we should give more users info to make an informed decision about which results to download.
- Stuart: docstrings of some clients provide helpful info.  But not directly visible through Fido
- Stuart: We aren't doing a good job at telling people we aren't providing the data.  We provide a tool to get data from the providers.
- Nabil: Are we responsible for a PhD downloading the wrong data because they were confused about which file to download?
- Laura: If people only use sunpy to get their data, they may not even know what VSO is.
- David S: We should provide URLs to data providers
- Ed Mansky: Give users some kind of warning if they request a data level below scientific quality?
- Does this make sunpy responsible for knowing/educating what data is scientific quality?
- Suggestion: Clients that provide at least some data that can be read by sunpy should live in core.  Clients that don't provide any data that can be read in core should live in their own locations.

### Decisions

- Clients that exclusively provide data that can't be read by core don't belong in core

- Better document where the Fido results come from so users can make informed decisions about which files to download.
  - Name Client
  - URL to data provider
  - Start of client docstring
- Reach out to users (Laura & Shane at DIAS students) as to what's confusing?  What's their mental map of what's going on?  WHat needs to be better emphasised and how?
- Leave current clients in core.
- Regarding new clients, we should accept them but first encourage people to get VSO to serve it.
- Write up these decisions in the development docs.

## Timeseries, Pandas & Astropy

What do we do about leap seconds?

Timeseries does:

- Loading
- Plotting
- Metadata handling (really good!)
- Units

Problem

- As we add methods, we keep making assumptions about the underlying data structures, i.e. Pandas.
- Python and Pandas don't support leap seconds.  Astropy does.

- Astropy timeseries still rough.
- Discussion point: Should we change underlying data structure to astropy table.

- Should we remove sunpy timeseries in favour of astropy timeseries?
  - Need to upstream our metadata handling.  Sunpy's metadata handling is much better.
  - Astropy timeseries is a Table with an Astropy Time object as the index and several time-specific methods.
  - Can enter other high level objects as column, e.g. a skycoord
  - Pandas very efficient
  - But pandas doesn't support units
  - Also, pandas will not carry around our metadata object.
  - If you want to operate in place on a data frame, you can't if you leave pandas.
    - But operating in place means you could invalidate the metadata object.  So technically that was never supported by TimeSeries, even though it was allowed.

### Consensus

- Open to moving to astropy TimeSeries underneath.

- Concerned about losing ability to operate and change data frame in place.
- Can pandas handle an astropy Time object??  Nabil will investigate.

Thursday 1st July
=================

## The Future of Composite Map

- Composite Map stores unordered list of maps, i.e. does not expect a physical property along the sequence dimension

- Allows plot settings to be set.
- It's a bunch of plotting helpers to plot maps on the same axes.
- CompositeMap aligns maps to the same WCS at plot time on the fly.
  - Doesn't change the stored maps.

Question

- Do people think this is still useful given Map can now "auto-align" to existing WCS Axes?

Discussion

- Albert: CompositeMap saves users from writing lots of lines of code for overlaying maps.  It carries around plot settings
- Will: Wy can't that be done with MapSequence?
  - Sequence assumes/requires an ordering along a physical axis.
  - CompositeMap doesn't care about this, of even if from they are from the instrument.
- Stuart: If you don't want the default CompositeMap plotting, is the CompositeMap API better than API?
- Laura: People often ask if they can save a CompositeMap.  Therefore they must using it for something else.
- Laura: Common use case: Plot images from multiple instruments at roughly same time, roughly same observer and over plot them.

Useful Uses for a Future CompositeMap

- Linking observations/Maps from the same platform, possibly at the same time.
- Store Map with overlapping FOVs and convert to a single Map with one WCS, e.g. .flatten()
  - E.g. EUV image, coronagraph, heliospheric imager
- Laura: Sounds like these could be compatible with NDCollection.

Let's consider creating an object that takes a collection/list of Maps and a target projection/output space.  Then you can reproject or flatten all the maps to the target WCS.

- A lot of overlap with sequence.  Perhaps have this as a function that takes a CompositeMap or MapSequence.

- Stuart has some money for redeveloping CompositeMap.  He will start by writing a function that reprojects a bunch of maps.
  - If anyone has thoughts on API let Stuart know.
- Shane: Students in DIAS do use Composite map
  - Laura: They use it to link observations and it is useful for plotting.

- Albert showed us how to use Map by itself to reproject a map onto a different WCS.

## The Future of Database (Stuart)

- What does it do?
  - Ingest a search result into a SQLAlchemy-like database
  - Stores FITS header, parameters from VSO search result, and absolute path to file
  - Provides ways of searching the database on your local machine
  - i.e. if you do the same VSO search twice, it'll tell you you've already got it
  - Arbitrary FITS header keyword search
  - Pull all the FITS headers from all your files
  - Does not exist but would be nice: interface to a shared storage backend
- Database as a local data provider for FIDO? (Will)
  - Doable, but issue is that it is difficult to compare results across data providers and know what results are equivalent
  - When it comes to the local data source, sunpy has to be the search client (Fido) and the data provider (database???)
  - Just need to register it as a Fido client
  - Maybe then database just becomes the module that maintains the local datasource, Fido is the interface to all queries
  - Would need to abstract away from VSO-specific queries. Each row would have a primary key for specifying what the source of the search result was
- What do people need for this to be useful?
  - Ability to have database use a shared backend, e.g. Postgres on a shared NFS mount (Shane)
    - This already *kind of* works, provided all the root filepaths on every machine are the same because database requires absolute paths
  - Be able to do this with other datasources than VSO
    - Difficulty with this is database has to know how to serialize the query results
    - This is made difficult by the fact that each Fido source response decides what keys it returns
- Should we keep it?
  - There are compelling reasons (David S)
  - Is it useful? No...maybe (Nabil)
  - Current maintainability and code quality does create technical debt
  - Being able to search your local files via Fido is very useful
  - General consensus: yes?
- The way forward:
  - A new Fido client for your local database
  - Database sets up the data source
  - Generalize data model for other data sources other than VSO
  - Refactor the attrs in database
- We will have to impose a data model on the query response tables (Stuart)
  - Currently these are unified but no data model imposed on them
  - Could potentially make writing a Fido client more complicated
- Need to sketch out a plan for making this useful as a local data source (Nabil)
- We have to be careful in how we define the schema (Nabil)
  - Schema defined by the metadata of each source we support
  - In SQLAlchemy (ORM), have to migrate the db every time the schema changes
  - Only need to add more columns as long as all the columns are nullable (Stuart)
  - This is our responsibility and we should define a schema carefully
- Decision?
  - Affiliated database package? (David S)
  - Closer to a core component of Fido than anything else (Stuart)
  - Lives in net? :grimace:
  - Leave database, don't touch it, and eventually deprecate it (Nabil)
  - Start working on "database2"
  - Good candidate for NumFocus small grant (Stuart)
  - Sophie and Shane possibly have money, man power (from SolarMonitor) to put towards this effort with a new hire
  - Good GSoC project as well? But very carefully scoped... (Nabil)

## Project Governance (Stuart)

- Typical US non-profit structure but is not itself a non-profit organisation

- Self electing board
- Lead dev elected by board and day to day running delegated to this person
- Financial matters still remit of the board
- Numfocus has oversight to make sure follow US non-profit rules (mainly financial)
- What does the project spend money on?
  - Stickers
  - NumFocus summit trips
  - GSoC money handled by NumFocus
- What are we paying for now?
  - Stuart pays for our RTD instance
- If we want to spend money...
  - Go to the board, ask if it is ok
  - Go to NumFocus, ask for the money
  - Can also file exense claims through NumFocus webpage
- What does the board do?
  - Approves SEPs, settles 50-50 splits
  - Higher-level decisions (i.e. funding)
  - Guide and advise (mostly more senior solar physicists)
- How does information/guidance from the board flow down to those implementing it? (David S)
  - Mostly advise the lead developer
  - Some stuff is just implemented by the board (e.g. SPD stuff)
- Problem: lots of board members are not able to deal with financial stuff related to the project because they are U.S. civil servants
- The board seems to exist in a vacuum (Nabil, David S)
  - Not clear to many of us what they do, what impact they have on the project
  - More transparency?
  - There are board meeting minutes in the wiki
  - Need more of a bridge between the board and the people who are doing day-to-day stuff
  - Does the board need to be refreshed?
- Is having only one lead developer a bad thing?
  - In terms of bus factor?
  - In terms of representation?
  - Board does provide checks and balances
- We have a lot of unfilled community roles (Nabil)
  - Why are we not great at recruitment?
  - How many people are even actually able to fill these roles?
  - Higher-level, less technical community roles, board should help look for those, fill those positions (Will)
  - Stuart: current governance says that this is the responsibility of the lead developer
- Proposed governance restructure (Stuart)
  - Board is entirely advisory, but leave it alone
  - Lead developer becomes a group of people
- What has astropy done?
  - NSF didn't trust them with money due to the structuring of the project
  - Now they have "voting members"
  - We want to be able to apply for big grants as a project, don't want our governance structure to prevent this
- Board is self-elected
- No one on this call has any say in who the lead developer is
- Are these issues?
