## Acid Precipitation and Remediation of Acid Lakes

# Group 1

K1=10−6.3, K2=10−10.3, KH=10−1.5molLatm, PCO2=10−3.5atm, and Kw=10−14.

1. Plot measured pH of the lake versus dimensionless hydraulic residence time (t/θ).

![pHgraph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph_ourdata1.png?raw=true)

Figure 1: Plot of concentration pH of lake as acid rain was added over time.

2. Assuming that the lake can be modeled as a completely mixed flow reactor and that ANC is a conservative parameter, equation (25) can be used to calculate the expected ANC in the lake effluent as the experiment proceeds. Graph the expected ANC in the lake effluent versus the hydraulic residence time (t/θ) based on the completely mixed flow reactor equation with the plot labeled (in the legend) as conservative ANC.
3. If we assume that there are no carbonates exchanged with the atmosphere during the experiment, then we can calculate ANC in the lake effluent by using equation (14) describing the ANC of a closed system. Calculate the ANC under the assumption of a closed system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as closed ANC.
4. If we assume that there is exchange with the atmosphere and that carbonates are at equilibrium with the atmosphere, then we can calculate ANC in the lake effluent by using equation (18) describing the ANC of an open system. Calculate the ANC under the assumption of an open system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as open ANC.

![ANCgraphcomp](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph_ourdataALL3.png?raw=true)

Figure 2: Plot of concentration calculated ANC over time from conservative, closed, and open calculations.


5. Analyze the data from the second experiment and graph the data appropriately. What did you learn from the second experiment?

In the second experiment, we added about half as much NaHCO3 as we added in the first experiment. Therefore, it had a lower ANC and so the lake was destroyed and unlivable in a shorter amount of time. The ANC worked the same way, it was just less, so less acid could be added from the rain before the pH fell drastically.

![pHgraph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph_2ndrun.png?raw=true)

Figure 3: Plot of concentration pH of lake as acid rain was added over time for second experiment with about half as much NaHCO3.

![ANCgraphcomp](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab2-Acid%20Rain/lab2_pHgraph_2ndrun_comp.png?raw=true)

Figure 4: Plot of concentration calculated ANC over time from conservative, closed, and open calculations for second experiment with about half as much NaHCO3.


