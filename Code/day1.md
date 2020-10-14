# __Data PreProcessing | Day 1__

<p align="center">
  <img src="https://cdn-images-1.medium.com/max/1200/1*cpJmJWsBb0gYLmXqEMns9g.jpeg">
</p>

Get the dataset from [here](https://github.com/Avik-Jain/100-Days-Of-ML-Code/tree/master/datasets) that is used in this example


### Why is Data PreProcessing important?
 <p>In real world, Data is dirty.<br>
  1. Incomplete: missing attributes, lack of certain attributes of interest.<br>
      e.g., fees=""<br>
  2. noisy: containing errors or outliers<br>
      e.g., fees="trtddh"<br>
  3. inconsistent: containing discrepancies in codes or names<br>
      e.g., was rating "1,2,3", now rating"A,B,C"<br>
<br>
   Data preparation, cleaning and transformation comprises the majority of the work in a data mining application</p>
  
  ### What is Data PreProcessing?
  <p>-The overall process of making data more suitable for data mining<br>
     -It includes several tasks employed in the process to make data more relevant<br></p>
  
  ### Data PreProcessing Tasks
  <p>-Data Cleaning<br>-Data Transformation<br>-Data Reduction<br>-Data Discretization<br></p>
  
  ## Step 1: Importing the libraries
  <p>The two python libraries we are going to use are:<br>
      1. Numpy: it contains math functions<br>
      2. Pandas: used to import and manage the datasets</p>
      
```Python
import numpy as np
import pandas as pd
```
## Step 2: Importing dataset
<p>Data sets are stored in .csv files. A .csv file stores data in tabular form in plain text.
We use the read_csv method from the pandas library to read data sets. Then we make separate matrix and vector of independent and 
dependent variables from the dataframes.<br><p>

```python
dataset = pd.read_csv('Data.csv')
X = dataset.iloc[ : , :-1].values
Y = dataset.iloc[ : , 3].values
```
## Step 3: Handling the missing data
<p>The raw data is rarely homogeneous. Data can be missing due to many reason, this missing data needs to be compensated for otherwise it will reduce the efficiency of the ML model. 
The missing data can be replaced by the mean or the median of its column. This is achieved by Imputer class of sklearn.preprocessing.</p>

```python
from sklearn.preprocessing import Imputer
imputer = Imputer(missing_values = "NaN", strategy = "mean", axis = 0)
imputer = imputer.fit(X[ : , 1:3])
X[ : , 1:3] = imputer.transform(X[ : , 1:3])
```
## Step 4: Encoding categorical data
<p>Catergorical data are variables that contain label values rather than numerical values.<br>
Example: Yes and No have no numerical values so these variables are needed to be encoded in mathematical values.
For this we use,LabelEncoder from sklearn.preprocessing.<br><p>

```python
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
labelencoder_X = LabelEncoder()
X[ : , 0] = labelencoder_X.fit_transform(X[ : , 0])
```
### Creating a dummy variable
```python
onehotencoder = OneHotEncoder(categorical_features = [0])
X = onehotencoder.fit_transform(X).toarray()
labelencoder_Y = LabelEncoder()
Y =  labelencoder_Y.fit_transform(Y)
```
## Step 5: Splitting the datasets into training sets and Test sets 
<p>Usually the data set is divied into two parts, one being used for training i.e., Training Set and the other which is for testing i.e., Testing Set. These sets are divided in 80/20. We import train_test_split() from the sklearning.crossvalidation library. </p>

```python
from sklearn.cross_validation import train_test_split
X_train, X_test, Y_train, Y_test = train_test_split( X , Y , test_size = 0.2, random_state = 0)
```

## Step 6: Feature Scaling
<p>Most ML models use euclidean distance between data points which features highly varying in magnitude, units and range pose problems. It is done by standardization and Z-normalization. StandardScalar of sklearning.preprocessing is imported.<br></p>

```python
from sklearn.preprocessing import StandardScaler
sc_X = StandardScaler()
X_train = sc_X.fit_transform(X_train)
X_test = sc_X.fit_transform(X_test)
```
### Done 1 down, 99 to go.
