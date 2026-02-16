---
layout: default
title: Computer Vision
permalink: /studying/computer-vision/
---

# Computer Vision Notes

{% raw %}
{% for note in site.studying %}
  {% if note.topic == "computer-vision" %}
    - [{{ note.title }}]({{ note.url }})
  {% endif %}
{% endfor %}
{% endraw %}
