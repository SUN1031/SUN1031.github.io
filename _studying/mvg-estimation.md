---
layout: default
title: Estimation
parent: multiple-view-geometry
date: 2026-02-17
---

# Estimation

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 4

---

## Why This Matters

Real image measurements are noisy and imperfect.
Feature correspondences never satisfy geometric constraints exactly.

Estimation provides methods to recover geometric models
(camera matrices, homographies, fundamental matrices)
from noisy observations.

Without estimation theory, multiple view geometry would remain
purely theoretical and unusable in real vision systems.

This chapter explains how vision algorithms turn data into geometry.

---

## Key Idea

Geometric relationships define constraints, but real data violates
them due to noise.

Therefore, we estimate model parameters by minimizing an error measure.

Core principles:

- formulate constraints as algebraic equations,
- solve linear systems for initial estimates,
- refine solutions using optimization.

The goal is to find parameters that best explain observations.

---

## Mathematical Formulation

### Linear Estimation Problem

Given observations:

$$
A\mathbf{x} = 0
$$

we seek a non-trivial solution $\mathbf{x}$.

Because noise exists, an exact solution usually does not exist.
Instead we minimize:

$$
\|A\mathbf{x}\|
$$

subject to:

$$
\|\mathbf{x}\| = 1
$$

---

### Solution via Singular Value Decomposition (SVD)

Let:

$$
A = U \Sigma V^T
$$

The optimal solution is the right singular vector corresponding
to the smallest singular value.

---

### Error Models

#### Algebraic Error

Simple but not geometrically meaningful:

$$
A\mathbf{x}
$$

---

#### Geometric Error

Distance between observed and predicted image points:

$$
d(\mathbf{x}, \hat{\mathbf{x}})
$$

More meaningful but nonlinear.

---

### Maximum Likelihood Estimation

Assuming Gaussian noise, parameter estimation becomes:

$$
\min \sum_i \|x_i - \hat{x}_i\|^2
$$

leading to nonlinear optimization problems.

---

### Nonlinear Refinement

Initial linear estimates are improved using iterative optimization:

- Gauss–Newton
- Levenberg–Marquardt

This process is often called **bundle adjustment** in later chapters.

---

## Intuition (My Understanding)

Linear solutions provide a rough geometric guess.
They are computationally convenient but physically inaccurate.

Optimization then adjusts parameters so predicted image projections
align with measured feature locations.

In essence:

1. Linear algebra gives a starting point.
2. Optimization makes it geometrically correct.

This explains why many vision pipelines follow a
"linear initialization → nonlinear refinement" pattern.

---

## Important Observations

- Noise makes exact geometric constraints impossible.
- SVD appears repeatedly across vision algorithms.
- Algebraic error is easy but misleading geometrically.
- Proper normalization improves numerical stability.
- Optimization quality depends strongly on initialization.

---

## Questions / Confusions

- How sensitive are solutions to feature localization error?
- When does linear estimation fail catastrophically?
- How does robust estimation (RANSAC) modify this framework?

---

## Connection to Robotics

Estimation underlies nearly every robotics perception system:

- pose estimation
- visual odometry
- SLAM optimization
- sensor calibration

Robotics pipelines repeatedly alternate between prediction
and parameter estimation under noise.
