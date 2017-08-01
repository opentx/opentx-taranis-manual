OpenTX on Taranis/Horus radios can act as a USB Joystick when connected to a personal computer.

### How to activate
* Ensure that [cli and massstorage options](radio_options.md) are not used
* Power up Taranis (do not activate Bootloader)
* Clear all warnings
* Connect USB cable, USB connect symbol appears.
* USB Joystick device should be available on computer.

### Description of Joystick interface
Taranis simulates a joystick device with:
* 8 analog axes
* 24 digital buttons

Analog axes are mapped to first eight channels: from CH1 to CH8. Valid output value for each channel is from -100 to 100.

Buttons are mapped to the remaining channels: form CH9 to CH32. Button is considered pressed when channel value is bigger than zero.

User should create a new model for joystick usage with following settings:
* TX module turned off
* servo limits at 100%
* appropriate mixes on channels 1 to 32
* optionally some exponential on analog axes (channels 1 - 8)

### Example model setup
TODO


### Technical details
Tranis simulates 8bit analog USB joystick. Channel outputs in range from -100% to 100% are mapped into 8 bit signed number from -127 to 127. Channel values higher than 100% or lower than -100% are truncated into 100% and -100% respectively.

----

## Using Taranis USB Joystick with CRRCsim on Linux

This setup describes how to compile and configure CRRCsim 0.9.112 flying simulator on Linux Mint 15 Olivia (based on Ubuntu Raring 13.04).

### Installation of CRRCsim

Start by downloading CRRCsim 0.9.112 source from [source](http://sourceforge.net/projects/crrcsim/files/crrcsim/crrcsim-0.9.12/crrcsim-0.9.12.tar.gz/download)

Before compilation we nedd to install needed packages (might need some more, that I installed before, look at output of ./configure for clues):
```
$ sudo apt-get install libplib-dev libportaudio-dev libsdl1.2-dev libjpeg-dev
$ ./configure
$ make
```
I choose not to install CRRCsim (`$ sudo make install`) and choose to run it from build directory.

### Joystick calibration
Joystick calibratin on linux with `jscal`  creates a small deadzone (deadband) around stick centres by default. Deadband means that small stick movements around centre position result in no movement on computer. This is undesirable for usage in RC simulators. Folowing steps are necessary to get reed of deadband.

First you calibrate joystick with jscal you get a calibration string like so:

```
$ jscal -c /dev/input/js0
Joystick has 4 axes and 8 buttons.
Correction for axis 0 is none (raw), precision is 0.
Correction for axis 1 is none (raw), precision is 0.
Correction for axis 2 is none (raw), precision is 0.
Correction for axis 3 is none (raw), precision is 0.

Calibrating precision: wait and don't touch the joystick.
Done. Precision is:                                                -2,   -2
Axis: 0:     0
Axis: 1:     0
Axis: 2:     0
Axis: 3:     0

Move axis 0 to minimum position and push any button.
Hold ... OK.
Move axis 0 to center position and push any button.
Hold ... OK.
Move axis 0 to maximum position and push any button.
Hold ... OK.
Move axis 1 to minimum position and push any button.
Hold ... OK.
Move axis 1 to center position and push any button.
Hold ... OK.
Move axis 1 to maximum position and push any button.
Hold ... OK.
Move axis 2 to minimum position and push any button.
Hold ... OK.
Move axis 2 to center position and push any button.
Hold ... OK.
Move axis 2 to maximum position and push any button.
Hold ... OK.
Move axis 3 to minimum position and push any button.
Hold ... OK.
Move axis 3 to center position and push any button.
Hold ... OK.
Move axis 3 to maximum position and push any button.
Hold ... OK.

Setting correction to:
Correction for axis 0: broken line, precision: 0.
Coeficients: 0, 0, 5263280, 5315391
Correction for axis 1: broken line, precision: 0.
Coeficients: 1, 1, 5212180, 5368545
Correction for axis 2: broken line, precision: 0.
Coeficients: -1, 0, 5315391, 5263280
Correction for axis 3: broken line, precision: 0.
Coeficients: -5, -4, 5534583, 5064665
```

Get the calibration string with this command:

```
$ jscal -p /dev/input/js0
jscal -s 4,1,0,0,0,5263280,5315391,1,0,1,1,5212180,5368545,1,0,-1,0,5315391,5263280,1,0,-5,-4,5534583,5064665 /dev/input/js0
```

The deadzone is defined by first two numbers, for example last channel:

```
Coeficients: -5, -4, 5534583, 5064665
```

Here the deadzone is from -5 to -4. We want this to be 0, 0 on all channels. We must edit string that was returned by jscal -p command. Just set two numbers that precede two large numbers to 0, 0:

Original:

```
jscal -s 4,1,0,0,0,5263280,5315391,1,0,1,1,5212180,5368545,1,0,-1,0,5315391,5263280,1,0,-5,-4,5534583,5064665 /dev/input/js0
```

Changed:

```
jscal -s 4,1,0,**0,0**,5263280,5315391,1,0,**0,0**,5212180,5368545,1,0,**0,0**,5315391,5263280,1,0,**0,0**,5534583,5064665 /dev/input/js0
```

Save this for later. You must do this procedure for your setup, don't use my numbers!

### Calibration testing

First set calibration, use above (version with **your calibration values**)
```
$ jscal -s 4,1,0,**0,0**,5263280,5315391,1,0,**0,0**,5212180,5368545,1,0,**0,0**,5315391,5263280,1,0,**0,0**,5534583,5064665 /dev/input/js0
```
Then run test:
```
$ jstest /dev/input/js0
```
The values should change with the slightest movement of stick around center position. If they stay zero, then you set wrong calibration parameters.

### Setting up CRRCsim

CRRCsim uses SDL interface to access joystick, by default SDL ignores joystick calibration that was set with jscal. To correct that, the environment variable `SDL_JOYSTICK_DEVICE` must be set [(explanation)](http://stackoverflow.com/questions/14543333/joystick-wont-work-using-sdl).  It is best to use a short script, that will set joystick calibration, export variable and run CRRCsim. Be sure to use you own calibration values inside the script:

```bash
#!/bin/sh

#set joystick calibration
jscal -s 4,1,0,0,0,5263280,5315391,1,0,0,0,5212180,5368545,1,0,0,0,5315391,5263280,1,0,0,0,5534583,5064665 /dev/input/js0

#configure SDL to use proper joystick device
export SDL_JOYSTICK_DEVICE=/dev/input/js0

#run sim
./crrcsim
```
