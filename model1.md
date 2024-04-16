---
title: Machine Learning Model N.1
---

## Linear Regression

For our first model, we used linear regression to predict the pricing of the houses. For this, we used the scikit learn library from python, the code used for this part can be found [here](./model1code).

Our prediction variable is the Median House Value, using the other columns in the dataset as inputs for the model.

The procedure we used was to make 1000 simulations of the regression, gathering the coefficients, the intercept and the score of each iteration so that we could make some inferences about the best parameters that we could use, for this we plotted the distribution of the parameters:

![Parameters Distribution](assets/Model1/Parameter%20Distribution.png)

With these plot, we can see that most of the parameters follow roughly a normal distribution, except for the parameters associated with the population and the households, which seem to have a bias in the distribution, which could explain some of the inaccuracy of the model. We also plotted the distribution of the scores throughout the iterations:

![Score Distribution](assets/Model1/Score%20Distribution.png)

Looking at this plot, we can see that the model's score doesn't have a lot of dispersion, being within a range of [0.6 - 0.68] having a big spike around 0.645.

We also calculated the average value of each of the parameters, using this average value as a good representation of the real parameters, using these values, we constructed a new regresssion and calculated it's score distribution with different cross-validation splits, with this, we got the following plot:

![Score Distribution with average Parameters](assets/Model1/Average%20Score%20Distribution.png)

Also, we created a Regression plot with the predicted values compared to the actual values using the entire dataset, this because the average parameters should be influenced equally by the entire dataset, out of this we got the following plot:

![Regplot image](assets/Model1/Regplot.png)

We can see there are some huge outliers in the plot, but most points are clustered around the line of regression, also, the score we got comparing the regression to the entire dataset was 0.6465617542482369.

Finally, we calculated the new average score and compared it to the average scores calculated in each iteration of the regression, improving the average by 0.0017014752125713573, and we can clearly see in the plot that the dispersion compared to the previos one was improved.

Even though using the average values gave us a better performance, we still think that a linear regression is not a good choice of machine learning model for our dataset, this is because we didn't get an score greater than 0.7, so it doesn't really capture the behavior of the data adecuately, but it can be useful to get a quick estimation of the output and takes very little time to train compared to bigger models, so we think it did a decent job.

## [Go back to Main Page](./)
