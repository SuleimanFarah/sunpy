# Organisation: OpenAstronomy

## Sub-Organization: SunPy

## Project: Remote Data in Sunpy

## Student Information

- **Name** : Gulshan Kumar
- **E-Mail** : gulshankumar1210iiit@gmail.com
- **Phone**: +91-9490415562
- **Time Zone** : **UTC**+05:30
- **IRC Handle** : gulshan_mittal
- **Github handle** : [blackeye](https://github.com/gulshan-mittal)
- **Blog**: [MyBlog](https://blackeye1210.wordpress.com)
- **Blog RSS feed :** [RSS Feed](https://blackeye1210.wordpress.com/feed/)

## University Information

- **University** : [International Institute of Information Technology, Hyderabad](https://www.iiit.ac.in)
- **Major:** Computer Science
- **Current Year:** Second Year
- **Expected Graduation Date:** 2021
- **Programme:** Bachelor of Technology (B.Tech) in Computer Science and MS by Research in Computer Science

## Open Source and Development Experience

Before contributing to **Sunpy** I have not had much Open Source experience but I have experience working on a team project, especially involving python.

- Made a **Shopping Portal** in **Python** using flask similar to OLX where you can buy or sell products. [Link to Project](https://github.com/gulshan-mittal/Shoppinghome)
- Made a **Proxy server and a client-server model in Python** using HTTP libraries. [Link1](https://github.com/gulshan-mittal/Proxy-Server) [Link2](https://github.com/gulshan-mittal/Socket-Programming)
- Made a **Bomberman** game using **Python** with **OOP Principles**. [Link to Project](https://github.com/gulshan-mittal/bomberman-game)
- Made a 2-D Pacman Killer game using **OpenGl**. [Link to Project](https://github.com/gulshan-mittal/Packman-Killer)
- Made a 3-D Legend of Zelda game Wind Walker using **OpenGl**. [Link to Repo](https://github.com/gulshan-mittal/Wind-Walker-3D-Zelda-Game)
- Made an Extreme Tic Toe Bot using **Python**. [Link to Bot](https://github.com/gulshan-mittal/Extreme-Tic-Tac-Toe)
- Build a State Restoring Quiz Game in **Ruby on Rails**. Modify that Project and conduct **Cache-in IIIT-H Felicity Buzz Event** where a number of people registered on it. [Link to Project](https://github.com/gulshan-mittal/State-Restoring-Quiz-game/tree/master/Quiz-game)

**Development Experience**: Mobile App Developer Intern at Statwig, T-Hub, IIIT Hyderabad.Made a Project Toad App similar to **Google Calendar**. Amazon **Alexa** developer and **Google Assistant** developer.

**GitHub Handle** : [blackeye](https://github.com/gulshan-mittal?tab=repositories)

**Operating System Experience:** Currently, I use **Ubuntu**. I also use Fedora, Linux Mint, and Windows.

Apart from the above projects, I am also proficient in **C, C++, javascript**.

## Pull Request & Issue

- [hgs_to_hcc(heliogcoord, heliocframe)](https://github.com/sunpy/sunpy/issues/2470) **`closed`**
- [hgs_to_hcc(heliogcoord, heliocframe) : Convert from Heliographic Stonyhurst to Heliograpic Carrington](https://github.com/sunpy/sunpy/pull/2502) **`merged`**
- [Add Heliocentric --> Heliocentric transformation Issue](https://github.com/sunpy/sunpy/pull/2469) **`closed`**

## Project Proposal

**Project:** Remote Data in SunPy

**Mentors** : [Stuart Mumford](https://github.com/Cadair), [Will Barnes](https://github.com/wtbarnes), [David Pérez-Suárez](https://github.com/dpshelio)

### Abstract

The aim of the **Sunpy** is to provide **data analysis** and helps in the field of **solar physics** by providing tools and functions which minimize the efforts of users in performing their tasks related to solar physics.The sunpy package needs access to the data files on the **remote (HTTP) server** for the data analysis used in former.Since SunPy has **no control** over the data on the servers, and the files on the servers may be replaced with different files with the same name, so there is a need for a module which ensures that the remote data is **downloaded** and **cached** before it is used on the client system. The project provides a way to **validate that the retrieved file has the expected hash** and also provide ways for users to override this hash i.e.,  **redownload** the data if they are aware of changes on the remote server.

The project will contain the **`remote_data_manager`** class, which will provide users a mechanism to download data from remote servers, versioning of data, caching and multiple mirror functionality of download function. The user will use the **API** to access the `remote_data_manager`. Apart from the few functions mentioned above, the API will provide the user with several options such as getting the latest version of a file means file on the basis of the **timestamp** in the cache, getting a file on the **basis of its hash** **value** etc.

### Motivation

Functions in sunpy are going to need data files present on a remote server to work and as of now, there is no proper system to control remote data so there is a need to design a system which could meet with the requirements of remote data in sunpy. There are some issues in sunpy which push me to design and build the remote data manager.

1. In **`download_file`** function which is currently used to download data for tutorials taken from [astropy](http://docs.astropy.org/en/stable/api/astropy.utils.data.download_file.html?highlight=download) doesn't support the override mechanism to download data.Also it **doesn't**meet with multiple mirror requirement if data is not present on one server. Motivation from  [Issue 1809](https://github.com/sunpy/sunpy/pull/1809).
2. There is some part of **`AIA`** response function which is varying with time. Right now the instrument info (e.g. reflection coefficients of mirrors, a gain of CCD, the quantum efficiency of CCD) are read straight from the .genx files in SSW. When a user creates an instance of the response class, he/she can choose a path to his/her  SSW install and the version of the instrument file he/she want (the default is 6). As of now, the problem how to either pull down this info from somewhere or store it (and version it somehow) has not been solved. The calculated response function is up to date depends on the instrument teams keeping the files in SSW up to date, the users local SSW install is up to date and the user selecting the newest version (since older versions are kept in SSW). This is **not a good** idea to purposed.Motivation from [Issue 1897](https://github.com/sunpy/sunpy/pull/1897).
3. **Timeout** error if data from the remote server exceeds the time limit.

### Project Goals

**Part1**: Evaluation of the methods proposed and ensuring the **best approach** for storing a local cache of data. There should be an implementation of a basic cache and download system, including test and documentation.

**Part2**: Design of a simple and functional API and have worked with my mentors and community for better understanding and implementing the design efficiently.The working **prototype** of this API also have to be done including its **tests**.

### Deliverables

1. **Cache and download system** along with its test and documentation.
2. **Simple and functional API** and its working prototype. Written examples for the gallery of how to use the functionality.
3. **Developer documentation** for the understanding of functionality. All the work should be done in a manner that Pull request should be merged after **review and feedback**.

### Detailed Description

#### Requirements elicitation

1. The first requirement is data is downloaded and cached to **`$HOME/sunpy/data...`**  when first needed. It is the folder that made automatically when you build the sunpy project. (Inside the data folder currently there are fts and fits  files and `sample_data` folder which also contains fits, txt, pha files.)
2. The  second requirement is do some kind of **validation** that will ensure that the data is transferred correctly. It can be done using the cryptographic hash function. As the project is dealing with **random data** on remote (HTTP) servers, there is a need to have a vigorous version-control data management system like git. The priority of this interesting requirement will be considered **high** in this project.
3. The Mechanism by which users can be allowed to **re-download data**.
4. The download code supports **multiple mirrors**.

### Design and Implementation

#### Remote Data Manager

In this project **`remote_data_manager`** is the core class which would handle the caching operations, download features, file handling, checksumming, validations etc. The `require`, `skip_hash_check`, `replace_file` and other helper function of this class will perform the above operations. The **`require`** function will **work as a decorator** and will be used to build an efficient caching mechanism. The skip_hash_check and replace_file function will be **implemented as a context manager**. The helper functions that I propose for API includes **`compare_hash`**, **`get_cached_urls`**,  **`delete_cache`**, **`get_file`**  which will be **used to access** `remote_data_manager`.

#### Caching

We need to cache  the downloaded data in a effective manner. We will use `require` function of  `remote_data_manager` which maintains a record of the cache. Here the `require` function work as a decorator. The code inside sunpy would ask for a given file name at a given url with given hash. Define a function named `myfetch()` that need some data :

```python
@remote_data_manager.require(name='file1',
                             urls=('https://server1/file1.fits', 'http://server2/file1.fits'),
                             shasum='1245645343545334')
def myfetch():
    filename = remote_data_manager.get_file('file1')
```

This adds the function name to the cache, and the files, when the code is run the downloader goes out and gets the file, verifies that it matches the provided hash using `compare_hash()`function of `remote_data_manager`and it puts it in a folder which probably has the function name in it, and then gives it to the function on request. **If a file already presents in the cache then it simply gave the path to the file without downloading**.

**Note:** `comapre_hash()` function will be implemented in `remote_data_manager` class .

The Cache will be maintained on a disk in the form of **JSON** (javascript object notation). The given ***JSON below*** describe how the cache database will look like, how it allows to override the hash check and replace the file.

```json
{
    "function_name": "myfetch",
    "fileaname": "file1",
    "default_hash": "1245645343545343",
    "fetch_hash": "1245645343545343",
    "list_hash": [
        {
            "hash": "1245645343545343",
            "size": "10",
            "created_at": "2018-3-15 06:00:00",
            "modified_at": "2018-3-15 06:15:00",
            "urls": [
                "https://server1/file1.fits",
                "https://server2/file1.fits"
            ]
        },
        ".......... other file caches belong to the same name"
    ]
 }
```

Here, **fetch_hash** will be fetched  by `get_hash`  function or hash attached with the file in remote_data_manager class, **default_hash** I assume it is the hash which I know for comparing or it is the hardcoded hash. **List_cash** maintains the list of a cache of files having same **shared key**.

- **Note**: We are also caching the older version of data.

### Storage and Download

- ***Storage:*** The file will be saved in the folder  `$HOME/sunpy/data/…` and the **name of the file determined by hash or time stamp ( `created at` field in the JSON of cache)**. The `modified_at` field in JSON of cache will maintain the individuality of the cached filename.

  - **Filename by hashing**: The name of the file will be the hash of filename plus modified time. Here modified time is taken into consideration to avoid the situation when the file is changed on the remote server and user redownload it.

    ```python
    import hashlib as hash
    Cached filename = hash.md5('orignal_filename' + modified_at).hexdigest()
    ```

    ​

  - **Filename by timestamp:** The `modified_at` field in JSON of the cache will be added to the original name of the file after the downloading.

    ```python
    Cached filename = original_filename + '_' + modified_at
    ```

    ​

- ***Download:***  For downloading data we are using `remote_data_manager` which uses the downloading function, for example, **`download_file`**  or implementation of new function can be made. In  **`require`** function as stated above will have a **timeout** parameter, **show_progress bar** (default value `true` in astropy download function) parameter as well.

  ​

- **For storing the cache efficiently**  `compare_hash` is made proficient and  hash value of two comparing files will be stored (**memoize**) so that there is no need to calculate the hash value repeatedly.

### Functions in Remote data manager

##### `skip_hash_check`

- A function which is used during downloading data.It is a user overriding thing if the data has changed on the remote server or something else would happen.
- **Implemented as a context manager**.

Skip hash sum check:

```python
with remote_data_manager.skip_hash_check():
    myfetch()
```

##### `replace_file`

- User overriding function to download a different file if he knows there is a newer version available.
- **Implemented as a context manager**.

Replace file:

```python
with remote_data_manager.replace_file(name='file1',
                                          shasum='1245645343545343',
                                          url='http://myserver/file1.fits'):
    myfetch()
```

- **Minute:** Any override would effectively create new entries, so we can link it to the original version by a **shared key**.  `Filename` can act as a shared key between the original version and the overridden version.

#### The functions which help in working prototype of  API

##### `compare_hash(file1, file2)`

- Used to compare hash values of two files efficiently.

**Note:** For efficiency we put a check first if the file size is different or not. It will save time for comparing hashing of big files.

```python
def compare_hash(file1,file2):
    if file1_size != file2_size:
        return different file = 1
    else:
        remote_data_manager.get_hash(file1) != remote_data_manager.get_hash(file2)
        return different file = 1
    return same file = 0
```

##### `get_cached_urls()`

- It provides the list of URLs in the cache database used for looking the files which are present in the cache.

```python
def get_cached_urls():
    return the cached urls
```

##### `delete_cache(file)`

- It deletes the cached files along with URLs in cached databse.

```python
def delete_cache(file):
    '''delete the cache'''
    return
```

##### `get_file(file)`

- It provides the file name along with the path of the file. **A association used will make an efficient function like objects which give the file by hash or time stamp**.

```python
def get_file(file):
    return filename determined by the hash function or timestamp
```

- **Note** : remote data manager is a complex function and may require some more supporting function for e.g `valid_url`(implemented in sunpy) , `get_file_size`, `get_hash` etc.

#### Hashing for validation

**Library used:** hashlib

In python hash object of different bits are available for e.g sha1(), sha224(), sha256(), sha384(),sha512(), MD5 . We will use sha1() if we need security because it will sufficient for comparing the validation of file and also not too big. if security value is not so high then **MD5sum will be used because it is more memory efficient and faster to compute.**

```python
import hashlib
m = hashlib.sha1()      '''Secured SHA-160 object'''
     #or
m = hashlib.md5()       '''Not secured but fast'''
def calculate_hash_func(file):
    return hash value of file  '''reading file data upto some buffer'''
```

- **Important:** **Every function which uses remote data will have a hash attached to it to access the remote data.**

**Note:** The **efficient implementation** of above-proposed design will be in the following way:

1. Firstly, the file is downloaded from the remote server by getting **URL** of the data source.
2. Secondly, the file is cached and **database** of cache will be maintained in JSON format.
3. **Use of exception raises for error handling** will be done in the following manner:
   1. If the **`download_file`** function is taking a long time and timeout occurs, an exception will be thrown using try and except statement.
   2. The URLs given in the URL's argument in `require` function are invalid, a URLError will be raised using urllib2 i.e. **urllib2.URLError**.
   3. The client system doesn't have enough space for the downloaded file to cache, an **OSError exception** derived from **EnvironmentError** will be raised.

### Testing and documentation

Documentation and writing tests will be done simultaneously along with each function proposed above. So, completion of each function will involve **writing code for implementation, writing tests for that feature, and documenting that feature**.

# Timeline

| Time Period                                                  | Plan                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| April 23, 2018 - May 13, 2018 (**Community Bonding Period**) | <ul><li> Read documentation and get more familiar with the code base.</li><li> Discuss with mentors and get a final idea of how to approach the project.</li><li>**Get familiar with the urllib, HTTP library , JSON, pytest, Astropy download_file function, AIA response, context manager, FIDO.**</li><li> Read code and get more familiar with the caching mechanism and try to get an idea of what challenges could  arise while implementing the caching mechanism. This is important because **caching mechanism should be efficient.**</li><li>**Discuss with the mentors and get the idea of proposed caching mechanism and also the storage of downloaded data.**</li><li>**Overview of the design and made a functional diagram to implement things**</li></ul> |
|                                                              | **Evaluation1 work starts**                                  |
| May 13, 2018 - May 19, 2018 (1 Week)                         | <ul><li>**Discuss with mentors and set up the structure of cache database:** Structure would be modular and ensuring it is efficient. <li>Implement the function for downloading data .</li><li>Writing documentation and basic test case to check download function. </li><li>**Make a Pull Request.**</li></ul> |
| May 20, 2018 - May 26, 2018 (1 Week)                         | <ul><li>**Integration with master if no issues.**</li><li>**Implement `require` function :**  In **remote data manager** build caching mechanism and all other functions that support it. </li><li>**Integrate** with download function.</li><li>Writing documentation and test to check the cache of download data.</li><li>**Make a Pull Request for review .**</li></ul> |
| May 27, 2018 - June 3, 2018 (1 Week)                         | <ul><li>**Integration with master if no issues .**</li><li>**Implement `get_file` and `compare_hash`function :** Function to get file name as well as path to the will be implemented.</li><li>Writing documentation and basic test case to check  function. </li><li>**Make a Pull Request for review .**</li></ul> |
| June 4, 2018 - June 10, 2018 (1 Week)                        | <ul><li>**Self Review** of Documentation and test cases: **It is important to move to next phase.**</li><li> **Fix Bug** (if any) come from review or any other **advice given by mentor** .</li><li>Prepared things already before the starting of Evaluation 1.</li> |
| **June 11, 2018 - June 15, 2018 (Evaluation 1/Buffer Period)** | **Evaluation 1 deliverables:** <ul><li>Evaluation of the methods proposed and ensuring the **best approach** for storing a local cache of data.</li><li>Implementation of a basic cache and download system , including test and documentation.</li><li>Continue to work on API.</ul> |
|                                                              | <ol><li>**Evaluation1 ends**</li><li>**Evaluation2 work starts**</li></ol> |
| June 15, 2018 - June 27, 2018 (2 Weeks)                      | <ul> <li>**Guidance from Mentors to implement the API for overriding download data**.</li><li>**Implement** `skip_hash_check` and `replace_file` function : Allows user to re-download data .</li><li>Write documentation for the function.</li></ul> |
| June 27, 2018 - July 02, 2018 (1 Week)                       | <ul> <li>Write the test cases for **`skip_hash_check`** and **`replace_file`** function.</li><li>**Make a Pull request for review.**</li><li>**Integrate with master if no issues.**</li><li> **If needed attach hash to above  functions.**</li><li> **Self review again the test and documentation because it is the base for 3rd and 4th requirement**.</li></ul> |
| July 03 , 2018 - July 08, 2018 (1 Week)                      | <ul><li> **Fix Bug upon self review( if present)** </li><li>**Make a Pull request for review.**</li> <li> Fix bug if found upon **mentor review or any other advice given by mentor.** </li><li>Prepared things before the starting of Evaluation 2.</li></ul> |
| **July 09, 2018 - July 13, 2018 (Evaluation 2/Buffer Period)** | **Evaluation 2 deliverables:** <ul><li> Designed a simple and functional API.</li><li>Made a  working prototype of  API support re - download of data and multiple mirrors, including tests.</li></ul><ul><li>Implement the requested changes if still pending</li></ul> |
|                                                              | <ol><li>**Evaluation2 ends**</li><li>**Final Evaluation work starts**</li></ol> |
| July 14 , 2018 - July 21, 2018 (1 Week)                      | <ul><li>**Implement `get_cached_urls` and `delete_cache`function.**</li><li> Documentation and write test cases for  **`get_cached_urls`** and **`delete_cache`** .</li><li>**Make a Pull request for review.**</li><li>**Integrate with master if no issues.**</li></ul> |
| July 22 , 2018 - August 05, 2018 (2 Weeks)                   | <ul><li>**Write Examples for the gallery of how to use the functionality:** It includes to test the  download function by download a file from remote server and then test the replace or re-download functionality of **`remote data manager`** . File will be replaced if data changes on remote server or if file is download from new server. </li><li>Evaluation of **`get_cached_urls`** & **`delete_cache`** by checking the file sizes and write their examples.</li><li>**Make a Pull request for review.**</li></ul> |
| August 06 , 2018 - August 14, 2018  **(Students Submit Code and Evaluations)** | <ul><li>Clean up code.</li><li>**Improve Documentation(Developer)** </li><li> Resolve merge conflicts (if any) and any pending work will be addressed in this time.</li><li>**All previous Pull request Merged after review and feedback.**</li></ul> |
| August 14 , 2018 - August 21, 2018                           | **Mentors submit final student evaluations**.                |
| **August 22**                                                | **Final results of Google Summer of Code 2018 announced.**   |

- **Important**: I will still work on issues of sunpy till **18th April** before community bonding period starts and I will also be active on **RIOT** and for updating the mentors during the coding period I will also write **weekly blog**.

## Software packages to be used

1. **Language:**  `Python`
2. Libraries and modules: ***HTTP client libraries, Checksumming and Caches, sunpy.util.progressbar, json, urllib, contextlib.***

## How I will successfully complete the project

This project interests me a lot and also fits my current skill sets. Also, I have worked on projects which have strict deadlines and high dependencies on other teammates' progress. This makes me confident of completing this project efficiently and smoothly.

Regularity in work and update mentors about work till date is very important for any projects and I will definitely follow these guidelines for my project.  I will also seek guidance if I am stuck at on particular problem. I will make Pull request regularly so that the mentors can keep track of my progress. Also, I will try to make the commit messages and documentation clear and concise to help anyone who works with the code in the future.

For a better idea of my approach,  I will spend time on the project before the coding period starts so that I can hit the ground running as soon as the coding period starts.

Even after the project ends, I will be available if anyone has any questions regarding my code.

## Benefits to the Community

1. Access to data files on remote (HTTP) server.

2. Data Available from the cache if the internet connection is not here and the file is present in the cache.

3. Provide a version control system of remote data so that one version of SunPy always gives the same answer.

## GSoC

#### Have you participated previously in GSoC? When? With which project?

I have not participated in GSoC before. This is the first time that I would be participating in GSoC.

#### Are you also applying to other projects?

**No.** This is the only project and SunPy is the only organization that I have applied for.

## Commitment

I don't have any other internships or work ( I don't plan on having any ) for the summer. I don't have any plans to go on vacation either.

My classes for the new semester will begin around August 1, but I would still be able to give sufficient time for the project as the academic load is very less during the initial few weeks of the semester.  I will be able to spare 40-42 hours for the project per week easily.

Also, because my summer vacation starts on May 1, I will start working on the project early so that I can try to complete the project well before the deadline ( around 2-3 weeks before the deadline ). This will also ensure that any extra unforeseen and time-consuming challenges will be taken care of ( there are also buffer periods to handle this ).

Also, SunPy is the only organization and this project is the only project that I have applied for.

## Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact me at gulshankumar1210iiit@gmail.com.
