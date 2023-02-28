# Organization: OpenAstronomy

## Sub-Organization: SunPy

### Student Information

Name: Pulkit Gera
Time     Zone: +0530 GMT
IRC Handle: darthgera
Github ID: darthgera123

### Education

Currently a sophomore at IIIT Hyderabad. Im enrolled in Btech in Computer Science with MS by research in Computer Science. Expected graduation by August 2022.

### University Information

University: IIIT Hyderabad
Major: Computer Science & Engineering
Current year: 2nd
Graduation date: August 2022
Degree: Bachelor of Engineering +MS by Research(Dual Degree)

### Pull Requests

The following are my Pull requests both open and close -
<https://github.com/sunpy/sunpy/pull/3015> - Mock data added on test_fermi_gbm
<https://github.com/sunpy/sunpy/pull/2891> - Replaced os with pathlib in test files #2891
I will keep contributing and working on more pull requests.
I use Elementary Os for the past 2 years now.I am also familiar with Git and SunPy workflow.

### Proposal abstract

The proposal is on the project **“Remote Data in SunPy”.** The idea is the some functionality in  in SunPy or in affiliated packages require  access to data files on remote (HTTP) servers. Some of them include AIA response functions in, where we need to include data provided by instrument teams relating to the calibrations or performance of the instruments, which are highly likely to change with time.I propose that we use parfive to download the data.The project requires building of a remote_data_manager which basically can do the following-

* Download and cache the files from remote HTTP/FTP servers.It should also be able to
* Store the hash and check with the server if the current data is upto date. If its behind, then it needs to be updates
* It should be able to be called by the user, if they want to update/ re-download the data
* The download should support multiple mirrors
* Provide a version control for data in SunPy . The idea is that previous instances of data must be present for the user to use at convenience.

### Implementation

**Idea**
The idea here is that we already have parfive, a asyncio downloader integrated into sunpy recently. It is a powerful library for downloading parallely and is now included in the last Sunpy release. Parfive therefore forms the core of the Remote data manager downloading.
Once the data is downloaded, we can now cache the data on the disk and store the metadata on a sql database, which can be easily accessed through sql-alchemy.
We also are able to mirror download the data through parfive. Not only that we could implement downloading by parts in parfive so that we can speed up the downloading process.

***

**Diagram**

