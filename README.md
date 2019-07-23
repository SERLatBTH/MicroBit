# MicroBit

The BBC micro:bit is a handheld, programmable micro-computer that can be used for all sorts of cool creations, from robots to musical instruments – the possibilities are endless.

## Content

* [In The Box](#in-the-box)
* [Chip Layout](#chip-layout)
* [MicroBit Specs And Features](#device's-functionalities-and-features)
* [Programming the MicroBit](#programming-the-microbits)
  * [Environment And Languages](#environment-and-languages)
  * [Writing Code: Blocks and JavaScript](#writing-code-blocks-and-javaScript)
  * [Writing Code - Python](#writing-code-python)
  * [Flashing the Chip](#flashingthe-chip)
* [Examples and Tutorials](#examples-and-tutorials)



## In The Box
When you get the micro:bit, here is the things that you need to have.
1. two AAA batteries
2. battery holder
3. micro USB cable
4. safety guide and ready set go
5. micro:bit
![alt text](/images/content.jpg)

## Chip Layout
![alt text](/images/overview.png)

## MicroBit Specs And Features

The micro:bit has the following physical features:

1. 25 individually-programmable LEDs

   LED stands for Light Emitting Diode. The micro:bit has 25 individually-programmable LEDs, allowing you to display text, numbers, and images. [Example:Flashing Heart](https://makecode.microbit.org/projects/flashing-heart)

2. 2 programmable buttons

   There are two buttons on the front of the micro:bit (labelled A and B). You can detect when these buttons are pressed, allowing you to trigger code on the device. [Example:Smiley Buttons](https://makecode.microbit.org/projects/smiley-buttons)

3. Physical connection pins

   There are 25 external connectors on the edge connector of the micro:bit, which we refer to as 'pins'. Program motors, LEDs, or other electrical components with the pins, or connect extra sensors to control your code! [Example:Banana Keyboard](https://makecode.microbit.org/projects/banana-keyboard)

4. Light and temperature sensors

   By reversing the LEDs of the screen to become an input, the LED screen works as a basic light sensor, allowing you to detect ambient light.[Examples - learn how to chart the light level on the screen with JavaScript](https://makecode.microbit.org/examples/plot-light-level)

   This sensor allows the micro:bit to detect the current temperature of the device, in degrees and Celsius.[Examples - discover how the temperature sensor works.](https://microbit.org/guide/temperature/)

5. Motion sensors (accelerometer and compass)

   An accelerometer measures the acceleration of your micro:bit; this component senses when the micro:bit is moved. It can also detect other actions, e.g. shake, tilt, and free-fall.[Example:Rock Paper scissors](https://makecode.microbit.org/projects/rock-paper-scissors)

   The compass detects the earth's magnetic field, allowing you to detect which direction the micro:bit is facing. The compass has to be calibrated before it can be used.

   'Calibrating' the compass ensures the compass results are accurate. For the MakeCode editor, use the 'calibrate compass' block. To calibrate the compass in Python use compass.calibrate().

   When the calibration begins, the micro:bit will scroll the instruction "Tilt to fill screen". To calibrate the compass, tilt the micro:bit to move the dot in the centre of the screen around until you have filled up the whole screen.Examples - create a working compass to find North in [JavaScript](https://makecode.microbit.org/projects/compass) or [Python](https://microbit-micropython.readthedocs.io/en/latest/tutorials/direction.html)!

6. Wireless Communication, via Radio and Bluetooth

   The radio feature allows you to communicate wirelessly between micro:bits. Use the radio to send messages to other micro:bits, build multiplayer games, and much more! [Example:Rock Paper Scissors Teams](https://makecode.microbit.org/projects/rps-teams)

   BLE (Bluetooth Low Energy) allows the micro:bit to control phones and tablets over Bluetooth. This communication works both ways, so you can also send code to your micro:bit wirelessly from your phone using one of our apps. Other apps, such as Swift Playgrounds and Scratch, use Bluetooth to talk to the micro:bit.

   Before using the Bluetooth feature you will need to pair your micro:bit with another device. Once paired, you can send programs wirelessly to your micro:bit. When you're using Radio, Bluetooth can still be used to update the code on your micro:bit, if you enter pairing mode - learn about the differences between radio and bluetooth in this support article.

7. USB interface

   The USB interface allows you to connect the micro:bit to your computer via a micro-USB cable, which will power the device and allow you to [download programs onto the micro:bit](https://microbit.org/guide/hardware/usb/).

## Programming the MicroBit

### Environment And Languages

Micro:bit can be programmed using Blocks, JavaScript, and Python. No environment setup required to write code for micro:bit, instead you need just a web browser to access the online editor, write your code and download it to micro:bit.

### Writing Code - Blocks and JavaScript
1. To write code using Blocks or JavaScript go to the online [MakeCode editor](https://makecode.microbit.org/)
2. Choose the desired language Blocks or JavaScript from the switch in the middle of the top bar.
3. Write your code. If you are using blocks then you can drag and drop the required piece of code from the left side bar.
4. A simulator is found in the editor on the left side that helps you test your code before writing it to the chip.
4. Click download to get a .hex file that can be used to program the micro:bit.
5. You can also choose to save the project in the editor. This will save the project in the browser you are using and will only be accessible from the same browser, using different browser or different computer you will not be able to access the projects.

### Writing Code - Python
1. To write code using Python go to the [online editor](https://python.microbit.org/v/1.1)
2. Write your code
3. Click download to get a .hex file that can be used to program the micro:bit
4. You can click on save to get python file (.py) of the source code
5. If you already have a .hex file or .py file you can load it by clicking on load button then choosing the file. Note: if you chose to load .hex file make sure you exported it using python editor not MakeCode Editor

### Flashing the Chip
After writing the code and extracting .hex file using the online editor then it is time to program the chip.
1. Connect micro:bit using the micro USB cable.
2. micro:bit will show in your computer as a drive.
3. Copy the .hex file to micro:bit drive.
4. You can now disconnect micro:bit and start using the program.
5. You can click the reset button on the back of micro:bit to start the program from the beginning.

## Examples and Tutorials

* [Micro Chat](microchat): As start you can start with micro chat, a small application that allows sending messages between microbits
* [Hot Or Cold](hotorcold): a game in which you should find hidden microbits.
* More examples and tutorials are available on [makercode website](https://makecode.microbit.org/)
