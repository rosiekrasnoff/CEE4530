# Gas Transfer
## Group 1 - Jiwon Lee and Rosie Krasnoff
##### March 8th

2.
![DO_vs_Time](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab4-Gas%20Transfer/DO_vs_Time.png?raw=true)

Figure 1. A representative subset of six of the tested flow rates showing dissolved oxygen vs. time.

3. A calculation of C* based on the average water temperature, $22^\circ C$ and the barometric pressure, 101.3 kPa using the equation C⋆=PO2e(1727T−2.105) finds a value of C*= 8.894 mg/L

``` python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats
import collections
import os
from pathlib import Path
import time

# This code is included because there is a bug in the version of this code that is in epa.
def aeration_data(DO_column, dirpath):
    """This function extracts the data from folder containing tab delimited
    files of aeration data. The file must be the original tab delimited file.
    All text strings below the header must be removed from these files.
    The file names must be the air flow rates with units of micromoles/s.
    An example file name would be "300.xls" where 300 is the flowrate in
    micromoles/s. The function opens a file dialog for the user to select
    the directory containing the data.

    Parameters
    ----------
    DO_column : int
        index of the column that contains the dissolved oxygen concentration
        data.

    dirpath : string
        path to the directory containing aeration data you want to analyze

    Returns
    -------
    filepaths : string list
        all file paths in the directory sorted by flow rate

    airflows : numpy array
        sorted array of air flow rates with units of micromole/s attached

    DO_data : numpy array list
        sorted list of numpy arrays. Thus each of the numpy data arrays can
        have different lengths to accommodate short and long experiments

    time_data : numpy array list
        sorted list of numpy arrays containing the times with units of seconds

    Examples
    --------

    """
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
dirpath = "/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/Aeration/Aeration"
dirpath='/Users/Rosie/github/CEE4530/Lab4-Gas Transfer/Aeration/Aeration/'
filepaths, airflows, DO_data, time_data = aeration_data(DO_column,dirpath)
epa.column_of_data('/Users/Rosie/github/CEE4530/Lab4-Gas Transfer/550.xls',1,-1,1,'Pa')
## Number 1
#delete data that is less than 2 or greater than 6 mg/L
DO_min = 2 * u.mg/u.L
DO_max = 6 * u.mg/u.L
for i in range(1,airflows.size,4):
  idx_start = (np.abs(DO_data[i]-DO_min)).argmin()
  idx_end = (np.abs(DO_data[i]-DO_max)).argmin()
  time_data[i] = time_data[i][idx_start:idx_end] - time_data[i][idx_start]
  DO_data[i] = DO_data[i][idx_start:idx_end]

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
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/DO_vs_Time.png')
plt.show()

## Number 3
T_w=22*u.celsius
Temp=T_w.to(u.K)
P = 101.3*u.kPa
C_star = epa.O2_sat(P,Temp)



#numb=airflows.size
numb=11

y=np.empty(numb,dtype="object")
delta_t=np.empty(numb,dtype="object")
for i in range(numb):
  t_temp=time_data[i].magnitude
  t_temp
  delta_t_temp=t_temp - t_temp[0]
  delta_t[i] = delta_t_temp
  # delta_t=np.append(delta_t,[delta_t_temp])
  do_temp=DO_data[i].magnitude
  numerator = C_star.magnitude - do_temp
  denominator = C_star.magnitude - do_temp[0]
  y_temp = np.log(numerator/denominator)
  y[i] = y_temp
x=delta_t

kvl = np.empty(numb,dtype="object")
for i in range(numb):
  x_temp = delta_t[i]
  y_temp = y[i]
  slope, intercept, r_value, p_value, std_err = stats.linregress(x_temp, y_temp)
  kvl[i] = slope

kvl


## Number 5
#Now plot the data and the linear regression
plt.plot(time_data[14], DO_data[14],'o')
plt.plot(x_temp, y_temp,'r')
plt.xlabel('time (s)')
plt.ylabel(' (mole/L)')
plt.legend(['data'])
plt.tight_layout()
#plt.savefig('')
plt.show()

## Number 6
plt.plot(airflows, kvl,'r')
#plt.plot(x, y,'r')
plt.xlabel('airflow rate (μmole/s) ')
plt.ylabel('k^v,l')
plt.tight_layout()
#plt.savefig('')
plt.show()

## Number 7
plt.plot(time_data, DO_data,'o')
plt.plot(x, y,'r')
plt.xlabel('airflow rate (μmole/s) ')
plt.ylabel('OTE')
plt.tight_layout()
#plt.savefig('')
plt.show()

```

4. Estimate k^v,l using linear regression and equation (103) for each data set.

$$Equation \; 103:$$
$$\ln \frac{C^{*} -C}{C^{*} -C_{0} } =-\hat{k}_{v,l} (t-t_{0} )$$

5. Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).
6. Plot k^v,l as a function of airflow rate (μmole/s).
7. Plot OTE as a function of airflow rate (?mole/s) with the oxygen deficit (C⋆−C) set at 6 mg/L.
8. Comment on the oxygen transfer efficiency and the trend or trends that you observe.
9. Propose a change to the experimental apparatus that would increase the efficiency.
10. Verify that your report and graphs meet the requirements.


# Conclusion

# Suggestions / Comments


# Appendix

``` python

```
