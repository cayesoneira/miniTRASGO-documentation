# Preparing the minGO

The `crontab` is configured to automatically execute the needed software when rebooting the system. It is possible, though, that some execution needs to be stopped and then relaunched, so it is interesting to know what are the especific required programs to work with minGO.

## The DCS (Data Control System)
The connection through the I2C protocol from the mingo PC to the hub containing the environment, HV and gas flow sensors is established thanks to the script with path: 

    media/externalDisk/gate/bin/dcs_om.sh

## Starting the DAQ (Data Acquisition)
In the directory `home/rpcuser/userscripts/trb399sc/` there are some essential scripts for the mingo operation. The first step is to start the data acquisition. The program to get the data from the TRB is found in `./startup_TRB399.sh`, which has a shorcut, `./startDAQ`. This starts the data adquisition system, but does not save any content into files. Once this is started we can set the triggers we want in the Central Trigger System (CTS), the subpage of the web-based DAQ control found in

    minitrasgo.fis.ucm.es:1234/cts/cts.htm
There we can select the standard trigger we want to use, that will be saved as Trigger Type (TT) 1. The other triggers, that can be automatically selected from a script, are in the directory `home/rpcuser/userscripts/trb399sc/trigger`: those are called when automatically performing through the `crontab` the self trigger (which is considering a hit in any layer a trigger and it is stored with the category TT 2).

## High Voltage control
At any window, execute `home/rpcuser/bin/HV/hv` with the following arguments:

- `-b <bus>` : Bus number
- `-I <Ilim>` : Current limiter (μA)
- `-V <Vset>`: High voltage value (kV)
- `-on` : Turn HV ON
- `-off` : Turn HV OFF

Examples:

    ./hv -b 0 -I 1 -V 5.5 -on 
<!-- tsk -->
    ./hv -b 0 -off

To see the information on HV and intensity in real time just type:

    watch -n 1 ./hv -b 0
