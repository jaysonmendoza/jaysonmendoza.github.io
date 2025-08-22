---
layout: post
title: Immersive Haptic Feedback Glove
description: A wearable VR glove that translates finger movement into digital signals and delivers tactile feedback through vibration and force, enabling realistic interaction with virtual objects. Built through iterative prototyping, from single-sensor proof-of-concepts to a multi-sensor, actuator-integrated wearable system.
skills:
- Embedded Systems (Arduino, ESP32)
- Microcontroller Programming (C++/Arduino IDE)
- Sensor Integration (Flex Sensors, IMU)
- Haptic Feedback (Vibration Motors, Force Actuators)
- CAD Modeling & 3D Printing
main-image: 
---

## Project Overview

The **Immersive Haptic Feedback Glove** is designed to bring the sense of touch into virtual reality. By combining **finger tracking sensors** with **vibration and force-feedback actuators**, the glove allows users to “feel” and manipulate digital objects as if they were real.  

This project was developed through multiple stages of **proof-of-concept prototypes**, gradually scaling from single-sensor tests to a fully wearable system.

---

## Proof of Concept: Finger Bend Detection

The first milestone was demonstrating that a **flex sensor** could accurately track finger bending.  
- A flex sensor was wired into a voltage divider circuit with an Arduino UNO.  
- Raw analog values were smoothed with an exponential moving average for stability.  
- The readings were displayed on the Serial Monitor, showing live response as the finger bent.  
