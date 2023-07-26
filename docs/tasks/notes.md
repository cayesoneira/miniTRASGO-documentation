# Jumble of notes
We will add here some notes that will eventually be included in a proper page of the documentation. This is essentialy a jumble of concepts and ideas.

- The space-charge effect is something to take into account: 20 yr ago they ignored it and calculations were essentially wrong. This effect is just the electric field produced inside the gap by the ions themselves and its change on the nominal electric field introduced between the plates.
- The text part of the output of the `startDAQ` that are of the form `0xc001 32 3/8 54e03` are just confirming the communication with everyone of the channels (therefore there are 32 orders like that).
- The DCS says `Copying from remote location` because it is connecting to itself.
- We saw in Pablo Cabanelas talk at the 3rd TRASGO meeting (June 27th, 2023, Santiago de Compostela) that a 1 cm Pb layer above TRAGALDABAS would stop electrons and hence improving the capabilities of the detector to identify muons. I think in some sense that is not a surprise: if you have a conflict differentiating electrons from muons and you just stop the electrons then it is somehow clear that you will be much more efficient identifying muons, rigth? **Juanjo, seeing Cabanelas work, showed surprise to the fact that there were less electrons when introducing the lead: he just thought that the muons would interact with the lead emiting even more electrons, not less**.
- Some libraries to simulate CR showers: CRY, CORSIKA, AIRES...
- Cosmic muons, some info: at sea level there are 1 muon/min/cm^2, 3-4 GeV, angular distribution follows cos^2(theta) law...
- Rigidity is such an important magnitude.
- This N-S, E-W parameters are actually *north minus south* and *east minus west*. If there is a symmetry then the E-W should be zero.
- Anger camera concept: a potential future branch for the TRASGO project.
- PCA: Principal Component Analysis. Statistical technique based on taking a set of correlated data and determining new, uncorrelated, variables.
- If the luminosity is high then the charge can be prop to the energy, but maybe at that range the mingo is blind (it saturates).

## Attention
- The gas emptying test is not giving the expected results (July 22nd, 2023): the gas is leaking much more than expected, skyrocketing the rate in selftrigger. This indicates that we should revisit the method of polipropilene fusion, since the assembly is not as tight as believed. If the detector is not so tight we might not be able to reach the 1 cc/min gas flux nominal rate of performance, and maybe we will need more (and therefore it will be more expensive).
