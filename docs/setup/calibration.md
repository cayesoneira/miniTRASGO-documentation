## Report creation
In ~/gate/bin the script `./sendReport.sh` can be executed to create a report in pdf. It is the only way right to force the creation of the merged .mat of Efficieny, Mean charge, etc. until we add a new one. And this merged datafiles accumulate the previous 10 days (this can be modified in the script).

The data processing will only take place if there are enough .hld files in queue. We can then *push* the creation of .mat files just by executing 

## Plateau calibration
It has to be performed at every location (and maybe several times a year or at the beginning of a measure campaign) since it depends on temperature, pressure, etc.



## FEE Charge calibration curve
Get the transformation from AU in time-charge to the proper units of charge (Coulombs).

![FEE calibration setup](https://github.com/cayesoneira/miniTRASGO-documentation/assets/93153458/c8b0de84-0890-4c57-9012-c443c591541c)
