**Connecting to a wireless network is actually very straightforward with circuitpython on the esp32-s2 QTpy**

There are no special libraries needed to scan for and connect to wireless netowrks, the `wifi` module provides those basic features:

- **Scan networks**
    ```
    from wifi import radio
    for network in radio.start_scanning_networks():
        print(network.ssid)
        print("    channel: "+str(network.channel)+"\n    sig strength (db): "+str(network.rssi))
    radio.stop_scanning_networks()
    ```
- **Connect to network**
    ```
    from wifi import radio
    radio.connect("your SSID here", "yourPassHere")
    print(radio.ipv4_address)
    ```
- **Ping**
    ```
    from wifi import radio
    from ipaddress import ip_address
    pingtarget=ip_address("8.8.8.8")
    radio.connect("your SSID here", "yourPassHere")
    print("Pinging 8.8.8.8:   "+str(radio.ping(pingtarget)*1000)+"ms")
    ```

At this point the **adafruit requests** library is going to greatly simplify http requests

Grab the whole bundle of adafruit libraries for your ciruitpython version at: circuitpython.org/libraries

libraries are installed by placing them in the `lib` folder in your circuitpython drive. The library is named `adafruit_requests/`

- **Basic HTTP request**
    ```
    from wifi import radio
    import ssl
    import socketpool
    import adafruit_requests as requests

    radio.connect("your SSID here", "yourPassHere")

    pool = socketpool.SocketPool(radio)
    requestSession = requests.Session(pool, ssl.create_default_context())

    print(requestSession.get("https://csu.org").text)
    ```
Now you are really cooking with gas - connected to a wifi net and communicating over ssl in just a couple lines of code, on a microcontroller! 

Another great way to parse aquirred data is in JSON format:
- **JSON parsing**
    ```
    from wifi import radio
    import ssl
    import socketpool
    import adafruit_requests as requests
    
    radio.connect("your SSID here", "yourPassHere")
    pool = socketpool.SocketPool(radio)
    requestSession = requests.Session(pool, ssl.create_default_context())
    response=requestSession.get("https://api.github.com/repos/fritzing/fritzing-app")
    print("stars on Fritzing repo:")
    print(response.json()['stargazers_count'])
    ```

You can do other request types, such as a POST to send data / control info

- **POST**
    ```
    from wifi import radio
    import ssl
    import socketpool
    import adafruit_requests as requests

    radio.connect("your SSID here", "yourPassHere")
    postData={"humidity":"25%", "temperature":"69deg", "datetime":"13:52   1/20/1999", "roomname":"livingroom"}
    pool = socketpool.SocketPool(radio)
    requestSession = requests.Session(pool, ssl.create_default_context())
    requestSession.post("http://your.server.address/datainputscript", data=postData)
    ```


This guide was distilled from the guide here: https://learn.adafruit.com/adafruit-metro-esp32-s2/circuitpython-internet-test