```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

#Number 1
#push the data file to your github and then get the url of the raw file.
data_file_path="https://raw.githubusercontent.com/aks224/4530-aks224/master/Lab%202%20-%20Acid%20Rain.xls"
# set the start index
start=419
#The pH data is in column 1
column=1
#help(epa.column_of_data)
lakepH=epa.column_of_data(data_file_path, start, 1, -1)

#extract the corresponding time data and convert to seconds
time = epa.column_of_time(data_file_path,start,-1).to(u.min)
residencetime=14.15*u.min
# hydraulic residence time t/θ
time
hrt = time/residencetime
hrt
#Now plot the graph
fig, ax = plt.subplots()
ax.plot(hrt,lakepH,'r')
lakepH
plt.xlabel('hydraulic residence time (min)')
plt.ylabel('pH')
plt.title('pH of lake')

plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_anya1.png')
plt.show()

#Number 2
#ANC_expected=[ANC_out−ANC_in⋅(1−e^−t/θ)]e^t/θ
#to find ANCo: they added .620 g of NaH2CO3

ANC_0=(.620*u.g)/(84.01*u.g/u.mol)/(4.246*u.L)
ANC_expected=epa.ANC_open(3)*(1-(np.exp(-hrt)))+(ANC_0*(np.exp(-hrt)))

#fig, ax = plt.subplots()
#ax.plot(hrt,ANC_expected,'b')
#plt.xlabel('hydraulic residence time (min)')
#plt.ylabel('ANC conservative')
#plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_anya2.png')
plt.show()


#Number 3
carbs=ANC_0
ANC_closed=epa.ANC_closed(lakepH,carbs)

#fig, ax = plt.subplots()
#ax.plot(hrt,ANC_closed,'g')
#plt.xlabel('hydraulic residence time (min)')
#plt.ylabel('ANC closed')
#plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_anya3.png')
plt.show()

#Number 4
#ANC_effluent=(PCO2*KH)/α0*(α1+2α2)+Kw/[H+]−[H+]

ANC_effluent = epa.ANC_open(lakepH)
#fig, ax = plt.subplots()
#ax.plot(hrt,ANC_effluent,'b')
#plt.xlabel('hydraulic residence time (min)')
#plt.ylabel('ANC open')
#plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_anya4.png')
plt.show()

# plotting all the ANCs together
ANC_graph=np.linspace(0,1.6,40)
fig, ax = plt.subplots()
ax.plot(hrt, ANC_expected, 'r', hrt, ANC_closed, 'g', hrt, ANC_effluent, 'b')
plt.title('Comparing ANC calculations')
plt.xlabel('hydraulic residence time (min)')
plt.ylabel('ANC (eq/L)')
plt.legend(['ANC conservative', 'ANC closed', 'ANC open'])
plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_anyaALL3.png')
plt.show()

#Number 5 (with our data)

data_file_path="https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab_2_Acid_rain_with_half_ANC.xls"
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
time = epa.column_of_time(data_file_path,start,-1).to(u.min)
residencetime = v/q # hydraulic residence time t/θ
hrt = time/residencetime
#Now plot the graph
fig, ax = plt.subplots()
ax.plot(hrt,lakepH2,'r')
plt.xlabel('hydraulic retention time (min)')
plt.ylabel('pH')
plt.title('pH in 2nd run')

plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_2ndrun')
plt.show()

#Number 5.2
#ANC_expected=[ANC_out−ANC_in⋅(1−e^−t/θ)]e^t/θ
#to find ANCo: added .620 g of NaH2CO3
ANC_02=(.317*u.g)/(84.01*u.g/u.mol)/(3.938*u.L)
ANC_expected2=epa.ANC_open(3)*(1-(np.exp(-hrt)))+(ANC_0*(np.exp(-hrt)))

#Number 5.3
carbs2=ANC_0
ANC_closed2=epa.ANC_closed(lakepH2,carbs)

#Number 5.4
#ANC_effluent=(PCO2*KH)/α0*(α1+2α2)+Kw/[H+]−[H+]
ANC_effluent2 = epa.ANC_open(lakepH2)

# plotting all the ANCs together
ANC_graph=np.linspace(0,1.6,40)
fig, ax = plt.subplots()
ax.plot(hrt, ANC_expected2, 'r', hrt, ANC_closed2, 'g', hrt, ANC_effluent2, 'b')
plt.title('Comparing ANC calculations')
plt.xlabel('hydraulic residence time (min)')
plt.ylabel('ANC (eq/L)')
plt.legend(['ANC conservative', 'ANC closed', 'ANC open'])
plt.savefig('/Users/Rosie/github/CEE4530/lab2_pHgraph_2ndrun_comp.png')
plt.show()


```
# Questions
1. What do you think would happen if enough NaHCO3 were added to the lake to maintain an ANC greater than 50μeq/L for 3 residence times with the stirrer turned off?
**If the stirrer were turned off, it would cause the NaHCO3 to simply sink to the bottom of the lake since its density = 2.2g/cm3 is higher than that of the lake. Some of the NaHCO3 will dissolve as it sinks, but even dissolved into water, it makes a more dense solution so that solution will also sink to the bottom. So, there will be less ANC at the top of the lake, where the acid is then added. Thus, the solution will acidify at the top faster than we saw with the stirrer turned on because the ANC will not be evenly distributed and the top of the lake will be lacking.**

2. What are some of the complicating factors you might find in attempting to remediate a lake using CaCO3?
**The density of CaCO3 is 2.71 g/cm³, which is higher than that of NaHCO3 at 2.2g/cm³, so it sinks quicker. This will exacerbate the issues discussed in question 1 above, where there will be a gradient of ANC because of the higher density. This problem will be made worse if there is no mixing. The solubility of CaCO3 is also much lower than that of NaHCO3, so even if one calculated how much CaCO3 to add to get the same ANC as we got from NaHCO3, the particles would likely not all dissolve, and therefore the actual ANC of the solution would not be as high as expected.**
