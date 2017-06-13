# Setting up OpenTX Companion for Taranis

The first thing is of course to download and install the appropriate version of OpenTX Companion for your system from the OpenTX home page.

Once the program is launched, you will see the main window.

Open the Settings Dialog with Settings->Settings.

![](images/companion-settings.png)

There are three tabs.

Radio Profile:
* Profile name - Name the profile for the hardware.
* Radio type - Choose the proper model type that you are using.
* Menu Language - Language you want the menu for the radio to display in.
* Build Options
  * notemplates: Removes the Templates menu page.
  * nogvars: Disables global variable support and the associated menu page.
  * ppmus: Displays channel values in microseconds instead of %.
  * timer3: provide a third timer.
  * cli: Instead of joystick emulation, USB connection is Command Line Interface
  * sqt5font: An alternative display font.
  * noheli: Removes the Heli CCPM mixer menu page.
  * mixersn: Add mixers view to CHANNEL MONITORS screen, pressing [ENT] switches between views.
  * nooverr: No OVERRIDE CHx functions available.
  * nogvars: Disable global variables.
  * eu: Removes D8 and LR12 Frsky protocols that are illegal in Europe after Jan 1st, 2015.
  * faichoice: Adds a menu entry in the radio general settings to enable FAI mode. Allows you to train on contest day with telemetry, then turn FAI mode on in the menu before the contest to disable telemetry. FAI mode can then not be turned off on the radio again without connecting to a computer to avoid cheating.
  * lua: Support for lua model scripts.
  * internal: Support for use with internal module hack.
  * faimode: Disables all telemetry except for RSSI and voltage, for compliance with contest regulations.
  * massto:  Instead of joystick emulation, USB connection is mass storage (as in the Bootloader).
  * ppmus:  Channel values displayed in us.
* Splash screen: selected splash screen.
* SD structure path: For radios with SD cards, Taranis and sky9x board, this lets you choose a folder on your hard drive where you have made a copy of what is on the SD card of the radio.  This allows OpenTX companion to populate the model image selector with the images that are on the card, and do the same for audio files.
* Backup Folder: Location of backup eproms
* Default Stick mode and channel order: These will be applied when creating a new EEPROM document in OpenTX companion.
* Automatically add version number to firmware files: When downloading a firmware file, its name includes the selected options. If this box is checked, the revision number will be appended to the filename to make it more convenient to maintain files of different versions.
* Offer to write FW to TX after download.

Application settings:
* Google Earth Executable
* Files to keep - number of firmware files to keep
* Show splash screen when companion starts
* Use model wizard when making a new model in companion
* Automatic check for OpenTX firmware updates
* Automatic check for Companion updates
* Automatic Backup Folder
* Enable writing automatic before writing firmware.
* Splash Screen Library
* User Splash Screens - location to store user created splash screens.  Splash screens need to be 212x64 pixels for Taranis, up to 16 grayscales.

Simulator settings:
* Simulator Capture capture folder
  * Only capture to clipboard
  * Remember simulator switch values
* Simulator Backlight: Choose th simulator backlight color.
* Joystick
* Simulator volume gain: volume gain for simulator




* Profiles: Allows storing different setting sets and easily switching between them. For example, if you have 2 different radios with different firmwares or board types it is not convenient to have to redo all settings (firmware selection, ticking options,...) every time you want to do operations on the other radio. So you can configure all settings, choose an empty profile with the number box, type a name to identify the particular radio, and click save. Do the same for the second radio. You will now be able to select the correct profile for the radio you are about to work on with the profile selector button and menu entry on OpenTX companion's main window. Note that the profiles can also store and retrieve each radio's stick calibration and hardware settings (voltage alarms, audio modes,...) from the General Settings page of an open document. This allows copying a document from one radio to the other without needing recalibration or reentering the hardware settings.

Joystick: This lets you configure a joystick to simulate the sticks in the radio simulator.
For a Taranis radio, the first thing you would do is select "OpenTX for FrSky Taranis" in the firmware dropdown. Select your firmware language, and the voice language. The top Download button will compile and download the latest available firmware version with the selected language and options. The bottom Download button will open your web browser on a page showing you a selection of voice packs available for the selected language.
Set your flight mode and preferred channel order in the dropdowns below, and dismiss the Preferences dialog with OK for now.
