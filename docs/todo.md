## To do list:
- Find the voltage plateau: study the behaviour of the efficiency with the high voltage (HV). We are around 5.5 kV.
- See how temperature, humidity, pressure affect the detector.
- Study the gas flow: if it is equal, if it decreases with time, which is the optimal value of flux (to save gas if possible).
- Document all data and software.
- See if an autocalibration software exists; else, write it. It should use three layers to calibrate the fourth for every layer.
- Write a visual interface for controlling the voltage, seeing the temperature, etc.
- See if it is interesting that some strips are wider than others in terms of resolution.
- See if it is interesting that the strips are crossed every layer, and even if it is interesting that they are of different shapes (just like the Coimbra RPC).
- Avoid if possible the relé for the future.
- Check the Alberto's power supply. If it works we will not need to change dramatically the architexture for future mingos.
- Calibrate mingo offset on time difference to obtain a realistic position of the event.
- Try to guess some physics we could learn from mingo.
- Recalculate the velocity of propagation of the signal on the strip
- Calculate the real active area, which is the area of the paint, to see what is the nominal large of the strips.
- Asignar nombres a las capas y ver dónde están los canales.
- Sometimes there are streamers: descargas bastante grandes que no llegan a ser chispas pero que se ven en los diagramas de carga sobre la superficie. Appear as a second peak in the charge spectrum histogram.
- En última instancia la forma de conocer a qué canal se corresponde cada strip es desconectar uno de los canales y ver después cuál deja de aparecer en el pdf.
- Create a code to reject in the efficiecy calculations those muons that do not pass through the forth layer (the first or the forth) because it passes throught the other three and we know that given that angle it goes outside of the detector.
- Change the pdf generation to include absolutely all the plots, specially the control plots. **We can use the excel from which the pdf is generated: there we can indicate what new plots we want (the variables must exist, of course)**.
- Add to the correlation plots a calculation on regression or directly in correlation to see when we are operating in normality.
- Update the code to measure once in a while automatically (*self-trigger*) to adquire all the events that the detector is measuring, not only muon coincidences, to characterize noise and health of the detector, etc. The thing is that a lot of events are occuring in the detector: streams coming from the electric system itself, gammas, electrons, etc.
- Correct the efficiency to be able to remeasure the voltage plateau.
- The efficiency in several planes: 4: 0.6, 3: 0.8, 2: 0.8, 1: 0.4. All should have the same value, but for
- Calculate the geometrical acceptance to check the differences in number in counts between layers.
- We can use planes 2 and 3 to estimate the voltage plateau because it is the best efficiency estimation.
- Modify to not use password to access the mingo PC.
- TDCs have to be calibrated. Apparently temperature plays a role when we want resolutions of 10 ps because it can change the size of some hardware component in the TDC, but since we need 100 ps or so temperature will not be important. Probably all this problem in the correlations can be solved just by calibrating correctly the TDC, since Alberto noticed there are numbers that do not have appropriate values (but until now we just did not pay attention to it).
- Remember: the width of the front-back correlation in time gives the total width of the strip.
- My way (Caye) to calibrate the offset of the strip: fit a y = a + b*x line to the correlation cloud in times, then the a must be the center offset for every strip.
- Calculate the zero of the charge is a actually difficult algorithm, but very interesting one to create.
- Create a tmux window for the HV.
- 

> Blocked quote

## To understand:
- The wide strip does not get more counts in the first layer (lower one): is this ok? why? *Could it be that because of being at the edge the fact of being wider does not five advantage?*
- Investigate why some strips appear larger than they are once applying the propagation velocity to get from time to distance. Maybe because the propagation velocity is different in some strips? Check for the plateau voltage and repeat the test.
- See why some random maxima in temperature are correlated with maxima at the muon detection. In words of Alberto, *sometimes the detector has a general offset*. We still do not know where it comes from.
- We suspect that layer 2 (second lower) has changed the name of the channel for some strips (maybe 1 and 2) because there is a strip with 1.3 times the counts of the rest of the strips. The wide strip is 1.5 wider than the narrow ones. **The same happens to the third layer**.
- El plano 1 (pág. 3 del pdf), en el mapa de eficiencia, no permite ver strips, sino que se ve una *patata caliente*: hay muchos puntos eficientes fuera del área del detector, que debería ser cuadrada. Esto **no** se puede explicar, en principio, mediante una coincidencia casual de un muón que no tiene nada que ver con el muón que pasa por los otros tres strips y llega al de abajo. Same with the 4th layer.
- In general the thinner strips have not all the same counts, when they should. Only the thicker strip should have more counts (a 50\% more).
- One of the strips of the layer 1 has far less counts than what it should. Probably an electronic issue.
- **See if the gaps in the correlation diagram in charge and time are due to the strip or to the electronics**.
- These gaps and the difference in slope are actually the reasons why some of the strips appear larger.
- The voltages applied diverge with time one from the other. It does not seem like a problem, but we do not know why.
- 

## The current plan:
- We have a problem with the correlation plots: some of the points are displaced with gaps and in a different-than-1 slope which

## Layer by layer (complete with the upper):
- Layer 1 (lower): wider strip does not get more counts.
- Layer 2 (second lower): heavyside
- Layer 3 (second upper): we should have 100\% efficiency 
- Layer 4 (uppermost): 
