---
layout: post
title:      "The Dangers of Under-fitting and Over-fitting"
date:       2020-05-01 16:21:00 +0000
permalink:  the_dangers_of_under-fitting_and_over-fitting
---


Machine learning models are an incredible powerful and useful tool for data scientists. When building a model, it is important to remember that with predictions comes prediction errors. These errors are due to a combination of bias and variance which have a trade-off relationship. Understanding these fundamentals is just the first step to building an accurate model and avoiding the pitfalls of under-fitting and over-fitting!
Back to basics!
The core understanding of supervised machine learning is that we are approximating a target function(f) that maps input variables (X) to an output variable (Y). The relationship is mathematically expressed as:

Where e represents the total error. The total error can actually be further split into three parts:

the square of the bias of the learning method
the variance of the learning method
the irreducible error
We will go over each of these terms in detail. As we go into a deeper review of bias and variance, it is important to remember that the data we collect and analyze is just a sample, thus is incomplete and has noise. How the model makes generalizations to the training data is important in determining how the model will react to new data.
So what is bias?
Bias, or bias error, can be defined as the difference between the expected prediction of our model and the correct value which we are trying to predict. High bias can cause our model to miss significant relations between our features (X) and target outputs (Y) so it cannot learn the training data or generalize to new data. This is also known as under-fitting. Under-fitted models are forced to make a lot of assumptions which can cause inaccurate predictions.
Now that we have a basic understanding of the concept of bias…
What is variance?
Variance is the variability of a model prediction for a given data point. It is the error from sensitivity to small fluctuations in the training data. When there is high variance, this can cause random noise (e) to be introduced into the training data rather than the intended outputs (Y). High variance is also known as over-fitting data. When the data is over-fitted, the model essentially learns the training data too well and therefore cannot generalize to new data.
The last error term is the irreducible error. Irreducible error is essentially the amount of noise from factors outside of our control and cannot be removed.
We can identify under-fitting and over-fitting by looking at the line of best fit. In the left graph below, we can see that the line is simple and does not follow many of the data points, thus showing high bias. The right graph below shows a line that follows almost every data point, even ones that may be noise or outliers, showing high variance. Our goal is to find a balance between these two extremes so that the majority of data points are explained with an appropriate amount of noise.

https://medium.com/greyatom/what-is-underfitting-and-overfitting-in-machine-learning-and-how-to-deal-with-it-6803a989c76
The relationship between bias and variance can also be easily visualized using a target example.

The center of the target represents a model with perfectly accurate predictions. Parametric or linear machine learning models (such as Linear Regression and Logistic Regression) often have a high bias but a low variance (bottom left). Non-parametric or non-linear machine learning algorithms (such as Decision Trees and k-Nearest Neighbors) often have low bias but high variance (top right). Our goal is to create a model with low bias and low variance (top left) where the error is least.
The Bias-Variance Trade-off
The aim is to get the model to generalize and classify new inputs appropriately. We can reduce the variance by having a more complex model, but then we risk having more bias. Inversely, if we have a model with lower complexity, the bias may be low, but then we risk having higher variance. Bias has a negative slope in response to model complexity while variance has a positive slope.

https://djsaunde.wordpress.com/2017/07/17/the-bias-variance-tradeoff/
We need to find a “sweet-spot” which compromises between bias and variance so there is enough noise in the training data to allow for generalization without classifying the training data inaccurately. This will allow us to find the model with the “best fit.”
How can we prevent Underfitting and Overfitting?
For Underfitting:
Make sure there is enough training data so that the error/cost function (e.g. MSE or SSE) is sufficiently minimized
For Overfitting:
Limit the number of features or adjustable parameters in the model. As the number of features increases, the complexity of the model also increases, thus creating a higher chance of overfitting.
Shorten the training so the model doesn’t “over-learn” the training data.
Add some form of regularization term to the error/cost function to encourage smoother network mappings (Ridge or Lasso regression are commonly used techniques)
Cross-Validation to minimize mean square error
Thank you for reading!
References:
https://machinelearningmastery.com/overfitting-and-underfitting-with-machine-learning-algorithms/
http://scott.fortmann-roe.com/docs/BiasVariance.html
https://elitedatascience.com/overfitting-in-machine-learning
https://medium.com/greyatom/what-is-underfitting-and-overfitting-in-machine-learning-and-how-to-deal-with-it-6803a989c76
https://towardsdatascience.com/understanding-the-bias-variance-tradeoff-165e6942b229
http://www.cs.bham.ac.uk/~jxb/INC/l9.pdf
https://djsaunde.wordpress.com/2017/07/17/the-bias-variance-tradeoff/
https://www.geeksforgeeks.org/underfitting-and-overfitting-in-machine-learning/
