# Measuring

Data Acquisition Backbone Core (DABC) is a software framework designed for distributed data acquisition. It serves as a backbone for managing and processing data from various experiments. One of its key features is its plug-in mechanisms, allowing it to be easily extended to support different data formats and experiments. In the context of test set-ups using the trb3 frontend readout, specific plug-ins have been developed to receive and merge HADES trbnet data packets through UDP connections. This enables efficient handling and combination of data from different sources within the HADES experiment.

Also important: mobile phones can actually interfere with miniTRASGO.




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

The `powercycle` (or something like that) is used to reboot: it is like going to the lab and turning off and then on the system (I just do not know if).

## DAQ Control

In the 1.DAQControl window, we go to ~/trbsoft/userscripts/trb$ and execute `./startDAQ`.

This starts the data adquisition system, but does not save any content into files.

## Threshold information
On the `Thresholds` window there is a script called `./setThresholds.sh` which puts the threshold to -40 mV; the `./startDAQ` includes this line, but we have to be sure that nothing changes the thresholds automatically, since we are usually executing `./startRun.sh` and not `./startDAQ`, which is started once per system reboot.

To check the value of the thresholds, just tyoe: ?????

## Trigger Control

To choose the trigger we want the system to consider we can go to the Central Trigger System, which is a web-based control center that can be accessed through `192.168.3.216:1234`.

## Run control

In the 2.DABC window, we do `cd ~/trbsoft/userscripts/trb` and execute `./startRun.sh`.

Now the data is collected into binary `.hld` files, saved at `/media/externalDisk/hlds/`.

Press `CTRL + C` to stop the run.

## Data usage and control
To check the number of events of a `.hld` file the line `daq_anal <.hld file>` can be executed; then it can just be stopped. This is mostly useful to know if a file is empty, because in that case the .hlds are ignored.

Also check that the .hlds have enough events, because in other case some .mats can be loaded, such as Rate.mat, but for example Eff.mat will not.
