# meta-hue
Philips Hue control using the meta driver

Support the new need jac4599/meta.

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
Also, the slider goes to 0 when you switch the light off ==> This part is a bit buggy as events can be lost ny neeo (nothing I can do). Depending on your case you may prefere going to the slider based driver wich are much more reliable.
