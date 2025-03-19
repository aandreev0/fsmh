# Connecting devices to Micro-Manager 2.0

Micro-Manager is a software program that helps control custom microscopes build from various components that don't necessarily talk well with each other. It [can support dozens of cameras, stages, filter wheels, and other devices](https://micro-manager.org/Device_Support) produced by different companies. Micro-manager provides graphical user interface and other function useful in microscopy. However, someone has to tell micro-manager how to operate these devices. This "glue" is called Device Adapter or a Driver.

## How Micro-Manager talks to devices?

Micro-Manager doesn't work by moving any particular stage or any specific camera. It knows that "camera" can "take image with exposure X" or that stage can "move home". Device adapters translate these commands into device-specific language using device-specific API or serial communications:

<table style="width:100%">
  <tr>
    <th>Real-world Action</th>
    <th>Micro-Manager Function</th>
    <th>Device Name</th>
    <th>Device Function</th>
  </tr>
  <tr>
    <td rowspan=3>Move stage to 0 (Home)</td>
    <td rowspan=3> Stage::Home() </td>
    <td> Pollux Stage</td>
    <td> Serial command "1 ncal"</td>
  </tr>
  <tr>
    <td>Thorlabs XY stage</td>
    <td>channelX.Home(60000)<br>channelY.Home(60000)</td>
  </tr>
  <tr>
    <td>Thorlabs Piezo</td>
    <td>stage.SetZero()</td>
  </tr>
</table>

Device Adapter is a "glue" that relays commands from Micro-Manager to the hardware components.

## Using pyDevice adapter

Native adapters for Micro-Manager are written in C++ and compiled against specific version of Micro-Manager. However, one can also create python-based device adapter using [pyDevice](https://github.com/micro-manager/mmCoreAndDevices/tree/main/DeviceAdapters/PyDevice) virtual device adapter.

For example, we have created 4 adapters:
- for linear stage (Pollux)
- XY stage and piezo Z stage (Thorlabs)
- filter wheel (Picard)

Code is to be released later.
