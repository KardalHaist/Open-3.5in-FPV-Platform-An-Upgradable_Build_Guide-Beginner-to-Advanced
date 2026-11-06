# Bill of Materials (BOM)

A **bill of materials** is the complete list of parts needed to build something. Prices are what I saw at checkout in October 2026 and will change. A dash (—) means I didn't record it.

## Parts on the quad

| # | Part | What it does (plain language) | Key spec | Price (USD) | Source |
|---|---|---|---|---|---|
| 1 | FlyFishRC Volador VX3.5 O4 frame | The carbon fiber skeleton everything bolts to | 160 mm wheelbase, 20x20 stack and VTX mounts (M2) | 42.27 | AliExpress |
| 2 | SpeedyBee F405 Mini + BLS 35A Mini V2 stack | Flight controller (the "brain") stacked on a 4-in-1 ESC (drives the four motors) | F405 processor, 35 A per motor, 3–6S input | 85.51 | AliExpress |
| 3 | T-Hobby (T-Motor) Pacer P1604 3800KV ×4 | Brushless motors | 1.5 mm shaft, 9x9 mm M2 mount, 4S rated | 63.90 (set of 4) | MEPS King |
| 4 | HQProp T3.5x2.5x3, 1.5 mm | Propellers | 3.5" diameter, 2.5" pitch, 3 blades | 7.30 (4 pairs) | AliExpress |
| 5 | Caddx Ratel 2 V2, 2.1 mm | Analog FPV camera | 1200TVL, 5–40 V input, about 8 ms latency | — | AliExpress |
| 6 | AKK FX3-ultimate | Video transmitter (sends the camera feed to the goggles) | 20x20 mount, 7–24 V input, 25/200/400/600 mW, SmartAudio | 22.99 | Amazon |
| 7 | SpeedyBee Nano 2.4 GHz ELRS receiver (TCXO) | Receives stick commands from the radio | 5 V input, CRSF protocol, IPEX antenna | — | AliExpress |
| 8 | Tattu R-Line V5 850 mAh 4S 150C | Battery | 14.8 V nominal, 16.8 V full, XT30 | 22.99 per pack | MEPS King |
| 9 | 35 V 470 µF low-ESR capacitor | Smooths voltage spikes on the battery input | Included with the stack | Included | — |
| 10 | 5.8 GHz VTX antenna | Radiates the video signal | Connector must match the VTX pigtail | — | — |

## Support equipment

| Part | What it does | Price (USD) | Source |
|---|---|---|---|
| ToolkitRC M4AC charger | Balance-charges the LiPo | 28.49 | MEPS King |
| iFlight XT30/XT60 smoke stopper | Current-limited test plug for first power-up | — | AliExpress |
| XT30 and XT60H connectors | Battery and charge-lead connectors | — | AliExpress |
| 5 V USB fan | Cools the VTX and ESCs on the bench | — | AliExpress |
| RadioMaster T8L (M2) | ELRS radio transmitter | — | Already owned |
| VR009 goggles | Analog 5.8 GHz goggles | — | Already owned |

## Retired part

| Part | Why it's listed |
|---|---|
| Cyclone 5.8G 1 W VTX (7–26 V, 25–1000 mW) | Original VTX. Its amplifier failed after an early power-up without an antenna. See the [case study](../troubleshooting/vtx-amplifier-failure.md). |

---

## Weight

| Measurement | Weight |
|---|---|
| **All-up weight (AUW), battery included** | **238.36 g** |

The **all-up weight** is everything that flies, battery included. It decides flight time and handling.

**Why 250 g matters:** in the US, a drone flown purely for recreation under 250 g doesn't have to be registered with the FAA. You still need the TRUST certificate and must follow the recreational rules. At 238.36 g this build is under that line with about 12 g to spare, so adding a GPS, a bigger battery, or a heavier camera could push it over. Flying commercially under Part 107 requires registration at any weight.

---|---|
| Frame with hardware | |
| Stack (FC + ESC) | |
| Motors ×4 | |
| Props ×4 | |
| Camera | |
| VTX + antenna | |
| Receiver + antenna | |
| Wiring, tape, capacitor | |
| **Dry weight (no battery)** | |
| Battery | |
| **All-up weight** | |

---

## Why these parts

**4S battery with 3800KV motors.** **KV** is a motor's unloaded speed per volt: 3800 × 14.8 V ≈ 56,000 RPM with no prop. Running a higher voltage (4S) means less current for the same power, so wires and ESCs run cooler. The P1604 3800KV is the manufacturer's 4S option for 3.5" props (they sell a lower-KV version for 6S).

**35 A ESC.** Sellers list the P1604's peak current at about 16.8 A per motor, so a 35 A ESC has roughly 2x headroom. Headroom matters because ESCs fail from heat, and heat rises with current.

**20x20 stack.** It matches the frame's 20x20 mounting pattern, and the SpeedyBee F405 Mini has Bluetooth for configuring from a phone.

**Analog video.** Analog is cheap, light, and low-latency (the Ratel 2 is rated around 8 ms). The trade-off is image quality. See [future improvements](../future-improvements.md) for digital options.

**850 mAh 4S.** A bigger pack holds more energy but adds weight the motors must carry, so flight time doesn't scale linearly with capacity. 850 mAh is a common middle ground for 3.5" quads.

**ELRS 2.4 GHz receiver.** It has to match the radio's band (the T8L is 2.4 GHz ELRS only).

**AKK FX3-ultimate VTX.** It was chosen as the replacement because it:
- bolts onto the frame's 20x20 VTX mount,
- accepts 7–24 V (so it runs from the flight controller's 9 V pad),
- has a 25 mW setting (the legal limit for US pilots without an amateur radio license),
- supports SmartAudio, so Betaflight can change channel and power without touching the VTX.

Machine-readable version: [bom.csv](bom.csv)
