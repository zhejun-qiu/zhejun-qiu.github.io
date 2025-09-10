---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{% comment %}
Expected front matter in each _publications/*.md:
title: "..."
authors: "Zhejun Qiu; Coauthor A; Coauthor B"   # optional if you set coauthors
coauthors: "Coauthor A and Coauthor B"          # optional; overrides 'authors' parsing
status: "R&R at International Studies Quarterly" # or "Submitted" | "Working Paper" | "Working in Progress"
abstract: "One-paragraph abstract..."
date: 2025-01-01
collection: publications
permalink: /research/your-slug/
{% endcomment %}

{% assign statuses = "R&R at International Studies Quarterly|Submitted|Working Paper|Working in Progress" | split: "|" %}
{% assign me = "Zhejun Qiu" %}

{% for s in statuses %}
  {% assign in_status = site.publications | where: "status", s %}

  {# --- SINGLE-AUTHORED FIRST --- #}
  {% for post in in_status %}
    {% assign withline = post.coauthors %}
    {% if (withline == nil or withline == '') and post.authors %}
      {% assign withline = post.authors
        | replace: me, ''
        | replace: ';;', ';'
        | replace: '  ', ' '
        | strip
        | replace_first: '; ', ''
        | replace: '; ', '; ' %}
    {% endif %}
    {% assign is_single = (withline == nil or withline == '') %}

    {% if is_single %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  {% if withline and withline != '' %}
    <p style="margin:.25rem 0 0;">with {{ withline | replace: ';', '; ' }}</p>
  {% endif %}
  {% if post.status %}
    <p style="margin:.25rem 0 0;">{{ post.status }}</p>
  {% endif %}
  {% if post.abstract %}
    <p class="archive__item-excerpt" style="margin:.35rem 0 0;"><strong>Abstract:</strong> {{ post.abstract }}</p>
  {% endif %}
</article>
    {% endif %}
  {% endfor %}

  {# --- THEN COAUTHORED --- #}
  {% for post in in_status %}
    {% assign withline = post.coauthors %}
    {% if (withline == nil or withline == '') and post.authors %}
      {% assign withline = post.authors
        | replace: me, ''
        | replace: ';;', ';'
        | replace: '  ', ' '
        | strip
        | replace_first: '; ', ''
        | replace: '; ', '; ' %}
    {% endif %}
    {% assign is_single = (withline == nil or withline == '') %}

    {% unless is_single %}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.25rem 0 0;">with {{ withline | replace: ';', '; ' }}</p>
  {% if post.status %}
    <p style="margin:.25rem 0 0;">{{ post.status }}</p>
  {% endif %}
  {% if post.abstract %}
    <p class="archive__item-excerpt" style="margin:.35rem 0 0;"><strong>Abstract:</strong> {{ post.abstract }}</p>
  {% endif %}
</article>
    {% endunless %}
  {% endfor %}
{% endfor %}
