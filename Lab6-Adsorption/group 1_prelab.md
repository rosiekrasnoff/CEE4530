# Adsorption Prelab
#### Group 1 - Jiwon Lee and Rosie Krasnoff
##### March 20th

1. A carbon column is packed with 15 cm of activated carbon and then used to remove 50 mg/L of red dye #40. The approach velocity is 1 mm/s, the porosity is 0.4, and the bulk density of the activated carbon is 0.5 g/cm3. How long will it take for the mass transfer zone to travel to the bottom of the carbon column?

given: $q_{50 mg/L}$ = 0.08

$$v_{mtz}=\frac{v_a C_0}{C_0\phi + q_0 \rho_{bulk \; adsorbent}}$$


$$\frac{L_{column}}{v_{mtz}} = t_{mtz}$$

It will take the mass transfer zone ___ to travel to the bottom of the carbon column. 


``` python
from aguaclara.core.units import unit_registry as u
import numpy as np

# givens
depth=15*u.cm
dye_conc=(50*u.mg/u.L).to(u.mg/u.cm**3)
v_a=(1*u.mm/u.s).to(u.cm/u.s)
p_bulk=(0.5*u.g/u.cm**3).to(u.mg/u.cm**3)
porosity=0.4
q0 = 0.08

1-0.5/2.1

v_mtz = (v_a*dye_conc)/((porosity*dye_conc)+(q0*p_bulk))
v_mtz

t_mtz = depth/v_mtz
t_mtz



```
