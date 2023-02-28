# Region of Interest

# **Organisation: OpenAstronomy**

## **Sub-Organization: SunPy**

## **Student Information**

* **Name:** Yudhik Agrawal

* **Time Zone:** +05:30 GMT

* **IRC Handle:** yudhik

* **Github ID:** [yudhik11](https://github.com/yudhik11)

* **Instant Messaging:** Google Hangout: [yudhik100@gmail.com](mailto:yudhik100@gmail.com)

## **University Information**

* **University:** [International Institute of Information Technology, Hyderabad](https://www.iiit.ac.in)

* **Major:** Computer Science and Engineering

* **Current Year:** Second Year (4th semester ongoing)

* **Expected Graduation Date:** 2021

* **Programme:** Bachelor of Technology (B.Tech) and Master of Science in Computer Science and Engineering by Research (Dual degree)

## **Work and Open Source Experience**

* Hackathons -- [megathon](https://github.com/Kanav-7/Megathon-17) (inter-college) and [amazon alexa hackathon](https://developer.amazon.com/alexa/console/ask/build/custom/amzn1.ask.skill.6da8f5a1-439d-4b04-bdc7-1833ab7312c3/development/en_US/dashboard)(going at present)

* Currently a core member of IIIT-Coding Club

* Made a [2D game](https://github.com/yudhik11/OpenGL-PacmanKiller) and [3D game](https://github.com/yudhik11/OpenGL-LOZ) in OpenGL

* Made an AI [tic-tac-toe bot](https://github.com/yudhik11/tic-tac-toe)

* Contributed in [scilab](https://www.scilab.org/en)

* [Js13k game](https://github.com/yudhik11/js13kgame) (JavaScript coding competition)

* **Operating System:** I use Ubuntu and Windows. Apart from the above projects, I am also proficient in C/C++ and I also love to participate in competitive programming.

## **PR links**

* Sunpy:

  * Region of Interest Object

    * (WIP) [https://github.com/sunpy/sunpy/issues/164](https://github.com/sunpy/sunpy/issues/164)

  * Functionality of concatenation of two Unified Responses from fido.fetch

    * (Open) [Overrode `+` operator for UnifiedResponse object](https://github.com/sunpy/sunpy/pull/2466)

  * The simple extension to Map Stonyhurst grid plotting.

    * (Merged) [Fixed Padding values in some of the documentation pages](https://github.com/sunpy/sunpy/pull/2497)

  * importing lightcurve and net under Python 2 ends the world

    * (WIP) [https://github.com/sunpy/sunpy/issues/2122](https://github.com/sunpy/sunpy/issues/2122)

  * Solved instant disappearing of timeseries plot

    * (Contributed in) [https://github.com/sunpy/sunpy/pull/2467](https://github.com/sunpy/sunpy/pull/2467)

* Scilab:

  * Arguments passed to the function in wrong order

    * (Merged) [Arguments in wrong order](https://codereview.scilab.org/#/c/19689/)

  * Typecasting wrong data type

    * (Merged) [Sizeof not portable](https://codereview.scilab.org/#/c/19660/)

  * Data Race condition

    * (WIP) [Data Race condition](https://codereview.scilab.org/#/c/19691/)

  * Storing a long number in int

    * (WIP) [Bad bit shift operation](https://codereview.scilab.org/#/c/19690/)

  * Division or modulo by zero

    * (WIP) [Division or modulo by zero](https://codereview.scilab.org/#/c/19693/)

  * Pointer value was not freed before returning

    * (WIP) [Resource Leak](https://codereview.scilab.org/#/c/19662/)

  * Null value being accessed

    * (WIP) [Explicit null dereferenced](https://codereview.scilab.org/#/c/19686/)

  * Useless call being made/ Dead code

    * (WIP) [Useless call](https://codereview.scilab.org/#/c/19658/)

## **Project Proposal Information**

**Project**: ***Region of Interest***

**Mentors :** [dpshelio](https://github.com/dpshelio) ,[wafels](https://github.com/wafels)

## **Abstract**

This project will need to redesign **roi.py** and **chaincode.py** to work well with coordinates used in the **ROI** and will cover not only images but other dimensions (**timeseries** or **multidimensional data**). This project aims to design and implement an object so that we can find **ROI in any physical dimension** ( such as spatial area or temporal range and interact with the rest of data types used in sunpy).

The **TimeRange object** could be used to store the **time extent** of the "region". The region of interest object should also be derivable from the main object classes - **HEK, HELIO.**

So user uses HEK module to get a **list of events** of some time range and also those instances can then be **drawn as overlays on a Map instance**, like **`map.show(overlays=hekEvent)`**.

We will start it by using ROI on images and then extend it to use timeseries as a parameter.

### **Project Goals :**

* Design the object to accommodate basic geometric shapes ( square, rectangle, circle, polygon, ..etc) as ROI.
* Interaction with other data types (overplot on maps, time ranges on timeseries,...).
* Overlaying Multiple ROI.
* Extract information from the interaction (overlay a sunspot detection on a corona image and extract the information related to ROI .e.g total area of that region or the date at which it was observed).
* Handling invalid user inputs.
  ​

### **Deliverables:**

* Making a fully functional ROI object which will be capable of interacting with multiple data types of the sunpy and return a spatial area or temporal range for the queries.

* ROI module will be capable of returning particular area in the Sun at a particular moment in time, with the extent of area, contour, when it was observed etc.

* ROI will also be capable of returning list of events for a specified time range for a HEK query and for HELIO (hfc is not accessible from sunpy in an easy way so it depends on how the module is modified during these months, so the feature will be implemented as guided by the mentors).

* User will be able to overlay multiple ROI at the same time eg: `aia.show(overlay = [roi1, roi2, ...]`.

* Make future addition of similar objects easier to integrate.

**Detailed Description:**

Currently, if users want to get information about Solar events such as flare information, active regions, they would have to first find HEK / HELIO results and after then specify the timerange (which is the window he is interested in) and then club those two as an overlay. Finally, after that while reproducing images user will have to specify the bounding box to focus on a certain region.

Eg. If a user is interested in the finding the biggest coronal hole within 80 degrees north/south of the equator in "sunpy.data.sample.AIA_171_IMAGE"

```python
Class roi(object):
 def __init__ (self, object = None , timeseries = None, responses = None, *argv, **kwargs):
  if object is  'hek':
   self.hek_roi(responses, *argv, **kwargs)
 def hek_roi(self, responses = None, *argv, **kwargs):
  # for all responses building a return value based on different
  # Arguments
  return roi_response

   def helio_roi(self, responses = None, *argv, **kwargs):
  # for all responses building a return value based on different
  # Arguments
  return roi_response
 def time_range(self):
  ....
  return TimeRange(self.start_time, self.end_time)
   def plot():
        ...
        return plot
    # various other functions


```

**<u>Class ROI</u>**

**Parameters:**

* **Object** – type of object.
* **timeseries** – will contain sample data and source.
* **Response** - (ndarray) - array of responses.
* **Methods** - args that will define ROI attributes and properties.

**Returns:**

* **Returns**  – A final ROI response which can be overlayed on an image.

**Actual Image of AIA_171**

![Actual Image of AIA_171](https://drive.google.com/uc?id=1_MfpyUQdVSbxUqul9hAjsS8BYLfIth2k)

## CODE COMPARISON

### Initializing map and collecting responses from HEK

```python
imports ...
aia_map = sunpy.map.Map(sunpy.data.sample.AIA_171_IMAGE)
hek_client = hek.HEKClient()
start_time = aia_map.date - timedelta(hours=2)
end_time = aia_map.date + timedelta(hours=2)
responses = hek_client.search(hek.attrs.Time(start_time, end_time),
                             hek.attrs.CH, hek.attrs.FRM.Name == 'SPoCA')
```

​

```python
### Work which ROI will automate

area = 0.0
for i, response in enumerate(responses):
   if response['area_atdiskcenter'] > area and np.abs(response['hgc_y']) < 80.0:
       area = response['area_atdiskcenter']
       response_index = i

ch = responses[response_index]
p1 = ch["hpc_boundcc"][9:-2]
p2 = p1.split(',')
p3 = [v.split(" ") for v in p2]
ch_date = parse_time(ch['event_starttime'])
ch_boundary = SkyCoord(
   [(float(v[0]), float(v[1])) * u.arcsec for v in p3],
   obstime=ch_date,
   frame=frames.Helioprojective)
rotated_ch_boundary = solar_rotate_coordinate(ch_boundary, aia_map.date)
```

```python
### ROI

req_roi = roi(object = 'hek', responses, area_atdiskcenter_max = true ,hgc_y_max = 80 )
```

```python
### Plotting

fig = plt.figure()
ax = plt.subplot(projection=aia_map)

aia_map.plot(axes=ax) #for current state
aia_map.plot(axes=ax, overlays = req_roi) #with ROI

ax.plot_coord(rotated_ch_boundary, color='c')
ax.set_title('{:s}\n{:s}'.format(aia_map.name, ch['frm_specificid']))
plt.colorbar()
plt.show()
```

**RESULT WITH MARKED ROI**

![RESULT WITH MARKED ROI](https://drive.google.com/uc?id=1DH5RLLP6ijn6RzvrSSHyqjoPtRYJ_mEC)

It will be more convenient to use ROI module as it will **save a user from writing a lot of code**. ROI will use various features to **enhance user experience** like aia.show(overlays=hek_events) will automatically **mark our ROI** with a certain **zoom** which is intended and will have space for **panning** as well.

The final reproduced image will look like:

![zoomed image](https://drive.google.com/uc?id=1b38cuhDC-WwwgcjCkCP6OLgigjNnCkco)

### Multiple ROI's plotted

### Current implementation without ROI

```python
responses =[None]*4

### Roi-1: (biggest active region within 50 degrees east/west on the equator line)

responses[1] = hek_client.search(hek.attrs.Time(start_time, end_time),hek.attrs.AR )

### Roi-2: (biggest active region within 50 degrees east/west on the equator line)

responses[2] = hek_client.search(hek.attrs.Time(start_time, end_time),hek.attrs.CH )

### Roi-3 (biggest coronal hole within 80 degrees north/south fn the equator)

responses[3] = hek_client.search(hek.attrs.Time(start_time, end_time),
                           hek.attrs.CH, hek.attrs.FRM.Name == 'SPoCA')

response_index = [None]*4
rotated_ch_boundary = [None]*4
for j in range(1,4):
 area = 0.0
 for i, response in enumerate(responses[j]):
      if j == 3 and response['area_atdiskcenter'] and response['area_atdiskcenter'] > area and np.abs(response['hgc_y']) < 80.0:
          area = response['area_atdiskcenter']
          response_index[j] = i
      elif response['area_atdiskcenter'] and response['area_atdiskcenter'] > area and np.abs(response['hgc_x']) < 50.0:
          area = response['area_atdiskcenter']
          response_index[j] = i

ch = responses[j][response_index[j]]
p1 = ch["hpc_boundcc"][9:-2]
p2 = p1.split(',')
p3 = [v.split(" ") for v in p2]
ch_date = parse_time(ch['event_starttime'])
ch_boundary = SkyCoord(
 [(float(v[0]), float(v[1])) * u.arcsec for v in p3],
 obstime=ch_date,
 frame=frames.Helioprojective)
rotated_ch_boundary[j] = solar_rotate_coordinate(ch_boundary, aia_map.date)
```

### With ROI

```python
responses = [None]*4

### Roi-1: (biggest active region within 50 degrees east/west on the equator line)

responses[1] = hek_client.search(hek.attrs.Time(start_time, end_time),hek.attrs.AR )

### Roi-2: (biggest active region within 50 degrees east/west on the equator line)

responses[2] = hek_client.search(hek.attrs.Time(start_time, end_time),hek.attrs.CH )

### Roi-3 (biggest coronal hole within 80 degrees north/south fn the equator)

responses[3] = hek_client.search(hek.attrs.Time(start_time, end_time),
                           hek.attrs.CH, hek.attrs.FRM.Name == 'SPoCA')

req_roi = [None]*4
for i range(1,4):
 if i == 3:
  req_roi[i] = roi(object = 'hek', responses[i], area_atdiskcenter_max = true ,hgc_y_max = 80 )
 else:
  req_roi[i] = roi(object = 'hek', responses[i], area_atdiskcenter_max = true ,hgc_x_max = 50 )</td>

  ∀roi  rotated_ch_boundary[i] = solar_rotate_coordinate(ch_boundary[i],

Aia_map . date )
ax = plt.subplot(projection=aia_map)
aia_map.plot(axes=ax)
∀roi  ax.plot_coord(rotated_ch_boundary[i], color='c')
```

![Multiple ROI marked](https://drive.google.com/uc?id=1-KXGFdYbdMyj_k4RJi_ufZLw47mmq5cv)

**Various Geometric Shapes which will help to plot ROI**

For geometric shapes like square and circle, the arguments for ROI can be passed like:

​

```python

Square[center_x, center_y, side_length]
Rectangle[center_x, center_y, breadth, height]
Circle[center_x, center_y, radius]

```

These geometric shapes can be used to represent ROI on a specific need and for the rest of the responses we can use chaincode([convex](http://mathworld.wolfram.com/ConvexPolygon.html) and [concave](http://mathworld.wolfram.com/ConcavePolygon.html) polygon).

#### **Invalid user input**

As mentioned in the issue: [2498](https://github.com/sunpy/sunpy/issues/2498)

**Invalid inputs** by the user can be handled by first checking whether the given args belong to a dictionary of attributes of the object.

**Proposed solution:**

* Returning each wrong argument can be cumbersome so an error message can be returned describing the method and args which are expected and the specific order.
* Rest of the handling can be done in accordance with the proposed solution that we come up along with the mentors.

<u>Hence the following are the **main tasks** of the project</u> :

1. Make the object that could be used to define the region of interest (ROI).
2. ROI module will use various objects and data types as inputs (HEK/HELIO) to be used as overlays which could be plotted on the same image.
3. Extract information from the interaction (overlay a sunspot detection on a corona image and extract the total area of that region or the date at which it was observed).
4. Later the ROI can be extended to objects like timeseries.
5. Extensive testing of different possibilities for the plot of ROI.

## **References:**

**HELIO**: [http://www.helio-vo.eu/](http://www.helio-vo.eu/)

**HEK:** [http://www.lmsal.com/hek/index.html](http://www.lmsal.com/hek/index.html)

**ROI:** [http://docs.sunpy.org/en/latest/guide/roi.html?highlight=roi](http://docs.sunpy.org/en/latest/guide/roi.html?highlight=roi)

**AIA to STEREO Coordinate Conversion:** [http://docs.sunpy.org/en/stable/generated/gallery/SDO_to_STEREO_Coordinate_Conversion.html#sphx-glr-generated-gallery-sdo-to-stereo-coordinate-conversion-py](http://docs.sunpy.org/en/stable/generated/gallery/SDO_to_STEREO_Coordinate_Conversion.html#sphx-glr-generated-gallery-sdo-to-stereo-coordinate-conversion-py)

**GOES Flare and HEK Plot:** [http://docs.sunpy.org/en/stable/generated/gallery/goes_hek_m25.html](http://docs.sunpy.org/en/stable/generated/gallery/goes_hek_m25.html)

**Timeseries:** [http://docs.sunpy.org/en/latest/code_ref/timeseries.html](http://docs.sunpy.org/en/latest/code_ref/timeseries.html)

## **Timeline**

<table>
<tr>

<td>Time Period</td>

<td>Plan</td>

</tr>

<tr>

<td> <b>Community Bonding</b> (April 24 - May 22, 2018) </td>

<td><ul> <li>Get <b>familiar with ROI</b> and responses from <b>various data-types</b> which can be used to plot ROI.</li><li>Laying the <b>base to start building ROI</b>.</li> <li>Learn more about the <b>various attributes of HEK/HELIO</b>.</li></ul>

</td>

</tr>

<tr>

<td></td>

<td><b>Coding Period Starts (May 14, 2018)</b></td>

</tr>

<tr>

<td>May 14 - 22, 2018 (Week 1)</td>

<td><ul><li>Implementing <b>basic geometric shapes</b> along with chaincode (eg: rectangle, circle, polygon etc).</li><li>Implement module for <b>more complex structures</b> (like chaincode where the shape is not consistent).</li></ul></td>

</tr>

<tr>

<td>May 23 - June 6, 2018 (Week 2 - Week 3)</td>

<td><ul><li>Embedding <b>hek / helio responses as inputs in ROI</b>.</li> <li>Querying for <b>multiple attributes</b>. Eg.

```python
region = ROI(hek_response)
region.plot() # overlay the plot over a hek region
region.position() # tells the centre of the location
region.area() # gives me the area of the region
region.date() # tells me when that was observed
```

</li></ul></td>

</tr>

<tr>

<td>June 6 - 14, 2018 (Week 4)</td>

<td><ul><li>Write <b>tests</b> and <b>documentation</b>.</li><li>Cross-check the work done for the submission of the first phase of evaluation.</li></ul></td>

</tr>

<tr>

 <td></td>

<td><b>First Evaluation ( June 11 - 15, 2017 )</b></td>

</tr>

<tr>

<td>June 15 - July 6, 2018 (Week 5 - Week 7)</td>

<td><ul><li><b>Overplotting ROI</b> on the map. </li><li>Accepting <b>multiple overlays</b> which will be plotted layerwise. Eg.

`aia.show(overlays = rois) rois = [ roi1, roi2, ....]`
</li></ul></td>

</tr>

<tr>

<td>July 7 - July 13, 2018 (Week 8)</td>

<td><ul><li>Write <b>tests</b> and <b>documentation</b>.</li> <li><b>Add 'timeseries'</b> as an attribute in ROI (as a number of instruments are supported through subclasses).</li> <li>Cross-check the work done for the submission of the second phase of evaluation.</li></ul> </td>

</tr>

<tr>

<td></td>

<td><b>Second Evaluation ( July 9 - 19, 2017 )</b></td>

</tr>

<tr>

<td>July 14 - July 28, 2018 (Week 9 - Week 10)</td>

<td><ul><li><b>Incorporating Timeseries</b> with <b>hek/helio events</b>.</li><li> Efficiently plotting <b>multiple attributes at the same time</b> without causing them to overlap and are <b>easily explorable and accessible</b>. </li></ul></td>

</tr>

<tr>

<td>July 29 - August 5, 2018 (Week 11)</td>

<td><ul><li>Handling <b>Invalid user inputs.</b>.</li><li><b>Buffer period</b>.</li></ul></td>

</tr>

<tr>

<td>August 6 - August 10, 2018 (Week 12 )

</td>

<td><ul><li>Work on any leftover tasks which were stuck before.</li><li>Write <b>tests</b> and <b>documentation</b>.</li> <li><b>Resolve merge conflicts</b> (if any).</li> <li><b>Refactoring of code</b></li></ul></td>

</tr>

<tr>

<td></td>

<td><b>Submit Code and Final Evaluations (August 6 - August 14)</b></td>

</tr>

<tr>

<td>August 14 - August 21, 2018</td>

<td><b>Mentors Submit Final Evaluations</b></td>

</tr>

<tr>

<td>August 22, 2018</td>

<td><b>Results Announced</b></td>

</tr>
</table>

### **Software packages to be used**

**Language:** Python

**Libraries and modules:** astropy, json, pytest, sympy

**SunPy dependencies:** numpy, scipy, matplotlib, suds, pandas

### **How I propose to complete the project:**

I have been contributing to SunPy from the beginning of the February. I will discuss design specific problems and implementation details with my mentors before starting a new topic. Also, if I feel any problem that needs to addressed or designed carefully, I would rather go through several documentations and try finding solutions online and won't hesitate approaching mentors for my doubts.

I spent a lot of time going through SunPy documentations and also through several references provided to me other than that. I also worked on some pseudo codes and got to know about its functionalities and figured out the way to design a solution.

* I will push to my pull requests regularly to keep my mentors updated on my work.
* I will be updating the documentation parallelly with functionalities and methods I implement.
* I will update my blogs regularly.
* I will be available all the time for reviews and answer questions regarding my implementation.

## **GSoC**

### **Have you participated previously in GSoC? When? With which project?**

**No.** This is the **first time** that I would be participating in GSoC

### **Are you also applying to other projects?**

**No.** **SunPy** is the only organization that I am applying for.

### **Commitments**

I commit to work for 35-40 hours a week during GSoC period. I don't have any other internship or work during this summer.

I have my end Semester exams from 19 April – 27 April so I won't be able to devote most of the time to the project. During that week I would be able to give 15-20 hrs and would further try whenever necessary.

My next semester will start from the 1st week of August still I would be able to devote most of my time as in the initial days of the semester we have less workload.

### **Eligibility**

Yes, I am eligible to receive payments from Google. For any queries, clarifications or further explanation of any approach/feature, feel free to contact me at yudhik100@gmail.com and I shall be happy to reply.
