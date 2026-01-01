---
layout: post
title: Smart pH Monitoring System
description: An automated pH monitoring and dosing system that measures solution pH and adds acid or base to maintain a target range. The system operates autonomously using a pH sensor, an Arduino microcontroller, and electrically driven pumps.
skills:
- Arduino
- pH Sensor
- Pumps
- Electronics
- Programming
main-image: /project.webp
---

## Project Overview

This project is an automated system that controls the pH of a liquid. A pH sensor continuously measures the solution, and an Arduino decides whether to add acid or base. Once powered on, the system runs without user input.

## How It Works

A pH probe is placed in the solution and sends readings to the Arduino. The Arduino compares the reading to preset limits.

- If the pH is too high, the acid pump turns on  
- If the pH is too low, the base pump turns on  

Each pump runs for a short time to avoid overcorrecting.

## Hardware

- Arduino microcontroller  
- pH sensor module  
- Two pumps (acid and base)  
- Tubing and containers for chemicals  
- Power supply and wiring  

Acid and base are stored in separate containers, each with its own pump and tubing.

## Testing

The system was tested by manually changing the pH of the liquid. The sensor detected the change and the correct pump activated to bring the pH back into range. The behavior was repeatable across multiple tests.

## Result

The final system demonstrates automatic sensing, decision-making, and actuation to maintain pH without manual intervention.

## Build Photos

![Build Photo 1](/_projects/Smart%20pH%20Monitoring%20System/IMG_8077.jpg)
![Build Photo 2](/_projects/Smart%20pH%20Monitoring%20System/IMG_8079.jpg)
![Build Photo 3](/_projects/Smart%20pH%20Monitoring%20System/IMG_8084.jpg)
![Build Photo 4](/_projects/Smart%20pH%20Monitoring%20System/IMG_8087.jpg)
![Build Photo 5](/_projects/Smart%20pH%20Monitoring%20System/pH1.jpg)

