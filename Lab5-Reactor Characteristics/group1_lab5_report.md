# Reactor Characteristics
#### Group 1- Jiwon Lee and Rosie Krasnoff (12 hours each)
##### Due March 27

## Introduction and Objectives

In the world of environmental engineering, reactors are ubiquitous. Everything from bodies of water, such as lakes, in nature, to settling tanks in treatment plants are "reactors" that allow chemical, biological, and physical processes to take place. One factor that engineers consider when working with reactors is the mixing level and the residence time. For instance, chlorine contactor tanks in water treatment are built to maximize the residence time of water in the tank to optimize the contact time between chlorine and pathogens. This experiment allows us to use tracer studies, with #40 Red Dye, to obtain estimates of the effective contact time by analyzing different reactor designs. Through this lab, we hope to modify the reactor to obtain a maximum value of t⋆ at F = 0.1, document our progress toward this goal by obtaining appropriate experimental data, and compare our experimental data with appropriate models.

Below are relevant equations:

$$E_{\left(t\right)}=\frac{C_t{\rlap{-} V }_r}{C_{tr}{\rlap{-} V }_{tr}}=e^{\left(-t/\theta \right)}$$

This equation allowed us to solve for E, the exit age distribution, by multiplying the concentration data by the volume of the reactor divided by the pulse input of the tracer.

$$F_{\left(t^{\star} \right)} =\int _{0}^{t^{\star} }E_{\left(t^{\star} \right)} dt^{\star}$$

This equation gave us the F (cumulative exit age) curve.

## Procedures

In the Reactor Characteristics lab, we performed multiple tests with different reactors to measure the reactor volume, residual reactor red dye concentration, and the flow rate. We set up the reactor system to pump distilled water from a 20 L Jerry can to the influent of the reactor, which is placed on a stir plate, and drained out with a straight short tube. Then, we proceeded to add a volume of red dye #40 stock that will give a maximum concentration of approximately 30 mg/L near the influent of the reactor and collected data until the majority of the tracer has exited. Finally, we repeated these steps for various types of reactors, including alternating CMFRs in series as well as a PFR. For a more detail procedure, refer to the [textbook](https://monroews.github.io/EnvEngLabTextbook/Reactor_Characteristics/Reactor_Characteristics.html).


## Results and Discussion
### Data Analysis

We used multivariable nonlinear regression to obtain the best fit between the experimental data and the two models by minimizing the sum of the squared errors. Using epa.Solver_AD_Pe and epa.Solver_CMFR_N, we minimized the error by varying the values of average residence time, (mass of tracer/reactor volume), and either the number of CMFR in series or the Peclet number.

For the first test, we just looked at a simple CMFR, with a pulse input of dye. The concentration of the red dye over time followed the expected path, and matched fairly well with the model (Figure 1). The model estimate of the number of reactors in series was 1, which is clearly correct and a good check that this model is working.

![trial 1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/CMFR.png?raw=true)

Figure 1. Plot showing the simple CMFR experimental data and the CMFR model.

For the second test, we modeled 4 CMFRs in series, using three baffles with 24 holes. The concentration of red dye followed the CMFR model, as expected, for the most part except the small dip in the beginning, presumably due to an air bubble near the photometer (Figure 2). Both the models are a close fit, the CMFR model is slightly more successful in capturing the shape of the curve after the peak better than the AD model in this case. The model estimate of the number of reactors in series was 1.61 and the estimate of the Peclet number was 1.22. The estimate for the number of reactors is pretty low, the estimate being under 2 when the actual system had 4, but this was likely due to the fact that there were "short cuts" through the holes in the baffles and around the edges that meant the reactor was a lot more mixed than 4 separate CMFRs would be.

![trial 2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/4_CMFR_with_holes.png?raw=true)

Figure 2. Plot showing the 4 CMFR experimental data and the CMFR and AD model.

