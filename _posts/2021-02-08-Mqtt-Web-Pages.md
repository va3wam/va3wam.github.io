---
title: "Using Web Pages to Process MQTT Messages"
author: Old Squire
author_profile: true
excerpt: "How to setup your environment to use web pages with MQTT messages."
last_modified_at: 2021-02-08T18:28:00-05:00
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
This article is part of a larger series covering the end to end [IoT technology stack](https://engineering.eckovation.com/iot-stack/) used to control and monitor the Twipe robot. The focus in this article is on Layer 3 - the communication layer.

## The Messaging Environment
The Twipe robot acts as an IoT Smart Connected Product (SCP) and uses an MQTT broker for publishing and subscribing to topics via QOS1 MQTT messages encapsulated in TCP/IP packets. Webpages are used for publishing and subscribing to topics to the same broker via MQTT messages inside of a persitent websocket tunnel.    

### Hardware
The MQTT broker runs on a Raspberry Pi 3 Model B v1.2. You can tell what version of Pi you have by looking at what is printed on the silkscreen of the PCB. The operator console is any machine capable of running a web browser. The Twipe Robot uses a 2.4GHz WiFi radio to connect to a local WiFi Access Point. 

### OS
The MQTT broker runs Raspian Linux 10 (Buster). You can get the OS version by typing this command in a terminal window:
> cat /etc/os-release
The robot runs FreeRTOS in order to manage it's WiFi stack as well as handle multitasking via the primitive xTaskCreatePinnedToCore(). The image we use comes bundled with the PlatformIO.

### Mosquitto
We use version 1.5.7 of the Mosquitto with websockets enabled for our MQTT broker. You can check the version of Mosquitto that you are running by issuing the command to start the Mosquitto service as follows (ignore the error messages you get if the service is already running). That command is:
> mosquitto 

## The Code
The operator console code uses the [Eclipse Paho](https://www.eclipse.org/paho/) library, HTML, Javascript and Cascading Style Sheets. Our code is built upon the excellent examples found [here](https://github.com/thomaslaurenson/MQTT-Subscription-Examples). The robot's firmware is written in C++ and uses the Arduino core libary from PlatformIO as well as the [AsyncMqttClient.h](https://github.com/marvinroger/async-mqtt-clientFupOLED) library for message queuing telemetry transport support.
