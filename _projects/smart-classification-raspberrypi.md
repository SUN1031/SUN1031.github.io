---
layout: project
title: Smart Brick Classification System with Raspberry Pi
tags: [Computer Vision, Embedded AI, Raspberry Pi, TFLite, Automation]
featured: true
thumbanil: /asset/images/raspberrypi/system-overview.jpg
summary: Real-time classification and automated sorting of toy bricks by color and size using Raspberry Pi, CNN inference, and servo-actuated conveyor system.
---

## Overview
This project presents a smart classification system that automatically sorts **toy bricks** according to their **color and size**. The system integrates a conveyor belt, camera module, and servo motors to form a complete perception–decision–action pipeline controlled by a Raspberry Pi.

Because Raspberry Pi does not provide sufficient memory and computational power for deep learning training, the neural network was trained in **Google Colab**, while only the optimized model was deployed on the Raspberry Pi using **TensorFlow Lite** for real-time inference.

---

## Classification Targets

![Toy brick categories](/assets/images/raspberrypi/bricks.jpg)

The system classifies bricks into **9 categories**, defined by:

- **3 colors:** red, green, blue
- **3 sizes:** large, medium, small

Each brick passes under the camera in a top-view configuration while moving on the conveyor belt. The Raspberry Pi analyzes the captured image and determines the brick category before activating the sorting mechanism.

---

## System Overview

![Smart brick classification system](/asset/images/raspberrypi/system-overview.jpg)

The complete platform consits of:
- **Conveyor belt** transporting bricks at constant speed
- **Camera module** capturing top-view images
- **Two servo motors** acting as sorting gates
- **Collection bins** for separated bricks
- **Breadboard and power circuit** for electronics interfacing

---

## Methodology

### 1. Brick Color Recognition
- A **CNN-based model** was designed to classify brick color
- Training executed on **Google Colab** due to Pi limitations
- The trained network was converted to **TFLite** for lightweight inference
- Only forward inference runs on the Raspberry Pi

### 2. Brick Size Estimation
- Brick contour extracted using **OpenCV**
- **Contour area** used to distinguish:
  - Small bricks
  - Medium bricks
  - Large bricks
 
### 3. Real-Time Operation Pipeline

1. Capture image while conveyor is moving
2. Run TFLite inference to predict brick color
3. Detect brick contour and compute area
4. Combine color + size → final class  
5. Generate PWM signals to servo motors
6. Physically sort the brick into the correct bin

---

## Implementation Tools

- **Python**
- **TensorFlow / TensorFlow Lite**
- **OpenCV**
- **Raspberry Pi GPIO**
- **Google Colab** (training environment)

---

## Results

- Successful **real-time brick classification** on Raspberry Pi
- Reliable recognition of **9 brick categories**
- Fully automated physical sorting using servo actuation
- Edge AI deployment achieved without external PC

---

## Demonstration Videos

### Color-Based Sorting

<div class="video-row">
  <div>
    <strong>Conveyor Belt</strong>
    <video controls width="100%">
      <source src="/assets/videos/brick/color_conveyor.mp4" type="video/mp4">
    </video>
  </div>

  <div>
    <strong>GUI Output</strong>
    <video controls width="100%">
      <source src="/assets/videos/brick/color_gui.mp4" type="video/mp4">
    </video>
  </div>
</div>

### Size-Based Sorting
  
<div class="video-row">
  <div>
    <strong>Conveyor Belt</strong>
    <video controls width="100%">
      <source src="/assets/videos/brick/size_conveyor.mp4" type="video/mp4">
    </video>
  </div>

  <div>
    <strong>GUI Output</strong>
    <video controls width="100%">
      <source src="/assets/videos/brick/size_gui.mp4" type="video/mp4">
    </video>
  </div>
</div>

---

## Acknowledgment

This project was supported by **Robodyne Systems Co., Ltd.**, which provided hardware compents and manufacturing support.

