## 9 November 2022

### Agenda

* Welcome to Newcomers
* Docs sprint scheduled for **18 November** (unless there are strong objections)
* Feedback from 4.1 RC
    * status of testing on all sponsored packages?
    * any feedback from other affiliated packages?
* PR Review

### Notes

* What should we do ahead of the docs sprint?
    * Will: map rotation example separated out using the diátaxis framework
    * Identify what content we have that falls into the certain areas
    * What does our content look like if we split it out
    * What has been done thus far?
* Goals of the sprint:
    * Plan for making incremental progress towards this goal

## 2 November 2022

### Agenda

* Welcome to Newcomers
* DST and meeting time
* Status of 4.1 release
* Docs sprint doodle: https://doodle.com/meeting/participate/id/b2xxQnAe
* SunPy LINCC talk next week: https://www.lsstcorporation.org/lincc/tech-talks
* Reviews on `eispac` PRs
    * Fido client: https://github.com/USNavalResearchLaboratory/eispac/pull/31
    * Map source: https://github.com/USNavalResearchLaboratory/eispac/pull/50
* PR Review

### Notes

- radiospectra discussion
- pydantic???
- `header_helper` discusssion
    - should we provide an additional namespace now that we have multiple helpers
    - proliferation of namespaces but also of things that live under the `.map` namespace
    - decided that since there are likely to be more header helpers, makes sense for them to live under their own namespace

## 26 October 2022

### Agenda

* Welcome to Newcomers
* Database deprecation announcement
    * https://hackmd.io/@5tUXI9ejSAmY27nKY7SvAA/BJW2JKLEi
* Docs Sprint Planning
    * Diátaxis refactor is large
    * We should figure out a day where we are all working on components of this refactor
    * Scope out a plan before hand
    * Preferably before the end of year
    * Possible dates--need a poll here
        * 4 November
        * 16 November
        * 18 November
        * 5 December
        * 8 December
* Governance Updates
* PR Review
    * Priority list for 4.1: https://github.com/sunpy/sunpy/milestone/90


### Notes

- JSOC cutout example failing; disable it for now
    - Should nail down what exactly is failing--download or the actual query service?
    - It looks like its actually the initial VSO query that is failing
- Remove sunpy-dev

#### Database deprecation plan

- Pending deprecation warning
- Nabil posted to mailing list, no responses

#### Docs refactor discussion
- Use sample data for HMI magnetogram upside down example
- Should have a "How-to" for downloading HMI magnetogram data
    - This uses `physobs.los_magnetic_field` which may not be obvious
- Stuart thinks most gallery examples should be how-tos, not tutorials
- We need a larger-scale plan about how to accomplish this
- There still seems to be some confusion about terminology in the diátaxis
  - Need both common agreement and common understanding before moving forward
- We should come up with some sort of minimal example of this applied to our docs
  - e.g. splitting out gallery examples into how-tos and tutorials
  - taking some of the coordinates pages and splitting them into the four quadrants



## 19 October 2022

### Agenda + minutes

* Welcome to Newcomers
* Paper wrap-up
    * Almost done
    * Submit by tomorrow (if at all possible)
* PR Review
    * Feature freeze is Friday (!)
    * What PRs need reviews?
    * Anything that we really want in 4.1 that has not been opened yet?
    * Review deprecations to make sure we've removed everything

### Notes

- Frontiers paper
    - Submit by Friday at lunch time
    - Jack reading over this afternoon
    - Will wrapping up the roadmap/governance and community section
    - Final read throughs today and tomorrow
- Feature freeze is Friday (10/21)
    - PRs that make it into 4.1 should be opened by Friday and reasonably close to complete
- Extended debate about `__author__`/`__email__` tags
    - See https://github.com/sunpy/sunpy/issues/3650

## 12 October 2022

### Agenda + minutes

* Welcome to Newcomers
* Paper progress
    * Lots of content is there
    * Still needs lots of tidying up though
    * Deadline for final draft EOB Friday (14th Oct)
    * Will be submitted a week today (19th Oct)
* Devstats are live: https://devstats.scientific-python.org/_generated/sunpy.html
    * Anything else we would want to see on this dashboard?
    * e.g. plots from our previous papers?
* Sprint Planning
    * Bi-monthly or quarterly
    * Lasting 1 day (starting in Europe, ending on West Coast)
    * Intention is two-fold
        * Get core devs working semi-synchronously for a confined period of time on a regular basis
        * Onboard new contributors (advertise on Twitter, AAS News, etc.)
    * Scope out sprints ahead of time
        * Structured, but not too structured...
    * Temper expectations appropriately
* SunPy Office Hours at GSFC
* DEMs in Python
* PR Review

### Notes

* What is the PyHC story?
    * Steve asks if there has been any progress agreement on standards for units, time, coordinates
    * Thus far, no progress...
    * There is a movement to have connectors between them, but no standards thus far
* xrtpy
    * ask them to join the sunpy channel
    * what can we do to better support them
    * also follow up on involving them in the instrument working group
    * There is also the "Instrument Working Group" channel
    * Reach out to Joy and Nick (maybe ask them if they would want to present at a community meeting?)
* DEMs
    * David will be working on DEMs for two weeks after first of the year
    * Documenting and wrapping current routines
    * Maybe implement MCMC version (time permitting)
    * Setup a call for others to weigh in towards the end of the year
* Packaging in Python
    * poetry
    * Stuart has issue with non-setuptools setups not supporting "-e" option
    * interesting, but too new?
    * We can use modern setuptools stuff and get most of the way there
    * Don't need a `setup.py` file to use setuptools


## 20 September 2022

### Agenda

* Roadmap
* Solo Workshop
* ndcube releases
* PR Review

## 14 September 2022

### Agenda

* Welcome to newcomers
* Standardized Metadata SEP: https://github.com/sunpy/sunpy-SEP/pull/61
* Frontiers paper status
* ASV
    * Status Albert's PR: https://github.com/sunpy/sunpy/pull/6392
    * What does this look like on PRs?
    * What is the role of ASV in our workflow?
    * How do we use ASV to evaluate PRs? visually? quantitatively?
* PR Review
    *  Make sure data examples achieve a single task #6384: https://github.com/sunpy/sunpy/pull/6384
    *  Deprecate timeseries peek() positional arguments #6310: https://github.com/sunpy/sunpy/pull/6310

### Notes

