# Robotic Inference [![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)

abstract
--------

working on a supplied data from a camera fixed above a conveyor belt and a collected data using a mobile camera, first using the supplied data with Nvidia DIGITS workflow to train a model by tuning the hyperparameters and choosing the best network to achieve a specific inference time and accuracy, second using the collected data for an inference idea and training a model using Nvidia DIGITS to deploy this model on an embedded  system like Jetson TX2 board.


Introduction
------------

the robotic kitchen is now an interesting part of robotics which full of challenges, due to the routine of life nowadays we are very busy because of the tight schedules, so it's difficult to take care of our food, people tend to approach fast-food instead of preparing healthy meals at home which leads to severe diseases.

nowadays there are some cooking robots which enable us to cook the food.

![robot1](https://meee-services.com/wp-content/uploads/2018/02/robot-chef_resize_md.jpg)

they are fully automated robots, so they have to capture the world around them using several kinds of sensors and cameras.
in turn classifying images around the robot and determining each kitchenware is a core element of the robot perception process, using Nvidia DIGITS workflow with a collected photos of spoons or forks or even no thing to train a network for the classification processes.


Background / Formulation
------------------------

several types of DNN’s have been developed on the ImageNet benchmark dataset like AlexNet, VGGNet, ResNet, Inception, GoogleNet and their many variations.

The increased accuracy is the result of breakthroughs in design and optimization, but comes at a cost when computation resources are considered.

The following table provides a sampling of the results (values are approximated from graphs in the paper), including a derived metric called information density. The information density is a measure of the efficiency of the network, or how much accuracy is provided for every one million parameters that the network requires.

![table](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/metrics.png)

Note that only the results based on a batch size of one are included. In most cases, the batch size provides a speedup in inference time but maintains the same relative performance among architectures. However, an exception is AlexNet, which sees a 3x speedup when going from 1 to 64 images per batch due to weak optimization of its fully connected layer.

for the supplied data collected using Jetson TX2 camera above a conveyor belt AlexNet gave a good results in this case however the other DNN’s may give more accurate results.

for the collected data, using about 350 image per class GoogleNet gave more accurate results than AlexNet using 0.001 learning rate.

Data Acquisition
----------------

### first the Supplied Data

for the supplied data there are 7570 image for the following 3 classes:
1. Bottle
2. Candy Box
3. Nothing

the data looks like this photo below :

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/data-p1-digits.jpg)

first by opening the DIGITS workspace we should see something like this

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/digits.png)

#### for image classification

- by choosing `images` then `classification` we will see something like so 
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/image-classification.png)

- adding our dataset url in this case using udacity workspace it will be `/data/P1_data`
- more setting can be done here like Minimum samples per class or maximum samples per class or even the percentage of validation photos and testing photos
- then by giving the dataset a name and choosing create :

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/dataset.png)

#### the model

- by choosing `images` then `classification` 
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/model-classification.png)

- now we can set the number of epochs, Snapshot interval, Base Learning Rate, Validation interval ....
- by choosing one of the 3 networks provided LeNet, AlexNet and GoogLeNet in this case AlexNet gave a good results.
- giving the model a name then create.

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/model.png)

### second the Collected Data

for the Collected Data there are 1070 image for the following 3 classes:
1. spoon
2. fork
3. no-thing

#### for image classification

- the collected data using mobile camera then by resizing the collected data to be 256*256 
- by choosing `images` then `classification`.
- adding our dataset url in this case using udacity workspace it will be `/data/kitchen`
- as previous more setting can be done like Minimum samples per class or maximum samples per class or even the percentage of validation photos and testing photos
- then by giving the dataset a name and choosing create :

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/dataset2.png)

samples of the collected data :

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/sample1.JPG)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/sample2.JPG)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/sample3.JPG)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/sample4.JPG)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/sample5.JPG)

#### the model

- by choosing `images` then `classification` 
- now we can set the number of epochs, Snapshot interval, Base Learning Rate, Validation interval ....
- by choosing one of the 3 networks provided LeNet, AlexNet and GoogLeNet in this case GoogLeNet gave a better results than AlexNet.
- giving the model a name then create.
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/model2.png)

Results
-------

### first the Supplied Data
- the output model graph for the supplied data using AlexNet 
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/graph1.png)

#### two ways to see the model results as below:
- by running the `evaluate` command in a new terminal in udacity workspace the results will be like so

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/evaluate.png)

- by choosing images for test

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/test1.png)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/test2.png)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/test3.png)



### second the Collected Data

#### the 2 models results AlexNet and GoogLeNet
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/graph2.png)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/graph3.png)

- to see this model result by choosing images for test

![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/test4.png)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/test5.png)
![](https://github.com/mohamedsayedantar/Robotic-Inference/blob/master/images/test6.png)

Discussion
----------

huge difference in accuracy between AlexNet and GoogLeNet as shown previously and this difference appear more with small number of data given to the model like the previous case about 1070 images only for classification, while this difference become smaller with increasing the number of data, after many attempts the inference time for GoogLeNet is greater than AlexNet.

Conclusion / Future Work
------------------------

for the inference time AlexNet is good, but developers in many cases look for the accuracy so GoogLeNet is the best choice, increasing the number of collected data will lead to increasing accuracy but in case too much data the change will be very small almost no thing.

for the robotic kitchen increasing the number of classes with almost every kitchenware known till now, will lead to more intelligent robots due to variety in classifying objects ability


references
----------

https://www.asme.org/engineering-topics/articles/robotics/the-robotic-kitchen-is-cooking
https://www.iflscience.com/technology/robot-chef-home-could-arrive-2017/
https://meee-services.com/how-to-use-cooking-robots-in-your-kitchen/




[Supplied Data Model](https://drive.google.com/open?id=17r0Osgwb-YWyuTxHR0YVG8fzLLeRKRTS)
