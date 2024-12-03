# How can we generate signals?


## Voltage levels and TTL

## Receiving signals from devices
- Impedance and current sinking/sourcing
- Logic levels and tolerances


# Implementation with Arduino

## Creating simple logic with Arduino

- counting frames
- when X, do Y
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

You can buy 30MHz two-channel function generator for \$300, while multi-functional DAQ with 2 analog output channels and 2MHz sampling rate can cost more than \$2000.

Using two- or four-channel generators allows synchronization of signals and phase offset, e.g. if you want one signals to be precisely 0.15ms ahead of another signal.

For example, [here author](https://arxiv.org/abs/1211.0578) is using 2-ch function generator to drive piezo (sine wave) and strobing LED (square pulses) with slightly different frequency to analyze resonant frequency of piezo actuator:

```{figure} ../../static/two-channel-function-generator.png
:alt: example output of a 2-ch function generator
:width: 250px
:align: center
```

# Sensors: temperature, humidity, flow

When running experiments we often need to record additional information such as temperature, light level, or humidity. Some external devices offer logging capabilities, but it might be also useful to construct custom device to record such data directly from the sensor. For example, [Arduino can be used](https://www.biorxiv.org/content/10.1101/2021.05.18.444705v1) to log (as well as control) temperature.

In such case the simple setup looks like this:
1. sensor reports data to Arduino, for example digital [DS18b20 sensor](https://www.adafruit.com/product/381) can report temperature through "1-wire" protocol
1. Arduino sends the data via serial port to python script running on PC
1. script writes the data in text file appending timestamp information

Off-the-self devices such as [Thorlabs USB temperature logger](https://www.thorlabs.com/thorproduct.cfm?partnumber=TSP01) provide similar capability without any tinkering but at ~3x price
