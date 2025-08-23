---
layout: post
title: Autonomous Tennis Ball Retrieval Robot
description: A mechanical system engineered to autonomously catch a free-falling tennis ball and deliver it six feet into a tray within 30 seconds. Built under strict design constraints, it uses a single input to activate, operates without human contact during motion, and adheres to rules prohibiting non-engineering materials, kit-based components, and temporary fasteners. The system was developed using CAD modeling, simulation, and digital manufacturing, with custom parts designed to proper tolerancing and GD&T standards for accurate fit and function. All components were fabricated using approved methods such as 3D printing to ensure compliance and reliability.
skills: 
- Mechanical Design
- SolidWorks
- 3D Printing
- Engineering Drawing & GD&T
- COTS Component Integration
main-image: /project.webp
---
## Mechanical Function

The mechanism uses a fixed, angled ramp to intercept a tennis ball dropped from approximately three feet. The ramp is mounted to a base and positioned so the ball makes contact after falling at least two feet, as required. The ball’s momentum carries it into a transfer channel driven by a crank-powered linear shuttle. A one-directional manual crank initiates the motion; no motor or controller is involved.

The shuttle moves the ball laterally across a six-foot span and releases it into a shallow tray. At no point does the mechanism make contact with the tray or operator. The entire operation completes within 30 seconds and is capable of resetting for an additional transfer cycle if needed.

## Simulation-Driven Reinforcement

SolidWorks Simulation was used to analyze stress distribution on the ramp during ball impact. Loads were applied at the impact zone, and fixed supports were placed at bolt hole locations. The von Mises analysis showed stress concentrations at the top and bottom edges of the ramp. To address this, vertical ribs were added to both sides, increasing stiffness and preventing deformation during repeated impacts.

![Simulation Analysis](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20SIM%201.png)  
*Von Mises stress plot showing high-stress regions at the ramp edges.*

## Animations

The following frames show the motion study performed in SolidWorks, demonstrating how the shuttle system captures and delivers the tennis ball. The sequence verifies that the design meets the time and distance requirements.

![Animation 1](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20ANIM%201.png)  
*Initial ball drop approaching the shuttle system.*

![Animation 2](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20ANIM%202.png)  
*Ball guided into the shuttle body for transfer.*

![Animation 3](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20ANIM%203.png)  
*Shuttle moving ball towards the tray with controlled motion.*

![Animation 4](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20ANIM%204.png)  
*Final release of the ball into the tray at the target position.*

## Fabrication Details

The ramp, shuttle base, and ball guide components were all 3D printed using PLA. Standard hex nuts and bolts (M4) were sourced from Ace Hardware and used to fasten printed parts to a plywood base. No adhesives, tape, or temporary fasteners were used. All parts were designed to comply with rules excluding foam, cardboard, erector sets, and non-engineering materials.

![COTS Components](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20COTS.png)  
*Commercial off-the-shelf hardware (M4 bolts and hex nuts) used for fastening 3D-printed parts.*

## Performance Constraints

- Ball must freefall at least 2 feet before contact  
- Tray must be 6 feet from the ball’s release point  
- No part of the mechanism can start within 1 foot of the tray  
- Mechanism must not touch the tray, person, or floor outside its footprint  
- Entire cycle must complete in under 30 seconds  

## Assembly Pictures

Here are photos of the assembly at different persspectives:

![Assembly Picture 1](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20PIC%201.png)
![Assembly Picture 2](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20PIC%202.png)
![Assembly Picture 3](/_projects/Autonomous%20Tennis%20Ball%20Retrieval%20Robot/CHP%20PIC%203.png)

## Demo Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/cayjFbJfd4g" 
title="Tennis Ball Transfer Mechanism Demo" frameborder="0" allowfullscreen></iframe>

