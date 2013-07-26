About me
========

- Name: Sebastian Humenda
- diploma computer science
- IRC Nick: Moomoc
- Github account: humenda
- Mail: s7369 \\\\at// mailbox DOT tu-dresden.de
- Web: http://crustulus.de

Project Description
===================

_Region Of Interest Object_

I have taken this idea from the sunpy SOCIS ideas page. I want to implement an
object, representing a region in space using coordinates. Furthermore this
region is bound in terms of time and possible energy.
It should also be possible to pass this object to HEK/HELIO (HER) query to filter
all features/events in this time range and region.
It should be possible to pass this object to the SDO cutout service
to get SDO data.

An additional requirement is that it should derive from major
module classes like lightcurve, map, etc.

Timeline
========


- 10.08-20.08: Holiday, but with some reading about the subject
- 20.08-25.08: get familiar with the techniques needed for implementation
    - read information about coordinate systems (where Region of Interest are
      specified in)
- 25.08-30.08: analyse phase
    - analyse problem, UML (?!)
    - present at the end to project
    - possibly lots of question asking
- 11. Sep: partial prototype
    - present a partial, but in its partiality working prototype
- Holiday: 29.09-04.10
- 07.10: in-between-presentation
    - present the project the status quo
    - discuss the implementation architecture
    - up to 50 % should be implemented
- 20.10: try to finish work
    - end implementation phase
    - start squashing bugs and the most certainly appearing hints from the
      project
- 01.11: prepare source tarball ;-)
