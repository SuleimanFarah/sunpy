# Space Weather Forecasting using Machine Learning

## Contact Information

* Name: Mina Sami Gorgi
* University: [Cairo University, Faculty of Engineering](http://eng.cu.edu.eg/en/), Egypt
* Email: minas.gorgy@gmail.com
* GitHub: [MinaSGorgy](https://github.com/MinaSGorgy)
* LinkedIn: [mina-sami](https://www.linkedin.com/in/mina-sami)
* Riot: [minasami](https://matrix.to/#/@minasami:matrix.org)

## About me

I am a senior Computer Engineering undergrad student interested in Space and Computer Vision. Accompanied by Ada -my alto saxophone named after ["Ada Lovelace"](https://en.wikipedia.org/wiki/Ada_Lovelace)- I also study music theory as a hobby. I am a sudo user -Ubuntu 18.04- and I mainly use VSCode for development basically because it's much lighter than IDEs and I already like doing my own build scripts.

## [Qualification PR](https://github.com/sunpy/sunkit-image/pull/24)

Implementing NAFE filter for enhancing fine structures in extreme ultraviolet images of the corona. Started as a mid-year-vacation side project where I intended to implement an Image Processing related research paper to develop my implementation skills in general and Python skills in specific.

## SOCIS details

I have participated previously in GSoC but not in SOCIS, more details about that in the Technical Background section.

I haven't applied to other projects. Actually, I was applying again to GSoC this year when I found this project so I switched to SOCIS and haven't even applied for any GSoC project.

I am eligible to receive payments and I plan to treat this project as a full time summer job. I would also be very happy to continue maintaining and contributing after the internship duration ends as I find SunPy a very nice community to be part of.

## Technical Background

### Google Summer of Code Student 2018 for [FFmpeg](https://www.ffmpeg.org/)

Implemented a multi-threaded [Color Constancy filter](https://summerofcode.withgoogle.com/archive/2018/projects/4807736529256448/) in C after comparing various research papers regarding low-level image statistics and machine-learning state-of-art techniques.

### PyTorch Scholarship [Challenge](https://sites.google.com/udacity.com/pytorch-scholarship-facebook/) from Facebook

* Selected as one of the 300 winners for a full 4-month Facebook scholarship to the Deep Learning [Nano-degree Program](https://www.udacity.com/course/deep-learning-nanodegree--nd101) out of 10,000 students where I am currently studying the theory and implementation of CNNs, RNNs and GANS as well as their model deployment.
* My model scored >95% accuracy during qualification phase.
* Mentored 2 other students during qualification phase which they both completed successfully.
* Developed a machine-learning-based Color Constancy [project](https://github.com/MinaSGorgy/Color-Constancy.git) for the side project fair.

### Graduation Project

A Low-price highly-accurate CNC-based 3D scanner using USB3 Vision industrial cameras and laser triangulation. We -a team of 4- possibly have a better theoretical accuracy than state-of-art papers and currently in components-purchasing phase. The project was granted funding by the ITAC for Graduation Projects criteria.

### Relevant Experience
* Led the research sub-team as part of a 22-person team developing a Scrabble AI player winning second place in a 4-teams competition.
* Built a self-moving CNC-based Chessboard with voice recognition for taking commands and an AI to play against (basically recreating Harry Potter's Chessboard from The Philosopher's stone movie but board-size and microprocessors-magic fueled). We -a team of 4- built this board from scratch: cut our own wood, drilled our own sheets and forged our own metal components. This is my second most favorite project I am proud of; the first included Assembly and music!
* Took part in [P&G](https://us.pg.com/) IT Egypt Challenge - ITECH 2019 where I was chosen as one of the 3% to solve real-life case studies of business analytics under mentor-ship & coaching from experienced P&G professionals. Afterwards, I was offered an interview based on my performance.
* Worked as a Freelance Software Engineer at [Upwork](https://upwork.com/) where I developed:
  * A lightweight cross-platform multi-threaded client-server app written in C from scratch along with CMake for building.
  * A piano-tiles styled game to run on GNU/Linux systems in terminal written in C/C++ along with CMake for building.
  * A real-time scoreboard Flutter mobile app with Firebase integration.
* Completed [Hacktoberfest Challenge](https://hacktoberfest.digitalocean.com/) 2018.

### Extracurricular Activities

* [**ICPC**](https://icpc.baylor.edu) Administrative Coach at The 2018 Egyptian Collegiate Programming Contest
* [**K Vector Foundation**](http://kvectorfoundation.com/) Head of Android Development Committee leading a team of 3 moderators teaching Android development to participants with almost no programming experience.
* **Model of American Congress** Delegate at Homeland Security and Governmental Affairs Committee debating various controversial topics in a multi-cultured environment

## Motivation

While I do believe I posses all the skills required by the project whether a strong Image Processing or Machine Learning background, resourcefulness or research skills, what makes me the best fit is that I am driven by my passion for learning, researching and challenging myself as a partially-color blind invading the field of Computer Vision. Whether developing the Color Constancy filter as my self-proposed project, or competing within 10,000 students for the Facebook-funded Deep Learning challenge. I believe that I can and I will deliver the best possible.

## Plan

From my point of view, the project mainly consists of 2 main parts: the first is producing an accurate model to help forecast the solar flares and the second is investigating assumptions and visualizing insights regarding the causes of these solar flares while also keeping the door open for new ideas.

Accordingly, I have set the plan as follows:

___
#### Community Bonding Period (18/5)
___

I will be taking my finals from 19/5 till 2/6 so this period will mainly include discussing contact methods, results reporting and any advanced instructions and goals regarding the project.

___
#### Coding Period Begins (3/6)
___

#### Month 1

The aim of the first month is to produce a basic fully-developed pipeline starting from fetching the data till model deployment, to act as a solid ground when later trying new models/ideas or validating assumptions:
* **Week 1**
  * Explore data
  * Discuss the pipeline development details: API design and integration with SunPy

* **Week 2**
  * Develop pipeline structure
  * Implement tests and sanity checks since these are the metrics for any model

* **Week 3**
  * Develop Fetch module
  * Improve parts of SunPy relevant to project scope(can be extended according to scope and this extension is supported by the sprints mentioned in month 3)

* **Week 4**
  * Develop and deploy first agreed-upon model. Suggestion for model: a transfer-learning model like VGG16 or so as it's fairly easy and accurate for our purpose(as above, can also be extended according to chosen model if needed)

By the end of first month there should be at least two pull requests: one for parts improved and one for newly added modules.

### Month 2

* **Week 1 - Week 2**
  * Focus on visualization and develop corresponding module
  * Start validating assumptions

* **Week 3 - Week 4**
  * Develop an advanced model(like RNNs) after comparing research papers and current state-of-art technique
  * Compare to previous model
  * Visualize corresponding results and assumptions

Two pull requests should be opened this month, one for visualization module and one for newly added model.

### Month 3

By now we should have a fully-developed pipeline that fetches, trains upon, predicts and visualize the data. We also should have 2 models, validation to assumptions and possibly new assumptions. The third month should properly be planned for near the end of month 2 based on the results and final status. Nevertheless, a basic schedule would be dividing the months into a maximum of 3 sprints each of about 10 days followed by a pull request, either trying new models/methods and visualizing them or completing any new goals set during last 2 months.

As mentioned, testing is implemented upfront. Documentation/gallery examples are included in each pull request.
