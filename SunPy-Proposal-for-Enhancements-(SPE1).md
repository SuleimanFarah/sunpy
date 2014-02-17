# What is a SPE?
SPE stands for SunPy proposal for Enhancements. A SPE is a design document modeled after the Python Proposal for Enhancements which describes a new SunPy feature, process, or major changes to existing processes or features. The purpose of the document is to present a concise technical specification and rational for the new feature or change to the SunPy community. The SunPy board is then charged to review the SPE and reach a decision as to whether the proposal should be accepted, rejected, or modified. The SunPy board shall also review the implementation of all SPEs. A member of the SunPy board may also request that a change to SunPy requires that a SPE be written and reviewed.

Changes that typically require a SPE
* the addition of a new feature to SunPy
* changes to the user-facing API
* major refactoring of the backend
Changes that do not typically require a SPE
* the addition of new sources to maps, light curves, spectra, etc.
* bug fixes
* minor enhancements

# SPE Types
There are generally two types of SPE.

* **Standard**: This SPE introduces and describes a new feature or changes to an existing feature (e.g. API change). The purpose of this type of SPE is to be at first proposal and eventually mature into a design document (if accepted). It is generally a good idea for a Standard SPE to come _before_ any code has been written.

* **Process**: This type of SPE describes a new process or a change to an existing process. in the management of the SunPy project. Examples include procedures, guidelines, changes to the SunPy decision-making process or management structure, and changes to the tools or environment used in SunPy. Any meta-SPE (proposed changes to the SPE process) is also considered a Process SPE.

# SPE Workflow

## Creation
SPEs should contain a concise description of a single new idea or proposal. SPEs are generally not necessary for small enhancements though a SPE may sometimes be requested by the SunPy board in some cases. A SPE begins its life as a proposal. Legibility, organization, and focus are key features of a successful SPE. SPEs can be rejected out-right if they lack any of those characteristics. All SPEs must identify a champion (usually the author) whose job it is to present and defend the proposal to the SunPy board. It is generally a good idea to discuss the new idea with the community and the board before going to the trouble of writing a SPE in order to gauge whether there is any chance of acceptance but it is not required. All SPEs shall be sponsored by at least one SunPy board member.

All SPEs creators should begin with the SPE template which is known as SPE1. SPE1 is stored in the sunpy/sunpy-SPE repository. Fork the repo and create a new file with your SPE. SPE are written with markdown.

### Amending a SPE
If a topic is already covered by an existing SPE and the change is not a major one than it is appropriate to propose an amendment to an existing SPE. All the usual rules apply and processes apply to the amendment of a SPE as for the creation of a new SPE.

## Submission
All new SPE should be pull requested into the sunpy/sunpy-SPE repository.

## Review Process
New SPEs currently undergoing discussion are pull requests into the sunpy-SPE repository. Discussions about the SPE can take place as part of the pull request but also using the standard SunPy discussion channels (IRC channel, mailing list, hangout). Once a SPE is officially submitted by pull request an SunPy editor must be assigned by the SunPy board. The role of the editor is to aid the submitter and make sure that the SPE follows the accepted standard. The author and editor can be the same person. A SPE must be accepted by a majority of the SunPy board. The status of a SPE can be any of the following

* **Discussion**: This means that SPE is currently being considered and a decision has not been made.
* **Accepted**: The SPE has been accepted and it will be assigned a number and merged into the sunpy-spe repository. A decision rational must be drafted and added to the SPE. If the SPE is of the Standard type then it can now be implemented.
* **Implemented**: Only valid for a Standard SPE. This status means that the feature discussed in the SPE is implemented and has been merged into the main SunPy repository. At least X members of the SunPy board must sign off on implementation for it to be accepted.
* **Rejected**: The SPE has been rejected. A decision rationale should be provided by the board and the SPE should still be assigned a number and merged in order to close the issue. It should be noted that a future SPE can supersede the decision.

# SPE Template

## Header
* **author(s)**: First Last, First Last
* **contact email**: me@myemail.org
* **date-creation**: YYYY-MM-DD
* **date-last-revision**: YYYY-MM-DD
* **type**: standard/process
* **status**: accepted/rejected

## Abstract
A short description of the SPE including a statement of the problem the SPE is seeking to solve

## Detailed Description
If this is a standard SPE this section should contain usage examples.

## Decision Rational
This is a great idea because...