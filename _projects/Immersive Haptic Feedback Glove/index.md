---
layout: post
title: Immersive Haptic Feedback Glove
description: A wearable glove designed to provide realistic tactile feedback for virtual reality environments, enabling users to feel virtual objects through precise force feedback and vibration patterns. Developed as a multidisciplinary engineering project, it integrates custom mechanical actuators, microcontroller-based control, and real-time software processing to deliver immersive and responsive haptic sensations. The glove was built with ergonomic considerations, lightweight materials, and optimized actuator placement to ensure comfort and prolonged usability.
skills:
- Embedded Systems Design
- Microcontroller Programming (Arduino/ESP32)
- Sensor Integration (Flex, IMU)
- Haptic Feedback Systems
- CAD Modeling & 3D Printing
main-image: 
---
## Functional Overview

The Immersive Haptic Feedback Glove simulates the sensation of touching and manipulating objects in a virtual environment by combining multiple sensing and feedback technologies. Finger flex sensors and an IMU track hand and finger positions, while miniature vibration motors and linear actuators apply pressure and texture cues to the user’s fingers. The system interfaces with VR software to trigger haptic patterns in real time, responding to object interactions such as gripping, sliding, or tapping.

## Hardware Architecture

Each finger is equipped with a flex sensor for motion tracking and a small linear actuator to provide force feedback. Vibration motors are strategically placed on the fingertips and palm to simulate texture and surface interaction. All sensors and actuators connect to a central microcontroller, which processes incoming data from the VR environment and outputs corresponding haptic signals. Custom 3D-printed mounts ensure secure component placement without impeding hand mobility.

## Software Control

A firmware layer written in C++ handles sensor polling, signal processing, and actuator control. The microcontroller communicates with a VR application via Bluetooth Low Energy (BLE), allowing wireless operation without restricting movement. Haptic patterns are generated dynamically based on collision events, object material properties, and user gestures within the virtual space.

## Fabrication Details

The glove base is made from a breathable, stretchable fabric to maintain comfort during extended use. All actuator mounts, sensor housings, and cable management components were designed in CAD and 3D printed with PETG for durability. Flexible wiring and low-profile connectors minimize bulk and maintain a lightweight feel. The system is modular, allowing easy maintenance or upgrades to sensors and actuators.

## Performance Highlights

- Real-time haptic feedback synchronized with VR interactions  
- Independent finger tracking with high positional accuracy  
- Modular design for easy component replacement  
- Wireless connectivity for unrestricted motion  
- Optimized weight distribution to reduce hand fatigue
