## Key milestones:
- Crear un datastream razonable que todo el mundo pueda entender: es decir, tratar de evitar el .hld, que es un formato no muy física-friendly. **Si queremos que miniTRASGO se use, necesitamos que los datos estén en una forma accesible. Y nada mejor para esto que tratar de definir un objetivo físico, por ejemplo, la tasa, y a partir de ahí ir construyendo de acuerdo a la necesidad**.
- Do a complete characterization of the telescope that will end up as a LIP internship paper (to present on September 7th, 8th) that could also become a full paper explaining the detector concept and development and maybe a month of stable data with rates and so on that could be published.

## To do list:
- See the hole in the gasless mingo-like RPC: it does not measure in an important region.
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
- What is the criteria to choose one of the charge values between the front and back?
- Heatmap in the celestial sphere
- If the luminosity is high then the charge can be prop to the energy, but maybe at that range the mingo is blind (it saturates).
- Add to the web-based CTS information about the logs.
- Do some geometric study.
- My time offset calibration method.
- Hans: eventually we should trigger with two planes.
- It is not a bad idea to simulate the building.
- Set milestones and distribute them.
- Set a timetable (daily, each two days, weekly, etc.) to do several important control processes: calibrate efficiency (with three layers), calibrate self trigger, and finally, maybe, measure with two layers: how often and for how long each process needs to be developed is something that we need to see.
- Decide the number of cells we are going to consider in the miniTRASGO to set a resolution value, but also to define some statistical stuff. If we determine, for exmaple, that the uncertainty in time is $\Delta t$, then the unertainty in positon is velocity of the signal in the strip*$\Delta t$ = position uncertainty: this means that we could effectively define 300 mm / position uncertainty cells in each strip, so the total number of pixels will be: 4 * 300 mm / (pos. uncertainty in each strip). So we could define how much is good statistics, i.e. how many count we need in the detector to have a minimum number of counts per pixel, which would define what are good statistics.
- Maybe the efficiency should be posed not in terms of layer efficiency but in terms of strip or even pixel efficiency, since **each strip is as different as the others not only between**
- Change layers to see if a certain behaviour is due to the geometry or to the layer itself.
- **The layers are situated at different distances to each other, BUT THE EFFICIENCY ANALYSIS DOES NOT TAKE THIS INTO ACCOUNT. Therefore, the efficienty numbers are wrong.**
- Calibrate the AU (Arbitrary Units) to get from it the position information, the time information, the charge information,etc. check specially if the charge behaviour is linear with the time difference.
- THE EFFICIENCY IN THE EFF.MAT FILES IS MADE AS THIS: ONE POINT PER .HLD FILE. SO IT COULD BE POSSIBLE THAT THERE ARE SOME .HLDs THAT HAVE TWO DIFFERENT HVs, IF THE DAQ WAS NOT STOPPED WHEN CHANGING THE HV. We are not going to avoid some .hld's being smaller because of some mistakes or because we stop the run before it is full, but we do can ensure that each .hld is only calculating with each one of the values of the HV.
- 1h approx could be enough when measuring the efficiency.
- The difference in timeStamps in Qmean, Str, Eff.mat, etc can give a clue on the mean time it takes to fill a .hlod, since each mean .mat is created from an individual .hld.
- To check the window in time of the trigger we can go to the TDC, write c001 in the search and then, once the page is loaded, see the c801 row. It says how wide the window is before and after the trigger: we could even shorten the window before, since we know that usually all the events are in -150 ns (we can see that in the Q1_F, etc files).
- ![image](https://github.com/cayesoneira/miniTRASGO-documentation/assets/93153458/04e027f9-11ed-45c9-aaa5-54365ed7d67b)
- Everyday (July 18th, 2023 for the first time) the ST is running 300 s.
- Change the matlab pdf legends and titles to be more clear about the layers.


> Blocked quote

## Crazy, future ideas
- Muon tomography with mingo.
- 


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
- The layers measure different mean rates, and it is a behavior that it has been seen in other RPC detectors here at Coimbra: it was always associated with the age of the detector, since older RPCs measure generally less in self-trigger (we say that they have less noise; **we should check also if they measure only less noise or just less measures in general**), but for this detector everything was built roughly at the same time. It could be that some layers affect the others. The thing is that, being the Trigger Multiplexer 0 is the lower layer and the Trigger Multiplexer 3 the upper layer, the values are like follow:

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/de0d5deb-82ae-4d08-94d7-6ff27f1e3ffc)
- ... as we see the **second upper layer** has the highest ratio, which does not make much sense. **We should measure with the detector put upside down to see if this is physical or if it is a detector-related effect**.
- In July 14th, 2023 night run we see good XY position maps, but not good charge diagrams.



## Questions that Alberto answered
- What is the criteria to choose of the two charges to make the charge diagram? Se hace la media.
- Can we obtain physical information of the charge diagram? It is there because of control and because we can.
- If there are several charges in the same layer, strip and event we choose the bigger one? YES, this makes sense when there is a huge particle that leaves charge in several strips next to each other: we could say then that the particle was most likely in the strip where it left the most charge. Hans wants to do multiparticle detection, but it is complex...
- Why is the XY charge diagram uniform if the XY counts diagram is not? (We know you explained this before but...) It is the mean charge of a series of events, so it should be uniform.
- The charge diagrams in the PDF are the same but with different scales? YES
- A streamer is a *descarga* that is not a spark, but it involves really a lot of charge. It is caused by the common functioning of the RPC, not due to a more energetic particle (but if there is a very energetic particle, yes, it could generate a streamer, so it is necessary but not sufficient condition). They are not desired, but are unavoidable when rising up the HV. We consider that if around a 1% or 2% of the events are streamers we are set in a good point. More than that could motivate to lower down the HV a little bit.
- How to do the streamer map? Are those points removed from the standard charge diagram? Because we saw they could appear as a second peak in the charge diagram. We take the charge spectra and just see a bump on the right side: currently our method is set a boundary from which we consider the values streamers. The charge spectra is not touched, but we do two different XY diagrams: one is the charge and other is the streamer, each one with the events that are on each side of that boundary we just defined previously. WE COULD FIT TWO CURVES INSTEAD OF SETTING A SIMPLE BOUNDARY: ONE TO THE USUAL CHARGE SPECTRA AND ONE TO THE BUMP TO DECIDE WHEN TO CONSIDER A POINT A STREAMER.
- What is the velocity of the signal inside the strip?
- Multiplicidad de los eventos? Just how many particles are involved in what we consider one event: the time window of a trigger.
- Consideraciones Este-Oeste, etc: due to the magnetic field of Earth we can see some symmetry between East-West in the arrival of CR, which would mean that measuring with good resolution in that direction is not so releveant as having good resolution in the North-South direction. This is why miniTRASGO has its strips all parallel and not crossed: because if the direction of better resolution is that in what the strip is pointing then aligning parallel all the strips could, hipotetically, give a high resolution in that precise direction. We should still study if this actually improves the resolution, because maybe the crossing of the strips even allows a better determination of position: as we see in the figure, we have to check if we obtain the small area (improved resolution) or we get the red one (worsened resolution):

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/de5d9c3d-ab24-4607-88cd-5caf9ea9cbf1)


## Questions that Alberto probably can answer
- What are those edges and accepted points in the rate vs. time diagram?
- What is the time resolution inside a strip?



