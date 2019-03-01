# Acid Rain and Acid Neutralizing Capacity

#### Group 1 - Jiwon Lee and Rosie Krasnoff
##### March 1st, 2019

## Introduction and Objectives


## Procedures

## Results and Discussion

## Acid Rain Data Analysis
1. Plot measured pH of the lake versus dimensionless hydraulic residence time (t/θ).

![pHgraph1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph1.png?raw=true)

Figure 1: Plot of concentration pH of lake as acid rain was added over time.

2. Assuming that the lake can be modeled as a completely mixed flow reactor and that ANC is a conservative parameter, equation (25) can be used to calculate the expected ANC in the lake effluent as the experiment proceeds. Graph the expected ANC in the lake effluent versus the hydraulic residence time (t/θ) based on the completely mixed flow reactor equation with the plot labeled (in the legend) as conservative ANC.
3. If we assume that there are no carbonates exchanged with the atmosphere during the experiment, then we can calculate ANC in the lake effluent by using equation (14) describing the ANC of a closed system. Calculate the ANC under the assumption of a closed system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as closed ANC.
4. If we assume that there is exchange with the atmosphere and that carbonates are at equilibrium with the atmosphere, then we can calculate ANC in the lake effluent by using equation (18) describing the ANC of an open system. Calculate the ANC under the assumption of an open system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as open ANC.

![ANCgraphcomp1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_ANC_comp.png?raw=true)

Figure 2: Plot of concentration calculated ANC over time from conservative, closed, and open calculations.

**Was the lake better modeled as in equilibrium with atmospheric CO2 or as not exchanging with atmospheric CO2?**  

5. Analyze the data from the second experiment and graph the data appropriately. What did you learn from the second experiment?

In the second experiment, we added about half as much NaHCO3 as we added in the first experiment. Therefore, it had a lower ANC and so the lake was destroyed and unlivable in a shorter amount of time. The ANC worked the same way, it was just less, so less acid could be added from the rain before the pH fell drastically.

![pHgraph2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph2.png?raw=true)

Figure 3: Plot of concentration pH of lake as acid rain was added over time for second experiment with about half as much NaHCO3 (0.317g).

![ANCgraphcomp2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_ANC_comp2.png?raw=true)

Figure 4: Plot of concentration calculated ANC over time from conservative, closed, and open calculations for second experiment with about half as much NaHCO3(0.317g).

## ANC Data Analysis
1. Plot the titration curve of the t=0 sample with 0.05 N HCl (plot pH as a function of titrant volume). Label the equivalent volume of titrant. Label the 2 regions of the graph where pH changes slowly with the dominant reaction that is occurring. (Place labels with the chemical reactions on the graph in the pH regions where each reaction is occurring.) Note that in a third region of slow pH change no significant reactions are occurring (added hydrogen ions contribute directly to change in pH).

![part1graph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab3-ANC/titrationcurve.png?raw=true)

In a region that occurs at a higher pH than we saw, the reaction $HCO_3^- <-> CO_3^2- + H^+$ would be occurring first. In the no reaction region, added hydrogen ions contribute directly to change in pH as noted in question prompt.

2. Prepare a Gran plot using the data from the titration curve of the t=0 sample. Use linear regression on the linear region or simply draw a straight line through the linear region of the curve to identify the equivalent volume. Compare your calculation of Ve with that was calculated by ProCoDA.

The Ve that we calculated using linear regression was 1.433 mL, which is essentially identical to that of ProCoDA at 1.433219 mL.


![part2graph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab3-ANC/Granplot.png?raw=true)

Figure 6. Gran titration of a sample.

3. Plot the measured ANC of the lake on the same graph as was used to plot the conservative, volatile, and nonvolatile ANC models (see questions 2 to 5 of the Acid Precipitation and Remediation of an Acid Lake lab). Did the measured ANC values agree with the conservative ANC model?

Although not identical, the measured ANC agrees pretty well with the conservative ANC model.

https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab3-ANC/ANC_comp_data_plot.png?raw=true


