### Date of Meeting
**20** **September** **2019**

### Attendance
- **Present:** Steven Christe (Chair), Kevin Reardon, Bin Chen, Stuart Mumford
- **Absent:** Tiago Pereira (technical issues), David Pérez-Suárez, Sabrina Savage, Jack Ireland, Monica Bobra, Russell Hewett

### Agenda

1. Proposal Readiness
1. Project roles
1. Board Committees
1. NumFocus Summit

### Meeting Notes

**Topic 1: Instrument-Prep routines - Sunpy core scope**

_Overarching Question_: How to interface with external packages developed by instrument/project teams?<BR>

We already have SEP-004 - is this sufficient? Maybe we need to add in some additional text about instrument packages?<BR>
Is an instrument package different than other affiliated packages? <BR>
We should document this, but maybe it doesn’t need to be in a SEP (for flexibility)?<BR>
Need more information about what does SunPy provide to affiliated packages?<BR>
Should finally write up a review process for accepting affiliated packages, adding more clarity and structure that we can point to.<BR>
New territory - not many (no?) instrument teams have already released data prep code in Python.<BR>
SunPy can offer support, community, framework, reviews.<BR>
Who funds this work? Instrument teams/projects/missions might have funding.<BR>
Would be better to provide guidance up front, before package is “complete” and needs to be integrated.<BR>
External package/Instrument team/Affiliated package liaison?<BR>

### Actions:
* Update SEP to express that affiliated package is the preferred way to integrate compliant, instrument-specific (or instrument-task-specific) packages into SunPy.
* Create more user friendly documentation on affiliated packages (how, why, who), standardize application process. Create a conda channel?
* Create an Instrument Team sub-Committee - monthly meetings? Include board members with different expertise.

***

**Topic 2:Community Roles Proposal:**

_Liaison Roles:_ <BR>
Noted Affiliated Package Liaison and Instrument Team Liaison in proposed role list.<BR>
Are these the same person? What are the different responsibilities?<BR>
Maybe there is some difference in needs/approach of two groups? The former works on compliance, the second on participation?<BR>
Should probably bring in space instrumentation expertise - to have insight on the management of code development for NASA and ESA projects.<BR>

Steven volunteered to be affiliated package liaison, Kevin and Bin (deputy) volunteered to be Instrument Team Liaisons. They are to draft responsibilities for Instrument Team Liaison.<BR>
Have an Affiliated Package/Instrument Subcommittee meeting. Lead developer appointee also on committee
Need to draw up charter for subcomittee.

_Other Community Roles:_ <BR>
Which community roles should be filled by Board members, which by broader community members? Instrument package liaison? Communications and Outreach Lead?<BR>

Some tasks have been automated - reduced workload of CI Maintainer, Release Manager.<BR>
Lead Newcomer Mentor could be an important role to bring in new users.<BR>

Communications and Outreach Lead - we need more public/social media presence.<BR>
Leads can deputize and delegate! But it is important that board maintain some oversight of communication strategy and approaches.<BR>

Also need an interface (liaison) to NumFocus. <BR>

Education Lead vs. Newcomer Mentor?<BR>
Education Lead manages resources to teach community, persistent artifacts, not as specific to sunpy
Mentor is more one-on-one interactions.<BR>
Some of these roles are more important and necessary than others.<BR>

Finance Committee is needed -- NumFocus Summit arrangements are moving forward.<BR>
Raises question of how to allocate SPD grant.

### Actions:
* Bin to get a letter from the SPD board about what is expected to be done with the SPD money.
* Add Ombudsperson and Diversity and Inclusion Lead
* Steven to create a board subcommittee and roles document. Should not be an SEP!
* Draft responsibilities for Instrument Team Liaison

***


**Topic 3: Proposal Preparation**

Create a Proposal Repository - old proposals, new ideas, possibilities for synergies with other projects.<BR>
Maintain a accessible copy of previous proposals for desired new frameworks.<BR>
Need to identify and document science uses of ndcube and other infrastructure - which could be attractive for funding agencies.<BR>
There will be another CSSI proposal call next year - we should be prepared.<BR>
Need a set of ideas/concepts for proposals with leads ready to go.<BR>
Identify a lead for collecting this information.<BR>

There should be an Official SunPy Webinar about ndcube - to demonstrate how it can be integrated into science use cases. Bin (and Kevin?) will be able to provide some sample data cubes.<BR>
This could/should be the first in an evolving series.

### Actions:
* Start SunPy webinar series
* Add webpage about webinars

***