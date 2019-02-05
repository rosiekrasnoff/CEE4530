## Prelab Question for Acid Precipitation and Remediation of Acid Lakes Prelab

Question: How many grams of NaHCO3 would be required to keep the ANC levels in a lake above 50 μeq/L for 3 hydraulic residence times given an influent pH of 3.0 and a lake volume of 4 L, if the current lake ANC is 0 μeq/L?

Solution: 6.75 grams of NaHCO3

```python
import math
from aguaclara.core.units import unit_registry as u
# ANC_in= [OH-]-[H+] and [H+]= 10^(-pH)
pH=3
ANC=10**(-pH)*u.eq/u.L
ANC_out=50*10**-6 # eq/L

hrt=3 #hydraulic residence time = t/θ


# rearrange equation ANC_out=ANC_in⋅(1−e−t/θ)+ANC_0⋅e−t/θ
ANC_0 = (ANC_out + ANC_in*(1-math.exp(-hrt)))*math.exp(hrt) /u.L
print (ANC_0)

# ANC_0 = [NaHCO3]_0
V = 4*u.L # volume of lake
g = ANC_0*84*V*u.g # grams of NaHCO3
print (g)

```
