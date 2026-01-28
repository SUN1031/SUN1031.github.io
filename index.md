---
layout: default
title: Home
---

# Choi Byeongseon

**Robotics Engineer**  
*M.Sc. in Robotics — August 2024*

---

Welcome to my website.

I received my Master’s degree in Robotics in August 2024.  
This website documents my academic work, master’s thesis, and future personal projects.

---

## Interests
- Mobile robotics
- Robotic manipulation
- Perception
- Planning and Control
- Machine learning

---

## Featured Projects

<div class="project-grid">

{% for project in site.projects %}
  {% if project.featured %}
  <a class="project-card" href="{{ project.url }}">
    <img src="{{ project.thumbnail }}" alt="thumbnail" />
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
    <span>{{ project.tags | join: " · " }}</span>
  </a>
  {% endif %}
{% endfor %}

</div>

---

## Links
- GitHub: https://github.com/SUN1031
- LinkedIn: (add later)
- CV: (add later)
