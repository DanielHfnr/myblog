---
title: Magic Mirror Part II
layout: post
---

In this part I want to give more detailled instructions which hardware components I used to build my Magic Mirror. 


* Raspberry Pi with power supply (I would recommend the Pi3 because of the WiFi capability)
* SD-Card 
* 24" TFT Screen with HDMI Cable
* USB-Microphone [(Link)](https://www.amazon.de/Seacue-Omnidirektionaler-Kondensator-Interviews-Netzwerksingen/dp/B071171DBP)
* USB-Speakers [(Link)](https://www.conrad.de/de/p/basetech-s181-2-0-pc-lautsprecher-kabelgebunden-6-w-schwarz-1425991.html)
* Powerstrip with appliance coupler [(Link)](https://www.amazon.de/dp/B003YG7AHS/ref=cm_sw_r_cp_tai_QKfSCbDZA7C5X)
* USB flush mount cable [(Link)](https://www.amazon.de/dp/B0728FW3FX/ref=cm_sw_r_cp_tai_sJfSCbQRGTTGJ)
* PIR-Sensor [(Link)](https://www.conrad.de/de/p/hc-sr501-pir-infrarot-bewegungsmelder-motion-sensor-modul-arduino-raspberry-pi-802235221.html)
* Ultrasonic-Sensor [(Link)](https://www.conrad.de/de/p/hc-sr04-abstandsmessung-ultraschall-ultrasonic-sensor-module-802235231.html)
* Temperature and Humidity Sensor [(Link)](https://www.conrad.de/de/p/iduino-feuchte-sensor-modul-1-st-se052-1485325.html)
* Spy-Mirror [(Link)](https://www.glas-star.de/spionsspiegelnachmass/chrome-spy-spiegel/chrome-spy-4mm-nach-ma%C3%9F/)





# Basic Setup of the Project


***Install Raspbian on the SD-Card and boot the Pi***

A complete instruction on how to install the Raspbian operating system on the SD-Card can be found here: [Link](https://thepi.io/how-to-install-raspbian-on-the-raspberry-pi/)

***Connect to WiFi and activate SSH***

In some cases it's convenient to connect to the Pi through SSH and work on your Computer. Instructions on how to do this can be found here: [Link](https://www.raspberrypi.org/documentation/remote-access/ssh/)

***Connect Microphone and Speakers to the Pi and install Amazon Alexa***

When the Microphone and the Speakers are connected and are working properly, Amazon's Alexa for voice control can be installed. A detailled instruction by Amazon is available here [Link](https://developer.amazon.com/de/docs/alexa-voice-service/required-hardware.html).

Once Alexa is installed and working, we enabled our Magic Mirror to play music from our favourite radio station or read the news through voice control. You can also checkout useful Alexa skills for controlling your smart home or other stuff. 


***Install Magic Mirror base project***

For the Raspberry Pi there is a automatic installation available, which makes it pretty easy to use. You can find a step by step guide here: [Link](https://github.com/MichMich/MagicMirror).

Once the installation is done you just have to configure some things like rotating the screen, disbale the screensaver and auto-hide the mouse pointer.

The last thing that needs to be done is to setup the Raspberry Pi that your Magic Mirror is automatically running after boot. All of these things are well described in the link above.  


# Connect the sensors

***PIR-Sensor***

The PIR-Sensor is used to turn off the screen behind the mirror when nobody is at home, or at least no one is in front of the mirror. This saves a lot of energy. Connect the VCC Pin of the Sensor to 5V of the Pi and also connect to GND. After that you just have to connect the OUT Pin of the Sensor to one of the Pis GPIOs. 

An example can be found here: [Link](https://tutorials-raspberrypi.de/raspberry-pi-bewegungsmelder-sensor-pir/)

The Sensors time delay and sensitivity can be adjusted directly on the board. The time delay determins how long the output remains high after detecting motion while the sensitivity sets the detection range from 3 meters to 7 meters.

Check if the sensor works as expected. For a system service, that automatically turns the screen off check here: [https://github.com/DanielHfnr/PIR-Sensor](https://github.com/DanielHfnr/PIR-Sensor). That's what I use for my Magic Mirror.

If you follow the instructions a service will be created, that runs after boot of the Raspberry Pi.

[//]: <> ![]({{"/assets/MagicMirror/pir.png"| absolute_url}})



***Temperature and Humidity Sensor***

With the DHT-11 sensor it is possible to measure the indoor temperature and humidity which will be shown in the Magic Mirror. For this I use a already existing module. 

An example on how to use and connect the sensor to the Pi can be found here: [Link](https://tutorials-raspberrypi.de/raspberry-pi-luftfeuchtigkeit-temperatur-messen-dht11-dht22/).
If you use the Sensormodule listed above in the Hardware listing you dont have to use a extra Pullup-Resistor, because it's already connected on the sensor board. Just connect to VCC, GND and the OUT Pin of the sensor to one of the GPIOs and the sensor is ready.

In my Magic Mirror the sensor is hidden behind the frame and not visible. 

[//]: <> ![]({{"/assets/MagicMirror/dht11.png"| absolute_url}})

***Ultrasonic Sensor***

The ultrasonic sensor in my Magic Mirror is used to switch pages through a very basic form of gesture control. There are a few modules out there to switch pages, all of them working in a different way and using different sensors. Another possible way could be through Alexas voice control. 

My Magic Mirror automatically switches pages if you hold your hand in front of the sensor for a short time. With the ultrasonicsensor it is possible to measure the distance to an object. If the distance is shorter than e.g. 15 cm the module for die Magic Mirror will detect a movement and will switch to the next page. 

A tutorial on how to connect the sensor to the Raspberry Pi can be found here: [Link](https://tutorials-raspberrypi.de/entfernung-messen-mit-ultraschallsensor-hc-sr04/).

The module for the Magic Mirror can be found on GitHub ([https://github.com/DanielHfnr/MMM-Switch](https://github.com/DanielHfnr/MMM-Switch)).



[//]: <> ![]({{"/assets/MagicMirror/ultraschall_Steckplatine.png"| absolute_url}})