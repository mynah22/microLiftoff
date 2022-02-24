This guide is accurate as of february 2022:

1) ensure python 3 is installed on your machine
2) download VSC from https://code.visualstudio.com/download and install
3) open the extensions menu, either by clicking the blocks icon on the left of the VSC window, or `ctrl + shift + x`
4) open your project folder with `file > open folder`
5) to enable autocompletion, on the bottom bar of VSC window click "all commands", then in command palette select 'Pico Go > configure Project'
6) recommended extensions will be presented on the left of the VSC window, install them all, then reload
7) Terminal should load on the bottom of the VSC window, if not press `ctrl + \` ` to open it up
7) make sure the 'Pico Console' is the console highlighted on the right of the terminal section 

9) once your device is flashed with the circuitpython firmware (see [Setup Guide](https://github.com/mynah22/microLiftoff/tree/main/qtpy-esp32s2/setup.md)), connect your microcontroller with circuitpython firmware, and hit the X symbol labeled 'pico disconnected' on the bottom of the VSC window. This will connect to your microcontroller and change the label to 'pico connected' with a check mark
10) ctrl + d will cancel the main program if it is running, and allow access to the REPL. 
11) you can also hit 'run' via the play button symbol in the top right of the window. In my experience this works only when the file is saved