## General considerations

- WHEN IN TRANSPORT REMOVE THE GAS PIPES IN ORDER TO GIVE IT A WAY OUT: changing preassure (e.g. Coimbra-Madrid) can change the shape of the RPCs if they are closed. Actually a spark chamber broke in the past because of this.

To connect to minitrasgo:

    Host mingo01
        HostName minitrasgo.fis.ucm.es
        User rpcuser


The miniTRASGO sends a daily report in pdf format with several figures of interest. It includes the logs from months (temperature, humidity, pressure, rate...) and also the trigger data from the **last day**, as it was set on July 18th, 2023: it sends a report at 8:30, but with the information from 23:30 to 00:00 of the following day.


> `crontab -e` opens a crontab window where you can schedule certain operations on the linux terminal. To translate to the date and hour format used by crontab just enter [Contrab guru](https://crontab.guru/).

Here you can find a [TRB book](http://jspc29.x-matter.uni-frankfurt.de/docu/trb3docu.pdf)
