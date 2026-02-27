# Serial port: ASCII commands

Many devices come with on-board interpreters of [ASCII commands](https://www.digikey.com/en/maker/tutorials/2024/ascii-the-history-behind-encoding) that bridge the gap between human-readable instruction and binary "language" of computers. However most commands are not very user-friendly to save bandwidth (amount of data sent between host computer and device).

For example, this [some specific linear stage](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=10459) command ``Amr00001000`` equals to

> Request a linear stage at address “A” to move 2mm from the
present position.
Linear stage has 2048 encoder pulses per mm, hence 2 mm 4096
pulses (0x1000 in hexadecimal).

You can design your own language of sending commands if you develop devices, specifically much more user-friendly. It all depends on implementation of the command processing.

In order to engage devices through such command interface, one has to:
 1. establish serial connection at proper baud rate
 1. usually initialize the device at a default state
 1. send command
 1. receive and interpret the response

Serial interface can be be access using applications or custom scripts. For windows we have wonderful PuTTY. In a pinch you can use Arduino IDE since it has built-in serial terminal (for all platforms).

Here an example Python code for working with [linear actuator from Newport](https://www.newport.com/f/linear-actuators-with-conex-controller):

```python
import serial
# set up serial connection
ser = serial.Serial('com3',baudrate=115200,timeout=1.0,parity=serial.PARITY_NONE, stopbits=serial.STOPBITS_ONE, bytesize=serial.EIGHTBITS)

# get current position for the stage 1
ser.write(str.encode('1TP\r\n'))  
# read response from the stage
print(ser.read(13))

# leave DISABLED state
ser.write(str.encode('01MM1\r\n'))
print(ser.read(13))

# Leave CONFIGURATION state
ser.write(str.encode('1PW0\r\n'))
print(ser.read(13))

# "home" the stage
ser.write(str.encode('01OR\r\n'))
print(ser.read(13))

# move to absolute position at 10µm
ser.write(str.encode('1PA10\r\n'))  
print(ser.read(13))
```

One caveat of using serial commands with devices is that movement is not instantaneous and you might need to repeatedly query the device to check if it has finished moving. Otherwise device might ignore all commands you send before movement was finished:

```python
def is_moving():
  # this command returns the current controller state:
  ser.write(str.encode('01MM?\r\n'))  
  # read return value
  return_value = int(ser.read(13))
  if return_value == 33:
    return False
  if return_value == 28: # stage is still moving
    return True
```
