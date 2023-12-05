# Nice Warm Coffee - Team 17 Final Project - Fall 2023

Coffee warmers have been around for quite some time. They are available at a relatively low cost from many of your favorite retailers. They are simple and tend to do their job quite well. Have you ever looked at them and thought: "These should be far far more expensive, complex, and bulky!"? If so, we have the product for you! Meet the brainchild of the Georgia Tech Mechatronics Team 17, Nice Warm Coffee! All you need is an expensive MyRio, a set of sensors, a warming plate, and a giant box to put everything in.

The main motivation behind this project is to provide a solution to a real-world problem that many people face every day - cold coffee. Our device will maintain a set temperature, detect the presence of a coffee cup, and warn the user about how hot the surface is at varying levels. Every device these days is smart - so why not your coffee warmer? The Nice Warm Coffee device can be completely monitored and controlled from your smartphone! Why? Why not?

## Requirements

![Team17_Eng_spec](https://github.com/dewall3/nice_warm_coffee/assets/62768921/eb5764a0-cf84-4110-a8b5-f3e962a87931)

## State Machine Diagram

![Team17_Project_SMD](https://github.com/dewall3/nice_warm_coffee/assets/62768921/3ed778d5-0406-43aa-91f3-a5b033bd39a0)

## Sensors and Actors

![Side_view](https://github.com/dewall3/nice_warm_coffee/assets/62768921/72eaec23-cec3-4815-8b0a-d7e731bd2d8a)

### I2C IR Camera (Adafruit AMG8833 using Panasonic Grid-Eye 8x8 sensor) [S1]
Used to measure the temperature of the coffee. 

https://learn.adafruit.com/adafruit-amg8833-8x8-thermal-camera-sensor

![Grid_Eye](https://github.com/dewall3/nice_warm_coffee/assets/62768921/89ec2d77-7c97-46b4-99cc-4bc00099e94e)

### I2C PMOD TMP3 [S2 - inside hot plate enclosure]
The TMP3 sensor is used to measure temperature within the hot plate to give an estimate of the danger level of touching the hot plate.

https://digilent.com/reference/pmod/pmodtmp3/reference-manual

### I2C Load Cell [S3]
A load cell is used to detect the presence of a cup of coffee. No cup - the device remains off. The cell itself is located beneath the hot plate. The I2C amplifier is mounted to the side of the box.

### 120V AC candle/mug warmer [A1]

Brand: ASAWASA
Model: 8S-CDXA-ZSX2

A PWM-controlled AC-dimmer switch is connected between the hot plate and the power supply. This enables our program to control the hot plate remotely via the MyRio. 
Part #: PWM1ChKrida

### PWM RGB LED [A2]
An RGB-LED is used as a visual indicator of the danger level of touching the hot plate. The light is green when the plate is cool, yellow when it is warming up, and red when it is too hot to touch (risk of burn).

Brand: EDGELEC
Model: ‎ED_YW05_RGB-4P-C

![Sensors_actors](https://github.com/dewall3/nice_warm_coffee/assets/62768921/32237451-41a9-4ac4-b344-bb3957b8455a)

## Wireless Communication

### WiFi MyRio Setup
The MyRio can be configured to connect over WiFi utilizing the NI MAX software. The MyRio must be configured in advance to connect to a specific network that the host computer will also be connected to. For simplicity, a custom hotspot SSID/password was made to enable the device to be started anywhere without reconfiguration.

NOTE: To connect to the webservices detailed below, the MyRio date and time must be accurate. The date/time reset every time the device loses power. To combat this, a SubVI can be used to set the time of the MyRio to match the host computer. One such SubVI was available through NI: <a href="https://learn-cf.ni.com/teach/riodevguide/code/rt-pc_set-rt-system-time-date-from-pc.html">Set Date and Time on MYRIO</a>

### SystemLink
The "NI SystemLink Server" package can be downloaded from the NI Package Manager using the GaTech license. This package is required to run the VI and is what enables the LabView program and MyRio to communicate with the WebVI using tags: <a href="https://www.ni.com/docs/en-US/bundle/systemlink/page/communicating-data-with-tags.html">NI Documentation on Using Tags</a>

### GWeb Services
HTML development resource (available through GaTech's NI license) that provides the means for creating WebVIs, which have a similar front panel and back panel setup similar to LabView. The "front panel" can be hosted on a website, such as ours: <a href="https://hosting.systemlinkcloud.io/webapps/05c91db7-e59d-4886-8364-4b6e4c14867b/content/ni-paths-NISHAREDDIR64/Web%20Server/htdocs/WebApp/index.html">WebVI</a>

## Demonstration

<a href="https://gtvault-my.sharepoint.com/:v:/g/personal/dwallace36_gatech_edu/EbN4DnTYsqlCpFK7Ce8ax5EBOd8VOqywoSlm-DWYyA8vqQ?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=r7S1AI">Demonstration Video</a>

## Challenges Encountered

Discuss challenges

## Wrap-Up

Conclusion
