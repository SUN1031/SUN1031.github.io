---
layout: default
title: 3D Reconstruction of Cameras and Structure
parent: multiple-view-geometry
date: 2026-02-17
---

# 3D Reconstruction of Cameras and Structure

Note from Hartley & Zisserman, Chapter 10

---

## Why This Matters

Understanding how 3D points project into images is the
foundation of visual SLAM and 3D reconstruction.

---

## Key Idea

A camera maps a 3D world point to a 2D image point using
a projective transformation.

---

## Mathematical Formulation

\begin{equation}
x = K [R|t] X
\end{equation}

where:

- $X$ — 3D world point
- $R, t$ — camera pose
- $K$ — intrinsic matrix

---

## Intuition (My Understanding)

The projection removes depth information, which explains
why multiple views are required to recover 3D structure.

---

## Important Observations

- Scale ambiguity exists in projective space.
- Geometry, not appearance, drives reconstruction.

---

## Questions / Confusions

- How does numerical instability affect estimation?
- When does normalization become necessary?

