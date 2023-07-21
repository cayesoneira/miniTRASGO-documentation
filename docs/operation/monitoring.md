# Monitoring indicators:

## Visual hardware monitoring

- mingo PC has a blue blinking light in the downside whose blink rate depends on the CPU load. A normal use requires a blinking rate. If it is stopped, bad sign.

## Data-based monitoring

- The correlation between the charge measured back and forth in the same strip has to be close to 1 (a plot helps to visualize) because the charge is not lost throughout the strip. This allows us to check if the back and front channels are well connected and also if the events are collected properly. Points over the axes will indicate that one side is measuring, the other not.
- The charge, once calibrated to have its first ramp up in the histogram in 0, has to keep like this, and has to be unimodal and both back and forth charges have to be simiral in shape. (This control condition is similar to that before).
- La uniformidad de la distribución espacial de la carga entre distintos strips de la misma layer es un criterio de control.
- The correlation between times measured back and forth, seen in a plot, can give hints on problems. We could see gaps and different angles to 45 degrees. The thicker the dispersion, the larger the strip. And a slope different to 45 degrees indicates that there is some kind of scalating acting on the large of the strip. One of the clocks might be slower? In fact we have seen gaps: **the solution passed from the fact that the calibration values of the TDC/TRB where wrongly set (see Troubleshooting)**.
- In summary: back and forth charge and time correlation diagrams are useful to see if everything is fine.
- The information from the self-trigger: the automatic measure of all the events from the detector. Counts per layer and strip and side. We should see how to turn this into an interesting graphic representation.
- The current is the most important parameter to know if a RPC has a serious problem.

## Gas flow and HV

There's a python script at `/home/rpcuser/pythonScripts/checkFlow.py` that checks the gas flow every hour, and if it reaches a certain lower threshold (currently set at 100), if turns off the HV. WE HAVE TO ADD IT TO THE ALARM MATLAB SCRIPT SO IT SENDS AN EMAIL WHEN IT STOPS THE HV, ELSE WE WILL JUST SEE THE HV TURNED OFF AND WE WILL NOT NOW WHY.

