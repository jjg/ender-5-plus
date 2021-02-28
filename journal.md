# Journal

## 02282021

Assembled the printer yesterday and managed to print one of the gcode files from the included MicroSD card, but wasn't able to print anything of my own.  Today I'm focused on getting any sort of a workflow in place, even if it's not the final, automated version.

The first attempt was made using PrusaSlicer and the Ender 5 Plus preset.  The result was the print head crashing into both the left X axis and plowing one of the bulldog clips across the glass bed.

I tried again, this time I modified the stock Ender 5 Plus profile to set the origin at 180x 180y (since the printer homes to the center of the bed) but the same thing happens.

I'm not used to a printer that is supposed to "just work", so when it doesn't I don't know what to do to fix it the way I would with a printer I built myself.  I really wish I could just type gcode into the printer's console and see what happens, but so far I've had no luck getting a console connection via octoprint.

After some manual moving of the axis it became clear that while the endstops of the x & y axis are at the rear-right corner of the printer, the origin is set for the front-left.  This makes sense except that when the x axis is moved to 0 it crashes the hot-end into the frame, and if moved along the Y axis to 0, runs over the bulldog clips holding the glass bed on.

So I modified the config in PrusaSlicer to set the origin to x 30 and y 0.  This should give us plenty of clearance...

While I was typing that the thing crashed into the hot-end again.  I don't know if it's not homing correctly or what, but something is fucked up.

This might be due to another problem I noticed yesterday.  There is a sensor for tramming the Z axis and I found that it overshoots the bed on the low end of the X axis.  I "scooched" the bed so that it would trip the sensor but after the earlier crash it seems to have un-scooched.

If this gets tripped-up again I might disable the auto-tram feature for now and just do it the old-fashioned way until I get a print out of it.

Well it's sort of working.  X still crashes when the machine is getting ready to print, but it moves more-or-less to the center and started printing.  Z was too close to the nozzle, almost scraping the glass but I was able to adjust it on-the-fly and increase the gap to a point where the print looked OK and the extruder stopped skipping (-2.00).

I'm not sure what to take-away from this.  Clearly I need to do something to make it stop crashing the X axis when it initializes, and I need to do something to make the Z compensation "stick".  

