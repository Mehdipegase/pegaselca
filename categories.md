---
layout: page
title: "Catégories"
permalink: /categories/
---

<ul>
  {% assign cats = site.posts | map: 'categories' | join: ',' | split: ',' | uniq | sort %}
  {% for c in cats %}
    {% if c != '' %}
      <li>
        <h3 id="{{ c | slugify }}"># {{ c }}</h3>
        <ul>
          {% for post in site.posts %}
            {% if post.categories contains c %}
              <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <small>({{ post.date | date: "%d %b %Y" }})</small></li>
            {% endif %}
          {% endfor %}
        </ul>
      </li>
    {% endif %}
  {% endfor %}
</ul>
