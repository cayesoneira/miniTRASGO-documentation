## Data retrieval

Raw data is located at `/media/externalDisk/hlds/`

You can transfer any file from miniTRASGO to your local machine using `scp` from the local terminal, not the mingo one:

    scp <user>@<remote machine>:<remote file> <local directory>
  
  For example:

    scp rpcuser@192.168.3.216:gate/system/devices/RCP01/data/dcData/data/2023-07-13-EffMap.mat ~/


## About the units of the timeStamps
In MATLAB, the date format you provided, 739077.6528125, represents a serial date number. MATLAB uses serial date numbers to represent dates as the number of days since January 0, 0000 (a fictitious date). To convert the serial date number to a readable date, you can use the `datestr` function in MATLAB.
