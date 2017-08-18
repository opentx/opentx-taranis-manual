# Frequently asked Questions (FAQ)

This section explains some questions that come up over and over again.

## Flashing receivers does not work with the Taranis Q X7

Connecting and flashing receivers with newer Q X7 models is a bit
different from other transmitters see the
[S-PORT flashing](s-port_flashing.md) section for more details.


## Two XJT modules, telemetry from internal and external module, Crossfire and internal module 

This is a bit more exotic question but comes up often enough so that it needs a proper explaination why this problematic.

Smart.port for S.port for short is a bus protocol that is used for
connecting sensors/flight controllers to receivers. When two devices
try to talk at the same time on the bus, the two signal interfere
which each other and the data is lost. This problem is solved by
having only one device on the bus that is the master. The receiver
will periodically ask each sensor to send new data and when the sensor
has its chance to send data no other sensor is allowed to talk.

On the Frsky radios the S.port pin between the internal and external
module is shared, they are electrally conncted. Unlike the receiver
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
that are contantly sent. The only way to ensure that no telemetry is
coming from an external XJT is though setting the DIP switches.

For the R9M module, enabling/disabling telemetry can be done by
software. OpenTX will automatically disable telemetry if internal
module is on too, to avoid these harde to detect errors.

The Crossfire module uses the sport pin not only for telemetry but
also for input. If the internal module also sends telemetry, the
communication to the Crossfire module is problematic.

