# Data: general considerations
Im this section we discuss the fundamental parts of the preliminary data treatment until it is ready to extract and analyze.

## Data retrieval

If needed, files from miniTRASGO can be transferred to a local machine using `scp`.

    scp <user>@<remote machine>:<remote file> <local directory>
  
For example:

    scp rpcuser@192.168.3.216:gate/system/devices/RCP01/data/dcData/data/2023-07-13-EffMap.mat ~/

## About the units of the timeStamps
In MATLAB, the date format, for example 739077.6528125, represents a serial date number. MATLAB uses serial date numbers to represent dates as the number of days since January 0, 0000 (a fictitious date). To convert the serial date number to a readable date, you can use the `datestr` function in MATLAB.

## Detector Control System
The slow control is controlling the flow-meters, the environment meter (bus 0 for the outside information, laboratory conditions, and bus 1 for that inside the DAQ, inside the box) and the HV through an I2C Hub that is connected to the minGO PC. This Hub allows the communication with the computer, back and forth. Actually the programs that retrieve data from these devices are called from the `crontab` periodically, so its name and path can be seen there. The operation is quite similar to that of the TRB: the devices drop a data file that is read and stored as a `.log` text file in `home/rpcuser/logs`. A `.log` for that day is updated each time it is loaded; when the day passed that file is moved to the `done` directory where all the previous ones are stored.

Every device has its own LookUp Table (LUT).

### The logs
Information about general variables involving temperature, pressure, humidity... obtained from the I2C hub. There is a `.log`, though, that does not come from the DCS but from the TRB: the Rate, whose information is configurated in a python script `~/gate/python/log_CTSrates_multiProcessing.py` instead of in a LookUp Table in the `~/gate/system/lookUpTables`. It is obtained thanks to `trbnetd`, a daemon.

## The LookUp Tables
They are stored in the `~/gate/system/lookUpTables`. It is a pending objective to write them in the same format: excel. They give information on how the programs that retrieve information store them, among other tasks.
