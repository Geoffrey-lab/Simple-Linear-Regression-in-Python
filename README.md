# Simple Linear Regression in Python

This repository contains a Jupyter Notebook that demonstrates the implementation of simple linear regression using Python. The notebook covers data loading, exploratory data analysis, visualization, and a step-by-step guide to implementing and evaluating a simple linear regression model.

## Notebook Content Overview

### 1. Data Loading and Preparation
- Import necessary libraries: `numpy`, `pandas`, `matplotlib`
- Load data from a CSV file into a Pandas DataFrame
- Rename DataFrame columns for ease of use

### 2. Data Exploration and Visualization
- Display the first few rows of the DataFrame
- Plot the ZAR/USD exchange rate and the value of exports over time
- Create a combined plot with dual y-axes for better visualization

### 3. Simple Linear Regression Implementation
- Scatter plot of the original dataset
- Function to generate predicted values based on a linear equation
- Plotting the original data along with the regression line

### 4. Model Evaluation
- Calculate errors between the true and predicted y-values
- Visualize the distribution of errors using a histogram
- Calculate and interpret the Residual Sum of Squares (RSS) to evaluate model fit

## Key Functions and Code Snippets

### Data Loading
```python
df = pd.read_csv('https://github.com/Explore-AI/Public-Data/blob/master/exports%20ZAR-USD-data.csv?raw=true', index_col=0)
df.columns = ['Y', 'X']
df.head()
```

### Data Visualization
```python
plt.plot(np.arange(len(df.Y)), df.Y)
plt.title("ZAR/USD over time")
plt.xlabel("Months")
plt.ylabel("ZAR/USD")
plt.show()

plt.plot(np.arange(len(df.X)), df.X)
plt.title("Value of Exports over time")
plt.xlabel("Months")
plt.ylabel("Exports (ZAR, millions)")
plt.show()
```

### Simple Linear Regression
```python
def gen_y(x_list, m, c):
    y_gen = []
    for x_i in x_list:
        y_i = m * x_i + c
        y_gen.append(y_i)
    return y_gen

y_gen = gen_y(df.X, 0.0002, -3)

plt.scatter(df.X, df.Y)
plt.plot(df.X, y_gen, color='red')
plt.ylabel("ZAR/USD")
plt.xlabel("Value of Exports (ZAR, millions)")
plt.show()
```

### Error Calculation and Model Evaluation
```python
errors = np.array(df.Y - y_gen)
print("Residual sum of squares:", (errors ** 2).sum())

plt.hist(errors)
plt.show()
```

## Conclusion
The notebook provides a practical example of how to implement and evaluate a simple linear regression model in Python. By following the steps outlined, users can gain a better understanding of the concepts and techniques involved in linear regression analysis.

Feel free to explore, modify, and extend the code to suit your specific needs. Contributions and feedback are welcome!
