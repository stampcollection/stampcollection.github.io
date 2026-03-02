---
layout: default
title: My Stamp Collection
---

<h1>My Stamp Collection</h1>

{% assign stamps_countries_slugs = site.stamps | map: "country" | uniq | map: "slugify" %}

{% for country in site.data.countries %}
  {% assign country_slug = country | slugify %}
  {% if stamps_countries_slugs contains country_slug %}
    <a href="/countries/{{ country_slug }}/">{{ country }}</a><br>
  {% else %}
    <span>{{ country }}</span><br>
  {% endif %}
{% endfor %}