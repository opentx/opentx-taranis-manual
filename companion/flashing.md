## Flashing your FrSky radio

As mentioned before, the program of your radio can be replaced, either
to change the display language or to take advantage of new functions
or corrections.  The first thing to do is to power your radio off and
connect it to your computer's USB port.

## Installing the driver (for Windows only)

Installing the driver is only needed when you want or need to flash
your radio directly from the PC. The Taranis models all have a
bootloader that allows flashing without these drivers. For flashing a
Horus TX or if you need to recover your Taranis, you will need to
install these drivers.

Installing the driver is only required the first time you flash your
radio on a given computer. If already done this step, you can skip
this section.
* Download the Zadig utility for your operating system from its homepage: http://zadig.akeo.ie/
* Run it as Administrator (Right-click and select the relevant entry).
* In the big dropdown, you should find an entry named either "STM32
  BOOTLOADER" or "STM Device in DFU mode". Select it, and click the
  "Install Driver" button.
* If you do not have one of those entries, choose Options -> List All
  Devices, and it should now appear in the list. Select it, and click
  the "Replace Driver" button. DO NOT do it for anything else than
  those 2 possibilities. If you see "FrSky Taranis Bootloader" you
  have connected your radio with power on instead of power off, and
  overwriting the driver with Zadig would render the SD card and
  models/settings inaccessible.

![](images/companion-zadig-1.png)

![](images/companion-zadig-2.png)

Zadig will install the driver, and should report success. When done you can dismiss the message and close it.

![](images/companion-zadig-3.png)

Should none of these options work, you can download the driver here and install it manually (instructions are on the download page).
When the driver is properly installed, you should see this in the device manager:

### Installing the flashing utility (Linux)

Dfu-util is avaialble in most distributions. For example in Ubuntu it can be installed by

```
sudo apt-get install dfu-util
```
### Setup for Mac OS X

Companion for Mac OS already includes the required ``dfu-util'' tool
and does not require any additional installation of tools or drivers. 

## Downloading and flashing the firmware

In OpenTX companion's preferences window, make sure the proper
firmware is selected (OpenTX for FrSky Taranis (X9D), or OpenTX for
Taranis Plus (X9D+) according to the hardware you have), and the
language / options match your preference, then click the top Download
button and select a location for the file. This will automatically
build and download the latest available version of OpenTX for Taranis.
Close the Preferences window, and select the Burn -> Write Flash
memory command. Make sure your radio is powered off and connected.
Browse for the file you just downloaded. It will be recognised
automatically and the version will be displayed.  If you wish to
replace the radio's splash screen, you can either load one from a file
or select it from the available library, and click the "Substitute
image in firmware" box.  Click "Burn to TX".  Once the progress bar is
done and the success prompt is shown you can dismiss it and disconnect
your radio :) If you get an error about the dfu-util executable not
being found, open the flashing tool settings with the Burn ->
Configure menu item. Browse for the dfu-util executable, which should
be: On Windows: In the OpenTX companion installation folder (by
default C:\Program Files\companion9x\dfu-util.exe on 32-bit systems,
and C:\Program Files (x86)\companion9x\dfu-util.exe on 64-bit
systems).  On Mac OS: ```/Applications/OpenTX Companion
2.2.app/Contents/Resources/dfu-util```

## Downloading and installing SD card content.

Once you have installed the firmware you will also need to install the
sd card content (unless you do not use a sd card).

See the [Sdcard](sdcard.md) for more details.
