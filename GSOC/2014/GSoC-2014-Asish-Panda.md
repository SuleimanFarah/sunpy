#Project Title
Re-implementation of sunpy.wcs as sunpy.coordinates

### Student Information
  ##### Name: Asish Panda
  ##### IRC nick : kaichogami
  ##### Github account : kaichogami

### Project Abstract

Currently the solar coordinate system is implemented in sunpy in `sunpy.wcs` file. The current module comes with various shortcomings:

1. There is no feasible way of representing solar coordinates in different coordinate representations.

2. Solar coordinates can only be transformed between each other. There is no way to 'create' them, which             limits, its functionality, ability to manipulate them.


This project aims to re-implement the current wcs as `sunpy.coordinates` using the idea described in APE5. This can be briefly explained as:

1. Creation of classes for coordinate representation(Cartesian, Spherical, cylindrical) . These classes would inherit from a common base class to avoid code duplication. Also the various methods for transformation between the representation would be present here.

2. Creating coordinate frame class(helio projective,  helio-centric and helio graphic). These will be subclasses of a parent coordinate frame class. Much of the transformation algorithm between them would be re-usable from the existing `sunpy.wcs`.

### Deliveries
1. Fully implemented and usable Representation Classes.
2. Working classes for solar coordinate system.
3. Ability to transform between different coordinate representation and different solar coordinates.
4. Transformation of solar frames to other celestial frames(as supported by astropy).
5. Integration of astropy.units in sunpy codebase(as much as time permits).
6. Successful tests for their implementation.
7. Documentation for the new changes.

### Detailed Plan and Time Schedule
###### 21 April - 18th May (Community Bonding Period)
1. Read documentation, practice code, get familiar with `astropy.coordinates`.
2. Active in IRC channel, communicate with my mentor.
3. Make my future goals clear. Get the final idea about the project implementation and approach I should take after discussing thoroughly with my mentor.

###### 19th May - 26th May (1 week)
Define the parent class of coordinate representation class. Much of this should
be re-usable from what is already present in   `astropy.coordinates.coordsystems.py`   .

###### 27th May - 10th June (2 weeks)
Define  the sub-classes of coordinate representation classes. Further, they would also contain the methods necessary to transform between various representation, and a single method for invoking them.
If all is implemented according to plan, a possible transformation would look as

   `c1 =  coords.CartesianRepresentation(x,y)`
   `c2 = c1.represent_as(coords.SphericalRepresentation)`

###### 11th June - 18th June (1 week)
During this period of time, I will make sure the tests are running and make documentations.

###### 19th June - 26th June (1 week)
Define the main base class for coordinate frame.
As for the midterm evaluation I plan to submit the new coordinate representation classes.

###### 27th June - 11th July (2 weeks)
Define the subclasses for solar coordinate frame.
These classes can be represented in any coordinate representation previously defined. I will also utilise this time for implementing the transformation between the solar coordinates using the transformation graph in astropy.coordinates. If all is implemented  according to plan, following would be possible:

    `hpc = coord.HPC(coords.CartesianRepresentation(x,y))`

    `hcc = hpc.transform_to(coords.HCC)`
And then again represented as spherical representation with

    `hcc_sphere = hcc.represent_as(coords.SphericalRepresentation)`

###### 12th July - 26th July (2 weeks)
Creating methods for transformation of solar coordinates to different celestial coordinates. This will require time as new algorithms needs to formulated.

###### 27th July - 3rd August (1 week)
Add tests, make documentations and make sure everything is working as planned.

###### 4th August - 14th August (1.5 weeks)
I will use this time to integrate astropy.unit into sunpy codebase. This will add more flexibility to the existing sunpy framework.

###### 15th August - 22nd August
Finalise everything, solve any bug that might arise, add missing documentations  and making sure tests passes.

### Commitment
I plan to work full summer dedicating it for the project. As for now I have no plans or vacation for summer. If by some unseen circumstances I happen to be absent, I will inform my mentor, also it will not last more than 2 days.
Although I should mention that because of my semester exams due on last week of April and will probably last till first week of May(schedule is not out yet) I will not be able to work 40 hours a week for that time, which I will make up for after my exams. (It will be over before the coding time begins).

### Code Samples
I created a pull request, adding tests for sun library, for increasing its tests coverage.  It can be found [here](https://github.com/sunpy/sunpy/pull/799)
Although not for sunpy, I submitted a patch which was merged later, showing a better error in case of failure of conversion in epoch class.
[Link](https://github.com/astropy/astropy/pull/2046)


###References
1. [W.T. Thompson](http://www.aanda.org/index.php?option=com_article&access=bibcode&Itemid=129&bibcode=2006A%2526A...449..791TFUL)

2. [APE5](https://github.com/eteq/astropy-APEs/blob/e27c3f6b0effd888d5fbc72ec098e6590cac4092/APE5.rst)

3. [APE5 implementation](https://github.com/eteq/astropy-api/blob/coordinates-round-2/coordinates_api_2.py)
