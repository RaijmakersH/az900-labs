---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# Content Directory

Hyperlinks to each of the walkthroughs. Instructors may choose to use the walkthrough as a demonstration or a student lab. 

## Walkthroughs

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Module | Walkthrough |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}


