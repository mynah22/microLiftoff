**Neopixels are individually addressable RGB LEDs. There is even one built in to this board**

The `neopixel` library is your friend here, grab the whole bundle of adafruit libraries for your ciruitpython version at: circuitpython.org/libraries
libraries and modules are installed by placing them in the `lib` folder in your circuitpython drive. The module is named `neopixel.mpy`

To set the onboard neopixel to a given color (green at full birghtness in this example), this is all that is needed:
```
from neopixel import NeoPixel
from board import NEOPIXEL

pixels=NeoPixel(NEOPIXEL, 1)
pixels[0] = (0,255,0)
```

colors are encoded in RGB format with 1-byte precision (0-255)