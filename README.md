# 626-Midterm

## Experiment design and data collection

A group of volunteers, aged between 19 and 48, are recruited to participate in the experiment. They performed a protocol consisting of six activities: three static postures (standing, sitting, lying) and three dynamic activities (walking, walking downstairs, and walking upstairs). The experiment also recorded postural transitions that occurred between the static postures. These are: stand-to-sit, sit-to-stand, sit-to-lie, lie-to-sit, stand-to-lie, and lie-to-stand. All participants wore a smart device on the waist during the experiment. It captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz using the embedded accelerometer and gyroscope of the device. In this context, the activities are considered outcomes, and the signals measured by the smart device are considered features. 

## Data files 

There are two data files in this code. One is the "training data", used the check whether the model fits well and compute and plot the accuracy to see the difference between them. Another data file is the "test data", for which to create the submitted files and check the accuracy through the leaderboard, then try the best to improve it. 

## Methods
In this projects' classifier, we use several methods to build classifiers, such as logistic regression, GLM with elastic net, lasso regression, ridge regression, linear discriminant analysis, SVM with linear kernel or radial kernel, neural network, adaboost, bagging, randomforest, etc. Through these models, use different packages and diffrent parameters to adjust the results, in order to get the best answer. One of the method and accuracy of them are as follows.

## 1. Binary Classifier
<br/>
a. Logistic regression 
<br/>
Accuracy: 100%
<br/>
b.  GLM with elastic net
<br/>
Accuracy: 99.01%
<br/>
c. Lasso regression
<br/>
Accuracy: 100%
<br/>
d. Ridge regression
<br/>
Accuracy: 99.91%
<br/>
e. Linear Discriminant Analysis
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
Accuracy: 100%
<br/>
i. Adaboost
<br/>
Accuracy:  99.91%
<br/>

## 2. Multi-class Classifier
<br/>
a. Bagging
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

## Comments on results and further improvement the classification accuracy.
For the binary classifier, there are several methods get the 100% accuracy, so we don't need to improve it.
<br/>

However, for the multi-class classifier, there are still space for us to improve it. As I missing some opportunities and submitted a wrong submitted file, I don't have any effective accuracy of testing data here. But I can provide some further improvement as follows.
<br/>

Specificly, we can try the function caretStack(all.models, ...) in the R package "caretEnsemble". This function is used to find a good linear combination of several classification or regression models, using either linear regression, elastic net regression, or greedy optimization.
<br/>

We can first use the caretList to build a list of models, or directly build the models by train(x, ...), then make a linear regression ensemble by the code caretStack(all.models, method='glm', trControl), or combine with the randomforest like caretStack(all.models, method='rf', trControl). 

<br/>
This method of combining several predictive models via stacking may have a better accuracy on the testing data.




