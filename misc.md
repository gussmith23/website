---
layout: default
title: Misc
---

Here's a catch-all list of everything else on my site.

{% for miscpost in site.misc %}
  - [{{miscpost.title}}]({{miscpost.url}})
{% endfor %}
