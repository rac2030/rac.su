+++
title = "Sensirion SDP3x Arduino driver"
description = "tbw."
tags = [
    "arduino",
    "sensor"
]
date = "2017-02-04"
categories = [
    "Arduino",
    "Library",
]
draft=false
+++

This Arduino library can be used to interface the [SDP3x](https://www.sensirion.com/products/differential-pressure-sensors/worlds-smallest-differential-pressure-sensor/) differential pressure sensor from [Sensirion](https://www.sensirion.com) over I2C to get the pressure difference and the temparature reading it exposes.

<!--more-->

# Usage example
{{< highlight cpp "linenos=inline,style=emacs" >}}
// To set a different I2C address, uncomment the define
// #define SDP3x_I2C_ADDRESS 0x21
#include "SDP3x.h"

// Setup routine runs once when you press reset
void setup() {
	// Initialize serial console
	Serial.begin(9600);
	// Initialize I2C communication
	Wire.begin();
}

// the loop routine runs over and over again forever
void loop() {
	// Simply print raw value, this can be viewed in the serial plotter
	Serial.print("Pressure difference: ")
	Serial.println(SDP3x.getPressureDiff());
	// delay for a 100ms until the next sensor reading
	delay(100);
	Serial.print("Temperature: ")
	Serial.println(SDP3x.getTemperature());
	// delay for a 100ms until the next sensor reading
	delay(100);
}
{{< /highlight >}}


# Sourcecode

https://github.com/rac2030/Arduino-Sensirion-SDP3x-driver