## Answers to Acid Rain Questions
1. If the experiment was repeated with the stirrer were turned off, it would cause the NaHCO3 to simply sink to the bottom of the lake since its density = 2.2g/cm3 is higher than that of the lake. Some of the NaHCO3 will dissolve as it sinks, but even dissolved into water, it makes a more dense solution so that solution will also sink to the bottom. So, there will be less ANC at the top of the lake, where the acid is then added. Thus, the solution will acidify at the top faster than we saw with the stirrer turned on because the ANC will not be evenly distributed and the top of the lake will be lacking.

2. Some complications of attempting to remediate a lake with CaCO3 include the density of CaCO3 is 2.71 g/cm³, which is higher than that of NaHCO3 at 2.2g/cm³, so it sinks quicker. This will exacerbate the issues discussed in question 1 above, where there will be a gradient of ANC because of the higher density. This problem will be made worse if there is no mixing. The solubility of CaCO3 is also much lower than that of NaHCO3, so even if one calculated how much CaCO3 to add to get the same ANC as we got from NaHCO3, the particles would likely not all dissolve, and therefore the actual ANC of the solution would not be as high as expected.

## Conclusion

In this lab, we replicated the effects of acid lake remediation in the form of sodium bicarbonate by adding enough to equal the negative ANC from the acid precipitation input plus the amount of ANC lost by outflow from the lake during the 15-minute design period. In this experiment, we saw that the ANC in all three cases (conservative, closed, and open) took an hydraulic residence time of approximately 1.1 to hit zero. The same pattern was observed when only half the amount of NaHCO3 was added - about 0.7 hydraulic residence time passed before the three ANCs approached 0.  

## Suggestions/Comments
We had complications with ProCoDa not saving our data properly, which then caused more problems because the data file could not be read easy when it was edited. Students should be warned to verify that data is saving properly before beginning experiments. Also, we had several leaks in our system because we weren't using the connectors properly (needed to twist and push to get a tighter fit). A warning about that would be helpful.  We would appreciate more clarity on what the expectations are for the lab report/postlab. What is the extent of "data analysis" that is expected and how should we be presenting it?

## Appendix

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

##ACID RAIN PORTION
#Number 1
#push the data file to your github and then get the url of the raw file.
data_file_path="https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab2-Acid%20Rain/Lab_2_Acid_Rain.xls"
# set the start index
start=26
#The pH data is in column 1
column=1
#help(epa.column_of_data)
lakepH=epa.column_of_data(data_file_path, start, 1, -1)

#extract the corresponding time data and convert to seconds
time = epa.column_of_time(data_file_path,start,-1).to(u.min)
Vol= 3.938*u.L #  volume of lake
q = 5.15*u.mL/u.sec # flow of acid into lake
q=q.to(u.L/u.min)

#extract the corresponding time data and convert to seconds
time = epa.column_of_time(data_file_path,start,-1).to(u.min)
residencetime = Vol/q # hydraulic residence time t/θ
hrt = time/residencetime
#Now plot the graph
fig, ax = plt.subplots()
ax.plot(hrt,lakepH,'r')
lakepH
plt.xlabel('hydraulic residence time')
plt.ylabel('pH')

#plt.savefig('/Users/Rosie/github/CEE4530/Lab2-Acid Rain/lab2_pHgraph1.png')
plt.show()

#Number 2
#ANC_expected=[ANC_out−ANC_in⋅(1−e^−t/θ)]e^t/θ
#to find ANCo: we added .628 g of NaH2CO3
mass_NA=.628*u.g
MM_NaH2CO3 = 84.01*u.g/u.mol

ANC_0=mass_NA/MM_NaH2CO3/Vol
ANC_expected=epa.ANC_open(3)*(1-(np.exp(-hrt)))+(ANC_0*(np.exp(-hrt)))

#fig, ax = plt.subplots()
#ax.plot(hrt,ANC_expected,'b')
#plt.xlabel('hydraulic residence time (min)')
#plt.ylabel('ANC conservative')
#plt.show()

#Number 3
carbs=ANC_0
ANC_closed=epa.ANC_closed(lakepH,carbs)
#fig, ax = plt.subplots()
#ax.plot(hrt,ANC_closed,'g')
#plt.xlabel('hydraulic residence time (min)')
#plt.ylabel('ANC closed')
#plt.show()

