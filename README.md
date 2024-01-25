# C64 Longboard RF replacement V2

![Board](https://github.com/TheRetroChannel/Commdore-64-RF-replacement-Longboard-V2/blob/main/Images/RF%20V2%20LONGBOARD.jpg)

The RF modulator in the C64 handles amplification and filtering for all video signals (including the ones on the C64 DIN connector). Unfortunately it does a very poor job and this is even more apparent with modern displays and upscalers, even CRTs with their inherent softening can reveal issues with the original RF modulator. One way to signifcantly improve the video output is to replace the RF modulator with a more modern and finely tuned solution, and why not add a few quality of life features while were at it.

This is an RF modulator replacement (RF delete) for the longboard Commodore 64 variants - these include ASSY KU-14194HB, 250407, 250425 and 250466. 

For shortboard C64 ASSY 250469 and Commodore 128 see [C64 Shortboard and C128 RF replacement V2](https://github.com/TheRetroChannel/Commodore-64-Shortboard-and-C128-RF-Replacement-V2). 

Note ASSY 326298 is not compatible with either of these RF modulator replacements but there are some [simple mods](https://youtu.be/agDFLPP9yIw) that can improve the video output of this revision.

You can purchase preassembled boards on my [Tindie store](https://www.tindie.com/stores/theretrochannel/)

A YouTube build and installation video is available [HERE](https://youtu.be/t5yx6tAaMuE)

## Feature summary
* Superior video output compared to the original RF modulator
* Direct S-Video output for S-Video capable displays and upscalers
* Optional HDMI (DVI) output for the large VIC-II Kawari
* Adjustable luma:sync ratio (contrast control)
* Signal passthrough to the C64 AV DIN - for those who prefer to use the standard DIN connector
* 3.5mm stereo audio output with the left channel dedicated to SID audio, and right channel selectable between SID audio (dual mono), composite video, and external (for dual SID setups, LumaCode, etc.)

## Changes from V1
* Component values tweaked and extra filters added - even better video output
* Added support for connecting VIC-II Kawari HDMI and LumaCode
* Added direct composite output via 3.5mm jack
* Added contrast control - something Commodore should have done
* Removed composite enable header and trimmer - no longer required thanks to point 1
* Removed direct luma/chroma connections - no longer required thanks to point 1
* Removed adjustable luma chroma pots - no longer required thanks to point 1
* Removed hard reset circuit - did anyone even use it?
* Better routing (slightly less pretty) and solid ground plane on bottom layer
* Board dimensions tweaked for better fitment

## Comparison shots

![64 comparison](https://github.com/TheRetroChannel/Commdore-64-RF-replacement-Longboard-V2/blob/main/Images/COMPARISONS%20250407%20PAL.png)
 
## Gathering components
The easiest way to order PCBs is through the shared project page on PCBWay. Simply click [this link](https://www.pcbway.com/project/shareproject/Commodore_64_Longboard_RF_Modulator_Replacement_V2_9f89285d.html) and add to your cart. Then scroll down to find the **Remove product No.** option and select **Specify a location**. PCBWay should then print their product number under the 3.5mm audio jack. You should be safe to leave all other options as the default ie. 2 layer FR-4, 1.6mm board thickness, HASL with lead, etc. Alternatively you can download the [gerber files](https://github.com/TheRetroChannel/Commdore-64-RF-replacement-Longboard-V2/blob/main/Files/Gerber_C64%20LB%20V2.zip)

Note PCBWay give me a small credit when ordering using the shared project page.

The [BoM](https://github.com/TheRetroChannel/Commdore-64-RF-replacement-Longboard-V2/blob/main/Files/BOM_C64_Longboard_RF_V2.xlsx) lists all components required and also includes friendly part names and example part links from AliExpress and Mouser for ease of ordering. Most are generic components so you can use your preferred parts supplier, but the recessed S-Video and HDMI connectors are very specific types and hard to find outside of AliExpress.

## Build
Component values are printed on the front side of the PCB under the part itself (where possible) this was done to ease the build process while still giving a "clean" look once the board has been populated. I prefer to start by soldering the flat components (diodes, resistors) and then the taller ones (capacitors, transistors, switch, AV connectors).

A HDMI connector can be mounted in the S-Video footprint (for the large VIC-II Kawari). The required parts are listed in the BoM. Please refer to the YouTube video linked above for details on how to mount and use the HDMI connector. **Note the Kawari outputs a DVI signal over HDMI, so you will still need to connect audio separately.**

Once all topside components have been soldered into place, install the 6 individual and 2 rows of 4 pin headers on the underside. For the rows of 4 it is recommeneded to only solder one pin, then check their alignment to make sure they are straight before soldering the remaining 3 pins. If you solder them all at once, it will be very hard to straighten them afterwards. 

Cut up another 6 individual headers and pull the black plastic spacers off with some pliers. Push these spacers onto each of the individual pin headers on the underside of the RF board. ![SPACERS](https://github.com/TheRetroChannel/Commdore-64-RF-replacement-Longboard-V2/blob/main/Images/lb%20standoffs.jpg)

## Install
Remove the original RF modulator, there are 4 tabs that need to be straightened and 4 grounding posts to be desoldered. You also need to desolder the 8 signal connections to the modulator - be very careful with these as they are easily damaged if not desoldered properly!

Insert the RF replacement into the mainboard (do not solder it in yet) and then the mainboard into the case. The rear ports should line up correctly in the case with no adjustment required (assuming the extra plastic spacers have been added as above). Once you have confirmed the alignment is correct, remove the mainbaord and proceed with soldering the ground posts and signal connections.

## Setup
### Right Channel Switch
Set the selector switch to the desired "right channel" output. A 3.5mm to 2x RCA cable or splitter is recommended

**Composite**: Left channel is SID audio, right channel is composite video.

**Dual Mono**: Both left and right channels are SID audio.

**External**: Left channel is SID audio, right channel will be whatever is connected to the "input" pin nearby. The most common use for this would be dual SID setups or LumaCode. For example if used with Lumacode, LUM from the VIC-II-dizer would connect to "input", and GND to "ground".

Remember audio signals can be safely spilt, but not video signals. You can for example use the 3.5mm jack for composite video on the right channel, and split the left channel audio into left and right (dual mono).

The board can also safely drive both composite and S-Video outputs at the same time but not dual S-Video or dual composite (using both the RF replacement output and C64 DIN connector). In most cases you shouldn't need to use the C64 DIN connector, but all the standard video and audio signals will still be available there if required.

### Contrast fine tune
Commodore used a fixed value resistor for all longboard RF modulators which doesn't take into account variances in the video output of each and every VIC-II. I've added this option so the output can be tailored for your VIC-II and display combination.

Set the potentiometer to the mid position and power on the C64. Change the foreground colour to white: POKE53281,1 and the border colour to light grey: POKE53280,15

Adjust the potentiometer to obtain the ideal contrast. Too low and the white will appear light grey, too high will cause white to bloom and text will appear to shrink. This adjustment may also have an effect on jailbars if present in the borders, so it is recommended to play around until you find a sweet spot. **Note this adjustment may have little to no effect depending on your display or upscaler - in which case it is recommended just to leave the trimpot at its mid position.**

### HDMI
This option will only work with the Large VIC-II Kawari that outputs a DVI signal over a micro HDMI connector. A micro HDMI port replaces the S-Video connector and a flat flex cable brings the HDMI from the Kawari to the rear of the 64 case. It is highly recommended to first confirm the HDMI output from the Kawari is compatible with your display as it does not output a standard resolution. Please also keep in mind this is a DVI signal, as such it does not carry audio - that's what the 3.5mm jack is for!

**Marvel at the beauty of your Commodore, force your friends, relatives, and random people on the internet to do the same.**

-------

To help me continue doing this kind of thing or just to say thanks, consider signing up as a [Patron](https://www.patreon.com/theretrochannel)
