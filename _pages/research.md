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

  {%- comment -%} --- SINGLE-AUTHORED FIRST --- {%- endcomment -%}
  {% for post in in_status %}
    {%- comment -%} Build coauthor line robustly (array or string) {%- endcomment -%}
    {% assign withline = post.coauthors %}
    {% if (withline == nil or withline == '') and post.authors %}
      {% if post.authors.first %}
        {# authors is an array #}
        {% assign co_list = '' %}
        {% for a in post.authors %}
          {% unless a == me or a contains "Zhejun" or a contains "Qiu" %}
            {% if co_list == '' %}
              {% assign co_list = a %}
            {% else %}
              {% assign co_list = co_list | append: '; ' | append: a %}
            {% endif %}
          {% endunless %}
        {% endfor %}
        {% assign withline = co_list %}
      {% else %}
        {# authors is a string #}
        {% assign authors_norm = post.authors
          | replace: ' and ', ';'
          | replace: '&', ';'
          | replace: ',', ';'
          | replace: '，', ';'
          | replace: '  ', ' ' %}
        {% assign withline = authors_norm
          | replace: me, ''
          | replace: ';;', ';'
          | strip %}
        {% if withline %}{% assign withline = withline | replace_first: '; ', '' %}{% endif %}
      {% endif %}
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

  {%- comment -%} --- THEN COAUTHORED --- {%- endcomment -%}
  {% for post in in_status %}
    {%- comment -%} Build coauthor line robustly (array or string) {%- endcomment -%}
    {% assign withline = post.coauthors %}
    {% if (withline == nil or withline == '') and post.authors %}
      {% if post.authors.first %}
        {# authors is an array #}
        {% assign co_list = '' %}
        {% for a in post.authors %}
          {% unless a == me or a contains "Zhejun" or a contains "Qiu" %}
            {% if co_list == '' %}
              {% assign co_list = a %}
            {% else %}
              {% assign co_list = co_list | append: '; ' | append: a %}
            {% endif %}
          {% endunless %}
        {% endfor %}
        {% assign withline = co_list %}
      {% else %}
        {# authors is a string #}
        {% assign authors_norm = post.authors
          | replace: ' and ', ';'
          | replace: '&', ';'
          | replace: ',', ';'
          | replace: '，', ';'
          | replace: '  ', ' ' %}
        {% assign withline = authors_norm
          | replace: me, ''
          | replace: ';;', ';'
          | strip %}
        {% if withline %}{% assign withline = withline | replace_first: '; ', '' %}{% endif %}
      {% endif %}
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
