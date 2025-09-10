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
  <h2 class="archive__item-title no_toc" style="margin:0;">
    {% if post.external_url %}
      <a href="{{ post.external_url }}">{{ post.title }}</a>
    {% elsif post.pdf %}
      <a href="{{ post.pdf }}">{{ post.title }}</a>
    {% else %}
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {% endif %}
  </h2>

  {% assign withline = post.coauthors %}
  {% if withline == nil or withline == '' %}
    {% if post.authors %}
      {% assign me = 'Zhejun Qiu' %}
      {% assign withline = post.authors | replace: me, '' | replace: ';;', ';' | replace: '  ', ' ' | strip | replace_first: '; ', '' | replace: '; ', '; ' %}
    {% endif %}
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
