# Supervised-learning-Linear-models-and-Loss-functions
In this project, I have worked with some data on possums. It is a relatively small data set, but it's a good size to try with ordinary least squares (OLS) and least absolute deviation (LAD), and to gain experience with supervised learning. I have written my own methods to fit both OLS and LAD models, and then at the end compared them to the models produced by the statsmodels package.

For this project, I examined some data representing possums in Australia and New Guinea. The code loads in a pandas data frame with 46 observations on the following 6 variables:

sex: Sex, either m (male) or f (female).
age: Age in years.
headL: Head length, in mm.
skullW: Skull width, in mm.
totalL: Total length, in cm.
tailL: Tail length, in cm.

There are three main parts in this code:
1- OLS estimation and plotting
2- Least Absolute Deviation Loss
3- Comparing with Statsmodel

**Section 1: "OLS estimation and plotting"**

Part 1:
I investigate the relationship between the possum's age and it's tail length by plotting a scatter plot of the age and tailL columns. My plot and my axes are labeld as well. If there are some data that are overlapping, you might need to add an alpha.

Part 2:
In linear model, predictions are obtained by computing 𝐲̂ =𝐗𝛽.
Here, 𝐗 is a design matrix, 𝛽 are coefficients, and 𝐲̂ are fitted/estimates/predicted values.  I want to define a model-prediction function yhat = linearModelPredict(beta,X) that takes a parameter vector beta and a matrix x of inputs, and produces a vector yhat containing the predicted (fitted) values that correspond to each row of the input matrix. It is assumed that beta has p rows and 1 column, and that x has n rows and p columns.
* As of Python 3.5, the @ symbol can be used for matrix multiplication.

Part 3:
I write a function called linearModelLossRSS which computes the loss function for an OLS model parameterized by 𝛽, as well as the gradient of the loss. I define a squared error loss function (loss, gradient)=linearModelLossRSS(beta, X, y) that takes a parameter vector beta, a matrix x of inputs, and a vector y of observed values, and produces the sum of squared errors between the observed and predicted (fitted) values, along with the gradient of the loss.  It is assumed that theta has p rows and 1 column, and x has n rows and p column, and y has n rows and 1 column.

Part 4:
Now that we have implemented a loss function in part 3, it's time to minimize it to fit the data.
I wrote a function called linearModelFit to fit a linear model. The functiona takes as its first argument a 2d-array x which houses the input data with one example per row, as its secod argument a 1d-array y of outcomes with one example per row, and as its third argument a function lossfcn which returns as a tuple the value of the loss, as well as the gradient of the loss.

This function is used to estimate the parameters that describe the relationship between a possum's age and its tail length, i.e.,  TailLengthˆ=𝛽0+𝛽1age.

Using this solution, the data point and the fitted line are plotted.


**Section 2: Least Absolute Deviation Loss**

Part 1:
In the previous section, I worked with the squared loss. Now, wI implement a linear model with least absolute deviation loss.

I wrote a function linearModelLossLAD which computes the least absolute deviation loss function for a linear model parameterized by  𝛽 , as well as the gradient of the loss. This function  takes as its first argument a 1d-array beta of coefficients for the linear model, as its second argument a 2d-array X of data, and as its third argument a 1d-array y of observed outcomes.

Part 2:
I use linearModelLossLAD to fit a linear model with least absolute deviation loss. The fit is plotted as well.

**Section 3: Comparing With Statsmodels**

Here, I fit both an OLS and a LAD model with statsmodels to compare coefficient estimates, R squared values, and I plot the fits. 
