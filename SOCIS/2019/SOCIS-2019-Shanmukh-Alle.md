## Space Weather Forecasting using Machine Learning

## About Me
* Name : Shanmukh Alle
* Contact Information
    - Email : shanmukh98@gmail.com
    - GitHub username : shanmukh98
    - Riot username : shanmukh98
    - Medium : medium.com/@shanmukh98
    - Time Zone : IST (UTC +5:30)
* Education
    - University : International Institute of Information Technology, Hyderabad, India
    - Degree : B.Tech with MS by Research in ECE

### Personal Background
I am a fourth year undergraduate student at IIIT-Hyderabad. I am a machine learning enthusiast and I have extensively explored various state of the art models and techniques in fields including but not limited to Computer Vision, NLP and Computational Sciences. I am proficient in C,C++,Python and Matlab. I have experience in building machine learning models in  Keras, Pytorch and Scikit-learn. I occasionally participate in data science contests. I am primarily interested in computer vision and its application in various fields of knowledge.
### Experience with Machine Learning
* Worked as Teaching Assistant for the course Statistical Methods in AI for fall 2018.
* Worked in a team of 3 to build a Manga/Comic colourisation system using Conditional Generative Adversarial Networks. Code for the project can be accessed here -> [manga_colourisation]

[manga_colourisation]: https://github.com/sudheerachary/Manga_Colorization
* Worked in a team of 4 to build a Neural Image Captioning System using attention based CNN. Code for the project can be found here -> [show-and-tell]

[show-and-tell]: https://github.com/Saiteja-Reddy/Show-and-Tell
* Worked in a team of 2 to build a deep learning based system that segments road networks from satellite images. A live demo of the project can be found here -> [road_extraction]

[road_extraction]: https://researchweb.iiit.ac.in/~shanmukh.alle/road_extraction.html

* Worked in a team of 2 to build a system that uses transformer networks to predict protein secondary structure given protein amino acid sequence. (Ongoing project)

* Top 0.5 percentile in [Flipkart GRID AI Challenge] 2019

[Flipkart GRID AI Challenge]: https://dare2compete.com/o/Flipkart-GRiD-Teach-The-Machines-2019-74928?utm_source=MailingList20&utm_medium=Mailer&utm_campaign=FlipkartGrid

* National finalist at [Microsoft GAINS AI Hackathon] 2017

[Microsoft GAINS AI Hackathon]: https://allevents.in/hyderabad/gains-ai-hackathon/290290021463159
___
## Proposal
### Introduction
Space weather is a branch of astronomy that deals with time varying conditions in the solar system. In this project we deal with forecasting of solar flares using machine learning methods. Solar flares are abrupt, powerful events that lead to sudden increase in the brightness on the sun which are observed near the surface close to a sunspot group. Solar flares have a potential to disrupt various human technologies that depend on EM radiations. Mobile phone
transmission interruptions, high-frequency communications, aircraft rerouting, and power-grid performance to name a few[[1]].

 Most of the methods mentioned in [[1]][[2]] do not use the structure of the sunspot cluster to arrive at a decision. Primarily, these methods make use of data measured from satellite sensors, such as Magnetic fields, continuum intensity etc. which do not explicitly incorporate structure of active region. In recent days, Convolutional Neural Networks have shown to work well in recognising complex patterns in images to perform various classification and regression tasks. Work done by Xin et al.[[3]] show that CNNs perform similar to the state of the art solar flare forecasting methods. A blog explaining the working of CNNs can be found here[[4]].

 The Sun spotter project data sets contain images of sunspots ranked based on their complexity which is defined based on the elo rating. It is observed that there is a direct relationship between solar flare activity and the complexity of a sunspot[[2]]. Apart from this, the data sets also contain additional information(SMART data) about the active regions in the images. Performance of machine learning models are known to scale with the amount of data available, hence we intend to improve the performance of CNNs for forecast by using this additional data.

The following section describes the proposed solution in detail.

### Proposed solution

#### Baseline CNN
As a baseline, we intend to implement a basic CNN model with 2D convolutions followed by a multi layer perceptron. The image of active region is fed in as input. The model will be trained to predict the class of solar flare as the output. The baseline when trained gives us an understanding of the complexity of the dataset and serves as a comparison.

