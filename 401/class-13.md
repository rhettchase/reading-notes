# Class 13 Reading Notes: Linear Regression

source: links below, chatGPT

- [How to Run Linear Regression in Python](https://www.activestate.com/resources/quick-reads/how-to-run-linear-regressions-in-python-scikit-learn/)
- [Linear Regression in Python](https://realpython.com/linear-regression-in-python/)
- [Introduction to Simple Linear Regressions](https://www.youtube.com/watch?v=KsVBBJRb9TE)
- [Understanding Train Test Split](https://builtin.com/data-science/train-test-split)
- [What is Linear Regression](https://www.statisticssolutions.com/what-is-linear-regression/)

## Can you explain the basic concept of linear regression and its purpose in the context of machine learning and data analysis?

Linear regression is a fundamental statistical and machine learning technique used to model the relationship between a dependent variable and one or more independent variables. The basic concept revolves around fitting a linear equation to observed data.

The purpose of linear regression in machine learning and data analysis is to predict the value of a dependent variable based on one or more independent variables. It's used for forecasting, time series modeling, and finding the causal effect relationships between variables. Its simplicity and interpretability make it a widely used statistical method in various fields.

- **Best Fit** – the straight line in a plot that minimizes the deviation between related scattered data points.
- **Coefficient** – also known as a parameter, is the factor a variable is multiplied by. In linear regression, a coefficient represents changes in a **Response** **Variable** (see below).
- **Coefficient of Determination** – the correlation coefficient denoted as 𝑅². Used to describe the precision or degree of fit in a regression. 
- **Correlation** – the relationship between two variables in terms of quantifiable strength and degree, often referred to as the ‘degree of correlation’.  Values range between -1.0 and 1.0. 
- **Dependent Feature** – a variable denoted as y in the slope equation **y=ax+b**. Also known as an Output, or a **Response.** 
- **Estimated Regression Line** – the straight line that best fits a set of scattered data points.
- **Independent Feature** – a variable denoted as x in the slope equation **y=ax+b**. Also known as an Input, or a predictor. 
- **Intercept** – the location where the **Slope** intercepts the Y-axis denoted b in the slope equation y=ax+b. 
- **Least Squares** – a method of estimating a **Best Fit** to data, by minimizing the sum of the squares of the differences between observed and estimated values.
- **Mean** – an average of a set of numbers, but in linear regression, Mean is modeled by a linear function.
- **Ordinary Least Squares Regression (OLS)** – more commonly known as Linear Regression. 
- **Residual** – vertical distance between a data point and the line of regression _(see Residual in Figure 1 below)._
- **Regression** – estimate of predictive change in a variable in relation to changes in other variables _(see Predicted Response in Figure 1 below)._
- **Regression Model** – the ideal formula for approximating a regression.
- **Response Variables** – includes both the Predicted Response (the value predicted by the regression) and the Actual Response, which is the actual value of the data point (see Figure 1 below).
- **Slope** – the steepness of a line of regression. **Slope** and **Intercept** can be used to define the linear relationship between two variables: **y=ax+b.**
- **Simple Linear Regression** – a linear regression that has a single independent variable.

## Describe the process of implementing a linear regression model using Python’s Scikit Learn library, including the necessary steps and functions.

**Import Necessary Libraries**:

- `numpy` for numerical operations.
- `matplotlib.pyplot` for plotting data and regression line.
- `LinearRegression` from `sklearn.linear_model` for the linear regression model.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

```

**Generate and Plot Random Data**:

- Use `numpy` to create random data points. In your example, `x` is an array of 50 random values, and `y` is a linear function of `x` with some added random noise.
- Plot these data points using `matplotlib`.


```python
rnstate = np.random.RandomState(1)
x = 10 * rnstate.rand(50)
y = 2 * x - 5 + rnstate.randn(50)
plt.scatter(x, y)
plt.show()

```

**Create and Train the Linear Regression Model**:

- Instantiate the `LinearRegression` model. The `fit_intercept=True` parameter includes the y-intercept in the model.
- Train the model on the data. `x` needs to be reshaped to a 2D array for this purpose, which is done using `x[:, np.newaxis]`.

```python
model = LinearRegression(fit_intercept=True)
model.fit(x[:, np.newaxis], y)

```

**Make Predictions and Plot the Regression Line**:

- Create a range of x-values (`xfit`) for which you want to predict y-values. This range should cover the extent of your data.
- Use the `predict` function of the model to get the corresponding y-values (`yfit`).
- Plot the original data points and the regression line.

```python
xfit = np.linspace(0, 10, 1000)
yfit = model.predict(xfit[:, np.newaxis])

plt.scatter(x, y)
plt.plot(xfit, yfit)
plt.show()

```

**Interpreting the Model** (Optional, but recommended):

- After fitting the model, you can extract the slope (coefficient) and intercept to understand the relationship your model has found.
- The coefficient tells you how much `y` changes for a one-unit increase in `x`.

The model's coefficients provide insights into the nature of the relationship between your variables.

## What is the purpose of splitting the dataset into train and test sets, and how does this contribute to the evaluation of a machine learning model’s performance?

1. **Assessing Generalization**: The primary purpose of splitting data into training and testing sets is to assess the model's ability to generalize to new, unseen data. The training set is used to train the model, while the testing set acts as a proxy for new data. This separation helps in evaluating how well the model performs on data it has not encountered during its training phase.

2. **Preventing Overfitting**: Overfitting occurs when a model learns the details and noise in the training data to the extent that it negatively impacts the performance of the model on new data. By evaluating the model on a separate test set, you can check for overfitting. If the model performs well on the training data but poorly on the test data, it's likely overfitting.

3. **Model Tuning**: The test set can be used to fine-tune the model parameters. After training, you can use the performance on the test set to make adjustments to the model's parameters or structure to improve its ability to generalize.

4. **Providing an Unbiased Evaluation**: The test set provides an unbiased evaluation of the model. Since the model has not been trained on the test data, its performance metrics (such as accuracy, precision, recall, etc.) on this data are a more reliable indicator of how it will perform in the real world.

5. **Cross-validation**: Sometimes, the data is further split into a validation set or used in a cross-validation setup. This allows for a more robust evaluation by training and testing the model on different subsets of the data and averaging the results, providing a better estimate of the model's performance.
