## Geometry of the telescope

- 4 parallel square RPC detectors (fig. 1):
  - Active area: 30x30 cm
  - Three 2 mm thick glass panes separated by 1 mm thick nylon monofilaments (fig. 2).
  - Two gaps of 1mm each filled with gas Freon (R134a).
  - Top and bottom glass panes covered with semiconducting paint on the inside.
  - High voltage applied between the paint layers (positive / negative).
  - 4 metal strips cover each RPC on top (fig. 3):
    - Asymmetrical widths.
    - 2 outputs: front and back.
- Discrimination electronics on one corner
- Trigger, DAQ, Control and Monitoring electronics in box between detectors 1 and 2.
- High voltage power supply box between detectors 2 and 3.
- Independent Freon gas tank, injected with calibrated holes + flow-monitors in the output (mutom like) + common bubbler.

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

General diagram: see fig. 5.

(MB: motherboard; DB: daighterboard; FEE: front-end electronics)

- Eight DABC discrimination DB (fig. 4) + control MB:
  - 4 input channels
  - Input: analog signal from the detector strips (MMCX connectors).
  - Output: square signal. Length proportional to charge deposited (32 pin connector).
  - Developed for the HADES detector (GSI).
- TRB3sc board:
  - Trigger selection and signal digitization.
  - 32 TDCs
  - Inputs: square signals from the DABC boards (2x 16 pin connectors).
  - Outputs: digital timestamp and length of each square signal (USB).
- ODroid Single Board Computer (SBC): General control and LAN communication.
- Solid State Drive (SSD): Data storage.
- High Voltage power supply:
  - Common for all detectors.
  - Software controlled.
  - Positive and negative voltages.
  - I2C protocol.
- Enviroment sensors:
  - One inside the electronics box, one outside.
  - Temperature, atmospheric pressure, humidity.
  - I2C protocol.
- Flow meters:
  - Gas flow monitoring.
  - I2C protocol.
- Low voltage power supply for the electronics:
  - Input: 48 V
  - Outputs: 12 V, 30? V
- Watchdog: ensures the electronics are turned on continuously.

---

![image](https://github.com/cayesoneira/miniTRASGO/assets/93153458/95f912cf-b274-4cfb-8519-419436ef5dd8)

_Figure 4_

---

![image](https://github.com/cayesoneira/miniTRASGO/assets/21690353/86c4fdca-18d2-4233-8ca4-95511cd59bbe)

_Figure 5_

---
