---
layout: post
title:      "Back to Basics: Hypothesis Testing"
date:       2020-05-01 16:19:55 +0000
permalink:  back_to_basics_hypothesis_testing
---


What is hypothesis testing? Why is it so important?
Hypothesis testing is at the core of every single experiment ever done. It is the process of creating a clear and testable question, analyzing the relevant data, and forming a conclusion which answers our original question.

Figure 1: Steps of the Scientific Method
A hypothesis is commonly referred to as an ‘educated guess’ or a possible explanation for an observed phenomena. For testing, we form two hypotheses: the alternative hypothesis and the null hypothesis. The null hypothesis is a statement reflecting no observed effect in our experiment while the alternative hypothesis directly contradicts the null.
These two can be confusing at times, so specific language is used in order to prevent drawing false conclusions. The objective of our testing is to prove evidence against the null hypothesis. If we obtain a p-value less than our significance level (alpha), we can reject our null hypothesis. If we obtain a p-value greater than our alpha, then we fail to reject our null hypothesis. The reason we say “fail to reject” instead of “accept” our null hypothesis is because the test only assesses whether available evidence exists to reject the null hypothesis. In other words, if we fail to reject the null, there is not enough evidence to disprove the null.

New scientist trying to decipher hypothesis testing language
Say I’m a scientist who is developing a drug to treat arthritis. I give 100 randomly selected patients with arthritis the drug (treatment group) and another 100 randomly selected patients with arthritis a placebo (control group). I observe after two weeks of treatment that 60% of patients who took the drug reported noticeable improvements to their symptoms while only 5% of patients who took the placebo reported improvements.
So what does this data mean? How do we know if the improvements occurred due to the drug or purely by chance? This is where we begin our hypothesis testing process!
Steps for Hypothesis Testing
Define the Null and Alternative hypotheses
Define the Acceptance Criteria (usually p<0.05)
Check Assumptions
Choose and execute a statistical test based on the assumptions
Draw conclusions
For this example, the null and alternative hypotheses would be written as:
Null Hypothesis (H0): The observations are due to pure chance. The drug has no effect on patients with arthritis.
Alternative Hypothesis (H1): The drug improves the symptoms of the patients with arthritis.
So the null hypothesis we are trying to disprove with our testing in this example states that there is no difference between patients who received the drug and patients who didn’t receive the drug. The p-value we are testing for is the probability that the data would be at least as extreme as those observed.

https://upload.wikimedia.org/wikipedia/en/0/00/P-value_Graph.png
In reality, there are four different possible outcomes to our testing.
The decision to reject the null hypothesis could be correct (i.e. there is actually a difference between the treatment and the control group).
The decision to reject the null hypothesis could be incorrect, it is known as Type I error (i.e. conclude the null is false and there actually is a difference between the treatment group and the control group).
The decision to retain the null hypothesis could be correct (i.e. there is no difference between the treatment group and the control group).
The decision to retain the null hypothesis could be incorrect, it is know as Type II error (i.e. conclude it is not false and there actually is no difference between the treatment and control group).

