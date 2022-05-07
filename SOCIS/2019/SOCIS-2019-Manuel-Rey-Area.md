# Space Weather Forecasting using Machine Learning
## Personal Info
- Name: Manuel Rey Area
- University: Autonomous University of Barcelona
- Email: mreyarea@gmail.com
- Github: [@manurare](https://github.com/manurare)

## About me
I am currently enrolled on the Computer Vision master programe at the Autonomous University of Barcelona (UAB). During the past four years I’ve been studying Telecommunications Engineering at University of Vigo as well in Spain and I specialized in Image and Sound. Also in my last year of my bachelors I did an Erasmus scholarship in Denmark where I coursed subjects in AI and medical imaging.

Since I discovered the field of Computer Vision I have never stopped learning. I started by raw image processing during my career and at the moment we are learning the core of Machine Learning apply to images. What defines me most is that I am not satisfied only with knowing how to use a specific framework or a specific library but I try to understand the roots (why and hows) of the techniques I am using thus building a strong and robust knowledge on the topic.

## Me and SOCIS
I have never participated in SOCIS or GSoC before. I am also applying for other projects as #53 from SOCIS.

If during the summer and until the conclusion of the SOCIS period mentors are happy with my job they think they think I am reliable source of help into the project I would love to keep working on it.

## Me the programmer
My most fluent programming languages are C/C++, Python and MATLAB. I use PyCharm along with Ubuntu to code in Python and Atom to code in C/C++ (Long life to Open Source!).

My biggest experience with open source libraries is OpenCV. I consider myself to have a strong background on it as I have used in my bachelor's thesis as the angular point. I also worked with different ML libraries as scikit-learn and different DL frameworks as Keras, PyTorch and TF.

My contribution to SunPy can be found [here](https://github.com/sunpy/sunpy/issues/3007)

## Me and the project
The reason why I chose this project it is because it involves vision, ML and space. In the case of the latter, I did my [bachelor thesis](https://github.com/manurare/Superresolution-VideoSequences) on super-resolution techniques for the identification of anonymous subjects in video sequences using _Drizzle_ which is an algorithm used in the Hubble Space Telescope to correct the drift caused in consecutive images by inner artifacts from the telescope. I enjoyed a lot this time working with it and it kept me on the lookout for new algorithms apply to astronomic purposes.

I believe that my bachelor thesis along with the fact that I am studying state of the art ML makes a perfect match for the project. Also, I would like to propose it as my master's thesis meaning that I will be completely dedicated to it with no distractions.

The dataset used for this project not only contains images but location, date and complexity for each case. First step is trying to generalize what relationship exists between complexity and the other variables. For this SunPy will be used by reading the metadata and scikit-learn to apply a model which better describes the link among them.

Also if there are images belonging to consecutive frames we could use RNNs (LSTMs or GRUs) to not forget about the past i.e, check if the activation of one region is given after another specific region or if the order of occurrences is random. The RNN inner state will be combined with CNN due to handle with images. Another thing to try is using ·D convolutions to check if there exist a temporal coherence. All this methodology will be performed using different frameworks (a consensus is needed) as PyTorch, Keras or TF always finding the optimal compatibility with SunPy.

If a classification is needed as we are always working with solar images it is hard to tell a classifier to differ between classes being the classes the region activated in a particular frame. To tackle this problem a siamese network can also be fine tuned. Therefore, it will cluster images with the same activated region together and as far as possible from the other clusters belonging to different activated regions.

With the date info it is possible to elaborate a mapping between active regions with a specific season. Also we can build a probabilistic model which will model the likelihood of a given active region given the previous or any other. This can be an extension to the RNN approach.

## Timeline
This a roughly described timeline as I think the optimal will be discussed with the mentor. There will be some things added and some removed and probably there will be more interest in some steps than others.
### Week 1-2
Getting familiarize with the dataset: how to read it, store metadata, image format etc. Also check if the dataset is balanced or not i.e, check if there are roughly the same amount of images per class (being the class the active region).
### Week 3-4
Implement the scikit-learn algorithm which better models the relationship between metadata i.e, location, date and complexity. Thus, when a new image is fed into the dataset it can be automatically arranged by this model.
### Week 5-10
Implement all the DL methodologies explained. This is the core of the project and it will take most of the time.
### Week 10-12
Debug code and execute all the necessary PRs. Create the notebooks asked in the definition of the project.
