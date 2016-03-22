# Organization: OpenAstronomy
# Sub-Organization: SunPy
## Student Information
* **Name:** Punyaslok Pattnaik
* **E mail:** punyaslok.pattnaik@gmail.com
* **Time Zone:** +05:30 GMT
* **IRC Handle:** itachi_uchiha
* **Github Username:** [Punyaslok](https://github.com/Punyaslok)
* **Blog :** [My Blog](https://punyaslokpattnaik.wordpress.com)
* **Blog RSS feed :** 

## University Information
* **University:** International Institute of Information Technology, Hyderabad
* **Major:** Computer Science
* **Current Year:** Second Year
* **Expected Graduation Date:** 2019
* **Programme:** Bachelor of Technology (B.Tech) in Computer Science and MS by Research in Computational Natural Sciences (Dual Degree)

## Work and Open Source Experience

I haven’t had much Open Source experience before contributing to SunPy, but I have experience working in team projects, especially involving python.

* Made a 2D cannon shooting game using OpenGL
* Made a 3D obstacle course maze game using OpenGL
* Made a Bidding Portal using web2py for easy auctioning of items, primarily to help departing students sell off bicycles, air coolers etc.
* Made a Donkey Kong game using pygame, and also tested it using pytest
* Handled the django backend part of a team project, which involved building a social networking site, aimed at movie lovers. The site had a django backend, and an AngularJS frontend.

**My github url :** [Punyaslok](https://github.com/Punyaslok)

**Operating System Experience:** Currently, I use Ubuntu. I also use Arch Linux and Windows.

Apart from the above projects, I am also proficient in C/C++ and I love sport programming.

## PR links
* **Astropy**
 * [Removed discussion of Keyword class in Getting Started section.](https://github.com/astropy/ccdproc/pull/296)
* **SunPy**
 * [Implemented feature request: split database by query into two databases](https://github.com/sunpy/sunpy/pull/1700)
 * [Database(default_waveunit) should take a Unit.](https://github.com/sunpy/sunpy/pull/1701)

## Project Proposal Information

**Project:** Improvements to the SunPy Database

**Mentors :** [Stuart Mumford](http://github.com/Cadair), [Simon Liedtke](http://github.com/derdon), [Steven Christe](http://github.com/ehsteve)

### Abstract :

The SunPy database module enables users to manage files on a disk, or a network hosted database. Users can find files by using physical parameters such as wavelength, time etc. or by using attributes such as instrument name. Queries can also be combined to form complex queries.

The database module also acts as a proxy and can handle downloading files from different clients. It takes queries and if the user wants to download files, the database makes the query and downloads the files, with the option of the user specifying the download path. It also has a caching mechanism so that if a same download query is made the second time, the files aren’t redownloaded.

The first part of the project would involve making several modifications to the database module used by SunPy to integrate the Fido interface with the database which will enable users to use only the Fido to make queries, instead of making separate queries for separate clients like VSO, LightCurve etc. Currently in the internal working of the database uses VSO queries, VSO download methods etc. So, for different individual clients like LightCurve, the user has to supply separate queries. *So, using the Fido store and query in the database, we can store many types of data in the database. Currently, only VSO and HEK data can be stored in the database.*

The second part involves improving the caching mechanism. Currently, the caching system uses queries to decide whether a file needs to be downloaded. So, if two queries have largely similar results, they both are completely downloaded.

### Project Goals :

**Part 1 :** Use Fido to replace VSO for doing internal database operations, primarily to achieve the goal of being able to store different formats of data in the database. This will create the ability to quickly support more and more data types in the future as support for each type can be added by creating relevant sub-classes.

**Part 2 :** Improve caching mechanism to eliminate downloading files that are already downloaded as part of a different query.

### Deliverables

1. **A fully functional database module** which will use the Fido attributes and will not be restricted to separate queries for VSO, HEK etc. The database should retain all its current abilities/features while using Fido. This involves querying, adding and downloading to the database.
2. **A new caching mechanism** for the database that improves performance in case of overlapping query results. This will be achieved by checking results of queries to eliminate duplicate downloads. The earlier model used to check only saved queries while caching. So, if 2 queries had a slight difference in downloaded files, with a large number of same results, there was no match and the overlapping queries were downloaded again.

### Detailed Description

**Part 1**

I would divide this part of the project into 4 broad subparts.
In sequence, they go like this:

1. **Querying with Fido**

   Currently the database uses client-specific queries like VSOClient().query to make a query for a specific client, in this case, VSO. Implement querying with Fido inside the database module. This means that a command like Database.query(attributes) will 

2. **Adding with Fido**

   Successfully add entries to the database from a Fido search result. Currently, client-specific functions like Database.add_from_vso_query_result() are used to add entries. Implement functionality such as Database.add_from_Fido_result() that will add the results of the QueryResponse object returned by the underneath client.

3. **Downloading with Fido**

   Given a Fido search query, download the relevant files from the client which Fido decides can best serve the query. This will involve downloading files from different clients for different types of queries. All files from all clients must be downloaded successfully.

4. **Miscellaneous**

  1. Test the database module again to ensure that all functionalities such as tag, star, undo etc. work fine after integrating Fido.
  2. Make the database module pass quantified code checks (optional)

**Note :** Documentation and writing tests will be done simultaneously along with each subpart. So, completion of each subpart will involve writing code for implementation, writing tests for that feature, and documenting that feature.

Specifically speaking, after implementing Part 1, the database will be able to take queries like `Fido.search(attrs.Time("2012/1/1", "2012/1/2"), attrs.Instrument('lyra'))` and decide which client can best serve the query and automatically handle adding to database, downloading files etc.

For example, currently we have to use specific queries like `vso.VSOClient().query(vso.attrs.Time('2001/1/1', '2001/1/2'), vso.attrs.Instrument('eit'))` for VSO and `hek.HEKClient().query(hek.attrs.Time('2011/08/09 07:23:56', '2011/08/09 12:40:29'),  hek.attrs.EventType(‘FL’))` for HEK.

**Part 2**

This part would mainly involve changing what items are stored in the cache. Now, instead of queries, the all the results that a query returns will be stored in the cache. This will involve changing the JSON format in order to store a query result. Also, along with that, encoding and decoding that new JSON will have to be done.

Now, for the cache to work, it has to be ensured that whenever a query is made through Fido, pre-existing same query results in the cache are matching correctly with the query results obtained from the Fido search. So, while downloading files, those files will be skipped whose query result entries are already in the database.

**Note :** Updates will be scheduled to the database package in small sections, rather than in one large pull request. The updates schedule is included in the timeline. Do this.

## Timeline

* April 22, 2016 - May 22, 2016 **(Community Bonding Period)**
  * Read documentation and get more familiar with how Fido works.
  * Discuss with mentors and get a final idea of how to approach the project.
  * **Get familiar with the various clients that Fido would be supporting and also understand how each client’s query is different from other clients and how to download data from each client.** This is important because later on one common query will have to be assigned to a client automatically, and downloads from that particular client will be made.
  * Read code and get more familiar with the caching mechanism and try to get an idea of what challenges could possibly arise while implementing the new caching mechanism. This is important because query results of multiple clients will be stored in the cache.

**Part 1 starts**

* May 23, 2016 - June 5, 2016 ( 2 weeks )
  * **Implement querying with Fido.** Ensure that the different clients are recognized correctly and correct results are returned. Cross check by using custom queries for each client.
  * Write tests for querying with Fido.
  * Document querying with Fido.

* June 6, 2016 - June 12, 2016 ( 1 week )
  * **Implement adding the Fido records to the database.**
  * Ensure that functionalities like display_entries etc. are working. Cross check by adding entries using specific client methods (the old way).
  * Document and write tests for adding while using Fido.

* June 13, 2016 - June 20, 2016 ( 1 week )
  * **Implement downloading files for VSO and HEK queries after querying database.**
  * Ensure that the correct files from the correct clients are being downloaded by checking using the old separate download functions.

* **June 21, 2016 - June 28, 2016 (Midterm Evaluations / Buffer period)**
  * **Mid term deliverables :**
    * Querying with Fido
    * Adding Fido records to the database
    * Downloading files from VSO and HEK queries using Fido. Downloading using other clients, tests and documentation will be done after mid-term evaluations.

* June 28, 2016 - July 4, 2016 ( 1 week )
  * **Implement downloading files for all other remaining clients.**
  * Cross check for every client by using the old separate download methods for downloading files.
  * Document and write tests for downloading files using Fido.

* July 5, 2016 - July 11, 2016 ( 1 week )
  * **Test and ensure that all other pre-existing functionalities of the database module like tag, star, undo etc. are still working.**
  * Clean up code to make it PEP8 compliant.
  * Finalize Part 1 of the project after reviewing it with mentors.

**Part 1 completed**

**Part 2 starts**

* July 12, 2016 - July 25, 2016 ( 2 weeks )
  * **Implement functionality that serializes each query result by converting them to JSON.** Make sure that the serialization and deserialization processes work correctly.

* July 26, 2016 - August 8, 2016 ( 2 weeks )
  * **Implement adding the new type of entries to the cache table in the database.**
  * **Implement searching through this database and check if all query results from all different clients are matching correctly.** This includes ensuring that pre-existing query results are detected correctly for every client, like VSO, HEK etc.
  * **Implement skipping downloading of files** in case there is a query result match in the cache.
  * Ensure that this “skipping” is working for all clients.

* August 9, 2016 - August 15, 2016 ( 1 week )
  * **Buffer period**
  * Write documentation and tests for the new caching mechanism.

**Part 2 completed**

* August 16, 2016 - August 24, 2016 **(Students Submit Code and Evaluations)**
  * Clean up code
  * Improve documentation
  * Resolve merge conflicts

* August 24, 2016 - August 30, 2016  **(Mentors Submit Final Evaluations)**

* August 30, 2016  **(Results Announced)**

### Software packages to be used
**Language:** Python

**Libraries and modules:** astropy, sqlalchemy, datetime, itertools, json, pytest

**SunPy dependencies :** numpy, scipy, matplotlib, pandas, suds

### How I will successfully complete the project:

I consider myself a quick learner who finds ways out of difficulties. Having selected a project that both fits my skill set and interests, I am confident to complete it on time. Also, I have worked on projects having strict deadlines and 

I will work on the project regularly and update mentors with my status as well as discuss further plan of action regularly. I will also push code on github on a regular basis. Also I will ensure that my commit messages and comments are insightful to any future reader of my code.
I will spend time on the project before the coding period begins so that I can start being productive as soon as coding period begins. I have started understanding the structure of UnifiedDownloader and I’m also already acquainted with the Database module. I will fully understand it and experiment with it before the coding period begins. I'll also remain available for any queries regarding my code well after successful completion of project.

### Benefits to the Community

**Part 1 :** The integration of Fido inside the database will enable researchers to easily use SunPy’s database to query and store various types of data locally. There will be no need to use separate queries for separate clients.

**Part 2 :** The improved caching mechanism will also help to save bandwidth, disk space and load on the VSO, HEK etc servers as only new results will be downloaded. It will also eliminate unnecessary wastage of time brought about by downloading the same files again.

## GSoC

### Have you participated previously in GSoC? When? With which project?

I have **not** participated in GSoC before. This is the first time that I would be participating in GSoC.

### Are you also applying to other projects?

**No.** This is the **only project** and **SunPy is the only organization** that I have applied for.

### Commitment
I don’t have any other internships or work ( I don’t plan on having any ) for the summer. I don’t have any plans to go on vacation either.

My classes for the new semester will begin around August 1, but I would still be able to give sufficient time for the project as academic load is very less during the initial few weeks of the semester.

Also, because my summer vacation starts on May 7, I will start working on the project early so that I can try to complete the project well before the deadline ( around 2-3 weeks before the deadline ). This will also ensure that any extra unforeseen and time consuming challenges will be taken care of ( there are also buffer periods to handle this ).

Also SunPy is the only organization and this project is the only project that I have applied for.

### Eligibility

**Yes**, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact me at punyaslok.pattnaik@gmail.com .