# Micro Chat

## Blocks
To write code in blocks, you should follow those steps.
1. Open the [editor](https://makecode.microbit.org/#)
2. Start new project
3. Add code by dragging blocks from the left side panel and into the white canvas.

## JavaScript
To write code in JavaScript start by doing the following.
1. Open the [editor](https://makecode.microbit.org/#)
2. Start new project
3. Switch to JavaScript on the top.

### Chat-1

1. Start by writing the following code.
   ```
   input.onButtonPressed(Button.A, function () {

   })
   ```
   input represents micro:chip's interfaces, i.e input buttons, sensors (temperature, light, compass...etc). input give you access to events triggered when specific action take place, e.g. onButtonPressed() which is triggered when a user press on a button of the micro:bit.
   onButtonPressed(parameter1, parameter2) takes two parameters, parameter1 is the button which this event is triggered for when pressed, parameter2 is a function, inside the function we will write the code that we want to execute when the button is pressed.

2. Inside onButtonPressed() we send a message by using radio.sendString("Hej!"). This will transfer messages using radio signal between micro:bit boards.
    ```
    radio.sendString("Hej!")
    ```
3. We show animation so we know we sent a message basic.showLeds('') with the shape we want to send (5x5). Then we pause for few milliseconds basic.pasue(200) before we clear the screen using basic.clearScreen() this gives you more time to see the icon before it disappears.
    ```
    basic.showLeds(`
        . . # # #
        . . . # #
        . . # . #
        . # . . .
        # . . . .
        `)
    basic.pause(200)
    basic.clearScreen()
    ```
4. To receive messages we use radion.onReceivedString() which takes a function with one parameter which is the received string. Inside the event we write basic.showString(receivedString) which will show the received string on the screen.
    ```
    radio.onReceivedString(function (receivedString) {
        basic.showString(receivedString)
    })
    ```
2.  The final code would looks like this.

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

### Chat-2

Now we are going to enhance our app a little more and try to extend it. Instead of a pre-set phrases we are going to let the user write the word they want to send, and add an animation on receiving of the message.
1. We define the following variables. message which stores the entire message that is going to be sent, alphabet as an array of letters and index to navigate alphabet array.

    ```
    let message = ""
    let alphabet: string[] = []
    let index = 0
    index = -1
    alphabet = ["A", "B", "C", "D", "E", "F"]
    ```
2. We move the code inside onButtonPressed(Button.A, function()){...} to input.onGesture(Gesture.shake, function()){...} and we reset message and index to initial values.

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

    ```
3. In onButtonPressed(Button.A, function()){...}, we increase index by 1, then we check if the index reached alphabet.length, which means it is out of range and we reset it there. Now we show the string to user to know if this is the letter they want basic.showString(alphabet[index]).
    ```
    input.onButtonPressed(Button.A, function () {
        index += 1
        if (index === alphabet.length) {
            index = 0
        }
        basic.showString(alphabet[index])
    })
    ```
4. We add the event onButtonPressed for button B and inside we add the letter on screen to the message variable. and reset index to -1.
    ```
    input.onButtonPressed(Button.B, function () {
        message = message + alphabet[index]
        index = -1
    })

    ```

5. Then to show animation when a message received we add basic.showIcon(IconNames.Sword) inside onReceivedString() .
    ```
    radio.onReceivedString(function (receivedString) {
        basic.showIcon(IconNames.Sword)
        basic.showString(receivedString)
    })
    ```
6. At the moment the message sent using radio can be read by any other micro:bit in the area. What if we want to avoid interference and conflict? what if we have more than one group using micro:bit in the same area. In this case we can use group id. By setting the group id micro:bit will only receive messages from micro:bit within this specific group id. To achieve this use the command radio.SetGroup(number) where number referrers to the group number and range between 0 and 255.
    ```
    radio.SetGroup(50)
    ```
7. After making the changes and extending it, the final code should looks like.
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
            index = 0
        }
        basic.showString("" + alphabet[index])
    })
    radio.onReceivedString(function (receivedString) {
        basic.showIcon(IconNames.Sword)
        basic.showString(receivedString)
        basic.clearScreen()
    })
    input.onButtonPressed(Button.B, function () {
        message = "" + message + alphabet[index]
        index = -1
    })
    let message = ""
    let alphabet: string[] = []
    let index = 0
    index = -1
    alphabet = ["A", "B", "C", "D", "E", "F"]
    radio.setGroup(132)

    ```
