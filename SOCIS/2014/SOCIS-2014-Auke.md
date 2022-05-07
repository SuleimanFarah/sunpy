## Project proposal

The current SunPy code runs only on python 2, whereas most Python projects are moving or have moved on to python 3. I would like to work on porting this project to python 3, if possible keeping python 2.7 compatibility. Since the code uses some C extensions, these will need some kind of upgrade or rewrite as well.

Additionally there are various bugs related to code quality and documentation, and as I am working on the code I hope to fix some of these as well.

I have previously worked on Python projects for various summers of code, and during my Electrical Engineering undergrad on C code, so in this sense I feel that I am technically qualified. Additionally I frequently work with git for collaborative development so this will not cause any problems.

## Additional notes

Biography: I'm currently studying for a master in maths at Cambridge Uni, looking to do a PhD in constructive categorical logic next year (so rather abstract but funnily enough closely related to CS). I have a BSc in applied maths and a BSc in electrical engineering from TU Delft. I did SOCIS last year (I basically rewrote the PyBRML library for bayesian reasoning & machine learning into modern Python code, and generalized the existing matlab-inspired code), and GSoC in 2010 (I wrote a component for the Gentoo package manager that was unfortunately too experimental to make it anywhere close to production).

Schedule: In June I'll mostly be celebrating having finished my exams, so I expect to do the bulk of the coding in July and August. I will also need to move from the UK to somewhere else in Europe (depending on where I will do my PhD) during the summer, so that will take up some time, and I want to go on a short holiday (less than a week).

* Week 1-3: get a first port to Python 3 working, keeping track of features that will have to be imported from \__future\__ for python 2.7
* Week 4: remove python <2.7 hacks and add \__future\__ imports to make the code run on pythons 2.7 and 3
* Week 5: check the coverage of the test suite and add tests where incompatibility due to code changes is possible
* Week 6: upgrade packaging, complete changes documentation
* Week 7: finalize python 3 port, inform community
* Week >8: work on the differential rotation project: bring it up to date and merge with master?
* Always: document changes and write PEP8-compliant code
