---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{%- assign statuses = "R&R at International Studies Quarterly|Submitted|Working Paper" | split: "|" -%}

{%- for s in statuses -%}
  {%- assign in_status = site.publications | where: "status", s -%}

  {# --- SINGLE-AUTHORED FIRST (no coauthors field) --- #}
  {%- for post in in_status -%}
    {%- assign co = post.coauthors | to_s | strip -%}
    {%- if co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>

  {%- if post.status -%}
    {%- assign status_txt = post.status -%}
    {%- if status_txt contains "International Studies Quarterly" -%}
      {%- assign status_txt = status_txt | replace: "International Studies Quarterly", "<em>International Studies Quarterly</em>" -%}
    {%- endif -%}
    <p style="margin:.25rem 0 0;">{{ status_txt }}</p>
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract" style="margin:.35rem 0 0;">
      <summary style="cursor:pointer;">Abstract</summary>
      <div class="archive__item-excerpt" style="margin:.4rem 0 0; font-size:.9em;">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}
</article>
    {%- endif -%}
  {%- endfor -%}

  {# --- THEN COAUTHORED (has coauthors field) --- #}
  {%- for post in in_status -%}
    {%- assign co = post.coauthors | to_s | strip -%}
    {%- unless co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>

  {%- if post.status -%}
    {%- assign status_txt = post.status -%}
    {%- if status_txt contains "International Studies Quarterly" -%}
      {%- assign status_txt = status_txt | replace: "International Studies Quarterly", "<em>International Studies Quarterly</em>" -%}
    {%- endif -%}
    <p style="margin:.25rem 0 0;">{{ status_txt }}</p>
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract" style="margin:.35rem 0 0;">
      <summary style="cursor:pointer;">Abstract</summary>
      <div class="archive__item-excerpt" style="margin:.4rem 0 0; font-size:.9em;">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}
</article>
    {%- endunless -%}
  {%- endfor -%}

{%- endfor -%}