#Number 4
#ANC_effluent=(PCO2*KH)/α0*(α1+2α2)+Kw/[H+]−[H+]

ANC_effluent = epa.ANC_open(lakepH)
#fig, ax = plt.subplots()
#ax.plot(hrt,ANC_effluent,'b')
#plt.xlabel('hydraulic residence time (min)')
#plt.ylabel('ANC open')
#plt.show()

# plotting all the ANCs together
ANC_graph=np.linspace(0,1.6,40)
fig, ax = plt.subplots()
ax.plot(hrt, ANC_expected.to(u.meq/u.L), 'r', hrt, ANC_closed.to(u.meq/u.L), 'g', hrt, ANC_effluent.to(u.meq/u.L), 'b')
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC (meq/L)')
plt.legend(['ANC conservative', 'ANC closed', 'ANC open'])
#plt.savefig('/Users/Rosie/github/CEE4530/Lab2-Acid Rain/lab2_ANC_comp.png')
plt.show()

#Number 5
data_file_path="https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab2-Acid%20Rain/Lab_2_Acid_rain_with_half_ANC.xls"
# set the start index
start=17
#The pH data is in column 1
column=1
#help(epa.column_of_data)
lakepH2=epa.column_of_data(data_file_path, start, 1, -1)
v = 3.938*u.L #  volume of lake
q = 5.15*u.mL/u.sec # flow of acid into lake
q=q.to(u.L/u.min)

#extract the corresponding time data and convert to seconds
time2 = epa.column_of_time(data_file_path,start,-1).to(u.min)
residencetime = v/q # hydraulic residence time t/θ
hrt2 = time2/residencetime
#Now plot the graph
fig, ax = plt.subplots()
ax.plot(hrt2,lakepH2,'r')
plt.xlabel('hydraulic retention time')
plt.ylabel('pH')
#plt.savefig('/Users/Rosie/github/CEE4530/Lab2-Acid Rain/lab2_pHgraph2.png')
plt.show()

#Number 5.2
#ANC_expected=[ANC_out−ANC_in⋅(1−e^−t/θ)]e^t/θ
#to find ANCo: added .317 g of NaH2CO3
mass_NA_2=.317*u.g

ANC_02=mass_NA_2/MM_NaH2CO3/Vol
ANC_expected2=epa.ANC_open(3)*(1-(np.exp(-hrt2)))+(ANC_0*(np.exp(-hrt2)))

#Number 5.3
carbs2=ANC_02
ANC_closed2=epa.ANC_closed(lakepH2,carbs)

#Number 5.4
#ANC_effluent=(PCO2*KH)/α0*(α1+2α2)+Kw/[H+]−[H+]
ANC_effluent2 = epa.ANC_open(lakepH2)

# plotting all the ANCs together
ANC_graph=np.linspace(0,1.6,40)
fig, ax = plt.subplots()
ax.plot(hrt2, ANC_expected2.to(u.meq/u.L), 'r', hrt2, ANC_closed2.to(u.meq/u.L), 'g', hrt2, ANC_effluent2.to(u.meq/u.L), 'b')
plt.xlabel('hydraulic residence time')
plt.ylabel('ANC (meq/L)')
plt.legend(['ANC conservative', 'ANC closed', 'ANC open'])
#plt.savefig('/Users/Rosie/github/CEE4530/Lab2-Acid Rain/lab2_ANC_comp2.png')
plt.show()

