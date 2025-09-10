---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{%- assign items = site.publications | sort: "date" | reverse -%}

{%- for post in items -%}
<article class="archive__item">
  <h2 class="archive__item-title no_toc" style="margin-bottom:.2rem;">
    {%- if post.external_url -%}
      <a href="{{ post.external_url }}">{{ post.title }}</a>
    {%- else -%}
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {%- endif -%}
  </h2>

  {#-- COAUTHORS LINE --#}
  {%- if post.coauthors -%}
    <p class="archive__item-excerpt" style="margin:.1rem 0 .4rem;">with {{ post.coauthors }}</p>
  {%- elsif post.authors -%}
    {%- assign me = 'Zhejun Qiu' -%}
    {%- assign co = post.authors | replace: me, '' | replace: ';;', ';' | replace: '  ', ' ' | strip -%}
    {%- assign co = co | replace_first: '; ', '' | replace: '; ', '; ' -%}
    {%- if co != '' -%}
      <p class="archive__item-excerpt" style="margin:.1rem 0 .4rem;">with {{ co | replace: ';', '; ' }}</p>
    {%- endif -%}
  {%- endif -%}

  {#-- OPTIONAL STATUS LINE (e.g., Working paper, R&R at ISQ) --#}
  {%- if post.status -%}
    <p class="archive__item-excerpt" style="margin:.1rem 0 .6rem;">{{ post.status }}</p>
  {%- endif -%}

  {#-- OPTIONAL ABSTRACT --#}
  {%- if post.abstract -%}
    <p class="archive__item-excerpt">{{ post.abstract }}</p>
  {%- endif -%}

  {#-- OPTIONAL LINKS ARRAY: links: [{label: "PDF", url: "/files/paper.pdf"}, {label:"Slides", url:"..."}] --#}
  {%- if post.links -%}
    <p class="archive__item-excerpt" style="margin-top:.4rem;">
      {%- for link in post.links -%}
        <a href="{{ link.url }}">{{ link.label }}</a>{% unless forloop.last %} &middot; {% endunless %}
      {%- endfor -%}
    </p>
  {%- endif -%}
</article>
<hr />
{%- endfor -%}
