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

## Featured Projects

{% for project in site.projects %}
  {% if project.featured %}
### [{{ project.title }}]({{ project.url }})
**{{ project.tags | join: ", " }}**

{{ project.excerpt }}

---
  {% endif %}
{% endfor %}

---

## Interests
- Mobile robotics
- Robot control
- Motion planning
- Perception
- ROS

---

## Links
- GitHub: https://github.com/SUN1031
- LinkedIn: (add later)
- CV: (add later)
