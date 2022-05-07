# Transition to AstroPy Time in SunPy

## Organisation: OpenAstronomy

# **1. Sub-organization**

SunPy

# **2. Basic Information**

* Name - Shresth Verma

* Email - [vermashresth@gmail.com](mailto:vermashresth@gmail.com)

* Github handle - vermashresth

* IRC nick - shresthverma

* Blog - vermashresth.github.io

* Telephone: +91 9910077387

* Time zone: UTC +5:30

# **3. University Information**

* University - Atal Bihari Vajpayee Indian Institute of Information Technology and   Management, Gwalior

* Field of study - Information Technology

* Current Year - Third

* Expected graduation date - 2020

* Degree - Integrated Bachelor and Master

# **4. Relevant Skills**

**Programming and Open Source development :**  Python is my language of preference and I have roughly 7 years of experience working in it. Apart from it, I am also comfortable with C, C++ (5 years of experience) and C# (3 years experience). I am also well versed with the working of github. I am relatively new to open source development but other than SunPy and AstroPy, I have also contributed in OpenCV and Shogun ML Toolkit.

**Coursework :**I have taken graduate level courses in Engineering Mathematics, Engineering Physics, Data Structures, Object Oriented Programming, Software Engineering, Modelling and Simulation, Design And Analysis of Algorithms.

**Libraries and Modules:**

Comfortable with *numpy* for linear algebra; *matplotlib, seaborn* for plotting and *pandas* for data analysis.

Familiar with *scipy* and done extensive work in *cv2* and deep learning libraries in python such as *Keras, Tensorflow, PyTorch*.

I have also been contributing to SunPy and AstroPy since December last year and am very much comfortable with its codebase now.

I have already worked on issues related to Time in SunPy as well as AstroPy as a result of which, I feel very much confident and motivated to work on this project.

More details about the contributions I have made in AstroPy and SunPy are at the very end of application.

# **5. Project Proposal Information**

Proposal Title : Transition to AstroPy Time in SunPy

Suggested mentors : Stuart Mumford, Nabil Freij, Punyaslok Pattnaik

**5.1 Abstract**

Time is a central concept in lots of sub-modules within SunPy and at present, SunPy uses `datetime.datetime` objects for representing time. This works fairly well except that `datetime.datetime` has numerous shortcomings when used in the domain of astronomy such as

