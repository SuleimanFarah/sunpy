Agenda
------

- release of 0.8 should happen by the SPD meeting
- website updates from stuart
- monica update for spd workshop

0.8 release – Stuart
--------------------

- freeze ~next Monday
- outstanding: documentation; guide section needs review
- vso client documentation
- need section on user guide for coordinates inside api docs
- fido is done and running; fairly stable; could use more use for testing
- fido is the new interface for downloading data
- one interface and determines correct client and consistent api
- major feature of 0.8
  - working on deprecating lightcurve to time series (wcs)
  - sunpy coordinates = astropy sky coordinates
  - corners of submap need to be in coordinates framework
  - albert added ability to move from solar coordinates to astro coordinates
  - can put galactic coordinates on sun, if you ever wanted to
  - no uses of wcs left
- biggest blocker for release right now is documentation
- rename net methods
- beta release early next week
- side discussion about aia cutouts through fido, not yet possible because of problem with how it is distributed to requester

website updates – Nabil/Stuart
------------------------------

- a few issues still outstanding
- main content issue – no formal board page / want bios & photos / github, affiliations or links
- need website and documentation consistency
- search is broken but will be fixed
- official launch with 0.8 / August 18th or 21st
- will be live before announcement (~week after next)
- buttons on home page at the bottom of some people screens (fine on all of savage's screens/browsers...shrug)
- SunPy version number not displayed
- need the latest version, how to install, and what to do with it immediately accessible
- steven still does not like sun in background because busy, reverse-scaled annoying

SunPy SPD workshop – Monica
---------------------------

- Wednesday, 6:30-8:30
- SPD business meeting at same time
- People need to have Python already installed since Binder appears dead
- Steven suggested eclipse notebook for Savage to present with a personal
eclipse photo for flair
- Other notebook suggestions: fido/coordinates
- Agenda for workshop:
  - Monica gives a ~15 minute overview of why Python is cool
  - Monica gives a ~5 minute lightning talk showcasing some interesting tools and/or analysis
in a jupyter notebook
  - Sabrina gives a ~5 minute lightning talk showcasing some interesting tools and/or analysis
in a jupyter notebook
  - Dan gives a ~5 minute lightning talk showcasing some interesting tools and/or analysis in a
jupyter notebook
  - Andrew gives a ~5 minute lightning talk showcasing some interesting tools and/or analysis
in a jupyter notebook
  - Andrew gives a ~10 minute lightning talk about Sunpy, governance, and how it differs from
SSWIDL
  - We have an interactive session that lasts ~1:15. During this interactive session, people
(either individually or in pairs) load up one of the four jupyter notebooks presented during the
lightning talks (using either their own machine or Binder) and work through the notebooks --
by understanding and executing the existing code, manipulating the code, and appending to
the code. All of us will be around to help people work through their notebook of choice.

AOB: Jack
---------

- He and Stuart are going to numfocus meeting to coordinate sustainability, may be room for one more.
