# Frequently asked Questions (FAQ)

This section explains some questions that come up over and over again.

## USB-C port on the Frsky X10 and X10s

__The USB-C port on the X10/X10s has a serious design flaw. Do not use
it for anything other than charging with the supplied charger__

USB-C has been designed to make it safe to plug arbitrary devices
together without having to fear damaging any device this way. This
done by mainly two main things that devices with an USB-C port *must*
comply with. Firstly, never switch on power unless being signalled to
do so and second *never* output anything other than 5V unless the
devices agree with the USB-PD protocol and only by use of the USB-PD
protocol to a different voltage. The signalling of allowing 5V output
can also be by use of a legacy cable (e.g. USB-C to micro USB or USB-C
to USB-C socket adapter).

The FrSky X10 the USB-C is abused as connector for the Lipo
charger. It violates the both of the USB-C safeguards. Instead of
presenting only 5V when signalled to do so, the USB-C connector on the
X10/X10s directly connects to the battery and outputs battery voltage
(up to 8.4V for the default 2S Lipo) regardless of what the other
device is. As almost all USB devices are only specified and tested for
5V, connecting the X10/X10s to any other USB devices (via USB-C to
USB-C or USB-C to USB-A cable) has a good chance to permanently damage
the other device. The USB-C port also provides no USB functionality.

The (less common) mini USB connector on the X10 is fine and is the
only USB that can and should be used to connect the X10 to a PC.

## Flashing receivers does not work with the Taranis Q X7

Connecting and flashing receivers with newer Q X7 models is a bit
different from other transmitters see the
[S-PORT flashing](s-port_flashing.md) section for more details.

## Voltage on Frsky Radios external module output

Note that the voltage on the external RF module PPM output pin is
driven by the battery voltage on the FrSky radios. Especially for
SBUS, which is normally 3.3V, this is too high. However, the output is
current limited by a 10 kΩ resistor, which limits the current to
around 1mA. The input protection diodes of FC processors should be
handle the higher voltage at such a low current and connecting the
output directly to a flight controller should be relatively safe. But
it is still outside the specification and you are doing that on your
risk. If you want to be really safe use a voltage divider or a level
shifter.
      


## Two XJT modules, telemetry from internal and external module, Crossfire and internal module 

This is a bit more exotic question but comes up often enough so that
it needs a proper explanation why this problematic.

Smart.port (S.port for short) is a bus protocol that is used for
connecting sensors/flight controllers to receivers. When two devices
try to talk at the same time on the bus, the two signal interfere
which each other and the data is lost. This problem is solved by
having only one device on the bus that is the master. The receiver
will periodically ask each sensor to send new data and when the sensor
has its chance to send data no other sensor is allowed to talk.

On the Frsky radios the S.port pin between the internal and external
module is shared, they are electrically connected. Unlike the receiver
and its sensors there is no coordination between the two modules. That
means if both modules send telemetry at the same time, neither gets
through.

If you have little telemetry coming from both modules, you might be
lucky enough that most telemetry sending is not at the same time and
that most of the telemetry is send without errors. As soon as the
amount of telemetry increases the chances of errors increase. They
system might like it is working, giving you a false sense that
everything is okay.

Even binding a receiver without telemetry is not enough to stop a XJT
module from sending telemetry, as there some module status messages
that are constantly sent. The only way to ensure that no telemetry is
coming from an external XJT is though setting the DIP switches.

For the R9M module, enabling/disabling telemetry can be done by
software. OpenTX will automatically disable telemetry if internal
module is on too, to avoid these hard to detect errors.

The Crossfire module uses the sport pin not only for telemetry but
also for input. If the internal module also sends telemetry, the
communication to the Crossfire module is problematic.

OpenTX 2.2.1 and later allows you to see the telemetry receive error
statistics under the statistics view (where also other debug information are presented).
