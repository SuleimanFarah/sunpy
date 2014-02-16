# What is a SPE?
SPE stands for SunPy proposal for Enhancements. A SPE is a design document modeled after the Python Proposal for Enhancements which describes a new SunPy feature, process, or major changes to existing processes or features. The purpose of the document is to present a concise technical specification and rational for the new feature or change to the SunPy community. The community is then charged to review the SPE and reach a decision as to whether the proposal should be accepted, rejected, or modified.

# SPE Types
There are generally two types of SPE.

* **Standard**: This SPE introduces and describes a new feature or changes to an existing feature (e.g. API change). The purpose of this type of SPE is to be at first proposal and eventually mature into a design document (if accepted). It is generally a good idea for a Standard SPE to come _before_ any code has been written.

* **Process**: This type of SPE describes a new process or a change to an existing process. in the management of the SunPy project. Examples include procedures, guidelines, changes to the SunPy decision-making process or management structure, and changes to the tools or environment used in SunPy. Any meta-SPE (proposed changes to the SPE process) is also considered a Process SPE.

# SPE Workflow

# Creation
SPEs should contain a concise description of a single new idea or proposal. SPEs are generally not necessary for small enhancements though a SPE may sometimes be requested by the community in some cases. A SPE begins its life as a proposal. Legibility, organization, and focus are key features of a successful SPE. SPE can be rejected out-right if they lack any of those characteristics. All SPEs must identify a champion (usually the author) whose job it is to present and defend the proposal to the community. It is generally a good idea to discuss the new idea with the community before going to the trouble of writing a SPE in order to gauge whether there is any chance of acceptance. 

All SPEs creators should begin with the SPE template which is known as SPE1. SPE1 is stored in the sunpy/sunpy-SPE repository. Fork the repo and create a new file with your SPE. SPE are written with markdown.

# Submission
All new SPE should be pull requested into the sunpy/sunpy-SPE repository.

# Review Process
New SPEs currently undergoing discussion are pull requests into the sunpy-SPE repository. Discussions about the SPE can take place as part of the pull request but also using the standard SunPy discussion channels (IRC channel, mailing list, hangout). 

# Acceptance Process
A SPE must be accepted by a majority of the sunpy core as well as a majority of the sunpy maintainers.

# SPE Template

## Header
Author(s): First Last, First Last
Contact Email: me@myemail.org
date-creation: YYYY-MM-DD
date-last-revision: YYYY-MM-DD
type: standard/process
status: accepted/rejected

## Abstract
A short description of the SPE including a statement of the problem the SPE is seeking to solve

