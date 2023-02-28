# Space Weather Forecasting using Machine Learning

## About Me

### <u>Biography</u>
I am Ayoob, a Software Engineering Student from IIT, Sri Lanka (degree affiliated with University of Westminster, UK) . I'm also **interning in the Big Data and Data Science Team** of Zone24X7 for a year (from July 2018) until June 2019, before beginning my final year of my Bachelors degree. As a Big Data Science intern my enthusiasm lie in impelling vasts amounts of data to yield structure and harmony from within.

I have been interested in Astronomy and Space from my early teens, and want to have more involvement in the field by contributing from the field of my training, Artificial Intelligence and Data Science.

Other than these my interests lie in Artificial Intelligence and am currently learning TensorFlow and Stacked GANs (Generative Adversarial Networks) for my Final year project for my degree starting September 2019.

My hobbies are cooking and reading books. When I'm doing neither I can be found hiking or riding my bicycle.

### <u>Contact Information</u>

**Student Name :** Mohamed Ayoob Nazeem

**Education :** Bachelors in Engineering (Hons) Software Engineering.
**Institute :** Informatics Institute of Technology - IIT Sri Lanka.

**Internship:** Big Data and Data Science Intern.
**Company:** Zone24X7 - Advanced Technology Center, Sri Lanka.

**Email :** mohamedayoob01@gmail.com (Primary) , nazeem.2016343@iit.ac.lk (Institute) , ayoobm@zone24x7.com (Internship)

