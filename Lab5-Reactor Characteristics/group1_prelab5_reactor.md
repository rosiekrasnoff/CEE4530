# Reactor Characteristics Prelab
#### Group 1 - Jiwon Lee and Rosie Krasnoff
##### March 6th

1. The flow through the orifices is in parallel because the flow goes through all of them simultaneously rather than one after another. You don't multiply the head loss for one orifice by the number of orifices to get the total head loss, because the orifices are in parallel.

Rearranging equation 83:
$$Q_{orifice} =n_{orifice}K_{orifice} A_{orifice} \sqrt{2g\Delta h}$$

$$\Delta h = \frac{(\frac{Q}{nKA})^2}{2g}$$

The change in hydraulic grade line for six orifices (aka total head loss) is 0.232 meters.

6 holes in 1 mm in diameter would not be a good design for this reactor because head loss is reduced as the number of holes increase. Thus, the ideal reactor would have more holes.  

``` python
import math as m
import aguaclara.core.constants as acc
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import aguaclara.core.physchem as pc

# given constants
Q=380*u.mL/u.min
Q=Q.to(u.m**3/u.sec)   #flow rate
n=6                    #number of holes
d=1*u.mm
d=d.to(u.m)            #diameter of holes
g=acc.GRAVITY
k=acc.VC_ORIFICE_RATIO #orifice coefficient

a=m.pi*(d**2)/4        #area of orifice

# calculating
head=pc.head_orifice(d,k,Q/n)

# we also hard coded it to double check
#change in hydraulic grade
h = (Q/(n*k*a))**2/(2*g)
```

2. As the Peclet number increases, dispersion decreases and the response becomes closer to plug flow. This can be seen in the graph below as the curve forms sharper peak at a higher magnitude when the Peclet number increases to 100. Also as Peclet number increases, the amount of time for E to reach its peak is longer.

![E_peclet_graph](https://github.com/rosiekrasnoff/CEE4530/blob/master/Lab5-Reactor%20Characteristics/E_peclet_graph.png?raw=true)

Figure 1. Exit Age Distribution (E(t⋆)) for a reactor that operates as a 1-dimensional advection-dispersion reactor with Peclet numbers of 1, 10, and 100 as a function of t*.

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
