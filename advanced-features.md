#Advanced features




## Audio

One of the major features of the radio is the speech output function.

The Taranis radio is capable of playing sounds in response to specific events.

The sound pack is available for download from within OpenTX companion.

Extract the ZIP file to the root of the micro-SD card (FAT12/16/43 format).  It will create the necessary sub-directories (e.g. SOUNDS/en for the English pack). 

To use the micro-SD card insert it in the card slot within the battery compartment.

Sounds will play in a clear voice for events like:
    * Reaching trim center/ends
    * Activation of a physical or custom switch
    * Signal low/critical
    * Telemetry lost/recovered

You can even play music in the background.

Custom sounds can be placed in the SOUNDS/(selected_language) folder of the card and will be available for use.  The name must be 8 characters at most, not counting the .wav extension, and with no special characters.

Language is set in the radio general settings and can be changed on the fly as long as the pack for that language is loaded on the card.

If you wish to create your own files, the required format is:
WAV, 8 or 16 bit, Mono
8, 16 or 32kHz sample rate
PCM, u-law or a-law compression

The stock sounds above use the best available quality, i.e. 16bit, 32kHz and PCM.

Audio operation is relatively simple as it only consists of 5 "and a half" Special Functions:
* **Play Track:** Just play an audio file from the SD card when the associated switch is active.  A repeat option is available, when set the sound will repeat at the set interval as long as the switch is active.  This can be used to announce flight modes, gear position, flap position etc when the associated switch is activated or on request.
* **Play Value:** Say the value of the selected parameter when the switch is active. The repeat parameter is available too.
* **BgMusic:** Starts playback of a background sound track.  Possibilities include a sound track or a timed flight program announcement. The switch must stay on to continue playback.
* **BgMusic ||:** This pauses the background track while active, and resumes playback when deactivated. The BgMusic switch must stay active the whole time or the track will start from the beginning again.
* **Vario:** Reproduces the sound of a glider variometer.  The variometer uses the altitude or vertical speed telemetry data.
* **Volume:** Adjusts the audio volume for the entire radio to the value of an input, e.g. a pot.

There are a some predefined sounds that are played automatically when an event happens.  This is accomplished by placing an appropriately named file in the right folder.

Custom sounds for the following events are supported:
* Flight Mode Change:

  When flight mode is activated, file /SOUNDS/(selected_language)/modelname/flightmodename-ON.wav is played if present.

  When flight mode is deactivated, file /SOUNDS/(selected_language)/modelname/flightmodename-OFF.wav is played if present.

  The "modelname" and "flightmodename" folder should be identical (including case) to your model's name and flight mode name respectively, with spaces replaced by underscores.
  
  Of course only the files you want and place on the card are played, if something doesn't interest you then just don't put a file for it.

## Global variables

We have already mentioned how global variables could be used to group multiple adjustments in one place, and to make that adjustment flight mode specific.

It was also noted that these could be adjusted in flight - this is done using the Adjust GVx special functions.

Any time the special function's switch is ON, the value of the global variable will follow the selected input.

As a reminder, there are 4 groups of inputs that can be switched between by pressing ENTER LONG on the input field, and don't forget to tick the safety box once you're done configuring and you've made sure the switch is off - again to avoid overwriting your GVAR by mistake while scrolling the source list.

This is the way to adjust values in flight. 

The special function's switch serves as a "lock" to freeze the value or allow adjustment.

When a variable is being updated, a popup with the  variable name and new value will show up on the main views.

One of the available sources for adjusting global vars is the list of channels.

This is probably the main way you'll use to adjust GVARs for a simple reason: Let's say you want to adjust a D/R ratio with the S1 pot.

If you select GV1 as the weight parameter of that rate line and just use the Adjust GV1 custom function with S1 as source, you will now be adjusting your rate between -100% and +100%.

Being able to disable and even reverse your rate doesn't sound terribly fun, so you'll want to limit the adjustment range.

The easiest way is to use a free channel for that.

Create a mixer line on say CH12, and use the weight/offset/curve parameters to make that channel's output cover a range of say +50 to +80% over the pot's throw. 

Then set the Adjust GV1 source to CH12.

Some interaction examples

The power of the system now comes from the combination of the different features.

Logical switches are sometimes used to create conditions that will trigger audio playback.

**Two examples:**

Using logical switch "LS1|d|>x Alt 10" as trigger for "Play Value Alt" would result in the altitude being announced every time it has changed by 10m/ft. 

Using logical switch "LS2 a < x Spd 35" triggering "Play Track lowspd" would play the lowspd.wav file on the SD card, that could be recorded to say "Low Speed" when GPS speed got under 35km/h.

If you have several parameters you want to have announced sequentially on request, you could set several Play Value Special Functions all triggered by the SHdown momentary switch as shown above.

A press of this switch will then trigger playback of all the parameters one after the other.

Logical switches can be used anywhere a switch is definable.  Nothing prevents you from reusing that same LS2 to trigger automatic flaps deployment once speed got below 35km/h.

That's right, anything can be used to affect anything.

## Flashing the bootloader

From time to time it will be necessary to flash the bootloader with a newer version.

Copy the currently downloaded firmware (.bin file) into the FIRMWARE directory of the SD card.

First you have to jump into the [Radio Menu](radio_menus.md) then hit the page button until you get to the SD CARD menu.   

Highlight the FIRMWARE directory and press the [Ent] key.

Highlight the bin file and Long Press [Ent].

Choose flash bootloader from the menu and press [Ent].

You can verify the bootloader version by going into the VERSION page of the Radio Menu.