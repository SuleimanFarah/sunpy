# 2022 SunPy Coordination Meeting Agenda and Notes

This is the official running notes document for the [2022 SunPy Coordination Meeting](https://sunpy.org/project/meetings#sunpy-coordination-meeting) held at DIAS in Dublin, Ireland and virtually. Below, we will list the agenda for each day followed by a sections for notes from each session. For each session, a discussion lead, a moderator, and a note taker will be designated. At the end of the coordination meeting, these notes will be published in a more digestable format on the wiki. **We should also publish a blog post describing the outcomes of the meeting.**

Presenters: Please add a link to your slides in the title of the session you're presenting for in the agenda for the appropriate day.

Decisions we made during discussions are marked with the 🥬 emoji
Points requiring further discussion and a decision are marked with the 🌻 emoji

## Useful Links

* [Meeting Webpage](https://sunpy.org/project/meetings#sunpy-coordination-meeting)
* [Matrix Chat](https://openastronomy.element.io/#/room/#sunpycoordinationmeeting:openastronomy.org)
* [Lunch reservations](https://docs.google.com/spreadsheets/d/1AER2_kJ69MtelSSBB4B3SrizNbTvsxnnZTUvws9MQh4/edit?usp=sharing)


## Monday 22 August

| Time | Title | Presenter | Moderator | Scribe | Desired Outcome |
|:----:|:-----:|:---------:|:---------:|:------:|:---------------:|
| 9:30 | State of the Core Package | Stuart Mumford | Will Barnes | David Stansby | |
| 10:00 | State of the Subpackages | Will Barnes | Stuart Mumford | David Stansby | |
| 11:00 | State of the Affiliated Packages | Package maintainers | Will Barnes | David Stansby | |
| 14:00 | OSTFL Summary | Albert Shih | | | |
| 14:30 | Documentation Review | Nabil Freij | | | Plan of action for more narrative docs, more searchable docs, cleaning up guides |
| 16:00 | Roadmap | Steven Christe | | | A vision for the future of the project |


### Notes
#### Introductions
- General chat about the logistics of several sessions later in the week
- If anyone has hack ideas, put them down below under the **Friday** heading.
- Discussion about what we want to get out of the meeting:
    - A decision on whether we want to go forward with work to make `sunpy.map.Map` inherit from `NDCube`
    - A decision on whether the metadata object in `sunraster` is suitable for moving into `sunpy` core
    - A list of features that people external to the core development team (e.g. instrument teams) think are missing from the SunPy ecosystem.
    - A Roadmap that serves as the long term vision for the project
    - A strategy for the long term sustainability of the package beyond the current core contributors
    - Some clear documentation on the what is and whys of the affiliated package system, with separate sections aimed at both users of the packages and developers of the packages
    - Decide what we want out of metadata handling...
    - Create a clear user-focused explanation of how the "sunpy ecosystem" works

We did a round of introductions (these names were updated throughout the day):
- In the room:
    - David Stansby
    - Marcus Hughes
    - Dan Ryan
    - Shane Maloney
    - Nabil Freij
    - Will Barnes
    - Stuart Mumford
    - Laura Hayes
    - Tiago Pereira
- Online:
    - Conor MacBride
    - Juraj Lorincik
    - Jan Gieseler
    - Pearse Murphy
    - Alasdair Wilson
    - Albert Shih

#### State of the Core Package -- Stuart Mumford
[Link to slides](https://cadair.github.io/sunpy-2022-state-of-the-project/)

- Unique feature of sunpy is community development
    - Anyone can report bugs, fix features, weigh in on the direction of the project at a high level
    - As a project, tries to be welcoming and friendly!
- Core package is most active part of the project
- In last 12 months have had 13 unique contributors to `sunpy/sunpy`
    - Would be interesting to get stats on people opening issues
    - Also interesting to check contributor churn (ie. how many people do one commit then don't come back)
- As well as sunpy core package, there are (see presentation linked above for a list)
    - several sponsored packages
    - the `sunpy.org` repo for the website
    - misc repos
- There are a number of named roles within the project. Three of them currently un-filled. **add link to website**
- Each sub-package within sunpy core has a maintainer - in theory this gives people ownership of each sub-package, but in practice everyone works on everyone else. **add link to website**
- One challenge we need to work on is the (un-)sustainability of growing the SunPy project into multiple repositories
    - This includes communicating this decision effectively
    - We should stop moving stuff into different repos until we have a vision for what this looks like

#### Status of the Sub-Packages -- Will Barnes
[Link to slides](https://docs.google.com/presentation/d/1QRAsN88lKxTfpYw-V9I_TRmxdmILc84g4tz1vhc7ho4/edit#slide=id.g6c14eb821cf36f5b_112)

- There is a list of the stability of various sub-packages **link to list of sub-packages on website**
- Overview of what's new in sunpy 3.1 and 4.0 **add links to what's new**
    - In `sunpy.coordinates` there is a context manager to account for differential rotation of the sun when transforming solar images
    - In `sunpy.net` added support for searching `CDAWeb`
    - Not a `sunpy` feature, but `parfive` (the package `sunpy` uses to download data) had a 2.0 release that
        - Deletes files from disk if the download files
        - Can resume from an iterrupted download
    - In `sunpy.map`, new `.reproject_to` method to reproject maps to different world coordinate systems
    - In `sunpy.map`, arithmetic operations (e.g. adding a quantity to map data)
    - In `sunpy.map`, updates to date/time handling to expose FITS 4 date metadata
    - Moved `sunpy.image.coalignment` to `sunkit-image`
    - Can now supply a different algorithm/backend for affine-transforming maps, e.g. a `cupy` backend for doing transforms on the GPU
    - `sunpy.timeseries` can read CDF files
        - 🌻 Doesn't support multi-dimensional datasets (e.g. velocity distribution functions) - we will discuss this more on Wednesday at 11:00
    - Misc updates:
        - `database` is not mainatined, and we no longer run tests.
            - 🥬 General feeling in the room is that we should get rid of it from sunpy core. Eventually will be re-written, but before that we should remove `sunpy.database`. We will:
            - Open an issue, email the mailing list on the presumption that this will happen and see if anyone complains
        - `sunpy.io.fits` was deprecated
            -  🥬 We should deprecate everything else in `sunpy.io` that is just used for reading files in and is duplicated by the map/timeseries factories
        -  In `sunpy.visualization` can draw limbs
        -  🌻 We need to decide what do do with everything in `sunpy.util` (this is not high priority...)

#### Status of Affiliated Packages - Will Barnes
[Link to slides](https://docs.google.com/presentation/d/1ZLTVthIw683u0OzcO13uafBgKUEJSMZV2kG2JqmadUw/edit#slide=id.g5cf11743d0441f_112)

- This week we need to sort out our messaging around the scope of sunpy core and the affiliated packages
- We also need an answer to "why should my package be an affiliated package?"

Package updates:
- **sunpy**: covered in previous session
- **NDCube**: **add link to slides** handling coordinate aware n-dimensional data.
    - A major refactor, version 2.0, has been released. Entire re-write of code base. Uses `astropy`'s WCS API.
    - 10 contributors to 2.0
    - `NDCube` paper being written to provide some of the background and historical context to `NDCube` 2.0
    - Used in DKIST pipeline, `sunraster`, `specutils`, other projects outside solar commumity
- **drms**
- **sunraster**
- **sunxpex**: package for solar x-ray spectroscopy. **Not released or stable!**
    - Includes thermal and non-thermal models of emission and code to fit them to observational spectral
    - Most functionality translated from solarsoft equivalents
    - will be rebranded sunkit-spex
    - roadmap to 0.1 under construction
- **sunkit-image**: for image processing on sunpy maps.
    - Haven't done a great job or promoting this, but it is potentially really widely useful!
    - Reasonably mature package
    - Still need to make sure everything operates on `Map`s instead of bare arrays.
- **aiapy**: for AIA image analysis
    - Nabil is primarily dev/maintainer
    - Developed by instrument team itself.
    - Has a Journal of Open Source Science paper.
    - Spinning this out from sunpy core gave the instrument team ownership over code, and prevented them from being bound from the sunpy core release cycle.
    - Current workflow is to load a map with `sunpy.map.Map`, and then use `aiapy` for any instrument specific analysis. 🥬 Add this info to the documentation on why this is structured like it is
- **pfsspy**: works well, does what it says on the tin.
    - Lots of new bits and pieces that could be added around the edges.
    - No longer actively maintained since lead maintainer (David S) no longer active in solar physics, so 🌻 unsure what the future of the package is.

General discsussion
- We now have several packages that depend on `sunpy.map.GenericMap`, so we need to be really careful making any API changes in the future (even with deprecation cycles)
- Some map sources can start in instrument specific package
- Current map sources in the wild:
    - pfsspy
    - DEM map sources
    - eispac
- 🌻 Will B and David S think we should drop "sponsored packages" as language, Stuart M thinks that there is still an important distinction to be made, but probably not as prominent - discuss this later
- What is a sponsored package?
    - Currently it's kind of a side project of existing maintainers, but ideally we would like to get away from this.
    - On a technical level a sponsored package means the lead SunPy developer decides who has commit access to a package.
    - Perhaps sponsored packages split into "generic packages" and "packages that are useful but at risk of being unmaintained"
    - Should add reason why there affiliated & sponsored packages, e.g. for aiapy reason it's affiliated is so instrument team retains control over the code
- Maybe useful to have a new library external to astropy/sunpy/ndcube into `gwcs
- `NDCube` example gallery please - we probably already have a lot of how-to guides locally on our laptops, but these should be collated and made public.
- Also `NDCube.io` please

#### OSTFL Summary -- Albert Shih

[Link to slides](https://docs.google.com/presentation/d/162ocqwNFagggQZzddkd3Hw95-A1X_KDAfOq68R781l0/edit?usp=sharing)

- SunPy is funded through NASA ROSES
- $640k over three years (ending 2024)
- Proposed split is Albert Y. Shih ~0.2 FTE, Will Barnes ~0.5 FTE, Stuart Mumford ~0.2 FTE
- Proposed activities:
    - Improve technical infrastructure
    - Supporting multi-point observations
    - Supporting large data sets (using dask)
        - Constructing dask array to hand off to processing is a large part of the challenge
        - This includes choosing how to chunk the array across different axes
        - Scope is to allow users to use a dask-like workflow with sunpy, without e.g. casting to numpy arrays and consuming lots of memory along the way
    - Providing training and outreach
- Technically funding is for maintenance as opposed to new features
- Status of effort: took a while to get money in the right places, but work has now started in the last couple of months
- Albert has a list of things to do for `sunpy.coordinates` (see the slides at the link above for this list)


#### Documentation Review -- Nabil Freij

**put link to slides here**

- Talking just about the core library here, but our discussion and choices will shape sponsored package documentation
- Documentation issues:
    - No updates to the user guide since sunpy 1.0
    - Exmaples are scattered and hard to find, no way to search just the examples.
    - Gallery has a mix of examples and tutorials
    - See slides (link above) for more issues
- Django **put link here** https://developer.mozilla.org/en-US/docs/Learn is an example of good documentation structure - they have a page about how the documentation is structured itself, and which bit you should go to depending on what you're looking for.
- There's a large gulf between "getting started" documentation and the very advanced API and other documentation

Ideas that came up during discussion
- Should be able to search the example gallery and API docs separately
- Add tags to examples for discoverability
- SunPy has become a teaching tool where new users learn about concepts that underly
- We have to be careful about writing very complex code (both source and in the documentation) that puts people off
- PUNCH uses prefect as a package, and they have a slack channel which is very well used

Proposed structure:

- Tutorials
- How-to guides
    - Have how-to guides in individual packages
    - **But** these should be collated in a single place so users don't have to guess which package to use for a specific task
- Explanation
- Reference
    - Have API reference in individual packages


General discussion about how we get users to interact. Helionauts is great because it's  a user "safe" space that isn't just full of developers, so users feel helpful. How do we tap into that to get useful user feedback?

Suggestion in the

🥬 TODO:
- Add the four documentation sections to the `sunpy core` landing page, even if they don't have any content
- Re-run a sunpy survey to ask people what needs to be improved about sunpy
- Push the openastronomy forum more in the documentation
- Push help avenues at the end of examples and tutorials and generally everywhere
- Move the ask questions bit of the discourse from a general bit to the sunpy bit
- "Chat (Matrix)" > "Chat" in website footer
- Add Discourse to the website footer
- Check about logging in to element/matrix with a GitHub login

### Roadmap - Steven Christe (moderator)

An out-of-date repository to this https://github.com/sunpy/roadmap

TODO - remove this repository and move it onto the sunpy website.

We agree that it is a good idea to have a roadmap. The roadmap is for the project broadly and not just for the package.

It should be reviewed every year at the coordination meeting.

* What are we doing well?
    * helio coordinates and coordinate-aware GenericMap
    * easy visualization
    * our documentation - probably best in class when compared to other helio packages.
    * open source development and open source science
    * testing code - good coverage
    * downloading data - Fido
    * community engagement - we respond very quickly and provide lots of support when asked. we have a weekly meeting and a good web presence and an active chat channel.
    * sunpy core releases - we release regularly and provide good changelogs
* What are we doing poorly? Where can we improve?
    * contributing to sunpy core and affiliated packages is difficult and takes a long time. Our developer documentation is not good enough and we are not very welcoming during reviews.
        * How to develop more developers who make regular and frequent contributions?
    * Doing anything with more than one map at a time (CompositeMap, MapSequence) - both the code and documentation needs improvements.
    * Visualisation of multiple maps on one axis (discoverability and docs).
    * Poor support for catalogues i.e., HEK
    * No support for spectra data in sunpy core
    * No support for multi dimensional time series data (astropy timeseries does provide some of this)
    * Time-distance data and plots
    * TimeSeries could support more instruments
    * We don't have a clear separation in SunPy's scope relative to space physics.
    * Metadata across our data class objects are not consistent - lots of things that could be done - Is this just an area for improvement?
    * Communicating that SunPy Project's capabilities are spread over multiple packages
        * Discoverability of these functionalities
    * Improving people's understanding of what sponsored and affiliated packages are, as well as the scope of core.
    * Clearly communicating the benefits of becoming sponsored/affiliated package.
* What to we want to stop doing?
    * database
    * remove compositeMap
    * get rid of sunpy generic timeseries class because astropy timeseries already does most of what we need. More discussion needed on this one.

TO DO: add to developer docs that PRs should be started as soon as you start work to get guidance as you write your code.

Definitions of time frames
* Near-term (1 year)
* Short-term (2-3 years)
* Long-term (5 years)

Priority list
* High - the sunpy community should be actively working to solve these, directly associated with things we are doing poorly
* Medium -
* Low - should be done in your spare time, not related to something we are doing poorly

Roadmap Items - should be associated to issues found

* Integrate NDCube into sunpy core (high priority, short-term).
    * Have Map inherit from NDCube and update API.
    * Have MapSequence inherit from NDCubeSequence
    * NDCube should be integrated into areas where WCS are used
    * Refactor Map visualisation code into a Plotter
* Metadata object (low priority, short-term) Stuart: Long term?
* TimeSeries Improvements
    * Align the sunpy TimeSeries API with the astropy TimeSeries API
    * Involves rebasing sunpy TimeSeries onto AstroPy TimeSeries (medium priority, )
* Database 2: This time it's personal (low priority, ???)
* Documentation (medium priority, near-term)
    * Explanation
    * Tutorials (inc download as notebook)
    * Clear separation of documentation modes
* Improve the contributor experience (high priority, near-term)
    *  Better define expectations of code quality for new contributors
    *  Better prepare new contributors for what to expect as part of a PR code review.
    *  Reduce expectations for new contributors!
* Clear messaging around project structure and Affiliated Packages
    * Package / functionality discovery
    * Clearly define the benefits of being an affiliated package
    * Expalin why a package might / might not be sponsored
* Develop a set of outreach materials for regular use
    * Tutorials
    * Branding
    * Talks
* Add first class support for spectral data to sunpy core
    * List out requirements for types of spectral data and find common ground
* Add support for radio data to sunpy core (this is too broad (is it?), making images with radio data? or just spectra?)
* Coordinates **Albert to fill in**

*When we write up the roadmap properley, make sure there's examples of specific missions/datasets that fall under spectra/radio data*

See the following pull request
https://github.com/sunpy/sunpy.org/pull/323

TODO: Add github login to matrix.

## Tuesday 23 August

| Time | Title | Presenter | Moderator | Scribe | Desired Outcome |
|:----:|:-----:|:---------:|:---------:|:------:|:---------------:|
| 9:00 | Outreach and Community | Laura Hayes | Will Barnes| | Clear pitch for the software workshop at the SPD meeting next year |
| 9:45 | Metadata Object API | Dan Ryan | | Will Barnes | Have a draft API sketched out |
| 11:00 | Communication Review | Nabil Freij | | Will Barnes | Plan for refactoring the help page in our docs |
| 14:00 | Governance | Stuart Mumford | Will Barnes | Shane Maloney | Draft of an SEP describing the new governance structure |
| 16:00 | Data Providers | Jack Ireland | Will Barnes | | Plan for liasing with data providers that we do not have a line of communication with already |

### Notes

#### [Outreach and Community / Communication Channel Review](https://docs.google.com/presentation/d/1xJWddqN7Db0G7CZU2vNGo3YRxrL6W4wr3azYHDHm0KQ/edit#slide=id.g146be120029_2_78) -- Laura Hayes

* community--users, futures devs, instrument teams, data providers
* why? grow, sustainable, identify needs, feedback loop between the users and devs (not necessarily different)
* "it didn't work so I tried something else/thought that sunpy can't do that" -- we want to avoid this
* we have a lot of forums--is it too many?
    * push discourse more?
* in the past, "short" tutorials at SPD, AGU
* the personal connection is big!
    * If you know someone already contributing, it lowers the barrier to entry significantly
* discussion re: whether to replace mailing list with discourse
    * Stuart: sunpy-dev mailing list is dead, we can do away with it
    * More effort needed to put into discourse before we can migrate
    * Mailing list is still reasonably active
    * discourse is more modern
    * mailing list and discourse are technologically equivalent
    * David: mailing list is 1-to-many, release announcements
    * "you can configure discourse to interact with it only via email"--Stuart
    * There is a lot of momentum behind the mailing list, academics love listservs/email
    * The mailing list has been around for a long time
* We've done a lot of tutorials at conferences, but they tend to be last minute
* Working directly with people is the best entry point!
    * Know someone in your lab, meet them at a conference
* The showcase/forum seems to be a successful format
    * Move forward with this feedback forum
    * At TESS, we didn't have much time for the actual feedback part (late in the day)
* Dedicated showcase time--gives people buy in
* Summer schools--STFC, PyHC, instrument workshops, ...
    * Put a face to the project for people early on in their career
* More strategic approach to having a presence at a conference
    * Plan ahead for the upcoming year!
    * Branding is important here
    * Twitter is a good platform for this
* Long term strategy for conference attendance
    * Where are the conferences
    * Who is going
    * What are we presenting
    * Find ways to get someone there if they are not/funding
* For instrument specific conferences, tutorials should be targeted to the data products from that instrument
* Danny--chat window directly in the docs
* Anecdotally, people don't use sunpy/python because of inertia from work
* Messaging around the ecosystem is not clear
    * Show that sunpy is an entrypoint to the ecosystem
    * Historical context, the "why" could help to clarify this in the docs
    * Comparison to SSW and the `gen/` tree
    * We need a graphic that captures this structure
* Our docs need way more visuals, less text
    * Text if they want it, but the visuals should tell you everything you need to know
* Funding for a SunPy Summer School
    * STFC
    * UKRI
    * how much money would this cost?
    * Scope needs to immediately be larger than just sunpy (+astropy, scipy ecosystem, etc.)
* Consistent branding across workshops, institutional presentations

Helionauts discussion

* We should pay attention to it but not feel obligated
* It is an important resource to the community, we should be careful in the way we talk about it
* Redirect people to sunpy channels of communication
    * Show them they are likely to get more help from our project channels

TODOs?

- 🥬 Delete the sunpy dev mailing list, all development discussion happens on GitHub and element
- 🥬 Investigate if we can configure discourse to automatically post announcements to the mailing list
- 🥬 Strategy for (slowly) migrating from sunpy mailing list to discourse
- 🥬 Build a tutorial template
- 🥬 Build a presentation template (in many formats!)
- 🥬 Remove blocks of text from the Getting Help page - make it really easy to click through to e.g. the mailing list/discourse/chat
- 🥬 Clean up the project readme
- 🥬 Run the survey more regularly

#### Metadata Object API -- Danny Ryan

* See https://github.com/sunpy/sunraster/blob/main/sunraster/meta.py
* Sliceable metadata object
* Want to agree on standardized names for common pieces of metadata
    * Access as attribute, not just key
    * `meta['OBSERVATORY']` or `meta.observatory`
* Representation independent of data source
* Somewhat of a generalization of what we are already doing in Map
* Hierarchy of metaclasses/ABCs define standardised names for common metadata, e.g. `meta.observatory`
* Should not be tied to FITS
* Nabil: Have you considered adding automatic attribute generation when adding keys?
    * Danny's initial feeling is no because the attributes should be drawn from the community-agreed standardised names. Users can add any metadata names, not necessarily just those agreed by the community and defined in the hierachy of metaclasses
* Sliceable part
    * Some metadata is "axis-dependent", i.e. that are different at different pixels along an axis, e.g. exposure time.
    * This metadata does not necessarily have a unique mapping from pixel to world, i.e. two images could have the same exposure time.  Therefore they are not coordinates and can't be described by WCS.
    * When data array is sliced, this metadata also needs to be sliced to stay consistent.
    * Metadata object sliced by the same slice item as is used for the data array.
* It's just a dictionary so the values can be anything, any Python object
* A bold proposal
    * Sunpy map should store metadata on metadata object
    * All convenience properties on the map are moved to the metadata object (e.g. `map.detector` vs `map.meta.detector`)
* David asked about a sample problem that that solves
    * Variable exposure time for slit position (see above)
    * Standardized API for metadata a la what we've done in Map
* Discussion about the extent to which we should keep around the original data and in what representation.

Is this model an acceptable way forward for SunPy data objects?
* Broadly speaking the group felt positively, but some specific issues were raised.
* As with Map, meta attributes provide an opportunity to combine metadata into more useful higher level objects, e.g. Quantities. Should the original metadata of which these objects are composed be kept or deleted?
    * Stuart - These metadata data should be stored in these objects as attributes and the metadata used deleted from the dict-like general metadata
    * This means any dict keys left de facto are deemed "not understood" by SunPy/metadata data object.
* David: User should not interact with the keys in the metadata, only the attributes
    * aka a user does not have to think about FITS keys
    * Unless those keys are not understood by the metadata framework and aren't parsed into higher level objects and stored in attributes.
* How does this related to WCS metadata?
    * Stuart - Map generates WCS on the fly from the meta.  Plus other WCS-related metadata is built from the metadata, e.g. `.observer_coordinate`.
    * FITS keys are flat, but many include both "normal" metadata keys as well as those used to create the WCS.
    * However, this is not always the case. In FITS with multiple extensions, the 0th extension has no data and "noraml" metadata, while other extensions have data and only WCS metadata.
    * Danny & Nabil - WCS information should be stored in a WCS object.  That way they can be broken away from the rest of the metadata. Stuart was concerned by this.
    * Nabil - Where should the `observer_coordinate` live?
        * It currently lives at `Map.observer_coordinate` but is built of the fly from the metadata.
        * This model intrinsically links WCS and meta.
        * Danny - Keep `observer_coordinate` at the `Map` level but have it build the SkyCoord from the WCS object, not the metadata, or have it stored as a static SkyCoord
        * Stuart did not agree. More discussion and understanding needed as Danny and Stuart could not understand each other's positions/concerns.
        * Nabil - Ideally the observer coordinate would be on the WCS object, i.e. `Map.wcs.observer_coordinate`.  Could this be achieved by engaging this astropy?
        * Stuart - In theory, maybe.  In practice probably not.
    * Consensus was not reached on separation of WCS and Meta.  More discussion and understanding required.
* Question to the room: Would people be happy to move Map's metadata from the Map level to `Map.meta` level?
    * Initial feeling yes.
    * Will & David - This would cause many people's workflows to break.
    * Stuart - This can be handled by a technical solution: if user calls an attribute that doesn't exist, Map searches for it in `Map.meta.XXX`.
    * Group agreed that the docs could/should tell people to used `Map.meta.XXX` but also support the `Map.XXX` for a long time.  Maybe `Map.XXX` can be deprecated over a long timescale.  But doesn't have to be.
    * Future SunPy data objects based on `NDCube`, e.g. a spectral object, should only support the `self.meta.XXX` API.

TODOs

* 🥬 A list of the things we want a metadata object to do
    * Is there a pre-existing metadata standard that could guide the development of a SunPy metadata object? (JI added this comment)
* Danny should merge a the fundamental infrastructure for this metadata model into ndcube before Map it made to inherit from NDCube.

#### Governance -- Stuart Mumford

* Goal of session to have structure pf new documentation for governance agreed
* SEP2 describes current governance structure
    * SEP2 was written in 2014 before numfocus
    * Followed US non-profit model
    * Self elected board votes on SEPs
    * Executive part runs the project Executive director = lead developer
    * Should have deputy or
    * All board members were active or recently active developers
    * Board has moved into more diverse as members transitioned to management roles
* Financial control moved from board to lead developer
    * many of current board members couldn't vote on financial matters
* Board has changed some what member left and onboarded
* Board is mainly mid-career (e.g. recently prof )
    * No PhD or grad students on board
    * At inception many board members were early career researchers
    * Some prizes define Early career as within 10 years of getting a PhD - should we adopt this definition?
* During COVID times board has been somewhat static
* Reorganisation of board governance structure
* What should the governance of the project do:
    * what should be kept
    * what needs to be changed
* Run for the community by the community
* Current structure can be overly bureaucratic
* What does the board do:
    * numfocus expenese approval
* Board has moved to a more advisory role
* Biggest changes need to be around the executive
* Action: Email board meeting notes out after meetings
* Projects, like sunpy need a final decision making body/members
* Primary role of board to ensure funding to meeting the project roadmap
* Should the board review the roadmap and activity to ensure actions are being taken to achieve roadmap
* Are the board responsible for enforcing CoC - lead developer should bring CoC violations to board which reviews actions taken by lead developer
* Point of board to bring somewhat outside perspective to justify project activities
* SEPs are not very visible to community - maybe add to website
* Stuart involved in astropy governance review to address astropy issue to obtain funding
    * project members - trusted community members who vote to elect the committee
        * how/how are project members defined?
            * nominated from existing members wtih min threshold
        * are you a member for life? emeritus members
        * how is it bootstrapped - small initial set created and then immdiate round of elections
    * executive (steering committee) become elected committee >=2 people ~4+/-
        * financial control
        * commit access control etc
        * odd or even number has implications for decision making
    * advisory board have no hard power but run elections and meet with and committee to advise (could trigger election if executive in stalemate)
    * seperation of concerns - members/executive/board?
    * does this not add more bureaucracy?
    * is the need for 4/5 people driven by time constraints or because of desire to ensure no 1/2 people could missmange
    * how do currrent project roles and executive interact
    * smaller version
        * members vote in lead dev
        * members also vote in other key roles instead of lead dev
    * very small community means some roles may overlap
    * members vote in lead, deputy and one other major role (maybe fincial)
    * if the board don't approve SEPs and there is no executative or small they have a lot of power
    * SEP are consensus based a vote would be to agree consensus has or has not been reached
    * Helpful to keep a guidance of the project from the outside interms of larger solar phyics community
    * advisory board (committee) could have slots for PhD, ECR etc
    * what roles should be voted - proposals:
        * lead and deputy and 3rd role?
        * why not two co-lead devs?
        * sepcific financial role
    * How do these proposal change/alter interaction with current and future funding
        * Do numfocus require a min number of people on executive?

#### Data Provider Relations -- Jack Ireland

* On broader view, NASA is making a big push so that data has better metadata and is easier to access, open-science is big theme going side (data, data-providers, open-source e.g. sunpy etc)
    * For SDAC, this means asking for more funding etc
    * SDAC budget now has specific support for sunpy developers
    * VSO has also expanded, more support that will continue and as needs change more support will be requested as needed
    * Good news - bigger push towards open science, meta data standards etc
* Will support for data providers etc go back in time? (i.e. looking at old data?)
    * Yes from Jack, effort for older data to be brought up to standards e.g. SOHO/LASCO data

* If there are instruments that need help in getting data into better standards for meta data etc there is scope to do this (maybe even SkyLab(!))
* VSO can also give assistance/advice for older datasets to be more easily queried etc (I think thats what was said?)
* How does support for sunpy development etc get accessed from this source?
    * Someone sends Jack an unsolicited proposal, and it is reviewed by people in the community
    * Decision would be made by folks on larger sunpy community (e.g. board etc) for larger proposed efforts/changes

* From VSO meeting - where do the VSO and sunpy responsibilites meet?
    * e.g. VSO client code
    * SOAR - David: two sides, want people to have access to the data, but on the other side dont want to write a specific client for every mission, so this is why the VSO is ideal
    * Another example, SUVI, level 2 data available online, however NOAA have asked not to provide it through the VSO due to fact its not of "scientific quality", however it is availble through sunpy

* VSO currently has available ~83% of the data that it says it will provide

* Propagation of errors to sunpy - how can a VSO error message become less opaque?
    * show there be a VSO dashboard to show errors, or what is down or not down. The VSO health status - e.g. "please check the VSO health status: `link`"
    * How to differentiate whether the search is wrong or can not be made due to server down or whether there is no actually no data available
    * The VSO also wants to point to the issue - for example the HAO could be down and want to propagate this (i.e. its not the VSO thats the issue its another server etc)
    * VSO also wants to provide an easy machine readable health report that checks every hour or so.
    * Future version of Fido could first check the health status of the VSO before going to query
        * however this would be a challenge as you build the query before you know what provider you are pinging
    * XRT another example, the data provider (CfA) is down and people think that sunpy or the VSO dont provide XRT where is actual fact they do if the issue with CfA is fixed (which it will be soon :tada:)


* In-situ data providers?
    * is spdf the vso of in-situ?
    * if there was a sole ESA mission would it be within the spdf to index that data?
    *


* No exchange of funds between NASA and NJAO but the VSO still provides the data. This is more of a mutual agreement - want data to be provided to community

* Difference between SOHO and Solar Orbiter in terms of combining in-situ and remote sensing data is that the data analysis environment have changed. Having one environment to combine both would be ideal. The VSO does not need to change etc.


* Could Fido be taken out of sunpy and be "one provider to rule them all"?
    * Will: Heliocloud people would be very interested of a data search functionality outside of sunpy i.e. be its own package?
    * If people wanted to download data outside scope of sunpy (e.g. magnetospheric) and use Fido, why should someone need to download sunpy? would this just become a large python VSO
    * However, do you want to fragment packages more, another package to maintain etc
    * View of others that want Fido outside of sunpy - why should I have the sunpy dependency?
    * The drive for one downloader to rule them all is from a NASA or overarching view of one big heliophysics downloader, maybe Fido has a HAPI interface
    * There's no point in moving it out unless someone is going to use. For example, where would the Fido clients live? the data model of the core attrs reflect the solar data provides (e.g. heavily influenced by VSO)
    * Several arguments for, but no one is making them (apart from having sunpy dependency)
    * Response to people to ask - ask they to raise and issue with their arguments

* VSO take-aways:
    * health reports
    * propagation of error messages back to user

* Data clients - what needs to go/stay?
    * Should there be duplicates - i.e. provide same data from different providers (e.g. VSO is down, but the webserver is up and visa versa)
    * Radio data is a good example
    * LYRA data is soon to be on the VSO
    * XRS is also a VSO ticker (but not a priority)

* Bigger picture - what clients should be in core?
    * could it be opt in?
    * should sunpy core only have vso/jsoc?
    * what about SOAR? shouldnt that be in core? It will be indexed by the VSO but the SOAR is still the official source.
    * VSO is more institutional but sunpy are more like talking to users
    * Should there be a formalized relationship between sunpy and VSO to have link between providers users?


* Data providers in both places (e.g. sunpy writes a client, but then it becomes available on VSO what should be done?)
    * VSO could be the institutional contact before we develop a client - support and assist in this as they have those relationships with instrument teams/providers

* How should the VSO be contacted? What is is the best way to message the VSO with an example?
    * VSO chat? Stuart and Will currently on the VSO chat
    * However the sunpy developers chat is also a place monitored
    * The shared chat system works well!

TODOs

- 🥬 PR the soar client to core, get the soar team to sign off on our implementation of our client, make sure it is feature complete
- 🥬 Re-review our list of clients and assess implications of getting rid of them from core if they are duplicated in the VSO


## Wednesday 24 August

| Time | Title | Presenter | Moderator | Scribe | Desired Outcome |
|:----:|:-----:|:---------:|:---------:|:------:|:---------------:|
| 9:00 | State of the CI | Conor Macbride | | | |
| 9:30 | Standards and Formatting | Nabil Freij/Stuart Mumford | | | Decide whether to apply black to the core repo; plan of action for doing cleanup/maintance throughout the repository; `mypy`????? |
| 11:00 | Supporting SolO | Shane Maloney/Laura Hayes | | | |
| 14:00 | IWG--Lightning Talks | instrument teams | Will Barnes | | Better understanding of how instrument teams are using sunpy and the SunPy ecosystem |
| 16:00 | IWG--Feedback Forum | instrument teams | Will Barnes | | Better understanding of the software needs of instrument teams and a plan for meeting those needs within the ecosystem |

### Notes

#### State of the CI -- Conor Macbride
**put link to slides here**
-  Currently run lots of automated checks when code is merged to make sure it's working as intended. See slides linked above for more details.
-  We use a number of services that run the tests and checks:
    -  Most of GitHub actions, using `tox` as a layer between the CI provider and `pytest`
    -  Figure tests use circleCI, because they have easy hosting of HTML artefacts
    -  Code checks use pre-commit.ci which is very fast, and can automatically fix codestyle issues
    -  Code coverage uses codecov.io
    -  Docs use readthedocs.com
    -  Changelog checks use OpenAstronomy/baldrick running on Stuart's server
    -  Automated backports use Meeseeks Box
    -  Azure pipelines is still used for some affiliated packages
-  Recent updates:
    -  Migrated from Azure Pipelines > GitHub actions on sunpy core
    -  New figure HMTL dashboard
    -  Both of these updates have been contributed upstream, giving them wider use beyond `sunpy` :tada:
-  Future updates:
    -  Improvements to benchmarking (currently using `asv`)
    -  Mocking HTTP requests for online tests to improve CI reliability and speed
    -  Add a CI status dashboard for all SunPy projects


🥬 Add a sunpy project board to keep track of larger projects separate from the issue tracker (e.g. sorting out remote testing with `vcrpy`)

### Standards and Formatting -- Stuart Mumford / Nabil Freij

* Current list of infrastructure TODOs: https://github.com/sunpy/sunpy-project/issues/2
* Motivation: have more uniformity across all of the repositories in our project
* Technical bits like formatting
* Also, make the way we review PRs across the all of the repos in the project more uniform
* Note that this is for sponsored packages only (under the sunpy org) and not affiliated packages
    * But also make it easier for outside packages to follow the template
* Vision for the future
    * Make a change to the package template (e.g. CI scripts)
    * Bot goes and opens a PR to any of the repos that are using that package template (e.g. affiliated packages)
    * https://cruft.github.io/cruft/ may be a possible solution
* Package template as it stands
    * Uses cookiecutter (package for generating package infra from a template)
    * Ability to configure with different options all saved in a file (version controlled)
    * OpenAstronomy has one and also primarily documentation on how to build a package: https://packaging-guide.openastronomy.org/en/latest/
    * It has been a bit neglected in the past few years
    * Original plan was to sunpy-ify this template
    * Stuart: package template is primarily for the sponsored packages
        * But also for affiliated packages who want to opt in to all of our workflow choices (e.g. all of our bots)
    * Question: what should we recommend to instrument teams asking how to structure a package?
        * OA template -- more stuff to be added, but what's there is solid
        * Stuart planning on working to update/maintain this
        * sunpy package template will build on top of this and be more opinionated
* Problem: we don't have a system of labels across all of our projects
    * We could define a single set of common labels (e.g. "Good First Issue") to be used across all repos
    * But this does not preclude tags used only on one repo (e.g. "Map" for core)
* Problem: we use different CI systems across all of the repositories
    * Some still on Azure
* List of things to standardize across all of the projects
    * PR review process
        * Nabil tends to be the one reviewing/merging PRs across other projects.
        * How do we get more reviews on non-core PRs etc?
            * Nabil could be more annoying.
            * Worried about review time on large PRs to non-core.
            * 🥬 Give everyone with commit access to core commit access
* Sponsored packages seems to have two meanings
    * Those that are on the page as sponsored packages
    * Those that are under the repo that we are working on
* Debate around what are the requirements for a repo being under the org?
    * If its there, it doesn't mean that its sponsored
    * But it does mean that we have to watch it/maintain it
* Marcus: if it is under the sunpy.org, I would assume there is a certain minimum quality
    * Laura: this could compromise people's impression of all of the other packages under our org
    * Solution: put some sort of disclaimer in the README that says something about the dev status
* We need to define a procedure for proposing a new package that will live under the org
    * Create an issue on sunpy-projects
    * Give rationale for why it should live under the org
    * Gather consensus from the community
* Precommit / codestyle
    * Type hints: telling the type of the inputs
        * Nabil wants to apply type hinting
        * Use mypy to do type checking
        * Nabil: many of the projects that we are depending
    * Precommit / black
    * This is (arguably) something that helps both the users and the developers
    * This adds a lot of dev overhead (you have to know how to use them) and reduces readability
        * Stuart tried to type hint in APE14 with no success
        * David: typing does make you think much harder about the complexity/scope of the code you're writing
    * Problems this is solving?
        * Shane: helps you find the bugs in your code much more quickly
        * Dan: adding types makes it easier to see (from a user) what the input types should be
    * Type hints: a developer-focused tool to ensure you're passing in the right thing and returning the right thing
    * Laura: presents larger barrier to new contributors to the package, more intimidating
        * Nabil: migration would be slow; numpy/scipy/pandas etc. use it as does plasmapy
        * Alasdair: it is only a negative if it is enforced on the PR
        * Stuart: it does still present a barrier to reading code / contributing to existing code
    * Consistent problem: will be a problem until astropy adopts type hinting

🥬 Update list of sponsored and affiliated packages on sunpy.org
🥬 Cleanup the repos under the org
🥬 Cleanup the teams under the org
🥬 Write an SEP for type hints
🥬 Write an SEP for black


#### Supporting Solar Orbiter data -- Shane Maloney
**put link to slides here**
- Encounter based solar mission
    - In-situ instruments always on
    - Remote sensing instruments mainly observing during remote sensing windows (30 days/orbit)
    - Not all instruments have full-disc field of view
    - No real time commanding of the spacecraft
    - Complex orbit
    - 10 different instruments
- Summary of data types produced by different instruments - see slides linked above
- Data availability is not continuous
- Want to support both searching/downloading and also interacting with the data
- Things that we can do in core to better support SolO
    - SOAR client into core
    - spectrogram/spectral cube object into core (from sunraster/radiospectra)?
    - Need a multi-dimensional timeseries object for some SWA (and probably other) data
    - Would be nice to do radio propagation with timeseries
- Existing SPICE software, being worked on by Ed Bahn:
    - Quicklook viewer (add a link?)
    - Working on fitting code

🥬 Get in touch with SPICE team and work out what they want the data to look like in sunpy core, including colormaps and norms

#### Instrument working group -- Will Barnes

Slides: https://docs.google.com/presentation/d/1Gp2xSjKwhuMRG1gLxIKmAu5c2duA2b-7gBFuWArK608/edit?usp=sharing

SPICE:

* SPICE is an imaging spectrograph
* Data product: 4D spectrogram data cubes
* Similar tools as IRIS, making them more general
* Reader in `sunraster`
* GSFC developing fitting tool

EIS [(github)](https://github.com/USNavalResearchLaboratory/eispac):

* EISPAC is the EIS Python Analysis Code
* Developed tools for searching/downloading files (archive of L1 files), reading and analysing data
* EISCube subclasses NDCube
* Based upon IDL-routines, uses mpfit.py to fit files
* Want tools for doing spectral modelling (e.g. using Chiantipy) for deriving information from the data (e.g. temperature etc).
* Future tools -
    * tools of quickly visualing, and exploring spectral fits. Want tools for user-generated fit templates
    * Collections for EISCubes for slicing and fitting multiple spectral cubes at once
    * Expansion of fit_spectra() to use other fitting packages such as astropy.modelling (but currently VERY slow)

* What overlap is there between EISPAC and the tools developed for SPICE?
    * There is alot of overlap, but EISPAC was developed in particular to analyse EIS in python
    * One of the main goals was continuity between IDL tools and Python tools which drove the choice of using mpfit
    * Lots of opportunity to collaborate

* EISPAC focused on L1 data, and several things in EISPAC that are specific to EIS and not needed, for example the (EIS) L1 file archive for SPICE. But of course SPICE has its own requirements.
    * Speed of development for need of analysis tools meant that the two were independently worked on (although communication between two was had)

* Some issues with NDCube with slicing and saving back to fits as some coordinate information is lost. More to do from NDCube side on this. EISPAC have overwritten the slicing of NDCube to keep track of coordinate information to save to fits file for loading into a sunpy map. Currently quite "hacky" in EISPAC.

Data search:

* EIS has a Fido client in development. EIS data is available from a directory tree, so first Fido client was a scraper on the site and searches for files between a certain time and not on any other factors. EISPAC searches the EIS catalogue rather than just the time period thats availale in the directory tree

* SOAR webpage has limited flexibility to search for specific data (such as currently its indexed over time and dataset ID and level). But ideally want to search over some metadata (not available at moment through sunpy_soar either).
    * What is needed is also to search over an observing mode/SOOP/event list etc.


SunCASA/EOVSA (Sijie):

* Expanded Owens Valley Solar Array (EOVSA) - imaging spectroscopic capabilities in GHz regime (radio interferometer)
* SunCASA open-source python package for synthesis imaging and visualizing solar spectral radio imaging data
* Dynamic spectra (freqtime), complex visibilities (polarization x baseline x frequency x time) and imaging products (freq x time x space x space)
* Relies on CASA, not ported to Python 3.7+, then SunCASA depends on SunPy 2
* EOVSASpectrogram class which subclassed from radiospectra and is in development
* Pure python development of reading measurment sets into Dask arrays (without needing CASA) see: https://casa-formats-io.readthedocs.io/en/latest/ :tada:
* Also developing pygsfit for fitting gyrosynchrotron emission. Its a widget based tool to visualize and analyse high-dimensional radio spectral imaging data. Spectral fitting based on GS and thermal emission model.
    * The fitting capability is available outside the GUI, it is also CLI

* Is SunCASA EOVSA specific? can a LOFAR ms be passed?
    * It was developed for EOVSA but can be expanded
    * As long as the ms is in the CASA format it _should_ work. However, in the US EOVSA is only the solar radio telescope with ms.
    * LOFAR should work, as SunCASA is quite generic.

* EOVSA within radiospectra:
    * Currently can read the ready made EOVSA dynamic spectra, and Fido can search for those dynamic spectra already available.
    * Small issue with getting the data to look same as on the EOVSA website, should be a small issue


PUNCH:

* PUNCH constallation of satellites to look at white light/polarisation of the Sun with a large field of view (6-180 solar radii)
* Pipeline:
    * instrument specific calibrarion -> alignment -> polarization resolution -> quality marking -> mosaic building -> F-corona and starfield subtraction
* Level 3 products are full resolution of brightness and polarization brightness and other things
* Pipeline is called "PUNCHBOWL", managed by Prefect, provide a python tools
* NDCube is core data handler!
* PUNCH can contribute the polarization resolution code as a separate package (affiliate package), and punchbowl too.
* Imaging mosaic using astropy reproject
* PUNCH wants a strong relationship with sunpy as it's being developed  :tada:
* how is reproject dealt with for different observer location?
    * how is the 3d position assumption used with PUNCH?
* There is currently no Affiliated Package Liaison - who should PUNCH contact directly -> Will! but also on the sunpy chat.
    * Will has now been added as the Affiliated Package Liason :tada:
* Data representation: currently PUNCH uses dictionaries of NDCubes. Need advice
    * NDCollections could be the solution! But PUNCH found issue with aligned axis - will chat offline
    * Other point -> Dan: Maybe the Metadata class could be a way to go, maybe we should standardise some metadata standard in solar? More discussion here
    * PUNCH can help shape this idea with their use cases


HERMES:

* HERMES a payload as part of the Lunar Gateway, which kind of like the ISS orbiting the Moon as part of the Artemis program
* HERMES : Heliophysics Environment and Radiation Measurment Experiment Suite
    * Particles and field instruments for radiation and space weather instruments
    * ESA also has a payload which is part of this too (ERSA)

* Launch was previously Nov 2024, but probably more like spring 2025. While to Moon, so data more like 2026
    * 2 years nominal science mission
    * Studies interplanetary medium (solar wind) and terrestial magnetotail
    * Pathfinder for space weather payloads for science and space weather

* 4 instruments on payload
    * MERIT, NEMISIS, SPAN-I, EEA
    * all space physics instruments
    * electron and proton flux, magnetic field vector, fluxgate sensor, ion flux/density/charge etc

* Link of this to sunpy -> Steve. But wants to base it on the development behind sunpy

* 4 instruments -> 4 packages (actually 5 packages)
    * this is a challenge and takes time, some help would be good

* NASA Heliophysics Division Science Data Management Policiy
    * all packages open source
    * codes for analysis will be available
    * but also code to go from lower level data to higher level data
    * both within packages
    * all processing will be done on the cloud (AWS), so this brings requiremnets to the packages so that they can be run on lambda functions
    * add data products will be provided as cdf files

* What is the data types of these measurements
    * mainly timeseries
    * fluxes in different energy bands
    * spectra as a function of time (and of angle as a function of time)

* Everything is being developed openly [(github)](https://github.com/HERMES-SOC)

* Space physics does not typically use WCS, so no real need for NDCube
    * if we want interoperability between in-situ, we need to think about how we develop wcs-driven data conatiners for remote sensing.

* Steve: someone should maintain a set of package templates that do not necessarily depend on sunpy
    * send them all to stuart

* There should be an instrument specific package template as requirments are different for analysis packages and instrument packages.


* Steve: We consider our userbase as people running locally, but we also have to consider people running on the cloud, and this is something we should think about, especially about running environments (and dev environments) on docker.
    * We'll chat about this more tomorrow

DKIST:
 * 4m ground-based telescope in Hawaii
 * 5 instruments
     * imagers, scanning split spectrograph + polarisation, spectropolarimetry

 * 12 TB a day of data once everything is up and running
 * All calibration codes are publically available on bitbucket, majority in python
 * Could end up 100s of 1000's of fits files per observation
 * NDCube 2.0 development was for DKIST datacenter (stuart)
 * Using dask for data within files, and gwcs for coordinates within array, all built upon NDCube
* All metadata in an asdf file, to describe info for data structure, gwcs etc - all the things
    * can download all the metadata for a dataset, and then can decide based on the metadata in that file what you want to do
    * asdf approach of having all metadata in one place is extremely useful, tested 100,000 files in one go, to check fits headers etc.
    * Want to make use of building [dask](https://www.dask.org) arrays for this

* Dask is great, lots to be done in solar/astro extensions of using it for our analysis (Will working on this amoung some others)
    *  Dask can be confusing on how it works - will that be abstracted away with sunpy/dkist tools? should be relatively easy locally but can be "fun" (really complicated) when doing things on severval remote servers


* Challenges for large data with sunpy - e.g. ground-based instruments. Cant load/play movie etc.
    * IDL does very well in terms of plotting images, matplotlib isnt build for this, and unable to do.
    * WCSAxis slows this down
    * Coordinate information not that important, unless you want to combine with other observations. If you want a quick look movie or look at a feature in particular, you really only need pixels
    * [PyQtGraph](https://www.pyqtgraph.org) is a good package for doing this
    * [napari](https://napari.org/stable/) is also good
    * [holoviews](https://holoviews.org) is another one

* Should speedy visualization of data be on the roadmap? i.e. quick plotting. Do we just throw away coordinates
    * sunpy has typically focused on coordinate aware arrays, but how does this fit into sunpy (e.g. just read data arrays with astropy and plot data array?)
    * regardless of where this lives within the sunpy project, there is a need within solar physics to rapidly visualise large datasets. This is missing from the project, so would be a good item to put in the Roadmap
    *

STIX:
 * STIX is great and developing well within sunpy ecosystem
 * could STIXMap and TimeSeries be upstreamed to core in the future? maybe but probably not a good idea -> core shouldnt have instrument specific sources


CubiXSS/MOXSI:
 * Multi-order X-ray Spectral Imager
 * Overlappograms - lots of orders, slitless spectrograph (i.e. without having to raster) but challengng to disentagle the information from the overlappogram
     * Will showed the magic that can be done with the wcs machinery :dizzy:


SST:
* Most people use the two main instruments: CHROMIS and CRISP
* Images of same field of view, scanning slit spectro-polarimetry (CHROMIS currently does not have polarimetry but may have in the future)
* SST is one of the highest throughput instruments currently operating - can be 2.9TB/hr, and can observe for many hours
* Existing pipeline called SSTRED in IDL [(on github)](https://github.com/ISP-SST/sstred)
    * users dont do this, this is done by an institute and provided
    * data is typically propriety but this is changing
    * issue as data is so large, hard to share
    * end result of pipeline is fits file. To write final files take at least one day
    * metadata is complient to SOLARNET standards
    * WCS-TAB is what is used

* data is visualized with a tool called CRISPEX (IDL)
    * can play movie of cube very quickly, both in time and wavelength
    * CRISPEX can also combine datasets not necessarily from same datasets (can be SST and IRIS for example)
    * two copies of data stored in memory, one in the inverse for quick computation. So if you need 100MB for your dataset, you actually need 200MB


### Package Template (Steve):

* There are tools to keep templates up-to date and packages that use the templates up-to date too
* [HERMES development/updates to package template](https://github.com/HERMES-SOC/hermes_core):
    * For HERMES, the plan is to use it on the cloud, so a dev container within the template. Development is done within this container. Can test within a certain machine, and so can test and ensure it works on the processing machnine. Production level code.
    * HERMES uses github actions rather than CircleCI
    * Instrument specific template may want a calibration directory for caibration files as these would want to be called by the package and also they can change
    * depends on the calibration files - could be on a remote server (based on size) or just in repo if small
    * lots of people doing this (calibration) so maybe we should provide a generic solution - which can of course be customised or changed based on needs
    * documentation: doc template which includes CMAD which is a requirement now from NASA Heliophysics
    * as procssing pileline now has to be available, this must be described and documented so needed in template
    * Would be good to agree on a high level API for thesis instrument packages. e.g. "calibrate_file" or something along those lines. It could be nice to provide a model API within the package. Another example is wavelength response class as this is used by many instruments etc.
    * Maybe get rid of tox - (Stuart shakes his head), just as things are tested within environement

What is benefit of a package that already exists to use a template?
* Steve: If you are using a template, indivudal maintainers dont need to continuously maintain the template, this can be done if the template updated. For example, if github actions changed etc. For easy of maintaining several packages
* You could have a template that maintains itself (opens PRs automatically to do updates)
* Same package structure between packages - easier for contributing and familiarity between them, more potential contributors (lower barrier to entry)
* On the other side, if you are not maintaining lots of packages (unlike HERMES/SunPy), this isnt as important. You have one package so easy enough to keep up to date as these package updates happen on longer timescales
* If starting from scratch, lots of benefits
* another example, setup.py is going away in next two years, so you would need to update the package. but if you had a bot to do updates, it would sort it out

## Thursday 25 August

| Time | Title | Presenter | Moderator | Scribe | Desired Outcome |
|:----:|:-----:|:---------:|:---------:|:------:|:---------------:|
| 9:00 | Frontiers Paper Hacking | everyone | | | a complete draft of the frontiers paper |
| 11:00 | The Next SunPy Paper | Will Barnes | | | A plan for when we will write the next paper and what it will include |
| 14:00 | xarray, WCS, and NDCube | Danny Ryan/Stuart Mumford | | | A better understanding of the differences between how xarray and NDCube/WCS treat coordinate systems and, if possible, a plan for an xarray implementation of NDCube. Add the notes on this to the NDCube docs! |
| 16:00 | Supporting Scalable/Cloud Computing | Will Barnes | | | A plan for implementing changes in sunpy to enable parallel/out-of-core computation with Dask |

### Notes

#### Xarray, WCS & NDCube

* xarray has already spanned multiple communities--from the earth sciences to the brain imaging/neuroscience community
* NDCube--WCS + array together
* impedance mismatch between WCS and xarray
    * astronomers store coordinate information in a WCS
* xarray now vs xarray 3 months ago
    * lots of work being done on flexible coordinate arrays
    * but hard to say what is and is not being supported
    * point of recent dev thrust by xarray is to allow analytically-defined coordinate arrays
    * very new!
    * But needs some testing with an astro case maybe
* Tom Nicholas working on unit support in xarray to have unit support in each dimension
    * Coordination amongst developers in xarray already to understand impedance mismatch between needs of different communities
* Stuart showing p2w example of how different dimensions return very different rich Python objects
    * e.g. Quantity, SkyCoord, Time
    * is this possible with xarray?
        * Martin: you can have arbitrary "attributes" as long as you can store them
            * An attribute can be anything, could be interpreted as the world coordinate
            * attribute tells you the type and the extra information you need to interpret it
            * Would the return types of the
        * when you select a point, you get the coordinate and the value
* In the present picture of xarray, you can do this with flexible index arrays
* FITS provides the standard for where you store the metadata to reconstruct your rich objects that are returned when indexing your array
* Danny making the point that NDCube is now agnostic to FITS WCS
    * Is the xarray approach being proposed a step back towards the old FITS way
    * Martin says no, you can use the same WCS object and attach it in an xarray object
    * `XArrayWCS` class and then would return that when indexing
        * Could be based on FITS, but does not have to be
* Originally, xarray was based on netCDF, but now goes beyond that
    * In the same way now, NDCube not tied to FITS
* What is the current status of this effort?
    * Martin: more fair to say that we (Anaconda) have been cheering this effort along
    * Alec Engell already doing this in his own work, but searching for funding explicitly to do this
    * Existing funding from NASA including Martin, Alec, Jim to try to finish off this effort
    * There are many people who really care about this
    * Stuart to represent astropy and sunpy people on this topic--to prototype this, he needs someone to tell him how xarray works
    * Flexible indexing stuff needs documentation
* Need contacts with the few people from xarray who have a really good handle on this and are looking for compelling use cases
    * Jim, Martin to reach out when someone comes back from holiday...Stuart to be the POC from astropy/sunpy side
* NDCube provides minimalist, but general API that community can build upon
    * Can NDCube become an API-defining wrapper for solar and astro
* CF conventions + xarray is assumption about how coordinates are arranged, named etc
    * Agreed upon document/standard
    * But CF is designed specifically for earth science
    * We already have a convention for the set of parameters we use
    * xarray could support that in the same way
* Still space for an NDCube object (as a subclass for xarray)?
    * Best of both worlds (astro-specific stuff + power of xarray)
    * data-tree example of glueing collection of things together with xarray subclasses
* We want something that benefits the users, unlocks different parts of the ecosystem
* Stuart: we stil have a lot to learn about xarray
* Danny: long term project of collaboration between these communities
    * Not competitive
* With large data volumes, not practical to pull everything down to your machine locally
    * xarray had to go through this transition
* Martin: fsspeck support for loading FITS in astropy
* Solar in this era has so much data, but not taking advantage of this data
    * Earth science has Pangeo, but there are still many people with older tools that are not doing this
    * three camps: can't deal with volumes, those who deal with volumes in old ways, Pangeo
* Python + Dask lends itself well
    * works on a variety of platforms
    * should be part of our pitch to "why sunpy/ndcube"
* kerchunk
    * way of indexing data files to present them as zarr
    * typically worked with HDF/CDF and then load them with xarray
    * save and then just load the metadata, don't need the specific data loaders
    * slice and dice with Dask and xarray
    * This also applies to FITS!
    * example using FITS but out on its own until astropy can read Zarr
    * interesting case (added complexity) will be astro and helio because things are gridded and evenly spaced in time
    * you can slice your files down before actually loading them
    * in principle, you can just get the stuff you need
    * "let's just pretend it is Zarr"
* Stuart: for dkist and aia, we need support for tiled compression
    * Example of this is Rice compression
    * Stuart and Tom are planning to reimplement tiled compression algorithm in pure Python, astropy won't have to rely on cfits
* kerchunk is a logical set of arrays -- more than just one xarray
    * If you're not using Zarr, you have to build up the Dask array yourself
    * with kerchunk, the chunks do not have to be uniform in size
* Danny: what is the ecosystem here?
    * similar to numpy in that it provides the storage memory object
    * things you can do to it
    * but mostly used by other projects
    * pandas on the other hand provides a lot of things that you can do to it and most people just use base pandas
    * xarray is closer to the pandas side
    * but ndcube is closer to the numpy side
    * ncube is a kernel around which a lot of other things are built
    * Martin: difference between those usages isn't that big
* We should at the very least pursue a prototype of this
    * whoever does NDCube 3 needs a very good understanding of xarray
    * but question of funding/time
    * Stuart and Danny spent A LOT of time on NDCube 2, but 3 doesn't have the same level of support
* What are the advantages of this?
    * Dask
    * interoperability with the larger scienticic python ecosystem -- not cutting ourselves off
    * multidimensional timeseries support would basically be done
* People are using xarray in solar now
    * we should not present ndcube as a competitor to that
    * xarray has first class support for lookup table coordinates now
* If all this stuff had been in xarray a few years ago, would we have NDCube?
* NDCube will still continue to exist, even if it is just a thin wrapper around xarray
* Support for rich Python objects returned is very important


Timeseries and xarray

* Stumbling block for using xarray may be time
    * No support for leap seconds
    * Many solar applications still require very high time precision

#### Supporting Scalable/Cloud Computing

* Heliocloud
    * effort by NASA to have compute + data in the cloud to support researchers
    * "how to we make heliophysics data useful in a cloud architecture"
* Stuart: can I use the data in the cloud outside of heliocloud?
    * You don't have to have a NASA ID, but you will pay for compute
    * There are also access costs
* Reason for this session
    * heliocloud created data analysis env for the summer school this year
    * involves many packages in the PyHC ecosystem
    * question for sunpy: how can/should sunpy support cloud-based science?
* Some operations on sunpy.Map force eager computation on a Dask array
    * Will needs to systematically identify these
    * figure out how to address these
    * Can we "daskify" SunPy? Where are the chokepoints?
        * Coordinates?
        * Reproject?
* Also I/O problems
    * Difficult
* Data formats are going to play a signficiant issue in how we enable science in the cloud
    * experiments with Zarr
    * kerchunk very useful -- translation layer between zarr and fits
* Zarr is two things
    * chunking specification
    * chunk file format + JSON file with description of these chunks
* you give kerchunk a specification regarding the structure of your files, knows where the binary data is
    * caveat: you're stuck with the chunking
    * caveat: you have to do file parsing to set up the metadata structure
* If AIA L1 data is supported, should rechunk to 256-by-256 (not 1 chunk per row)
* Use case: fitting spectra from sections of SST data
    * not as simple when you have more arbitrary functions
* Friction between Dask and astropy
* You can use with SunPy with Dask
* Outstanding questions about using SunPy functionality with Dask arrays
* People aren't necessarily telling us about the incompatibilities they're encountering

 TODO

* Example of how to use Dask + NDCube
     * How to create a Dask-backed NDCube
* Example of how to use Dask with sunpy
     * Extend existing examples
     * Would also be useful in finding chokepoints
* Assess whether coordinates stack can be Dask-ified
* Reproject

## Friday 26 August

### Hack Day Ideas

Brainstorm your ideas here. Once we settle on a few projects, we can write more long form descriptions and put them in the next section.

* An example gallery for NDCube -- Will
* Map/NDCube refactor experiment -- Will
* Add basic dunder methods to NDCube -- Will
* NDCubeify radiospectra -- Shane
* Funding in Europe -- Shane
* Re-do the sunpy.org landing page to put the sponsored package ecosystem front and center -- David
* Presentation branding -- Will
* Do some outstanding affiliated package reveiws
* Draft an SEP defining an API for a generalised metadata object
* ASV -- Albert
* SolarOrbiter Meeting -- Shane
* Draft an SEP proposing standardised metadata data attribute names -- Danny
* Add `pfsspy` project status and roadmap to the documentation -- David
* Improving Element onboarding and discoverability -- Stuart
* Finish `vcrpy` work
* Write https://github.com/psf/fundable-packaging-improvements/blob/master/FUNDABLES.md for the SunPy project
* Fix [NDCollection bug Marcus reported](https://github.com/sunpy/ndcube/issues/535) -- Marcus
* NDCube for solar radio interferometric images -- Pearse
* Scoping out a sunpy-models package/in-core (e.g. X-ray emissin models etc)


### Hack Day Projects

### Hack Day Results
