This page is meant as a temporary place to store coding standards developed by the SunPy coding community.

## Submitting Code
In order to maintain a high-quality code, all code should be submitted as a pull requested so that the SunPy community can review the code and provide feedback. Pull requests can be accepted by the original author if more than 24 hours have passed.

## Variable Names
In general the use of short cryptic variable names is discouraged.

## Porting Code from IDL

### Naming conventions
Naming conventions should be converted to a more Pythonic style when applicable unless the function is very well-known and already has an intuitive name.

### Documentation
Copying the explanation (being careful to make modifications if things have changed) from the original IDL documentation, and including a reference to exactly where the code came is enough. While it may be informative to have the entire IDL documentation preserved in the Python code, it could also bog the code down and distract the user from the important information. If the user really needs to find out more information about the original version of the function, they can use the reference provided (e.g. under See Also) to the IDL routine.