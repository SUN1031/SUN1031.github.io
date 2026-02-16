---
layout: default
title: Introduction to Multi-View Geometry
topic: computer-vision
tags: [geometry, epipolar, vision]
date: 2026-02-16
---

## Why Multi-View Geometry?

Understanding how 3D structure emerges from multiple 2D images
is fundamental for visual SLAM and robot perception.

This study focuses on geometric reasoning rather than
pure learning-based approaches.

---

## Concepts Studied

- Camera projection model
- Epipolar geometry
- Essential & Fundamental matrices

---

## Notes

## Camera Projection Model

A 3D point projects onto the image plane as:

$$
x = K [R | t] X
$$

where:

- $K$ — intrinsic matrix
- $R$ — rotation
- $t$ — translation

