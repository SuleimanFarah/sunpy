# Project: Solar Weather Forecasting using Linear Algebra

## Summary of proposal

### What excites me about this project? Why did I choose it?

Just reading the title of the project was enough for me.
A desire to work on problems like this is what got me into computer science and machine learning in the first place. To be able to work on problems in various fields of science and understand them in a way which wasn't even possible a few decades ago.
There's tremendous potential for applying data-driven solutions to solar physics and I wish to do my part in it.
I am two months short of having a full year's worth of professional experience in machine learning and am well acquainted with SunPy. This gives me confidence that I would be able to finish this project successfully and on time.

### Challenges with the project

#### 1) Search Events Object

- The first challenge with creating a Search Events Object would be matching the Active Regions in the Sunspotter data set with the Active Regions in various Solar Data catalogues, like HEK and Helio. We only need to worry about matching Sunspotter ARs to any catalogue that has NOAA AR numbers. Once we have the NOAA AR numbers for the ARs, we can access various other catalogues easily.

- Matching catalogues (joining tables) when the fields are not exactly with the same value (i.e., allowing to specify what counts as a match) would be the next task. For example, for any given observation date, the HEK data for the ARs usually does not match exactly with the Sunspotter data. This is made evident by the lack of proper overlap in the [various full disk plots that I have made in this notebook](https://github.com/Raahul-Singh/SolarWeatherForecasting/blob/master/Data%20Preprocessing.ipynb).

- This matching of various ARs across Sunspotter data and the HEK will be done by first identifying common fields and then to match the rows, the algorithm described in the [Tool for OPerations on Catalogues And Tables (TOPCAT)](http://www.star.bris.ac.uk/~mbt/topcat/sun253/pairMatch.html) [which is explained in the TOPCAT match algorithm reference](http://www.star.bris.ac.uk/~mbt/topcat/sun253/matchAlgorithm.html) will be used.

- Next, we extend the `hek2vso` client and work towards better integrating it with FIDO. The idea is to create a single interface for getting the metadata and the various types of files associated with an observation. The long term idea is to get a unified interface where we can get data and meta-information about any event from a given observation date. One of the outcomes would be, the user being able to get event-specific information from HEK or other sources and use them in conjunction with the downloaded HMI and AIA data [as is being done in the SunPy Gallery example on using AIA and HMI data together.](https://docs.sunpy.org/en/stable/generated/gallery/sunpy_other_packages/reprojection_align_aia_hmi.html#sphx-glr-generated-gallery-sunpy-other-packages-reprojection-align-aia-hmi-py)

Another aspect of this Search Events Object would be a dictionary that would map names between different catalogues so that the same `features.attribute` can be used on different catalogue searches (e.g., a flare is translated as FL in HEK and as the different flare tables on HELIO).
The object would be made subscript-able to facilitate easy access.

#### 2 ) Data Preprocessing

For the forecasting, the biggest challenge would be the data preprocessing and making it ready to be fed into the learning pipeline.
For any machine learning project, the preprocessing plays a major role in the ability of the learning algorithm to learn from the data set.
In the Sunspotter data set, there is a significant bias. The following is a list of the percentage of positive samples per class (not mutually exclusive):

| Forecasting Parameter  | Percentage of Positive samples         |
| ---                    | ---                                    |
|No-flare                |24.00%                                  |
|C1flr12hr               |11.37%                                  |
|C1flr24hr               |14.40%                                  |
|C5flr12hr               | 8.12%                                  |
|C5flr24hr               | 8.97%                                  |
|M1flr12hr               | 7.22%                                  |
|M1flr24hr               | 7.55%                                  |
|M5flr12hr               | 7.56%                                  |
|M5flr24hr               | 7.66%                                  |

- For dealing with this problem, I propose using a method similar to the one described in the paper `Predicting Solar Flares Using a Novel Deep Convolutional Neural Network` [Xuebao Li, Yanfang Zheng, et al 2020](https://iopscience.iop.org/article/10.3847/1538-4357/ab6d04/pdf).
- For the sake of conciseness, the main ideas are:
  - It is pretty obvious that the number of M-level magnetogram samples is far less than that of No-flare/C-level magnetogram samples, which is consistent with the fact most ARs do not yield major flares in the period of any given 24 hr. This would result in a serious class-imbalance issue, which is a major problem in the field of machine learning.
  - To deal with this, first ARs are categorized into three levels (i.e., No-flare, C, M). “Level = M” indicates that an AR yields at least one M-level flare; “Level = C” indicates that an AR yields at least one C-level flare but no M-level flares “Level = No-flare” indicates that an AR only yields microflares (weaker than C1.0 flares).
  - We shall construct about 10 separate Cross-Validation data sets by the method of shuffle and split Cross-Validation based on AR segregation (AR segregation is, to balance out the classes, I will make sure that the ten Cross-validation splits that I make will have an almost equal number of C, M and No flare producing ARs.). First, we randomly shuffle the AR numbers in different levels of No-flare/C/M and then split the AR numbers at a ratio of around 80%:20% which would correspond to training and testing data respectively.
  - The advantage of this method is that in each of the 10 data sets, not only do the samples in the testing data set not overlap with those in the training data set but also the ARs in the testing data set are disjoint from those in the training data set. We train and evaluate our model on these 10 separate training and testing data sets. We adopt the loss function calculated from the weighted cross-entropy loss.

I'll be modifying the code from the [repository mentioned in the original paper](https://github.com/FlarePrediction/Repository) to produce the 10 Cross-Validation splits. These modifications would mostly be for making the preprocessing step into a SunPy compliant class, which can be merged into the main repository.

##### Further

In any data-driven problem, the challenge is to get the best possible performance with minimum resource consumption. In addition to this, the decision making (for example, classification) done by the machine learning algorithm should also be explainable.
I, therefore, propose to use an Autoencoder to distil the information in the images and use this encoding in further forecasting algorithms.

- Autoencoder is an unsupervised artificial neural network that learns how to efficiently compress and encode data then learns how to reconstruct the data back from the reduced encoded representation to a representation that is as close to the original input as possible. Autoencoder, by design, reduces data dimensions by learning how to ignore the noise in the data.

    Here are some awesome resources on Autoencoders:
    1. [An introduction to different flavours of Autoencoders](https://www.jeremyjordan.me/autoencoders/)
    2. [What Regularized Auto-Encoders Learn from the Data Generating Distribution](https://arxiv.org/abs/1211.4246)

- In addition to being used with a neural network, this lower-dimensional encoding can also be fed to simpler Machine Learning models. In my experience, the complexity and the representation of data plays a very important role in any learning task. If with simpler models, we can get results comparable to computationally heavy black box algorithms like neural networks, we should prefer them as they are easier to debug and explain.

The reasons why I would prefer reducing the dimensionality of knowledge using Autoencoders over creating more data by using algorithms like GANs to solve the class imbalance problem is:

- There would be no way to verify the effect of the AR metadata on the final classification. If we mix real observations with artificially produced data, we would still only have the observed metadata (from sources like HEK) for the real data. This would restrict us to simply using images for our forecasting.
- We would only produce more image data. This restricts us to image only algorithms, as the data set would remain imbalanced for all other algorithms.
- GANs are amongst the most computationally expensive algorithms and are not always stable enough to get diverse data production. There are [various other problems like mode collapse, etc.](https://medium.com/@jonathan_hui/gan-why-it-is-so-hard-to-train-generative-advisory-networks-819a86b3750b) which may cause major problems, quite unrelated to our main task of flare forecasting.

#### 3) Training Time and Resources

Different algorithms will consume a different amount of resources in terms of memory and training time.
I shall be running all the algorithms locally on my machine equipped with an NVIDIA 1050Ti GPU.
If need be, I'll migrate to Google Colab.

#### 4) Testing and Integration

All the code written in this project shall be rigorously tested, following all of SunPy's testing standards and other general good practices.
For the machine learning model, I shall be following [industry standards for testing and debugging](https://developers.google.com/machine-learning/testing-debugging).
I shall also take inspiration from popular blogs with [some nice code references for unit testing and logging](https://towardsdatascience.com/unit-testing-and-logging-for-data-science-d7fb8fd5d217).

## Implementation

I plan on implementing various algorithms in order of increasing model complexity.
These models will map various inputs to the following forecast parameters.

| Forecast Parameter     | Description                                                            |
| ---                    | ---                                                                    |
| `c1flr12hr`            | at least one C1.0 or greater flare within 12 hr after the observation. |
| `c1flr24hr`            | at least one C1.0 or greater flare within 24 hr after the observation. |
| `c5flr12hr`            | at least one C5.0 or greater flare within 12 hr after the observation. |
| `c5flr24hr`            | at least one C5.0 or greater flare within 24 hr after the observation. |
| `m1flr12hr`            | at least one M1.0 or greater flare within 12 hr after the observation. |
| `m1flr24hr`            | at least one M1.0 or greater flare within 24 hr after the observation. |
| `m5flr12hr`            | at least one M5.0 or greater flare within 12 hr after the observation. |
| `m5flr24hr`            | at least one M5.0 or greater flare within 24 hr after the observation. |

The accuracy of the model in predicting these parameters would be its accuracy in forecasting the solar weather.

## Deliverables

This project will have the following deliverables:

- A fully integrated Search Events Object, supported with rigorous testing. This will have all the features as described above, and more which will be decided on further consultation with the mentors during the community bonding period.

- Multiple notebooks for the SunPy Examples gallery that highlight each algorithm implemented along with an interpretation of the results.

- The best performing trained model, properly documented and tested, along with instructions on how to use it.
  This will be made inheriting a separate `ML Algorithm` abstract object so that more machine learning related work can be easily integrated in the future.

- A separate `Data Preprocessing` Object that will be used in this project and could be extended for future ML work.

- Instructions on how to retrain the model if necessary.

### Timeline

___

#### Community Bonding Period

___

- The basic layout for implementing the Search Events Object shall be designed at this time. I would take into account the work done in the FIDO project and work towards implementing the Search Events Object as per our requirement. The efforts on this project will also complement the FIDO metadata project with tools and uses cases.

- I shall spend this time exploring the data set, discussing possible modifications to the architectures and hyperparameter tuning with my mentors, and continuing my contributions to SunPy.

- I also plan on familiarising myself with the SMART algorithm and its outputs from the ground up using the [IDL implementation](https://github.com/TCDSolar/SMART). This will help me understand the various parameters and their generation.

- Since Google has provided an extra week this year for community bonding, I shall use this time to recreate the ELO rating in python and compare it with other ratings (e.g., [Glicko's](https://en.wikipedia.org/wiki/Glicko_rating_system),
  [Bradley-Terry's](https://en.wikipedia.org/wiki/Bradley%E2%80%93Terry_model)).

  [Glicko](https://github.com/sublee/glicko) is an implementation I found on GitHub that I can fork and use according to our data set.

___

#### Coding Period Begins

___

#### Week 1

- As per the official timeline mentioned, this week will be spent visualising different types of data, the magnetograms, univariate, multivariate analysis of the SMART detection properties concerning both flare generation and the ELO complexity score. I shall be making all the plots in multiple notebooks for the SunPy examples gallery.

- The statistical analysis of the ELO complexity score and its variation concerning with the production of flares will be analyzed. It is believed that the more complex an active region, the more likely it is to produce flares. The work done this week will help test this belief.

- Further, I would begin working on the Search Events Object as has been described above.

#### Week 2

- Having already tinkered with the data set, I have created [a few basic plotting functions and a few helper functions to query the HEK database using HEKClient](https://github.com/Raahul-Singh/SolarWeatherForecasting/blob/master/Data%20Preprocessing.ipynb) Here are a few random examples. The red squares have been plotted using the Sunspotter data and the blue rectangles have been plotted from the queried HEK data. All functions are in the above-mentioned link. The red squares have been overplotted on purpose as the Sunspotter data set lacks the information about the shape of the bounding boxes.

![Rectangled AR example 1](https://i.imgur.com/C36St72.png)
![Rectangled AR example 2](https://i.imgur.com/HglNyXX.png)

- This week shall be used to complete most of the Search Events Object. Following this, I wish to give `testing` at least four to five days to make it completely merge ready.

#### Week 3

- Having completed all the previous tasks, we are now ready to tackle the forecasting problem head-on. The third week shall be used in completing the data preprocessing as described in the previous section. This shall take the first half of the third week.

- Next, I will implement various models to map the complexity scores directly to the flare observations. We shall not be considering the images as of yet.

- These models shall serve as benchmarks for comparing against deep learning models.

- All of the following will be implemented using Scikit-Learn and other ML libraries:

  - Random Forest
  - SVM
  - XGBoost

- These are all standard models. This is the part where I experiment with different linear algebra models mentioned in the problem statement. I do not expect the best result from any of them but they will help in determining the next course of action we take as we apply deep learning methods in the later weeks.

- If need be, other ratings (e.g., [Glicko's](https://en.wikipedia.org/wiki/Glicko_rating_system),
  [Bradley-Terry's](https://en.wikipedia.org/wiki/Bradley%E2%80%93Terry_model)) will be used and the predictions on them will be compared against the ELO trained model predictions.

- All the implementations will be accompanied by an analysis blog post on the nature of the algorithm, an analysis of the results and possible deductions about the performance metrics.

#### Week 4

- This will be a buffer week to ensure :

* The Search Events Object is implemented, fully documented and well tested.
- We have all the Exploratory Data analysis plots for SunPy Examples Gallery.
- The basic Machine Learning model is up and running.

___

#### Phase 1 Evaluation

___

#### Week 5

- Week 5 shall be used to reimplement the best performing algorithm implemented during week 3 and 4, but this time taking into account the SMART properties along with the ELO complexity score.

- The results obtained here will likely be less accurate taking into account the increase in the input complexity.

- To combat this, Dimensionality Reduction algorithms like `Principal Component Analysis` shall be used to find out the most important combination of features.

- The best performing algorithm shall be trained and tested on this reduced data set. It is expected to give a boost in the prediction accuracy.

#### Week 6 -  Week 7

- At this point, we move into the domain of Deep Learning.

- For week 6, I shall be implementing a Deep Convolution Neural Network based on the paper, <br/>
 `Deep Learning-Based Solar Flare Forecasting Model. I. Results for Line-of-sight Magnetograms` [Huang et al.](https://iopscience.iop.org/article/10.3847/1538-4357/aaae00/pdf)

- We begin using the images of the Active Regions obtained from [sunspotter](http://www.sunspotter.org) and map them to the flare observation labels.

- The reason for implementing a paper is that I get something that is relatively known to work. I can build on top of it, rather than start from scratch.

- With 210692 images, the network may take a long time to train and we will need to train again every time we tweak the hyperparameters of the network, so I am allotting two weeks for this initial network implementation.

This shall be implemented using either the PyTorch or TensorFlow2.0 libraries, which shall be decided after discussing with the mentors.

#### Week 8

- Whereas all the SMART parameters can be treated as sensor inputs, the complexity score represents more of a **belief or a confidence** parameter.

- The complexity score, when scaled to a range of [0,1] can be considered a probability score for the Active Region to produce a flare.

- For week 8, I shall be implementing the best performing implementation of the CNN from the previous weeks, with a major augmentation. I shall be multiplying the output of the biggest hidden layer with scaled ELO score corresponding to the input image. This shall give the network information about the complexity and will allow the network to train accordingly.

- Comparing the results with the un-augmented network, we shall have further evidence whether the ELO complexity score correlates to the flare production or not.

This shall be implemented using either the PyTorch or TensorFlow2.0 libraries, which shall be decided after discussing with the mentors.
___

#### Phase 2 Evaluation

___

#### Week 9 - Week 10

- Here I plan on implementing an original idea for a multichannel neural network, which would have the ability to take both the Sunspotter SMART detection values along with the corresponding images. I plan on making these different types of inputs compatible by first training an AutoEncoder network on the Active Region images to learn an effective lower-dimensional encoding for the images. This shall be concatenated and re-normalised with the processed SMART detection values and the complexity score to make the final feed-forward neural network that will learn the mapping.

- Autoencoder will be like a `Neural Network` version of SMART which when given a particular image of an AR, will characterise it with some properties. It will give us a vector of distilled information from each image, but unlike SMART, it is a black box. We will not know what the values in that vector represent.

- I shall also retrain the best performing non-Deep Learning model from previous weeks to see if we can get comparable results from less computationally taxing algorithms.

This shall be a rather unchartered territory and I will give a full two weeks to implement this.

#### Week 11 - Week 12

- The last two weeks of the project shall be used to summarise the results of all the various experiments based on the different algorithms.
- After selecting the best performing model, its performance shall be tested on SDO/HMI data.
- An extensive notebook shall be written detailing the use of the model and possible ways to tweak the hyperparameters.
- If time permits, as a side quest, I shall implement a neural network that directly maps the Active Region images with the ELO complexity rating. This shall help in automating the complexity prediction for magnetograms in the future.

#### Week 13

- The final week shall be used to add final touches to the deliverables.

___

#### Final Evaluation

___

## Personal Info

- Time zone: UTC+05:30
- GitHub handle: [Raahul-Singh](https://github.com/Raahul-Singh)
- Riot: @raahulsingh:matrix.org

### Education

- University: Indian Institute of Information Technology, Sri City
- Major: Computer Science
- Current Year: 2nd year

### Open Source background and Programming experience

- Programming Languages: Python, C++, C, Java(Basic knowledge)
- Contributions to SunPy:
  - As of writing this proposal, [I have 8 merged and 5 WIP PRs on SunPy repo.](https://github.com/sunpy/sunpy/pulls?q=is%3Apr+Raahul+Singh+is%3Aclosed)
   <br/>Some prominent ones are :
    - [Significant reducuction of the download time for the data set used in this project through the HelioViewer API.](https://github.com/sunpy/sunpy/pull/3862)
    - [Rectangle coordinate parser to support multiple ways of specifying rectangular regions of  interest.](https://github.com/sunpy/sunpy/pull/3737)
    - [Integrating parfive==1.1rc2 with SunPy.](https://github.com/sunpy/sunpy/pull/3822)
    - [Implementing Limb Darkening correction.](https://github.com/sunpy/sunpy/pull/3728)
    - [Informing user when and what coordinate information may be missing when making a map.](https://github.com/sunpy/sunpy/pull/3692)

I have opened [7 issues](https://github.com/sunpy/sunpy/issues?q=author%3ARaahul-Singh+is%3Aissue) on the SunPy repository and have a [cumulative of 25 contributions to SunPy](https://github.com/sunpy/sunpy/issues?q=author%3ARaahul-Singh+is%3Aopen)

- Contributions to other repos:
  - Parfive
    - [Adds support for passing User Agent headers and Proxies](https://github.com/Cadair/parfive/pull/32)
  - And other contributions to EinstienPy and ChiantiPy.
- I will be contributing to SunPy throughout the selection process and beyond.

## You and GSoC

### Have you participated previously in GSoC? When? Under which project?

**No**, This is my first time participating in GSoC.

### Are you also applying to other projects?

**No**, I am fully focused on this project.

### Commitments

I don't have any other internship or work during this summer and have no plans for any vacations either. <br/>
I can work full time on the project and can give ~35-40 hours per week and more if required.

### Eligibility

Yes, I am eligible to receive payments from Google.

### References and useful papers

- `Deep Learning-Based Solar Flare Forecasting Model. I. Results for Line-of-sight Magnetograms` [Huang et al.](https://iopscience.iop.org/article/10.3847/1538-4357/aaae00/pdf)

- `Solar flare prediction using advanced feature extraction, machine learning and feature selection` [Ahmed OW, Qahwaji RSR, Colak T, Higgins PA, Gallagher PTand Bloomfield DS (2013) Solar physics. 283(1): 157-175](https://bradscholars.brad.ac.uk/handle/10454/7581)

- `Predicting Solar Flares Using a Novel Deep Convolutional Neural Network` [Xuebao Li, Yanfang Zheng, et al 2020](https://iopscience.iop.org/article/10.3847/1538-4357/ab6d04/pdf)
