### Date of Meeting

9th June 2014

### Agenda

- Lead Developer Report
- 0.4.1 versus 0.5
- Vote on Units SEP
- Vote on Absentee voting clause
- Discuss Coordinates SEP

### Attendance

**Present**: Steven Christe (Chair), David Perez-Suarez (Vice-Chair), Andrew Inglis (Secretary), Albert Shih, Thomas Robitaille, Stuart Mumford

**Absent**: Jack Ireland, Juan Carlos Martinez Oliveros, Russell Hewett

### Meeting Notes

- Vote is held on acceptance of electronic/remote voting clause added to SEP-0002. Result: **6-0 in favour of the clause**

- Vote is held on the acceptance of the Units SEP (SEP-0004: using AstroPy units within SunPy). Result: **6-0 in favour of the clause.**

- **Lead Developer report:**
  - Sunpy 0.4.1 has been released.
  - Currently SunPy has problems compiling under Anaconda 2.0. Working on a solution.
  - Travis is now set up to run in parallel, to speed up testing of PRs. Still outstanding issues with Travis timing out when downloading data or querying web-based services like VSO.
  - Discussion of whether offline instances of the Travis tests could be run separately from full ‘online’ test runs. This would provide a baseline level of testing and verification.
  - SunPy 0.5 was delayed slightly. Partly motivated by a desire to wait for AstroPy 0.4. Also some 0.5 issues still outstanding. Desire to get GOES Temperature and Emission Measure code into 0.5, along with AIA_PREP functionality. Lightcurve refactor, astropy quantities and WCS likely to be 0.6.

- Discussion of WCS SEP postponed until a later date.

- SunPy.org data domain is now set up. This enables us to host demo data files.

**Meeting ends.**
