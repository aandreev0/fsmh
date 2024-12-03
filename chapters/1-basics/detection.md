# Detecting optical signals

Light detectors converting incoming photons into electrical signals that can be digitized to produce images.

It is important to understand few characteristics of the digitized signal.

- background level
- offset
- dark counts
- noise (multiple sources/types)
- signal/noise (SNR) and signal/background (SBR) ratio
- shot noise
- electronic gain applied

## Single-pixel detectors

Laser-scanning microscopy (confocal, two-photon, near-field super-resolution and other types) relies on point detectors for high sensitivity and low-noise detection. Commonly we use PMT and GaAsP detectors and move the sample or position of illuminated point to achieve 2D imaging.

## Camera-based sensors

2D sensors combine multiple pixels to detect light coming from various points within field of view. Currently sCMOS technology is prevalent for scientific imaging.

## Spectral detection

Both single-pixel detectors and cameras can be used to acquire spectral information from the sample. To achieve fast, one-shot acquisition linear detectors are often used where spectral information is spread across multiple pixels. [When using 2D sensors](https://www.nature.com/articles/ncomms8990), data can be multiplexed to acquire spatial and spectral information at the same time.

## Signal averaging

When signal is low we might want to perform averaging of measurement to improve SNR. It can be done in multiple ways:

1. temporal averaging: increase exposure (when using camera), average images together, repeat and average measurement from single-pixel detector
1. spatial (digital) averaging: bin pixels together (camera) or average pixels after acquisition
1. spatial (optical) averaging: reduce magnification factor of the system

Apart from decrease in spatial/temporal resolution, such averaging carries another drawbacks. For example, electronic binning will [not decrease readout noise](https://www.teledynevisionsolutions.com/learn/learning-center/imaging-fundamentals/binning/) as binning happens after pixels were digitized. [Longer exposure](https://www.teledynevisionsolutions.com/learn/learning-center/scientific-imaging/thermal-control-for-long-exposure-imaging/) can lead to accumulation of thermal noise.

## Power / light flux meters
