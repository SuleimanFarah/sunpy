# Metadata searches using Fido

#### Mentors: @cadair, @nabobalis

## Personal Information

- Name: Abhijeet Manhas

- Timezone: UTC+05:30

- Github: [abhijeetmanhas](https://github.com/abhijeetmanhas)

- Email: abhijeetmanhas720@gmail.com

- Riot: [@abhijeetmanhas:matrix.org](https://riot.im/app/#/user/@abhijeetmanhas:matrix.org)

- Blog: [@abhijeetmanhas720](https://medium.com/@abhijeetmanhas720)

- Location: Mandi, India

## Education

- University: [Indian Institute of Technology Mandi](http://iitmandi.ac.in)

- Major: Computer Science and Engineering

- Current year: Second year

- Expected Graduation: July 2022

- Degree: Bachelor of Technology

## Background

I have been interested in Astronomy since my school days. I participated in various National level competitions like the *National Standard Examination in Astronomy* and qualified the state merit. After completing high school, I joined the Indian Institute of Technology for undergraduate studies in Computer Science. In June 2019, I was selected as the coordinator of **Space Technology and Astronomy Cell** (STAC) in IIT Mandi. I got to learn and engage in a lot of astrophysics and python owing to the open-source culture established by our seniors in the STAC and Programming Club of IIT Mandi. I actively coordinated in organizing **AstraX** (the annual Astro-meet) which witnessed lead developers of two astropy affiliated packages as keynote speakers. I also gave a talk on *how to be an astronomer using python* in a **Python Software Foundation** sponsored event in Mandi, India followed by a hands-on session.

## Work done in SunPy

<table>
    <tr>
    <td><b>S. no.</b></td>
    <td><b>Pull Requests</b></td>
    <td><b>Status</b></td>
    </tr>
    <tr>
    <td>1</td>
    <td>Created BaseHeliographic class <a href="https://github.com/sunpy/sunpy/pull/3595">#3595</a></td>
    <td>Merged</td>
    </tr>
    <tr>
    <td>2</td>
    <td>Removed astropy helpers from various files <a href="https://github.com/sunpy/sunpy/pull/3676">#3676</a>
    </td>
    <td>Merged</td>
    </tr>
    <tr>
    <td>3</td>
    <td>Removed old SJI classes <a href="https://github.com/sunpy/sunraster/pull/123">#123</a></td>
    <td>Merged</td>
    </tr>
    <tr>
    <td>4</td>
    <td>Implemented Groundclients for Fido <a href="https://github.com/sunpy/sunpy/pull/3763">#3763</a></td>
    <td>Open (WIP)</td>
    </tr>
    <tr>
    <td>5</td>
    <td>Implemented ACE Clients <a href="https://github.com/sunpy/sunpy/pull/3705">#3705</a></td>
    <td>Open (Approved)</td>
    </tr>
    <tr>
    <td>6</td>
    <td>Implemented _get_time_for_url in GenericClient <a href="https://github.com/sunpy/sunpy/pull/3863">#3863</a></td>
    <td>Open (Approved)</td>
    </tr>
    <tr>
    <td>7</td>
    <td>Fixed deprecationwarning due to vso.attrs <a href="https://github.com/sunpy/sunpy/pull/3813">#3813</a>
    </td>
    <td>Closed</td>
    </tr>
    <tr>
    <td>8</td>
    <td>Implemented VSMClient <a href="https://github.com/sunpy/sunpy/pull/3809">#3809</a></td>
    <td>Open</td>
    </tr>
    <td>9</td>
    <td>Implemented KanzelhoheClient <a href="https://github.com/sunpy/sunpy/pull/3810">#3810</a></td>
    <td>Open</td>
    <tr>
    <td>10</td>
    <td>Implemented Gong and Farside Clients <a href="https://github.com/sunpy/sunpy/pull/3811">#3811</a></td>
    <td>Open (Approved)</td>
    </tr>
    <tr>
    <td>11</td>
    <td>Implemented BBSOClients <a href="https://github.com/sunpy/sunpy/pull/3812">#3812</a></td>
    <td>Open</td>
    </tr>
</table>

## Why this Project?

I started using SunPy last winter; initially for AIA maps in slides for a session. From November I started to interact with the community by joining the riot channel and mailing list. I then explored its issues and tried to work on various submodules out of which sunpy/net seems to be more intriguing for me, I continued some client PRs and by making them compatible with current SunPy’s version, I became familiar with changes undergone by the submodule and how works.
Fido naturally seemed to be an obvious project for me in SunPy after the ideas list were out and I was very excited to go for it.

# The Project Plan

## Synopsis

**Federated internet data obtainer** (Fido) is a very powerful query and fetch interface when it comes to its flexibility and versatility with different types of clients and query attributes. The data archives available at various FTP and HTTP sites mostly offer file-based records accessible easily through time ranges, and Fido evolved to efficiently handle such queries.

This project will be an attempt to refactor the net module by standardizing all client classes and their responses. It will enable Fido to parse metadata queries and allow users to inspect them as well. The project will also attempt to solve download failures with JSOC and VSO as in [Issue #3336](https://github.com/sunpy/sunpy/issues/3336)  and [Issue #3773](https://github.com/sunpy/sunpy/issues/3733) respectively.

This would be followed by writing pytests for various untested functions in the module.
The project will end with easy interpretable documentation of code and gallery examples wherever possible; I will be constantly maintaining my blog as well so please feel free to check it before evaluation!

Breaking down the project into components:-

## 1. Implement Abstract Base Class for responses from all clients

A large part of the task has already been completed as of [PR #3770](https://github.com/sunpy/sunpy/pull/3770) (further Fido Refactoring) which implements ABC for `GenericClient`, `VSOClient`, and `JSOCClient`. I will transition the current response implementations of `HEKClient` and `HECClient` to `BaseQueryResponse` as well.

### 1.1 ABC for HEKClient

Hek `_download` returns a HEKTable as a response which is a customized `astropy.table`. A new class `HEKResponse` inheriting `BaseQueryResponse` is to be made and the `search` will return the response object. Various new methods for operations on HEKTable will be defined in the Response class.

### 1.2 ABC for HECClient (Helio Event Catalogue)

The `time_query` of HEC can be renamed to search for uniformity with other clients. `HECResponse` inheriting BaseQueryResponse will receive a `VOtable` object. The `build_table` method will be responsible for appending all attributes from the table and return response in a more human-readable form.

## 2. Chosen metadata columns in Response tables of DR Clients

The one thing which bugged me while working with sunpy/net was ‘nan’ values in the wavelength column of the response table of DR Clients. This issue was also raised here [#3221](https://github.com/sunpy/sunpy/issues/3321). There really should be a way by which users can decide what columns they want to see in the table.

The way I am thinking to solve it is by making a dictionary `meta_cols` data member of client class with keys as attrs (column name to be shown in the result table) and values. The `build_table` of `ClientResponse` will use meta_cols to make the `Astropy.table.Table`.

The meta_cols values will be filled using helper functions defined within the source client class or to be retrieved from the file name read by Scraper. For example, for `GOESClient` the `get_goes_sat_num()` call  will result in ```meta_cols[‘sat_no’].append(sat_num)```.

This will be of course followed by native and Fido tests for the implementation.

## 3. Fido MetaData only queries for JSOC, HEK and HELIO Clients

These clients generally obtain metadata for the records. Except for the JSOCClient, all do not inherit the `BaseClient` class. In fact, we already have a `search_metadata` function for JSOCClient. The way by which Fido correctly uses the desired client for data retrieval is through the implementation of `_can_handle_query`. This subtask can be done as:-

### 3.1  Make HEC and HEK clients as subclasses of BaseClient

This will also include adding `_can_handle_meta_search` in each subclass to register the attrs which can be handled by the respective client.

### 3.2 Implement `search_metadata` in fido_factory

This will be responsible for dispatching the correct client based on the function`_can_handle_meta_search`. Luckily, the response objects would already have been standardized after task 1. Users will have to pass the arguments say for example:-
```Fido.search_metadata(a.EventType('FL'), a.Time(start,end))``` and Fido will know to use HEKClient for matching records through _can_handle_meta_search registration.
This will return a modified dictionary of metadata and the `__repr__` function for this dictionary will ensure the output is human-readable.
<!--
### 3.3 Standardizations for HelioViewer*

It would be slightly typical to standardize the  `HelioViewerClient` since it has four types of searchers’ namely `get_closet_image`, `get_jp2_header` returning dict and `download_jp2`, `download_png` returning a file url.
 For those returning dict, a similar API to `meta_cols` shall be implemented allowing a few default columns and user-chosen columns. The `attrs` passed in the query will be used for meta only response for those which return a url. To increase interpretability, Users can provide options to display Sunpy maps in the response table also.
-->

## 4. Query inspection and post search Filtering

 The feature worked for VSO till v0.9.9 but broke when v1.0.0 was released. After knowing the bad commit, first I’ll correct it for VSO and then add a `search` method to query response objects of all clients.

### 4.1 Implement filter_results for net attrs

`_filter_results` and decorators for this function registration (`@_filter_results.register`) for all query operators shall be implemented in `~sunpy.net.attrs` . Attrs for JSOC will inherit this functionality with some JSOC specific tweaks to query filtering.

### 4.2 Filtering using Fido

Before implementing this, first I’ll register QR objects based on the client by which they are used as raised in [issue #3732](https://github.com/sunpy/sunpy/issues/3732). Then add a search function to `UnifiedResponse` class of `fido_factory.py` similar to the way explained for the rest clients.

<hr>

## Deliverables

- ABC for query response objects for HEK and HELIO Clients.

- `meta_cols` implementation in DR Clients.

- Functions for Metadata only searches for HEK and HELIO clients.

- API for Post search query for HEK, HELIO, VSO and dataretriever clients.

- Register QR objects based on clients.

- Latest parfive integration for fixing proxy issues with Fido.

- Deal with VSO issues while fetching queries.

- Adding Cdf reader to sunpy.

- Integration of ACE Clients and GroundClients to sunpy/net.

- Documentation of the above code and necessary Gallery examples.

## Timeline

### Community bonding period (May 4 - June 1)

I'll spend this time interacting with mentors and the community and discuss the strategy to solve download fails for special cases of queries. I will also raise issues or feature requests as I explore the module.

The community bonding period is almost one month this time, so I would spend some of it in completing the changes directed for my open Pull Requests. The tasks I will work upon:-

- Implement a `.cdf` file reader in sunpy. Many files accessible through **CDAWeb** are mostly of this extension so it would be handy to have such reader in `~sunpy.util` or `~sunpy.io`; if in future such files are to be independently read by SunPy. Luckily there is also a python library for it ([cdflib](https://github.com/MAVENSDC/cdflib)).

- Get all [groundclients PRs](https://github.com/sunpy/sunpy/pull/3763) complete and reviewed by maintainers and the same for [ACE Clients](https://github.com/sunpy/sunpy/pull/3705/).

### Week 1 (June 1 - June 8)

Make clients know the time-ranges from the urls itself instead of an extra function [Issue 3715](https://github.com/sunpy/sunpy/issues/3715).

### Week 2 - Week 3 (June 8 - June 22)

Implementing ABC for HEKClient and HECClient responses.

### Week 4 (June 22 - June 29)

Registration of Query Response objects based on clients they are used by.

___

#### EVALUATION 1 (June 29 - July 3)

___

### Week 5 (June 29 - July 6)

Make HEC, HELIO and HEK clients as subclasses of BaseClient

### Week 6 - Week 7 (July 6- July 20)

Implement `meta_cols` for DR Clients for query-specific columns in the response table.

### Week 8 (July 20 - july 27)

Make `GOESClient` able to know the satellite number without being hard-coded date-wise using `scraper` ([Issue #3337](https://github.com/sunpy/sunpy/issues/3337)).
___

#### EVALUATION 2 (June 29 - July 3)

___

### Week 9 (July 27 - August 3)

Implement post-search queries for all clients and through Fido.

### Week 10 - Week 11 (August 3 - August 17)

- Add `can_handle_meta_search` function in clients to make fido know which client to use for meta searching.

- Implement `search_metadata` for meta-specific clients and in Fido.

### Week 12 (August 17 - August 24)

- Solve issues about download failures using VSO and JSOC.

- Complete documentation and add some gallery examples wherever required.

### Week 13 (August 24  - August 31)

Final touchups (if left) to the deliverables.
___

#### FINAL EVALUATIONS (August 24 - August 31)

___

## Open-source Background and Experience

- Programming Languages: Python, C++, C, Javascript.

- Quite familiar with OOP in python, pytest, args and kwargs, decorators, etc.

- OS: Linux(Ubuntu) and Windows 10. Experience with both terminal and powershell.

- **Contributions to SunPy**

  - I have a total of [10 Pull requests in Sunpy (6 net labelled), with 2 merged,1 approved and 1 WIP.](https://github.com/sunpy/sunpy/pulls?q=is%3Apr+author%3Aabhijeetmanhas)

  - [Raised 4 issues in sunpy.](https://github.com/sunpy/sunpy/issues?q=is%3Aissue+author%3Aabhijeetmanhas+)

  - [One merged PR in sunpy/sunraster.](https://github.com/sunpy/sunraster/pull/123)
  - I have been contributing to sunpy since the last three months and have been quite active in the community. Many of my PRs were oriented towards redesigning dataretriever clients and suitable tests for them including optimizations. Working majorly on them made me very familiar with the workflow of `~sunpy.net` submodule and Fido.

- Contribution in EinsteinPy and raised 3 issues in glue-solar and glue-astronomy as well.

- Lead maintainer of [Space Technology and Astronomy Cell](https://github.com/STAC-IITMandi), IIT Mandi and responsible for maintaining many astrophysics oriented projects. Major ones include:-

  - [Astrocker: Dockerizing all astropy affiliated packages on any system at once](https://github.com/STAC-IITMandi/astrocker)

  - [activities.iitmandi.co.in](https://activities.iitmandi.co.in) (dynamic site for event scheduling in Django)

  - Exoplanet Detection by scraping data from K2 archive

  - SATLABS: Source code for blimp satellite for weather data collection

  - Pseudo-Simulation of n-bodies in Newtonian gravity

- I have done a lot of mini-projects dealing with web-scraping using Selenium python such as [automatic Whatsapp birthday wisher.](https://github.com/abhijeetmanhas/hpybday_shreyasb)

## Me and GSoC

### Have you participated previously in GSoC? When? Under which project?

I haven’t participated in GSoC before.

### Are you applying to other projects?

I haven’t applied to any other project and focused on Fido.

### Commitments?

I don’t have any internships or other projects to do in summer. I won’t be even having classes in June and July, so I can fully commit my time to the project. I can easily commit 35-45 hours a week to my project.
For one week in June, I’ll be busy with my end-sem examinations.
I will love to contribute to SunPy even after the GSoC period. Integrating the HESPE data archive will be my next objective after the summer of code.

### Eligibility?

Yes, I’m eligible to receive payments from Google.
