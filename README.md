### DEVELOPED BY : KULASEKARAPANDIAN K
### REGISTER NO : 212222240052
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

## AIM:
To illustrate how to perform time series analysis and decomposition on the Ethereum (ETH) price dataset using Python.


## ALGORITHM:
1. Import the required packages like pandas, matplotlib, and statsmodels.
2. Read the data using pandas from the provided Ethereum dataset.
3. Convert the dateTime column to a datetime object and set it as the index.
4. Perform seasonal decomposition using the seasonal_decompose function on the close price column with a daily periodicity (96 periods for 15-minute interval data).
5. Plot the data components: observed, trend, seasonal, and residual plots.
6. Display the overall results through graphical representations.

## PROGRAM:
```python
# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('ETH15M.csv')

# Convert 'dateTime' column to datetime and set it as the index
df['dateTime'] = pd.to_datetime(df['dateTime'], format='%Y-%m-%d %H:%M:%S')
df.set_index('dateTime', inplace=True)

# Perform seasonal decomposition on the 'close' price column (additive model)
# Assuming a period of 96 to capture daily patterns (since the data is in 15-minute intervals, 96 represents one day)
decomposition = seasonal_decompose(df['close'], model='additive', period=96)

# Plot and save each component separately

# Observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='blue')
plt.title('Observed')
plt.ylabel('Observed')
plt.show()

# Trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='green')
plt.title('Trend')
plt.ylabel('Trend')
plt.show()

# Seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='red')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.show()

# Residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.show()
```

### OUTPUT :
#### First five rows of the dataset:
![image](https://github.com/user-attachments/assets/47a15cdf-908a-4324-a803-b8e1916727e0)

#### Observed plot:
![image](https://github.com/user-attachments/assets/f286cc14-f136-4942-b852-ec7e3336b1a8)

#### Seasonal plot representation: 
![image](https://github.com/user-attachments/assets/71428e0a-e3bf-4155-b54f-0a7094267505)

#### Trend plot representation:
![image](https://github.com/user-attachments/assets/db9b01b4-771e-463e-bb08-00e2c1a99311)

#### RESIDUAL :
![image](https://github.com/user-attachments/assets/a4e70001-a759-4955-acde-0a531da984ab)

## RESULT :
Thus, the Python code for time series analysis and decomposition on the Ethereum dataset was successfully executed, and the observed, trend, seasonal, and residual components were visualized.