To improve the performance, additional important numerical features about the active region obtained from HEK or Helio or the Sun spotter dataset can be added one by one to the multilayer perceptron. This step involves performing some exploratory data analysis to understand the importance of specific features.
The dataflow can be observed in the image below.
<div style="text-align:center"><img src="https://researchweb.iiit.ac.in/~shanmukh.alle/images/1.jpg" /></div>


Since the task is formulated as a classification problem the objective function will be cross entropy calculated between the predicted and ground truth class labels of the image.
#### Siamese CNN
It is a well documented fact that multi-task learning[[6]] improves the performance of each of the tasks trained on when the tasks are highly correlated.
Hence, we propose to train a CNN on two objective functions.
1. Forecast loss (generally some form of cross entropy)
2. Complexity prediction loss (mse on the predicted values or on a transformed version of them)

To train the model on complexity information we use a Siamese neural network that has a two CNNs with shared weights that act as feature extractors and a contrastive function. Given a pair of images the model is trained to predict the probability of one being more complex than the other when given to a human. Since the complexity is encoded in the form of elo ratings we use<img src="https://researchweb.iiit.ac.in/~shanmukh.alle/images/3.png" alt="drawing" width="100"/> as the contrastive function to predict the probability.

The same function can be used to generate the ground truth probability values from elo ratings of the selected pair of images.

The contrastive function used is the equation used to get the win probability in a match between two players given their elo rating[[7]].

An explanation of how Siamese neural networks can be found here [[5]]

Training the CNN feature extractor in the form of a Siamese network has the following advantages when compared to direct prediction of elo rating.
* Only the relative complexity difference between images is considered as the contrasitve loss used the difference in the predicted features
* Amount of training samples increases quadratically since pairs of images are chosen for each training iteration
* The neural network trains better due to more updates per training iteration

We train CNN feature extractor to minimise the sum of both the loss functions.

The dataflow can be observed in the image below.

<div style="text-align:center"><img src="https://researchweb.iiit.ac.in/~shanmukh.alle/images/2.jpg" /></div>


___
## Coding Period


#### Week 1
- Familiarise with datasets
- Determine various parameters to extract from HEK

#### Week 2
- Perform exploratory data analysis

#### Week 3 - Week 4
- Implement the baseline model in keras and train
- Debug if problems occur
- Performance analysis of baseline model on test set divided from Sunspotter datasets

#### Week 5 - Week 8
- Implement Siamese Network in keras
- Experiment various CNN architectures
- Debug is problems occur

#### Week 9
- Build test set with images from SDO/HMI obtained through HEK

#### Week 10
- Analyse the performance of both the models on Test set
- Code clean up

#### Week 11
- Write a tutorial on usage of both the models

#### Week 12
- Buffer
___
#### Final Evaluation
___
### References
[1]: https://www.sciencedirect.com/science/article/pii/B9780128127001000030
1. Leka, K. D., and Graham Barnes. "Solar flare forecasting: present methods and challenges." Extreme Events in Geospace. Elsevier, 2018. 65-98.

[2]: https://iopscience.iop.org/article/10.3847/0004-637X/829/2/89/meta
2. Barnes, Graham, et al. "A Comparison of flare forecasting methods. I. Results from the “all-clear” workshop." The Astrophysical Journal 829.2 (2016): 89.

[3]: https://iopscience.iop.org/article/10.3847/1538-4357/aaae00/pdf
3. Huang, Xin, et al. "Deep learning based solar flare forecasting model. I. results for line-of-sight magnetograms." The Astrophysical Journal 856.1 (2018): 7.

[4]: https://skymind.ai/wiki/convolutional-network
4. A nice blog on Convolutional Neural Networks [[4]]

[5]: https://qr.ae/TWISUG
5. A nice explanation of Siamese Neural Networks [[5]]

[6]: https://towardsdatascience.com/multitask-learning-teach-your-ai-more-to-make-it-better-dde116c2cd40
6. A nice blog on Multitask learning [[6]]

[7]: https://www.geeksforgeeks.org/elo-rating-algorithm/
7. Elo rating to win probability[[7]]
