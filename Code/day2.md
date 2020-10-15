# Simple Linear Regression | Day 2

<p align="center">
  <img src="https://365datascience.com/wp-content/uploads/2017/08/The-linear-regression-model.png">
</p>

<p>Simple linear regression is a technique that predicts a metric variable from a linear relation with another metric variable.
Remember that “metric variables” refers to variables measured at interval or ratio level. The point here is that calculations -like addition and subtraction- are meaningful on metric variables (“salary” or “length”) but not on categorical variables (“nationality” or “color”).</p>
<p >
  Any linear relation can be defined as Y’ = A + B * X. Let's see what these numbers mean.
  
  <img src="http://www.spss-tutorials.com/img/simple-linear-regression-equation-linear-relation.png">
</p>




# Step 1: Data Preprocessing
<p>We will follow the following steps in the day 1:<br>
- Import Libraries<br>
- Import the data sets<br>
- Compensate for missing data<br>
- Encoding missing data<br>
- Spliting the data into training and test<br>
- Feature Scaling<br>

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

dataset = pd.read_csv('studentscores.csv')
X = dataset.iloc[ : ,   : 1 ].values
Y = dataset.iloc[ : , 1 ].values

from sklearn.cross_validation import train_test_split
X_train, X_test, Y_train, Y_test = train_test_split( X, Y, test_size = 1/4, random_state = 0) 
```

# Step 2: Fitting Simple Linear Regression Model to the training set
<p>To fit the dataset into the model we use LinearRegression from sklearn.linear_model library. Then we make the object regressor from LinearRegression class. Now we will fit the regressor object into our data set using fit() method of linear regression.</p>

 ```python
 from sklearn.linear_model import LinearRegression
 regressor = LinearRegression()
 regressor = regressor.fit(X_train, Y_train)
 ```
 # Step 3: Predecting the Result
 <p>Now we will predict the observations from our test set. We will save the output in Y_pred. To predict the result we use the predict method from LinearRegression class on regressor we trained in the last step.</p>
 
 ```python
 Y_pred = regressor.predict(X_test)
 ```
 
 # Step 4: Visualization 
  <p>Next step is to visualize results. We will use matplotlib.pyplot to make scatter plots of our training result and test result to see how close our model predicted the value.</p>

 ## Visualising the Training results
 ```python
 plt.scatter(X_train , Y_train, color = 'red')
 plt.plot(X_train , regressor.predict(X_train), color ='blue')
 ```
 ## Visualizing the test results
 ```python
 plt.scatter(X_test , Y_test, color = 'red')
 plt.plot(X_test , regressor.predict(X_test), color ='blue')
 ``` 
#Done 2 down, 98 to go.
