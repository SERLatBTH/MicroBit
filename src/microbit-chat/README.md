# Micro Chat


## Blocks



## JavaScript

chat-1

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

chat 2

```
input.onGesture(Gesture.Shake, function () {
    radio.sendString(message)
    basic.showLeds(`
        . . # # #
        . . . # #
        . . # . #
        . # . . .
        # . . . .
        `)
    message = ""
    index = -1
    basic.pause(200)
    basic.clearScreen()
})
input.onButtonPressed(Button.A, function () {
    index += 1
    if (index >= alphabet.length) {
        index = -1
    }
    basic.showString("" + alphabet[index])
})
radio.onReceivedString(function (receivedString) {
    basic.showIcon(IconNames.Sword)
    basic.showString(receivedString)
})
input.onButtonPressed(Button.B, function () {
    message = "" + message + alphabet[index]
    index = -1
})
let message = ""
let alphabet: string[] = []
let index = 0
index = -1
alphabet = ["A", "B", "C"]
```
