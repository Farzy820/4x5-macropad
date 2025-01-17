# 4x5-Macropad

A 3D-printed, hand-soldered 4x5 macropad powered by an Arduino Pro Micro, running QMK and compatible with VIA. I created this as a school project, and after a few friends showed interest in making their own, I decided to share my project along with a tutorial here.

## What You'll Need
### Electronics:
- Arduino Pro Micro
- 20 × 1N4148 Diodes
- 20 × Keyswitches
- 4x4mm Button 
- Jumper Wires
### Tools:
- Soldering iron
- Hot glue gun
- Electrical tape
### Other Materials:
- Access to a 3D printer for the case and keyswitch bracket

## Installation and Setup
### Firmware
- First, you want to download the latest version of QMK MSYS from [QMK MSYS](https://msys.qmk.fm/) and QMK Toolbox from [QMK Toolbox](https://qmk.fm/toolbox), as well as [VIA](https://github.com/cebby2420/via-desktop/releases/tag/v2025.1.13) if you wish to keep a local instal copy. Otherwise, you can also reprogram keys from its [browser version](https://usevia.app/).

### Assembly
- After 3D printing the parts, you can start assembling your macropad. Place all your keys inside the bracket, making sure all the pins face one direction, as shown.

![keyboard layout](https://github.com/user-attachments/assets/e7cc85ac-eefe-43d9-b3ad-035709b7a15e)

- Now, start with your columns. Solder all the top pins of each switch together with wires. A useful tip is to use copper wire cut to length to make contact with each pin.

![keyboard layout columns](https://github.com/user-attachments/assets/792591f1-d4b6-48a8-8f89-8eafa6001ea2)

- Next, move on to the rows. Trim the top of each diode (the non-black side) down to about 1 cm. Then, solder the trimmed ends to the bottom pins of each switch, making sure the black ends are facing downwards. Bend the leads of the diodes so they make contact with the other bent diodes next to them.

![keyboard layout rows](https://github.com/user-attachments/assets/7e60f486-a2bd-44f3-a16e-418abe78bc91)


## Tutorials I Followed
- ["This Keyboard Will Make You More Productive! DIY Macropad Build + QMK Setup"](https://www.youtube.com/watch?v=BcXycScePHM)
- ["How To Setup VIA On Any QMK Keyboard"](https://www.youtube.com/watch?v=7d5yzBOup9U)
