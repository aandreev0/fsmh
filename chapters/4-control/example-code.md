# Example code to generate signals

## Python and NI DAQ



## Arduino

**TTL pulse every 1 second**

**TTL pulse every 1 second**

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
