---
layout: page
title: Research Journal
permalink: /research-journal
---
In 2021, I committed to trying to write a short research journal entry every week. Here are the results.
<table class="post-list">
  {% for post in site.research_journal %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td>{{ post.date | date: "%D" }}</td> <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      {% endif %}
    </tr>
  {% endfor %}
</table>
