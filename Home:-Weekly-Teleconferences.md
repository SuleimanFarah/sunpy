# Weekly Community Meetings

The SunPy weekly community meeting is held every Wednesday at 16:00 UTC. The link to these weekly teleconferences can be found [here](https://sunpy.org/jitsi). The minutes for each meeting are recorded below. The agenda and minutes for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). Community members should feel free to edit the agenda and add items as appropriate. Agenda items not covered at this week's meeting will be bumped to the agenda for the following week. Typically, the lead developer or deputy lead developer will announce the community meeting in the chat a few hours prior to the start of the meeting.

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
