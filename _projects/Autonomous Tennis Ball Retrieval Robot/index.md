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
## Detailed Mechanical Function

The mechanism captures the tennis ball mid-air using a sloped ramp designed to absorb impact and redirect motion. Once collected, the ball is guided through a channel system actuated by a single input—a crank or motor trigger—driving the transport mechanism. All components are mechanically linked, ensuring the motion sequence unfolds without the need for sensors or real-time control. The mechanism maintains full clearance from the tray, user, and floor, complying with strict interaction rules.

## Simulation and Structural Design

Simulation efforts focused on the ramp component, which absorbs the full energy of the falling ball. Using SolidWorks Simulation, von Mises stress analysis identified the top and bottom edges as the most vulnerable areas under load. Reinforcement ribs were added to increase stiffness and prevent deformation. This allowed the part to maintain structural integrity across repeated impacts without excessive material use.

## Part Manufacturing and Tolerancing

Parts were designed from scratch and fabricated via 3D printing using engineering-grade filament. All major components were dimensioned with proper tolerancing, including feature control frames and datums per GD&T standards. Fastening methods were selected to ensure rigidity and repeatable assembly without violating design rules against adhesives, string, or temporary fixes.

## Drawing and Documentation

The complete design package includes assembly drawings, a bill of materials, and fully detailed 2D engineering drawings for two custom parts. These drawings meet industry standards and were created to support manufacturability, inspection, and functional alignment. The documentation reflects a workflow intended for physical production—not just modeling.

## Execution Constraints

- Only approved engineering materials (no foam, cardboard, or craft materials)
- No prefabricated kits or shortcut connectors
- No sensors, microcontrollers, or active control systems
- Only one manual input allowed per activation
- Maximum cycle time: 30 seconds

