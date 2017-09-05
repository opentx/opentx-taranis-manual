# The firmware compilation options are
This page list the different options that are availabe for the [different radios](http://www.open-tx.org/radios)

## All radios

* ppmus: Displays channel values in microseconds instead of %.
* nooverridech: No OVERRIDE CHx functions available.
* faimode: Disables all telemetry except for RSSI and voltage, for compliance with contest regulations.
* faichoice: Adds a menu entry in the radio general settings to enable FAI mode. Allows you to train on contest day with telemetry, then turn FAI mode on in the menu before the contest to disable telemetry. FAI mode can then not be turned off on the radio again without connecting to a computer to avoid cheating.

## Arm Radios
Sky9X, Ar9X, 9XR Pro and all FrSky radios

* eu: Removes D8 FrSky protocol support which is not legal for use in the EU on radios sold after Jan 1st, 2015
* multimodule: [DIY Multiprotocol TX Module](https://github.com/pascallanger/DIY-Multiprotocol-TX-Module) support

## FrSky Radios

* noheli: Removes the Heli CCPM mixer menu page.
* nogvars: Disables global variable support and the associated menu page.
* lua: Support for lua model scripts.
* luac: Enable Lua compiler
* bindopt: Enable menu for binding D16 receiver with/without telemetry
  and 9-16ch instead of 1-8ch
* cli: Instead of joystick emulation, USB connection is Command Line Interface
* masstorage:  Instead of joystick emulation, USB connection is mass storage (as in the Bootloader).

## FrSky Taranis
This includes the Tranis X9D, X9D+, X9E and Q X7
* sqt5font: An alternative display font.
* internalppm: Support for PPM internal module hack. Only enable if
  you place to replace the internal module with a custom module.
* horusstick (X9E only): Horus gimbals installed (Hall sensors)
* shutdownconfirm (X9E only): Confirmation before radio shutdown
* haptic (X9D only): Haptic module installed

## FrSky Horus
For the Horus X12S
* pcbdev: Use ONLY with first DEV pcb version (Beta Horus)


## AVR radios only
Gruvin9x, FlySky 9X and Mega250 radio
* notemplates: Removes the Templates menu page.