![UML Diagram](https://lh3.googleusercontent.com/MQppHDRokVs1Z7cJ82NfiNjKuh809zGovKvx_rg_vqh5CgFUs9z5dV1z1dKZ8iodOdDZweWv1494QrNUzn51TpxOEmqQlR9Ff_24z8vtAysNrbRG6_3FyPzZGEqAf1jpvOZ-5zc)

***

**Cache**
We would be using sqlite for storing metadata about the files upon downloading. The metadata will be interacted using sqlalchemy which is designed for efficient and high-performing database access, adapted into a simple and Pythonic domain language.  The reason we use sqlite is because its very fast to make subset queries such as on date very fast and is very reliable. It would be used along with sql alchemy which makes querying incredibly easy and safe.
This will be retrieved back  through jsonify in the following form

 `[
     {
         "file_name": "file1",
         "function_name": "func1",
         "version":"v1",
         "urls":[
             "url1","url2"],
         "skip_hash":"no",
         "shasum":123,
         "created_at":"<some timestamp>",
         "last_modified":"<some timestamp>",
       “last_used”:”<some timestamp>”,
     }
 ]`

The various fields are explained as follows:-

* File_name: Name of the file
* Function_name: The function in the file. Its under the impression that one file will have one function as we dont want to interfere with other function within the same file's data.
* Version: It contains the version which it has. The originally downloaded will be referred as 1 and every subsequent override will be updated and stored.This will be used for versioning of the data.
* Skip_hash: This will be used to identify whether the hash of the downloaded file needs to be checked after downloading or not.
* Last_modified: This will be used to request a file with a different modified time.
* Last_used:whenever it is last_used

Beyond this, we would need to implement locking mechanism in order to maintain data integrity of the json objects returned.Two functions namely def lock_cache() and def unlock_cache() will be used.
Here's the basic procedure:

* Check the cache for the file, return if its available
* If the file is not in the cache, then implement a lock
* Inside the lock, check the cache again, you might have been blocked
* Use the file and cache it
* Release the lock
The locks will be implemented using the `threading` module.

***

**File Storage**
The files will be stored in
`./sunpy/data/function_name/name`

The name will be hashed as a combination of function name and last modified which will give a unique name to it.

`import hashlib`
`cached_file_name = hashlib.md5(file_name + modified_at+version_name).hexdigest()`

***

**Remote Data Manager**
The remote_data_manager will be implemented as a factory with multiple functionalities. It includes checking of hashsum,caching of files, fetching of files from cache,etc. The following are the functions:

`@remote_data_manager_add_to_buffer`
This will basically add the file, function name to the cache. When the function is called, it will check the cache. If hit, do nothing, else download,verify the hash and add to cache.The idea is that it is responsible for providing the files to other functions.
`def read_file_obj()`
This will basically read and return the contents of the file after it fetches from the buffer mentioned above. The user doesnt have to worry about the file descriptors

`def ret_file()`
This will be implemented as a context manager where we return the file contents.

`def replace_file()`
This will update with the newest version of the file but not remove the previous version of the default file.This will be implemented as a context manager and have **kwargs argument where if skip_hash is to be set

`def clear_cache()`
This will clear the disk if it exceeds limit. This function will also be accessible through API.

`def remove_last()`
In case disk memory is full, we check the last_used timestamp and remove the file

`def get_file_hash()`
Get file with some hash value.

`def get_latest_file()`
File with latest data.

Other functions include some helpers such as `is_valid_url`,`lock_cache`,`unlock_cache`,etc.

***

**Mirroring**
Currently there is no retry with different urls feature in parfive which makes it a poor choice for mirror downloading. However, this problem can be solved with by a simple hack through which we could make parfive work with multiple urls therefore making it a good candidate for downloading multiple mirrors.

As specified in PR #2993 with this simple hack and extrapolating further, the remote data manager would support downloading mirrors.

`dl = parfive.Downloader(overwrite=overwrite)`

***

**Error Handling**
The implementation of remote_data_manager would require error handling of errors and a pipeline since we are dealing with a lot of files. The function replace_file would be implemented as a context manager.

The pipe line would involve:-

* Obtain the remote url of the data source
* Check the file cache and if not present download the file from remote server
* Update the File cache

In cases where the remote server is  down, it would first check the cache again. If there exists an instance where old data is present it would proceed with that and inform the user. If no old version is present it would then it would throw an exception informing the user about server being down.

Exhaustive error handling will be done at each instance to ensure it doesn't break down.

### Software packages to be used

`json,urllib, threading, contextlib, parfive, hashlib, pytest, sqlalchemy`

### Additional Tasks

Since all other data are downloaded through parfive, we could extend the caching mechanism in the same way. Though the rest require custom urls, we can use the same caching mechanism and optimize the search process even further. Also we could cache the urls as obtaining the urls each time is another overhead. This would optimize the process even further. A file whose url is cached will be cached and therefore we only need to check the urls to see if a file is cached.

### How I propose to complete this project

I have been contributing to SunPy since January and have been in constant touch with the mentors (Nabobalis and Cadair). I am comfortable around with the code base now and with solving more issues, i feel ill be fully comfortable with the testing part. I have regularly completed projects in my college within a week where in I have had no prior knowledge about the concepts involved, which I believe has given me the skill and confidence to complete this project satisfactorily.
I would push my work to the remote work as and when I complete, so that mentors could review my work and give their feedback.I would be in constant touch with the mentors

### Deliverables

The following are the deliverables for the project:

* Implement a cache system
* A ​ Remote Data Manager​ with the following basic features:
>
> * Validate the downloaded file by checking its checksum
> * Caching a given remote data file
> * Mechanism to allow the user to override the cache
> * Allow download from multiple mirrors
>
* Allow multiple downloads to happen in parallel
* API to access​ the Remote Data Manager
* Write tests and documentation
* Add ​ examples on using the module to the ​ example gallery (​ 1 or 2 jupyter
* notebooks​ )

### Benefits to The Community

The project offers several benefits to the community.
● It would provide a ​ version control system of remote data so that one version of
SunPy always gives the same answer
● It would allow the user to work with an ​ earlier version of data file even if it has
modified​ in the remote server
● It provides a ​ caching mechanism so that the user need not download a file that
is already present with them

### Timeline

Note: I would be writing documentation, tests and doctests along with writing the code for the module proposed in the project. This would make sure that mentors are able to understand my ideas lucidly, to ensure correctness and ease of maintainability. I would be opening PRs regularly so that SunPy developers can review my code and provide valuable feedback. I would also be pushing regularly to my own fork so that mentors can keep track of my progress.
**Community Bonding Period (May 7 - May 26)**
My vacations start on May 3rd. So I would like to code at least a small part during this period.
I am familiar with most libraries that are going to be used and have a good idea about the python features that will be used like context managers and decorators. These are the following tasks I plan to do-

* Get familiar with certain aspects of codebase like parfive, net, timeseries, FIDO,AIA
* Finalize the cache structure and organization
* Finalize on what sort of checksum to use(md5/sha)
* Versioning the files
* Completing the API design
* Learning about context managers, decorators, tox in detail.

**Coding Period Begins**

**Week 1 (May 27 - June 2)**

* Write helper functions like lock_cache,unlock_cache to ensure data_integrity.
* Write other functions such as clear_cache(),etc.

**Week 2 - Week 3 (June 3 - June 16)**

* Start working on the various functionalities such as @add_to_buffer, read_file_obj.ret_file.
* Write tests for them.

**Week 4 - Week 5 (June 17 - June 23)**
The main idea is to get a working remote_data_manager working by the end of this period which has caching and download functionality completed. It will also act as a buffer period to complete any other tasks or issues.
Also will write documentation for the code as well as complete the tests.

***

**Phase 1 Evaluation**

***

**Week 6-7 (June 25 - July 7)**

* Review API design and make required changes. Keeping in mind scalability.
* Implement replace_file function to allow overide
* Write functions which query the cache on last modified version, whose hash was mentioned,etc

**Week 8 (July 8 - July 14)**

* Implement mirror downloading with parfive.
* Complete the tests for the API
* Add documentation for the code written till now

**Week 9 (July 15 - July 21)**
This period will act as a buffer. Will complete any pending work during this time.

***

**Phase 2 Evaluation**

***

**Week 10 - Week 11 (July 23 - August 6)**

* Complete remaining functions such as remove_last,etc
* Complete testing for API
* Finish up any remaining testing and documentation.
* Begin working on the jupyter notebooks that would be added to the example gallery

**Week 12 - Week 13 (August 7 - August 25)**

If all went well, by this time I would be done with my work. During this time I would propose on doing additional task such as extrapolating the project to other clients and making it as a common remote_data_manager. This would ensure optimizing the time for all the clients. Otherwise this would act as a buffer period for finishing any leftover tasks

* Complete written documentation
* Add necessary developer documentation
* Remain in touch with mentors over potential bug fixes and issues that are unresolved which I would resolve.
* Hopefully get the work merged with the master branch of Sunpy

***

**Final Evaluation**

***

### About Me

Hi, my name is Pulkit Gera. I go by the nick darthgera on Riot and darthgera123 on github. Im currently a sophomore in IIIT Hyderabad. Im pursuing a Bachelors + MS by Research in Computer Science.
My interests include programming, open source and reading blogs. I started contributing to open source in my first year itself by resolving some issues for Hacktoberfest. Some of the projects Ive worked on are as follows-

* Developed College E-Cell website using Django
* Developed a Quiz Portal using React and Go
* Developed a Shell in C
* Developed a 2D game(Jetpack Joyride) in OpenGL
* Developed a 3D airplane simulation in OpenGL
* Developed a Proxy Server in Python
* Developed an AI bot playing ultimate tic tac toe using alpha beta pruning
These projects are all on my [github](https://github.com/darthgera123)
I came across Sunpy via going through a friend of mine's contributions and found the project a bit unusual. After contributing to it, I really liked the mission. I enjoyed going over other PR's to get a hang of it along with keep myself updated.The thing I like most about Python is how easily you can hack/prototype things, with such smooth ease. Interning with SunPy would strengthen my skills in Python and also make me a better developer and give me insight to a scientific libraries.
When Im not programming, either Im following Man Utd or playing badminton

## GSOC

### Have you participated previously in GSoC? When? With which project?

No, this is the first time I am participating in Google Summer of Code.

### Are you also applying to other projects?

No, OpenAstronomy(SunPy) is the only organisation I am applying to.

### Are you eligible to receive payments from Google?

Yes, I am eligible to receive payments from Google.

### How much time do you plan to invest in the project before, during, and after the Summer of Code?

I don't have any other internships or work ( I don't plan on having any ) for the summer. I don't have any plans to go on vacation either. My classes for the new semester will begin around August 1, but I would still be able to give sufficient time for the project as academic load is very less during the initial few weeks of the semester. I will be able to spare 35-40 hours for the project per week easily.
Also, because my summer vacation starts on May 3, I will start working on the project early so that I can try to complete the project well before the deadline ( around 2-3 weeks before the deadline ). This will also ensure that any extra unforeseen and time consuming challenges will be taken care of (there are also buffer periods to handle this).

### Will you continue contributing to SunPy after the Summer of Code too ?

Yes, I will keep contributing to SunPy after the Summer of Code too.

### Eligibility

Yes, I am eligible to receive payments from Google. For any queries, clarifications or
further explanations, feel free to contact​ ​ pulkit.gera@research.iiit.ac.in