For the third test, we modeled 3 CMFRs in series, using two baffles with gaps on alternating sides. The concentration of red dye followed the AD model pretty closely by accurately modeling the initial increase in dye concentration with the addition of the pulse input (Figure 3). The model estimate of the number of reactors in series was 3.01 and the estimate of the Peclet number was 4.04. In this experiment we were more careful about closing up leaks to prevent mixing between baffles other than in the gaps that were left on purpose. Thus, our data was much closer to an ideal system of 3 CMFRs and the model was able to very accurately predict the number of reactors in series.

![trial 3](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/3_CMFR_alternating.png?raw=true)

Figure 3. Plot showing the 3 alternating CMFR experimental data and the CMFR and AD model.

Similarly, for the fourth test, we modeled 4 CMFRs in series, using three baffles with gaps on alternating sides (Image 1). The concentration of red dye followed the AD model better as it captures the initial increase in concentration more accurately (Figure 4). The model estimate of the number of reactors in series was 3.67 and estimate of the Peclet number was 5.48. Although 3.67 is a pretty good approximation for this reactor, the data may have suffered from potential "dead volumes" or leaks along the system.


<img src="https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/Pictures/4%20CMFR.JPG?raw=true" width = 800/>

Image 1. Well-mixed 4 CMFRs with alternating baffles.

![trial 4](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/4_CMFR_alternating.png?raw=true)

Figure 4. Plot showing the 4 alternating CMFR experimental data and the CMFR and AD model.

Lastly, we modeled a plug flow reactor using a ~100ft long , 1/4 in tubing (Image 2). Both models reflect the measured dye concentration to the same degree of accuracy as they follow the exact same curves (Figure 5). The model estimate of the number of reactors in series was 70.71 and the estimate of the Peclet number was 139.17. Since PFRs are ideally equivalent to an infinite number of CMFRs in series, 70 was along the lines of what we expected for this test.




<img src="https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/Pictures/PFR%20running.JPG?raw=true" width = 300/>

Image 2. PFR reactor as well-mixed fluid runs through.

![trial 5](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/PFR.png?raw=true)

Figure 5. Plot showing the PFR experimental data and the CMFR and AD model.

Comparing the trends in the estimated values of N and Pe across the experiments, our reactor modifications decreased dispersion in our reactors. As we increased the number of reactors in series by either adding additional baffles or modeling a plug flow, the Peclet number increased as expected. As the Peclet number increases the dispersion decreases and the response becomes closer to plug flow. This matches with our model estimate of the Peclet number for PFR since it was the highest of all 5 trials.

To find the length of time before dye started coming out in the effluent, we made E and F graphs for each of the five trials. With these graphs one can visualize both the concentrations of red dye in the reactor and the amount of time in takes for all the dye to travel throughout the reactor.

For the first test, the t* when F=0.1, which is how long it takes for 10% of the dye to leave, was 0.06352.

![trial 1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/1-E_and_F.png?raw=true)

Figure 6. Exit age (E) and Cumulative exit age (F) curves for a simple CMFR.

For the second test, the t* when F=0.1 was 0.2066.

![trial 2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/2-E_and_F.png?raw=true)

Figure 7. Exit age (E) and Cumulative exit age (F) curves for 4 CMFRs with 24 holes.

For the third test, the t* when F=0.1 was 0.3051.

![trial 3](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/3-E_and_F.png?raw=true)

Figure 8. Exit age (E) and Cumulative exit age (F) curves for 3 alternating CMFRs.

For the fourth test, the t* when F=0.1 was 0.3426.

![trial 4](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/4-E_and_F.png?raw=true)

Figure 9. Exit age (E) and Cumulative exit age (F) curves for 4 alternating CMFRs.

For the last test, the t* when F=0.1 was 0.9414.

![trial 5](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/5-E_and_F.png?raw=true)

Figure 10. Exit age (E) and Cumulative exit age (F) curves for a PFR.

