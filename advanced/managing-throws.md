# Managing Throws

There are two main things to consider when managing throws for a particular control surface.

They are:

* How far can the control surface physically travel?
* How far do you want it to travel?

There are several choices that can be made to resolve these issues:

* Use the [Outputs](/outputs.md) screen to **limit** what is output by the radio.
* Use a [Curve](/curves.md) in the [Inputs](/inputs.md) screen.
* Use a [Curve](/curves.md) in the [Mixer](/mixer.md) screen.

## Using Outputs to limit travel

Using the Outputs screen is the simplest and most direct way to limit actual travel of the control surface.

For example, if you only want the aileron to travel a maximum of 50% and have the stick be able to travel the entire distance of its physical movement, just change the Min and Max numbers to 50.

![](/assets/Outputs-50.png)

There is no way to assign a switch to to this setting, however, and the limits will apply to all flight modes.

A good example for when you would use this method is that even though an elevator could physically travel a full inch, doing that would make the plane behave badly and out of control.  Setting output limits would reduce the possibility of the elavator traveling too far no matter what you put into the Inputs or Mixer screens.



## Using a Curve in the Inputs/Mixer screen

You can achieve the same results as above by setting up a linear "curve" that looks like this:

![](/assets/linear-50.png) 


Both of the above setups will produce something that will look something like this:

 ![](/assets/Ele-far-right.png)  ![](/assets/CM-Ail-50.png) 

 



