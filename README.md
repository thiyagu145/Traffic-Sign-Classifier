# Traffic-Sign-Classifier
The Github repository contains the project files of Project-2 of Self Driving Car Nanodegree program on Udacity. In this repository, the jupyter notebook file of the main project along with the html version of the notebook are available. The trained model is also uploaded along with the readme file for the project. 

The dataset used for training the model is the German Traffic Sign Dataset. The number of train, test and validation images are given below:
1) Training Images: 34799
2) Testing Images: 12630
3) Validation Images: 4410

The total number of signs in the dataset are 43. From the jupyter notebook, we can see the total number of each sign in the dataset. A random sign is displayed in the notebook. All images are of the size 32x32 with 3 channels. 

## Pre-processing Techniques used
1) RGB to Gray scale
The first step in pre-processing is to convert the color images into gray scale. This is done by averaging the values of the three channels in each image. For an image classification task, the color does not play that much of an importance. If you consider other examples such as image segmentation etc, we may need a color image to work on. For a classification task, the color does not matter and we look only on the edges and other structural information in the image. Hence, it is better to convert the 3-channel image to a single channel gray image. Another advantage is that, the number of parameters are also reduced if we consider the gray scale image. 
2) Image normalization
The image values are in the range of 0-255. They are normlized between the values of -1 and +1 for making the range smaller. A lot of features are extracted from the images. For any machine learning model, the images have to be normalized to make all the images in the same range. If the features are in different ranges, the optimization will not be able to work efficiently. This is the reason why the images have to be normalized before the features are extracted. 

## Model Architecture
The architecture was based on the LeNet architecture. There were some changes made to the architecture to improve the performance. The summary of the model used is given below

**Layer1** : Convolution with 6 filters of kernel size 5x5 followed by a relu activation <br />
**Layer2** : Max Pooling of kernel size 2x2  <br />
**Layer3** : Convolution with 16 filters of kernel size 5x5 followed by a relu activation <br />
**Layer4** : Max Pooling of kernel size 2x2 <br />
**Layer5** : Convolution with 32 filters of kernel size 3x3 followed by a relu activation <br />
**Layer6** : Fully connected layer by concatenating flattened layer3 and layer5 followed by dropout of 0.5 during training <br />
**Layer7** : Fully connected with input 1888 and output 1024 <br />
**Layer8** : Fully connected with input 1024 and output 512 <br />
**Layer9** : Fully connected with input 512 and output 43 (Output number of classes) <br />

## Model Training
The hyper-parameters for training the model are given below: <br />
Batch Size: 128 <br />
Number of epochs: 40 <br />
Learning Rate: 0.001 <br />
Optimizer: Adam <br />

## Solution Approach
The original LeNet-5 architecture gave an accuracy of 90% on the validation set. Hence to improve that, I used the architecture given in the LeNet for traffic sign classification paper. The architecture is given below

![alt text](https://raw.githubusercontent.com/thiyagu145/Traffic-Sign-Classifier/master/model-arch/model-architecture.png)

Though the number of filters and the kernel sizes were not exactly similar to the architecture from the paper, the basic skeleton was taken. The highest validation accuracy was about **95.8%** and the test accuracy was around **94.1%**
The accuracy increases slightly when augmented dataset is used. Hence, to get higher accuracies, different architectures have to be tried. <br />

The main difference between the modified LeNet model and the original are that, in the original model only the outputs of the last layers are considered for classification, whereas in the modified model the initial layers outputs are also considered. This implies that, both the initial layer feature maps as well as the final layer feature maps are considered for classification and hence, the classification accuracy is high. 

## Model performance on new images
Eight new traffic signs were obtained from the internet for traffic sign classification purpose. All the images are very good. They are taken in very good lighting conditions. Hence it will not be that difficult for the model to classify these images correctly. Also, the eight images are diverse and hence by use of these images, we can decide on the perfomance of the model to some extent. <br />
The model has an accuracy of **87.5%** on these new images. 7/8 images were classified correctly. This conveys that the model performance is very good and needs some more fine tuning to improve the performance. The results along with the softmax probabilites are given in the jupyter notebook. <br />
The accuracy on the test dataset is around 94.1%. The accuracy on the new images is 87.5%. This is not a lot of difference because the number of images in the test set are very high when compared to that of the number of images in the new image dataset. Hence, we cannot compare both these accuracies directly since the number of images are not the same in both the datasets. Also, the sign 25(road work) is misclassified as sign 11(right of way). This might be due to the fact that both these images have similar type of edges. Thus, the model performs very well on the traffic signs downloaded from the internet. 

