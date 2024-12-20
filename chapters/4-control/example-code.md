# Example code to generate signals

## Python and NI DAQ

```Python
# generated using chatgpt `generate sample code that make NI DAQ generate sawtooth wave using python`

import nidaqmx
from nidaqmx.constants import WaveformType
import numpy as np

# Parameters
device_name = "Dev1"  # Replace with your device name
ao_channel = f"{device_name}/ao0"  # Analog output channel
rate = 1000  # Sample rate (samples per second)
duration = 2  # Duration of the signal in seconds
frequency = 2  # Frequency of the sawtooth wave in Hz
amplitude = 5  # Peak-to-peak amplitude in volts
offset = 0  # DC offset in volts

# Calculate the total number of samples
num_samples = int(rate * duration)

# Generate the sawtooth waveform data
t = np.linspace(0, duration, num_samples, endpoint=False)  # Time vector
sawtooth_wave = amplitude * (t * frequency - np.floor(t * frequency)) + offset

# Create a task to output the waveform
with nidaqmx.Task() as task:
    # Add an analog output channel
    task.ao_channels.add_ao_voltage_chan(ao_channel, min_val=-10.0, max_val=10.0)

    # Configure the timing for continuous waveform generation
    task.timing.cfg_samp_clk_timing(rate, sample_mode=nidaqmx.constants.AcquisitionType.CONTINUOUS)

    # Write the waveform to the buffer
    task.out_stream.write_regen_mode = nidaqmx.constants.RegenerationMode.ALLOW_REGENERATION
    task.write(sawtooth_wave, auto_start=False)

    # Start the task
    print(f"Generating sawtooth wave on {ao_channel}. Press Ctrl+C to stop.")
    task.start()

    # Keep the script running until interrupted
    try:
        while True:
            pass
    except KeyboardInterrupt:
        print("\nStopping waveform generation.")

```

## Arduino

**TTL pulse every 1 second**

```C
int outputPin = 0; // use digital pin 0 for output
void setup() {
  Serial.begin(115200);
  pinMode(outputPin, OUTPUT);
  digitalWrite(outputPin, LOW);
}

void loop() {
  digitalWrite(outputPin, HIGH);
  delay(1); // sleep 1ms
  digitalWrite(outputPin, LOW);
  delay(999); // sleep 999 ms
}

```

**TTL pulse every 10 input triggers (50% duty cycle at 10ms interval)**

```C
int outputPin = 0; // use digital pin 0 for output
int inputPin = 1;
int volatile counter = 0;

void setup() {
  Serial.begin(115200);
  pinMode(outputPin, OUTPUT);
  digitalWrite(outputPin, LOW);
  pinMode(inputPin, OUTPUT);

}

void loop() {
  if(digitalRead(inputPin) == HIGH){
    counter++;
    if (counter >= 10){
      digitalWrite(outputPin, HIGH);
      counter = 0;
    }
    delay(7); // wait till trigger goes low
  }
  delay(1);
}

```

**Triangle wave using [Digital-to-analog Converter](https://docs.arduino.cc/tutorials/uno-r4-minima/dac/) (DAC) on UNO R4**

```C
/*
  based on
  docs.arduino.cc/tutorials/uno-r4-wifi/dac
*/

#include "analogWave.h"
analogWave wave(DAC);

int freq = 10;  // in hertz, change accordingly

void setup() {
  Serial.begin(115200);
  wave.saw(freq);
}

void loop() {
}
```

**Triangle wave and timed triggers using separate [MCP4725 DAC](https://www.adafruit.com/product/935)**

When performing imaging with piezo scanning we sometimes want to trigger camera at repeatable positions, for example, in case of light-sheet imaging. Let's say we want to take 10 images while scanning through 100µm range

```C
#include <Wire.h>             //wire library
#include <Adafruit_MCP4725.h> // MCP4725 library from adafruit

int vol_per_second = 1; // volumes per second
int z_steps = 10; // steps (frames) per volume
float step_duration = 1000*1000/vol_per_second/z_steps; // duration of one frame in µs
int symmetry = 0.9; // symmetry of triangle wave, defines how much time we spend on flyback
int trigger_pin = D1;
int dac_value = 0; // goes from 0 to 4095

void setup(){
  // https://electronoobs.com/eng_arduino_tut119.php
  MCP4725.begin(0x60); // Default I2C Address of MCP4725 breakout board (sparkfun). If not try 0x61 or 0x62
}


void loop(){

  for (int step = 0; step++; step <z_steps){
    // define one step size
    dac_value = step/z_steps * 4095;
    // move stage
    MCP4725.setVoltage(dac_value, false);

    // trigger camera
    digitalWrite(trigger_pin, HIGH);
    // pause after moving stage
    delay((symmetry) * step_duration);
    // end camera trigger
    digitalWrite(trigger_pin, LOW);

  }
  MCP4725.setVoltage(0, false); // back to baseline
  // wait for steady-state
  delay((1-symmetry) * step_duration * z_steps);

}

```
