# space
## Personal Information:
Name: Michael J. Malocha
IRC handle: mjm159@irc.freenode.net
Github name: mjm159
Skype: mmalocha13
Blog: <http://mjm159.wordpress.com/>

## Bio:
As an applicant for the Google summer of code, I feel that I should make a small introduction about myself. From my application you can see that my full name is Michael Malocha, I go by Mike and Michael, but if I to pick, I prefer to go by Michael. I am from Seattle, and go to school in the lovely region of Northern California. I am finishing my 4th year of school I didn't decide to study Computer Science until 2 years ago. I started University pursuing Marine Biology, but soon felt that it wasn't what I wanted to do with my life. I decided to take a couple different classes to try out some of the different sciences and in the process I took the "Introduction to Computer Science" course that my school offered. When the semester ended, I wasn't satisfied stopping there, and needed to know more about these incredible machines we so often take for granted. I'll be the first to admit that I am not the most experienced applicant in this program, but I feel that my very intense desire to improve my understanding of this field coupled with budding desire to contribute to the open source community will lend themselves to the SunPy project. I will work hard and regularly communicate with the SunPy community. Thank you for taking the time to consider my application.

## Project Proposal: SunPy - Database of Local Data
### Abstract
 When using the SunPy library, the VSO toolkit allows users to download solar data to their local systems. One of the problems with this data, is that after it is downloaded and used, it is stored in such a way that it is not super conducive for future re-use. The proposed idea is to add the functionality of a SQLite database. It would interact with the VSO toolkit during downloads to keep track of the data and its corresponding metadata in a functional local database, thus enabling future querying and re-use.

### Deliverables

* Create framework for a local SQLite database that interfaces with VSO
* Stores file path
* Stores attached metadata such as instrument, wavelength, source, etc.
* Create a namespace for querying the local database for specific sets of data
* When using VSO to gather new data, query the local database to prevent redundant downloads of data
* Provide documentation and testing

### Schedule
**Community Bonding (May 27th - Jun. 16th)**

* Become a Git power user
* Generally Review codebase and submit tests
* Review SQLite-Python API
* Become familiar with VSO toolkit

**Week 1: Database & Codebase Design (Jun. 17th - Jun. 23rd)**

* Work with mentors to define important data fields
  * What types of metadata should be included (i.e. parts from the heliophysical event metadata webservice)
  * How it should be organized
* Use fields to define tables
* Determine primary and foreign keys
* Create an entity relationship diagram
* Hone diagram and table details with community
* Create interaction model between database, python interface, VSO toolkit

**Week 2 and 3: Database Construction (Jun. 24th - Jul. 7th)**

* Build example database
* Populate with example data
* Run tests and refine

**Week 4: Local Database Build Scripts (Jul. 8th - Jul. 14th)**

* Write python script to create local database when SunPy is first run (for each user)
  * Should prompt user
  * Allow user to specify a destination directory or use the default
* Interface with SunPy configuration file
  * Use or create a flag that determines the first use of SunPy
* Configuration file for local database

**Week 5, 6 and 7: Python Interface Build and Midterm Review (Jul. 15th - Aug. 4th)**

* Outline namespace, classes, functions and constants for python framework to interface with the SQLite database
  * Needs to refer to a config file
  * Provide optimized infrastructure for querying the local database and quickly storing downloaded data
* Review and refine model with mentors
* Write code
* Test and refine

**Week 8: Refine (Aug. 5th - Aug. 11th)**

* Editing, testing, documenting and auditing progress

**Week 9 and 10: Interface with VSO (Aug. 12th - Aug. 25th)**

* Integrate with the VSO toolkit
  * Create framework to translate VSO requests into queries for local database via the previously developed
  * Build algorithm to refer to local database for pre-existing data when making VSO request

**Week 11 and 12: Configuration files and Documentation (Aug. 26th - Sept. 8th)**

