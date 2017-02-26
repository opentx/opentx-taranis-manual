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

A few interaction examples

The power of the system now comes from the combination of the different features.

Logical switches can be used to create conditions that will trigger audio playback.

**Two examples:**

Using logical switch "LS1\|d\|&gt;x Alt 10" as trigger for "Play Value Alt" would result in the altitude being announced every time it has changed by 10m/ft.

Using logical switch "LS2 a &lt; x Spd 35" triggering "Play Track lowspd" would play the lowspd.wav file on the SD card, that could be recorded to say "Low Speed" when GPS speed got under 35km/h.

If you have several parameters you want to have announced sequentially on request, you could set several Play Value Special Functions all triggered by the SHdown momentary switch as shown above.

A press of this switch will then trigger playback of all the parameters one after the other.

But as we know that logical switches can be used anywhere a switch is definable, nothing prevents you from reusing that same LS2 to trigger automatic flaps deployment once speed got below 35km/h.

That's right, anything can be used to affect anything.



