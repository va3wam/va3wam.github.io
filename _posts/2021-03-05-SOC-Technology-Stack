---
title: "Twipe Robot SOC Technology Stack"
author: Old Squire
author_profile: true
excerpt: "The SOC technology stack used for the Twipe project."
last_modified_at: 2021-03-07T18:28:00-05:00
categories:
  - SOC
  - Technology stack
  - Architecture
tags:
  - SOC
  - Technology stack
  - Architecture
---
This article breaks down the technology at the heart (or rather brain) of the Twipe robot design.
<br>
![SOCTechStack](/assets/images/techStack.jpeg "Twipe SOC Technology Stack")

## User Layer
* Twipe robot 
* Operator Console 
* OTA, MQTT, Websockets, Web server HTTP

## Application Layer
* Firmware via C++ and Arduino core & libraries

## Operating System/Compiler Layer
* FreeRTOS
* Espressif RV32IMC Instruction Set Architecture (ISA) Tensilica Extended RiskV
  + Cadance Xtensa GCC compiler 
 
## Chip Architecture Layer
* Tensilica Lx6 32 bit architecture
  + 40 nm
  + 240MHz CPU
  + 600 DMIPS
  + 82 instructions 
  + 32bit Arithmetic Logic Unit (ALU)
    - Espressif extended Register Transfer Level (RTL)  

## Silicon Layer
* WROOM32 module
  + ESP32-S family
  + Dual core Espressif ESP32-D0WDQ6 fabless design
  + 4Mb flash (SPI)
  + USB to serial converter
  + WiFi (20% CPU of core 0)
    - 802.11n (2.4 GHz up to 150 Mbps)
  + Bluetooth classic LE 
  + Taiwan Semiconductor Manufacturing Company (TSMC) foundry
