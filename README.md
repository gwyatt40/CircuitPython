# CircuitPython
## Hello Circuit Python 
### Description

This was an introduction to Circuit Python using an Arduino Metro. I used the Caret text editor and uploaded a code that caused a red light to glow on the Metro board. 

### Evidence

```C++
import board
import neopixel //board and neopixel libraries added to circuit py


dot = neopixel.NeoPixel(board.NEOPIXEL, 1)


print("Make it red!") //serial monitor print


while True:
     dot.fill((50,0,0)) //loop controlling brightness of LED

 ```

### Image

<img src="Images/RedLight.png" alt="Hello Circuit Python Red Light" width="350" height="350">


### Reflection
 
Lessons Learned:

- In order to upload code to the Metro from Caret, you must first type it into the Caret platform, save it as a .py file, and then connect the board and drag the code file into the CIRCUITPY section of the files application. 
- To edit the code while it is connected to the Arduino, open the file in Caret, edit it, and then press save with the new changes. 
- "while True:" is basically the Circuit Python version of Void Loop. 
- You must import information into the Circuit Python code in order for it to understand specific functions. (i.e. import board, import time, import neopixel) 
- Eject Arduino from files (by clicking up arrow next to CIRCUIT PYTHON) before unplugging it. 
- Helpful website I used to figure everything out: [Adafruit: Using Circuit Python on a Chromebook](https://learn.adafruit.com/using-circuit-playground-express-makecode-circuitpython-on-a-chromebook/caret-editor) 



## CircuitPython Servo
### Description
This was a two-step project, the first step was to wire a servo so it would continuosly move back and forth 180 degrees. The next step was to set up capacitive touch with two wires so that the servo would move one way or the other depending on which wire was pressed. 

### Evidence
```C++

import time
import board
import pulseio
import touchio
from adafruit_motor import servo
 
# create a PWMOut object on Pin A2.
pwm = pulseio.PWMOut(board.A2, frequency=50)
 
# Create a servo object, my_servo.
my_servo = servo.ContinuousServo(pwm)

touch_A0 = touchio.TouchIn(board.A0)  # Not a touch pin on Trinket M0!
touch_A1 = touchio.TouchIn(board.A1)  # Not a touch pin on Trinket M0!
 
while True:
   
    if touch_A0.value:
        print("Touched A0!")
        my_servo.throttle = 1.0
        time.sleep(2.0)
        
    if touch_A1.value:
        print("Touched A1!")
        my_servo.throttle = -1.0
        time.sleep(2.0)
        

 ```

### Video

[CircuitPython Servo Video](https://github.com/gwyatt40/CircuitPython/blob/main/Images/IMG_0130.MOV)
     


### Reflection 
- Capacitive touch works for all analog pins (A0-A5) on Arduino Metro Express. 
- Can't just tap the wire, have to make sure that it is pressed enough to activate the pin. 
- As always, GOOGLE TO FIND CODE. And read through the website so you can be sure you're using the right version. 
- When shifting between testing multiple codes, only one can be named code.py and run, so other codes should be given test names, and can switch names out to run them.
- If you change the pins in the original code, make sure you change evey instance of the pin. 
- Websites I used: 
     - [Adafruit CircuitPython Servo](https://learn.adafruit.com/circuitpython-essentials/circuitpython-servo) 
     - [Adafruit CircuitPython Cap Touch](https://learn.adafruit.com/adafruit-metro-m0-express-designed-for-circuitpython/circuitpython-cap-touch)
     
 

