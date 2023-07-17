Converts binary data in the .hld files to into .mat files readable with Matlab or Octave, which contain:

- Ebtime : vector NEvents x 1 : Event builder time, global time with second precision.
- For RPC l={1,2,3,4} and strip side s={F,B}:
    - Ql_s : matrix NEvents x 4 : Charge (Length of the digital pulse (ns))
    - Tl_s : matrix NEvents x 4 : Timestamp (ns)
- TRBs : struct 1 x 1 : Deprecated
- triggerType : vector NEvents x 1 : Trigger type (1 = muon, 2 = self trigger)

The system automatically unpacks the data once per day and saves it to

    ~/gate/system/devices/mingo01/data/ana/TT1
