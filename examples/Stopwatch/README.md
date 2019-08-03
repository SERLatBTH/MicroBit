# Stopwatch

Stopwatch is a familiar app, its purpose is to measure or count the time in seconds for an interval. It's straight forward, you press button A to start the count, then an led will flash indicating that the counter is working, press button A again will stop the count and show the elapsed time since last time the button is clicked

This tutorial will show you the JavaScript code step by step

1. We will need two variables, results which will hold the total elapsed time in seconds and start_time which will hold the time when we start counting.
```JavaScript
let result = 0
let start_time = 0
```

2. Now we need to specify what happens when button A is pressed. We can do that by calling input.onButtonPressed(), which is an event that will trigger when a button is pressed, we need to pass to it the button letter and a function.

```JavaScript
input.onButtonPressed(Button.A, function () {

})
let result = 0
let start_time = 0
````

3. When button A is pressed one of two actions should take place based on two conditions. The first is when the counter is not started yet, we can find that by checking the start_time value to see if it is zero then that means the button is not pressed and the counter is idle, at this point we start the counter by assigning value to start_time and start flashing the led.

```JavaScript
input.onButtonPressed(Button.A, function () {
    if (start_time == 0) {
        start_time = input.runningTime()
        while (true) {
            led.toggle(2, 2)
            if (input.buttonIsPressed(Button.A)) {
                break
            }
        }
    }
})
let result = 0
let start_time = 0
start_time = 0
```

4. The second condition is when button A is already pressed and the counter is running, at this point we will calculate the time elapsed and then show the time on the Leds twice, after that we reset the start_time variable to zero and clear the screen so the user can measure another time interval. Below is the final code.

```JavaScript
input.onButtonPressed(Button.A, function () {
    if (start_time == 0) {
        start_time = input.runningTime()
        while (true) {
            led.toggle(2, 2)
            if (input.buttonIsPressed(Button.A)) {
                break
            }
        }
    } else {
        result = Math.idiv(input.runningTime() - start_time, 1000)
        for (let index = 0; index <= 1; index++) {
            basic.showNumber(result)
        }
        start_time = 0
        basic.clearScreen()
    }
})
let result = 0
let start_time = 0
start_time = 0
```
