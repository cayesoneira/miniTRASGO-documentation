# Jumble of notes
We will add here some notes that will eventually be included in a proper page of the documentation. This is essentialy a jumble of concepts and ideas.

- The rates can be accepted or edges. Accepted means that it triggered and the detector had enough time to get the charge signal. Edges means that the trigger was done so close to other signal that the system, even if it can count as a rate since it is detected by the TRB, cannot actually store the information of time and charge. Hence, it will only contribute to the rate, but not to the other analysis.
- To calculate the necessary HV one needs to know the temperature of the room. From it, the density of the gas can be calculated and these RPC detectors must work in a certain regime of the Townsend ratio: E/rho (electric field applied/gas density), in particular around 240 Towsends for miniTRASGO. This means that the HV is chosen accordingly with the density of the gas, and hence with the temperature. We have several options, anyway, we could also (and it is the option we are choosing) set the voltage constant around the plateau and later correcting the rates by the efficiency, which is a better option than changing everytime the potential: an error could be devastating for the detector and also we are changing constantly the regime of the electric field, which needs to stabilize inside the RPC.
- The multiplication in charge in RPCs is usually 10^6.
- One if the fundamental parameters of RPC detectors is the Townsend first parameter: alpha = 1/lambda.
- There are two types of RPCs: those with 1-2 mm gaps, that are useful only for triggering and have around 1 ns of time resolution (minGO is one of those) and those called timing RPCs that have 50 ps of time resolution: these are more complicated because require gas mixing and very high electric fields, which make them delicate detectors.
- Simulating the building is interesting (as we saw in the TRASGO meeting at USC).
- The space-charge effect is something to take into account: 20 yr ago they ignored it and calculations were essentially wrong. This effect is just the electric field produced inside the gap by the ions themselves and its change on the nominal electric field introduced between the plates.
- Some muon tomography could be done with mingo, since it has 4 planes. Study this.
- All the software for RPCs in Coimbra is made for HADES, so it is fairly complicated.
- The time values given by the detector are negative because the trigger is always after the measurements: the buffer stores everything for a while, then we decide to keep it or not.
- `daq_anal` is apparently the software that takes the `.hld` and writes it in hexa from binary.
- What does `.hld` stand for?
- The charge is given in ns becasue it is calculated as a width in times by the mother and doughterboards.
- In principle the discriminator signal is a constant value function. We could change it up and down to let more or less events happen (higher discrimination values will limit the amount of events considered) but in principle no other function but a constant can be given to the discriminator.
- No fear with misconnecting cables in mingo BUT WITH THOSE TWO IDENTICAL ONES, that we should paint or so.
- The internal clock of the mingo PC is set in UTC (Coordinated Universal Time).
- ASCIS is a chip that carries out the same function as the DB and MB (red electronics): amplifying, turning into digital, etc.
- If the TRB changes an IP has to be given to it from mingo PC, which is a process *that a computer engineer would do in 30 ms*. We will not take notes on how to do it since it only has to be done in very special ocasions.f
- trbnetd is a daemon that allows communication with the TRB.
- From the ssh connection to mingo PC we can execute `sudo reboot` to restart the mingo PC.
- fpga is the neuralgic center of the TRB.
- `watch -n <number of seconds> <command>` will repeat the same command given any n seconds.
- The text part of the output of the `startDAQ` that are of the form `0xc001 32 3/8 54e03` are just confirming the communication with everyone of the channels (therefore there are 32 orders like that).
- The plateau should be around 5.5 kV.
- The DCS says `Copying from remote location` because it is connecting to itself.
- The charge also has to be calibrated: it has to ramp up from 0. There are a lot of different algorithms to get this value, none of them is foolproof, infallible.
- Any event would drop the same amount of charge in the gap: a few electrons. The thing is that the HV turns this into approximately the same big charge that will be measured independently of the energy of the original particle. In the best case (*if we dream*) we could, in high multiplicity events, try to collect multiples of that charge that usually a single particle deposits. If we could get this total charge and we divide by the usual value of the charge deposited by any lonely particle we could just get the number of particles that participated in that event. WE COULD DO THIS, TAKING PROFIT ON THE FACT THAT WE HAVE TWO SIDED DETECTED STRIPS, SETTING ONE OF THE SIDES OF THE DETECTOR TO HAVE A VERY BIG DINAMIC RANGE SO IT CAN MEASURE A LOT OF CHARGE, NOT ONLY THE USUAL CHARGE DEPOSITED BY A LONELY PARTICLE (the other side would measure as usual). ACTUALLY HANS' IDEA IS TO SET A LEAD LAYER ABOVE THE DETECTOR AND, STUDYING THE MULTIPLICITY OF THE ELECTRONS AND SECONDARY PARTICLES GENERATED IN THE LEAD THAT WILL ENTER MINGO, DOING AS WE JUST SAID, GUESS THE ENERGY OF THE ORIGINAL PARTICLE THAT HIT THE LEAD.
- RPC detectors have several unique and important practical features, such as good spark protection and excellent time resolution, even down to few tens of picoseconds.
- We saw in Pablo Cabanelas talk at the 3rd TRASGO meeting (June 27th, 2023, Santiago de Compostela) that a 1 cm Pb layer above TRAGALDABAS would stop electrons and hence improving the capabilities of the detector to identify muons. I think in some sense that is not a surprise: if you have a conflict differentiating electrons from muons and you just stop the electrons then it is somehow clear that you will be much more efficient identifying muons, rigth? **Juanjo, seeing Cabanelas work, showed surprise to the fact that there were less electrons when introducing the lead: he just thought that**
- Some libraries to simulate CR showers: CRY, CORSIKA, AIRES...
- Cosmic muons, some info: at sea level there are 1 muon/min/cm^2, 3-4 GeV, angular distribution follows cos^2(theta) law...
- Rigidity is such an important magnitude.
- This N-S, E-W parameters are actually *north minus south* and *east minus west*. If there is a symmetry then the E-W should be zero.
- This idea:

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/45422867-b163-4117-8dce-5e3e32aac516)

