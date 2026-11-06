# Future Improvements

[← Back to README](README.md)

This build works, but there's plenty of room to improve it. Here's what I'd consider next, roughly from cheapest to most involved.

## 1. Digital video

Analog is cheap and has very low latency, but the picture is low resolution and noisy. Digital systems send HD video, at the cost of more money and a little more latency.

| System | Rough total cost (VTX + goggles) | Latency | Notes |
|---|---|---|---|
| Walksnail Ascent | About $185–200 | About 32–35 ms | Cheapest HD; new ecosystem, Ascent goggles only |
| DJI O4 Air Unit + Goggles N3 | About $390 | About 31 ms | Best image; this frame and FC are designed for DJI |
| HDZero | About $430 and up | About 8 ms | Lowest-latency digital; lower resolution |

Prices are approximate (late 2026) and change often. The VX3.5 frame has a DJI O4 camera mount, and the SpeedyBee stack has dedicated DJI pads and a cable, so DJI would be the easiest swap.

**A GoPro isn't a video link.** Action cameras add 100 ms or more of delay. Pilots mount one to *record* HD footage while flying on a separate low-latency FPV feed.

## 2. Tuning

- **Blackbox logging:** record gyro and motor data in flight, then view the noise spectrum in Blackbox Explorer or PIDtoolbox.
- **Filter tuning:** with the RPM filter already running (thanks to Bluejay), the other filters can often be relaxed for less delay.
- **PID tuning** for the 3.5" size and 4S power.

## 3. Measurements

- **Current sensor calibration** against an inline wattmeter.
- **Flight time:** predicted versus measured.
- **Thrust stand:** measure thrust, current, and efficiency (grams per watt) for these motors and props, and compare with the manufacturer's data.

## 4. Hardware

- **GPS rescue:** a small GPS module enables Betaflight's return-to-home failsafe (watch the weight margin).
- **Buzzer:** a lost-model beeper for finding the quad after a crash.
- **Better antennas:** a matched circular-polarized antenna pair (RHCP on both the VTX and the goggles) reduces multipath breakup.
- **Prop guards or a cinewhoop conversion** for flying near people or indoors.
- **Fix the radio's web UI connection,** to unlock full T8L configuration.

## 5. Weight budget

At 238.36 g the quad is about 12 g under the 250 g line. Any added hardware (GPS, buzzer, a digital air unit, a bigger battery) should be weighed against that margin. A lighter frame hardware set or a smaller battery would buy room.
