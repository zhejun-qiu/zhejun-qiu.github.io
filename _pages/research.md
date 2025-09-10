---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{% assign statuses = "R&R at International Studies Quarterly|Submitted|Working Paper|Working in Progress" | split: "|" %}

{% for s in statuses %}
  {% assign in_status = site.publications | where: "status", s %}

  {%- comment -%} Single-authored (no coauthors field) first {%- endcomment -%}
  {% for post in in_status %}
    {% assign co = post.coauthors | to_s | strip %}
    {% if co == '' %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  {% if post.status %}<p style="margin:.25rem 0 0;">{{ post.status }}</p>{% endif %}
  {% if post.abstract %}<p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>{% endif %}
</article>
    {% endif %}
  {% endfor %}

  {%- comment -%} Then coauthored (has coauthors field) {%- endcomment -%}
  {% for post in in_status %}
    {% assign co = post.coauthors | to_s | strip %}
    {% unless co == '' %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>
  {% if post.status %}<p style="margin:.25rem 0 0;">{{ post.status }}</p>{% endif %}
  {% if post.abstract %}<p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>{% endif %}
</article>
    {% endunless %}
  {% endfor %}
{% endfor %}
