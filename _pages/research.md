---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{% assign items = site.publications | sort: "date" | reverse %}

{% for post in items %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>

  {% assign withline = post.coauthors %}
  {% if withline == nil or withline == '' and post.authors %}
    {% assign me = 'Zhejun Qiu' %}
    {% assign withline = post.authors
        | replace: me, ''
        | replace: ';;', ';'
        | replace: '  ', ' '
        | strip
        | replace_first: '; ', ''
        | replace: '; ', '; ' %}
  {% endif %}
  {% if withline and withline != '' %}
    <p style="margin:.25rem 0 0;">with {{ withline | replace: ';', '; ' }}</p>
  {% endif %}

  {% if post.status %}
    <p style="margin:.25rem 0 0;">{{ post.status }}</p>
  {% endif %}

  {% if post.abstract %}
    <p class="archive__item-excerpt" style="margin:.35rem 0 0;">{{ post.abstract }}</p>
  {% endif %}
</article>
{% endfor %}
