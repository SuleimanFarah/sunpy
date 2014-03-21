## Student Information
    Name(*): Rajul
    Time zone(*): UTC +5:30
    IRC handle including network: rajul@irc.freenode.net
    Source control username(s)(*): rajul-iitkgp
    Provide your user id on Launchpad, Github, Sourceforge, or whatever system your project uses
        Github : rajul-iitkgp, rajul
    Blog(s)(*): http://pettycoder.blogspot.in
    GSoC Blog RSS feed(*): http://pettycoder.blogspot.com/feeds/posts/default?alt=rss

Proposal Title (*)

SunPy: A ginga based data explorer / database browser

Proposal Abstract

Exploring solar data for interesting events and extracting important information is important for being able to do research. Currently, such a GUI program does not exist for Python. However, with the current capabilities of Ginga, it offers a very good base. It allows us to expand to meet the requirements for solar data. Ginga has already several features such as FITS (Flexible Image Transport System), a common image format used in solar physics, support and several plugins that allow basic analysis of data and enable rendering of graphical scientific data.

It also supports several back-ends. Ginga is designed to use a plugin system. This enables SunPy specific plugins to be written that can be installed by any user. We would want to create several plugins that would allow Ginga to be widely spread throughout the solar community.We would want a plugin that uses SunPy's database explorer module and supporting Solar coordinates using AstroPy's WCS module. Further, we want to expand other Ginga plugins like the slit plugin to work on 3D data to produce x-y plots.
Project Background and Idea

In IDL (Interface Description Language), there are two major sources of GUIs for exploring solar data, Solarsoft packages and CRISPEX. Both are using IDL's widget system whose back-end is Motif and make ugly GUIs. Exploring solar data for interesting events and extracting important information is important for being able to do research.

Currently, such a GUI program does not exist for Python. However, with the current capabilities of Ginga, it offers a very good base. It allows us to expand to meet the requirements for solar data. Ginga has already several features such as FITS support and several plugins that allow basic analysis of data. It also supports several back-ends.

Ginga is designed to use a plugin system. This enables SunPy specific plugins to be written that can be installed by any user. We would want to create several plugins that would allow Ginga to be widely spread throughout the solar community.

We would want a plugin that uses SunPy's database explorer module and supporting Solar coordinates using AstroPy's WCS module. Further, we want to expand other Ginga plugins like the slit plugin to work on 3D data to produce x-y plots.

The core part of the project is to make Ginga understand solar coordinates and then to make a GUI widget to integrate into ginga that allows browsing of SunPy database. Ginga supports too many backends but it is more sensible to focus on one GUI backend, ideally QT, than code the plugins for all of them. We can always side-port to other backends as needs evolve. What we want are SunPy specific plugins. Sunpy has a database module which really needs a GUI. However, there is currently no SunPy GUI. Some IDL alternatives for using as GUI tools to browse solar data are currently used. But extending Ginga, which is a nice modernish GUI program is quite needed.

 Project Deliverable

A typical SunPy database record holds meta data and links to files on disk.

