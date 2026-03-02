---
layout: default
title: My Stamp Collection
---

<h1>My Stamp Collection</h1>

{% assign current_letter = "" %}
{% assign countries = site.stamps | map: "country" | uniq | sort %}

{% for country in countries %}
  {% assign first_letter = country | slice: 0 | upcase %}

  {% if first_letter != current_letter %}
    {% assign current_letter = first_letter %}
    <h2>{{ current_letter }}</h2>
  {% endif %}

  <a href="/countries/{{ country | slugify }}/">{{ country }}</a><br>
{% endfor %}