---
layout: project
title: Human-Guiding Autonomous Mobile Robot
tags: [ROS, SLAM, Navigation]
featured: true
thumbnail: /assets/images/navigation/thumbnail.png
summary: Development of a Human-Centered Mobile Robotics Platform with Physical Interaction.
---

## Overview

Autonomous mobile robots are increasingly deployed in shared human environments such as public facilities, transportation hubs, and service spaces. While navigation and localization technologies have advanced significantly, guiding humans safely and comfortably remains a challenging problem.

Most robots assume humans will adapt to robotic behavior. In reality, users move unpredictably, walk at different speeds, and often struggle with conventional interfaces such as touchscreens or voice commands.

This project explores an alternative approach:

> **Designing an autonomous robot that adapts its motion and behavior to humans through continuous physical interaction.**

The objective was to develop a human-guiding mobile robot capable of:

- Stable autonomous mobility
- Safe operation in shared environments
- Natural human–robot interaction
- Adaptive motion synchronized with human movement

The final system integrates mechanical design, kinematic modeling, sensor fusion, and a novel physical interaction interface called the **Smart Handle**.

---

## Design Philosophy

Early prototypes revealed that navigation accuracy alone does not guarantee effective human guidance. Users often had difficulty maintaining distance from the robot or interacting naturally.

The project therefore followed three guiding principles:

1. **Human comfort over maximum autonomy**
2. **Physical interaction over abstract interfaces**
3. **Robustness through system integration**

The robot was designed as a **human-centered autonomous system**, where interaction continuously influences motion behavior.

---

## System Architecture

The robot was implemented using a modular ROS-based architecture separating perception, interaction, and control layers.

### High-Level Pipeline

Sensors → State Estimation → Interaction Interpretation → Motion Control → Actuation

### Core Subsystems

- Differential-drive mobile platform
- Sensor-fusion pose estimation
- Adaptive velocity controller
- Physical human–robot interaction interface
- Real-time behavior integration

---

## Hardware Development

### Mobile Robot Base

A custom mobile robot base was designed to provide stable and precise motion suitable for human-guidance tasks.

A differential-drive configuration was selected due to:

- Predictable kinematics
- Accurate low-speed control
- Mechanical simplicity
- Indoor maneuverability

Mechanical development included:

- Motor and caster wheel placement optimization
- Structural frame design
- Balanced mass distribution
- Expandable mounting structure

Motor torque requirements were calculated using load moment of inertia analysis to ensure reliable operation during human interaction.

---

### Electrical System

The electrical architecture supports continuous autonomous operation and sensor integration.

**Main components**

- Intel NUC mini-PC running ROS
- Motor drivers and encoder interfaces
- Power regulation and distribution modules
- Integrated sensor network

**Sensors**

- Wheel encoders for odometry
- Obstacle detection sensors
- Rear-facing camera for user monitoring
- Flex sensors embedded in the Smart Handle

---

## Software Development

### Kinematic Modeling and Motion Control

Forward kinematics for the differential-drive robot were analytically derived to enable precise motion control.

The differential drive model is:

$$
\dot{x} = v \cos \theta
$$

$$
\dot{y} = v \sin \theta
$$

$$
\dot{\theta} = \omega
$$


A Jacobian-based formulation converts wheel velocities into robot motion commands.

Control objectives included:

- Smooth acceleration and deceleration
- Stable low-speed motion
- Safe interaction-aware behavior

---

### Pose Estimation via Sensor Fusion

Indoor environments introduce uncertainty due to wheel slip and sensor noise. A sensor fusion–based pose estimation approach was implemented to improve robustness.

Benefits:

- Reduced localization drift
- Improved trajectory stability
- Reliable motion estimation during interaction

---

## Smart Handle: Physical Human–Robot Interaction

### Motivation

Traditional robot interfaces rely on speech or graphical interaction, which can be unreliable or unintuitive in real environments.

The **Smart Handle** enables interaction through physical connection, allowing users to communicate naturally through movement.

---

### Interface Design

The Smart Handle connects the robot and user using a flexible leash embedded with flex sensors.

**Design goals**

- Intuitive interaction
- Comfortable following distance
- Continuous human–robot feedback
- Reliable operation in constrained environments

Handle deformation becomes a measurable representation of user behavior.

---

### Adaptive Motion Control

A linear regression model maps handle bending to estimated user–robot distance.

Robot behavior adapts dynamically:

- Increased bending → robot slows down
- Normal state → maintain speed
- Excessive separation → robot stops and waits

This enables synchronized motion between human and robot.

---

### Intelligent Interaction via Neural Networks

An Artificial Neural Network (ANN) processes flex sensor signals to recognize interaction patterns.

Supported interactions:

- Walking intention detection
- Stop requests
- Gesture-based command input
- Behavior changes via handle motion

This allows communication without speech or screens.

---

### Control Integration

Flex Sensors → Signal Processing → Neural Network → Interaction State → Motion Controller

Human interaction directly influences navigation behavior in real time.

---

## Experimental Evaluation

![Robot](/assets/images/navigation/robot.jpg)

### Mobility Performance

- Stable indoor navigation achieved
- Smooth velocity adaptation during guidance
- Reliable obstacle avoidance
<video controls width="100%"
  preload="metadata"
  playsinline
  muted>
  <source src="/assets/videos/navigation/obstacle-avoidance.mp4" type="video/mp4">
</video>

### Interaction Performance

- Accurate estimation of user distance
- Adaptive speed control validated experimentally
- Successful gesture recognition using ANN models

### Human Guidance Behavior

The robot maintained consistent user-following behavior and safely adjusted motion based on interaction feedback.

---

## Key Contributions

- Designed and built a complete autonomous mobile robotics platform
- Developed a reusable differential-drive robot base
- Implemented kinematic modeling and sensor-fusion localization
- Proposed the **Smart Handle**, a novel physical human–robot interaction interface
- Integrated machine learning into real-time motion control
- Demonstrated human-centered adaptive robot behavior

---

## Lessons Learned

- Human interaction must be integrated into control design from the beginning.
- Physical interfaces can outperform traditional digital interfaces.
- Real-world robotics challenges are dominated by system integration.
- Reliable autonomy emerges from hardware–software co-design.

---

## Technologies Used

- **ROS (Robot Operating System)**
- C/C++, Python
- Differential Drive Kinematics
- Sensor Fusion
- Neural Networks
- Embedded Linux
- Mobile Robotics Hardware Design
