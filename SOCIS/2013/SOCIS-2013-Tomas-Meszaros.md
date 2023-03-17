Personal Details
================

- Name: Tomas Meszaros
- Email: exo@tty.sk
- IRC: examon (online most of the time at irc.freenode.net and irc.oftc.net)
- GitHub: examon (<https://github.com/examon>)

Background and Programming Experience
=====================================

I've graduated this year from the Slovak University of Technology with BSc. in Applied Informatics. I'm currently enrolled in Masaryk University (CZ, Brno) and planning to continue studying computer science.

I started with programming at the high school, probably about 5 years ago. Python was my first language and I have done several projects in Python since then (my own small, but also bigger open-source projects). I like Python because of its flexibility, which is very handy. Writing in Python is always fun for me and debugging is not really that much painful (in comparison to C). I can also read/write code in other languages (Java, C++, C#, etc.), however I use mostly Python and C (sometimes Bash).

I heavily rely on Git/GitHub and vim when I'm programming. Life so is much easier with those tools and I feel very comfortable and in control when I'm using them.

I'm long time Linux user (over 5 years now) so I'm programming on my Linux box. I've got experience with every major distribution and can fix almost every problem on my own.

Project
=======

I would like to work on the "Improvements to Map 3D classes". Currently, mapcube object represents series of spatially aligned images, but there is requirement for additional feature development (for example: being able to sort the Maps in the cube; image registration routine able to align images in the cube to a high degree of accuracy).

Because MapCube is implemented as a list of Map object, it would be required for the further work to implement conversion between this list of Maps and a 3D map object (using np.ndarray).

Furthermore, improvements to MapCube should include the possibility to store a MapCube of CompositeMaps (CompositeMap class also requires a lot of improvement).

I'm still student and apparently got a lot of free time during this summer :-) so I'm willing to invest a lot of time into this project.

Time Line
=========

- ```Week 1-2:``` Research more about the problem and desired problem solution. Identify the required features and discuss with mentor/community potential approach and methods used for the development.

- ```Week 3-4:``` Get more familiar with the MapCube code. Design and implement "sort the Maps in the cube"  feature prototype.

- ```Week 5-6:``` Get feedback from mentor and community. Fix potential bugs, write tests and documentation for written code. Discuss design/implementation for "image registration routine upgrade" feature.

- ```Week 7-8:``` Midterm review. Design and Implement "image registration routine upgrade". Get feedback, debug written code, write tests and documentation.

- ```Week 9-10:``` Cleanup written code. Fix potential bug or write additional requested functionality by the community. Discuss approach for implementing "list<->np.ndarray conversion".

- ```Week 11-12:``` Implement "list<->np.ndarray conversion". Get feedback, cleanup and document implementation. Design and implement prototype for "storing MapCube of CompositeMaps" feature.

- ```Week 13-14:``` Final review. Last code cleanup, write missing tests and documentation. Get feedback, implement missing parts or improve current code.

Experience with SunPy
=====================

I'm already familiar with the SunPy development workflow (Git/GitHub) although I'm not a long time SunPy user or developer.

I wanted to understand the SunPy code so I've gone through the issues marked on the SunPy GitHub page and tried to fix some of them (<https://github.com/sunpy/sunpy/pull/512>). I think the code is pretty well written and easy to read/understand for me.
