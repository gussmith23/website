---
layout: page
title: Research Journal
permalink: /research-journal
---
In 2021, I committed to trying to write a short research journal entry every week. Here are the results.
<ul style="list-style: none">
  {% for post in site.research_journal %}
    <li>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        {{ post.date | date: "%B %d %Y" }} <a href="{{ post.url }}">{{ post.title }}</a>
      {% endif %}
    </li>
  {% endfor %}
</ul>
