---
layout: default
title: Computer Vision
permalink: /studying/computer-vision/
---

# Computer Vision Notes

<ul>
{% for note in site.studying %}
  {% if note.topic == "computer-vision" %}
    <li>
      <a href="{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endif %}
{% endfor %}
</ul>
