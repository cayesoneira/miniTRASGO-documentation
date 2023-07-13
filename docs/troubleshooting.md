## The strips appear larger than they are
When seeing the XY diagram it might be that some strips appear larger. We checked the correlation in times and charges between front (F) and back (B) to see that there is no perfecet correlation, but a slope slightly different to 45 degrees and some regular gaps in the cloud of points.

Alberto noticed it had to be with the calibration values of the TDC, solving not only the mingo problem but the RPC issue that was sometimes observed at HADES. Those values where seen to be *out of the usual* some time ago, but never played a mayor role until we changed the TRB in July 13th, 2023: both TRBs had this issue, but with the new one this was the only, isolated problem, so we could study it in detail.


## The correlation pattern has a lot of values over the axes
This was caused because the **TRB/TDC???? (I do not know what is more precise)** was calculating the times properly but, for some reason, was confusing the leading with trailing edge of the digital signal. The error was corrected just by changing a posteriori one value with the other. We changed the TRB in July 13th, 2023 to make sure the problem was with this component, and in fact it was. We kept the new TRB for simplicity and we are trying to contact the manufacturer company to discuss the issue. 
