
# Homemade-30V-4A-DC-PSU
My \[in development\] homemade DC PSU of 30 V / 4 A

Hi. To power future electronic projects of mine (have a few in mind), I've decided to make a DC power supply. Not a simple one, like 5 V / 500 mA or something like that - a power PSU (if you can call it that).

**This project uses LTspice (forget the "AGS Script" language from GitHub - it's wrong).**

## Characteristics
### Intended generic ones
- Should be able to generate from 0 V to at least about 30 V between any pins (30 V because it's around the necessary to control the CRT of an oscilloscope I bought - Tektronix 2201)
- Should be able to drive minimally high currents (else it won't be able to do much)
- Must be as efficient as possible, but at least 60% (the more, the better though - with any ideas that come to mind)
- Must have short-circuit and current limiting protections
- Low to very low output ripple (mega maximum of 5%, ideally 1-2%, or even better 1% or less - I read that "For a 5 vdc supply 50mv ripple is an acceptable figure." (1% then), but also that that CPUs need 1% at mega maximum of ripple, with less being the ideal)
- Able to cool down itself (fans), preferably dynamically (less power dissipation)
### Current ones
#### Unregulated module
- It's being designed for max 30 V and 4 A (the transformer I bought can provide 34 V /4 A max on the output)
- Max current on all components of 6 A, including the fuse (1.5 x 4 = 6. Not 2x - more expensive... 1.5 should be enough I guess)
- NTC thermistor on the input to limit the inrush current
- 40 mF in input capacitors to have the ripple stay low even on low loads (as of 2022-01-04, that results in 2% output ripple at 28 V / 4 A with a 7 Ohm load --> means that at lower voltages much lower ripple will happen, and at 9 V / 4 A the ripple is of 9 µV (0.0001%), which seems more than perfect)
- Unregulated voltage outputs for generic supply (like the fan, which needs 12 V)
- Automatic switch between the transformer output to save power with a relay and a comparator (if less than, like, 16 V requested on the PSU output, use the 12 VAC winding. More than 18 V requested, use the 24 VAC winding. Else, \[haven't taken care of that, but I think it should keep the winding in use\]
- Schmitt trigger is in the works too, to fix a problem of instability (at least when I imagine the circuit working, but I think it's right) when the voltage gets too near the op-amp comparison voltage
#### Regulator module
- Precision regulator to use for the op-amp to compare with the output, while also being a very low regulator voltage (the greater the comparator voltage, the greater the minimum - and I'd still like a very low output voltage to test on very low voltage devices, if I ever want to, like a clock)


## Calculations
To see the calculations for everything, check the Calculations.docx file. I'm writing everything in there.

## Pictures
(There are more on the Photos folder)

<img src="Photos/IMG_20220916_185118_0.jpg" width="500"><img src="Photos/IMG_20220613_200632_0.jpg" width="500">

## Final notes
It's being really cool to make this PSU. It's also taking me much time, because I'm not at home to solder anything on it, so I can only develop on LTspice and think if that matches what I think that would happen in practice (intuition (what I used to realize there would be a problem on the unregulated module comparator without some better mechanism than a simple op-amp) and the little experience I still have).

Also, if any component files are missing, tell me and I'll provide them (I found a lot of devices on a ZIP and downloaded them all and I use any device that is comparable to the ones I have available).
