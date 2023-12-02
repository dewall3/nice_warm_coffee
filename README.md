# Nice Warm Coffee - Team 17 Final Project - Fall 2023

Coffee warmers have been around for quite some time. They are available at a relatively low cost from many of your favorite retailers. They are simple and tend to do their job quite well. Have you ever looked at them and thought: "These should be far far more expensive, complex, and bulky!"? If so, we have the product for you! Meet the brainchild of the Georgia Tech Mechatronics Team 17, Nice Warm Coffee! All you need is an expensive MyRio, a set of sensors, a warming plate, and a giant box to put everything in.

## Requirements

Engineering and user specifications.

State machine diagram.

## Sensors and Actors

### I2C IR Camera (Adafruit AMG8833 using Panasonic Grid-Eye 8x8 sensor)
Used to measure the temperature of the coffee. 

https://learn.adafruit.com/adafruit-amg8833-8x8-thermal-camera-sensor

### I2C PMOD TMP3
The TMP3 sensor is used to measure temperature within the hot plate to give an estimate of the danger level of touching the hot plate.

https://digilent.com/reference/pmod/pmodtmp3/reference-manual

### I2C Load Cell
A load cell is used to detect the presence of a cup of coffee. No cup - the device remains off.

### 120V AC candle/mug warmer

Brand: ASAWASA
Model: 8S-CDXA-ZSX2

### PWM AC Dimmer
A PWM-controlled AC-dimmer switch is connected between the hot plate and the power supply. This enables our program to control the hot plate remotely. 

Part #: PWM1ChKrida

### PWM RGB LED
An RGB-LED is used as a visual indicator of the danger level of touching the hot plate. The light is green when the plate is cool, yellow when it is warming up, and red when it is too hot to touch (risk of burn).

Brand: EDGELEC
Model: ‎ED_YW05_RGB-4P-C

## Wireless Communication

### WiFi MyRio Setup

### SystemLink

### GWeb Services

## Demonstration

Video demonstration goes here

## Challenges Encountered

Discuss challenges

## Wrap-Up

Conclusion
