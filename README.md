# optical-encoder-pcb
A standalone pcb for Ploopy's optical encoder design.

# Status
I decided not to go ahead with this mainly because QMK doesn't really support quadrature and custom encoder drivers simultaneously (and why would they? - so bougie).
Also, the infrared leds are not in stock.

The theory was that I'd use the optical encoder for the mk20's 'ring' encoder, as it'd have less operating friction.

Anyways, I think the basics here would work - obviously I spent very little time on the pcb design.

# How it works
Pretty simple - until you get to the maths and code.

- a pair of infrared led/sensor combos aiming 'through' the scroll wheel
- matching resistors
- scroll wheel with a specific amount of holes to let light pass through
- lit up = analogue pin high; darkened = low

Basically you have power, ground, analog1, analog2.  When the LED light is interrupted by the wheel, the analog input goes low and thus the computer can do something about it.  Your polling code looks at the analog inputs and determines what to do based on the combinations of on/off received over a time period.

I also used a VIK connector cuz why not: https://github.com/sadekbaroudi/vik/

Fun sidenote - the silicone surface on their scroll wheel is actually a silicone ring (on Aliexpress, search 'silicone ring fish scale').

# Further reading
https://www.eeworldonline.com/rotary-encoders-part-1-optical-encoders/
https://github.com/ploopyco/qmk_firmware/blob/master/keyboards/ploopyco/common/opt_encoder_simple.c 
https://github.com/ploopyco/qmk_firmware/blob/master/keyboards/ploopyco/ploopyco.c#L101 
https://github.com/ploopyco/classic-trackball/tree/master/hardware/Electronics/Schematics

# My take on the design
![Schematic](/images/schematic.png)
![PCB](/images/pcb-overview.png)