# Advanced features

## Flight modes

Flight modes in OpenTX are relatively simple compared to most radios. The settings are simple: A name (displayed on the main views), a switch to activate them, a trim setting and 2 fade in/out settings. Yet they are very powerful, because the main settings are actually just located somewhere else: in the D/Rs and mixers. Each of these has a flight mode selection list, that will determine in which one(s) they are active. So (nearly) everything is done through dedicated mixers. The mixers that are controlled by a flight mode will see their activation fade in/out according to the mode's settings. As the trims can be made flight-mode specific (they are by default), using flight modes to activate things like gear or flaps allows using the separate set of trims to counter the extra drag that often causes an effect on pitch.

## Telemetry values

The following will assume your radio is loaded with a microSD card and a valid voice pack, which should be the case as it is supplied with the radio. Probably the most important telemetry value is RSSI, which is an indication of how much signal the receiver in the model is seeing from the radio, and will warn you in advance if you are at risk of losing control be it due to external interference, excessive distance, badly oriented or damaged antennas etc. The telemetry settings page gives you 2 alarm levels you can set that will be announced in clear voice ("RF signal low" and "RF signal critical"). They are set by default to levels that have been considered suitable and safe for normal line of sight flight (45 and 42), but if you want to adjust them yourself the following explanations will be useful.

RSSI on FrSky equipment is represented using a logarithmic scale (dB), not using percentage. 

This means that when RSSI is high, a small difference in the distance between the transmitter and receiver will lead to a big change of the RSSI value.

It is perfectly normal to see a value of about 100 when next to the model, and already down in the 70's by the time you've walked to the other end of the field.

When you have a reading of 50, it will however take a lot of extra distance to reach the alarm level of 45. 

The basic approximation rule is that a doubling of distance between pilot and model will result in a drop of 6dB of the RSSI value, which should make the previous explanation clear.

If you are 5m away from the model it only takes another 5m to reduce RSSI by 6dB, but if you are 600m away from the model it will then take another 600m to reduce the value by the "same" 6dB.

Loss of control will happen when RSSI reaches a value of about 38, so setting an alarm at 10 is useless.

From the above explanation you can see that between the default critical alarm (42) and usual practical loss of control we have a margin of about 4dB, or range factor of around 1.5.

The alarms are thus rather conservative, and in normal conditions even if you heard the critical alarm you would still be far from losing control (you should be at around >1000m distance, with another 500m to spare).

Intermittent loss due to local fades and antenna orientation mismatches could, however, get more and more frequent.

As mentioned earlier, the default alarms are deemed safe for usual line of sight flight.

However, with FPV setups, especially when coupled with automatic return to home systems and properly configured failsafes, the safety margin can be reduced and you should be able to extract more or less double of the standard range out of the system.

It is up to you to safely experiment.

Once the margin gets reduced, influence of external interference sources will start to become more noticeable.

It is practicly impossible to predict the behavior of a given installation in a particular model.

The Taranis also has an alarm that will warn you of the telemetry downlink being lost or recovered.

The telemetry link behaves similarly to the control link and is transmitted with the same power level, so it should have essentially similar range, and the conservative alarms for the control link described above should ensure the telemetry link is always available.

However, it is possible that for any reason (manufacturing tolerances resulting in slightly different range of the up and down links, local interference sources in close proximity to the radio,...) the telemetry link is lost prematurely, in which case a warning is essential as you need to be aware that any telemetry-based alarms will NOT sound anymore.

Obviously, if the radio can't pick up the RSSI info from the receiver it won't be able to warn you about low RSSI.

Similarly, if you are relying on information from an onboard voltage or current sensor to know when to land, the alarms you set for this won't sound if telemetry data is unavailable.

So be aware of the "Telemetry lost" audio alert and act accordingly, whether by falling back to other sources of info or by turning back to land and investigate the reason for the loss of telemetry feed.

Note that when the radio and receiver are very close to each other (usually <1m) you may get spurious "telemetry lost" and "telemetry recovered" alarms. 

This is not a malfunction and will stop when the 2 devices are separated.

The rest of the telemetry subject in itself has mostly been covered already.

The telemetry settings page allows you to configure the different parameters that have been explained in the menu overviews. 

The telemetry views will show the data as configured. If you have a microSD card in your radio, you can use the "SD Logs" custom function to record the telemetry data while in flight.

It can then be played back in OpenTX companion or opened in spreadsheet programs.

## Audio

