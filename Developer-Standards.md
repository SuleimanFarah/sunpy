This page is meant as a temporary place to store coding standards developed by the SunPy coding community.

## Language Standard
English is the default language for all doc strings and inline commands. Variables names should also be based on english words. In addition, the standard for spelling is American english.

## Submitting Code
In order to maintain a high-quality code, all code should be submitted as a pull requested so that the SunPy community can review the code and provide feedback. Pull requests can be accepted by the original author if more than 24 hours have passed.

## Variable Names
In general the use of short cryptic variable names is discouraged.

## Porting Code from IDL

### Naming conventions
Naming conventions should be converted to a more Pythonic style when applicable unless the function is very well-known and already has an intuitive name.

### Documentation
Copying the explanation (being careful to make modifications if things have changed) from the original IDL documentation, and including a reference to exactly where the code came is enough. While it may be informative to have the entire IDL documentation preserved in the Python code, it could also bog the code down and distract the user from the important information. If the user really needs to find out more information about the original version of the function, they can use the reference provided (e.g. under See Also) to the IDL routine.

## Core Requirements and Recommendations [tbd]

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
* The package should follow the style guide in the next section.