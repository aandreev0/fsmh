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

It consists of few major parts: collimated laser source of desired diameter; pair of galvo mirrors that steer beam; 4f system of scan lens and tube lens that relay light to the objective; dichroic element that allows excitation light to pass and reflects fluorescence into the single-pixel detection device (PMT). All distances can be set in CAD software, conflicts checked, and final assembly verified.

## Making custom parts

Designing part and integrating it into existing setup is half of the battle. Second part is actually manufacturing the part. It is important to understand that physical part will not be perfect compared to the 3D rendering: the real part will have tolerances and other imperfections introduced based on the method of manufacturing. Generally speaking, for most parts CNC from metals and plastics will reduced amount of imperfections.

- 3D Printing is an additive method where material is deposited on base. It can be performed using filament extraction (better for larger parts with lower resolution) and lithography (SLA used for smaller parts when higher resolution is necessary). Any 3D printing device will require training and practice and maintenance is required regularly.

- CNC (computer numerical control mill or lathe) is a machine that can selectively remove material to create final part following computational model. To actually perform CNC from CAD, tool-path needs to be generated beforehand (very hard problem) and so many proprietary solutions were developed. Chances are you will outsource CNC work (e.g. Protolabs in the US) or will ask for help from friendly engineer familiar with CNC. Final step after CNC is finishing metal parts, for example, [anodizing aluminum](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=14891) for nicer finish and rust prevention.


- [Laser cutting](https://sendcutsend.com/materials/acrylic/) is a CNC process where design creates a 2D path of high-power laser cutting though plastic (such as acrylic). This is perfect tool for making boxes, chambers, sample holders, and other types of housings. To make things water-proof we can use silicone adhesive or other type of glue. Laser cutter at lower power also allows for engraving for example for making [user-friendly faces for custom device enclosures](https://www.ponoko.com/blog/design-ideas/mounting-and-protecting-custom-pcbs-with-laser-cut-faceplates-panels-and-enclosures/).

```{image} ../../static/52-lasers-024912-enclosure.webp
:alt: 52lasers laser-cut PCB enclosure with engraving
:width: 400px
:align: center
```

*from [52lasers](https://52lasers.com/2018/02/28/130-pcb-enclosure/#jp-carousel-3023)*

## Examples of projects

### Sample holders

Biologists come up with the most fun experiments for microscopy. Potential samples and geometries of imaging are truly endless. To successfully perform these experiments they need ways of mounting samples and positioning on a microscope.

Custom sample holder then will bridge microscope (custom or commercial) with a sample that microscope is not supporting natively. For example, one of the most common microscopes is inverted or upright confocal, optimized for imaging slides or glass-bottom dishes with immobilized samples. However, by utilizing custom sample holders researchers can [image *in vivo* plant growth](https://elifesciences.org/articles/26792) or experiment with [stretchable films](https://pubs.rsc.org/en/content/articlelanding/2012/an/c2an36001b) or perform [3D imaging by rotating sample](https://onlinelibrary.wiley.com/doi/full/10.1111/jmi.12263). Light-sheet microscopes require [special holders due to imaging geometry](https://www.janelia.org/open-science/zeiss-lightsheet-z1-sample-holder).

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
