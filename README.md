# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 03/11/2026


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv('Electric_Production.csv')

data['DATE'] = pd.to_datetime(data['DATE'])
data['Year'] = data['DATE'].dt.year
# Set the 'DATE' column as the index
data.set_index('DATE', inplace=True)
print(data.head())

# Plotting the Data
ar1 = data['Year'].values.reshape(-1, 1)
ma1 = data['IPG2211A2N'].values.reshape(-1, 1)
plt.plot(ar1,ma1,label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

# Perform time series decomposition
period=13
result = seasonal_decompose(data['IPG2211A2N'],model='multiplicative', period=period)

# Plot the seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Plot the trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

# Plot the original time series
plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['IPG2211A2N'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()
```















### OUTPUT:
FIRST FIVE ROWS:<br>
<img width="295" height="265" alt="image" src="https://github.com/user-attachments/assets/4e2cd9e0-9052-4e0a-9936-94f2d38e045e" />



PLOTTING THE DATA:<br>
<img width="687" height="540" alt="image" src="https://github.com/user-attachments/assets/7e6152d7-6bea-4cfa-86d1-8d26629a9209" />



SEASONAL PLOT REPRESENTATION :<br>
<img width="703" height="163" alt="image" src="https://github.com/user-attachments/assets/0d848de3-e3d0-40af-9189-114fe2c32570" />



TREND PLOT REPRESENTATION :<br>
<img width="687" height="168" alt="image" src="https://github.com/user-attachments/assets/a12fb7a3-24f1-4c7a-b2dd-a315eca4b524" />

OVERAL REPRESENTATION:<br>
<img width="986" height="166" alt="image" src="https://github.com/user-attachments/assets/98b667b0-7569-4734-9961-cd3fac9f049b" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
