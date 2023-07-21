## Data retrieval

Raw data is located at `/media/externalDisk/hlds/`

You can transfer any file from miniTRASGO to your local machine using `scp` from the local terminal, not the mingo one:

    scp <user>@<remote machine>:<remote file> <local directory>
  
  For example:

    scp rpcuser@192.168.3.216:gate/system/devices/RCP01/data/dcData/data/2023-07-13-EffMap.mat ~/


## About the units of the timeStamps
In MATLAB, the date format you provided, 739077.6528125, represents a serial date number. MATLAB uses serial date numbers to represent dates as the number of days since January 0, 0000 (a fictitious date). To convert the serial date number to a readable date, you can use the `datestr` function in MATLAB.


## Data stream

1. The **TRB**, TRB3 from now on, sends its information through ethernet packets that are *floating* to the network.
2. From the Odroid SBC, the software **DABC** (Data Acquisition Backbone Core, it comes from GSI) takes those packages and stores them in `/media/externalDisk/hlds/` as `.hld` files, written in binary. They contain all the TRB information, not only rates but times (trailing and leading).
3. `CopyFiles` copies the `.hld` (only if there is more than one), also it is executing continously, to the `~/gate/system/devices/TRB3/data/daqData/rawData/dat`. This `CopyFiles` has many features and it is modifyable.
4. The `unpacker` is one of the key programs of the minGO datastream. It takes the `.hld` from its location, creates a temporary folder and uncompresses it inside it. Then it processes it in a first step to be matlab readable into the directory `~/gate/system/devices/TRB3/data/daqData/rawData/mat`. This is a first matlab file that is not physics frindly, since it is written in the language the TRBs handle: epoch, coarse, fine times... **However, this can be interesting to study for some that are interested in a more raw analysis**. The unpacker, then and automatically, in a second step that applies LUTs (LookUp Tables), builds the `.mat` that contains the time and charge in a very readable format and stores them in `~/gate/system/devices/TRB3/data/daqData/varData`; a small subroutine turns this info into ascii that will be stores in `~/gate/system/devices/TRB3/data/daqData/asci`. The unpacking is finished. Note: the unpacker starts to work only if there are two or more `.hld` files, and it can be run in parallel in several unpackings: this program just communicates with itself to share the unpacking. Also it is worth mentioning that the unpacker uses in a certain part `daq_anal` to convert the `.hld` from binary to hexadecimal.
5. Now the automatic analysis begins: each 5 s the `ana.sh`, which is in `~/gate/software/ana`, is executed. It calculates for each plane and for the telescope as a whole a lot of parameters. As before, there have to be two or more files to be executed automatically. The `ana.sh` (which actually calls `ana.m`) applies the calibration procedure, the random displacement of the pixels, etc. Actually all the analysis is done in this part.
6. It gives as an output, stored in `~/gate/system/devices/mingo01/data/ana`, and respectively in one of these directories: TT1, TT2 and Vars (TT stands for *trigger type*, which can be 1: coincidence or 2: self-trigger), the results. The most important files to start studying physics are those in `Vars`, which are also classified in TT1 and TT2: some `.mat` that hace two parts: outputvarplane, which is information plane by plane, and outputvartelescope, which is information of the telescope as a whole (efficiencies, for example). When `ana.m` ends calculating all this, it copies and distributes it to the rest of the parts of the telescope.


### The data in data/ana/Vars/TT1

| Index | Name         | Type | Description                                          |
|-------|--------------|------|------------------------------------------------------|
| 01    | EBTime       |      | EB time                                              |
| 02    | rawEvents    | num  | Initial number of Events                             |
| 03    | Events       | num  | Final events after pedestal and left, right cuts    |
| 04    | runTime      | num  | Time of the hld in seconds                          |
| 05    | Xraw         | 1D   | X raw in strips                                      |
| 06    | Yraw         | 1D   | Y raw                                                |
| 07    | Q            | 1D   | Final charge                                         |
| 08    | Xmm          | 1D   | Final X (across the strip)                           |
| 09    | Ymm          | 1D   | Final Y (along the strip)                            |
| 10    | T            | 1D   | Final T                                              |
| 11    | Qmean        | num  | Mean of the Q                                        |
| 12    | QmeanNoST    | num  | Mean of the Q without Streamers                     |
| 13    | Qmedian      | num  | Median of the Q                                      |
| 14    | QmedianNoST  | num  | Median of the Q without Streamers                   |
| 15    | ST           | num  | % of Streamers                                       |
| 16    | XY           | 2D   | Hit map                                              |
| 17    | XY_Qmean     | 2D   | Q mean map                                           |
| 18    | XY_Qmedian   | 2D   | Q mean map                                           |
| 19    | XY_ST        | 2D   | Hits above streamer level                            |
| 20    | Qhist        | 2D   | Charge histogram                                     |


## Detector Control System
The slow control is controlling the flow-meters, the environment meter (bus 0 for the outside information, laboratory conditions, and bus 1 for that inside the DAQ, inside the box) and the HV through an I2C Hub that is connected to the minGO PC. This Hub allows the communication with the computer, back and forth. Actually the programs that retrieve data from these devices are called from the `crontab` periodically, so its name and path can be seen there. The operation is quite similar to that of the TRB: the devices drop a data file that is read and stored as a `.log` text file in `home/rpcuser/logs`. Every device has its own LookUp Table (LUT).

### The logs
(...)

There is a `.log`, though, that does not come from the DCS but from the TRB: the Rate, whose information is configurated in a LUT. It is obtained thanks to `trbnetd`, a daemon.


## The LookUp Tables
They are stored in the `~/gate/system/lookUpTables`. It is a pending objective to write them in the same format: excel. They give information on how the programs that retrieve information store them, among other tasks.


--------------------

en ..../bin/ para crear y enviar el pdf:
./createReport.sh
./sendReport.sh
