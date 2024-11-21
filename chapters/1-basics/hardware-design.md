# Hardware design for microscopy

Involved a lot of CAD work. You can read about it more in [the *Nature Methods* opinion](https://www.nature.com/articles/s41592-022-01484-5)

## Assembling from parts

When buying hardware parts off-the-shelf, we often get access to 3D models. Assembling these in software of your choice (Autodesk, Solidworks, OpenSCAD, FreeCAD or other)

In general, hardware design from parts should start after the optical design has been finished that is optical elements were picked and arrangement has been decided. Hardware design then will be used to place these elements in real space, relative to mounting points, sample holder stage, and other parts of the system.

As an exercise, you can practice by assembling a point-scanning two-photon laser microscope (in non-de-scanned mode).

```{image} ../../static/2p-laser-scanning-microscope.png
:alt: sketch of point-scanning two-photon laser microscope in Fusion360
:width: 400px
:align: center
```

It consists of few major parts: collimated laser source of desired diameter. 

## Making custom parts
- 3D Printing
- CNC
- Getting your parts manufactured
- laser cutting

## Examples of projects

### Sample holders

Biologists are capable of coming up with the most fun experiments for microscopy. Potential samples and geometries of imaging are truly endless. To successfully perform these experiments they need ways of mounting samples and positioning on a microscope.

Custom sample holder then will bridge microscope (custom or commercial) with a sample that microscope is not supporting natively. For example, one of the most common microscopes is inverted or upright confocal, optimized for imaging slides or glass-bottom dishes with immobilized samples. However, by utilizing custom sample holders researchers can [image *in vivo* plant growth](https://elifesciences.org/articles/26792) or experiment with [stretchable films](https://pubs.rsc.org/en/content/articlelanding/2012/an/c2an36001b) or perform [3D imaging by rotating sample](https://onlinelibrary.wiley.com/doi/full/10.1111/jmi.12263)

### Optical adapters

Optical systems often involves different interfaces, specifically different types of threads on parts. To overcome this incompatibility, we can often purchase adapters (see [Thorlabs thread adapters](https://www.thorlabs.com/navigation.cfm?guide_id=2327) page for many examples). However, sometimes needed components don't exist or have wrong dimensions.

To overcome this issue, we can use CNC machining or 3D printing to generate custom adapters, or create "join" parts that can connect commercially-available adapters to create new adapters.

```{image} ../../static/optical-adapter.png
:alt: optical adapter to connect oculars with SM1 system
:width: 400px
:align: center
```


### Embedded systems

Part of microscopy systems or the whole imaging setups can be assembled on a custom base to achieve portability and rigidity, or uniformity of the components. Such embedded systems combine custom and off-the-shelf parts, often with custom adapters and mounting hardware to make strong and reliable hardware system. One example is [Flamingo light-sheet microscope](https://huiskenlab.com/flamingo/):

```{image} ../../static/flamingo.png
:alt: flamingo microscope
:width: 400px
:align: center
```
