# Hot Or Cold

Is a game in which you should find hidden microbits before other players. There are two types of microbits in this game, beacons and hunters. A Beacon is a hidden microbit that it emits a signal. A Hunter is the microbit in hand that is used to find beacons by detecting the signal sent by beacons.

## JavaScript

## Beacon
A beacon will emit a signal by sending number. An icon will display indicating that it is sending. The patter will keep repeating forever.

```
//set group number
radio.setGroup(1)
//enable transmit of serial number
radio.setTransmitSerialNumber(true)
//set the transmit power of the radio signal
radio.setTransmitPower(6)

//a loop to keep always excuting
basic.forever(function () {
    //send number
    radio.sendNumber(0)
    //show heart icon indicating it is sending
    basic.showIcon(IconNames.Heart)
    basic.showIcon(IconNames.SmallHeart)
})
```

## Hunter
The hunter will be used to find beacons. When the hunter receives a number it will store the signal strength. Then it will display the value of the signal strength or an icon that represents how close the beacon is from the hunter. The player can choose to show number or icon.

```
// variable to store received signal strength
let signal;
// set group number
radio.setGroup(1)
// event triggered when a number is received
radio.onReceivedNumber(function (receivedNumber) {
    // get the received signal strength
    signal = radio.receivedSignalStrength()
    // check signal strength
    if (signal < -90) {
        // show icon from the predefined list
        basic.showIcon(IconNames.SmallDiamond)
    } else if (signal < -80) {
        basic.showIcon(IconNames.Diamond)
    } else {
        basic.showIcon(IconNames.Square)
    }
})

```

### Multiple Beacons

To make the game more interesting, we are going to modify the code of the hunter to distinguish between different beacons signals. When a new beacon is found then it is added to an array of beacons and the score for the player will increase. We can distinguish between different beacon by reading the serial number from the received signal (number or string), since we already enabled send serial number in beacons code no changes needed to that code. When button B is pressed it will show the score.

```
// variable to store received signal strength
let signal = -200
// stores the received serial number
let serialNumber = 0
// array to store found beacons
let beacons: number[] = []
// player score
let score = 0
// set group number
radio.setGroup(1)
// event triggered when a number is received
radio.onReceivedNumber(function (receivedNumber) {
    // get the received signal strength
    signal = radio.receivedSignalStrength()
    // get the recieved serial number
    serialNumber = radio.receivedSerial()
    // clear leds
    led.stopAnimation()
    // check signal strength
    if (signal < -90) {
        // show icon from the predefined list
        basic.showIcon(IconNames.SmallDiamond)
    } else if (signal < -80) {
        basic.showIcon(IconNames.Diamond)
    } else {
        basic.showIcon(IconNames.Square)
        // check if the signal is from new beacon
        // this means that the player have found new beacon
        if (signal > -50 && beacons.indexOf(serialNumber) < 0) {
            // add it to the list
            beacons.push(serialNumber)
            // increase the score by one and display it
            score++
            basic.showNumber(score)
        }
    }
})
// event triggered when button is pressed change
// display type to numbers
input.onButtonPressed(Button.B, function () {
    // clear leds
    basic.showNumber(score)
})
```
