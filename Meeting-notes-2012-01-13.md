Location: GSFC
Present: Keith Hughitt, Steven Christe, Albert Shih, Richard Schwartz, Jack Ireland

1. Python Namespace issues

Description of problem: https://github.com/sunpy/sunpy/issues/99

No ideal solution decided on during discussion. Although PEP8 discourages function-level imports, it is probably okay for things are that only used in one function. __all__ should be used to manage * imports, but not for manipulating the namespace. How are other projects (e.g. Astropy) handling this?