- Scintillators would also work to make a miniTRASGO. Maybe plastic ones? Luis said that the cost is a nightmare.
- PCA: Principal Component Analysis. Statistical technique based on taking a set of correlated data and determining new, uncorrelated, variables.
- The showers:

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/a801a4f0-d95d-4898-8f6f-9655292cbbe9)

- Sometimes there are streamers: descargas bastante grandes que no llegan a ser chispas pero que se ven en los diagramas de carga sobre la superficie. Appear as a second peak in the charge spectrum histogram.
- En última instancia la forma de conocer a qué canal se corresponde cada strip es desconectar uno de los canales y ver después cuál deja de aparecer en el pdf.
- The efficiency in several planes: 4: 0.6, 3: 0.8, 2: 0.8, 1: 0.4. All should have the same value, but for
- If the luminosity is high then the charge can be prop to the energy, but maybe at that range the mingo is blind (it saturates).
- THE EFFICIENCY IN THE EFF.MAT FILES IS MADE AS THIS: ONE POINT PER .HLD FILE. SO IT COULD BE POSSIBLE THAT THERE ARE SOME .HLDs THAT HAVE TWO DIFFERENT HVs, IF THE DAQ WAS NOT STOPPED WHEN CHANGING THE HV. We are not going to avoid some .hld's being smaller because of some mistakes or because we stop the run before it is full, but we do can ensure that each .hld is only calculating with each one of the values of the HV.
- 1h approx could be enough when measuring the efficiency.
- To check the window in time of the trigger we can go to the TDC, write c001 in the search and then, once the page is loaded, see the c801 row. It says how wide the window is before and after the trigger: we could even shorten the window before, since we know that usually all the events are in -150 ns (we can see that in the Q1_F, etc files).
-  ![image](https://github.com/cayesoneira/miniTRASGO-documentation/assets/93153458/04e027f9-11ed-45c9-aaa5-54365ed7d67b)
-  Everyday (July 18th, 2023 for the first time) the ST is running 300 s.



## From Hans' presentation
Algunos observables directos accesibles a un detector tipo MINGO:
- Tasa de rayos cósmicos aislados
- Tasas de distintas multiplicidades de rayos cósmicos
- Tasa de muones
- Tasa de electrones
- Espectro de energía de electrones
- Distribución angular de incidencia de muones
- Distribución angular de incidencia de electrones
- Distribución del tiempo de llegada entre rayos cósmicos
- Distribución de tiempos entre eventos
- Distribución de tiempos en grupos de partículas


Observables indirectos:
- Variaciones en la actividad solar y clima espacial
- Variaciones atmosféricas
- Variaciones en el campo magnético terrestre
- Variaciones en la tasa total del fondo de rayos cósmicos


Otras posibilidades:
- Los detectores pueden disponerse fácilmente en red, sincronizados, para cubrir
mayores superficies

## Attention
- The gas emptying test is not giving the expected results (July 22nd, 2023): the gas is leaking much more than expected, skyrockeing the rate in selftrigger. This indicates that we should revisit the method of polipropilene fusion, since the assembly is not as tight as believed. If the detector is not so tight we might not be able to reach the 1 cc/min gas flux nominal rate of performance, and maybe we will need more (and therefore it will be more expensive).
- The current is not a good monitoring indicator in minGO (even though it usually is in RPCs): it is around 150 nA, when in Hades was in the order of 4 nA: this means that this current is not indicator of avalanches, but some residual currents flowing continously through the detector. Also, we can conclude this from the fact that the change in voltage does not change at all the current measured. Also it does not change when the gas starts to lower (in the gas emptying test).


![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/1238032e-7baf-4882-804f-d5526154e978)

