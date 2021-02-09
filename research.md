---
layout: default
title: Research
order: 1
---

Links relevant to my research:

  - [Research Journal]({% link _research_journal/index.md %})
{% for page in site.research %}
  - [{{page.title}}]({{page.url}})
{% endfor %}
