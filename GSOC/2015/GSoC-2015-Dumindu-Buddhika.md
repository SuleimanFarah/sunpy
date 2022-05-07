# Application for GSOC 2015

## Student Information

* **Name:** Dumindu Buddhika Karunathilaka
* **Email:** dumindukarunathilaka@gmail.com
* **Time-zone:** +0530 GMT
* **IRC Handle:** dumindux@irc.freenode.net
* **Github:** dumindux
* **Blog:**
* **Blog RSS feed:**

## University Information

* **University:** University of Moratuwa
* **Major:** Computer Science and Engineering
* **Current year:** Third year
* **Graduation Date:** 2016
* **Degree:** Bachelor of Science in Engineering.

## Project Proposal Information

**Proposal Title:** Improvements to the SunPy Database

### **Abstract:**

The database module provides functionality to users to manage collections of files on disk in a way not reliant upon folder structure and file name. The database allows users to find files on disk by either physical parameters, such as wavelength and time or properties of the instrument such as name and spacecraft. It also allows more complex queries by enabling searches of the raw meta data associated with the files. database module also stops multiple downloads of the same file thus saving bandwidth. This proposed project aims to improve the functionality provided by the current database module implementation by focusing on following major areas.

  1. Integration of UnifiedDownloader code to database search.
  2. Support for relative paths in the database module.
  3. Support all data supported by `sunpy.lightcurve` module in the database.
  4. Split database by query into two databases.

### **Detailed Description**

**1. Integration of UnifiedDownloader code to database search.**

The current implementation of database module has direct integration of VSO to download solar physics data. UnifiedDownloader integration will remove the direct integration of VSO from database module and will use UnifiedDownloader for downloading purposes. This adds a unified system for downloading. Following are the initially identified places where UnifiedDownloader should be integrated to database module.

Modify method `_download_and_collect_entries`in Database class. This method is currently responsible for downloading data given a VSO QueryResponse object. UnifiedDownloader integration changes this method.

Modify method `download` in database class. Currently  download method queries from a VSOClient and dowlaods data using the QueryResponse object received. With the integraton of UnifiedDownloader this method will be modified to query from UnifiedDownloader and download data using UnifiedResponse object.

Include method `download_from_unified_query_result` in Database class. Current implementation supports downloading entries from a VSO QueryResponse object. Including this method adds the functionality to download and save to database using UnifiedResponce object.

