# Devices can't follow signals perfectly

## Software: signal generation jitter

## Hardware: galvo mirror response

```{image} ../../static/galvo-signal-response.png
:alt: galvo mirror response
:width: 250px
:align: center
```

Galvo mirror steers laser beam following input electrical signal. However, the response (provided by sensor inside galvo) is not perfectly following the input signal. [Some microscopes](https://www.nature.com/articles/s41598-023-46245-2) are sensitive enough to that discrepancy and require correction. Such correction is done by adjusting parameters of PID controller that transforms input signal into voltage that drives mirror. Because galvo systems are assembled for the specific mirror, the PID parameteres are embedded in hardware using adjustable potentiometers on the control board.

## Hardware: piezo response

Another example is piezo collar to move objective that is often used for 3D imaging (z-scanning). These devices are heavier and need to be able to move objectives of different weights, so calibration is more complicated (PID adjustment) and performed inside the device's software.

```{image} ../../static/piezo-collar-response.png
:alt: piezo collar repsonse
:width: 250px
:align: center
```
