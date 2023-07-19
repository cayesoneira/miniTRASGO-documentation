## SSH Connection:
Connecting to the miniTRASGO PC is mandatory to execute some key operations such as starting the voltage, the DAQ (Data Adquisition System), etc. To do so, while in the same network, a ssh connection can be establisehd from the terminal:
    
    ssh -X rpcuser@192.168.3.216
    
It will ask for a password, which is currently private (ask us) because it is the same for many devices at LIP Coimbra. Once we write it we will be inside the miniTRASGO computer. To leave the ssh connection just write `exit`.

While connected, we can enter one of the terminal sessions currently running with

    tmux attach -t 0

> To erase a `tmux` window just type `CTRL+B, ???`, to create one just press `CTRL+B, C`. You can rename them with `tmux rename-window <new name>`.

## Desktop connection
To connect to the desktop of the miniTRASGO computer just write in your local terminal the following: `vncviewer 192.168.3.216:0`; the IP has to be replaced by the one the device has assigned. Then just write the password that it is the same for every mingo related stuff.

## High Voltage control
At any window, do `cd ~/bin/HV` and execute `./hv` with the following arguments:

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

## DAQ Control

In the 1.DAQControl window, we go to ~/trbsoft/userscripts/trb$ and execute `./startDAQ`.

This starts the data adquisition system, but does not save any content into files.

## Threshold information
On the `Thresholds` window there is a script called `./setThresholds.sh` which puts the threshold to -40 mV; the `./startDAQ` includes this line, but we have to be sure that nothing changes the thresholds automatically, since we are usually executing `./startRun.sh` and not `./startDAQ`, which is started once per system reboot.

## Trigger Control

To choose the trigger we want the system to consider we can go to the Central Trigger System, which is a web-based control center that can be accessed through `192.168.3.216:1234`.

## Run control

In the 2.DABC window, we do `cd ~/trbsoft/userscripts/trb` and execute `./startRun.sh`.

Now the data is collected into binary `.hld` files, saved at `/media/externalDisk/hlds/`.

Press `CTRL + C` to stop the run.
