---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{%- comment -%}
This page lists every item in the "publications" collection.
Requirements for items to appear:
  1) Files live in a folder named _publications/ (plural)
  2) Each file has front matter with:
       collection: publications
       title: "..."
       date: YYYY-MM-DD
Optional fields: authors, venue, permalink, etc.
{%- endcomment -%}

{%- assign items = site.publications | sort: "date" -%}
<p class="archive__subtitle" style="opacity:.7">Found {{ items | size }} item(s).</p>

{%- if items and items.size > 0 -%}
  {%- for post in items reversed -%}
    {%- include archive-single.html -%}
  {%- endfor -%}
{%- else -%}
  <p>No research items found. Make sure your files are in <code>_publications/</code> and each has <code>collection: publications</code> in the front matter.</p>
{%- endif -%}

{%- comment -%}
If you later want grouped headings (Books / Journal Articles / Conferences),
uncomment this block AND ensure each item has a matching "category" value.

{% if site.publication_category %}
  {% for category in site.publication_category %}
    {% assign title_shown = false %}
    {% for post in site.publications reversed %}
      {% if post.category != category[0] %}{% continue %}{% endif %}
      {% unless title_shown %}
        <h2>{{ category[1].title }}</h2><hr />
        {% assign title_shown = true %}
      {% endunless %}
      {% include archive-single.html %}
    {% endfor %}
  {% endfor %}
{% endif %}
{%- endcomment -%}

