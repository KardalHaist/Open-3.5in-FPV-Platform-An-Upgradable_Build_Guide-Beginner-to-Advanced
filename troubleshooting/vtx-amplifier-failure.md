# Case Study: A VTX Amplifier That Failed Silently

[← Back to troubleshooting](README.md) · [Back to README](../README.md)

**Summary:** Betaflight said the video transmitter was working, but the goggles showed only static. Measuring the current draw at different power settings showed the VTX's output amplifier wasn't producing any power. The most likely cause was that I had powered the VTX earlier **without an antenna attached**. A replacement VTX fixed the problem.

---

## Symptom

- The goggles showed pure **snow** (static) on every channel, even with the goggles held a few inches from the quad.
- Auto-search on the goggles found nothing.
- Betaflight's VTX tab showed the VTX as **ready: true**, on Band A channel 1 at 25 mW.
- The VTX's LED showed the band, channel, and power I set.

## Step 1: Rule out the goggles

I powered up my tiny whoop (a known-good analog quad). The goggles locked onto it immediately. **Goggles and their antennas: fine.**

> **Side finding:** the whoop's VTX said "Raceband 3," but the goggles labeled the channel "E6." Cheap goggles often use their own channel naming. Always match by **frequency (MHz)**, not by label.

## Step 2: Why "ready: true" didn't mean "transmitting"

A VTX has two separate parts:

| Part | What it does | What "ready: true" proves |
|---|---|---|
| **Controller** (microcontroller) | Talks to Betaflight over SmartAudio, drives the LEDs | ✅ Powered and communicating |
| **Power amplifier (PA)** | Boosts the radio signal to 25–1000 mW and sends it to the antenna | ❌ Nothing |

"Ready" only confirms the controller is alive. The amplifier can be dead while the controller still works perfectly, which is exactly what happened here.

## Step 3: Check the power supply (multimeter)

| Test | Mode | Probes | Result |
|---|---|---|---|
| Short circuit | Continuity, battery unplugged | VTX power pad to ground | No beep ✅ |
| Supply voltage | DC volts, battery plugged in | VTX power pad to ground | Correct voltage ✅ |

So the VTX was getting the right power, and nothing was shorted.

> **Mistake to avoid:** at one point I measured with the multimeter in **current (mA) mode with the probes across the power pads**. That shorts the supply through the meter and can blow the meter's internal fuse. To measure current, the meter must be **in series** (inserted into the wire), never across a supply. Afterward, I checked the fuse by switching to ohms and touching the probes together; near 0 Ω means the fuse is OK.

## Step 4: Measure the current draw (the key test)

A working amplifier draws noticeably more current at higher output power, because it has to put more energy into the radio signal. I used the flight controller's own current sensor (Betaflight → **Power & Battery** tab) to compare the total draw with the VTX in different states.

| VTX state | Total current | Total power (at about 16.3 V) |
|---|---|---|
| Unplugged | 0.10 A | 1.6 W |
| Plugged in, 25 mW | 0.18 A | 2.9 W |
| 200 mW | 0.14 A | 2.3 W |
| 1 W | 0.18 A (0.14 A on retest) | 2.9 W |

Screenshots: [unplugged](../media/screenshots/vtx-current-unplugged.png) · [25 mW](../media/screenshots/vtx-current-25mw-plugged-in.png) · [200 mW](../media/screenshots/vtx-current-200mw.png) · [1 W](../media/screenshots/vtx-current-1w.png) · [1 W retest](../media/screenshots/vtx-current-1w-retest.png)

**How to read this:**
- Plugging in the VTX added about **80 mA**. That's the controller and support circuits waking up.
- Going from 25 mW all the way to **1 W added nothing measurable.** The readings stayed within the sensor's roughly ±40 mA jitter.
- **For comparison,** published figures for other VTXs at 12 V:

| VTX | At 25 mW | At high power |
|---|---|---|
| AKK FX3-ultimate | 100 mA | 320 mA at 600 mW |
| FXT ARES 1 W | 200 mA | 480 mA at 1 W |
| Rush Tank | 95 mA | 380 mA at 800 mW |

  A working VTX should draw a few hundred mA *more* at high power than at 25 mW.

**Conclusion:** the controller works, the supply voltage is correct, and the current never rises with power. **The amplifier isn't producing output.**

> **Honest limits of this test:** the ESC's current sensor is designed to measure tens of amps, so it is noisy at a fraction of an amp. An inline wattmeter would give cleaner numbers. But a missing rise of a few hundred mA is large enough to see even on a coarse sensor, and it matched the pure static in the goggles.

## Root cause (most likely)

Early in the build, I powered the VTX for a bench test **without its antenna**. With no antenna, the amplifier has nowhere to send its energy. The power reflects back into the amplifier as heat, and it can be destroyed in seconds, especially on a 1 W VTX.

## Fix

I replaced it with an **AKK FX3-ultimate**. The control wiring stayed on the same pads:

| Old VTX wire | New VTX wire | FC pad |
|---|---|---|
| 7–26 V | Red (DC in) | 9V |
| GND | Black | G |
| VIDEO | Yellow | VTX |
| DATA | Green (SmartAudio) | T1 |

The new VTX gave a picture immediately: Band B channel 3, 25 mW.

## Lessons

1. **Antenna on before power. Every time.** Even for a 10-second test.
2. **"Ready" means the controller is alive. It does not mean the VTX is transmitting.**
3. **Current draw versus power setting** is a quick, free way to check a VTX's amplifier with tools you already have.
4. **Never unplug a powered VTX.** Breaking a live circuit can cause a voltage spike that damages electronics. I did this once during testing and shouldn't have.
