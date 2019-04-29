

```python

from aguaclara.research.peristaltic_pump import vol_per_rev_3_stop
from aguaclara.core.units import unit_registry as u

round(vol_per_rev_3_stop(color="orange-yellow"), 6)

Flow_per_rev=0.019439*u.mL
rev_per_min=5/u.min

FR=Flow_per_rev*rev_per_min
FR

FR=.064*u.mL/u.min

(2*u.ml/FR).to(u.min)



#calculate amount of Na2SO3 to add
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats


desired_COD=500*u.mg/u.liter
#convert from mg O2 to mg NA2SO3
conv=7.897

mass_NA2SO3=desired_COD*conv

print('Mass to add to 100 mL:',mass_NA2SO3.to(u.g/u.mL)*100*u.mL)








```
