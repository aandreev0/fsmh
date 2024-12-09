# Optical design



## Geometric optics

## Point-spread function (PSF)

PSF represents a three-dimensional image of a point source and contains information about light wavelength, magnification, all types of aberrations, and spatial inhomogeneity of imaging system (e.g. PSF is different in center vs edge of image). PSF is tightly coupled with the definition of resolution: for two point objects to be "resolved" their PSFs need to be distinguishable. How we define that is up to the user, for example commonly used [Rayleigh criterion](http://hyperphysics.phy-astr.gsu.edu/hbase/phyopt/Raylei.html) sets distance between point sources at 0.61*wavelength/NA objective (see more [here](https://physics.stackexchange.com/questions/264925/where-does-the-0-61-come-from-in-r-sin-theta-0-61-lambda))

```{image} ../../static/resolution_limits.jpg
:alt: resolution limits
:width: 400px
:align: center
```

*Image taken from [UT Advanced Microscopy core](https://advanced-microscopy.utah.edu/education/super-res/)*

In super-resolution microscopy such as PALM/STORM/MINFLUX resolution is defined through statistical accumulation of estimated positions of point sources, not from single image. Use of deconvolution can mathematically increase resolution even though the optical system and corresponding PSF stay unchanged.

According to [Niquist criterion](https://en.wikipedia.org/wiki/Nyquist_frequency) to truthfully reconstruct PSF we need to sample it with at least twice the spatial frequency. If optical resolution (from PSF estimation) is expected to be 0.5µm, then we need to have data collection resolution 0.25µm (or finer) using scanning or camera-based detection.

Optical resolution necessary for particular experiment depends on the size of features we are interested in. As discussed in [](../3-experiment/microscopy-experiments.md), lateral size and spacing between objects (molecules, cells, or regions of interest) is important to consider when designing experiment.

## Aberrations and real optics

We need to remember several common types of aberrations:
- spherical: due to lens shape light at the edges is focused in different location that light along optical axis
- chromatic: difference in light path of different wavelength due to dispersion
- refraction within sample: due to non-homogeneity of refractive index of the sample (e.g. lipids vs proteins in the sample)

Some of these aberrations can be corrected by lens design, for example [achromatic doublets](https://en.wikipedia.org/wiki/Achromatic_lens) can correct spherical and chromatic aberrations. Apart from price, these lenses can have higher reflection and absorption than comparable spherical singlets. Aspherical lenses are another alternative at even higher price and more limited

## How to make things move

- kinematic mirror mount
- Z stages
- voice coils
- linear actuators
- piezo actuators
- digital micromirror device (DMD)
