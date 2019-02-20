# Gas Transfer Prelab
### Group 1 - Jiwon Lee and Rosie Krasnoff
##### 02/20/19

1. Calculate the mass of sodium sulfite needed to reduce all the dissolved oxygen in 750 mL of pure water in equilibrium with the atmosphere and at 22∘C.

balanced equation: $${O}_{{2}} +{2SO}_{{3}}^{-{2}} \stackrel{{cobalt}}{\longrightarrow}{2SO}_{{4}}^{-{2}}$$

```python
# constants
import math as m
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
MM_SS=126043*u.mg/u.mol # molar mass of Na2SO3
MM_O=32000*u.mg/u.mol # molar mass of water
vol_w= 750*u.mL # volume of water


DO_solubility=epa.O2_sat(1*u.atm,(22+273)*u.kelvin) # calculate solubility of dissolved oxygen in 22C water
ratio_SSw = 2 #2 moles of sodium sulfite to 1 mole water
DO_solubility
# calculation of mass of sodium sulfite
mass_SS= vol_w.to(u.L)*DO_solubility/MM_O*ratio_SSw*MM_SS
print(mass_SS)

```
$$ 750 mL \; H_2O \cdot \frac{{8.92\; mg \; O}_{{2}} }{{1L\; H}_{{2}O}} \frac{{mole\; O}_{{2}} }{{32000\; mg\; O}_{{2}} } \cdot \frac{{2\; mole\; Na}_{{2}} {SO}_{{3}} }{{mole\; O}_{{2}} } \cdot \frac{{126,000\; mg\; Na}_{{2}} {SO}_{{3}} }{{mole\; Na}_{{2}} {SO}_{{3}} } = \; 52.72 \; mg\; Na_2 SO_3 $$

52.72 milligrams of sodium sulfite is needed to reduce all the dissolved oxygen in 750 mL of pure water.

2. Describe your expectations for dissolved oxygen concentration as a function of time during a reaeration experiment. Assume you have added enough sodium sulfite to consume all of the oxygen at the start of the experiment. What would the shape of the curve look like?

One should expect a graph of dissolved oxygen concentration as a function of time to be increasing from the initial concentration of 0 mg/L towards C*, the saturation concentration, asymptotically. The shape of the graph is logarithmic; the initial slope of the curve would be the most positive, and the slope would approach zero as time continues.

3. Why is k^v,l not zero when the gas flow rate is zero? How can oxygen transfer into the reactor even when no air is pumped into the diffuser?

The gas transfer coefficient is not zero even when there is no air being pumped through the water because there is gas exchange happening at the surface of the water where it meets the air; the reactor is open. The oxygen in the air can dissolve into the water right at the surface if the dissolved oxygen concentration is very low.

4. Describe your expectations for k^v,l as a function of gas flow rate. Do you expect a straight line? Why?

Yes; k^v,l has a linear relationship with gas flow rate, so I would expect a straight line. As gas flow rate increases, the bubbles increase in surface area, and so there is a larger area over which gas transfer occurs, so k^v,l increases.

5. A dissolved oxygen probe was placed in a small vial in such a way that the vial was sealed. The water in the vial was sterile. Over a period of several hours the dissolved oxygen concentration gradually decreased to zero. Why? (You need to know how dissolved oxygen probes work!)

Although the vial is completely sealed, the dissolved oxygen concentration gradually decreases to zero because the oxygen reacts with a silver (Ag) cathode of the probe and, thus, is reduced to water, so eventually no oxygen will remain.
