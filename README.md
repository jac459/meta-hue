# meta-hue
Philips Hue control using the meta driver

Support the new need jac459/meta.

https://www.youtube.com/watch?v=Kld_LGcWAuM

https://www.youtube.com/watch?v=bJgt0cqvB9M


## Setup
### Step 1 : Install in the meta
#### Prerequisite
In order to use this file, you need to have the metadriver installed. Please refere to this page for further instructions:
https://github.com/jac459/meta
#### Installation
To install, downnoad the file you want and move it to the "activated" folder.
philipsHue.json ==> control your bulbs.
philipsHueGroup.json ==> control your grous (room and zones).

Restart the metadriver :

### Step 2 : Install in the neeo app
In the neeo app, add a device and search for Meta or Hue until you find the drivers.
When you load the driver the first time, follow the instructions in order to grant access to you HUE Bridge.
/!\ Important if you make a wrong manipulation or change your HUE Bridge and want to refresh the HUE drivers, you need to delete the ****-datastore.json** files. This files are created by the metadriver in order to save your HUE keys as well as IP address, etc...
##### If you use the non-sliders devices.
You will find your devices in the room you have put the driver in under the light nomination.
##### Ensure your using POWER ON and POWER OFF when launching and Closing the recipe.
Power On and Power Off are the events used by the meta in order to listen to the device.
In your case, if you don't do it, you will not be able to see the state change in your Hue through the hue application.
if you put all the device under one device, you need to call all power on and off individually.
##### Choose your shortcuts.
when loading the recipe, you can suppress all the slides except the ones with shortcuts. 

## Usage
It is pretty much like the neeo HUE except that you have the color picker.
Also, the slider goes to 0 when you switch the light off ==> This part is a bit buggy as events can be lost ny neeo (nothing I can do). Depending on your case you may prefere going to the slider based driver wich are much more reliable.'

## Troubleshooting

### I wrongly pressed the next button 
If you didn't follow the right process, you may need to restart from scratch the process.
To do that, you may have to delete the -DataStore.json file created when you did the setup.
You can delete it through the meta-core driver directly through the interface if you use a RPI.
If you don't, you need to go in the meta folder and then the /active folder and look for the -datastore related to your driver.
Suppress it. Restart the meta. Restart the setup process.

### I can't find any HUE Bridge.
If you don't have a standard install of the meta (on a RPI) or a complex network with a mDNS blocker, you may not be able to discover the HUE automatically.
In this case, you will need to go in your meta folder and look for a file named (exactly with the right casing) resultsDiscovery.json.
If the file exists, update it. If the file doesn't exist, create it and update it.

This file is written in JSON format and should look like that (not listing particularly only your hue but all your devices (in this example you can see google home devices)):

```
[
    {
        "name": "googlerpc-1._googlerpc._tcp.local",
        "ip": "192.168.30.148",
        "mac": "48:b0:2d:3d:3a:23",
        "short": "_googlerpc._tcp.local",
        "port": 8012
    },
    {
        "ip": "192.168.30.148",
        "mac": "48:b0:2d:3d:3a:23",
        "port": 10001
    },
    {
        "name": "googlerpc._googlerpc._tcp.local",
        "ip": "192.168.30.178",
        "mac": "94:be:44:a9:c3:5e",
        "short": "_googlerpc._tcp.local",
        "port": 8012
    },
    
   .......
  
]
```

Each entries in this list correspond to one of your devices. 

If you don't have a Hue entry, you should add to the file an entry like that:
```
    {
        "name": "Philips Hue - 74250E._hue._tcp.local",
        "ip": "192.168.50.242",
        "mac": "0",
        "short": "_hue._tcp.local",
        "port": 443
    }
```

What is important here is to keep the name as it is and replace the IP by your own bridge IP.

BE CAREFUL:
In Json, the last item in a list shouldn't have a comma after it. BUT if you have a list each other items than the last one should have a comma at the end.










