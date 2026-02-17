---
layout: default
title: 3D Reconstruction of Cameras and Structure
parent: multiple-view-geometry
date: 2026-02-17
---

# 3D Reconstruction of Cameras and Structure

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 10

---

## Why This Matters

After estimating epipolar geometry, the next goal is to recover:

1. camera motion,
2. 3D scene structure.

This process turns image correspondences into a geometric
model of the world.

It forms the basis of:

- structure-from-motion,
- stereo vision,
- visual SLAM pipelines.

---

## Key Idea

Two images constrain camera geometry through the Fundamental Matrix.
From this relationship, we can reconstruct:

- camera projection matrices,
- 3D point locations.

However, reconstruction from uncalibrated cameras is only
determined **up to a projective transformation**.

Thus, geometry can be recovered consistently,
but not yet metrically.

---

## Mathematical Formulation

### From Fundamental Matrix to Cameras

Given $F$, canonical camera matrices can be chosen as:

$$
P = [I \mid 0]
$$

$$
P' = [[e']_\times F \mid e']
$$

where:

- $e'$ is the epipole in the second image,
- $[e']_\times$ is the skew-symmetric matrix.

These cameras reproduce the same epipolar geometry.

---

### Triangulation

Given corresponding image points:

$$
\mathbf{x} \leftrightarrow \mathbf{x}'
$$

the 3D point $\mathbf{X}$ satisfies:

$$
\mathbf{x} = P\mathbf{X}, \quad
\mathbf{x}' = P'\mathbf{X}.
$$

Stacking constraints yields a linear system solved via SVD.

This process is called **triangulation**.

---

### Projective Ambiguity

If $H$ is any $4 \times 4$ projective transformation,

$$
P \rightarrow PH^{-1}, \quad
\mathbf{X} \rightarrow H\mathbf{X}
$$

produces identical image projections.

Therefore reconstruction is unique only up to projective scale.

---

## Intuition (My Understanding)

Each image provides a viewing ray toward a 3D point.
The true point lies at the intersection of rays from both cameras.

Because measurements are noisy, rays rarely intersect exactly.
Triangulation finds the point that best satisfies both projections.

Without calibration, reconstruction preserves geometry
only in a projective sense — shapes are consistent but
distances are distorted.

---

## Important Observations

- Fundamental matrix determines camera geometry up to projective ambiguity.
- Reconstruction requires choosing a canonical camera frame.
- Triangulation converts correspondences into 3D points.
- Noise prevents exact ray intersection.
- Metric reconstruction requires calibration (Essential matrix).

---

## Questions / Confusions

- How unstable is triangulation for small camera baselines?
- How does projective ambiguity affect downstream optimization?
- When does reconstruction become numerically ill-conditioned?

---

## Connection to Robotics

This chapter describes the initialization stage of many
visual SLAM systems:

1. estimate correspondences,
2. compute Fundamental matrix,
3. recover camera motion,
4. triangulate initial landmarks.

The resulting structure serves as the starting map
for iterative pose and map refinement.
