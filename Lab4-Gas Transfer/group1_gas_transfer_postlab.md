# Gas Transfer
## Group 1 - Jiwon Lee and Rosie Krasnoff
##### March 8th



``` python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
import collections
import os
from pathlib import Path

# This code is included because there is a bug in the version of this code that is in epa.

def aeration_data(DO_column, dirpath):
    #return the list of files in the directory
    filenames = os.listdir(dirpath)
    #extract the flowrates from the filenames and apply units
    airflows = ((np.array([i.split('.', 1)[0] for i in filenames])).astype(np.float32))
    #sort airflows and filenames so that they are in ascending order of flow rates
    idx = np.argsort(airflows)
    airflows = (np.array(airflows)[idx])*u.umole/u.s
    filenames = np.array(filenames)[idx]

    filepaths = [os.path.join(dirpath, i) for i in filenames]
    #DO_data is a list of numpy arrays. Thus each of the numpy data arrays can have different lengths to accommodate short and long experiments
    # cycle through all of the files and extract the column of data with oxygen concentrations and the times
    DO_data=[epa.column_of_data(i,0,DO_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,0,-1)).to(u.s) for i in filepaths]
    aeration_collection = collections.namedtuple('aeration_results','filepaths airflows DO_data time_data')
    aeration_results = aeration_collection(filepaths, airflows, DO_data, time_data)
    return aeration_results

# The column of data containing the dissolved oxygen concentrations
DO_column = 2
#dirpath = "/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/Aeration/Aeration"
#dirpath='/Users/Rosie/github/CEE4530/Lab4-Gas Transfer/Aeration/Aeration/'
filepaths, airflows, DO_data, time_data = aeration_data(DO_column,dirpath)

## Number 1
#delete data that is less than 2 or greater than 6 mg/L
DO_min = 2 * u.mg/u.L
DO_max = 6 * u.mg/u.L
for i in range(airflows.size):
  idx_start = (np.abs(DO_data[i]-DO_min)).argmin()
  idx_end = (np.abs(DO_data[i]-DO_max)).argmin()
  time_data[i] = time_data[i][idx_start:idx_end] - time_data[i][idx_start]
  DO_data[i] = DO_data[i][idx_start:idx_end]
  #Accumulator_P[i] = Accumulator_P[i][idx_start:idx_end]

## Number 2

#getting all the data
for i in range(airflows.size):
  plt.plot(time_data[i], DO_data[i],'-')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(airflows.magnitude)
plt.show()

#pick 5 representative values
plt.plot(time_data[0], DO_data[0],'-', time_data[4], DO_data[4],'-', time_data[9], DO_data[9],'-', time_data[13], DO_data[13],'-', time_data[23], DO_data[23],'-')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['100', '225', '475', '575', '950'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/DO_vs_Time.png')
plt.show()

## Number 3


```

2. Plot a representative subset of the data showing dissolved oxygen vs. time. Perhaps show 5 plots on one graph.

![DO_vs_Time](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/E_peclet_graph.png?raw=true)

3. Calculate C⋆ based on the average water temperature, barometric pressure, and the equation from environmental processes analysis called O2_sat. C⋆=PO2e(1727T−2.105) where T is in Kelvin, PO2 is the partial pressure of oxygen in atmospheres, and C⋆ is in mg/L.
4. Estimate k^v,l using linear regression and equation (103) for each data set.

$$Equation \; 103:$$
$$\ln \frac{C^{*} -C}{C^{*} -C_{0} } =-\hat{k}_{v,l} (t-t_{0} )$$

5. Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).
6. Plot k^v,l as a function of airflow rate (μmole/s).
7. Plot OTE as a function of airflow rate (?mole/s) with the oxygen deficit (C⋆−C) set at 6 mg/L.
8. Comment on the oxygen transfer efficiency and the trend or trends that you observe.
9. Propose a change to the experimental apparatus that would increase the efficiency.
10. Verify that your report and graphs meet the requirements.





# Appendix
``` python

```
