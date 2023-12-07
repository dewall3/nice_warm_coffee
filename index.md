# Nice Warm Coffee - Team 17 Final Project - Fall 2023

Coffee warmers have been around for quite some time. They are available at a relatively low cost from many of your favorite retailers. They are simple and tend to do their job quite well. Have you ever looked at them and thought: "These should be far far more expensive, complex, and bulky!"? If so, we have the product for you! Meet the brainchild of the Georgia Tech Mechatronics Team 17, Nice Warm Coffee! All you need is an expensive MyRio, a set of sensors, a warming plate, and a giant box to put everything in.

The main motivation behind this project is to provide a solution to a real-world problem that many people face every day - cold coffee. Our device will maintain a set temperature, detect the presence of a coffee cup, and warn the user about how hot the surface is at varying levels. Every device these days is smart - so why not your coffee warmer? The Nice Warm Coffee device can be completely monitored and controlled from your smartphone! Why? Why not?

## Requirements

![Team17_Eng_spec](https://github.com/dewall3/nice_warm_coffee/assets/62768921/eb5764a0-cf84-4110-a8b5-f3e962a87931)

## State Machine Diagram

![Team17_Project_SMD](https://github.com/dewall3/nice_warm_coffee/assets/62768921/3ed778d5-0406-43aa-91f3-a5b033bd39a0)

## Sensors and Actors

![Side_view_2](https://github.com/dewall3/nice_warm_coffee/assets/62768921/ea5bc7b4-5376-4cb5-984f-98e06d598e95)

### I2C IR Camera (Adafruit AMG8833 using Panasonic Grid-Eye 8x8 sensor) [S1]
Used to measure the temperature of the coffee. 

https://learn.adafruit.com/adafruit-amg8833-8x8-thermal-camera-sensor

![Grid_Eye_2](https://github.com/dewall3/nice_warm_coffee/assets/62768921/c396cef1-a285-4b92-99a1-066c81a9c91f)

### I2C PMOD TMP3 [S2 - inside hot plate enclosure]
The TMP3 sensor is used to measure the temperature within the hot plate to give an estimate of the danger level of touching the hot plate.

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

![Sensors_actors_2](https://github.com/dewall3/nice_warm_coffee/assets/62768921/632a1bd6-c6f7-4ad2-9855-f34762df169a)

## Wireless Communication

### LabView Code
<a href="https://github.com/dewall3/nice_warm_coffee/tree/main/Coffee_Wifi">LabView Code Available in Repository

### WiFi MyRio Setup
The MyRio can be configured to connect over WiFi utilizing the NI MAX software. The MyRio must be configured in advance to connect to a specific network that the host computer will also be connected to. For simplicity, a custom hotspot SSID/password was made to enable the device to be started anywhere without reconfiguration.

NOTE: To connect to the web services detailed below, the MyRio date and time must be accurate. The date/time reset every time the device loses power. To combat this, a SubVI can be used to set the time of the MyRio to match the host computer. One such SubVI was available through NI: <a href="https://learn-cf.ni.com/teach/riodevguide/code/rt-pc_set-rt-system-time-date-from-pc.html">Set Date and Time on MYRIO</a>

### SystemLink
The "NI SystemLink Server" package can be downloaded from the NI Package Manager using the GaTech license. This package is required to run the VI and is what enables the LabView program and MyRio to communicate with the WebVI using tags: <a href="https://www.ni.com/docs/en-US/bundle/systemlink/page/communicating-data-with-tags.html">NI Documentation on Using Tags</a>

![LabView_back](https://github.com/dewall3/nice_warm_coffee/assets/62768921/b946c5a7-832c-446d-9116-501d61e9e3c4)

### GWeb Services
HTML development resource (available through GaTech's NI license) that provides the means for creating WebVIs. 

The "Panel" on GWeb Services operates in a very similar manner to a LabView front panel:
![WebVI](https://github.com/dewall3/nice_warm_coffee/assets/62768921/1a76bd9a-6490-448a-832e-7bfd4ea98498)


The "Diagram" on GWeb Services operates in a very similar manner to a LabView back panel:
![GWeb_back_panel](https://github.com/dewall3/nice_warm_coffee/assets/62768921/04bde37c-8479-4146-9bbf-c6c1945b048c)


## Demonstration

{% include youtube.html id="ghzMjdlc4OU" %}

## Challenges and Lessons Learned

One of the biggest challenges encountered was heat generation. When most of the budget goes to expensive sensors and a MyRio, sometimes corners have to be cut. In this case, the heating element was a very inexpensive 17W "Candle Warmer". This proved to be quite ineffective at warming up the coffee. It does a decent job at maintaining a temperature, but raising the temperature takes an absurd amount of time. In the demonstration video above, the temperature goes from approximately 95° F to 105° F. The video's speed has been increased significantly. The original recording was over an hour long! Because of this, the warmer only does anything useful at 100% power, so one of the original "optional" goals in the requirements above had to be abandoned. There was simply no feasible way to create a smart feedback adjustment with this particular heat source.

Another optional goal that had to be abandoned was the self-deployment of the MyRio. Combining deployment with the WiFi and WebVI interface ended up being a bit beyond the scope of our capabilities. 

Finally, we noticed that the IR camera had temperature readings that sometimes seemed off. Since the sensor is measuring the surface temperature (at the interface between liquid and air), the direct measurement is likely not a good representation of the mean liquid temperature. There was no time to address this, but a future upgrade could include a temperature correction of some kind determined by comparing IR surface temperature data to temperature data collected by a submerged sensor.

Despite these minor setbacks, we feel that our device was able to perform admirably. The web-based control aspect also worked far better than we could have hoped. We learned how to successfully build and deploy an HTML package, transmit data back and forth in LabView through a web server, and set up the MyRio for wireless operation. 

