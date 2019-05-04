# String Digester
### Rosalie Krasnoff and Jiwon Lee
##### May 13th 2019

## Introduction and Objectives
to create a plant that is optimized for low cost and a high performance, and looking at the regions a future wastewater plant would serve, trickling filters are a promising technology due to their low-energy requirements


A trickling filter is a secondary wastewater treatment system that removes organic matter from the wastewater through biological means, and is crucial for the removal of harmful pathogens. Looking to improve on the traditional industrial-scale trickling filter design, previous work identified an issue with the process: there is a substantial amount of unused space in the trickling treatment unit due to the uneven flow of wastewater across the system (preferential flow). The primary objective of this sub-team is to continue to develop a novel design for a highly efficient trickling filter with a minimized footprint in terms of space.



## Procedures



## Results and Discussion
### Data Analysis

``` python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.physchem as pc
import aguaclara.core.utility as ut
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats


# Flow rate = 5 rpm
# Data for flat string
Na2SO3_string_5rpm = (np.array([0.016,0.016,0.159,0.159,0.159,0.397])*u.g).to(u.mg)
DO_string_5rpm = np.array([7.2,6.7,2.1,5,4.1,0.3])*u.mg/u.L

slope1, intercept1, r_value, p_value, std_err = stats.linregress(Na2SO3_string_5rpm, DO_string_5rpm)
slope1 = slope1/u.mg

plt.plot(Na2SO3_string_5rpm, DO_string_5rpm, 'o', label='measured DO using string at 5rpm')
plt.plot(Na2SO3_string_5rpm, intercept1 + slope1*Na2SO3_string_5rpm, 'r', label='fitted line')
plt.xlabel(r'$Na_{2}SO_{3}$ (mg)');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/string_at_5rpm.png')
plt.show()

# DO data for loopy yarn
# 3.3 point might not be good!!!
Na2SO3_yarn_5rpm = (np.array([0.016,0.016,0.016,0.158,0.158,0.158,0.397,0.397])*u.g).to(u.mg)
DO_yarn_5rpm = np.array([5.7,7,7,3.3,5.8,6.7,.15,1])*u.mg/u.L

slope2, intercept2, r_value, p_value, std_err = stats.linregress(Na2SO3_yarn_5rpm, DO_yarn_5rpm)
slope2 = slope2/u.mg

plt.plot(Na2SO3_yarn_5rpm, DO_yarn_5rpm, 'o', label='measured DO using yarn at 5 rpm')
plt.plot(Na2SO3_yarn_5rpm, intercept2 + slope2*Na2SO3_yarn_5rpm, 'r', label='fitted line')
plt.xlabel(r'$Na_{2}SO_{3}$ (mg)');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/yarn_at_5rpm.png')
plt.show()



# Constant Na2SO3
# Data for flat string
Flowrate_string = np.array([5,5,5,20,20,20,50,50])*u.revolution/u.min
DO_string = np.array([2.1,5,4.1,2.1,2,0.3,0.2,0.3])*u.mg/u.L


slope3, intercept3, r_value, p_value, std_err = stats.linregress(Flowrate_string, DO_string)
slope3 = slope3/Flowrate_string.units

plt.plot(Flowrate_string, DO_string, 'o', label='measured DO using string at various flow rates')
plt.plot(Flowrate_string, intercept3 + slope3*Flowrate_string, 'r', label='fitted line')
plt.xlabel(r'Flow Rate $\frac{rev}{min}$');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/string_at_rpms.png')
plt.show()

# DO data for loopy yarn
# 3.3 point m

# DO data for loopy yarn
Flowrate_yarn = np.array([5,5,5,20,20,20,20,50,50,50,50])*u.revolution/u.min
DO_yarn = np.array([3.3,5.8,6.7,5.6,5.01,4.9,4.5,0.5,1.2,1,0])*u.mg/u.L

slope4, intercept4, r_value, p_value, std_err = stats.linregress(Flowrate_yarn, DO_yarn)
slope4 = slope4/Flowrate_yarn.units

plt.plot(Flowrate_yarn, DO_yarn, 'o', label='measured DO using yarn at various flow rates')
plt.plot(Flowrate_yarn, intercept4 + slope4*Flowrate_yarn, 'r', label='fitted line')
plt.xlabel(r'Flow Rate $\frac{rev}{min}$');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/yarn_at_rpms.png')
plt.show()



```





## Conclusion

## Suggestions/Comments

# Appendix
