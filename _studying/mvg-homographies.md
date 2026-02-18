---
layout: default
title: Scene Planes and Homographies
parent: multiple-view-geometry
date: 2026-02-17
---

# Scene Planes and Homographies

Hartley & Zisserman — *Multiple View Geometry in Computer Vision*  
Chapter 13

---

## Why This Matters

General 3D reconstruction requires estimating epipolar geometry
and triangulating points. However, when scene points lie on a plane,
the relationship between two images becomes much simpler.

In this case, corresponding image points are related by a
**homography**, a single projective transformation.

Homographies are fundamental in:

- panorama stitching,
- augmented reality tracking,
- planar SLAM,
- image registration.

They provide a simpler alternative to full 3D reconstruction.

---

## Key Idea

If all observed points lie on a plane, then the mapping between
two images can be described by a single matrix:

$$
\mathbf{x}' = H\mathbf{x}.
$$

This means correspondence search no longer requires epipolar geometry;
the entire transformation is captured by one projective mapping.

A homography represents how one image of a plane transforms
into another under camera motion.

---

## Mathematical Formulation

### Homography Mapping

A homography is defined as:

$$
\mathbf{x}' \sim H\mathbf{x},
$$

where

$$
H \in \mathbb{R}^{3 \times 3}
$$

is defined up to scale.

---

### Plane-Induced Homography

Given cameras:

$$
P = K[I|0], \quad P' = K'[R|t],
$$

and a scene plane with normal $\mathbf{n}$ and distance $d$,
the homography becomes:

$$
H = K'(R - \frac{t\mathbf{n}^T}{d})K^{-1}.
$$

This shows homography depends on:

- camera motion,
- plane geometry,
- camera calibration.

---

### Degrees of Freedom

A homography has 8 degrees of freedom (up to scale).

At least **four point correspondences** are required to estimate $H$.

---

### Relation to Epipolar Geometry

- General scenes → Fundamental matrix $F$
- Planar scenes → Homography $H$

Homography is a special-case simplification of two-view geometry.

---

## Intuition (My Understanding)

A plane removes depth variation.
All points lie on a single geometric surface, so perspective effects
become predictable.

Instead of rays intersecting arbitrary 3D locations,
the entire image undergoes a coherent projective warp.

Thus image motion can be explained without reconstructing depth.

Homography captures how viewing direction changes relative to the plane.

---

## Important Observations

- Homographies describe planar scenes exactly.
- Pure camera rotation also produces a homography.
- Homography estimation requires fewer correspondences than $F$.
- Planar scenes cause degeneracy for fundamental matrix estimation.
- Many vision systems detect planar motion before attempting 3D reconstruction.

---

## Questions / Confusions

- How can one distinguish planar motion from general motion robustly?
- When does homography approximation fail in near-planar scenes?
- How is plane estimation integrated into SLAM systems?

---

## Connection to Robotics

Homographies are widely used in robotics perception:

- visual tracking on planar surfaces,
- AR marker detection,
- drone landing using planar targets,
- initialization of visual SLAM in low-parallax motion.

They provide a computationally efficient model when full 3D
reconstruction is unnecessary.
