---
layout: default
title: Research
order: 1
---

Links relevant to my research:

{% for page in site.research %}
  - [{{page.title}}]({{page.url}})
{% endfor %}