We need a plugin for Ginga, that shall have the following capabilities for browsing SunPy's database:

    *

      Solar coordinate handling capabilities
    *

      Database record viewing. Browsing, edit, add and delete database records
    *

      Viewing and Plotting of solar co-ordinates that are contained in files pointed to in the database. Browse, edit, add and delete solar co-ordinates from solar data files.
    *

      Preview of one or multiple records and their associated data
    *

      Filtering/Searching of records based on various parameters/meta-data in database like source, provider, instrument, etc.
    *

      Plotting facility from Ginga as it is an image viewer
    *

      We may need to extend Ginga itself to handle 3d analysis of fits files
    *

      Ability to run various scientific operations from within the plugin and also display the results
    *

      Import and export database records as text and from/to CSV, Spreadsheet, HTML files
    *

      Import and export solar co-ordinates from one file format to another

 Project Implementation and Tasks

    *

      Design and Developing a GUI interface based on Ginga using Qt, for browsing SunPy database and solar data

                +

                  Design a GUI interface that can be used for simple browsing of database records in SunPy database
                +

                  Develop the above design into a Ginga plugin for Qt backend

        * Implementation

                +

                  Ginga has two logical development paths:
                      # using only the Ginga rendering class in a program
                      # starting with the full-featured reference viewer that comes with Ginga and customizing it for some special purpose, typically by modifying one of the plugins or writing a new plugin.
                + The first approach is probably best for when the developer has a custom application in mind, needs a minimal but powerful viewer or wants to develop an entirely new full-featured viewer. The second approach is probably best for end users or developers that are mostly satisfied with the reference viewer as a general purpose tool and want to add some specific enhancements or functionality. Because the reference viewer is based on a flexible plugin architecture this is fairly easy to do.
                + Using the basic rendering class in new programs
                      #

                        Ginga basically follows the Model-View-Controller (MVC) design pattern. The "view" classes are rooted in the base class ImageView. Ginga supports backends for different widget sets through various subclasses of this class.

                        Typically, we can pick a GUI toolkit that has a supported backend (Gtk, Qt or Tk) and write a GUI program using that widget set with the typical Python toolkit bindings and API.
                + Writing plugins for the reference viewer
                      # The philosophy behind the design of the reference viewer distributed with the Ginga is that it is simply a flexible layout shell for instantiating instances of the viewing widget described in the earlier section. All of the other important pieces of a modern FITS viewer--a panning widget, information panels, zoom widget, analysis panes--are implemented as plugins: encapsulated modules that interface with the viewing shell using a standardized API. This makes it easy to customize and to add, change or remove functionality in a very modular, flexible way.
                + I think that a data explorer / database browser for  SunPy, shall require the use of both the above described approaches during development. I plan to use Qt GUI library for development.
                + Reference: https://github.com/ejeschke/ginga/blob/master/doc/manual/developers.rst

    *

      Develop Solar coordinate handling capabilities in the plugin

                + Use the Astropy's WCS module: astropy.wcs contains utilities for managing World Coordinate System (WCS) transformations in FITS files. These transformations map the pixel locations in an image to their real-world units, such as their position on the sky sphere.
                + Implementation:
                      # The World Coordinate System standard is often used in FITS files in order to describe the conversion from pixel to world (e.g. equatorial, galactic, etc.) coordinates. Given a FITS file with WCS information, we can create an object to represent the WCS transformation either by directly supplying the filename or the header of the FITS file
                      # Once the WCS object has been created, you can use the wcs_pix2world method to convert pixel to world coordinates
                      # Reference: http://python4astronomers.github.io/astropy/wcs.html

    *

      Developing an interactive viewing functionality of a database record (a typical database record in SunPy comprise meta-data and file_name that contains solar data for that entry). So need to fetch and render database records from the SunPy's database using Database Explorer module

                      #

                        Implementation: Integration of functionality for exploration within the database from the GUI by using the SunPy's database explorer module to perform the following functions
                      #

                        Connecting to the database
                      #

                        Fetching entries
                      #

                        Adding entries: Adding entires from one or more FITS (Flexible Image Transport System) files, from VSO (Virtual Solar Observatory) interface, and also manually
                      #

                        Displaying entries in a tabular form
                      #

                        Deleting entries
                      #

                        Editing entries: Starring and unstarring entries, Setting and removing tags, Changing custom attributes,
                      #

                        Undoing and redoing operations
                      #

                        Querying the database
                            *

                              Using VSO attributes
                            *

                              Database-specific attributes
                      #

                        Caching
                      # Reference: http://docs.sunpy.org/en/stable/guide/acquiring_data/database.html

    *

      Developing interactive viewing functionality of the solar data contained in a file pointed to in a database record, and viewing of solar co-ordinates

                      #

                        Ginga already has FITS (Flexible Image Transport System) support, as it is basically a scientific image viewer
                      #

                        Implement functionality to read data (solar co-ordinates) from files, typically FITS files, and use the capabilities in AstroPy's WCS module to handle the data and map images as described above
                      # Use the already implemented FITS reference viewer in Ginga complete with- a panning widget, information panels, zoom widget, analysis panes-- implemented as plugins: encapsulated modules that interface with the viewing shell using a standardized API, to render the data

    *

      Develop plotting capability of solar data (solar co-ordinates) and rendering graph/image (ginga is basically an astronomical FITS file viewer)

                      #

                        Ginga has fair plotting capabilities. We can build upon those.
                      # Ginga uses matplotlib for plotting of data
                      # Reference: https://github.com/ejeschke/ginga/blob/master/ginga/qtw/Plot.py

    *

      Extend Ginga itself to handle 3d analysis of fits files

                      #

                        We need to expand some Ginga plugins like the slit plugin to work on 3D data to produce x-y plots.

    *

      Develop import/export functionality from/to different file formats

    *

      Develop capability to run various scientific operations on the solar data from within the GUI and viewing results and generation of reports

                      #

                        Integrate various SunPy's modules and functionality with the GUI, to perform actions on the database and solar data files

 Tools and technologies to be used:

    *

      Language : Python
    *

      GUI library: Qt, PyQt
    *

      GUI Framework: Ginga, a toolkit designed for building viewers for scientific image data in Python, visualizing 2D pixel data in numpy arrays. It can view astronomical data such as contained in files based on the FITS (Flexible Image Transport System) file format.

