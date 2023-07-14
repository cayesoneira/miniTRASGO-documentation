## Data retrieval

Raw data is located at `/media/externalDisk/hlds/`

You can transfer any file from miniTRASGO to your local machine using `scp`:

    scp <user>@<remote machine>:<remote file> <local directory>
  
  For example:

    scp rpcuser@192.168.3.216:gate/system/devices/RCP01/data/dcData/data/2023-07-13-EffMap.mat ~/

## Unpacker

Converts binary data in the .hld files to into .mat files readable with Matlab or Octave, which contain:

- Ebtime : vector NEvents x 1 : Event builder time, global time with second precision.
- For RPC l={1,2,3,4} and strip side s={F,B}:
    - Ql_s : matrix NEvents x 4 : Charge
    - Tl_s : matrix NEvents x 4 : Timestamp
- TRBs : struct 1 x 1 : Deprecated
- triggerType : vector NEvents x 1 : Trigger type (1 = muon, 2 = self trigger)

The system automatically unpacks the data once per day and saves it to

    ~/gate/system/devices/mingo01/data/ana/TT1

## Pre-Analysis

The system also creates and calculates a series of quatities once per day and saves them to
  
    ~/gate/system/devices/mingo01/data/dcData/data
  
and
  
    ~/gate/system/devices/RPC01/data/dcData/data