* Metadata SEP Discussion
    * Question of whether this should be done in SunPy
    * This is an ontology defined in Python objects
    * Trade study on existing ontologies and understand which ones are useful before completely inventing a new one
    * We want complext Python objects--do we also want the components blown out as separate attributes to be accessed?
        * e.g. distance from the Sun to observer as its own property
    * Living document that can be updated as we find more metadata that should be part of the standard
        * Common metadata that people want
        * Should it be an SEP?
        * Is it an ontology if it is constantly being added to?
        * What is the criteria for adding to this metadata "standard"?
    * Not all metadata objects have to use all of these
        * but if they do use that, they should use this name
    * Provides a vocabulary with expected return types and also meanings
    * We should leave WCS out of this (a harder problem to solve)
    * Map kind of already does this, we use the Map properties as an informal/implicit metadata standard
    * This is just formalizing that existing vocabulary
    * Can we at least agree on the names?
        * Then maybe take a stab at implementing it in Map and see how it goes
    * What existing solar/heliophysics vocabularies can we pull from?
        * VSO - https://umbra.nascom.nasa.gov/vso/docs/dm_1.8.html
        * EGSO - https://hesperia.gsfc.nasa.gov/ssw/vobs/egso/doc/EGSO.Data.Model.v1.4.pdf
        * SPASE - https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2018SW002038
        * HAPI - https://github.com/hapi-server/data-specification/blob/master/hapi-3.0.0/HAPI-data-access-spec-3.0.0.md
    * More general astrophysics vocabularies
        * UCD - https://ivoa.net/documents/UCD1+/20210616/EN-UCDlist-1.4-20210616.html
        * IVOA - https://wiki.ivoa.net/twiki/bin/view/IVOA/IvoaDataModel 
        
* Kevin is working with three graduate students taking a course on scientific software engineering who are looking for a semester-long software project 
    * Where is the best place to contribute?
    * Concern about amount of work on the side of the maintainers
    * Open PRs early, come talk to us early
    * December deadline for the course
    * Engage with the process from the beginning
    * David just opened a bunch of issues on `sunkit-instruments` that are scoped relatively small--good intro to opening a PR, making a contribution
    * Dan has mentioned that `ndcube` has some less esoteric issues open at the moment as well
    * See the "Good First Issue" tag on multiple repos
    * Also see Newcomer's Guide: https://docs.sunpy.org/en/latest/dev_guide/contents/newcomers.html
    * Potential projects
        * `sunkit-image`
            * limb darkening: https://github.com/sunpy/sunkit-image/issues/68
            * NAFE: https://github.com/sunpy/sunkit-image/issues/6
            * https://github.com/sunpy/sunkit-image/issues/10
            * STARA: https://github.com/sunpy/sunkit-image/issues/37
        * GOES EM/T functions in `sunkit-instruments` (Dan/Laura)
        * Refactor of spectral fitting code in `sunkit-spex` (Dan/Shane)
        * Adding resampling and/or arithmetic operations to NDCube (Dan)
* Paper discussion
    * Continue with use of "affiliated"
    * Aim to have a full draft by end of September; will give us two weeks to iterate, make corrections before submitting ~15 October

## 31 August 2022

### Agenda

* Welcome to newcomers
* Frontiers paper status
    * We've been given an extension until mid October (no more extending!!)
    * TODO: divvy up sections and start writing
    * TODO: make a "science-y" figure
    * TODO: make a figure laying out project structure
* Small development grant application: https://docs.google.com/document/d/1bS6mFd3XJ7cbHvgpPfdVmFLFErLOEYqeeN_ndeLQNY4/edit
* PR Review
    *  Make sure data examples achieve a single task #6384: https://github.com/sunpy/sunpy/pull/6384
    *   Deprecate timeseries peek() positional arguments #6310: https://github.com/sunpy/sunpy/pull/6310
    *   Mask values when reading CDF files #5956: https://github.com/sunpy/sunpy/pull/5956

### Notes

- Discussion about https://github.com/sunpy/ndcube/pull/541
    - Suffers from issues with dask bringing arrays into memory
- Frontiers paper
    - Deadline is mid-October
    - Discussed plan of action for dividing up work
    - Divided up work
- Discussion on affiliated/sponsored nomenclature
    - present: Will, David, Nabil, Alasdair (Jack, Laura and Danny present for some but dropped off before the discussion concluded)
    - use of the terms "affiliated" and "sponsored" is (potentially) confusing
    - everything is an "affiliated" package
    - those that are maintained by the project are sponsored packages, i.e. the project is responsible for their maintenance and direction
    - affiliated packages are maintained by the community (not necessarily the project) and must meet criteria for being an affiliated package as established by our affiliated package criteria: https://sunpy.org/project/affiliated
    - It was proposed that we make the following changes to the nomenclature around our package structure:
        - Do away with the terms "sponsored" and "affiliated"
        - Define "The SunPy Ecosystem" to include all packages which we previously considered "affiliated"
        - The requirements to be part of the Ecosystem would be the same as those laid out by the current affiliated package requirements
        - On our website, we would then list each package in the Ecosystem and list who maintains it.
        - Those packages previously referred to as "sponsored" would just be listed as maintained by "The SunPy Project" (e.g. sunpy, ndcube) 
        - All others would list the appropriate person/organization as their maintainer (e.g. David Stansby for pfsspy)
        - The core package (sunpy) is part of the ecosystem
        - If we want to make this change, it would require a new SEP or changes to the existing affiliated package SEP
    - Regarding Figure 1 for the Frontiers paper
        - it was suggested that we have an umbrella labeled "The SunPy Ecosystem" and then have all packages underneath, including the core package
        - these could be grouped by functionality but perhaps not explicitly so
        - All packages live under the umbrella
        - We seemed to decide that we don't want to indicate any sort of hierarchy in this figure
        - Nabil suggested we should start thinking about logos for the other packages in the ecosystem
    - It was suggested that we may want to have a separate logo for the package and the ecosystem
        - Keep the current logo for the package, come up with alternate logo for ecosystem?

## 17 August 2022

### Agenda

* After action report from TESS
* Coordination meeting logistics
    * Coffee??? We at least need a plan for where it will be picked up from
    * Remote participation setup--what needs to be done on the ground before we get there?
    * Identify a presenter for each session
        * Master running notes doc: https://demo.hedgedoc.org/fqLNg0xpStac_M9v92v99Q?edit
        * Everyone can contribute notes here
        * Post this on the meeting webpage
    * Another Twitter announcement--when?
    * Others?
* PR Review

### Notes


## 3 August 2022

### Agenda

* AGU Abstract (due today!!)
    * https://demo.hedgedoc.org/I2tJv-heQia0n2nlqgOJpA#
* TESS Session Planning
    * Another Tweet on Monday (i.e. the first day of the meeting)
* Coordination meeting logistics
    * Coffee
    * Remote participation setup--what needs to be done on the ground before we get there?
    * Instrument working group
    * Finalize agenda by 15 August
    * Identify a discussion lead for each session by 15 August
    * Another Twitter announcement--when?
    * Others?
* Contributor/Reviewer Checklist
    * Build contributor checklist from this: https://github.com/sunpy/sunpy/pull/6346
    * Reviewer checklist as well? Maybe auto-generated once the PR is moved from "draft" to "ready for review"?
* Backport bot
* Infrastructure priorities

### Notes

* Coordination meeting
    * Stuart to follow up with Shane re: setup for streaming
    * Coffee can be expensed to OpenCollective, but we need to figure out where to buy it...
    * Agenda still needs some shuffling around

## 27 July 2022

### Agenda

* Recent bugfix release (3.1.8)
    * Thanks Nabil and David!
    * User feedback pointed this bug out to us and it was fixed in ~hours, released in days
    * A success story!
* TESS Session Planning
    * Tweet (Laura/Stuart)
    * Solar News/UKSP (Will)
    * Discussion questions for second half of session
* Coordination meeting logistics
    * Coffee
    * Remote participation setup
    * Instrument working group
    * Others?
