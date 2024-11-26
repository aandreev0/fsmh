# Making devices talk to each other

Microscopes are complex systems with significant electro-mechanical features and separate parts need to communicate with each other.

Cameras, stages, light sources, and other devices need to be activated or switched from one mode to another at an appropriate time, for example to achieve multi-color imaging or time-locked stimulation in animal experiments.

Devices usually can receive and send signals using voltage levels: for example, if voltage is 5V it is considered "HIGH" or "1". In practice, devices can define "HIGH" as voltage between 2V and 5V, and "LOW" or zero as voltage between 0V and 0.8V. If voltage is between 0.8V and 2V then the signal is "undefined" and the device might or might not perform triggered action.

Consider camera example. Modern scientific cameras provide GPIO (general-purposes input/output) interface in a single Hirose-type connector:

<span float="left">

```{image} ../../static/CS895CU_Back_Panel_D2-400.gif
:alt: back of cmos camera
:width: 250px
:align: left
```

```{image} ../../static/8050-CAB1_male_hirose_150px.gif
:alt: hirose pinout
:width: 150px
:align: center
```
</span>

Pins on the connector are providing different signals: ground voltage, input (hardware trigger), output (exposure) or other signals. For example, if voltage between ground pin and input trigger pin reaches "HIGH" level, then the camera will perform exposure. Depending on software setting of the camera, the exposure duration will be defined from user interface or will last as long as the voltage is "HIGH".
