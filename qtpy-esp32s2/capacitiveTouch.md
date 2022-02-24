**Implementing capacitive inputs is trivial**

The QT Py boards come with several pins that can be used as capacitive sensors. On the ESP32-S2 QT Py these are **A2, A3, SDA, SCL** and **TX**.

An example using A2 would look like:
```
from time import sleep
from board import A2
from touchio import TouchIn

touchpad=TouchIn(A2)

while True:
    if touchpad.value:
        print('detecting touch')
    sleep(0.01)
```
Screws, nails, fruit, and other objects can now become inputs for your system.