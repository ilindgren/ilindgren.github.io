---
layout: post
title:      "Dealing with Highly Dimensional Data using Principal Component Analysis "
date:       2020-05-01 16:50:48 +0000
permalink:  dealing_with_highly_dimensional_data_using_principal_component_analysis
---


A beginners guide to PCA and how to implement it using sklearn (with code!)

A common issue for data scientists when creating an algorithm is having too many variables. Naturally, you would think that adding more information would only make your model better, but with every feature you add comes another dimension. As humans, we can only visualize things in 2-dimensions or 3-dimensions. For data, this rule does not apply! Data can have an infinite amount of dimensions, but this is where the curse of dimensionality comes into play.
The Curse of Dimensionality is a paradox that data scientists face quite frequently. You want to use more information in order to improve the accuracy of your machine learning model, but the more features you add, the number of dimensions (n) increases. As the dimensionality of the feature space increases, the number of configurations increases exponentially, and in turn, the number of configurations covered by observation decreases.
Our ultimate goal as data scientists is to create simple models that can run quickly and are easy to explain. When we have a large amount of features, our model becomes more complex and the explainability decreases. To deal with these complicated datasets, Principal Component Analysis is an ideal method to reduce the dimensions of your data.
What is Principal Component Analysis and what is it used for?
Principal Component Analysis, or more commonly known as PCA, is a way to reduce the number of variables while maintaining the majority of the important information. It transforms a number of variables that may be correlated into a smaller number of uncorrelated variables, known as principal components. The principal components are linear combinations of the original variables weighted by their variances (or eigenvalues) in a particular orthogonal dimension. The main objective of PCA is to simplify your model features into fewer components to help visualize patterns in your data and to help your model run faster. Using PCA also reduces the chance of overfitting your model by eliminating features with high correlation.
It is important to note that you should only apply PCA to continuous variables, not categorical. Although technically you can use PCA on one-hot encoded or otherwise binary data, it does not work very well. This is because PCA is designed to minimize variance (squared deviations) which is not very meaningful when performed on binary variables. If you have mixed data, alternative methods like MCA may work better.
So how can you tell how much information is retained in your PCA?
We use Explained Variance Ratio as a metric to evaluate the usefulness of your principal components and to choose how many components to use in your model. The explained variance ratio is the percentage of variance that is attributed by each of the selected components. Ideally, you would choose the number of components to include in your model by adding the explained variance ratio of each component until you reach a total of around 0.8 or 80% to avoid overfitting.
Luckily for us, sklearn makes it easy to get the explained variance ratio through their .explained_variance_ratio_ parameter! We will use this in our coding example.

Photo by NASA on Unsplash
Example PCA using Sklearn
First, let’s load the iris dataset for our code-a-long example. The iris dataset is a famous dataset contains measurements for 150 iris flowers from three different species.
from sklearn import datasets
import pandas as pd
 
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
df['Target'] = iris.get('target')
df.head()

2. Next, we will separate all columns in the ‘features’ list to a variable ‘X’ and the ‘target’ variable to ‘y’.
# Create features and target datasets
features = ['sepal length (cm)', 'sepal width (cm)', 'petal length (cm)', 'petal width (cm)']
X = df[features].values
y = df['Target'].values
3. We have to standardize the data before implementing PCA. This is absolutely necessary because PCA calculates a new projection of our data on a new axis using the standard deviation of our data. PCA gives more weight to variables that have higher variances than variables with low variances, so it is important to normalize the data on the same scale to get a reasonable covariance.
from sklearn.preprocessing import StandardScaler

# Standardize the features
X = StandardScaler().fit_transform(X)

# Preview X
pd.DataFrame(data=X, columns=features).head()

4. Now, we will import PCA using sklearn and project our original data, which has 4 dimensions, into 2 dimensions. In this part, sklearn creates a covariance matrix to calculate eigenvectors (principal components) and their corresponding eigenvalues. The eigenvectors determine the directions of the new feature space and the eigenvalues determine the magnitude, or variance, of the data along the new feature axes.
# Import PCA from sklearn
from sklearn.decomposition import PCA

# Instantiate PCA
pca = PCA(n_components=2)

# Fit PCA to features
principalComponents = pca.fit_transform(X)
5. To better visualize the principal components, let’s pair them with the target (flower type) associated with the particular observation in a pandas dataframe.
# Create a new dataset from principal components 
df = pd.DataFrame(data = principalComponents, 
                  columns = ['PC1', 'PC2'])

target = pd.Series(iris['target'], name='target')

result_df = pd.concat([df, target], axis=1)
result_df.head(5)

6. Now we can visualize the principal components according to the class distribution using the target data. This code creates a scatterplot from the principal components while color coding the examples by flower type each example is classified as.
# Visualize Principal Components with a scatter plot
fig = plt.figure(figsize = (12,10))
ax = fig.add_subplot(1,1,1) 
ax.set_xlabel('First Principal Component ', fontsize = 15)
ax.set_ylabel('Second Principal Component ', fontsize = 15)
ax.set_title('Principal Component Analysis (2PCs) for Iris Dataset', fontsize = 20)

targets = [0, 1, 2]
colors = ['r', 'g', 'b']
for target, color in zip(targets, colors):
    indicesToKeep = iris['target'] == target
    ax.scatter(result_df.loc[indicesToKeep, 'PC1'], 
               result_df.loc[indicesToKeep, 'PC2'], 
               c = color, 
               s = 50)
ax.legend(targets)
ax.grid()

7. We can see that the three classes are pretty distinct and fairly separable. We can conclude that the compressed data representation is most likely sufficient for a classification model. We can compare the variance in the overall dataset to what was captured from our two primary components using .explained_variance_ratio_.
# Calculate the variance explained by priciple components
print('Variance of each component:', pca.explained_variance_ratio_)
print('\n Total Variance Explained:', round(sum(list(pca.explained_variance_ratio_))*100, 2)

We can see that our first two principal components explain the majority of the variance in this dataset (95.81%)! This is an indication of the total information represented compared to the original data.
Summary
The key takeaways from this article are:
PCA is a commonly used dimension reduction technique.
The goal of PCA is to simply your model features into fewer, uncorrelated features to help visualize patterns in your data and help it run faster.
Only apply PCA to continuous data.
Make sure your data is normalized before applying PCA!!
***
Thanks for the read!
If you like my blog posts, you can support me by following my Medium here. You can also connect with me via my LinkedIn here.
***
References:
https://towardsdatascience.com/a-one-stop-shop-for-principal-component-analysis-5582fb7e0a9c
https://deepai.org/machine-learning-glossary-and-terms/curse-of-dimensionality
https://elitedatascience.com/overfitting-in-machine-learning
https://www.geeksforgeeks.org/principal-component-analysis-with-python/
https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html
https://www.researchgate.net/profile/Dominique_Valentin/publication/239542271_Multiple_Correspondence_Analysis/links/54a979900cf256bf8bb95c95.pdf
https://www.visiondummy.com/2014/03/eigenvalues-eigenvectors/
https://sebastianraschka.com/Articles/2015_pca_in_3_steps.html
https://etav.github.io/python/scikit_pca.html
Flatiron Data Science Curriculum Section 37
