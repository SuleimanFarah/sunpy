# Adding Support for Resampling Data with NDCube  

**Organization:** OpenAstronomy  
**Sub-organization**: sunpy  

**Mentors**:  
1. Dan Ryan ([@DanRyanIrish](https://github.com/DanRyanIrish))  
2. Stuart Mumford ([@Cadair](https://www.github.com/cadair/))  

## Personal Details
**Adwait Bhope**  
[adwaitbhope@gmail.com](mailto:adwaitbhope@gmail.com)  

GitHub: [@adwaitbhope](https://www.github.com/adwaitbhope/)  
Matrix: @adwaitbhope  

Final year CS undergrad at **Univerity of Pune**(SPPU), admitted to **Pune Vidyarthi Griha's College of Engineering and Technology**, India.  

## Google Summer of Code

* **Have you participated in GSoC previously?**  
No, this is the first time I'm applying to an organization.  

* **Are you also applying to other projects?**  
Yes, I plan to apply to another one of sunpy’s projects: [Update sunraster to ndcube 2.0](https://openastronomy.org/gsoc/gsoc2021/#/projects?project=update_sunraster_to_ndcube_2.0) under OpenAstronomy.

* **Are you eligible to receive payments from Google?**  
Yes, I’m eligible.

* **How much time do you plan to invest in the project before, during, and after the Summer of Code?**  
I will be able to satisfy the official GSoC guideline of 18 hours per week throughout. I expect my college exams to be over before the coding period begins on 7th June. I’m currently interning at a company as a Software Engineer, but I believe it won’t hamper my commitment to GSoC.  
After the Summer of Code, I’ll keep contributing with code as well as other things like docs. The community is very active and new work is always available.  


## Programming Experience

Being in my final year, I’ve accumulated a fair amount of programming experience until now. I have worked on multiple projects across different domains like mobile app development, backend web development, and machine learning.  

I love participating in hackathons and developing solutions. Our team recently won [Smart India Hackathon](https://www.sih.gov.in/) (India’s biggest hackathon), where I was the team leader. We worked on a Machine Learning based solution for calculating a safe speed for a vehicle to drive at, based on its surroundings. We’re currently writing a paper on our approach and hope to get it published. We also went on to win the [ASEAN India International Hackathon](https://india-asean.mic.gov.in/) a few weeks ago.  

My experience with Python started with learning backend web development using Django. I’ve gotten proficient with it now. I’m currently interning at a company where I’m the primary person tasked with writing REST APIs with Python. A few months ago, we also developed the initial stage of a mutual fund portfolio management portal, whose development was sponsored by Principal Global Services, a Fortune 500 FinTech company. The entire backend for this application was written using Python.  

I have some more Python experience related to machine learning, much of it from my previous internship at Resolute AI in Bangalore, India. This mostly entailed work with libraries like TensorFlow, Keras, numpy, pandas, etc. I worked on developing a model that tracked PPE kit compliance for people working in the healthcare industry.  

I’m involved in the clubs at my campus like the [Google Developer Student Club](https://dsc.community.dev/pune-vidyarthi-grihas-college-of-engineering-and-technology-pune/) as the Technical Head. We organize and conduct technical workshops for fellow juniors. Through this, I’ve had the opportunity to reach hundreds of students and help them through their journey.  

Some of my Python projects:  
1. A desktop GUI app for Object Recognition  
[https://github.com/adwaitbhope/object_recognition_poc](https://github.com/adwaitbhope/object_recognition_poc)  

2. A client-side app for running Object Detection  
[https://github.com/adwaitbhope/sih-client-side-object-detection](https://github.com/adwaitbhope/sih-client-side-object-detection)  

3. REST backend for a mobile app  
[https://github.com/adwaitbhope/denizen-backend](https://github.com/adwaitbhope/denizen-backend)  

Here is a summary of some relevant subjects I studied at college:  
1. Engineering Mathematics (I, II and III), Engineering Physics  
2. Data Structures & Algorithms, Object-Oriented Programming  
3. Computer Graphics, Engineering Graphics  
4. Design & Analysis of Algorithms, Theory of Computation  
5. Software Modelling & Design, Software Testing & Quality Assurance  

These courses have strengthened my grasp of core computer science concepts and programming logic. Also, I believe that some of these courses like Mathematics, Physics, and Graphics will specifically help me with the science side of things as I contribute to this organization.  

Also, here is a link to my [resume](https://drive.google.com/file/d/1iiVsDDRansZqcWlrrfbqGImdOeW3-JNF/view?usp=sharing) for reference.  

## Contributions to sunpy

1. (Merged) Fixed a bug in DataManager  
[https://github.com/sunpy/sunpy/pull/5089](https://github.com/sunpy/sunpy/pull/5089)  

2. Added namespaces for downloaded files  
[https://github.com/sunpy/sunpy/pull/5111](https://github.com/sunpy/sunpy/pull/5111)  

3. (Misc.) Invalid link on the GSoC webpage of this project  
[https://github.com/OpenAstronomy/openastronomy.github.io/issues/285](https://github.com/OpenAstronomy/openastronomy.github.io/issues/285)  

4. (Misc.) Fixed a typo in a function doc reference  
[https://github.com/sunpy/ndcube/pull/419](https://github.com/sunpy/ndcube/pull/419)  


## Why This Project

I’m currently working on my final year academic project with our mentor from Persistent Systems Ltd., India. We are collecting spectral data of galaxies in the optical region from the Sloan Digital Sky Survey, and working on setting up a Machine Learning pipeline that can predict the age of the galaxy. In fact, we are using astropy, one of the sub-organizations here, to handle the FITS files.  

I have always been excited about stars, galaxies, and other astronomical entities, and keep reading about them. All of the above project exposure piqued my interest, and I was enthralled when I discovered OpenAstronomy as one of the organizations.  

In our project, we had to resample all the spectral data on the same grid so that it can be fed to the ML algorithms. We used the Python package [`pysynphot`](https://github.com/spacetelescope/pysynphot) to achieve this. Upon seeing a similar project under OpenAstronomy, it was a no-brainer for me. I understand why this functionality would be helpful since I had to experience it myself firsthand. I find it exciting that this will make it convenient for scientific researchers to tinker with their data.  

* **Why are you suited to work on this project?**  
As stated above, I understand the motive behind this project, I have good experience with Python and programming in general, and I also have some exposure to Astronomy. I have made contributions to sunpy, and I feel comfortable with the math that goes behind these WCS transformations. I believe this makes me a strong candidate for the project.  


## Existing Work

There are other packages (like `pysynphot` that I mentioned above) that can resample data, but Astropy’s `reproject` is probably the most helpful one for `ndcube`. It will accept an `NDCube` along with a target WCS and will project the data on it accordingly. This will make it very easy for `ndcube` to support resampling. The challenge to construct a WCS object with the necessary modifications remains, as reproject will not help with that.

Currently, there are multiple algorithms supported by `reproject` like Interpolation, HEALPIX Projection, DeForest Adaptive Resampling, etc. For Interpolation, it supports "nearest-neighbour", "bilinear", "biquadratic", and "bicubic".  


## What I've Explored

I studied a bit about different coordinate systems and WCS from this article that [@nabobalis](https://www.github.com/nabobalis) shared with me. It provided me with a clearer understanding of how these transformations work. I have put some code together, trying to resample an `NDCube` using bicubic interpolation. I upscaled the wavelength axis by a factor of 10, manually creating a new WCS that supported this transformation. For this, I modified the `CDELT` parameter that corresponds to pixel width (for real-world values). I have also plotted a slice of the cube to compare the result.  

The code and the graph can be found at this gist: [https://gist.github.com/adwaitbhope/d056fd5a5a8eb5781a9ccc5615a644f0](https://gist.github.com/adwaitbhope/d056fd5a5a8eb5781a9ccc5615a644f0).  

* **How do you plan to implement the project?**  
First, I plan to closely study different use cases for resampling. It is key to identify the necessary type of WCS transformations. I will be studying more about this to figure out how to create a new WCS that supports the resampled data.  
My first step would be to get an API up and running, that solves a basic use case, something like a Minimum Viable Product. This can involve modifying `NDCube`’s other parameters like `extra_coords`. The API can then be extended to more complicated use cases.  
There are some more things to plan before starting with the implementation, such as deciding whether to support only integer values as the scaling factor. This will largely depend on how we are able to use `reproject` with `ndcube`.  

* **Does the project include API changes?**  
Yes, this project will introduce a new API. In the original [issue](https://github.com/sunpy/ndcube/issues/155) that referenced this topic, @DanRyanIrish (one of the mentors) has ideated a possible API. Under the hood, ndcube will construct a new WCS object and resample the data along with other parameters like `extra_coords`. This will make a powerful API that will let users manipulate all their data with a single function call.  
However, I don’t suppose that there will be any breaking change to the existing API.  

* **Will you need additional software package requirements?**  
Yes, the primary requirement will be Astropy’s `reproject`, which is released as a separate package [here](https://github.com/astropy/reproject). This package implements the necessary mathematical algorithms we can use for resampling, thereby reducing effort and redundancy. Its API is easy to use with NDCube, as demonstrated in the gist that I have linked above.  


## Timeline

|Period    |Plan                             |Date    |
|----------|---------------------------------|--------|
|Community Bonding Period|<ul><li>I'll utilize this time to keep contributing to sunpy and ndcube in other issues or PRs. This will help me get familiar with the community and understand how things work.<li>If possible, I'll try to get a headstart on understanding the math behind WCS transformations.</ul>|17^th May - 7th June|

|1       |<ul><li>Study ndcube and WCS transformations<li>Study how `astropy.wcs` is coupled with `NDCube`</ul>|22 June |
|        |ons                                       
