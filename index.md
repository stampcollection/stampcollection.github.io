---
layout: default
title: My Stamp Collection
markdown: false
---

<h1>My Stamp Collection</h1>

{% assign stamps_countries_slugs = site.stamps | map: "country" | uniq | map: "slugify" %}
{% assign current_letter = "" %}

{% for country in site.data.countries %}
  {% assign first_letter = country | slice: 0 | upcase %}
  {% assign country_slug = country | slugify %}

  {% if first_letter != current_letter %}
    {% assign current_letter = first_letter %}
    <h2>{{ current_letter }}</h2>
  {% endif %}

  {% if stamps_countries_slugs contains country_slug %}
    <a href="/countries/{{ country_slug }}/">{{ country }}</a><br>
  {% else %}
    <span>{{ country }}</span><br>
  {% endif %}
{% endfor %}