# Acid Rain and Acid Neutralizing Capacity

#### Group 1 - Jiwon Lee and Rosie Krasnoff (10 hours each)
##### March 1st, 2019

## Introduction and Objectives
As fossil fuel emissions continuously increase in today’s world, acid precipitation has been worsening as well. Globally, lakes being impacted as the sulfuric and nitric acid in acid rain acidifies these bodies of water. Delving deeper into this widespread issue, it is evident that the pH of the effected lakes is lower than that of a healthy lake in the range of 6.5 to 8.5. This ideal range can be accredited to the natural carbonate system which acts as a buffer and helps to control the pH. However, action needs to be taken for lakes that are no longer healthy on their own. This experiment allows us to explore a common remediation method of applying ANC directly to the lake surface. Through this lab, we aimed to gain information and knowledge about how remediation of applying ANC into a lake would work and the extent to which it is a successful method.

Below are relevant equations:

$$ 1.\;ANC=C_T \left(\alpha_1 +2\alpha_2 \right)+\frac{K_w}{\left[H^+ \right]} - \left[H^+ \right] $$ $$ 2.ANC=\frac{P_{CO_2} K_H }{\alpha_0 } (\alpha_1 +2\alpha_2 ) + \frac{K_w }{\left[H^+ \right]} - \left[H^+ \right]$$$$ 3. \;{ANC}_{{0}} {\; }=\left[{ANC}_{out} - ANC_{in} \cdot \left(1 - {\mathop{e}\nolimits^{-t/\theta}} \right)\right]{\mathop{e}\nolimits^{t/\theta}}$$ $$4. \;ANC=\frac{V_e N_t }{V_s } $$

## Procedures

