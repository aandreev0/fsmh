# Super-resolution microscopy experiments

Super-resolution imaging is done using tools that provide information about localization of fluorescent molecules beyond [diffraction limit](../1-basics/optical-design.md#point-spread-function-psf).

There are basically two ways to achieve super-resolution beyond diffraction limit: One is to confine the source of the signal, and another is to computationally (statistically) increase spatial frequency of the image.

## Confining the source of signal

First method to mention is [STED](https://en.wikipedia.org/wiki/STED_microscopy) which is a fluorescence microscopy technique that utilizes point-scanning method (similar to confocal microscope) with crucial difference that two laser beams are used: one for fluorescence excitation and second beam shaped as a doughnut for depletion of the excited molecules. You should read [the original paper from 1994](https://opg.optica.org/ol/abstract.cfm?uri=ol-19-11-780).

```{image} ../../static/sted_schematics.jpg
:alt: STED schematics
:width: 500px
:align: center
```

Because the depletion process is non-linear in respect to STED laser power the molecules in excited state are depleted much more efficiently on the boundary than closer to the center of the doughnut (see [the figure above](https://zeiss-campus.magnet.fsu.edu/tutorials/superresolution/stedconcept/indexflash.html)). While both excitation and depletion beams are diffraction-limited, the resulting volume of excited molecules is smaller than the diffraction-limited volume of excited molecules if STED beam is not used.

Second way to achieve confinement of source of signal is to physically localize the excitation light below diffraction limit. It can be done using [near-field scanning optical microscopy](https://en.wikipedia.org/wiki/Near-field_scanning_optical_microscope) which utilizes optical fiber with core smaller than diffraction limit (e.g. 50nm). More technical [details can be found elsewhere](https://phys.libretexts.org/Courses/University_of_California_Davis/Biophysics_241%3A_Membrane_Biology/05%3A_Experimental_Characterization_-_Spectroscopy_and_Microscopy/5.06%3A_Near-field_Scanning_Optical_Microscopy_%28NSOM%29).

## Computational analysis

To increase spatial resolution beyond optical limitations we can employ several computational methods. An approach that is easiest to explain uses single-molecule localization. If sources of fluorescence are far apart
