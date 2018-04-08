# Final Project Bletchley 02
In the present social environment privacy and security are becoming more prominent topics, especially considering the large amount of investments into IT and new forms of computing, such as quantum computing and artificial intelligence. It is of paramount importance that new systems become more tied to the users' biometric features.

## Introduction
The current method through which systems identify and classify users is by inputting user's pictures, often normalized, into a convolutional network. However, these methods are often computationally expensive, thus providing for unfeasible widespread adoption into current security infrastructures. Ideally, PIN-codes and passwords should be replaced by a biometric security which could be implemented for example at the payment terminal of your nearest supermarket.

## Hypothesis
Our hypothesis is centred around the idea that systems could reduce computational expenses and still classify users biometrically with a reasonable accuracy. Our approach is to reduce the input size to a chain of computations by eliminating the dependency on full images to a set of coordinates which represent the facial landmarks of a human. 

## Approach
The present approach utilizes data collected from [The Open University of Israel](https://www.openu.ac.il/home/hassner/Adience/data.html) as the training data for the model. Additionally, OpenCV is used in order to identify facial landmarks (coordinates) based on the [library's pre-trained model](https://github.com/AKSHAYUBHAT/TensorFace/blob/master/openface/models/dlib/shape_predictor_68_face_landmarks.dat), Imutils is used to normalize images, and DLib is used to predict the facial features of a given input. Subsequently, the landmarks are used as inputs for the predictive models which classify users by age groups and gender.

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

### Data Processing
Our initial step in cleaning the data in the correct form was by removing all NaN's and NONE's from the description data (Master_text_folder.txt). Secondly, the facial ID's and image ID's are merged in order to match the image ID from the training images. Afterwards, all redundant information is removed from the target data, for example tilt angles of a face. Subsequently, all the images are loaded in the correct format by OpenCV, Imutils is used to process the images, and the facial landmarks are located through DLib. When locating facial landmarks batches of 100 images are used to reduce system strain on active memory and back-up progress made. Lastly, the targets are one-hot encoded in order to feed this data to the predictive models.

The input data of the neural network is a flattened array of 68 landmark coordinates, which in results in a 1-dimensional array of 136 entries. 

## Results
In order to substantiate our findings several models are constructed with differenct characteristics. 

### Gender Classification
From the analysis it is evident that current input data does not contain sufficient information to outperform random guessing. 
Multiple models are built by tweaking parameters such as dropout, quantity of layers and size of layers, however, at best the model performs 52.90%, which is insignificantly better than random guessing. 

### Age Classification







