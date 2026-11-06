# 04 · ESC Firmware: Upgrading to Bluejay

[← Previous: Soldering](03-soldering-and-wiring.md) · [Back to README](../README.md) · [Next: Betaflight setup →](05-betaflight-setup.md)

The SpeedyBee BLS 35A ESC ships with **BLHeli_S**, an older firmware for 8-bit ESCs. I replaced it with **Bluejay**, a free, open-source firmware for the same hardware.

## Why bother?

**Bidirectional DShot.** Stock BLHeli_S only receives commands. Bluejay can also send each motor's RPM back to the flight controller. Betaflight uses that RPM data for the **RPM filter**: since it knows exactly how fast each motor spins, it can remove the motor vibration noise from the gyro signal at precisely the right frequencies.

What that gets you:
- cleaner gyro data, so smoother flight;
- cooler motors, because the flight controller isn't reacting to noise;
- room for better tuning later.

Bluejay also allows a higher **PWM frequency** (how fast the ESC switches the motor coils) and custom startup tunes.

## How I flashed it

1. Remove the props. Connect the FC by USB and plug in the battery (the ESC needs battery power to be flashed).
2. Open **ESC Configurator** (esc-configurator.com) in Chrome or Edge and connect.
3. Click **Read settings** to confirm all four ESCs are detected.
4. Choose **Flash all**, select **Bluejay** and the latest stable version, then choose the PWM frequency.
5. Wait for all four ESCs to finish. **Don't unplug anything mid-flash.**
6. Read settings again to confirm the new version.

| Setting | Value |
|---|---|
| Firmware | Bluejay (latest stable at the time of flashing) |
| Motor direction | Set per motor here or in Betaflight |

## Turning on the RPM filter in Betaflight

1. **Configuration tab:** set **Motor protocol** to DShot300 (or DShot600) and turn on **Bidirectional DShot**.
2. **Motor poles:** set to **14**. The P1604 is a 12N14P motor (12 stator teeth, 14 magnets), and Betaflight needs the magnet count to convert electrical RPM to real RPM.
3. Save and reboot. Then check the **Motors tab**: each motor should show an RPM reading and an error rate near 0%.

**If the RPM shows 0 or the error rate is high,** the ESC isn't running Bluejay, or Bidirectional DShot isn't enabled.
