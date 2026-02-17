---
layout: default
title: Computation of the Camera Matrix P
parent: multiple-view-geometry
date: 2026-02-17
---

# Computation of the Camera Matrix P

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 7

---

## Why This Matters

The camera matrix connects measurable image points to real-world
3D geometry. In practice, the matrix is unknown and must be estimated
from data.

Computing the camera matrix enables:

- camera calibration,
- pose estimation,
- 3D reconstruction,
- initialization of multi-view geometry algorithms.

This chapter shows how geometry becomes a solvable estimation problem.

---

## Key Idea

Given correspondences between 3D points and their image projections,

$$
\mathbf{X}_i \leftrightarrow \mathbf{x}_i,
$$

we can estimate the camera matrix

$$
\mathbf{x} = P\mathbf{X}.
$$

Each correspondence produces linear constraints on the entries of $P$.
Stacking many constraints yields a homogeneous linear system solved
using SVD.

This method is known as the **Direct Linear Transform (DLT)**.

---

## Mathematical Formulation

### Camera Projection

For homogeneous coordinates:

$$
\mathbf{x} = P\mathbf{X}
$$

where:

- $\mathbf{X} = (X, Y, Z, 1)^T$
- $\mathbf{x} = (x, y, 1)^T$
- $P$ is a $3 \times 4$ matrix.

---

### Cross-Product Constraint

Because vectors are equal only up to scale:

$$
\mathbf{x} \times (P\mathbf{X}) = 0.
$$

This produces linear equations in the unknown entries of $P$.

---

### Linear System

Each correspondence contributes two independent equations:

$$
A\mathbf{p} = 0
$$

where $\mathbf{p}$ contains the 12 elements of $P$.

At least **six point correspondences** are required.

---

### Solution via SVD

Compute:

$$
A = U\Sigma V^T
$$

The solution is the singular vector corresponding to the smallest
singular value.

The resulting matrix is defined up to scale.

---

### Data Normalization

Before estimation, coordinates should be normalized:

- center points at origin,
- scale average distance to $\sqrt{2}$ (2D) or $\sqrt{3}$ (3D).

Normalization greatly improves numerical stability.

---

## Intuition (My Understanding)

Each 3D–2D correspondence constrains how the camera must map
space into the image.

One correspondence restricts many possible cameras,
but multiple correspondences intersect to determine a single
consistent projection model.

DLT finds the camera that best aligns all viewing rays
with observed image points.

Linear estimation gives a rough camera;
nonlinear optimization later refines it.

---

## Important Observations

- The solution is projective (scale ambiguity remains).
- Poorly distributed points lead to unstable estimation.
- Normalization is essential for numerical conditioning.
- DLT provides initialization, not final accuracy.
- Optimization typically follows linear estimation.

---

## Questions / Confusions

- How sensitive is DLT to outlier correspondences?
- How does planar point configuration affect solvability?
- When does nonlinear refinement significantly change results?

---

## Connection to Robotics

Computing $P$ is equivalent to determining how a robot's camera
is positioned relative to the world.

This underlies:

- camera calibration pipelines,
- pose estimation,
- AR tracking,
- visual SLAM initialization.

DLT represents the first step from raw observations
to a usable geometric model of perception.
