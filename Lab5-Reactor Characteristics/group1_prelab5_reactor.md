# Reactor Characteristics Prelab
#### Group 1 - Jiwon Lee and Rosie Krasnoff
##### March 6th

1. Calculate the change in hydraulic grade line between baffled sections of a reactor with a flow rate of 380 mL/min. The reactor baffles are perforated with 6 holes 1 mm in diameter. Is the flow through these orifices in series or in parallel? Do you multiply the head loss for one orifice by the number of orifices to get the total head loss? Are the orifices in parallel or in series? Use the pc.head_orifice function to calculate the head loss through an orifice. The vena contracta for the orifice can be found at aguaclara.core.constants.VC_ORIFICE_RATIO. Why would 6 holes 1 mm in diameter not be a good design for this reactor?

``` python
import math as m
import aguaclara.core.constants as acc
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd


# given constants
Q=380*u.mL/u.min
Q=Q.to(u.m**3/u.sec)   #flow rate
n=6                    #number of holes
d=1*u.mm
d=d.to(u.m)            #diameter of holes
g=acc.GRAVITY
k=acc.VC_ORIFICE_RATIO #orifice coefficient

a=m.pi*(d**2)/4        #area of orifice

help(pc.head_orifice)

#change in hydraulic grade
h = (Q/(n*k*a))**2/(2*g)
h
```
rearrange equation 83:
$$Q_{orifice} =n_{orifice}K_{orifice} A_{orifice} \sqrt{2g\Delta h}$$

$$\Delta h = \frac{(\frac{Q}{nKA})^2}{2g}$$

The change in hydraulic grade line for six orifices is 0.232 meters. Since we multiply the head loss for one orifice by The flow through these orifices in series or in parallel? Do you multiply the head loss for one orifice by the number of orifices to get the total head loss? Are the orifices in parallel or in series?

2. On a single graph plot the exit age distribution (E(t⋆)) for a reactor that operates as a 1-dimensional advection-dispersion reactor with Peclet numbers of 1, 10, and 100 (there will be three plots on the graph and thus a legend is required). The x-axis should be t⋆ from 0.0 to 3.0. Comment on the shapes of the curves as a function of the Peclet number. Note that the advective dispersion equation is undefined for t⋆=0. Use the epa.E_Advective_Dispersion(t,Pe) function.

```python
t=np.linspace(0.01,3,100)
p1 = epa.E_Advective_Dispersion(t,1)
p10 = epa.E_Advective_Dispersion(t,10)
p100 = epa.E_Advective_Dispersion(t,100)

fig, ax = plt.subplots()
ax.plot(t, p1, 'r', t, p10, 'g', t, p100, 'b')
plt.xlabel('t*')
plt.ylabel('E')
plt.legend(['Peclet=1', 'Peclet=10', 'Peclet=100'])
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Lab5-Reactor Characteristics/E_peclet_graph.png')
plt.show()

```
As the Peclet number increases the dispersion decreases and the response becomes closer to plug flow.
