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
// determines the display type icon or number
let display = 0
// set group number
radio.setGroup(1)
// event triggered when a number is received
radio.onReceivedNumber(function (receivedNumber) {
    // get the received signal strength
    signal = radio.receivedSignalStrength()
    // checks if display is set to zero then show icon
    if (display == 0) {
        // check signal strength
        if (signal < -90) {
            // show icon from the predefined list
            basic.showIcon(IconNames.SmallDiamond)
        } else if (signal < -80) {
            basic.showIcon(IconNames.Diamond)
        } else {
            basic.showIcon(IconNames.Square)
        }
    } else {
        // show numbers if display is not zero
        basic.showNumber(signal)
    }
})
// event triggered when button is pressed change
// display type to icon
input.onButtonPressed(Button.A, function () {
    display = 0
})
// event triggered when button is pressed change
// display type to numbers
input.onButtonPressed(Button.B, function () {
    display = 1
})

```
