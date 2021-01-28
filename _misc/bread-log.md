---
layout: default
title: Bread Log
entries:
  - title: White Bread
    date: 1/19/2021
    schedule: 
      - ["8:28am" , autolyse]
      - ["8:52" , mix + fold]
      - ["10:06" , fold]
      - ["10:44" , fold]
      - ["4:30pm" , separate + shape]
      - ["5:39" , in oven]
      - ["6:01" , lid off]
      - ["6:20" , out of oven]
    pictures:
      - path: /assets/bread-log/2021-01-19/loaf1.jpg
        alt: Loaf of bread
      - path: /assets/bread-log/2021-01-19/loaf1-under.jpg
        alt: Loaf of bread
      - path: /assets/bread-log/2021-01-19/loaf2.jpg
        alt: Loaf of bread
      - path: /assets/bread-log/2021-01-19/loaf2-under.jpg
        alt: Loaf of bread
---

<style>
    table, table td, table tr, table tbody, table tr:nth-child(even) {
        border: none;
        padding: 0;
    }
    table tr:nth-child(even) {
        background-color: transparent;
    }
    table td:nth-child(1) {
        padding-right: 1em;
    }
    table td:nth-child(2) {
        width: 100%;
    }

</style>

{% for bread-entry in page.entries %}
{% assign date = bread-entry.date | date: "%d" %}

## {{date}}: {{bread-entry.title}}

<table>
{% for schedule-entry in bread-entry.schedule %}
  <tr><td>{{schedule-entry[0]}}</td><td>{{schedule-entry[1]}}</td></tr>
{% endfor %}
</table>

{% for picture in bread-entry.pictures %}
<figure>
  <img src="{{picture.path}}" alt="{{picture.alt}}" style="width:100%">
  <figcaption>
    {{picture.caption}}
  </figcaption> 
</figure>
{% endfor %}

{% endfor %}