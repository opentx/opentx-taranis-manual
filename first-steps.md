# First steps. Setting up a model

Now that you've seen the basics and that your battery has some charge, what about a little bit of practice?

The radio comes from the factory with the sticks already calibrated, so the first thing to do with your radio is to configure the general settings.

From the main view go to the [Radio Menu](radio_menus.md) (MENU LONG) and set the time, date, sound volumes to your preference (the lower end of the volume slider is typically needed when using headphones, while the upper end is good for using with the internal speaker). 

You may also want to play with the backlight setting, set the RF country code to your location, the default channel order to your preference, and the stick mode to match your flying style.

Battery gauge and alarm are factory set for the supplied battery.

##Binding

The radio will have created an empty model for you, so after having gone back to the main view you'll be able to go to the [Model Setup](model_setup.md) (MENU SHORT then PAGE SHORT). 

Set the RF mode to match the receiver you want to use. 

###Internal module

When using the internal module to bind your receiver select the "Bind" field and press the ENTER key. 

The radio will beep every few seconds. 

Now follow your receiver's instructions for binding (press and hold the F/S button then apply power for D and X receivers, connect jumper to S pins of channels 1 and 2 and apply power for V8x-II receivers). 

The receiver LED will flash fast to confirm binding. 

Press exit on the radio, Remove the jumper on the receiver if applicable, and cycle receiver power. 

You should now have servo control of channels 1-4 with the sticks.

###External module

Ensure you have turned off the internal module and select the correct mode RF for your module.

For XJT and DSM module follow binding instructions for internal module.

For PPM follow instructions provided by the module manufacturer.

## OpenTX basics

Now that everything works, it's time to stop a moment for some theory about the basic usage of the OpenTX firmware.

As briefly described above, OpenTX differs from the majority of mainstream radios by its programming philosophy. Owners of Multiplex radios will however feel at home very quickly, as the principles are very similar. 

Most commercial transmitters offer a choice between a limited set of predefined usage scenarios (airplane, glider, helicopter), a number of functions that are commonly used with such models (delta, flaperon, camber, butterfly...), and have fixed assignments sticks always control their respective channels).

OpenTX offers a blank canvas on which you will build your setup: the [mixer screen](mixer.md). 

This approach ensures maximum flexibility because whatever you do, you will never have to work around what the radio expects you to do, which is a blessing for anybody having to work with "new" model types or configurations which still "don't exist" for mainstream radio manufacturers, and as such for which the built-in functions are usually useless. 

So you can see it that way: For some model types, usual predefined functions can allow setting up a model in seconds (just enable a function), but for others you'll spend hours trying to get around their limitations. 

On OpenTX everybody is more or less at the same level - it might take a little longer at the beginning to set up a seemingly simple model, but a complicated one won't take much more. 

Since there is no existing function you can just turn on, it will require basic understanding of how your model is supposed to work, and what you want each control surface to do. 

This means that you might even learn something about your model while setting it up!

The control order path starts from the hardware controls, goes through the [INPUTS](inputs.md) screen (anything affecting control response like dual rates and exponential), continues to the [Mixer](mixer.md), and ends up being adapted to the mechanical characteristics of the model in the [OUTPUTS](outputs.md) screen.

## Everything about the mixer screen

We'll start with the mixer as it is the center of the radio. 

The mixer screen lists the 32 output channels to which you can link one or more inputs from a long list of physical controls (sticks, pots, trims, switches), logic sources, other channels and trainer inputs. 

Each assignment is implemented with a mixer line. A new model will have 4 predefined mixer lines on channels 1,2,3 and 4 that link to the 4 sticks according to the channel order preference you have set. These are there purely for convenience, and can of course be edited or deleted.

Let's delete them all by highlighting them, pressing ENTER LONG and choosing "Delete". Your mixer screen is now empty, which means the radio does nothing at all. 

Well the radio does do something. The radio sends out the number of channels that are defined on the model setup page to the receiver (channels 1-8 by default), but as those channels are empty in the mixer screen no servo will respond, they'll all be centered. 

You won't go very far with that, so you'll want to add control inputs to those channels. You'll create a mixer line on CH1 by highlighting it and pressing ENTER LONG, and will end up in the EDIT MIX page. 

