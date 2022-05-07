### Date of Meeting

19th September 2014

### Agenda

- Lead Developer Report
- SEP review

### Attendance

**Present**: Steven Christe (Chair), Andrew Inglis (Secretary), Albert Shih, Stuart Mumford, Thomas Robitaille, Russel Hewett,  Juan Carlos Martinez Oliveros, Jack Ireland (late)

**Absent:** David Perez-Suarez (Vice-chair

### Meeting Notes

- **Stuart** gave a brief report covering latest SunPy updates. Google summer of code has concluded and was very successful. SIPwork also resulted in a lot of interest in and positive feedback about SunPy.

- Discussion of SEP 0005 - Coordinates.
  - Possible that the SkyCoord class may be tweaked by AstroPy in the future, but the rest of the package should be relatively stable. **Steven** suggested that the name SkyCoord may be misleading.
  - Transformation of the observer (e.g. from STEREO to SDO point of view) is not implemented yet, but should be possible in the current framework. This will be crucial for upcoming solar missions, like Solar Orbiter and Solar Probe Plus. According to **Thomas** there are also plans in Astropy for dealing with this by defining an Observer Location class. Some discussion of what the Observer class must contain.

- **Albert** departed the meeting.

- **Juan** followed up from the last meeting, thinking about what would make SunPy more attractive to new users. Juan said that most functions were now available in SunPy, but suggested constructing a function that can convert SSW maps to SunPy Maps. Related to that, **Steven** suggested creating a package called pySSW, which would contain such helper/converter functions. This package would be separate from SunPy but would depend on SunPy.

- Vote on whether to vote on the Coordinates SEP. **The board voted (7-0 in favour) to allow a special vote on this SEP by correspondence**. A time window of at least one week must be provided for voting to take place, as defined in SEP-0002.

- The next board meeting is scheduled for **Friday 17th October**.
