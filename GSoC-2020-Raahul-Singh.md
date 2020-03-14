# Project: Solar Weather Forecasting using Linear Algebra
## Summary of proposal


### What excites me about this project? Why did I choose it?
Just reading the title of the project was enough for me.
A desire to work on problems like this is what got me into computer science and machine learning in the first place. To be able to work on problems in various fields of science and understand them in a way which wasn't even possible a few decades ago.
There is a tremendous potential for applying data-driven solutions to solar physics and I wish to do my part in it.
I am a few months short of having a full year's worth of professional experience in machine learning and am well acquainted with SunPy. This gives me confidence that I would be able to finish this project successfully and on time.

### Challenges with the project

#### Data Preprocessing

The biggest challenge would be the data preprocessing and making it ready to be fed into the learning pipeline.
For any Machine Learning project, the preprocessing plays a major role in the ability of the learning algorithm to learn from the dataset.
In the Sunspotter dataset, there is a significant bias. The following is a list of the percentage of positive sample per class (not mutually exclusive):

| Forcasting Parameter | Percentage of Positive samples |
| ---                                | ---                                                |
|No-flare                |24.00%                                  |
|C1flr12hr               |11.37%                                  |
|C1flr24hr               |14.40%                                        |
|C5flr12hr               | 8.12%                                  |
|C5flr24hr               | 8.97%                                  |
|M1flr12hr               | 7.22%                                  |
|M1flr24hr               | 7.55%                                  |
|M5flr12hr               | 7.56%                                  |
|M5flr24hr               | 7.66%                                  |

