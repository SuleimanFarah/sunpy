```
[17:00:21] Meeting started by davidps
[17:01:39] Meeting chairs are: cadair, 
[17:03:23] LINK: https://docs.google.com/document/d/11oWYaZqbJYZiUoKD2rK-kZzoWZAbBBr9h1OkZ-w7LZ0/edit?usp=sharing [SunPy Org Meeting Agenda - Google Drive]
[17:04:23] Current subject: Agree on the agenda, (set by DavidPS)
[17:06:00] INFO: We don't have a decission process for our first decissions
[17:13:10] <DavidPS> There are two options on the moment, one is talk about the structure of SunPy first, the other is to talk first about the scope
[17:17:01] INFO: The agenda has been aproved: Scope, Mission, Structure
[17:17:52] Current subject: The Scope of SunPy library, (set by DavidPS)
[17:18:58] <Cadair> The running notes are here:
[17:19:00] LINK: http://home.cadair.com/sunpy/%23SunPy/2014-03-05-17:00_SunPy-Organisation-Meeting.log [None]
[17:20:06] INFO: SunPy purpose:To provide a community-developed, free and open-source solar data analysis environment in Python (ehsteve)
[17:22:32] INFO: SunPy Organisation purpose: To facilitate and promote the development and maintenance of a community-lead, free and open-source solar data analysis environment in Python
[17:23:32] <DavidPS> ehsteve thinks whether Python is our only aim... or we want to cover a broader scope
[17:25:21] <DavidPS> renstar argue whether this also covers SolarSoft
[17:26:39] <DavidPS> ehsteve worries whether a webapp (no in python) would conflict with SunPy - Python marriage
[17:27:33] <DavidPS> affiliate packages could solve this issue
[17:28:58] <DavidPS> Andrew, Cadair and renstar suggest to remove Python from our moto
[17:30:01] <DavidPS> ehsteve said: Could SSW jump to us and ask to support them?
[17:30:28] <DavidPS> jack I, renstar: What about GDL, PDL, ...
[17:31:46] <DavidPS> ehsteve: Python was our main tool, do we want it in our mission statement?
[17:32:20] <DavidPS> Cadair, that's fine for our mission statement, but maybe not for our main moto
[17:33:09] <DavidPS> renstar, we could sell it as big scope (non based just in python) and even aim to control SSW.
[17:33:34] <DavidPS> ehsteve, prefer to start small, just Python first
[17:33:45] <renstar> to clarify: I was not arguing either way.  I just wanted to lay the options out specifically.
[17:34:21] <DavidPS> thanks renstar
[17:35:00] <DavidPS> Vote: do we want Python or not in our scope?
[17:37:32] <Cadair> Andrew +1
[17:37:37] <Cadair> Albert +1
[17:37:43] <Cadair> Steven +1
[17:37:48] <Cadair> Jack +1
[17:37:59] <Cadair> Russell +0 (no dog in this one, i just want it done right)
[17:37:59] <DavidPS> David +1
[17:38:05] <Cadair> Stuart +1
[17:38:14] <Cadair> Where plus one represent for Python
[17:39:23] INFO: We have Python in our purpose statement!
[17:40:43] <DavidPS> Are we providing a environment or software? - renstar asks
[17:44:52] <DavidPS> yt uses environment, astropy uses package - Cadair said
[17:45:31] <DavidPS> Jack I. suggested suite
[17:46:08] <DavidPS> Albert is not sure about environment.
[17:46:52] <DavidPS> Astropy manages a list of packages through the affiliates programme
[17:47:07] <DavidPS> (Cadair's explanation)
[17:50:05] <DavidPS> renstar suggests to use eco-system 
[17:52:11] <DavidPS> ehsteve thinks Packages is too limiting
[17:53:18] INFO: We are trying to find the right word: environment, packages, suite, eco-system, ...
[17:56:10] <DavidPS> Cadair thinks the Organisation should not build/make the environment itself, but make it possible to build so by the user
[17:59:54] INFO: Voting for: "To facilitate and promote the development, maintenance and use of community-led, free and open-source solar data analysis software based in the scientific Python environment."
[17:59:58] <Cadair> Vote:
[18:01:09] <Cadair> What is the purpose of of the SunPy Organization:
[18:01:34] INFO: "To facilitate and promote the use and development of community-led, free and open-source solar data-analysis software based on the scientific Python environment.
[18:02:21] <Cadair> passed by absolute majority
[18:03:28] Current subject: Structure of the project, (set by DavidPS)
[18:03:40] LINK: https://github.com/sunpy/sunpy/wiki/SunPy-Proposal-for-Enhancements-%28SPE1%29 [SunPy Proposal for Enhancements (SPE1) · sunpy/sunpy Wiki · GitHub]
[18:04:27] LINK: https://docs.google.com/document/d/1Ms2L9fmv2QK5txqTHpab3RPeFth05Eouh8WBsq9NDeA/edit?usp=sharing [Google Drive]
[18:04:37] <Cadair> Which is a google doc version of the first link
[18:04:46] <DavidPS> (updated)
[18:06:25] <DavidPS> ehsteve: SPE2 depends on SPE1, but the board of decission is defined on SPE2
[18:06:57] <DavidPS> ehsteve describes the purposes of SPE (Sunpy Proposals for Enhancements)
[18:07:14] <DavidPS> This is: how major changes get review and incorporated in SunPy
[18:07:53] <DavidPS> Examples: New features, changes user-facing API, major refactoring, ...
[18:09:10] <DavidPS> The board is a group of people to keep the aim of sunpy... it does not mean they need to be part of the implementation team
[18:11:35] <DavidPS> ehsteve explains the workflow for new SPE, how it is presented, discussed and aproved or not.  One of the boards have to be sponsored by one member of the board
[18:11:56] <DavidPS> SPEs can always be ammended
[18:13:09] <DavidPS> This will be made through the normal process of the PR through github
[18:14:23] <DavidPS> SPEs will have always a number (like python) even if they are rejected
[18:15:17] <DavidPS> Cadair suggests SEP: Sunpy Enhanced Proposal
[18:15:36] <DavidPS> which can be confused with Solar Energetic Particles (SEPs)
[18:16:04] <DavidPS> renstar suggest to keep like the community: Python uese PEP, we should use SEP
[18:16:34] INFO: Voting SEP/SPE
[18:16:34] <Cadair> ehsteve, SEP
[18:16:47] <DavidPS> DavidPS: SEP
[18:17:01] <Cadair> Cadair, SEp
[18:17:06] <Cadair> Jack: SEP
[18:17:19] <Cadair> s/SEP/SPE
[18:17:50] <Cadair> Albert: SPE
[18:17:57] <Cadair> Andrew: SPE
[18:18:03] <Cadair> renstar, SEP
[18:18:49] INFO: we will use SEP (even if people - other solar physicists - thinks this is a joke)
[18:19:55] <DavidPS> Cadair does not like the large formality for the proposition of new SEPs
[18:20:03] <DavidPS> (or so I understood)
[18:20:09] <Cadair> yes
[18:20:50] <DavidPS> ehsteve wants to know how the board represents the community
[18:21:10] LINK: https://github.com/astropy/astropy-APEs/blob/master/APE1.rst#ape-review [astropy-APEs/APE1.rst at master · astropy/astropy-APEs · GitHub]
[18:21:30] <DavidPS> Cadair suggests the wording of APE1 (astropy)
[18:22:19] <renstar> im going to second Cadair
[18:22:38] <DavidPS> Cadair thinks all the formality could intimidate
[18:25:40] <DavidPS> renstar and Cadair want to make it clear that SEPs are community-led
[18:32:41] INFO: Anyone can submit a SEP
[18:34:14] Current subject: What goes into a SEP, (set by DavidPS)
[18:35:29] <Cadair> General agreement on What is an SEP
[18:37:04] <DavidPS> SEP should be submitted for major new features, major changes to user-facing API, major refactoring
[18:37:09] <Cadair> General agreement on SEP types
[18:37:16] INFO: SEP types agreed
[18:37:32] Current subject: SEP workflow, (set by DavidPS)
[18:39:18] <DavidPS> ehsteve suggest that each SEP should be sponsored by a board member, Cadair does not understand  why...
[18:40:04] <DavidPS> ehsteve explains this is for help on understanding the process and to have a person in charge on the process
[18:40:31] INFO: all SEPs will have a member assigned to them
[18:41:05] <DavidPS> less pressure to the author
[18:41:47] <DavidPS> renstar, thinks the case would be like: - Hey, does Sunpy can do X? - No, but you can propose it
[18:42:09] <DavidPS> instead of -Hey! let's make Sunpy to display earquakes measurements
[18:43:31] <DavidPS> renstar sugegst the filenames with 4 digits: ie. sep0001
[18:43:42] <DavidPS> though it can be refered as SEP1
[18:43:57] <DavidPS> Just for better file sorting
[18:44:43] INFO: ammending seems good to everyone
[18:45:28] Current subject: Review processes of SEPs, (set by DavidPS)
[18:47:01] <DavidPS> renstar suggests that code may be ready before the SEP is accepted
[18:49:13] <DavidPS> Cadair: suggest how you envisions the API looks like in someway separated on the SEP
[18:49:28] <DavidPS> (astropy has a API repository to test them)
[18:52:41] <DavidPS> ehsteve, how is in charge to review the implementation of SEPs?
[18:53:10] <DavidPS> ACTION thinks the ones that have writing rights to repository
[18:53:23] <Cadair> +1
[18:54:19] <DavidPS> ehsteve, SEP2 has an structure for it.  like Lead Developer (and the other trusted developers)
[18:54:49] <DavidPS> renstar, this is like  B**L -... not for life... like python itself
[18:54:58] <DavidPS> renstar, could you put this rigth?
[18:55:00] <renstar> BDFL
[18:55:47] <DavidPS> This is, like Cadair has been done for the whole last year
[18:56:45] <DavidPS> Cadair, thinks lead developer would be in charge...
[18:57:37] <DavidPS> [Cadair, fill the blank]
[18:57:42] INFO: Albert leaves
[19:00:43] INFO: Lead developer functions implements what the board wants and has full organization over the repo and runs all the day to day stuff, selected by the board,
[19:02:41] <DavidPS> ACTION discussions should be on mailing list or github pr?
[19:03:08] <DavidPS> Cadair: Thinks it should be on mailing list as it has a larger audience
[19:03:20] INFO: Andrew leaves
[19:04:05] INFO: Andrew doesn't leave... just a few more minutes
[19:05:16] <DavidPS> renstar, suggests to remove IRC channel, and keep the discussion to be kept on the mailing list
[19:05:23] <DavidPS> as a more better forum
[19:05:42] <DavidPS> as it's preserved.
[19:06:48] <Cadair> So is GH
[19:06:49] <DavidPS> ehsteve, thinks whether the discussion should also be on the pull request
[19:09:42] <DavidPS> ACTION we should link the thread to the PR discussion in GH
[19:10:48] INFO: All SEP discussions shall take place on the mailing list, and linked to the SEP in the PR
[19:12:50] INFO: Normal channels for code review will be formalised in the future
[19:14:46] <DavidPS> but... does this mean that another body have to be built for the code review?
[19:15:01] <DavidPS> Cadair, renstar thinks that this can be done organically
[19:15:44] INFO: Once an SEP is accepted, its implementation can be reviewed through the usual process. 
[19:16:00] INFO: renstar leaves
[19:16:33] INFO: renstar is still here
[19:17:09] <DavidPS> Cadair proposes to create the repo and do the PR.
[19:17:40] <DavidPS> ehsteve: suggests we are in agreeement, so no more email discussion about it.
[19:17:53] INFO: Everyone agrees!
[19:18:21] ACTION: ehsteve creates repo and PR SEP1
[19:19:14] <DavidPS> (ehsteve, you need to ".agreed to create SEP repo and PR SEP1)
[19:19:34] Current subject: When is the next meeting?, (set by DavidPS)
[19:19:52] ACTION: Cadair creates doodle poll
[19:20:26] INFO: everyone left
[19:20:30] Meeting ended by Cadair, total meeting length 8408 seconds
```