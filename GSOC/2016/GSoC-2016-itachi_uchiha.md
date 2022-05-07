## Organization: OpenAstronomy

## Sub-Organization: SunPy

## Student Information

* **Name:** Punyaslok Pattnaik
* **E mail:** punyaslok.pattnaik@gmail.com
* **Time Zone:** +05:30 GMT
* **IRC Handle:** itachi_uchiha
* **Github Username:** [Punyaslok](https://github.com/Punyaslok)
* **Blog :** [My Blog](https://punyaslokpattnaik.wordpress.com)
* **Blog RSS feed :** <https://punyaslokpattnaik.wordpress.com/feed/>

## University Information

* **University:** [International Institute of Information Technology, Hyderabad](https://www.iiit.ac.in)
* **Major:** Computer Science
* **Current Year:** Second Year
* **Expected Graduation Date:** 2019
* **Programme:** Bachelor of Technology (B.Tech) in Computer Science and MS by Research in Computational Natural Sciences (Dual Degree)

## Work and Open Source Experience

I haven’t had much Open Source experience before contributing to SunPy, but I have experience working in team projects, especially involving python.

* Made a 2D cannon shooting game using OpenGL [Repo link](https://github.com/Punyaslok/OpenGL-2D-Game)
* Made a 3D obstacle course maze game using OpenGL  [Repo link](https://github.com/Punyaslok/3D-Obstacle-Game)
* Made a Bidding Portal using web2py for easy auctioning of items, primarily to help departing students sell off bicycles, air coolers etc.  [Repo link](https://github.com/Punyaslok/Bidding-Portal)  [Deployment Link](http://punyaslokpattnaik.pythonanywhere.com/Bidding_Portal)
* Made a Donkey Kong game using pygame, and also tested it using pytest [Repo link](https://github.com/Punyaslok/Donkey-Kong-Game)
* Handled the django backend part of a team project, which involved building a social networking site, aimed at movie lovers. The site had a django backend, and an AngularJS frontend. The code for this project is confidential.

**My github url :** [Punyaslok](https://github.com/Punyaslok)

**Operating System Experience:** Currently, I use Ubuntu. I also use Arch Linux and Windows.

Apart from the above projects, I am also proficient in C/C++ and I love sport programming.

## PR links

* **Astropy**
* [Removed discussion of Keyword class in Getting Started section.](https://github.com/astropy/ccdproc/pull/296)
* **SunPy**
* [Implemented feature request: split database by query into two databases](https://github.com/sunpy/sunpy/pull/1700)
* [Database(default_waveunit) should take a Unit](https://github.com/sunpy/sunpy/pull/1701)
* [Download and fetch both accept kwargs now.](https://github.com/sunpy/sunpy/pull/1719)
* [Fixed the test_add_entry_from_hek_qr test](https://github.com/sunpy/sunpy/pull/1717)

## Project Proposal Information

**Project:** Improvements to the SunPy Database

**Mentors :** [Stuart Mumford](http://github.com/Cadair), [Simon Liedtke](http://github.com/derdon), [Steven Christe](http://github.com/ehsteve)

### Abstract

The SunPy database module enables users to manage files on a disk, or a network hosted database. Users can find files by using physical parameters such as wavelength, time etc. or by using attributes such as instrument name. Queries can also be combined to form complex queries.

The database module also acts as a proxy and can handle downloading files from different clients. It takes queries and if the user wants to download files, the database makes the query and downloads the files, with the option of the user specifying the download path. It also has a caching mechanism so that if a same download query is made the second time, the files aren’t redownloaded.

The first part of the project would involve making several modifications to the database module used by SunPy to integrate the Fido interface with the database which will enable users to use only the Fido to make queries, instead of making separate queries for separate clients like VSO, LightCurve etc. Currently in the internal working of the database uses VSO queries, VSO download methods etc. So, for different individual clients like LightCurve, the user has to supply separate queries. *So, using the Fido store and query in the database, we can store many types of data in the database. Currently, only VSO and HEK data can be stored in the database.*

The second part involves improving the caching mechanism. Currently, the caching system uses queries to decide whether a file needs to be downloaded. So, if two queries have largely similar results, they both are completely downloaded.

### Project Goals

**Part 1 :** Use Fido to replace VSO for doing internal database operations, primarily to achieve the goal of being able to store different formats of data in the database. **This will create the ability to quickly support more and more data types in the future as support for each type can be added by creating relevant sub-classes.**

**Part 2 :** Improve caching mechanism to eliminate downloading files that are already downloaded as part of a different query.

### Deliverables

1. **A fully functional database module** which will use the Fido attributes and will not be restricted to separate queries for VSO, HEK etc. The database should retain all its current abilities/features while using Fido. This involves querying, adding and downloading to the database.
2. **A new caching mechanism** for the database that improves performance in case of overlapping query results. This will be achieved by checking results of queries to eliminate duplicate downloads. The earlier model used to check only saved queries while caching. So, if 2 queries had a slight difference in downloaded files, with a large number of same results, there was no match and the overlapping queries were downloaded again.

### Detailed Description

**Part 1**

I would divide this part of the project into 4 broad subparts.
In sequence, they go like this:

1. **Adding with Fido**

   Successfully add entries to the database from a Fido search result. Currently, client-specific functions like `Database.add_from_vso_query_result()` are used to add entries. Implement functionality such as `Database.add_from_Fido_result()` that will add the results of the `QueryResponse` object returned by the underneath client.

2. **Querying with Fido**

   Currently the `Database.query()` function supports querying inside the database only by using VSO attributes (although other “Database module” specific attributes such as `tag`, `star` etc. are supported). So, now in the first step of implementing Fido, `Database.query()` should support querying using Fido attributes. This will remove the constraint of being able to use only VSO attributes for searching data.

3. **Downloading with Fido**

   Given a Fido search query, download the relevant files from the client which Fido decides can best serve the query. This will involve downloading files from different clients for different types of queries. All files from all clients must be downloaded successfully.

   There will be many file types which will be returned by different clients. Currently the database module handles FITS file types pretty well. So, in order to store metadata of other file types such as `ana`, `jp2` etc. a new feature can be implemented which will allow newer file types in the future to specify their metadata format and hence they can be easily stored in the database.

   Also, it would be better if a mapping is created which relates each client to its possible file types, which could allow the caching mechanism to become even faster while searching for data of a particular client in the future.

4. **Miscellaneous**

1. Test the database module again to ensure that all functionalities such as `tag`, `star`, `undo` etc. work fine after integrating Fido.
2. Make the database module pass quantified code checks (optional)

**Note :** Documentation and writing tests will be done simultaneously along with each subpart. So, completion of each subpart will involve writing code for implementation, writing tests for that feature, and documenting that feature.

Specifically speaking, after implementing Part 1, the database will be able to take queries like `Fido.search(attrs.Time("2012/1/1", "2012/1/2"), attrs.Instrument('lyra'))` and decide which client can best serve the query and automatically handle adding to database, downloading files etc.

For example, currently we have to use specific queries like `vso.VSOClient().query(vso.attrs.Time('2001/1/1', '2001/1/2'), vso.attrs.Instrument('eit'))` for VSO and `hek.HEKClient().query(hek.attrs.Time('2011/08/09 07:23:56', '2011/08/09 12:40:29'),  hek.attrs.EventType(‘FL’))` for HEK.

**Part 2**

This part would mainly involve changing what items are stored in the cache. Now, instead of queries, the all the results that a query returns will be stored in the cache. This will involve changing the JSON format in order to store a query result. Also, along with that, encoding and decoding that new JSON will have to be done.

Now, for the cache to work, it has to be ensured that whenever a query is made through Fido, pre-existing same query results in the cache are matching correctly with the query results obtained from the Fido search. So, while downloading files, those files will be skipped whose query result entries are already in the database. All query results from all supported clients must be matching correctly.

**Note : Updates will be scheduled to the database package in small sections, rather than in one large pull request. These updates will be separate PRs for each independent feature. The updates schedule is included in the timeline.**

**Note : Apart from the PRs/updates, I will push code regularly to my github fork regularly so that my mentors can keep track of my progress.**

## Timeline

| Time Period        | Plan           |
| ------------- | ------------- |
| April 22, 2016 - May 22, 2016 **(Community Bonding Period)**      |   <ul><li>Read documentation and get more familiar with how Fido works.</li><li>Discuss with mentors and get a final idea of how to approach the project.<li>**Get familiar with the various clients that Fido would be supporting and also understand how each client’s query is different from other clients and how to download data from each client.** This is important because later on one common query will have to be assigned to a client automatically, and downloads from that particular client will be made.</li><li>**Discuss with mentors and get a final idea of which client will serve which kinds of files and decide how the metadata of each file type will be stored in the database. Also finalize how to store metadata of any file types which are not currently supported ( maybe create an additional feature that will allow easy additions of new file types’ metadata to the database in the future ).**</li><li>Read code and get more familiar with the caching mechanism and try to get an idea of what challenges could possibly arise while implementing the new caching mechanism. This is important because query results of multiple clients will be stored in the cache.</li></ul>|
| | **Part 1 starts** |
| May 23, 2016 - May 29, 2016 ( 1 week ) | <ul><li>**Implement adding the Fido records to the database.**</li><li>Ensure that functionalities like `display_entries` etc. are working. Cross check by adding entries using specific client methods (the old way).</li><li>Document and write tests for adding while using Fido.</li><li>**Update 1 : Push code which will enable the database to accept Fido records/entries.**</li></ul> |
| May 30, 2016 -  June 12, 2016 ( 2 weeks ) | <ul><li>**Implement querying with Fido.** Ensure that the different clients are recognized correctly and correct results are returned. Cross check by using custom queries for each client.</li><li>Write tests for querying with Fido.</li><li>Document querying with Fido.</li><li>**Update 2 : Push code so that querying inside the database is successfully done using Fido attributes.**</li></ul> |
| June 13, 2016 - June 20, 2016 ( 1 week ) | <ul><li>**Implement downloading files for VSO and HEK queries after querying database.**</li><li>Ensure that the correct files from the correct clients are being downloaded by checking using the old separate download functions.</li></ul> |
| **June 21, 2016 - June 28, 2016 (Midterm Evaluations / Buffer period)** | **Mid term deliverables :**<ul><li>Querying with Fido</li><li>Adding Fido records to the database</li><li>Downloading files from VSO and HEK queries using Fido. Downloading using other clients, tests and documentation will be done after mid-term evaluations.</li><li>Continue work on downloading files using Fido.</li></ul> |
| June 28, 2016 - July 4, 2016 ( 1 week ) | <ul><li>**Implement downloading files for all other remaining clients.**</li><li>**For all supported file types, implement storing their metadata in the database. The database module already handles FITS files pretty well.**</li><li>**If needed, create a new feature/wrapper which will allow new file types’ metadata to be added easily to the database in the future.**</li><li>Cross check for every client by using the old separate download methods for downloading files.</li><li>Document and write tests for downloading files using Fido.</li><li>**Update 3 : Push code so that files from all clients can be downloaded from a Fido search result.**</li></ul> |
| July 5, 2016 - July 11, 2016 ( 1 week ) | <ul><li>**Test and ensure that all other pre-existing functionalities of the database module like `tag`, `star`, `undo` etc. are still working.**</li><li>Clean up code to make it PEP8 compliant.</li><li>Finalize Part 1 of the project after reviewing it with mentors.</li></ul> |
| | **Part 1 completed**<br />**Part 2 starts** |
| July 12, 2016 - July 25, 2016 ( 2 weeks ) | <ul><li>**Implement functionality that serializes each query result by converting them to JSON.** Make sure that the serialization and deserialization processes work correctly.</li></ul> |
| July 26, 2016 - August 8, 2016 ( 2 weeks ) | <ul><li>**Implement adding the new type of entries to the cache table in the database.**</li><li>**Implement searching through this database and check if all query results from all different clients are matching correctly.** This includes ensuring that pre-existing query results are detected correctly for every client, like VSO, HEK etc.</li><li>**Implement skipping downloading of files** in case there is a query result match in the cache.</li><li>Ensure that this “skipping” is working for all clients.</li></ul> |
| August 9, 2016 - August 15, 2016 ( 1 week ) | <ul><li>**Buffer period**</li><li>Write documentation and tests for the new caching mechanism.</li><li>**Update 4 : Push code so that the database successfully uses the new caching mechanism.**</li></ul> |
| | **Part 2 completed** |
| August 16, 2016 - August 24, 2016 **(Students Submit Code and Evaluations)** | <ul><li>Clean up code</li><li>Improve documentation</li><li>Resolve merge conflicts (if any)</li></ul> |
| August 24, 2016 - August 30, 2016 | **Mentors Submit Final Evaluations** |
| August 30, 2016 | **Results Announced** |

```
DavidPS: When saying "push" in the updates, do you mean to GH or to do a
         Pull Request?
         I cannot talk for the mentors in this project, but I would prefer
         to see frequently updates and pushes to your fork (almost daily).

         An important point that hasn't been mentioned is how you plan to
         handle data stored in files that are not FITS.

itachi_uchiha: By "push" in each update, I meant a Pull Request for each
               independent feature. It has been mentioned in the project
               idea that a large PR at the end isn't recommended.

               Apart from the updates/PRs, I plan on pushing code to my
               github fork regularly so that the mentors can keep track of
               my progress. I've mentioned it explicitly now just before the
               timeline.

               Added the file handling part.

```

### Software packages to be used

**Language:** Python

**Libraries and modules:** astropy, sqlalchemy, datetime, itertools, json, pytest

**SunPy dependencies :** numpy, scipy, matplotlib, pandas, suds

### How I will successfully complete the project

I am confident of completing this project because this project interests me a lot and also fits my current skill sets. Also, I have worked on projects having strict deadlines and high dependencies on other teammates' progress.

I will work on the project regularly and also regularly update mentors with my progress and also seek guidance if I am stuck at a particular problem. I will also push code regularly so that the mentors can keep track of my progress. Also I'll try to make the commit messages and documentation clear and concise to help anyone who works with the code in the future.

I will spend time on the project before the coding period so that I have a good final idea of my approach and I can hit the ground running as soon as the coding period starts. I have started understanding the structure of UnifiedDownloader and I’m also already acquainted with the Database module. I will fully understand it and experiment with it before the coding period begins.

Even after the project ends, I will be available if anyone has any questions regarding my code.

### Benefits to the Community

**Part 1 :** The integration of Fido inside the database will enable researchers to easily use SunPy’s database to query and store various types of data locally. There will be no need to use separate queries for separate clients. **Support for querying, adding and downloading for any new client in the future can be added easily by just defining a new class from which Fido can use its functionalities.**

**Part 2 :** The improved caching mechanism will also help to save bandwidth, disk space and load on the VSO, HEK etc servers as only new results will be downloaded. It will also eliminate unnecessary wastage of time brought about by downloading the same files again.

## GSoC

### Have you participated previously in GSoC? When? With which project?

I have **not** participated in GSoC before. This is the first time that I would be participating in GSoC.

### Are you also applying to other projects?

**No.** This is the **only project** and **SunPy is the only organization** that I have applied for.

### Commitment

I don’t have any other internships or work ( I don’t plan on having any ) for the summer. I don’t have any plans to go on vacation either.

My classes for the new semester will begin around August 1, but I would still be able to give sufficient time for the project as academic load is very less during the initial few weeks of the semester.  I will be able to spare 35-40 hours for the project per week easily.

Also, because my summer vacation starts on May 7, I will start working on the project early so that I can try to complete the project well before the deadline ( around 2-3 weeks before the deadline ). This will also ensure that any extra unforeseen and time consuming challenges will be taken care of ( there are also buffer periods to handle this ).

Also SunPy is the only organization and this project is the only project that I have applied for.

### Eligibility

**Yes**, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact me at punyaslok.pattnaik@gmail.com .

```
DavidPS: it looks a pretty good application, I cannot comment much more :)

         Good luck!!
```
