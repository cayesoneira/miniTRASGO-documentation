# General considerations
This page section includes the different steps in the operation of minGO. In first place, the configuration, where how to turn on all minGO devices is explained. In second place, the calibration. In third place, the actual measure, when taken into account the calibrating procedure, and how to retrieve data. In forth place, the monitoring, and how to ensure it is measuring properly.

Before all of that, a small explanation on how to connect to the device from an external computer.

## Connecting to miniTRASGO
There are two ways to connect to miniTRASGO: pure terminal connection or showing its Desktop in an external computer.

### SSH Connection

Connecting to the miniTRASGO PC is mandatory to execute some key operations such as starting the voltage, the DAQ (Data Adquisition System), etc. To do so, while in the same network, a ssh connection can be establisehd from the terminal. To connect to minitrasgo, using the VPN of the Universidad Complutense de Madrid, just add to the config file (or use in the `ssh`) the following information:

    Host mingo01
        HostName minitrasgo.fis.ucm.es
        User rpcuser
    
It will ask for a password, which is currently private (ask us) because it is the same for many devices at LIP Coimbra. Once we write it we will be inside the miniTRASGO computer. To leave the `ssh` connection just write `exit`.


### Desktop connection
To connect to the desktop of the miniTRASGO computer just write in your local terminal the following, where the IP has to be replaced by the direction the device has assigned. Then just write the password that it is the same for every mingo related stuff.

    vncviewer minitrasgo.fis.ucm.es:0
