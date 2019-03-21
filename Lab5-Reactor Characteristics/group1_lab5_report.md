# Reactor Characteristics
#### Group 1- Jiwon Lee and Rosie Krasnoff ( hours each)
##### March 27

## Introduction and Objectives
## Procedures
## Results and Discussion
### Data Analysis
## Conclusion
## Suggestions/Comments



1. Use multivariable nonlinear regression to obtain the best fit between the experimental data and the two models by minimizing the sum of the squared errors. Use epa.Solver_AD_Pe and epa.Solver_CMFR_N. These functions will minimize the error by varying the values of average residence time, (mass of tracer/reactor volume), and either the number of CMFR in series or the Peclet number.

2. Generate a plot showing the experimental data as points and the model results as thin lines for each of your experiments. Explain which model fits best and discuss those results based on your expectations.

3. Compare the trends in the estimated values of N and Pe across your set of experiments. How did your chosen reactor modifications effect dispersion?
Report the values of t⋆ at F = 0.1 for each of your experiments. Do they meet your expectations?


graph E curve -> integrate to get F curve (numpy cumulative sum; numpy trapz)
write a function to find F = 0.1
  looks through array and find values
  smth like this:
  DO_min = 2 * u.mg/u.L
  DO_max = 6 * u.mg/u.L
  for i in range(airflows.size):
    idx_start = (np.abs(DO_data[i]-DO_min)).argmin()
    idx_end = (np.abs(DO_data[i]-DO_max)).argmin()
    time_data[i] = time_data[i][idx_start:idx_end] - time_data[i][idx_start]
    DO_data[i] = DO_data[i][idx_start:idx_end]

4. Evaluate whether there is any evidence of “dead volumes” or “short circuiting” in your reactor.
5. Make a recommendation for the design of a full scale chlorine contact tank. As part of your recommendation discuss the parameter you chose to vary as part of your experimentation and what the optimal value was determined to be.


