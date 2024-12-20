# Light sources

Light generation and delivery to sample is foundational problem in microscopy. Light sources can be specified by few characteritics such as:

- spectral content: which wavelengths are present in the light source? How wide is the spectrum?
- frequency of modulation: is it a pulsed source or continous-wave?
- control: can we electronically control amplitude or frequency of light?
- is the light polarized?
- is the light coherent? (in case of lasers)
- is the light collimated when leaving the light source?
- what is the shape of the light beam?

## Laser sources

Laser sources can provide coherent light with narrow (from 0.01nm for continuous-wave sources to >20nm for femtosecond pulsed laser) spectrum, well-defined polarization, high-quality beam shape, and stable frequency (in case of pulsed lasers). Multiple lasers with different wavelengths can be packaged [into a single device](https://www.coherent.com/lasers/laser-engine/galaxy), coupled into a single optical fiber for compact and efficient delivery to the imaging setup. Ideally, we want a device where amplitude of each laser output can be independently modulated.

Special case for lasers is Argon-ion laser that produces multiple peaks such as 488nm (used for GFP) and 514nm (YFP).

## LEDs and lamps

For many applications we can use LED sources or lamps. Most of the wide-field fluorescence microscopes are using mercury lamps with spectrum that has multiple characteristic peaks. For example, mercury lamp has peak at 405nm (that excites commonly-used DAPI stain) and 546nm (can excite rhodamine B). Other sources such as xenon lamps provide broadband spectral output without characteristic peaks in the visible (300-700nm) range
