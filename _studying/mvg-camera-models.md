---
layout: default
title: Camera Models
parent: multiple-view-geometry
date: 2026-02-17
---

# Camera Models

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 6

---

## Why This Matters

A camera defines how the 3D world becomes a 2D image.
All multiple view geometry problems — pose estimation, triangulation,
epipolar geometry, and SLAM — depend on an accurate camera model.

Understanding the camera matrix explains:

- how pose and calibration are represented,
- why images lose depth information,
- how geometry connects world coordinates to pixels.

This chapter provides the mathematical foundation of visual perception.

---

## Key Idea

A camera is modeled as a **projective mapping**
from 3D projective space to the image plane.

The mapping is represented by a matrix:

$$
\mathbf{x} = P\mathbf{X}
$$

where:

- $\mathbf{X}$ — 3D world point (homogeneous coordinates)
- $\mathbf{x}$ — image point
- $P$ — camera projection matrix.

The camera matrix combines:

1. camera pose (position and orientation),
2. internal camera parameters.

---

## Mathematical Formulation

### Camera Projection Matrix

The general camera model:

$$
P = K [R \mid t]
$$

where:

- $R$ — rotation matrix ($3 \times 3$)
- $t$ — translation vector
- $K$ — intrinsic calibration matrix.

---

### Intrinsic Parameters

$$
K =
\begin{bmatrix}
f_x & s & c_x \\
0 & f_y & c_y \\
0 & 0 & 1
\end{bmatrix}
$$

Parameters:

- $f_x, f_y$ — focal lengths
- $(c_x, c_y)$ — principal point
- $s$ — skew parameter.

These describe how camera coordinates map to pixel coordinates.

---

### Extrinsic Parameters

Extrinsics describe camera pose:

$$
[R \mid t]
$$

They transform world coordinates into the camera coordinate frame.

---

### Projection Process

A 3D point projects as:

$$
\mathbf{x} = K(R\mathbf{X} + t)
$$

followed by perspective division:

$$
(x, y) =
\left(
\frac{x_1}{x_3},
\frac{x_2}{x_3}
\right)
$$

---

## Intuition (My Understanding)

The camera matrix separates two ideas:

- **Where the camera is** (extrinsics)
- **How the camera sees** (intrinsics)

The camera first moves the world into its own coordinate system,
then performs perspective projection.

Depth is lost because multiple 3D points along the same viewing ray
produce the same image coordinate.

Thus, a single image cannot recover absolute scale.

---

## Important Observations

- The camera matrix has 11 degrees of freedom (up to scale).
- Intrinsics remain fixed for a calibrated camera.
- Extrinsics change as the camera moves.
- Projection is linear in homogeneous coordinates.
- Calibration determines metric reconstruction accuracy.

---

## Questions / Confusions

- How sensitive is reconstruction to intrinsic calibration error?
- When can skew be safely ignored?
- How does lens distortion integrate with this model?

---

## Connection to Robotics

The camera model directly connects perception and motion:

- visual odometry estimates $R$ and $t$,
- SLAM repeatedly updates extrinsic parameters,
- calibration determines metric accuracy,
- sensor fusion aligns camera pose with IMU frames.

The matrix $P = K[R|t]$ is effectively the mathematical interface
between a robot and the visual world.
