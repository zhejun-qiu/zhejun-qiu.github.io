---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

<!-- hide the built-in page title and style the divider + abstract toggle -->
<style>
  .page__title{display:none}
  .section-split{
    border:0; height:1px; margin:2.25rem 0 2rem;
    background:linear-gradient(90deg,transparent 0,#e3e3e3 18%,#cfcfcf 50%,#e3e3e3 82%,transparent 100%);
  }
  details.abstract { margin:.4rem 0 0; }
  details.abstract > summary{
    cursor:pointer; user-select:none; font-weight:600; outline:none;
  }
  /* optional: subtle caret style (supported in modern browsers) */
  details.abstract > summary::marker { content:"▸ "; }
  details.abstract[open] > summary::marker { content:"▾ "; }
  .archive__item-excerpt { margin:.4rem 0 0; font-size:.9em; }
</style>

{%- assign cond_accepted = site.publications | where: "status", "Conditionally accepted at International Studies Quarterly" | sort: "date" | reverse -%}
{%- assign rr_pp = site.publications | where: "status", "R & R at Political Psychology" | sort: "date" | reverse -%}
{%- assign submitted = site.publications | where: "status", "Submitted" | sort: "date" | reverse -%}
{%- assign working = site.publications | where: "status", "Working Paper" | sort: "date" | reverse -%}

<h1 style="margin:1rem 0 .5rem; font-size:1.8rem;">Under Review</h1>

{%- comment -%} 1. Conditionally accepted {%- endcomment -%}
{%- for post in cond_accepted -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>

  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>
  {%- endunless -%}

  {%- if post.title == "Refugee Policies, Foreign Aid, and Political Violence in the Global South" -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.9em; color:#777;">
      2026 Dina Zinnes Best Graduate Student Paper Award, SSIP, ISA
    </p>
  {%- endif -%}

  {%- if post.status -%}
    {%- assign status_txt = post.status | replace: "Submitted", "" | strip -%}
    {%- if status_txt contains "International Studies Quarterly" -%}
      {%- assign status_txt = status_txt | replace: "International Studies Quarterly", "<em>International Studies Quarterly</em>" -%}
    {%- endif -%}
    {%- if status_txt contains "Political Psychology" -%}
      {%- assign status_txt = status_txt | replace: "Political Psychology", "<em>Political Psychology</em>" -%}
    {%- endif -%}
    {%- if status_txt != "" -%}
      <p style="margin:.25rem 0 0;">{{ status_txt }}</p>
    {%- endif -%}
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
{%- endfor -%}

{%- comment -%} 2. R&R {%- endcomment -%}
{%- for post in rr_pp -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>

  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>
  {%- endunless -%}

  {%- if post.title == "Refugee Policies, Foreign Aid, and Political Violence in the Global South" -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.9em; color:#777;">
      2026 Dina Zinnes Best Graduate Student Paper Award, SSIP, ISA
    </p>
  {%- endif -%}

  {%- if post.status -%}
    {%- assign status_txt = post.status | replace: "Submitted", "" | strip -%}
    {%- if status_txt contains "International Studies Quarterly" -%}
      {%- assign status_txt = status_txt | replace: "International Studies Quarterly", "<em>International Studies Quarterly</em>" -%}
    {%- endif -%}
    {%- if status_txt contains "Political Psychology" -%}
      {%- assign status_txt = status_txt | replace: "Political Psychology", "<em>Political Psychology</em>" -%}
    {%- endif -%}
    {%- if status_txt != "" -%}
      <p style="margin:.25rem 0 0;">{{ status_txt }}</p>
    {%- endif -%}
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
{%- endfor -%}

{%- comment -%} 3. Submitted — single-authored first {%- endcomment -%}
{%- for post in submitted -%}
  {%- assign co = post.coauthors | to_s | strip -%}
  {%- if co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>

  {%- if post.title == "Refugee Policies, Foreign Aid, and Political Violence in the Global South" -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.9em; color:#777;">
      2026 Dina Zinnes Best Graduate Student Paper Award, SSIP, ISA
    </p>
  {%- endif -%}

  {%- if post.status -%}
    {%- assign status_txt = post.status | replace: "Submitted", "" | strip -%}
    {%- if status_txt contains "International Studies Quarterly" -%}
      {%- assign status_txt = status_txt | replace: "International Studies Quarterly", "<em>International Studies Quarterly</em>" -%}
    {%- endif -%}
    {%- if status_txt contains "Political Psychology" -%}
      {%- assign status_txt = status_txt | replace: "Political Psychology", "<em>Political Psychology</em>" -%}
    {%- endif -%}
    {%- if status_txt != "" -%}
      <p style="margin:.25rem 0 0;">{{ status_txt }}</p>
    {%- endif -%}
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
  {%- endif -%}
{%- endfor -%}

{%- comment -%} 4. Submitted — coauthored second {%- endcomment -%}
{%- for post in submitted -%}
  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>

  {%- if post.title == "Refugee Policies, Foreign Aid, and Political Violence in the Global South" -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.9em; color:#777;">
      2026 Dina Zinnes Best Graduate Student Paper Award, SSIP, ISA
    </p>
  {%- endif -%}

  {%- if post.status -%}
    {%- assign status_txt = post.status | replace: "Submitted", "" | strip -%}
    {%- if status_txt contains "International Studies Quarterly" -%}
      {%- assign status_txt = status_txt | replace: "International Studies Quarterly", "<em>International Studies Quarterly</em>" -%}
    {%- endif -%}
    {%- if status_txt contains "Political Psychology" -%}
      {%- assign status_txt = status_txt | replace: "Political Psychology", "<em>Political Psychology</em>" -%}
    {%- endif -%}
    {%- if status_txt != "" -%}
      <p style="margin:.25rem 0 0;">{{ status_txt }}</p>
    {%- endif -%}
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
  {%- endunless -%}
{%- endfor -%}

<hr class="section-split" />

{%- comment -%} Dissertation chapters (subset of publications) {%- endcomment -%}
{%- assign diss_shared = site.publications | where: "title", "Shared Suffering, Shared Peace? Refugee Return, Violent Displacement, and Communal Violence" -%}
{%- assign diss_beyond = site.publications | where: "title", "Beyond Violence: Manipulating Internal Displacement Through Selective Public Goods Provision During Civil War" -%}
{%- assign dissertation = diss_shared | concat: diss_beyond -%}

<h1 style="margin:0 0 .5rem; font-size:1.8rem;">Dissertation Chapters</h1>

{%- comment -%} Dissertation — single-authored first {%- endcomment -%}
{%- for post in dissertation -%}
  {%- assign co = post.coauthors | to_s | strip -%}
  {%- if co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
  {%- endif -%}
{%- endfor -%}

{%- comment -%} Dissertation — then coauthored (future-proof) {%- endcomment -%}
{%- for post in dissertation -%}
  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>
  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
  {%- endunless -%}
{%- endfor -%}

<hr class="section-split" />

<h1 style="margin:0 0 .5rem; font-size:1.8rem;">Working Papers</h1>

{%- comment -%} Working Papers — single-authored first (no per-item status line) {%- endcomment -%}
{%- for post in working -%}
  {%- if post.title != "Shared Suffering, Shared Peace? Refugee Return, Violent Displacement, and Communal Violence" and post.title != "Beyond Violence: Manipulating Internal Displacement Through Selective Public Goods Provision During Civil War" -%}
    {%- assign co = post.coauthors | to_s | strip -%}
    {%- if co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
    {%- endif -%}
  {%- endif -%}
{%- endfor -%}

{%- comment -%} Working Papers — then coauthored (no per-item status line) {%- endcomment -%}
{%- for post in working -%}
  {%- if post.title != "Shared Suffering, Shared Peace? Refugee Return, Violent Displacement, and Communal Violence" and post.title != "Beyond Violence: Manipulating Internal Displacement Through Selective Public Goods Provision During Civil War" -%}
    {%- assign co = post.coauthors | to_s | strip -%}
    {%- unless co == '' -%}
<article class="archive__item" style="margin:0 0 1rem 0;">
  <h2 class="archive__item-title no_toc" style="margin:0;">{{ post.title }}</h2>
  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">with <em>{{ co }}</em></p>
  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">{{ post.abstract }}</div>
    </details>
  {%- endif -%}
</article>
    {%- endunless -%}
  {%- endif -%}
{%- endfor -%}
