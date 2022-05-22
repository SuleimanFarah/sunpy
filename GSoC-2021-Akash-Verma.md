# [SunPy] Building, Testing, and Wrapping HelioViewer API in a Package

## Personal Details and Contact Information

* Name: Akash Verma

* Email: [akashzsh08@gmail.com](mailto:akashzsh08@gmail.com)

* Github: [@akash5100](https://github.com/akash5100)

* University: Shri Shankaracharya Institute of Professional Management and Technology, Raipur, Chhattisgarh, India.

* Timezone: Indian Standard Time (UTC+05:30).

* [Resume](https://docs.google.com/document/d/1iqOQ1Cc5LfY3E92EodiKU9qQHVNyoGzieibwHxTa7oQ/edit?usp=sharing), [website](https://akashverma.vercel.app/).

I, Akash Verma, am pursuing a B.Tech in Computer Science from India. I aspire to be a vivid backend programmer. I also have various other interests such as physics, mathematics, and astronomy. I also enjoy reading science and biography books about inventors and physicists.

## Synopsis

The **[Helioviewer](https://helioviewer.org/)** project is developing a suite of technologies that allow users around the world to visualize, browse and access these heterogeneous datasets in a highly customizable fashion. They do so by providing public APIs to the developers. In sunpy, we can query to Helioviewer API to get those data, with the help of a **[HelioviewerClient](https://docs.sunpy.org/en/stable/api/sunpy.net.helioviewer.HelioviewerClient.html#helioviewerclient)** instance that can be used to make HTTP requests and manipulate the results as required.

The current HelioviewerClient in sunpy does not offer full access to the Helioviewer API and is limited to these five endpoints:

* **GET** /v2/getJP2Image/

* **GET** /v2/takeScreenshot/

* **GET** /v2/getClosestImage/

* **GET** /v2/getDataSources/

* **GET** /v2/getJP2Header/

But the Helioviewer API has a huge number of endpoints that provide different functionality.

The current implementation doesn’t integrate with Fido (sunpy’s search and download interface) and also, the HelioviewerClient doesn’t belong to sunpy’s core and needs to be moved out of the codebase.

In this project, I will be proposing wrapping every aspect of Helioviewer API in a Python package and extending its support to Fido with the help of a new client.

Through this project, I will be working with **[Nabil Freij](https://github.com/nabobalis)**, **[Jack Ireland](https://github.com/wafels)**, and **[Daniel Garcia Briseno](https://github.com/dgarciabriseno)** as my mentors.

## Approach

First, and most importantly, how we will fetch data from the API, writing test cases and documentation, and second, extending Helioviewer support to the Fido client.

There are many ways to fetch data from an API, the most famous and simplest will be using the library **[requests](https://docs.python-requests.org/en/latest/)**.

### **1. Structuring the Helioviewer Package**

There are two possibilities. First, to use a **set of functions,** a straightforward implementation of methods and the other is to use **Classes**. They both have their own positives and negatives.

**Why do we need Class?**

Sometimes the OOP concept makes things complicated but sometimes they are quite useful, for example, reusability of code (**inheritance**), ease of maintenance, adding new features, flexibility, and hiding the code not needed by the user (**abstraction**), etc.

In this model, instead of using a big central class, we can either create a class for each endpoint or a class for a similar group of endpoints. In this way, we divide functions into groups. We are making a package as a final product and this could be a good and valid reason not to use a big central class.

To have a consistent interface and clean structure, make a **parent class** that wraps the URL, HTTP method, Parameters, sending, and handling of the response.

```python
# we could use an environment variable to set baseurl
# of the package.

BASEURL = "https://api.helioviewer.org/v2/"
class HTTPLayer:
    """
    Parent Wrapper Class
    """

    def __init__(self):
    # we can also set url with self.url
    pass

    def request(self, url, query):
    # using requests
    response = requests.get(url, params=query)
    return response

    def parse_response(self, response):
    # returns a parsed result after getting response
    # all the parsing logic, depends on the endpoint
    return result
```

Writing the endpoint method will totally depend on the number of the required and optional parameters of endpoints. Each **endpoint class** will **inherit** the parent class and overrides the URL, HTTP method, and Parameters. Separating the Request and Response parts will make the unit tests easier.

The endpoint class can be like

```py

class getJP2Header(HTTPLayer):
    """
    Endpoint Class
    """
    def __init__(self, id: int, callback: str=None):
    self.id = id
    self.callback = callback
    url = BASEURL + "getJP2Header/"
    def parse_response(self, response):
    # This contains the parsing logic.
    # for now, just returning the raw data
    return response.text

    def request(self):
    # Returns a response object
    # All the required parameters
    
    query = {
    "id": self.id,
    }

    # If the optional parameter is passed,
    # then append to dictionary

    if self.callback not None:
        query["callback"] = self.callback
        response = self.request(self.url, query)
        # This could be a link to the downloaded file
        result = self.parse_response(response)
        return result
```

A more complex solution would be to making subclasses, putting them in an "endpoints" directory like **endpoints/getJp2Header.py** endpoints would have an `__init__.py` that exposes all the individual APIs. Then the interface HelioviewerClient would **import {endpoints}** and attach them to itself. Then to add a new endpoint you would drop another file like **endpoints/new_endpoint.py** and it would get picked up automatically.

When we call a method, the following stuff happens:

* Create a dictionary of parameters.

* Make an HTTP request, and get the response object.

* Parse the response object and create a result.

* Return the result.

After the implementation of **request** and **response** parts, a finishing touch by the implementation of exceptions for the bad/illegal argument combinations, for example when a user **calls** a method **without arguments**, instead of popping an error like

```shell

Traceback (most recent call last):

    File "example_requests.py", line 26, in &lt;module&gt;

    res = API.getJP2Header()

TypeError: getJP2Header() missing 3 required positional arguments: 'source_id', 'Path', and 'callback'
```

The errors will be understandable to Users, like

```s
getJP2Header()

TypeError: Missing arguments 'SOURCE_ID', 'PATH', 'CALLBACK'
```

Another example would be, if a user **calls** a method with the **wrong argument**,

```s
getJP2Header()

TypeError: Invalid argument: 'SOURCE_ID' must be 'INTEGER' not 'STRING'
```

#### The Package in use
The usage of the client will be simple and straightforward, the user creates an instance of the endpoint, and then it will be used to make queries against the API using the same parameters one would use to make a web request.

The usage of already implemented endpoint methods will not change in the new implementation, so the old user will stay familiar with the usage, although it may be decided while implementation.

The usage of the package will be like

```python
from HelioviewerApi import getJP2Header
api = getJP2Header()
api.request(params)
self.request("getJP2Header", params)
```

[Here is a gist to show how the above will work.](https://gist.github.com/akash5100/b0d130e3c412449a0baa50842298965e)

#### Testing

Writing tests for an API wrapper or a program that interacts with an external database is slightly more complicated. The challenges we going to face:

* The changes in the data from API will make the test unpredictable.

* Latency due to connection will slow down the test.

**The Solution**

If we **mock our requests**, we receive data from our requests which does not change over time. Hence no connection is set up between the server and the client. We can use pytest as our testing framework as most of the SunPy project uses pytest. I admit that I am fairly new to testing, therefore I learned unittest before learning pytest and [wrote a gist to show a simple test using unittest.](https://gist.github.com/akash5100/cb6a6040dfd5a2de32215a0035c067e0)

#### API Endpoints

Setting the implementation of the API endpoint methods as the priority, I decided that, if ~2 endpoints methods were implemented per week, we can achieve wrapping 55% of API before the first evaluation, if any endpoint requires low effort then I can also implement more than ~ 3 endpoints. The first one or two will take longer. then subsequent ones should be faster. Once we have the class hierarchy setup adding new endpoints should be a lot easier. This will save time for the implementation of the **Fido client**. Implementing each endpoint will include writing a test case along with documentation for each of them. Every endpoint implementation will be pushed in a different git branch with a clear summary, rather than a single big pull request. This will help mentors to monitor my progress easily and probably save their time.

Here’s a list of all the API endpoint classes that will be implemented, in this project:

* **JPEG2000** [5 endpoints]

* **Movies** [5 endpoints]

* **Screenshots** [2 endpoints]

* **Official Clients** [4 endpoints]

* **Youtube** [4 endpoints]

* **Web Site** [1 endpoint]

### **2. The Fido Client**

Talking to **[Daniel Garcia Briseno](https://github.com/dgarciabriseno)**, I found that the Fido client will be a **[scraper](https://docs.sunpy.org/en/latest/dev_guide/contents/extending_fido.html#writing-a-new-scraper-client)** and all the images are accessible from the base url, [https://api.helioviewer.org/jp2/](https://api.helioviewer.org/jp2/).

#### Implementing the Scraper Client

The scraper client uses the URL scraper to find files on the remote server. The three components that are needed to make the Scraper client are

* Attribute** Base Url**: [https://api.helioviewer.org/jp2/](https://api.helioviewer.org/jp2/)

* Attribute **Pattern: **This is a template that is used to extract the metadata from URLs matched by **Base Url**.

For example, **[https://api.helioviewer.org/jp2/AIA/335/2012/01/29/](https://api.helioviewer.org/jp2/AIA/335/2012/01/29/)** this URL can be used to make a request, breaking it down we have this template

![Screenshot from 2022-05-22 13-09-09](https://user-images.githubusercontent.com/53405133/169684263-21f06e76-47f2-43c6-b602-1400549602bf.png)

* Define a method **register_value()** which registers **attributes** supported by the client. The attrs returned by this method are used to match the client search attrs.

## Deliverables

#### Deliverable 1

Expected by Evaluation 1

**Wrapper**

* **Parent class** wrapping the HTTP methods, URL, and parameters and its unit tests.

* **Five** endpoint classes for the API group **JPEG2000** and their unit tests.

* **Five** endpoint classes for the API group **Movies** and their unit tests.

* **Two** endpoint classes for the API group **Screenshots** and their unit tests.

* Documentation for all the Classes built so far. Add example requests and responses for the API endpoint class with their functionality.

#### Deliverable 2

Expected by Evaluation 2, end of the coding period

* **Four** endpoint classes for the API group **Official Clients** and their unit tests.

* **Four** endpoint classes for the API group **Youtube** and their unit tests.

* **One** endpoint class for the API group **Web Site** and their unit tests.

* Documentation for all the Classes built so far. Add example requests and responses for the API endpoint class with their functionality.

**Extending Fido Client**

* Helioviewer Client and test cases.

* Corresponding documentation.

* Remove the current code from the SunPy.

## Timeline

---

### Community Bonding Period [May 20 - June 12]

---

**Week 1 [May 20 - May 26]**

* Meet with mentors and request which part of the proposal needs the most work.

* Investigate and research the part of the project which requires the most work.

* Ask mentors and understand the structure of Wrapper.

**Week 2 [May 27 - June 2]**

* Study **mock requests** and get comfortable with testing.

* Finalize the architecture of the **wrapper** and present them to the mentors.

**Week 3 [June 3 - June 12]**

* Ask for implementation details on **Fido** Client, and research them.

* Present a final architecture of Fido Client to the mentors and apply required changes to them.

* Research and plan about missing details, show my **Kanban Board** for the summer to my mentors and ask for their advice.

* Getting familiar with the new python package setup and ready to start the new adventure.

---

### First Coding Period [June 13 - July 25]

---

**Week 4 and week 5 [June 13 - June 26]**

* Implement the HTTP **parent class**.

* Subclass for **JPEG 2000** API group endpoints (4 endpoint classes).

* Write tests and documentation for the same.

**Week 6 and Week 7 [June 27 -July 10]**

* Complete the **getStatus** endpoint subclass of the **JPEG 2000** API group.

* Implement subclass for **Movies** API group endpoints (3 endpoint classes).

* Write tests and documentation for the same.

**Week 8 and Week 9 [July 11 - July 24]**

* Implement the **downloadMovie,** **playMovie** endpoint subclass of the **Movies** API group.

* Implement the **takeScreenshot** and **downloadScreenshot** endpoint subclass of the **Screenshots** API group endpoints.

* Write tests and documentation for the same.

---

### First evaluation date [July 25]

---

### Second Coding Period [July 25 - September 4]

---

**Week 10 and Week 11 [July 26 - August 8]**

* Implement the **getClosestImage**, **getDataSources, getTile, and shortenURL** endpoint subclass of the **Official Clients** API group.

* Write tests and documentation for the same.

**Week 12 and Week 13 [August 9 - August 22]**

* Complete the **youtube** API group endpoint subclass with tests and documentation.

**Week 14 [August 23 - August 29]**

* Implement the **getNewsFeed** API group endpoint subclass with tests and documentation.

* Implement the Helioviewer **genericClient** for the Fido client.

**Week 15 [August 30 - September 4]**

* Complete the Implementation of the Fido client.

* Write testing for the Fido client.

* Write documentation of the Fido client.

---

### Coding period ends

---

## About me

This is my first time participating in GSoC. I am eligible to participate and receive payment from Google. I am not applying to any other organizations. I don't have any other commitments in the summer. So, I have decided to dedicate 4 - 6 hrs per day.

I read a few books by Stephen Hawking and got fascinated by physics and astronomy. Searching organizations for Google summer of code I came to know that there are astronomy-based open source organizations. When I started open source, I read a blog about [How to be an open source gardener](https://steveklabnik.com/writing/how-to-be-an-open-source-gardener) and I am inspired by that. For a long time, I wish to do something like this for an open source organization and I think this is my best opportunity. So, after GSoC, I planned to start preparing for my master’s entrance exam and along with that, I will become an open source gardener at Sunpy or openAstronomy, cleaning up issues like weeds in the garden and helping community members. The new package will be a project that I wrote and I wish to keep supporting the maintainers of the package with my continuous contributions.

## Coding experience

I am skilled in **Python** and **C** languages with the knowledge of Data Structures and Algorithms both theoretically and practically. I also love backend programming.

I was fortunate to be mentored by **[Audrey Roy Greenfeld](https://github.com/audreyfeldroy)** and **[Daniel Roy Greenfeld](https://github.com/pydanny)** authors of the famous Django book “**[Two Scoops of Django](https://www.google.com/search?q=Two+scoops+of+Django&sxsrf=APq-WBvKW8B4l2afu--YOo8nc2AzxXKS8A%3A1649480706696&ei=AhRRYtXyKaKMseMPr9-vyAw&ved=0ahUKEwjV-9e8mob3AhUiRmwGHa_vC8kQ4dUDCA4&uact=5&oq=Two+scoops+of+Django&gs_lcp=Cgdnd3Mtd2l6EAMyBAgjECcyBAgAEEMyBQgAEIAEMgUIABCABDIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgAQyBQgAEIAEMggILhCABBDUAjoHCAAQRxCwAzoHCAAQsAMQQzoMCC4QyAMQsAMQQxgBOgcIIxCwAhAnOgQIABANOgcILhDUAhANSgQIQRgASgQIRhgAUJIHWIEKYOgZaAFwAXgAgAF-iAH7AZIBAzAuMpgBAKABAcgBDcABAdoBBAgBGAg&sclient=gws-wiz)**” and creators of project **[Cookiecutter](https://github.com/cookiecutter/cookiecutter/)**. Under their guidance, I worked as an intern on a project titled **BookBuilder** to automate the process of book building using python ([gist](https://gist.github.com/akash5100/fa8c66edf9dabf565e159c87490e70ae)) for their book called “**[A Wedge of Django](https://www.feldroy.com/books/a-wedge-of-django)**” (a newer version yet to be released), This project was aimed at taking one or more google document files, pulling them down to a server, and rendering them out as PDF and ePub. Under them, I have also worked on a project titled **Voice-helper** which was a minimum viable product that uses artificial intelligence to improve voice recognition software integration with Discord and/or other desktop apps ([demo](https://drive.google.com/file/d/1U0tO_O0IyE6qmrWXn-mFFnfNsooMcXMr/view)).

[Here is a certificate for the above mentioned activities.](https://drive.google.com/file/d/1YN8NuCM4yi4dDCnYiH1FJZS-DYeMQiNJ/view?usp=sharing)

## Open source experience

* For an NGO called **[MHF](https://www.margaritahumanitarian.org/)**, I started a python project called **[helpmespeak](https://github.com/margaritahumanitarian/helpmespeak)** which later became the backend of the **Voice-helper** project mentioned above.

* My other contributions to open source are at [Learning Equality/Kolibri](https://github.com/learningequality/kolibri/pulls?q=is%3Apr+is%3Aclosed+author%3Aakash5100), [MHF/FingerTips](https://github.com/margaritahumanitarian/FingerTips/pulls?q=is%3Apr+is%3Aclosed+author%3Aakash5100), and [Greenstand/tree tracker-web-map-client](https://github.com/Greenstand/treetracker-web-map-client/pulls?q=is%3Apr+is%3Aclosed+author%3Aakash5100).

## What contributions have I made to Sunpy so far?

* In PR [#5980](https://github.com/sunpy/sunpy/pull/5980) (coding) and [#6024](https://github.com/sunpy/sunpy/pull/6024) (updating docs), I wrote a test case for **timeseriesbase** so that you can pass in a numpy array.

* PR [#5961](https://github.com/sunpy/sunpy/pull/5961), Adds an example to show "how to reproject a map to a map projection with a custom origin".

My plans after submitting the proposal **[April 19 - May 19]**

* Keep in touch with the mentors, I decided to work on these issues

* [Test for memory mapping](https://github.com/sunpy/sunpy/issues/1774). (sunpy/sunpy)

* [Upstream longitude equality helper to astropy](https://github.com/sunpy/sunpy/issues/3821). (sunpy/sunpy)

* [Content overlaps side nav bar as screen width decreases](https://github.com/sunpy/sunpy-sphinx-theme/issues/136). (sunpy/sunpy-sphinx-theme)

* Along with solving the above-mentioned issues, I will continue to study unittest and pytest, research the mock request, and learn more about **decorators** in Python.

## Why This Project?

The theme of this project attracted me due to my previous attachments with similar ventures which enables me to understand the project better and be comfortable with the workings and requirements.