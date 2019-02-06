## Laboratory Measurements and Procedures



```python
from aguaclara.core.units import unit_registry as u
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

# Load data from file
data_file_path = "https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab1_concentration_voltage_data.tsv"

df = pd.read_csv(data_file_path,delimiter='\t')
print(df)
list(df)
columns = df.columns

Conc = df.iloc[:,0].values * u.mg/u.L
Voltage = df.iloc[:,1].values * u.V

dark_V =	-1.307035 * u.V
blank_V	= 3.563451 * u.V

# Calculate absorbance from voltage
A = -np.log10((Voltage-dark_V)/(blank_V-dark_V))

# Linear regression
slope, intercept, r_value, p_value, std_err = stats.linregress(Conc,A)

# Intercept is unitless
print(intercept)
slope = slope /Conc.units
print(slope)

# Now create a figure and plot the data and the line from the linear regression.
fig, ax = plt.subplots()
# plot the data as red circles
ax.plot(Conc, A, 'ro', )

#plot the linear regression as a black line
ax.plot(Conc, slope * Conc + intercept, 'k-', )

# Add axis labels using the column labels from the dataframe
ax.set(xlabel=list(df)[0])
ax.set(ylabel=list(df)[1])
ax.legend(['Measured', 'Linear regression'])
ax.grid(True)

# Save file
#plt.savefig('/Users/Rosie/github/CEE4530/Lab1_plot')
plt.show()











```
