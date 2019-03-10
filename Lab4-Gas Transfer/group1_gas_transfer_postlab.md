# Gas Transfer
## Group 1 - Jiwon Lee and Rosie Krasnoff
##### Deadline extended: Due March 12th

2.
![DO_vs_Time](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab4-Gas%20Transfer/DO_vs_Time.png?raw=true)

Figure 1. A representative subset of six of the tested flow rates showing dissolved oxygen vs. time.

3. A calculation of C* based on the average water temperature, $22^\circ C$ and the barometric pressure, 101.3 kPa using the equation C⋆=PO2e(1727T−2.105) finds a value of C*= 8.894 mg/L

4. Estimate k^v,l using linear regression and equation (103) for each data set.

Using linear regression and equation 103 (typed below), we found the k^v,l for each data set to be as follows:
0.00272, 0.00365, 0.00347, 0.003194, 0.00420,0.00669, 0.006456, 0.00851, 0.00904, 0.00904, 0.00715, 0.00739, 0.006467, 0.00977, 0.01143, 0.00907, 0.01083, 0.01080, 0.00708, 0.00695, 0.00998, 0.00494, 0.01142


5. ![time_vs_C](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab4-Gas%20Transfer/DO_vs_Time.png?raw=true)


$$Equation \; 103:$$
$$\ln \frac{C^{\star} -C}{C^{\star} -C_{0} } =-\hat{k}_{v,l} (t-t_{0} )$$

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

airflows.size

## Number 1
#delete data that is less than 2 or greater than 6 mg/L
DO_min = 2 * u.mg/u.L
DO_max = 6 * u.mg/u.L
for i in range(airflows.size):
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
plt.plot(time_data[0], DO_data[0],'-', time_data[4], DO_data[4],'-', time_data[10], DO_data[10],'-', time_data[15], DO_data[15],'-', time_data[22], DO_data[22],'-')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(['100', '225', '500', '725', '950'])
#plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/DO_vs_Time.png')
plt.show()

## Number 3
T_w=22*u.celsius
Temp=T_w.to(u.K)
P = 101.3*u.kPa
C_star = epa.O2_sat(P,Temp)

## Number 4
numb=airflows.size

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
  kvl[i] = -1*slope

## Number 5
trial_N=0
t=np.linspace(0,200,500)
#equation C=C_star-(C_star-C0)*np.exp(-kvl*t)
C0 = DO_data[trial_N][0].magnitude
C=C_star.magnitude-(C_star.magnitude-C0)*np.exp(-kvl[trial_N]*t)

#Now plot the data and the linear regression
plt.plot(t,C,'r')
plt.plot(time_data[trial_N], DO_data[trial_N],'o')
plt.xlabel('time (s)')
plt.ylabel(' DO concentration (mg/L)')
plt.legend(['model','data for flow=100 $\mu M/s$'])
plt.tight_layout()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/time_vs_C.png')
plt.show()

## Number 6
plt.plot(airflows, kvl,'o-')
plt.xlabel('airflow rate ($\mu M/s$) ')
plt.ylabel('k^v,l')
plt.tight_layout()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/airflow_rate_vs_kvl.png')
plt.show()

## Number 7
V=.750*u.L
T=293*u.K
MW=32*u.gram/u.mole
nair=airflows.to(u.mole/u.s)
P=101.3*u.kPa
P=P.to(u.atm)
f=0.21
deltaC=6*u.mg/u.L
OTE = np.array((V*kvl*(deltaC))/(MW*nair*f))

plt.plot(airflows, OTE,'o-')
plt.xlabel('airflow rate (μmole/s) ')
plt.ylabel('oxygen transfer efficiency')
plt.tight_layout()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab4-Gas Transfer/airflow_rate_vs_OTE.png')
plt.show()

```


5. Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).


6. Plot k^v,l as a function of airflow rate (μmole/s).
7. Plot OTE as a function of airflow rate (?mole/s) with the oxygen deficit (C⋆−C) set at 6 mg/L.

$$OTE=\frac{\dot{n}_{aq\; o_{2} } }{f_{O_{2} } \dot{n}_{air} } =\frac{V\hat{k}_{v,l} \left(C^{\star} -C\right)}{f_{O_{2} } \dot{n}_{air} MW_{O_{2} } }$$


8. Comment on the oxygen transfer efficiency and the trend or trends that you observe.
9. Propose a change to the experimental apparatus that would increase the efficiency.
10. Verify that your report and graphs meet the requirements.


# Conclusion

# Suggestions / Comments


# Appendix

``` python

```
