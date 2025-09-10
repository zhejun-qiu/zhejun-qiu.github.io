---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

<!-- hide the built-in page title -->
<style>.page__title{display:none}</style>

{%- assign rr = site.publications | where: "status", "R&R at International Studies Quarterly" -%}
{%- assign submitted = site.publications | where: "status", "Submitted" -%}
{%- assign under_review = rr | concat: submitted | sort: "date" | reverse -%}
{%- assign working = site.publications | where: "status", "Working Paper" | sort: "date" | reverse -%}

<h1 style="margin:1rem 0 .5rem; font-size:1.8rem;">Under Review</h1>

{%- comment -%} Under Review — single-authored first {%- endcomment -%}
{%- for post in under_review -%}
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
    <p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>
  {%- endif -%}
</article>
  {%- endif -%}
{%- endfor -%}

{%- comment -%} Under Review — then coauthored {%- endcomment -%}
{%- for post in under_review -%}
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
    <p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>
  {%- endif -%}
</article>
  {%- endunless -%}
{%- endfor -%}

<h1 style="margin:1.25rem 0 .5rem; font-size:1.8rem;">Working Papers</h1>

{%- comment -%} Working Papers — single-authored first (no per-item status line) {%- endcomment -%}
{%- for post in working -%}
  {%- assign co = post.coauthors | to_s | strip -%}
  {%- if co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  {%- if post.abstract -%}
    <p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>
  {%- endif -%}
</article>
  {%- endif -%}
{%- endfor -%}

{%- comment -%} Working Papers — then coauthored (no per-item status line) {%- endcomment -%}
{%- for post in working -%}
  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>
  {%- if post.abstract -%}
    <p class="archive__item-excerpt" style="margin:.35rem 0 0; font-size:.9em;"><strong>Abstract:</strong> {{ post.abstract }}</p>
  {%- endif -%}
</article>
  {%- endunless -%}
{%- endfor -%}
