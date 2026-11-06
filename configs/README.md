# Betaflight Configuration

[← Back to README](../README.md)

## Settings summary

| Area | Setting |
|---|---|
| Receiver | Serial RX on UART2, CRSF (ELRS) |
| VTX | SmartAudio on UART1, Band B channel 3 (5771 MHz), 25 mW, pit mode off |
| Bluetooth | MSP on UART4 at 115200 (SpeedyBee app) |
| Motor protocol | DShot with Bidirectional DShot on (needs [Bluejay](../build-log/04-esc-firmware-bluejay.md)) |
| Motor poles | 14 |
| Current meter | Onboard ADC, scale 250, offset −500 |
| Voltage meter | Onboard ADC, scale 110 |
| Cell limits | Min 3.3 V, warning 3.5 V, max 4.3 V |

## Backing up settings (the `diff all` file)

A **diff** lists only the settings you changed from the defaults. It's the standard way to save and share a Betaflight setup.

1. Connect the FC and open the **CLI** tab in Betaflight Configurator.
2. Type `diff all` and press Enter.
3. Click **Save to File** and name it `betaflight-diff.txt`.
4. Put the file in this folder.

**To restore:** paste the contents into the CLI, then type `save`.