* PR Review

### Notes

* TESS Session Planning
    * Will: Put together slides for guiding discussion
    * Discussion questions for second half of session
        * What has been your experience using SunPy? The good? The bad?
        * What is missing from SunPy that you would like to see?
        * What would you like to be able to do with SunPy that you can't currently do?
        * What do you think about SunPy’s online documentation and examples?
        * If you’re using Python packages in place of SunPy for your solar physics data analysis, why is that?
        * Do you know how to contact SunPy if you have a question?
        * Do you know what PyHC is?
        * Do you use SunPy with other parts of the PyHC ecosystem?
* Coordination Meeting planning
    * Need to add an item for roadmap discussion
    * Who to invite for scalable computing discussion
        * Raphael Attie
        * Brian Thomas (and ask anyone from APL...Sandy Antunes, John Vandegriff)
        * Mark Cheung / Paul Wright

## 20 July 2022

### Agenda

* Frontiers paper deadline is now 31 August
* Coordination meeting logistics
    * Coffee
    * Remote participation setup
    * Others?
* TESS Session Planning
    * 6-7:30 PM on 10 August (Wednesday)
    * Rough outline of program
    * Advertise session (Twitter, mailing lists, etc.)
* Notes from SciPy?
* PR Review

### Notes

* Frontiers paper delayed
* Error messages re: failed downloads
    * What's the best way to propagate information to the user about failed downloads/unavailable servers?
    * Need to close loop between users and upstream data providers
    * Better error messages spit out by Fido?

## 6 July 2022

### Agenda

* TESS Session--finalized for Wednesday evening (8/10)
* SunPy Tutorial at SPHERE Workshop
* Finalize Coordination Meeting Schedule
    * We should post a first draft of this on the webpage by the end of the week
    * https://demo.hedgedoc.org/C9AvEImbTyav1NIy36PuZg?edit
* Thoughts on correspondence with instrument teams
    * https://demo.hedgedoc.org/aaeE1nMxQ-yhRCcvuEvbAw?view
