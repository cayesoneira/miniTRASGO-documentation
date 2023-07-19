## Terminal sessions

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

|   Session 0  |   Session 1   |
|:------------:|:-------------:|
|   0:Main01   |    0:Main01   |
| 1:DAQControl |     1:Dcs     |
| 2:DABC       | 2:CopyFiles   |
| 3:Thresholds | 3:Unpacker01  |
| 4:HLDs       | 4:Unpacker02  |
| 5:Control    | 5:Unpacker03  |
| 6:Var        | 6:Ana         |
|              | 7:Report      |
|              | 8:Control     |
|              | 9:LogCritical |
|              | 10:LogNet     |
|              | 11:LogSystem  |
|              | 12:Var        |

---

## Folder structure

- bin  boot  dev  etc  mnt  opt  proc  resize.log  root  run  sbin  snap  srv  sys  tmp  usr  var lib  lost+found
- /media
    - /externalDisk
        - /hlds: here the trigger data files are stored.
- /home: everything interesting is inside this directory except the trigger data files.
    - /rpcuser
        - /bin
            - /HV
                - hv: used to control the High Voltage.
            - /flowmeter
                - GetData
                - GetFlow
        - /gate
            - /system
                - /devices: includes all the data coming from every component of the mingo system.
        - /hlds (empty???)
        - /linux
        - /logs: includes all the info taken by the high voltage and *climate* sensors. **What is that rates_ file??**. All the current data is here.
            -/done: all the full log files will be put here. **Is this info then stores in the /gate/system/devices???**.
        - /mnt: EMPTY
        - /perl5: ???
        - /pythonscripts: only has one .py and I do not think it is very important.
        - /trbsoft: Trigger and Readout Board software
     
## Look Up Tables (LUTs)
Every device involved in the system has a LUT designated in order to explain how to read the files and also some alarm configured. For example the LookUpTableTRB.m has an alarm system which is the following:

    {<0 or 1 if it is on/off>, <minimum value to triger the alarm>, <how many times has to occur to trigger the alarm>}
    {<0 or 1 if it is on/off>, <maximum value to triger the alarm>, <how many times has to occur to trigger the alarm>}
