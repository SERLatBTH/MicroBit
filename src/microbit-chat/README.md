# Micro Chat


## Blocks



## JavaScript

```
input.onButtonPressed(Button.A, function () {
    radio.sendString("Hej!")
    basic.showLeds(`
        . . # # #
        . . . # #
        . . # . #
        . # . . .
        # . . . .
        `)
    basic.pause(200)
    basic.clearScreen()
})
radio.onReceivedString(function (receivedString) {
    basic.showString(receivedString)
})

```