One of the major features of the radio is the speech output function. Provided a microSD card (FAT12/16/32 format) loaded with the sound pack available for download from within OpenTX companion is inserted in the slot in the battery compartment, the radio will be able to play audio files in response to various events like reaching trim center/ends and activation of a switch (physical or custom), to play a background music file, and last but not least to announce every available value (telemetry, parameter, stick position) in clear voice. Custom sounds can be placed in the SOUNDS/(selected_language) folder of the card and will be available for use (name must be 8 characters at most, not counting the .wav extension, and with no special characters). Language is set in the radio general settings and can be changed on the fly as long as the pack for that language is loaded on the card.
ZIP files with the standard voice packs can be downloaded from within OpenTX companion, or here. Extract the ZIP file to the root of the SD card, and it will create the necessary subdirectories (e.g. SOUNDS/en for the English pack). If you wish to create your own files, the required format is:
WAV, 8 or 16 bit, Mono
8, 16 or 32kHz sample rate
PCM, u-law or a-law compression
The stock sounds above use the best available quality, i.e. 16bit, 32kHz and PCM.
Audio operation is relatively simple as it only consists of 5 "and a half" Custom Functions:
Play Track: Just play an audio file from the SD card when the associated switch is active. A repeat option is available, when set the sound will repeat at the set interval as long as the switch is active. This can be used to announce flight modes, gear position, flap position etc when the associated switch is activated or on request.
Play Value: Say the value of the selected parameter when the switch is active. The repeat parameter is available too.
BgMusic: Starts playback of a background music track (that can of course also be a timed flight program announcement). The switch must stay on in order to continue playback.
BgMusic ||: This pauses the background track while active, and resumes playback when deactivated. The BgMusic switch must stay active the whole time or the track will start from the beginning again.
Vario: Reproduces the sound of a glider variometer using the altitude or Vertical speed telemetry data.
Volume: Adjusts the audio volume for the entire radio to the value of an input, e.g. a pot.
The following example shows a few Custom Functions set to announce what switches activate when they are, as well as SHdown triggering playback of the value of Timer 2 followed by the consumption (mAh count obtained from an FrSky FAS-100 current sensor onboard).

In addition to the sounds played by custom functions, there are a few predefined sounds that will be played automatically when an event happens if an appropriately named file is placed in the right folder.
Currently the following events are supported:
Flight Mode Change:
When flight mode is activated, file /SOUNDS/(selected_language)/modelname/flightmodename-ON.wav is played if present
When flight mode is deactivated, file /SOUNDS/(selected_language)/modelname/flightmodename-OFF.wav is played if present.
The "modelname" and "flightmodename" folder should be identical (including case) to your model's name and flight mode name respectively, with spaces replaced by underscores. Of course only the files you want and place on the card will be played, if something doesn't interest you then just don't put a file for it.

## Global variables

We have already mentioned how global variables could be used to group multiple adjustments in one place, and to make that adjustment flight mode specific. It was also noted that these could be adjusted in flight - this is done using the Adjust GVx custom functions. Any time the custom function's switch is ON, the value of the global variable will follow the selected input. As a reminder, there are 4 groups of inputs that can be switched between by pressing ENTER LONG on the input field, and don't forget to tick the safety box once you're done configuring and you've made sure the switch is off - again to avoid overwriting your GVAR by mistake while scrolling the source list.
This is the way to adjust values in flight. The custom function's switch serves as a "lock" to freeze the value or allow adjustment. When a variable is being updated, a popup with the variable name and new value will show up on the main views.
One of the available sources for adjusting global vars is the list of channels. This is probably the main way you'll use to adjust GVARs for a simple reason: Let's say you want to adjust a D/R ratio with the S1 pot. If you select GV1 as the weight parameter of that rate line and just use the Adjust GV1 custom function with S1 as source, you will now be adjusting your rate between -100% and +100%. Being able to disable and even reverse your rate doesn't sound terribly fun, so you'll want to limit the adjustment range. The easiest way is to use a free channel for that. Create a mixer line on say CH12, and use the weight/offset/curve parameters to make that channel's output cover a range of say +50 to +80% over the pot's throw. Then, set the Adjust GV1 source to CH12.
A few interaction examples

The power of the system now comes from the combination of the different features. Custom switches can be used to create conditions that will trigger audio playback, for example using custom switch "CS1|d|>x Alt 10" as trigger for "Play Value Alt" would result in the altitude being announced every time it has changed by 10m/ft. "CS2 a<x Spd 35" triggering "Play Track lowspd" would play the lowspd.wav file on the SD card, that could be recorded to say "Low Speed" when GPS speed got under 35km/h. If you have several parameters you want to have announced sequentially on request, you could set several Play Value Custom Functions all triggered by the SHdown momentary switch as shown above. A press of this switch will then trigger playback of all the parameters one after the other.
But as we know that custom switches can be used anywhere a switch is definable, nothing prevents you from reusing that same CS2 to trigger automatic flaps deployment once speed got below 35km/h. That's right, anything can be used to affect anything.

