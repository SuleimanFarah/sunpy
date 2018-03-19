# Project Proposal
## Project: Transition to Astropy Time in SunPy
- Name: Vishnunarayan K I
- Organisation: SunPy

#### Personal Info

- Time zone: UTC+05:30
- GitHub handle: [vn-ki](https://github.com/vn-ki)
- Link to sample code as pull requests: [#2559](https://github.com/sunpy/sunpy/pull/2559)

#### Education

- University: [Indian Institute of Technology, Indore](http://iiti.ac.in/)
- Major: Computer Science
- Current Year: 1st year

###### Open Source background and Programming experience

- Programming Languages: Python, C++, C, JavaScript, Java(Basic knowledge)
- Contributions to other repos:
  - mps-youtube:
    - [Refactor player.py](https://github.com/mps-youtube/mps-youtube/pull/753) (Large scale refractor to make player object-oriented)
    - [Show metadata..](https://github.com/mps-youtube/mps-youtube/pull/739)
    - [Add tab completion...](https://github.com/mps-youtube/mps-youtube/pull/789)
    - [Fix json error...](https://github.com/mps-youtube/mps-youtube/pull/785)
    - [Change setup.py...](https://github.com/mps-youtube/mps-youtube/pull/782)
    - [Fix cyclic import](https://github.com/mps-youtube/mps-youtube/pull/807)
  - pafy:
    - [Add support for youtube channels](https://github.com/mps-youtube/pafy/pull/196)
    - [Add indexing for playlist](https://github.com/mps-youtube/pafy/pull/195)
    - [Fix throttling...](https://github.com/mps-youtube/pafy/pull/203)
  - spotify-downloader:
    - [Switch to youtube API](https://github.com/ritiek/spotify-downloader/pull/191)
    - [Beautify videotime...](https://github.com/ritiek/spotify-downloader/pull/217)
    - [Filter items other ...](https://github.com/ritiek/spotify-downloader/pull/249)
  - [unified-social-api[WIP]](https://github.com/kanishkarj/unified-social-api)


I have worked on some independent projects too, mainly in python.  
- [anime-downloader](https://github.com/vn-ki/anime-downloader) (Python)
- [YoutubePlayer](https://github.com/vn-ki/YoutubePlayer) (Python)
- [Debtman](https://github.com/vn-ki/debt-man-pwa) (Progressive Web App using ionic3)
- [Continue on PC](https://github.com/vn-ki/ContinueOnPC) (Android app)

I belive this project suites my current knowledge of python and I am sure that I will be able to complete it in *time*.

#### Interest in OpenAstronomy

In a python book I read (Learn Python The Hard Way), the author [said](https://learnpythonthehardway.org/book/advice.html),

> "People who can code in the world of technology companies are a dime a dozen and get no respect. People who can code in biology, medicine, government, sociology, physics, history, and mathematics are respected and can do amazing things to advance those disciplines."

Of course, I did not follow this advice (because of immense interest in computer science) but I promised myself that I will do my best to help people in these fields. At this point, I have enough knowledge to start doing this and I want SunPy to be my first venture into this world.

# Synopsis

`parse_time` is a very old function in sunpy. It serves a lot of purpose from parsing time strings to parsing `numpy.datetime64`. The function evolved overtime to become a very complex function. But `datetime` comes with its quirks. It cannot handle leap seconds. In any case, switching to `astropy.Time` gives more control to the user and simplifies the current `parse_time` function. Some advantages of `astropy.Time` are mentioned in the introduction to astropy Time [documentation](http://docs.astropy.org/en/stable/time/#introduction) (Quoting the docs, *Time object maintains sub-nanosecond precision* and *supporting time scales (e.g. UTC, TAI, UT1, TDB) and time representations (e.g. JD, MJD, ISO 8601) that are used in astronomy* ). `astropy.Time` would be easier to work with on the user side and is better than `datetime` with respect to astronomy.

`parse_time` is extensively used in sunpy. It is used mainly in `sunpy.net`. So any changes to `parse_time` would affect a lot of sunpy. Ignoring the changes to examples and documentation, the following parts of sunpy would require changes.

- `sunpy.net`: This module would require the most change.
- `sunpy.timeseries`
- `sunpy.instr`:  Uses a lot of `datetime`.
- Some other modules (`coordinates`, `database`, ...) which use `parse_time` to a small extent.

Changes to the examples would be confined to modifying them for `astropy.Time` instead of `datetime` and `astropy.TimeDelta` instead of `datetime.timedelta`.

## Tasks

- Equivalents to `datetime` functions

  - `datetime.strftime` could be replaced with a [custom format](http://docs.astropy.org/en/stable/time/#writing-a-custom-format) of `Time` ([Link](https://github.com/astropy/astropy/issues/7309) to tracking issue of adding this feature directly to `Time`) or `time.strftime(format_string, time.gmtime(Time.unix))`.

  - Creating `Time` from timestamps can accomplished using either a custom format or converting to datetime first.

  - `datetime.strptime` will be changed to `Time(datetime.strptime())`.

  NOTE: The above mentioned is open for discussion and will be decided during community bonding period.

- Equivalent of `datetime.timedelta`

  I would make a function `get_timedelta(**kwargs)` to return `astropy.TimeDelta`. This is because `astropy.TimeDelta` does not accept seconds, minutes etc.

- **Changes to `parse_time`**
  - String parsing: Right now my plan is to use   `astropy.Time` primarily and fallback to the current  regex when `astropy.Time` can't parse the   `time_string`. But however this is open for   discussion and may change once the coding starts  based on the comments from mentors. Parsing strings   is a very powerful feature of `parse_time` now. It  supports a large variety of strings. So it makes  sense that this feature stays.

| Format         | Possible solution with  `astropy.Time` |
| :------------- | :------------------- |
| ts = (1966, 2, 3)        | `Time('{}-{}-{}'.format(*t))` |  
| ts = 765548612.0, 'utime' | `Time(ts,  format='utime')` Using custom format in  `sunpy.time.utime` |  
| ts = pandas.Timestamp() |`Time(pandas.Timestamp)`  |  
| ts = pandas.Series() | `np.array([Time(v) for vin  ts])` |  
| pandas.DatetimeIndex() | `np.array([Time(v) forv   in ts])` |  
| np.datetime64('2005-02-01T00') | See Note below|  
| np.arange('2005-02') | See Note below |  
| np.arange('2005-02-01T00') | See Note below |  
| ts = astropy.time.Time | `ts` |  
| 'now' | `Time.now()` |  

  NOTE: Conversion of `np.datetime64` to `astropy.Time`   can be accomplished by [this  comment](https://github.com/astropy/astropy/issues/642  8#issuecomment-362224248) in astropy/#6428.

- Changes to other modules

    Modules are mentioned in summary above. The   change mostly include changing them to use   `astropy.Time` instead of `datetime`. This is  summed up above in the first point of this  section.

# Project Plan

- Pre community bonding Period ( - April 23)

  I would familiarize myself with the code base. I would use this time to the fullest so that I can make up for the lost week during community bonding period and I can concentrate on `time` related stuff during community bonding period.

- Community Bonding Period (April 23 - May 14)

  I have exams from april 20th to 28th. I will be inactive during that week. Excluding that week most of my time will go into learning more about `parse_time` and usage of `datetime` in sunpy.

  I would also try to port some parts (maybe `time.timerange`) of the code to use `astropy.Time` using `sunpy.time._astropy_time` so as to get an idea of what are the consequences of changing to `astropy.Time`. This function will be removed once the project is complete.  

  During the last week I will finish of the work on [#2408](https://github.com/sunpy/sunpy/pull/2408) (Refactor parse_time) and get it merged.

- Phase 1 (May 15 - June 17)

  - May 15 - June 3

    Make `parse_time` use `astropy.time`. Most of the stuff here should be straight forward. But there are some subtle differences to be inspected here. For example, only dates of the format `yyyy-mm-dd` is supported by `astropy.Time` where `parse_time` can parse both `yyyy-mm-dd` and `yyyy/mm/dd`.

    Finally, finish transition of `sunpy.time` to use `astropy.time`.

    If everything goes well and `parse_time` porting ends sooner than expected, then the tests and docs will be written in this period giving more time for porting modules.

  - May 28 - June 10

    Write the necessary tests and documentation for the new `parse_time`.

  - June 11 - June 17

    Change `sunpy.coordinates` and `sunpy.database` to use `astropy.time`.

- *Evaluation 1 (June 11 - June 15)*

- Phase 2 (June 18 - July 15)

  - Change `sunpy.net`, `sunpy.instr`, and `sunpy.timeseries` to use `astropy.time`. Tests will be rewritten simultaneously.

  - `net` contains the most extensive use of `parse_time`, so this will take the most time.


- *Evaluation 2 (July 9 - July 13)*

- Phase 3 (July 16 - August 14)

  - Finish up the transition.
  - Write necessary documentation. Rewrite examples to reflect the changes. Write a migratory guide for existing users.
  - A week is buffer time in case some problems crop up.

### Schedule Availability

As I mentioned before, I will have exams from april 20th to april 28th (Fortunately this is during community bonding period and can be easily covered).

During the coding period I don't have any other commitment than GSoC. Thus I can easily give more than 40 hours per week for the project.

My summer vacations end on July 20th (3 weeks before the deadline). Even after the vacations I am sure I can dedicate ~40 hours for the project (My classes account for ~24 hour a week).
