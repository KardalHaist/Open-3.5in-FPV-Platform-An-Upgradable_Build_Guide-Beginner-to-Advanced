# Troubleshooting Log

[← Back to README](../README.md)

Every problem I hit during the build, what caused it, and how I fixed it.

| Problem | Cause | Fix | Status |
|---|---|---|---|
| [No video, only static](#no-video-only-static) | VTX amplifier failed | Replaced the VTX | ✅ Fixed |
| [Won't arm: "MSP" flag](#wont-arm-msp-flag) | Configurator connected over USB | Disconnect USB, arm on battery | ✅ Expected behavior |
| [Gritty motor](#gritty-motor) | Likely bearing side-load or stiff grease | Inspected; ran smooth after checks | ⚠️ Monitor |
| [VTX button broke off](#vtx-button-broke-off) | Pressure while tightening hardware | Not needed with SmartAudio | ✅ Worked around |
| [Radio won't connect to its web UI](#radio-wont-connect-to-its-web-ui) | No serial port appears in Windows | Bound with the bind button instead | ⚠️ Open |
| [Goggle channel names don't match](#goggle-channel-names-dont-match) | Goggles use their own labels | Match by frequency (MHz) | ✅ Fixed |
| [Betaflight shows 1 cell](#betaflight-shows-1-cell) | Cell-count guess at plug-in | Replug the battery | ✅ Fixed |

---

## No video, only static

Full case study: **[vtx-amplifier-failure.md](vtx-amplifier-failure.md)**. In short: Betaflight said the VTX was ready, but its current draw didn't rise when I raised the power, so the amplifier wasn't working.

## Won't arm: "MSP" flag

**MSP** (MultiWii Serial Protocol) is the link Betaflight Configurator uses. Betaflight refuses to arm while Configurator is connected, so a quad on your desk can't spin up unexpectedly. Disconnect in Configurator, unplug USB, and arm from the battery. The Setup tab lists any other arming flags.

## Gritty motor

One brand-new motor felt sandy and uneven when turned by hand. The others had only the faint, even notchiness of the magnets (**cogging**, which is normal).

**How to check a motor:**
1. Take it off the frame and spin it by hand. If it's smooth off the frame, the mounting screws are too long or the mount is pressing on it.
2. Flick it and compare how long it coasts against a good motor.
3. Look into the gap between the bell and the stator with a flashlight for debris. The magnets attract metal dust.
4. Wiggle the bell. A clunk or play means a worn bearing.

Squeezing the base improved it, which suggests the bearing was sitting slightly off-center. That's a fix to monitor, not a cure. **Don't squeeze motors as a repair**, and replace or return a motor that stays gritty.

## VTX button broke off

The original VTX's push button snapped off cleanly while I was tightening hardware nearby. The button only changes channel and power by hand. With SmartAudio wired up, Betaflight does the same job, so the VTX still works without it. If it's needed, the button can be reflowed back onto its pads (if they're intact).

## Radio won't connect to its web UI

The RadioMaster T8L has no screen. It is configured through a web page in Chrome or Edge. Windows played the USB connect sound, but no COM port appeared in Device Manager.

**Tried:**
- different cables (some USB-C cables only charge),
- different ports,
- closing other programs,
- rebooting.

**Workaround:** binding doesn't need the web UI. The T8L binds with its bind button, and the receiver enters bind mode after three quick power cycles.

**Still to try:**
- check `joy.cpl` (the T8L may be appearing as a game controller);
- test on another computer;
- contact RadioMaster support.

## Goggle channel names don't match

My whoop's VTX reported "Raceband 3," but the VR009 goggles showed "E6" for the same signal. Budget goggles don't always follow the standard band labels. **Always match by frequency in MHz.** This quad runs **5771 MHz** (Band B, channel 3).

## Betaflight shows 1 cell

The Power & Battery tab showed "Cells: 1" and a nonsense voltage drop (−11.93 V). Betaflight guesses the cell count when the battery is connected, and it guessed wrong. Unplugging and replugging the battery fixed it. If it happens repeatedly, check the voltage meter scale.
