# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1.Import necessary libraries for numerical operations, data handling, and preprocessing.

2.Load the startup dataset (50_Startups.csv) using pandas.

3.Extract feature matrix X and target vector y from the dataset.

4.Convert feature and target values to float and reshape if necessary.

5.Standardize X and y using StandardScaler.

6.Add a column of ones to X to account for the bias (intercept) term.

7.Initialize model parameters (theta) to zeros.

8.Perform gradient descent to update theta by computing predictions and adjusting for error.

9.Input a new data point, scale it, and add the intercept term.

10.Predict the output using learned theta, then inverse-transform it to get the final result.

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: HENRIPRASATH S
RegisterNumber:  212223230077
*/
```
```
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler

def linear_regression(X1,y,learning_rate = 0.1, num_iters = 1000):
    X = np.c_[np.ones(len(X1)),X1]
    
    theta = np.zeros(X.shape[1]).reshape(-1,1)
    
    for _ in range(num_iters):
        
        predictions = (X).dot(theta).reshape(-1,1)
        
        errors=(predictions - y ).reshape(-1,1)
        
        theta -= learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta

data=pd.read_csv("50_Startups.csv")
data.head()
X=(data.iloc[1:,:-2].values)
X1=X.astype(float)

scaler=StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)

X1_Scaled=scaler.fit_transform(X1)
Y1_Scaled=scaler.fit_transform(y)
print(X1_Scaled)
print(Y1_Scaled)

theta= linear_regression(X1_Scaled,Y1_Scaled)

new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)

new_Scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1,new_Scaled),theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted value: {pre}")
```

## Output:
![Screenshot 2025-03-13 141619](https://github.com/user-attachments/assets/cbbff262-6f65-4803-a85b-bebb28fc0779)

![Screenshot 2025-03-13 141707](https://github.com/user-attachments/assets/8319838a-89f5-42e5-a738-11c6cc62919b)


## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
