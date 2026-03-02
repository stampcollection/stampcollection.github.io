---
layout: default
title: My Stamp Collection
---

<h1>My Stamp Collection</h1>


{% assign stamps_countries_slugs = site.stamps | map: "country" | uniq | sort | map: "slugify" %}

{% for country in site.data.countries %}
  {% assign country_slug = country | slugify %}
  {% if stamps_countries_slugs contains country_slug %}
    <!-- Country has at least one stamp → clickable -->
    <a href="/countries/{{ country_slug }}/">{{ country }}</a><br>
  {% else %}
    <!-- Country has no stamps → plain text -->
    <span>{{ country }}</span><br>
  {% endif %}
{% endfor %}