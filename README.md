# klipper-fake-toolchanger
Allows gcode T commangs to trigger an M600
## Features
* Sends an M117 message and action_respond_info text to the klipper console (and anything configured to listen) with the next toolchange, which along with a reference of which colour is intended wit heach tool means forgetful people have a prompt for which colour comes next. It's also obvious that it's a toolchange not a _filament (motion) sensor_ triggered runout. 
* allows separate print temperature, flow multiplier, pressure advance etc., compared to a colour change by layer approach which typically uses one filament settng all the way, so potentially layering materials with similar temperatures but wildly different elasticity like PLA and TPU.
* can be used as a full MMU-style for prints of just a few layers, like game counters, or a few swaps to get a logo in the bottom or top layers.
* Always resets to T0 when the printer is reset, leads to less confusing printer state issues.

## Requirments
* A working M600 command, ideally with auto-eject and push-button load and purge commands, there's an example in [strayr-k-macros](https://github.com/strayr/strayr-k-macros) that builds on the PAUSE/RESUME and PARK code and you need to be able to move the toolhead somewhere safe during a pause and you need a way to manually purge the filament. My macro package is a bit overkill so just get a working M600 ewahtever way you're happy with/
## PrusaSlicer/Superslicer setup
* Set 6 (or adjust macro for more) extruders and single-extruder Multi Material in printer settings
* set all the distances to zero in "Single Extruder MM setup"
* Disable the wipe tower

