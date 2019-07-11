## Laboratory Measurements and Procedures

1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python!
**The spreadsheet is attached in the email.**
2. Create a graph of absorbance vs. concentration of red dye 40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.
**(see code below)
We removed the data from the very high and low concentrations because they were at the limit of the instrument, meaning that the data was not linear.**
![absorbanceplot](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab1_plot.png?raw=true)

Figure 1: Plot showing absorbance vs concentration of red dye #40 for standards. Data shows the expected linear relationship.
3. What is the value of the extinction coefficient, ε?
**ε = 0.002316 m^2/mg. The values of ε change for each different concentration and absorbance, so we used the slope from the equation to solve for epsilon. (see details in code comments)**


```python
from aguaclara.core.units import unit_registry as u
import numpy as np
import math
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

# Load data from file
data_file_path = "/Users/Rosie/github/CEE4530/Lab1-Fundamentals/Lab1_concentration_voltage_data.tsv"


df = pd.read_csv(data_file_path,delimiter='\t')
print(df)
list(df)
columns = df.columns

Conc = df.iloc[:,0].values * u.mg/u.L
Voltage = df.iloc[:,1].values * u.V

#constants from measurements in ProCoDa, dark voltage and blank voltage
dark_V =-1.307035 * u.V
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
ax.set(ylabel='Absorbance')
ax.legend(['Measured', 'Linear regression'])
ax.grid(True)
ax.set(title='Absorbance of light as a function of concentration of red dye')

# Save file
plt.savefig('/Users/Rosie/github/CEE4530/Lab1_plot')
plt.show()

# Calculate extinction coefficient
# A = e*b*c
# y = m*x+intercept, but intercept is negligible, so we can use the slope, m, to solve for e:
# m=e*b
# b = length of simple photometer
b = (3/4 * u.inch).to(u.m)
m=slope.to(u.m**3/u.mg)
print(m)
e=m/b # extinction coefficient
print(e)


```
4. Did you use interpolation or extrapolation to get the concentration of the unknown?
**We used interpolation to get the concentration of the unknown because the 14 mg/L was within the range of our data.**
5. What measurement controls the accuracy of the density measurement for the NaCl solution?
**Step 1 of the Measuring Density section where we weigh a volumetric flask with 100 mL of the NaCl solution controls the accuracy of the density measurement because a volumetric flask is the least accurate.**
6. What density did you expect (see prelab 2)?
**We expected a density of 55.4428 g/L.**
7. Approximately what should the accuracy be for the density measurement?
**The accuracy for the density measurement is that of a volumetric flask at 0.16mL/100mL.**
8. Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown.
**Through this lab, we gained familiarity via experiment with measurements of masses, volumes, and preparation of chemical solutions of known composition. More specifically, we are now able to: calibrate and use electronic balances, use the photometer and record data with ProCoDa, utilize a digital pipette, prepare dilutions, and measure concentrations using a photometer. We found that there are limits to the ability of the photometer and that at high concentrations of red dye, the photometer maxed out and no longer saw a difference between difference concentrations. Based on our data, we found an extinction coefficient of ε = 0.002316 m^2/mg, estimated the concentration of the unknown as 14 mg/L and had practice making various strengths of standards, helping us become more comfortable and familiar with many lab techniques.**
