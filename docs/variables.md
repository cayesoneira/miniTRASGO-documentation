# Variables and diagrams

## Variables given by the DAQ
The main variables the detector allows to obtain are times and charges, but the charge calculation comes from the width of the digital signal that is created as a response to the main signal.

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/95f912cf-b274-4cfb-8519-419436ef5dd8)

We have time and charge for each side of each strip. These events are saved in T1_F, T1_B, Q1_F and Q1_B. Then T1_F and T1_B are substracted to obtain the position on the strip (we will need a calibration) and a selection is made between Q1_F and Q1_B to obtain the final charge spectra based on the criteria **WHICH ONE???**.

## Variables derived from those
- Difference in times multiplied by the velocity of the signal in the strip gives the position of the event in the strip.
- The charge can give a measure of the energy of the event???
- Since the trigger can be configured to be the crossing of three planes, i.e. a coincidence, we can measure with certain resolution the direction of incidence of the muon.
- 

Interesting diagrams:
- Charge spectra:
- XY diagram: comes from the time differences; needs to be calibrated to eliminate the offset of the center of the band.
- XY charge diagram:
- XY Streamer diagram:
- XY Efficiency map:
- NEW: Time F-B correlation map:
- NEW: Charge F-B correlation map:
- logs. vs time: intensity, high voltage, temperature, pressure, humidity, rate of events
