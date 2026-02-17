---
layout: default
title: Epipolar Geometry and the Fundamental Matrix
parent: multiple-view-geometry
date: 2026-02-17
---

# Epipolar Geometry and the Fundamental Matrix

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 9

---

## Why This Matters

When two cameras observe the same scene, their images are not
independent. Epipolar geometry describes the geometric constraint
linking corresponding image points across views.

This constraint:

- reduces correspondence search from 2D to 1D,
- enables stereo reconstruction,
- forms the basis of visual odometry and SLAM.

It is the fundamental relationship between two uncalibrated cameras.

---

## Key Idea

A 3D point observed by two cameras defines a plane containing:

- the two camera centers,
- the 3D point.

This plane is called the **epipolar plane**.

Its intersection with each image plane produces an
**epipolar line**.

Therefore, a point in one image must lie on a specific line
in the other image.

This relationship is encoded by the **Fundamental Matrix** $F$.

---

## Mathematical Formulation

### Epipolar Constraint

For corresponding points:

$$
\mathbf{x}'^T F \mathbf{x} = 0
$$

where:

- $\mathbf{x}$ — point in image 1
- $\mathbf{x}'$ — corresponding point in image 2
- $F$ — Fundamental matrix ($3 \times 3$).

---

### Epipolar Lines

Given a point $\mathbf{x}$:

$$
\mathbf{l}' = F\mathbf{x}
$$

is the epipolar line in the second image.

Similarly:

$$
\mathbf{l} = F^T \mathbf{x}'
$$

is the epipolar line in the first image.

---

### Properties of the Fundamental Matrix

- rank$(F)=2$
- defined up to scale
- has 7 degrees of freedom
- depends only on relative camera geometry.

---

### Epipoles

Epipoles are projections of one camera center into the other image:

$$
F\mathbf{e} = 0, \quad F^T\mathbf{e}' = 0.
$$

They lie at the intersection of all epipolar lines.

---

### Relation to Camera Matrices

If cameras are:

$$
P, \quad P'
$$

then:

$$
F = [\mathbf{e}']_\times P'P^+,
$$

where $P^+$ is the pseudo-inverse of $P$.

---

## Intuition (My Understanding)

A point in the first image corresponds not to a single point
but to a ray in 3D space.

When viewed from the second camera, that ray projects as a line,
not a point.

Thus correspondence search is constrained to one dimension.

Epipolar geometry encodes purely geometric relationships,
independent of scene structure.

It depends only on relative camera motion.

---

## Important Observations

- Epipolar geometry exists even without calibration.
- Correspondence search becomes dramatically simpler.
- Fundamental matrix estimation requires multiple matches.
- Degenerate configurations (e.g., planar scenes) cause ambiguity.
- The constraint arises purely from projective geometry.

---

## Questions / Confusions

- How does noise affect rank-2 enforcement?
- Why does planar structure lead to degeneracy?
- How does the Essential matrix refine this relationship?

---

## Connection to Robotics

Epipolar geometry underlies:

- stereo depth estimation,
- visual odometry,
- feature matching constraints,
- SLAM initialization.

Robots use the epipolar constraint to reject incorrect matches
and estimate relative motion between frames.
