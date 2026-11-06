# Measurements and Analysis

[← Back to README](../README.md)

Measured data from the build. Raw numbers are in the `.csv` files in this folder so they can be plotted or reused.

## 1. Cell balance during charging

From the M4AC charger screen ([photo](../media/photos/17-charger-balance-screen.jpg)), charging at 0.5 A:

| Cell | Voltage (V) |
|---|---|
| 1 | 3.861 |
| 2 | 3.864 |
| 3 | 3.854 |
| 4 | 3.865 |
| **Spread (max − min)** | **0.011 V (11 mV)** |
| **Mean** | **3.861 V** |

The cells match within 11 mV, so the pack is healthy. Pack voltage was 15.4 V at 58% charge. Data: [cell-balance.csv](cell-balance.csv)

## 2. VTX current draw versus power setting

Measured with the flight controller's onboard current sensor (scale 250, offset −500) at about 16.3 V. The full interpretation is in the [case study](../troubleshooting/vtx-amplifier-failure.md).

| State | Current (A) | Power (W) |
|---|---|---|
| VTX unplugged | 0.10 | 1.6 |
| 25 mW | 0.18 | 2.9 |
| 200 mW | 0.14 | 2.3 |
| 1 W | 0.18 | 2.9 |
| 1 W (retest) | 0.14 | 2.3 |

**Takeaway:** a working VTX draws a few hundred mA more at high power. This one didn't change at all, which showed the amplifier was dead. Data: [vtx-current.csv](vtx-current.csv)

**Limitation:** the ESC current sensor reads up to about 63 A and is noisy below 1 A. An inline wattmeter would give a clean measurement.

## Next measurements I want to take

- **Current sensor calibration:** compare the Betaflight current reading against an inline wattmeter at several throttle levels, then correct the scale and offset.
- **Predicted versus measured flight time** from the battery capacity and average current.
- **Blackbox gyro spectrum** before and after the RPM filter (see [future improvements](../future-improvements.md)).
