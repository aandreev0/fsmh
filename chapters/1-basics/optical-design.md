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

## Aberrations

## Real optics

## How to make things move
