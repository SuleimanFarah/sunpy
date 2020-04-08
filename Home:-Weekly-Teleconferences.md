# Weekly Community Meetings

The SunPy weekly community meeting is held every Wednesday at 16:00 UTC. The link to these weekly teleconferences can be found [here](https://sunpy.org/jitsi). The minutes for each meeting are recorded below. The agenda and minutes for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). Community members should feel free to edit the agenda and add items as appropriate. Agenda items not covered at this week's meeting will be bumped to the agenda for the following week. Typically, the lead developer or deputy lead developer will announce the community meeting in the chat a few hours prior to the start of the meeting.

## 15 April 2020

The collaboratively editable version of the minutes and agenda for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). These will be archived here on the wiki following the meeting.

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
