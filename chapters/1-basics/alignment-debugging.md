# Alignment and debugging the microscope

Microscopes are complex systems comprising hardware and software elements. Optimal performance depends on precise settings, hardware alignment, correct electronic connections and signals. System that deviates from "optimal performance" can exhibit any of these issues:

## Common symptoms of misalignment/technical issues:

- Sudden or gradual decrease in detected signal from samples prepared following same protocol
- Decrease in resolution / "blur" over whole sample or parts of sample
- Sudden issues with color imaging & co-localization
- Imaging not performed at expected frame rate
-

All elements of imaging systems can change with time due to various reasons:

## Common sources of issues

- reversible changes in software: change in imaging settings
- reversible changes in hardware: change of filter sets; light sources; disconnection of cables; devices turned off/capped; shutters closed
- permanent changes in hardware: laser aging; [light damage to mirrors](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=9025&tabname=Damage%20Thresholds); damage to electronics (DAQ channels); [damage to sensors](https://www.spiedigitallibrary.org/journals/optical-engineering/volume-56/issue-3/034108/Laser-induced-damage-threshold-of-camera-sensors-and-micro-optoelectromechanical/10.1117/1.OE.56.3.034108.full); [physical damage to detection objective or dirt](https://x.com/Nat_Prunet/status/1631747764320174081)
- permanent changes in software: backwards-incompatible software update; filled-up storage space; network connectivity issues
- drift in hardware: vibrations, metal/glass expansion due to [temperature changes](https://x.com/JLazzariDean/status/1567680867002363905), [HVAC performance](http://dx.doi.org/10.7517/issn.1674-0475.180303)
- drift in *wetware*: old reagents,  

## Custom and Commercial system have different issues

Custom setups are more affected by changes in hardware alignment or updates that break existing experiments. With custom setups we have the opportunity to "quickly tweak" something or add a new feature - all these changes can potentially create issues with other experiments. The answer to that is documentation of any changes and "locking down" the geometry when data-gathering is happening. There should be a cut-off time after which no hardware changes are allowed so that data can be collected in uniform fashion.

Commercial systems often have stable hardware configuration that is locked "under covers". Thus most of the issues require specialist's visit which can take weeks to schedule. Modern systems include options for remote digital adjustment of some settings, thus you might be able to get help sooner. To expedite the service, it is crucial to collect and share test data when asking for help: show the "test" baseline data and current results and explain why the current results are unsatisfactory. The problem might be simpler to solve than you thought originally.

## Tools for alignment and debugging

- sample reference images "This is how it supposed to look". It is important to regularly make and store reference images of the data from various relevant sample that might include experimental samples, images of fluorescent beads, or solutions of fluorescent dye. Photographs of the setup, especially cables connecting devices together can serve as references for how the setup supposed to look. Finally, screenshots are the best way to store information about parameters and setting of the software components.
- pinholes and [iris diaphragm](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=206) along the laser beam paths. Pinholes are important for microscope alignment to guide laser beam from source to objective. Don't rush removing these elements after alignment has been achieved, it is very useful to check drift or movement by re-guiding the beam.
- [shearing plate interferometer](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_ID=2970) is used to make sure coherent light is collimated
- [indicator cards for IR light](https://www.edmundoptics.com/p/laser-detection-card-ir/12140/)
- Test samples for different parts of the microscope: fluorescent dye like FITC for illumination PSF (e.g. light-sheet or [2P-LSM](https://www.newport.com/mam/celum/celum_assets/Figure_297-Photonics_Handbook_800w.jpg)); fluorescent beads for characterizing detection PSF; sample fixed on slides or in [3D polymer gels](https://www.mypolymers.com/bio-133-enables-diverse-applications-in-fluorescence-microscopy-2/)

## Building microscope for easier alignment

CAD-based design helps with faster and more accurate assembly and with finding potential issues earlier. Other tools that help with building better microscope is use of cage systems for rough pre-alignment, centering elements on the tapped holes of the optical table, and having mirror pairs upstream of critical elements that require light being aligned along optical axis. Image planes (if there are several, e.g. 4f relay system) should be accessible for investigation. If the main light source is invisible light, consider adding a low-power visible light laser that can be used as a guide.
