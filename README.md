# Traffic-Sign-Classifier
The Github repository contains the project files of Project-2 of Self Driving Car Nanodegree program on Udacity. In this repository, the jupyter notebook file of the main project along with the html version of the notebook are available. The trained model is also uploaded along with the readme file for the project. 

The dataset used for training the model is the German Traffic Sign Dataset. The number of train, test and validation images are given below:
1) Training Images: 34799
2) Testing Images: 12630
3) Validation Images: 4410

The total number of signs in the dataset are 43. From the jupyter notebook, we can see the total number of each sign in the dataset. A random sign is displayed in the notebook. All images are of the size 32x32 with 3 channels. 

## Pre-processing Techniques used
1) RGB to Gray scale
The first step in pre-processing is to convert the color images into gray scale. This is done by averaging the values of the three channels in each image. 
2) Image normalization
The image values are in the range of 0-255. They are normlized between the values of -1 and +1 for making the range smaller. 

## Model Architecture
The architecture was based on the LeNet architecture. There were some changes made to the architecture to improve the performance. The summary of the model used is given below

**Layer1** : Convolution with 6 filters of kernel size 5x5 followed by a relu activation. 
**Layer2** : Max Pooling of kernel size 2x2. 
**Layer3** : Convolution with 16 filters of kernel size 5x5 followed by a relu activation. 
**Layer4** : Max Pooling of kernel size 2x2. 
**Layer5** : Convolution with 32 filters of kernel size 3x3 followed by a relu activation. 
**Layer6** : Fully connected layer by concatenating flattened layer3 and layer5 followed by dropout of 0.5 during training. 
**Layer7** : Fully connected with input 1888 and output 1024. 
**Layer8** : Fully connected with input 1024 and output 512. 
**Layer9** : Fully connected with input 512 and output 43 (Output number of classes). 

## Model Training
The hyper-parameters for training the model are given below:
Batch Size: 128
Number of epochs: 40