The normalized time increases as we improved our reactor, which is what we would expect. The t* was 0.06352 for a simple CMFR, 0.2066 for 4 CMFRs with 24 holes, 0.3051 for 3 alternating CMFRs, 0.3426 for 4 alternating CMFRs, and 0.9414 for a PFR. This makes sense because with each improvement (added or alternating baffles), the dye spends a longer time in the reactor. However, it's important to note that F should approach 1.0 - it's an indication that all the dye has left the reactor - but all of our models have failed to do so since the graphs show our F curves either less than or greater than 1.0. There are lots of calculations and approximations that go into finding F, so there are many places that this error may arise from. E is calculated using the hydraulic retention time, which is calculated from our measured volume and the approximate flow rate. The flow rate was just approximated, not measured, so there could certainly be error from that. Also, there are two calculations from theta, the method just mentioned and also the estimate from the model, so those two different estimates give different F plots.

There were definitely evidences of "dead volumes" in our reactors. In both of the alternating CMFR models, there were areas - specifically near the edges of the baffles - that never had any contact time with the red dye.

For the 4 CMFRs with 24 holes, the predicted theta from our volume and flow rate is 314.7 seconds and the theta from the AD model is 142.2 seconds. This means that the dye left the reactor much quicker than was expected based just on the flow rate and volume. This is because there were flow paths possible through the reactor that allowed the dye to "short circuit" and not actually get mixed in the reactor. Thus, some of the dye was able to leave the reactor much sooner than predicted. This same phenomenon occurred in the next two trials as well:
- For the 3 alternating CMFRs, the predicted theta from our volume and flow rate is 327.6 second and the theta from the AD model is 202.2 seconds
- For the 4 alternating CMFRs, the predicted theta from our volume and flow rate is 306.5 seconds and the theta from the AD model is 213.8 seconds.

For the PFR, we would expect very little dead volume, because the dye is moving through the tube and dye comes out faster than we though it would. This somewhat lines up with our output that the predicted theta from our volume and flow rate is 80 seconds and the theta from the AD model is 64.79 seconds; however, we do not actually know the volume of the PFR and used a rough estimate, so it is possible that these values would actually be closer if we knew the exact length of the tubing and could calculate the exact volume.

### Recommendation
From our five trials, we would conclude that the plug flow reactor allowed the most optimal contact time between the water and the red dye. We varied how long and/or direct the path to the exit from the influent was. The longer the path, the better the reactor. An ideal chlorine contact tank would maximize the residence time of water in the tank to optimize the contact time between chlorine and pathogens. In an ideal world, we would want to have a really long pipe as a chlorine contact chamber. Obviously, this is not realistic because that requires a lot of space and dosage is complicated in a closed system without an opening. Thus, we would turn to our next best option - CMFRs in series with alternating baffles. The idea would be to use many walls within a large tank to create a long snaking channel for the water to travel through. The system should maximize the time the chlorine spends in the reactor by making the path to the effluent winding.

## Conclusion
In the Reactor Characteristics lab, we compared different reactor models to test what the most ideal system would be to optimize the hydraulic residence time of red dye in contact with the water in the reactor. First, we observed that both the CMFR and the advective dispersion model were quite good matches for the data that we recorded. We were also able to observe that the CMFR did a reasonably good job at computing the number of CMFRs we had if the system was designed well and didn't have leaks or shortcut flows. We found that as we increased the number of reactors in series by either adding more baffles, alternating them by adding gaps, or using a tube, the Peclet number increased as expected. This makes sense because as the Peclet number increases, the response becomes closer to plug flow and dispersion decreases as a result. Lastly, the normalized time spent in the reactor increases as we improved our reactor. Thus, we can conclude that the contact time increased as the reactors had longer paths from the influent to the effluent. Due to physical and monetary constraints, we recommend using many baffles in a large tank when building a chlorine contact chamber to create a long, snaking path.

