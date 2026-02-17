---
layout: default
title: Projective Geometry and Transformations
parent: multiple-view-geometry
date: 2026-02-17
---

# Projective Geometry and Transformations

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapters 2–3

---

## Why This Matters

Projective geometry provides the mathematical language of image formation.
A camera does not preserve Euclidean properties such as distances or angles;
instead, it preserves projective relationships.

Understanding projective space explains:

- why depth information is lost in images,
- why scale ambiguity exists,
- how multiple views recover 3D structure.

This framework is fundamental for visual SLAM, 3D reconstruction,
and camera pose estimation.

---

## Key Idea

Images are projections of 3D scenes onto a 2D plane through a
**projective transformation**.

Rather than working in Euclidean coordinates, points are represented
in **homogeneous coordinates**, allowing projection and perspective
division to be expressed linearly.

Key concepts:

- Homogeneous coordinates unify finite and infinite points.
- Projection becomes a linear mapping in projective space.
- Geometric transformations are represented by matrices.

---

## Mathematical Formulation

### Homogeneous Coordinates

A 2D point:

$$
(x, y)
$$

is represented as:

$$
\mathbf{x} = (x, y, 1)^T
$$

More generally,

$$
\mathbf{x} \sim (\lambda x, \lambda y, \lambda)^T
$$

for any nonzero scalar $\lambda$.

---

### Projective Transformation (Homography)

A projective transformation is:

$$
\mathbf{x}' = H \mathbf{x}
$$

where

$$
H \in \mathbb{R}^{3 \times 3}
$$

is defined up to scale.

---

### Camera Projection

A 3D point projects into an image as:

$$
\mathbf{x} = P \mathbf{X}
$$

where

- $\mathbf{X} \in \mathbb{P}^3$ (projective 3D point)
- $\mathbf{x} \in \mathbb{P}^2$ (image point)
- $P$ is a $3 \times 4$ camera matrix.

---

### Perspective Division

Image coordinates are recovered by:

$$
(x, y) =
\left(
\frac{x_1}{x_3},
\frac{x_2}{x_3}
\right)
$$

---

## Intuition (My Understanding)

Projective geometry treats scaling as irrelevant information.
Two vectors that differ only by scale represent the same point.

This makes sense physically:

A camera measures direction of light rays, not absolute distance
along the ray.

Points at infinity naturally arise because parallel lines in 3D
appear to meet in images (vanishing points).

Thus, projective space models perspective effects naturally,
while Euclidean geometry cannot.

---

## Important Observations

- Linear algebra works cleanly only in homogeneous coordinates.
- Perspective projection becomes linear before normalization.
- Points at infinity encode direction information.
- Homographies describe planar scene transformations.
- Many vision algorithms estimate geometry only up to scale.

---

## Questions / Confusions

- How does numerical conditioning affect homography estimation?
- When does affine geometry become a sufficient approximation?
- How do projective ambiguities propagate into bundle adjustment?

---

## Connection to Robotics

Projective geometry explains why monocular SLAM suffers from
scale ambiguity and why additional constraints (stereo, IMU,
or known baselines) are required to recover metric scale.