Project Timeline

21 April to 19 May:

    *

      Community Bonding period
    *

      Besides I shall utilize this time to come up to speed with the Documentation and Design and codebase

19 May to 28 May: (10 Days)

    *

      Design and Developing a GUI interface based on Ginga using Qt, for browsing SunPy database and solar data

29 May to 5 June: (7 days)

    *

      Develop Solar coordinate handling capabilities in the plugin

6 June to 12 June: (5 days)

    *

      Integration of functionalities for exploration within the database from the GUI

13 June to 27 June: (15 days)

    *

      Developing an interactive viewing functionality of a database record (a typical database record in SunPy comprise meta-data and file_name that contains solar data for that entry)

    *

      Developing interactive viewing functionality of the solar data contained in a file pointed to in a database record, and viewing of solar co-ordinates
    * Extend upon the plotting capability of Ginga and rendering graph/image of Solar data
    *

      23 June to 27 June: Mid-Term Evaluation

28 June to 4 July: (7 days)

    *

      Extend Ginga itself to handle 3d analysis of fits files

5 July to 11 July: (7 days)

    *

      Develop import/export functionality from/to different file formats

12 July to 18 July: (7 days)

    *

      Develop capability to run various scientific operations on the solar data using SunPy modules from within the GUI and viewing results and generation of reports

19 July to 28 July: (7 days)

    *

      Although I shall develop tests side-by-side with development, I shall take this week to include more test cases to increase coverage and comprehensively test the code
    * Also, simulate as well as manually execute user actions to test the GUI

30 July to 5 August: (7 days)

    * I have kept this time for debugging the developed code

6 August to 12 August: (7 days)

    *

      Document my work by writing both developer and user manuals

13 August to 22 August: (10 days)

    *

      BUFFER TIME
    *

      18 August to 22 August: Final Evaluation

Link to a patch/code sample, preferably one you have submitted to your sub-org

 

Some other Code Samples:

    * GSOC 2012 work: https://www.google-melange.com/gsoc/project/google/gsoc2012/rajul09/5207287069147136
    * Fjord bug fix: https://github.com/mozilla/fjord/pull/123
    * Financial Time-Series analysis for Stock Prices prediction: https://github.com/rajul/HMM-project
    *  Network Analysis of Natural Signals: https://github.com/psjinx/network-analysis-of-natural-signals

Additional Information:

I am a final year undergraduate student at the Indian Institute of Technology Kharagpur. I am majoring in Chemistry and am very highly interested in Scientific Computing. I have taken up courses in Complex Networks, Distributed Computing, Algorithms, Data Structures, Computational Chemistry, Computational Biophysics, in the past. I have also taken up numerous research projects in varied fields, like Machine Learning, Computational Finance, Computational Chemistry, and Network Analysis. I have completed a Google Summer of Code in 2012, where I participated with the organization Network Time. I also interned at the Barclays' Technology division, and worked with their Market Risk IT team.
I am an intermediate level programmer in Python, C/C++, Java. I am also knowledgeable about Groovy, Ruby, PHP. I have had little experience making GUI applications using Visual Studio. However, I have not yet used PyQt. Although, I have not worked on too many GUI applications, I have developed a number of websites using various technologies like Django, Grails, PHP, Drupal, etc. I have used many testing frameworks in the past, like pytest, Spock, NUnit, Junit. I have given links to a number of my code samples above.

    *  Link to my CV: https://drive.google.com/file/d/0B2mFOuJDrIXmRGloNE5ZazRHZTA/edit?usp=sharing

Other Schedule Information

My main focus during the period of GSoC, shall be development for GSoC itself. I suppose that I shall be able to devote my full attention and time to it and can easily work on the project for like 35-40 hours per week. However, I am ready to put in any extra time and effort that might be demanded by the project. As far as I can as I can anticipate, I shall be having my vacations during most part of GSoC. However, my college does open towards the end of GSoC, in August. I shall not be having any exams during this period and I do not have any travelling plans as of yet.
 