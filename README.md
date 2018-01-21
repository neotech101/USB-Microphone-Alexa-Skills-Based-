# USB-Microphone
## Based on Microphones


## Table of Contents
1. [Introduction](#introduction)
2. [Bill of Materials/Budget](#bill-of-materialsbudget)
3. [Time Commitment](#time-commitment)
4. [Mechanical Assembly](#mechanical-assembly)
5. [Soldering](#soldering)
6. [Power up](#power-up)
7. [Unit Testing](#unit-testing)
8. [Production Testing](#production-testing)
9. [Is it Reproducible?](#reproducible)


### Introduction

Welcome to the introduction part of my Project i.e. USB-Microphone(Alexa-Skills Based).USB-Microphone is basically a microphone that we plug into the raspberry pi and it is being used for the Voice Recognition. 

The motive of this project is to replicate the skills of Alexa and make a device that reads your audio and give feedback accordingly. I have added speakers to my Project materials as we want the audible and clear feedback. This Project helps you understand the connectivity between various parts of rasperry Pi and USB Microphone 


#### System Diagram

![System Diagram](https://github.com/PRana02/USB-Microphone-Alexa-Skills-Based-/blob/master/system%20diagram%20alexa.jpg)


### Bill of Materials/Budget
The materials required to build the USB-Microphone are Raspberry Pi 3, SunFounder USB 2.0 Mini Microphone for Raspberry Pi 3 and Logitech Z130 Compact Computer Speakers.

1) Raspberry Pi 3 (CanaKit Starter Kit):

* [Amazon](https://www.amazon.ca/CanaKit-Raspberry-Complete-Starter-Kit/dp/B01CCF6V3A/ref=sr_1_2?s=electronics&ie=UTF8&qid=1516549400&sr=1-2&keywords=rapberry+pi) CAD $99.99

2) USB 2.0 Mini Microphone:
 
* [Amazon](https://www.amazon.ca/SunFounder-Microphone-Raspberry-Recognition-Software/dp/B01KLRBHGM/ref=sr_1_1?s=electronics&ie=UTF8&qid=1516549033&sr=8-1&keywords=sunfounder+usb+microphone) CAD $39.46 
* [Ebay](https://www.ebay.ca/itm/SunFounder-USB-2-0-Mini-Microphone-for-Raspberry-Pi-3-2-Module-B-RPi-1-Model/232430660307?hash=item361df26ad3:g:bYIAAOSwySFZf1pf) US $8.62

3) Logitech Z130 Compact Computer Speakers:

* [The Source](https://www.thesource.ca/en-ca/computers-and-tablets/computer-accessories/computer-speakers/logitech-z130-compact-computer-speakers/p/108008204) CAD $39.99

At the time when I bought the materials, the raspberry pie was $112.99, Sunlight sensor was $36.64 and Connector interface for the raspberry pi was $36.17, plus the shipping $15.41. The total cost for buying the materials was $201.21.

### Time Commitment
This project can be completed in a couple of days if you followed the mechanical assembly and the diagram. From my experience it took me 1 to 2 weeks to complete the build. I first had to order the materials which will take around a week to arrive. Once you receive the materials, I set up the raspberry pi which took around 3 hours. Connection the parts to the raspberry pi took around 30-60 minutes. And then setting up the code on the raspberry pi and testing the code took around a 1 hour.

Overall, I think the needed time to complete this build should be around 3 hours daily for 2-3 days.

### Mechanical Assembly

1) First, power of the Raspberry Pi
2) Next, will be connecting the connector interface to the Raspberry pi 3. While holding the connector interface, align the pins on the Raspberry Pi 3 GPIO header and carefully push down the connector interface board on to the Raspberry Pi 3 board.
3) Then, plug in a Grove Cable that comes with the Grove Sunlight sensor to the sunlight sensor and plug the other end of the cable to any of the I2C plugs on the connector interface. 
4) Once everything is connected, you can power up the Raspberry Pi. If you see a blue LED on the connector interface it shows that the connector interface is connected.


Below is the outcome after you connect the parts to the raspberry pi.

![Sunlight finish build](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/Sunlight%20finish%20build.jpg)

### Soldering
There was no soldering required with the sunlight sensor. The sunlight sensor is connected by using the Grove Cable to the connector interface on the raspberry pi.

### Power Up
Before power up the Raspberry pi, check the micro SD card to see if it has the contents of NOOBS operation system installer which contains Raspbian. If not, you can download, unzip and copy the folder contents of [NOOBS](https://downloads.raspberrypi.org/NOOBS_latest) into the root directory of the micro SD card.
On the first boot you will be prompted to install the operating system and configure the wifi setting. Once the raspberry pi is done installing the operating system. The first thing is to enable I2C because by default it is not enable. I2C bus allows the devices like the sunlight sensor to be connected and detected on to the Raspberry Pi.
To enable I2C: from the Start Menu -> Preferences -> Raspberry Pi configuration -> Interface set I2C to Enabled. 

Next on the terminal type the following command to check that you have i2c-tools utility installed.
```
sudo apt-get install -y python-smbus
sudo apt-get install -y i2c-tools
```

### Unit Testing

To check if the raspberry pi is detecting the sunlight sensor:
Open the terminal and type the command 
```
sudo i2cdetect -y 1
```

If you see this, it means that the raspberry pi is detecting the sunlight sensor and you connected the sensor to the raspberry pi correctly.

![sunlight i2c detect](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/Sunlight%20sensor%20i2c%20detect.png)

0x60 is the Sunlight Sensor.

The next step is to install the APscheduler. The Advanced Python Scheduler is a task scheduler that lets you schedule functions to be executed at times of your choosing.

On the terminal type the follow command to install APscheduler.
```
Sudo pip install setuptools –upgrade
Sudo pip install apscheduler
```

Next is to install the software and download the code to run the sunlight sensor
You can download the files required to run the sunlight sensor [here](https://minhaskamal.github.io/DownGit/#/home?url=https:%2F%2Fgithub.com%2FRaphaelNajera%2FSunlight_Sensor%2Ftree%2Fmaster%2Ffirmware).

Unzip the file and save it on the root directory on your raspberry pi. 

On the terminal type the following command:
```
cd firmware/Adafruit_Python_PureIO
sudo python setup.py install
```

To run the code, enter the follow command:
```
cd firmware
python SunIOT.py
```
The program will execute.



### Production Testing:
Once the program successfully executes the output will display the Vis (visible light), IR (infrared light) and UV Index (UV-Light) from the sunlight sensor. 

Pictures of the sunlight sensor project and the code running:

![sunlight powering up](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/sunlight%20sensor%20powered%20up.jpg)


![sunlight sensor output](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/Sunlight%20sensor%20output.png)

### Reproducible?
By following this build instruction, I believe you will be able to reproduce the sunlight sensor project. I have provided in my GitHub, budget, instruction on how to build and setup the code.
