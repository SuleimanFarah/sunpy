# Organisation : OpenAstronomy

## Sub-Organization: SunPy

## Project : Remote Data in Sunpy



## Student Information

- **Name** : Gulshan Kumar
- **E-Mail** : gulshankumar1210iiit@gmail.com
- **Time Zone** : **UTC**+05:30
- **IRC Handle** : gulshan_mittal
- **Github handle** : [blackeye](https://github.com/gulshan-mittal)





## University Information

- **University** : [International Institute of Information Technology, Hyderabad](https://www.iiit.ac.in)
- **Major:** Computer Science
- **Current Year:** Second Year
- **Expected Graduation Date:** 2021
- **Programme:** Bachelor of Technology (B.Tech) in Computer Science and MS by Research in Computer Science 





## Open Source and Development Experience

Before contributing to **Sunpy** i have not had much Open Source experience but i have experience of working in team project , working at Software level . I often work on Python project and have a good experience of python libraries.

-  Made a **Shopping Portal** in **Python** using flask similar to olx where you can buy or sell products. Use of UML and deploy it by nginx . [Link to Project](https://github.com/gulshan-mittal/Shoppinghome)
-  Made a **Proxy server and a client - server model in Python** using HTTP libraries . [Link1](https://github.com/gulshan-mittal/Proxy-Server) [Link2](https://github.com/gulshan-mittal/Socket-Programming)
- Made a **Bomberman** game using **Python** with **OOP Principles** . [Link to Project](https://github.com/gulshan-mittal/bomberman-game)
- Made a 2-D Pacman Killer game using **OpenGl**. [Link to Project](https://github.com/gulshan-mittal/Packman-Killer)
- Made a 3-D Legend of Zelda game Wind Walker using **OpenGl**. [Link to Repo](https://github.com/gulshan-mittal/Wind-Walker-3D-Zelda-Game) 
- Made a Extreme Tic Toe Bot using **Python** . [Link to Bot](https://github.com/gulshan-mittal/Extreme-Tic-Tac-Toe)
- Build a State Restoring Quiz Game in **Ruby on Rails**. Modify the Project and conduct **Cache-in IIIT-H Felicity Buzz Event** where number of people registered on it. [Link to Project](https://github.com/gulshan-mittal/State-Restoring-Quiz-game/tree/master/Quiz-game)

**Development Experience** : Mobile App Developer Intern at Statwig, T-Hub ,IIIT Hyderabad .Made a Project Toad App similar to **Google Calendar** .  Amazon **Alexa** developer and **Google Assistant** developer.

**GitHub Handle** : [blackeye](https://github.com/gulshan-mittal?tab=repositories)

**Operating System Experience:** I am using currently **Ubuntu** . I have also use fedora, linux mint and Windows.

**Programming Experience** : Proficient in C, C++ , Python.

Apart from these also proficient in **javascript**. Experience of shell scripting also.



## Pull Request & Issue

- [hgs_to_hcc(heliogcoord, heliocframe)](https://github.com/sunpy/sunpy/issues/2470) **`closed`**
- [hgs_to_hcc(heliogcoord, heliocframe) : Convert from Heliographic Stonyhurst to Heliograpic Carrington](https://github.com/sunpy/sunpy/pull/2502) **`merged`**
- [Add Heliocentric --> Heliocentric transformation Issue ](https://github.com/sunpy/sunpy/pull/2469) **`closed`**




## Project Proposal

**Project:** Remote Data in SunPy

**Mentors** : [Stuart Mumford](https://github.com/Cadair), [Will Barnes](https://github.com/wtbarnes), [David Pérez-Suárez](https://github.com/dpshelio)



### Abstract

Some functionality in SunPy or in affiliated packages is going to need access to **data files on remote (HTTP) servers**. Examples of this include data provided by instrument teams relating to the calibrations or performance of the instruments, this kind of data are highly likely to change with time.

This project needs to be designed and implemented under the assumptions that SunPy **has no control over the data** on these servers, and that files on the servers may be replaced with different files with the same name. This functionality will therefore have to validate the retrieved files have the expected hashes, while providing ways for users to override this hash if they are aware of changes on the remote server.

There are many requirements for this project. Data is **download and cached** to `$HOME/sunpy/data/...` when first needed. There is some validation that the data has been **transferred correctly** (sha hashes etc). There should be a mechanism by which we can allow users to **re-download data.** The download code supports **multiple mirrors**.  



### Motivation

Functions in sunpy are going to need datafiles present on remote server to work and as of now there is no proper system to control remote data so there is a need to design system which could meet with the requirements of remote data in sunpy. There are some issue in sunpy which push me to design and build the remote data manager.

1. In **`download_file`** function which is currently used to download data for tutorials taken from [astropy](http://docs.astropy.org/en/stable/api/astropy.utils.data.download_file.html?highlight=download) doesn't support the override mechanism to download data.Also it **doesn't **meet with multiple mirror requirement if data is not present on one server. Motivation from  [Issue 1809](https://github.com/sunpy/sunpy/pull/1809).
2. There is some part of **`AIA`** response function which is varying with time. Right now the instrument info (e.g. reflection coefficients of mirrors, gain of CCD, quantum efficiency of CCD) are read straight from the .genx files in SSW. When user create an instance of the response class, he/she can choose a path to his/her  SSW install and the version of the instrument file he/she want (the default is 6). As of now, the problem how to either pull down this info from somewhere or store it (and version it somehow) 
   has not been solved. The calculated response function is up to date depends on the instrument teams keeping the files in SSW up to date, the users local SSW install being up to dateand the user selecting the newest version (since older versions are kept in SSW) . This is **not a good** idea to purposed.Motivation from [Issue 1897](https://github.com/sunpy/sunpy/pull/1897).
3. **Time out** error if data from the remote server exceeds time limit.




### Project Goals

**Part1** : Evaluation of the methods proposed and ensuring the **best approach** for storing a local cache of data. There should be implementation of a basic cache and download system , including test and documentation.

**Part2** : Design of a simple and functional API and have worked with my mentors and community for better understanding and implementing the design efficiently.The working **prototype** of this API also have to be done including its **tests**. 


### Deliverables

1. **Cache and download system** along with its test and documentation. 
2. **Simple and functional API** and its working prototype. Written examples for the gallery of how to use the functionality.
3. **Developer documentation** for the understanding of functionality. All the work should be done in a manner that Pull request should be merged after **review and feedback**.


### Detailed Description

#### Requirements elicitation

1. The first requirement is data is downloaded and cached to **`$HOME/sunpy/data...`**  when first needed. It is the folder that made automatically when you build the sunpy poroject. (Inside the data folder currently there are fts and fits  files and `sample_data` folder which also contain fits , txt , pha files.)
2. The second requirement is a quite interesting and i put it as a  **high priority** requirement.In this there is need do some **validation** that the data has been transferred correctly.It can be done using **cryptographic hash function**. But here one question arises that if the data on the remote server has changed (consciously due to calibration change) and we have stored a sha hash in the code , then our downloads will start to gave errors and the only way to fix for this approach is to do a new Sunpy release with a bug fix. The alternative is to not store hashes and just assume the data is what we anticipated and roll with it. It would be better to pin the version of data to the code, it means that in theory as long as the **remote data is available one version of SunPy will always give the same answers**. (Same code same data).  A mechanism to skip download verification if the user knows what they are doing can also be used here. Also here in this project we are dealing with random data on the internet so there is no way to persuade the provider to version their data properly. Need of **efficient mechanism** to tackle this problem is needed.
3. Mechanism by which users can be allowed to **re-download data** . 
4. The download code supports **multiple mirrors**. 



### Design and Implementation

#### Caching

We need to cache  the downloaded data in a effective manner. We will use `remote_data_manager` which maintains a record of the cache and can provide many feature like getting the hash value, getting the  file etc. The code inside sunpy would ask for a given file name at a given url with given hash. Define a function named `myfetch()` that need some data :

```python
@remote_data_manager.require(name='file1',
                             urls=('https://server1/file1.fits', 'http://server2/file1.fits'), 
                             shasum='1245645343545334')
def myfetch():
    filename = remote_data_manager.get_file('file1')
```

This adds the function name to the cache, and the files, when the code is run the downloader goes out and gets the file, verifies that it matches the provided hash using `compare_hash()`function of `remote_data_manager`and it puts it in a folder which probably has the function name in it, and then gives it to the function on request. **If a file already present in cache then it simply gave the path to the file without downloading**.

**Note:** `comapre_hash()` function will be implemented in `remote_data_manager` class . Along with it we have to use 

Cache will be maintained on a disk in the form of **json** (javascript object notation). The given ***json below*** describe how the cache database will look like , how it allows to override the hash check and replace the file.

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
            "urls": [
                "https://server1/file1.fits",
                "https://server2/file1.fits"
            ]
        },
        ".......... other file caches belongs to same name"
    ]
 }
```
Here, **fetch_hash** will be fetched  by `get_hash`  function or hash attached with the file in remote_data_manager class, **default_hash** i assume it is the hash which i know for comparing or it is the hard coded hash.**List_cash** maintains the list of  cache of files having same **shared key** which is file name. 

**Note**: We are also caching the older version of data. 


### Storage and Download

- ***Storage :*** The file will be saved in the folder  `$HOME/sunpy/data/…` and the **name of the file determined by hash or time stamp ( `created at` field in the cache  json)** .
- ***Download :***  For downloading data  we are using `remote_data_manager` which uses downloading function for example  **`download_file`**  or implementation of new function can be made . In  **`require`** function as stated above will have a **time out** parameter , **show_progress bar** (default value `true` in astropy download dunction) as well. 
- **The downloaded data is cached and stored safely and efficiently.**


### Function in Remote data manager

##### `skip_hash_check`

Function which is used during downloading data.It is a user overriding thing if the data has changed on the remote server or something else would  happen.

Skip hash sum check:

```python
with remote_data_manager.skip_hash_check():
    myfetch()
```



##### `replace_file`

User overriding function to download a different file if he knows there is a newer version available.

Replace file:

```python
with remote_data_manager.replace_file(name='file1',
                                          shasum='1245645343545343',
                                          url='http://myserver/file1.fits'):
    myfetch()
```


- **Minute:** Any override would effectively create new entries , so we can link  it to the original version by a **shared key**.  `Filename` can act as a shared key between the original version and the overriden version.







#### The function which help in working prototype of  API:

##### `compare_hash(file1, file2) `

- Used to compare hash values of two files efficiently.

**Note :** For efficiency we put a check first if the file size is different or not. It will save time for comparing hashing of big files .

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

- It provides the list of urls in the cache used for looking the files which are present in the cache.

```python
def get_cached_urls():
    return the cached urls 
```



##### `delete_cache(file)`

- It deletes the cache by deleting files.

```python
def delete_cache(file):
    '''delete the cache'''
    return 
```



##### `get_file(file)`

It provides the file name along with the path of file. **A association used will make a efficient function like objects which give the  file  by hash or time stamp**. 

```python
def get_file(file):
    return filename determined by hash function or time stamp
```

- **Note** : remote data manager is a complex function and may require some more supporting function for e.g `valid_url`(implemented in sunpy) , `get_file_size`, `get_hash` etc.





#### Hashing for validation

**Library used :** hashlib 

In python hash object of different bits are available for e.g sha1(), sha224(), sha256(), sha384(),sha512(), MD5 . We will use sha1() if we need security because it will sufficient for comparing the validation of file and also not too big. if security value is not so high then **MD5sum will be used because it is more memory efficient and faster to compute.** 

```python
import hashlib
m = hashlib.sha1()  				'''Secured SHA-160 object''' 
    	#or 
m = hashlib.md5()  					'''Not secured but fast'''
def calculate_hash_func(file):
    return hash value of file		'''reading file data upto some buffer'''	
```

- **Important :** **Every function which uses remote data will have a hash attached to it to access the remote data.**






**Note:** The **efficient implementation** of above proposed design will be in the following way:

1. Firstly File is downloaded from the remote server by getting url of data source.
2. Then file is cached along with a cached json where we update the url field.
3. **Also exception raises will be used for error handling.** 





### Testing and documentation

Documentation and writing tests will be done simultaneously along with each function proposed above. So, completion of each functionality will involve **writing code for implementation, writing tests for that feature, and documenting that feature**.



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



- **Important** : I will still  work on issues of sunpy till **18th April** before community bonding period starts and i will also be active on **RIOT** and for updating the mentors during coding period i will also write **weekly blog**.  




## Software packages to be used

1. **Language:**  `Python`
2. Libraries and modules: ***HTTP client libraries, Checksumming and Caches, sunpy.util.progressbar, json, urllib, contextlib.*** 





## How I will successfully complete the project:

This project interest me a lot and also fits my current skill sets. Also, I have worked on projects which have strict deadlines and high dependencies on other teammates' progress. This makes me confident of completing this project efficiently and smoothly.

Regularity in work and update mentors about work till date is very important for any projects and i will definitely follow these guidelines for my project.  I will also seek guidance if I am stuck at a particular problem. I will make Pull request of code regularly so that the mentors can keep track of my progress. Also I will try to make the commit messages and documentation clear and concise to help anyone who works with the code in the future.

For a better idea of my approach,  i  will spend time on the project before the coding period starts so that i can hit the  ground running as soon as the coding period starts.

Even after the project ends, I will be available if anyone has any questions regarding my code.



## Benefits to the Community

1. Access to data files on remote (HTTP) server.

2. Data Available from the cache it the internet connection is not here and file is present in the cache.

3. Provide a version control system of remote data so that one version of SunPy always gives the same answer.




## GSoC

#### Have you participated previously in GSoC? When? With which project?

I have not participated in GSoC before. This is the first time that I would be participating in GSoC.



#### Are you also applying to other projects?

**No.** This is the only project and SunPy is the only organization that I have applied for.




## Commitment

I don’t have any other internships or work ( I don’t plan on having any ) for the summer. I don’t have any plans to go on vacation either.

My classes for the new semester will begin around August 1, but I would still be able to give sufficient time for the project as academic load is very less during the initial few weeks of the semester.  I will be able to spare 40-42 hours for the project per week easily.

Also, because my summer vacation starts on May 1, I will start working on the project early so that I can try to complete the project well before the deadline ( around 2-3 weeks before the deadline ). This will also ensure that any extra unforeseen and time consuming challenges will be taken care of ( there are also buffer periods to handle this ).

Also SunPy is the only organization and this project is the only project that I have applied for.



## Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact me at gulshankumar1210iiit@gmail.com .