* For dealing with this problem, I propose using a method similar to the one described in the paper `Predicting Solar Flares Using a Novel Deep Convolutional Neural Network` [Xuebao Li, Yanfang Zheng, et al 2020](https://iopscience.iop.org/article/10.3847/1538-4357/ab6d04/pdf).
* For the sake of conciseness, the main ideas are:               
    * It is pretty obvious that the number of M-level magnetogram samples is far less than that of No-flare/C-level magnetogram samples, which is consistent with the fact most ARs do not yield major flares in the period of any given 24 hr. This would result in a serious class-imbalance issue, which is a major problem in the field of machine learning.
    * To deal with this, first ARs are categorized into three levels (i.e., No-flare, C, M). “Level = M” indicates that an AR yields at least one M-level flare; “Level = C” indicates that an AR yields at least one C-level flare but no M-level flares “Level = No-flare” indicates that an AR only yields microflares (weaker than C1.0 flares).
    * We shall construct about 10 separate CV data sets by the method of shuffle and split CV based on AR segregation. First, we randomly shuffle the AR numbers in different levels of No-flare/C/M and then split the AR numbers at a ratio of around 80%:20% which would correspond to training and testing data respectively.
    * We employ undersampling and image augmentation schemes to alleviate the issue of class imbalance. On the one hand, we undersample the data set by randomly choosing No-flare/C-level samples with around 2 samples per 10 samples. One the other hand, we adopt image augmentation schemes to artificially increase the number of M-level samples by rotating and reflecting images, which makes the model invariant to the rotation and reflection in pixel values.
    * The advantage of this method is that in each of the 10 data sets, not only do the samples in the testing data set not overlap with those in the training data set but also the ARs in the testing data set are disjoint from those in the training data set. We train and evaluate our model on these 10 separate training and testing data sets. We adopt the loss function calculated from the weighted cross-entropy loss.

* I’ll be modifying the code from the [repository mentioned in the original paper](https://github.com/FlarePrediction/Repository) to produce the 10 CV splits.

#### Training Time and Resources
Different algorithms will consume a different amount of resources in terms of memory and training time.
I shall be running all the algorithms locally on my machine equipped with an NVIDIA 1050Ti GPU.
If need be, I’ll migrate to Google Colab.

## Implementation
I plan on implementing various algorithms in order of increasing model complexity.
These models will map various inputs to the following forecast parameters.


| Forecast Parameter     | Description                                                                                         |
| ---                       | ---                                                                                                |
| `c1flr12hr`                 | at least one C1.0 or greater flare within 12 hr after the observation. |
| `c1flr24hr`         | at least one C1.0 or greater flare within 24 hr after the observation. |
| `c5flr12hr`         | at least one C5.0 or greater flare within 12 hr after the observation. |
| `c5flr24hr`         | at least one C5.0 or greater flare within 24 hr after the observation. |
| `m1flr12hr`         | at least one M1.0 or greater flare within 12 hr after the observation. |
| `m1flr24hr`         | at least one M1.0 or greater flare within 24 hr after the observation. |
| `m5flr12hr`         | at least one M5.0 or greater flare within 12 hr after the observation. |
| `m5flr24hr`         | at least one M5.0 or greater flare within 24 hr after the observation. |

The accuracy of the model in predicting these parameters would be its accuracy in forecasting the solar weather.

## Deliverables
 
This project will have the following deliverables:
* Multiple notebooks for the Sunpy Examples gallery that highlight each algorithm implemented along with an interpretation of the results.
* The best performing trained model, properly documented and with instructions on how to use it.
* Instructions on how to retrain the model if necessary.
* A well documented and tested SunPy Search Events Object for querying Heliophysics Events Knowledgebase using HEKClient API.

### Timeline
___
#### Community Bonding Period 
___

- I shall spend this time exploring the dataset, discussing possible modifications to the architectures and hyperparameter tuning with my mentors, and continuing my contributions to SunPy.
- I also plan on implementing the SMART algorithm in python from the ground up using the [IDL implementation](https://github.com/TCDSolar/SMART). This will help me understand the various parameters and their generation.

___
#### Coding Period Begins
___

#### Week 1
- As per the official timeline mentioned, this week will be spent visualising different types of data, the magnetograms, univariate, multivariate analysis of the SMART detection properties with respect to both flare generation and the ELO complexity score. I shall be making all the plots in multiple notebooks for the SunPy examples gallery.

#### Week 2 

- Having already tinkered with the dataset, I have created a few basic plotting functions. Here is the [link](https://github.com/Raahul-Singh/SolarWeatherForecasting/blob/master/Data%20Preprocessing.ipynb) to the notebook that holds them. Here a few random examples. The red squares have been plotted using the Sunspotter data and the blue rectangles have been plotted from the queried HEK data. All functions are in the above-mentioned link. The red squares have been overplotted on purpose as the Sunspotter dataset lacks the information about the shape of the bounding boxes.

![Rectangled AR example 1](https://i.imgur.com/C36St72.png)
![Rectangled AR example 2](https://i.imgur.com/HglNyXX.png)

- I have also created a few helper functions to query the HEK database using HEKClient. I plan to further work on them and create the SunPy Search Events Object. I wish to give this at least four to five days to make this completely merge ready.

#### Week 3 - Week 4 

- Having completed all the previous tasks, we are now ready to tackle the problem head-on. First, the fourth week shall be used in completing the data preprocessing as described in the previous section.
- After ensuring that all the Cross-Validation sets are relatively balanced, the fifth week shall be used to implement a simple logistic regression model which a linear algebra model to map the complexity scores to the flare observations.
- This model shall serve as a benchmark for comparing all other models.
___
#### Phase 1 Evaluation 
___

#### Week 5 - Week 6 

- Here, having completed the data preprocessing earlier, we will be able to use various machine learning algorithms with relative ease. All the following will be implemented using Scikit-Learn library.
- For weeks 6 and 7, I shall make various models based on the following algorithms:
    
    * Decision Trees
    * Random Forest
    * SVM
    * SVM with Kernel

- All the implementations will be accompanied by an analysis blog post on the nature of the algorithm, an analysis of the results and possible deductions on the accuracy metric.

#### Week 7 
* Week 8 shall be used to implement models based on:
    * XGBoost
- Like with the previous implementations, this will be accompanied by an analysis blog post on the nature of the algorithm, an analysis of the results and possible deductions on the accuracy metric.

#### Week 8 

- At this point, we move into the domain of Deep Learning.
- For week 9, I shall be implementing a Deep Convolution Neural Network based on the paper, <br/>
 `Deep Learning-Based Solar Flare Forecasting Model. I. Results for Line-of-sight Magnetograms` [Huang et al.](https://iopscience.iop.org/article/10.3847/1538-4357/aaae00/pdf)

This shall be implemented using either the PyTorch or TensorFlow2.0 libraries, which shall be decided after discussing with the mentors.
___
#### Phase 2 Evaluation 
___

#### Week 9 - Week 10 
- Here I plan on implementing an original idea for a multichannel neural network, which would have the ability to take both the Sunspotter SMART detection values along with the corresponding images. I plan on making these different types of inputs compatible by first training an AutoEncoder network on the Active Region images to learn an effective lower-dimensional encoding for the images. This shall be concatenated and re-normalised with the processed SMART detection values and the complexity score to make the final feed-forward neural network that will learn the mapping.
This shall be a rather unchartered territory and I will give a full two weeks to implement this.

#### Week 11 - Week 12 
- The last two weeks of the project shall be used to summarise the results of all the various experiments based on the different algorithms.
- After selecting the best performing model, it shall be tested on SDO/HMI data from HEK.
- An extensive notebook shall be written detailing the use of the model and possible ways to tweak the hyperparameters.
- If time permits, as a side quest, I shall implement a neural network that directly maps the Active Region images with the ELO complexity rating. This shall help in automating the complexity prediction for magnetograms in the future.  

#### Week 13 
- The final week shall be kept as a buffer to complete any work that for any reason was not completed on time and also to add final touches to the deliverables.
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
       * [Significant reducuction of the download time for the dataset used in this project through the HelioViewer API.](https://github.com/sunpy/sunpy/pull/3862)
       *  [Rectangle coordinate parser to support multiple ways of specifying rectangular regions of  interest.](https://github.com/sunpy/sunpy/pull/3737)
       * [Integrating parfive==1.1rc2 with SunPy.](https://github.com/sunpy/sunpy/pull/3822)
       * [Implementing Limb Darkening correction.](https://github.com/sunpy/sunpy/pull/3728)
       * [Informing user when and what coordinate information may be missing when making a map.](https://github.com/sunpy/sunpy/pull/3692)
       
- Contributions to other repos:
  - Parfive
      - [Adds support for passing User Agent headers and Proxies](https://github.com/Cadair/parfive/pull/32)
  - And other contributions to EinstienPy and ChiantiPy.
- I will be contributing to SunPy throughout the selection process and beyond.

### Work Experience

##### 1) Global Remote Mentoring (IBM GRM) Intern
###### IBM India
###### Duration : Four months
- Worked on multimodal datasets containing stereo RGB and Lidar data for autonomous driving.
- Studied about camera parameters and the linear algebra behind switching from one perspective to another.

##### 2) Data Science Intern
###### Masho, an e-commerce startup from Bangalore, India
###### Duration : Four months
- Implemented Image to Image Similarity model using Siamese Networks for the Recommendation System, giving a robust recommendation.

#####  3) Machine Learning Intern
###### Indian Institute of Technology, Roorkee, India
###### Duration : Three months
- Made a model for understanding the behavior of various parameters like Sugar content, Acidity, Firmness, Ethyl Alcohol concentration and their visualization for Post-Harvest Apple data.
- Made a predictor model for charting the evolution of these parameters over a period of six months from harvest.

I think I have enough experience with python development to produce high quality, testable code.

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

* `Deep Learning-Based Solar Flare Forecasting Model. I. Results for Line-of-sight Magnetograms` [Huang et al.](https://iopscience.iop.org/article/10.3847/1538-4357/aaae00/pdf)

* `Solar flare prediction using advanced feature extraction, machine learning and feature selection` [Ahmed OW, Qahwaji RSR, Colak T, Higgins PA, Gallagher PTand Bloomfield DS (2013) Solar physics. 283(1): 157-175](https://bradscholars.brad.ac.uk/handle/10454/7581)

* `Predicting Solar Flares Using a Novel Deep Convolutional Neural Network` [Xuebao Li, Yanfang Zheng, et al 2020](https://iopscience.iop.org/article/10.3847/1538-4357/ab6d04/pdf)


