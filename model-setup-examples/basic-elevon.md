## Basic Elevon

Elevons are control surfaces that combine the functions of the elevator and the aileron.

You usually see this sort of configuration on tailless aircraft.

A good example of this is an aircraft known asa "flying wing".

![](/assets/flying-wing.jpg)

As you can see from the picture above, the airleron and elevator surfaces reside in the same physical control surface.

For this to work, you have to create a "mix" so that this can be accomplished.  Here is what basic elevon set up might look like on your radio, we are using the default AETR output.

[![](/assets/elevon-inputs.png)](/inputs.md)

[![](/assets/elevon-mixer.png)](/mixer.md)

In this example, the [exponential](/curves.md) on the Aileron and Elevator inputs are set to 60%.   This is not a required setting.

Additionally, the negatives values were required for this particular plane, you may not need to use the negative values for the Ailerons as shown here.

For the Elevator setting, you will need to have them be opposite as shown here.

To set up this particular plane, you would need to plug the left control surface into the Aileron port of the receiver \(Channel 1\) and the right surface into the Elevator port of the receiver \(Channel 2\).

When you apply up Elevator, both physical control surfaces should move in unison upward, as you might expect.

Similarly with the Ailerons, left stick should push the left surface up and the right surface down.

Because of servo orientation, receiver used, and other factors, you may need to change the values on the mixer lines to a positive value \(100\) or to use the reverse function in the [OUTPUTS](/outputs.md) screen.

