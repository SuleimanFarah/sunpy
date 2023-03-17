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
    - [Refactor player.py](https://github.com/mps-youtube/mps-youtube/pull/753) (Large scale refractor to make  player object-oriented)
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

I have worked on some independent projects too, mainly in Python.

- [anime-downloader](https://github.com/vn-ki/anime-downloader) (Python)
- [YoutubePlayer](https://github.com/vn-ki/YoutubePlayer) (Python)
- [Debtman](https://github.com/vn-ki/debt-man-pwa) (Progressive Web App using ionic3)
- [Continue on PC](https://github.com/vn-ki/ContinueOnPC) (Android app)

I believe this project suites my current knowledge of Python and I am sure that I will be able to complete it in *time*.

#### Interest in OpenAstronomy

In a Python book I read (Learn Python The Hard Way), the author [said](https://learnpythonthehardway.org/book/advice.html),

> "People who can code in the world of technology companies are a dime a dozen and get no respect. People who can code in biology, medicine, government, sociology, physics, history, and mathematics are respected and can do amazing things to advance those disciplines."

Of course, I did not follow this advice (because of immense interest in computer science) but I promised myself that I will do my best to help people in these fields. At this point, I have enough knowledge to start doing this and I want SunPy to be my first venture into this world.

#### Note

> In the below sections,

1. `astropy.time` means `astro.time` module which includes `Time`, `TimeDelta` etc.
2. `astropy.Time` or simply `Time` means `astropy.time.Time`
3. `astropy.TimeDelta` or simply `TimeDelta` means `astropy.time.TimeDelta`

# Synopsis

`parse_time` is a very old function in SunPy. It serves a lot of purpose from parsing time strings to parsing `numpy.datetime64`. The function evolved overtime to become a very complex function. But `datetime` comes with its quirks. It cannot handle leap seconds. In any case, switching to `astropy.Time` gives more control to the user. Some advantages of `astropy.Time` are mentioned in the introduction to astropy Time [documentation](http://docs.astropy.org/en/stable/time/#introduction) (Quoting the docs, *Time object maintains sub-nanosecond precision* and *supporting time scales (e.g. UTC, TAI, UT1, TDB) and time representations (e.g. JD, MJD, ISO 8601) that are used in astronomy*). `astropy.Time` would be easier to work with on the user side and is better than `datetime` with respect to astronomy.

`parse_time` is extensively used in sunpy. It is used mainly in `sunpy.net`. So any changes to `parse_time` would affect a lot of sunpy. Ignoring the changes to examples and documentation, the following parts of sunpy would require changes.

- `sunpy.net`: This module would require the most change.
- `sunpy.timeseries`
- `sunpy.instr`:  Uses a lot of `datetime`.
- Some other modules (`coordinates`, `database`, ...) which use `parse_time` to a small extent.

Changes to the examples would be mostly confined to modifying them for `astropy.Time` instead of `datetime` and `astropy.TimeDelta` instead of `datetime.timedelta`.

The modules `net` and `instr` uses `TimeRange`. `TimeRange.start` and `TimeRange.end` are initialized by `parse_time`. This would mean that the switch to `astropy.Time` would affect how `TimeRange` will be used.

## Tasks

- **Planned contributions to astropy**
  - Format class for `numpy.datetime64`: This would add support for `numpy.datetime64` as input and output.([Link](https://github.com/astropy/astropy/issues/4982) to the issue on astropy)

  - Fix `to_datetime` in `astropy.TimeDelta`: Right now, `to_datetime` in `TimeDelta` does not work as expected. ([Link](https://github.com/astropy/astropy/issues/4982) to the issue on astropy.)

  - Formatting of time: `Time` does not provide a good way to format it now (like `strftime` for `datetime`). I would add a similar function based on the comments from community. ([Link](https://github.com/astropy/astropy/pull/7323) to the PR on astropy)

- **Changes to `parse_time`**
  - String parsing: Right now my plan is to use   `astropy.Time` primarily and fallback to the current  regex when `astropy.Time` can't parse the   `time_string`. But however this is open for   discussion and may change once the coding starts  based on the comments from mentors. Parsing strings   is a very powerful feature of `parse_time` now. It  supports a large variety of strings. So it makes  sense that this feature stays.

  - The following table demonstrates how we would deal with the rest of `time_string` types.

| Format         | Possible solution with  `astropy.Time` |
| :------------- | :------------------- |
| ts = (1966, 2, 3)        | `Time('{}-{}-{}'.format(*ts))` |
| ts = 765548612.0, 'utime' | `Time(ts,  format='utime')` Using custom format in  `sunpy.time.utime` |
| ts = pandas.Timestamp() |`Time(ts)`  |
| ts = pandas.Series() | `np.array([Time(v) for v in ts])` or `Time([v for v in ts])` |
| pandas.DatetimeIndex() | `np.array([Time(v) for v in ts]) Time([v for v in ts])` |
| np.datetime64('2005-02-01T00') | See gist below|
| np.arange('2005-02', '2005-03', dtype='datetime64[D]') | See gist below |
| np.arange('2005-02-01T00', '2005-02-01T10', dtype='datetime64') | See gist below |
| ts = astropy.time.Time | `ts` |
| 'now' | `Time.now()` |
| ts = datetime() | `Time(ts)` |
| `ts = datetime.date` | `Time(ts.isoformat())` |

  NOTE: Conversion of `np.datetime64` to `astropy.Time`   can be accomplished by [this  gist](https://gist.github.com/vn-ki/01b6d32b7a255e796ea54e8b882c8512) based on the issue astropy/#6428. The current implementation of parse_time cannot convert np.datetime64(‘2012-06-18T02:00:05.453000000-0400'). This gist gives `parse_time` the ability to convert the mentioned `np.datetime64`s.

  Before returning `Time`, `.replicate` function could be called on it so that we get a uniform format for all the returned `Time` objects.
  We could also set the scale as we need (utc, tai etc.).
  Ex: `return Time(..., format='unix', scale='utc').replicate('iso')`

- **Handling of timedelta**

  See [this gist](https://gist.github.com/vn-ki/a0bd705673cc17d86c344c60840fa31d) for the complete implementation.
  I would make a new function `get_timedelta` to return `TimeDelta`. This would simplify the initialization of `TimeDelta` and could be used by users too.

- Changes to other modules

    Modules are mentioned in summary above. The   change mostly include changing them to use   `astropy.Time` instead of `datetime`. This is  summed up above in the first point of this  section.

- **Equivalents to `datetime` functions**

  - `datetime.strftime` could be replaced with a [custom format](http://docs.astropy.org/en/stable/time/#writing-a-custom-format) of `Time` or the following code can be used (if contributions to astropy don't make it for some reason)

  ```python
  def strftime(time, format_string):
      time.strftime(format_string, time.gmtime(time.unix))

  strftime(Time.now(), <some format string>)
  ```

  - `datetime.utcfromtimestamp(ts)` can be replaced by `Time(ts, format='unix')`.

  - `datetime.fromtimestamp` returns the local datetime. To do this with `astropy.Time`.

  ```python
  def localtime_from_timestamp(ts):
      tz_str = time.strftime('%z', time.localtime())
      tz = u.hour*int(tz_str[1:3])+u.minute*int(tz_str[3:])
      return Time(ts, format='unix') + TimeDelta(+tz if tz_str[0]=='+' else -tz)

  localtime_from_timestamp(1371479761)
  ```

  - `datetime.strptime` will be changed to the following function.

  ```python
  def strptime(time_string, format_string):
      time_tuple = time.strptime(time_string, format_string)
      return Time("{}-{}-{}T{}:{}:{}".format(*time_tuple))

  strptime("30 Nov 00", "%d %b %y")
  ```

  NOTE: The above mentioned is open for discussion and will be decided during community bonding period.

# Project Plan

- **Community Bonding Period (April 23 - May 14)**

  - I have exams from april 20th to 28th. I will be inactive during that week. Excluding that week most of my time will go into learning more about `parse_time` and usage of `datetime` in SunPy.

  - I would also try to port some parts of the code to use `astropy.Time` using `sunpy.time._astropy_time` so as to get an idea of what are the consequences of changing to `astropy.Time`. This function will be removed once the project is complete.

  - During this time I would also work on some contributions towards astropy( Possibly *Improvement to `TimeDelta`* and *Format class for numpy.datetime64* because these would affect the way we go about changing `parse_time`). I won't get them merged, but most of the work would be done during this period.

  - During the last week I will finish of the work on [#2408](https://github.com/sunpy/sunpy/pull/2408) (Refactor parse_time) and get it merged. This will be the base for the rest of the work on `parse_time`.

- **Phase 1 (May 15 - June 17)**

  - **May 15 - June 3**

    - Make `parse_time` use `astropy.time`. Most of the stuff here should be straight forward. But there are some subtle differences to be inspected here. For example, only dates of the format `yyyy-mm-dd` is supported by `astropy.Time` where `parse_time` can parse both `yyyy-mm-dd` and `yyyy/mm/dd`.

    - Finally, finish transition of `sunpy.time` to use `astropy.time`.

    - If everything goes well and `parse_time` porting ends sooner than expected, then the tests and docs will be written in this period giving more time for porting modules.

  - **May 28 - June 10**

    - Write the necessary tests and documentation for the new `parse_time`.

    - Research on implementation of astropy tasks.

  - **June 11 - June 17**

    - Change `sunpy.coordinates` and `sunpy.database` to use `astropy.time`.

    - Research on how to fix `to_datetime` in `astropy.TimeDelta` and open a WIP PR in astropy repo.

- ***Evaluation 1 (June 11 - June 15)***

- **Phase 2 (June 18 - July 15)**

  - Change `sunpy.net`, `sunpy.instr`, and `sunpy.timeseries` to use `astropy.time`. Tests will be rewritten simultaneously.

  - `net` contains the most extensive use of `parse_time`, so this will take the most time.

  - Work on providing a formatting interface for `astropy.Time`. I have already opened a PR ([link](https://github.com/astropy/astropy/pull/7323)) in AstroPy GitHub repo. This would be the most important addition to astropy Time in connection with this project as all calls to `datetime.strftime` can be replaced with this.

- ***Evaluation 2 (July 9 - July 13)***

- **Phase 3 (July 16 - August 14)**
  - Work on getting `numpy.datetime64` to work with `astropy.Time`. (The implementation would be similar to the gist mentioned in parse_time section)

  - Finish up work on formatting interface of `astropy.Time`.
  - Finish up `to_datetime` fix of `astropy.TimeDelta`.
  - Finish up the transition.
  - Write necessary documentation. Rewrite examples to reflect the changes. Write a migratory guide for existing users.
  - A week is buffer time in case some problems crop up.

  NOTE: AstroPy 3.1 will be releasing in November, so there is enough time to get all PRs merged. Though I will try my best to get them merged before the final evaluation.

### Schedule Availability

As I mentioned before, I will have exams from April 20th to April 28th (Fortunately this is during community bonding period and can be easily covered).

During the coding period I don't have any other commitment than GSoC. Thus I can easily give more than 40 hours per week for the project.

My summer vacations end on July 20th (3 weeks before the deadline). Even after the vacations I am sure I can dedicate ~30 hours for the project (My classes account for ~24 hour a week).

## GSoC

### Have you participated previously in GSoC? When? Under which project?

No, I have **not** participated in GSoC before. This is the first time I am participating in GSoC.

### Are you also applying to other projects?

**No** ,This is the **only project** and **SunPy is the only organization** that I am applying for.

### Commitments

I don't have any other internship or work during this summer. I have no plans for any vacations either.

### Eligibility

Yes, I am eligible to receive payments from Google.
