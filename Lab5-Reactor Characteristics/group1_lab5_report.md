# Reactor Characteristics
#### Group 1- Jiwon Lee and Rosie Krasnoff ( hours each)
##### Due March 27

## Introduction and Objectives
## Procedures
## Results and Discussion
### Data Analysis
## Conclusion
## Suggestions/Comments



1. Use multivariable nonlinear regression to obtain the best fit between the experimental data and the two models by minimizing the sum of the squared errors. Use epa.Solver_AD_Pe and epa.Solver_CMFR_N. These functions will minimize the error by varying the values of average residence time, (mass of tracer/reactor volume), and either the number of CMFR in series or the Peclet number.

2. Generate a plot showing the experimental data as points and the model results as thin lines for each of your experiments. Explain which model fits best and discuss those results based on your expectations.

![trial 1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/CMFR.png?raw=true)

Figure 1. Plot showing the simple CMFR experimental data and the CMFR model.

![trial 2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/4_CMFR_with_holes.png?raw=true)

Figure 1. Plot showing the 4 CMFR experimental data and the CMFR model.

In trial 2, the CMFR model fits better and discuss those results based on your expectations.

![trial 3](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/3_CMFR_alternating.png?raw=true)

Figure 1. Plot showing the 3 alternating CMFR experimental data and the CMFR model.

In trial 3, the CMFR model fits better and discuss those results based on your expectations.

![trial 4](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/4_CMFR_alternating.png?raw=true)

Figure 1. Plot showing the 4 alternating CMFR experimental data and the CMFR model.

In trial 4, the CMFR model fits better and discuss those results based on your expectations.

3. Compare the trends in the estimated values of N and Pe across your set of experiments. How did your chosen reactor modifications effect dispersion?

Trial 1: The model estimate of the number of reactors in series was 1.0.

Trial 2: The model estimate of the number of reactors in series was 1.6087605429907506. The model estimate of the Peclet number was 1.2178282957059587.

Trial 3: The model estimate of the number of reactors in series was 3.0132831433153338. The model estimate of the Peclet number was 4.044518749000499.

Trial 4: The model estimate of the number of reactors in series was 3.669886514421101. The model estimate of the Peclet number was 5.479660899821685.


4. Report the values of t⋆ at F = 0.1 for each of your experiments. Do they meet your expectations?




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

5. Evaluate whether there is any evidence of “dead volumes” or “short circuiting” in your reactor.

dye comes out faster than you though it would

6. Make a recommendation for the design of a full scale chlorine contact tank. As part of your recommendation discuss the parameter you chose to vary as part of your experimentation and what the optimal value was determined to be.


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
from scipy import integrate
from sklearn import preprocessing

# Number 1

#Trial 1: simple CMFR
CMFR_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/trial%201.xls'

#find the row after the last note in the file.
epa.notes(CMFR_path)
CMFR_firstrow = epa.notes(CMFR_path).last_valid_index() + 1
CMFR_firstrow

#eliminate the beginning of the data file
CMFR_firstrow = CMFR_firstrow + 10

CMFR_time_data = (epa.column_of_time(CMFR_path,CMFR_firstrow,180)).to(u.s)
CMFR_concentration_data = epa.column_of_data(CMFR_path,CMFR_firstrow,1,180,'mg/L')

#CMFR volume and flowrate
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
plt.savefig('/Users/Rosie/github/CEE4530/Lab5-Reactor Characteristics/CMFR.png', bbox_inches = 'tight')
plt.show()


#Trial 2: 4 CMFRs (3 baffles) with 24 holes each
#Load a data file for a reactor with baffles.
trial2_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/trial%202.xls'
trial2_firstrow = epa.notes(trial2_path).last_valid_index() + 1
trial2_time_data = (epa.column_of_time(trial2_path,trial2_firstrow,-1)).to(u.s)
trial2_concentration_data = epa.column_of_data(trial2_path,trial2_firstrow,1,-1,'mg/L')

#subtract initial concentration from all data to correct
trial2_concentration_data = trial2_concentration_data - trial2_concentration_data[0]
trial2_V = (2.578-.585)*u.L
trial2_Q = 380 * u.mL/u.min
trial2_theta_hydraulic = (trial2_V/trial2_Q).to(u.s)
trial2_C_bar_guess = np.max(trial2_concentration_data)/2
#use solver to get the CMFR parameters
trial2_CMFR = epa.Solver_CMFR_N(trial2_time_data, trial2_concentration_data, trial2_theta_hydraulic, trial2_C_bar_guess)
trial2_CMFR.C_bar
trial2_CMFR.N
trial2_CMFR.theta.to(u.s)
print('The model estimate of the number of reactors in series was', trial2_CMFR.N)

