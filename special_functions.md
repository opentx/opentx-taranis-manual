# Special Functions

This is the place where switches can be used to trigger special functions such as trainer mode, soundtrack playback, speech output of variables etc.

The first column selects the trigger, which can be any switch (physical or custom) or ON (always on). A LONG press of the ENTER key will switch to "toggle" mode (ending with t), i.e. the selected input will be turned on when the selected switch is activated, and will remain on until it is deactivated and reactivated again.
Scrolling through the list you will also find a few more options: One (triggers just once when loading a model or turning the radio on), SHdownS (short press of the momentary switch), SHdownL (long press of the momentary switch).

The available functions are:
* Safety CHx: When active, the output of CHx is forced to the selected value. A checkbox is there to enable the function, which you would typically do after ensuring the value is set correctly and the switch is off if your model is powered.
* Trainer, TrainerXXX: Enables trainer mode globally, and for individual functions. Unless a custom function is set for an individual function, turning the one set for Trainer automatically activates all 4 sticks.
* Instant trim: When activating the selected switch the current stick positions will be added to their respective trims. This is typically assigned to a momentary switch, and used on a maiden flight if you expect trims to be way off. Instead of frantically clicking the trim tabs, you would hold the sticks so that the model flies straight, and depress the switch once. It is best to remove that entry after the maiden flight, to avoid hitting it by mistake and bringing the model badly out of trim again.
* Play Sound: Play a simple tone from the available list.
* Reset: Resets the selected item (Timer 1, Timer 2, telemetry values, or all of those)
* Vario: Turns on variometer sounds (see Telemetry setup)
* Play track: Plays a sound file from the SD card, with repeats at the specified interval
* Play value: Speaks the current value of the selected parameter, with repeats at the specified interval
* SD Logs: Logs the telemetry values to SD card at the specified interval
* Volume: Adjusts sound volume using the selected source
* Backlight: Turns backlight on
* BgMusic, BgMusic || (pause): Plays a selected soundtrack from the SD card. The BgMusic Pause item pauses the track when activated and resumes it once inactive again, while switching BgMusic off stops the track completely.
* Adjust GVx: When active, sets the relevant global variable to the value of the specified source. The adjustment source can be one of 4 groups cycled through using a LONG press of the ENTER key:
A fixed value
A proportional control, or a channel with for example specified curve/weight/offset to limit the adjustment range
Another GVAR
+1/-1, to increment/decrement the GVAR with each activation.
A long press of the ENTER key on a custom function's label will bring up a popup menu that allows you to copy/paste/delete an entry for more convenient entry of similar settings.