## Suggestions/Comments
The lab manual asked us to pump **tap water** from a 20 L Jerrican to the influent of your reactor. However, this was not the case. **Distilled water** was actually needed for the experiment and we had to redo our trial because we started to pump tap water into our reactor. Other than that, this lab was easy to follow! After being successful with our plug flow reactor model, we would recommend that more students should experiment with it! It would be useful to do more development of the PFR and figure out how to get dye in without getting air bubbles, which we certainly struggled with.

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
plt.xlabel(r'$time (sec)$')
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
plt.xlabel(r'$time (sec)$')
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
plt.xlabel(r'$time (sec)$')
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
trial5_V = .400*u.L
trial5_Q = 300 * u.mL/u.min
trial5_theta_hydraulic = (trial5_V/trial5_Q).to(u.s)
trial5_theta_hydraulic
trial5_C_bar_guess = np.max(trial5_concentration_data)/2
#use solver to get the CMFR parameters

#edit function, change solver to assume 50 CMFRs instead of 1
def Solver_CMFR_N_PFR(t_data, C_data, theta_guess, C_bar_guess):
    """Use non-linear least squares to fit the function
    Tracer_CMFR_N(t_seconds, t_bar, C_bar, N), to reactor data.
    Parameters
    ----------
    t_data : float list
        Array of times with units
    C_data : float list
        Array of tracer concentration data with units
    theta_guess : float
        Estimate of time spent in one CMFR with units.
    C_bar_guess : float
        Estimate of average concentration with units
        (Mass of tracer)/(volume of one CMFR)
    Returns
    -------
    tuple
        theta : float
            residence time in seconds
        C_bar : float
            average concentration with same units as C_bar_guess
        N : float
            number of CMFRS in series that best fit the data
    """
    C_unitless = C_data.magnitude
    C_units = str(C_bar_guess.units)
    t_seconds = (t_data.to(u.s)).magnitude
    # assume that a guess of 50 reactors in series is close enough to get a solution
    p0 = [theta_guess.to(u.s).magnitude, C_bar_guess.magnitude,50]
    popt, pcov = curve_fit(epa.Tracer_CMFR_N, t_seconds, C_unitless, p0)
    Solver_theta = popt[0]*u.s
    Solver_C_bar = popt[1]*u(C_units)
    Solver_N = popt[2]
    Reactor_results = collections.namedtuple('Reactor_results','theta C_bar N')
    CMFR = Reactor_results(theta=Solver_theta, C_bar=Solver_C_bar, N=Solver_N)
    return CMFR

trial5_CMFR = Solver_CMFR_N_PFR(trial5_time_data, trial5_concentration_data, trial5_theta_hydraulic, trial5_C_bar_guess)
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
plt.plot(trial5_time_data.to(u.s), trial5_concentration_data.to(u.mg/u.L),'or')
plt.plot(trial5_time_data.to(u.s), trial5_CMFR_model,'b')
plt.plot(trial5_time_data.to(u.s), trial5_AD_model,'g')
plt.xlabel(r'$time (sec)$')
plt.ylabel(r'Concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['Measured dye','CMFR Model', 'AD Model'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab5-Reactor Characteristics/PFR.png', bbox_inches = 'tight')
plt.show()


#Number 3

#Trial 1
t_star1 = CMFR_time_data/CMFR_theta_hydraulic # hydraulic residence time
E1 = CMFR_concentration_data.to(u.mg/u.L)*CMFR_V/CMFR_CMFR.C_bar
F1 = integrate.cumtrapz(E1,t_star1, initial=0)
plt.plot(t_star1,E1,'r')
plt.plot(t_star1,F1,'g')
plt.xlabel(r't*')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/1-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Trial 2
t_star2 = trial2_time_data/trial2_theta_hydraulic # hydraulic residence time
E2 = trial2_concentration_data.to(u.mg/u.L)*trial2_V/trial2_AD.C_bar
F2 = integrate.cumtrapz(E2,t_star2, initial=0)
plt.plot(t_star2,E2,'r')
plt.plot(t_star2,F2,'g')
plt.xlabel(r't*')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/2-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Trial 3
t_star3 = trial3_time_data/trial3_theta_hydraulic # hydraulic residence time
E3 = trial3_concentration_data.to(u.mg/u.L)*trial3_V/trial3_AD.C_bar
F3 = integrate.cumtrapz(E3,t_star3, initial=0)
plt.plot(t_star3,E3,'r')
plt.plot(t_star3,F3,'g')
plt.xlabel(r't*')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/3-E_and_F.png', bbox_inches = 'tight')
plt.show()