**2. Support for relative paths in the database module (issue #783).**

This allows a centralized database with multiple users, all referencing a central file store mounted with different absolute paths on each client. As the initial solution only the absolute path will be stored in a `DatabaseEntry`. If a query is run on absolute path then the paths are directly compared to obtain the results. But if the query is run on a relative path then Database entries with the queried relative path as a suffix in the absolute path will be returned.

Following are the points identified for the changes to be made.

`Database.query(Path('/abs/path'))` - search absolutely. When a path is specified starting from a slash or a drive letter the path will be considered as an absolute path. The query will return results with exact path matches.

`Database.query(Path('rel/path'))` - search relative to base path. When a path is specified without starting from a slash or a drive letter the path will be considered as a relative path. The query will return results which have the paths with the specified relative path as a suffix.

`Database.download(…, path='/abs/path')` - This is the current implementations. This will download data with path as the given absolute path

`Database.download(…, path='rel/path')` - absolute path is taken as base_path+relative_path adn use it to download data.

`Database.fetch` - This also operates as the download method mentioned above.

base path can be stored in sunpyrc file. It can also be optionally overridden at the time of the database creation.

`db = Database('sqlite:///', basepath='/path')'`

**3. Support all data supported by the `sunpy.lightcurve` module in the database.**

Current database module implementation does not integrate with lightcurve data. The current database supports database entries to be created from FITS files. But the current database module integration does not support downloading and saving lightcurve type FITS file data. Communicating with the person who is doing lightcurve re-factor project when dealing with meta data will be needed.

Under this phase,

* Meta data related to lightcurve data will be identified.
* Support to download lightcurve data in database module will be added(with UnifiedDownloader).
* Support to save lightcurve meta data in the database will be added.

**4. Split database by query into two databases(issue #917)**

This feature will add the ability to split a database up into two databases by a query: the function will return two databases where one of them contains all the entries that match the passed query and the other one contains all other entries. This function will be very useful if someone needs to divide database entries based on some query.

The high level signature of the function is,
 `split_database(database, database2, *query)`

database2 will be filled with entries that did not match the query while database will have all the entries that match the query.

## Timeline
|Period|Description|
|------|-----------|
|Community Bonding Period (April 27 – May 25)| I would like to utilize this period to go through the SunPy code base(Specially database module, lightcurve module and new UnifiedDownloader code) and solve any misunderstandings/problems by talking with mentors|
|May 25 – June 7 (14 days)|Working on implementing and modifying methods required to integrate UnifiedDownloader to database module.|
|June 8 – June 12(4 days)|Writing tests for the code written earlier. Updating documentation. Re-factoring the code. At this point I will have completed section 1.|
|June 13 – June 26(14 days)|Working on implementing the support for relative paths in database search. Writing test cases to test code for supporting relative paths. At this point I will have completed section 2.|
|June 27 – July 03(Buffer Period 7 days)|Buffer Period for completing any incomplete work. Midterm evaluation.|
|July 04 – July 10(7 days)|Identifying and understanding metadata related to lightcurve.|
|July 11 - July 24(14 days)|Adding support to download lightcurve data and saving metadata in the database.
|July 24 - July 30(7 days)|Writing tests for the code and completing any remaining work from previous week. Completing documentation. At this point I will have completed section 3.|
|July 31 - August 6(7 days)|Working on to implement a method to a split database by query into two databases and writing tests related to that. At this point I will have completed section 4.|
|August 7 - August 17(Buffer Period 11 days)|Finish any remaining work. Improve test coverage. Fix any bugs with the code and finalizing work.|

## Code Samples

Code samples of contributions to opensource projects including SunPy.

**SunPy**

Fix for issue #1171 (VSO download filenames have incorrect extension).

* Pull request- <https://github.com/sunpy/sunpy/pull/1341>

Test cases added for noaa clients in UnifiedDownloader.

* Pull request- <https://github.com/sunpy/sunpy/pull/1334>

Fix for issue #1342(database complains of EIT non-existent wavelengths units)

* Pull request- <https://github.com/sunpy/sunpy/pull/1346>

**Tor Project**

A script to create report of the status of Tor default bridges which are shipped with Tor Browser.

* Code- <https://github.com/dumindux/TorBridgeChecker/blob/master/tor_bridgecheck.py>

A small bug-fix for Stem library.

* Ticket- <https://trac.torproject.org/projects/tor/ticket/14628>

## About me
I am a third year undergraduate student from Department of Computer Science and Engineering, University of Moratuwa, Sri Lanka. I am pursuing a BSc(eng) in Computer Science and Engineering. My first programming language is C. Then I learned Java and then I found Python and fell in love with it. I have been freelancing on Fiverr.com in my free times for over a year with Python(also with Java but mostly with Python) which gave me a good experience in writing different kinds of python programs. I have sometimes helped out my friends who are following other engineering fields(Civil engineering, Mechanical engineering etc) with simple scripts for some of their calculations. I am fluent in SQL and have experience in using git. I have a strong interest in mathematics and algorithms. I am also interested in information security and anonymity(thus Tor Project). I use Ubuntu as the operating system in my computer. I am currently in the last few weeks of my six month internship with Leapset incorporated(www.leapset.com). I am mostly working with Java, JavaScript and databases there. We are building a card swipe based authentication system for their main product.

As most people, I have always fascinated about the sky and astronomy  since I was a kid. I read quite often about astronomy when I was in high school. I find its really wonderful that this project gives me an opportunity to work with something related to an area I fancy about using my skills. I hope this is a great opportunity for me to learn something about solar physics too. Though I always supported FOSS(and use open source software mostly) I haven't contributed in development before. I think this is a good opportunity to begin contributing to open source.
