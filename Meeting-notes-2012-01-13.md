Location: GSFC
Present: Keith Hughitt, Steven Christe, Albert Shih, Richard Schwartz, Jack Ireland

**1. Python Namespace issues**

Description of problem: https://github.com/sunpy/sunpy/issues/99

No ideal solution decided on during discussion. Although PEP8 discourages function-level imports, it is probably okay for things are that only used in one function. __all__ should be used to manage * imports, but not for manipulating the namespace. How are other projects (e.g. Astropy) handling this?

(unresolved)

**2. Cleaning up the docs**
Steven is working on cleaning of the code reference section of the docs and consistently using autosummary/automodule to avoid adding extra overhead. Using autosummary for the bulk of the code reference generation makes it easier for contributors to have their code documentation automatically included and provides an incentive to write good documentation.

In general though it is not recommended (e.g. see numpy docs) that autosummary be used to automatically generate everything, but instead the documentation skeleton should be hand-crafted with autosummary filling in relevant sections. We will wait one year and reconsider our approach and see if something more involved like this is needed.

**3. instr module**
Question: Where should mission-specific code be kept?

Currently a "instr"module is used with sub-directories like "sdoaia". What about "instr.sdo.aia"? Any other schemes that would work well?

(unresolved)

**4. TimeRange**

*A generic "Range" base class should be created based on newly-added TimeRange class; this way other types of ranges (e.g. EnergyRange) could be easily incorporated in the future.
*Should TimeRange accept list input? e.g. TimeRange(['2012-01-01, '2011-05-13', etc])?

