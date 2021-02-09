---
layout: page
title: Research Journal
---
In 2021, I committed to trying to write a short research journal entry every week. Here are the results.
<table class="post-list">
  {% assign posts = site.research_journal | sort: 'date' | reverse | where_exp:"item", "item.draft != true" %}
  {% for post in posts %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td>{{ post.date | date: "%D" }}</td> <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      {% endif %}
    </tr>
  {% endfor %}

  <!-- add empty row for spacing -->
  <!-- TODO i'm sure there's a cleaner way to do this -->
  <tr><td></td></tr>

  <!-- drafts -->
  {% assign sorted = site.research_journal | sort: 'date' | reverse | where_exp:"item", "item.draft == true" %}
  {% for post in sorted %}
    <tr>
      {% assign filename = post.path | split: "/" | last %}
      {% if filename != "index.md" %}
        <td><em>draft</em></td> <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      {% endif %}
    </tr>
  {% endfor %}
</table>
