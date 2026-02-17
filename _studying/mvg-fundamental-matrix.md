---
layout: default
title: Computation of the Fundamental Matrix F
parent: multiple-view-geometry
date: 2026-02-17
---

# Computation of the Fundamental Matrix F

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 11

---

## Why This Matters

The Fundamental Matrix encodes the geometric relationship
between two images. In practice, it must be estimated from
matched feature points.

Computing $F$ allows:

- correspondence validation,
- camera motion estimation,
- 3D reconstruction initialization,
- visual odometry and SLAM front-end operation.

This chapter provides the algorithms that transform feature matches
into geometric understanding.

---

## Key Idea

Corresponding image points satisfy the epipolar constraint:

$$
\mathbf{x}'^T F \mathbf{x} = 0.
$$

Each correspondence provides one linear constraint on the entries of $F$.

By collecting enough correspondences, we solve for $F$
using linear estimation followed by constraint enforcement.

The most important methods are:

- the **8-point algorithm**
- the **7-point algorithm**.

---

## Mathematical Formulation

### Linear Constraint

Let

$$
\mathbf{x} = (x, y, 1)^T, \quad
\mathbf{x}' = (x', y', 1)^T.
$$

Then:

$$
\mathbf{x}'^T F \mathbf{x} = 0
$$

expands into a linear equation in the elements of $F$:

$$
[x'x, \; x'y, \; x', \; y'x, \; y'y, \; y', \; x, \; y, \; 1]\mathbf{f} = 0,
$$

where $\mathbf{f}$ stacks the entries of $F$.

---

### Matrix Form

Stacking $n$ correspondences gives:

$$
A\mathbf{f} = 0.
$$

---

### 8-Point Algorithm

Steps:

1. Normalize image coordinates.
2. Construct matrix $A$.
3. Solve using SVD.
4. Reshape solution into matrix $F$.
5. Enforce rank-2 constraint.
6. Denormalize.

---

### Rank-2 Constraint

Because $\text{rank}(F)=2$:

1. Compute SVD:

$$
F = U\Sigma V^T
$$

2. Set smallest singular value to zero.
3. Reconstruct $F$.

---

### Normalization (Critical Step)

Points are transformed so that:

- centroid is at origin,
- average distance is $\sqrt{2}$.

This dramatically improves numerical stability.

---

### 7-Point Algorithm

Uses seven correspondences.

Produces up to three possible solutions by enforcing:

$$
\det(F) = 0.
$$

Used when minimal solutions are required (e.g., RANSAC).

---

## Intuition (My Understanding)

Each matching feature pair constrains how the two cameras
can be positioned relative to one another.

Many matches intersect to define a consistent epipolar geometry.

The linear solution finds the best approximate geometry,
while enforcing rank-2 ensures physical validity.

Normalization prevents numerical dominance by large coordinates.

---

## Important Observations

- At least 8 correspondences are needed for a linear solution.
- Raw coordinates lead to unstable estimation.
- Rank enforcement restores geometric validity.
- Outliers severely degrade estimation quality.
- Robust estimation (e.g., RANSAC) is usually required.

---

## Questions / Confusions

- Why does normalization improve conditioning so dramatically?
- How sensitive is $F$ estimation to feature localization noise?
- When should the 7-point algorithm be preferred over the 8-point algorithm?

---

## Connection to Robotics

Fundamental matrix estimation is a core step in
visual odometry pipelines:

1. detect features,
2. match features,
3. estimate $F$,
4. recover camera motion,
5. triangulate landmarks.

It allows robots to infer motion purely from image observations.
