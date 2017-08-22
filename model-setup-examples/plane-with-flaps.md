# Plane with Flaps - One Servo

There are many ways to implement flaps on a plane.  The simplest being selecting a slider to directly control the placement of the flaps.

In this example, several different ways were implemented to accomplish similar ends.

Both flaps are controlled by one servo.

The Flap servo is assigned to the the Flap input, shown below, which is driven by switch SC.

![](/assets/Flaps-inputs.png)

![](/assets/Flaps-mixer.png)

The mixer screen has several different additional options selected.  In addition to controlling the flaps, the elevator is adjusted as the flaps deploy so the plane does not balloon up.

The adjustments for Curve 2 and Curve 3 will be specific for your plane.  The curves below are just an example of possible settings.

As the flap is fully deployed the elevator is slightly adjusted down by the amounts shown in Curve 2 below.

Curve 2

![](/assets/Flaps-cv2.png)



Curve 3 controls the amount of the flap that deploys  as the switch is moved through the three positions.

Curve 3

![](/assets/Flaps-cv3.png)



Channel 2 is set to slow the deployment of the additional elevator to take three seconds.

Settings for Channel 2

![](/assets/mixer-ch2-1.png)

![](/assets/mixer-ch2-2.png)



Channel 5 is set to slow the deployment of the flaps to take four seconds and to retract in two seconds.  In other words, it deploys slower than it retracts.

Settings for Channel 5

![](/assets/mixer-ch5-1.png)

![](/assets/mixer-ch5-2.png)









