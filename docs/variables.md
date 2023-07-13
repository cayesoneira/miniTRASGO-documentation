# Variables and diagrams
The main variables the detector allows to obtain are times and charges, but the charge calculation comes from the width of the digital signal that is created as a response to the main signal.

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/95f912cf-b274-4cfb-8519-419436ef5dd8)

We have time and charge for each side of each strip. These events are saved in T1_F, T1_B, Q1_F and Q1_B. Then T1_F and T1_B are substracted to obtain the position on the strip (we will need a calibration) and a selection is made between Q1_F and Q1_B to obtain the final charge spectra.
