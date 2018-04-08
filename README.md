# Final Project Bletchley 02
In the present social environment privacy and security are becoming more prominent topics, especially considering the large amount of investmenmts into IT and new forms of computing, such as quantum computing and artificial intelligence. It is of paramount importance that new systems become more tied to the users' biological features.

## Introduction
The current method through which systems identify, classify users nowadays is by inputting user's pictures, often normalized, into a convolutional network. However, these methods are often computationally expensive, thus providing for unfeasible widespread adoption into current security infrastructures. Ideally, PIN-codes and passwords should be replaced by a biometric security which could be implemented for example at the payment terminal of your nearest supermarket.

## Hypothesis
Our hypothesis is centred around the idea that systems could reduce computational expenses and still classify users biometrically with a reasonable accuracy. Our approach is to reduce the input size to a chain of computations by eliminating the dependency on full images to a set of coordinates which represent the facial landmarks of a human. 

## Approach
The presen approach utilizes data collected from [The Open University of Israel](https://www.openu.ac.il/home/hassner/Adience/data.html) as the training data for the model. Additionally, OpenCV is used in order to identify facial landmarks (coordinates) based on the [libraries pre-trained model](https://github.com/AKSHAYUBHAT/TensorFace/blob/master/openface/models/dlib/shape_predictor_68_face_landmarks.dat). Subsequently, the landmarks are used as inputs for the predictive models which classify users by age groups and gender.

### Classes
In order to derive proper age classes we considered the distribution of observations in proportion to the sample. The classes of the present model are described below:

| Category     | Age Range |
|--------------|-----------|
| Toddler      | 0 => 3    |
| Young Child  | 4 => 6    |
| Child        | 7 => 14   |
| Teenager     | 15 => 20  |
| Adolescent   | 21 => 24  |
| Young Adult  | 25 => 32  |
| Adult        | 33 => 48  |
| Abraham      | 49 => 59  |
| Elderly      | 60+       |

![Alt text](AgeDistribution.png?raw=true "Age Distribution")

## Results

