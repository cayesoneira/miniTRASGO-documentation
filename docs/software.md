## Operating the miniTRASGO:
Connecting to the miniTRASGO PC is mandatory to execute some key operations such as starting the voltage, the DAQ (Data Adquisition System), etc. To do so, while in the same network, a ssh connection can be establisehd from the terminal:
    
    ssh -X rpcuser@192.168.3.216
It will ask for a password, which is currently private (ask us) because it is the same for many devices at LIP Coimbra. Once we write it we will be inside the miniTRASGO computer. To leave the ssh connection just write `exit`.

The TRASGO team decided to build a `tmux` multiplexer to develop a series of operations in a multiple, permanently open shell. Everything could be done through the main terminal session, but one at a time, and our computer has to be connected. This way we separate visually diffetent executions, as well as we can execute in the background the measuring operations. Any activity on the multiplexer will be shown in real time to every user conncected to a `tmux` session. We can access it through the terminal inside the miniTRASGO computer. First we see the `tmux` sessions avaliable:

    tmux ls
It will give as output:
- `0: 7 windows (created Tue Jul 11 15:06:22 2023) (attached)`: utilized for measurement operations.
- `1: 13 windows (created Tue Jul 11 15:06:22 2023) (attached)`: utilized for data treatment.
- `webserver: 1 windows (created Tue Jul 11 15:12:07 2023)`: gives info on the trigger activity; not interactive.

So the line to enter any session is:

    tmux attach -t <session name: 0, 1 or webserver>
  
To leave the `tmux` session just press `CTRL + B, D`. Let's see what is inside these sessions and how to operate with it.

---

## Session 0:
- 0:Main01
- 1:DAQControl
- 2:DABC (why this name???)
- 3:Thresholds
- 4:HLDs
- 5:Control
- 6:Var

## Session 1:
- 0:Main01
- 1:Dcs
- 2:CopyFiles
- 3:Unpacker01
- 4:Unpacker02
- 5:Unpacker03
- 6:Ana
- 7:Report
- 8:Control
- 9:LogCritical
- 10:LogNet
- 11:LogSystem
- 12:Var

---

## Measuring 101:
In `tmux attach -t 0`:

### High Voltage control
In the ??? window, `cd ~/bin/HV` and execute the executable `hv` with the following arguments:

- `-b <bus>` : Bus number
- `-I <Ilim>` : Current limiter (μA)
- `-V <Vset>`: High voltage value (kV)
- `-on` : Turn HV ON
- `-off` : Turn HV OFF

Examples:

    ./hv -b 0 -I 1 -V 5.5 -on

    ./hv -b 0 -off

### Starting the DAQ

In the 1.DAQControl window, we go to ~/trbsoft/userscripts/trb$ and execute `./startDAQ`

### Startig a Run

In the 2.DABC window, we go to ~/trbsoft/userscripts/trb$ and execute `./startRun.sh`  

---

## The content of the computer:
/
- bin  boot  dev  etc  mnt  opt  proc  resize.log  root  run  sbin  snap  srv  sys  tmp  usr  var lib  lost+found
- 
- /media
    - /externalDisk
        - /hlds: here the trigger data files are stored.
- /home: everything interesting is inside this directory but the trigger data files.
    - /rpcuser
        - /bin
            - /HV
                - hv: used to ramp up the High Voltage.
            - /flowmeter
                - GetData
                - GetFlow
        - /gate ???
        - /hlds (empty???)
        - /linux
        - /logs: includes all the info taken by the high voltage and *climate* sensors. **What is that rates_ file??**. All the current data is here.
            -/done: all the full log files will be put here.
        - /mnt: EMPTY
        - /perl5: ???
        - /pythonscripts: only has one .py and I do not think it is very important.
        - /trbsoft: Trigger and Readout Board software
     
`CTRL + C` to stop the DAQ process.
