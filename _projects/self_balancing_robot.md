---
layout: page
title: Controlling a Self Balancing Robot with Music Notes
description: Mechatronics Project
img: assets/img/self_balanced.gif
# redirect: https://unsplash.com
importance: 4
category: robotics
---

### Building the Robot

I have built a self balancing robot using a TI microcontroller and developed C code in Code Composer Studio. First, soldered all the components onto the main PCB which were all given to me as a part of the Mechatronics course. I have also 3D printed stands to hold the robot in case of a failure and motor attachment parts. After building the hardware needed, I started coding the software to control the robot using the microcontroller.

I have learned and gained hands-on experience in SPI, I2C, Analog to Digital conversions as well as experience using VMMs and oscilloscopes. In addition, I designed a small PCB using EagleCAD. I have developed understanding principle of operation and application of sensors, transducers, and actuators to mechanical systems.

### Using Music Notes to Steer the Robot

I implemented a way to control a self balancing robot that utilizes a microphone and music notes. Using the Texas Instruments' Fast Fourier Transform (FFT) library, I was able to recognize different notes played from my phone using a piano app and steer the robot.

Using an analog to digital converter, I converted the analog signal received by the microphone. Then, I saved the results into an array. Using the FFT library enabled me to recognize different notes. The main way to recognize the notes was to look at the output array of the FFT and find the maximum frequency found. In order to decrease the error, I made sure that the last 3 notes recognized are the same. After that I implemented a state machine that makes decisions depending on the note recognized by the robot. In addition, I used two array to run the FFT on, which enabled me to keep recording until I have a full array. I kept changing the input array between these two array called 'ping' and 'pong'.

In addition to steering the robot, a specific pattern of music notes makes the robot do a specific move such as spinning. In my implementation, I used a start note that puts the robot to a listening state which counts up until it hears the second note in a specific time frame and continues to listen for the other notes in the same way. If it recognizes all the notes in the expected order and in the expected time frames, it toggles an LED on the robot and starts to do the specific move.
