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
- First, you want to download the latest version of [QMK MSYS](https://msys.qmk.fm/) and [QMK Toolbox](https://qmk.fm/toolbox), as well as [VIA](https://github.com/cebby2420/via-desktop) if you wish to keep a local install copy. Otherwise, you can also reprogram keys from its [browser version](https://usevia.app/).

### Assembly
- After [3D printing the parts](https://www.printables.com/model/1152899-4x5-macropad), you can start assembling your macropad. Place all your **switches** inside the bracket, making sure all the pins face one direction, as shown.

![keyboard layout](https://github.com/user-attachments/assets/e7cc85ac-eefe-43d9-b3ad-035709b7a15e)

- Now, start with the columns. Solder all the top pins of each switch together using wires. A useful tip is to use copper wire cut to length to make contact with each pin.

![keyboard colums](https://github.com/user-attachments/assets/fb39b13b-8762-46b5-b09b-434b9ebd21e4)

- Next, move on to the rows. Trim the top of each diode (the non-black side) down to about 1 cm. Then, solder the trimmed ends to the bottom pins of each switch, making sure the black ends are facing downwards. Bend the leads of the diodes so they make contact with the other bent diodes next to them.
- Be sure to add electrical tape over the columns that could come into contact with the diodes to prevent short circuits.

![keyboard rows](https://github.com/user-attachments/assets/b33c0ff6-2c44-443f-86c7-9e3897143f42)
### Getting the Arduino Ready
- Take your button and solder two wires to its contacts. Then, place the button near the designated hole and secure it in place with hot glue.
- Next, get your Arduino and open QMK MSYS to program the keyboard, and QMK Toolbox to flash the program to the Arduino.
- In QMK MSYS, type `qmk new-keyboard` and press **Enter**. You will then be prompted to enter a keyboard name—name it `4x5_macropad`. After that, you will be asked for your GitHub username and real name; enter your name for both if you don't have a GitHub account.

![Screenshot 2025-01-20 113755](https://github.com/user-attachments/assets/d2f1faba-535d-4136-83e5-e0f4fc798c28)

- You'll be asked to **Pick a base layout**. Select `none of the above` if it isn't already selected, then press **Enter**.
- You’ll be prompted to confirm if you're using a separate development board. Type `y`, then choose **Pro Micro** from the list.

![image](https://github.com/user-attachments/assets/7ecc42e7-464c-45dc-a498-87ee5e34c4b2)

- Now, your project folder is ready. Copy the project location and open the folder in [VS Code](https://code.visualstudio.com/download). Then, go to `keyboard.json`.
- In `keyboard.json`, you'll need to make a few changes. Open my [keyboard.json](https://github.com/Farzy820/4x5-macropad/edit/main/keyboard.json)to see what needs to be changed.
- Next, go to the **`keymaps/default`** folder and open `keymap.c`.
- Replace the contents of the file with the code from my [keymap.c](https://github.com/Farzy820/4x5-macropad/blob/main/keymap.c). `keymap.c` defines the macropad's button layout. If you wish to hardcode a layout that will work across any device, you can find the keycodes in QMK's [Basic Keycodes](https://docs.qmk.fm/keycodes_basic).
- Go back to the keymaps folder, copy **`default`**, but rename it to **`via`**, and create a new file named **`rules.mk`**. In `rules.mk`, add **`VIA_ENABLE = yes`**, then save. This setting enables VIA compatibility for your macropad.
- Finally, download [via.json](https://github.com/Farzy820/4x5-macropad/blob/main/via.json) and move it to the `keymaps` directory. Make sure to open the file and enter the correct information as stated in its comments.
  
### Your file tree should look like this 
![image](https://github.com/user-attachments/assets/fee2fcc7-3b22-47f9-811a-0a799996cb11)

- Open QMK MSYS and enter `"qmk compile -kb 4x5_macropad -km via"`. It will take a minute, but you will see a check with [OK] after many of the lines.
- Now that the file is ready for flashing, open QMK Toolbox and make sure the MCU says **ATmega32U4**, since that is the processor the arduino uses, then click `Open`
![image](https://github.com/user-attachments/assets/1e93059c-ac9e-44e7-a64a-bba98f4971f3)
- Go to `\Users\<user>\qmk_firmware` and select `4x5_macropad_via.hex` and enable auto-flash, then plug in your Arduino to start the flashing process
![image](https://github.com/user-attachments/assets/99d6ed39-7072-491f-9ef4-35b6953a5404)

### Final steps 
- Hot glue the Arduino into its designated slot in the case, then follow the wiring diagram to connect the switches to the board. 
![keyboard wiring](https://github.com/user-attachments/assets/b50724c1-79b9-4230-a455-d92dda9ec6e9)
- *If your Arduino isn't flashing, press the reset button twice quickly to set it into bootloader mode.*
- QMK Toolbox has its own keyboard tester if you've created your own layout. Otherwise, open VIA and enable the **"Show Design"** tab. 
![Screenshot 2025-01-20 140156](https://github.com/user-attachments/assets/9fa39cf3-5a84-43e3-b18a-b1dd58fd3580)
-In the **Design Tab**, you'll see a button labeled `Load`. Click on it and open the `via.json` file you saved. You should now see the layout. 
![image](https://github.com/user-attachments/assets/8d19898b-eab1-4526-a894-6cd7522b4fc5)
- In the **Configure Tab**, the macropad should now appear. Test your inputs by going to the **Key Tester** tab and enabling the test matrix to see if everything is working. If it isn't there, double check the `pid` and `vid` are both matching as mentioned earlier.
![Screenshot 2025-01-20 141011](https://github.com/user-attachments/assets/f875b23a-3b51-4212-b67f-220610705f33)
- If everything is working, you can now fully assemble the macropad and start using it!
![20250117_150145](https://github.com/user-attachments/assets/0eb90760-8e50-4e15-825c-7640a7827148)
![20250117_150202](https://github.com/user-attachments/assets/33d2aba0-16e8-4132-9b70-f2b048dba73e)
*If you have any issues, try reflashing the firmware, checking the wiring connections.*

## Future Plans
For now, this is it, but I may merge the project into the official [QMK](https://github.com/qmk/qmk_firmware/tree/master/keyboards) and [VIA](https://github.com/the-via/keyboards) repos later on. I’m also considering adding a screen sometime in the future as a v2 version. Any suggestions for improvements or features would be greatly appreciated!


## Tutorials I Followed
- ["This Keyboard Will Make You More Productive! DIY Macropad Build + QMK Setup"](https://www.youtube.com/watch?v=BcXycScePHM)
- ["How To Setup VIA On Any QMK Keyboard"](https://www.youtube.com/watch?v=7d5yzBOup9U)
