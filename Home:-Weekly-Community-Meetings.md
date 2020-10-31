# Weekly Community Meetings

The SunPy weekly community meeting is held every Wednesday at 16:00 UTC. The link to these weekly teleconferences can be found [here](https://sunpy.org/jitsi). The minutes for each meeting are recorded below. The agenda and minutes for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). Community members should feel free to edit the agenda and add items as appropriate. Agenda items not covered at this week's meeting will be bumped to the agenda for the following week. Typically, the lead developer or deputy lead developer will announce the community meeting in the chat a few hours prior to the start of the meeting.

## 28 October 2020

### Agenda

* 2.1 release triage
* PR Discussion
* Issue discussion


### Minutes

## ROSES Call Notes

* Emphasize that these duties are not constrained to the core code base
* This role is largely focused on the project as a whole--make sure to emphasize this in the proposal

### A List of things to do right now!

* Daily issue triage
    * Back catalogue
    * As they come in
* Mailing list/Discourse maintenance
* Dev-ops automation infrastructure
    * Package template
    * CI monitoring
    * Make this less human in the loop!
* Development work
    * Adopting stale PRs
    * Less development in the first year, more in later years
    * Big feature requests from the community!
    * Offload science features to community and review
    * Non-science features that are important to the package and useful, but less likely to be implemented by the community
* Fill open roles
* Organize coordination meeting
* Affiliated package
    * Review / Re-review procedures
    * Webpage
    * Recruitment -- interfacing with instrument teams (instrument teams should front some cash)
    * Updates for breaking changes in sunpy/other dependencies (e.g. Fido in radiospectra)
* Interfacing with upstream changes
    * Need to react quickly to these changes! These are the most time-sensitive
    * How do we monitor these changes?
    * Data providers
        * e.g. GOES XRS
    * Packages
    * CI
* Mentoring
    * Filling open roles
    * Educating community
    * Onboarding contributors

### Reorganize

* Large future project design
    Scope out and describe on issues project plans for large features i.e. metadata rewrite. To facillitate contributions or funding from other places etc. Also have discussions about these things before the dev work happens.

* Day-to-day Duties
    * Issue triage
    * PR review
    * CI monitoring
    * Mailing List / Chat support
    * Helping with releases / doing bugfixes
* Technical infrastructure
    * Development of Project Automation
        * Package template & auto PR bot
        * CI dashboard
        * Release reminder bot
        * Completely autonomus bugfixes
        * Document the shit out of all of this for benefit of wider community
    * CI maintenance
    * Sponsored package template / updates
* Project infrastructure
    * Milestone policies
    * Drafting SEPs
    * Organize weekly meetings
    * Organize coordination meetings
* Interfacing with and reacting to upstream changes
    * Need to react quickly to these changes! These are the most time-sensitive
    * How do we monitor these changes?
    * Data providers
        * e.g. GOES XRS
    * Packages
    * CI
* Community Interaction
    * What features do we need in the project?
    * Fill open roles
    * Affiliated package
        * Review / Re-review procedures
        * Webpage
        * Recruitment -- interfacing with instrument teams (instrument teams should front some cash)
        * Updates for breaking changes in sunpy/other dependencies (e.g. Fido in radiospectra)

## 21 October 2020

### Agenda

* Milestones
* 2.1 release triage
* PR Discussion
    *  Remove self_test() references from docs https://github.com/sunpy/sunpy/pull/4586
* Issue discussion

### Minutes

* Policy on PR milestones
    * Milestones should only go on PRs that block a release
    * Backport PRs should be milestoned to the bugfix release
    * Manual backport PRs should include only one backport per PR and should be milestoned in the same way as automatic backports and should reference the original PR
    * Where do we record this new policy?

## 14th October 2020

### Agenda

* PR Discussion
* Issue discussion
* Small dev grant
    
### Minutes

* Discussion of LASCO headers--fix is fine given the inconsistency between the metadata and image
* NDCube 2.0
    * Done when it's done
    * We should wait on 2.0 before starting discussion about how to use it as the base data structure for `Map`
* Coordination meeting
    * Need to discuss revamping of `Map`
    * Probably best to wait until January/February 2021
* The sponsored package dashboard is cool
* We have a lot of sponsored packages, maintaining them is hard
    * e.g. `radiospectra` and `drms` need retemplating
    * Everytime the package template gets updated, it would be nice to be able to propagate these changes downstream
* Laura interested in doing more work on `radiospectra`, possibly with help of students; needs reviving!

## 7th October 2020

### Agenda

* PR Discussion
* Issue discussion
    
### Minutes

* map.rotate PR addressed https://github.com/sunpy/sunpy/pull/4502/files
* We need to properly test how different package affine transform and their effects on the data.
* We should test the 'ground-truth' of a map.rotate with reproject (flux conservation) with other affine transformations on a SDO image. This is worth writing a paper upon with the results - as a 'standard'/best practices that can be referenced. 
* Mike has lots of work done on different methods on image processing - hasn't published (yet) but definitely worth talking about more.
* See this [PR on aiapy](https://gitlab.com/LMSAL_HUB/aia_hub/aiapy/-/issues/1) regarding the agreemement between SSW and aiapy

## 30 September 2020

### Agenda

* Project repo (https://github.com/sunpy/sunpy-project/issues)
* sunkit-instruments
* outreachy
* Coordination meeting
* PR Discussion
* Issue discussion
    
### Minutes

* outreachy
    * Project ideas: https://demo.codimd.org/n5vdYiSnSAC33jNXmUtvdQ#
* ndcube
    * Experiment with extra coords on real world data
    * Path towards using NDCube to replace Map?
    * Needs discussion at coorindation meetin

## 23 September 2020

### Agenda

* PR Discussion
    * https://github.com/sunpy/sunpy/pull/4432 - Ignore out-of-range years for an SRS query
    * https://github.com/sunpy/sunpy/pull/4476 - Force metadata to be a MetaDict
* Issue discussion
    * https://github.com/sunpy/sunpy/issues/4478 - OpenCV as an alternate affine transform library
* Transferring `instr` issues from `sunpy` core to `sunkit-instruments`
* `CompositeMap` woes (issue [#2745](https://github.com/sunpy/sunpy/issues/2745) et al.)
* [`aiapy` JOSS paper](https://gitlab.com/LMSAL_HUB/aia_hub/aiapy/-/merge_requests/79)--feedback welcome!
* NDCube 2.0 NDCube strikes back (https://demo.codimd.org/54dm5gPMQmmJux6fV-3AOQ)

    
### Minutes
* PR Discussion
    * https://github.com/sunpy/sunpy/pull/4432 - Ignore out-of-range years for an SRS query
        * Merged, might backport
    * https://github.com/sunpy/sunpy/pull/4476 - Force metadata to be a MetaDict
        * Decided that it's probably not possible to trigger the fallback to basic wcs?
    * https://github.com/sunpy/sunpy/pull/4394 - Functionality to client to download new GOES 16/17 data and reprocessed 13/14/15
        * Discussion of which data to default to (new or old data)
        * Discussion of whether to force the user to specify a version
        * Decided to add provider option to switch between old/new data, and default to new data
 * Issue discussion
    * https://github.com/sunpy/sunpy/issues/4478 - OpenCV as an alternate affine transform library
        * Lots of different affine transform implementations will be out there
        * First bit of work is defining an `AffineTransform` base class that provides an interface for custom transform implementations
* Discussion of affine transform/rotate
    * Result of rotate() depends on whether you have scikit-image installed or not
    * This can result in different results between the two implementations
    * General reluctance to change/add stuff without first understanding the current behaviour
    * Decided that the best way forward is to allow users to had their own functions into affine_transform.
* Transferring `instr` issues from `sunpy` core to `sunkit-instruments`
    * Way forward with this is to
        * Do a first release of sunkit-instruments
        * Deprecate code in sunpy core
        * Transfer issues form core to sunkit-
* `CompositeMap` woes (issue [#2745](https://github.com/sunpy/sunpy/issues/2745) et al.)
    * Need to build `reproject` into `CompositeMap`
    * People often assume that this will be done automatically
* [`aiapy` JOSS paper](https://gitlab.com/LMSAL_HUB/aia_hub/aiapy/-/merge_requests/79)--feedback welcome!
    * Being written right now!

## 9 September 2020

### Agenda

* PR Discussion
    * https://github.com/sunpy/sunpy/pull/4451 - Use bunit in sunpy.map
    * https://github.com/sunpy/sunpy/pull/4455 - Improve title of differential rotation example
* Affiliated package re-reviews https://github.com/sunpy/sunpy.org/issues/242
* Affiliated package for various solar models (Will)
* Performance versus elegance, i.e. how do we deal with the question "why is sunpy so slow???" (Will)
    
### Minutes
* PR Discussion
    * https://github.com/sunpy/sunpy/pull/4451 - Use bunit in sunpy.map
        * Comments added
    * https://github.com/sunpy/sunpy/pull/4455 - Improve title of differential rotation example
        * Merged
* Affiliated package re-review
    * Concerns about how much extra effort this will place on reviewers, editors for affiliated packages
    * We should probably have a re-evaluation PR/issue template for affiliated package maintainers to request a rereview
    * We should explicitly note which version (e.g. via the commit hash or version) which will make it easier to diff the current versus review versions. See [this issue](https://github.com/sunpy/sunpy.org/issues/243)
* Affiliate package for solar models
    * Similar goal to the datasets repo
    * Would bring together "canonical" models in solar physics, e.g. interior temperature, density as a function of radius, VAL/VAL-C atmospheres
    * Will's use cases: analytical loop models like RTV, Martens, Serio, isothermal
    * Others? Scope for now is any kind model that can be reference from literature
    * Ideally, this should all be analytical/empirical and not complex, computationally intensive codes (i.e. should not include field extrapolation codes, MHD, even 1D loop models)
    * Action item: Will to create a gist outlining a possible vision for this package
* How do we deal with "sunpy is slow"?
    * There is often feedback about sunpy being "slow," particular in the context of `sunpy.map.Map`
    * sunpy is very general. While we do not ignore performance considerations, we do not optimize for them.
    * There is a fear that as Python use in solar physics increases, users may drop sunpy or not use it to it's full potential because of actual or perceived performance bottlenecks
    * We want to *encourage* users to report (or provide code contributions!) if they find that performance can be increased at different places or if some part of the package hampers their research workflows.
    * See [this issue on the aiapy repo](https://gitlab.com/LMSAL_HUB/aia_hub/aiapy/-/issues/76) where Stuart exhaustingly benchmarked an aiaprep workflow
    * Opened https://github.com/sunpy/sunpy/issues/4459 for future discussion.

## 2 September 2020

### Agenda

- PR Discussion
    - Ready for review:
        - https://github.com/sunpy/sunpy/pull/4433, Move colormap data to .csv files
        - https://github.com/sunpy/sunpy/pull/4432, Ignore out-of-range years for an SRS query
        - https://github.com/sunpy/sunpy/pull/4418, Add some missing bits to the API docs
- 2.1 Release
- Other Topics
    
### Minutes
- PR Discussion
    - 4433 is ready to go with a rebase if tests pass
    - 4432 should wait for the GenericClient refactor PR
    - 4418 waiting on a doc build to pass
    - 3738 is not generic enough, and will need so much refactoring that it will be worth starting again, so decided to close.
- 2.1 feature freeze is the 23rd October

## 19 August 2020

### Agenda

- GSOC
    - Fido
    - Glue Solar
    - Sunspotter
- PR Discussion
- Other Topics
    - SPD Chat

## 12 August 2020

### Agenda

- GSOC
    - Fido
    - Glue Solar
    - Sunspotter
- PR Discussion
    - [#4405](https://github.com/sunpy/sunpy/pull/4405)
    - [#4391](https://github.com/sunpy/sunpy/pull/4391)
    - [#4378](https://github.com/sunpy/sunpy/pull/4378)
    - [#4394](https://github.com/sunpy/sunpy/pull/4394)
- Other Topics

## 5 August 2020

### Agenda

- GSOC
    - Glue Solar
    - Sunspotter
    - Fido
- PR Discussion
    - [#4405](https://github.com/sunpy/sunpy/pull/4405)
    - [#4391](https://github.com/sunpy/sunpy/pull/4391)
    - [#4378](https://github.com/sunpy/sunpy/pull/4378)
    - [#4394](https://github.com/sunpy/sunpy/pull/4394)
- Other Topics
    
### Minutes

- GSOC
    - Glue Solar
        - Docs build
        - tox issues
        - Dev guide
    - Sunspotter
    - Fido
        - Gallery example combining HELIO, HEK, and JSOC
        - Old IRIS JSOC issue
        - Integration of scraper/dataretriever with redesign of GenericClient [#4321](https://github.com/sunpy/sunpy/pull/4321)
- PR Discussion
    - GOES PR
        - waiting on GenericClient updates
        - we still aren't quite sure how to support the old FITS data for 13-15
        - maybe an extra `attr`?
        - But how best to handle data from multiple servers...
    - JSOC url-tar PR
        - Can this be used with `Fido`?
        - Should this be an `attr` rather than a keyword argument?
        - Discussion about using `JSOCClient` directly rather than through `Fido`
        - What do `request_data` and `get_request` do that `search` and `fetch` don't?

## 22 July 2020

### Agenda

- GSOC
- PR Discussion
    
### Minutes 

- GSOC
    - Fido
        - Ideally we shouldn't have separate `Time` attrs for HEK and non-HEK queries. But then how to discriminate between HEK and non-HEK queries?
        - Documenting the return type of all the HEK columns; is this a worthwhile exercise? 
    - Sunspotter
    - Glue
- GOES XRS Discussion
    - We seem to ...


## 15 July 2020

### Agenda

- GSOC
- PR Discussion
    - https://github.com/sunpy/sunpy/pull/4333
    - https://github.com/sunpy/sunpy/pull/4053
    - https://github.com/sunpy/sunpy/pull/4236
    - https://github.com/sunpy/sunpy/pull/4343
    - https://github.com/sunpy/sunpy/pull/4350
    - https://github.com/sunpy/sunpy/pull/4331
    
### Minutes 

- GSOC
    - Fido
        - Combined metadata and data product searches now working, e.g. HEC and XRS queries
        - Helio queries require table name. If not specified user is prompted for it.
    - Sunspotter
    - Glue
        - WCS autolinking PR
        - Preferred colormap PR
        - 1D Spectrum with WCS PR
- PR Discussion
    - Differential rotation test and HMI synoptic map PRs pretty much ready to be merged
    - Put off ERFA discussion until next week (or the next time that interested parties are present)
    - Nabil's PR for removing all deprecated 1.1 code is pretty much ready to be merged as well.
- We need a 2.0.2 release soon, mostly for the NOAA fix


## 8 July 2020

### Agenda

- GSOC
- PR Discussion

### Minutes 

* Upadates on GSoC projects:
    * Fido
    * Sunspotter (Rahuul is unwell, so he gave an update on the channel)
        1. Further progress on the Search Events Object. We figured out where to get the NOAA number matched with SunSpotter data. There was a problem with the units that was mostly resolved. The SEO as was discussed should be done mostly by the end of the week.
        2. I will be preparing a presentation for DavidPS on the different architectures of Neural Nets. Since we're interested in time series analysis, I'll include RNNs, LSTMs, etc as well.
        3. The basic pipeline is done for the CNN in pytorch, so it'll be plug an play mostly from now on, for experiments.
    * Glue
        * Updates to 1D profile viewer--now working with time slider :tada:

* Change in NOAA sunspot indices files (PR [#4340](https://github.com/sunpy/sunpy/pull/4340))
    * Old text files on FTP server no longer exist
    * Now in JSON format so we support both
    * A lot of changes for a bugfix release--how to best document this?
    * Big changelog? In the docs?
* PRs need reviewing--we are up to 40+
* Stuart will not be present next week; Will or Nabil will run the meeting
* SciPy is this week

## 17 June 2020

### Agenda

- GSOC
- CI changes
    - Figure tests
    - RTD PR builds
- Post 2.0 changes.
- Pull Requests

### Minutes 

* Upadates on GSoC projects:
    * Fido
        * Generalized the way we get URLs from DR Clients from query attrs 
        * Concatenation of query results
        * Question regarding duplicate GOES files--just different formatting or actually different results
    * Sunspotter
    * Glue
        * Completed a working version of the upstreaming of the WCSAxes enabled `glue` 1D Profile Viewer (where PR needs debugging and tidying up)
        * Introduced a new icon for the pixel extraction tool originally in `glue-solar` (to be upstreamed)
        * Added a non-collapsing `slice` function option for the 1D Profile viewer (in additional to the standard statistics operations)


* RTD now builds on pull requests!
    * Do we want to continue to have CircleCI and RTD builds for each PR?
    * Move docs build off of CircleCI?
    * Figure tests should stay on Circle
    * We don't want to build the docs in 3 places on every PR
    * Parallelize the doc build?
    * Running docs build on dev 
    * Proposal
        * Build docs + gallery on RTD
        * "No-gallery" doc build on Azure (no dev dependencies)
* Figure tests
    * Previously, running figure tests under conda
    * Matplotlib wheels include version of freetype
    * No freetype dependency so we can run figure tests in tox!
    * Can easily run figure tests locally now :tada:
* Mysterious macOS conda-forge failures still mysterious. See [PR #4293](https://github.com/sunpy/sunpy/pull/4293)


## 10 June 2020

### Agenda

- GSOC
- What is blocking the 2.0 release?

### Minutes 

* Upadates on GSoC projects: Fido, Sunspotter, Glue
* 2.0 Release
    * Finish the "What's New"
    * Failures on the "devdeps" test point to problem with bleeding edge astropy and behavior of how `astropy.time.Time` behaves under numpy operations; possibly related to [astropy/astropy#10337](https://github.com/astropy/astropy/pull/10337)
* Pull Requests
    * [#4266](https://github.com/sunpy/sunpy/pull/4266)
    * [#4267](https://github.com/sunpy/sunpy/pull/4267)

## 3 June 2020

### Agenda

- GSOC
- 2.0 blockers

### Minutes 

#### GSoC

##### FIDO

- [#4055](https://github.com/sunpy/sunpy/pull/4055) ready for review

##### Sunspotter

- [#4238](https://github.com/sunpy/sunpy/pull/4238) table matcher, in progress with euclidian distance and cosine similarity.
- Requested to have it also as example in the gallery.
- Some people not convinced this should live on core

##### Glue

- click and see a spectrum profile of that pixel

#### 2.0 Blockers

## 13 May 2020

- Discussion of potential Fido clients: https://docs.google.com/document/d/1KYpqebFisjMRYJEoYKBJxqwIMW_jO2gaUsNVBCu_B7Y/edit#heading=h.ybxw3flop3dy
- sunpy 2.0 outstanding PRs: https://github.com/sunpy/sunpy/milestone/41
- 2.0 Release
- How should we deal with the `instr` subpackage in terms of the new `sunkit-instruments` repo?

## 6 May 2020

The collaboratively editable version of the minutes and agenda for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). These will be archived here on the wiki following the meeting.

## 29 April 2020

No community meeting was held due to the Python in Heliophysics Spring Meeting.

## 22 April 2020

### The road to 2.0
We need to review all PRs https://github.com/sunpy/sunpy/milestone/41 to get ready for an RC this week.

### pyastro Hack ideas
See https://docs.google.com/spreadsheets/d/1gsEQ3_xxHw4_gPnkfEna2IPqN9e7Cdom8KM_o6TVaUE/edit#gid=0 for the official list

- Magnetogram sources/clients/examples (led by dstansby)

### Meeting notes

- Meeting streamed onto YouTube for posterity
- 2.0 PRs
    - Rectangle - leave for Albert to review
    - Attr registration - waiting on changes in response to review
    - User config - needs another review, should change funciton name to `copy_default_config`
    - JSOC error - re-milestone to 2.1
    - VSO fetch fix - re-milestone to 2.1
    - Moving constants - restarted failing build, waiting for Albert to review
    - Map singeldispatch - merged
    - What's new - add ideas!
- General chat about differences bewtween old and new differential rotation code

## 15 April 2020

### Agenda

#### PRs
- **Added an HTML summary for Map and MapSequence** -https://github.com/sunpy/sunpy/pull/3951
- **Add contour map method** - https://github.com/sunpy/sunpy/pull/3909
    - Suggestions for meaninful tests?
- **Map now raises the file that failed to load if it errors on reading** - https://github.com/sunpy/sunpy/pull/3727
    - David S. suggests opening a new PR/branch, as devs are now just force pushing to the original contributor's branch...
    - Nabil suggests its ok.


### Minutes


* Merged sunpy.sun.sun Pr
* #3951 needs review
* Discussion on methods on map vs functions in maputils relating to #3909, decided to put `contour()` in `maputils`.

## 8 April 2020

### Agenda

* Follow-up from SunPy Coordination Meeting last week
* Issue triage
* PR review
    *  **add .cmap and .norm property to plot_settings**
        *  https://github.com/sunpy/sunpy/pull/3624 - we said we would make a decision on this at the dev meeting but I don't think we did
    * **Implemented Groundclients in continuation with PR 2619**
        * https://github.com/sunpy/sunpy/pull/3763 - need to check the clients and VSO return same data products, and whether VSO can provide real time data now.
    * **modified search metadata to return Astropy.Table**
        * https://github.com/sunpy/sunpy/pull/3950
    * **Add a other issue template**
        *  https://github.com/sunpy/sunpy/pull/3940
    * **Added an HTML summary for Map and MapSequence**
        *  https://github.com/sunpy/sunpy/pull/3951
    * **Fix deprecated decorator**
        * https://github.com/sunpy/sunpy/pull/3982
* Co-working hour
    * Time(s)? Day(s)?


### Minutes

**Present:** Jack, Albert, Shane, Nabil, Stuart, Will, David S.

* Follow up from coordination meeting
    * How often do we want these to happen?
    * Nabil suggested having more frequent, shorter, and focused meetings, e.g. around 3.0 -- weekly?
    * Should we tie times of meetings to the release schedule? (this happened, somewhat by coincidence, this time around)
    * At the very least, annual coordination meetings
* Issue triage
    * Boring, but needs to be done (mostly a TODO for Will)
    * Be more aggressive about closing issues, they can always be reopened
* `instr` issues need to be moved over to the `sunkit-instruments` repo
* PRs
    * HTML `__repr__` PR [#3951](https://github.com/sunpy/sunpy/pull/3951)
        * *nearly done
        * other features should go into other PRs
        * would be good to generalize to NDCube, but a lot of work
    * Deprecated decorator PR [#3982](https://github.com/sunpy/sunpy/pull/3982)
        * Merge soon
        * Create issue/PR upstream to astropy
        * break version calculation out into its own function
    * `cmap` and `norm` property PR [#3624](https://github.com/sunpy/sunpy/pull/3624)
        * We underestimated how integrated `plot_settings` is in `Map`
        * Replace with a `plot_settings` subclass of `dict` that pulls out the plot-specific parts of the API
        * Deprecate `__getitem__` on this new object and then provide `cmap`, `norm`, etc. as properties on this object
        * Squash existing commits to preserve the contribution, close this PR,  and open a new PR on top of this branch (TODO for Nabil)
* Coworking hours
    * 9:00 UTC and 17:00 UTC
    * Tuesday (but reassess to see if this works for everyone)
