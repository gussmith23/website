---
layout: default
title: Writing
order: 2
---

{% assign sorted = site.writing | sort: 'date' | reverse %}
{% for writing_post in sorted %}
  - [{{writing_post.title}}]({{writing_post.url}})
{% endfor %}
