## Table Of Contents
####  a. Project Overview
#### b. Project Motivation/Goal
#### c. Algorithms
#### d. Dataset
#### e. Challenges
#### f. Conclusion
#### g. Credits 

## Project Overview

Anomaly detection helps in the  early detection of critical outliers in a system. Based on the context, these outliers can be detrimental and result in loss of resources, and time through errors, fraud, manipulation of stocks, and other such malicious activities. Outliers can also be beneficial for example in investing, and arbitrage. Business decisions that leverage anomaly detection, which used to require intense human resource and capacity can now be completed in a short time through versatile models and automation. In the banking industry, credit card fraud detection using machine learning is not just a trend but a necessity for them to put proactive monitoring and fraud prevention mechanisms in place. Machine learning is helping these institutions to reduce time-consuming manual reviews, costly chargebacks and fees, and denials of legitimate transactions.

## Project Motivation/Goal

I have een part of Finance industry for last 6 years and have a high domain knowledge on working of Credit Crads and Loans. For essential working of these instruments, Fraud detection is a necessity. Therefore , i tried my hands on this very important aspect of Finance Industry

## Algorithm

The project pipeline can be briefly summarized in the following four steps:
•	Data Understanding: Here, we need to load the data and understand the features present in it. This would help us choose the features that we will need for our final model.
•	Exploratory data analytics (EDA)/Data Preprocessing: Normally, in this step, we need to perform univariate and bivariate analyses of the data, followed by feature transformations, if necessary. For the current data set, because Gaussian variables are used, we do not need to perform Z-scaling. However, we can check if there is any skewness in the data and try to mitigate it, as it might cause problems during the model-building phase.

Well, some of the data points in a skewed distribution towards the tail may act as outliers for the machine learning models which are sensitive to outliers and hence that may cause a problem. Also, if the values of any independent feature are skewed, depending on the model, skewness may affect model assumptions or may impair the interpretation of feature importance. 
a.	As we observed, the data shows a high class imbalance. Over 2,00,000 cases are mapped to 0, but hardly 500 cases are mapped to 1. Any machine learning algorithm would work well when there is equal representation of each of the classes. However, in this case, no matter which model you build, the underlying algorithm will learn more about the non-fraudulent cases rather than the fraudulent ones. Therefore, the loss function optimization will be heavily biased to the former type of data. This is known as the ‘minority class problem’.
Now, we can use certain methods to mitigate this problem. They are as follows:
Undersampling: In this method, we have the choice of selecting fewer data points from the majority class for your model-building process. In case we have only 500 data points in the minority class, we will also have to take 500 data points from the majority class; this will make the classes somewhat balanced. However, in practice, this method is not effective because we will lose over 99% of the original data.
Oversampling: Using this method, we can assign weights to randomly chosen data points from the minority class. This way, the occurrence of each data point will be multiplied by the assigned weight, and the machine learning algorithm will now be able to focus on this class while optimizing the loss function. However, this method does not add any new information and may even exaggerate the existing information quite a bit.
Synthetic Minority Over-Sampling Technique (SMOTE): In this process, you can generate new data points, which lie vectorially between two data points that belong to the minority class. These data points are randomly chosen and then assigned to the minority class. This method uses K-nearest neighbors to create random synthetic samples.
ADAptive SYNthetic (ADASYN): This is like SMOTE, with a minor change in the generation of synthetic sample points for minority data points. For a particular data point, the number of synthetic samples that it will add will have a density distribution, whereas, for SMOTE, the distribution will be uniform. The aim here is to create synthetic data for minority examples that are harder to learn, rather than the easier ones.

•	Model Selection: K-nearest neighbour is a simple, supervised machine learning algorithm used for both classification and regression tasks. It performs these tasks by identifying the neighbours that are nearest to a data point. For classification tasks, it takes the majority vote and for regression tasks, it takes the average value from the neighbours. 
The k in KNN specifies the number of neighbours that the algorithm should focus on. For example, if k = 3, then, for a particular test data, the algorithm observes the three nearest neighbours and takes the majority vote from them. Depending on the majority of the classes from the three nearby points, the algorithm classifies the test data.
XGBoost stands for ‘eXtreme Gradient Boosting'. It is a decision-tree-based ensemble ML algorithm that uses a gradient boosting framework. It is a highly effective and widely used machine learning method and has applications for structured as well as unstructured data.
XGBoost is an extended version of gradient boosting, where it uses more accurate approximations to tune the model and find the best fit. The added features here are:
o	Optimization through second-order derivatives: The second-order partial derivative of the loss function provides a more detailed picture of the gradient direction. Thus, you can easily find the global minima in comparison to doing it using the first-order derivative.
o	Advanced regularization (Lasso and Ridge) to penalize the model based on the number of trees and the depth of the model: Higher the number of trees, higher will be the number of nodes in each tree and greater will be the penalty attached to it. Whenever you need to add a new node, you will need to check for a minimum reduction in the loss. If there is no significant reduction, you will not create the node.
o	Fast learning through parallel and distributed computing enables quicker model exploration.
Because of parallel processing (speed) and model performance, we can say that XGBoost is gradient boosting on steroids.

The thumb rule is that whenever we have structured data, we can use high-performing models such as random forest/XGBoost.
•	Hyperparameter Tuning: This is the final step at which you can try different models and fine-tune their hyperparameters until you get the desired level of performance.
Normally, in the machine learning process, we divide the data into train, test and validation sets to evaluate the model’s performance. However, the test and validation sets may cause variance to increase when the performance of a particular test set might differ from that of another test set.

## Challenges

This dataset is used to detect the credit card fraud detection. This is a classification problem. This is an imbalanced dataset based on target variable. So In this Project, I will use encoding and decording techniques to balanced dataset.

These are various techniques as follows -

i.   Cross Validation Like KFOLD and Hyperparameter Tuning (Logistics Regression )
ii.  Ensemble Technique - Random Forest
iii. Under Sampling
iv.  Over Sampling
v.   SMOTETomek
vi.  Ensemple Technique - EasyEnsembleClassifier

## Dataset

The data set includes credit card transactions made by European cardholders over a period of two days in September 2013. Out of a total of 2,84,807 transactions, 492 were fraudulent. This data set is highly unbalanced, with the positive class (frauds) accounting for 0.172% of the total transactions. The data set has also been modified with Principal Component Analysis (PCA) to maintain confidentiality. Apart from ‘time’ and ‘amount’, all the other features (V1, V2, V3, up to V28) are the principal components obtained using PCA. The feature 'time' contains the seconds elapsed between the first transaction in the data set and the subsequent transactions. The feature 'amount' is the transaction amount. The feature 'class' represents class labelling, and it takes the value 1 in cases of fraud and 0 in others.
The distribution plots of the variables were Gaussian, which might indicate the effects of transformations that had already occurred on the data set.
The data set that was used during this project was obtained from Kaggle  ( https://www.kaggle.com/mlg-ulb/creditcardfraud ). It contains thousands of individual transactions that took place over a course of two days and their respective labels.


