About me
========

- Name: Lukas Svaty
- student of masters degree (IT security)
- IRC Nick: StLuke
- Mail: svatykyjas `at` gmail `dot` com

### THE NAME OF THE PROJECT
Glymur / OpenJPEG 1.5 write interface

### SUMMARY
At this moment Glymur is using openJPEG for images stored in JPEG
format. Support latest versions of openJPEG with full support and 1.5
with read support only. As openJPEG is defaultly in version 1.5 in most
operation systems (ArchLinux, Fedora...). Full support of openJPEG 1.5
is required.

### INTENTS
My intention is to add write support for openJPEG 1.5. Creating write
support of glymur for openJPEG 1.5 allows users using this openJPEG
version to write JPEG files.

### BENEFITS
Full support of JPEG on most operation systems (using openJPEG 1.5)

### DELIVERABLES
I am going to deliver interface for write support of openJPEG 1.5. My
plan is to continue after SOCIS on full support of older versions of
openJPEG 1.5. I found out till this moment debian packages contains
only openJPEG of version 1.3 so adding support for older versions
would appreciate community using sunpy/glumur and debian packages.

### PLAN
Will be determined with mentor.
1. get to know glymur and ctypes interface
2. get to know openJPEG 1.5 interface
3. add write interface for openJPEG v.1.5
4. test on distributions:
* Fedora
* ArchLinux
* Red Hat Enterprise Linux


### Timeline
this is a hard timeline in the worst-case scenario
- august:
    - 1. 8 - 31. 9 - getting familiar with sunpy, glymur, python-ctype, openJPEG
- september: study interface of openJPEG 1.5, 1.4, 1.3
    - 1. 9. - 15. 9. - getting familiar with openJPEG interface for older versions
    - 15. 9. - 30. 9. - implementation of interface for openJPEG 1.5
- october: review by mentor
    - 1. 10. - 20. 10. - if suceessfull adding implementation of interface for openJPEG 1.4 and 1.3
    - 23. 10 - 31. 10. - finishing work

### COMMUNICATION
- lukassvaty `at` gmail `dot` com,
- lsvaty `at` redhat `dot` com
 - stluke/lsvaty @freenode #sunpy

mentor:
 - john.g.evans.ne `at` gmail `dot` com
 - jevans @ freenode #sunpy

### QUALIFICATION
I am student of Brno University of Technology in Czech republic and
intern at Red Hat Czech. Got advanced experience in C language from
both school and work project currently I am working on python testing
framework. Due to my skills in python and C connecting this knowledge
I can benefit from this project learning ctype library of python.
Sunpy organisation will gain full support of older version of
openJPEG. Which is default to most common linux operation system. For
the future enhancement I would like to add to glymur after SOCIS project
also full support for versions 1.3, 1.4 as I found out some
distributions still support these (This will be consulted with my
mentor).
