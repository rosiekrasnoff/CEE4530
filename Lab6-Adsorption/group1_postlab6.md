# Adsorption Lab
## Group 1 - Jiwon Lee and Rosie Krasnoff (10 hours each)
##### April 17th


### Contactor Results and Analysis
We created plots for the breakthrough curves showing C/C_0 versus time for the trials with no activated carbon (Figure 1), for the trials with some activated carbon (Figure 2), and then we replotted Figure 2 with a restricted range to be able to make clearer comparisons with Figure 1 (Figure 3.)


![No activated carbon](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab6-Adsorption/No_Activated_Carbon.png?raw=true)

Figure 1. Graph showing the dimensionless value of $ \frac {concentration}{stock \space concentration}$ as a function of the dimensionless value of $ \frac {time}{HRT}$ for the systems without activated carbon. The legend shows the different flow rates at which the experiment was run.


![Activated C](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab6-Adsorption/Activated_Carbon.png?raw=true)

Figure 2. Graph showing the dimensionless value of $ \frac {concentration}{stock \space concentration}$ as a function of the dimensionless value of $ \frac {time}{HRT}$ for the systems with activated carbon, the amount of AC is indicated in the legend, along with the flow rate.


![Activated C range](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab6-Adsorption/Activated_Carbon_range.png?raw=true)

Figure 3. Graph is simply Figure 2 with the range restricted in the x-axis for an easier comparison with the no activated carbon graph. It shows the dimensionless value of $ \frac {concentration}{stock \space concentration}$ as a function of the dimensionless value of $ \frac {time}{HRT}$ for the systems with activated carbon, the amount of AC is indicated in the legend, along with the flow rate.

We found the time when the effluent concentration was 50% of the influent concentration and then plotted those time values as a function of the activated carbon used (Figure 4). Because the various experiments were not all conducted at the small flow rate, this representation of the data is not all that meaningful because there are other factors at play that are not illustrated. In a second graph, we restricted the data to that which had been collected when using a flow rate of around 0.5 mL/s (Figure 5). This graph has a much clearer trend: as the mass of activated carbon used increases, the time until the effluent concentration was 50% of the influent concentration also increases. Because of a lack of data at high levels of activated carbon, it is too difficult to ascertain the nature of that relationship; it could be linear, it also looks at if it has the potential to be exponential.

![time to 50%, all](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab6-Adsorption/All_Flow_Rates.png?raw=true)

Figure 4. For every experiment, the time to takes for the effluent concentration to reach 50% of the influent concentration is plotted at a function of the mass of activated carbon in the column. Some points correspond to flow rates of 0.5 mL/s, others to flow rates of over 2 mL/s.

![time to 50%, 5 mL/s](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab6-Adsorption/Same_Flow_Rates.png?raw=true)

Figure 5. The graph shows the time to takes for the effluent concentration to reach 50% of the influent concentration is plotted at a function of the mass of activated carbon in the column for only the experiments where a flow rate of about 0.5 mL/s was used.

We found the retardation factor using equation (95) and the q_0 value using equation (97) for each of the trials run with some mass of activated carbon. The results are reported in table 1 below. We also graphed q_0 as a function of activated carbon (Figure 6).

$$ (95) \ R_{adsorption} = \frac{t_{mtz}}{t_{water}} $$


$$ (97) \ q_0 = \left(R_{adsorption} - 1\right) \frac{C_0 \phi V_{column}}{M_{adsorbent}} $$


Table 1. Retardation factor and q_0 for all experiments.
| Mass of AC (grams)| Flow rate (mL/s)| retardation factor | q_0 |
| ---- | ---- | ---- | ---- |
| 0.5 | 0.5 | 0.8959 | -0.0003209 |
| 0.601 | 0.5 | 0.7839 | -0.0005539  |
| 1.66 | 0.5 | 2.486 | 0.001379 |
| 2 | 0.466 | 3.875 | 0.002214 |
| 4 | 0.466 | 0.5151 | -0.0001867 |
| 13.8 | 2.6 | 3.96 | 0.0003304 |
| 15 | 0.5 | 17.09 | 0.001652 |
| 15.63 | 2.6 | 4.775 | 0.000372 |
| 29.34 | 0.467 | 662.3 | 0.03472 |


![q0](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab6-Adsorption/q_0.png?raw=true)

Figure 6. This graph shows the mass of absorbate per mass of absorbent, $q_0$, as a function of the mass of activated carbon used for a concentration of $50\frac{mg}{L}$. We can observe an upwards trend as $q_0$ increases as more activated carbon is used.

As the mass of activated carbon used increases at a constant flow rate, the retardation factor, for the most part, increased as well. This makes sense since activated carbon slows down the water traveling through the bed, increasing the time necessary for the mass transfer zone to travel through. Likewise, we can observe a similar trend between $q_0$ and the mass of activated carbon used (Figure 6). However, all the assumptions we made (reactor volume, time for water to travel through the bed, and deriving t_mtz from the time that it takes for the concentration at the effluent to reach 50% of the influent concentration) has resulted in some unrealistic, or impossible, $q_0$ values (i.e. negative).


