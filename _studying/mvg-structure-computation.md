---
layout: default
title: Structure Computation
parent: multiple-view-geometry
date: 2026-02-17
---

# Structure Computation

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 12

---

## Why This Matters

After estimating camera geometry, the next goal is to recover
accurate 3D point locations.

Although triangulation conceptually finds the intersection of
viewing rays, real measurements contain noise, meaning rays rarely
intersect exactly.

Structure computation studies how to estimate 3D points in a way
that is geometrically meaningful and numerically stable.

This step is essential for:

- stereo reconstruction,
- structure-from-motion,
- SLAM landmark creation.

---

## Key Idea

A 3D point is reconstructed from multiple image observations by
finding the point whose projections best agree with measured image
points.

Rather than intersecting rays directly, reconstruction becomes an
optimization problem minimizing reprojection error.

Different triangulation methods correspond to different error models.

---

## Mathematical Formulation

### Projection Equations

Given cameras:

$$
\mathbf{x} = P\mathbf{X}, \quad
\mathbf{x}' = P'\mathbf{X},
$$

we seek the 3D point $\mathbf{X}$.

---

### Linear Triangulation

Using cross-product constraints:

$$
\mathbf{x} \times (P\mathbf{X}) = 0,
$$

we obtain a linear system:

$$
A\mathbf{X} = 0.
$$

Solution is obtained via SVD.

This provides an initial estimate.

---

### Reprojection Error

The geometrically meaningful error is:

$$
\sum_i \|\mathbf{x}_i - \hat{\mathbf{x}}_i\|^2,
$$

where $\hat{\mathbf{x}}_i$ is the projection of the estimated
3D point.

---

### Optimal Triangulation

The optimal estimate minimizes reprojection error:

$$
\min_{\mathbf{X}} \sum_i d(\mathbf{x}_i, P_i\mathbf{X})^2.
$$

This is a nonlinear optimization problem typically solved using:

- Gauss–Newton
- Levenberg–Marquardt.

---

## Intuition (My Understanding)

Each camera observation defines a ray in space.
Due to noise, rays do not intersect exactly.

Triangulation finds the point closest to all rays simultaneously.

Linear triangulation is fast but approximate.
Optimal triangulation adjusts the point so its projected images
align with observed features.

Thus reconstruction accuracy depends more on reprojection agreement
than geometric intersection.

---

## Important Observations

- Linear triangulation is only an initialization.
- Reprojection error is the correct geometric error measure.
- Small camera baselines cause large depth uncertainty.
- Numerical stability depends on camera configuration.
- Optimization significantly improves reconstruction accuracy.

---

## Questions / Confusions

- How does baseline length affect depth variance quantitatively?
- When does triangulation become degenerate?
- How is optimal triangulation integrated into bundle adjustment?

---

## Connection to Robotics

Structure computation corresponds to landmark estimation in SLAM:

1. estimate camera motion,
2. triangulate landmarks,
3. refine positions through optimization.

Accurate triangulation directly affects map quality,
pose estimation stability, and long-term tracking performance.
