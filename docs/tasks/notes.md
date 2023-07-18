# Just a page to use as a notebook

We will add here some notes that will eventually be included in a proper page of the documentation. This is essentialy a jumble of concepts and ideas.

- Some RPCs at Coimbra are sais to be *gasless*: this means that it has ionizing gas, of course, but that it is a closed cage that does not need to be refilled in a constant gas flux. Some voices claim that the gas properties might be lost in high particle flux regime due to creation of free radicals, etc. but the fact is that for now (July 14th, 2023) they have used a really big RPC (more than 1 m * 1 m) for Cosmic Ray detection and no efficienty loss is seen. Maybe in very high luminosity (e.g. at CERN) the gas actually will lose properties.
- The thicker the gap, the higher the efficiency, since there is more distance for the avalanche to grow and become noticeable. The problem: bigger gaps require larger times for the ions to be collected (microseconds to travel a 1-2 mm gap), and also, since there is more charge involved in the processes, more charge could acumulate on the glass layers with no time to get automatically *dispersed/evacuated* through the surface, and hence reaching the initial state, so there would be a nominal electric field affected by these charges that would be smaller than the one desired. In other words: great time precision requires thinner gaps. This motivated the idea of the multiple gap in an attemp to reach the efficiency of a thick gap without losing other properties. Actually minGO has 2 gaps that would allow to reach the 90% in efficiency.
- Of course RPCs are detectors for charged particles.
- One of the plates must necessarily be resistive (also both could be), and approximately 10^12 ohms/cm to stop undesired avalanches that would create sparks that could kill the electronics. A resistivity that is too big would not allow any detection at all. The resistivity comes from the glass, the conductivity (to establish the field) comes from the paint (an acrilic, artistic, painter, paint: for some reason the manufacturer gives the resistivity as technical specification).
- The gas that miniTRASGO uses is F134a, aka freon, usually found in refrigerator units. The name is 1,1,1,2 Tetrafluoroetano and it does not hurt the Ozone layer, but it is a greenhouse effect gas. The new european(?) laws discourage its use and require special protocols for its treatment, which is making the refrigerator manufacturers to stop its use and therefore creating a surpluss that is making it cheaper for us to buy.

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/1238032e-7baf-4882-804f-d5526154e978)

- To calculate the necessary HV one needs to know the temperature of the room. From it, the density of the gas can be calculated and these RPC detectors must work in a certain regime of the Townsend ratio: E/rho (electric field applied/gas density), in particular around 240 Towsends for miniTRASGO. This means that the HV is chosen accordingly with the density of the gas, and hence with the temperature.
- The multiplication in charge in RPCs is usually 10^6.
- One if the fundamental parameters of RPC detectors is the Townsend first parameter: alpha = 1/lambda.
- There are two types of RPCs: those with 1-2 mm gaps, that are useful only for triggering and have around 1 ns of time resolution (minGO is one of those) and those called timing RPCs that have 50 ps of time resolution: these are more complicated because require gas mixing and very high electric fields, which make them delicate detectors.
- How long does it take for a muon to cross miniTRASGO?
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
- The DCS says `Copying from remote location` because it is conncecting to itself.
- The charge also has to be calibrated: it has to ramp up from 0. There are a lot of different algorithms to get this value, none of them is foolproof, infallible.
- Any event would drop the same amount of charge in the gap: a few electrons. The thing is that the HV turns this into approximately the same big charge that will be measured independently of the energy of the original particle. In the best case (*if we dream*) we could, in high multiplicity events, try to collect multiples of that charge that usually a single particle deposits. If we could get this total charge and we divide by the usual value of the charge deposited by any lonely particle we could just get the number of particles that participated in that event. WE COULD DO THIS, TAKING PROFIT ON THE FACT THAT WE HAVE TWO SIDED DETECTED STRIPS, SETTING ONE OF THE SIDES OF THE DETECTOR TO HAVE A VERY BIG DINAMIC RANGE SO IT CAN MEASURE A LOT OF CHARGE, NOT ONLY THE USUAL CHARGE DEPOSITED BY A LONELY PARTICLE (the other side would measure as usual). ACTUALLY HANS' IDEA IS TO SET A LEAD LAYER ABOVE THE DETECTOR AND, STUDYING THE MULTIPLICITY OF THE ELECTRONS AND SECONDARY PARTICLES GENERATED IN THE LEAD THAT WILL ENTER MINGO, DOING AS WE JUST SAID, GUESS THE ENERGY OF THE ORIGINAL PARTICLE THAT HIT THE LEAD.
- RPC detectors have several unique and important practical features, such as good spark protection and excellent time resolution, even down to few tens of picoseconds.
- We saw in Pablo Cabanelas talk at the 3rd TRASGO meeting (June 27th, 2023, Santiago de Compostela) that a 1 cm Pb layer above TRAGALDABAS would stop electrons and hence improving the capabilities of the detector to identify muons. I think in some sense that is not a surprise: if you have a conflict differentiating electrons from muons and you just stop the electrons then it is somehow clear that you will be much more efficient identifying muons, rigth? **Juanjo, seeing Cabanelas work, showed surprise to the fact that there were less electrons when introducing the lead: he just thought that**
- Some libraries to simulate CR showers: CRY, CORSIKA, AIRES...
- Cosmic muons, some info: at sea level there are 1 muon/min/cm^2, 3-4 GeV, angular distribution follows cos^2(theta) law...
- A telegram bot to obtain data from miniTRASGO.
- Rigidity is such an important magnitude.
- This N-S, E-W parameters are actually *north minus south* and *east minus west*. If there is a symmetry then the E-W should be zero.
- This idea:

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/45422867-b163-4117-8dce-5e3e32aac516)

- Scintillators would also work to make a miniTRASGO. Maybe plastic ones? Luis said that the cost is a nightmare.
- PCA: Principal Component Analysis. Statistical technique based on taking a set of correlated data and determining new, uncorrelated, variables.
- The showers:

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/a801a4f0-d95d-4898-8f6f-9655292cbbe9)

- 
