# RatOS Klipper configs

This repo is just a copy of my user configs for my V-core-3 3D printer running Ratrigs customized version of klipper, RatOS.

These configs are specific to my setup, I have not made any effort to make them generic, so if you copy them please make sure
to verify they work with your setup.

## Extra info

### Dock location

I am using MFBS rigid backplate, which has a different probe catch, please verify the dock locations in euclid macros if you plan to use this!

### Euclid stuff

I have setup the Euclid probe to be deployed and kept deployed if the klipper variable `variable_start_of_print` is set to True. 
To do this in your start print gcode in your slicer add the following:

```gcode
SET_GCODE_VARIABLE MACRO=RatOS VARIABLE=start_of_print VALUE=True
```

And add this to your end gcode:

```gcode
SET_GCODE_VARIABLE MACRO=RatOS VARIABLE=start_of_print VALUE=False
```

Finally make sure you add that variable to your `RatOS` macro in the `MACRO CONFIGURATION` section of your `printer.cfg`

```gcode
variable_start_of_print: False
```

Essentially what is happening is in the stow macro we check if this is set, and if it is we assume that we are doing the 
home->z-tilt->home->bed mesh dance at the start of a print, and we don't stow the probe until we finish the bed mesh.

### Prime blob

I have overridden the prime blob to move it over and away from the euclid dock. Again depending on your setup this may or
may not land in a good spot for you.
