# End to End Deep Learning for Self Driving Cars

<img src = "https://github.com/Swetadas-1718/Self-Driving-Car-End-to-End-Deep-Learning-model/blob/main/waymo.jpg">

Today, we can see fully self-driving cars on the road. Some call it a fad , while some call it a marvel of technology. I know, driverless vehicles is quite an impossible concept to believe in.

These vehicles carry passengers from a point to another point and are promised to reduce fuel consumption, provide passenger a safer journey and reduce 95% errors caused by humans.

The key question should be "Are they safer than us ?" instead of "Are they perfect ?".

## Problem definition
We are building a minimal version of self driving car using a front camera view. Our CNN end to end model predicts the steering angles for a smooth ride. Predicting steering angle can be considered as a regression problem.

## Dataset

Refer this: https://github.com/SullyChen/Autopilot-TensorFlow

There are total 45406 images in the dataset along with their steering angles for training.

## Train and Test split
We will split the dataset in a ratio of 80:20 sequentially.

## Objective
Our objective is to predict the correct steering angle for self driving car. Here our loss is MSE ( mean squared loss ) and we will try to reduce this to as low as possible.

## Observation from the pdf of train and test "y" values

- Train y's and Test y's are not completely overlapping.
- There is a some difference between train and test data
- I oberserved that, most often the steering angle is 0 radian, as most roads are leading straight.
- Most of the values lie between -2 to +2.
- This observation is in radians.
- I build a very simple base line model.

## Base Line Model

- Test_MSE(MEAN) : 0.191127
- Test_MSE(ZERO) : 0.190891
- Observation :
  - Ideal Mean Square Value = 0, as most of values are close to 0 radians.
  - So, any model i train should have MSE on test data less than 0.19.
  
## Deep Learning Model( For Regression )

- We take single image --> predict an angle
- So here we are not using sequential information( not taking sequence of images )
- We can have ConvNet based regression( just the loss will change ).

## Architecture of the model

<img src= "https://github.com/Swetadas-1718/Self-Driving-Car-End-to-End-Deep-Learning-model/blob/main/cnn-architecture-624x890.png">

- The first layer of the network performs image normalization which helps the GPU processing to be accelerated.
- The convolutional layers are designed to perform feature extraction, and are chosen empirically through a series of experiments by nvidia.
- We then use strided convolutions in the first three convolutional layers with a 2×2 stride and a 5×5 kernel, and a non-strided convolution with a 3×3 kernel size in the final two convolutional layers.
- We follow the five convolutional layers with three fully connected layers, leading to a final output control value which is inverse of tan.

## Libraries

- Tensorflow
- OpenCV

## Author
- Swetapadma Das - Complete Work
