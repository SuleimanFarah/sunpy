### Project : Transition to Astropy Time

### Abstract

#### Mentors : @Cadair, @Nabobalis, @Punyaslok


As a research organisation, SunPy involves working with scientific data and hence precision is really fundamental for analysis of those data.

Majority of SunPy uses the `datetime.datetime` object as its representation of time.
However using only `datetime.datetime` has demerits including less precision as opposed to `astropy.time` which supports much higher precision representations of time such as leap seconds. `astropy.time` also supports time formats e.g. TAI time which can not be done using `datetime.datetime`. Hence switching to `astropy.time` is required in order to support such additional features.

The project will involve two parts.

Firstly,  majority of the SunPy library using `datetime` should be modified to use `astropy.Time`.
Secondly, the `parse_time` function residing under the `sunpy.time` module is used by majority of the modules under `sunpy.net`. The function parses a time string and returns a `datetime` object. It therefore needs redesigning in order to return `astropy.Time` object.


The SunPy net module involves a lot of work using the `sunpy.time.parse_time` function. Hence transition to `astropy.time` will not only involve redesign to `astropy.time.Time` but also update to the modules under sunpy.net using `sunpy.time.parse_time`.


### Milestones

* Transition of every part of the SunPy code base to `astropy.Time` instead of using `datetime.datetime` for representation of time.

* Redesigning of the `sunpy.time.parse_time` to return `astropy.Time` object upon parsing any time like inputs. Also in addition the function should have a better API design as opposed to the present situation.

* Updating the modules under `sunpy.net` to use the modified version of `parse_time`.

* Including tests for the newly designed `parse_time` along with proper documentation. Also some of the documentation needs to be updated or created wherever any SunPy module will be using `astropy.Time` instead of `datetime`.



------------------------------------------


### Detailed Description

#### Switching to Astropy.Time from Datetime

A major part of this project involves switching to `astropy.Time` for the modules currently using `datetime` object.

This will involve updating the current functions which involves working on `datetime` objects and switch them to use
`astropy.Time` objects. Apart from this, it will also involve modifying changes to operations performed upon `datetime` objects
which might become invalid upon operating on `astropy.Time` objects.

For example there are many instances of the function `datetime.strftime`. Hence modification needs to be done to use the corresponding sub-function under `astropy.Time`.

Secondly, tests involving functions operating on `datetime` objects needs to be changed and new tests need to be written down for modules working with
`astropy.Time` object.

Also documentation for all such modules under the sunpy codebase needs to be updated to support `astropy.Time`.


#### Redesign of `sunpy.time.parse_time` function

Currently most of the time related operations under SunPy is based on `sunpy.time.parse_time` function. Most modules under
`sunpy.net` like `vso` , `jsoc` and `helio` use `sunpy.time.parse_time`.

###### A quick comparison between **datetime.datetime** and **astropy.time.Time**

