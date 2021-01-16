---
layout: default
title: Research
order: 1
---

Links relevant to my research:

  - [Research Journal](/research-journal)
{% for page in site.research %}
  - [{{page.title}}]({{page.url}})
{% endfor %}
