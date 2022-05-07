### Date of Meeting

21 February 2018

### Attendance

- **Present: David, Stuart, Juan, Steve, Monica, Sabrina, Jack, Kevin, Russell**
- **Absent: Albert**

### Agenda

1. Releases update
2. GSOC update
3. SPD committee update
4. NumFOCUS survey about shared infrastructure
5. IRISPy - news regarding relations with IRIS team?
6. Definition and process for affiliated packages (including provisional status)

### Meeting Notes

**Topic 1:**

- 2 new releases: 0.8.4 & 0.8.3
  - 0.8.4 required for AstroPy compatibility
  - 0.8.3 does not currently work with AstroPy due to an issue with a bug fix

- In progress: 0.9 & 1.0
  - 0.9 includes change from current library concerning VSO interaction & will include a revised JSOC client
  - 1.0 deletes Python 2 support and uses AstroPy time object instead of date time object
    - <http://docs.astropy.org/en/stable/time/>

New VSO/SunPy liaison

**Topic 2:**

- GSOC progressing well
  - Currently 5 SunPy projects; open to more
    - <http://openastronomy.org/gsoc/gsoc2018/#/projects>
  - Looking for more mentors
    - <https://google.github.io/gsocguides/mentor>
    - <https://github.com/OpenAstronomy/GSoC/blob/master/application_students.md>
  - Tutorials:
    - <http://openastronomy.org/gsoc/gsoc2018/#/projects?project=astropy_learn_website>

**Topic 3:**

- SPD committee agenda item:
  - Jack will present request to SPD committee at upcoming TESS meeting

- TESS presentations:
  - SunPy poster submitted to TESS meeting via Andrew Inglis and Jack
  - Python NDCubed poster submitted by Danny Ryan

**Topic 4:**

- NumFOCUS survey
  - Questions about what support is needed from NumFOCUS (e.g., web hosting)
  - Discussion about possibly requesting support for FIDO upgrades
  - <https://www.surveymonkey.com/r/shared_infrastructure>

**Topic 5:**

- IRISPy talks ongoing
  - merging of parallel IRIS and SunPy efforts led to development of splinter NDCubed effort led by Danny Ryan and Stuart
  - GUI QuickLook tool guidance being managed by Stuart
  - NDCubed is a generic tool that will be merged into core package
  - IRISPy is not far enough along yet to be an affiliated package

**Topic 6:**

- Affiliated package (AP) management discussion
  - discussion over instrument specific packages
    - core packages built to work on already calibrated with minimal processing
    - affiliated instrument packages handle data nuances
    - <https://github.com/sunpy/sunpy-SEP/blob/master/SEP-0004.md>
  - qualifications to be listed as an AP need to be delineated
    - tests/documentation/use of available functions
    - set of enforceable standards needed
    - using AstroPy experience as a foundation
      - official registry
      - tiers: provisional, accepted[, sponsored/branded]
      - light code review process
      - <http://www.astropy.org/affiliated/>
      - <https://github.com/ejeschke/ginga/issues/555>
  - purpose of APs to not duplicate code, to get widespread use, and to work together for the positive evolution of the tools
    - build with core library
  - implementation more difficult than expected based on IRISPy experience (e.g. GitHub use, ownership issues)
  - voting process for accepting APs under review, possibly separate from the board

**AOB**
