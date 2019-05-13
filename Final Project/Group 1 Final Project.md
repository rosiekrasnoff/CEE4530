# String Digester
### Rosalie Krasnoff and Jiwon Lee
##### May 13th 2019

## Introduction and Objectives

Strings could provide an alternative "filter media" for a modified trickling filter in a wastewater treatment system. Trickling filters are a technology that have not been improved significantly since the 1970s or 80s, and there is great room for improvement of the efficiency of treatment and use of space by improving the design. There is a team of students at Cornell on AguaClara working on the development of a string digester for secondary wastewater treatment, which could potentially offer huge increases in energy and treatment efficiency. This design features wastewater being treated by biofilm as it trickles down string, in a design that would feature hundreds to thousands of strings hanging millimeters apart, each treating a trickle of wastewater.

The development of this project is still a work in progress, and key components of the design have yet to be verified. One aspect of the design that required experimentation to confirm proof of concept was the question of whether there would be enough oxygen available to the wastewater on the string to allow for proper treatment. This lab experiment was designed with the objective of determining whether aeration occurs as the water trickles down the string and how variables like the type of string and flow rate might impact the degree of aeration. The availability of oxygen is necessary in order for treatment to occur, so we needed to verify that aeration occurs for the current design of a string digester to be possible.


## Procedures
#### Apparatus
The experimental apparatus consists of a metal rod, microtubing, string (or yarn), small effluent collector, peristaltic pump, and deoxygenated solution (Fig. 1).

