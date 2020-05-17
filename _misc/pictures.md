---
layout: post
title: My Pictures
permalink: /pictures
date:   2020-05-16 15:51:00 -0400
last_modified_at:   2020-05-16 15:51:00 -0400
pictures:
  - path: /assets/personal-pictures/2020-03-15-westport-surfing.jpg
    alt: Collin and Gus at Westport
    caption: Collin and I on my first surf trip to Westport trip of 2020 (and last, before the coronavirus shutdown!)
    date: March 15th, 2020
  - path: /assets/personal-pictures/2020-02-24-post-quals.jpg
    caption: <a href="{{site.data.references.zach}}" target='_blank'>Zach</a>, myself, and <a href="{{site.data.references.luis}}" target='_blank'>Luis</a> after my qualifying presentation!
    date: February 24th, 2020
---
{% for picture in page.pictures %}
  <figure>
    <img src="{{picture.path}}" alt="{{picture.alt}}" style="width:100%">
    <figcaption>
      {% if picture.date %}<b>{{picture.date}}</b>{% endif %}
      {{picture.caption}}
    </figcaption> 
  </figure>
  <br />
{% endfor %}
