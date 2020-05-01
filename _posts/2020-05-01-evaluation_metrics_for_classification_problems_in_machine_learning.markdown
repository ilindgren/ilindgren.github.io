---
layout: post
title:      "Evaluation Metrics for Classification Problems in Machine Learning"
date:       2020-05-01 16:21:49 +0000
permalink:  evaluation_metrics_for_classification_problems_in_machine_learning
---


Knowing how to create a machine learning model is a big step towards becoming a successful Data Scientist, but the first model is rarely ever the ‘best’ model. Evaluating the quality of our machine learning model is extremely important for continuing to improve our model until it performs as best as it can. For classification problems, evaluation metrics compare the expected class label to the predicted class label or interpret the predicted probabilities for the class labels. Classification problems are common and have many real world applications such as detecting spam emails, targeted marketing, fraud detection or assessing if a patient is at high risk for developing a particular disease diagnosis. In this blog post we will review some of the different types of classification evaluation metrics for these types of problems.
1. Confusion Matrix
2. Precision
3. Recall
4. Accuracy
5. F1-Score
6. AUC ROC
Confusion Matrix
A confusion matrix is a table with four different combinations of predicted and actual values. This is a great way to visualize the different outputs and to calculate the Precision, Recall, Accuracy, and F-1 Score as well as the AUC-ROC. We will go over each of these in more detail later in this blog. First, let’s break down the TP, FP, FN, and TN in a confusion matrix.

Confusion Matrix
True Positives (TP) : The number of times our model predicted YES and the actual output was also YES.
True Negatives (TN): The number of times our model predicted NO and the actual output was NO.
False Positives (FP): The number of times our model predicted YES and the actual output was NO. This is known as a Type 1 Error.
False Negatives (FN): The number of times our model predicted NO and the actual output was YES. This is known as a Type 2 Error.
Precision —
Precision can be described as the fraction of relevant instances among the retrieved instances. This answers the question “ What proportion of positive identifications was actually correct?” The formula is as follows:

In the terms of our confusion matrix, the equation can be represented as:

Precision expresses the proportion of the data points our model says was relevant actually were relevant.
Recall —
Recall, also known as sensitivity. This answers the question “What proportion of actual positives was classified correctly?” This can be represented by the following equation:

In our confusion matrix, it would be represented by:

Recall expresses which instances are relevant in a data set. It is important to examine both the Precision AND Recall when evaluating a model because they often have an inverse relationship. When precision increases, recall tends to decrease and vice versa.
Accuracy —
Accuracy is determining out of all the classifications, how many did we classify correctly? This can be represented mathematically as:

Using our confusion matrix terms, this equation is written as:

We want the accuracy score to be as high as possible. It is important to note that accuracy may not always be the best metric to use, especially in cases of a class-imbalanced data set. This is when the distribution of data is not equal across all classes.
For example, let’s say that we are looking to build a model to help diagnose people with brain cancer. If our model just classified every single person as not having brain cancer, we would be correct the overwhelming majority of the time, but the cost of someone not being diagnosed when they do, in fact, have brain cancer is devastating. Depending on the industry, these costs may outweigh the accuracy of the model. In imbalanced cases like these, it is better to use the F1-Score instead.
F1-Score —
The F1 Score is a function of precision and recall. It is used to find the correct balance between the two metrics. It determines how many instances your model classifies correctly without missing a significant number of instances. This score can be represented by the following equation:

Having an imbalance between precision and recall, such as a high precision and low recall, can give you an extremely accurate model, but classifies difficult data incorrectly. We want the F1 Score to be as high as possible for the best performance of our model.
AUC (Area Under Curve) ROC(Receiver Operating Characteristics) Curve
The AUC ROC curve is a graph which shows the performance of a classification model at all thresholds. ROC is a probability curve and AUC represents degree of separability. ROC plots the following parameters:
True Positive Rate (TPR), also known as recall or sensitivity, which was explained in the previous section.

False Positive Rate (FPR), also known as specificity, the ratio of the false positive predictions compared to all values that are actually negative.

Both the RPR and FPR are within the range [0, 1]. The curve is the FPR vs TPR at different points in the range [0, 1]. The best performing classification models will have a curve similar to the green line in the graph below. The green line has the largest Area Under the Curve. The higher the AUC, the better your model is performing. A classifier with only 50–50 accuracy is realistically no better than randomly guessing, which makes the model worthless (red line).

I hope that this blog helps clarify the different metrics used to evaluate the performance of classification models in machine learning!
If there is a takeaway from this blog post, make sure to remember that there is no evaluation metric that works for all problems. It depends on the industry and what kind of data set you have to work with.
Thanks for reading!
References:
https://developers.google.com/machine-learning/crash-course/classification/true-false-positive-negative
https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62
http://gim.unmc.edu/dxtests/ROC3.htm
https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c
https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9
