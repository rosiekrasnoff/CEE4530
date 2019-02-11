## Prelab Questions for ANC lab
#### Feb 13th, 2019

1. Compare the ability of Cayuga lake and Wolf pond (an Adirondack lake) to withstand an acid rain runoff event (from snow melt) that results in 20% of the original lake water being replaced by acid rain. The acid rain has a pH of 3.5 and is in equilibrium with the atmosphere. The ANC of Cayuga lake is 1.6 meq/L and the ANC of Wolf Pond is 70 μeq/L. Assume that carbonate species are the primary component of ANC in both lakes, and that they are in equilibrium with the atmosphere. What is the pH of both bodies of water after the acid rain input? Remember that ANC is the conservative parameter (not pH!). Hint: You can use the scipy optimize root finding function called brentq. Scipy can’t handle units so the units must be removed using .magnitude.}

```python
import math
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize

# ANC_in= [OH-]-[H+] and [H+]= 10^(-pH)
pH_rain=3.5
ANC_rain=10**(-pH_rain)*u.eq/u.L

# givens
ANC_CL_0 = 1.6*10**-3 *u.eq/u.L # initial ANC of Cayuga Lake
ANC_WP_0 = 70*10**-6 *u.eq/u.L # initial ANC of Wolf pond

# Calculate ANC after rain event for each pond
ANC_CL = (ANC_rain*(.2) + ANC_CL_0*(.8))/1
ANC_WP = (ANC_rain*(.2) + ANC_WP_0*(.8))/1

# Calculate pH of Cayuga Lake
def ANC_zeroed(pHguess, ANC):
  return ((epa.ANC_open(pHguess) - ANC).to(u.mol/u.L)).magnitude

def pH_open(ANC):
  return optimize.brentq(ANC_zeroed, 0, 14,args=(ANC))

print('The pH of Cayuga Lake after the rain is',pH_open(ANC_CL))

#Calculate pH of Wolf Pond
def ANC_zeroed(pHguess, ANC):
  return ((epa.ANC_open(pHguess) - ANC).to(u.mol/u.L)).magnitude

def pH_open(ANC):
  return optimize.brentq(ANC_zeroed, 0, 14,args=(ANC))

print('The pH of Wolf Pond after the rain is' ,pH_open(ANC_WP))

```

2. What is the ANC of a water sample containing only carbonates and a strong acid that is at pH 3.2? This requires that you inspect all of the species in the ANC equation (Equation (33)) and determine which species are important.

**At low pH (< pK1=4.3) most of the carbonates will be carbonic acid. So, the species $$HCO_3^-$$ and $$ CO_3^{-2}$$ can be ignored in the equation for ANC (Equation (33)). Also because the pH is low, OH- can be assumed to be zero because it is so small in comparison to the H+ concentration. So the ANC equation simplifies to just $$ANC =  - [H^+]$$**

```python
pH_SA = 3.2 # pH of the strong acid
ANC = -10**(-1*pH_SA)
print(ANC)
```
ANC is -0.000630957344480193

##Do we need to do this?


3. Why is [H+] not a conserved species?
**[H+] is not a conserved species because they react to form new species. In this case, they can react with the carbonate ions.**
