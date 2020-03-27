<!----- Conversion time: 1.282 seconds.


Using this Markdown file:

1. Cut and paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β20
* Fri Mar 27 2020 03:42:06 GMT-0700 (PDT)
* Source doc: Space Weather Forecasting using Linear Methods - Amogh Jahagirdar
* This is a partial selection. Check to make sure intra-doc links work.
----->



# Space Weather Forecasting using Linear Methods 

Name: Amogh Jahagirdar

University: National Institute of Technology, Tiruchirappalli, India

Course: Bachelor of Technology, Instrumentation and Control Engg. (Major) and Computer Sci.(Minor)

Email: [jramogh@gmail.com](mailto:jramogh@gmail.com)

Github: [https://www.github.com/amogh-jrules](https://www.github.com/amogh-jrules)

Kaggle: [https://www.kaggle.com/amoghjrules](https://www.kaggle.com/amoghjrules)

LinkedIn: [https://www.linkedin.com/in/amoghjahagirdar/](https://www.linkedin.com/in/amoghjahagirdar/)

Contact No.: +91 9082180199


## About Me:

I am a 3rd year undergraduate student and OSS enthusiast and love contributing to projects that impact human lives. Apart from programming, I enjoy reading and going on runs.


## GSOC:

I have not participated in GSoC before and will not be applying to any other projects. I am eligible to receive payments from Google.

I already have been working with the idea and have been sharing my progress with the mentors regularly. During the program I will be comfortably able to allocate 5-6 hours a day and will put in extra hours if the schedule demands it.

I will be having a round of examinations in the Summer because my University has shifted semester dates because of the COVID-19 outbreak. Apart from that, I will not be taking any vacations over the duration of the program.


## Programming:

My first hobby project was a sprite based game back in 10th grade. It received 70,000+ downloads on the Play Store. I have been professionally coding for the past 3 years. In the past I have worked with the Hyperledger Blockchain framework and with GroceriStar, which is an OSS driven startup in Ukraine.

I am ranked in the top 0.5% (Rank 495 of 100000+) on Google's Competitive Machine Learning and Data Science platform, [kaggle.com](https://www.kaggle.com). Having worked in the field of Data Science for the entirety of the past year, I have acquired decent experience with respect to Linear ML Models, Python. (Some of [my work](https://www.kaggle.com/amoghjrules/notebooks) related to modelling methods, feature engineering, etc.)

Recently, I co-authored a [research paper](https://drive.google.com/open?id=1xif6lI7y224q3yi5LA4_-kuG7cPpT6-o) for Beebots, which is a blockchain-based decentralised swarm robotic system. I implemented and tested a density-based clustering algorithm in Python which helped optimize the bots’ behaviour. [(Github repo)](https://github.com/spider-tronix/bee-bots)

Last winter, I mentored at the Tensorflow organisation at Google Code-In. I meticulously reviewed 70+ tasks (mostly Python based) and provided constructive criticism and assisted them in debugging their code. [(Certificate)](https://drive.google.com/open?id=1UlXxFnHFcCmjo99-NzAe25X8B5UH4OtU)

In September 2019, I worked on Ytality, a product ecosystem to transmit vitals of an ailing patient via the cloud, pass them through disease-diagnosis models and display them to doctors. I trained models using TensorFlow and Keras on extensive datasets of EEG, ECG and heart-sound classifications. [(Details and Code)](https://devfolio.co/submissions/ytality)

All my above projects have git-based version control and are hosted on github.com. I have a working understanding of git, which I have gained from practical use. My OSS experience can be tracked via [my Github contributions](https://github.com/amogh-jrules).

 

[Contributions](https://github.com/sunpy/sunpy/issues?q=author%3Aamogh-jrules) to SunPy (5 PRs, 2 merged, 4 issues, 3 closed)

[Notebook](https://www.kaggle.com/amoghjrules/predicting-solar-activity) containing my exploratory analyses and implementation of baseline models 

[Colab notebook](https://colab.research.google.com/drive/1gfoyXNClV2NbKCiAdX4JJr255QfocmXc) with Sunspotter EDA with interacting with SunPy modules


## Proposal: 

Most people do not realise that the Sun and solar weather can affect their daily life. Although there have been multiple attempts to forecast solar weather, I feel there remains a lot left to be done in the field. I want to achieve the state of the art forecasting ability for Solar weather. 

What excites me about this project is the long lasting impact my work will have on human lives and the fact that I will be able to contribute a tiny bit to the overall progress of mankind.

I chose this project because it aligns with my technical skills and interests. Moreover, the SunPy community is very responsive and receptive, which is a sign that they are passionate about the project.

As mentioned earlier, I have a sound background in Machine Learning, Neural networks and Data Science. Being fluent in Python will enable me to write clean, readable code and maintain the high coding standards of the library. Self motivated and enthusiastic, I will not have any problem working independently, asking the mentors for help only when it is really needed.


## Implementation:

For simplicity, I have broken down the project into a number of subtasks, as shown below:


### Task 1 - Data Preprocessing :

It involves feature cleaning (e.g., converting timestamps into an ordinal variable), handling missing values, normalizing data.



*   Metric for normalization - Z-Score


### Task 2(a) - Exploratory Data Analysis: 

Exploratory Data Analysis or EDA involves plotting graphs inorder to uncover underlying trends in the data and relations between the independent features. It consists of :



*   Visualising the distribution of variables
*   Plotting Pearson Correlation Coefficients and more

The inferences obtained on analyzing these plots will provide the basis on which the modeling technique(s) are chosen.

![](https://i.postimg.cc/2SJFfGpX/image.png)
### Task 2 (b) - Feature Generation:

The inference obtained will not only be used to choose the appropriate models, but will also be used to analyze the possibility of generating new more information rich features by combining 2 or more features with a low correlation score, or dropping redundant features to improve the model.


### Task 3 - Data Modelling:

Here is where most of the heavy-lifting will be done.



*   Implementing a [Deep Flare Net (DeFN) for Solar Flare Prediction](https://arxiv.org/abs/1805.03421). It will involve:
    *   Multilayer Image-based DNN to predict the probability of flares occuring within the next X hr of time in an active region
    *   Further used to determine the most likely maximum classes of flares 
    *   The cost function this NN will be the minimization of cross entropy
    *   A major advantage of this implementation are that the features are human readable unlike CNNs which extract imaging features that we cannot understand.
    *   It is also possible to rank these features in order of importance. (High computational power required)
    *   Will be implemented with Pytorch or TF Keras
*   Using linear and non-linear models from sklearn, xgboost and lightgbm. They will be:
    *   Logistic Regression
    *   Support Vector Machine
    *   Random Forest Regressor
    *   Elastic Net
    *   Lasso
    *   XGBoost Regressor
    *   Light Gradient Boosting Machine Regressor
*   Ensemble learning pipeline. This will consist of:
    *   Averaged Voting - predictions of all models are averaged
    *   Weighted Voting - the predictions of models are given varied weights based on their importances/contribution to accuracy
    *   Out of Fold Meta-Modeling - the predictions of all models are taken in as training data for a meta-model which gives the final classification
*   Hyperparameter optimisation to further optimize models.
    *   GridSearchCV from sklearn - allows us to pass a range of values for each parameter, out of which the optimal value is searched and selected

These methods are the industry standard in modern day data-science. I have just made a baseline implementation of the same in the notebook and yet I was able to achieve accuracy upwards of 88%.


### Task 4 - Implementing the pipeline as an API into SunPy:

Integrating the above trained models into a SunPy model class with member functions like fit, predict and feature importances, with the ability to choose between the different modelling techniques shown above. 


### Task 5 - Writing unit and integration tests

This constitutes writing unit tests for each sub-module within the project and integration tests to ensure that there are no conflicts within the module itself.


### Task 6 - Documentation

Writing down documentation which clearly explains the purpose of the module, the classes, member functions, callbacks and other details along with their usage.


### Challenges:

On plotting out the target variable (the classification variable) a clear bias towards the negative class is visible. This unbalanced target distribution can lead to poorly trained models. Having 

discussed this with the mentors before, I decided to implement Stratified K-Fold validation. Stratified K-Fold takes K-Fold validation a step further in that it ensures that the distribution of classes in every fold is identical to that of the overall dataset. I have already implemented a flexible Stratified K-Fold generating pipeline as a means of generating Out of Fold training data.
![Target distributions](https://i.postimg.cc/cJWkv3Bm/target.png)
## Timeline:


### Community Bonding Period (May 4 - June 1)



*   Reading through research papers that will be implemented.
*   Re-setup local development environment
*   Interaction with the community


### Week 1 (June 1 - June 7)



*   Data cleaning, handling missing values
*   Trying out different normalization techniques and choosing one that suits best
*   Complete data pre-processing


### Week 2 (June 7 - June 14)



*   Exploratory Data Analysis
*   Feature generation


### Week 3 (June 15 - June 22)



*   Train models from sklearn, xgboost and lgbm
*   Implement ensemble learning


### Week 4 (June 23 - June 29)



*   Publish the preprocessed, feature generated dataset
*   Consolidate all the various plots, models and techniques implemented in the past month into a jupyter notebook for the SunPy example gallery


### Evaluation 1 (June 29 - July 3)


### Week 5 - 6 (July 4 - July 18)



*   Implementation of Deep Flare Network (DeFN)


### Week 7 (July 18 - July 25)



*   Write a jupyter notebook showing the use of the neural network for SunPy example gallery
*   Write unit tests for the linear model pipeline


### Evaluation 2 (July 27 - July 31)


### Week 8 (August 1 - August 7)



*   Write unit tests for the neural network pipeline
*   Write integration tests for the project


### Week 9 (August 8 - August 14)



*   Complete integration into the official SunPy library
*   Test out the model against SDO/HMI data
*   Write a notebook showcasing the same, along with external hyperparameter tuning for the neural network 


### Week 10 (August 14 - 24)



*   Documentation and final touches


### Final Evaluation


<!-- Docs to Markdown version 1.0β20 -->