![schematic](https://github.com/rosiekrasnoff/CEE4530/blob/master/Final%20Project/schematic.PNG?raw=true)
Figure 1. Schematic of string aeration experiment.

1. Step up experiment as shown in Figure 1. Use a peristaltic pump installed with a microtubing head.
2. Cut an excess of microtubing and stretch one of the edges to be thin enough to go through the tabs for the peristaltic pump. Prepare the microtubing as is typical and install it into the peristaltic pump.
3. The purpose of the metal rod is to have access to the ceiling so make sure to obtain one that's long enough so that you can hook it onto the ceiling, but not too long that it will make the string too short.
4. Cut the string/yarn to be approximately an inch off the lab table once connected to the metal rod.
5. Tie the string/yarn onto the metal rod and hook it to the ceiling before moving further to make sure it's at a good length.
6. Carefully position and tape the microtubing to the string/yarn so that each droplet will fall directly onto said string/yarn. This is important since we're testing the aeration potential of a string digester and don't want the water droplets to fall directly into the effluent collector.
7. Hang the metal rod-string/yarn-microtubing apparatus onto the ceiling.

#### Dissolved Oxygen Probe
1. Install the membrane cap on the Dissolved Oxygen Probe. You can refer to the [textbook](https://monroews.github.io/EnvEngLabTextbook/Gas_Transfer/Gas_Transfer.html#install-the-membrane-cap-on-the-dissolved-oxygen-probe).
2. Calibrate the DO Probe by referring to the [textbook](https://monroews.github.io/EnvEngLabTextbook/ProCoDA/ProCoDA.html#dissolved-oxygen-sensor-do).
3. Store the probe in a beaker with distilled water while running the trials.
4. The probe does not need to be calibrated again for the rest of the experimental period unless the probe readings seem to be off. The membrane cap should be dried after every experiment day and reinstalled before every experiment day.

#### Experimental Method
Test aeration potential for both the string and yarn at varying rpms with varying amounts of $Na_{2}SO_3$.
1. Set up the apparatus,
2. Make the deoxygenated solution by filling a 100 mL beaker with 1000 $u$L of the stock 0.1 $\frac{mg}{mL}$ $CoCl_2$ solution and the rest with distilled water then adding the appropriate amount of $Na_{2}SO_3$.
3. Pump the deoxygenated solution at a high rpm (between 50 and 100) to wet the string/yarn. The water won't trickle down properly if the string/yarn isn't wetted. Do this for about 5 minutes. Use a different beaker than the designated effluent collector to collect the water.
4. Lower the rpm to the testing pumping rate and let it run for 10 minutes at this lower rpm to allow for the flow rate to reach an stable state.
5. After running it for about 10 minutes, start the actual collection with the effluent collector until you have about 2 mL to make an accurate DO measurement.
6. Measure the DO using the DO probe. Make sure to slightly wiggle the probe around because the DO probe tends to consume oxygen as it runs so it's important that you don't let it sit in one spot for too long as the dissolved oxygen level will fall and give an inaccurate reading.
7. Repeat each trial at least twice.
8. Note that the deoxygenated solution will need to be remade every time you run the experiment. The solution can simply be dumped down the sink at the end of each experiment day since the $CoCl_2$ is diluted to such a low concentration.


## Results and Discussion
### Data Analysis

*add tables*
Table 1. Constant flow rate of 5rpm.
|COD (from Na2SO3 in 100 mL water) | DO for flat string (mg/L) | DO for loopy yarn (mg/L) |
| ----- | ------- | ---------- |
|**20 mg/L** (from 0.016 g Na2SO3)| 7.2 6.7 | 5.7, 7.0, 7.0  |
|**200 mg/L** (from 0.158 g Na2SO3)| 2.1, 5, 4.1 |3.3, 5.8, 6.7 |
|**503 mg/L** (from 0.397 g Na2SO3)| 0.3 | 0.15, 1.0|

Table 2. Constant COD of **200 mg/L** (from 0.158 g Na2SO3)

| Flow rate | DO for flat string (mg/L) | DO for loopy yarn (mg/L) |
| ----- | ------- | ---------- |
|5 rpm | 2.1, 5, 4.1 | 5.8, 6.7  |
|20 rpm | 2.1, 2, 0.3 | 5.6, 5.05, 4.9, 4.5 |
|50 rpm | 0.2, 0.3 | 0.5, 1.2, 1, 0 |






![string_5rpm](https://github.com/rosiekrasnoff/CEE4530/blob/master/Final%20Project/string_at_5rpm.png?raw=true)

Figure 1. Independent variable: COD (from Na2SO3 added)
Constant: Flow rate = 5rpm (0.1 mL/min)


## Conclusion

## Suggestions/Comments

We faced a lot of issues with using the DO probe. Unfortunately, low flow rate and DO probe consumption of oxygen made taking a DO reading difficult. Ideally, we would have the outflow actively flowing over a DO probe continuously to be able to have constant measurements, but that isn’t possible because our flow rate needs to be quite slow and we're measuring in a very small container with a limited amount of volume (~ 2 mL). Even with our "wiggle" method, the DO probe would continue to consume oxygen so we were never sure that our measurements were accurate. Thus, in the future, we would recommend getting micro DO probes. Additionally, our string digester would often dry up during a trial due to evaporation, especially when running at slower flow rates, due to lab environment. Moving forward, we would suggest running the experiment in a setting more similar to the real world in regards to humidity levels.


# Appendix
``` python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.physchem as pc
import aguaclara.core.utility as ut
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats


# Flow rate = 5 rpm
# Data for flat string
Na2SO3_string_5rpm = (np.array([0.016,0.016,0.159,0.159,0.159,0.397])*u.g).to(u.mg)
DO_string_5rpm = np.array([7.2,6.7,2.1,5,4.1,0.3])*u.mg/u.L

slope1, intercept1, r_value, p_value, std_err = stats.linregress(Na2SO3_string_5rpm, DO_string_5rpm)
slope1 = slope1/u.mg

plt.plot(Na2SO3_string_5rpm, DO_string_5rpm, 'o', label='measured DO using string at 5rpm')
plt.plot(Na2SO3_string_5rpm, intercept1 + slope1*Na2SO3_string_5rpm, 'r', label='fitted line')
plt.xlabel(r'$Na_{2}SO_{3}$ (mg)');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/string_at_5rpm.png')
plt.show()

# DO data for loopy yarn
# 3.3 point might not be good!!!
Na2SO3_yarn_5rpm = (np.array([0.016,0.016,0.016,0.158,0.158,0.158,0.397,0.397])*u.g).to(u.mg)
DO_yarn_5rpm = np.array([5.7,7,7,3.3,5.8,6.7,.15,1])*u.mg/u.L

slope2, intercept2, r_value, p_value, std_err = stats.linregress(Na2SO3_yarn_5rpm, DO_yarn_5rpm)
slope2 = slope2/u.mg

plt.plot(Na2SO3_yarn_5rpm, DO_yarn_5rpm, 'o', label='measured DO using yarn at 5 rpm')
plt.plot(Na2SO3_yarn_5rpm, intercept2 + slope2*Na2SO3_yarn_5rpm, 'r', label='fitted line')
plt.xlabel(r'$Na_{2}SO_{3}$ (mg)');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/yarn_at_5rpm.png')
plt.show()


# Combine both plots
plt.plot(Na2SO3_string_5rpm, DO_string_5rpm, 'og', label='string')
plt.plot(Na2SO3_string_5rpm, intercept1 + slope1*Na2SO3_string_5rpm, 'g', label='string fit')
plt.plot(Na2SO3_yarn_5rpm, DO_yarn_5rpm, 'ob', label='yarn')
plt.plot(Na2SO3_yarn_5rpm, intercept2 + slope2*Na2SO3_yarn_5rpm, 'b', label='yarn fit')
plt.xlabel(r'$Na_{2}SO_{3}$ (mg)');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/both_at_5rpm.png')
plt.show()


# Constant Na2SO3
# Data for flat string
Flowrate_string = np.array([5,5,5,20,20,20,50,50])*u.revolution/u.min


Flowrate_string = np.array([.105,.105,.105,,0.413,0.413,0.414,1.0315,1.0315)
DO_string = np.array([2.1,5,4.1,2.1,2,0.3,0.2,0.3])*u.mg/u.L


slope3, intercept3, r_value, p_value, std_err = stats.linregress(Flowrate_string, DO_string)
slope3 = slope3/Flowrate_string.units

plt.plot(Flowrate_string, DO_string, 'o', label='measured DO using string at various flow rates')
plt.plot(Flowrate_string, intercept3 + slope3*Flowrate_string, 'r', label='fitted line')
plt.xlabel(r'Flow Rate $\frac{rev}{min}$');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/string_at_rpms.png')
plt.show()

# DO data for loopy yarn
# 3.3 point m

# DO data for loopy yarn
Flowrate_yarn = np.array([5,5,20,20,20,20,50,50,50,50])*u.revolution/u.min
DO_yarn = np.array([5.8,6.7,5.6,5.01,4.9,4.5,0.5,1.2,1,0])*u.mg/u.L

slope4, intercept4, r_value, p_value, std_err = stats.linregress(Flowrate_yarn, DO_yarn)
slope4 = slope4/Flowrate_yarn.units

plt.plot(Flowrate_yarn, DO_yarn, 'o', label='measured DO using yarn at various flow rates')
plt.plot(Flowrate_yarn, intercept4 + slope4*Flowrate_yarn, 'r', label='fitted line')
plt.xlabel(r'Flow Rate $\frac{rev}{min}$');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/yarn_at_rpms.png')
plt.show()

# Combine both plots
plt.plot(Flowrate_string, DO_string, 'og', label='string')
plt.plot(Flowrate_string, intercept3 + slope3*Flowrate_string, 'g', label='string fit')
plt.plot(Flowrate_yarn, DO_yarn, 'ob', label='yarn')
plt.plot(Flowrate_yarn, intercept4 + slope4*Flowrate_yarn, 'b', label='yarn fit')
plt.xlabel(r'Flow Rate $\frac{rev}{min}$');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.legend()
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/both_at_rpms.png')
plt.show()

# DO vs HRT for string
String_V = 0.77*u.mL
FR_string = np.array([.105,.105,.105,.420,.420,.420,1.05,1.05])*u.mL/u.min
HRT = String_V/FR_string
plt.plot(HRT, DO_string, 'og', label='string')
plt.xlabel(r'HRT ($\theta$)');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.title('HRT vs DO of Flat String')
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/stringHRT.png')
plt.show()

# DO vs HRT for yarn
Yarn_V = 1.858*u.mL
FR_yarn = np.array([.105,.105,.420,.420,.420,.420, 1.05, 1.05, 1.05,1.05])*u.mL/u.min
HRT_yarn = Yarn_V/FR_yarn
plt.plot(HRT_yarn, DO_yarn, 'ob', label='yarn')
plt.xlabel(r'HRT $\theta$');
plt.ylabel(r'DO ($\frac{mg}{L}$)');
plt.title('HRT vs DO of Loopy Yarn')
plt.savefig('C:/Users/Jiwon Lee/github/rosie/Final Project/yarnHRT.png')
plt.show()

#calculate COD from amount of Na2SO3 added
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.utility as ut
from scipy import optimize
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats

mass_NA2SO3=0.158*u.g

#convert from mg O2 to mg NA2SO3
conv=7.897


COD=mass_NA2SO3/(100*u.mL)/conv
COD
COD.to(u.mg/u.L)

print('Mass to add to 100 mL:',mass_NA2SO3.to(u.g/u.mL)*100*u.mL)




```
