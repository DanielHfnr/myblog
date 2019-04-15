---
title: Magic Mirror Part I
layout: post
---

Whats the first thing you do in the morning? Maybe a short look into the mirror.  With a Magic Mirror you can check the weather and see the upcoming birthdays of your friends and family at the same time. And a lot more things like showing your newest E-Mails are possible with a smart mirror. A Magic Mirror is basically a web server running on a Raspberry Pi, which shows useful information. The computer screen connected to the Raspberry will be located behind a spy mirror which is reflective on one side and transparent at the other.

In the fist part I want you to show how my Magic Mirror looks like:

![]({{"/assets/MagicMirror/Mirror.JPG"| absolute_url}})

The frame is compeltely built by myself out of wood from the river Isar. In the frame you can see a PIR-Sensor, which is used to turn off the screen behind the mirror, when there is no movement detected for longer than 60 seconds. This safes a lot of energy. You can also see a ultrasonic sensor. It is used to switch pages by a very basic form of gesture control. In this way it is possible to get more useful content into your mirror. 

Integrated in the frame is also a temperature sensor to show the current temperature and humidity in my flat. Also not visible integrated in the frame is a USB-Microphone and USB-Speakers, used for the Amazon Alexa integration for the Raspberry Pi. 


In the next post I will give you more detailled information about which Hardware and Software components I used to build my Magic Mirror.