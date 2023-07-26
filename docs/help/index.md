## The strips appear larger than they are
When seeing the XY diagram it might be that some strips appear larger. We checked the correlation in times and charges between front (F) and back (B) to see that there is no perfect correlation, but a slope slightly different to 45 degrees and some regular gaps in the cloud of points.

Alberto noticed it had to be with the calibration values of the TDC, solving not only the mingo problem but the RPC issue that was sometimes observed at HADES. Those values where seen to be *out of the usual* some time ago, but never played a mayor role until we changed the TRB in July 13th, 2023: both TRBs had this issue, but with the new one this was the only, isolated problem, so we could study it in detail.

It could also be that, since the signals in the strips travel theoretically through the edges of the strip, and not in stright lines, that a very wide strip could have a non-negligble *edge effect* that would make the signals to arrive later: it would add to the times a value that would strongly depend on the width of the strip, and therefore the strips would look larger.

## The correlation pattern has a cloud of negative values
This was caused because the **TRB/TDC???? (I do not know what is more precise)** was calculating the times properly but, for some reason, was confusing the leading with trailing edge of the digital signal. The error was corrected just by changing a posteriori one value with the other. We changed the TRB in July 13th, 2023 to make sure the problem was with this component, and in fact it was. We kept the new TRB for simplicity and we are trying to contact the manufacturer company to discuss the issue.

## The correlation pattern has a lot of values over the axes
This could be explained in several ways:
- In many cases only one of both sides (front or back) of the strip is measuring. We should test the electronics with the polimeter to checck if it is working.
- The channels are mixed up between the front and back of different strips, which breaks the correlation pattern. Just reconnect the coaxial cables (**see the technical name of that cable**) that go from the strip to the daughterboard (DB) in the correct channels.

## The `startRun.sh` keeps executing in the background
You will have to list all the processes, in particular those that use the `dabc_exe` with `ps -ef | grep dabc` (if you `cat startRun.sh` it will say `dabc_exe EventBuilder_TRB399.xml`), and then

    kill -9 <id_1> <id_2> <...>

## The system is not measuring
That is most probably an error on the `./startDAQ` execution. Just run it again.

## The TRB has been changed, so the PC does not find it
If the TRB changes an IP has to be given to it from mingo PC, which is a process *that a computer engineer would do in 30 ms*. We will not take notes on how to do it since it only has to be done in very special ocasions.
