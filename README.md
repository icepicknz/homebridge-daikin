# homebridge-daikin

Supports Daikin Air Conditioners on HomeBridge

Initially will be built to support talking to a Daikin BRP072A42 Wifi Adapter for a FTXS series Split System Air Conditioner, and once that's working, aim to add support for other Daikin Wifi adapters and Air Conditioners as the information becomes available

# Installation

NOT YET SET UP ON NPM, THESE STEPS ARE NOT YET VALID

1. Install homebridge using: npm install -g homebridge
2. Install this plugin using: npm install -g homebridge-daikin
3. Update your configuration file. See sample-config.json in this repository for a sample. 

# Configuration

Configuration sample:

 ```
    {
        "bridge": {
            ...
        },
        
        "description": "...",

        "accessories": [
            {
                "accessory": "Daikin Air Conditioner",
                "name": "Daikin Demo",
                "apiroute": "http://myurl.com"
            }
        ],

        "platforms":[]
    }
```
# API Expectations

The `apiroute` is used for two main calls: Get info such as current activity and sensor readings from the thermostat and set the target temperature and modes. The Aircon LAN adapter provides two directories for these settings and data:

1. `/common` uses POST and GET methods for control and system information about the Aircon (e.g software version, MAC address, Reboot System, Region)

2. `/aircon` uses POST and GET methods to set Aircon related information (e.g Target Temperature, Modes like Heat and Cool, Temperature Sensor Readings, Timers)

# Credit

This whole plugin is based on homebridge-thermostat, tuned just for Daikin units specifically. Please check out the original (https://github.com/PJCzx/homebridge-thermostat) and if you have any improvements that are not specific to Daikin systems, contribute there!

Information for the HTTP GET and POST requests is vastly informed from daikin-control (https://github.com/ael-code/daikin-control) with a bit of testing with my own unit to verify commands and find additional settings