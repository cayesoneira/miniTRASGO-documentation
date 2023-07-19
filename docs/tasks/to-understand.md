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
- What are those edges and accepted points in the rate vs. time diagram? The *accepted* are the triggers that actually gave a measure that is registered on the file. The *edges* are those triggers that were *triggered* during the dead time of the detector, i.e. too close to other trigger so it cannot be registered into the files. The *asserted* is something we have to see.
- What is the time resolution inside a strip?
- How to measure the velocity of the signal inside a strip?
