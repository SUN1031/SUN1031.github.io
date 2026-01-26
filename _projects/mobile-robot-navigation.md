---
layout: project
title: Autonomous Mobile Robot Navigation
tags: [ROS2, SLAM, Navigation, Gazebo]
---

## Overview
This project focuses on building an autonomous mobile robot capable of navigating unknown indoor environments.

## Objectives
- Implement full navigation pipeline
- Perform SLAM using LiDAR
- Plan collision-free paths
- Test in simulation and real robot

## System Architecture
Describe your node structure, TF tree, and data flow.

![Robot](/assets/images/navigation/robot-large.jpg)

## Implementation
- ROS2 navigation stack
- Mapping and localization
- Path planning and control
- Simulation in Gazebo

## Results
- Stable localization
- Successful goal reaching
- Robust obstacle avoidance
<video controls width="100%">
  <source src="/assets/videos/navigation/obstacle-avoidance.mp4" type="video/mp4">
</video>

The robot successfully avoided obstacles while moving.

## Future Work
- Dynamic obstacle handling
- Multi-robot navigation
- Real-world deployment
