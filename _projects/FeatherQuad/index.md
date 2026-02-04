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

## MATLAB Validation

All flight behavior was validated virtually in MATLAB prior to any physical build.

---

### Hover & Thrust Feasibility
- Hover thrust computed using \( T = mg \)
- Per-motor hover thrust calculated for a quad configuration
- Thrust margin verified to be well above minimum requirement

Result: **PASS — sufficient thrust margin**

---

### Open-Loop Attitude Dynamics
Uncontrolled roll dynamics were simulated to verify rigid-body equations of motion.

**Result:** Roll angle diverges as expected for an open-loop rigid body, confirming correct inertia and dynamics modeling.

![Open-loop attitude response](_projects/FeatherQuad/Figure_1.png)

---

### Closed-Loop Attitude Control (PD)
A PD controller was applied to stabilize attitude.

**Result:**  
- Roll angle converges to reference  
- Angular rate decays to zero  
- System is stable and controllable  

![PD roll angle tracking](_projects/FeatherQuad/Figure_2.png)

---

### Full 6-DOF Flight Simulation
A full six-degree-of-freedom rigid-body model was simulated with altitude and attitude control.

**Observed behavior:**
- Altitude rises smoothly and stabilizes at the target
- Roll, pitch, and yaw remain bounded and stable
- Total thrust converges to \( mg \)

**Results:**

**Altitude**
![Altitude response](_projects/FeatherQuad/Altitude.png)

**Roll**
![Roll response](_projects/FeatherQuad/Roll.png)

**Pitch**
![Pitch response](_projects/FeatherQuad/Pitch.png)

**Yaw**
![Yaw response](_projects/FeatherQuad/Yaw.png)

**Total Thrust Command**
![Total thrust command](_projects/FeatherQuad/Total%20Thrust%20Command.png)

---

### Conclusion
MATLAB simulations confirm that the drone design is dynamically feasible, stable under control, and capable of sustained hover, validating the design prior to physical fabrication.

