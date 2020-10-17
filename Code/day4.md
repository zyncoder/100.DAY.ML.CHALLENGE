# Intro to Logistic Regression | Day 4

<p align="center">
  <img src="https://www.machinelearningplus.com/wp-content/uploads/2017/09/linear_vs_logistic_regression.jpg">
</p>

<p>Thus far our focus has been on describing interactions or associations between two or three categorical variables mostly via single summary statistics and with significance testing. From this lesson on, we will focus on modeling. Models can handle more complicated situations and analyze the simultaneous effects of multiple variables, including mixtures of categorical and continuous variables.</p>

### Binary Logistic Regression is a special type of regression where binary response variable is related to a set of explanatory variables, which can be discrete and/or continuous. The important point here to note is that in linear regression, the expected values of the response variable are modeled based on combination of values taken by the predictors. In logistic regression Probability or Odds of the response taking a particular value is modeled based on combination of values taken by the predictors. Like regression (and unlike log-linear models that we will see later), we make an explicit distinction between a response variable and one or more predictor (explanatory) variables. We begin with two-way tables, then progress to three-way tables, where all explanatory variables are categorical. Then we introduce binary logistic regression with continuous predictors as well. In the last part we will focus on more model diagnostics and model selection.

Logistic regression is applicable, for example, if:<br>

- we want to model the probabilities of a response variable as a function of some explanatory variables, e.g. "success" of admission as a function of gender.<br>
- we want to perform descriptive discriminate analyses such as describing the differences between individuals in separate groups as a function of explanatory variables, e.g. student admitted and rejected as a function of gender<br>
- we want to predict probabilities that individuals fall into two categories of the binary response as a function of some explanatory variables, e.g. what is the probability that a student is admitted given she is a female<br>
- we want to classify individuals into two categories based on explanatory variables, e.g. classify new students into "admitted" or "rejected" group depending on their gender.</p>
