---
layout: default
title: Projects
---

## Projects

Below are selected academic and personal robotics projects.

---

{% for project in site.projects %}
### [{{ project.title }}]({{ project.url }})
**Tags:** {{ project.tags | join: ", " }}

{% endfor %}
