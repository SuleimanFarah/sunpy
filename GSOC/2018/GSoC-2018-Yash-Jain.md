## Organization : OpenAstronomy

## Sub-Organization : SunPy

---

### Project : Remote Data in SunPy

##### Mentors : [Stuart Mumford](http://github.com/Cadair), [David Pérez-Suárez](http://github.com/dpshelio), [Will Barnes](http://github.com/wtbarnes)

---

## About me

---

### Contact Information

---

* **Name**: Yash Jain

* **Time Zone**: IST (UTC+5:30)
* **Chat handle**: yashkgp
* **Github id**: [yashkgp](https://github.com/yashkgp)
* **Email**: [yashjainjain1704@gmail.com](mailto:yashjainjain1704@gmail.com)
* **Blog**: [medium/@yashjainjain1704](https://medium.m/@yashjainjain1704)

### Education

---

* **University**: [Indian Institute of Technology, Kharagpur](http://www.iitkgp.ac.in/)

* **Major**: Integrated MS Course in Mathematics and Computing
* **Current Year**: 2nd year (4th semester ongoing)
* **Expected Graduation cum Post-graduation**: 2021

### Personal Background

---

Hello, I am Yash Jain, a second year undergraduate student at IIT Kharagpur, India. I'm pursuing a degree in Mathematics and Computing. I code on my Ubuntu Desktop using vim as I think the availability of a large number of plugins for vim makes its customizable to suit my needs. I am comfortable with a lot of programming languages but I specifically like Python because of its intuitive interface and very broad spectrum of usage from simple scripting to web applications and scientific uses.

## Pull Requests

---
Here is a list of all my merged and unmerged contributions to SunPy in a chronological order:

* `Merged`Fixes Documentation changes due to NumPy 1.14 [# 2404][1] : Due to NumPy 1.14 some of the doc tests failed. This PR tried to fix them.

* `Closed`Rhessi returns database files of multiple months.[#2418][2] : This PR was a feature request that enabled Rhessi Fido queries to return database files for multiple months.
* `Merged`Adds filters for AstropyDeprecationWarning for 0.8 [#2476][3] : This PR explicitly caught  `AstropyDepreiationWarning` on the import of representation module and silenced it for Sunpy0.8.
* `Merged`Replaces astropy-helper with sphinx-astropy [#2494][4] : This Pr splits outs the sphinx-related functionality from astropy-helpers to a dedicated sphinx-astropy package and reformats `conf.py` to make it more succinct.
* `Merged`Adds Test for TRACEMap [#2504][5] : This PR increases the test coverage by adding source test for trace maps.
* `Open`Adds Power Spectrum example for a timeseries [#2496][6] : This adds an example that estimates Power Spectrum Density of a TimeSeries Object.
* `Open` Adds figure test for Mapcubeanimation [#2546](https://github.com/sunpy/sunpy/pull/2564) :Updated PR [#2356](https://github.com/sunpy/sunpy/pull/2356) by adding figure test for Mapcubeanimator to it.

## Proposal abstract

---
This project deals with creating a entirely new functionality for SunPy named `remote_data_manager`, which will provide users a mechanism to download data from remote(HTTP) servers and various functionalities related to it (versioning of data, caching, checksumming etc).

This project is going to be designed and implemented under the assumptions that SunPy has no control over the data on the remote (HTTP) servers, and that files on the servers may be replaced with different files with the same name.

 `remote_data_manager`  will, therefore, have to validate the retrieved files have the expected hashes while providing ways for users to override this hash if they are aware of changes on the remote server and want to purposely replace that file.

## The Problem and Motivation

 ---
 Some functionality in SunPy or in affiliated packages needs access to data files on remote (HTTP) servers. As SunPy integrates more and more instruments and functionalities, there is a need to have a robust version control data management system. Some of the issues that are forcing us to design and implement remote data manager are:-

 1. A part of AIA instrument info is time-dependent and keeps changing regularly. For now, the instrument information like reflection coefficients of mirrors, the gain of CCD, the quantum efficiency of CCD are read directly from the .genx files in SolarSoftWare. Whenever a user creates an instance of the response class, he/she have to choose a path to his/her SSW and install the version of the instrument file that he/she wants.
So, the calculated response function is up to date depends on:
     * The instrument teams keeping the files in SSW up to date.
     * The user's local SSW install being up to date.
     * The user selecting the newest version (since older versions are also kept in SSW)

This is definitely not a long-term solution.

2. Currently SunPy uses AstroPy's `download_file` to download remote data for tutorials like [hmi_synoptic_maps](https://github.com/sunpy/sunpy/blob/master/examples/hmi_synoptic_maps.py).One of the few problems that AstroPy's `download_file` possess is that it doesn't version the data it downloads.It doesn't provide an override mechanism to redownload data whenever data changes on the remote server (deliberately due to calibration change etc.). This could be a really useful feature if we are tying SHA hash to our source code.

With these 2 issues stated, I have only scratched the surface, there are possibly many more uses of `remote_data_manager` that one can think of.

## The Plan

---
In a broad sense, `remote_data_manger` will have the following functionalities:-

 1. `remote_data_manger` will download and cache the data to `$HOME/sunpy/data/...` when its first needed.

 2. `remote_data_manger` will do some kind of validation that will ensure that the data is transferred correctly (SHA or MD5 hashes).
 3. `remote_data_manger`  will provide a mechanism by which users can re-download data whenever data changes on the remote server.
 4. `remote_data_manager` will support multiple mirrors.

##### Proposed API

The above mentioned functionalities will be achieved by the following functions:-

```python
def require (remote_url, mirror_urls,shahash,filename,timeout,show_progress=True):
"""
Parameters
----------
remote_url : str
    The URL of the file to download
mirror_urls : list of str, optional
    These mirror urls will be used whenever there's a problem
    with the remote url.
show_progress : bool, optional
    Whether to display a progress bar during the download
timeout : float,optional
    The timeout, in seconds.If None, timeout will be read from
    configuration settings.
hash : str
    Hash code with which the downloaded file will
    be compared with.
filename : str
    the local name of the downloaded file.

Raises
------
urllib2.URLError
    Whenever there's a problem getting the remote file.
OSError
    Whenever there's not enough space to download the file

"""
```

This function will work as a decorator and will have the following functionalities:-
* It will accept `remote_url` as an argument and download the file  from the `remote_url`
* If there is a problem with the `remote_url` , it will use the `mirror_urls` to download the file.
* It will also cache the downloaded data and add the function's name to the cache.
* It will verify the downloaded data with the provided hash.

* If the file is already present in the cache, it will do nothing.
* The file will be saved in the directory  `$HOME/sunpy/data/file_name/…` and with the name of the file determined by the it's  hash.
* Database of cache will be maintained in a JSON file.

A glimpse of proposed cache database :

```perl
{
 “file_name” : “stuartsfile”
 "function_name" : "myfunction",
  “default _version” : ”1245645343545343”
  “current_version” : ”1245645343545343”
  “total_size” : “82”
  "versions" : [
       {
         “hash” : “1245645343545343”
         “size” : “40”
         “time_stamp” : “2017-11-31 23:59:59”
         “urls” : [
                    “https://server1/file1.fits”
                    “http://server2/file1.fits”
                ]
        }
        {
         “hash” : “1362155212253213”
         “size” : “42”
         “time_stamp” : “2017-12-31 23:59:59”
         “urls” : [
            ”http://myserver/file1.fits”
            ]
        }
    ]
}
 ```

 This JSON file is made in accordance with Issue [#1939][7]

where,
`file_name` will act as a shared key between all the versions of a file .
`current_version` is the version of the file that will be returned by `get` function.
`default Version` is the version of the file that is compatible with our code (the file whose SHA hash is hard coded to the source code ).
By default, both `current_version` and `default_version` will point to the same file

```python
def get(filename):
"""
Parameters
----------
filename : str
Returns
-------
local_path : str
    returns the local path to the current_version of the filename,
    whose name is determined by it's  hash.
"""
```

This function will search for the filename argument in the cache and will return the local path to the current_version of the filename .

#### Usage

Define a function that needs remote data :

```python
@remote_data_manager.require(remote_url='https://server1/file1.fits',
                             mirror_urls=['http://server2/file1.fits'],
                             shasum='1245645343545343',file_name = 'stuartsfile')
def myfunction():
    filename = remote_data_manager.get('stuartsfile')
```

This will add the function's name to the cache, when the code is run the downloader goes out and gets the file, verifies that it matches the provided hash and it puts it in the folder `$HOME/sunpy/data/stuartsfile/…` , and then gives it to the function on request.

```python
@contextlib.contextmanager
def skip_hash_check(timeout,show_progress=True):
"""
Parameters
----------
show_progress : bool, optional
    Whether to display a progress bar during the download
timeout : float ,optional
    The timeout, in seconds.If None, timeout will be read from
    configuration settings.
"""
```

This function allows users to download the same file from the same server even if the hash has changed(i.e. the file has changed on the remote host). This function is a context manager, and hence will be used with a`with`-`as` statement.

#### Usage

```python
with remote_data_manager.skip_hash_check():
    myfunction()
```

This will download a new version of the same file from the same server and add it to cache. `skip_hash_check` will also change `current_version` in the cache database to point to the newly downloaded file, so when `get` function is called inside `myfunction` it returns the path to the newly downloaded file. At last, after `myfunction` is executed, `skip_hash_check` will again set `current_version` to default.

```python
@contextlib.contextmanager
def replace_file(remote_url, mirror urls, shahash,filename,timeout,show_progress=True):
"""
Parameters
----------
remote_url : str
    The URL of the new file to download
mirror urls : list of str, optional
    These mirror urls will be used whenever there's a problem
    with the remote url.
show_progress : bool, optional
    Whether to display a progress bar during the download
timeout : float, optional
    The timeout, in seconds.If None, timeout will be read from
    configuration settings.
shahash : str
    SHA hash code with which the new downloaded file will
    be compared with.
filename : str
    the file name.

Raises
------
urllib2.URLError
    Whenever there's a problem getting the remote file.
OSError
    Whenever there's not enough space to download the file

"""
```

This function will allow users to download a newer version of the file from a totally different url. This function is also a context manager.

#### Usage

 ```python
 with remote_data_manager.replace_file(remote_url='http://myserver/file1.fits',
                                       shasum='1862354754121',
                                       file_name='stuartsfile'):
    myfunction()
```

This will download a new version of the file from a different url, validate the downloaded file with the user provided SHA hash and add it to cache. `replace_file` will  change `current_version` in the cache database to point to the newly downloaded file, so when `get` function is called inside `myfunction`, it returns the path to the newly downloaded file. At last, after `myfunction` is executed, `replace_file` will again change `current_version` to default.

This function will also allow users to use older versions of file. If the SHA hash provided by the user is already present in the cache(older versions), `replace_file` will change `current_version` of the file to the user provided SHA hash.  Thus when `get` function is called , it returns the path of the file specified by the user.

### Utility Functions

```python
def get_cached_urls(file_name=None,time_range=None):
"""
Get the list of URLs along with their filename in the cache.
Especially useful for looking up what files are stored in
your cache when you don't have internet access.
Parameters
----------
file_name : str , optional
    If provided, function will return cached urls
    for the provided file name.
time_range : TimeRange , optional
    If provided ,will return the cached urls
    during that time range .

Returns
-------
cached_urls : list
    List of cached URLs along with their filename.
"""
```

```python
def clear_download_cache(hash_or_filename=None):
"""
Clears the data file cache by deleting the local file(s).
Parameters
----------
hash_or_filename : str or None
    If None, the whole cache is cleared.  Otherwise, either specify a
    hash for the cached file that is supposed to be deleted, or a filename that
    should be removed from the cache if present.
"""
```

( Utility functions are greatly inspired by AstroPy's `data` module.)
The functionality of each utility function is aptly explained in the string docs.
Helper functions like `compute_hash`, `get_free_space_in_dir` will be directly imported from AstroPy's data Module.

Now, to maintain the integrity of the data stored in cache database, cache directory must be locked before writing. For this, wrapper functions will be written around AstroPy's `_acquire_download_cache_lock`,`_release_download_cache_lock`. This will provide a way to lock cache directory before writing.

## Timeline

---
This is merely a modest sketch. I have tried to be as lenient as possible in assigning the weekly tasks.I will be writing developer documentation along with user documentation.The last 1-2 days of a Week will usually be reserved for code review or buffers to complete work which has not been completed in the allotted time.

Though I intend to keep in touch with the mentor throughout the week and ensure that I am going in the right direction, I have tried to maintain a feasible feedback mechanism in the schedule so as to ensure that my mentor gives feedback on a reviewable quantity of code at appropriate intervals.

Apart from below mentioned timeline, I will also write blogs weekly, so that mentors can evaluate and keep track of work that I am doing.

* **Pre GSoC Period (upto 23 April)**
  * Continue working on SunPy issues and open new Pull Requests on GitHub. Read information/documentation related to the project.

* **Community bonding period (23 April - 13 May)**
  * Read the documentation and get more familiar with the code base(especially modules which use remote data).
  * Get familiar with JSON, pytest, urllib, decorators, context managers.
  * Read code and get more familiar with the downloading and caching mechanism used by AstroPy's `download_file` and try to get an idea of what challenges could possibly arise while implementing the new caching mechanism.
  * Thoroughly discuss with mentors the changes (if any) they want in above-proposed API and get a final idea of how to approach the project.

---

Coding Begins
---

* **Week 1 - Week 3 (May 14 -June 3)**
  * Discuss with the mentors and finalize the structure of cache database.
  * Write wrapper function for _acquire_download_cache_lock and_release_download_cache_lock.
  * Implement require function (a basic cache and download system) along with all the helper functions needed.
  * Write tests and documentation for require function.

* **Week 4 (June 4 - June 10)**
  * Implement `get` function.
  * Write tests and documentation for `get` function.
* **Week 5 (June 11 - June 17)**
  * Add any missing test cases and fix bugs(if any).
  * Send a PR for review.
  * It is not necessary that everything goes as planned out and there might be unavoidable delays due to a nasty bug hidden from eyesight.Therefore, this week is kept as a buffer.

---

**Phase 1 Evaluation**
---

* **Week 6 and Week 7 (June 18 - July 1)**
  * Discuss with mentors how the above-proposed API for overriding downloaded data can be improved to make it more robust and user-friendly.
  * Address the requested changes( if any ) in the previously mentioned PR.
  * Successfully implement an override mechanism, allowing users to re-download the data (`skip_hash_check` and `replace_file`).
* **Week 8 (July 2 - July 8)**
  * Write tests and documentation for `skip_hash_check` and `replace_file` .
  * Fix Bugs (if any ).
* **Week 9 (July 8 - July 15)**
  * This week is kept as a buffer to complete any left-over in the previous periods
  * Update the previously opened PR.
  * Clean the code.

 **Phase 2 Evaluation**

* **Week 10 and Week 11(July 14 -July 28)**
  * Write Examples for the gallery on how to use this module. Examples will be written for o following 3 scenarios:
    * Download a file from a remote server.
    * Replace a file if the data changes on the remote server.
    * Replace a file with file from a totally different server.

  * Update the previously opened PR.
  * Implement utility functions
* **Week 12 and Week 13 (July 29- August 14)**
  * Add Tests and Documentation for Utility Functions
  * Write Examples for utility functions.

  * See if there exist any bugs that were not addressable before. Any pending work or issues will be addressed to during this time
  * Solve merge Conflicts
  * Complete leftover documentation(both user and developer).
  * Solve PEP8 Issues
  * Address the requested changes( if any ) in the previously opened PR.
  * Get the PR merged into the master branch.

### Software Packages to be used

**Language** : Python

**Modules** : json, urllib , pytest, contextlib.

### Benefits to the Community

Once implemented, remote_data_manger will provide the following benefits :
* A version control remote data management system, allowing users to download data from remote servers.
* It will provide a caching mechanism so that the user doesn't have download the data again and again.
* It will provide a override mechanism so that user can redownload the same file if the  file has changed on remote server.
* It will also make sure that,  if remote data is available, one version of SunPy  always give the same output.

### How I propose to complete the project

I am pretty confident of completing this project because I have fairly good experience in python. Few of my  projects that I am personally  fond of are :
* Automated text summarization using nltk.
* Object detection using keras framework.
* Question Answering Chatbot for  AgNext. ( The code for this project is confidential )
My fascination towards open source is rather new. I started contributing to SunPy in January. Apart from SunPy , I have also contributed to SymPy .
I will strictly follow my proposed timeline .I will be pushing my changes to  remote fork daily and will  also keep updating my mentors over my progress both through chat and blog.I will spend a lot of my time to have a good hands-on experience before the coding period starts. This will help me to avoid any problems later.Even after the GSoC coding period ends, I will  be available if anybody has questions regarding my work.

### Other Schedule Information

I have my end semester exams from 20 April -  28 April. So, I won't be completely available during the Community Bonding Period. However, I would try my best to complete the tasks mentioned in the Community Bonding Period.

I don't have any other internship during this summer.
I commit working for 40 hours a week (Mon-Sat) during GSoC period. I am also willing to work on Sundays if my mentor(s) and I feel that I am falling behind on my project work.

I might take a vacation of 4-5 days during the GSoC period. However, I will continue to work on the project during that period, although for a lesser amount of time.I have distributed my work accordingly.

Even after my new semester starts(16 July), I can easily dedicate around 5 hours during weekdays and 8 hours during weekends, as the academic load during the start of the semester is quite low.However, I have distributed work in such a way that there is less load in the last 4 weeks.

#### Have you participated previously in GSoC? When? Under which project?

No, I have not participated in GSoC previously. This is the first time I am taking part in GSoC.

#### Are you also applying to other projects?

No, I am not applying to any other project.

### Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or
further explanations, feel free to contact yashjainjain1704@gmail.com.

---

[1]: https://github.com/sunpy/sunpy/pull/2404
[2]: https://github.com/sunpy/sunpy/pull/2418
[3]: https://github.com/sunpy/sunpy/pull/2476
[4]: https://github.com/sunpy/sunpy/pull/2494
[5]: https://github.com/sunpy/sunpy/pull/2504
[6]: https://github.com/sunpy/sunpy/pull/2496
[7]: https://github.com/sunpy/sunpy/issues/1939