#Trial 4
t_star4 = trial4_time_data/trial4_theta_hydraulic # hydraulic residence time
E4 = trial4_concentration_data.to(u.mg/u.L)*trial4_V/trial4_AD.C_bar
F4 = integrate.cumtrapz(E4,t_star4, initial=0)
plt.plot(t_star4,E4,'r')
plt.plot(t_star4,F4,'g')
plt.xlabel(r't*')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/4-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Trial 5
t_star5 = trial5_time_data/trial5_theta_hydraulic # hydraulic residence time
t_star5 = trial5_time_data/trial5_AD.theta
E5 = trial5_concentration_data.to(u.mg/u.L)*trial5_V/trial5_AD.C_bar
F5 = integrate.cumtrapz(E5,t_star5, initial=0)
plt.plot(t_star5,E5,'r')
plt.plot(t_star5,F5,'g')
plt.xlabel(r't*')
plt.ylabel(r'exit age')
plt.legend(['E','F'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/5-E_and_F.png', bbox_inches = 'tight')
plt.show()

#Number 4
#write a function to find the time when F = 0.1
#looks through array and find values

#Trial 1
desired_F = 0.1
for i in range(CMFR_concentration_data.size):
    if F1[i-1] < desired_F and F1[i] > desired_F:
      desired_t_star1 = t_star1[i]

print('The t* when F=0.1, which is how long it takes for 10% of the dye to leave, is', desired_t_star1)

#Trial 2
desired_F = 0.1
for i in range(trial2_concentration_data.size):
    if F2[i-1] < desired_F and F2[i] > desired_F:
      desired_t_star2 = t_star2[i]

print('The t* when F=0.1, which is how long it takes for 10% of the dye to leave, is', desired_t_star2)

#Trial 3
desired_F = 0.1
for i in range(trial3_concentration_data.size):
    if F3[i-1] < desired_F and F3[i] > desired_F:
      desired_t_star3 = t_star3[i]

print('The t* when F=0.1, which is how long it takes for 10% of the dye to leave, is', desired_t_star3)

#Trial 4
desired_F = 0.1
for i in range(trial4_concentration_data.size):
    if F4[i-1] < desired_F and F4[i] > desired_F:
      desired_t_star4 = t_star4[i]

print('The t* when F=0.1, which is how long it takes for 10% of the dye to leave, is', desired_t_star4)

#Trial 5
desired_F = 0.1
for i in range(trial5_concentration_data.size):
    if F5[i-1] < desired_F and F5[i] > desired_F:
      desired_t_star5 = t_star5[i]

print('The t* when F=0.1, which is how long it takes for 10% of the dye to leave, is', desired_t_star5)


# Number 5
# comparing predicted theta and theta from the data


#Trial 2
print('The predicted theta from our volume and flow rate is', trial2_theta_hydraulic)
print('The theta from the AD model is', trial2_AD.theta)

#Trial 3
print('The predicted theta from our volume and flow rate is', trial3_theta_hydraulic)
print('The theta from the AD model is', trial3_AD.theta)

#Trial 4
print('The predicted theta from our volume and flow rate is', trial4_theta_hydraulic)
print('The theta from the AD model is', trial4_AD.theta)

#Trial 5
print('The predicted theta from our volume and flow rate is', trial5_theta_hydraulic)
print('The theta from the AD model is', trial5_AD.theta)

```
