---
layout: single
author_profile: false
permalink: /software/
title: "Software"
excerpt: "Summary of the languages, coding standards, tools and best practices used for our projects."
toc: true
header:
  caption: "Software"
  image: "/assets/images/software.jpg"
tipue_search_active: true
exclude_from_search: false

---

## Programming Languages
Our projects are developed using the following programming languages.

### Arduino/C++
Embedded systems are programed in C++ using Arduino core libraries.

### FreeRTOS
<a href="https://freertos.org/">FreeRTOS</a> runs along side the C++ code in our embedded systems on the ESP32 SOC.  Currently we only use it for its primitive <a href="https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/system/freertos.html">xTaskCreatePinnedToCore()</a> which is used to manage mutli-threaded process execution. Aside from chip manufaturers, other large players are starting to embrace FreeRTOS including <a href="https://aws.amazon.com/">Amazon Web Services</a> (AWS) to address IOT for microcontrollers including the ESP32 SOC. They have created <a href="https://techcrunch.com/2017/11/29/amazon-freertos-is-a-new-operating-system-for-microcontroller-based-iot-devices/">AWS FreeRTOS</a>. With the advent of AWS embracing FreeRTOS it may well be that other FreeRTOS primitives will be implemented for features such as voice command via Alexa voice services in the future.         

### Electron Framework
Desktop applications are developed using the <a href="https://www.electronjs.org/">Electron Framework</a> which uses <a href="https://en.wikipedia.org/wiki/JavaScript">Javascript</a>, <a href="https://en.wikipedia.org/wiki/Cascading_Style_Sheets">CSS</a> and <a href="https://en.wikipedia.org/wiki/HTML">HTML</a>.

### Static web content
Documentation stored on the Github hosting service is written in Gem, Jekyll, <a href="https://en.wikipedia.org/wiki/Markdown">Markdown</a>,  <a href="https://en.wikipedia.org/wiki/HTML">HTML</a>, <a href="https://en.wikipedia.org/wiki/Cascading_Style_Sheets">CSS</a>, <a href="https://en.wikipedia.org/wiki/JavaScript">Javascript</a>. 

## Tools
The following software is recommended for developing a VA3WAM project.

### Text Editor
Our projects are written using <a href="https://code.visualstudio.com/">Visual Studio Code</a> (VSC) as your enhanced text editor. Within VSC install these plug-ins:
<ul>
    <li><a href="https://github.com/bbenoist/vscode-doxygen">Doygen</a></li>
    <li><a href="https://github.com/christophschlosser/doxdocgen">Doygen Document Generator</a></li>
    <li><a href="https://github.com/Microsoft/vscode-cpptools">C/C++</a></li>
    <li><a href="https://github.com/mdickin/vscode-markdown-shortcuts">Markdown Shortcuts</a></li>
    <li><a href="https://github.com/Microsoft/vscode-themes">Markdown Theme Kit</a></li>
    <li><a href="https://github.com/AlanWalk/Markdown-TOC">Markdown TOC</a></li>
    <li><a href="https://github.com/DavidAnson/vscode-markdownlint">Markdown Lint</a></li>
    <li><a href="https://github.com/platformio/platformio-vscode-ide">PlatformIO IDE</a> - embedded programming <a href="https://en.wikipedia.org/wiki/Integrated_development_environment">IDE</a></li>
    <li><a href="https://github.com/Gruntfuggly/todo-tree">Todo Tree</a></li>
</ul>

### IDE
Our embedded systems are programmed using <a hraf="https://platformio.org/">PlatformIO</a>. HTML content is written using the <a href="https://www.seamonkey-project.org/">Sea Monkey</a> Internet Application Suite. 

## Remote Messaging Protocol
Messaging for our embedded appications is done using the MQTT protocol, the <a href="https://mosquitto.org/"> Mosquito MQTT Broker</a> and the <a href="http://mqttfx.org/">MQTTfx</a> MQTT client.
        
## Standards
When contributing to our repositories please follow these standards. 

### C++
This <a href="http://www.edparrish.net/common/cppdoc.html">link</a> points to a set of standards used for coding in C++. 
In addition to these standards comments should be markdown compliant using /// followed by XML tags. Source code tags are 
parsed using <a href="https://en.wikipedia.org/wiki/Doxygen">DoxyGen</a> to produce documentation.

### Versioning
We use <a href="http://semver.org/">SemVer</a> for versioning. We use the Github release process to package up known working 
code configuraitons. SVC for VA3WAM repositories is handled using <a href="https://git-scm.com/">Git</a>.

### Naming Variables and Files
We use <a href="https://en.wikipedia.org/wiki/Camel_case">camelCase</a> for naming variables in our code as well as when naming files. 

### Readme Files
Our Github respositories must contain a readme file that is based on this 
<a href="https://github.com/va3wam/TWIPe/blob/Andrew/README.md">template</a>.
