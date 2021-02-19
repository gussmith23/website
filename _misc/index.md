---
layout: default
title: Misc
order: 3
---

Here's a catch-all list of everything else on my site.

{% for miscpost in site.misc %}
{% assign filename = miscpost.path | split: "/" | last %}
{% if filename != "index.md" %}

- [{{miscpost.title}}]({{miscpost.url}})

{% endif %}
{% endfor %}
