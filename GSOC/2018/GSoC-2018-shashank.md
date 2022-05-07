# Remote Data In SunPy

## Organisation: OpenAstronomy

## Sub-organisation: SunPy

## About Me

### Contact Information

- Name: S. Shashank
- Email: s.shashank2401@gmail.com
- Time Zone: +05:30 GMT
- Github Handle: [talsperre](https://github.com/talsperre)
- Chat Handle: grenko
- Resume: [link](https://researchweb.iiit.ac.in/~shashank.s/static/Resume.pdf)

### Personal Background

I am S. Shashank, a second year computer science major at IIIT Hyderabad, India. I have prior experience with open source and have contributed to other organizations as well. I love programming a lot, particularly in Python and C++. I use Ubuntu mainly for coding purposes and my favourite editor is Sublime Text.

### University Information

- **University:** [International Institute of Information Technology, Hyderabad](https://www.iiit.ac.in/)
- **Major:** Computer Science
- **Current Year:** 2nd Year (4th semester ongoing)
- **Expected Graduation Date:** 2021
- **Program:** Bachelor of Technology (B. Tech) and MS by research in Computer Science and Engineering

## PR links and Issues Worked on

- Merged:
  - [Fixed title bug in sunpy.timeseries.rhessi](https://github.com/sunpy/sunpy/pull/2477)
  - [Some simple extensions to Map Stonyhurst grid plotting](https://github.com/sunpy/sunpy/issues/2308)
- Closed:
  - [Replaced figure.show() with plt.show() to solve instant disappearing of timeseries plot](https://github.com/sunpy/sunpy/pull/2467)
- Open Issues:
  - [The repr of GenericMap raises an error if the WCS is an unknown type](https://github.com/sunpy/sunpy/issues/2452)
- Authored Issues & PR's:
  - [Issues](https://github.com/sunpy/sunpy/pulls?q=is%3Apr+author%3Atalsperre)

## Project Proposal Information

**Mentors:** Stuart Mumford, David Pérez-Suárez, Will Barnes

### Abstract

SunPy is a package for solar physics that is also used for solar data analysis. The library has several functionality that requires access to data on remote HTTP servers.  The data such as those provided by instrument teams is highly likely to change with time. Thus, there is a requirement for a module which ensures that the **remote data is downloaded and cached before it is used in a function.**

Since SunPy has no control over the remote data on the servers, it should have a way to **validate** that the retrieved file has the same **expected hash.** The module should allow the user to **redownload the data**, i.e.  allow a user to override the hash if the user is aware of the changes made in the server. There should also be support for **download of data through multiple mirrors.** The main aim of this module is to **provide a version control system** for data in SunPy such that if the given remote data is available then **one version of SunPy will always give the same result.** Such a versioning system also needs to ensure that the **previous versions of a file are not removed** in case the user would like to use them also.

### Motivation

Several functions in SunPy require data files to work like instrument calibration data or timeseries data. A prominent example of this is the AIA response function.  The AIA response  changes significantly over time and there needs to be a way to take a remote file and ensure that it is downloaded before it is used in a function. In the current scenario, a user needs to have the given file locally in order to use a given function. One of the main aims of this module is to solve this issue. There should also be a versioning of the data files so that a given version of SunPy always returns the same result. Thus, a caching system based on a data manager would help to solve these problems.

### Deliverables

The following are the deliverables for the project:

- Implement a cache system
- A **Remote Data Manager** with the following basic features:
  - Validate the downloaded file by checking its checksum
  - Caching a given remote data file
  - Mechanism to allow the user to override the cache
  - Allow download from multiple mirrors
  - Allow multiple downloads to happen in parallel
  - **Show a progress bar** for the download if time permits
- **API to access** the Remote Data Manager
- Write tests and documentation
- Add examples on using the module to the example gallery (1 or 2 jupyter notebooks)

### Implementation

The implementation would be based on the following flow diagram:

![Flow Diagram](https://raw.githubusercontent.com/talsperre/images/master/diagram-5.png)

The implementation would consist of a ```remote_data_manager``` class. It would handle several aspects of the module such as **maintaining a record** of the File & URL cache and interacting with the remote data server.

There would be **two caches: URL cache & File cache**. On requesting a file using remote url, the url would first be checked in the URL cache. If it is present,  only then would the search proceed further in the file cache. The URL cache would help in making the **module faster** as iterating through the file cache each time a request is made would be time consuming.

The file cache structure and implementation has been discussed in detail below. The ```remote_data_manager``` would be accessed using a **suitable API** by the user level functions. It would provide the user with options to access the ```remote_data_manager``` in several ways and also provide methods to interact with the cache.
___

#### Cache

##### File Cache

The project requires the implementation of a robust cache that needs to store several details like the **filename, function name, creation time, hashsum** etc. The size of the cache need not be very large and hence the storage of the data can be **done using json files stored in the disk.**

The following cache structure is proposed:

```javascript
[
  {
    "file_name": "file1",
    "function_name": "function1",
    "default": "yes",
    "urls": [
      "url1",
      "url2",
      "url3"
    ],
    "skip_hash_check": "no",
    "shasum": "1234",
    "created_at": "2016-05-18 17:18:56.793709",
    "modified_at": "2018-03-18 17:18:56.793709"
  }
]
```

The underlying assumption made here is that **each unique function would have a new file** even if the file name is the same. This is because in the future we may like to override the file for a given function but not for the other function. Thus, **a new file would be cached for each unique function as well as each new version of the file available.** The previous versions of the file would remain in the cache for use whenever needed.

The ```default``` attribute has two values: ```yes``` and ```no```. If it is ```yes``` then, it means that the given file is the default version that must be returned for that function. With such a scheme, if the user wants to override the default file for a function, then we would need to only modify the one which has ```default``` value as ```yes```.

The ```created_at``` attribute exists to tell the user when the file was first requested. Thus, it would help the user check if the file has changed since then in the remote data server. The ```modified_at``` tells us when the file was last modified. One of the uses of it would be that a user would have an option to request a file from the cache that was modified most recently.

The ```skip_hash_check``` attribute would be used to identify whether the hash of the downloaded file needs to be checked after downloading or not. It would be used by the ```skip_hash_check``` function.

In order to ensure **data integrity** of the json files, I propose two helper functions ```acquire_cache_lock``` and ```release_cache_lock``` in the ```remote_data_manager```. Once a lock is attained, data access can be done using the cache. The locks would be implemented using the ```threading``` module of python.

##### URL Cache

Apart from the file cache there would also be a **persistent URL cache.** Its purpose would be to simply **speed up the caching** process. When a remote data is requested, first we would check if the url is in the given cache already, only then we will proceed to check in the file cache. If not present, then proceed to download the file from the remote url.

The **URL cache** can be implemented as a **persistent set** that can be accessed using the python ```shelve``` module. A set should be used for this purpose as it can check **membership very fast.**

___

#### File Storage

The files would be stored in the following path:

```bash
$HOME/sunpy/data/function_name/cached_file_name
```

In order to ensure **uniqueness of the filename**, the files themselves would be stored as combination of ```file_name``` & ```modified_at```. They can even be hashed if required.

One such scheme is as follows:

```python
cached_file_name = "_".join(file_name + modified_at)
```

Another scheme could be:

```python
import hashlib
cached_file_name = hashlib.md5(file_name + modified_at).hexdigest()
```

___

#### Remote Data Manager

The ```remote_data_manager``` is reasonably complex and it is the core class that would handle the caching operations, file handling, checksumming etc. It must also be able to handle the opening and closing of files as well as other errors easily. Thus, I propose that the functions of ```remote_data_manager``` like ```get_readable_obj``` be yield a **Context Manager.**

The following would be the main functions in the ```remote_data_manager```:

##### ```require```

This would be **implemented as a decorator** which when applied to a function would add the file, function name to the cache. When the function is called, the downloader would go and get the file, verify that it matches the hash and put it in its corresponding path.

In case the file is already present in the cache, the it would do nothing.

Usage:

```python
@remote_data_manager.require(name='abc', urls=['server1/file1.fits'], shasum='12')
def myfunction():
    filename = remote_data_manager.get_file_contents('abc')
```

##### ```get_file_contents```

The function would **return the contents of a file** after either downloading it or fetching it from the cache. It would directly provide the contents to the user and thus they would not have to worry about opening and closing of file handlers.

##### ```get_readable_obj```

Given a remote URL, it returns a context manager that yields a readable file-like object. It fetches the file from the cache if already present else it downloads the file.

Usage:

```python
with remote_data_manager.get_readable_obj(urls=['url']) as f:
    content = f.read()
```

##### ```download_file``` & ```download_files_in_parallel```

It would be an internal function used by the ```remote_data_manager``` that takes a url as input and downloads the remote data. It can cache the result if required. Ideally the user would never have the need to call this function directly as there would be an API layer over it. Either the function defined in ```sunpy.net``` module can be used or a new one can be implemented.

##### ```skip_hash_check```

This function would allow the user to **skip hashsum check** while downloading the file. It would basically change the ```skip_hash_check``` attribute in the cache database to yes. Once ```myfunction``` is executed, it will revert the database back to its original state. It would be implemented as a **context manager.**

Usage:

```python
with remote_data_manager.skip_hash_check():
    myfunction()
```

##### ```replace_file```

It provides the user with functionality to **download the newer version** of the file if it is available. It would modify the default version of the file in the json database by changing the value of the default attribute. It will however not remove the previous version of the default file.

Usage:

```python
with remote_data_manager.replace_file(name='abc', shasum='1234', urls=['mno/abc.fits']):
    myfunction()
```

___

To supplement these main functions, several helper functions need to be defined. Some of them would be ```is_valid_url```, ```is_valid_path```, ```compute_hash```, ```acquire_cache_lock```, ```release_cache_lock```, ```get_free_space_indir```, ```check_free_space_indir```.
___

#### Additional API

The API would be used for accessing the ```remote_data_manager```. Apart from the few functions mentioned above, the API should also ideally provide the user with several options such as **getting the latest version of a file** in the cache, **getting a file on the basis of its hash value** etc. The API would also need to provide methods to directly access the URL & File cache such as:

- Getting all the cached urls
- Clearing the File & URL cache

The following are the major functions of the API apart from a few mentioned above in the Remote Manager section:

##### ```get_file_by_hash```

This function would **return the version of the file whose hash** was mentioned. If no such file is found then **return an Exception.**

Usage:

```python
mydata = remote_data_manager.get_file_by_hash(hash='1234')
```

##### ```get_latest_file```

This function would **return the latest version** of a file in the cache.

```python
mydata = remote_data_manager.get_latest_file(file_name='abc')
```

##### ```get_file_by_modified_time```

The function would **return the version** of file that was **modified immediately** after the ```modified_time``` provided to the function. It would return an exception if the file is not already present in the cache or if no such file with given ```file_name``` exists in the cache whose ```modified_time``` is greater than that provided.

Usage:

```python
mydata = remote_data_manager.get_file_by_modified_time(file_name='abc', modified_time='2016-05-18 17:18:56.793709')
```

Similarly there would be functions such as ```clear_file_cache```, ```clear_url_cache``` & ```get_cached_urls```.

___

#### Error Handling

The implementation of the ```remote_data_manager``` and the API requires subtle handling of errors. Since this module would require the opening and closing of several files, the functions such as ```get_readable_obj``` and ```skip_hash_check``` would be implemented as a context manager.

The whole download and caching process consists of 4 major portions:

1. Get the remote url of the data source
2. Update the URL cache
3. Download the file from the remote server
4. Update the File cache

In this case, the order of operations matter a lot. For proper error handling, the correct order is actually ```1 -> 3 -> 2 -> 4```. If the order ```1 -> 2 -> 3 -> 4``` is followed, then it might result in an error. This is because if the download failed and the URL cache was updated, then an entry would already have been added to the URL cache, even though the file could not be cached.

However there are two options for the correct order itself: ```1 -> 3 -> 2 -> 4``` and ```1 -> 3 -> 4 -> 2```. The second option is better as it would be more efficient. The reasoning is that, in case step 4 results in an error (i.e. File cache could not be updated), then an entry of the remote url is anyways added in the URL cache. The next time the file is requested, it would be first be checked in the URL cache and then further search would proceed. However it would not find any corresponding entry in the File cache. Thus, the File cache was traversed unnecessarily.

However, if we use the order ```1 -> 3 -> 4 -> 2```, then if step 4 fails, no entry is added to the File as well as URL cache. Thus, when the file is requested again, it would first be checked in the URL cache and since no entry exists, the search would stop at that point of time itself. Thus, we are able to skip the File cache traversal itself.

Thus, the order of operations should be: ```1 -> 3 -> 4 -> 2``` for better efficiency.
___

#### Modules Used

```json```, ```urllib```, ```threading```, ```contextlib```, ```sunpy.util.progressbar```, ```hashlib```, ```pytest```
___

## Timeline & Deliverables

### Community Bonding Period (April 23 - May 14)

During the community bonding period I would get to know more about the codebase. I would try to get familiar with some python http libraries like ```urllib``` and with context managers and decorators in python. I am familiar with a few modules in ```sunpy.net``` but would also have a look at ```aia``` response and other such modules which might need the use of data manager. I would also finalize on the cache structure and organization during this period.

During this time I would also discuss with the mentors to know properly which all features should the API provide. Some time would also be given to study about writing tests using ```pytest``` and finalizing the download mechanism.

At the end of the Community Bonding Period, I aim to:

- Get familiar with sunpy codebase, in particular modules like FIDO, net, AIA response, timeseries (RHESSI) etc.
- Finalize the cache structure and organization. Decide on all the parameters that the cache should store and begin working on a basic implementation
- Finalize on various aspects of the download functionality such as the type of checksum to use (md5 / sha), how many versions of a file to cache etc.
- Learn about ```pytest``` and **context managers**, **decorators** in detail.
- Get an overview of all the functionality that needs to be provided by the API

___

### Coding Period Begins

___

### Week 1 (May 15 - May 21)

- Begin coding the helper functions such as ```acquire_cache_lock```, ```release_cache_lock``` to ensure data integrity
- Write helper functions for the download functionality such as ```is_valid_url```, ```compute_checksum```, ```get_free_space_indir```.

### Week 2 - Week 3 (May 21 - June 3)

- Begin working on the basic download functionality.
  - Implement the ```require```, ```get_readable_obj```, ```get_file_contents``` functions
- Start working on the tests for the downloader

### Week 4 - Week 5 (June 4 - June 17)

The main aim would be to ensure that by the end of the first evaluation a fully working caching and download functionality is implemented. This period will also server as a buffer period to complete any other pending tasks or issues.

- Complete the tests
- Add documentation for the code written till now.

___

### Phase 1 Evaluation

___

### Week 6 - Week 7 (June 18 - June 30)

- Implement the ```replace_file``` function to allow override facility
- Write functions to query the cache:
  - Get the version of the file which was modified most recently
  - Get the version of the file whose hash was mentioned
  - Get the latest version of the file that existed before a given time (Would use the ```modified_at``` parameter in cache)

### Week 8 (July 1 - July 8)

- Implement ```download_files_in_parallel```
- Complete the tests for the API
- Add documentation for the code written till now
- If time is still left then begin next weeks work

### Week 9 (July 9 - July 15)

This period will also act as a buffer period for the second part of the project

- Complete any pending or left over tasks

___

### Phase 2 Evaluation

___

### Week 10 - Week 11 (July 15 - July 29)

- Write additional functionality for the API like ```clear_cache```, ```get_cached_urls```
- Complete all the tests for the API as well as the download functionality and cache
- Complete all the user as well as developer documentation
- Begin working on the jupyter notebooks that would be added to the example gallery

### Week 12 - Week 13 (August 1 - August 14)

If things went fine till now, then I would be done with my target till now. This period will basically act as a buffer period.

- Complete any left-over tasks
- If there is time left then I would like to work on improving the module by adding features like a progress bar. (Can use the progress bar made in ```sunpy.utils.progressbar```)
- I would be in touch with the mentors and if there are any further issues or bugs that are left unresolved then I would work on them.
- Hopefully get the work merged with the master branch of SunPy

___

### Final Evaluation

___

### How I will successfully complete the project

I am confident of completing this project as the project suits my interests and I have a fairly good experience with python. I have previously worked on projects that have strict deadlines and have a good prior experience with open source.

I would push my work to the remote fork frequently so that the mentors can review my progress whenever required. I would always be in constant communication with my mentors to update them on my current progress and seek their guidance whenever I am stuck in any issue.

Even after GSoC ends, I will actively contribute to SunPy and be available if anyone has any questions regarding my code.

### Benefits to the Community

The project offers several benefits to the community.

- It would provide a version control system of remote data so that one version of SunPy always gives the same answer
- It would allow the user to work with an earlier version of data file even if it has modified in the remote server
- It provides a caching mechanism so that the user need not download a file that is already present with them

## GSOC

### Have you participated previously in GSoC? When? With which project?

No, I have not participated in GSoC before.  This is the first time I am participating in GSoC.

### Are you also applying to other projects?

No, I am not applying to any other projects. This is the only project and SunPy is the only org that I am applying for.

### Commitment

I would not be involved in any other internship or work during the summers. Since, my vacations starts on May 1, I would be able to start early and try to complete the project well before the deadline.

My classes for the new semester would begin from August 1, but I would still be able to give at least 40 hours per week as there is less academic load during the first few weeks of the semester.

### Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact s.shashank2401@gmail.com
