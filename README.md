# Nice Warm Coffee - Team 17 Final Project - Fall 2023

Coffee warmers have been around for quite some time. They are available at a relatively low cost from many of your favorite retailers. They are simple and tend to do their job quite well. Have you ever looked at them and thought: "These should be far far more expensive, complex, and bulky!"? If so, we have the product for you! Meet the brainchild of the Georgia Tech Mechatronics Team 17, Nice Warm Coffee! All you need is an expensive MyRio, a set of sensors, a warming plate, and a giant box to put everything in.

## Requirements

Engineering and user specifications.

State machine diagram.

## Sensors and Actors

### I2C Grid-Eye IR Camera
Used to measure the temperature of the coffee. The IR temperature sensor will only read the surface temperature, which tends to be lower due to the interface with the air. To account for this, we looked at temperature from the IR thermometer vs temperature from a submerged thermometer and applied a correction factor to compensate.

### I2C PMOD TMP3
The TMP3 sensor is used to measure temperature within the hot plate to give an estimate of the danger level of touching the hot plate.

### I2C Load Cell
A load cell is used to detect the presence of a cup of coffee. No cup - the device remains off.

### PWM AC Dimmer
A PWM-controlled AC-dimmer switch is connected between the hot plate and the power supply. This enables our program to control the hot plate remotely. 

### PWM RGB LED
An RGB-LED is used as a visual indicator of the danger level of touching the hot plate. The light is green when the plate is cool, yellow when it is warming up, and red when it is too hot to touch (risk of burn).

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