| Features | `datetime.datetime` |  `astropy.time.Time` |
| ------------- |:-------------:|:-----------------:|
| Time formats              |   It includes limited time formats. [Time format links](https://github.com/sunpy/sunpy/blob/24ac587c8754ee2fd86c1164c16dc45e7affb02d/sunpy/time/time.py#L27). It does not support time formats like Barycentric Dynamical Time(TDB), International Atomic Time(TAI) among others.| `astropy.time.Time` includes different types of time formats like TAI,TDB,TCB and TCB among others. [Time format links](https://github.com/astropy/astropy/blob/ad1b26915adbb1c360ae88eb4c2a7b0c17e577bd/astropy/time/core.py#L36)  [Issue #2155](https://github.com/sunpy/sunpy/issues/2155)|
| Level of Precision              |  It ignores leap seconds since datetime can not handle leap seconds.             | It can handle leap seconds.    [Issue Link 993](https://github.com/sunpy/sunpy/issues/993). A good thing about `astropy.time` is that it supports setting the precision from the user side|
| Support for Location                |     The current module doesn't support for passing any location frame (an EarthLocation instance)`astropy.coordinates.EarthLocation` | Supports location as user input to the `astropy.Time` class. [Code Link](https://github.com/astropy/astropy/blob/ad1b26915adbb1c360ae88eb4c2a7b0c17e577bd/astropy/time/core.py#L216)

The main change that will involve is to make the `sunpy.time.parse_time` return `astropy.Time`object instead of returning `datetime` objects as of now.
Secondly, the `sunpy.time.parse_time` needs to have a more robust API along with additional features supported by `astropy.Time`. Hence redesigning `sunpy.time.parse_time` function will help the current function to evolve itself into a good API with more features.


### Proposed Solution

There are many shortcomings in `parse_time` function as discussed above which we shall overcome as part of this GSOC project. The following shows a point wise demerit of `parse_time` and its possible solution using `astropy.time.Time`

*  **Working on time strings and setting the format**
   - `parse_time` does not support any provision for different time formats like `iso`, `isot` and `fits` to name a few.
      The following code throws an error while parsing time string of `utc` format in `parse_time`.

      ```
       from sunpy.time import parse_time
       parse_time('2011-01-01T00:10:00.000(UTC)')

      ```

       while we can easily do so in case of `astropy.time.Time`
       ```
       import astropy.time as tm

       x = tm.Time('2011-01-01T00:10:00.000(UTC)')
       ```

       So one possible solution is to check if the given time string is of the above type. If the time string is of the
       above format '2011-01-01T00:10:00.000(UTC)' then we can define a new function , say `diff_format()`to take such
       string as input and return `astropy.time.Time` instance. Later we can make a check if the input string is of the
       above format, then we can just call the `diff_format()` function within the `parse_time`.
      ```
        def parse_time(time_string):

          if(time_string_format is not valid):
             call diff_format

        def diff_format(time_string) :
            return r.Time(time_string)
        ```

  -  **Setting format**

        `astropy.time.Time` has provision for setting the format from the user side. Like if the given time string is in `fits`, the user can also set the time string to own's format choice like `iso`
        ```
         import astropy.time as tm

         x = tm.Time('2011-01-01T00:10:00.000(UTC)')
         //  Its in `fits` format

        x.format = 'iso' // Converting to time format `iso`
        ```

        One solution can be done as follows.
        Within the `parse_time` function we can make provision for allowing the user to set the format by calling the corresponding `Time.format` function on the input string and setting it to the user input format.

- **Setting the Scale**
If the input time string is in `utc` format,    `astropy.time.Time` can set it to other formats like `tai`,    `tdb` and other.
```
   x = tm.Time('2011-01-01T00:10:00.000(UTC)')
   // its in `utc` format.

   x.set_scale('tai')  // setting it to TAI formats
```

  For providing such functionality in `parse_time` we can take user input for the scale and accordingly call the `set_scale` under `astropy.time` from within the `parse_time` to set the scale.


In the end the new tests need to be written down for the newly designed `sunpy.time.parse_time` function since the function will now support `astropy.Time` functionalities
and will return `astropy.Time` object as input.

Since most of the modules under `sunpy.net` uses `parse_time`, the function call and the methods of operating on the object return by the `parse_time` function needs to be
modified. Lastly suitable tests for each such module will have to be written down and replace the existing tests.

Documentation for the parse_time function needs to be written along with suitable examples depicting the `parse_time` returning `astropy.Time` objects.
Similarly documentation for the modules under `sunpy.net` using `parse_time` needs to be updated.



### Timeline

| Time Period |  My Work Plan  |
|:-------------:|:-------------:|
|May 14 - Jun 11| <li> **First Week** -- Dedicate this time to knowing more about the project, work with mentors and discuss with them the desired changes to `parse_time`. I would share my proposed design for returning `astropy.Time` object and upon consent will start implementing the basic functionality. This period would also be dedicated to knowing about the API changes required in `parse_time` and the design for adding extra functionalities of `astropy.Time` like seting scale and format under the functon.</li>  <li>**Second Week** -- Start working on refactoring the `parse_time` function to return `astropy.Time` object.  Also dedicate this time to work on adding features like Time formats for TAI, TDB and others.</li>   <li>**Third Week and Fourth Week**  Work on precision implementation in the current function with guidance to `astropy.time.Time.precision`. Write a function under the `parse_time`class that can set the precision of time by calling `astropy.Time._set_precision`.</li>
|Jun 11 -Jun15|  **Phase 1 Evaluation** - Have the modified version of `parse_time` ready. Should address to any prevalent bugs that may occur due to involvement of new functions. Once its set up , I plan to start working on the tests for the newly designed function. Apart from this, I will try to complete as much as documentation possible. |
|Jun 15 - Jul 9| <li> **First Week** Start working on updating the modules under `sunpy.net` for transition to use `astropy.Time`. This will involve modifying the functions currently taking input as `datetime` to updating them to use `astropy.Time` object. Also the inside body of such function needs to be changed in order to support `astropy.Time` objects.</li> <li> **Second Week**  During this time I plan to work on implementing the tests for all such modules where the transition is required.</li> <li> **Third Week** Dedicate this time to working on documentation for the modules where transition is required. </li> <li>**Fourth Week** During this time , I plan to work on updating the examples. Since the current examples work on datetime objects, they need to be updated to use `astropy.Time`.</li>
|Jul 9 - Jul 13|**Phase 2 Evaluation**  Remaining time will be dedicated to check for any bugs or breaks in the code where the transitions are made.  Cover up any remaining related issues during this time.|
|Jul 13 - August 6 | <li>**First Week** During this time, I plan to replace all usage of previous `parse_time` function with the newly designed one. This will require changes to most of the `sunpy.net` modules like `helio`, `vso`. Much of the code in each of these modules will need to be modified a bit in order to tune in to the newly designed function.</li> <li>**Second Week** Work on increasing test coverage wherever its required.</li> <li>**Third Week** Provide a more detailed documentation for the modules using `parse_time` along with support examples for the user to correlate to.|
|August 6 - 14|**Final Week** - See to if there exist any bugs that was not addressable before. Any pending work or issues will be addressed to during this time|
