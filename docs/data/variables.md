# Data extracted by mingo
In this page we explain, based on mingo design, what is the data about, from raw to some options for the possible derived variables.

## Raw data
The main variables the detector allows to obtain are times and charges, but the charge calculation comes from the width of the digital signal that is created as a response to the main signal, as it was said in other pages. The data collects, then, time and charge for each side of each strip. These events are saved in T1_F, T1_B, Q1_F and Q1_B, for the lowest layer (we should change this according to the new criteria), etc. A value of time is stored aside with each event information.

## Processed data
From this raw data there are some analysis we can perform: some of them are simple and important for monitoring, but we also include other more advanced ideas that can be used to de physics with the telescope.

### Standard analysis
- T1_F and T1_B are substracted (we will need a calibration). This difference in times multiplied by the velocity of the signal in the strip gives the position of the event in the strip. We can get maps of counts from this.
- A mean is made between Q1_F and Q1_B to obtain the charge por event. If there is an event with more than one strip that collected charge then the strip with the highest charge is taken. Maps of charge can be obtained from this, as well as charge spectra distributions. This includes streamer maps.
- Since the trigger can be configured to be the crossing of three planes, we can measure efficiency for the fourth plane.

### Advanced analysis
- The directional information can 
