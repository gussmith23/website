---
layout: default
title: Writing
order: 2
---

{% for writing_post in site.writing %}
  - [{{writing_post.title}}]({{writing_post.url}})
{% endfor %}
