1) connect board to pc with a data-capable cord. The neopixel should be flowing through colors
2) the reset button is the one furthest from the usb port on the board. You will press the button twice:
   a) the first press will cause the neopixel to go purple for a brief moment
   b) if pressed a second time *during the moment the light is purple*, the board will enter uf2 bootloader mode. The light will go green if a data connection can be established, if it stays red try a different cable or usb port. 
3) once in uf2 bootloader mode with a green light, the board should appear as a usb storage device.
4) copy the latest circuitpython firmware for the board (https://circuitpython.org/board/adafruit_qtpy_esp32s2) onto the storage device. The board should automagically reboot.
5) once rebooted the board will expose a different storage device (default circuitpython behavior). A file named `code.py` or `main.py` is run as the main program, while `boot.py` is run prior to the main script, and allows configuration of features that can only be enabled or disabled at boot (midi, usb storage device, usb HID device). Saving `code.py` or `main.py` will cause the board to automatically reboot and run the code. 

lots of other great starting info can be found here: https://learn.adafruit.com/adafruit-qt-py-esp32-s2/overview 