##ANC LAB PORTION
#Number 1
Gran_data_0 = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab3-ANC/lab%203%20ANC%2C%20t%3D0.xls'
# The epa.Gran function imports data from your Gran data file as saved by ProCoDA.
# The epa.Gran function assigns all of the outputs in one statement
V_titrant_0, pH_0, V_Sample_0, Normality_Titrant_0, V_equivalent_0, ANC_0 = epa.Gran(Gran_data_0)
fig, ax = plt.subplots()
ax.plot(V_titrant_0,pH_0,'r')
ax.grid(True)
plt.xlabel('volume of titrant (mL)')
plt.ylabel('pH')
#ax.annotate('equivalent volume', xy=(1.433219, 2.8), xytext=(0.8, 4), arrowprops=dict(facecolor='black', shrink=0.10),)
plt.axvline(x=V_equivalent_0.magnitude,color='b')
ax.annotate('$HCO_3^- + H^+ <-> H_2CO_3$', xy=(0.75, 6.25), xytext=(0.45, 7), arrowprops=dict(facecolor='black', shrink=0.10),)
ax.annotate('no reaction', xy=(2, 3.2), xytext=(1.7, 5), arrowprops=dict(facecolor='black', shrink=0.10),)
plt.legend(['titration curve', 'equiv titrant vol'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab3-ANC/titrationcurve.png')
plt.show()

#Number 2
#Define the gran function.
def F1(V_sample_0,V_titrant_0,pH_0):
  return (V_sample_0 + V_titrant_0)/V_sample_0 * epa.invpH(pH_0)
#Create an array of the F1 values.
F1_data = F1(V_Sample_0,V_titrant_0,pH_0)

N_good_points = 3
#use scipy linear regression. Note that the we can extract the last n points from an array using the notation [-N:]
slope, intercept, r_value, p_value, std_err = stats.linregress(V_titrant_0[-N_good_points:],F1_data[-N_good_points:])
#reattach the correct units to the slope and intercept.
intercept = intercept*u.mole/u.L
slope = slope*(u.mole/u.L)/u.mL
V_eq = -intercept/slope
ANC_sample = V_eq*Normality_Titrant_0/V_Sample_0
print('The r value for this curve fit is', ut.round_sf(r_value,5))
print('The equivalent volume was', ut.round_sf(V_eq,5))
print('The acid neutralizing capacity was',ut.round_sf(ANC_sample.to(u.meq/u.L),5))

#The equivalent volume agrees well with the value calculated by ProCoDA.
#create an array of points to draw the linear regression line
x=[V_eq.magnitude,V_titrant_0[-1].magnitude ]
y=[0,(V_titrant_0[-1]*slope+intercept).magnitude]
#Now plot the data and the linear regression
plt.plot(V_titrant_0, F1_data,'o')
plt.plot(x, y,'r')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('Gran function (mole/L)')
plt.legend(['data'])
plt.tight_layout()
plt.savefig('/Users/Rosie/github/CEE4530/Lab3-ANC/Granplot.png')
plt.show()

#Number 3
# getting the ANC values at various times
Gran_data_5 = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab3-ANC/lab%203%20ANC%2C%20t%3D5m.xls'
V_titrant_5, pH_5, V_Sample_5, Normality_Titrant_5, V_equivalent_5, ANC_5 = epa.Gran(Gran_data_5)

Gran_data_10 = 'https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab3-ANC/lab%203%20ANC%2C%20t%3D10%202nd%20try%2C%20more%20bad.xls'
V_titrant_10, pH, V_Sample_10, Normality_Titrant_10, V_equivalent_10, ANC_10 = epa.Gran(Gran_data_10)

# at t = 15, we measured pH, ANC=[H+]
pH_15=3.93
ANC_15=-epa.invpH(pH_15)
ANC_15

# at t = 20, we measured pH
pH_20=3.41
ANC_20=-epa.invpH(pH_20)
ANC_20
10**-3.41

# create a vector of ANC of the lake
time_lake=np.array([0,5,10,15,20])*u.min
ANC_lake = np.array([(ANC_0.to(u.meq/u.L)).magnitude, (ANC_5.to(u.meq/u.L)).magnitude, (ANC_10.to(u.meq/u.L)).magnitude, (ANC_15.to(u.meq/u.L)).magnitude, (ANC_20.to(u.meq/u.L)).magnitude])*u.meq/u.L

# plotting all the ANCs together
ANC_graph=np.linspace(0,1.6,40)
fig, ax = plt.subplots()
ax.plot(time, ANC_expected.to(u.meq/u.L), 'r', time, ANC_closed.to(u.meq/u.L), 'g', time, ANC_effluent.to(u.meq/u.L), 'b')
ax.plot(time_lake, ANC_lake, 'o')
plt.xlabel('time (mins)')
plt.ylabel('ANC (meq/L)')
plt.legend(['ANC conservative', 'ANC closed', 'ANC open', 'ANC data points'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab3-ANC/ANC_comp_data_plot.png')
plt.show()
```
