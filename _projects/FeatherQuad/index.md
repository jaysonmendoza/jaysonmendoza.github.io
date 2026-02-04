---
layout: post
title: FeatherQuad
description: This project focuses on designing and virtually testing a custom quadcopter from scratch. The drone’s components, mass, and geometry are defined, then its flight behavior is modeled and tested in MATLAB to verify stable hover and control. A custom 3D-printed frame is designed in SolidWorks and analyzed to ensure it is strong and stiff enough for flight. The goal is to validate the drone’s design through simulation and analysis before building it physically.
skills:
- CAD Design
- 3D Printing
- Electronics Integration
- Soldering
- Flight Tuning
main-image: /drone_pic1.png
published: true
---

## COTS Parts List

| Item | Qty | Unit Price (USD) | Total Price (USD) | Notes |
|------|-----|------------------|-------------------|-------|
| Transmitter + Receiver (Radiolink T8FB + R8EF) | 1 | 49.99 | 49.99 | 8-channel 2.4 GHz RC system |
| Battery | 1 | 11.72 | 11.72 | 4S 1500 mAh 80C LiPo (XT60) |
| Flight Controller | 1 | 33.99 | 33.99 | HGLRC F405 8S V1, ICM42688P |
| ESC | 1 | 39.99 | 39.99 | SEQURE 65A 4-in-1, 2–6S, AM32 |
| Propellers | 1 | 9.99 | 9.99 | HQProp 5×4.3×3 (8 pcs, CW/CCW) |
| Motor | 4 | 15.75 | 62.99 | Axisflying AE2207 V2 1960KV (set of 4) |
| **Subtotal** | **6 items** | — | **208.67** | Amazon cart total |

## SolidWorks Screenshot
<img src="/_projects/FeatherQuad/Screenshot%202026-02-03%20182645.png" alt="SolidWorks Screenshot" style="max-width:100%; height:auto;">

## MATLAB Simulation Results

<p><strong>Altitude Response (6-DOF Simulation)</strong></p>
<img src="/_projects/FeatherQuad/Altitude.png" style="max-width:70%; height:auto;">

<p><strong>Roll Response (6-DOF Simulation)</strong></p>
<img src="/_projects/FeatherQuad/Roll.png" style="max-width:70%; height:auto;">

<p><strong>Pitch Response (6-DOF Simulation)</strong></p>
<img src="/_projects/FeatherQuad/Pitch.png" style="max-width:70%; height:auto;">

<p><strong>Yaw Response (6-DOF Simulation)</strong></p>
<img src="/_projects/FeatherQuad/Yaw.png" style="max-width:70%; height:auto;">

<p><strong>Open-Loop Attitude Dynamics</strong></p>
<img src="/_projects/FeatherQuad/Figure_1.png" style="max-width:70%; height:auto;">

<p><strong>Closed-Loop Attitude Control (PD)</strong></p>
<img src="/_projects/FeatherQuad/Figure_2.png" style="max-width:70%; height:auto;">

<p><strong>Total Thrust Command vs Time</strong></p>
<img src="/_projects/FeatherQuad/Total Thrust Command.png" style="max-width:70%; height:auto;">



---

### Conclusion
MATLAB simulations confirm that the drone design is dynamically feasible, stable under control, and capable of sustained hover, validating the design prior to physical fabrication.

