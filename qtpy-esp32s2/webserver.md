##  Parse POST data with the python3 `http.server` module  ##

This is a guide demonstrating how to set up a webserver on a computer/SBC that you can use to capture data from a microcontroller via HTTP

- spinning up a cgi aware web server is literally a single line of python: `sudo python3 -m http.server --cgi 80`
    - the directory you execute this command in will be the root of your webserver, so you may want to create a new folder and spin the server up there
- consider the following example:
    - create a folder in the webserver root named `cgi-bin` (this is the default location for serverside scripts) 
    - within `cgi-bin` create a file named `recordTemp.py` with the following contents:
        ```
        #!/usr/bin/env python3
        import cgi
        form=cgi.FieldStorage()
        temperatureFilePath = 'temp.txt'

        currentTemperature=form['temperature'].value

        with open(temperatureFilePath, 'w') as f:
            f.write(currentTemperature)
        ```
    - make sure the script is executable: `sudo chmod +x recordTemp.py`
    - and create the temperature file in the webserver root: `touch temp.txt` , and set permissions `chmod 666 temp.txt`
    - now when a client submits a POST request to http://yourHostname.domain.xyz/recordTemp.py with a value in the `temperature` field it will be written to the `temp.txt` file on the server. Life is good!