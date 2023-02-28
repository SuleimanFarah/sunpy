### Date of Meeting

5th May 2014

### Agenda

- SEP-0004 Quantities (ready for vote?)
- Discussion on SEP-0003 Light curve factory
- Need for other SEPs (e.g. meta refactor)
- Discussion on voting by proxy (Considerations include establishing quorum, verification of proxy status, dispute resolution, etc.)
- SOCIS 2014

- Lead Developer Report
  - sub-domains (hosting)
  - PR acceptance
  - GSOC 2014

### Attendance

**Present**: Steven Christe (Chair), David Perez-Suarez (Vice-Chair), Andrew Inglis (Secretary), Albert Shih, Stuart Mumford, Jack Ireland, Tom Robitaille, Juan Carloz Martinez Oliveros

**Absent**: Russell Hewett

### Meeting notes

- **Discussion of SEP-0004**, regarding the use of **AstroPy Quantities**.
- The SEP states that classes and functions involving physical units must accept only Quantities. If a Quantity is not given, the function will give an error. Exceptions are allowed in cases where Quantities adversely affect performance, or where Quantities are incompatible with other dependencies (e.g. Scipy).
- Questions as to how Quantities would relate to time data, e.g. how is parse_time or TimeRange affected by this. Consensus that there is no strong reason to change the time functionality, since it is already unit aware through datetime.
- Decision needed on how to document the exceptions where Quantities are not used. Otherwise it may be forgotten whether the omission of Quantities was intentional.
- How does Quantities deal with variables such as DN in AIA images, which are not real physical quantities/units? Likely that these would not be Quantities.
- **Consensus** to drop the requirement to return output quantities as SI units in SEP-0004

- **Discussion of SEP-0003**, regarding the **Lightcurve Factory** postponed until a future meeting.

- The issue of **proxy voting** is raised. Currently no procedure for this within SunPy.
  - As SunPy becomes more international, this will become a more important issue, as Board members will inevitably be absent.
  - One possibility would be to arrange offline votes. The system would involve specifying a specific time window (e.g. 1 day) for Board members to cast their vote (e.g. by email, doodle poll).

- Vote is held on whether to allow proxy voting. Result is **7-0 against allowing proxies, with 1 abstention**.

- Vote is held on whether voting by email/remote means should be allowed in exceptional cases. ‘Exceptional circumstances' would have to be agreed at a prior Board meeting. **Result is 7-0 in favour, with 1 abstention**.

**Albert Shih** departed the meeting.

**Juan Carlos Martinez Oliveros** departed the meeting

### Other business

- SunPy was accepted for ESA Summer of Code in Space for 2014
- Work is ongoing to transfer full control of Sunpy.org to the SunPy organization - Dr Alex Young, NASA/GSFC is the current owner for historical reasons.
- Hosting of SunPy demo data: Stuart Mumford has a current subscription to www.servage.net that may be used for this purpose.
- GSOC students in the introductory phase. Have 4 students this year.

- Next meeting is provisionally **scheduled for 9th June 2014 at 17:00 GMT**.

**Meeting ends**.
