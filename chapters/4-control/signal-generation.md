# How can we generate signals?


## Voltage levels and TTL

## Receiving signals from devices
- Impedance and current sinking/sourcing
- Logic levels and tolerances


# Implementation with Arduino

## Creating simple logic with Arduino

- counting frames

If you want to provide stimuli at specific interval or specific frames of the acquisition, you can either pre-program serier of triggers to camera and stimuli apparatus; or you can count frames (using Exposure signal from camera) and perform stimulation trigger at specific counts, e.g. every 100 frames. This can be implemented using simple Arduino code for almost any imaging system that provides Exposure signal ([camera-based](https://www.vision-doctor.com/en/camera-technology-basics/trigger-functions.html) and point-scanning system as well, see example from [ScanImage software](https://docs.scanimage.org/Concepts/Volume+Imaging.html))

- when X, do Y
- driving LEDs

## Advanced details
- Interrupts

There are two main ways to detect incoming signal: continuous polling of the pin and using interrupts.

```C
// using polling:
void loop(void){
  if(digitalRead(pin) == HIGH){
    // do stuff
  }
}

// using interrupts:
void setup(void){
  pinMode(interruptPin, INPUT_PULLUP);
  attachInterrupt(digitalPinToInterrupt(interruptPin), isr, RISING)
}

void isr() {
  // do stuff
}


```

- Digital-to-analog converters
- Real-time data processing
- Serial port communications

# DAQ (NI DAQs)

More advanced technology for generating fast, predictable signals with option for feedback loops is using Data Acquisition (DAQ) platform such as National Instrument devices (currently "gold standard") or very similar Advantech iDAQ (at lower price point). Here we discuss several specific example of using DAQ for driving microscope operations.

# Function/Waveform generators

Function generators (waveform generators) are specialized devices that output high-quality signals with high sampling frequency but only specific waveform. While DAQ device can produce any arbitrary shape of signal, e.g. squared sine wave multiplied by triangle wave of different frequency, function generators offer limited variety of output functions. As it commonly happens, the tradeoff is speed vs customization.

You can buy 30MHz two-channel function generator for \$300, while multi-functional DAQ with 2 analog output channels and 2MHz sampling rate can cost more than \$2000. There are stand-alone waveform generators as well as cards that need PC-based programming (same as DAQs).

Using two- or four-channel generators allows synchronization of signals and phase offset, e.g. if you want one signals to be precisely 0.15ms ahead of another signal or with a precise frequency difference.

For example, [here author](https://arxiv.org/abs/1211.0578) is using 2-ch function generator to drive piezo (sine wave) and strobing LED (square pulses) with slightly different frequency to analyze resonant frequency of piezo actuator:

```{figure} ../../static/two-channel-function-generator.png
:alt: example output of a 2-ch function generator
:width: 250px
:align: center
```

# Sensors: temperature, humidity, flow, light

When running experiments we often need to record additional information such as temperature, light level, or humidity. Some external devices offer logging capabilities, but it might be also useful to construct custom device to record such data directly from the sensor. For example, [Arduino can be used](https://www.biorxiv.org/content/10.1101/2021.05.18.444705v1) to log (as well as control) temperature.

In such case the simple setup looks like this:
1. sensor reports data to Arduino, for example digital [DS18b20 sensor](https://www.adafruit.com/product/381) can report temperature through "1-wire" protocol
1. Arduino sends the data via serial port to python script running on PC
1. script writes the data in text file appending timestamp information

Off-the-self devices such as [Thorlabs USB temperature logger](https://www.thorlabs.com/thorproduct.cfm?partnumber=TSP01) provide similar capability without any tinkering but at ~3x price
