# Spectra and filters

When designing imaging experiment we aim to achieve several outcomes:
- maximize collected signal
- minimize amount of excitation light
- separate signal from different fluorophores
- avoid detecting scattered excitation light

 Fluorescent molecule's signal is a function of excitation efficiency and detection filtering efficiency. Adding the above mentioned constraints makes the process of selecting fluorophores, filters, dichroics, and lasers difficult especially when we want to co-localize several fluorophores (think blue, green, and red channels in 3-channel imaging). Tools such as [FPbase](https://www.fpbase.org/) are extremely useful in designing experiment and checking assumptions.

 Here, for example, [FPbase allows one to design an experiment](https://www.fpbase.org/microscope/4yL4ggAozzcMwTU4Ae7zxF/) given constraints such as fluorophore, camera sensitivity, filters, and other optical elements. By changing filters, for example, we can see how signal changes

 ```{image} ../../static/fpbase-yokogawa.png
 :alt: fpbase example microscope
 :width: 600px
 :align: center
 ```

It is important to remember: excitation and emission spectra of fluorophores can be extremely wide. Nearly every organic molecule can be excited by 405nm laser (at different efficiency of course). Same way some light sources (LEDs) have very wide spectrum and will "leak" through the filters. Things are exacerbated by the fact that dichroic filters are designed for 0 degree angle of incidence (AOI) and [have different transmission of light at other angles](https://alluxa.com/optical-filter-specs/angle-of-incidence-aoi-and-polarization/). Similarly, transmission depends on light polarization (random in LEDs, linear in lasers). Dichroic mirrors are designed for 45&deg; AOI and [also affected by angle of incoming light](https://jascoinc.com/applications/absolute-reflectance-measurement-dichroic-mirror/).
