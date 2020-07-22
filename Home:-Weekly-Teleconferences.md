# Weekly Community Meetings

The SunPy weekly community meeting is held every Wednesday at 16:00 UTC. The link to these weekly teleconferences can be found [here](https://sunpy.org/jitsi). The minutes for each meeting are recorded below. The agenda and minutes for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). Community members should feel free to edit the agenda and add items as appropriate. Agenda items not covered at this week's meeting will be bumped to the agenda for the following week. Typically, the lead developer or deputy lead developer will announce the community meeting in the chat a few hours prior to the start of the meeting.
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