* Fall instruction begins, reduced hours on project
* Implement user settings
  * Create configuration protocols that allow users to set preferences during VSO requests in regards to the new data downloaded and the already stored data.
* Write and edit a lot of the documentation for the newly developed code base

**Week 13: Buffer (Sept. 9th - Sept. 15th)**

* Just planning a little time in case I've had any miscalculations in time requirements for project chunks

**Week 14: Polish and Final Evaluations (Sept. 16th - Sept. 27th)**

* Polish code
* Complete final tests
* Finish Documentation
* Submit Evaluations

**GSoC 2013 Code Submit Deadline (Sept. 27th - Oct. 1st)**

## Additional Information:
### Contribution to SunPy
Change coordinates when using peek(): <https://github.com/sunpy/sunpy/pull/450>
### Alternate Project Idea:
[HELIO & HEK](https://github.com/sunpy/sunpy/wiki/GSoC-2013-Ideas#helio--hek) - Adding queries and advanced functionality

**Deliverables:**
* A library of functions that allow a user to query the HEK database and run a VSO query based on the results
* A library of functions that allow a user to query the HELIO database and run a VSO query based on the results
* Meta-data translation dictionary between VSO, HEK and HELIO

**Schedule Outline:**
Community bonding period:
* Become GIT power user
* Become familiar with SunPy codebase
* Become more proficient in Python
* Play with HELIO and HEK databases

Week 1 & 2:
* Understand the HEK & HELIO databases
  * Learn the API's
  * Create test cases and implementations
* Learn VSO codebase
* Create Entity-Relationship diagrams of the databases
  * Some kind of map of the meta-data

Week 3:
* Work to create a translating meta-data/database-field dictionary between HEK & VSO
* Work to create a translating meta-data/database-field dictionary between HELIO & VSO

Week 4:
* Outline classes and functions for taking HEK results and generating VSO queries
* Outline classes and functions for taking HELIO results and generating VSO queries

Week 5 & 6:
* Write classes and functions to take HEK & HELIO results and generating VSO queries

Week 7 & 8:
* Testing, editing and documenting new functions
* Midterm review

Week 9:
* Outline classes and functions needed to overplot event contours on images from combined HEK and VSO results

Week 10 & 11:
* Write classes and functions needed to overplot

Week 12:
* Test, edit, document newly written functions
* Test interactions between between newly contributed classes and functions

Week 13:
* Buffer

Week 14:
* Polish code
* Final tests
* Final documentation
* Submit evaluations

### Curriculum Vitae:
Here is a link to my [curriculum vitae](http://nrs-projects.humboldt.edu/~mjm159/documents/cv2.pdf)
### Why SunPy:
After looking through the database of projects and organizations, the SunPy project caught my attention. I love sci-fi novels and the idea of working on a project exploring our friendly, neighborhood star, makes me think of a more advanced time when we as humans have charted and explored our local solar system. I’ve wanted to learn more about astronomy in general for about a year, and this opportunity seems like a great place to learn. As a last reason why SunPy became my focus for this year’s GSoC is that it has the database project. Since my first database class, I’ve been really interested in learning use and integrate databases with applications and this project would really allow me hone those skills. All those points together add up to why I’m interested in applying to this project.
### Vacation Days
It's very probably that over the summer I will go on some weekend trips such as camping or driving up north to visit my family. This would mostly be over weekends but might require some weekdays for travel. It would be a good guess to say that I will probably need a total of a weeks worth of time, but that would be spread out over the whole summer. I'd be working on weekly objectives and I believe that with a few hours on weekends I could easily account for any missed days.
Another thing to take into account is that Fall instruction will begin part way through the last couple weeks of the program. That said, I feel that I should just have small aspects of the project left to finish, and the way my schedule is looking I should have a lot of hours after class to work on the project.
### Final note
Subscribing to the concept of quality over quantity, I decided to focus my energies on a single proposal and after searching through the database of projects, I chose to focus on the SunPy project, and should I be considered please note that there won't be any conflict with other possible GSoC projects.
