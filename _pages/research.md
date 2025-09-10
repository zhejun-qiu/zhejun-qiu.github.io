---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

{% assign items = site.publications | sort: "date" %}
{% for post in items reversed %}
  {% include archive-single.html %}
{% endfor %}