### Conclusion
In this lab, we investigated the removal of dissolved species through adsorption to a solid phase by looking into the breakthrough characteristics of red dye #40 on activated carbon in a continuous-flow carbon contactor at a concentration of $50\frac{mg}{L}$. Using a set up with a carbon column connected to a peristaltic pump, red dye, and reverse osmosis water, we modeled the adsorption process used commonly in water treatment plants. From the experiment, we were able to collect data regarding the breakthrough time of the column with and without activated carbon, time when the effluent concentration was 50% of the influent concentration, and the retardation factor. We were able to observe a couple significant trends from the experiment: as more activated carbon is used, both the time until the effluent concentration was 50% of the influent concentration as well as the $q_0$ increases.

### Suggestions/Comments

To make the analysis more simple, we would suggest considering making the experiments more uniform across the class. This would include requiring all the lab groups to perform the experiment both with and without activated carbon as well asking them to use the same flow rates. Also it would be better to find a trend if there were different masses assigned to different lab groups so that we could get a good range of mass values instead of a lot at low masses and a couple high ones.

Also, we suggest a modification of the set-up diagram in the lab manual with regards to the 3 way valves to be more clear about which are the two ways the valve should alternate between.

Keep thinking about a way to avoid getting air bubbles in the tubes, it was definitely something we struggled to deal with and was a time consuming thing to fix.


