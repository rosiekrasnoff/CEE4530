## Laboratory Measurements and Procedures



```python
from aguaclara.core.units import unit_registry as u
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

data_file_path = "https://raw.githubusercontent.com/rosiekrasnoff/CEE4530/master/Lab1_concentration_voltage_data.tsv"

df = pd.read_csv(data_file_path,delimiter='\t')
print(df)
list(df)
columns = df.columns
print(columns)

```
