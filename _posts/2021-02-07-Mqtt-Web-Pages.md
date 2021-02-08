---
title: "Using Web Pages to Process MQTT Messages"
author: Old Squire
author_profile: true
excerpt: "How to setup your environment to use web pages with MQTT messages."
last_modified_at: 2021-02-07T18:28:00-05:00
categories:
  - MQTT
  - Messaging
  - HTML
  - Javascript
  - Websockets
tags:
  - mqtt
  - websockets
  - javascript
  - messaging
---
This article is part of a larger series covering the end to end [IoT technology stack](https://engineering.eckovation.com/iot-stack/) used to control and monitor the Twipe robot. The focus here is on the communication layer.

## The Messaging Environment
The Twipe robot acts as an IoT Smart Connected Product (SCP) and uses an MQTT broker for publishing and subscribing to topics via QOS1 MQTT messages encapsulated in TCP/IP packets. Webpages are used for publishing and subscribing to topics to the same broker via MQTT messages inside of persitent websockets.    

### Hardware
MQTT broker runs on a Raspberry Pi 3 Model B v1.2. This is printed on the solkscreen of the PCB.

### OS
Raspian Linux 10 (Buster). You can get the OS version as follows

> cat /etc/os-release

### Mosquitto
Mosquitto MQTT broker version 1.5.7

Check the version you are running by issuing the command to start the Mosquitto service as follows (ignore the error messages you get if the service is already running).

> mosquitto 

## The Code
The code used here came from [here](https://github.com/thomaslaurenson/MQTT-Subscription-Examples).