#Create the CMFR model curve based on the scipy.optimize curve_fit
#parameters. We do this with dimensions so that we can plot both models and
#the data on the same graph. If we did this in dimensionless space it wouldn't
#be possible to plot everything on the same plot because the values used to
#create dimensionless time and dimensionless concentration are different for
#the two models.
trial2_CMFR_model = (trial2_CMFR.C_bar*epa.E_CMFR_N(trial2_time_data/trial2_CMFR.theta, trial2_CMFR.N)).to(u.mg/u.L)

#use solver to get the advection dispersion parameters
trial2_AD = epa.Solver_AD_Pe(trial2_time_data, trial2_concentration_data, trial2_theta_hydraulic, trial2_C_bar_guess)
trial2_AD.C_bar
trial2_AD.Pe
trial2_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(trial2_AD.C_bar*trial2_V ,2) )
print('The model estimate of the Peclet number was', trial2_AD.Pe)
print('The tracer residence time was',ut.round_sf(trial2_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(trial2_AD.theta/trial2_theta_hydraulic).magnitude)

#Create the advection dispersion model curve based on the solver parameters
trial2_AD_model = (trial2_AD.C_bar*epa.E_Advective_Dispersion((trial2_time_data/trial2_AD.theta).to_base_units(), trial2_AD.Pe)).to(u.mg/u.L)

#Plot the data and the two model curves.
plt.plot(trial2_time_data.to(u.s), trial2_concentration_data.to(u.mg/u.L),'ro')
plt.plot(trial2_time_data.to(u.s), trial2_CMFR_model,'b')
plt.plot(trial2_time_data.to(u.s), trial2_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
#plt.savefig('Examples/images/Dispersion.png', bbox_inches = 'tight')
plt.savefig('/Users/Rosie/github/CEE4530/Lab5-Reactor Characteristics/4_CMFR_with_holes.png', bbox_inches = 'tight')
plt.show()


#Trial 3: 3 alternating CMFRs
#Load a data file for a reactor with baffles.
trial3_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/trial%203.xls'
trial3_firstrow = epa.notes(trial3_path).last_valid_index() + 1
trial3_time_data = (epa.column_of_time(trial3_path,trial3_firstrow,-1)).to(u.s)
trial3_concentration_data = epa.column_of_data(trial3_path,trial3_firstrow,1,-1,'mg/L')

trial3_concentration_data = trial3_concentration_data - trial3_concentration_data[0]
trial3_V = (2.659-.584)*u.L
trial3_Q = 380 * u.mL/u.min
trial3_theta_hydraulic = (trial3_V/trial3_Q).to(u.s)
trial3_C_bar_guess = np.max(trial3_concentration_data)/2
#use solver to get the CMFR parameters
trial3_CMFR = epa.Solver_CMFR_N(trial3_time_data, trial3_concentration_data, trial3_theta_hydraulic, trial3_C_bar_guess)
trial3_CMFR.C_bar
trial3_CMFR.N
trial3_CMFR.theta.to(u.s)
print('The model estimate of the number of reactors in series was', trial3_CMFR.N)

#Create the CMFR model curve based on the scipy.optimize curve_fit
#parameters. We do this with dimensions so that we can plot both models and
#the data on the same graph. If we did this in dimensionless space it wouldn't
#be possible to plot everything on the same plot because the values used to
#create dimensionless time and dimensionless concentration are different for
#the two models.
trial3_CMFR_model = (trial3_CMFR.C_bar*epa.E_CMFR_N(trial3_time_data/trial3_CMFR.theta, trial3_CMFR.N)).to(u.mg/u.L)

#use solver to get the advection dispersion parameters
trial3_AD = epa.Solver_AD_Pe(trial3_time_data, trial3_concentration_data, trial3_theta_hydraulic, trial3_C_bar_guess)
trial3_AD.C_bar
trial3_AD.Pe
trial3_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(trial3_AD.C_bar*trial3_V ,2) )
print('The model estimate of the Peclet number was', trial3_AD.Pe)
print('The tracer residence time was',ut.round_sf(trial3_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(trial3_AD.theta/trial3_theta_hydraulic).magnitude)

#Create the advection dispersion model curve based on the solver parameters
trial3_AD_model = (trial3_AD.C_bar*epa.E_Advective_Dispersion((trial3_time_data/trial3_AD.theta).to_base_units(), trial3_AD.Pe)).to(u.mg/u.L)

#Plot the data and the two model curves.
plt.plot(trial3_time_data.to(u.s), trial3_concentration_data.to(u.mg/u.L),'or')
plt.plot(trial3_time_data.to(u.s), trial3_CMFR_model,'b')
plt.plot(trial3_time_data.to(u.s), trial3_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab5-Reactor Characteristics/3_CMFR_alternating.png', bbox_inches = 'tight')
plt.show()


#Trial 4: 4 alternating CMFRs
#Load a data file for a reactor with baffles.

trial4_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/trial%204.xls'
trial4_firstrow = epa.notes(trial4_path).last_valid_index() + 1
trial4_time_data = (epa.column_of_time(trial4_path,trial4_firstrow,-1)).to(u.s)
trial4_concentration_data = epa.column_of_data(trial4_path,trial4_firstrow,1,-1,'mg/L')

#I noticed that the initial concentration measured by the photometer wasn't
#zero. This suggests that there may have been a small air bubble in the
#photometer or perhaps there was some other anomoly that was causing the
#photometer to read a concentration that was higher than was actually present in
#the reactor. To correct for this I subtracted the initial concentration reading
#from all of the data. This was based on the assumption that the concentration
#measurement error persisted for the entire experiment.#

trial4_concentration_data = trial4_concentration_data - trial4_concentration_data[0]
trial4_V = (2.529-.588)*u.L
trial4_Q = 380 * u.mL/u.min
trial4_theta_hydraulic = (trial4_V/trial4_Q).to(u.s)
trial4_C_bar_guess = np.max(trial4_concentration_data)/2
#use solver to get the CMFR parameters
trial4_CMFR = epa.Solver_CMFR_N(trial4_time_data, trial4_concentration_data, trial4_theta_hydraulic, trial4_C_bar_guess)
trial4_CMFR.C_bar
trial4_CMFR.N
trial4_CMFR.theta.to(u.s)
print('The model estimate of the number of reactors in series was', trial4_CMFR.N)

#Create the CMFR model curve based on the scipy.optimize curve_fit
#parameters. We do this with dimensions so that we can plot both models and
#the data on the same graph. If we did this in dimensionless space it wouldn't
#be possible to plot everything on the same plot because the values used to
#create dimensionless time and dimensionless concentration are different for
#the two models.
trial4_CMFR_model = (trial4_CMFR.C_bar*epa.E_CMFR_N(trial4_time_data/trial4_CMFR.theta, trial4_CMFR.N)).to(u.mg/u.L)

#use solver to get the advection dispersion parameters
trial4_AD = epa.Solver_AD_Pe(trial4_time_data, trial4_concentration_data, trial4_theta_hydraulic, trial4_C_bar_guess)
trial4_AD.C_bar
trial4_AD.Pe
trial4_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(trial4_AD.C_bar*trial4_V ,2) )
print('The model estimate of the Peclet number was', trial4_AD.Pe)
print('The tracer residence time was',ut.round_sf(trial4_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(trial4_AD.theta/trial4_theta_hydraulic).magnitude)

#Create the advection dispersion model curve based on the solver parameters
trial4_AD_model = (trial4_AD.C_bar*epa.E_Advective_Dispersion((trial4_time_data/trial4_AD.theta).to_base_units(), trial4_AD.Pe)).to(u.mg/u.L)

#Plot the data and the two model curves.
plt.plot(trial4_time_data.to(u.s), trial4_concentration_data.to(u.mg/u.L),'or')
plt.plot(trial4_time_data.to(u.s), trial4_CMFR_model,'b')
plt.plot(trial4_time_data.to(u.s), trial4_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab5-Reactor Characteristics/4_CMFR_alternating.png', bbox_inches = 'tight')
plt.show()


#Trial 5: PFR pump with 0.35 mL of dye (last try)
trial5_path = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab5-Reactor%20Characteristics/reactor%20data/trial%205_PFR.xls'
trial5_firstrow = epa.notes(trial5_path).last_valid_index() + 1
trial5_time_data = (epa.column_of_time(trial5_path,trial5_firstrow,-1)).to(u.s)
trial5_concentration_data = epa.column_of_data(trial5_path,trial5_firstrow,1,-1,'mg/L')

#I noticed that the initial concentration measured by the photometer wasn't
#zero. This suggests that there may have been a small air bubble in the
#photometer or perhaps there was some other anomaly that was causing the
#photometer to read a concentration that was higher than was actually present in
#the reactor. To correct for this I subtracted the initial concentration reading
#from all of the data. This was based on the assumption that the concentration
#measurement error persisted for the entire experiment.#

trial5_concentration_data = trial5_concentration_data - trial5_concentration_data[0]
trial5_V = 400*u.mL
trial5_Q = 380 * u.mL/u.min
trial5_theta_hydraulic = (trial5_V/trial5_Q).to(u.s)
trial5_theta_hydraulic
trial5_C_bar_guess = np.max(trial5_concentration_data)/2
#use solver to get the CMFR parameters
trial5_CMFR = epa.Solver_CMFR_N(trial5_time_data, trial5_concentration_data, trial5_theta_hydraulic, trial5_C_bar_guess)
trial5_CMFR.C_bar
trial5_CMFR.N
trial5_CMFR.theta.to(u.s)

#Create the CMFR model curve based on the scipy.optimize curve_fit
#parameters. We do this with dimensions so that we can plot both models and
#the data on the same graph. If we did this in dimensionless space it wouldn't
#be possible to plot everything on the same plot because the values used to
#create dimensionless time and dimensionless concentration are different for
#the two models.
trial5_CMFR_model = (trial5_CMFR.C_bar*epa.E_CMFR_N(trial5_time_data/trial5_CMFR.theta, trial5_CMFR.N)).to(u.mg/u.L)

#use solver to get the advection dispersion parameters
trial5_AD = epa.Solver_AD_Pe(trial5_time_data, trial5_concentration_data, trial5_theta_hydraulic, trial5_C_bar_guess)
trial5_AD.C_bar
trial5_AD.Pe
trial5_AD.theta

print('The model estimated mass of tracer injected was',ut.round_sf(trial5_AD.C_bar*trial5_V ,2) )
print('The model estimate of the Peclet number was', trial5_AD.Pe)
print('The tracer residence time was',ut.round_sf(trial5_AD.theta ,2))
print('The ratio of tracer to hydraulic residence time was',(trial5_AD.theta/trial5_theta_hydraulic).magnitude)

#Create the advection dispersion model curve based on the solver parameters
trial5_AD_model = (trial5_AD.C_bar*epa.E_Advective_Dispersion((trial5_time_data/trial5_AD.theta).to_base_units(), trial5_AD.Pe)).to(u.mg/u.L)

#Plot the data and the two model curves.
plt.plot(trial5_time_data.to(u.s), trial5_concentration_data.to(u.mg/u.L),'r')
plt.plot(trial5_time_data.to(u.s), trial5_CMFR_model,'b')
plt.plot(trial5_time_data.to(u.s), trial5_AD_model,'g')
plt.xlabel(r'$time (min)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab5-Reactor Characteristics/PFR.png', bbox_inches = 'tight')
plt.show()





#Number 3

#Trial 1
t_star1 = CMFR_time_data/CMFR_theta_hydraulic # hydraulic residence time
E = CMFR_concentration_data.to(u.mg/u.L)*CMFR_V/CMFR_CMFR.C_bar
F = integrate.cumtrapz(E,t_star1, initial=0)
plt.plot(t_star1,E,'r')
plt.plot(t_star1,F,'g')
plt.xlabel(r'hydraulic residence time (t*)')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/1-E_and_F.png', bbox_inches = 'tight')
plt.show()



#Trial 2
t_star2 = trial2_time_data/trial2_theta_hydraulic # hydraulic residence time
E = trial2_concentration_data.to(u.mg/u.L)*trial2_V/trial2_AD.C_bar
F = integrate.cumtrapz(E,t_star2, initial=0)
plt.plot(t_star2,E,'r')
plt.plot(t_star2,F,'g')
plt.xlabel(r'hydraulic residence time (t*)')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/2-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Trial 3
t_star3 = trial3_time_data/trial3_theta_hydraulic # hydraulic residence time
E = trial3_concentration_data.to(u.mg/u.L)*trial3_V/trial3_AD.C_bar
F = integrate.cumtrapz(E,t_star3, initial=0)
plt.plot(t_star3,E,'r')
plt.plot(t_star3,F,'g')
plt.xlabel(r'hydraulic residence time')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/3-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Trial 4
t_star4 = trial4_time_data/trial4_theta_hydraulic # hydraulic residence time
E = trial4_concentration_data.to(u.mg/u.L)*trial4_V/trial4_AD.C_bar
F = integrate.cumtrapz(E,t_star4, initial=0)
plt.plot(t_star4,E,'r')
plt.plot(t_star4,F,'g')
plt.xlabel(r'hydraulic residence time')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/4-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Trial 5
t_star5 = trial5_time_data/trial5_theta_hydraulic # hydraulic residence time
E = trial5_concentration_data.to(u.mg/u.L)*trial5_V/trial5_AD.C_bar
F = integrate.cumtrapz(E,t_star5, initial=0)
plt.plot(t_star5,E,'r')
plt.plot(t_star5,F,'g')
plt.xlabel(r'hydraulic residence time')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/5-E_and_F.png', bbox_inches = 'tight')
plt.show()












# 4
trial4_AD.theta
trial4_theta_hydraulic
t_star = trial4_time_data/trial4_theta_hydraulic
E = trial4_concentration_data.to(u.mg/u.L)*trial4_V/trial4_AD.C_bar
trial4_AD.C_bar

F = integrate.cumtrapz(E,t_star, initial=0)
plt.plot(t_star,F,'g')
plt.show()




```
