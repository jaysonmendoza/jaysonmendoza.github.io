---
layout: post
title: Smart pH Monitoring System
description: An automated pH monitoring and dosing system that measures solution pH and adds acid or base to keep it within a target range. The system runs autonomously using an Arduino, a pH sensor, and two pumps.
skills:
- Arduino
- pH Sensor
- Pumps
- Electronics
- Programming
main-image: /project.webp
---

## Project Overview

This project is an automatic pH control system. A pH probe measures the acidity of a liquid, and an Arduino decides whether to add acid or base. Once powered on and given a target pH, the system runs on its own without user interaction.

## How It Works

The pH sensor sends readings to the Arduino. The Arduino compares the current pH to a user-defined target value.

- If the pH is too low, the base pump turns on  
- If the pH is too high, the acid pump turns on  
- If the pH is within range, both pumps remain off  

Each pump runs briefly to prevent overshooting the target pH.

## Hardware Used

- Arduino microcontroller  
- pH sensor module  
- Two pumps (acid and base)  
- LCD display  
- Tubing and chemical containers  
- Power supply and wiring  

Acid and base are kept in separate containers with dedicated tubing.

## Build Photos

<img src="/_projects/Smart%20pH%20Monitoring%20System/IMG_8077.jpg" width="500">
<img src="/_projects/Smart%20pH%20Monitoring%20System/IMG_8079.jpg" width="500">
<img src="/_projects/Smart%20pH%20Monitoring%20System/IMG_8084.jpg" width="500">
<img src="/_projects/Smart%20pH%20Monitoring%20System/IMG_8087.jpg" width="500">
<img src="/_projects/Smart%20pH%20Monitoring%20System/pH1.jpg" width="500">

## Arduino Code

```cpp
#include <LiquidCrystal.h>

#define SensorPin 0

LiquidCrystal lcd(2, 3, 4, 5, 6, 7);

unsigned long int avgValue;
int buf[10], temp;

byte acidPump = 8;
byte basePump = 10;

float desiredPH;
float tolerance = 0.10;

bool phSet = false;

void setup() {
  Serial.begin(9600);
  while (!Serial);

  pinMode(acidPump, OUTPUT);
  pinMode(basePump, OUTPUT);

  digitalWrite(acidPump, HIGH);
  digitalWrite(basePump, HIGH);

  lcd.begin(16, 2);
  lcd.clear();

  lcd.setCursor(0, 0);
  lcd.print("Enter desired pH");
  lcd.setCursor(0, 1);
  lcd.print("via Serial");
}

void loop() {

  if (!phSet) {
    if (Serial.available() > 0) {
      desiredPH = Serial.parseFloat();
      while (Serial.available()) Serial.read();

      phSet = true;

      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Target pH:");
      lcd.print(desiredPH, 2);
      delay(2000);
      lcd.clear();
    }
    return;
  }

  for (int i = 0; i < 10; i++) {
    buf[i] = analogRead(SensorPin);
    delay(10);
  }

  for (int i = 0; i < 9; i++) {
    for (int j = i + 1; j < 10; j++) {
      if (buf[i] > buf[j]) {
        temp = buf[i];
        buf[i] = buf[j];
        buf[j] = temp;
      }
    }
  }

  avgValue = 0;
  for (int i = 2; i < 8; i++) {
    avgValue += buf[i];
  }

  float currentPH = (float)avgValue * 5.0 / 1024.0 / 6.0;
  currentPH = 3.5 * currentPH;

  lcd.setCursor(0, 0);
  lcd.print("pH:");
  lcd.print(currentPH, 2);
  lcd.print(" T:");
  lcd.print(desiredPH, 2);

  lcd.setCursor(0, 1);

  if (currentPH < desiredPH - tolerance) {
    digitalWrite(basePump, LOW);
    digitalWrite(acidPump, HIGH);
    lcd.print("Adding BASE   ");
  }
  else if (currentPH > desiredPH + tolerance) {
    digitalWrite(acidPump, LOW);
    digitalWrite(basePump, HIGH);
    lcd.print("Adding ACID   ");
  }
  else {
    digitalWrite(acidPump, HIGH);
    digitalWrite(basePump, HIGH);
    lcd.print("pH STABLE     ");
  }

  delay(1000);
}

