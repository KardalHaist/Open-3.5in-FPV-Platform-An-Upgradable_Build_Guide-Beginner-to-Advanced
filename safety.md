# Safety

[← Back to README](README.md)

## LiPo batteries

- **Never charge unattended.** Charge on a non-flammable surface or in a LiPo-safe bag.
- **Charge at 4.20 V per cell** for a standard LiPo. 4.35 V is for LiHV packs only.
- **Charge at 1C or less.** For an 850 mAh pack, 1C is 0.85 A. I charge at 0.5 A.
- **Always connect the balance lead** when charging.
- **Store at about 3.8 V per cell** if you won't fly for several days.
- **Retire puffed (swollen) packs.** Don't charge or fly them.
- **Never use a Li-ion cell charger** (one made for 18650s) on a LiPo pack.
- If a pack gets hot, smells, or swells while charging, unplug it and move it outdoors onto concrete or sand.

## First power-up and bench work

- **Props off** for all bench testing, motor tests, and Betaflight work.
- **Smoke stopper** for the first power-up and after any re-soldering.
- **Continuity check** battery + to − before the first power-up. No beep means no short.
- **VTX antenna on before power, every time.** [Here's what happens otherwise](troubleshooting/vtx-amplifier-failure.md).
- Keep a fan on the VTX and ESC during long bench sessions.
- Don't unplug a powered VTX or disconnect wires while powered.
- Measure current with the meter **in series**, never with the probes across a supply.

## Flying

- **Test failsafe** before the first flight. Turning off the radio must stop the motors.
- Fly in an open area away from people, roads, and airports.
- **Video power:** 25 mW unless you hold an amateur radio license. That's the limit for license-free 5.8 GHz video in the US.
- **US rules:** recreational pilots need the TRUST certificate. Recreational drones of 250 g or more must be registered. This build weighs 238.36 g with its battery, so it is just under the line; re-weigh after adding parts.
- Follow local airspace rules. B4UFLY and similar apps show restricted areas.