* Firstly,  `datetime.datetime` doesn’t have a notion of leap seconds. This results in the loss of precision (as reported in issue [https://github.com/sunpy/sunpy/issues/993](https://github.com/sunpy/sunpy/issues/993)).

* Secondly,  `datetime.datetime` works at local time while solar physicists may need to work with more FITS compliant time formats such as TAI, TDB, TT, UT1 etc.  This problem can be solved by transitioning to the Time object in AstroPy. It provides a much powerful representation of Time as it supports various Time Formats,  Time scales and efficient interconversion between them using the ERFA’s python wrapper.

* Another reason is that, some time scales are sensitive to observer’s location (such as TDB scale) and require an EarthLocation object (or a tuple which can instantiate one) to be passed along so as to define them. This isn’t possible at all with  `datetime.datetime` but is supported in  `astropy.time.Time`.

* There is a support of different Time formats in  `astropy.time.Time` such as jd, mjd, unix, cxcsec which can provide diverse forms of representations of the internal time keeping machinery.

* Lastly  `datetime.datetime` lacks the ability to use astropy.units.quantity as input. This transitioning would thusl allow us to use astropy.units.quantity inherently because of its support in  `astropy.time.Time`.

In addition to transitioning to  `astropy.time.Time`, another major change would be to redesign  `sunpy.time.parse_time` that is used all over the SunPy codebase. It is one of the earliest pieces of code in SunPy and over time, with new use cases coming up, it has grown organically into a very cluttered function. Thus, refactoring `parse_time` into a more neat function that returns  `astropy.time.Time` object would be one of the major goals of this project.

**5.2 Project Goals**

**Part 1**: This would involve refactoring of the  `sunpy.time.parse_time` function. Currently, this function takes in input a time string so as to return a datetime.time object. But we would like it to return an  `astropy.time.Time` object instead. This will need major planning beforehand of how we want to present it to users. In addition to this, it will involve writing extensive tests for the refactored function and comprehensive documentation for the same.

**Part 2:** This would involve other modules in SunPy such as sunpy.timeseries, spectra, database and vso, hek clients in  `sunpy.net` to be modified in order to work with   `astropy.time.Time`. Again, this would need some tests and added documentation to assist users in making the transition.

**5.3 Deliverables**

1. A fully functional `parse_time` function which still allows the user to pass all the previously supported formats of time string inputs and returns an  `astropy.time.Time` object. In addition to that, it should also be able to support additional input formats , parameters and string input options which are exclusively available in  `astropy.time.Time` such as coordinates, time scale, time format etc. Moreover, this refactoring will be done with aim to tidy up the current API structure of `parse_time`.

2. All the modules of SunPy will now use the refactored `parse_time` function and will work on  `astropy.time.Time` instead of  `datetime.datetime`. This will majorly affect   `sunpy.net` along with some changes in other modules such as  sunpy.coordinates, sunpy.database, sunpy.timeseries, sunpy.instr, sunpy.spectra . Apart from this, the project will include writing additional tests to support newer functionalities and modifying previous tests to be in accord with  `astropy.time.Time` object.

**5.4 Detailed Description and Implementation**

**Part 1 Refactoring `parse_time`**

**1)  Object Conversion to AstroPy Time**

The main idea here is to change the API of `parse_time` to be a thin wrapper around  `astropy.time.Time`. From design point of view, this will have many advantages, such as

* Some of the cases written in `parse_time` can be covered and parsed by  `astropy.time.Time` under the hood.

* For instance, pandas timestamp and datetime objects are already supported by  `astropy.time.Time` as input so they wouldn’t be needed to be written as explicitly different cases.

* Another thing that can be removed by use of  `astropy.time.Time` is utime format (or in fact any Time format) as it is now supported as a time format ([https://github.com/sunpy/sunpy/pull/2409](https://github.com/sunpy/sunpy/pull/2409))

Now, the structure of refactored `parse_time` can either first parse using  `astropy.time.Time` and then fall back upon the explicitly defined formats supported by `parse_time` or the other way round. I believe that it would be better the latter way because of ease in error handling. That is, if `parse_time` formats can’t handle the string input, it will try  `astropy.time.Time` (for inputs such as '2018-03-20T00:00:00.000(UTC)') and if astropy can’t handle it either, then a meaningful error will be thrown by the error handling machinery of  `astropy.time.Time`.

After this, only the cases which are new for astropy Time (such as ‘now’ or np.datetime64) would have to be explicitly parsed by `parse_time` and even they would be reduced to a bunch of object conversions to astropy time. This would also simplify much of regex parsing of `parse_time` as some part of it would be handled by astropy time.

**2) Single Dispatch in `parse_time`**

Another aim of this refactoring is to tidy up the code. As implemented in [https://github.com/sunpy/sunpy/pull/2408](https://github.com/sunpy/sunpy/pull/2408), using the Single Dispatch Decorator ([https://www.python.org/dev/peps/pep-0443/](https://www.python.org/dev/peps/pep-0443/))  would be a great way to write `parse_time` meaningfully. We can make the parsing by  `astropy.time.Time` as the default case when none of the other formats match. Thus, my plan for the new `parse_time` API would be something like this

[https://gist.github.com/vermashresth/41b39280a0cbad06cc01a90381b9c646](https://gist.github.com/vermashresth/41b39280a0cbad06cc01a90381b9c646)

Some things to note in this implementation

* Whenever a new format is decided to be supported for time_string, we can easily extend this by registering a new function to convert_time. This will prevent the previous problem of complex nested conditionals.

* Special care would have to be taken for cases such as tuple which can mean differently for `parse_time` and AstroPy time like in the case (2018,3,3) and (‘2018-03-03’, ‘2018-03-04’). Similar cases might arise for string regex where discussion would be needed for deciding how the new `parse_time` should interpret the time string.

* Another change here is that, time_format parameter is removed from parameters and instead, `format` parameter for AstroPy would be used as a more generic term for the  `astropy.time.Time` object created. The user can also specify Time scale, location, precision and all the parameters that the Time object supports which would be passed on from **kwargs of `parse_time` to  `astropy.time.Time` at object creation.

The next subpart of this implementation would be to write tests that make sure that newer functionality of `parse_time` work properly. This would include tests related to time formats that weren’t supported earlier, time scales, cases where there might be ambiguity between old `parse_time` behaviour and newer results. Furthermore, we need to add documentation explaining the newer features as well as changes in API so as to assist user in making the transition.

**Part 2 : Making rest of the SunPy to work with AstroPy Time**

**1) Changes within sunpy.time**

* Firstly, some more functions in sunpy.time need to be transitioned to Astropy Time. This involves sunpy.time.TimeRange to use  `astropy.time.Time`Delta instead of datetime.timedelta so that Time Range can work seamlessly with AstroPy time and to prevent loss of precision.

* Another change would be regarding the function `_astropy_time` which takes in input a time instance and tries to return  `astropy.time.Time` object. Since this project aims to convert all Time instances in SunPy to use AstroPy Time, this function would become redundant. The function is primarily used in Ephemeris calculations using SunPy coordinate frames and can be easily replaced by the refactored `parse_time` function.

**2) Replacing datetime functions with equivalent Astropy time objects and functions**

Next part is to modify any piece of code in SunPy that relies on  `datetime.datetime` for time keeping machinery and replace it with  `astropy.time.Time`.

* A large amount of code exists where datetime is used in tests but it is mainly for creating datetime object and can be easily replaced with corresponding  `astropy.time.Time` object.

* Same goes with datetime.timedelta to be replaced with `time.TimeDelta`. However, some additional tests will be added here so as to test new functionality.

* More challenging part would be to convert other functionalities of datetime such as datetime.strftime, datetime.timestamp and datetime.strptime. Although it is possible to write  functions for string formatting on  `astropy.time.Time`, it would be better to add features in AstroPy to support these functionalities.

**3) Make changes in other SunPy modules to work with  `astropy.time.Time`**

This includes modules such as net, timeseries, coordinates, instr, spectra and timeseries. Some minor changes would also be needed inn sunpy.roi, sunpy.map, sunpy.database.

Majorly, the work would be in  `sunpy.net` which uses time extensively for getting remote data over a range of time. Currently, there are many ways of retrieving data in SunPy, through hek client, vso client, fido queries etc and all of them parse the time string of time range and keep them as datetime objects. This is done as special  `sunpy.net`.attr.Attr class. A transition will have to be made to switch it to AstroPy time and make it compliant with the existing tests.

**Part 3**

**Testing and Documentation**

Writing lots of new tests, changing documentation, adding examples in documentation and modifying doctrings regarding datetime, documentation regarding changes, improving error handling, increasing test coverage and adding some examples in the SunPy examples gallery regarding manipulation with Time (I think it is an important domain which lacks narrative examples).

**6. Timeline**

April 23rd, 2018 - May 13th, 2018

**Community Bonding Period**

* Read documentation and try out various functionality of SunPy so as to get familiar with it.

* Discuss with mentors what they have in plan about the idea and decide the final approach to go with the project. This would mainly involve concrete planning of refactoring of `parse_time` function and the preferable API that should be presented to users.

* Get in touch with developers who maintain the Astropy Time part. This is required so as to assist in implementing features needed to complete this project (such as string formatting of  `astropy.time.Time` object). Moreover, it would also be worthwhile to start working on these features in this period.

* Discuss vital features that are required in the scientific community in relation to this project.

* Get an idea of challenges that might arise while implementing the project plan.

May 14th, 2018 - June 14th, 2018

**Official Coding Begins, Phase 1**

* **Week 1 (May 14th)**

  * Start with the refactoring of `parse_time` function using the single dispatch method following up from the PR already in place.

  * Develop wrappers to create  `astropy.time.Time` object from all existing types that `parse_time` supports such as pandas.series, np.datetime64 etc.

  * Make sure that previous tests don’t break with the changes in `parse_time` and also modify some tests if needed (such as those which are expecting `parse_time` to return  `datetime.datetime` object)

* **Week 2 (May 28th)**

  * Evaluate the string formats that already exist in AstroPy time which need not be explicitly implemented in `parse_time` and remove them from existing implementation.

  * Discuss with mentors the way time scale, time formats, precision should be assigned by the user through `parse_time`.

  * Implement the additional parameters passed to `parse_time` though **kwargs to be passed on to  `astropy.time.Time` object at creation.

* **Week 3, 4 (May 28th - June 14th )**

  * Add tests to check new functionality of `parse_time` function.

  * Add documentation explaining the changes in `parse_time` and docstrings of return type.

  * Work upon the features required in  `astropy.time.Time` and get those PRs merged.

  * Buffer time in case things take longer to implement.

June 15th

**Phase 1 Evaluation Deadline**

June 16th, 2018 - July 12th, 2018

**Phase 2 Coding**

* **Week 5 (June 16th)**

  * Make changes in sunpy.time.TimeRange so as to use  `astropy.time.Time`Delta in internal machinery.

  * Start transitioning all tests to use  `astropy.time.Time` objects instead of  `datetime.datetime`.

  * Make necessary changes for transition in modules not using Time extensively such as maps, coordinates, roi, physics, database, io.

* **Week 6 (June 23rd)**

  * Begin the modification of code in  `sunpy.net` to work with  `astropy.time.Time` and discuss with mentors about possible additional options that might have to be added.

  * Simultaneously, add tests for  `sunpy.net` to be compliant with  `astropy.time.Time`.

  * `sunpy.net` has the most extensive use of Time so this will take the longest time in transitioning.

* **Week 7, 8 (June 30th - July 12th)**

  * Transition of  instr, timeseries, spectra modules to use AstroPy Time.

  * Add tests related to these modules too and continue to work on  `sunpy.net`.

  * Make the code pep8 compliant and do code clean ups.

July 13th

**Phase 2 Evaluation Deadline**

July 14th, 2018 - August 14th, 2018

**Final Phase Coding**

* **Week 9, 10 (July 14th - August 3rd)**

  * Write tests and documentations to account for the changes and refactoring done.

  * The documentation should also serve as a guide to users to make them aware of changes as well as new functionalities that the API offers.

* **Week 11, 12 (August 4th - August 14th)**

  * Update the examples in docstrings to be in accordance with the newer API for Time.

  * Add examples in SunPy example gallery demonstrating the use of Time object in SunPy as well as the time strings that it supports.

  * Buffer period for work that might take longer to implement.

  * Get ready for final evaluation!

August 14th - August 21st

**Final Evaluation**

August 22nd

**Results Announced!**

August 23rd -

**Continue contributing to AstroPy and SunPy**

**Note: I will regularly push code to my github fork instead of having one large PR at the end so that reviewing code is easier and my mentors can keep track of my progress.**

**7. Benefits to the Community**

This project will allow SunPy to completely switch over to AstroPy time. This will result in greater precision and improved flexibility for using time scales and formats. Moreover, refactoring `parse_time` would tidy up the code that has been one of the oldest one in SunPy.

**8. Link to Patches**

**SunPy**

Download files with cache and progressbar

[https://github.com/sunpy/sunpy/pull/2562](https://github.com/sunpy/sunpy/pull/2562)

Added convolution filter and peakfinding examples

[https://github.com/sunpy/sunpy/pull/2488](https://github.com/sunpy/sunpy/pull/2488)

Refactor `parse_time`

[https://github.com/sunpy/sunpy/pull/2408](https://github.com/sunpy/sunpy/pull/2408)

**AstroPy**

Use n_models only to initialize model sets

[https://github.com/astropy/astropy/pull/7271](https://github.com/astropy/astropy/pull/7271)

Added LOCAL time scale

[https://github.com/astropy/astropy/pull/7122](https://github.com/astropy/astropy/pull/7122)

Fix for poor performance in Angle.**str** and Angle.*repr_latex*

[https://github.com/astropy/astropy/pull/7004](https://github.com/astropy/astropy/pull/7004)

Contribution to other repositories

**Shogun ML toolkit**

Detect cblas.h during cmake for openblas

[https://github.com/shogun-toolbox/shogun/pull/4013](https://github.com/shogun-toolbox/shogun/pull/4013)

**9. GSOC**

### **Have you participated previously in GSoC? When? With which project?**

No, I have NOT participated in GSOC before, this is my first time.

### **Are you also applying to other projects?**

No. This is the only project I am applying for.

### **9.1 Commitments**

I am free for the summer of 2018 as I am not having any internship. But I do have my final term exams from 1st May to 6th May. Luckily, this lies in the community bonding period so it shouldn’t affect the project much. My summer holidays would end in the last week of July but I am sure I can spend 35-40 hours working on this project even during regular classroom schedule as it is not that hectic.

Apart from this, I have to start working on my btech project in second half of July but that won’t require more than 4 hours a week of commitment as it is only the initial phase involving discussion with faculty.

I have also added buffer periods in my proposed timeline so that there is time to cover up lagging milestones(just in case there are any) or if any particular stage takes longer to implement. This will ensure that work gets completed at right time before the deadline.

### **9.2 Eligibility**

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanations, feel free to contact me at **vermashresth@gmail.com.**
