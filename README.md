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

for the collected data GoogleNet gaved more accurate results than AlexNet using 0.001 learning rate.

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








### second the Collected Data














[Supplied Data Model](https://drive.google.com/open?id=17r0Osgwb-YWyuTxHR0YVG8fzLLeRKRTS)