* PR Review
    * [#6323](https://github.com/sunpy/sunpy/pull/6323) has generated a lot of dicsussion
    * [#6262](https://github.com/sunpy/sunpy/pull/6262)

## 29 June 2022

### Agenda

* Frontiers Paper Progress
* Coordination Meeting agenda
* PR Review

### Notes

* Frontiers paper progress
    * Will will add text from proposal
    * Will and Nabil to reorganize that text
    * Need to think about a coherent way to present affiliated package organization and justify/flesh out our philosophy
* Coordination meeting agenda
    * See the agenda doc [here](https://demo.hedgedoc.org/C9AvEImbTyav1NIy36PuZg?edit)
    * Instrument Team Day notes:
        * Instrument presentations (state of analysis tools, show us what you're doing)
            * HERMES (Steven Christe) -- instrument package template
        * Feedback forum
            * First, focus on functionality
            * Then, foucus on standards
            * It is on us to demonstrate why an instrument package would want to foster interoperability
                * We should demonstrate why playing in the ecosystem benefits an instrument team
                * "Why would you want to use sunpy"
                * This is mostly focused on user-tools, but what about processing pipelines as well?
                    * HERMES, PUNCH, MUSE conversation
            * We want to build an ecosystem
            * How close to the ecosystem do you want to be?
                * being in the ecosystem doesn't necessarily mean being an affiliated package
            * Where are the gaps
            * What could sunpy be doing better?
            * Are our affiliated package requirements too onerous?
            * Feedback on the affiliated package requirements/process?

## 15 June 2022

### Agenda

* TESS Meeting session
    * Aiming for a ~2 hr session Monday evening
    * will cost $650 but should be able to pay with SPD money
    * unknown if remote participation will be possible (it is not a hybrid meeting...)
    * Thoughts?
        > Title: SunPy Showcase and Community Forum
        > Description: We invite members of the solar physics community to showcase the interesting ways that they've used SunPy in their research and to contribute feedback to guide the direction of the package and the future of the SunPy ecosystem. The first half of this session will feature a lightning talk round in which users are invited to present a single slide for 3 minutes showcasing how they've made use of SunPy in their research. In the second half of this session, we will hold a community forum to discuss how the solar physics community at large is making use of the SunPy ecosystem, with the discussion informed by the preceding presentations on uses of SunPy. Several core SunPy maintainers will be present to give a brief introduction to the ecosystem and guide discussion. In particular, we would like to know where researchers are making use of SunPy, where they are not using SunPy, and where they feel the strengths and weaknesses of the ecosystem are. We invite all members of the solar physics community to contribute feedback on the current state of the SunPy ecosystem, whether they are actively using Python and SunPy or not. Additionally, we encourage participation and contributions from both senior and early-career members of the community.
* Coordination meeting planning
    * Check in with Shane re: LOC things
    * What do we need to do "on the ground" prior to the meeting?
    * [Agenda](https://demo.hedgedoc.org/C9AvEImbTyav1NIy36PuZg?edit): ideally we would firm this up by **1 July**
    * Accomodation? 
* Oh god `draw_` methods make it stop: https://github.com/sunpy/sunpy/pull/6251#pullrequestreview-1006105303
* PR Review

### Notes

* coordination meeting
    * user feedback session from those at DIAS/Trinity
    * coffee catered, lunch we will go out (adhere to schedule for sake of remote participants)
    * Shane will chase down guest Wi-Fi codes
    * IT needs--Stuart will handle machine for streaming to Jitsi, Shane to contact IT about audio in the room
    * need to set agenda soon-ish--Will and Stuart to draft agenda, people can add to it as they see fit; main motivation is that participants coming in for only a session or two know when they need to drop in
* Draw methods
    * proliferation of GenericMap API--too much code in mapbase (Stuart)
    * Can we just move all `draw_*` methods to visualization?

## 8 June 2022

### Agenda

* PyHC Summer School Debrief (Will and Stuart)
* [SunPy Frontiers paper](https://www.frontiersin.org/research-topics/33555/snakes-on-a-spaceship-an-overview-of-python-in-space-physics)
    * Due **29 July**--we should begin a draft now
    * Will submitted the abstract with Stuart, Nabil, and Laura as coauthors (Authorship on the paper itself can be changed at time of submission)
    * This is a high-level overview of the package and affiliated packages (little to no implementation detail)
    * This is going to be [expensive](https://www.frontiersin.org/about/publishing-fees)--is it worth it?
* Presence at TESS
    * Response from SPD: we can have a shorter afternoon session or a longer evening session
    * Latter may compete with other evening events
    * Need to decide ASAP
* SunPy nuggets
    * Put call out for people who have done interesting things with SunPy
    * Publish a (short!) blog post summarizing what they've done as notebooks
    * Stuart suggests having a few in the pipe before we start putting them up
    * Could give them on a DOI via Zenodo such that they're citable (people can get credit!)
* Coordination meeting planning
    * Check in with Shane re: LOC things
    * [Agenda](https://demo.hedgedoc.org/C9AvEImbTyav1NIy36PuZg?edit): ideally we would firm this up by **1 July**
* PR Review

### Notes

* SunPy Frontiers paper
    * Can use ROSES money
    * there is confusion about core versus affiliated package--good to have something to point people towards
    * can use the text from the ROSES proposal as a starting point
    * Laura will create Overleaf template--move to GH later
    * Should think about using showyourwork: https://show-your.work/en/latest/
* SO/PyHC wrap up
    * Lots of interest in contributing to SunPy from those at SO Workshop
    * support for SO in-situ data is an area we need to improve in--lots of demand!
    * Established relationship with SOAR--hopefully close loop when users report problems to us
    * Laura said some people at SO Workshop still using HelioPy for in-situ data--should identify what functionality in HelioPy has not been covered by other packages
* TESS
    * Albert suggested asking participants for 1 slide showing a cool things (i.e. research) they've done with SunPy
    * Maybe use this as a jumping off point for a community forum about what functionality users want to see in SunPy
    * We want to keep this relatively high-level--should not turn into a tech support session (but gladly will do that other times throughout the week!)
    * Suggestion was that Monday evening would probably be best--people still energized and then gives them rest of week to think about any other problems they want to discuss
    * Could even hold "SunPy office hours" during coffee breaks (very informally)


## 25 May 2022

### Agenda

* ASV Demo for Albert?
    * "Getting Started with ASV"
* Presence at TESS
* Draft of abstract for Frontiers article
* Should we support integer data?
    * See Will's issue about rotate and `missing=NaN`
* Meta (Steve)
* PR Review

### Notes

* Presence at TESS
    * Email organizers and ask for room (Dale Gary is a good first contact)
    * Charge? Use SPD money for things like this..
    * Hybrid meeting? Should we figure out how to broadcast this regardless?
    * Is this a good idea?
        * SC: still continegent of people that know nothing about SunPy
        * The distribution of advanced/beginners is bimodal
        * Formal/informal discussion: discussion of what you like/dislike about SunPy, anatomy of a PR
    * Live poll for questions
        * Some way to capture the feedback we get from the community
* Frontiers abstract (https://www.frontiersin.org/research-topics/33555/snakes-on-a-spaceship-an-overview-of-python-in-space-physics)
    * Outline the difference between the package and project
    * Say what is in core, what are the primary capabilities (coordinates, data download, data structures)
    * Summarize the current affiliated package landscape (new ones! aiapy, pfsspy) as well as possilby new affiliated packages? (e.g. sunxspex, fiasco, ....)
        * Probably worth summarizing our affiliated package review process as this is new post our 1.0 paper...
    * what is our vision for the future (e.g. standardizing on NDCube)
    * Better support for reprojection
    * Up and coming high level features: rebasing on NDCube, metadata model, scalable performance with Dask

## 18 May 2022

### Agenda

* Adopting sunpy-soar: Maintenence promises and precidents.
    * Will got a response back from the help desk re: SOAR query errors--open up line of communication this way? or better for those closer to SolO (i.e. Laura/Shane) to make this contact
* Presence at TESS
    * SunPy after-hours tutorial per usual?
    * Do we have money/space to do this? Would SPD/AAS allow it?
        * Who do we contact about this?
        * Too late in the game?
    * "New contributor" mini workshop?
        * Anatomy of a sunpy contribution
        * Do a live PR submission and review cycle
        * Rather than demoing how to use sunpy, how to contribute to sunpy
        * Emphasis on contributions that are not just code too!
        * Can we resonably do this in a few hours?
* PR Review

### Notes

* Nabil: move all external clients besides JSOC and VSO to an external package?
    * Enables us to make changes to these clients not on a usual sunpy release cycle
    * No new clients in core?
* Will and Stuart to meet in person with SOAR team at ESAC in late May
* Will needs to follow up with TESS organizers re: getting space for workshop
    * Seems to be universally agreed upon that this is a good idea

## 11 May 2022

### Agenda

* PR Review

### Notes

* Please register for coordination meeting if you've not already
    * If we don't have a true critical mass of in-person people, is it worth considering going virtual-only?
* Frontiers Snakes on a Spaceship submission
    * consensus is that we should submit something
    * abstract deadline impending and submission deadline as well (29 July)
    * Laura will contact Sophie re: scope of the papers
    * Think about what we want to emphasize: what science does sunpy enable?
* Also start thinking about another ApJ paper for v5.0...
* Docs gallery refactor using things from Jupyterbook; see https://github.com/orgs/sunpy/projects/1

## 4 May 2022

### Agenda

* Sign up for the coordination meeting! https://sunpy.org/project/meetings
* Upcoming release of v4.0
    * Need for RC2?
    * More milestones?
    * Anything that *really* needs to make it in?
* PR Review

### Notes

* Coordination meeting
    * Things to add to the website:
        * hotels
        * google map
        * travel funding information
    * Shane will look into costs for coffee/snacks
        * Maybe can use numfocus money
        * May need to collect small amount of cash from everyone
    * Who do we want to invite from instrument teams?
        * SolO--particularly in-situ stuff (EPD, RPW)
        * PSP
        * PUNCH
        * EUVST
        * Radio people--LOFAR, EOVSA, solar with ALMA
        * would be nice to get as many in person as possible!
    * Agenda
        * have a relatively
    * Breakdown of full session versus break out sessions?
        * Main lecture hall
        * 3 side rooms
        * Maybe 1 office
        * This will depend on number of participants and who comes

## 27 April 2022

### Agenda

* SciPy BoF Session ideas? <https://www.scipy2022.scipy.org/bof-sessions>
* Coordination Meeting Announcement (<https://demo.hedgedoc.org/C9AvEImbTyav1NIy36PuZg?edit>)
  * Duration: 4 days? 5 days?
  * Hard cap on in-person attendance? I've put 40.
  * Mailing lists: sunpy, sunpy-dev, UKSP, Solar News, Helionauts, OA Discourse
* GSOC
* PR Review

### Notes

## 20 April 2022

### Agenda

* Discussion of what "draft" means
  * See [#6085](https://github.com/sunpy/sunpy/pull/6085)
  * Should the context of what "draft" is be in the PR template?
  * Need a consensus about what we mean by "draft"
  * Does GH have a way to adjust permissions on who can mark as draft?
* SSL Certificate Verification Failure on things that access NOAA data?
  * <https://github.com/sunpy/sunpy/runs/6083862087?check_suite_focus=true#step:8:23179>
  * The NGDC NOAA domain is currently undergoing maintaince until the 21st <https://www.ngdc.noaa.gov/index.html>, this is probably the issue
* PR Review

### Notes

* Skip the NOAA tests? Or don't check the SSL cert?
  * Tell someone they need to fix their certificates
* Will and Nabil giving short PyHC presentation on affiliated package ecosystem
* Draft status discussion
  * shouldn't mark as draft without explanation
  * Will: should "mark as draft" be used as a review tool?
  * Stuart: particularly in context of new contributors, should encourage them to mark as draft if we think the PR is not ready for review (e.g. needs significant work before doing review)

## 30 March 2022

### Agenda

* Firming up coordination meeting plans
* Timeseries refactor PR: [#5834](https://github.com/sunpy/sunpy/pull/5834 )
* PR Review

### Notes

* We need to book a room/firm up dates for the meeting
  * Will will get in touch with Shane to book room at DIAS for 22 August barring any major objections in the next few days.
* Significant discussion on Albert's new affine transform PR
* Agreement that default for missing in rotate should be NaN
* Timeseries PR review still needs to be addressed--Stuart and Will will provide reviews

## 23 March 2022

### Agenda

* Coordination meeting--quick planning meeting on Friday?
* WE WILL BE ADDING MAXWELLS AND STUART CAN NOT STOP ME
* Status of ASV?
* Deprecations
  * `sunpy.io.fits` -- going private
  * `sunpy.image.coalignment` -> `sunkit_image.coalignment`
  * `sunpy.physics.solar_rotation` -> `sunkit_image.coalignment` (in progress) -- we need to refactor coalignment capabilities in `sunkit_image`
  * `GenericMap.shift` -> `.shift_reference_coord` (in progress)
* What features to try and get into 4.0?
  * Feature freeze is in ~1 month
  * Current list at <https://docs.sunpy.org/en/latest/whatsnew/4.0.html>
* PR Review

### Notes

* Ideally would like to lock down a date by Monday
  * Quick planning meeting Friday?
  * Will will put a message in the chat
* ASV is up and running
  * <https://github.com/sunpy/sunpy-benchmarks>
  * Only a minimal set of benchmarks exist currently
  * We should be strategic about what benchmarks we add and when
  * Adding new benchmarks and running them over the history of the project takes a long time (~6 hours)
  * For PRs, comparison is just between the PR and main
  * Weird regression in `parse_time`?
* Milestoning more things for 4.0
* Good progress on changelog bot

## 16 March 2022

### Agenda

* Fill out the coordination meeting planning survey if you have not already (<https://forms.gle/dtaYfaw2csDqUoaW6>)
* SunPy Tutorial at PyHC Summer School
* GitHub Actions
* `physics.solar_rotation` (<https://github.com/sunpy/sunpy/issues/5965>)
* IRIS SJI Maps (<https://github.com/sunpy/sunpy/issues/5962>)
* PR Review

### Notes

* Should there be a models subpackage in core? (Dan)
  * Models would have to be physics-based and solar-specific, e.g. thermal X-ray bremsstrahlung using solar abundances.
  * Models would be widely used/integral to at least a sub-field of solar physics.
  * Models are stable over years, i.e. are rarely going to change.
  * Subpackage would not contain complex tools like fitting infrastructures.
  * What models should go in?  What should the bar for inclusion be?
  * Should this even be in core?
  * This seems like a topic for the coordination meeting...
* (Jack) I have to leave, but one issue for the coordination meeting an issue I would like discussed is the use of SunPy in cloud environments. Are there changes to SunPy that could enable it to use a cloud environment more efficiently? We should have more experience to report on this topic at the end of the summer.
  * (Will) It depends on what you mean by "enable it to use a cloud environment more efficiently", but I think this is somewhat covered by our OSTFL proposal--one of our proposed improvements is improving support for large datasets, e.g. making Map operations Dask-friendly.
* GH Actions migration is going well/mostly working
* Mapsequence derotate
  * Agreed it at least needs to be renamed
  * Deprecate and put into `sunkit-image`?
* IRIS SJIMap needs to be fixed, but also will be deprecated soon (in favor of irispy)

## 9 March 2022

### Agenda

* Coordination meeting planning survey: <https://forms.gle/pj74HicDgjBAWcj36>
* PR Review

### Notes

* Please fill out coordination survey
* PyHC have asked about presentations for some affiliated packages
  * More general presentation on affiliated package ecosystem?
* PR "cheat sheet" (see <https://github.com/sunpy/sunpy/issues/5944>)
  * should this go in the template?
  * is the current template useful? reevaluate?

## 2 March 2022

### Agenda

* 2022 Coordination Meeting
  * Hybrid format
  * Proposed locations: Washington, D.C. (American University) or Dublin (DIAS)
  * Proposed dates: mid to late summer--will depend on location
  * Duration? 4 days? 5 days?
  * Will needs to put together a larger poll to get a sense of best date/location combination
* Policy for supporting multiple versions of test deps (<https://github.com/sunpy/sunpy/pull/5926>)
* `conda-forge` errors: <https://github.com/conda-forge/sunpy-feedstock/pull/114>
* CI Status?
* Kicking off instrumentation working group again
  * <https://github.com/orgs/sunpy/projects/1/views/1>
  * <https://demo.hedgedoc.org/aaeE1nMxQ-yhRCcvuEvbAw?view>
* PR Review

### Notes

* `conda-forge` errors
  * asdf problems
  * Stuart cannot look at them at the moment
  * Skip the tests?
  * Something wrong with `asdf` on conda?
  * Trying pinning to 2.9.2?
  * `asdf` on `conda-forge` is broken
* Test deps
  * We now support versions of test dependencies released in the last 12 months
* CI
  * Work is happening upstream in openastronomy repositories to replicate Azure functionality in Github Actions
  * Conor suggested adding Apple Silicon M1 builds
  * Note that these would be untested because we don't have CI there
* Coordination meeting
  * DIAS is looking like a more attractive option
  * Poll needed, but summer is ideal
  * Is there a meeting we should be looking to coincide with? (maybe the SO workshop...)
  * As far as American meetings go, there is SPD/TESS in Seattle

## 23 February 2022

### Agenda

* TimeSeries summary
* Continued saga of Azure builds
* `conda-forge` feedstock for affiliated/sponsored packages
* GSOC?
* Comments restructuring of examples: <https://github.com/sunpy/sunpy-project/issues/11#issuecomment-1043342482>
* Kicking off instrumentation working group again
  * <https://github.com/orgs/sunpy/projects/1/views/1>
  * <https://demo.hedgedoc.org/aaeE1nMxQ-yhRCcvuEvbAw?view>
* PR Review

### Notes

* Timeseries quicklook
  * Matt gave us a demo of the new quicklook functionality being developed for timeseries
  * Plotly and non-plotly versions--very neat!
  * There is significant resistance to adding plotly as even an optional dependency
  * Healthy debate on purpose of plot versus quicklook methods
  * It would be cool to support plotly (other plotting backends), but we are largely bound to matplotlib because of WCSAxes
  * David points out that matplotlib does do interactive plotting in the notebook
  * Stuart: people can pull their data into any kind of visualization framework
  * `bokeh` is another option too (David: the docs are really great!)
  * Laura: used both `bokeh` and `plotly`, found the former to be more user-friendly.
  * **Potential Topic for coordination meeting: how much work do we do to support other kinds of plotting?**
* Azure
  * Stuart has call with them soon
  * Is it time to just move on? to GH actions
  * David: basic testing and doc are working in the `sunpy/sunpy` repo
  * Stuart: need to recreate the OA template repo
  * David: Will open issue to collect TODOs for the template: <https://github.com/sunpy/sunpy/issues/5913>
* Feedstocks
  * `sunkit-image`
* GSoC
  * All of our projects are listed (Will/Stuart still need to scope out DB project a bit more)
  * Not as much OA participation as in previous years
* Examples
  * Laura/Shane did straw poll of students and many said searching for examples was an issue
  * Even core contributors have issues finding which examples show what
  * docs.sunpy.org could become docs for the ecosystem, not just for the core library.
  * Stuart: have to be careful about breaking URLs
  * We should be motivated by a plan to restructure our docs/guide, not just a particular technology choice

## 10 February 2021

### Agenda

* Release blockers for 2.1
* GSoC Projects
* Anything else?

## 06 January 2021

### Agenda

* NDCube 2.0
* QueryResponses
* 2.1 Schedule

### Notes

#### NDCube 2.0

Issues to be tackled, but not much time between Stuart and Danny at the moment. All contributions welcome.

## 16th December 2020

This is the last community meeting of 2020

### Agenda

* NDCube 2.0 API and how it relates to sunpy Map

### Notes

Dan Ryan presented a notebook showing a comparison between `Map` and `NDCube` 2.0: <https://github.com/DanRyanIrish/notebooks/blob/master/ndcube_as_map/ndcube20_as_map.ipynb>

* Side-by-side comparison of Map and NDCube in their current states
* NDCube strictly follows NumPy array ordering in pixel space (row, column)
* Can you create a `WCSAxes` instance ahead of time and then pass it into `NDCube.plot()`?
  * Will will try this and follow up
  * This is easy in `Map.plot`, should be easy in `NDCube`
* `submap` -> `crop` -- generalized N-dimensional cropping
  * Spatial bounds are now `SkyCoord`
  * Shouldn't have to specify bounds in dimensions that you don't want to slice
* NDCube does not assume alignment between pixel and world space
  * In HPC, can never have true independence between lon/lat because of projection of 3D image onto 2D screen
* Can animate any arbitrary number of axes
* Global coordinates
* How do we go about reimplementing `Map` on top of `NDCube`?
  * First pass: just try to reimplement `Map` exactly
  * This will reveal rough edges, pain points
  * Opportunity to rethink API for 3.x?

## 3rd December 2020

* Stuart: Maybe we should advertise our weekly community meetings better (Some outreach work in order?)

* PUNCH (Guests: Matt West and Dan Seaton)
  * To be open-sourced and based in Python
  * To be afiliated with SunPy (in the works)
  * Have a frozen version to be remained untouched (kind of like SunPy's LTS?)
  * GitHub to host the new addition from PUNCH to SunPy
  * PyPi for release with `pip` (Maybe conda as well?)
  * Laura suggested talk about package template for affiliated package applications (i.e., packaging for "structure" stuff)
  * Matt expressed concerns about accuracy or relevance of latest version of official SunPy docs
  * Matt: Actual transform code
  * Stuart: Elements.io as the de facto SunPy IRC channel, bridged with Slack via Matrix
  * Matt: Concern about conversing about code dev over video telecons / call
  * Matt: Have specific questions to ask
  * PUNCH `transforms` package
    * Ingest data products as FITS files
    * For specific transformation between different coordinate systems
    * Using an azimuth for coordinate transformations
    * Optical astronomy/ system - distortions in the imaging (due to various factors such as atmospheric aberrations?)
    * Polynomial distortion algo needs to be worked into (interfaced with) SunPy's `map` module
    * Can use Astropy `wcs.WCS` to handle the projection
    * (Thanks so Solar-Probe)
    * SunPy map objects - represents meta tranlator / standardizer (for the converstion between coordinate systems)
    * Aiming for APE 14 compliance
    * I/O issues as observed by Matt (exporting/importing after transformation), cannot be regenerated with SunPy currently without a patch
    * Stuart: A valid FITS header conforming to APE 14 standard should allow such I/O issues to be resolved
    * Matt: Issues with WCS (only recommondations for nonlinear projections), will need to adopt a non-linear approach upstream by Astropy (Action item: PR's to follow?)
    * Recommendations: "Perfect" FITS (with proper header specs) format for input data products should work with existing Astropy/SunPy ecosystem
    * Matt: Feel there is a need for a community docs for best practices for FITS handling for solar physics? (Answer: A recent publication as suggested by Stuart)
    * PUNCH is currently working feverishly to develop code products for software infrastructure
    * FITS header in solar physics observed to be in dire need of standardizaiton
    * Matt's bigger question: Having SunPy involved in PUNCH would be mutually beneficial
    * Application as a transform package (suggested IRC channels? workflow for integration between PUNCH and SunPy)
    * Dan R.: Incorporation of use of NDCube in PUNCH work?
    * Dan R.: Respect PUNCH is mission-based
    * PUNCH: Open to relying on SunPy chatroom for the time-being, with specific questions to be redirected to PUNCH specific channel later (as suggested by Dan R.)
    * Stuart: Affiliated package application is currently being updated to remain relevant, all are welcome to open an issue there
    * Matt: What happens to deprecated affiliated packages (Stuart: As long as it works we would keep it, despite it being outdated, unless there is serious issues with the exising package)
    * Matt: Concerned for time to process the application (Laura clarified), worried might get stuck
    * Stuart: SunPy is very open to feedback from PUNCH
    * Matt: See SunPy as a potential "wrapper"
    * Stuart: Expected something that are missing from the transforms package originally written in Perl by Dan S.
    * Matt: Package architecture developed about 10 years ago, so may need reworking
    * Matt: Some mem tests have been conducted on the existing codebase as benchmarking
    * Matt: Jacobian in there probably will not be rewritten as it is written (def: a matrix for storing 2nd order derivatives for the tranformation?)
    * Craig may be attending future SunPy meetings
    * Specific Python questions... (to be continued)
      * Superclass with a whole bunch of methods
      * Subclass to reverse the name of two of the method the superclass for some inverse transform but would like to call forward transform (a layered superclass)
      * Super-superclass
      * Stuart: We will need to see the code
      * Albert: Should be doable, but... (with caveats)
      * Not private functions, but protected ones to be manipulated
  * Will: We would like to see more interaction with instrument teams
  * Laura: PUNCH contact emails are kind of hidden, but found

* NDCube 2.0 (post Beta)
  * Dan needs feedback
  * Could be useful if more feedback can be gotten regarding the API
  * Previously received feedback is too technical and not general enough
  * Dan would really want new user to try it out and give honest feedback regarding functionality
  * Before next week would be great (hoping possbily before Christmas)
  * A focused discussion during next week's / next next week's community meeting would be great
  * Ideally NDCube 2.0 should come out before SunPy 2.1, at least that's the expectations

* 2.1 PR's, etc.
  * Metadata is holding up branching, needs another review
    * CI is largely passing
  * Stuart will give it a review one more time
  * Doc PR needs week before feature freeze
  * Will need to update "What's New" as well
  * 2 PR's open for a bug open on the googlemail mailing
    * Can backport the fix for only one of the two
    * The CTYPE's been missing
    * Should default to a particular projection instead of leaving it "open"
  * Pixel-to-world bug needs attention
    * World-to-pixel returns an array of floats, wouldn't be able to used in submaps directly, will need to be multiplied by pixels first...
    * Basically boils down to: What do submaps do (by design as well as construction)?
    * Stuart: WCS attributes coming from an NDCube perspective is fundamental
    * Stuart: Why are we special-casing particular attributes
  * Not to milestone the self tests (according to Nabil, someone says...)
  * Will: Too hasty in approving a PR before some real CI/CD check failures
  * Stuart: We do have the option of adding some "checks and balances" to the existing CI/CD mechanism as a secondary safeguard (for foolproof of genuine test failures)
  * Stuart working on Azure configs for CI/CD checks (in "Stages")
  * Stuart: API breaking stuff should be one thing we should be avoid doing
  * (Maybe a warning to the console should be in order?)
  * Dan: Depracation could be a solution
  * Stuart: pending depracation warnings to the console (so as not to yell at people at their face figuratively)
  * Laura: many people complains about SunPy morphing / evoling too fast
  * Stuart: warning fatigue observed
  * Albert: Should encourage adoption and usage of WCS for it to gain traction
  * Stuart: wary of making significant changes to the `map` API
  * Dan: Would like to understand the metadata problem mentioned more (Stuart: why the `map` approach for the metadata transformation)
  * Stuart: Metadata issue much like the polynomial distortion correction / fitting algo raised by PUNCH
  * Dan: generic data object to a map object (for which Stuart agrees)

* NASA ROSES grant application (1st call)
  * Albert is in the process of writing the proposal for SunPy to be due in mid-January 2021

* Outreachy
  * Skipped for this week as agreed with mentors

## 18 November

### Agenda

* 2.1
* 2.1 pull Requests (<https://github.com/sunpy/sunpy/pulls?q=is%3Aopen+is%3Apr+milestone%3A2.1>)
* Core dependencies <https://github.com/sunpy/sunpy/issues/4655>

### Notes

## 4 November

### Agenda

* 2.1
* 2.1 pull Requests (<https://github.com/sunpy/sunpy/pulls?q=is%3Aopen+is%3Apr+milestone%3A2.1>)
* Test behaviour discussion
  * Should the tests fail if all the deps aren't installed? (<https://github.com/sunpy/sunpy/issues/3701>)
  * Should the tests fail if servers are offline?
  * Should the tests fail if pytest plugins are not installed? (<https://github.com/sunpy/sunpy/issues/4612>)

### Notes

## 28 October 2020

### Agenda

* 2.1 release triage
* PR Discussion
* Issue discussion

### Minutes

## ROSES Call Notes

* Emphasize that these duties are not constrained to the core code base
* This role is largely focused on the project as a whole--make sure to emphasize this in the proposal

### A List of things to do right now

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
  * Remove self_test() references from docs <https://github.com/sunpy/sunpy/pull/4586>
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

* map.rotate PR addressed <https://github.com/sunpy/sunpy/pull/4502/files>
* We need to properly test how different package affine transform and their effects on the data.
* We should test the 'ground-truth' of a map.rotate with reproject (flux conservation) with other affine transformations on a SDO image. This is worth writing a paper upon with the results - as a 'standard'/best practices that can be referenced.
* Mike has lots of work done on different methods on image processing - hasn't published (yet) but definitely worth talking about more.
* See this [PR on aiapy](https://gitlab.com/LMSAL_HUB/aia_hub/aiapy/-/issues/1) regarding the agreemement between SSW and aiapy

## 30 September 2020

### Agenda

* Project repo (<https://github.com/sunpy/sunpy-project/issues>)
* sunkit-instruments
* outreachy
* Coordination meeting
* PR Discussion
* Issue discussion

### Minutes

* outreachy
  * Project ideas: <https://demo.codimd.org/n5vdYiSnSAC33jNXmUtvdQ>#
* ndcube
  * Experiment with extra coords on real world data
  * Path towards using NDCube to replace Map?
  * Needs discussion at coorindation meetin

## 23 September 2020

### Agenda

* PR Discussion
  * <https://github.com/sunpy/sunpy/pull/4432> - Ignore out-of-range years for an SRS query
  * <https://github.com/sunpy/sunpy/pull/4476> - Force metadata to be a MetaDict
* Issue discussion
  * <https://github.com/sunpy/sunpy/issues/4478> - OpenCV as an alternate affine transform library
* Transferring `instr` issues from `sunpy` core to `sunkit-instruments`
* `CompositeMap` woes (issue [#2745](https://github.com/sunpy/sunpy/issues/2745) et al.)
* [`aiapy` JOSS paper](https://gitlab.com/LMSAL_HUB/aia_hub/aiapy/-/merge_requests/79)--feedback welcome!
* NDCube 2.0 NDCube strikes back (<https://demo.codimd.org/54dm5gPMQmmJux6fV-3AOQ>)

### Minutes

* PR Discussion
  * <https://github.com/sunpy/sunpy/pull/4432> - Ignore out-of-range years for an SRS query
    * Merged, might backport
  * <https://github.com/sunpy/sunpy/pull/4476> - Force metadata to be a MetaDict
    * Decided that it's probably not possible to trigger the fallback to basic wcs?
  * <https://github.com/sunpy/sunpy/pull/4394> - Functionality to client to download new GOES 16/17 data and reprocessed 13/14/15
    * Discussion of which data to default to (new or old data)
    * Discussion of whether to force the user to specify a version
    * Decided to add provider option to switch between old/new data, and default to new data
* Issue discussion
  * <https://github.com/sunpy/sunpy/issues/4478> - OpenCV as an alternate affine transform library
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
  * <https://github.com/sunpy/sunpy/pull/4451> - Use bunit in sunpy.map
  * <https://github.com/sunpy/sunpy/pull/4455> - Improve title of differential rotation example
* Affiliated package re-reviews <https://github.com/sunpy/sunpy.org/issues/242>
* Affiliated package for various solar models (Will)
* Performance versus elegance, i.e. how do we deal with the question "why is sunpy so slow???" (Will)

### Minutes

* PR Discussion
  * <https://github.com/sunpy/sunpy/pull/4451> - Use bunit in sunpy.map
    * Comments added
  * <https://github.com/sunpy/sunpy/pull/4455> - Improve title of differential rotation example
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
  * Opened <https://github.com/sunpy/sunpy/issues/4459> for future discussion.

## 2 September 2020

### Agenda

* PR Discussion
  * Ready for review:
    * <https://github.com/sunpy/sunpy/pull/4433>, Move colormap data to .csv files
    * <https://github.com/sunpy/sunpy/pull/4432>, Ignore out-of-range years for an SRS query
    * <https://github.com/sunpy/sunpy/pull/4418>, Add some missing bits to the API docs
* 2.1 Release
* Other Topics

### Minutes

- PR Discussion
  * 4433 is ready to go with a rebase if tests pass
  * 4432 should wait for the GenericClient refactor PR
  * 4418 waiting on a doc build to pass
  * 3738 is not generic enough, and will need so much refactoring that it will be worth starting again, so decided to close.
* 2.1 feature freeze is the 23rd October

## 19 August 2020

### Agenda

* GSOC
  * Fido
  * Glue Solar
  * Sunspotter
* PR Discussion
* Other Topics
  * SPD Chat

## 12 August 2020

### Agenda

* GSOC
  * Fido
  * Glue Solar
  * Sunspotter
* PR Discussion
  * [#4405](https://github.com/sunpy/sunpy/pull/4405)
  * [#4391](https://github.com/sunpy/sunpy/pull/4391)
  * [#4378](https://github.com/sunpy/sunpy/pull/4378)
  * [#4394](https://github.com/sunpy/sunpy/pull/4394)
* Other Topics

## 5 August 2020

### Agenda

* GSOC
  * Glue Solar
  * Sunspotter
  * Fido
* PR Discussion
  * [#4405](https://github.com/sunpy/sunpy/pull/4405)
  * [#4391](https://github.com/sunpy/sunpy/pull/4391)
  * [#4378](https://github.com/sunpy/sunpy/pull/4378)
  * [#4394](https://github.com/sunpy/sunpy/pull/4394)
* Other Topics

### Minutes

* GSOC
  * Glue Solar
    * Docs build
    * tox issues
    * Dev guide
  * Sunspotter
  * Fido
    * Gallery example combining HELIO, HEK, and JSOC
    * Old IRIS JSOC issue
    * Integration of scraper/dataretriever with redesign of GenericClient [#4321](https://github.com/sunpy/sunpy/pull/4321)
* PR Discussion
  * GOES PR
    * waiting on GenericClient updates
    * we still aren't quite sure how to support the old FITS data for 13-15
    * maybe an extra `attr`?
    * But how best to handle data from multiple servers...
  * JSOC url-tar PR
    * Can this be used with `Fido`?
    * Should this be an `attr` rather than a keyword argument?
    * Discussion about using `JSOCClient` directly rather than through `Fido`
    * What do `request_data` and `get_request` do that `search` and `fetch` don't?

## 22 July 2020

### Agenda

* GSOC
* PR Discussion

### Minutes

* GSOC
  * Fido
    * Ideally we shouldn't have separate `Time` attrs for HEK and non-HEK queries. But then how to discriminate between HEK and non-HEK queries?
    * Documenting the return type of all the HEK columns; is this a worthwhile exercise?
  * Sunspotter
  * Glue
* GOES XRS Discussion
  * We seem to ...

## 15 July 2020

### Agenda

* GSOC
* PR Discussion
  * <https://github.com/sunpy/sunpy/pull/4333>
  * <https://github.com/sunpy/sunpy/pull/4053>
  * <https://github.com/sunpy/sunpy/pull/4236>
  * <https://github.com/sunpy/sunpy/pull/4343>
  * <https://github.com/sunpy/sunpy/pull/4350>
  * <https://github.com/sunpy/sunpy/pull/4331>

### Minutes

* GSOC
  * Fido
    * Combined metadata and data product searches now working, e.g. HEC and XRS queries
    * Helio queries require table name. If not specified user is prompted for it.
  * Sunspotter
  * Glue
    * WCS autolinking PR
    * Preferred colormap PR
    * 1D Spectrum with WCS PR
* PR Discussion
  * Differential rotation test and HMI synoptic map PRs pretty much ready to be merged
  * Put off ERFA discussion until next week (or the next time that interested parties are present)
  * Nabil's PR for removing all deprecated 1.1 code is pretty much ready to be merged as well.
* We need a 2.0.2 release soon, mostly for the NOAA fix

## 8 July 2020

### Agenda

* GSOC
* PR Discussion

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

* GSOC
* CI changes
  * Figure tests
  * RTD PR builds
* Post 2.0 changes.
* Pull Requests

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

* GSOC
* What is blocking the 2.0 release?

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

* GSOC
* 2.0 blockers

### Minutes

#### GSoC

##### FIDO

* [#4055](https://github.com/sunpy/sunpy/pull/4055) ready for review

##### Sunspotter

* [#4238](https://github.com/sunpy/sunpy/pull/4238) table matcher, in progress with euclidian distance and cosine similarity.
* Requested to have it also as example in the gallery.
* Some people not convinced this should live on core

##### Glue

* click and see a spectrum profile of that pixel

#### 2.0 Blockers

## 13 May 2020

* Discussion of potential Fido clients: <https://docs.google.com/document/d/1KYpqebFisjMRYJEoYKBJxqwIMW_jO2gaUsNVBCu_B7Y/edit#heading=h.ybxw3flop3dy>
* sunpy 2.0 outstanding PRs: <https://github.com/sunpy/sunpy/milestone/41>
* 2.0 Release
* How should we deal with the `instr` subpackage in terms of the new `sunkit-instruments` repo?

## 6 May 2020

The collaboratively editable version of the minutes and agenda for the upcoming meeting can be found [here](https://demo.codimd.org/GAEnxycXQcCQLrAFN7ie8A). These will be archived here on the wiki following the meeting.

## 29 April 2020

No community meeting was held due to the Python in Heliophysics Spring Meeting.

## 22 April 2020

### The road to 2.0

We need to review all PRs <https://github.com/sunpy/sunpy/milestone/41> to get ready for an RC this week.

### pyastro Hack ideas

See <https://docs.google.com/spreadsheets/d/1gsEQ3_xxHw4_gPnkfEna2IPqN9e7Cdom8KM_o6TVaUE/edit#gid=0> for the official list

* Magnetogram sources/clients/examples (led by dstansby)

### Meeting notes

* Meeting streamed onto YouTube for posterity
* 2.0 PRs
  * Rectangle - leave for Albert to review
  * Attr registration - waiting on changes in response to review
  * User config - needs another review, should change funciton name to `copy_default_config`
  * JSOC error - re-milestone to 2.1
  * VSO fetch fix - re-milestone to 2.1
  * Moving constants - restarted failing build, waiting for Albert to review
  * Map singeldispatch - merged
  * What's new - add ideas!
* General chat about differences bewtween old and new differential rotation code

## 15 April 2020

### Agenda

#### PRs

- **Added an HTML summary for Map and MapSequence** -<https://github.com/sunpy/sunpy/pull/3951>
* **Add contour map method** - <https://github.com/sunpy/sunpy/pull/3909>
  * Suggestions for meaninful tests?
* **Map now raises the file that failed to load if it errors on reading** - <https://github.com/sunpy/sunpy/pull/3727>
  * David S. suggests opening a new PR/branch, as devs are now just force pushing to the original contributor's branch...
  * Nabil suggests its ok.

### Minutes

* Merged sunpy.sun.sun Pr
* #3951 needs review
* Discussion on methods on map vs functions in maputils relating to #3909, decided to put `contour()` in `maputils`.

## 8 April 2020

### Agenda

* Follow-up from SunPy Coordination Meeting last week
* Issue triage
* PR review
  * **add .cmap and .norm property to plot_settings**
    * <https://github.com/sunpy/sunpy/pull/3624> - we said we would make a decision on this at the dev meeting but I don't think we did
  * **Implemented Groundclients in continuation with PR 2619**
    * <https://github.com/sunpy/sunpy/pull/3763> - need to check the clients and VSO return same data products, and whether VSO can provide real time data now.
  * **modified search metadata to return Astropy.Table**
    * <https://github.com/sunpy/sunpy/pull/3950>
  * **Add a other issue template**
    * <https://github.com/sunpy/sunpy/pull/3940>
  * **Added an HTML summary for Map and MapSequence**
    * <https://github.com/sunpy/sunpy/pull/3951>
  * **Fix deprecated decorator**
    * <https://github.com/sunpy/sunpy/pull/3982>
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
