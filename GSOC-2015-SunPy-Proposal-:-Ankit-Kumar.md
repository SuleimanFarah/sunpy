### Sub-organization: SunPy

###1. Student Information
* **Name:** Ankit Kumar
* **Email:** ankitkmr.iitk@gmail.com, technocrat.ankit@gmail.com
* **Telephone:** +091-9621304455, +091-9911176810
* **Address:** House No. 1537, Sector 10 A, Gurgaon, Haryana-122001, India
* **Time Zone:** +0530 GMT
* **IRC Handle:** 
* **Github ID:** ankitkmr
* **Instant Messaging information:** Google Hangout (ankitkmr.iitk@gmail.com)
* **HomePage:** http://home.iitk.ac.in/~ankitkmr/
* **Blog:** http://home.iitk.ac.in/~ankitkmr/blog/
* **Blog RSS:**  http://feed43.com/sunpygsoc2015.xml

***
### Education:

I completed my primary and secondary education from Delhi Public School, Maruti Kunj [April 1997 - March 2010]. Some of the teachers in School were really amazing. They would show videos, organize discussion sessions, lab demonstrations and what not! They made studying real fun. From their I went to Delhi Public School R.K Puram for my Senior High School.

Currently, I am a third year undergraduate studying Materials Science and Engineering at Indian Institute of Technology, Kanpur. I will graduate from here in April, 2016.


###2. University Information
* **University:** Indian Institute of Technology Kanpur
* **Major:** Material Science and Engineering
* **Current Year:** Third Year
* **Expected Graduation Date:** 2016
* **Degree:** Bachelor of Technology (B.Tech)

###3. Some of my bragging rights:

* Secured **All India Rank 5112** among more than 5,20,000 students in IIT-JEE 2012
* Was among **top 1%** in All India Engineering Entrance Examination 2012
* Awarded the prestigious **Kishore Vaigyanik Protsahan Yojna(KVPY)** fellowship by the Department of Science and Technology,Government of India in the year 2012


###4. Work and Open Source Experience:

Although I haven't really had much experience contributing to Open source Projects, I have extensive experience in developing projects implementing scientific and mathematical ideas by using Python and its Libraries. 

* I built a set of scripts that used panda, numpy, scipy, matplotlib, QSTK to perform algorithmic trading, price-timeseries chart plotting.

* I also  implemented a grain strain measurement software based on Electron BackScattering Diffraction (EBSD) maps last semester using Python, numpy, scipy and matplotlibs for my Mechanical Properties Lab. It would read in grain data from EBSD files, store them and correlate them to data points in second EBSD file, recognize closed grains and calculate grain strain

* In Current semester as well I am heading the development of SaaS project, a cloud based extractive metallurgy simulation by using Python for module development of all the ore processing units, Bootstrap for frontend and Python web micro-framework flask for backend. 

You may find my software source code here: https://github.com/ankitkmr

Apart from the above projects, I am also proficient in C/C++ and have done quite a lot of sport programming.

**Operating System Experience:** Currently, I use Mac OSx. Also I have used Ubuntu and Windows for a few years back.

***

###5. Sunpy - Support for analysis of Solar Energetic Particles

###6. Proposal Abstract:
A short description of your proposed project

###7. Software packages to be used
* **Language:** Python
* **Libraries and modules:** pandas, datetime, scipy, numpy, matplotlib

###8. How I will successfully complete the project:

I consider myself a quick learner who finds ways out of difficulties. I have been an active user of Stack Overflow in the past and know where to go for various programming related questions. Having selected a project that both fits my skill set and excites me very much, I am confident to complete it on time. Also the fact that I have had done various projects in the past requiring similar nature of working with pandas timeseries and visualizations, I have a good grasp on the implementation intricacies of this project.

I will work on the project regularly and update mentors with my status as well as discuss further plan of action regularly. I will also push code on github on a regular basis. Also I will ensure that my commit messages and comments are insightful to any future reader of my code.

I will spend some time on the project before the coding period begins so that I can start being productive as soon as coding period begins. I have started understanding the structure of LightCurve, UnifiedDownloader. I'll spend more time on it once it has been updated more in future. I will fully understand it and experiment with it before the coding period begins. I'll also remain available for any queries regarding my code well after successful completion of project. 


###9. Deliverables

###10. Benefits to Community
Don't forget to make your case for a benefit to the organization, not just to yourself.  Why would Google and your organization be proud to sponsor this work? How would open source or society as a whole benefit? What cool things would be demonstrated?

###11. Proposal Detailed Description/Timeline:

Please include timeline with milestones, preferably weekly ones. You may wish to read the GSoC student guide which includes several examples of good proposals with timelines, or our own information at SummerOfCode/Application
Note that any pre-work such as setup and reading documentation should take place during the community bonding period (April 27-May 24). Students will be expected to start producing code starting on May 25th.

###12. Link to a patch/code sample:

I patched SunPy issue **[#798](https://github.com/sunpy/sunpy/issues/798)** : Pandas dataframe values return as numpy.datetime64 objects in local time zone. parse_time does not understand these objects.

My PR is here **[PR #1344](https://github.com/sunpy/sunpy/pull/1344)** : Adds support for numpy.datetime64 and strings with timezone info. Some details about my PR :-

* It added support for to parse time_string of type numpy.datetime64 in parse_time function.
* It also added support for parsing time_string of type string with timezone information attached in the end in parse_time function
* I also added test cases for my patch in the test_time.py file in accordance with sunpy development guide.

It is yet to be merged.


***

###13. Motivation:

I have always been interested in astronomy, solar systems, planets. To add to interests, Physics and Programming have always been my favorite subjects. Physics because it helps me to understand the world around me through an objective thought system and Programming because it is empowering. I was introduced to programming in my first year of college and software development in my third semester. I took an online course that semester which taught Algorithmic Trading and it involved writing scripts which interacted with data in different files, manipulated it and presented it in different forms. I had already learnt Python the previous summer and applying it in this completely non-convention way ( and the ease with which I could do it) blew my mind. That is where I can point and say that I loved Python and Development. It helped me to build tools for all the amazing scientific theories that I had read and actually use them. That was amazing. I also ended up making a few python games using simplegui as a part of online course offered by Rice University. And It was cool to have my friends/blockmates to play the pingpong game that I coded. Oh I can't tell how awesome I felt back then !! And as it was I ended up doing all my major development projects afterwards in Python only.

###14. Schedule:

I do not have any other internship or involvements(and I am not planning to have any) for the Summer 2015. I may go on vacation (for 3-4 days) but that will be either before the coding period begins or after the coding period ends. In case it clashes with the coding period, I'll ensure that I complete that weeks work in advance before going away (which won't be for more than a week in any case)
 
I have classes during last two weeks of coding period but since the academic load is very less in the beginning of semester, I will be able to spare at least 30-35 hours for the project per week. Also, to be on a safer side, I will begin early (Since our institute summer vacation starts from 1 May) and try to complete the project around 1-3 weeks before the deadline.

Also I haven't applied to any other organization except SunPy.

###15. Eligibility:
Yes, I am eligible to receive payments from Google.
For any queries, clarifications or further explanation of any approach/feature feel free to contact me at **ankitkmr.iitk@gmail.com** and I shall be happy to reply.