### Appendix
``` python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.physchem as pc
import aguaclara.core.utility as ut
import numpy as np
import matplotlib.pyplot as plt
import collections
import os
from pathlib import Path
import pandas as pd
import statistics

def adsorption_data(C_column, dirpath):
    """This function extracts the data from folder containing tab delimited
    files of adsorption data. The file must be the original tab delimited file.

    Parameters
    ----------
    C_column : int
        index of the column that contains the dissolved oxygen concentration
        data.
    dirpath : string
        path to the directory containing aeration data you want to analyze
    Returns
    -------
    filepaths : string list
        all file paths in the directory sorted by flow rate
    time_data : numpy array list
        sorted list of numpy arrays containing the times with units of seconds
    Examples
    --------
    """
    #return the list of files in the directory
    metadata = pd.read_csv(dirpath + '/metadata.txt', delimiter='\t')
    filenames = metadata['file name']
    #extract the flowrates from the filenames and apply units
    #sort airflows and filenames so that they are in ascending order of flow rates


    filepaths = [dirpath + '/' + i for i in filenames]
    #C_data is a list of numpy arrays. Thus each of the numpy data arrays can have different lengths to accommodate short and long experiments
    # cycle through all of the files and extract the column of data with oxygen concentrations and the times
    C_data=[epa.column_of_data(i,epa.notes(i).last_valid_index() + 1,C_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,epa.notes(i).last_valid_index() + 1,-1)).to(u.s) for i in filepaths]

    adsorption_collection = collections.namedtuple('adsorption_results','metadata filenames C_data time_data')
    adsorption_results = adsorption_collection(metadata, filenames, C_data, time_data)
    return adsorption_results


C_column = 1
dirpath = "https://raw.githubusercontent.com/monroews/CEE4530/master/Examples/data/Adsorption"

metadata, filenames, C_data, time_data = adsorption_data(C_column,dirpath)
metadata
Column_D = 1 * u.inch
Column_A = pc.area_circle(Column_D)
Column_L = 15.2 * u.cm
Column_V = Column_A * Column_L
#I'm guessing at the volume of water in the tubing, in the photometer, and in the space above and below the column. This parameter could be adjusted!
Tubing_V = 60 * u.mL
Flow_rate = ([metadata['flow (mL/s)'][i] for i in metadata.index])* u.mL/u.s
Mass_carbon= ([metadata['carbon (g)'][i] for i in metadata.index])* u.g
Tubing_HRT = Tubing_V/Flow_rate
#to make things simple we are assuming that the porosity is the same for sand and for activated carbon. That is likely not true!
porosity = 0.4
C_0 = 50 * u.mg/u.L

#estimate the HRT for all of the columns
HRT = (porosity * Column_V/Flow_rate).to(u.s)

#zero the concentration data by subtracting the value of the first data point from all data points. Do this in each data set.
for i in range(np.size(filenames)):
  C_data[i]=C_data[i]-C_data[i][0]

#Number 1

#Create a graph of the columns that didn't have any activated carbon
mylegend = []
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] == 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(metadata['flow (mL/s)'][i]) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$');
plt.xlim(right=3,left=0);
plt.ylabel(r'$\frac{C}{C_0}$');
plt.legend(mylegend);
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/No_Activated_Carbon.png')
plt.show()

# create a graph of the columns that had different masses of activated carbon. Note that this includes systems with different flow rates!
mylegend =[]
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] != 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(ut.round_sf(metadata['carbon (g)'][i],3)) + ' g, ' + str(ut.round_sf(metadata['flow (mL/s)'][i],2)) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$');
plt.xlim(right=100,left=0);
plt.ylabel(r'$\frac{C}{C_0}$');
plt.legend(mylegend);
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/Activated_Carbon.png')
plt.show()


mylegend =[]
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] != 0):
    plt.plot(time_data[i], C_data[i]/C_0,'-');
    mylegend.append(str(ut.round_sf(metadata['carbon (g)'][i],3)) + ' g, ' + str(ut.round_sf(metadata['flow (mL/s)'][i],2)) + ' mL/s')

plt.xlabel(r'time (secs)');
plt.xlim(right=1000,left=0);
plt.ylabel(r'$\frac{C}{C_0}$');
plt.legend(mylegend);
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/Activated_Carbon.png')
plt.show()



mylegend =[]
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] != 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(ut.round_sf(metadata['carbon (g)'][i],3)) + ' g, ' + str(ut.round_sf(metadata['flow (mL/s)'][i],2)) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$');
plt.xlim(right=3,left=0);
plt.ylabel(r'$\frac{C}{C_0}$');
plt.legend(mylegend);
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/Activated_Carbon_range.png')
plt.show()

#Number 2
desired_t=[0]*np.size(filenames)
desired_C = 0.5*C_0
for j in range(np.size(filenames)):
  for i in range(1,C_data[j].size):
    if (C_data[j][i-1] < desired_C) and (C_data[j][i] > desired_C):
      desired_t[j] = (time_data[j][i]).magnitude


# Create a graph of the time when the effluent concentration was 50% of the influent concentration and the mass of activated carbon used
plt.plot(Mass_carbon, desired_t, 'o')
plt.xlabel('activated carbon (g)');
plt.ylabel('time to reach 50% of influent concentration (s)')
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/All_Flow_Rates.png')
plt.show()

desired_t2=[0]*np.size(filenames)
desired_C = 0.5*C_0
for j in range(np.size(filenames)):
  for i in range(1,C_data[j].size):
    if (C_data[j][i-1] < desired_C) and (C_data[j][i] > desired_C):
      if (Flow_rate[j]).magnitude < 1:
        desired_t2[j] = (time_data[j][i]).magnitude
      else:
        desired_t2[j] = float('nan')

#new plot, using only data with flow rate of ~0.5mL/s
plt.plot(Mass_carbon, desired_t2, 'o')
plt.xlabel('activated carbon (g)');
plt.ylabel('time to reach 50% of influent concentration (s)')
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/Same_Flow_Rates.png')
plt.show()


#Number 3
#Time for water to travel through the bed

V1=desired_t[0]*u.second*Flow_rate[0]
V2=desired_t[1]*u.second*Flow_rate[1]
V3=desired_t[2]*u.second*Flow_rate[2]
V4=desired_t[3]*u.second*Flow_rate[3]
avg_V= (V1+V2+V3+V4)/4


t_w_0_5mL = avg_V/Flow_rate[0]
t_w_2_6mL = avg_V/Flow_rate[2]


#Time for the mass transfer zone to travel through the bed is the time that it takes for the concentration at the effluent to reach 50% of the influent concentration

t_mtz = desired_t*u.sec
#Calculate retardation factor for the experiements that had AC in them (5-13)
#R = t_mtz/t_water

R5 = t_mtz[4]/t_w_0_5mL
R6 = t_mtz[5]/t_w_0_5mL
R7 = t_mtz[6]/t_w_0_5mL
R8 = t_mtz[7]/t_w_0_5mL
R9 = t_mtz[8]/t_w_0_5mL
R10 = t_mtz[9]/t_w_2_6mL
R11 = t_mtz[10]/t_w_0_5mL
R12 = t_mtz[11]/t_w_2_6mL
R13 = t_mtz[12]/t_w_2_6mL

R = (R5, R6, R7, R8, R9, R10, R11, R12, R13)

R
#Number 4
bed_porosity = 0.4
q_0 = [0]*9
i=4
for j in range(0,len(R)):  
  q_0[j] = (R[j]-1)*(C_0).to(u.g/u.L)*bed_porosity*(Column_V).to(u.L)/Mass_carbon[i]

  print('When the mass of carbon is',Mass_carbon[i])
  print('and the flow rate is',Flow_rate[i])
  print('then the retardation factor is',R[j])
  print('and q_0 is',q_0[j])
  print('')
  i=i+1

#Create a graph of q_0 and mass of activated carbon used for each column
plt.plot(Mass_carbon[4:13], q_0, 'o')
plt.xlabel('activated carbon (g)');
plt.ylabel(r'$q_0$')
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab6-Adsorption/q_0.png')
plt.show()


Mass_carbon[4:13]



```
