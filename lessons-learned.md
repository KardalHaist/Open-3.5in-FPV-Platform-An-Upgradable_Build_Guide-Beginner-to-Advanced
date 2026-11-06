# Lessons Learned

[← Back to README](README.md)

What I'd tell myself before starting.

## Hardware

1. **Antenna before power, without exception.** One short bench test without an antenna cost me a VTX.
2. **Check every motor by hand before soldering.** Spin it, feel for grit, and check it again once mounted. A screw that's too long can ruin a motor.
3. **Match mounting patterns before buying.** My frame takes 20x20 and 25.5x25.5 mm VTXs. Several VTXs I considered had 30.5 mm holes and would not have fit.
4. **Check voltage ratings.** Some VTXs are 5 V only and would die on a battery pad.
5. **Small buttons and parts break.** The VTX button snapped off while I was tightening hardware nearby. Work around delicate components carefully.
6. **Athletic tape is a great cheap motor-wire guard.** It's fast, light, and survives crashes.

## Electrical

7. **"Ready" isn't "working."** A device's controller can talk normally while its main function (such as the VTX amplifier) is dead.
8. **Current draw is a diagnostic tool.** If a load doesn't draw more current when it's asked to do more work, it isn't doing the work.
9. **Current meters go in series.** Putting the probes across a supply in current mode shorts it.
10. **A regulated supply is better than raw battery** for sensitive electronics, because the voltage stays steady when the battery sags.

## Software and setup

11. **Arming is blocked while Configurator is connected.** That's a safety feature, not a bug.
12. **Match video by frequency, not channel name.** Different brands label the same frequency differently.
13. **Bluejay is worth the five minutes.** It enables the RPM filter.
14. **Save a `diff all`** before and after every big change.

## Documentation

15. **Take photos at every stage.** You can't recreate an unboxing or a solder joint after the fact.
16. **Write down numbers as you go.** Voltages, currents, and settings are what make a build log useful.
