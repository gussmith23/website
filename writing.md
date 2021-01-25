---
layout: default
title: Writing
order: 2
---


<style>
table.custom {
  border: 0px solid black;
}
table.custom * :nth-child(even) {
  background-color: transparent;
}
table.custom * {
  padding: 0;
  background-color: transparent;
  border: 0px solid black;
}
</style>

<table class='custom'>
  {% assign sorted = site.writing | sort: 'date' | reverse %}
  {% for post in sorted %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td style='text-align:right; padding-right:1em'>{{ post.date | date: "%B %d %Y" }}</td> <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      {% endif %}
    </tr>
  {% endfor %}
</table>
