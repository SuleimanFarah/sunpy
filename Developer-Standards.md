## Submitting Code
In order to maintain a high-quality code, all code should be submitted as a pull requested so that the SunPy community can review the code and provide feedback. Pull requests can be accepted by the original author if more than 24 hours have passed.

## Core Requirements and Recommendations [tbd]
These standards are heavily copied from astropy. Thanks astropy!

###  Language Standard
English is the default language for all doc strings and inline commands. Variables names should also be based on english words. In addition, the standard for spelling is American english.

* The package should meet the interface requirements set out by the coordination committee.
* Package layout and documentation should follow the form of the template package included in the core package source distribution [not yet implemented].
* Packages must be compatible with Python 2.6, 2.7, and 3.x (for 3.x compatibility, the 2to3 tool will be used).
* The package should be importable with no dependencies other than the Python Standard Library (v2.6), NumPy, SciPy, matplotlib, and components already in the core library.
* Additional dependencies are allowed for sub-modules or in function calls, but they must be noted in the package documentation and should only affect the relevant component.
* Docstrings must be present for all public classes/methods/functions, and must follow the form outlined in the “Documentation Guidelines” document [tbc]. Additionally, examples or tutorials in the package documentation are strongly recommended.
* Unit tests are encouraged for all public methods and functions, and should adhere to the standards set in the “Testing Guidelines” document [tbc].
* C extensions will be allowed only when the provide a significant performance enhancement over pure python. When C extensions are used, the python interface must meet interface guidelines, and the use of Cython is strongly recommended.
* If an external C library is needed, the source code for the library should be bundled with the sunpy core. Additionally, the package must be compatible with using a system-installed library instead of the version included in astropy.
* Packages can include data in [path tbd] as long as it is less than about 100 kb. If the data exceeds this size, it should be hosted outside the source code repository and downloaded using the approved sunpy mechanism [tbc].
* All persistent configuration should be stored using the functions in sunpy.config.
* General utilities necessary for but not specific to the package should be placed in the <packagename>.utils module. These utilities will be moved to the sunpy.utils module when the package is integrated into the core package. If a utility is already present in sunpy.utils, the package should always use that utility instead of re-implementing it in <packagename>.utils.
* Packages implementing many classes/functions not relevant to the component requested will not be accepted - the package should only include the required functionality and relevant extensions.
* The use of short cryptic variable names is highly discouraged.

## Coding Style/Conventions
These standards are heavily copied from astropy. Thanks astropy!

* The code will follow the standard PEP8 ‘Style Guide for Python Code’ (http://www.python.org/dev/peps/pep-0008/). In particular, this includes using only 4 spaces for indentation, and never tabs. A pep8.py checker script is available at http://pypi.python.org/pypi/pep8.
* The “import numpy as np”, “import matplotlib as mpl”, and “import matplotlib.pyplot as plt” naming conventions should be used wherever relevant. 
* Classes should either use direct variable access, or python’s property mechanism for setting object instance variables. “get_value”/”set_value” style methods should be used only when getting and setting the values requires a computationally-expensive operation.

## Porting Code from IDL
As much code already exists in SolarSoft and written in IDL, it is expected that many functions will need to be translated from IDL to Python for inclusion in sunpy. The following describes the sunpy standards for how this should be done.

### Naming conventions
Much of the code in SolarSoft has its roots in Fortran. Fortran is restrictive programming languages in terms of variable names therefore many variable and function names are short and cryptic. The sunpy convention is to use easily understandable and more verbose names. Many python shells provide automatic code completion so the user experience is not likely to be impacted by longer names. When converting IDL code, the code should be converted to a more Pythonic style (e.g. more verbose, clearer) when applicable unless the function is very well-known and already has an intuitive name.

### Documentation
Copying the explanation (being careful to make modifications if things have changed) from the original IDL documentation, and including a reference to exactly where the code came is the standard. While it may be informative to have the entire IDL documentation preserved in the Python code, this is discouraged. If the user really needs to find out more information about the original version of the function, they can use the reference provided (e.g. under See Also) to the IDL routine.
