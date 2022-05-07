### Date of Meeting

25th July 2014

### Agenda

- Lead Developer Report
- lists versus iterators
- upcoming code and SEPs (or lack thereof)
- downloading structure and the database
- IDL helper functions?

### Attendance

**Present**: Steven Christe (Chair), David Perez-Suarez (Vice-Chair), Andrew Inglis (Secretary), Albert Shih, Stuart Mumford, Russell Hewett, Juan Carlos Oliveros Martinez

**Absent:** Thomas Robitaille, Jack Ireland

### Meeting Notes

- **Steven** initiated a **discussion** of the nature of SunPy. Whether we should consider it as it’s own ‘environment’, or whether it is more of a package that exists within the wider Python ‘environment’. This was linked to the issue of whether, within SunPy, it is philosophically acceptable to deviate from what is considered 'Pythonic' in order to provide a different 'environment' for users. Different points of view were raised, without a clear consensus.

- A related **discussion** was raised regarding becoming compatible with Python 3.x. Currently dropping SunPy support for Python 2.6 is imminent. It was agreed that SunPy Developers need to become more familiar with Python 3.x for future development. **Decision made** to write an SEP for the transition between 2.x to 3.x
  - A timeline for transitioning to Python 3 is also present in the SunPy roadmap, and may need updating.

- **Discussion** of the role of affiliated packages and what constitutes one. This discussion was motivated by a proposed TEBBS package (Daniel Ryan) and a DEM calculation package (Drew Leonard).
  - It was generally agreed that the main SunPy repository should contain data calibration routines, such as AIA_PREP etc, and instrument response information.
  - It is less clear clear whether packages that are not calibration based, such as science tools like TEBBS or DEM calculation packages, should be contained within the SunPy package or should be affiliated.
  - Some **advantages** of including such packages in the main repository that were mentioned:
    - Increases the functionality of SunPy, and the number of users
    - Helps the community to agree on standard utilities instead of re-inventing them
    - Allows the SunPy team to more easily assist in the package development
  - some **disadvantages** of including such packages in the main repository that were mentioned:
    - may obscure credit from the original author of the package
    - if the original developer departs or moves on, then the SunPy team must maintain the code
    - may give the impression that there is one standard procedure when there may be many.

  - SunPy could support **two different types** of affiliated package, similar to AstroPy. 1) A package that is a repository within the SunPy organisation (e.g. github.com/sunpy/tebbs). 2) A package that is completely external to SunPy but depends on SunPy.

  - **Decided that an SEP is needed** on the role of affiliated packages.
  - **Decided** that TEBBS (Daniel Ryan) provides a good **test case** for how an affiliated package can be developed. **Stuart** will coordinated with Dan. This will help answer the current questions.

- **Discussion** of having enough SEPs. Current GSOC students look unlikely to complete their SEPs. Generally agreed that **mentors** need to do a better job of assisting with SEPs and have a better idea of what is required.

- **Russell** proposed that future GSOC projects should be in the form of an SEP, at least in draft form.

- **Juan Carlos** initiated a discussion about the current practicality of SunPy, in particular, what are the key features and priorities needed in SunPy to make it viable for the wider community.
  - **Juan Carlos** mentioned that a popular request from solar physicists was additional instrument routines
  - **Steven** suggested that the roadmap be prioritized towards items that will benefit users. This will help with correct prioritization of open issues and additional features.
  - The board asked **Juan Carlos** to investigate what potential users really want from SunPy by canvassing the community. This will subsequently be translated into SunPy issues. This will also enable **prioritization** of open issues.

**Russell** departs the meeting.

Meeting concludes.