Scroll to the "Source" field, press ENTER, and select the control you want to act on CH1. You can do it by browsing the list with the + and - keys, or take the easy route and just move the desired control (if it's a physical one, of course). 

Move the aileron stick, and the field will change to Ail (it might have already been there if your channel order preference set in the general settings had A for the first channel, as that's taken into account). 

You can leave the other parameters at their default settings, which means:
* The mix ratio of this input is 100%, so the scaling of the mixer line's output will be equal to its input. A value of -50% would mean the output would be half of the input and inverted.
* There is no offset, so with an input of 0 the output of the mixer line will also be 0. A value here would shift the response by that much percentage of (input x weight).
* Trim is ON, it could instead be excluded from the calculation (OFF), or one of the other trims could be used (for cross-trimming for example). D/R and expo (the entries on the OUTPUTS screen for that channel) are used. Unticking the box would mean the mix receives the raw stick input even if a D/R is active.
* Differential is 0, so the mixer output will be symmetrical on both sides. A value of 20% would mean the line's output would be 20% less on the negative side than on the positive one. The "Diff" field is editable, and by using the +/- keys on it you'll be able to select a curve instead (predefined or custom).
* The mixer line is active for all flight modes. By "unticking" some of the numbers, you would disable that line whenever the corresponding flight mode is selected.
* No switch is assigned to the line, so it's always active (as long as the flight modes setting above allows it). Selecting a switch (physical or logical) would allow activating or deactivating the line when needed.
* Warning is off. If set to 1,2 or 3 the radio would emit 1,2 or 3 short beeps every few seconds to let you know that line is active.
* Multiplex is Add, so this line is just added to the previous ones on the same channel. If set to multiply it would multiply the calculated result of the lines above it, and if set to replace it would replace anything that's above it whenever it's active.
* Delays are 0, so if that line had a switch assigned it would be activated/deactivated instantly when the switch is toggled. Time is in seconds.
* There is no slowing down, so the line's output reacts instantly to input changes. Times set here are expressed in seconds to cover the entire range (-100 to +100). If 2 seconds are selected, the line's output will take 0.5 second to gradually sweep from 0 to +50% if the input was moved by that much or the mixer line was activated/deactivated by a switch.
* You can also name the mixer line. This name is shown on the main mixer screen, so setting names is a good idea to help maintain complex setups where you might have many lines on each channel.

Note that at any time in the Mixer screen and the EDIT/INSERT MIX dialogs you can press MENU LONG to bring up the channel monitor. This makes it easy to try the different parameters and see their effect on the channel's output. 

In addition to this, you will see that on the mixer screen each active line has its name and source displayed in bold, so it's always clear at any given time as to which lines are actively contributing to the channel output.

The description is long, but in practice if we now do it again to control CH2 with the elevator stick it will only take a couple of seconds to select CH2, press ENTER LONG, scroll to Source, press ENTER, move the Elevator stick, and press EXIT twice. 

Setting up the mixer for a vast number of basic models is as simple as that. 

###Flaps example

In addition to the 4 basic channels, let's say that you want to configure a model with flaps.  Assuming the flaps are on their own servo and you want to control it with switch SB, just find a free channel to connect your servo to (let's say CH6).

Scroll to CH6 on the mixer screen, insert a mixer line, flip the SB switch when in edit mode on the source field, and EXIT twice. 

If you want to adjust the up/mid/full positions, a good idea would be to set up a 3-point custom curve. 

In the Curve setting, select c1, exit edit mode, and still on the curve field press MENU. You will be brought to the curve editor. Select "3pt" as type, select the Y value of the first point, and adjust its position. 

Do the same for the other 2 points, and exit.

###Retracts example

Now something more "complicated". 

As an example, if your model has retracts, it only needs two postions, Gear UP and Gear DOWN.  Most switches have three positions that provide -100%, 0%, and +100%, respectively.

You can change this three position behavior by using the very convenient MAX source, that represents a fixed value. 

Create a mixer line on a channel (e.g. CH5) with MAX as source and +100% weight, you could name it "Gear Up". 

Now create a 2nd mixer line under the first one by pressing ENTER LONG on it and selecting "Insert After". Choose MAX again as source.  By default the val for the weight defaults to 100.  Since we want this to be -100, we can use a handy shortcut - Highlight the weight number, press ENT to enter edit mode, and then press the + and - keys together. 

There, -100%. 

Scroll to the "Multpx" setting, and select "Replace". 

Now go to the switch setting, enter edit mode, flip SA in the UP position (flick it out of it first if it's already there), and press the + and - keys together. This will turn the "SAup" entry into "!SAup". 

This means the line is active whenever SA is NOT in the UP position. Name the line as "Gear Down" and you're done.  What happens is: CH5 will be at 100% by default (the first mixer line is in effect), BUT when SA is either in the middle or in the down position the 2nd line will activate and replace the first one, turning the output to -100%. 

If you go back to the mixer screen and play with SA switch, you'll see that when it's in the down or middle position the 2nd line will turn bold as it becomes active.  The first line fades back to normal as it has been deactivated because the Multplx of the second line is set to Replace.

Again that seems long, but takes as much as about 30 seconds when you're used to it.

It is easy to see that we could have set the second line to use switch "SAup", and that subsequently the role of the 2 lines would be swapped (second active when switch is up, first in the other 2 positions). 

But then I wouldn't have had the opportunity to explain the !, and also as a personal preference I like my switch default positions to be UP, and the first mixer line on a channel to be the default value.

###Dual Airleron Example
A little simple one next: You have 2 ailerons with separate servos. Using a Y-cable to link them is too old-school nowadays, so let's use another channel. 

We already have the first aileron on CH1, CH5 and 6 are taken by gear and flaps, so let's use CH7. 

We have an aileron that must move with the aileron stick, which is actually just like the first one. 

So let's just copy the first mixer by highlighting it and pressing ENTER LONG, and selecting copy. 

Move it to CH7 and press ENTER. 

This would work just fine, but I'll throw in a personal preference again, and change its weight to -100% because "logically" that aileron is supposed to move in the opposite direction. 

We'll see later why this makes sense.

### Delta mix example

Let's do a delta mix. 

As always, ask yourself, what kind of control surfaces do we have, and what do we want them to do?

We have 2 elevons.

They must move in the same direction when the elevator stick is moved, but they must move in opposite directions when the aileron stick is moved.

So, let's pick 2 channels to connect our servos to. CH3 and 7, because... why not. Trying to make you forget about old school fixed channel assignments here ;)

CH3 must move with the elevator stick, so we create a mixer line with Ele as source on it. 

CH3 must also move with the aileron stick, so we create a 2nd mixer line with Ail as source. We leave multiplexing set to "Add", as that's exactly what we want to do - the 2 inputs must be added together.

Now let's discuss the weights a little. They are now set to 100%. This means that a full deflection of the aileron stick will create a full deflection of CH3, same for the elevator stick. But now as we add the 2 together, if we put the stick in the upper right corner (assuming mode 2) we have 100% + 100% = 200% output on CH3. 
Now, the limits defined on the OUTPUTS screen are set to 100% - which means that the output will be clipped. 

When the mixer's output for a channel goes beyond 100%, the servo won't move any further. 

This is not different from other radios - predefined delta mixes will usually give you ratios to enter for elevator and aileron authority, which is just the same. If you enter too high ratios some of the stick throw will be ineffective.

Now the discussion as to what to set the ratios to is probably endless - some are happy with 100% and clipping, some will like 50% so that there is never any clipping, and some like myself will like something a bit in the middle - I use 70%.

So, let's say we now have 2 mixer lines on CH3, 70% Ail and 70% Ele. 

As we said, CH7 must respond the same way to the elevator input, so we add a 70% Ele mixer too. 

It must respond to the aileron stick by the same amount, but in the opposite direction, so we'll set... -70%.

This is the reason for which I set -100% in the previous dual aileron example. Forcing yourself to enforce that logic thinking even when not really necessary will help you to get it right when it's needed. 

For example in the dual aileron scenario we could have set both ailerons to 100%, then used servo reverse to invert one aileron to achieve the same result on the model. BUT in the delta scenario this wouldn't work.

## OUTPUTS screen

Now that the mixer is configured and the controls' behaviors are defined, the next step is to set up the way these orders will be carried through to the servos. 

At this point you'll want to actually connect your servos to your receiver, remove the control horns from the servos, the props from the motors (safety first), and connect a receiver battery. 

Bind the receiver if not done yet.

Center all controls (you can look at the channel monitor and aim for 0), and for each servo start by mounting the horns so that they're as close to perpendicular to the control linkage they're going to drive as possible. 

Murphy's law ensures that it's always right between 2 of the steps, so use the PPM center adjustment to make them perfectly perpendicular. 

Using this setting instead of subtrim avoids losing throw, and makes sure the outputs seen in the channel monitor are real "control" inputs. 

Connect your linkages so that the control surfaces are at neutral (or middle of their expected throw for things such as flaps).

Now move the radio's controls carefully to exercise the servos but being aware of possible mechanical binding. 

Set servo reverse where needed. 

Adjust the linkages in order to have a little more throw than what you'll ever need in both directions. 

If there is a little binding on one side to reach the appropriate side on the other and/or the throws are not symmetrical it's not a problem.

Adjust min and max limits so that:
* You have a little bit more throw than what you'll ever need
* There is no mechanical binding
* Throws are the same on both sides with full control input deflection

We're done for this screen. You've already named your channels of course ;)

## Inputs screen (Dual Rates/Expo)

You've probably noticed there's one thing we haven't done yet - adjust throws. That's what we'll do now.

For each stick, create a rate line. 

Set the weight to achieve the desired throws. Add expo if desired. This is your default rate, so don't choose a switch.

If you want multiple rates, create a new line before the default one, enter the new rate/expo, choose a switch. 

Repeat as many times as desired. 

What's important to know is that the first line that has its switch on (starting from the top) will be the active one. 

So if you create rates below one with no switch - it will never be active. 

Think about the priority if you choose switch combinations that can lead to 2 rates having their switch on - the top one will override the other. 

Ideally you should choose your switches so that never happens.

There, we can go and fly!

##Model setup guidelines

Time for a little summary. 

As we've seen, there's literally an infinite number of ways to do the same thing in the firmware, so let's mention a few good practices when setting up models. 

If you stick to them they will help you set up your model quicker, keep your setup clean, and understand what you did 6 months later. 
With a simple 4-channel model where each servo is controlled by only one control input, if you want to reduce aileron throw you could do it either with the aileron D/R, in the weight of the mixer line linking the Aileron stick to the aileron channel, and with the Limits for that channel. 

For such a simple model it won't matter much where you do it, but as soon as you'll get to more complicated models with flaperons, butterfly mixes etc, doing it in the limits for example would simply make it impossible to set up the model properly.

Start with the mixer setup. 

As we did above, think about what controls you have on your model and what they should do, and choose which receiver channel you want to use for each of them. 

On each of those channels, create one mixer line for each of the transmitter controls that should act on it. 

Figure out the relative amount of movement each of those must lead to, based on 100%. 

Forget about throws for now, if one control must have half the authority of the other set one to 100% and one to 50%. 

Keep the mixer dedicated ONLY to the "logical" part of the setup. 

If for example for complex gliders you have more than one control surface that needs to receive the same group of mixers, isolate those as a "Function" on a free "virtual" channel you know you won't use it for a servo, e.g. CH10. 

Then reference it in the required output channels with a 100% CH10 mixer line. 

This will save mixer lines and add to clarity. 

Name your channels and mixes that aren't self-explanatory.

Set the servo parameters. 

Take good care of the mechanical setup, the better it is the easier the radio setup and the more precise your controls will be. If you need to use subtrim to artificially shift a control (for example in case of flaperons that need a far greater throw on the low side than on the high side), remember to use the "=" output mode to keep symmetry.

Always define control throws using the INPUTS screen.

Now the throws are adjusted, the mixer is set for good logic and the outputs are set for good mechanical fit. 

As every part of the setup is clearly separated, should you need to change something any adjustment will only require intervention on one of the screens. 

If you crash or change something mechanically, it will be the OUTPUTS screen. 

If your throws are too big, OUTPUTS screen. 

If a compensation amount or mixing ratio is wrong, mixer screen.

Remember that there are custom switches that can be set to combine various functions, for example allow activation of some mixers only if another one is active, etc.

It is also good practice to make use of the "Safety CHx" custom function to define a safety switch for the throttle channel of electric models. 

Select your throttle lock switch, select the correct function for your throttle channel, set the value to -100, then tick the box. 

While you should always set up your model without it being powered, or at least without a prop mounted, the safety box is there to OU forcing the channel to the default value of 0 (mid throttle) while browsing the function list if your switch is active.

The "Instant Trim" custom function can be used if you expect your model could be badly out of trim on the first flight, see the [Special Functions](special_functions.md) section for a full description.

Once the flight is over, the "Trims -> Subtrims" function at the bottom of the OUTPUS page can be used to transfer the trim contents into the subtrim settings. 

Be aware that unless the servo mode is set to "=" an excessive subtrim amount can lead to dissymmetric throws and influences settings like differential.

