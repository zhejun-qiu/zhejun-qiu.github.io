---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{% assign statuses = "R&R at International Studies Quarterly|Submitted|Working Paper|Working in Progress" | split: "|" %}
{% assign me = "Zhejun Qiu" %}

{% for s in statuses %}
  {% assign in_status = site.publications | where: "status", s %}

  {% for post in in_status %}
    {% assign withline = post.coauthors %}
    {% if (withline == nil or withline == '') and post.authors %}
      {% assign authors_norm = post.authors
        | replace: ' and ', ';'
        | replace: ',', ';'
        | replace: '，', ';'
        | replace: '  ', ' ' %}
      {% assign withline = authors_norm
        | replace: me, ''
        | replace: ';;', ';'
        | strip
        | replace_first: '; ', ''
        | replace: '; ;', ';' %}
    {% endif %}
    {% assign is_single = (withline == nil or withline == '') %}

    {% if is_single %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  {% if post.status %}<p style="margin:.25rem 0 0;">{{ post.status }}</p>{% endif %}
  {% if post.abstract %}<p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>{% endif %}
</article>
    {% endif %}
  {% endfor %}

  {% for post in in_status %}
    {% assign withline = post.coauthors %}
    {% if (withline == nil or withline == '') and post.authors %}
      {% assign authors_norm = post.authors
        | replace: ' and ', ';'
        | replace: ',', ';'
        | replace: '，', ';'
        | replace: '  ', ' ' %}
      {% assign withline = authors_norm
        | replace: me, ''
        | replace: ';;', ';'
        | strip
        | replace_first: '; ', ''
        | replace: '; ;', ';' %}
    {% endif %}
    {% assign is_single = (withline == nil or withline == '') %}

    {% unless is_single %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ withline | replace: ';', '; ' }}</em></p>
  {% if post.status %}<p style="margin:.25rem 0 0;">{{ post.status }}</p>{% endif %}
  {% if post.abstract %}<p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>{% endif %}
</article>
    {% endunless %}
  {% endfor %}
{% endfor %}
