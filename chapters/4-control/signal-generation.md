# How can we generate signals?


## Voltage levels and TTL

## Receiving signals from devices
- Impedance and current sinking/sourcing
- Logic levels and tolerances


# Implementation with Arduino

## Creating simple logic with Arduino
- when X, do Y
- counting frames
- driving LEDs

## Advanced details
- Interrupts
- Digital-to-analog converters
- Real-time data processing
- Serial port communications

# DAQ (NI DAQs)

More advanced technology for generating fast, predictable signals with option for feedback loops is using Data Acquisition (DAQ) platform such as National Instrument devices (currently "gold standard") or very similar Advantech iDAQ (at lower price point). Here we discuss several specific example of using DAQ for driving microscope operations.

# Function generators

Function generators are specialized devices that can output high-quality signals with high sampling frequency but only specific waveform. While DAQ device can produce any arbitrary shape of signal, e.g. squared sine wave multiplied by triangle wave of different frequency, function generators offer limited variety of output functions. As commonly happens, the tradeoff is speed vs customization.

You can buy 30MHz two-channel function generator for $300, while multi-functional DAQ with 2 analog output channels and 2MHz sampling rate can cost more than $2000.

Using two- or four-channel generators allows synchronization of signals and phase offset, e.g. if you want one signals to be precisely 0.15ms ahead of another signal.

# Sensors: temperature, humidity, flow
