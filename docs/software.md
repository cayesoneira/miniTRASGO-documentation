## Operating the miniTRASGO:
Connecting to the miniTRASGO PC is mandatory to execute some key operations such as starting the voltage, the DAQ (Data Adquisition System), etc. To do so, while in the same network, a ssh connection can be establisehd from the terminal:
    
    ssh -X rpcuser@192.168.3.216
It will ask for a password, which is currently private (ask us) because it is the same for many devices at LIP Coimbra. Once we write it we will be inside the miniTRASGO computer. To leave the ssh connection just write `exit`.

The TRASGO team decided to build a `tmux` multiplexer to develop a series of operations in a multiple, permanently open shell. Any activity on it will be shown in real time to every user conncected to a `tmux` session. We can access it through the terminal inside the miniTRASGO computer. First we see the `tmux` sessions avaliable:

    tmux ls
It will give as output:
- `0: 7 windows (created Tue Jul 11 15:06:22 2023) (attached)` --> utilized for measurement operations.
- `1: 13 windows (created Tue Jul 11 15:06:22 2023) (attached)` -> utilized for data treatment.
- `webserver: 1 windows (created Tue Jul 11 15:12:07 2023)` -> gives info on the trigger activity; not interactive.

So the line to enter any session is:

    tmux attach -t <session name: 0, 1 or webserver>
  
To leave the `tmux` session just press `CTRL + B, D`.

## Session 0:

## Session 1:



`CTRL + C` to stop the DAQ process.
