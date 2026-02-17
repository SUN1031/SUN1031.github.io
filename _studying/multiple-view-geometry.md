---
layout: default
title: Multiple View Geometry
topic: computer-vision
tags: [geometry, epipolar, vision]
date: 2026-02-16
---

## Source
Hartley & Zisserman — Multiple View Geometry in Computer Vision

---

## Why This Matters

Understanding how 3D points project into images is the
foundation of visual SLAM and 3D reconstruction.

---

## Contents

<ul>
{% for note in site.studying %}
  {% if note.parent == "multiple-view-geometry" %}
    <li>
      <a href="{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endif %}
{% endfor %}
</ul>

