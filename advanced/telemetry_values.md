# Telemetry Values

The following assumes your radio has a micro-SD card and a valid voice pack.  The micro-SD card is included with the Taranis radio.

Probably the most important telemetry value is RSSI.  It is an indication of how strong the signal from the receiver is being seen from the radio.

The radio will warn you in advance if you are at risk of losing control.  Some possibilities are external interference, excessive distance, badly oriented or damaged antennas.

The telemetry settings page gives you 2 alarm levels you can set.  Each of the entries will announced in clear voice ("RF signal low" and "RF signal critical")

They are set by default to levels that are suitable and safe for normal line of sight flight (45 and 42).

If you want to adjust them yourself the following explanations will be useful.

RSSI on FrSky equipment is represented using a logarithmic scale (dB), not using percentage. 

This means that when RSSI is high, a small difference in the distance between the transmitter and receiver will lead to a big change of the RSSI value.

It is perfectly normal to see a value of about 100 when next to the model, and down in the 70's by the time you've walked to the other end of the field.

When you have a reading of 50, it will, however, take a lot of extra distance to reach the alarm level of 45. 

The basic approximation rule is that a doubling of distance between pilot and model, will result in a drop of 6dB of the RSSI value.  Hopefully this makes the previous explanation clear.

If you are 5m away from the model, it only takes another 5m to reduce RSSI by 6dB.  If you are 600m away from the model it will then take another 600m to reduce the value by the "same" 6dB.

Loss of control will happen when RSSI reaches a value of about 38, so setting an alarm at 10 is useless.

From the above explanation, you can see that between the default critical alarm (42) and usual practical loss of control we have a margin of about 4dB.  This is a range factor of around 1.5.

The alarms are thus rather conservative, and in normal conditions, even if you heard the critical alarm, you would still be far from losing control.  When the critical alarm sounds you should be at around 1000m distance, with another 500m to spare.

At this distance intermittent loss could get more and more frequent due to local fades and antenna orientation mismatches.

As mentioned earlier, the default alarms are safe for usual line of sight flight.

However, with FPV setups, especially when coupled with automatic return to home systems and properly configured failsafes, the safety margin can be reduced and you should be able to extract more or less double of the standard range out of the system.

It is up to you to experiment safely.

Once the margin gets reduced, influence of external interference sources will start to become more noticeable.

It is practically impossible to predict the behavior of a given installation in a particular model.

The Taranis also has an alarm that will warn you of the telemetry down-link is lost or recovered.

The telemetry link behaves similarly to the control link. It is transmitted with the same power level, so it should have a similar range.  The conservative alarms for the control link, as described above, should ensure the telemetry link is always available.

However, it is possible that for any reason (manufacturing tolerances resulting in slightly different range of the up and down links, local interference sources in close proximity to the radio,...) the telemetry link is lost prematurely, in which case a warning is essential as you need to be aware that any telemetry-based alarms will NOT sound anymore.

It makes sense that if the radio can't pick up the RSSI info from the receiver it won't be able to warn you about low RSSI.

Similarly, if you are relying on information from an onboard voltage or current sensor to know when to land, the alarms you set for this won't sound if telemetry data is unavailable.

It is important to be aware of the "Telemetry lost" audio alert and act accordingly.  Fall back to other sources of info or by turning back to land and investigate the reason for the loss of telemetry feed.

It is possible to receive spurious "telemetry lost" and "telemetry recovered" messages when the transmitter and receiver are less than a meter apart.

This is not a malfunction and will stop when the 2 devices are physically separated.

The rest of the telemetry subject in itself has already been covered.

The telemetry views will show the data as configured.  If you have a micro-SD card in your radio, you can use the "SD Logs" special function to record the telemetry data while in flight.

You can then play it back in OpenTX companion or opened in spreadsheet programs.