## Acid Precipitation and Remediation of Acid Lakes

# Group 1

K1=10−6.3, K2=10−10.3, KH=10−1.5molLatm, PCO2=10−3.5atm, and Kw=10−14.

1. Plot measured pH of the lake versus dimensionless hydraulic residence time (t/θ).

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

#push the data file to your github and then get the url of the raw file.
data_file_path="https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab_2_Acid_Rain.xls"
# set the start index
start=1
#The pH data is in column 1
column=1
#help(epa.column_of_data)
lakepH=epa.column_of_data(data_file_path,1, -1)
v = 4*u.L #  volume of lake
q = .267*u.L/u.min # flow of acid into lake
#extract the corresponding time data and convert to seconds
time = epa.column_of_time(data_file_path,start).to(u.min)
residencetime = v/q # hydraulic residence time t/θ
hrt = time/residencetime
#Now plot the graph
fig, ax = plt.subplots()
ax.plot(residencetime,lakepH,'r')
plt.xlabel('time (min)')
plt.ylabel('pH')
#plt.yscale('log')

plt.savefig('Examples/images/pHgraph')
plt.show()

```

2. Assuming that the lake can be modeled as a completely mixed flow reactor and that ANC is a conservative parameter, equation (25) can be used to calculate the expected ANC in the lake effluent as the experiment proceeds. Graph the expected ANC in the lake effluent versus the hydraulic residence time (t/θ) based on the completely mixed flow reactor equation with the plot labeled (in the legend) as conservative ANC.
3. If we assume that there are no carbonates exchanged with the atmosphere during the experiment, then we can calculate ANC in the lake effluent by using equation (14) describing the ANC of a closed system. Calculate the ANC under the assumption of a closed system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as closed ANC.
4. If we assume that there is exchange with the atmosphere and that carbonates are at equilibrium with the atmosphere, then we can calculate ANC in the lake effluent by using equation (18) describing the ANC of an open system. Calculate the ANC under the assumption of an open system and plot it on the same graph produced in answering question #3 with the plot labeled (in the legend) as open ANC.
5. Analyze the data from the second experiment and graph the data appropriately. What did you learn from the second experiment?
