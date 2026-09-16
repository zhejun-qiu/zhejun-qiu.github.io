---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

<!-- Hide built-in page title and style dividers + abstract toggle -->
<style>
  .page__title {
    display: none;
  }

  .section-split {
    border: 0;
    height: 1px;
    margin: 2.25rem 0 2rem;
    background: linear-gradient(
      90deg,
      transparent 0,
      #e3e3e3 18%,
      #cfcfcf 50%,
      #e3e3e3 82%,
      transparent 100%
    );
  }

  details.abstract {
    margin: .4rem 0 0;
  }

  details.abstract > summary {
    cursor: pointer;
    user-select: none;
    font-weight: 600;
    outline: none;
  }

  details.abstract > summary::marker {
    content: "▸ ";
  }

  details.abstract[open] > summary::marker {
    content: "▾ ";
  }

  .archive__item-excerpt {
    margin: .4rem 0 0;
    font-size: .9em;
  }
</style>


{%- assign peer_reviewed = site.publications
  | where: "status", "Accepted at International Studies Quarterly"
  | sort: "date"
  | reverse
-%}

{%- assign minor_pp = site.publications
  | where: "status", "Minor Revision at Political Psychology"
  | sort: "date"
  | reverse
-%}

{%- assign submitted = site.publications
  | where: "status", "Submitted"
  | sort: "date"
  | reverse
-%}

{%- assign working = site.publications
  | where: "status", "Working Paper"
  | sort: "date"
  | reverse
-%}


<!-- ========================================================= -->
<!-- PEER-REVIEWED PUBLICATIONS -->
<!-- ========================================================= -->

<h1 style="margin:1rem 0 .5rem; font-size:1.8rem;">
  Peer-Reviewed Publications
</h1>

{%- for post in peer_reviewed -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {% if post.paperurl %}
      <a href="{{ post.paperurl | relative_url }}"
         target="_blank"
         rel="noopener">
        {{ post.title }}
      </a>
    {% else %}
      {{ post.title }}
    {% endif %}
  </h2>

  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">
      with <em>{{ co }}</em>
    </p>
  {%- endunless -%}

  <p style="margin:.25rem 0 0;">
    <strong>Accepted</strong> at <em>International Studies Quarterly</em>
  </p>

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

{%- endfor -%}


<hr class="section-split" />


<!-- ========================================================= -->
<!-- UNDER REVIEW -->
<!-- ========================================================= -->

<h1 style="margin:0 0 .5rem; font-size:1.8rem;">
  Under Review
</h1>


<!-- 1. Political Psychology — Minor Revision -->

{%- for post in minor_pp -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  {%- assign co = post.coauthors | to_s | strip -%}
  {%- unless co == '' -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">
      with <em>{{ co }}</em>
    </p>
  {%- endunless -%}

  <p style="margin:.25rem 0 0;">
    <strong>Minor Revision</strong> at <em>Political Psychology</em>
  </p>

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

{%- endfor -%}


<!-- 2. Submitted — single-authored first -->

{%- for post in submitted -%}

  {%- assign co = post.coauthors | to_s | strip -%}

  {%- if co == '' -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  {%- if post.title == "Refugee Policies, Foreign Aid, and Political Violence in the Global South" -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.9em; color:#777;">
      2026 Dina Zinnes Best Graduate Student Paper Award, SSIP, ISA
    </p>
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

  {%- endif -%}

{%- endfor -%}


<!-- 3. Submitted — coauthored second -->

{%- for post in submitted -%}

  {%- assign co = post.coauthors | to_s | strip -%}

  {%- unless co == '' -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">
    with <em>{{ co }}</em>
  </p>

  {%- if post.title == "Refugee Policies, Foreign Aid, and Political Violence in the Global South" -%}
    <p style="margin:.2rem 0 0; font-style:italic; font-size:.9em; color:#777;">
      2026 Dina Zinnes Best Graduate Student Paper Award, SSIP, ISA
    </p>
  {%- endif -%}

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

  {%- endunless -%}

{%- endfor -%}


<hr class="section-split" />


<!-- ========================================================= -->
<!-- DISSERTATION CHAPTERS -->
<!-- ========================================================= -->

{%- assign diss_shared = site.publications
  | where: "title",
  "Shared Suffering, Shared Peace? Refugee Return, Violent Displacement, and Communal Violence"
-%}

{%- assign diss_beyond = site.publications
  | where: "title",
  "Beyond Violence: Manipulating Internal Displacement Through Selective Public Goods Provision During Civil War"
-%}

{%- assign dissertation = diss_shared | concat: diss_beyond -%}


<h1 style="margin:0 0 .5rem; font-size:1.8rem;">
  Dissertation Chapters
</h1>


<!-- Dissertation — single-authored first -->

{%- for post in dissertation -%}

  {%- assign co = post.coauthors | to_s | strip -%}

  {%- if co == '' -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

  {%- endif -%}

{%- endfor -%}


<!-- Dissertation — coauthored future-proof -->

{%- for post in dissertation -%}

  {%- assign co = post.coauthors | to_s | strip -%}

  {%- unless co == '' -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">
    with <em>{{ co }}</em>
  </p>

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

  {%- endunless -%}

{%- endfor -%}


<hr class="section-split" />


<!-- ========================================================= -->
<!-- WORKING PAPERS -->
<!-- ========================================================= -->

<h1 style="margin:0 0 .5rem; font-size:1.8rem;">
  Working Papers
</h1>


<!-- Working Papers — single-authored first -->

{%- for post in working -%}

  {%- if post.title != "Shared Suffering, Shared Peace? Refugee Return, Violent Displacement, and Communal Violence"
      and post.title != "Beyond Violence: Manipulating Internal Displacement Through Selective Public Goods Provision During Civil War" -%}

    {%- assign co = post.coauthors | to_s | strip -%}

    {%- if co == '' -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

    {%- endif -%}

  {%- endif -%}

{%- endfor -%}


<!-- Working Papers — coauthored second -->

{%- for post in working -%}

  {%- if post.title != "Shared Suffering, Shared Peace? Refugee Return, Violent Displacement, and Communal Violence"
      and post.title != "Beyond Violence: Manipulating Internal Displacement Through Selective Public Goods Provision During Civil War" -%}

    {%- assign co = post.coauthors | to_s | strip -%}

    {%- unless co == '' -%}

<article class="archive__item" style="margin:0 0 1rem 0;">

  <h2 class="archive__item-title no_toc" style="margin:0;">
    {{ post.title }}
  </h2>

  <p style="margin:.2rem 0 0; font-style:italic; font-size:.95em;">
    with <em>{{ co }}</em>
  </p>

  {%- if post.abstract -%}
    <details class="abstract">
      <summary>Abstract</summary>
      <div class="archive__item-excerpt">
        {{ post.abstract }}
      </div>
    </details>
  {%- endif -%}

</article>

    {%- endunless -%}

  {%- endif -%}

{%- endfor -%}
