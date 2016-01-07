# Thinking Cleaner for Homebridge

Homebridge is a lightweight NodeJS server you can run on your home network that emulates the iOS HomeKit API. [Learn more about Homebridge](https://github.com/nfarina/homebridge)

This is a plugin to control your Thinking Cleaner via HomeKit. 
Since Siri supports devices added through HomeKit, this means that with Homebridge you can ask Siri to control your Thinking Cleaner! For example you can say _`Siri, turn Dusty on.`_ and your Roomba will start cleaning!

Or you can use a Homekit app for iOS to create scenes and start claning your house when you say: 

 * _Siri, I'm leaving._
 
The possibilities are endless!
 
# Installation

### Homebridge
If you haven't installed Homebridge yet, use these steps on the Homebridge page to get it up and running: [Learn more about the Homebridge installation](https://github.com/nfarina/homebridge)

### Thinking Cleaner plugin

First of all we are going to install the Thinking Cleaner plugin by executing:

    sudo npm install -g homebridge-thinkingcleaner

As easy as that! Now let's configure the plugin.

# Configuration

**We expect you have created a `config.json` already using the steps on the [Homebridge](https://github.com/nfarina/homebridge) page**

Now we are going to add the Thinking Cleaner accessory to the `config.json` file. In the `config.json` add the following to the `accessories` section:

```JSON
{
    "platform": "Roomba",
    "name": "Dusty",
    "ip_address": "127.0.0.1"
}   
```

For example:
 ```JSON
"accessories": [
    {
        "platform": "Roomba",
        "name": "Dusty",
        "ip_address": "127.0.0.1"
    }   
]
```

Replace `Dusty` with the name you gave your Thinking Cleaner during setup. (You don't necessarily have to enter the same name as you entered during setup, but it's recommended). *_This is also the name Siri will use for control_*

If you do not know the IP address of your Thinking Cleaner, simply leave it blank and your Thinking Cleaner will be discovered automatically.
**NOTE**: When you have multiple Thinking Cleaner devices, you **must** fill in the IP address

# Using

Now you should be able to run Homebridge again and the Thinking Cleaner plugin ready for usage:

    $ homebridge
    Loaded plugin: homebridge-thinkingcleaner
    Registering accessory 'homebridge-thinkingcleaner.Roomba'
    ---
    Loaded config.json with 1 accessories and 0 platforms.
    ---
    Loading 0 platforms...
    Loading 1 accessories...
    [Dusty] Initializing Roomba accessory...

Homebridge is now ready to receive commands to control your Thinking Cleaner via HomeKit!

**Siri note**: The way I added the Thinking Cleaner to HomeKit is by pretending the Thinking Cleaner is a switch: turn on to start cleaning and turn off to stop and dock. Note that you can't say _`Siri, start cleaning.`_ as HomeKit doesn't support (robot) vacuum cleaners (yet)