https://www.sagepub.com/sites/default/files/upm-binaries/43443_7.pdf
We want to minimize the chances of a type I or type II error occurring, so it is important to check a few assumptions before deciding which statistical test to perform. These assumptions, if violated, could dictate if the results of the analysis can be misleading.
Assumptions to check:
1. Normality - the data has a normal (or at least symmetric) distribution. We can check this using visualizations such as histograms or tests like the Shapiro-Wilk test.
2. Homogeneity of variances - data from multiple groups have the same variance. We can check this using the Levene test.
3. Independence - The data is independent of each other. This assumption may be satisfied by randomly selecting the samples, then dividing the samples into appropriate sub-groups.
Types of Statistical Tests
There are many different statistical tests we can run so in this blog, we will do a brief overview of a few commonly used ones.
If you don’t know the population standard deviation and you have a small sample size, you can use a t-test to compare two means to determine if they are different from each other.
One-tailed T-test- is directional. It is when you want to know if a parameter from the treatment group is greater than (or less than) a corresponding parameter from the control group.
Two-tailed T-test- is when the direction of difference is unknown. It is for when you want to test if a parameter falls between (or outside of) a range of two given values.
One Sample T-test- compares the mean of your sample data to a known value.
Two Sample T-test- used to determine if two population means are equal. These can be paired or independent. Our previous clinical trial example is a good illustration of a paired t-test since it is comparing how two groups change after treatment.
A modification of the t-test is called Welch’s T-test for Unequal Variances. The purpose of this test is similar in that it determines if two sample means are significantly different, but unlike the standard t-tests, Welch’s increases the test power for samples with unequal variance by adjusting the degrees of freedom. Welch’s tends to perform better than the standard t-test when the sample sizes and variances are unequal between groups and gives the same result as the standard t-test when the sample sizes and variances are equal.
When comparing differences between three or more independent groups, ANOVAs are useful. ANOVA is short for “Analysis of Variance” and it compares the amount of variation between groups with the amount of variation within groups (F-ratio calculation). For ANOVA, we assume a normal distribution and similar variances within different independent groups. As the average difference between the groups becomes greater than the difference within the groups, the F-ratio becomes larger than 1. Larger F-ratios tend to give smaller p-values.
Level Up! Monte Carlo Simulation
Monte Carlo simulation is the new kid on the block for fast and powerful statistical testing. It is a computerized method which allows people to take into account the risk in quantitative analysis and decision making. Unlike the previous tests we mentioned in this blog, Monte Carlo is a non-parametric test, therefore there are no assumptions made regarding the distribution.
In order to calculate the probability of an event occurring, it is important to know the number of occurrences and the number of possible outcomes. When there are a large amount of variables, the permutations grow exponentially to a point where the sample spaces are too large to analyze all the possible outcomes. This is where Monte Carlo comes in! Monte Carlo simulation substitutes a range of values for any factor with inherent uncertainty and then calculates results over and over, each time with a different random set of values.
References:
Figure 1: https://www.researchgate.net/figure/STEPS-OF-THE-SCIENTIFIC-METHOD-43_fig1_270876016
https://www.students4bestevidence.net/p-value-in-plain-english-2/
https://blog.minitab.com/blog/adventures-in-statistics-2/understanding-hypothesis-tests-significance-levels-alpha-and-p-values-in-statistics
https://www.stat.berkeley.edu/~hhuang/STAT141/Lecture-FDR.pdf
https://www.sagepub.com/sites/default/files/upm-binaries/43443_7.pdf
https://www.statisticshowto.datasciencecentral.com/statistical-power/
https://www.statisticshowto.datasciencecentral.com/degrees-of-freedom/
https://en-author-services.edanzgroup.com/blogs/statistics-anova-explained
https://www.palisade.com/risk/monte_carlo_simulation.asp

What are some methods we can use?

Log Transformation:

Example distribution before (left) and after (right) log transformationThis is one of the most commonly used transformations to address skewed (asymmetrical) data to reduce variability and make your data less skewed.

Min-Max Scaling:

The objective of Min-Max scaling is to  shift the values closer to the mean of the column. This method scales the data to a fixed range, usually [0, 1] or [-1, 1]. A drawback of bounding this data to a small fixed range is that we will, in turn, end up with smaller standard deviations, which suppresses the weight of outliers in our data.

Standardization (Z-Score Normalization):

Standardization is used to compare features that have different units or scales. This is done by subtracting a measure of location (x- x̅) and dividing by a measure of scale ( σ). 
This transforms your data so the resulting distribution has a mean of 0 and a standard deviation of 1. This is method is useful (in comparison to normalization) when we have important outliers in our data and we don't want to remove them and lose their impact. 

Unit Vector Transformation:

This method uses the Pythagorean Theorem (vx² + vy²=v²) in order to determine the magnitude (hypotenuse) of a vector.

To normalize the vector, we divide each component by the magnitude of the vector in order to scale down to 1. For example, a vector with value 10 divided by 10 equals 1. To scale down to vector size 1, all other components need to be divided by the same amount, 10, as well. So using this method, we can change the length of the vector without affecting the direction. 

When performing unit vector transformations, you can create a new variable x' with a range [0,1]. 

Mean Normalization:

This normalization will create the distribution of features between [-1, 1].

Box Cox Transformation: 

Box Cox is used to stabilize the variance (eliminate heteroskedasticity) and transform non-normal dependent variables to a normal shape.

Any value of λ when our datapoint (y) is equal to 1 evaluates to 1. Therefore, when we subtract our datapoint (y^ λ) from 1, we center our transformed data around 0. By dividing by λ, we are normalizing the exponential increase of λ from the numerator. The boxcox function in Scipy tests a range of λ values and returns the value that makes your data look the most normal. 

These are just a few of the ways we can transform our data. These methods become especially useful and necessary when using machine learning algorithms. 

*References:*
https://sebastianraschka.com/Articles/2014_about_feature_scaling.html

https://www.statisticshowto.datasciencecentral.com/box-cox-transformation/

https://www.khanacademy.org/computing/computer-programming/programming-natural-simulations/programming-vectors/a/vector-magnitude-normalization

https://en.wikipedia.org/wiki/Feature_scaling
