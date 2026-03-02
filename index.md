---
layout: default
title: My Stamp Collection
---

<h1>My Stamp Collection</h1>

{% assign stamps_countries = site.stamps | map: "country" | uniq %}

{% for country in site.data.countries %}
  {% if stamps_countries contains country %}
    <!-- Country has at least one stamp → clickable -->
    <a href="/countries/{{ country | slugify }}/">{{ country }}</a><br>
  {% else %}
    <!-- Country has no stamps → plain text -->
    <span>{{ country }}</span><br>
  {% endif %}
{% endfor %}