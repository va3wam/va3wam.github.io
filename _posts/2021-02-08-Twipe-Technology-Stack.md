---
title: "Twipe Robot Technology Stack"
author: Old Squire
author_profile: true
excerpt: "The IoT technology stack used for the Twipe project."
last_modified_at: 2021-02-08T18:28:00-05:00
categories:
  - IoT
  - Technology stack
  - Architecture
tags:
  - IoT
  - Technology stack
  - Architecture
---
The Twipe robot end to end architecture model is based on a five layer [IoT technology stack](https://engineering.eckovation.com/iot-stack/). 
In this article we will review the high level details of this architecture.

## Layer 1: Device Hardware
The robot has a two wheeled inverted pendulum design. It uses a custom PCB to integrate a series of off the shelf development boards to 
dynamically balance the inherently unstable robot. 

### Main processor
The processing logic for the robot is provided by an Adafruit Huzzah32 development board which features an Espressif ESP32 System On A Chip 
(SOC). This processor is responsible for handling the logic to balance the robot as well as to handle all the real-time communication with 
an operator as required.

### Motion Sensors
The robot’s motion tracking is provided by an Invensense MPU6050 inertial measurement unit development board which combine a 3-axis 
microelectromechanical gyroscope and a 3-axis accelerometer on the same silicon die, together with an onboard Digital Motion Processor (DMP),
which processes complex 6-axis MotionFusion algorithms. 

### Power Management
Twipe is powered by direct current provided by a Mastercraft 20V max lithium-ion battery. This voltage is stepped down to a 12 volt bus, a 5 
volt bus and a 3.3 volt bus using a Drok LM2596 multiple output power supply.  

### Motor
Twipe moves on two Makeblock 42BYG bipolar stepper motors driven by signals from the ESP32 SOC via a pair of Polulu MD20B development boards 
featuring the Texas Instrument DRV8825 bipolar stepper motor driver.  

### Physical Properties
The Twipe robot's chassis measures 8.5" tall by 5.25" wide by 3.75" deep. When the wheels are attached to TWIPe the robot's height measures 
8.625" tall. Twipe's body is milled from Acetron GP and weighs xxx ounces and required a calculated detent torque of yyy in order to maintain
its balance in a fixed position. The robot will need to make aaa DMP calculations per second, update the stepper motors bbb times per second,
and send telemetry data to an operator at a rate of ccc bps over a wifi link.

## Layer 2: Device Software
The Twipe robot must read accelerometer and gyroscope data from an inertial measurement unit to determine the robot’s orientation and then 
use a Proportional Integral Derivative (PID) algorithm to maintain an upright posture. Realtime telemetry must be sent out and realtime
operator commands must be recieved over a Wifi connection.

### Operating System
FreeRTOS is used to run a WiFi stack as well as the primitive xTaskCreatePinnedToCore() which is used to manage mutli-threaded process 
execution.  

### Application Software
Embedded systems are programed in C++ using Arduino core libraries.

## Communications

### Telemetry data


