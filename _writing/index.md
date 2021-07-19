---
layout: default
title: Writing
order: 2
---


<!-- markdownlint-disable MD033 -->
<table class='post-list'>
  {% assign sorted = site.writing | sort: 'date' | reverse | where_exp:"item", "item.draft != true" %}
  {% for post in sorted %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td>{{ post.date | date: "%D" }}</td>
        <td>
          <a href="{{ post.url }}">
          {% if post.featured %}
          <b>{{ post.title }}</b>
          {% else %}
          {{ post.title }}
          {% endif %}
          </a>
        </td>
      {% endif %}
    </tr>
  {% endfor %}

  <!-- add empty row for spacing -->
  <!-- TODO i'm sure there's a cleaner way to do this -->
  <tr><td></td></tr>

  <!-- drafts -->
  {% assign sorted = site.writing | sort: 'date' | reverse | where_exp:"item", "item.draft == true" %}
  {% for post in sorted %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td><em>draft</em></td> <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      {% endif %}
    </tr>
  {% endfor %}
</table>
<!-- markdownlint-enable MD033 -->
