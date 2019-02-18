# Gas Transfer Prelab
### Group 1 - Jiwon Lee and Rosie Krasnoff
##### 02/20/19

1. Calculate the mass of sodium sulfite needed to reduce all the dissolved oxygen in 600 mL of pure water in equilibrium with the atmosphere and at 22∘C.

balanced equation: $${O}_{{2}} +{2SO}_{{3}}^{-{2}} \stackrel{{cobalt}}{\longrightarrow}{2SO}_{{4}}^{-{2}}$$

```python

# constants
import math as m
from aguaclara.core.units import unit_registry as u
MM_SS=126043*u.mg/u.mol # molar mass of Na2SO3
MM_O=32000*u.mg/u.mol # molar mass of water
vol_w= 600*u.mL # volume of water
DO_solubility=8.8*u.mg/u.L # solubility of dissolved oxygen in 22C water
ratio_SSw = 2 #2 moles of sodium sulfite to 1 mole water

# calculation of mass of sodium sulfite
mass_SS= vol_w.to(u.L)*DO_solubility/MM_O*ratio_SSw*MM_SS

```
$$ 600 mL \; H_2O \cdot \frac{{8.8\; mg \; O}_{{2}} }{{1L\; H}_{{2}O}} \frac{{mole\; O}_{{2}} }{{32000\; mg\; O}_{{2}} } \cdot \frac{{2\; mole\; Na}_{{2}} {SO}_{{3}} }{{mole\; O}_{{2}} } \cdot \frac{{126,000\; mg\; Na}_{{2}} {SO}_{{3}} }{{mole\; Na}_{{2}} {SO}_{{3}} } = \; 41.594 \; mg\; Na_2 SO_3 $$

41.59419 milligrams of sodium sulfite is needed to reduce all the dissolved oxygen in 600 mL of pure water.

2. Describe your expectations for dissolved oxygen concentration as a function of time during a reaeration experiment. Assume you have added enough sodium sulfite to consume all of the oxygen at the start of the experiment. What would the shape of the curve look like?

One should expect a graph of dissolved oxygen concentration as a function of time to be increasing from the initial concentration of 0 mg/L towards C*, the saturation concentration, asymptotically. The initial slope of the curve would be the most positive, and the slope would approach zero as time continues.


3. Why is k^v,l not zero when the gas flow rate is zero? How can oxygen transfer into the reactor even when no air is pumped into the diffuser?

The gas transfer coefficient is not zero even when there is no air being pumped through the water because there is gas exchange happening at the surface of the water where it meets the air. The oxygen in the air can dissolve into the water right at the surface if the dissolved oxygen concentration is very low.

4. Describe your expectations for k^v,l as a function of gas flow rate. Do you expect a straight line? Why?**

No; k^v,l does not have a linear relationship with gas flow rate. As gas flow rate increases, k^v,l generally increases, but when the concentration of oxygen is closed to the saturation point, then no matter how much you increase the flow rate of air, no more oxygen will dissolve in the water and so the relationship between k^v,l and gas flow rate is not linear.

5. A dissolved oxygen probe was placed in a small vial in such a way that the vial was sealed. The water in the vial was sterile. Over a period of several hours the dissolved oxygen concentration gradually decreased to zero. Why? (You need to know how dissolved oxygen probes work!)

Although the vial is completely sealed, the dissolved oxygen concentration gradually decreases to zero because the oxygen reacts with a silver (Ag) cathode of the probe and, thus, is reduced to water.
