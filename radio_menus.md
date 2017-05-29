## Radio menus

A LONG press of the MENU key brings up the radio setup menu:

![](images/radio-setup.png)

* Date/Time: To be set, they serve as info but also to give a correct timestamp to files and logs saved by the radio.
* Battery range: range of the graphical radio battery meter on the main views. To be set accordingly with the battery type you use (2s lipo here).
* Sound settings: Mode, Master volume, individual volumes of all mixed sources (Beeps, sound files, variometer, background music), beep duration and pitch.
* Contrast: Screen contrast setting.
* Alarms -> Sound off: if "Sound Mode" is "Quiet", the radio will not even sound warnings like a low battery. This alarm will remind you of that when turning the radio on.
* Inactivity alarm will remind you if you have forgotten to turn the radio off.
* Backlight -> Mode: If set to Keys, Controls or Both, the backlight will turn on when a stick/switch is moved and/or a key is pressed, for the duration set below.
* Backlight -> Alarm: Backlight will flash when an alarm sounds.
* Splash screen: On Taranis the splash will always be shown as the memory takes some time to load. Setting this on will just show it for longer.
* GPS time zone is there to show you the correct time when a GPS is present, and coordinate format lets you adjust display format to your liking.
* Country code: Must match your geographical location to keep RF transmission parameters within regulatory requirements.
* Voice language: Allows you to choose the language of the voice announcements. Note that the list contains all supported languages, but you also need to ensure a voice pack for that language has been loaded onto the SD card (in a subfolder of the SOUNDS directory).
* Units: Allows choosing between metric and imperial units for telemetry values.
* FAI mode (if the "FAI choice" option is selected in OpenTX companion): Disables all telemetry displays other than RSSI and voltage to comply with contest regulations. This is one-way, i.e. when you turn it on with this menu option it can't be disabled anymore, you need to connect the radio to the PC and use OpenTX companion to turn it off again (to prevent cheating). This allows you to come to the field, do your checks / test flights with telemetry, and turn the restricted mode on before the beginning of the contest on the radio itself.
* Default channel order: Defines the order of the 4 default mixers that are inserted on channels 1-4 when creating a new model. Set this to your preference. They can of course always be moved later, this is just a time-saving option.
* Mode: This is your stick mode, e.g. Mode 1 for throttle and aileron on the right stick, Mode 2 for throttle and rudder on the left stick.
