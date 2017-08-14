# Basic concepts

OpenTX companion handles 2 main tasks:

* Managing radio settings and models
* Downloading new radio firmwares, and transferring them to the radio.

An important thing to understand is how things are stored on the radio. We will talk of 2 different types of memories, Flash and EEPROM.

* Flash is the memory where the radio's firmware or "operating system" resides. "Flashing the radio" means replacing the firmware.   Flashing the radio allows you to upgrade to a newer version or to change language.  Models and settings are not affected when flashing the firmware.  On the Taranis, flashing is done with the radio OFF.  So turn the radio off, then plug it to the computer's USB port.
* EEPROM is the separate settings/model memory.  Reading it allows backing up and editing in OpenTX companion, writing it sends the result of the edits back to the radio.  On the Taranis, this is done with the radio ON. Turn it on, dismiss any warnings in order to get to the main views, then plug the USB cable. You will see two USB drives appear, one is the SD card, and one is the EEPROM virtual drive.

OpenTX Companion will thus handle 2 different types of files.

Firmware files, that can be downloaded from the Preferences dialog, which are non-editable and can just be transferred to/from the radio, and EEPROM files for which OpenTX companion provides an editor that allows to change anything in the same way that would be done on the radio itself.

When creating \(File-&gt;New\) or opening \(either by dragging it onto the main window or via the File-&gt;Open menu command\) an EEPROM file, a document window will appear.

Several of those windows can be open at the same time, allowing you to copy models or settings between files.

Trying to open a firmware file the same way will throw an error saying the file is invalid - this doesn't mean that the firmware is invalid, but simply that it is not a settings file.

![](/images/companion-models-list.png)

The document window consists in a "General Settings" entry on which you can double-click to access the radio settings, and a number of model slots \(60 for the Taranis\).

The model slot that is displayed in bold is the one that is currently selected on the radio.

It can be chosen in OpenTX companion by right-clicking on the model slot, and choosing "Use as default".

Double-clicking on a model slot will open the editor for that model, creating one if it was empty.

![](/images/companion-menu-read-write.png)

Memory operations to/from the radio are handled by the different entries of the "Read/Write" menu:

* Read EEPROM from TX will read the EEPROM contents from the radio, and open them in a new document in OpenTX companion. The document is opened for editing, but is not saved to disk automatically.
* Write EEPROM to TX sends a currently open and selected document \(if you have more than one open, make sure to click on the one you want to transfer first to select it\) to the radio.
* Read EEPROM memory to File will read the EEPROM contents from the radio directly into a file. This is the preferred way to backup your radio's settings as it will be saved "as is" without OpenTX companion processing it. Click the entry, choose a location and filename, and save.
* Write EEPROM memory from File will allow you to select a file, and will transfer it as is to the radio. This is the preferred way to restore a backup as again no processing is going on.
* Write Flash memory will flash the radio's firmware from the selected file. Once the file is selected, you have the option to replace the default splash screen with an image of your choice, or the default image selected in the preferences.
* Read Flash memory will back up the firmware that is currently on the radio to a file.



