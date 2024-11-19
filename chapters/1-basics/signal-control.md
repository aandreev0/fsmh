# Making devices talk to each other

Microscopes are complex electro-mechanical systems and parts need to communicate with each other.

Cameras, stages, light sources, and other devices need to be activated or switched from one mode to another at an appropriate time, for example to achieve multi-color imaging or time-locked stimulation for animal experiments.

Devices usually can receive and send signals using voltage levels: for example, if out voltage is 5V it considered "HIGH" or "1".

## Voltage levels and TTL

## Receiving signals from devices
- Impedance and current sinking/sourcing
- Logic levels and tolerances

## Creating simple logic
- when X, do Y
- counting frames
- driving LEDs

## Implementation with Arduino and NI DAQ
- 5V Logic: in and out
- Interrupts
- Digital-to-analog converters

## Arduino as glue to talk with PC
- Serial port communications
