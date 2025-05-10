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

## Fabrication Details

The ramp, shuttle base, and ball guide components were all 3D printed using PLA. Standard hex nuts and bolts (M4) were sourced from Ace Hardware and used to fasten printed parts to a plywood base. No adhesives, tape, or temporary fasteners were used. All parts were designed to comply with rules excluding foam, cardboard, erector sets, and non-engineering materials.

## Performance Constraints

- Ball must freefall at least 2 feet before contact  
- Tray must be 6 feet from the ball’s release point  
- No part of the mechanism can start within 1 foot of the tray  
- Mechanism must not touch the tray, person, or floor outside its footprint  
- Entire cycle must complete in under 30 seconds  
- Extra credit available for a second cycle within time limit
