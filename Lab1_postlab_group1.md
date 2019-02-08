## Laboratory Measurements and Procedures

1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python!
2. Create a graph of absorbance vs. concentration of red dye 40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.

We removed the data from the high and low concentrations because they were at the limit of the instrument, meaning that the data was

3. What is the value of the extinction coefficient, ε?
4. Did you use interpolation or extrapolation to get the concentration of the unknown?
5. What measurement controls the accuracy of the density measurement for the NaCl solution?
6. What density did you expect (see prelab 2)?
7. Approximately what should the accuracy be for the density measurement?
8. Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown.
9. Verify that your report and graphs meet the requirements as outlined on the course website.





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
plt.savefig('/Users/Rosie/github/CEE4530/Lab1_plot')
plt.show()


# Calculate extinction coefficient
# e = A/bc
b = 0.000000465*u.m # length of simple photometer
c = Conc*u.mg/u.L
e = A/b*c*u.mg/u.m*math.exp(2)










```
