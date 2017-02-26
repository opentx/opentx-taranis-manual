## Audio

One of the major features of the radio is the speech output function.

The Taranis radio is capable of playing sounds in response to specific events.

The sound pack is available for download from within OpenTX companion.

Extract the ZIP file to the root of the micro-SD card \(FAT12/16/43 format\).  It will create the necessary sub-directories \(e.g. SOUNDS/en for the English pack\).

To use the micro-SD card insert it in the card slot within the battery compartment.

Sounds will play in a clear voice for events like:

* Reaching trim center/ends
* Activation of a physical or custom switch
* Signal low/critical
* Telemetry lost/recovered

You can even play music in the background.

Custom sounds can be placed in the SOUNDS/\(selected\_language\) folder of the card and will be available for use.  The name must be 8 characters at most, not counting the .wav extension, and with no special characters.

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
* **BgMusic \|\|:** This pauses the background track while active, and resumes playback when deactivated. The BgMusic switch must stay active the whole time or the track will start from the beginning again.
* **Vario:** Reproduces the sound of a glider variometer.  The variometer uses the altitude or vertical speed telemetry data.
* **Volume:** Adjusts the audio volume for the entire radio to the value of an input, e.g. a pot.

There are a some predefined sounds that are played automatically when an event happens.  This is accomplished by placing an appropriately named file in the right folder.

Custom sounds for the following events are supported:

* Flight Mode Change:

  When flight mode is activated, file /SOUNDS/\(selected\_language\)/modelname/flightmodename-ON.wav is played if present.

  When flight mode is deactivated, file /SOUNDS/\(selected\_language\)/modelname/flightmodename-OFF.wav is played if present.

  The "modelname" and "flightmodename" folder should be identical \(including case\) to your model's name and flight mode name respectively, with spaces replaced by underscores.

  Of course only the files you want and place on the card are played, if something doesn't interest you then just don't put a file for it.

## 



