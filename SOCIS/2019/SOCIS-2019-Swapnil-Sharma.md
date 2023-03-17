# Project Title

**Space Weather Forecasting using Machine Learning**

# INTRODUCTION

## ABOUT ME

**Full Name:** Swapnil Sharma

**Time Zone:** IST (UTC+5:30)

**Email:** swap.sha96@gmail.com

**Github ID:** [swapsha96](https://github.com/swapsha96)

**Riot/Slack Handle:** swapsha96

**Blog:** https://medium.com/@swapsha96

**RSS Feed:** [RSS](https://medium.com/feed/@swapsha96)

# EDUCATION

**University:** Indian Institute of Technology Mandi

**Degree:** Bachelors in Computer Science and Engineering

**Current Graduation Year:** Fourth year (8th semester ongoing)

# PERSONAL BACKGROUND

I am an undergraduate student from India who loves to contribute to Open Source projects. My newly developed interests are **Machine/Deep Learning, Full Stack Development and Astronomy**. I am proficient in C, C++, Python, and Javascript. I have experience with machine learning frameworks like scikit-learn, Tensorflow and Keras.

My interest grew in astronomy when I joined Astronomy Club in the college. I was the club coordinator in the second year. As a coordinator, I organised events like night sky stargazing, meteor shower star party, quizzes and other events to increase the participation of students from different fields of science and engineering. I also like astrophotography and trekking.

# PREVIOUS PROJECTS

I participated in **Google Summer of Code 2018** in which I worked with astronomy researchers to apply Fourier techniques to time-domain X-ray data of black holes and neutron stars. My project focused on coding new algorithms for Stingray, an open-source Python package using state-of-the-art “spectral-timing” techniques. I implemented the full chain of phase-resolved spectroscopy of quasi-periodic oscillations. The project was at the intersection of signal processing, Fourier analysis, and open-source scientific software development.

In 2016, I worked on an **STScI project**, 3D-HST data extractor and API interface with Dr Ivelina Momcheva (Mentor) and Mr Ayush Yadav. We developed new API endpoint for object search and web interface to display information from Hubble Project data set and images from FITS files.

## MACHINE/DEEP LEARNING PROJECTS

I took '*Deep Learning and its Applications*' and '*Data Mining*' course in college that helped me to build interest and skills in Machine Learning and Data Science. I have worked on various projects and some of them are as the following:

1. **Ego/Non-ego Video Classification using Neural Networks**: I, in a team of two, designed a neural network to classify egocentric and non-egocentric videos using 2D convolution. We used FlowNet 2.0 for optical flow estimation and ResNet for image classification. Our network achieved an accuracy of 74%.

2. **MiraPy: Python Package for Machine Learning in Astronomy**: MiraPy is a Python package for Deep Learning in Astronomy. It is built using Keras for developing ML models to run on CPU and GPU seamlessly. The aim is to make applying machine learning techniques on astronomical data easy for astronomers, researchers and students. Following are some of the experiments that I am working on right now:

	- Classification of X-Ray Binaries using neural network
	- Astronomical Image Reconstruction using Autoencoder
	- Classification of the first catalog of variable stars by ATLAS
	- Classification of different states of GRS1905+105 X-Ray Binaries using Recurrent Neural Network (RNN)
	- Feature extraction from Images using Autoencoders and its applications in Astronomy

It is under development but I look forward to its official release before graduation.

[Github repository](https://github.com/mirapy-org/MiraPy)

[Jupyter notebook tutorials](https://github.com/mirapy-org/notebooks)

# PULL REQUESTS

Following is the link to my contributions to SunPy on Github: [link](https://github.com/sunpy/sunpy/pulls?q=is%3Apr+sort%3Aupdated-desc+author%3Aswapsha96+is%3Aclosed)

# The Proposal

## ABSTRACT

Space weather studies Sun-Earth interaction events. One of these, is the effect of solar flares have on our civilisation. The forecast of solar flares is not a solved problem, and many approaches have been tried. Sunspotter is a citizen science project that asked volunteers to classify solar active regions by their complexity - as it's believed complexity has a direct relationship with their activity. With more than 25,000 volunteers and millions of classifications produced, we've got a very nice dataset that can be used to train a neural network. The images used come from the MDI instrument, which is onboard of SoHO - the NASA-ESA mission that's been observing the sun for more than two decades.

## DESCRIPTION

The primary datasets come from **Sunspotter project**: All-Clear and 14 years of SoHO/MDI which contains the information of active regions on Sun and their classification. It can be used for various machine learning problems like classification, unsupervised clustering of images, and ranking of images based on their complexity. Each dataset contains information about the date and location of each active region used in the project and how it was classified by the volunteers. The volunteers were simply asked which image from a set of two seemed more complex, and by an Elo rating system provided a score. Visualization of data plays an important role in which we will use SunPy and sklearn-image. Firstly, We need to make some check to see that score and solar flares are related.

The project also involves acquiring MDI sun images from Solar and Heliospheric Observatory using VSO. Once we have the model with MDI then we can start to tune it to HMI (SDO). It will also include querying and downloading from solar feature archives like HEK or HELIO. Using scikit-image, we will obtain the segments from the FITS files using the position coordinated provided in the data available.

The **prediction of the score of complexity** can be done using either the AR properties of the images or using the images themselves. This problem can be seen as a regression problem for which ML models such as **Linear regression, Gradient Boosting regressor and Random Forest regressor** can be used. We'll find scikit-learn handy for this purpose. The components of the complete process will be put into SunPy for easy use.

The dataset also contains data of **pairwise comparison of active region images** which can be used to re-run the rating using different parameters or a different system altogether. **Bradley-Terry model** is a good example of a probability model which predicts the outcome of paired comparisons. For this purpose, `choix` can be used which a Python library that provides various inference algorithms.

All the classes and methods implemented will be properly documented and unit tests will be written for each piece of code. I will also work on Jupyter notebooks demonstrating the complete workflow so that anyone can use in their practice. I will write blog posts regularly to record my progress and discuss ML models on Medium.

# TIMELINE

## CURRENT PROGRESS

My current progress can be tracked on Jupyter Notebook on [Github](https://github.com/swapsha96/socis/blob/master/Playing%20with%20Sunspotter%20Dataset.ipynb).

**I have finished getting familiar with Sunspotter data** (point 1 of possible ideas in SunPy SOCIS wiki page). It involves extracting the dates, coordinates and file names from the database. It contains three CSV files (`lookup_properties, lookup_timesfits and rankings`) which contain details of images and the Elo rating score. `classifications.csv` contains pairwise comparisons of images.

![Flux vs Score Scatter Plot](https://i.imgur.com/q0C21E2.png)

`Flux vs Score Scatter Plot`

I applied Feature Reduction algorithm called **Principle Component Analysis (PCA)** algorithm for 2D visualization of active regions with respect to their ranking scores using AR properties by SMART algorithm.

![2D visualization of principal components of AR properties](https://i.imgur.com/LmJkPQ7.png)

`2D visualization of principal components of AR properties (colour varies with respect to score)`

I worked on prediction of the score of complexity using seven AR properties of images using regression models. I applied the min-max scaling transformation on input data. Following are the models that I used along with RMSE error and R2 score:

| Regression Model                  | RMSE Error | R^2 score |
|-----------------------------------|------------|----------:|
| Linear Regression                 | 76.6269    |    0.5438 |
| **Random Forest Regression**      | **41.9074**|	**0.8668** |
| Multi-layer Perceptron Regression | 55.0330    |    0.7647 |

The parameters of the models are in my jupyter notebook.

I worked on Pairwise Ranking Bradley-Terry probability model. For this purpose, I used choix package for the same. It also provides other algorithms to get rankings of images.

## CODING PERIOD

### Week 1-2

We will choose an approach to the design of a SunPy search events object based on the images using HEK or HELIO. It will also involve segmentation of active regions from FITS files.

### Week 3-4
I will work on finding the relationship between solar flare activities and properties of active regions. Using classification dataset, I will try various ranking algorithms and determine the best one to use for our purpose.

### Week 5-6

I will perform more experiments with different machine learning methods (discussed in previous sections) to find the best model. For this part, we will work with Sunspotter database. I will write blog posts to discuss our approaches and results.

### Week 7-10

I will check the accuracy of the model with SDO images from HEK. For this, we will perform feature extraction from MDI images. Later, we will extend it to HMI images.

### Week 11-12

I will merge all the leftover implementations (if any). I will ensure that all the classes and methods are well-documented, there is full test coverage and everything is working properly. I will work on Jupyter notebook describing the complete pipeline of preprocessing and machine learning techniques.

### FUTURE WORK

I would like to work on **Image Segmentation of active regions using Deep Learning**. There are powerful AI segmentation techniques which have various real-life applications like self-driving cars, medical MRI imaging and many more! It would be interesting to find if we can leverage ML models for the purpose of finding active regions which in return will help us to study solar flares and coronal mass ejection. I performed an experiment for the same and below is the result.

![Comparison of original image, ground truth and output image](https://i.imgur.com/vuDAf1X.png)

My neural network requires improvement which I would like to work on with the help of the project mentors.
