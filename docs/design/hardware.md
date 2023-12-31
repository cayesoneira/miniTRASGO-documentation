## Frame of reference convention and nomenclature

The x axis follows the direction of the strip, the z is pointing down (to reflect the most likely direction of the incoming cosmic ray) and y is dextro-rotatory respect to the other two. Later we will associate this frame of reference with the cardinal points, making easy to transform into any other frame of reference, such as equatorial or galactical, more useful for physical purposes.

![mingo](https://github.com/cayesoneira/miniTRASGO-documentation/assets/21690353/f9801f0b-73a7-4bb7-98f7-d1948eaadc27)

## Geometry of the telescope

- 4 parallel square RPC detectors (fig. 1):
    - Active area: approximately 30x30 cm (we have to calculate it effectively).
    - Three 2 mm thick glass panes separated by 1 mm thick nylon monofilaments (fig. 2).
    - Two gaps of 1 mm each filled with R134a gas.
    - Top and bottom glass panes covered with semiconducting paint on the inside.
    - High voltage applied between the paint layers (positive / negative).
    - 4 metal strips cover each RPC on top (fig. 3):
        - Asymmetrical widths.
        - 2 outputs: front and back.
- Front-end electronics (FEE) on one corner.
- Trigger, DAQ, Control and Monitoring electronics in box between detectors 1 and 2.
- High voltage power supply between detectors 2 and 3.
- Independent R134a gas tank, injected with calibrated holes and a flow-monitor in the output for each RPC (mutom like).

![image](https://github.com/cayesoneira/miniTRASGO/assets/21690353/0b2716cf-5745-44cd-9137-250d9f6d70d8)

_Figure 1_

---

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/3c83d2de-22cb-4d7d-b89d-8f52a7710ed9)

_Figure 2_

---

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/8e34e594-e490-4610-9654-66b07d65f65d)

_Figure 3_

---

## Electronics
![General diagram](https://github.com/cayesoneira/miniTRASGO/assets/21690353/86c4fdca-18d2-4233-8ca4-95511cd59bbe)

_Figure 4. General diagram._

---

- Front-end electronics (FEE): Developed for the HADES detector (GSI).
    - Daughterboards (DB): the daughterboard includes in a Hidronav piece, with all the components on one side, the main electronics to turn the signal generated by the RPC into a LVDS (Low Voltage Differential signal). See the full scheme in fig. 5. The discriminator level is a constant value that can be modified. The working value is -40 mV.
        - 4 input channels per DB (the order of the channels is BACD).
        - Input: analog signal from the detector strips (MMCX connectors), usually independent of the energy of the incoming particle.
    - Motherboard (MB): the motherboard gets power from a special power source (the one that we only have one more piece of and Alberto Blanco handmaded one that is going to test) and gives it to the DBs and also communicates the DB LVDS to the TRB. That power source needs to have 20 W, but doubling it to 40 W is recommended to cover some errors that could kill the chips in the circuit in case the current stops flowing and the condensers still accumulate charge.
        - Output: square LVDS. Length proportional to charge deposited, time indicating the instant of the event. The signals come from the FEE to the TRB in a 32 pin connector (4 strips per layer, Front and Back per strip: 4*4*2 = 32).
- TRB3sc (Time-of-Flight Reconstruction Board). [Official documentation](http://jspc29.x-matter.uni-frankfurt.de/docu/trb3docu.pdf). It has a FPGA (Field-Programmable Gate Array.). TRB only sends the information when its buffer is full. When the rate is very high this is not even noticeable, but when it is very low it could be that the buffer could take some seconds to be full: this will be relevant when setting the times, since the hlds will have times that are not very reliable. This can be seen in the DABC execution window (in the tmux), where the rate will be 0 for seconds, then suddenly get a slightly higer rate.
    - Coming directly from the HADES experiment.
    - Trigger selection and signal digitization.
    - 32 Time-to-Digital Converters (TDC).
    - Inputs: square LVDS (low voltage differential signal) from the DB (2x 16 pin connectors).
    - Outputs: digital timestamp and length of each square signal (USB).
- USB-ethernet board: allows the direct communication with the TRB even though the overall system is not connected to the internet. For example in the FEE test setup we do not have that web board so we need a router to connect TRB and PC aside to the internet and then one to another.
- ODroid Single Board Computer (SBC): general control and LAN communication.
- Solid State Drive (SSD): data storage.
- High Voltage power supply:
    - Common for all detectors, connected in parallel.
    - Software controlled.
    - Positive and negative voltages.
    - I2C protocol.
    - It has a low power consumption since it has only the basic control electronics and it gets the voltage from a fundamentally different way than usual sources (ask Alberto Blanco for more info).
- Enviroment sensors:
    - One inside the electronics box, one outside.
    - Temperature, atmospheric pressure, humidity.
    - I2C protocol.
- Flow meters.
    - Gas flow monitoring.
    - I2C protocol.
- Low voltage power supply for the electronics:
    - Input: 48 V
    - Outputs: 12 V, 30??? V
- Watchdog: ensures the electronics are turned on continuously.

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/95f912cf-b274-4cfb-8519-419436ef5dd8)

_Figure 5_

---

## Non-electronical components: gas flow
The gas flow is monitored only by the flow at the end, but not at the beginning.

**The camping blue valve, when "closed", still lets some gas flow.** Also take into account that once closed the gas still has 6 bars of pressure, so it will take around 15-20 min to fully stop flowing. Then the detector will just work with the gas it has, but with no pressure, so it will start to leak and loose the purity of the R134A.

When transporting the equipment, it is essential to remove the gas pipes to allow for a safe release of pressure, especially during changes in pressure due to transportation (e.g., Coimbra-Madrid route). Failure to do so could potentially alter the shape of the RPCs (Resistive Plate Chambers) if they remain closed under varying pressure conditions. In the past, a spark chamber was damaged because this precaution was not taken.
