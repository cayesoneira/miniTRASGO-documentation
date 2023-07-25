# Monitoring

## Daily report
The miniTRASGO sends a daily report in pdf format with several figures of interest. It includes the logs from months (temperature, humidity, pressure, rate...) and also the trigger data from previous days (how previous?) processed into maps of counts and charge, as well as mean values of charge and streamers.

## Visual hardware monitoring

- mingo PC has a blue blinking light in the downside whose blink rate depends on the CPU load. A normal use requires a blinking rate. If it is stopped, bad sign.
- The mingo PC has a fan to refrigerate the box of the PC that works every time.
- Check all the wires are well connected, and also the pipes.

## Data-based monitoring
We present some variables and how we can do monitoring with them.

### Time and charge back and forth
Taking the most raw data, which is the time and charge (instant and width of the LVDS) in each channel (i.e. each side of the strip) can give interesting monitoring analysis.
- The correlation between times measured back and forth, seen in a plot, can give hints on problems. The thicker the dispersion, the larger the strip, since the dispersion informs on the strip width. On the other hand, the correlation should be close to 1 since the sum of the times is the length of the strip, so it is constant.
- The correlation between the charge measured back and forth in the same strip has to be close to 1 (a plot helps to visualize) because the charge is not lost throughout the strip. This allows us to check if the back and front channels are well connected and also if the events are collected properly. Points over the axes will indicate that one side is measuring, the other not.

In summary: back and forth charge and time correlation diagrams are useful to see if everything is fine.

### Maps
Maps of position and charge, both in coincidence and in self trigger, give information on critical areas of the layer. The count diagram should depict a number of counts higher in the wide strip. The charge, on the other hand, since it is mean charge per event, should be uniform. Any variation from this should be studied properly, since it is most likely no physical effects but a instrumental issue. The strips, but the wide one, should not be distinguished from one another if the RPC performance is alright: every strip should act the same.

If there are areas that in different observations often display a lot of streamers, it means that there is an error in that region.

### Charge spectrum
- The charge, once calibrated to have its first ramp up in the histogram in 0, has to keep like that calibration.
- Also, the distribution is bimodal with two peaks: one for the usual avalanches and other one for the streamers, which have a much bigger value.
- The uniformity of the spatial distribution of the mean charge between different strips of the same layer is also a control criterion (even though some geometrical considerations should be taken into account).

### Streamers
1-2% of Streamers is tolerable. We should not be over 10%. Areas of common streamer

### From the log files
- The pure information on rates,specially in self trigger, can also give very direct clues on the different performance of the strips. And so we could see if there is an error in any of them.
- The HV variation shold be checked to see if there is some error.
- Environment values (temperature, pressure, hunidity) have to be in a reasonable interval.
- The current is usually the most important parameter to know if a RPC has a serious problem. Not in miniTRASGO, since the residual currents are actually pretty high.
- The gas flow should never be below a certain threshold that it is important to define. There is a Python script located at `/home/rpcuser/pythonScripts/checkFlow.py` responsible for monitoring gas flow every hour. If the gas flow drops below a specified lower threshold (currently set at 100), it automatically turns off the HV (High Voltage). To ensure timely notification, we need to incorporate this Python script into the alarm MATLAB script. By doing so, the system will send an email alert whenever the HV is turned off. This way, we will be promptly informed of any HV shutdowns and the reason behind it, avoiding confusion or uncertainty.

