---
layout: default
title: Writing
order: 2
---


<table class='post-list'>
  {% assign sorted = site.writing | sort: 'date' | reverse %}
  {% for post in sorted %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td>{{ post.date | date: "%D" }}</td> <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      {% endif %}
    </tr>
  {% endfor %}
</table>
