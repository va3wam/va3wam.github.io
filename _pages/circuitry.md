---
layout: single
author_profile: false
permalink: /circuitry/
title: "Circuitry"
excerpt: "How we design and manufacture the circuitry for our projects."
toc: true
header:
  caption: "Circuitry"
  image: "/assets/images/circuitry.jpg"
tipue_search_active: true
exclude_from_search: false

---

## PCB Design
The main tools that we use to design <a href="https://en.wikipedia.org/wiki/Printed_circuit_board">Printed Circuit Boards</a> (PCBs) are the open source tool <a href="https://fritzing.org/home/">Fritzing</a> and <a href="https://en.wikipedia.org/wiki/AutoCAD">AutoCAD</a>'s <a href="https://www.autodesk.ca/en/products/eagle/overview?referrer=%2Fproducts%2Feagle%2Foverview">Eagle CAD</a>.

### Units in Eagle
Being Canadians, so we should be using metric units, but for some strange reason (maybe rationalized by the nature of the parts we're using) we do a lot of stuff in imperial units. This is important when a board layout starts its journey from Eagle to Fusion. BEFORE you do the DXF file export, you must change the units from metric to imperial.

## PCB Fabrication
After about a year of refining a PCB milling procedure it was decided that the cost and quality of the boards that we were producing could not match what a fabrication service could do for us so we have now switched to outsourcing our PCB fabrication. We currently use the serives of <a href="https://www.pcbway.com/">PCBWAY</a> though we also short listed these services for future consideration:
<ul>
<li><a href="https://oshpark.com/">OSHPARK</a></li>
<li><a href="https://jlcpcb.com/">JLC</a></li>
<li><a href="https://www.seeedstudio.com/">Seeed</a></li>
</ul>

## Common Components
The following development boards are commonly used components in the prototype circuitry of our projects.
  
### ESP32
<img src="/assets/images/huzzah32.jpg" alt="ESP32" height="100" width="100"> 
The Espressif <a href="https://en.wikipedia.org/wiki/ESP32">ESP32</a> is the <a href="https://en.wikipedia.org/wiki/System_on_a_chip">SoC</a> at the centre of all projects at this time. The Adafriut <a href="https://learn.adafruit.com/adafruit-huzzah32-esp32-feather/downloads">Huzzah32</a> development board is the platform used for designs. The plan is to do this until the time comes to fabricate an <a href="https://en.wikipedia.org/wiki/Single-board_computer">SBC</a> for a dedicated application.
<ul>
<li><a href="https://github.com/va3wam/va3wam.github.io/blob/master/doc/esp32_technical_reference_manual_en.pdf">Technical Reference Manual</a></li>
</ul>

### MPU6050
<img src="/assets/images/gy521.jpg" alt="MPU6050" height="100" width="100"> 
The Invensense <a href="https://en.wikipedia.org/wiki/InvenSense">MPU6050</a>
<a href="https://en.wikipedia.org/wiki/Microelectromechanical_systems">MEMS</a>
<a href="https://en.wikipedia.org/wiki/Inertial_measurement_unit">IMU</a> 
is the motion detection 
<a href="https://en.wikipedia.org/wiki/System_on_a_chip">SoC</a> 
of choice. The plan is to use the The GY521 development board until the time comes to fabricate an 
<a href="https://en.wikipedia.org/wiki/Single-board_computer">SBC</a> 
for a dedicated application.
<ul>
<li><a href="https://invensense.tdk.com/products/motion-tracking/6-axis/mpu-6050/">TDK</a></li>
<li><a href="https://github.com/va3wam/va3wam.github.io/blob/master/doc/MPU6050/App%20Note%201%20-%20Motion%20Driver%206.12%20Getting%20Started.pdf">Getting Started</a></li>
<li><a href="https://github.com/va3wam/va3wam.github.io/blob/master/doc/MPU6050/App%20Note%202-%20Motion%20Driver%206.12%20Features%20Guide.pdf">Features Guide</a></li>
<li><a href="https://github.com/va3wam/va3wam.github.io/blob/master/doc/MPU6050/App%20Note%203-%20Motion%20Driver%206.12%20Porting%20Guide.pdf">Porting Guide</a></li>
<li><a href="https://github.com/va3wam/va3wam.github.io/blob/master/doc/MPU6050/MPU%20HW%20Offset%20Registers%201.2.pdf">Registers</a></li>
</ul>

### OLED
<img src="/assets/images/I2C-OLED.jpg" alt="OLED" height="100" width="100"> 
The SOLOMON SYSTECH <bold>SSD1306</bold> <a href="https://en.wikipedia.org/wiki/CMOS">CMOS</a> driver integrated with a 0.96" 128x64 <a href="https://en.wikipedia.org/wiki/OLED">OLED</a> on a generic board is used in projects requiring data and graphics display capabilities.
The board suppports two different I2C addresses. Since we use 2 OLEDs for the robot we need to change one of the addresses. If you look at the silkscreen on the back of the board (see image 1) 
<img src="/assets/images/I2C-OLED-back.jpg" alt="OLED" height="100" width="100">
you will see a place where you can select the I2C address by moving a 407ohm surface mount resistor between two pads. You change the address by desoldering the resistor and moving it to a second pad. The addresses that you can select are shown on the silkscreen as 0x7A (01111010b) and 0x78 (01111000b). NOtew that when you scan the I2C bus you will not see any devices with either of these addresses. You will however see devices with the addresses 0x3D (00111101b) and 0x3C (00111100b). These are the OLEDs. Whay the different address? If you look carefully at the first and second set of addresses you will notice that second 2 addresses are just the first 2 addresses bit shifted to the right one bit. This occurs becasue in common I2C communication the first seven bits of the "address byte" contains the device address and the last bit is a read/write bit. 0 is write and 1 is read. The I2C library that you are using is manipulating the addresses to conform with this convension.

### DRV8825
<img src="/assets/images/DVR8825.jpg" alt="DRV8825" height="100" width="100"> 
The Texas Instruments <a href="http://www.ti.com/product/DRV8825">DRV8825</a> bipolar stepper motor driver on the Polulu <a href="https://www.pololu.com/product/2133">Md20B</a> breakout boards is used for controlling <a href="https://en.wikipedia.org/wiki/Stepper_motor">stepper motors</a>.
<ul>
<li><a href="https://github.com/va3wam/va3wam.github.io/blob/master/doc/DVR8825/drv8825.pdf">Data Sheet</a></li>
</ul>

#### DRV8825 Calibration Procedure
A calibration procedure is required during set up of the controller. The procedure and required circuit is detailed <a  href="https://forum.arduino.cc/index.php?topic=415724.0">here</a>. Note that the current target for the controllers is 0.4AMPS per the spec sheet linked in the Motor page. The following is a breakdown on the calibration steps:

#### Calculate VREF
Step one is to figure out what the target output of the DVR8825 is. This is required to ensure that the motors are not damaged by passing too much current to the coils of the stepper motors

<ul>
<li>Our motors have a constant current rating of 0.4AMPs.</li>
<li>Current Limit = VREF x 2</li>
<li>0.4AMPs = VREF x 2</li>
<li>VREF = 0.4AMPs/2</li>
<li>VREF = 0.2VDC</li>
</ul>

#### Torque Requirements
We have determined that the 0.4A motors lack the torque required to effectively balance TWIPi. We have learned that in order to increase torque we must increase the current (Amps). We have also learned that to increase speed we must increase voltage. Finally, we have learned that torque drops with speed increases. 

With this new information we now realize that in order to increase the available torque we need new motors that are rated to handle more current (Amps). We are now going to try using motors rated to handle 1.7AMPS. This should give us effectively 4 times the current which we hope will produce the additional torque that we need for TWIPi. 

It should also be noted that the DRV8825 motor controller that we are using can handle voltages ranging from 4 to 45VDC as well as current up to 2.5 AMPS. We have learned that by using single step mode (which we are) the motor driver only passes 71% of the current to the coils so we think we can set the current limit slightly higher which will give us another modest boost in torque. Here are the values and formulas we are using for TWIPi with the new motors:

<ul>
<li>Vref (read with a multi meter at the POT) = 1/2 maximum current</li> 
<li>In single step mode we only pass 71% of the configured current limit</li>
<li>We can increase the current limit on the motor controller knowing that only 71% of the current is passed to the motors</li>
</ul>

Available torque is calculated as follows:
Set the DRV8825 to Vref = 0.5(1.7*(100/71)) ~= 1.2V
Which in turn passes 1.7AMPS to the motor
We know that the new motor is rated with a holding torque of40N.cm (56oz-in). Our old motor was rated at 37oz-in for reference. We believe this new motor will achieve its torque rating with the current we will pass it. We do not think that the old motor was achieving its advertised torque at the speed we are using. All of this is to say that we are currently hoping (praying) that by changing to new motors with a higher current rating, which in turn allows us to increase the current that we pass through the motor driver we will get sufficient torque to balance TWIPi. 

#### Detent torque
One last not about torque. We have also learned that the maximum torque that can be achieved once the motor is moving at low speeds (which we will assume is any speed we need to balance on the spot) is calculated as follows:

Holding torque - 2 * Detent torque = 40N.cm - 2 * 2.2N.cm = 35.6N.cm

This is relevant once we get beyond simply trying to balance on the spot and actually try to move about with TWIPi. 

#### Testing Results
With the new motor we calibrated the DRV8825 to  1.2V. This resulted in a noticeable increase in torque but we also noted that only 0.8AMPs were being drawn from the power supply being driven at 12VDC. We then tried increasing the calibration number to see if we could draw 1.7AMPS from the power supply. At over 1AMP being drawn the motor stopped spinning. As we gradually reduced the AMPs being passed the motor would run for a bit then stop. We think this was the DRV8825 using thermal protection and cutting out until it cooled down. When we reduced the calibration number back to 1.2V and the power supply indicated that it was passing 0.8AMPS then the motor ran without cutting out so we assume that the DRV8825 is no longer over heating.

#### Wire up tuning circuit
Use this diagram to wire up the calibration circuit
<a href="https://github.com/va3wam/TWIPi/blob/master/img/DVR8825-calibrate.png">DVR8825 calibration</a>

#### Probe and calibrate
- Set your multi meter to read DC voltage
- Put the negative probe to ground and the positive probe to the POT
- Turn the POT until the meter reads 0.2V (200 mV)

---
