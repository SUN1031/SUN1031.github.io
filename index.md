---
layout: default
title: Home
---

## Welcome

This website is a space where my projects, studies, and ideas come together. It reflects my journey as a robotics engineer-learning though experimentation, solving problems with curiosity, and turning concepts into real systems.

### Why "Bezalel's Craft"?

The name of this site is inspired by the Biblical craftsman Bezalel. He was a builder who transformed ideas into tangible work, and that spirit resonates with how I approach engineering.

I see technology as a form of craftsmanship: understanding materials, tools, and principles, then shaping them into something meaningful. Each project is an opportunity to learn, refine, and create with intention.

### What You'll Find Here

- Explorations in robotics, control, and intelligent systems
- Projects developed during my studies and personal research
- Reflections on problem-solving and design
- Ongoing experiments and ideas

This site is a living workshop-an evolving record of what I build and what I continue to learn.

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
