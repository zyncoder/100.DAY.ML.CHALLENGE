# Multiple Linear Regression | Day 3

<p align="center">
  <img src="https://aegis4048.github.io/images/featured_images/multiple_linear_regression_and_visualization.png">
</p>

<p>Multiple linear regression attempts to model the relationship between two or more explanatory variables and a response variable by fitting a linear equation to observed data. Every value of the independent variable x is associated with a value of the dependent variable y. The population regression line for p explanatory variables x1, x2, ... , xp is defined to be y = 0 + 1x1 + 2x2 + ... + pxp. This line describes how the mean response y changes with the explanatory variables. The observed values for y vary about their means y and are assumed to have the same standard deviation . The fitted values b0, b1, ..., bp estimate the parameters 0, 1, ..., p of the population regression line.<br>
Since the observed values for y vary about their means y, the multiple regression model includes a term for this variation. In words, the model is expressed as DATA = FIT + RESIDUAL, where the "FIT" term represents the expression 0 + 1x1 + 2x2 + ... pxp. The "RESIDUAL" term represents the deviations of the observed values y from their means y, which are normally distributed with mean 0 and variance . The notation for the model deviations is .<br>

Formally, the model for multiple linear regression, given n observations, is<br>
yi = 0 + 1xi1 + 2xi2 + ... pxip + i for i = 1,2, ... n.<br>

In the least-squares model, the best-fitting line for the observed data is calculated by minimizing the sum of the squares of the vertical deviations from each data point to the line (if a point lies on the fitted line exactly, then its vertical deviation is 0). Because the deviations are first squared, then summed, there are no cancellations between positive and negative values. The least-squares estimates b0, b1, ... bp are usually computed by statistical software.<br>

The values fit by the equation b0 + b1xi1 + ... + bpxip are denoted i, and the residuals ei are equal to yi - i, the difference between the observed and fitted values. The sum of the residuals is equal to zero.<br>

The variance ² may be estimated by s² =<img src="http://www.stat.yale.edu/Courses/1997-98/101/msemult.gif"> , also known as the mean-squared error (or MSE).
The estimate of the standard error s is the square root of the MSE.


## Step 1: Data Preprocessing
We will follow the following steps in the day 1:
- Import Libraries
- Import the data sets
- Compensate for missing data
- Encoding missing data
- Spliting the data into training and test
- Feature Scaling

### Importing the libraries
```python
import pandas as pd
import numpy as np
```
### Importing the dataset
```python
dataset = pd.read_csv('50_Startups.csv')
X = dataset.iloc[ : , :-1].values
Y = dataset.iloc[ : ,  4 ].values
```

### Encoding Categorical data
```python
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
labelencoder = LabelEncoder()
X[: , 3] = labelencoder.fit_transform(X[ : , 3])
onehotencoder = OneHotEncoder(categorical_features = [3])
X = onehotencoder.fit_transform(X).toarray()
```

### Avoiding Dummy Variable Trap
```python
X = X[: , 1:]
```

### Splitting the dataset into the Training set and Test set
```python
from sklearn.cross_validation import train_test_split
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size = 0.2, random_state = 0)
```
## Step 2: Fitting Multiple Linear Regression to the Training set
Just like in the Simple Regression model, To fit the dataset into the model we use LinearRegression from sklearn.linear_model library. Then we make the object regressor from LinearRegression class. Now we will fit the regressor object into our data set using fit() method of linear regression.


```python
from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, Y_train)
```

## Step 3: Predicting the Test set results
Now we will predict the observations from our test set. We will save the output in Y_pred. To predict the result we use the predict method from LinearRegression class on regressor we trained in the last step.


```python
y_pred = regressor.predict(X_test)
```
# Done 3 down, 97 to go.
