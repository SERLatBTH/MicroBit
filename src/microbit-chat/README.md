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
basic.forever(function () {

})

```


<div style="position:relative;height:calc(300px + 5em);width:100%;overflow:hidden;"><iframe style="position:absolute;top:0;left:0;width:100%;height:100%;" src="https://makecode.microbit.org/---codeembed#pub:_HTwCVURFxeRk" allowfullscreen="allowfullscreen" frameborder="0" sandbox="allow-scripts allow-same-origin"></iframe></div>
