# OctoPrint Mini Guide
A complete guide for setting up Octoprint for the Prusa Mini.

## What You Need
This guide will be more useful if you have all the equipment required. Here is a list:

- [ ] Prusa Mini 3D Printer
- [ ] Raspberry Pi (Raspberry Pi A, B, A+, B+, 2B, 3A+, 3B, 3B+, 4B 1/2/4GB, don't bother with zero models) w/ a power cord. The faster the model the better.
- [ ] SD card (the bigger then better, especially if you have a camera)
- [ ] A USB or raspberry pi compatible camera (optional but highly recommended)
- [ ] A USB A to USB micro cord

## Setup
Now it's time to set it up.

### Download and Flash Octoprint

1. Download the Etcher applicatoin to flas the SD card: https://www.balena.io/etcher/
2. Go to https://octoprint.org/download/ and download the latest OctoPrint image.
3. Insert your SD card into your computer.
4. Open Etcher
    - Click on "Flash from file" and select your newly downloaded OctoPrint image.
    - Click on "Select target" and select the sd card drive.
    - Click on "Flash!" and wait until flash drive is finished.

### Setup Wi-Fi
If you plan on using ethernet, skip this step.

1. Download the Sublime Text Editor: https://www.sublimetext.com/3
2. On your computer navigate to the newly flashed SD card. There will be a file called ```octopi-wpa-supplicant.txt```. Open this in sublime text.
3. Change the WPA 2 section with your SSID and Wi-Fi password (at least you should be using this vs WEP or no security). This is shown below.
4. Save ```octopi-wpa-supplicant.txt``` and close sublime text.

__Before__
```
## WPA/WPA2 secured
#network={
#  ssid="put SSID here"
#  psk="put password here"
#}
```
__After__
_This assumes the wi-fi network you are connecting to is called "YourWifi" and the password to connect to it is called "yourwifipassword"_
```
## WPA/WPA2 secured
#network={
#  ssid="YourWifi"
#  psk="yourwifipassowrd"
#}
```
Go here for more detailed instructions: https://community.octoprint.org/t/wifi-setup-and-troubleshooting/184

### Setup OctoPrint
Now it's time to setup OctoPrint specific to you. This includes setting up better security, your mini printer, etc. First we start with the command line, then we will complete the setup using the OctoPrint web interface.

#### Power up your OctoPrint server
In order to setup OctoPrint it's time to power it up.

1. Remove the mini sd card from your computer and insert it into your raspberry pi. 
2. Connect power to your raspberry pi.

#### Command Line Setup
This will setup some system level settings (Linux):

1. Log into your Pi via SSH (it is located at octopi.local if your computer supports bonjour or the IP address assigned by your router), 
    - default username is “pi”, default password is “raspberry”. 
2. Run ```sudo raspi-config```. Once that is open:
3. Change the password via “Change User Password”
4. Change the configured timezone via “Localization Options” > “Timezone”.

#### OctoPrint Setup (web interface)
Finally we are really to setup your mini printer and OctoPrint stuff

##### Print bed & build volume

| Setting Name | Prusa Mini Value |
| --- | --- |
| Form Factor | Rectangular |
| Origin | Lower Left |
| Heated Bed | true |
| Heated Chamber | false |
| Width (X) | 180mm |
| Depth (Y) | 180mm |
| Height (Z) | 180mm |
| Custom Bounding Box | true |
| X Coordinates | 0 / 180 |
| Y Coordinates | -4 / 180 |
| Z Coordinates | 0 / 180|

##### Axes

| Setting Name | Prusa Mini Value |
| --- | --- |
| X | 10800 mm/min |
| Y | 10800 mm/min |
| Z | 720 mm/min |
| E | 4800 mm/min |

##### Hot end & extruder

| Setting Name | Prusa Mini Value |
| --- | --- |
| Nozzle Diameter | 0.4 mm |
| Number of Extruders | 1 |

## Plugins
Plugins allow developers to expand the base functionality of OctoPrint. There are at least a couple of plugins that should be considered "must haves" for mini owners. Each plugin can consume addition resources which can result in degraded printing performance if OctoPrint is slow to send the current g-code instructions over the serial connection as a result of your raspberry pi's CPU being too high. 

### Must Have Plugins
Here are the plugins you should defenitley install:

| Plugin Name | Description |
| --- | --- |
| baz | bim |

## Common Issues

1. a

  2. b
  
    3. c
    
## Sources

