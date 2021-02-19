---
layout: default
title: Research
---

Links relevant to my research:

- [Research Journal]({% link _research_journal/index.md %})
{% for page in site.research %}
{% assign filename = page.path | split: "/" | last %}
{% if filename != "index.md" %}

- [{{page.title}}]({{page.url}})

{% endif %}
{% endfor %}
