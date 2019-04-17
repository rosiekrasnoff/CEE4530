

```python

from aguaclara.research.peristaltic_pump import vol_per_rev_3_stop
from aguaclara.core.units import unit_registry as u

round(vol_per_rev_3_stop(color="orange-yellow"), 6)

Flow_per_rev=0.019439*u.mL
rev_per_min=5/u.min

FR=Flow_per_rev*rev_per_min
FR

FR=.064*u.mL/u.min

(1*u.ml/FR).to(u.min)

```
