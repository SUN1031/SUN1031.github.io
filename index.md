---
layout: default
title: Home
---

# Welcome to Bezalel’s Craft

Bezalel’s Craft is a story about **engineering**.

Before it is about any particular technology, it is about a simple human act:  
seeing something that does not yet exist and deciding to build it anyway.

Engineering can be understood as a form of **craftsmanship**.  
It begins with questions, passes through drawings and calculations,  
and finally reaches the stubborn reality of materials and motion.  
Every design becomes a conversation between idea and world.

This website is the record of that conversation—  
projects shaped by curiosity, mistakes, and persistence.

### Why the Name?

**Bezalel** is a biblical figure known as a **craftsman and builder**.  
His name is used here to represent the figure of the maker—  
someone who transforms **imagination into structure** through patience and skill.

It stands for an attitude:  
listening to materials, respecting constraints,  
and still trying to create something a little better than before.

Bezalel’s Craft is the space where that attitude lives.


### What You’ll Find Here

- Explorations of how ideas become working systems  
- Projects built through study and trial  
- Reflections on design, failure, and improvement  
- Ongoing experiments that are still under construction

This site is a living workshop—always learning, never finished.

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
- <a href="https://github.com/SUN1031" target="_blank" rel="noopener noreferrer">GitHub</a>
- LinkedIn: coming soon
- CV: coming soon
