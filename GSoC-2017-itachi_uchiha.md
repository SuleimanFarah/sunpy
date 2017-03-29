## Organization: OpenAstronomy
## Sub-Organization: SunPy
## Student Information
* **Name:** Punyaslok Pattnaik
* **E mail:** punyaslok.pattnaik@gmail.com
* **Time Zone:** +05:30 GMT
* **IRC Handle:** itachi_uchiha_
* **Github Username:** [Punyaslok](https://github.com/Punyaslok)
* **Blog :** [My Blog](https://punyaslokpattnaik.wordpress.com)
* **Blog RSS feed :** https://punyaslokpattnaik.wordpress.com/feed/

## University Information
* **University:** [International Institute of Information Technology, Hyderabad](https://www.iiit.ac.in)
* **Major:** Computer Science
* **Current Year:** Third Year
* **Expected Graduation Date:** 2019
* **Programme:** Bachelor of Technology (B.Tech) in Computer Science and MS by Research in Computational Natural Sciences (Dual Degree)

## Work and Open Source Experience

I participated in GSoC under SunPy in 2016.

[GSoC 2016 Product Submission](https://github.com/Punyaslok/sunpy/pull/1)


**My github url :** [Punyaslok](https://github.com/Punyaslok)

**Operating System Experience:** I use Ubuntu, Arch Linux and Windows.

Apart from the above projects, I am also proficient in C/C++ and I love sport programming.

## PR links
* **Astropy**
 * [Removed discussion of Keyword class in Getting Started section.](https://github.com/astropy/ccdproc/pull/296)
* **SunPy (excludes GSoC 2016 work)**
 * [Implemented feature request: split database by query into two databases](https://github.com/sunpy/sunpy/pull/1700)
 * [Database(default_waveunit) should take a Unit](https://github.com/sunpy/sunpy/pull/1701)
 * [Download and fetch both accept kwargs now.](https://github.com/sunpy/sunpy/pull/1719)
 * [Fixed the test_add_entry_from_hek_qr test](https://github.com/sunpy/sunpy/pull/1717)
 * [Now downloads take place in the correct directory](https://github.com/sunpy/sunpy/pull/1856)
 * [Quick Examples for the database package](https://github.com/sunpy/sunpy/pull/1822)


## Project Proposal Information

**Project:** Sun, Right now!

**Mentors :** [Stuart Mumford](http://github.com/Cadair), [David Pérez-Suárez](http://github.com/dpshelio)

### Abstract :

The Sun releases large amounts of magnetic energy in the form of X-rays, EUV (Extreme ultraviolet), radio waves and high energy particles regularly. This kind of radiation bursts can threaten space and ground based technological infrastructure. Hence it is important to monitor solar activity to be prepared for potential threats.

The surface of the Sun is not uniform but is in fact dotted with Active Regions (ARs), which are regions with very strong magnetic fields. These fields can prevent the normal convective processes on the solar surface leading to regions with lower than average temperatures. These features are called Sunspots. These sunspot systems can be very complex and sometimes the AR associated with them can give rise to Solar Flares, which are sudden releases of magnetic energy (1025 J).

The main purpose of this project is to provide near real-time information on solar activity and active regions. It will be completely powered by SunPy, and will be accessible to a wide variety of users. It will serve, among other things, active region information, full solar disk images etc.

In order to serve this data, an additional Fido client will need to be implemented which will download DSCOVR data. This client will provide Real-time Solar Wind and Magnetometer data.

Also for proton and electron flux data to be served, a new instrument will need to be added to GOES.

Hence his project would have these main tasks :
1. Make a new Fido client for DSCOVR data
2. Add new instrument in GOES for getting proton flux and electron flux data
3. Building the webapp - This needs to get updated everyday for new plots to come in.
4. Design a database schema to handle the data - keep extra fields to account for future interactive js support.
5. New Individual clients addition, one by one.
6. Generate new plots for each client everyday  ( cronjob type of thing, `schedule.every().day.at("10:30").do(job)`  )
7. On initial deployment, make plots of past year’s files and save them


### Project Goals :

1. A DSCOVR client for Fido.
2. A new instrument for obtaining proton and electron flux data.
3. A website which serves solar activity data along with AR information.

### Deliverables

1. A fully functional Fido client which will get plasma and B-field data from DSCOVR
2. Proton and electron flux data availability in GOES
3. A fully functional website which shows the latest images and allows browsing and querying for old images/plots.
4. If interactive js cannot be completed within the time frame, make sure that the database schema is designed so that future work on interactive js would not need any extra data which was not there earlier in the database.
5. Make future addition of new clients easier for the webapp.

### Detailed Description

**Database Schema**

Database → Multiple Client tables → Each client has 2 tables

I thought each client should have separate table only for the reason that future replacement of that data’s source should not tamper with other clients’ data indexing.

Every client will have 2 tables :
* Image table
* Info / metadata table

Image table
* ID (numbered serially, i.e. 6 images will be numbered from 1 to 6) - Primary Key
* Start Date-time
* End Date-time
* Resolution
* File path

Info / metadata table ( client is already known, no need for a separate field )
* ID (numbered serially) - Primary Key
* Start Date-time
* End Date-time
* FITS file path ( may be needed in future if we need to replot past data )
* Python Script path ( Assuming we’ll generate the python script beforehand). If it is decided to just template render it with flask, then this field won’t be needed.
* Additional parameters specific to each instrument

**Join operations for query to be done using start and end date-times.**

List of data sources ( Decreasing priority ) :
1. HMI → LOS_magnetic_field  ( almost done ) → start with this
2. AIA (imaging) - works
3. HMI (imaging)
    1. LOS - done
    2. Continuum - works
4. GOES (timeseries)
    1. X-Rays - Works
    2. Protons - needs implementation of additional instrument
    3. Electrons - needs implementation of additional instrument
5. EVE (timeseries) - works
6. <s>ACE (timeseries)</s>    DSCOVR (timeseries) → This replaces ACE
    1. Plasma
    2. B Field
7. EUVI  (imaging)
    1. STEREO_A - works
    2. STEREO_B - works

**Note :** **_works_** above means that I have written a standalone python script for which plotting and overlaying of active region works.

**Reference :**
* Hieronymous’ list(not linking it as I have an edit link)
* [Solar Monitor](www.solarmonitor.org)
* [Real-Time Solar Wind](http://www.swpc.noaa.gov/products/real-time-solar-wind)
* [https://www.ngdc.noaa.gov/dscovr/portal/index.html#/download/1490227200000;1490572799999](https://www.ngdc.noaa.gov/dscovr/portal/index.html#/download/1490227200000;1490572799999)


### How Time Allocation was made in the Timeline
To get a fair estimate of how much time to allocate to each client, I wrote scripts to plot each client’s data. Among all clients, common parameters are :
* Input : Date Range
* Output : Plot of that client with AR information from SRS plotted on top of it.
Most clients worked well and hence lesser time has been allocated to them as all their implementation would be similar to the magnetogram example.

[Magnetogram overplotting gallery example #2037](https://github.com/sunpy/sunpy/pull/2037)

A sample image from the magnetogram plot + AR info on top of it (blue dots are AR locations):
![](https://github.com/Punyaslok/proposal_images/blob/master/magnetogram-ars.png)

Also I took into account Cadair’s suggestion for this year’s projects : finished, polished and merged PRs at the end is better than a lot of unmerged PRs at the end. Hence I have taken a bit more time to ensure that a client is fully up and running before moving to the next client.

* Document and keep track of all policy decisions made.
* Make it a rule to post all policy decisions on that PR page. Avoids unnecessary confusion/time-wasting later on.


## Timeline

| Time Period        | Plan           |
| ------------- | ------------- |
| **Community Bonding** May 5 - 30, 2017     |   <ul><li>Get familiar with Flask</li><li>Set up a simple flask webapp that can run and display the [magnetogram example](https://github.com/sunpy/sunpy/pull/2037). This will act as a base upon which the whole project will be built.</li><li>Set up the database for this LOS_magnetic_field and make sure the webapp is up and running for any queries for LOS_magnetic_field.</li></ul>|
| | **Coding Period Starts (May 30, 2017)** |
| June 1 - 7, 2017 ( 1 week ) | <ul><li>Add AIA client</li><li>Write and run job to populate database with past years’ plots</li></ul> |
| June 8 - 22 ( 2 weeks ) | <ul><li>Add HMI client ( LOS would’ve already been done )</li><li>Add instrument to download proton flux and electron flux data in GOES</li><li>Complete the instrument implementation</li><li>Add GOES client to website</li></ul> |
| June 23 - 30, 2017 ( 1 week ) | <ul><li>Add EVE client</li><li>Write and run job to populate database with past years’ plots</li></ul> |
| | **First Evaluation ( June 26 - 30, 2017 )** |
| July 1 - 21, 2017 ( 3 weeks ) | <ul><li>Implement new Fido client to download DSCOVR data</li><li>Add DSCOVR client to website</li><li>Write and run job to populate database with past years’ plots</li></ul> |
| | **Second Evaluation ( July 24 - 28, 2017 )** |
| July 21 - 28, 2017 ( 1 week ) | <ul><li>Add EUVI</li><li>Write and run job to populate database with past years’ plots</li></ul> |
| July 29 - August 5, 2017 ( 1 week ) | **Buffer Period** |
| August 6 - 19, 2017 ( 2 weeks ) | <ul><li>Write scheduled jobs for each client which will run once everyday to update the existing data with new plots.</li></ul> |
| August 20 - 26 ( 1 week ) | <ul><li>Final polishing</li><li>Re-check daily scheduled jobs. Make sure they work correctly for each client.</li></ul> |
| | **Second Evaluation ( July 24 - 28, 2017 )** |
| | **Second Evaluation ( July 24 - 28, 2017 )** |

### How I will successfully complete the project:

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