# Appendix
``` python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
import numpy as np
import matplotlib.pyplot as plt
from aguaclara.research.procoda_parser import *
import pandas as pd
from scipy import special
from scipy.optimize import curve_fit
import collections

# Number 1

#The following file is from a CMFR
CMFR_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/1%20CMFR.xls'

# find the row after the last note in the file. This assumes that the last note marks the beginning of the test.
epa.notes(CMFR_path)
CMFR_firstrow = epa.notes(CMFR_path).last_valid_index() + 1
CMFR_firstrow

#I eliminate the beginning of the data file because this is a CMFR and the
#first data was taken before the dye reached the sensor. Note that eliminating
#some data from the beginning of the data file will not change the analysis
#except in the estimate of the initial tracer mass.#
CMFR_firstrow = CMFR_firstrow + 10

CMFR_time_data = (epa.column_of_time(CMFR_path,CMFR_firstrow,-1)).to(u.s)
CMFR_concentration_data = epa.column_of_data(CMFR_path,CMFR_firstrow,1,-1,'mg/L')

# CMFR volume and flowrate
CMFR_V = (2.590-.596)*u.L
CMFR_Q = 380 * u.mL/u.min

#here we set estimates that we will use as starting values for the curve fitting
CMFR_theta_hydraulic = (CMFR_V/CMFR_Q).to(u.s)
CMFR_C_bar_guess = np.max(CMFR_concentration_data)

#The Solver_CMFR_N will return the initial tracer concentration,
#residence time, and number of reactors in series.
#This experiment was for a single reactor and so we expect N to be 1!
CMFR_CMFR = epa.Solver_CMFR_N(CMFR_time_data, CMFR_concentration_data, CMFR_theta_hydraulic, CMFR_C_bar_guess)
#use dot notation to get the 3 elements of the tuple that are in CMFR.

print('The model estimated mass of tracer injected was',ut.round_sf(CMFR_CMFR.C_bar*CMFR_V ,2) )
print('The model estimate of the number of reactors in series was', CMFR_CMFR.N)
print('The tracer residence time was',ut.round_sf(CMFR_CMFR.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(CMFR_CMFR.theta/CMFR_theta_hydraulic).magnitude)

#create a model curve given the curve fit parameters.

CMFR_CMFR_model = CMFR_CMFR.C_bar * epa.E_CMFR_N(CMFR_time_data/CMFR_CMFR.theta,CMFR_CMFR.N)
plt.plot(CMFR_time_data.to(u.min), CMFR_concentration_data.to(u.mg/u.L),'r')
plt.plot(CMFR_time_data.to(u.min), CMFR_CMFR_model,'b')

plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model'])
#plt.savefig('Examples/images/CMFR.png', bbox_inches = 'tight')
plt.show()

#Load a data file for a reactor with baffles.

CMFRs_with_24baffles_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/4%20CMFRs%20w%2024%20holes.xls'
holes24_baffle_firstrow = epa.notes(CMFRs_with_24baffles_path).last_valid_index() + 1
one_baffle_time_data = (epa.column_of_time(CMFRs_with_24baffles_path,holes24_baffle_firstrow,-1)).to(u.s)
one_baffle_concentration_data = epa.column_of_data(CMFRs_with_24baffles_path,holes24_baffle_firstrow,1,-1,'mg/L')

#I noticed that the initial concentration measured by the photometer wasn't
#zero. This suggests that there may have been a small air bubble in the
#photometer or perhaps there was some other anomoly that was causing the
#photometer to read a concentration that was higher than was actually present in
#the reactor. To correct for this I subtracted the initial concentration reading
#from all of the data. This was based on the assumption that the concentration
#measurement error persisted for the entire experiment.#

one_baffle_concentration_data = one_baffle_concentration_data - one_baffle_concentration_data[0]
one_baffle_V = 2.25*u.L
one_baffle_Q = 380 * u.mL/u.min
one_baffle_theta_hydraulic = (one_baffle_V/one_baffle_Q).to(u.s)
one_baffle_C_bar_guess = np.max(one_baffle_concentration_data)/2
#use solver to get the CMFR parameters
one_baffle_CMFR = epa.Solver_CMFR_N(one_baffle_time_data, one_baffle_concentration_data, one_baffle_theta_hydraulic, one_baffle_C_bar_guess)
one_baffle_CMFR.C_bar
one_baffle_CMFR.N
one_baffle_CMFR.theta.to(u.s)

#Create the CMFR model curve based on the scipy.optimize curve_fit
#parameters. We do this with dimensions so that we can plot both models and
#the data on the same graph. If we did this in dimensionless space it wouldn't
#be possible to plot everything on the same plot because the values used to
#create dimensionless time and dimensionless concentration are different for
#the two models.
one_baffle_CMFR_model = (one_baffle_CMFR.C_bar*epa.E_CMFR_N(one_baffle_time_data/one_baffle_CMFR.theta, one_baffle_CMFR.N)).to(u.mg/u.L)

#use solver to get the advection dispersion parameters
one_baffle_AD = epa.Solver_AD_Pe(one_baffle_time_data, one_baffle_concentration_data, one_baffle_theta_hydraulic, one_baffle_C_bar_guess)
one_baffle_AD.C_bar
one_baffle_AD.Pe
one_baffle_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(one_baffle_AD.C_bar*one_baffle_V ,2) )
print('The model estimate of the Peclet number was', one_baffle_AD.Pe)
print('The tracer residence time was',ut.round_sf(one_baffle_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(one_baffle_AD.theta/one_baffle_theta_hydraulic).magnitude)

#Create the advection dispersion model curve based on the solver parameters
one_baffle_AD_model = (one_baffle_AD.C_bar*epa.E_Advective_Dispersion((one_baffle_time_data/one_baffle_AD.theta).to_base_units(), one_baffle_AD.Pe)).to(u.mg/u.L)

#Plot the data and the two model curves.
plt.plot(one_baffle_time_data.to(u.s), one_baffle_concentration_data.to(u.mg/u.L),'r')
plt.plot(one_baffle_time_data.to(u.s), one_baffle_CMFR_model,'b')
plt.plot(one_baffle_time_data.to(u.s), one_baffle_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
#plt.savefig('Examples/images/Dispersion.png', bbox_inches = 'tight')
plt.show()



```
