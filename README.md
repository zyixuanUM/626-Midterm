# 626-Midterm

## Experiment design and data collection

A group of volunteers, aged between 19 and 48, are recruited to participate in the experiment. They performed a protocol consisting of six activities: three static postures (standing, sitting, lying) and three dynamic activities (walking, walking downstairs, and walking upstairs). The experiment also recorded postural transitions that occurred between the static postures. These are: stand-to-sit, sit-to-stand, sit-to-lie, lie-to-sit, stand-to-lie, and lie-to-stand. All participants wore a smart device on the waist during the experiment. It captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz using the embedded accelerometer and gyroscope of the device. In this context, the activities are considered outcomes, and the signals measured by the smart device are considered features. 

## Data files 

There are two data files in this code. One is the "training data", used to check whether the model fits well and compute and plot the accuracy by the pROC package to see the difference between them. Another data file is the "test data", for which to create the submitted files and check the accuracy through the leaderboard, then try the best to improve it. 

## Methods
In this project's classifier, we use several methods to build classifiers, such as logistic regression, GLM with elastic net, lasso regression, ridge regression, linear discriminant analysis, SVM with linear kernel or radial kernel, neural network, adaboost, bagging, randomforest, etc. Through these models, use different packages and different parameters to adjust the results, in order to get the best answer. One of the methods and their accuracy are as follows. Most of the functions come from the caret package and other required packages.
<br/>

Split the training data into training and testing data by using sample() function, then use the training to build the model and use the testing to predict the model by using predict() function and compute the accuracy.

## 1. Binary Classifier
Build a binary classifier to classify the activity of each time window into static (0) and dynamic (1). For this task, consider postural transitions as static (0).
<br/>

a. Logistic regression 
<br/>
Using glm() function in the base.
<br/>
Accuracy: 100%
<br/>
b.  GLM with elastic net
<br/>
library(glmnet) with 0 < alpha <1
<br/>
Accuracy: 99.01%
<br/>
c. Lasso regression (alpha = 1)
<br/>
Accuracy: 100%
<br/>
d. Ridge regression (alpha = 0)
<br/>
Accuracy: 99.91%
<br/>
e. Linear Discriminant Analysis
<br/>
library(MASS)
<br/>
Accuracy: 100%
<br/>
f. SVM
<br/>
SVM with linear kernel: 100%
<br/>
SVM with radial kernel: 100%
<br/>
g. Single Hidden-layer Neural Network
<br/>
library(neuralnet)
<br/>
Accuracy: 100%
<br/>
i. Adaboost
<br/>
Accuracy:  99.91%
<br/>

## 2. Multi-class Classifier
<br/>
Build a refined multi-class classifier to classify walking (1), walking_upstairs (2), walking_downstairs (3), sitting (4), standing (5), lying (6), and static postural transition (7)

<br/>

a. Bagging
<br/>
library(adabag)
<br/>
Accuracy: 88.37%
<br/>
b. Adaboost
<br/>
Accuracy: 96.78%
<br/>
c. SVM
<br/>
SVM with linear kernel: 98.54%
<br/>
SVM with radial kernel: 97.47%
<br/>
d. Randomforest
<br/>
library(randomForest)
<br/>
Accuracy: 98.07%
<br/>
e. BP neural network
<br/>
Accuracy: 96.14%
<br/>
f. LDA
<br/>
Accuracy: 98.07%
<br/>

The summarized tables and ROC plots are in the code.

## Comments on results and further improvement the classification accuracy
The result of each classification from the training data can be seen in table() or confusionMatrix().
<br/>
For the binary classifier, there are several methods that get 100% accuracy, so we don't need to improve it. Choose the SVM with linear kernel as the final algorithm for it has 100% accuracy with the fastest system time.
<br/>

However, for the multi-class classifier, there is still space for us to improve it. As I missed some opportunities and submitted a wrong submitted file, I don't have any effective accuracy of testing data here. But I can provide some further improvements as follows. Also, choose the SVM with linear kernel as the final algorithm for it has one of the highest accuracies with the fastest system time.
<br/>

Specifically, we can try the function caretStack(all.models, ...) in the R package "caretEnsemble". This function is used to find a good linear combination of several classification or regression models, using either linear regression, elastic net regression, or greedy optimization.
<br/>

We can first use the caretList to build a list of models, or directly build the models by train(x, ...), then make a linear regression ensemble by the code caretStack(all.models, method='glm', trControl), or combine with the randomforest like caretStack(all.models, method='rf', trControl). 

<br/>
This method of combining several predictive models via stacking may have better accuracy on the testing data.




