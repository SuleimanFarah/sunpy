# Application for GSOC 2015

## Student Information
* **Name:** Dumindu Buddhika Karunathilaka
* **Email:** dumindukarunathilaka@gmail.com
* **Time-zone:** +0530 GMT
* **IRC Handle:** dumindux@irc.freenode.net
* **Github:** dumindux
* **Blog:**
* **University:** University of Moratuwa
* **Major:** Computer Science and Engineering
* **Current year:** Third year
* **Graduation Date:** 2016
* **Degree:** Bachelor of Science in Engineering.

## Project Proposal Information
**Proposal Title:** Improvements to the SunPy Database

### **Abstract:**
The database module provides functionality to users to manage collections of files on disk in a way not reliant upon folder structure and file name. The database allows users to find files on disk by either physical parameters, such as wavelength and time or properties of the instrument such as name and spacecraft. It also allows more complex queries by enabling searches of the raw meta data associated with the files. database module also stops multiple downloads of the same file thus saving bandwidth. This proposed project aims to improve the functionality provided by the current database module implementation by focusing on three major areas.

  1. Integration of UnifiedDownloader code to database search.
  2. Support for relative paths in the database module.
  3. Support all data supported by `sunpy.lightcurve` module in the database.


###**Detailed Description**

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

base path will be stored in sunpyrc file. If there was no base path specified download method will throw an exception.

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

##Timeline
|Period|Description|
|------|-----------|
|Community Bonding Period (April 27 – May 25)|
|May 26 – June 2|
|June 2 – June 9|
|June 9 – June 16|
|June 16 – June 23|
|June 23 – June 30|
|June 30 – July 7|
|July 7 – July 14|
|July 14 – July 21|
|July 21 - July 28|
|July 28 – August 4|
|August 4 - August 11|
|August 11 - August 18|
|August 18 - August 24|

## Code Samples

Code samples of contributions to opensource projects including SunPy.

**SunPy**

Fixed issue #1171 (VSO download filenames have incorrect extension).
* Pull request- https://github.com/sunpy/sunpy/pull/1341

Test cases added for noaa clients in UnifiedDownloader.
* Pull request- https://github.com/sunpy/sunpy/pull/1334

**Tor Project**

A script to create report of the status of Tor default bridges which are shipped with Tor Browser.
* Code- https://github.com/dumindux/TorBridgeChecker/blob/master/tor_bridgecheck.py

A small bug-fix for Stem library.
* Ticket- https://trac.torproject.org/projects/tor/ticket/14628