In the Acid Rain lab, we modeled acid rain precipitating into a lake by pumping an acidic feed solution into a tub of water + NaHCO3 (the ANC). We kept track of the pH level by taking samples from the lake effluent every 5 minutes for 20 minutes. Then we proceeded to repeat the experiment with less NaHCO3 to test the effects of the amount of ANC added to the lake. For a more detail procedure, refer to the [textbook](https://monroews.github.io/EnvEngLabTextbook/Acid_Rain/Acid_Rain.html).

In the ANC lab, we determined the ANC of the five samples we took in the Acid Rain lab. Using a titration process, we added 0.05 N HCl (the titrant) using a digital pipette in increments until the pH reached a certain point. For a more detail procedure, refer to the [textbook](https://monroews.github.io/EnvEngLabTextbook/Acid_Neutralizing_Capacity/Acid_Neutralizing_Capacity.html#theory).

## Results and Discussion
### Acid Rain Data Analysis
We plotted the measured pH of the lake versus dimensionless hydraulic residence time (t/θ) to get a visualization of how pH changed over time (Figure 1).

![pHgraph1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph1.png?raw=true)

Figure 1. Plot of concentration pH of lake as acid rain was added over time.

Calculations were made using three different assumptions for ANC:
1. Assuming that ANC is a **conservative** parameter, equation 3 can be used to calculate the expected ANC in the lake effluent as the experiment proceeds.
2. Assuming there are no carbonates exchanged with the atmosphere during the experiment, then we can calculate ANC in the lake effluent by using equation 1 describing the ANC of a **closed** system.
3. Assuming that there is exchange with the atmosphere and that carbonates are at equilibrium with the atmosphere, then we can calculate ANC in the lake effluent by using equation 2 describing the ANC of an **open** system.

The results of these calculations were plotted versus hydraulic residence time so the three methods could be compared (Figure 2).

![ANCgraphcomp1](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_ANC_comp.png?raw=true)

Figure 2. Plot of concentration calculated ANC over time from conservative, closed, and open calculations.

The lake is better modeled with the assumption that CO2 is not exchanging with the atmosphere, because the closed model is much closer to the conservative model. The conservative model is very good, because it assumes very little, just that ANC is conservative which is a very logical assumption. Therefore, the more closely a model aligns with the conservative model, the better, so the closed model does pretty well.

In the second experiment, we added about half as much NaHCO3 as we added in the first experiment. Therefore, it had a lower ANC and so the lake was destroyed and unlivable in a shorter amount of time. The curve of the pH over time is the same in the first and second experiment, which can be seen in a comparison of Figure 1 and Figure 3. The ANC worked the same way, it was just less, so less acid could be added from the rain before the pH fell drastically. Again, a comparison of different methods of calculating ANC was created, see Figure 4.

![pHgraph2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph2.png?raw=true)

Figure 3. Plot of concentration pH of lake as acid rain was added over time for second experiment with about half as much NaHCO3 (0.317g).

![ANCgraphcomp2](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_ANC_comp2.png?raw=true)

Figure 4. Plot of concentration calculated ANC over time from conservative, closed, and open calculations for second experiment with about half as much NaHCO3(0.317g).

If the experiment was repeated with the stirrer were turned off, it would cause the NaHCO3 to simply sink to the bottom of the lake since its density = 2.2g/cm3 is higher than that of the lake. Some of the NaHCO3 will dissolve as it sinks, but even dissolved into water, it makes a more dense solution so that solution will also sink to the bottom. So, there will be less ANC at the top of the lake, where the acid is then added. Thus, the solution will acidify at the top faster than we saw with the stirrer turned on because the ANC will not be evenly distributed and the top of the lake will be lacking.

Some complications of attempting to remediate a lake with CaCO3 include the density of CaCO3 is 2.71 g/cm³, which is higher than that of NaHCO3 at 2.2g/cm³, so it sinks quicker. This will exacerbate the issues discussed in question 1 above, where there will be a gradient of ANC because of the higher density. This problem will be made worse if there is no mixing. The solubility of CaCO3 is also much lower than that of NaHCO3, so even if one calculated how much CaCO3 to add to get the same ANC as we got from NaHCO3, the particles would likely not all dissolve, and therefore the actual ANC of the solution would not be as high as expected.

### ANC Data Analysis
Using the measured data from the t=0 titration, the pH titration curve was plotted as a function of titrant volume that had been added (Figure 5). The equivalent volume of titrant is labeled with a vertical blue line. If the titration curve was complete, there would be three regions of the graph where pH changes slowly. In two of these regions, the dominant reaction is occurring. In a region that occurs at a higher pH than we saw, the reaction $ HCO_3^- \Rightarrow CO_3^2- + H^+ $ would be occurring first. Because we started at pH 8, we didn't observe that so it isn't in Figure 5. In the second region, the reaction is $HCO_3^- + H^+ \Rightarrow H_2CO_3$. In the third region, there is no reaction, because added hydrogen ions contribute directly to change in pH.

![part1graph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab3-ANC/titrationcurve.png?raw=true)

Figure 5. Titration curve of the t=0 sample with 0.05 N HCl.

Next, using linear regression on the linear region of the data from the titration curve of the t=0 sample, the Gran plot was plotted (Figure 6). Comparing the equivalent volume that we calculated using linear regression with that of ProCoDa, we found that both were essentially identical at 1.433219 mL (see equation 4), suggesting that we likely calculated the value the exact same way as ProCoDA did.

![part2graph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab3-ANC/Granplot.png?raw=true)

Figure 6. Gran titration of a sample.

Finally, a comparison with the 3 ANC models from the Acid Rain portion above was made to the measure ANC from the titration data (Figure 7). A visual assessment suggests that the closed model is the most accurate in comparison to the measured ANC data points. Although not identical, the measured ANC also agrees pretty well with the conservative ANC model.

![part3graph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab3-ANC/ANC_comp_data_plot.png?raw=true)

Figure 7. Plot of conservative, closed, open, and measured ANC concentration over time.

In the ANC lab, we made an error in collecting data in ProCoDa during the titration of the t=10 sample. This may have led to potential errors in our data point at t=10.

## Conclusion
In the Acid Rain lab, we replicated the effects of acid lake remediation in the form of sodium bicarbonate by adding enough to equal the negative ANC from the acid precipitation input plus the amount of ANC lost by outflow from the lake during the 15-minute design period. In this experiment, we saw that the ANC in all three cases (conservative, closed, and open) took an hydraulic residence time of approximately 1.1 to hit zero. The same pattern was observed when only half the amount of NaHCO3 was added - about 0.7 hydraulic residence time passed before the three ANCs approached 0.  

In the ANC lab, we determined the ANC of our five acid rain samples using a titration method by adding in 0.05 N HCl with a pipette. With our t=0 sample, we performed linear regression on our data to obtain a Gran plot. This plot allowed us to find the equivalent titrant volume. Additionally, we did analysis on all five samples to be able to compare the measured ANC data of our five sample points with the three cases mentioned above to conclude that the closed model is the most ideal.

## Suggestions/Comments
With the Acid Rain lab, we had complications with ProCoDa not saving our data properly, which then caused more problems because the data file could not be read easy when it was edited. Students should be warned to verify that data is saving properly before beginning experiments. Also, we had several leaks in our system because we weren't using the connectors properly (needed to twist and push to get a tighter fit). A warning about that would be helpful. Additionally, in the ANC lab, things were very straight forward and we felt adequately prepared.

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
carbs=(ANC_0*(np.exp(-hrt)))
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
plt.savefig('/Users/Rosie/github/CEE4530/Lab2-Acid Rain/lab2_ANC_comp.png')
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
#to find ANC_0: added .317 g of NaH2CO3
mass_NA_2=.317*u.g

ANC_02=mass_NA_2/MM_NaH2CO3/Vol
ANC_expected2=epa.ANC_open(3)*(1-(np.exp(-hrt2)))+(ANC_02*(np.exp(-hrt2)))

#Number 5.3
carbs2=(ANC_02*(np.exp(-hrt2)))
ANC_closed2=epa.ANC_closed(lakepH2,carbs2)

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
plt.savefig('/Users/Rosie/github/CEE4530/Lab2-Acid Rain/lab2_ANC_comp2.png')
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
ax.annotate('$HCO_3^- + H^+ \Rightarrow H_2CO_3$', xy=(0.75, 6.25), xytext=(0.45, 7), arrowprops=dict(facecolor='black', shrink=0.10),)
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

# at t = 20, we measured pH
pH_20=3.41
ANC_20=-epa.invpH(pH_20)

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
plt.legend(['ANC conservative', 'ANC closed', 'ANC open', 'measured ANC'])
plt.savefig('/Users/Rosie/github/CEE4530/Lab3-ANC/ANC_comp_data_plot.png')
plt.show()
```