**GitHub :**  [Ayoob7](https://github.com/Ayoob7)

**Other communication medium :** [LinkedIn](https://www.linkedin.com/in/mohamed-ayoob-815227147/) , **Skype :** mohamedayoob01@gmail.com


### <u>Institute Referee</u>

**Institution :** Informatics Institute of Technology, Sri Lanka (IIT Sri Lanka)
**Degree program :** Bachelors in Engineering (Hons) Software Engineering (3rd year of 4 years)

**Contact to Verify :** **Guhanathan Poravi - Senior Lecturer, Informatics Institute of Technology.**
Informatics Institute of Technology, 57 Ramakrishna Road, Colombo 06, Sri Lanka.

**Tel :** +94 112 360212 / 402(Ext)
**Email :** guhanathan.p@iit.ac.lk



### <u>Internship Referee</u>



**Company :** Zone24X7 (Advanced Technology Center)
**Title :** Big Data and Data Science Intern (10th month of 12 months)



**Contact to Verify :** **Bathiya Lakmal Priyadarshana - Architect / Senior Manager - Big Data and Data Science**

Zone24x7 (Private) Limited, 460, Nawala Road, Koswatta, Sri Lanka. (Advanced Technology Center)
Zone24x7 Incorporated, 3150 Almaden Expressway, Suite 234, San Jose, California 95118 USA. (Headquarters)

**Tel:** +94 11 2033900 / 141 (Ext)
**Email :** bathiyap@zone24x7.com

## Technical Experience and Community Engagement

I have been programming for 4 years , and using Ubuntu 16 as my main OS. Since I started programming using Python, I am extremely comfortable with the Python syntax and workflow.

I have done **courses from Lynda on Statistics and Data Science** ( full list [here](https://www.linkedin.com/in/mohamed-ayoob-815227147/) under License and Certifications) , and courses on Machine Learning , FullStack Foundations and Computer Science from Udacity.

My fluency in devops and languages includes:
 - Python , Java , Scala , Swift
 - Git - GitHub
 - Linux , Bash - process pipes, shell scripts, environments.
 - Libraries and packages like TensorFlow, SciKitLearn, Pandas, Numpy, MatPlotLib, Apache Spark.


Regarding opensource projects , I have participated and mentored my junior students to complete the Mozilla Global Sprint. I co founded the [AI Research Club](https://www.facebook.com/iitAiResearch/) in my campus to carry out AI research and educational programs. I am a [GitHub Developer Program member](https://github.com/Ayoob7) and in the GitHub Campus Expert Training at the moment. I write articles in [Medium](https://medium.com/@mohamedayoob01) as well.

I also made a pull request on SunPy [here](https://github.com/sunpy/sunpy/pull/3061), where one of the committers gave me helpful and supportive feedback. Further the branch I'm working on is [here](https://github.com/Ayoob7/sunpy/tree/issue-fixes) in the forked repository.


Specifically for Forecasting and Machine Learning I have been working on recommendation systems during my internship and also studied by myself to know the following statistical and neural models.

 - Time Series prediction - using Recurrent Neural Networks - this would prove useful in flare detection.
 - Association Analysis - Frequency Pattern , Apriori Algorithm
 - Classifiers - Support Vector Machines and Naive Bayes.

This is a set of [repositories](https://github.com/Ayoob7?tab=repositories) that I made, worked on or made boilerplate code for easy implementation. The following are repos exclusively on Python.

 - [Regression Template](https://github.com/Ayoob7/Regression-Template)
 - [QueryableDictionary](https://github.com/Ayoob7/English-Interactive-Dictionary-Python/blob/master/Dictn.py)

## Project Description

### Prologue

There are many harmful effects of solar flares on the human civilization. This project is an effort to predict and forecast the solar flares before they happen. It is believed that the complexity of solar flares have direct correlations with their activities. We have a data-set classified by volunteers in a campaign called **SunSpotter**. The classified images come from the MDI (Michelson Doppler Imager) on the SoHO (Solar and Heliospheric Observatory). To normalize the human errors they used an **Elo Rating system** when classifying  the images.

This project will be using components from SunPy while using other libraries like SciKitLearn SciKitImage and Tensor-flow to create a model by training the above images. To forecast and predict the change in Space Weather.

### History

This project is possible and is a next iteration due combined efforts of past students and volunteers. The trail of progress of this project has been mentioned below.

 1. SunSpotter - collected data on 2 occasions - [All-Clear](https://zenodo.org/record/1478966#.XMgaK3YzZhE) and [14 years](https://doi.org/10.5281/zenodo.1478971) (Same format but different data) - Classification
 2. [HEK](http://docs.sunpy.org/en/stable/guide/acquiring_data/hek.html) - able to search images - a querying service (images of flares, spots etc.)
 3. [Classified Features](https://www.dias.ie/cp-geophysics/astro/astro-research/astro-solar-physics-and-space-weather/esa-summer-of-code-in-space-2019/) -  a SOCIS project to classify using Convolutional Neural Networks
 4. Forecast Space weather - **This is the Scope of this project.** Take existing classified data points and forecast for future predictions.

### Design

This project is principally about answering the validity of this scientific hypothesis (from the Wiki Page).

> It's believed that an active region has more chances to flare if it looks more complex. Does this data validate the hypothesis? **If not what does it prove?** - Emphasis added.

I would like to approach this not only as a time-series-anomaly-detection approach (using Recurrent Neural Networks) but as a **forecasting**  proposition as well.
Hence I would like to try out to map the data to the following different models.

 1. Recurrent Time series **Anomaly Detection** (Ref 1) - since we are dealing with temporal data and want to detect anomalies (flares) [RNNs based LSTMs](https://www.elen.ucl.ac.be/Proceedings/esann/esannpdf/es2015-56.pdf) written in TensorFlow is an ideal solution for anomaly detection in the industry.

 2. Statistical **Forecasting** - Since we use **Elo rating** during the data preparation it would also be nice to experiment  using conventional statistical approaches to time series data as well. [FaceBook Prophet](https://facebook.github.io/prophet/) is very good at forecasting and much faster than machine learning models because they are based on statistical models rather than neural networks.
 3. I'm also comfortable with Conventional Machine Learning tasks like classification, clustering, regression and feature engineering principles, will try out with **Convolutional Neural Networks (CNNs)** to classify the images as well.

I'll list down the sub processes I would like to carry out during the coding.

1. **Exploratory Data Analysis (EDA)** - there are different files having different data, hence have to formalise them into the machine learning workflow to carry out feature engineering.
2. **Feature engineering** - Query solar features using HEK, and engineer them separately, that's because the 3 above models ingress different types of data.
3. Split the data into **test-train-validation** split.
4. **Create the models and test accuracy** for the best one.
5. Implement **visual report** using the statistical data visualization tool [seaborn](https://seaborn.pydata.org/) (MatPlotLib is part of sunpy and I can use seaborn along with it. SeaBorn makes MPL prettier) and **document them in a series of Medium Articles**.
6. **Test cases** for data access and model failures. (using PyTest as used in SunPy)
7. **Pickle** the best model in a server for fast predictions. ([Python pickle](https://docs.python.org/3/library/pickle.html))  [Why Pickle ML models?](https://machinelearningmastery.com/save-load-machine-learning-models-python-scikit-learn/)
8. **Documentation for SunPy Example Gallery on using the model.**



- **Optional** - Load the model in an [Apache Spark](https://spark.apache.org) Cluster - it's easy when running these machine learning jobs on large scale for it to slow down, hence in the industry we use Spark as an analytics engine for it to run on different clusters dynamically for large scale sequential processing in real time.

**NOTE**  : with the exception of writing test cases and documentation, at the end of each subprocess I will be opening a pull request to be reviewed and ratified by the mentor.
Test cases and Documentation will be done in parallel with the respective sub processes.

### Dependencies

 - [TensorFlow](https://www.tensorflow.org/) (essential) - for the Recurrent Neural Network (RNNs) based LSTMs and Convolutional Neural Network (CNNs)
 - [Pickle](https://docs.python.org/3/library/pickle.html) - (recommended) - Saving and loading ML models
 - [SeaBorn](https://seaborn.pydata.org/) (recommended) - advanced Visualization
 - [FB Prophet](https://facebook.github.io/prophet/) (recommended) - Forecasting
 - [PySpark](https://spark.apache.org/docs/latest/api/python/index.html) (optional) - BigData management and Clusterizing the processes.

### Final Deliverable Artifacts

 - Trained , tested and validated **Model** that has been cross validated by time series anomaly detection, statistical forecasting  and Deep Convolutional approaches
 - **3 articles** on the each of the approaches.
 - **Final documentation** for the Example Gallery
 - **Test Case class**

## Other Commitments
I don't have any commitments during the coding period, and other than my internship, which will end by June, I'm totally free until the end of September, when the final year of my degree begins. So I'm counting on working full time during those 3 months.

## Schedule
I use Trello to keep track of tasks

### Week 1
Explore the Data and do some EDA (Exploratory Data Analysis) on it. Particularly  we have 5 different CSV files containing data fields.
### Week 2
Work on SunPy search events objects based in HEK querying + Feature engineering  + Data pre-processing - **Pull Request**
### Week 3-4
Implement Machine Learning models - based on the above 3 approaches mentioned. (Anomaly Detection , Statistical , Deep Neural Networks) -
**Pull Request**

### Week 5-6
Articles on the above three approaches to the problem. Complete Test Cases for the 3 approaches, and start on SunPy Example Gallery Notebook.

### Week 7
Work on unconventional approaches to this problem like **disentangled variational auto-encoders** (Ref 2), (figuring out ways solar flares can occur - here we are not merely checking for **correlation**, we are checking for **causality** to answer the validity of the scientific hypothesis this project is addressing.  - **Pull Request**

### Week 8-9
Compare and validate the Accuracy, Recall (not for auto-encoders) , Precision (not for auto-encoders)  and F1 score of all the tested models with the SDO images. - **Pull Request**

### Week 10
Finalize the left over works, including the test cases, articles and complete them. - **Pull Request**

### Week 11 - 12
Cushioning Week - for any unexpected delays or roadblocks. If not will be working on the refining the documentation and the articles.


## Future Work

I briefly touched upon auto-encoders and the Causal relationship of solar flares (week 7) , future work can handle, on an entirely independent research on the **causal vs correlation**  relationship between the features and solar flares. In addition to that we can also have **stackedGANS** to synthesize potential images prior to solar flares, this will help astronomers be better prepared to solar flares.


## References

1. [Long Short Term Memory Networks for Anomaly Detection in Time Series](https://www.elen.ucl.ac.be/Proceedings/esann/esannpdf/es2015-56.pdf)
2. [Causal Effect Inference with Deep Latent-Variable Models](https://arxiv.org/pdf/1705.08821.pdf)
