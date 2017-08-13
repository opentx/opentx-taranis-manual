# Flight modes

Flight modes in OpenTX are simple compared to most radios.

A name \(displayed on the main views\), a switch to activate them, a trim setting and 2 fade in/out settings.

Yet they are very powerful, because the main settings are actually just located somewhere else: in the D/Rs and mixers.

Each of these has a flight mode selection list, that will determine in which one\(s\) they are active.

Most everything is controlled through dedicated mixers.

The mixers that are controlled by a flight mode will see their activation fade in/out according to the mode's settings.

As the trims can be made flight-mode specific \(they are by default\), using flight modes to activate things like gear or flaps allows using the separate set of trims to counter the extra drag that often causes an effect on pitch.

As a contrived example, here is what you might see on your Flight Modes page on the radio.

![](/assets/screenshot_x9d+_17-08-09_06-43-12.png)

The currently active Flight mode is FM0 \(the default\).

FM0 behaves a little differently because it always active unless a flight mode below it sets itself active via a switch.

The settings for FM1 are  as follows:

* There is no name \(10 characters are allowed\).  
* It will be active when Switch A is in the top position
* For the Rudder, it will add trims from Flight Mode 0 \(FM0 trims + FM1 trim\) 
* For the Elevator, it will only use trims set in Flight Mode 1
* For the Throttle, it will add the trims from Flight Mode 2
* For the Ailerons, it will disable the trims all together
* There is no Fade In
* There is no Fade out

If you set the switch to SA on FM1 and FM2, it will use FM1 settings.  This is the first one it encounters.





