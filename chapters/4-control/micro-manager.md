# Connecting devices to Micro-Manager 2.0

Micro-Manager is a software program that helps control custom microscopes build from various components that don't necessarily talk well with each other. It [can support dozens of cameras, stages, filter wheels, and other devices](https://micro-manager.org/Device_Support) produced by different companies. Micro-manager provides graphical user interface and other function useful in microscopy. However, someone has to tell micro-manager how to operate these devices. This "glue" is called Device Adapter or a Driver.

## How Micro-Manager talks to devices?

Micro-Manager doesn't work by moving any particular stage or any specific camera. It knows that "camera" can "take image with exposure X" or that stage can "move N microns". Device adapters translate these commands into device-specific language using device-specific API or serial communications.

## Using pyDevice adapter

Native adapters for Micro-Manager are written in C++ and compiled against specific version of Micro-Manager. However, one can also create python-based device adapter using [pyDevice](https://github.com/micro-manager/mmCoreAndDevices/tree/main/DeviceAdapters/PyDevice) virtual device adapter.

For example, we have created 4 adapters:
- for linear stage (Pollux)
- XY stage and piezo Z stage (Thorlabs)
- filter wheel (Picard)

Code is to be released later.
