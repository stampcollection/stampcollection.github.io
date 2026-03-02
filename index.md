---
layout: default
title: My Stamp Collection
---

<h1>My Stamp Collection</h1>

{% assign stamps_countries = site.stamps | map: "country" %}

{% assign current_letter = "" %}

{% for country in site.data.countries %}

  {% assign first_letter = country | slice: 0 | upcase %}

  {% if first_letter != current_letter %}
    {% assign current_letter = first_letter %}
    <h2>{{ first_letter }}</h2>
  {% endif %}

  {% if stamps_countries contains country %}
    <a class="country-enabled"
       href="/countries/{{ country | downcase | replace: ' ', '-' }}.html">
       {{ country }}
    </a>
  {% else %}
    <span class="country-disabled">
      {{ country }}
    </span>
  {% endif %}

  <br>

{% endfor %}
